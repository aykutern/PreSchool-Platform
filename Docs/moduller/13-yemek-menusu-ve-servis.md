# 13 Yemek Menüsü ve Servis

Haftalık menü okul bazında yayınlanır ve çocuğun diyet kısıtlarıyla eşleştirilir; servis modülü biniş-iniş kayıtlarıyla veliye anlık bildirim verir, canlı konum ileri fazdadır.

## Amaç, kapsam ve aktörler

Modül haftalık yemek menüsünü okul bazında yayınlar ve çocuğun diyet kısıtlarıyla eşleştirir; servis tarafı güzergah, araç ve biniş-iniş kayıtlarıyla veliye anlık bilgi verir. Modül Faz 3'tedir; canlı konum ayrı bir aday olarak 14'te ele alınır.

**Kapsam içi**

- Haftalık menü: öğün bazında kalemler, alerjen etiketleri, yaş grubu varyantı (isteğe bağlı), şablon ve kopyalama, PDF.
- Diyet kısıtı eşleştirmesi: çocuğun alerji ve diyet bilgisiyle (03, 11) çakışan kalemlerin veli ve öğretmene işaretlenmesi.
- Servis: güzergahlar, duraklar, araç, hostes ataması, çocuk–güzergah ataması.
- Biniş-iniş kaydı (hostes, çevrimdışı çalışır) ve veli bildirimleri.
- Devamlılıkla entegrasyon (04): servise binmeyen çocuk için sorgu, servis iptali listesi.
- Akşam teslimde teslim yetkilisi kuralı (03).

**Kapsam dışı**

- Mutfak stoku, satın alma, yemek üretim planlaması.
- Servis ücretleri (14 Aidat).
- Canlı araç konumu (14 adayı).
- Araç bakım ve şoför özlük takibi.

**Aktörler**

| Aktör | Modüldeki işi |
| --- | --- |
| Ofis | Menüyü girer ve yayınlar, çocuk–güzergah atamasını yapar |
| Okul müdürü | Güzergah, araç ve hostesi tanımlar; raporları izler |
| Veli | Menüyü ve çakışmaları görür, servis bildirimlerini alır, servis iptali bildirir |
| Öğretmen | Yemek saatinde alerjen uyarı listesini görür |
| Servis hostesi | Biniş ve inişi işaretler, akşam teslimi kaydeder |
| Şoför | Hesabı yoktur; hostes kaydeder |

## Kullanıcı hikayeleri

| ID | Rol | Hikaye | Öncelik | Faz |
| --- | --- | --- | --- | --- |
| YS-01 | Ofis | Haftalık menüyü öğün bazında girip yayınlamak istiyorum, böylece veliler panoya bakmak zorunda kalmasın. | Must | Faz 3 |
| YS-02 | Veli | Bu haftanın menüsünü ve çocuğumun alerjisiyle çakışan kalemleri görmek istiyorum, böylece önlem alayım. | Must | Faz 3 |
| YS-03 | Öğretmen | Yemek saatinde alerjen uyarısı olan çocukları listede görmek istiyorum, böylece yanlış yemek verilmesin. | Must | Faz 3 |
| YS-04 | Ofis | Geçen haftanın menüsünü kopyalayıp düzenlemek istiyorum, böylece her hafta sıfırdan girmeyeyim. | Should | Faz 3 |
| YS-05 | Ofis | Menüyü PDF olarak indirmek istiyorum, böylece panoya da asabileyim. | Could | Faz 3 |
| YS-06 | Okul müdürü | Güzergahları, durakları, aracı ve hostesi tanımlamak istiyorum, böylece servis düzeni sistemde olsun. | Must | Faz 3 |
| YS-07 | Ofis | Çocuğu güzergaha ve durağa atamak istiyorum, böylece hostes listesi doğru olsun. | Must | Faz 3 |
| YS-08 | Servis hostesi | Çocuk bindiğinde ve okula indiğinde tek dokunuşla işaretlemek istiyorum, böylece veli anında bilsin. | Must | Faz 3 |
| YS-09 | Veli | Çocuğum servise bindiğinde ve okula ulaştığında bildirim almak istiyorum, böylece içim rahat olsun. | Must | Faz 3 |
| YS-10 | Veli | Yarın servis kullanmayacağımızı bildirmek istiyorum, böylece hostes boşuna beklemesin. | Should | Faz 3 |
| YS-11 | Servis hostesi | Akşam teslimde çocuğu kime verdiğimi kaydetmek istiyorum, böylece teslim kaydı olsun. | Must | Faz 3 |
| YS-12 | Okul müdürü | Servise binmeyen ama okula gelen veya gelmeyen çocuk tutarsızlıklarını görmek istiyorum, böylece açık kalmasın. | Should | Faz 3 |

