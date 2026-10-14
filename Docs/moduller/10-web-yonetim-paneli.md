# 10 Web Yönetim Paneli

Web paneli marka ve okul yöneticilerinin çalışma alanıdır: kurulum, kullanıcılar, öğrenciler, raporlar, ayarlar ve KVKK talepleri buradan yönetilir; veliler web paneline hiç girmez.

## Amaç, kapsam ve aktörler

Web paneli marka ve okul yöneticileri ile ofisin tek çalışma alanıdır: kurulum, kullanıcılar, öğrenciler, duyurular, raporlar, ayarlar, denetim izi ve KVKK talepleri burada yürütülür. Veliler web paneline hiç girmez; öğretmen Faz 2'de uzun rapor yazımı için girebilir. Bu sayfa panelin kabuğunu ve ortak işlevlerini tanımlar; modül ekranlarının kuralları ilgili modül sayfalarındadır.

**Kapsam içi**

- Panel kabuğu: okul seçici (marka yöneticisi), sol menü, genel arama (öğrenci, veli, personel), bildirim merkezi, yardım.
- Müdür ana sayfası: sabah paneli (09), bekleyen onaylar, uyarılar. Marka ana sayfası: okullar tablosu, metrikler, uyarılar.
- Modül ekranları: 01–09 ve 11–13'ün web ekranları (ilgili sekmelerde listelenir).
- Ortak işlevler: toplu içe aktarma (öğrenci, personel), dışa aktarma, filtreler ve kaydedilmiş görünümler (Faz 2), toplu işlemler.
- Ayarlar merkezi: marka ve okul ayarları (01), bildirim şablonları (09), aydınlatma ve rıza metinleri sürümleri, saklama politikası (08).
- Denetim izi görüntüleyici: kim, ne, ne zaman, hangi kayıt; filtre ve dışa aktarma.
- KVKK talepleri: erişim, düzeltme, silme, itiraz taleplerinin kaydı ve süre takibi.
- Yardım: ekran başına kısa kılavuz, sürüm notları.

**Kapsam dışı**

- Veli web erişimi (K5).
- Mobil uygulamanın webde çoğaltılması; öğretmen işleri mobildedir.
- Gelişmiş iş zekâsı panoları (Faz 3).

**Aktörler**

| Aktör | Modüldeki işi |
| --- | --- |
| Marka yöneticisi | Tüm okullar, standart ayarlar, metin sürümleri, saklama politikası, denetim izi |
| Okul müdürü | Okul operasyonu, onay kuyruğu, okul ayarları, raporlar |
| Ofis | Kayıt, davetler, içe aktarma, KVKK talep girişi, veli–ofis kanalı |
| Sağlık sorumlusu | 11 Sağlık web ekranları (Faz 2) |
| Öğretmen | İsteğe bağlı rapor yazımı (Faz 2) |
| Teknik destek | Faz 2 adayı: marka yöneticisinin sınırlı alt rolü (Roller ve Yetkiler, özel durumlar); MVP'de yoktur |

## Kullanıcı hikayeleri

| ID | Rol | Hikaye | Öncelik | Faz |
| --- | --- | --- | --- | --- |
| WP-01 | Okul müdürü | Sabah panele girdiğimde bekleyen işleri ve uyarıları tek ekranda görmek istiyorum, böylece güne nereden başlayacağımı bileyim. | Must | MVP |
| WP-02 | Marka yöneticisi | Okullar arasında tek tıkla geçmek ve her okulu aynı menüyle yönetmek istiyorum, böylece öğrenme maliyeti olmasın. | Must | MVP |
| WP-03 | Ofis | Öğrenci, veli veya personeli ada ya da telefona göre 2 saniyede bulmak istiyorum, böylece telefonda veliyi bekletmeyeyim. | Must | MVP |
| WP-04 | Ofis | Excel'den öğrenci ve veli listesi yükleyip hataları düzeltip aktarmak istiyorum, böylece ilk geçiş hızlı olsun. | Should | MVP |
| WP-05 | Okul müdürü | Bekleyen onayları (duyuru, rapor, nakil, veli kısıtlama) tek kuyruktan işlemek istiyorum, böylece hiçbiri unutulmasın. | Should | MVP |
| WP-06 | Marka yöneticisi | Aydınlatma ve rıza metinlerini sürümleyerek yayınlamak ve velilerin yeni sürümü görmesini ve gerekiyorsa yeniden rıza vermesini istemek istiyorum, böylece KVKK kayıtları güncel kalsın. | Must | MVP |
| WP-07 | Marka yöneticisi | Denetim izinde bir öğrencinin verisine kimin ne zaman baktığını görmek istiyorum, böylece şikâyetleri inceleyebileyim. | Must | MVP |
| WP-08 | Ofis | Bir velinin KVKK talebini kaydedip süresi içinde yanıtlandığını izlemek istiyorum, böylece yasal süre kaçmasın. | Should | MVP |
| WP-09 | Okul müdürü | Sık kullandığım filtreleri kaydedip hızlı erişmek istiyorum, böylece her seferinde ayarlamayayım. | Could | Faz 2 |
| WP-10 | Öğretmen | Uzun gelişim raporlarını bilgisayarda yazmak istiyorum, böylece telefonda uğraşmayayım. | Should | Faz 2 |
| WP-11 | Marka yöneticisi | Panelde yapılan her ayar değişikliğini kimin yaptığını ve eski değeri görmek istiyorum, böylece hatayı geri alabileyim. | Must | MVP |
| WP-12 | Ofis | Toplu işlemle bir sınıftaki tüm velilere daveti yeniden göndermek istiyorum, böylece tek tek uğraşmayayım. | Should | MVP |

