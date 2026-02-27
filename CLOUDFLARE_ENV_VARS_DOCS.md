# 📋 Dokumentasi Lengkap Environment Variables
## Warung • Cloudflare Pages Functions (v28+)
> **File:** `functions/[[path]].js` — by dukunseo.com

---

## 🚀 CARA DEPLOY & SETTING DI CLOUDFLARE

### A. Upload File ke Cloudflare Pages

1. Login ke [https://dash.cloudflare.com](https://dash.cloudflare.com)
2. Pilih menu **Pages** → klik project kamu
3. Klik **Deployments** → **Upload assets** (atau connect ke GitHub/GitLab)
4. Upload seluruh folder project, pastikan `functions/[[path]].js` ikut terupload
5. Tunggu build selesai ✅

---

### B. Setting Environment Variables

1. Masuk ke **Cloudflare Dashboard** → **Pages** → pilih project
2. Klik tab **Settings** → **Environment Variables**
3. Klik **Add variable**
4. Isi **Variable name** dan **Value**
5. Pilih environment: **Production** dan/atau **Preview**
6. Klik **Save**
7. **Lakukan Redeploy** agar perubahan aktif:
   - Klik tab **Deployments** → klik **...** pada deployment terbaru → **Retry deployment**

> ⚠️ **PENTING:** Perubahan environment variables **tidak langsung aktif** tanpa redeploy. Selalu lakukan redeploy setelah mengubah variable.

---

### C. Cara Mengisi Nilai Variabel

- **String biasa:** langsung isi teksnya, contoh: `Situs Streaming Gratis`
- **Boolean:** isi `true` atau `false`
- **Angka:** isi angkanya saja, contoh: `24`
- **Kode HTML iklan:** paste full kode script dari provider iklan kamu
- **Variabel wajib:** `WARUNG_DOMAIN`, `WARUNG_NAME`, `DAPUR_API_KEY`

---

## 📦 DAFTAR LENGKAP SEMUA VARIABLE

---

## 🏠 SECTION 1 — IDENTITAS SITUS (WAJIB)

| Variable | Default | Keterangan |
|---|---|---|
| `WARUNG_DOMAIN` | *(auto-detect dari hostname)* | **[WAJIB]** Domain situs kamu, tanpa `https://`. Contoh: `namadomain.com` |
| `WARUNG_NAME` | *(auto-detect dari subdomain)* | Nama situs. Contoh: `NamaSitus` |
| `WARUNG_TAGLINE` | `Streaming gratis kualitas terbaik` | Tagline/slogan situs |
| `WARUNG_BASE_URL` | `https://{WARUNG_DOMAIN}` | Base URL lengkap. Isi jika pakai subdirectory. Contoh: `https://namadomain.com` |
| `WARUNG_TYPE` | `A` | Tipe konten situs: `A` = Video only, `B` = Album only, `C` = Video + Album |

---

## 🔌 SECTION 2 — KONEKSI DAPUR API (WAJIB)

| Variable | Default | Keterangan |
|---|---|---|
| `DAPUR_API_KEY` | *(kosong)* | **[WAJIB]** API Key dari dapur.dukunseo.com untuk mengambil konten |
| `DAPUR_BASE_URL` | `https://dapur.dukunseo.com` | URL server Dapur. Jangan diubah kecuali pakai self-hosted |
| `DAPUR_DEBUG` | `false` | Set `true` untuk menampilkan error detail di console (gunakan saat testing saja!) |

---

## 🔍 SECTION 3 — SEO & META

| Variable | Default | Keterangan |
|---|---|---|
| `SEO_DEFAULT_DESC` | `Streaming gratis kualitas terbaik. Akses mudah, tanpa registrasi.` | Meta description default untuk halaman yang tidak punya deskripsi sendiri |
| `SEO_KEYWORDS` | `streaming, video, album, cerita, gratis` | Meta keywords default (pisahkan dengan koma) |
| `SEO_TWITTER_SITE` | *(kosong)* | Handle Twitter/X untuk Twitter Card. Contoh: `@namaakun` |
| `SEO_OG_IMAGE_W` | `1200` | Lebar gambar OG default (piksel) |
| `SEO_OG_IMAGE_H` | `630` | Tinggi gambar OG default (piksel) |

---

## 📂 SECTION 4 — URL PATH / ROUTING

> Ganti slug URL sesuai bahasa/kebutuhan. **Jangan gunakan spasi atau karakter khusus.**

| Variable | Default | Contoh URL yang dihasilkan |
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

---

## 📊 SECTION 5 — TAMPILAN KONTEN

| Variable | Default | Keterangan |
|---|---|---|
| `ITEMS_PER_PAGE` | `24` | Jumlah item per halaman (grid konten) |
| `RELATED_COUNT` | `8` | Jumlah konten related/terkait yang ditampilkan di halaman detail |
| `TRENDING_COUNT` | `10` | Jumlah konten trending di halaman utama |

---

## 💰 SECTION 6 — IKLAN (ADS)

### 6.1 Pengaturan Global Iklan

| Variable | Default | Keterangan |
|---|---|---|
| `ADS_ENABLED` | `true` | `true` = tampilkan iklan, `false` = matikan SEMUA iklan di seluruh situs |
| `ADS_ADSENSE_CLIENT` | *(kosong)* | Publisher ID Google AdSense. Contoh: `ca-pub-1234567890123456`. Isi jika pakai AdSense |
| `ADS_LABEL` | *(kosong)* | Label teks di atas iklan (global override). Contoh: `Iklan` atau `Sponsored` |

---

### 6.2 Slot Iklan Per-Posisi

> Setiap slot punya 3 variabel: kode **Desktop**, kode **Mobile**, dan **on/off**.
> Jika variabel dikosongkan → otomatis pakai kode magsrv default.

#### 📍 HEADER TOP — Banner paling atas halaman

| Variable | Default | Keterangan |
|---|---|---|
| `ADS_HEADER_TOP_ENABLED` | `true` | `false` untuk mematikan slot ini |
| `ADS_HEADER_TOP_DESKTOP` | kode magsrv zone 5823946 | Kode HTML iklan header untuk **Desktop** |
| `ADS_HEADER_TOP_MOBILE` | kode magsrv zone 5824016 | Kode HTML iklan header untuk **Mobile** |

---

#### 📍 BEFORE GRID — Sebelum grid konten

| Variable | Default | Keterangan |
|---|---|---|
| `ADS_BEFORE_GRID_ENABLED` | `true` | `false` untuk mematikan slot ini |
| `ADS_BEFORE_GRID_DESKTOP` | kode magsrv zone 5823946 | Kode HTML iklan sebelum grid untuk **Desktop** |
| `ADS_BEFORE_GRID_MOBILE` | kode magsrv zone 5824016 | Kode HTML iklan sebelum grid untuk **Mobile** |

---

#### 📍 MID GRID — Ditengah grid konten

| Variable | Default | Keterangan |
|---|---|---|
| `ADS_MID_GRID_ENABLED` | `true` | `false` untuk mematikan slot ini |
| `ADS_MID_GRID_DESKTOP` | kode magsrv zone 5823946 | Kode HTML iklan tengah grid untuk **Desktop** |
| `ADS_MID_GRID_MOBILE` | kode magsrv zone 5824016 | Kode HTML iklan tengah grid untuk **Mobile** |
| `ADS_MID_GRID_INSERT_AFTER` | `6` | Sisipkan iklan setelah item ke-N di grid (angka) |

---

#### 📍 AFTER GRID — Setelah grid konten

| Variable | Default | Keterangan |
|---|---|---|
| `ADS_AFTER_GRID_ENABLED` | `true` | `false` untuk mematikan slot ini |
| `ADS_AFTER_GRID_DESKTOP` | kode magsrv zone 5846572 | Kode HTML iklan setelah grid untuk **Desktop** |
| `ADS_AFTER_GRID_MOBILE` | kode magsrv zone 5845680 | Kode HTML iklan setelah grid untuk **Mobile** |

---

#### 📍 SIDEBAR TOP — Atas sidebar

| Variable | Default | Keterangan |
|---|---|---|
| `ADS_SIDEBAR_TOP_ENABLED` | `true` | `false` untuk mematikan slot ini |
| `ADS_SIDEBAR_TOP_DESKTOP` | kode magsrv zone 5824012 | Kode HTML sidebar atas untuk **Desktop** |
| `ADS_SIDEBAR_TOP_MOBILE` | kode magsrv zone 5846568 | Kode HTML sidebar atas untuk **Mobile** |

---

#### 📍 SIDEBAR MID — Tengah sidebar

| Variable | Default | Keterangan |
|---|---|---|
| `ADS_SIDEBAR_MID_ENABLED` | `true` | `false` untuk mematikan slot ini |
| `ADS_SIDEBAR_MID_DESKTOP` | kode magsrv zone 5824012 | Kode HTML sidebar tengah untuk **Desktop** |
| `ADS_SIDEBAR_MID_MOBILE` | kode magsrv zone 5846568 | Kode HTML sidebar tengah untuk **Mobile** |

---

#### 📍 SIDEBAR BOTTOM — Bawah sidebar

| Variable | Default | Keterangan |
|---|---|---|
| `ADS_SIDEBAR_BOTTOM_ENABLED` | `true` | `false` untuk mematikan slot ini |
| `ADS_SIDEBAR_BOTTOM_DESKTOP` | kode magsrv zone 5824012 | Kode HTML sidebar bawah untuk **Desktop** |
| `ADS_SIDEBAR_BOTTOM_MOBILE` | kode magsrv zone 5846568 | Kode HTML sidebar bawah untuk **Mobile** |

---

#### 📍 AFTER CONTENT — Setelah konten/artikel

| Variable | Default | Keterangan |
|---|---|---|
| `ADS_AFTER_CONTENT_ENABLED` | `true` | `false` untuk mematikan slot ini |
| `ADS_AFTER_CONTENT_DESKTOP` | kode magsrv zone 5846572 | Kode HTML setelah konten untuk **Desktop** |
| `ADS_AFTER_CONTENT_MOBILE` | kode magsrv zone 5845680 | Kode HTML setelah konten untuk **Mobile** |

---

#### 📍 FOOTER TOP — Atas footer

| Variable | Default | Keterangan |
|---|---|---|
| `ADS_FOOTER_TOP_ENABLED` | `true` | `false` untuk mematikan slot ini |
| `ADS_FOOTER_TOP_DESKTOP` | kode magsrv zone 5846572 | Kode HTML footer atas untuk **Desktop** |
| `ADS_FOOTER_TOP_MOBILE` | kode magsrv zone 5845680 | Kode HTML footer atas untuk **Mobile** |

---

### 6.3 Contoh Kode Iklan yang Bisa Dipakai

**Google AdSense:**
```
<ins class="adsbygoogle" style="display:block" data-ad-client="ca-pub-XXXXX" data-ad-slot="YYYYYYY" data-ad-format="auto" data-full-width-responsive="true"></ins><script>(adsbygoogle=window.adsbygoogle||[]).push({});</script>
```

**Magsrv (format baru):**
```
<script async type="application/javascript" src="https://a.magsrv.com/ad-provider.js"></script> <ins class="eas6a97888e2" data-zoneid="ZONE_ID_KAMU"></ins> <script>(AdProvider = window.AdProvider || []).push({"serve": {}});</script>
```

**Mematikan 1 slot saja (contoh matikan mid_grid):**
```
ADS_MID_GRID_ENABLED = false
```

**Mematikan semua iklan:**
```
ADS_ENABLED = false
```

---

## 📞 SECTION 7 — KONTAK & HALAMAN STATIS

| Variable | Default | Keterangan |
|---|---|---|
| `CONTACT_EMAIL` | `admin@{WARUNG_DOMAIN}` | Email untuk halaman contact & footer |
| `CONTACT_EMAIL_NAME` | `{WARUNG_NAME} Admin` | Nama pengirim email di form kontak |

---

## 🔒 SECTION 8 — KEAMANAN

| Variable | Default | Keterangan |
|---|---|---|
| `HMAC_SECRET` | *(kosong)* | Secret key untuk HMAC token signing. Isi dengan string acak panjang. Contoh: `aBcXyZ123random456secret` |
| `HONEYPOT_PREFIX` | `trap` | Prefix URL honeypot untuk menangkap bot. Contoh: `trap` → URL `/trap/xxx` akan redirect bot |
| `SITEMAP_SALT` | `{WARUNG_DOMAIN}` | Salt untuk randomisasi urutan sitemap. Biarkan default kecuali ada kebutuhan khusus |

---

## 🎯 SECTION 9 — KEYWORD CANNIBALIZE (SEO Landing Pages)

| Variable | Default | Keterangan |
|---|---|---|
| `CANNIBALIZE_PATH` | `k` | Path URL untuk keyword landing pages. Contoh: `k` → URL `/k/nama-keyword` |
| `CANNIBALIZE_KEYWORDS` | *(daftar panjang default)* | Daftar keyword target, dipisah koma. Contoh: `film hot,video viral,streaming gratis`. Jika kosong, pakai daftar default |

---

## 📋 RINGKASAN VARIABLE WAJIB

Berikut variable **minimum yang harus di-set** agar situs berfungsi:

```
WARUNG_DOMAIN      = namadomain.com
WARUNG_NAME        = Nama Situs Kamu
DAPUR_API_KEY      = (api key dari dapur.dukunseo.com)
```

---

## 📋 TEMPLATE LENGKAP — Copy & Paste

Salin template di bawah ini, isi nilainya, lalu input satu per satu di Cloudflare Dashboard:

```
# === WAJIB ===
WARUNG_DOMAIN               = namadomain.com
WARUNG_NAME                 = Nama Situs Kamu
DAPUR_API_KEY               = ISI_API_KEY_DAPUR

# === IDENTITAS ===
WARUNG_TAGLINE              = Streaming gratis kualitas terbaik
WARUNG_TYPE                 = A

# === SEO ===
SEO_DEFAULT_DESC            = Nonton streaming gratis kualitas HD. Tanpa registrasi, akses langsung.
SEO_KEYWORDS                = streaming, video, nonton, gratis, terbaru
SEO_TWITTER_SITE            =

# === URL PATH ===
PATH_CONTENT                = tonton
PATH_SEARCH                 = cari
PATH_CATEGORY               = kategori
PATH_TAG                    = tag
PATH_ALBUM                  = album

# === KONTEN ===
ITEMS_PER_PAGE              = 24
RELATED_COUNT               = 8
TRENDING_COUNT              = 10

# === IKLAN GLOBAL ===
ADS_ENABLED                 = true
ADS_ADSENSE_CLIENT          =

# === IKLAN — HEADER TOP ===
ADS_HEADER_TOP_ENABLED      = true
ADS_HEADER_TOP_DESKTOP      = (paste kode iklan desktop)
ADS_HEADER_TOP_MOBILE       = (paste kode iklan mobile)

# === IKLAN — BEFORE GRID ===
ADS_BEFORE_GRID_ENABLED     = true
ADS_BEFORE_GRID_DESKTOP     = (paste kode iklan desktop)
ADS_BEFORE_GRID_MOBILE      = (paste kode iklan mobile)

# === IKLAN — MID GRID ===
ADS_MID_GRID_ENABLED        = true
ADS_MID_GRID_INSERT_AFTER   = 6
ADS_MID_GRID_DESKTOP        = (paste kode iklan desktop)
ADS_MID_GRID_MOBILE         = (paste kode iklan mobile)

# === IKLAN — AFTER GRID ===
ADS_AFTER_GRID_ENABLED      = true
ADS_AFTER_GRID_DESKTOP      = (paste kode iklan desktop)
ADS_AFTER_GRID_MOBILE       = (paste kode iklan mobile)

# === IKLAN — SIDEBAR TOP ===
ADS_SIDEBAR_TOP_ENABLED     = true
ADS_SIDEBAR_TOP_DESKTOP     = (paste kode iklan desktop)
ADS_SIDEBAR_TOP_MOBILE      = (paste kode iklan mobile)

# === IKLAN — SIDEBAR MID ===
ADS_SIDEBAR_MID_ENABLED     = true
ADS_SIDEBAR_MID_DESKTOP     = (paste kode iklan desktop)
ADS_SIDEBAR_MID_MOBILE      = (paste kode iklan mobile)

# === IKLAN — SIDEBAR BOTTOM ===
ADS_SIDEBAR_BOTTOM_ENABLED  = true
ADS_SIDEBAR_BOTTOM_DESKTOP  = (paste kode iklan desktop)
ADS_SIDEBAR_BOTTOM_MOBILE   = (paste kode iklan mobile)

# === IKLAN — AFTER CONTENT ===
ADS_AFTER_CONTENT_ENABLED   = true
ADS_AFTER_CONTENT_DESKTOP   = (paste kode iklan desktop)
ADS_AFTER_CONTENT_MOBILE    = (paste kode iklan mobile)

# === IKLAN — FOOTER TOP ===
ADS_FOOTER_TOP_ENABLED      = true
ADS_FOOTER_TOP_DESKTOP      = (paste kode iklan desktop)
ADS_FOOTER_TOP_MOBILE       = (paste kode iklan mobile)

# === KONTAK ===
CONTACT_EMAIL               = admin@namadomain.com
CONTACT_EMAIL_NAME          = Admin Situs

# === KEAMANAN ===
HMAC_SECRET                 = (string acak panjang, contoh: xK9mP2qL7nR4sT6wA1bC3dE5)
HONEYPOT_PREFIX             = trap
SITEMAP_SALT                = (biarkan kosong = pakai domain)

# === KEYWORD SEO ===
CANNIBALIZE_PATH            = k
CANNIBALIZE_KEYWORDS        = (biarkan kosong = pakai default, atau isi sendiri)
```

---

## ❓ FAQ

**Q: Apakah semua variable harus diisi?**
A: Tidak. Hanya `WARUNG_DOMAIN`, `WARUNG_NAME`, dan `DAPUR_API_KEY` yang wajib. Sisanya punya nilai default.

**Q: Bagaimana jika saya tidak isi variabel iklan?**
A: Sistem otomatis pakai kode iklan magsrv default yang sudah ada di dalam file. Tidak ada slot kosong.

**Q: Apakah perubahan variable langsung aktif?**
A: Tidak. Harus Redeploy setelah mengubah variable agar perubahan aktif.

**Q: Cara matikan iklan di halaman tertentu saja?**
A: Tidak bisa per-halaman via env var. Matikan per-slot (contoh: `ADS_MID_GRID_ENABLED = false`) atau matikan semua dengan `ADS_ENABLED = false`.

**Q: Format CANNIBALIZE_KEYWORDS?**
A: Pisahkan dengan koma. Contoh: `nonton film,video terbaru,streaming gratis,bokep indo`

**Q: Apa bedanya `ADS_ENABLED = false` vs matikan per slot?**
A: `ADS_ENABLED = false` matikan **semua** iklan sekaligus. Matikan per slot lebih selektif, iklan di posisi lain tetap jalan.

---

*Dokumentasi ini dibuat berdasarkan source code `functions/[[path]].js` v28.0 — dukunseo.com*
