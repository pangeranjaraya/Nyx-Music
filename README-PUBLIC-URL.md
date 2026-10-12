# NyxMusic — Paket 1: Hosting URL Publik (GitHub + Vercel)

Paket ini khusus untuk menerbitkan frontend web dan API NyxMusic. Paket Android Studio akan disiapkan terpisah setelah URL publik sudah didapatkan.

## Isi paket
- `public/` — frontend website NyxMusic
- `api/` — fungsi API Vercel (search, lyrics, artist, album, ytplay, dan endpoint terkait)
- `package.json` — dependensi runtime
- `vercel.json` — konfigurasi routing/deployment
- `README.md` — dokumentasi asli proyek

## Mendapatkan URL publik
Saya tidak bisa menerbitkan URL atas nama Anda tanpa akses akun GitHub/Vercel. Ikuti langkah berikut:

1. Ekstrak ZIP ini.
2. Buat repository baru di https://github.com/new (misalnya `nyxmusic-api`).
3. Unggah **isi folder hasil ekstrak** ke root repository, bukan folder ZIP-nya. Pastikan `api/`, `public/`, `package.json`, dan `vercel.json` terlihat di root.
4. Buka https://vercel.com/new lalu login dengan GitHub.
5. Import repository `nyxmusic-api`, lalu pilih Deploy. Untuk proyek ini, jangan set Root Directory ke `api` atau `public`; gunakan root repository.
6. Setelah deployment selesai, Vercel akan menampilkan domain HTTPS seperti `https://nama-proyek.vercel.app`. Itulah domain publik/API Base URL.
7. Uji frontend dengan membuka domain tersebut.
8. Uji API search dengan membuka:
   `https://NAMA-DOMAIN-ANDA.vercel.app/api/search?query=adele&type=songs`
   Ganti `NAMA-DOMAIN-ANDA` dengan domain yang diberikan Vercel. Respons JSON berarti endpoint sudah merespons; `status: true` dengan hasil lagu menunjukkan pencarian berhasil pada saat pengujian.

## Konfigurasi URL untuk aplikasi Android (nanti)
Masukkan domain saja sebagai API Base URL, misalnya:
`https://nama-proyek.vercel.app`
Jangan tambahkan `/api` di ujungnya.

## Penting
- ZIP ini belum berisi proyek Android Studio; itu sengaja dipisahkan sesuai urutan kerja.
- Saya tidak dapat membuat domain Vercel yang benar-benar publik hanya dari ZIP. Domain baru tersedia setelah Anda menghubungkan repository ke akun Vercel dan deployment berhasil.
- Deployment berhasil tidak menjamin semua sumber audio pihak ketiga selalu tersedia. Endpoint `/api/ytplay` bergantung pada layanan eksternal dan dapat berubah/rate-limit.
- Jika deployment gagal, buka Vercel → Project → Deployments → pilih deployment → Build Logs, lalu kirimkan error-nya untuk diperbaiki.
- Jangan unggah token, password, atau secret ke repository publik.
