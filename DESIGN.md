# Sağlam Makina — Tasarım Sistemi

Modern endüstriyel kurumsal dil. Keskin köşeler, hairline çizgiler, teknik mono etiketler, yüksek kontrast.

## Renkler

| Token | Değer | Kullanım |
|-------|-------|----------|
| `--ink` | `#0E1319` | Ana koyu zemin |
| `--steel` | `#161F2A` | Topbar, footer, hover zemin |
| `--steel-2` | `#1D2937` | Kurumsal bölüm zemini |
| `--paper` | `#F4F3EF` | Açık bölüm zemini (sektörler) |
| `--accent` | `#4360A9` | Logo ana rengi (kraliyet mavisi) — CTA, bantlar, buton zeminleri |
| `--accent-ink` | `#FFFFFF` | Mavi zemin üzeri metin |
| `--accent-text` | `#8FA3D9` koyu / `#34497C` açık tema | Metin/ikon vurguları — kicker, linkler, sayılar. Hero ve sürdürülebilirlik bandında her zaman `#8FA3D9` |
| `--blue` / `--blue-deep` | `#2E7CC3` / `#10395C` | Marka mavisinin modern tonu — sürdürülebilirlik gradyanı |
| `--text-on-dark` | `#E8EBEE` | Koyu zemin üzeri metin |
| `--muted-on-dark` | `#94A1AE` | Koyu zemin üzeri ikincil metin |

## Tipografi

- **Display (başlıklar):** Archivo 500–800 — büyük, sıkı letter-spacing (-0.015em)
- **Gövde:** Inter 400–600
- **Teknik/mono:** JetBrains Mono — kicker'lar, istatistik bandı, numaralar (01, S/01), tarihler

## Kurallar

- Border radius: 0 (keskin köşeler, endüstriyel dil)
- Çizgiler: 1px hairline — `rgba(255,255,255,.12)` koyu, `rgba(14,19,25,.14)` açık zemin
- Kicker deseni: 28px sarı çizgi + mono uppercase + .18em letter-spacing
- Numaralandırma: ürünler `01–06`, sektörler `S/01–S/05`
- İkonlar: lucide (CDN, `0.454.0` sürümüne sabitli — marka ikonları için), asla elle SVG yazma
- Metin yerleşimi: Pretext (`pretext-inline.js`) — `[data-pretext]` elemanları resize'da yeniden akar
- Scroll animasyonu yok (yazdırma/snapshot güvenilirliği için bilinçli karar)
- Dark mode: `prefers-color-scheme` ile açık bölümler koyulaşır

## Tema Sistemi

- Varsayılan **dark**; `#themeBtn` ile geçiş, `localStorage('sm-theme')` ile kalıcı.
- Token'lar `:root` (dark) ve `:root[data-theme="light"]` altında: `--bg`, `--bg-2`, `--bg-3`, `--text`, `--muted`, `--line`, `--header-bg`, `--logo-filter`.
- **Sabit kalan bölümler:** hero (fotoğraf + koyu overlay), statbar ve CTA (sarı), sürdürülebilirlik (mavi gradyan), sektörler (kontrast açık bölüm).
- Logo (`assets/logo.png`) koyu temada `brightness(0) invert(1)` filtresiyle beyazlatılır.

## Çok Dillilik (TR / EN / AR)

- `I18N` sözlüğü index.html içinde; elemanlar `data-i18n` (textContent) ve `data-i18n-html` (markup içeren) ile işaretli.
- Topbar'daki `.lang-switch` butonları; seçim `localStorage('sm-lang')` ile kalıcı.
- **Arapça:** `dir="rtl"` + Cairo fontu; letter-spacing sıfırlanır, yön ikonu SVG'leri `scaleX(-1)` ile çevrilir. Yön bağımlı CSS'te logical property (`padding-inline-start`, `inset-inline-end`, `border-inline-start`) kullanılır.
- Dil değişiminde `window.__pretextRefresh()` çağrılır — Pretext tüm metinleri yeniden ölçer.

## Görseller (assets/)

Kaynak: saglammakina.com (müşterinin kendi görselleri). `logo.png`, `faaliyet.jpg` (hero arka planı — otomotiv hattı), `sector-*.png` (sektör küçük görselleri), `hero.webp` (kurumsal bölüm — tel raf punta uygulaması), `uretim.jpg`, `kariyer.webp`, `haber-makine.png` (haber kartları).

## Breakpoint'ler

375px (mobil) / 768px (tablet) / 1100px (nav → hamburger) / 1440px (masaüstü)

## Sayfalar

- `index.html` — ana sayfa. Hero arka planında `assets/saglammakina.mp4` (autoplay/muted/loop, `prefers-reduced-motion`'da gizlenir, poster: faaliyet.jpg). Ortak stiller `styles.css`'te.
- `hesap.html` — Hasır Çelik Tel Panel Ağırlık Hesaplayıcı. Kaynak: `hasir_tel_agirlik_hesabi.xlsx` formülleri birebir JS'e taşındı (çelik yoğunluğu 7850 kg/m³, adet = ROUNDDOWN(uzunluk/göz)+1). TR/EN/AR + tema destekli; sayı biçimi `Intl.NumberFormat` ile yerel ayara göre.

## Önizleme

`.claude/launch.json` → `saglam-makina` (npx http-server, port 4173).
