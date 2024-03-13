```
ffmpeg \
-y \
-threads 0 \
-i 'srt://3.37.111.252:5002?mode=caller' \
-c:v libx264 \
-crf 13 \
-maxrate 100000000 \
-bufsize 100000000 \
-time_base 1/90000 \
-g 1 \
-c:a aac \
-f_strict experimental \
-syncpoints none \
-write_index false \
-f nut -

```