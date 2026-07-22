# 📊 SISMON MAGANG — Sistem Monitoring Magang PLN ICON+

![License](https://img.shields.io/badge/License-Proprietary-blue.svg)
![React](https://img.shields.io/badge/Frontend-React%20%7C%20TypeScript%20%7C%20Vite-61DAFB?logo=react)
![Node.js](https://img.shields.io/badge/Backend-Express.js%20%7C%20Node.js-339933?logo=node.js)
![MongoDB](https://img.shields.io/badge/Database-MongoDB%20Atlas-47A248?logo=mongodb)

**SISMON MAGANG** adalah aplikasi web *fullstack* terintegrasi yang dirancang khusus untuk memonitor, mengelola, dan mengevaluasi kegiatan peserta magang di **PLN ICON+**. Sistem ini mengubah proses pemantauan manual (seperti lembar kehadiran kertas dan rekap spreadsheet terpisah) menjadi ekosistem digital yang akurat, terpusat, dan berjalan secara *real-time*.

---

## 🚀 Fitur Utama

### 1. 🔒 Autentikasi & Hak Akses Multi-Role
- **Peserta Magang (User)**: Akses ke fitur absensi, pencatatan pekerjaan harian, melihat statistik performa diri, dan pengajuan kendala/keluhan.
- **Admin**: Akses untuk memantau kehadiran, rekapitulasi pekerjaan harian peserta, pembuatan QR Code absensi, serta pengelolaan laporan kendala.
- **Superadmin**: Seluruh hak akses Admin ditambah manajemen penilaian performa (evaluasi & ranking), kelola data admin/peserta, pengaturan target seksi, dan konfigurasi sistem.

### 2. 📲 Absensi Digital berbasis QR Code
- **Dynamic QR Code**: Admin dapat membuat QR Code absensi harian secara cepat.
- **Scanner Terintegrasi**: Peserta melakukan *scan* QR Code dari browser HP/Desktop dengan validasi lokasi dan timestamp otomatis.
- **Kalender Kehadiran**: Tampilan visual status kehadiran harian (Hadir, Izin, Sakit, Alpa, Terlambat) serta konfigurasi ambang batas keterlambatan.

### 3. 📝 Pencatatan & Monitoring Pekerjaan Harian
- Log aktivitas pekerjaan harian (deskripsi tugas, volume berkas/buku/bundle yang diselesaikan).
- Grafik distribusi kerja dan rekapitulasi volume pekerjaan per peserta.
- Pemantauan progres pekerjaan secara harian dan bulanan oleh Admin.

### 4. ⭐ Manajemen Penilaian Performa & Ranking
- Evaluasi kinerja berbasis **5 Kriteria Baku**:
  1. **Kedisiplinan**
  2. **Kualitas Kerja**
  3. **Inisiatif**
  4. **Kerjasama**
  5. **Komunikasi**
- Kalkulasi skor otomatis dan penentuan **Grade (A, B, C, D, E)**.
- Fitur **Leaderboard & Ranking** untuk perbandingan performa antar peserta secara obyektif.

### 5. 📈 Dashboard Analitik Real-Time
- Visualisasi data interaktif menggunakan **Chart.js**.
- Ringkasan statistik kehadiran, jam kerja efektif, distribusi pekerjaan, dan grafik progres mingguan.
- Dashboard terpisah yang disesuaikan untuk User dan Admin/Superadmin.

### 6. 📑 Ekspor Laporan ke Excel (.xlsx)
- Ekspor data laporan resmi siap cetak menggunakan **ExcelJS**.
- Mencakup: Rekapitulasi Absensi, Rekap Pekerjaan Harian, Penilaian Performa, dan Log Aktivitas Sistem.

### 7. 💬 Laporan Kendala & Keluhan
- Fitur pengajuan kendala/masalah fasilitas bagi peserta magang.
- Fitur tindak lanjut dan pembaruan status keluhan oleh pihak manajemen/admin.

---

## 🛠️ Teknologi yang Digunakan

### Frontend
- **Framework & Language**: React 18, TypeScript, Vite
- **Styling**: Tailwind CSS, Custom CSS Modular
- **Visualisasi & Animasi**: Chart.js, React-Chartjs-2, GSAP (GreenSock)
- **Utilities**: HTML5-QRCode (Scanner), QRCode (Generator), ExcelJS, File-Saver, React Router DOM v6

### Backend
- **Runtime & Framework**: Node.js, Express.js
- **Database & ODM**: MongoDB (Atlas/Local), Mongoose
- **Security & Auth**: JSON Web Token (JWT), Bcrypt.js, CORS, Selfsigned (HTTPS Local)
- **File Upload & Export**: Multer, ExcelJS, Morgan (Logging)

---

## 📂 Struktur Direktori Project

```text
sismon_magang/
├── backend/                        # Server Side API (Express.js & MongoDB)
│   ├── cert/                       # Sertifikat SSL untuk HTTPS lokal
│   ├── middleware/                 # Middleware autentikasi & upload file
│   ├── models/                     # Schema Mongoose (User, Attendance, WorkLog, dll)
│   ├── routes/                     # Router API Endpoints
│   ├── uploads/                    # Penyimpanan file static (foto profil, dll)
│   ├── seed.js                     # Script seeding data awal
│   ├── update-superadmin.js        # Script update role user ke Superadmin
│   ├── server.js                   # Entry point aplikasi backend
│   ├── package.json
│   └── vercel.json                 # Konfigurasi Serverless Deployment Vercel
│
├── frontend/                       # Client Side Web Application (React + Vite)
│   ├── public/                     # Static assets (logo, favicon, dll)
│   ├── src/
│   │   ├── components/             # Component UI reusabel (Navbar, Modal, Toast, dll)
│   │   ├── context/                # Context Provider (AuthContext, ThemeContext)
│   │   ├── hooks/                  # Custom React Hooks
│   │   ├── pages/                  # Halaman Aplikasi
│   │   │   ├── admin/              # Halaman Dashboard, Penilaian, Absensi, QR Code, dll
│   │   │   ├── user/               # Halaman Absensi, Input Kerja, Profil, Kendala, dll
│   │   │   └── auth/               # Halaman Login & Register
│   │   ├── services/               # Integrasi API Services
│   │   ├── styles/                 # File Styling & Tailwind Setup
│   │   └── types/                  # Definisi Tipe Data TypeScript
│   ├── package.json
│   ├── tailwind.config.js
│   ├── vite.config.ts
│   └── vercel.json
│
├── ATTENDANCE_CALENDAR_GUIDE.md    # Panduan penggunaan modul kalender absensi
├── BACKEND_REQUIREMENTS_MANAJEMEN_PENILAIAN.md # Dokumentasi kebutuhan API penilaian
├── PANDUAN_UPDATE_SUPERADMIN.md    # Panduan promosi role user ke superadmin
└── README.md                       # Dokumentasi utama aplikasi
```

---

## ⚙️ Panduan Instalasi & Jalankan Aplikasi

### Prerequisites
Sebelum memulai, pastikan telah menginstall:
- [Node.js](https://nodejs.org/) (Versi 18+ direkomendasikan)
- [MongoDB](https://www.mongodb.com/) (Lokal atau URI MongoDB Atlas)
- Git & npm / yarn

---

### 1. Setup Backend

1. Masuk ke direktori `backend`:
   ```bash
   cd backend
   ```

2. Install seluruh dependency:
   ```bash
   npm install
   ```

3. Buat file `.env` di dalam folder `backend` (dapat meniru `.env.example`):
   ```env
   PORT=5000
   MONGODB_URI=mongodb://localhost:27017/pln_magang_monitoring
   JWT_SECRET=pln-iconplus-magang-secret-key-2026
   JWT_EXPIRES_IN=7d
   ```

4. *(Opsional)* Jalankan seeding data awal (membuat admin & sampel data):
   ```bash
   npm run seed
   ```

5. Jalankan server dalam mode development:
   ```bash
   npm run dev
   ```
   Server Backend akan berjalan di `http://localhost:5000`.

---

### 2. Setup Frontend

1. Buka terminal baru dan masuk ke direktori `frontend`:
   ```bash
   cd frontend
   ```

2. Install seluruh dependency:
   ```bash
   npm install
   ```

3. Jalankan server development Vite:
   ```bash
   npm run dev
   ```

4. Buka alamat lokal yang tertera pada terminal (biasanya `http://localhost:5173`) pada browser Anda.

---

## 🔑 Pengaturan Role Superadmin

Untuk mempromosikan akun user biasa/admin menjadi **Superadmin** agar dapat mengakses menu **Manajemen Penilaian**, gunakan script CLI yang sudah disediakan:

```bash
cd backend
node update-superadmin.js email_user@domain.com
```

*(Untuk panduan selengkapnya mengenai pengelolaan role, silakan baca [PANDUAN_UPDATE_SUPERADMIN.md](file:///c:/Users/LENOVO/Documents/magang/fix-app/sismon_magang/PANDUAN_UPDATE_SUPERADMIN.md))*

---

## 🔌 Dokumentasi Endpoints API Utama

| Method | Endpoint | Deskripsi | Akses Role |
| :--- | :--- | :--- | :--- |
| `POST` | `/api/auth/login` | Login user & dapatkan JWT Token | Public |
| `POST` | `/api/auth/register` | Registrasi akun peserta magang baru | Public |
| `GET` | `/api/auth/me` | Mengambil data profil user terautentikasi | All Authenticated |
| `GET` | `/api/users` | Mengambil daftar seluruh user | Admin, Superadmin |
| `PATCH` | `/api/users/:id/role` | Mengubah role user | Superadmin |
| `POST` | `/api/attendance/scan` | Melakukan absensi via scan QR Code | User |
| `GET` | `/api/attendance/recap` | Mengambil rekapitulasi data absensi | Admin, Superadmin |
| `POST` | `/api/qrcode/generate` | Membuat QR Code absensi harian | Admin, Superadmin |
| `POST` | `/api/work-logs` | Menginput log pekerjaan harian | User |
| `GET` | `/api/work-logs` | Mengambil daftar log pekerjaan | All Authenticated |
| `POST` | `/api/performance/evaluate` | Menginput penilaian performa peserta | Superadmin |
| `GET` | `/api/performance/rankings` | Mengambil data rangking performa peserta | Admin, Superadmin |
| `POST` | `/api/complaints` | Mengirimkan laporan kendala/keluhan | User |
| `GET` | `/api/dashboard/stats` | Mengambil statistik agregat dashboard | All Authenticated |

---

## 📄 Lisensi & Hak Cipta

© 2026 **PLN ICON+**. Seluruh hak cipta dilindungi undang-undang. Aplikasi ini dikembangkan untuk kebutuhan operasional dan monitoring internal magang PLN ICON+.