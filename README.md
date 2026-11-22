# RZK Piso WiFi OpenWrt firmware

Choose the folder for the exact device model and hardware revision. Each channel folder contains a firmware image and its SHA-256 checksum.

| Device | Hardware revision | Downloads |
| --- | --- | --- |
| [Ruijie RG-EW1200G Pro](ruijie_rg-ew1200g-pro-v1.1/) | v1.1 | [Stable](ruijie_rg-ew1200g-pro-v1.1/stable/) · [Beta](ruijie_rg-ew1200g-pro-v1.1/beta/) · [Dev](ruijie_rg-ew1200g-pro-v1.1/dev/) |

## Channels

- **Stable** — built from the Portal `stable` branch; recommended for normal use.
- **Beta** — built from the Portal `beta` branch; for testing upcoming changes.
- **Dev** — built from the Portal `main` branch; for development and testing.

## Verify and flash a sysupgrade image

These images are for upgrading a router already running compatible OpenWrt. Do not flash them through the stock firmware's upgrade page. Check the model and hardware revision, back up your configuration, and use a wired connection and reliable power.

1. Download the `*-sysupgrade.bin` and `sha256sums` from the **same** channel folder. Place them together, keep the original filename, and run:

   ```sh
   sha256sum -c sha256sums
   ```

   Continue only if the image reports `OK`.
2. In OpenWrt LuCI, go to **System → Backup / Flash Firmware** and select the verified image under **Flash new firmware image**. If you use SSH instead, copy the verified image to `/tmp` on the router, then run `sysupgrade -T /tmp/<downloaded-filename>` to test it before running `sysupgrade /tmp/<downloaded-filename>`.
3. Stop if the compatibility check fails; do not force the upgrade. Once flashing starts, do not disconnect power. Wait for the router to reboot before reconnecting.
