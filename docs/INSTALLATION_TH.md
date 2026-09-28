# ติดตั้งบน Debian 13 — ภาษาไทย

## Requirements

```text
Debian 13 x86_64
LAN access to PTZ camera
Git + Git LFS
sudo/root access
```

## Clone

```bash
sudo apt update
sudo apt install -y git git-lfs
git lfs install
git clone https://github.com/Supakorn289/smart-fire-detection-v2.1.git ~/smart-fire-release
cd ~/smart-fire-release
git lfs pull
```

## ตรวจ model

```bash
ls -lh models/fire.pt
sha256sum models/fire.pt
```

Expected SHA-256:

```text
49dc0464d99a6c250cf3c3e305d4149c3d4ce3ee354d9d7a5ae1cb8c53a22183
```

## Bootstrap

```bash
sudo ./deploy/install-manager-stack.sh
```

Path สำคัญ:

```text
/opt/smart-fire-detection-v2
/etc/smart-fire-detection/production.env
/etc/smart-fire-detection/manager.token
```

อย่านำสองไฟล์ใน `/etc/smart-fire-detection/` ขึ้น GitHub

## ตรวจ Manager

```bash
systemctl --no-pager status smart-fire-manager.service
ss -lntp | grep ':5050'
```

เปิด `http://<SERVER-IP>:5050/`

## ก่อน Commissioning

เตรียม Camera IP, username/password, PTZ/HTTP port, RTSP port/path, Preset P1–P9, checkerboard, ระยะจริง และ landmark สำหรับ Geometry

การติดตั้ง software ผ่านไม่ได้หมายถึง Production acceptance ของ Site ใหม่ ต้องทำ commissioning และ validation ตามหน้างานจริง
