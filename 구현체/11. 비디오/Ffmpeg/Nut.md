https://ffmpeg.org/nut.html

https://www.ffmpeg.org/~michael/nut.txt

어떤 시간 동기화가 필요한 경우 사용

---

```
data_size = lsb + msb * mul - elision

lsb = (main_header)lsb[frame_code]
msb = (frame) v
mul = (main_header)mul[frame_code]
elision = (main_header)elision_header[header_idx]

즉, frame_code와 header_idx 를 알아야함.
frame_code = (frame) f(8) ( 즉, < 256 )
header_idx = (frame) v

---
msb_pts_shift = (stream) , 7이라고 해보자
1 << msb_pts_shift = 10000000
mask = 01111111 (-1)
mask/2 = 00111111 (>>1)
delta = last_pts - mask/2

pts_l

```