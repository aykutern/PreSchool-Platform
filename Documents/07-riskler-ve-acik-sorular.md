# Riskler ve Açık Sorular

En yüksek riskler veli benimsemesi, öğretmen iş yükü ve çocuk verisinin korunmasıdır; karar bekleyen sorular sahip ve durum sütunlarıyla izlenir.

## Riskler

Olasılık ve etki sütunları açılır listedir; her risk gözden geçirmesinde güncellenir. En yüksek üç risk veli benimsemesi, öğretmen iş yükü ve çocuk verisinin korunmasıdır.

| # | Risk | Olasılık | Etki | Önlem | Sahip |
| --- | --- | --- | --- | --- | --- |
| R1 | Veli benimsemesi düşük kalır; WhatsApp alışkanlığı sürer | Yüksek | Yüksek | Kayıtta hesap açma, paralel dönemden sonra WhatsApp kapanışı, veli videoları, aktivasyon raporu | Okul müdürü |
| R2 | Öğretmen iş yükü artar, girişler aksar | Orta | Yüksek | Toplu giriş, sınıf başına 10 dakika hedefi, şablonlar, çevrimdışı, pilotta süre ölçümü | Ürün sahibi |
| R3 | Çocuk verisi sızıntısı (fotoğraf, sağlık) | Düşük | Yüksek | Rıza modeli, rol bazlı erişim, imzalı bağlantılar, denetim izi, sızma testi, hukuk görüşü | Marka yöneticisi |
| R4 | Okullar arası veri karışması | Düşük | Yüksek | Her sorguda marka ve okul filtresi, satır düzeyi güvenlik, otomatik izolasyon testleri | Teknik lider |
| R5 | Kapsam genişlemesi; aidat ve günlük rapor MVP'ye sızar | Yüksek | Orta | Faz kapıları, değişiklik kurulu, MoSCoW tabloları | Ürün sahibi |
| R6 | SMS maliyeti ve teslim sorunları | Orta | Orta | Günlük üst sınır, anlık bildirim öncelikli, yedek sağlayıcı, maliyet raporu | Teknik lider |
| R7 | Mağaza onay gecikmeleri (Apple, Google) | Orta | Orta | Erken hesap açma, gizlilik beyanları, test sürümü planı | Mobil lider |
| R8 | Çevrimdışı senkron çakışmaları | Orta | Orta | Giriş zamanına göre son yazan kazanır, idempotency anahtarı, değişiklik geçmişi, pilotta saha testi | Mobil lider |
| R9 | Personel değişiminde erişim açık kalır | Orta | Yüksek | Hesap kapatma akışı, 60 saniyede iptal, aylık erişim denetimi | Okul müdürü |
| R10 | Velayet ihtilafında yanlış kişiye bilgi gider | Düşük | Yüksek | Kısıtlı veli düzeyi, teslim yetkilisi listesi, ofis prosedürü | Ofis |
| R11 | Yasal saklama süreleri belirsiz kalır | Orta | Orta | Hukuk görüşü Faz 0'da, ayarlanabilir politika, yasal bekletme | Hukuk danışmanı |
| R12 | Teknoloji seçimi ekip deneyimiyle uyuşmaz | Orta | Orta | Faz 0'da mimari deneme, ekip beceri envanteri | Teknik lider |
| R13 | Medya depolama maliyeti (Faz 3) | Orta | Düşük | Sıkıştırma, saklama süresi, soğuk depo | Teknik lider |
| R14 | Google servisleri olmayan cihazlarda bildirim ulaşmaz | Düşük | Orta | Gelen kutusu ve SMS özeti, pilotta cihaz dağılımı ölçümü | Mobil lider |
| R15 | Öğretmenlerin kişisel telefonlarında çocuk verisi (şifreli önbellek, yükleme kuyruğu, fotoğraflar) | Orta | Yüksek | Uygulama içi çekim galeriye yazmaz, hesap kapanışında yerel veri silinir, uzaktan çıkış; cihaz politikası (kurum cihazı veya mobil cihaz yönetimi) Faz 0'da karara bağlanır | Okul müdürü |

## Karar bekleyen sorular

Yirmi iki soru geliştirme başlamadan yanıt bekler; her satırda analizin önerdiği yanıt ve karar sahibi vardır, durum sütunu açılır listedir. Modüle özgü küçük sorular ilgili modül sayfalarının sonundaki listelerdedir.