## İş kuralları ve işlevsel gereksinimler

**Yemek menüsü**

1. Menü okul ve haftaya bağlıdır; öğünler okul ayarıdır (kahvaltı, öğle, ikindi); yaş grubu varyantı isteğe bağlıdır.
2. Her kalem alerjen etiketleri taşır (süt, yumurta, gluten, fındık ve fıstık, balık, soya, susam gibi); alerjen listesi marka düzeyinde tanımlanır ve güncel mevzuatla doğrulanır.
3. Yayınlanan menü velilere görünür; çocuğun diyet kısıtı veya alerjisiyle çakışan kalem velinin ekranında işaretlenir, öğretmene o gün sabah uyarı listesi gider.
4. Menü değişikliği “güncellendi” etiketiyle görünür; aynı gün değişikliğinde çakışma uyarısı yeniden hesaplanır.
5. Şablon ve kopyalama; PDF dışa aktarma.

**Servis**

6. Güzergah alanları: okul, ad, yön (sabah, akşam), duraklar (ad, sıra, tahmini saat), araç (plaka), hostes (kullanıcı), şoför (ad, telefon; hesap yok).
7. Çocuk ataması: güzergah, durak, yön, başlangıç ve bitiş tarihi; sabah ve akşam farklı olabilir.
8. Biniş-iniş: hostes listeden işaretler (bindi, binmedi, okula indi, eve teslim edildi ve kime); saat kendiliğinden; çevrimdışı çalışır. Her işaret veliye anlık bildirim üretir.
9. Sabah okula ulaşan çocuk yoklamada “servisle geldi” bilgisini taşır. Servise binmeyen çocuk için hostes “binmedi” işaretler; veliye sorgu gider (04 kuralıyla uyumlu, tek sorgu).
10. Veli servis iptali (gün veya aralık) bildirir; çocuk hostes listesinden düşer, iptal geçmişi tutulur.
11. Akşam teslim: teslim yetkilisi listesinden kişi seçilir (03); listede olmayan kişi için velinin tek seferlik onayı gerekir (03 kural 7).
12. Hostes güzergah gecikmesini tek dokunuşla bildirir; güzergahtaki velilere bildirim gider.
13. Canlı araç konumu bu modülde yoktur; 14'teki aday olarak ayrı karar gerektirir (GPS, pil, konum verisi KVKK).
14. Raporlar: güzergah doluluğu, biniş-iniş tutarsızlıkları (servise bindi ama yoklamada yok), zamanlama sapmaları.

## Veri, ekranlar ve bildirimler

**Varlıklar**

| Varlık | Anahtar alanlar | Not |
| --- | --- | --- |
| Menü | okul, hafta, durum, yayınlayan | Haftada bir |
| Menü kalemi | menü, gün, öğün, ad, alerjenler, yaş grubu varyantı | Alerjenler marka listesinden |
| Alerjen çakışması | kayıt, menü kalemi, tür | Hesaplanan, 03 ve 11'den |
| Güzergah | okul, ad, yön, araç, hostes, şoför | Araç plaka alanıdır; ayrı araç varlığı yok |
| Durak | güzergah, ad, sıra, tahmini saat | Sıralı |
| Güzergah ataması | kayıt, güzergah, durak, yön, başlangıç, bitiş | Sabah ve akşam ayrı olabilir |
| Biniş kaydı | atama, tarih, yön, durum, saat, teslim alan, hostes | Çevrimdışı kuyruklu |
| Servis iptali | kayıt, tarih aralığı, bildiren veli | Hostes listesinden düşürür |

