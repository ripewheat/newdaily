ffmpeg -i input.mp4 -i cover.png -map 0 -map 1 -c copy -disposition:v:1 attached_pic output.mp4

将图片 cover.png 做为 input.mp4 的封面图。

关键是 `-disposition:v:1 attached_pic` 这句，即把 map 后的第二个视频流（ cover.png ）做为 output.mp4 的封面。