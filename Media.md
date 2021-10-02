# Media

Commands for converting, processing, optimising and managing media files

## Information

Show basic information about media file

    file <media-file>

Show detailed information about image files (macOS only)

    sips -g all <image-file>

Show detailed information about audio files (macOS only)

    afinfo <audio-file>

Show information from multimedia streams and files (requires ffmpeg)

    ffprobe <audio-file>

# Images

## Sips

Sips - Scriptable image processing system (macOS only)

- Formats: jpeg, tiff, png, gif, jp2, pict, bmp, qtif, psd, sgi, tga

Convert image between file formats (Quality: 0 - 100 or low, normal, high, best)

    sips -s format <format> -s formatOptions <quality> <input-file> --out <output-file>

Example converting PNG to JPG using high quality compression

    sips -s format jpeg -s formatOptions high foo.png --out foo.jpg

Examples batch processing all JPG files

    sips -s format jpeg -s formatOptions low *.jpg
    sips --resampleWidth 300 *.jpg

Scale width or height of image in pixels maintaining aspect ratio

    sips --resampleWidth <width> <input-file> --out <output-file>
    sips --resampleHeight <height> <input-file> --out <output-file>

Scale both width and height until either reach the max dimension (`-Z` flag)

    sips --resampleHeightWidthMax <max-dimension> <input-file> --out <output-file>
    sips -Z <max-dimension> <input-file> --out <output-file>

Resize image to exact height and width regardless of aspect ratio

    sips -z <height> <width> <file>

Rotate image by specified degrees clockwise

    sips -r <degrees-clockwise> <file>

Flip image in specified direction (horizontal, vertical)

    sips -f <direction> <file>

Crop image to specified height and width

    sips -c <height> <width> <file>

Pad image by expanding size (with optional fill colour for added region)

    sips -p <height> <width> <file>
    sips -p <height> <width> --padColor <hex-color> <file>

## WebP

Install Google WebP image processor

    brew install webp

Decompress WebP image to PNG

    dwebp <wepb-image-file> -o <png-output-filename>

Decompress all WebP images in current directory to PNG images (processing 8 in parallel)

    find . -type f -name "*.webp" | xargs -P 8 -I {} dwebp {} -o {}.png

Compress image to WebP format using specified quality from 0 to 100

    cwebp -q <quality> <input-file> -o <output-file>

# Audio / Video

## Audio File Utilities

Play audio file (macOS only)

    afplay <file>

Play audio file with volume (`-v`), playback rate (`-r`) and duration in seconds (`-t`)

    afplay <file> -v <volume> -r <rate> -t <time>

Convert audio file format

    afconvert -f <file-format> -d <data-format> -b <bit-rate> <input-file> <output-file>

Example converting audio file from wav to mp3 at 128kbps

    afconvert -f mp4f -d aac -b 128000 input.wav output.mp3

## FFmpeg

Install FFmpeg audio / video processor

    brew install ffmpeg

Play audio file (`-nodisp` for direct CLI playback without GUI)

    ffplay <audio-file>
    ffplay -nodisp <audio-file>

## VLC

Open network stream

    vlc <stream-url>

Demuxing raw PCM audio for playback

    vlc --demux=rawaud --rawaud-channels <channel-count> --rawaud-samplerate <sample-rate> <file>

Example 2 channel PCM audio at 8kHz

    vlc --demux=rawaud --rawaud-channels 2 --rawaud-samplerate 8000 audio.pcm

## youtube-dl

Install youtube-dl

    brew install youtube-dl

List media format and quality options available

    youtube-dl -F '<video-url>'

Download mp4 video file

    youtube-dl -f best[ext=mp4] '<video-url>'

Download mp3 audio file

    youtube-dl -fx best --audio-format mp3 '<video-url>'

Pipe output directly to VLC

    youtube-dl -o - '<video-url>' | vlc -

Pipe output directly to Chromecast via VLC

    youtube-dl -o - '<video-url> | vlc --sout="#chromecast{ip=<chromecast-ip>}" -