**Ekranlar**

| Ekran | Platform | Rol | İçerik |
| --- | --- | --- | --- |
| Menü yönetimi | Web | Ofis | Hafta, öğünler, kalemler, alerjenler, kopyala, yayınla, PDF |
| Haftanın menüsü | Mobil | Veli, öğretmen | Gün ve öğün; çakışan kalem işareti |
| Alerjen uyarı listesi | Mobil | Öğretmen | Bugün çakışması olan çocuklar ve kalemler |
| Güzergah yönetimi | Web | Okul müdürü | Güzergah, duraklar, araç, hostes |
| Çocuk ataması | Web | Ofis | Güzergah ve durak seçimi, tarihler |
| Hostes listesi | Mobil | Servis hostesi | Durak sırasıyla çocuklar, bindi veya binmedi, okula indi, teslim |
| Servis durumu | Mobil | Veli | Bugünkü biniş-iniş durumu, tahmini saatler |
| Servis iptali | Mobil | Veli | Tarih veya aralık, neden |
| Servis raporları | Web | Okul müdürü | Doluluk, tutarsızlık, zamanlama |

**Bildirimler**

| Olay | Alıcı | Kanal | Zamanlama |
| --- | --- | --- | --- |
| Menü yayınlandı | Veliler | Haftalık özet | Pazartesi 08:00 (sessiz saat dışı) |
| Alerjen çakışması | Öğretmen, veli | Anlık bildirim | Sabah 08:00 |
| Servise bindi, okula ulaştı, eve teslim edildi | Veliler | Anlık bildirim | Anında |
| Servise binmedi | Veliler | Anlık bildirim, yanıt butonlu | Anında |
| Servis iptali | Hostes | Uygulama içi | Anında |
| Güzergah gecikmesi | Güzergah velileri | Anlık bildirim | Hostes bildirince |

## Uç durumlar, kabul kriterleri ve açık sorular

**Uç durumlar**

- Menü aynı gün değişti: çakışma yeniden hesaplanır, öğretmen ve ilgili veliler anında bildirim alır.
- Çocuğun diyet kısıtı girilmemiş: çakışma uyarısı üretilmez; ofis eksik profilleri listede görür.
- Hostes telefonu çevrimdışı: kayıtlar kuyruğa alınır, bağlantı gelince veli bildirimleri giriş saatiyle gider.
- Çocuk sabah servisle gelip akşam veliyle gidiyor: yön bazında atama; akşam listesinde yer almaz.
- Teslim yetkilisi listede yok: 03 kural 7; onay gelmezse çocuk okula geri getirilir ve ofis aranır (okul prosedürü).
- Hostes değişti veya izinli: müdür geçici hostes atar; eski hostesin listesi kapanır.
- Servis arızası: müdür güzergahı o gün iptal eder; velilere acil bildirim.
- Veliler canlı konum bekliyor: beklenti yönetimi için duyuru; karar 14'te.

**Kabul kriterleri**

- Alerjen çakışması veli ve öğretmen ekranında işaretlenir (otomatik test, 11 verisiyle).
- Servis iptali bildirilen çocuk hostes listesinde görünmez (otomatik test).
- Biniş bildirimi işaretten sonra p95 10 saniye içinde (Kesişen Konular NFR), en geç 1 dakikada veliye ulaşır; çevrimdışı kayıt bağlantıdan sonra 1 dakika içinde senkronlanır.
- Teslim yetkilisi dışındaki kişiye teslim, veli onayı olmadan kaydedilemez (otomatik test).
- Menü PDF'i 5 saniyede üretilir.

**Açık sorular**

- [ ] Her okulda servis hostesi var mı; yoksa şoför mi kaydedecek (hesap gerekir)?
- [ ] Canlı araç konumu ne zaman ve hangi yöntemle (araç cihazı veya hostes telefonu)?
- [ ] Menüde yaş grubu varyantı gerekli mi?
- [ ] Alerjen listesi standardı hangi mevzuata göre belirlenecek? (doğrulanmalı)
- [ ] Servis ücretleri aidat modülüne mi bağlı olacak?
