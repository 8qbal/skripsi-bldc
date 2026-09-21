# Referensi Software / Firmware

## skadimoe9-Skripsi-BLDC-Motor-Control
Sumber: https://github.com/skadimoe9/Skripsi-BLDC-Motor-Control (clone, hanya referensi – jangan diedit langsung).
Firmware FOC untuk board VESC 4.12 (STM32F405RGT6), dibuat dengan STM32CubeMX/CubeIDE.

- `Core/Inc`, `Core/Src` – source utama (sama persis dengan yang di dalam .rar):
  - `foc_control.c/h`, `foc_math.c/h` – algoritma FOC (Clarke/Park, SVPWM)
  - `adc_sense.c/h`   – pembacaan arus/tegangan
  - `hall_sensor.c/h` – posisi rotor via hall sensor
  - `open_loop.c/h`   – mode open loop
  - `vesc_can.c/h`, `vesc_uart.c/h`, `can_log.c/h` – komunikasi
  - `hw_conf.h`       – mapping pin ke hardware VESC
- `SkripsiCek.ioc`   – konfigurasi CubeMX (MCU STM32F405RGTx, CubeMX 6.15.0, FW_F4 V1.28.3)
- `SkripsiCek.rar`   – arsip project CubeIDE lengkap (asli dari repo)
- `SkripsiCek-full/` – hasil ekstrak .rar (tanpa folder `Debug/` hasil build):
  ada `Drivers/` (HAL + CMSIS), `.project`, `.cproject`, `.mxproject`

## Cara buka di STM32CubeIDE
File > Import > Existing Projects into Workspace > pilih folder `SkripsiCek-full/`.
Kalau CubeMX minta firmware package, pakai **STM32Cube FW_F4 V1.28.3** (atau biarkan
CubeMX migrasi ke versi terbaru, lalu regenerate code – `Core/Src` user code aman
karena ada di blok `USER CODE BEGIN/END`).
