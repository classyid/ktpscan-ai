# KTPScan AI

![KTPScan AI](https://via.placeholder.com/850x400?text=KTPScan+AI)

KTPScan AI adalah sistem ekstraksi data dari Kartu Tanda Penduduk (KTP) Indonesia menggunakan Gemini AI dari Google. Sistem ini terdiri dari Google Apps Script backend, API RESTful, dan webhook WhatsApp untuk kemudahan akses.

## 🌟 Fitur Utama

- **Ekstraksi Data Otomatis**: Mengekstrak NIK, nama, alamat, dan informasi lainnya dari gambar KTP
- **API RESTful**: Menyediakan endpoint untuk integrasi dengan sistem lain
- **Integrasi WhatsApp**: Ekstrak data KTP langsung dari WhatsApp dengan mengirim gambar
- **Penyimpanan Data**: Menyimpan hasil ekstraksi ke Google Spreadsheet untuk analisis lebih lanjut
- **Logging Lengkap**: Mencatat semua aktivitas untuk audit dan pemecahan masalah
- **No-Code Solution**: Dibangun dengan Google Apps Script - tidak perlu server atau infrastruktur kompleks

## 🏗️ Arsitektur Sistem

Sistem ini terdiri dari tiga komponen utama:

1. **Google Apps Script Backend**
   - Menangani proses ekstraksi data dengan Gemini AI
   - Menyimpan data ke Google Spreadsheet
   - Menyediakan endpoint API

2. **API RESTful**
   - Menerima gambar dalam format base64
   - Mengembalikan data KTP dalam format JSON
   - Mendukung CORS untuk integrasi web

3. **Webhook WhatsApp**
   - Menerima pesan dan gambar dari WhatsApp
   - Mengirim gambar ke API untuk diproses
   - Mengirim hasil ekstraksi kembali ke pengirim

## 📋 Komponen Teknis

### Google Apps Script

Google Apps Script digunakan untuk mengintegrasikan Gemini AI, Google Drive, dan Google Sheets, membuat solusi tanpa perlu server (serverless).

```javascript
// Contoh implementasi utama
const PROMPT_TEMPLATE = `Fokus HANYA pada dokumen yang terlihat seperti Kartu Tanda Penduduk (KTP) Indonesia...`;

function processImage(fileData, fileName, mimeType) {
  // Implementasi ekstraksi data
}
```

### API RESTful

API yang dibangun dengan Google Apps Script Web App, menyediakan akses ke sistem ekstraksi data KTP.

```javascript
// Contoh endpoint API
function doPost(e) {
  // Implementasi endpoint POST
}
```

### Webhook WhatsApp

PHP script untuk menerima pesan WhatsApp, mengekstrak gambar, dan berkomunikasi dengan API.

```php
// Contoh implementasi webhook
function processKTP($image_data) {
  // Implementasi proses KTP
}
```

## 🚀 Cara Penggunaan

### Melalui API

```bash
curl -X POST https://script.google.com/macros/s/YOUR_DEPLOYMENT_ID/exec \
  -d "action=process-ktp" \
  -d "fileData=BASE64_ENCODED_IMAGE" \
  -d "fileName=ktp.jpg" \
  -d "mimeType=image/jpeg"
```

### Melalui WhatsApp

1. Simpan nomor WhatsApp bot Anda
2. Kirim gambar KTP dengan keterangan `.ktp`
3. Bot akan membalas dengan hasil ekstraksi data

## ⚙️ Instalasi dan Konfigurasi

### Google Apps Script Setup

1. Buat project baru di [Google Apps Script](https://script.google.com/)
2. Copy kode Google Apps Script dari `src/apps-script/main.js`
3. Deploy sebagai Web App, pilih "Anyone, even anonymous"
4. Salin URL deployment untuk digunakan di webhook WhatsApp

### WhatsApp Webhook Setup

1. Upload file webhook PHP ke web server Anda
2. Update URL API di konfigurasi
3. Konfigurasikan layanan WhatsApp API Anda (Mpedia) untuk menggunakan webhook

## 🔒 Keamanan dan Privasi

- Data KTP adalah data sensitif - **gunakan sistem ini dengan tanggung jawab**
- Pastikan penggunaan sesuai dengan peraturan perlindungan data di Indonesia
- Implementasikan enkripsi untuk penyimpanan data
- Jangan simpan data KTP lebih lama dari yang diperlukan

## 📜 Lisensi

Proyek ini dilisensikan di bawah MIT License - lihat file [LICENSE](LICENSE) untuk detail.

## 👥 Kontribusi

Kontribusi selalu disambut! Silakan buka issue atau pull request jika Anda ingin berkontribusi pada proyek ini.
