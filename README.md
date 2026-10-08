# englishku

Aplikasi web belajar bahasa Inggris harian, dari nol sampai bisa percakapan (A1–B1).
Tiap hari 1 paket latihan ±10 menit dengan 5 langkah: sambung garis kata–gambar,
hafal kosakata, kuis dengar & pilih, tirukan dengan rekam suara + cek ucapan AI,
dan susun kalimat.

Bisa di-install di HP (PWA). Data tersimpan lokal di browser masing-masing.

## Fitur

- 🔗 **Sambung garis** — ketuk kata lalu ketuk gambar yang cocok (pemanasan)
- 🖼️ **Lihat & dengar** — hafal kosakata baru dengan gambar + audio
- 🔊 **Dengar & pilih** — kuis pendengaran
- 🎙️ **Tirukan** — rekam suara sendiri, bandingkan dengan contoh
- 🗣️ **Cek ucapan AI** — ucapan diubah jadi teks Inggris lalu dinilai per kata (butuh Chrome + internet)
- 🧩 **Susun kalimat** — latihan struktur kalimat (level A2 ke atas)
- 🔁 **Paket Ulasan** — kata yang pernah salah muncul lagi otomatis (pengulangan berjeda)
- 🧒🧑 **Mode Anak / Dewasa** — tampilan dan kalimat menyesuaikan usia
- 🔥 **Streak harian** — progres tersimpan di HP

## Kurikulum

Berdasar standar CEFR dan riset pembelajaran bahasa (comprehensible input i+1,
spaced repetition, retrieval practice):

| Stage | Isi | Target |
|---|---|---|
| A1 Dasar | ±90 kata benda inti | kenal & ucapkan |
| A2 Sehari-hari | ±60 frasa harian | ngobrol simpel |
| B1 Percakapan | ±60 situasi nyata | percaya diri ngobrol |

Semua kalimat memakai kaidah i+1: hanya memakai kata yang sudah diajarkan di
paket itu atau sebelumnya.

## Menjalankan

File statis biasa, tidak perlu build:

```bash
cd englishku
python -m http.server 8000
# buka http://localhost:8000 di browser
```

Untuk akses dari HP lain: gunakan `ngrok http 8000`, atau upload ke hosting
(cPanel) — sudah termasuk `manifest.json` + `sw.js` agar bisa di-install
sebagai PWA (butuh HTTPS).

## Struktur

| File | Fungsi |
|---|---|
| `index.html` | Seluruh aplikasi (satu file) |
| `manifest.json` | Konfigurasi PWA |
| `sw.js` | Service worker (offline + update) |
| `version.json` | Nomor versi untuk cek update otomatis |
| `icon-192.png.b64` / `icon-512.png.b64` / `icon-180.png.b64` | Ikon dalam format base64 |

### Mengembalikan ikon

File biner tidak bisa di-upload via API, jadi ikon disimpan sebagai base64.
Untuk mendapatkan kembali file PNG-nya:

```bash
base64 -d icon-192.png.b64 > icon-192.png
base64 -d icon-512.png.b64 > icon-512.png
base64 -d icon-180.png.b64 > icon-180.png
```

## Lisensi

MIT — bebas dipakai, diubah, dan disebarkan.
