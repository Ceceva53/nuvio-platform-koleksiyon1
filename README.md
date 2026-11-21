# Nuvio Türkçe – Stremio Eklentisi

Bu proje, Nuvio kaynaklarından seçilen beş sağlayıcıyı Stremio eklenti HTTP API'si üzerinden sunmak için hazırlanmış Node.js tabanlı bir uyarlama iskeletidir.

## Desteklenen sağlayıcılar

- HDFilmCehennemi
- FilmMakinesi
- FilmEkseni
- DiziBal
- DiziYou

## Gereksinimler

- Node.js 18 veya üzeri
- İnternetten erişilebilen bir sunucu (başka cihazlarda kullanmak için HTTPS önerilir)

## Yerel çalıştırma

Depo kök dizininde terminal açın ve çalıştırın:

```bash
npm start
```

Sunucu varsayılan olarak `7000` portunu kullanır. Ardından manifest adresi:

```text
http://localhost:7000/manifest.json
```

## Render üzerinde yayınlama

1. Bu depoyu GitHub'a yükleyin.
2. Render'da **New + → Blueprint** seçeneğini açın.
3. GitHub deponuzu bağlayın ve depodaki `render.yaml` dosyasını seçin.
4. `render.yaml`, depo kök dizinindeyse Render servisi otomatik yapılandırabilir. Dosyalar bir alt klasördeyse Render servisinin **Root Directory** alanını o klasöre ayarlayın.
5. Dağıtım tamamlandığında Render'ın verdiği alan adının sonuna `/manifest.json` ekleyin.

Örnek (gerçek adres Render tarafından verilir):

```text
https://SERVIS-ADIN.onrender.com/manifest.json
```

Bu adresi Stremio'da **Addons / Eklentiler → Install via URL** alanına ekleyin.

## API uç noktaları

- `/manifest.json` – Stremio eklenti manifest'i
- `/catalog/{type}/{id}.json` – Katalog sonuçları
- `/stream/{type}/{id}.json` – Yayın akışları

## Önemli uyumluluk notu

Bu proje, Nuvio sağlayıcılarını Stremio'nun katalog ve yayın yanıt biçimlerine uyarlamak için hazırlanmıştır. Nuvio ve Stremio veri modelleri birebir aynı değildir. Sağlayıcı sitelerinin erişilebilirliği, sayfa yapısı, anti-bot korumaları ve kaynakların döndürdüğü veri biçimleri nedeniyle canlı ortamda sağlayıcı bazında düzeltme gerekebilir. Yalnızca manifest dosyasını barındırmak yeterli değildir; Node.js sunucusunun çalışır durumda olması gerekir.

Dağıtımın başarılı olması, bütün katalogların veya yayın bağlantılarının çalıştığını tek başına garanti etmez. Lütfen yalnızca erişim ve kullanım hakkınız olan içerikleri kullanın.
