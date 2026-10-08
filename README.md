# ◆ DIAMOND RADIO — Custom ATS-25 Firmware

Custom firmware for the **ATS-25** receiver (ESP32 + Si4735 + 2.8" ILI9341 touch screen).
Also community-confirmed on the **ATS-120 Pro** (ILI9341) and the **ATS25 Pro+ AIR**
(ST7789 — dedicated build, available in the website installer's hardware list).
An independent freeware project.

> **Status: v1.0.1 — PUBLIC BETA** — released for testing. The first stable version
> follows when all planned features are complete.
>
> **This repository hosts the first public beta only.** Newer versions are NOT
> uploaded here — always get the latest firmware from the official website:
> **https://diamondradio.web.app**

**GitHub:** https://github.com/khanfar/DiamondRadio
**Website & web installer:** https://diamondradio.web.app

---

## Features

- **Digital decoders on the radio** — FT8 / FT4, CW (Morse), RTTY, SSTV (17 modes,
  auto-detect, thumbnails) — no PC needed
- **FTx world map** — decoded stations plotted with distance/bearing, gray-line
  day/night, zoom & pan, QTH locator support
- **EiBi shortwave database** — 9,000+ stations with names and schedules,
  ONAIR filter, updatable over USB
- **Propagation page** — live solar data (SFI/A/K) with per-band day/night conditions
- **Memories** — 100 per band, name/edit/move/organize
- **Bands** — FM (EU/US/JP ranges), LW, MW, all SW broadcast bands, ham 160 m–10 m,
  CB, AIR; IARU Region 1/2/3 band plans
- **WiFi** — saved networks, NTP clock (UTC/LOC), time-zone world map, FIND ME
  automatic locator
- **Themes** — three GUI color themes, switchable in Settings
- **Calibration** — per-band frequency (ppm), touch screen, knob direction/sensitivity
- **SDR integration** — companion web monitor: radio telemetry + HackRF/RTL-SDR
  spectrum that follows the radio
- **PC logging** — decoded digital messages over USB serial

## Download & Install

### Easiest way — web installer (recommended)

Open the [DIAMOND RADIO web installer](https://diamondradio.web.app/install.html) in **Chrome or Edge**, connect the radio via USB,
and click **◆ INSTALL DIAMOND RADIO**. It automatically backs up your current firmware
to your PC first, then installs and boots the new firmware.

### Manual way — download the .bin from GitHub

The files here are the **v1.0.1 public beta snapshot** — for any newer version,
use the [official website](https://diamondradio.web.app) instead.
Download a firmware file from this repository's
[Releases](https://github.com/khanfar/DiamondRadio/releases) page (or the files below),
then on the web installer use **5 · Advanced → Install a custom .bin**:

| File | Flash address | When to use |
|---|---|---|
| `diamond-radio-full.bin` (4 MB) | **0x0** | First install — works from **any** current firmware (stock or other custom firmware). Contains bootloader + partition table + app. |
| `diamond-radio-app.bin` (~2.2 MB) | **0x10000** | Quick update — only if the radio **already runs DIAMOND RADIO** (custom partition table already in place). |

> ⚠ Never flash the app-only file at 0x10000 over a stock or other custom firmware installation —
> the partition tables differ. For the first install always use the **full** image at **0x0**.

### Requirements

- Chrome or Edge browser (Web Serial API)
- USB **data** cable (charge-only cables won't work)
- CH340/CH341 USB-serial driver: https://www.wch-ic.com/downloads/CH341SER_EXE.html

### Safety

- Always let the installer make the backup (or use **Backup only**) before flashing.
- The ESP32 bootloader lives in ROM — a failed flash cannot permanently brick the radio;
  just connect and flash again.
- To go back: flash your backup `.bin` at address **0x0**.

### EiBi database

After installing, use the **EiBi database update** section on the web installer to send
the shortwave schedule to the radio. Update about twice a year (late March / late October).

## Community

- Telegram: https://t.me/+aftBqV_qRMlkZDVi
- Facebook: https://www.facebook.com/share/g/1EpCchUdzj/
- YouTube: https://www.youtube.com/@DiamondRadioOfficial

## License

DIAMOND RADIO is **freeware** — free to download, install, and share as an
unmodified binary. The source code is private and not published. See
[LICENSE](LICENSE) for the full terms.

Third-party components and credits are listed in [NOTICE.txt](NOTICE.txt)
(ft8_lib — MIT, PU2CLR SI4735 — MIT, TFT_eSPI, DSEG7 font — OFL, NASA Blue Marble imagery).

## Compliance

- [sbom.spdx.json](sbom.spdx.json) — Software Bill of Materials (SPDX 2.3):
  every third-party component in the build, with its license. No GPL/copyleft
  components are included.
- [NOTICE.txt](NOTICE.txt) — full third-party copyright and license texts.