| # | Soru | Önerilen yanıt | Karar sahibi | Durum |
| --- | --- | --- | --- | --- |
| S1 | Tek uygulama mı, veli ve öğretmen için iki ayrı uygulama mı? | Tek uygulama, iki mod | Proje sahibi | Açık |
| S2 | Veli kimliği telefon numarası ve SMS kodu mu olsun? | Evet; e-posta isteğe bağlı | Proje sahibi | Açık |
| S3 | Mezuniyet sonrası salt-okunur süre 30 gün mü? | 30 gün (marka ayarıyla 0–90 gün) | Proje sahibi | Açık |
| S4 | Veri sınıfı bazında saklama süreleri ne olacak? | Hukuk görüşü; yer tutucular KVKK tablosunda | Hukuk danışmanı | Açık |
| S5 | Barındırma Türkiye'de mi olacak? | Evet; yurt dışı seçeneği için hukuk görüşü | Proje sahibi, teknik lider | Açık |
| S6 | Teknoloji yığını (Flutter, Spring Boot, Vue 3, PostgreSQL) kabul mu? | Öneri kabul; Faz 0'da mimari deneme | Teknik lider | Açık |
| S7 | Müdürün mesaj kanallarını görmesi varsayılan açık mı? | Açık; aydınlatma metninde yazılı | Proje sahibi | Açık |
| S8 | Öğretmen duyuruları müdür onayı gerektirsin mi? | İlk dönem evet | Okul müdürleri | Açık |
| S9 | Yaş grupları ve doğum tarihi kesim tarihi? | Marka standardı, 30 Eylül | Eğitim koordinatörü | Açık |
| S10 | Gelişim göstergeleri hangi MEB program sürümüne göre ve kim tarafından hazırlanacak? | Güncel program; eğitim koordinatörü | Eğitim koordinatörü | Açık |
| S11 | Dönem sayısı ve rapor son tarihleri? | İki dönem; Ocak ve Haziran | Eğitim koordinatörü | Açık |
| S12 | Grup fotoğraflarında mezun çocuk politikası? | Salt-okunur süre bitiminde etiketler kaldırılır ve grup medyası diğer velilere kapanır; dosyalar 30 gün sonra silinir | Proje sahibi, hukuk danışmanı | Açık |
| S13 | SMS sağlayıcısı ve aylık bütçe? | Faz 0'da teklif alınır | Teknik lider | Açık |
| S14 | Pilot okul hangisi olacak? | Orta büyüklükte, istekli yönetim | Proje sahibi | Açık |
| S15 | Ürün adı ve marka görselliği? | – | Proje sahibi | Açık |
| S16 | Öğretmen web erişimi MVP'de mi? | Faz 2 | Proje sahibi | Açık |
| S17 | Sınıf kapasitesi engel mi, uyarı mı? | Uyarı | Okul müdürleri | Açık |
| S18 | T.C. kimlik numarası zorunlu mu? | MEB kayıt yükümlülüğü doğrulanmalı; zorunluysa şifreli ve yalnızca ofis görür, değilse isteğe bağlı | Proje sahibi, hukuk danışmanı | Açık |
| S19 | Dijital izin formu onayı hukuken yeterli mi? | Hukuk görüşü; gerekirse ıslak imza seçeneği | Hukuk danışmanı | Açık |
| S20 | Mevcut veri kaynakları (Excel, başka yazılım) neler, aktarım nasıl? | Faz 0'da envanter | Ofis | Açık |
| S21 | Sağlık ve alerji verisinin hukuki dayanağı ne; rıza vermeyen velinin çocuğu için alerji alanı açılabilir mi? | Hukuk görüşü; öneri: alerji ve diyet işareti çocuğun güvenliği için rıza dışı bir dayanakla tutulur, ayrıntılı profil açık rızayla | Hukuk danışmanı | Açık |
| S22 | FCM üzerinden giden bildirimler yurt dışına aktarım sayılıyor; hangi mekanizma uygulanacak? | Hukuk görüşü (standart sözleşme, Kurul bildirimi); olumsuzsa adsız bildirim şablonu ve içeriğin uygulama içinde yüklenmesi | Hukuk danışmanı, teknik lider | Açık |

## Varsayımlar

Analiz, aşağıdakileri doğrulanmamış varsayım olarak kabul etmiştir; biri yanlış çıkarsa ilgili modül ve faz planları güncellenir.

- Markanın bütün okulları aynı tüzel kişilik altındadır; veri sorumlusu tektir. Farklı tüzel kişilikler varsa KVKK rolleri (veri sorumlusu ve işleyen) ayrıca tanımlanır.
- Veliler akıllı telefon kullanır; kullanmayanlar için SMS özeti ve ikinci veli yeterlidir.
- Okulların internet bağlantısı vardır; çevrimdışı çalışma istisna durumlar içindir.
- Öğretmenler okulun verdiği veya kendi telefonlarını kullanır; cihaz politikası (kurum cihazı mı, kişisel mi) Faz 0'da netleşir; kişisel telefon kullanımı R15 ile izlenir.
- Ölçek: en çok 5 okul, okul başına 12 sınıf, sınıf başına 20 çocuk (K10); tasarım 10 katına göre yapılır.
- MEB raporlama yükümlülükleri mevcut yöntemlerle sürer; uygulama bunları ikame etmez, yalnızca dışa aktarımla destekler (doğrulanmalı).
- Geliştirme ekibi Spring Boot ve Vue deneyimine sahiptir; mobil için Flutter öğrenme süresi Faz 0'a dahildir.
- Aidat ve ödeme süreçleri MVP süresince mevcut muhasebe yöntemiyle yürür.
- Dokümandaki tüm süre, sayı ve maliyet ifadeleri yaklaşıktır; sipariş veya sözleşme dayanağı değildir.
