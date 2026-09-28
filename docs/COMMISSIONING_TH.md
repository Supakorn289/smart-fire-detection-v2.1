# Commissioning 0→100 — ภาษาไทย

## PTZ Presets

ตั้ง P1–P9 ในตัวกล้องด้วย CamFinder/เครื่องมือผู้ผลิตก่อน แล้วใช้ Manager ตรวจ

```text
P1   0°
P2  45°
P3  90°
P4 135°
P5 177.5°
P6 315°
P7 270°
P8 225°
P9 182.5°
```

## ลำดับทำงาน

```text
Camera / RTSP
→ PTZ Verification
→ Camera Intrinsics
→ Distance Calibration
→ Distance Verification
→ Cross-Preset Geometry
→ Final Verification
→ Immutable Revision
→ Activation Plan
→ Activate
```

PRODUCTION เพิ่ม:

```text
True North
GPS
Telegram
Full Sweep
Runtime Soak / Acceptance
```

## Intrinsics

เก็บ checkerboard หลายตำแหน่ง/ระยะ/orientation หลีกเลี่ยงภาพซ้ำมุมเดิมทั้งหมด

## Distance

แยก Calibration points กับ Verification points ห้ามใช้ชุดเดียวกันเป็น independent validation

## Geometry overlap pairs

```text
P1-P2 P2-P3 P3-P4 P4-P5 P1-P6 P6-P7 P7-P8 P8-P9 P5-P9
```

แยก Fit marks และ Holdout marks

## Activation

ใช้เฉพาะ revision ที่ validated แล้ว ระบบออกแบบให้ backup → atomic switch → preflight → restart → health check และ rollback เมื่อ fail

## ห้ามทำ

- ห้าม copy calibration Site อื่นโดยไม่ validate
- ห้ามแก้ ACTIVE calibration เพื่อข้าม gate
- ห้ามเปิด True North/GPS แบบเดา
- ห้ามเผยแพร่ credential/token/private coordinates
