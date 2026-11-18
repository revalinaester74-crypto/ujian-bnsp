# Backend Data Siswa

REST API sederhana untuk membaca dan mengelola data siswa. Aplikasi menggunakan
Node.js, Express, dan MySQL.

## Persyaratan

- Node.js dan npm
- MySQL
- Database yang nama dan aksesnya sesuai dengan konfigurasi di `.env`
- Tabel `siswa` dengan kolom `kode_siswa`, `nama_siswa`, `alamat_siswa`,
  `tgl_siswa`, dan `jurusan_siswa`

## Instalasi

Buka PowerShell di folder proyek, lalu jalankan:

```powershell
cd .\backend
npm install
```

## Konfigurasi

Buat atau sesuaikan file `.env` di folder `backend`:

```env
PORT=5000
DB_HOST=localhost
DB_USER=nama_user_mysql
DB_PASSWORD=password_mysql
DB_NAME=nama_database
DB_PORT=3306
```

Ganti nilai contoh dengan konfigurasi MySQL lokal Anda. Jangan membagikan atau
mengunggah `.env` yang berisi kredensial.

Pastikan MySQL aktif, database sudah dibuat, dan tabel `siswa` memiliki kolom
yang disebutkan di atas sebelum menjalankan API.

## Menjalankan server

Mode pengembangan (otomatis mulai ulang saat file berubah):

```powershell
npm run dev
```

Mode biasa:

```powershell
npm start
```

Secara default server berjalan di `http://localhost:5000`. Buka alamat tersebut
untuk memeriksa server. Jika port 5000 sedang digunakan, hentikan server lain
yang memakainya atau ubah `PORT` di `.env` (misalnya menjadi `5001`), lalu
jalankan ulang aplikasi.

## Endpoint

Semua endpoint menerima dan mengirim JSON, kecuali `GET /` yang mengirim teks.

| Method | Path | Keterangan |
| --- | --- | --- |
| `GET` | `/` | Memeriksa apakah server berjalan |
| `GET` | `/api/siswa` | Mengambil semua data siswa |
| `POST` | `/api/siswa` | Menambahkan data siswa |
| `PUT` | `/api/siswa/:kode` | Mengubah data siswa berdasarkan kode |
| `DELETE` | `/api/siswa/:kode` | Menghapus data siswa berdasarkan kode |

Contoh body untuk `POST /api/siswa`:

```json
{
  "kode_siswa": "S001",
  "nama_siswa": "Nama Siswa",
  "alamat_siswa": "Alamat Siswa",
  "tgl_siswa": "2005-01-31",
  "jurusan_siswa": "Rekayasa Perangkat Lunak"
}
```

Untuk `PUT /api/siswa/:kode`, kirim `nama_siswa`, `alamat_siswa`, `tgl_siswa`,
dan `jurusan_siswa` dalam body JSON. Contoh: `PUT /api/siswa/S001`.

## Catatan

- Pastikan hanya ada satu proses server yang menggunakan port yang sama.
- API memerlukan koneksi MySQL yang berhasil sebelum server mulai menerima
  permintaan.
