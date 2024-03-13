ffmpeg {전역옵션} {입력 파일 옵션} {입력url} {출력파일 옵션} {출력url}

- 해상도 변경
```
ffmpeg -i Astalgia_of_Phantasm_text.mp4 -vf "scale=-1:720" output.mp4

ffmpeg -i Astalgia_of_Phantasm_text.mp4 -s 1920x1080 output.mp4
```


- CRF 적용
	- 오디오의 경우 -strict experimental을 해야한다나 뭐라나
```
ffmpeg -i Big_Buck_Bunny_1080_10s_30MB.mp4 -c:v libx264 -crf 45 -c:a aac -strict experimental output_45.mp4

ffmpeg -i output_43.mp4 -c:v libx264 -crf 23 -c:a aac -strict experimental output_43_23.mp4

```

  
- n초 간격으로 자르기
```
ffmpeg -i Astalgia_of_Phantasm_text.mp4 -reset_timestamps 1 -sc_threshold 0 -g 5 -force_key_frames "expr:gte(t, n_forced * 5)" -segment_time 5 -f segment ./segment/output_%03d.mp4

-force_key_frames "expr:gte(t, n_forced * 5)"
를 통해서 I 프레임을 강제로 5초 간격으로 넣어주어야함.

```

- 일정 부분 30초 자르기
```
ffmpeg -i input.mp4 -c:v libx264 -c:a copy -ss 00:10:00 -t 00:00:30 output.mp4
```

- 여러 인코딩 옵션들
```
ffmpeg -y -i Big_Buck_Bunny_1080_10s_30MB.mp4 \
-pix_fmt yuv420p \
-vcodec libx264 -vprofile main -level 30 -b:v 4000k -minrate 0 -maxrate 8000k -bufsize 700k -r:v 30.00 -tune zerolatency \
-vf "scale=-1:-1" \
-movflags faststart \
-f mp4 output.mp4

```
  

- 머지
```
ffmpeg -f concat -safe 0 -i list.txt -c copy 출력파일.mp4

list.txt
file 'input0.mp4'
file 'input1.mp4'
...

머지시 dts 오류 -> timescale을 일치시켜서 인코딩 해야함.
-video_track_timescale 24000

```


- vmaf
```
ffmpeg -i output_op0_000.mp4 -i output_org_000.mp4 -filter_complex "[0:v]framerate=30,scale=1920x1080[distorted];[1:v]framerate=30[ref];[distorted][ref]libvmaf" -f null -
```

- 씬 감지
```
ffmpeg -y -i Astalgia_of_Phantasm_text.mp4 -vf "select=gt(scene\,0.2),scale=640:-1,tile=6x80" -frames:v 1 -qscale:v 3 preview.jpg
```


- 인코딩 정보 삽입
```

```

- RTMP - > ts
```
ffmpeg -i rtmp://127.0.0.1/live/SkKKgrkEp -flags +global_header -f segment -segment_time 60 reset_timestamps 1 -vf scale=1920:-1 test_v0_1920.%d.ts
```

권장 비트레이트

　 576, 30fps : 1500Kbps = 1.5Mbps

　 720, 24fps : 2000Kbps = 2 Mbps

　 720, 30fps : 2500Kbps = 2.5Mbps

　 720, 48fps : 3100Kbps = 3.1Mbps

　 720, 60fps : 3500Kbps = 3.5Mbps

　1080, 24fps : 3500Kbps = 3.5Mbps

　1080, 30fps : 4000Kbps = 4 Mbps

　1080, 48fps : 4900Kbps = 4.9Mbps

　1080, 60fps : 5500Kbps = 5.5Mbps

    
