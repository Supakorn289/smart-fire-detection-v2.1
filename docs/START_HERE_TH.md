# เริ่มต้นใช้งาน Smart Fire Detection v2

## 1. เครื่องเป้าหมาย

แนะนำ Debian 13 x86_64, Python 3.12 และ network ที่เข้าถึง PTZ camera ได้

## 2. ติดตั้ง Git LFS และ Clone

```bash
sudo apt update
sudo apt install -y git git-lfs
git lfs install

git clone https://github.com/Supakorn289/smart-fire-detection-v2.1.git ~/smart-fire-release
cd ~/smart-fire-release
git lfs pull
```

ตรวจ model:

```bash
sha256sum models/fire.pt
```

ต้องได้:

```text
49dc0464d99a6c250cf3c3e305d4149c3d4ce3ee354d9d7a5ae1cb8c53a22183
```

## 3. ติดตั้งระบบ

```bash
sudo ./deploy/install-manager-stack.sh
```

Installer จะติดตั้ง source ไป `/opt/smart-fire-detection-v2`, สร้าง production environment, Manager token และ systemd services

## 4. ตรวจ service

```bash
systemctl is-active smart-fire-manager.service
systemctl is-active smart-fire-manager-agent.service
systemctl is-active smart-fire-calibration-worker.service
systemctl is-active smart-fire-calibration-watchdog.service
systemctl is-active smart-fire-detection.service
systemctl is-enabled smart-fire-detection.service
```

ก่อน Activation: Manager/Agent/Worker/Watchdog ควร active และ Detection ควร inactive/disabled

## 5. เปิด Manager

```bash
hostname -I
sudo cat /etc/smart-fire-detection/manager.token
```

เปิด `http://<SERVER-IP>:5050/` แล้วเลือก **ตั้งค่าพื้นที่ใหม่**

อ่านต่อ: [COMMISSIONING_TH.md](COMMISSIONING_TH.md)

> ห้าม copy calibration ของ Site อื่นมาใช้แทน Site ใหม่โดยไม่ validate
