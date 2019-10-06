# Media

Commands for converting, processing, optimising and managing media files

## VLC

Demuxing raw PCM audio for playback

    vlc --demux=rawaud --rawaud-channels <channel-count> --rawaud-samplerate <sample-rate> <file>

Example 2 channel PCM audio at 8kHz

    vlc --demux=rawaud --rawaud-channels 2 --rawaud-samplerate 8000 audio.pcm

## WebP

Install Google WebP image processor

    brew install webp

Decompress WebP image to PNG

    dwebp <wepb-image-file> -o <png-output-filename>

Decompress all WebP images in current directory to PNG images (processing 8 in parallel)

    find . -type f -name "*.webp" | xargs -P 8 -I {} dwebp {} -o {}.png

Compress image to WebP format using specified quality from 0 to 100

    cwebp -q <quality> <input-file> -o <output-file>
