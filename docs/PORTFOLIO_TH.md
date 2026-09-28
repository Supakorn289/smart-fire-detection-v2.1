# Portfolio Guide — ภาษาไทย

## Project Summary

ระบบ Edge AI ตรวจจับไฟ/ควันด้วยกล้อง PTZ ที่รวม Computer Vision, calibrated camera geometry, distance estimation, cross-preset fusion และ web commissioning/deployment บน Debian

## Engineering Highlights

- Ultralytics YOLO + PyTorch CPU
- Multi-frame confirmation
- PTZ synchronization / stable-frame gate
- Camera intrinsics / distance calibration
- Cross-preset rotation geometry
- Cross-preset object fusion
- Alert deduplication / Telegram
- Flask + Waitress Commissioning Manager
- Immutable revision / activation / rollback
- systemd deployment
- GitHub Actions / automated tests

## Public validation

```text
Repository CI: PASS
Full Software Tests: PASS
Automated tests: 142 PASS
Offline preflight: 0 failures
```

## Historical LAB geometry result

| Metric | Result |
|---|---:|
| Holdout targets | 353 |
| Median abs azimuth error | 0.738° |
| Mean abs azimuth error | 0.853° |
| P90 abs azimuth error | 1.693° |
| Pair checks | 9/9 PASS |

ผลนี้เป็น historical LAB evidence ไม่ใช่ accuracy guarantee ของ Site ใหม่

## GitHub media ที่ควรเพิ่ม

```text
assets/hero.png
assets/hardware-setup.jpg
assets/manager-overview.png
assets/commissioning-wizard.png
assets/architecture.png
assets/detection-demo.gif
```

ต้อง sanitize credential, private IP/coordinates, faces/license plates ตามความเหมาะสม

## Resume bullet

> Developed an AI PTZ fire/smoke surveillance platform on Debian using Python, OpenCV, Ultralytics YOLO, calibrated camera geometry, web commissioning, systemd services, and transactional activation/rollback with automated testing and GitHub CI.
