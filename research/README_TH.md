# Research Package — ภาษาไทย

เอกสารงานวิจัยหลัก:

- [METHODOLOGY.md](METHODOLOGY.md)
- [REPRODUCIBILITY.md](REPRODUCIBILITY.md)
- [RESULTS.md](RESULTS.md)
- [MODEL_CARD.md](MODEL_CARD.md)
- [DATA_AVAILABILITY.md](DATA_AVAILABILITY.md)
- [CITATION.cff](../CITATION.cff)

ทุก experiment ควรบันทึก Git tag/commit, model SHA-256, hardware, OS/Python, camera/resolution/lens state, calibration revision, LAB/PRODUCTION mode, sample counts และ fit/holdout separation

Historical LAB geometry validation:

```text
Holdout targets: 353
Median abs azimuth error: 0.738°
Mean abs azimuth error: 0.853°
P90 abs azimuth error: 1.693°
Max abs azimuth error: 4.523°
Median 3D angular error: 0.885°
P90 3D angular error: 1.856°
Pair checks: 9/9 PASS
```

ผลดังกล่าวเป็น historical laboratory evidence ไม่ใช่ค่ารับประกันของ Site ใหม่
