# Video engineer task 01


Your task is to create a script that takes `stream` or `file` as an input and returns `Low Latency MPEG-DASH` stream.

    $ script -source <url/file> -target master.mpd [options]

## Acceptance criteria:
- Any programming language, whatever libraries are necessary
- Use FFMPEG binary or FFMPEG framework API
- Encoder any of `libx264`, `nvenc_h264`, `qsv_h264`
- ABR target stream (1080p, 720p, 480p)
- Custom I-frames pattern (option: `-idr <int>`)
- Burn-in local time clock in picture while transcoding
- Deliver the project via a public GitHub repository

## Bonus points:
- Tune encoder settings to get:
  - minimal VBR bitrate fluctuations
  - suggest optimal picture quality/bitrate balance for each stream in asset
- Get parallel HLS output stream in the same FFMPEG command line
- Use signle decoder for all encoders in FFMPEG pipeline
- Use nvenc/qsv hardware encoding (option: `-encoder <nvenc_h264/qsv_h264/libx264>`)
- Wait for a stream to start and analyze any 60 seconds of target DASH stream to get:
  - GOP/I-frames structure with timecodes (ffprobe or any other tool).
  - VMAF/SSIM/PSNR values
