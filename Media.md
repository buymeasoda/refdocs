# Media

Commands for converting, processing, optimising and managing media files

# VLC

## Demux

Demuxing raw PCM audio for playback

    vlc --demux=rawaud --rawaud-channels <channel-count> --rawaud-samplerate <sample-rate> <file>

Example 2 channel PCM audio at 8kHz

    vlc --demux=rawaud --rawaud-channels 2 --rawaud-samplerate 8000 audio.pcm
