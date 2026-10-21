
<div align="center">

<svg width="80" height="80" viewBox="0 0 24 24" fill="none" stroke="#000000" stroke-width="2.5" stroke-linecap="square" stroke-linejoin="miter">
  <path d="M5 5h14L5 19h14" />
</svg>

# ZUNERATOR

**Alight Motion Premium Activation Gateway**

[![Version](https://img.shields.io/badge/version-2.4_PRO-black?style=for-the-badge)](#)
[![Status](https://img.shields.io/badge/status-online-10b981?style=for-the-badge)](#)
[![Design](https://img.shields.io/badge/design-brutalist--modern-e11d48?style=for-the-badge)](#)
[![Backend](https://img.shields.io/badge/backend-node.js-0f172a?style=for-the-badge)](#)
[![License](https://img.shields.io/badge/license-proprietary-0f172a?style=for-the-badge)](#)

<p align="center">
  <i>"Dari email. Jadi Premium."</i><br />
  Platform aktivasi lisensi Alight Motion Premium yang dirancang untuk kecepatan, kejelasan, keamanan, dan didukung asisten AI.
</p>

---

</div>

## Ringkasan Proyek

**ZUNERATOR** adalah aplikasi berbasis web yang berfokus pada penyederhanaan proses aktivasi lisensi Alight Motion Premium. Aplikasi ini menghadirkan pendekatan antarmuka **Brutalist-Modern**, yaitu kombinasi antara minimalisme fungsional dan estetika *developer console* yang khas.

Alih-alih menyajikan formulir panjang yang membingungkan, ZUNERATOR menggunakan alur **Wizard 4 Langkah** yang memandu pengguna secara linear dari awal hingga akhir. Setiap langkah dirancang agar hanya menampilkan informasi yang relevan, sehingga pengguna tidak pernah merasa tersesat.

Lebih dari sekadar formulir aktivasi, ZUNERATOR juga dilengkapi dengan **AIHELP Assistant**, asisten virtual cerdas yang siap menjawab pertanyaan, memandu penggunaan, dan memberikan solusi atas kendala pengguna kapan saja tanpa perlu menunggu tim dukungan manusia.

---

## Filosofi Desain

Setiap elemen visual pada ZUNERATOR dipilih dengan alasan yang jelas. Tidak ada ornamen berlebihan, tidak ada gradien yang mengganggu fokus, dan tidak ada animasi yang memperlambat interaksi.

Pendekatan ini menghasilkan antarmuka yang:

- **Fokus pada Tugas** — Setiap piksel melayani tujuan fungsional.
- **Mudah Dibaca** — Kontras tinggi antara teks dan latar memastikan keterbacaan.
- **Terasa Teknis namun Ramah** — Nuansa *console* membangun kepercayaan tanpa terasa mengintimidasi.
- **Konsisten** — Setiap halaman dan komponen mengikuti *design language* yang sama.

### Design Tokens

| Token | Nilai | Visual |
| :--- | :--- | :--- |
| Background | `#fcfcfc` | Light Off-White |
| Text Primary | `#0f172a` | Slate 900 |
| Accent | `#e11d48` | Rose 600 |
| Typography Sans | Inter | Clean & Legible |
| Typography Mono | JetBrains Mono | Technical & Precise |
| Border Radius | `md` / `xl` | Sharp & Structured |
| Signature Effect | Dot Pattern & ASCII Art | Brutalist / Retro |

---

## Fitur Utama

### 1. Wizard Aktivasi 4 Langkah
Alur linear yang membimbing pengguna dari awal hingga akhir:
1. **Kirim Link** — Pengguna memasukkan alamat email target.
2. **Cek Email** — Instruksi jelas untuk membuka kotak masuk dan menyalin tautan.
3. **Verifikasi** — Menempelkan tautan untuk mengaktifkan lisensi.
4. **Struk** — Menampilkan bukti aktivasi digital yang bisa disimpan.

Setiap langkah hanya menampilkan elemen yang relevan, dengan indikator progres visual yang bergerak seiring pengguna menyelesaikan setiap tahapan.

### 2. AIHELP Assistant
Asisten virtual berbasis AI yang dapat diakses kapan saja melalui tombol mengambang di sudut kanan bawah. AIHELP dirancang untuk:
- Menjawab pertanyaan umum seputar proses aktivasi.
- Memberikan panduan langkah demi langkah jika pengguna bingung.
- Menjelaskan istilah teknis dengan bahasa yang mudah dipahami.
- Mengarahkan pengguna ke kontak dukungan manusia jika diperlukan.

### 3. Terminal Log
Panel visual yang menampilkan status sistem secara langsung. Pengguna dapat melihat setiap respons sistem dalam format *monospace*, meniru pengalaman menggunakan *command line*.

### 4. Struk Digital
Setelah aktivasi berhasil, pengguna menerima struk digital yang berisi rincian akun, status lisensi, dan masa aktif. Struk ini dapat dijadikan bukti sah aktivasi.

### 5. Fully Responsive
Tata letak dioptimalkan untuk berbagai ukuran layar, mulai dari ponsel hingga monitor desktop.

---

## Arsitektur Keamanan (Backend Proxy)

Untuk mencegah pencurian API Key dan penyalahgunaan sistem, ZUNERATOR menggunakan arsitektur **Backend Proxy**. Seluruh logika komunikasi dengan layanan pihak ketiga disembunyikan di sisi server, tidak di-*expose* ke browser pengguna.

### Alur Komunikasi

```text
[Browser Pengguna] 
       ↓ (Request tanpa API Key)
[Zunerator Frontend] 
       ↓ (Fetch ke endpoint lokal)
[Backend Proxy (Node.js/Vercel)] 
       ↓ (Menyisipkan API Key secara rahasia)
[API Gateway Provider]
```

Dengan pendekatan ini:
- API Key tidak pernah dikirim ke browser.
- Tidak ada kebocoran kredensial melalui *Inspect Element*.
- Konfigurasi sistem dapat diubah tanpa mengubah kode frontend.

---

## Panduan Instalasi & Deployment

### 1. Persiapan Frontend
Unduh file `index.html` (aplikasi utama) dan pastikan tampilan UI berjalan dengan baik.

### 2. Setup Backend Proxy (Node.js)
Karena frontend membutuhkan perantara untuk mengamankan API Key, kita menggunakan Node.js yang di-*deploy* ke Vercel.

Buat folder baru untuk backend, lalu siapkan tiga file berikut:

**`package.json`**
```json
{
  "name": "app",
  "version": "1.0.0",
  "main": "index.js",
  "dependencies": {
    "axios": "^1.6.0",
    "cors": "^2.8.5",
    "express": "^4.18.2"
  }
}
```

**`vercel.json`**
```json
{
  "version": 2,
  "builds": [
    {
      "src": "index.js",
      "use": "@vercel/node"
    }
  ],
  "routes": [
    {
      "src": "/(.*)",
      "dest": "index.js"
    }
  ]
}
```

**`index.js`**
*(Di sinilah seluruh logika API diletakkan. Kredensial disamarkan dan dipecah menjadi beberapa bagian untuk mencegah pembacaan langsung. Kode lengkapnya ada pada file `index.js` di repositori ini).*

### 3. Deploy ke Vercel
1. Upload ketiga file backend ke repositori GitHub.
2. Hubungkan repositori tersebut ke Vercel.
3. Klik **Deploy**. Vercel akan memberikan Anda URL publik (contoh: `https://zunerator-backend.vercel.app`).

### 4. Menghubungkan Frontend ke Backend
Di file frontend (`index.html`), ubah konfigurasi URL API agar mengarah ke URL Vercel backend Anda:

```javascript
const API_BASE = "https://zunerator-backend.vercel.app/api";
```

Setelah ini, seluruh proses aktivasi akan berjalan melalui proxy yang aman, dan API Key Anda tidak akan pernah ter-*expose* ke publik.

---

## Cara Menggunakan AIHELP Assistant

AIHELP Assistant adalah fitur inti pada ZUNERATOR yang dirancang untuk membantu pengguna kapan saja.

### Mengakses AIHELP
1. Buka halaman ZUNERATOR di *browser* Anda.
2. Perhatikan tombol bulat berwarna gelap di sudut kanan bawah halaman.
3. Klik tombol tersebut untuk membuka jendela obrolan AIHELP.

### Bertanya kepada AIHELP
Setelah jendela obrolan terbuka, Anda dapat langsung mengetik pertanyaan pada kolom input di bagian bawah. Contoh pertanyaan yang bisa diajukan:
- "Bagaimana cara verifikasi link?"
- "Mengapa saya tidak menerima email?"
- "Apa itu magic link?"
- "Berapa lama proses aktivasinya?"

AIHELP akan merespons dalam hitungan detik dengan jawaban yang jelas dan terstruktur.

### Batasan AIHELP
AIHELP memiliki batasan yang jelas untuk menjaga keamanan dan akurasi. AIHELP tidak akan:
- Membagikan informasi sensitif atau kredensial sistem.
- Melakukan tindakan atas nama pengguna tanpa persetujuan.
- Mengklaim keberhasilan aktivasi yang tidak terverifikasi.
- Memberikan jawaban spekulatif atas hal yang tidak dapat diverifikasi.

Jika AIHELP tidak dapat membantu, pengguna akan diarahkan secara otomatis ke kanal kontak resmi.

---

## Panduan Visual Antarmuka

| Area | Deskripsi |
| :--- | :--- |
| Header | Navigasi ringkas dengan logo dan tombol aksi utama. |
| Hero | Judul besar dengan aksen *dot-matrix* dan deskripsi singkat. |
| Wizard Panel | Kartu utama berisi form 4 langkah dengan indikator progres. |
| Terminal Log | Panel gelap dengan teks monospace untuk melihat status sistem. |
| Statistik Ringkas | Empat kartu kecil berisi metrik sistem yang logis. |
| Marquee | Teks berjalan berisi nama endpoint yang tersedia. |
| AI Assistant | Tombol mengambang dengan modal obrolan interaktif. |
| Footer | Informasi hak cipta dan identitas pengembang. |

---

## Prinsip Keamanan

ZUNERATOR dirancang dengan prinsip-prinsip berikut:

- **Minimalisasi Data** — Aplikasi tidak meminta informasi pribadi yang tidak diperlukan.
- **Transparansi Proses** — Setiap langkah ditampilkan secara jelas kepada pengguna.
- **Validasi Berlapis** — Setiap input diperiksa sebelum diproses lebih lanjut.
- **Pembatasan AI** — AIHELP tidak diizinkan membagikan informasi sensitif atau melakukan tindakan yang tidak sah.
- **Penyembunyian Kredensial** — Seluruh API Key dan konfigurasi sistem berada di sisi server, tidak di frontend.

---

## Struktur Repositori

```text
zunerator/
├── public/
│   └── index.html       # Aplikasi utama (Frontend)
├── index.js             # Logika Backend Proxy (API)
├── package.json         # Dependensi backend
├── vercel.json          # Konfigurasi routing
└── README.md            # Dokumentasi proyek
```

---

## Kontak dan Dukungan

Proyek ini dikembangkan dan dikelola oleh **zukechi**. Untuk pertanyaan, masukan, atau kendala teknis di luar cakupan AIHELP, silakan hubungi melalui kanal berikut:

- **WhatsApp** — [6285183885551](https://wa.me/6285183885551)
- **Instagram** — [@zusyni](https://instagram.com/zusyni)
- **Email** — [zukechi3@gmail.com](mailto:zukechi3@gmail.com)

Setiap pesan akan direspons dalam waktu yang wajar. Untuk kendala teknis, sertakan tangkapan layar atau deskripsi singkat agar proses penanganan lebih cepat.

---

<div align="center">

<sub>© 2026 <b>zunerator.vercel.app</b>. Seluruh hak cipta dilindungi.</sub><br />
<sub><i>"Dibangun untuk proses yang ingin tumbuh."</i></sub>

</div>
