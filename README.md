# Sağlam Makina — Kurumsal Web Sitesi

Modern endüstriyel kurumsal site + mühendislik hesaplayıcısı.

**Canlı site:** https://omerbulbul91.github.io/saglam-makina-web/

## Sayfalar

| Sayfa | Açıklama |
|-------|----------|
| [index.html](index.html) | Ana sayfa — hero videosu, ürün grupları, sektörler, kurumsal, sürdürülebilirlik, haberler |
| [hesap.html](hesap.html) | Hasır Çelik Tel Panel Ağırlık Hesaplayıcı (Excel formülleriyle birebir) |

## Özellikler

- **Dark / Light tema** — sağ üstteki güneş/ay butonu, seçim tarayıcıda saklanır
- **3 dil:** Türkçe · English · العربية (Arapça'da otomatik RTL + Cairo fontu)
- **Hero arka plan videosu** — `prefers-reduced-motion` tercihinde fotoğrafa düşer
- **Pretext** ile dinamik metin yerleşimi — metinler resize'da yeniden akar
- Framework yok, derleme yok — saf HTML/CSS/JS, herhangi bir statik sunucuda çalışır

## Yerelde çalıştırma

```bash
npx http-server . -p 4173
# http://localhost:4173
```

## Yayınlama

Site GitHub Pages ile `main` branch'inden yayınlanır. `main`'e atılan her commit
1-2 dakika içinde otomatik olarak canlıya çıkar:

```bash
git add .
git commit -m "değişiklik açıklaması"
git push
```

Tasarım sistemi detayları için [DESIGN.md](DESIGN.md).
