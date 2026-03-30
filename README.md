# html-AI
# 🤖 PocketAI

> AI chat ringan berbasis browser — dukung **Cloud (Claude API)** dan **Lokal (Ollama, 100% offline)** dalam satu file HTML.

![PocketAI](https://img.shields.io/badge/PocketAI-v2.0-7c6aff?style=for-the-badge)
![License](https://img.shields.io/badge/license-MIT-48c97e?style=for-the-badge)
![Offline](https://img.shields.io/badge/offline-ready-48c97e?style=for-the-badge)
![No Install](https://img.shields.io/badge/no_install-required-ff6a9b?style=for-the-badge)

[![Deploy static content to Pages](https://github.com/suryadi346-star/html-AI/actions/workflows/static.yml/badge.svg)](https://github.com/suryadi346-star/html-AI/actions/workflows/static.yml)

---

## ✨ Fitur Utama

| Fitur | Keterangan |
|-------|-----------|
| ☁ **Cloud Mode** | Chat dengan Claude (Anthropic) via API |
| 🦙 **Lokal Mode** | Chat dengan model Ollama, 100% offline & privat |
| ⚡ **Streaming** | Response muncul token per token secara real-time |
| 🔄 **Auto-detect** | Otomatis mendeteksi model Ollama yang terinstall |
| 💬 **Conversation History** | AI mengingat konteks percakapan |
| 🎨 **Dark UI** | Antarmuka gelap modern, mobile-friendly |
| 📋 **Markdown Rendering** | Bold, inline code, dan code block dirender rapi |
| 🚫 **Zero Install** | Cukup buka file HTML di browser — selesai! |

---

## 🚀 Cara Pakai

### Mode Cloud (Claude API)

1. Buka file `pocketai.html` di browser
2. Pastikan koneksi internet aktif
3. Pilih mode **☁ Cloud** (sudah aktif secara default)
4. Mulai chat!

> Mode Cloud menggunakan **Claude API dari Anthropic**. Jika dipakai melalui Claude.ai, API key sudah terhubung otomatis.

---

### Mode Lokal (Ollama — Offline)

#### 1. Install Ollama

```bash
# Linux / macOS
curl -fsSL https://ollama.ai/install.sh | sh

# Windows
# Download installer dari: https://ollama.ai
```

#### 2. Jalankan Ollama dengan CORS Enabled

> ⚠️ **Wajib** mengaktifkan CORS agar browser bisa terhubung ke Ollama.

```bash
# Linux / macOS
OLLAMA_ORIGINS="*" ollama serve

# Windows (Command Prompt)
set OLLAMA_ORIGINS=*
ollama serve

# Windows (PowerShell)
$env:OLLAMA_ORIGINS="*"; ollama serve
```

#### 3. Download Model

```bash
# Ringan & cepat (~1.9 GB)
ollama pull qwen2.5:3b

# Seimbang (~2 GB)
ollama pull llama3.2

# Powerful (~4.1 GB)
ollama pull mistral

# Microsoft Phi (~2.2 GB)
ollama pull phi3.5
```

#### 4. Buka PocketAI

1. Buka `pocketai.html` di browser
2. Klik tombol **🦙 Lokal** di header
3. Klik **⟳ Detect** — model akan terdeteksi otomatis
4. Pilih model dari dropdown, lalu mulai chat!

---

## 🖥️ Screenshot

```
┌─────────────────────────────────────────────────────┐
│  🤖 PocketAI    [☁ Cloud] [🦙 Lokal]   [Model ▾] │
├─────────────────────────────────────────────────────┤
│                                                     │
│              ✦ PocketAI                             │
│    Chat dengan AI — Cloud atau Lokal                │
│                                                     │
│  ┌─────────────────────────────────────────────┐   │
│  │ 👤  Halo, apa itu machine learning?          │   │
│  └─────────────────────────────────────────────┘   │
│                                                     │
│  ┌─────────────────────────────────────────────┐   │
│  │ ✦  claude-sonnet-4-6                        │   │
│  │ Machine learning adalah...                  │   │
│  └─────────────────────────────────────────────┘   │
│                                                     │
├─────────────────────────────────────────────────────┤
│  [ Ketik pesan…                          [➤] ]     │
└─────────────────────────────────────────────────────┘
```

---

## 🔧 Konfigurasi

### Ganti Model Cloud

Di header, klik dropdown model untuk memilih:
- `claude-sonnet-4-6` — Cerdas & seimbang (default)
- `claude-haiku-4-5` — Sangat cepat & ringan

### Ganti Host Ollama

Jika Ollama berjalan di port atau host berbeda, ubah di field input host:

```
http://localhost:11434     ← default
http://192.168.1.5:11434  ← remote LAN
```

### System Prompt

Edit bagian `system` di dalam fungsi `sendCloud()` atau `sendOllama()` di file HTML untuk mengubah kepribadian AI:

```javascript
system: 'Kamu adalah PocketAI, asisten AI yang cerdas...'
```

---

## 🧩 Struktur File

```
pocketai.html        ← Satu file, semua fitur
```

Seluruh aplikasi dikemas dalam **satu file HTML** tanpa dependensi eksternal (kecuali Google Fonts untuk tipografi).

---

## 🔐 Privasi

| Mode | Data dikirim ke | Offline? |
|------|----------------|----------|
| ☁ Cloud | Server Anthropic (Claude API) | ❌ Butuh internet |
| 🦙 Lokal | Hanya ke Ollama di komputer kamu | ✅ 100% offline |

Mode Lokal tidak mengirim data apapun ke luar perangkat kamu.

---

## ⚙️ Perbandingan Mode

| | ☁ Cloud (Claude) | 🦙 Lokal (Ollama) |
|---|---|---|
| **Kecepatan** | Cepat | Tergantung hardware |
| **Kualitas** | Sangat tinggi | Baik (tergantung model) |
| **Privasi** | Data ke server | 100% lokal |
| **Biaya** | API usage | Gratis |
| **Internet** | Wajib | Tidak perlu |
| **Setup** | Langsung pakai | Install Ollama dulu |

---

## 🛠️ Teknologi

- **Vanilla JavaScript** — tanpa framework
- **Claude API** (`claude-sonnet-4-20250514`) — mode cloud
- **Ollama API** (`/api/chat`) — mode lokal
- **Server-Sent Events / NDJSON Streaming** — real-time response
- **CSS Custom Properties** — theming dinamis cloud/lokal
- **Google Fonts** — Syne + JetBrains Mono

---

## ❓ Troubleshooting

**Ollama tidak terdeteksi?**
- Pastikan Ollama berjalan dengan `OLLAMA_ORIGINS="*"`
- Cek apakah port 11434 aktif: `curl http://localhost:11434/api/tags`
- Beberapa browser memblokir request ke `localhost` — coba gunakan browser berbeda

**Response berhenti di tengah?**
- Tambah `max_tokens` di kode (default: 1024)
- Untuk model lokal besar, pastikan RAM cukup

**Model Ollama tidak muncul?**
- Jalankan `ollama list` untuk cek model yang terinstall
- Pull model terlebih dahulu: `ollama pull llama3.2`

---

## 📄 Lisensi

MIT License — bebas digunakan, dimodifikasi, dan didistribusikan.

---

## 🙏 Inspirasi

Proyek ini terinspirasi dari [PocketPal AI](https://github.com/a-ghorbani/pocketpal-ai) — aplikasi mobile yang menjalankan model AI lokal langsung di perangkat.

---

<div align="center">
  Dibuat dengan ❤️ menggunakan Claude AI
</div>
