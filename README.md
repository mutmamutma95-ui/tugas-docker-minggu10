# Tugas Minggu 11: CI untuk Repo Compose

[![CI](https://github.com/mutmamutma95-ui/tugas-docker-minggu10/actions/workflows/compose-check.yml/badge.svg)

**Nama:** Muudmainah

**NIM:** 202557201063

**Mata kuliah:** Teknologi Open Source

## Deskripsi

Repository ini digunakan untuk menguji konfigurasi
Docker Compose WordPress dan MySQL secara otomatis
menggunakan GitHub Actions.

## Isi Repository

- .github/workflows/compose-check.yml
- docker-compose.yml
- .env.example
- .gitignore

## Cara Kerja Workflow

Workflow berjalan ketika terjadi push ke branch main
atau ketika terdapat Pull Request.

Job validate berjalan pada ubuntu-latest dan
melakukan tiga langkah yaitu checkout repository,
menyalin .env.example menjadi .env, dan memvalidasi
file Docker Compose.

## Bukti

1. Run hijau di tab Actions

   ![Run hijau](bukti/1-run-hijau.png)

2. Pull Request dengan check gagal

   ![PR merah](bukti/2-pr-merah.png)

3. Badge status di README

   ![Badge](bukti/3-badge.png)

## Tautan Pull Request

[https://github.com/mutmamutma95-ui/tugas-docker-minggu10.git]

## Kendala dan Cara Mengatasinya

[- *Kesalahan sintaks pada docker-compose.yml:* Sempat terjadi kesalahan penulisan seperti sservices:, indentasi yang kurang tepat, dan format ${...} sehingga validasi gagal. Cara mengatasinya adalah memperbaiki struktur YAML di docker-compose.yml dan mengeceknya secara lokal dengan docker compose config -q sebelum di-push.
- *Run gagal tidak langsung muncul saat push ke branch uji-gagal:* Pada compose-check.yml, pemicu push hanya diatur untuk branch main (branches: [main]). Cara mengatasinya adalah membuka Pull Request dari uji-gagal ke main agar event pull_request berjalan dan menampilkan status gagal (Compose Check merah), lalu memperbaiki file di branch tersebut dan me-push ulang hingga statusnya kembali hijau.]

## Refleksi Singkat

CI membantu memeriksa konfigurasi Docker Compose
secara otomatis. Dengan adanya CI, kesalahan konfigurasi
dapat diketahui sebelum perubahan digabungkan.
