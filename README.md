# 🍜 Warung — Cloudflare Pages Functions
> Streaming site engine berbasis Cloudflare Pages + Dapur API  
> by [dukunseo.com](https://dukunseo.com)

---

## 📁 Struktur Project

```
project/
├── functions/
│   └── [[path]].js     ← Engine utama (semua routing & logic ada di sini)
├── public/
│   ├── assets/
│   │   ├── og-default.jpg
│   │   └── no-thumb.jpg
│   └── index.html      ← (opsional, bisa kosong)
└── README.md
```

---

## 🚀 Deploy ke Cloudflare Pages

### Langkah 1 — Buat Project Baru

1. Login ke [dash.cloudflare.com](https://dash.cloudflare.com)
2. Klik **Pages** → **Create a project**
3. Pilih **Upload assets** (tanpa Git) atau connect ke **GitHub/GitLab**

### Langkah 2 — Upload / Connect

**Cara A — Upload langsung (drag & drop):**
- Zip seluruh folder project
- Drag & drop ke halaman upload Cloudflare Pages
- Klik **Deploy site**

**Cara B — Connect GitHub:**
- Pilih repository kamu
- Build settings:
  - **Framework preset:** `None`
  - **Build command:** *(kosongkan)*
  - **Build output directory:** `public`
- Klik **Save and Deploy**

### Langkah 3 — Set Environment Variables

1. Masuk ke **Settings** → **Environment Variables**
2. Klik **Add variable**, isi nama & nilai
3. Pilih environment **Production** (dan **Preview** jika perlu)
4. Klik **Save**

### Langkah 4 — Redeploy

Setelah set variable, selalu lakukan redeploy:
- Tab **Deployments** → klik **...** pada deployment terbaru → **Retry deployment**

### Langkah 5 — Custom Domain (opsional)

- Tab **Custom domains** → **Set up a custom domain**
- Ikuti instruksi DNS Cloudflare

---

## ⚙️ Environment Variables

> Semua konfigurasi dilakukan via **Cloudflare Dashboard → Settings → Environment Variables**.  
> Tidak ada file `wrangler.toml`. Tidak perlu CLI.

### 🔴 Wajib Diisi

| Variable | Contoh | Keterangan |
|---|---|---|
| `WARUNG_DOMAIN` | `namadomain.com` | Domain situs tanpa `https://` |
| `WARUNG_NAME` | `Nama Situs` | Nama situs yang tampil di halaman |
| `DAPUR_API_KEY` | `xxxx-xxxx-xxxx` | API Key dari dapur.dukunseo.com |

### 🟡 Identitas Situs

| Variable | Default | Keterangan |
|---|---|---|
| `WARUNG_TAGLINE` | `Streaming gratis kualitas terbaik` | Slogan situs |
| `WARUNG_TYPE` | `A` | `A` = Video only · `B` = Album only · `C` = Video + Album |
| `WARUNG_BASE_URL` | `https://{domain}` | Base URL lengkap, isi jika pakai subdirectory |

### 🟡 Dapur API

| Variable | Default | Keterangan |
|---|---|---|
| `DAPUR_BASE_URL` | `https://dapur.dukunseo.com` | URL server Dapur, jangan diubah kecuali self-hosted |
| `DAPUR_DEBUG` | `false` | Set `true` untuk debug log di console (testing only) |

### 🟡 SEO

| Variable | Default | Keterangan |
|---|---|---|
| `SEO_DEFAULT_DESC` | `Streaming gratis kualitas terbaik...` | Meta description default |
| `SEO_KEYWORDS` | `streaming, video, album, gratis` | Meta keywords default |
| `SEO_TWITTER_SITE` | *(kosong)* | Handle Twitter/X, contoh: `@namaakun` |
| `SEO_OG_IMAGE_W` | `1200` | Lebar OG image (px) |
| `SEO_OG_IMAGE_H` | `630` | Tinggi OG image (px) |

### 🟡 URL Path

| Variable | Default | URL |
|---|---|---|
| `PATH_CONTENT` | `tonton` | `/tonton/judul-video` |
| `PATH_SEARCH` | `cari` | `/cari?q=keyword` |
| `PATH_CATEGORY` | `kategori` | `/kategori/video` |
| `PATH_TAG` | `tag` | `/tag/nama-tag` |
| `PATH_ALBUM` | `album` | `/album/nama-album` |
| `PATH_ABOUT` | `about` | `/about` |
| `PATH_CONTACT` | `contact` | `/contact` |
| `PATH_FAQ` | `faq` | `/faq` |
| `PATH_DMCA` | `dmca` | `/dmca` |
| `PATH_TERMS` | `terms` | `/terms` |
| `PATH_PRIVACY` | `privacy` | `/privacy` |

### 🟡 Tampilan Konten

| Variable | Default | Keterangan |
|---|---|---|
| `ITEMS_PER_PAGE` | `24` | Jumlah item per halaman |
| `RELATED_COUNT` | `8` | Jumlah konten related di halaman detail |
| `TRENDING_COUNT` | `10` | Jumlah konten trending di homepage |

### 🟢 Iklan — Global

| Variable | Default | Keterangan |
|---|---|---|
| `ADS_ENABLED` | `true` | `false` = matikan semua iklan |
| `ADS_ADSENSE_CLIENT` | *(kosong)* | Publisher ID AdSense, contoh: `ca-pub-123456` |
| `ADS_LABEL` | *(kosong)* | Label global di atas iklan, contoh: `Iklan` |

### 🟢 Iklan — Per Slot

Setiap slot punya 3 variable: `_ENABLED`, `_DESKTOP`, `_MOBILE`.  
Jika kode dikosongkan → pakai kode magsrv default otomatis.

| Slot | Enable | Desktop | Mobile |
|---|---|---|---|
| Header atas | `ADS_HEADER_TOP_ENABLED` | `ADS_HEADER_TOP_DESKTOP` | `ADS_HEADER_TOP_MOBILE` |
| Sebelum grid | `ADS_BEFORE_GRID_ENABLED` | `ADS_BEFORE_GRID_DESKTOP` | `ADS_BEFORE_GRID_MOBILE` |
| Tengah grid | `ADS_MID_GRID_ENABLED` | `ADS_MID_GRID_DESKTOP` | `ADS_MID_GRID_MOBILE` |
| Setelah grid | `ADS_AFTER_GRID_ENABLED` | `ADS_AFTER_GRID_DESKTOP` | `ADS_AFTER_GRID_MOBILE` |
| Sidebar atas | `ADS_SIDEBAR_TOP_ENABLED` | `ADS_SIDEBAR_TOP_DESKTOP` | `ADS_SIDEBAR_TOP_MOBILE` |
| Sidebar tengah | `ADS_SIDEBAR_MID_ENABLED` | `ADS_SIDEBAR_MID_DESKTOP` | `ADS_SIDEBAR_MID_MOBILE` |
| Sidebar bawah | `ADS_SIDEBAR_BOTTOM_ENABLED` | `ADS_SIDEBAR_BOTTOM_DESKTOP` | `ADS_SIDEBAR_BOTTOM_MOBILE` |
| Setelah konten | `ADS_AFTER_CONTENT_ENABLED` | `ADS_AFTER_CONTENT_DESKTOP` | `ADS_AFTER_CONTENT_MOBILE` |
| Footer atas | `ADS_FOOTER_TOP_ENABLED` | `ADS_FOOTER_TOP_DESKTOP` | `ADS_FOOTER_TOP_MOBILE` |

**Variable tambahan mid grid:**

| Variable | Default | Keterangan |
|---|---|---|
| `ADS_MID_GRID_INSERT_AFTER` | `6` | Sisipkan iklan setelah item ke-N di grid |

### 🟡 Kontak

| Variable | Default | Keterangan |
|---|---|---|
| `CONTACT_EMAIL` | `admin@{domain}` | Email kontak |
| `CONTACT_EMAIL_NAME` | `{nama} Admin` | Nama pengirim email |

### 🔵 Keamanan

| Variable | Default | Keterangan |
|---|---|---|
| `HMAC_SECRET` | *(kosong)* | Secret key acak untuk signing token |
| `HONEYPOT_PREFIX` | `trap` | Prefix URL jebakan bot, contoh: `/trap/xxx` |
| `SITEMAP_SALT` | `{domain}` | Salt randomisasi sitemap |

### 🔵 SEO — Keyword Cannibalize

| Variable | Default | Keterangan |
|---|---|---|
| `CANNIBALIZE_PATH` | `k` | Path URL keyword pages, contoh: `/k/nama-keyword` |
| `CANNIBALIZE_KEYWORDS` | *(daftar default panjang)* | List keyword, pisah koma. Kosong = pakai default |

---

## 📋 Template Variable — Siap Pakai

Copy semua ini, isi nilainya, input satu per satu di Cloudflare Dashboard:

```
WARUNG_DOMAIN               = namadomain.com
WARUNG_NAME                 = Nama Situs Kamu
DAPUR_API_KEY               = ISI_API_KEY_DAPUR_DI_SINI

WARUNG_TAGLINE              = Streaming gratis kualitas terbaik
WARUNG_TYPE                 = A

SEO_DEFAULT_DESC            = Nonton streaming gratis kualitas HD. Tanpa registrasi.
SEO_KEYWORDS                = streaming, video, nonton, gratis, terbaru

ITEMS_PER_PAGE              = 24
RELATED_COUNT               = 8
TRENDING_COUNT              = 10

ADS_ENABLED                 = true
ADS_HEADER_TOP_ENABLED      = true
ADS_HEADER_TOP_DESKTOP      = (paste kode iklan desktop)
ADS_HEADER_TOP_MOBILE       = (paste kode iklan mobile)
ADS_MID_GRID_ENABLED        = true
ADS_MID_GRID_INSERT_AFTER   = 6
ADS_MID_GRID_DESKTOP        = (paste kode iklan desktop)
ADS_MID_GRID_MOBILE         = (paste kode iklan mobile)
ADS_AFTER_GRID_ENABLED      = true
ADS_AFTER_GRID_DESKTOP      = (paste kode iklan desktop)
ADS_AFTER_GRID_MOBILE       = (paste kode iklan mobile)
ADS_SIDEBAR_TOP_ENABLED     = true
ADS_SIDEBAR_TOP_DESKTOP     = (paste kode iklan desktop)
ADS_SIDEBAR_TOP_MOBILE      = (paste kode iklan mobile)
ADS_AFTER_CONTENT_ENABLED   = true
ADS_AFTER_CONTENT_DESKTOP   = (paste kode iklan desktop)
ADS_AFTER_CONTENT_MOBILE    = (paste kode iklan mobile)
ADS_FOOTER_TOP_ENABLED      = true
ADS_FOOTER_TOP_DESKTOP      = (paste kode iklan desktop)
ADS_FOOTER_TOP_MOBILE       = (paste kode iklan mobile)

CONTACT_EMAIL               = admin@namadomain.com
CONTACT_EMAIL_NAME          = Admin Situs
HMAC_SECRET                 = isi-string-acak-panjang-di-sini
HONEYPOT_PREFIX             = trap
```

---

## 💡 Tips

- **Iklan tidak muncul?** Pastikan `ADS_ENABLED = true` dan kode iklan sudah diisi
- **Ganti provider iklan?** Cukup update variable `_DESKTOP` / `_MOBILE` di dashboard, redeploy
- **Matikan 1 slot iklan?** Set `ADS_xxx_ENABLED = false` pada slot yang diinginkan
- **Multi-domain?** Buat project Pages berbeda untuk setiap domain, set `WARUNG_DOMAIN` & `WARUNG_NAME` yang berbeda
- **Perubahan tidak aktif?** Jangan lupa **Redeploy** setelah simpan variable baru

---

## 🔧 Cara Update File JS

1. Edit `functions/[[path]].js` di lokal
2. Upload ulang via Cloudflare Pages dashboard → **Create new deployment**
3. Drag & drop folder project yang sudah diupdate
4. Deploy — variable yang sudah di-set **tidak perlu diisi ulang**

---

*Warung v28.0 · dukunseo.com*
