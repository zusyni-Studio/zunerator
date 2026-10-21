
<div align="center">

<!-- LOGO SVG -->
<svg width="80" height="80" viewBox="0 0 24 24" fill="none" stroke="#000000" stroke-width="2.5" stroke-linecap="square" stroke-linejoin="miter">
  <path d="M5 5h14L5 19h14" />
</svg>

# ZUNERATOR

**Alight Motion Premium Activation Gateway**

[![Version](https://img.shields.io/badge/version-2.4_PRO-black?style=for-the-badge&logo=vercel)](#)
[![Status](https://img.shields.io/badge/status-online-emerald?style=for-the-badge&logo=statuspage)](#)
[![API](https://img.shields.io/badge/API_Integration-GenCipta-e11d48?style=for-the-badge)](#)

<p align="center">
  <i>"Dari email. Jadi Premium."</i><br />
  Aktivasi lisensi Alight Motion Premium secara otomatis, cepat, dan aman melalui integrasi Gateway GenCipta.
</p>

---

</div>

## ⚡ Tentang Proyek

**ZUNERATOR** adalah aplikasi berbasis web yang dirancang untuk menyederhanakan proses aktivasi lisensi Alight Motion Premium. Menggunakan pendekatan **Brutalist-Modern** dengan antarmuka minimalis ala *developer console*, aplikasi ini memandu pengguna melalui alur *wizard* 4 langkah yang terstruktur, terintegrasi langsung dengan API resmi, dan dilengkapi dengan asisten AI.

### ✨ Fitur Utama

- 🚀 **4-Step Activation Wizard**: Alur linear yang jelas (Kirim Link → Cek Email → Verifikasi → Struk).
- 🛡️ **AIHELP Assistant**: Chatbot cerdas yang terintegrasi dengan *server-controlled system prompt* untuk keamanan maksimal.
- 📟 **Technical Aesthetic**: Desain terinspirasi dari *developer console*, menggunakan *dot-matrix typography*, *grid layout*, dan terminal log.
- ⚡ **Real-time Feedback**: Log sistem langsung menampilkan *response* JSON dari backend.
- 🔒 **Anti-Hallucination & Guardrail**: Sistem validasi berlapis pada *output* AI dan respons API.
- 📱 **Fully Responsive**: Tampilan optimal dari perangkat *mobile* hingga *desktop*.

---

## 🎨 Design System

Proyek ini menggunakan *design language* yang sangat spesifik untuk memastikan konsistensi UI/UX:

| Token | Value | Visual |
| :--- | :--- | :--- |
| **Background** | `#fcfcfc` | Light Off-White |
| **Text Primary** | `#0f172a` | Slate 900 |
| **Accent** | `#e11d48` | Rose 600 |
| **Typography** | `Inter` & `JetBrains Mono` | Clean & Technical |
| **Border Radius** | `md` / `xl` | Sharp / Structured |
| **Effect** | *Dot Pattern* & *ASCII Art* | Brutalist/Retro |

---

## 🛠️ Tech Stack

- **Frontend Core**: HTML5, Vanilla JavaScript (ES6+)
- **Styling**: [Tailwind CSS](https://tailwindcss.com/) (via CDN)
- **Typography**: [Google Fonts](https://fonts.google.com/) (Inter, JetBrains Mono)
- **Icons**: [Font Awesome 6](https://fontawesome.com/)
- **External API**: GenCipta Gateway (`https://gateway.gencipta.com/api`)

---

## 🚀 Panduan Instalasi

Karena ini adalah *single-file application* (satu file HTML), Anda tidak memerlukan *build tools* yang rumit.

### 1. Clone / Download
Unduh file `index.html` (atau `aplikasi_generator_alight_motion.html`) dari repositori ini.

### 2. Jalankan Lokal
Cukup buka file tersebut menggunakan *browser* (Chrome, Edge, Safari, Firefox). 

*(Opsional)* Disarankan menggunakan *Live Server* di VS Code untuk pengalaman *development* yang lebih baik:
```bash
# Jika menggunakan VS Code, klik kanan file HTML -> Open with Live Server
# Atau via Python:
python -m http.server 8000
```

### 3. Konfigurasi
Buka file HTML dan cari bagian konfigurasi di dalam tag `<script>`:
```javascript
const AUTH_KEY = "Bearer <YOUR_GEN_CIPTA_API_KEY>";
const API_BASE_URL = "https://gateway.gencipta.com/api";
```

---

## ⚠️ Security & Production Notice

> **PENTING (Sesuai Master Prompt Bagian 8):** 
> Saat ini `AUTH_KEY` dan *System Prompt AI* di-*embed* secara *client-side* (di dalam file HTML/JS). Untuk mencegah penyalahgunaan (API Key Leak / Prompt Injection via DevTools), **WAJIB HUKUMNYA** memindahkan *logic* ke *backend proxy* sebelum melakukan *deployment* ke *production*.

**Rekomendasi Arsitektur Production:**
1. Gunakan **Vercel Serverless Functions** atau **Cloudflare Workers**.
2. Simpan `AUTH_KEY` di dalam *Environment Variables* server.
3. Frontend hanya memanggil endpoint internal Anda (contoh: `/api/proxy/send-link`).

---

## 📂 Struktur File

```text
zunerator/
├── index.html       # Single-file App (HTML + CSS + JS)
└── README.md        # Dokumentasi Proyek
```

---

## 🤝 Kontak & Dukungan

Dikembangkan dan dikelola oleh **zukechi**. Jika Anda mengalami kendala teknis terkait API atau membutuhkan bantuan langsung, silakan hubungi:

- 💬 **WhatsApp**: [6285183885551](https://wa.me/6285183885551)
- 📸 **Instagram**: [@zusyni](https://instagram.com/zusyni)
- ✉️ **Email**: [zukechi3@gmail.com](mailto:zukechi3@gmail.com)

<br />

<div align="center">
  <sub>© 2026 <b>zunerator.vercel.app</b>. All rights reserved.</sub><br />
  <i>"Dibangun untuk proses yang ingin tumbuh."</i>
</div>
