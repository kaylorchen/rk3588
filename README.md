# 添加源
```bash
sudo wget http://apt.kaylordut.cn/kaylor-keyring.gpg -O /etc/apt/keyrings/kaylor-keyring.gpg
sudo tee /etc/apt/sources.list.d/kaylor-rk3588.list <<EOF
deb [signed-by=/etc/apt/keyrings/kaylor-keyring.gpg] http://apt.kaylordut.cn/rk3588/ubuntu/ $(lsb_release -sc) main
EOF
```
