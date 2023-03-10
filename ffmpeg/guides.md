# Basic Usages

## Converting a video format:

`ffmpeg -i input.mp4 output.avi`

This command converts a video file from MP4 format to AVI format.

## Extracting audio from a video:

`ffmpeg -i input.mp4 -vn -acodec copy output.mp3`

This command extracts the audio from the input video file and saves it as an MP3 file. The `-vn` option tells FFmpeg to ignore the video stream and only process the audio stream, and the `-acodec` copy option tells FFmpeg to copy the audio codec from the input file to the output file without re-encoding it.

## Cutting a video:

`ffmpeg -i input.mp4 -ss 00:01:00 -t 00:00:30 -c copy output.mp4`

This command cuts a 30-second segment from the input video starting at the 1-minute mark and saves it as a new MP4 file. The `-ss` option specifies the start time in the format `HH:MM:SS`, and the `-t` option specifies the duration of the segment.

## Merging multiple videos:

`ffmpeg -i "concat:input1.mp4|input2.mp4|input3.mp4" -c copy output.mp4`

This command merges multiple video files into a single file. The `concat` filter is used to concatenate the input files, and the `-c` copy option tells FFmpeg to copy the video and audio codecs from the input files to the output file without re-encoding them.

# Advance Usages

## Changing video resolution and aspect ratio:

`ffmpeg -i input.mp4 -vf "scale=640:360,setsar=1:1" -c:v libx264 -crf 18 -preset veryfast -c:a copy output.mp4`

This command rescales the input video to a resolution of 640x360 and sets the aspect ratio to 1:1. The `-vf` option is used to specify the video filtergraph, and the `scale` and `setsar` filters are used to resize the video and adjust the aspect ratio. The `-c:v` option specifies the video codec, and the `-crf` and `-preset` options are used to control the quality and encoding speed. The `-c:a` copy option tells FFmpeg to copy the audio stream from the input file to the output file without re-encoding it.

## Adding subtitles to a video:

`ffmpeg -i input.mp4 -vf subtitles=subs.srt -c:v libx264 -crf 18 -preset veryfast -c:a copy output.mp4`

This command adds subtitles to the input video from a separate SRT file called subs.srt. The `-vf` option is used to specify the video filtergraph, and the subtitles filter is used to add the subtitles to the video. The rest of the command is similar to the previous example.

## Extracting frames from a video:

`ffmpeg -i input.mp4 -ss 00:01:00 -r 1 -vframes 1 output.jpg`

This command extracts a single frame from the input video at the 1-minute mark and saves it as a JPEG image file. The `-r` option specifies the frame rate, and the `-vframes` option specifies the number of frames to extract.

## Converting audio files to different formats:

`ffmpeg -i input.flac -ab 320k output.mp3`

This command converts an input FLAC audio file to an MP3 file with a bit rate of 320 kbps. The `-ab` option specifies the audio bit rate.
