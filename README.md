# 🏗️ ARM — Alvend Readymix Management System

**ARM (Alvend Readymix Management)** adalah aplikasi web *single-file* berbasis HTML + JavaScript untuk mengelola operasional penjualan dan pengiriman beton ready-mix. Aplikasi mencakup manajemen order, tracking pengiriman truk secara real-time, invoice, hardcopy request, laporan After Delivery Report (ADR), hingga master data (plant, mutu beton, wilayah, sales, dan customer).

> **Versi:** `v2.31.1-PRO-EXCEL`  
> **Tipe:** Single-file Web App (HTML + CSS + JS)  
> **Storage:** Browser LocalStorage + BroadcastChannel (realtime sync antar tab)  
> **Bahasa:** Indonesia

---

## 📋 Daftar Isi

1. [Fitur Utama](#-fitur-utama)
2. [Role & Hak Akses](#-role--hak-akses)
3. [Akun Demo](#-akun-demo)
4. [Cara Menjalankan](#-cara-menjalankan)
5. [Struktur Menu](#-struktur-menu)
6. [Alur Bisnis Utama](#-alur-bisnis-utama)
7. [Master Data](#-master-data)
8. [After Delivery Report (ADR)](#-after-delivery-report-adr)
9. [Upload Wilayah via Excel/CSV](#-upload-wilayah-via-excelcsv)
10. [Realtime & Sinkronisasi Data](#-realtime--sinkronisasi-data)
11. [Teknologi](#-teknologi)
12. [Struktur Data (DB Object)](#-struktur-data-db-object)
13. [Shortcut & Tips](#-shortcut--tips)
14. [Batasan & Catatan](#-batasan--catatan)
15. [Lisensi](#-lisensi)

---

## ✨ Fitur Utama

| Modul | Deskripsi |
|---|---|
| 🔐 **Autentikasi** | Login multi-role (Owner, Admin, Sales, Customer) |
| 📊 **Dashboard** | Ringkasan order, volume terkirim, QC, dan progres per periode (bulan/tahun) |
| ➕ **Input Order** | Form order lengkap: customer, sales, proyek, wilayah (Kota → Kecamatan → Kelurahan), plant, mutu beton, metode cor, QC toggle |
| 📦 **ARM Order** | Daftar order dengan filter multi-plant, truck list, qty list, delivered, remain |
| 🚛 **Tracking Pengiriman** | Update status truk (Batching → Loading → Berangkat → Sampai → Penuangan → Selesai), termasuk **Reject** dengan alasan |
| 📈 **After Delivery Report** | Laporan pengiriman detail per truk, siap diekspor ke Excel/CSV |
| 🧾 **Invoice** | Preview, share ke customer, notifikasi otomatis |
| 📩 **Hardcopy Request** | Customer bisa request hardcopy invoice, owner memproses pengiriman |
| 🏭 **Master Data** | Kelola Plant, Mutu Beton, Wilayah (Kecamatan & Kelurahan), Sales, Customer |
| 🔔 **Notifikasi** | Real-time notifikasi ke customer saat ada update order/pengiriman/invoice |
| 📤 **Upload Wilayah** | Import data Kecamatan & Kelurahan dari file Excel/CSV/TXT |
| 🔄 **Realtime Sync** | Data tersinkron antar tab browser via `BroadcastChannel` + `localStorage` |

---

## 👥 Role & Hak Akses

### 1. **Owner**
- Akses penuh ke semua menu
- Kelola master data (Plant, Mutu, Wilayah, Sales, Customer)
- Kelola & share invoice
- Proses hardcopy request
- Update status order & pengiriman

### 2. **Admin**
- Dashboard
- Input Order
- ARM Order
- After Delivery Report
- Update status order & pengiriman

### 3. **Sales**
- Sama seperti Admin
- Fokus pada order yang dibuat

### 4. **Customer**
- Dashboard pribadi
- Order Saya (hanya order miliknya)
- Invoice Saya (yang sudah di-share)
- Notifikasi
- Request hardcopy invoice

---

## 🔑 Akun Demo

| Role | Email | Password |
|---|---|---|
| Owner | `owner@alvend.com` | `owner123` |
| Admin | `admin@alvend.com` | `admin123` |
| Sales | `sales@alvend.com` | `sales123` |
| Customer | `customer@alvend.com` | `customer123` |

> ⚠️ Akun demo ini hanya untuk development/testing. Ganti dengan autentikasi backend untuk produksi.

---

## 🚀 Cara Menjalankan

1. **Simpan file** `index.html` (atau `arm.html`) di komputer/server.
2. **Buka file** langsung di browser (Chrome/Edge/Firefox):
   - Klik dua kali file, atau
   - Drag & drop ke browser, atau
   - Akses via URL jika di-host di web server (Apache/Nginx).
3. **Login** menggunakan salah satu akun demo di atas.
4. Data akan otomatis tersimpan di **LocalStorage** browser.

> 💡 Untuk fitur upload Excel, browser **harus terkoneksi internet** saat pertama kali membuka aplikasi (untuk memuat library SheetJS dari CDN).

---

## 🧭 Struktur Menu

### Owner