## İş kuralları ve işlevsel gereksinimler

1. Panel yalnızca personel rolleriyle açılır; veli hesabının web girişi API düzeyinde reddedilir.
2. Yönetici rolleri TOTP ile girer (02). Oturum 60 dakika hareketsizlikte kapanır (02 kural 7); hassas işlemler (saklama politikası, rol atama, dışa aktarma) yeniden doğrulama ister.
3. Okul bağlamı: her ekran seçili okula göre süzülür. Marka yöneticisi okul seçiciyle geçer; “tüm okullar” görünümü yalnızca raporlarda ve listelerde vardır.
4. Genel arama: ad, soyad, telefonun son dört hanesi, e-posta; sonuçlar kapsama göre süzülür. Arama metni kaydedilmez, açılan kayıtlar denetim izine yazılır.
5. Toplu içe aktarma: şablon indirme, yükleme, doğrulama önizlemesi, hatalı satır raporu, kısmi aktarım; sonuç e-posta ile bildirilir.
6. Onay kuyruğu yalnızca başkasının başlattığı talepleri toplar: öğretmen duyurusu (06), gelişim raporu (07, Faz 2), ilaç talebi (11, Faz 2; sağlık sorumlusu yoksa), nakil kabulü (03), veli kısıtlama (03). Devir (01) müdürün kendi işlemidir, kuyruğa girmez. Her öğe kim ve ne zaman bilgisiyle listelenir; red veya geri gönderme nedeni zorunludur.
7. Ayar değişiklikleri kim, eski değer, yeni değer ve zaman bilgisiyle denetim izine düşer; kilitli ayarlar okul ekranında salt-okunurdur.
8. Metin sürümleri: aydınlatma metni, açık rıza metinleri ve izin formu şablonları sürümlenir. Aydınlatma metni onay değil bilgilendirme kaydıdır: yeni sürüm bir sonraki açılışta gösterilir, görüntülenen sürüm ve zaman kaydedilir. Açık rıza ayrı alınır; rıza vermeyen veli yalnızca rızaya bağlı özellikleri (fotoğraf, sağlık) kaybeder, yoklama, mesaj ve duyuru kapanmaz (hukuk görüşü alınmalı).
9. KVKK talepleri: tür (erişim, düzeltme, silme, itiraz), talep eden, çocuk, tarih, son tarih (yasal süre; doğrulanmalı), durum, yanıt belgesi. Son tarihe 5 gün kala uyarı gider.
10. Denetim izi okuma erişimlerini de kapsar (öğrenci kartı, sağlık, mesaj inceleme). Filtreler: kullanıcı, kayıt, işlem türü, tarih; CSV dışa aktarma; saklama süresi KVKK tablosuna göre.
11. Tarayıcı ve erişilebilirlik: Chrome, Edge, Safari ve Firefox'un son iki büyük sürümü; klavyeyle gezinme; 1280 piksel ve üzeri için tasarım, 1024'te çalışır.
12. Her ekranda kısa açıklama ve yardım bağlantısı; sürüm notları panelde yayınlanır.

## Veri, ekranlar ve bildirimler

**Varlıklar**

| Varlık | Anahtar alanlar | Not |
| --- | --- | --- |
| Panel tercihi | kullanıcı, varsayılan okul, kaydedilmiş filtreler | Faz 2 |
| Onay öğesi | tür, kaynak kayıt, durum, atanan, zaman, karar nedeni | Modüllerden beslenir |
| İçe aktarma işi | tür, dosya, satır sayısı, hata raporu, durum, yükleyen | Sonuç e-posta ile bildirilir |
| Metin sürümü | tür, sürüm, içerik, yayın tarihi, zorunlu onay | Aydınlatma, rıza, izin formu |
| Metin görüntüleme ve rıza kaydı | kullanıcı, sürüm, zaman, cihaz | KVKK kanıtı |
| KVKK talebi | tür, talep eden, çocuk, tarih, son tarih, durum, yanıt belgesi | Yasal süre doğrulanmalı |
| Denetim kaydı | kullanıcı, işlem, kayıt türü, kayıt kimliği, eski ve yeni değer, zaman, kaynak (web / mobil / sistem) | Kesişen Konular |

