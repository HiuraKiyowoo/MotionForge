# MotionForge

**Cinematic motion graphics for the open web.**

MotionForge adalah Agent Skill yang membantu AI coding agent membuat motion graphic, opener, promo, explainer, product demo, kinetic typography, UI showcase, dan visual storytelling yang terasa seperti video—bukan slideshow.

MotionForge memakai fondasi **HTML, CSS, JavaScript, GSAP**, dan **Three.js bila diperlukan**. Output default berupa satu `index.html` yang dapat diputar langsung di browser, autoplay, dan loop.

> MotionForge dikembangkan dari [Bang Motion](https://github.com/bangtutorial/bang-motion) oleh Bang Tutorial. Aturan, starter, dan referensi asal tetap berada di bawah lisensi MIT.

## Yang bisa dibuat

- Product opener dan promo
- Website atau SaaS demo
- Kinetic typography
- Bumper, ident, intro, dan outro
- Explainer 16:9 atau 9:16
- Visual storytelling berbasis kamera dan scene
- Animated UI showcase
- Web animation yang siap dirender menjadi MP4

## Instalasi dengan `npx skills`

### Mode interaktif — direkomendasikan

CLI akan menampilkan pilihan skill, agent, scope, metode symlink/copy, dan konfirmasi:

```bash
npx skills add https://github.com/HiuraKiyowoo/MotionForge
```

Pilih:

1. Skill: `motionforge`
2. Agent: `Hermes Agent` atau coding agent lain
3. Scope: global atau project
4. Method: symlink atau copy

### Instalasi langsung ke Hermes Agent

```bash
npx skills add https://github.com/HiuraKiyowoo/MotionForge \
  --skill motionforge \
  --agent hermes-agent \
  --global \
  --copy \
  --yes
```

Jika nama agent pada versi CLI Anda berbeda, gunakan mode interaktif dan pilih **Hermes Agent** dari daftar.

### Instalasi ke semua agent yang terdeteksi

```bash
npx skills add https://github.com/HiuraKiyowoo/MotionForge \
  --skill motionforge \
  --agent '*' \
  --global \
  --copy \
  --yes
```

### Melihat skill sebelum memasang

```bash
npx skills add https://github.com/HiuraKiyowoo/MotionForge --list
```

### Memperbarui instalasi

```bash
npx skills update motionforge
```

## Struktur repo

```text
MotionForge/
├── README.md
├── LICENSE
└── skills/
    └── motionforge/
        ├── SKILL.md
        ├── assets/
        ├── references/
        └── scripts/
```

Struktur `skills/` memungkinkan repo ini berkembang menjadi katalog skill dan preset motion yang dapat dipilih dari UI `npx skills`.

## Contoh penggunaan

```text
Gunakan MotionForge untuk membuat promo 30 detik untuk navernovel.my.id.
Gunakan palet charcoal dan cyan, tanpa voice-over, hanya backsound instrumental.
```

```text
Gunakan MotionForge untuk membuat explainer 45 detik dalam rasio 9:16.
Jangan membuatnya seperti slideshow; gunakan satu dunia visual dan camera movement.
```

```text
Gunakan MotionForge untuk membuat kinetic typography dari tagline brand saya.
```

## Prasyarat

Untuk menonton hasil:

- Browser modern
- Internet untuk CDN GSAP dan font, bila digunakan

Untuk verifikasi dan export opsional:

- Node.js + Puppeteer
- FFmpeg untuk export MP4

Output tetap harus dapat ditonton tanpa `npm install`.

## Lisensi

MotionForge menggunakan lisensi MIT. Lihat [LICENSE](LICENSE). Kredit kepada Bang Tutorial dan proyek asal Bang Motion dipertahankan sesuai lisensi.
