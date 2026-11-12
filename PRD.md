# PRD - Website Klinik

## 1. Scope

### 1.1 Tujuan
Website klinik untuk mengelola pendaftaran pasien, pemeriksaan dokter, dan pengambilan obat secara terintegrasi.

### 1.2 Pengguna
| Role | Deskripsi |
|------|-----------|
| Pasien | Mendaftar kunjungan, melihat jadwal dokter dan riwayat berobat |
| Dokter | Memeriksa pasien, mengisi diagnosis, membuat resep |
| Resepsionis | Mengelola pendaftaran, jadwal, dan antrean pasien |
| Apoteker | Memproses resep dan menyerahkan obat |

### 1.3 In Scope
**Pasien**
- Registrasi dan login
- Daftar kunjungan (pilih poli, dokter, jadwal)
- Lihat status antrean dan riwayat kunjungan

**Resepsionis**
- Konfirmasi atau ubah jadwal kunjungan
- Pendaftaran pasien walk-in
- Kelola antrean

**Dokter**
- Lihat daftar pasien hari ini
- Input hasil pemeriksaan dan diagnosis
- Buat resep obat

**Apoteker**
- Lihat resep masuk
- Update status resep (diproses, siap, diserahkan)
- Kelola stok obat dasar

### 1.4 Out of Scope
- Pembayaran online
- Integrasi BPJS/asuransi
- Telemedicine
- Aplikasi mobile native

### 1.5 Asumsi dan Batasan
- Satu klinik, satu cabang
- Pasien sudah punya akun sebelum daftar kunjungan
- (tambahkan sesuai kesepakatan tim)

---

## 2. Userflow

### 2.1 Alur Gabungan
```mermaid
flowchart TD
    A[Pasien daftar kunjungan] --> B[Resepsionis konfirmasi]
    B --> C[Pasien masuk antrean]
    C --> D[Dokter periksa dan input diagnosis]
    D --> E[Dokter buat resep]
    E --> F[Apoteker proses resep]
    F --> G[Pasien ambil obat]
```

### 2.2 Userflow Pasien
```mermaid
flowchart TD
    A[Buka website] --> B{Sudah punya akun?}
    B -- Belum --> C[Registrasi]
    B -- Sudah --> D[Login]
    C --> D
    D --> E[Pilih poli dan dokter]
    E --> F[Pilih jadwal]
    F --> G[Submit pendaftaran]
    G --> H[Lihat status antrean]
    H --> I[Lihat riwayat kunjungan]
```

### 2.3 Userflow Dokter
```mermaid
flowchart TD
    A[Login] --> B[Lihat daftar pasien hari ini]
    B --> C[Pilih pasien]
    C --> D[Input pemeriksaan dan diagnosis]
    D --> E[Buat resep]
    E --> F[Simpan dan selesai]
```

### 2.4 Userflow Resepsionis
```mermaid
flowchart TD
    A[Login] --> B[Lihat pendaftaran masuk]
    B --> C{Jadwal tersedia?}
    C -- Ya --> D[Konfirmasi pendaftaran]
    C -- Tidak --> E[Ubah jadwal atau tolak]
    D --> F[Pasien masuk antrean]
    E --> B
```

### 2.5 Userflow Apoteker
```mermaid
flowchart TD
    A[Login] --> B[Lihat resep masuk]
    B --> C[Siapkan obat]
    C --> D{Stok cukup?}
    D -- Ya --> E[Tandai siap diambil]
    D -- Tidak --> F[Hubungi dokter atau ganti obat]
    F --> C
    E --> G[Serahkan ke pasien]
```
