# Klaros — "Editöryel Mono" amiral teması

Blocofy platformu için ücretsiz amiral tema. Pure-Liquid — her section/block
kendi `{% schema %}` JSON bloğunu satır içinde taşır (Horizon/Shopify konvansiyonu).

## Tasarım dili — Editöryel Mono

- Kâğıt zemin (`#F6F3EC`), mürekkep metin (`#1B1A17`), kil aksan (`#B25334`).
- Başlıklar **Newsreader** serif, gövde **Inter**; bol boşluk ritmi; 0.5px hairline
  ayraçlar; düz yüzeyler — gradient/gölge/blur yok.
- Renkler platform color-scheme sistemine (`--color-*`) bağlıdır; `asset/theme.css`
  `:root`'ta editöryel paleti varsayılan tutar (scheme yokken editöryel görünür).
- Tema-özel ölçüler `--klaros-*` namespace'inde (font/genişlik/ritim/radius);
  `config/settings_schema.json` ayarları layout'ta `{{ settings.x }}` → `--klaros-*`
  olarak eşlenir.

## Yapı

```
asset/         # theme.css — Editöryel Mono tasarım sistemi (temanın ruhu)
block/         # Section blokları (card, faq-item, testimonial, …)
config/        # settings_schema.json — kapsamlı tema ayarları (Shopify modeli)
layout/        # theme.liquid — belge iskeleti + font/ayar eşlemesi
partial/       # header/footer + form parçaları
section/       # Sayfa section'ları (her biri {% schema %} taşır)
blueprint.json # Tema kurulunca üretilen dinamik içerik mimarisi (blog)
```

## Kullanım

Platform `pnpm pull-themes` bu repo'yu `.theme-cache/klaros/`'a klonlar ve dosya
içeriklerini `starter-themes.data.ts`'e gömer. `klaros` temasını seçen yeni
müşteriler kayıt anında kendi kopyalarını alır.

## Yazım kuralları

- Her `section/*.liquid` + `block/*.liquid` MUTLAKA `{% schema %}` bloğu taşımalı.
- Şema alan tipleri: platform repo'sunda `packages/cms/src/types/field.ts`.
- Renkler `var(--color-*)` ile (color-scheme devralınır); tema ölçüleri `--klaros-*`.
- Yapısal veri (schema.org / JSON-LD) platform varsayılanıdır;
  `partial/structured-data.liquid` bilinçli olarak boştur.
