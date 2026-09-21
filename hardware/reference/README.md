# Referensi Hardware

## vedderb-bldc-hardware (VESC 4.12)
Sumber: https://github.com/vedderb/bldc-hardware (clone, hanya referensi – jangan diedit langsung).

File desain: `vedderb-bldc-hardware/design/`
- `BLDC_4.pro`        – project (format legacy KiCad 4)
- `BLDC_4.sch` + sheet (`Power.sch`, `mosfets.sch`, `CAN.sch`, `STM32F4 64LQFP.sch`, ...)
- `BLDC_4.kicad_pcb`  – layout PCB
- `BLDC_4.pdf`        – skematik siap baca
- `Libraries/`        – footprint & symbol custom (dirujuk via `fp-lib-table`)
- `Gerber/`, `3D/`, `BLDC4.12_BOM.ods`

## Cara buka di KiCad 10
Project asli format KiCad 4 dan merujuk library sistem lama (`device`, `conn`, `power`, ...)
yang sudah tidak ada -> semua symbol tampil `??`. Sudah diperbaiki dengan menambahkan:
- `design/sym-lib-table`        – tabel library project
- `design/BLDC_4-cache.kicad_sym` – hasil konversi `BLDC_4-cache.lib` (berisi semua symbol yang dipakai)

Langkah:
1. `kicad vedderb-bldc-hardware/design/BLDC_4.pro`
2. Buka Schematic Editor. Kalau muncul dialog *Rescue Symbols* -> OK.
   Kalau masih ada `??`, jalankan Tools > Edit Symbol Library Links,
   lalu *Map Orphans* / pilih library `BLDC_4-cache` untuk semua.
3. File > Save (project dikonversi ke `.kicad_pro` / `.kicad_sch`).
4. PCB Editor: abaikan warning zone fill legacy, tekan `B` untuk refill zone.

Kalau mau dipakai sebagai basis desain sendiri, copy folder `design/` ke `../design/` lalu edit di sana.
