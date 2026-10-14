# Anaokulu Platformu

Bir markaya bağlı birden çok anaokulunu tek sistemde yöneten, mobil öncelikli platform. Veliler ve öğretmenler tek mobil uygulamayı (Veli ve Öğretmen modları) kullanır; okul yönetimi yalnızca web panelinden çalışır. Mezun olan veya ayrılan öğrencinin uygulamayla ilişkisi tanımlı bir süre sonunda biter.

**Durum:** analiz aşaması. Geliştirme henüz başlamadı; teknoloji seçimi öneri niteliğindedir ve [05-teknik-mimari.md](05-teknik-mimari.md) içinde alternatifleriyle tartışılmıştır.

## Analiz dokümanı

Dokümanın canlı ve düzenlenebilir sürümü Claude Doc olarak tutulur: <https://claude.ai/code/artifact/c0bdd837-2151-4ed3-8466-4b9645630531>

Bu klasör o dokümanın 14 Ekim 2026 tarihli Markdown dışa aktarımıdır. Açılır listeler (öncelik, faz, durum) düz metin olarak, çizimler PNG olarak aktarılmıştır. Değişiklik önce canlı dokümanda yapılır, sonra buraya yeniden aktarılır; iki kopya ayrıştığında canlı doküman esastır.

### İçindekiler

| Bölüm | Dosya |
| --- | --- |
| Genel bakış: yönetici özeti, hedefler, kapsam, paydaşlar, fazlama, kararlar | [00-genel-bakis.md](00-genel-bakis.md) |
| Roller ve yetkiler: rol tanımları, yetki matrisi, kapsam kuralları | [01-roller-ve-yetkiler.md](01-roller-ve-yetkiler.md) |
| Modüller: liste, fazlar, bağımlılıklar, sayfa yapısı | [02-moduller.md](02-moduller.md) |
| 01 Organizasyon ve Akademik Yapı | [moduller/01](moduller/01-organizasyon-ve-akademik-yapi.md) |
| 02 Kullanıcılar, Kimlik ve Erişim | [moduller/02](moduller/02-kullanicilar-kimlik-ve-erisim.md) |
| 03 Öğrenci Yönetimi ve Yaşam Döngüsü | [moduller/03](moduller/03-ogrenci-yonetimi-ve-yasam-dongusu.md) |
| 04 Devamlılık Takibi | [moduller/04](moduller/04-devamlilik-takibi.md) |
| 05 Mesajlaşma | [moduller/05](moduller/05-mesajlasma.md) |
| 06 Duyurular, Takvim ve Etkinlikler | [moduller/06](moduller/06-duyurular-takvim-ve-etkinlikler.md) |
| 07 Gelişim Takibi | [moduller/07](moduller/07-gelisim-takibi.md) |
| 08 Mezuniyet ve Ayrılış | [moduller/08](moduller/08-mezuniyet-ve-ayrilis.md) |
| 09 Bildirimler ve Raporlama | [moduller/09](moduller/09-bildirimler-ve-raporlama.md) |
| 10 Web Yönetim Paneli | [moduller/10](moduller/10-web-yonetim-paneli.md) |
| 11 Sağlık ve İlaç Takibi (Faz 2) | [moduller/11](moduller/11-saglik-ve-ilac-takibi.md) |
| 12 Günlük Rapor ve Medya Galerisi (Faz 3) | [moduller/12](moduller/12-gunluk-rapor-ve-medya-galerisi.md) |
| 13 Yemek Menüsü ve Servis (Faz 3) | [moduller/13](moduller/13-yemek-menusu-ve-servis.md) |
| 14 İleri Faz Modülleri (aday listesi) | [moduller/14](moduller/14-ileri-faz-modulleri.md) |
| Kesişen konular: çok kiracılı yapı, KVKK, güvenlik, çevrimdışı, performans, denetim izi | [03-kesisen-konular.md](03-kesisen-konular.md) |
| Veri modeli: varlıklar, ilişkiler, durum makineleri, Mermaid ERD | [04-veri-modeli.md](04-veri-modeli.md) |
| Teknik mimari: öneri, alternatifler, API, ortamlar, işletim | [05-teknik-mimari.md](05-teknik-mimari.md) |
| Yol haritası: fazlar, kapılar, MVP tanımı, kaba büyüklük | [06-yol-haritasi.md](06-yol-haritasi.md) |
| Riskler ve açık sorular (S1–S22) | [07-riskler-ve-acik-sorular.md](07-riskler-ve-acik-sorular.md) |
| Sözlük | [08-sozluk.md](08-sozluk.md) |

Çizimler `images/` altındadır ve ilgili sayfalara gömülüdür.

## Geliştirmeye başlamadan önce karar bekleyenler

Tam liste ve durumları için [07-riskler-ve-acik-sorular.md](07-riskler-ve-acik-sorular.md). Öne çıkanlar:

- Mezuniyet sonrası salt-okunur süre (öneri 30 gün, 0 gün seçilebilir) — S3
- MEB Okul Öncesi Eğitim Programı'nın hangi sürümünün esas alınacağı — S10
- Fotoğrafların ayrılış sonrası saklama süresi — S12
- Öğretmenlerin web paneline erişimi (Faz 2 adayı) — S16
- TC kimlik numarasının saklanıp saklanmayacağı — S18
- Sağlık verisinin KVKK dayanağı ve anlık bildirim (FCM) ile yurt dışı veri aktarımı; hukuk görüşü gerekir — S21, S22

Mevzuat ve müfredat ifadeleri dokümanda "doğrulanmalı / hukuk görüşü alınmalı" olarak işaretlidir; büyüklük ve süre tahminleri yaklaşıktır.

## Klasör yapısı

```
Docs/
  README.md        Bu dizin
  00–08 *.md       Genel bakış, roller, modüller, kesişen konular, veri modeli, mimari, yol haritası, riskler, sözlük
  moduller/        Modül sayfaları (01–14)
  images/          Çizimler (PNG)
```
