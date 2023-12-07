# 添加源
```bash
sudo wget http://apt.kaylordut.cn/kaylor-keyring.gpg -O /etc/apt/keyrings/kaylor-keyring.gpg
sudo tee /etc/apt/sources.list.d/kaylor-rk3588.list <<EOF
deb [signed-by=/etc/apt/keyrings/kaylor-keyring.gpg] http://apt.kaylordut.cn/rk3588/ubuntu/ $(lsb_release -sc) main
EOF
```

# gstreamer
```bash
sudo  gst-launch-1.0 -vvv v4l2src device=/dev/video12 ! video/x-raw, format=(string)YUY2, width=640, height=480 ! mpph264enc ! h264parse ! rtph264pay ! udpsink host=192.168.23.111 port=5600
gst-launch-1.0 udpsrc port=5600 caps='application/x-rtp, media=(string)video, clock-rate=(int)90000, encoding-name=(string)H264' ! rtph264depay ! avdec_h264 ! clockoverlay valignment=bottom ! autovideosink fps-update-interval=1000 sync=false
```
