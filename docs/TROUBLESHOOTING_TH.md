# Troubleshooting — ภาษาไทย

## Service status

```bash
systemctl is-active smart-fire-manager.service smart-fire-manager-agent.service smart-fire-detection.service smart-fire-calibration-worker.service smart-fire-calibration-watchdog.service
```

## Logs

```bash
sudo journalctl -u smart-fire-manager.service -n 100 --no-pager
sudo journalctl -u smart-fire-manager-agent.service -n 100 --no-pager
sudo journalctl -u smart-fire-calibration-worker.service -n 100 --no-pager
sudo journalctl -u smart-fire-detection.service -n 150 --no-pager
```

## Offline preflight

```bash
cd /opt/smart-fire-detection-v2
./venv/bin/python preflight.py --offline
```

WARN/SKIP ของ Site calibration เป็นไปได้บนเครื่องที่ยังไม่ commission

## Model

```bash
sha256sum /opt/smart-fire-detection-v2/models/fire.pt
```

## Manager port

```bash
ss -lntp | grep ':5050'
```

## Disk usage

```bash
df -h
du -xhd1 /opt /home/fire 2>/dev/null | sort -h
```

อย่า paste token/password/production.env ลง Issue สาธารณะ
