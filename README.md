# VenomRP Kamu Hesaplayıcı

Bu dosya, proje kökündeki [`index.html`](./index.html) için ayrı bir açıklama dokümanıdır. Mevcut `README.md` dosyasını değiştirmez.

## Nedir?

`index.html`, VenomRP sunucusu için hazırlanmış tek dosyalık bir kamu cezası hesaplayıcısıdır. Harici kütüphane veya kurulum gerektirmez. Tarayıcıda açılarak doğrudan kullanılabilir.

## Özellikler

- Tek dosyada çalışır: HTML, CSS ve JavaScript aynı dosyadadır.
- Sunucu kuralları, DarkRP kuralları ve özel durumlar ayrı ayrı listelenir.
- Aşamalı cezalar butonlarla seçilir.
- Toplam warn sayısına göre ek ceza veya ek yaptırım hesaplanır.
- Jail, warn, blacklist, ban gibi kamu dışı sonuçlar ayrı gösterilir.
- `Cezadan Kaçmak` gibi sabit eklemeler doğrudan toplama eklenir.

## Kullanım

1. `index.html` dosyasını tarayıcıda aç.
2. İstersen üstteki arama alanından ihlal ara.
3. Gerekli ihlalleri `Ekle` veya aşama butonları ile listeye ekle.
4. Oyuncunun toplam warn sayısını gir.
5. Sağ taraftaki sonuç özetinden toplam kamu ve ek yaptırımları kontrol et.

## Hesap Mantığı

- En yüksek kamu cezası tam uygulanır.
- Diğer kamu cezaları yarım uygulanır ve yukarı yuvarlanır.
- Warn eşiği tek bant mantığıyla çalışır:
  - `5 warn` -> `+5 kamu`
  - `10 warn` -> `+15 kamu`
  - `15 warn` -> `+20 kamu`
  - `20 warn` -> `7 gün yasaklama` ve `warnlar silinir`
- `20 warn` durumunda alt warn ödülleri ayrıca eklenmez.
- Kamu dışı yaptırımlar yarım hesap kuralına girmez.

## Notlar

- Bu araç yerel kullanım için hazırlanmıştır.
- Kural listesi doğrudan dosyanın içindeki JavaScript veri yapısında tutulur.
- Yeni ihlal eklemek veya mevcut kamu miktarını değiştirmek için `index.html` içindeki kural tanımları düzenlenebilir.
