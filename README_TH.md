# Smart Fire Detection v2 — ภาษาไทย

[![Repository CI](https://github.com/Supakorn289/smart-fire-detection-v2.1/actions/workflows/ci.yml/badge.svg)](https://github.com/Supakorn289/smart-fire-detection-v2.1/actions/workflows/ci.yml)
[![Full Software Tests](https://github.com/Supakorn289/smart-fire-detection-v2.1/actions/workflows/full-tests.yml/badge.svg)](https://github.com/Supakorn289/smart-fire-detection-v2.1/actions/workflows/full-tests.yml)
[![Release](https://img.shields.io/github/v/release/Supakorn289/smart-fire-detection-v2.1)](https://github.com/Supakorn289/smart-fire-detection-v2.1/releases)

ระบบตรวจจับไฟและควันด้วย AI สำหรับกล้อง PTZ IP Camera บน Debian Linux พร้อม Web Commissioning Manager, Camera Intrinsics, Distance Calibration, Cross-Preset Geometry, Revision, Safe Activation และ Rollback

> เป็นระบบวิจัย/วิศวกรรม ไม่ใช่อุปกรณ์ Fire Alarm ที่ผ่านการรับรองมาตรฐาน

## เริ่มจากตรงไหนดี

| เป้าหมาย | เอกสาร |
|---|---|
| ติดตั้งบนเครื่องใหม่ | [START_HERE_TH](docs/START_HERE_TH.md) |
| ติดตั้ง Debian แบบละเอียด | [INSTALLATION_TH](docs/INSTALLATION_TH.md) |
| Commissioning 0→100 | [COMMISSIONING_TH](docs/COMMISSIONING_TH.md) |
| แก้ปัญหา | [TROUBLESHOOTING_TH](docs/TROUBLESHOOTING_TH.md) |
| Portfolio | [PORTFOLIO_TH](docs/PORTFOLIO_TH.md) |
| Research | [Research ภาษาไทย](research/README_TH.md) |

## สถานะ

- Public source code: พร้อม
- GitHub Release: พร้อม
- Git LFS model distribution: พร้อม
- Repository CI: PASS
- Full Software Tests: PASS
- Automated tests: 142 PASS
- Offline preflight: 0 failures
- Site calibration: ต้องทำใหม่ตามกล้อง/สถานที่
- Production True North/GPS/Telegram acceptance: ต้องตรวจหน้างานจริง

## ติดตั้งแบบย่อ

```bash
sudo apt update
sudo apt install -y git git-lfs
git lfs install

git clone https://github.com/Supakorn289/smart-fire-detection-v2.1.git ~/smart-fire-release
cd ~/smart-fire-release
git lfs pull

sha256sum models/fire.pt
sudo ./deploy/install-manager-stack.sh
```

Expected model SHA-256:

```text
49dc0464d99a6c250cf3c3e305d4149c3d4ce3ee354d9d7a5ae1cb8c53a22183
```

หลังติดตั้งเปิด:

```text
http://<SERVER-IP>:5050/
```

Manager token:

```bash
sudo cat /etc/smart-fire-detection/manager.token
```

## Workflow

```text
Camera / RTSP
→ PTZ Presets
→ Intrinsics
→ Distance
→ Distance Verification
→ Cross-Preset Geometry
→ Final Verification
→ Revision
→ Activation
```

PRODUCTION ต้องตรวจ True North / GPS / Telegram / Full Sweep / Runtime Acceptance เพิ่มตาม Site จริง

## Portfolio / Research

โปรเจกต์แสดงทักษะด้าน Computer Vision, Edge AI, PTZ control, camera calibration, geometric localization, Flask/Waitress, Debian/systemd, CI/testing และ reproducible research

ดู [PORTFOLIO_TH](docs/PORTFOLIO_TH.md) และ [research/README_TH.md](research/README_TH.md)

## ห้ามนำขึ้น Public GitHub

- Camera password
- Telegram token/chat ID
- Manager token
- `production.env`
- private coordinates/captures
- `calibration/.manager/`
- Site-specific active calibration/revisions
