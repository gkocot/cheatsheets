Generate test video and make it available as RTSP/RTP stream.
```code
ffmpeg -f lavfi -i testsrc=size=640x480:rate=30 -vf "drawtext=text='%{pts\:gmtime\:$(date +%s)\:%H-%M-%S} %{n}':box=1:boxcolor=0x00000000@1:fontsize=30:fontcolor=white, format=yuv420p" -vcodec libx264 -f mpegts - | cvlc - --no-sout-audio --sout-keep --sout=#gather:rtp{sdp=rtsp://192.168.2.184:8554/test}
```

Loop video file over RTSP/RTP.
```code
cvlc 5754_d11079f1-c91e-4d65-ae4e-8d3f417baa48_S0.mp4 --loop --no-sout-audio --sout-keep --sout=#gather:rtp{sdp=rtsp://192.168.2.184:8554/test}
```