**Ekranlar**

| Ekran | Platform | Rol | İçerik |
| --- | --- | --- | --- |
| Müdür ana sayfası | Web | Okul müdürü | Sabah paneli, bekleyen onaylar, uyarılar, kısayollar |
| Marka ana sayfası | Web | Marka yöneticisi | Okullar tablosu, metrikler, uyarılar |
| Okul seçici ve menü | Web | Tüm panel rolleri | Okul bağlamı, modül menüsü |
| Genel arama | Web | Ofis, müdür, marka yöneticisi | Öğrenci, veli, personel sonuçları |
| Onay kuyruğu | Web | Okul müdürü | Bekleyen öğeler, onayla veya geri gönder |
| Toplu içe aktarma | Web | Ofis, müdür | Şablon, yükle, önizle, aktar, hata raporu |
| Ayarlar merkezi | Web | Marka yöneticisi, müdür | Katmanlı ayarlar, kilitler, değişiklik geçmişi |
| Metin sürümleri | Web | Marka yöneticisi | Aydınlatma, rıza, izin formu şablonları; yayınla |
| KVKK talepleri | Web | Ofis, müdür, marka yöneticisi | Talep listesi, süre, yanıt belgesi |
| Denetim izi | Web | Marka yöneticisi, müdür (okul) | Filtreli kayıt listesi, dışa aktarma |
| Yardım ve sürüm notları | Web | Tüm panel rolleri | Kılavuzlar, değişiklikler |

Modüllere özgü web ekranları (öğrenci kartı, yoklama paneli, duyuru yazma, raporlar) ilgili modül sayfalarında listelenmiştir.

**Bildirimler**

| Olay | Alıcı | Kanal | Zamanlama |
| --- | --- | --- | --- |
| Onay bekleyen öğe | İlgili yönetici | Uygulama içi, e-posta özeti | Anında; günlük özet |
| KVKK talebi son tarihi yaklaşıyor | Ofis, müdür | E-posta | 5 gün kala |
| İçe aktarma tamamlandı | Yükleyen | E-posta | İşlem sonunda |
| Yeni metin sürümü yayınlandı | Tüm veliler | Uygulama içi bilgilendirme ekranı | Sonraki açılışta |
| Hassas işlem yapıldı (dışa aktarma, politika değişimi) | Marka yöneticisi | E-posta | Anında |

## Uç durumlar, kabul kriterleri ve açık sorular

**Uç durumlar**

- Müdür iki okuldan sorumlu: okul seçici her iki okulu gösterir; raporlar okul bazında ayrışır.
- Marka yöneticisi okul işlemi yapıyor: işlem “marka düzeyinden” işaretlenir, okul müdürüne bilgi gider.
- Veli yeni aydınlatma metnini görüntülemeden geçemez (bilgilendirme kaydı); açık rızayı reddeden veli yalnızca rızaya bağlı özellikleri kaybeder, uygulama kapanmaz (kural 8; hukuk görüşü).
- İçe aktarmada mükerrer kayıt: 03 kural 19 uygulanır.
- Eski tarayıcı: uyarı şeridi, temel işlevler çalışır.
- Mezun çocuk için KVKK talebi: arşivden yanıtlanır; anonimleştirilmişse “veri yok” yanıtı belgelenir.
- Denetim izi büyüdü: 12 aydan eski kayıtlar soğuk depoya taşınır, sorgu yavaşlar ama kaybolmaz.

**Kabul kriterleri**

- Müdür ana sayfası 2 saniyede, genel arama 2 saniyede sonuç verir (1.200 öğrencilik veriyle).
- Veli hesabıyla web girişi reddedilir (otomatik test).
- Her ayar değişikliği denetim izinde eski ve yeni değerle görünür (otomatik test).
- Yeni metin sürümü yayınlanınca bilgilendirme ekranı bir sonraki açılışta çıkar; görüntüleme ve varsa rıza, sürüm numarasıyla kaydedilir.
- 500 satırlık içe aktarma 2 dakikadan kısa sürer ve hata raporu satır numarası verir.
- Yönetici rolleri TOTP olmadan panele giremez.

**Açık sorular**

- [ ] Öğretmen web erişimi MVP'de mi, Faz 2'de mi? (Öneri: Faz 2; S16)
- [ ] Teknik destek rolü gerekli mi; kapsamı ne olacak?
- [ ] KVKK talebi yanıt süresi ve iş akışı hukuk görüşüyle doğrulanmalı.
- [ ] Açık rıza vermeyen velide hangi özellikler kapanır? (Öneri: yalnızca fotoğraf ve sağlık; hukuk görüşü)
- [ ] Panel için ayrı alan adı ve marka görselliği kim tarafından hazırlanacak?
