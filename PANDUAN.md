# E-Kasir Bang Zod — Panduan Instalasi
## A. Backend (Google Apps Script)
1. script.google.com → Proyek baru. Buat 4 berkas: `Kode.gs`, `Setup.gs`, `Notifikasi.gs`, `DocEngine.gs` (isi dari folder `backend/`). Di Project Settings centang "Show appsscript.json" lalu tempel isi `appsscript.json`.
2. Pilih fungsi `setupAppEnvironment` → ▶ Run **SEKALI** → izinkan akses. Ini membuat folder Drive, Spreadsheet (23 sheet inti), data contoh, 3 akun, template invoice, dan trigger.
3. Deploy → New deployment → Web app → Execute as **Me**, Access **Anyone** → salin URL `/exec`. Update berikutnya: Manage deployments → ✏️ → New version (URL tetap).
4. Akun awal (GANTI SEGERA di menu Pengaturan): `owner@bangzod.id / Owner#12345`, `kasir@bangzod.id / Kasir#12345`, `stok@bangzod.id / Stok#12345`.
## B. Backend tools
- Reset data contoh: jalankan `resetDataDummy()` di editor (atau menu Pengaturan → Reset, ketik RESET). Akun & template tidak tersentuh.
- Reset sandi Owner: Project Settings → Script Properties → tambah `RESET_PASSWORD_BARU` (min 8 karakter) → jalankan `resetPasswordSuperadmin()`. Properti otomatis dihapus & semua sesi lama dicabut.
## C. Frontend (GitHub Pages)
1. Edit `frontend/js/config.js`: isi `GAS_URL` dengan URL `/exec`.
2. Buat repo **Public** di github.com (tanpa README). Dari folder `frontend/` lewat terminal:
```
git init
git add .
git commit -m "Upload pertama"
git branch -M main
git remote add origin https://github.com/USERNAME/NAMA-REPO.git
git push -u origin main
```
(password = Personal Access Token). Settings → Pages → Deploy from branch `main` / root. Redeploy: `git add . && git commit -m "update" && git push`.
## D. Notifikasi & Dokumen
- WA: daftar fonnte.com, scan QR, salin token → menu **WA & CRM** → isi token → centang aktif → Simpan. Email memakai kuota Gmail.
- Invoice: buat Google Docs berisi placeholder `{{NOMOR}} {{PELANGGAN}} {{ITEM_LIST}} {{TOTAL|rupiah}}` dst → menu **Dokumen** → tempel URL → Pindai.
