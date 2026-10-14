# 09 Bildirimler ve Raporlama

Tüm modüller tek bildirim motorunu kullanır (anlık bildirim, uygulama içi, SMS yedeği, e-posta); raporlama devam, mesaj, duyuru ve gelişim metriklerini okul ve marka düzeyinde sunar.

## Amaç, kapsam ve aktörler

Modül iki ortak hizmeti toplar: tüm modüllerin kullandığı bildirim motoru (anlık bildirim, uygulama içi gelen kutusu, SMS yedeği, e-posta) ve yönetimin okul ile marka düzeyinde izlediği raporlar. Modüller olay üretir; bu modül kime, hangi kanaldan, ne zaman gideceğine karar verir ve iletimi izler.

**Kapsam içi**

- Olay kataloğu: her modülün olayları, varsayılan alıcı, kanal, öncelik, zamanlama (anında veya özet).
- Kanallar: anlık bildirim (FCM ile iOS ve Android), uygulama içi gelen kutusu ve rozetler, SMS (kritik ve yedek), e-posta (yönetici ve raporlar).
- Kullanıcı tercihleri: kanal, kişisel sessiz saat, özet saati; okul sessiz saatleriyle birleşim.
- Özetleme: günlük akşam özeti (gözlem notu, bilgi duyuruları), haftalık özet (plan).
- Teslim takibi: gönderildi, iletildi, açıldı; geçersiz cihaz belirteçlerinin temizlenmesi.
- Şablonlar: Türkçe (İngilizce altyapı), değişkenler, marka adı.
- Raporlar (MVP): günlük yoklama durumu, devam oranları, duyuru okunma, mesaj yanıt süresi, gelişim raporu tamamlanma, veli aktivasyonu, doluluk.
- Raporlar (Faz 2): dönem ve yıl trendleri, okullar arası karşılaştırma görselleri (yan yana tablo MVP'dedir), zamanlanmış e-posta raporları.

**Kapsam dışı**

- Pazarlama bildirimleri ve kampanyalar.
- Veli tarafında çocuklar arası karşılaştırma analitiği.
- İş zekâsı aracı entegrasyonu (Faz 3 adayı: veri ambarına dışa aktarım).

**Aktörler**

| Aktör | Modüldeki işi |
| --- | --- |
| Modüller (sistem) | Olay üretir |
| Veli ve personel | Alıcıdır; tercihlerini yönetir |
| Okul müdürü | Okul raporlarını ve sabah panelini izler |
| Marka yöneticisi | Olay kataloğunu ve şablonları düzenler, okullar arası raporları ve teslim kalitesini izler |
| Ofis | Uygulama kullanmayan veliler için SMS özetini açar |

## Kullanıcı hikayeleri

| ID | Rol | Hikaye | Öncelik | Faz |
| --- | --- | --- | --- | --- |
| BR-01 | Veli | Bana yalnızca önemli şeyler için bildirim gelsin, geri kalanı akşam özetinde toplansın istiyorum, böylece telefonum sürekli çalmasın. | Must | MVP |
| BR-02 | Veli | Bildirim izni kapalıysa bile uygulama içinde okunmamış rozetini görmek istiyorum, böylece hiçbir şeyi kaçırmayayım. | Must | MVP |
| BR-03 | Veli | Akıllı telefonu olmayan eşime kritik bilgiler SMS ile gitsin istiyorum, böylece o da haberdar olsun. | Should | MVP |
| BR-04 | Öğretmen | Mesai dışı bildirimler sabah gelsin istiyorum, böylece akşamım bölünmesin. | Must | MVP |
| BR-05 | Marka yöneticisi | Bildirim metinlerini markanın diliyle düzenlemek istiyorum, böylece iletişim tutarlı olsun. | Should | MVP |
| BR-06 | Okul müdürü | Sabah panelinde girilmemiş yoklama, yanıtsız mesaj ve okunmamış acil duyuru sayılarını tek ekranda görmek istiyorum. | Must | MVP |
| BR-07 | Okul müdürü | Aylık devam, duyuru okunma ve mesaj yanıt süresi raporunu PDF olarak almak istiyorum, böylece yönetim toplantısında kullanayım. | Should | MVP |
| BR-08 | Marka yöneticisi | Okulları aynı göstergelerle yan yana görmek istiyorum, böylece sapmayı erken fark edeyim. | Should | MVP |
| BR-09 | Marka yöneticisi | Her pazartesi haftalık özet raporu e-posta ile gelsin istiyorum, böylece panele girmeden izleyeyim. | Could | Faz 2 |
| BR-10 | Sistem | Geçersiz cihaz belirteçlerini temizlemek ve teslim oranını izlemek istiyorum, böylece bildirimler sessizce kaybolmasın. | Must | MVP |
| BR-11 | Okul müdürü | Veli aktivasyon oranını sınıf bazında görüp aktive olmayanları listelemek istiyorum, böylece ofis arayabilsin. | Must | MVP |
| BR-12 | Marka yöneticisi | Raporların ham verisini CSV olarak almak istiyorum, böylece kendi analizimi yapayım. | Should | MVP |

## İş kuralları ve işlevsel gereksinimler

**Olay ve yönlendirme**

1. Her modül olay yayınlar (örneğin “haber verilmemiş devamsızlık”). Olay kataloğu her olay için varsayılan alıcı kümesini, kanalı, önceliği (bilgi / önemli / acil) ve zamanlamayı (anında / özet) tanımlar; marka düzeyinde düzenlenir.
2. Alıcı kümesi her seferinde kapsam kurallarına göre çözülür (Roller ve Yetkiler); kısıtlı veli ve mezun kapsamı listelerden çıkar (08).
3. Öncelik davranışı: bilgi özetlenebilir ve sessiz saate uyar; önemli anında gider ve sessiz saate uyar; acil anında gider, sessiz saati aşar ve 5 dakika içinde açılmazsa SMS yedeği alır.

**Olay kataloğu (MVP)**

Katalog MVP olaylarını tek listede toplar; Faz 2 ve 3 modüllerinin olayları ilgili sayfalardaki Bildirimler tablolarında tanımlıdır ve aynı sütunlarla buraya eklenir. Öncelik sütunu sessiz saat ve SMS davranışını belirler (kural 3).

| Olay | Modül | Alıcı | Öncelik | Kanal | Zamanlama |
| --- | --- | --- | --- | --- | --- |
| Veli daveti | 02 | Veli | Önemli | SMS | Anında |
| Giriş kodu | 02 | Veli | Acil | SMS | Anında |
| Yeni cihazdan giriş | 02 | Kullanıcı | Önemli | Anlık bildirim, SMS | Anında |
| Hesap kilitlendi veya kapatıldı | 02 | Kullanıcı, ofis | Önemli | SMS, uygulama içi | Anında |
| Sınıf atandı veya değişti | 01, 03 | Veli, öğretmenler | Önemli | Anlık bildirim | Anında |
| Kayıt donduruldu veya açıldı | 03 | Veli, öğretmen | Önemli | Anlık bildirim | Anında |
| Veli yetkisi kısıtlandı | 03 | Okul müdürü (onay), tam yetkili veli | Önemli | Uygulama içi | Anında |
| Yoklama saati geçti, sınıf girilmedi | 04 | Öğretmen; 30 dk sonra müdür | Önemli | Anlık bildirim | Yoklama saatinde |
| Haber verilmemiş devamsızlık sorgusu | 04 | Tam ve sınırlı veliler | Önemli | Anlık bildirim; 60 dk yanıt yoksa SMS | Kesinleşmeden 15 dk sonra |
| Veliye ulaşılamadı | 04 | Ofis | Önemli | Uygulama içi | 60 dk sonra |
| Ardışık devamsızlık eşiği | 04 | Okul müdürü, ofis | Önemli | Uygulama içi, e-posta | Yoklama kesinleşince |
| Geç alma | 04 | Veli, ofis | Önemli | Anlık bildirim | Kapanış saatinde |
| Çocuk teslim edildi | 04 | Veli | Bilgi | Anlık bildirim (veli tercihi) | Teslim anında |
| Yeni mesaj | 05 | Kanal üyeleri | Önemli | Anlık bildirim | Anında; sessiz saatte ertelenir |
| Acil mesaj | 05 | Sınıf öğretmenleri, ofis | Acil | Anlık bildirim; 5 dk sonra SMS | Anında |
| Yanıtsız mesaj eşiği | 05 | Öğretmen; müdür | Bilgi | Uygulama içi; müdüre e-posta | 2 ve 4 saat |
| Yeni duyuru (bilgi) | 06 | Kapsamdaki veliler | Bilgi | Günlük özet | Özet saatinde |
| Yeni duyuru (önemli, acil) | 06 | Kapsamdaki veliler | Önemli / Acil | Anlık bildirim; acilde SMS yedeği | Yayın anında |
| Okudum hatırlatması | 06 | Onaylamayan veliler | Önemli | Anlık bildirim | 24 saat sonra |
| Rapor yayınlandı | 07 | Tam ve sınırlı veliler | Önemli | Anlık bildirim | Yayın anında |
| Gözlem notu paylaşıldı | 07 | Veli | Bilgi | Günlük özet | Özet saatinde |
| Rapor son tarihi yaklaşıyor | 07 | Öğretmen, müdür | Bilgi | Uygulama içi | 7 ve 1 gün önce |
| Mezuniyet veya ayrılış işlendi | 08 | Tam ve sınırlı veliler | Önemli | Anlık bildirim, SMS | İlk gün |
| Salt-okunur süre bitiyor | 08 | Veliler | Önemli | Anlık bildirim | 7 ve 1 gün önce |
| Veri paketi hazır | 08 | Talep eden veli | Önemli | Anlık bildirim, SMS, e-posta (varsa) | Hazır olunca |
| Erişim sona erdi | 08 | Veliler | Önemli | SMS | Süre bitişinde |
| Günlük özet | 09 | Veli | Bilgi | Anlık bildirim | Özet saati (varsayılan 17:30) |

**Kanallar ve yedekleme**

4. Birincil kanal anlık bildirimdir (FCM; iOS'ta APNs üzerinden). Cihazda izin yoksa veya belirteç geçersizse uygulama içi gelen kutusu yine yazılır.
5. SMS yedeği: acil öncelik (anlık bildirim 5 dakika içinde açılmazsa), giriş kodu ve davet, hesap yaşam döngüsü ve güvenlik olayları (02, 08), 04'teki devamsızlık sorgusu (60 dakika yanıt yoksa); “uygulama kullanmıyor” işaretli veliler için önemli olaylar (okul ayarı). Maliyet için okul başına günlük SMS üst sınırı vardır.
6. E-posta: personel davet ve parola, yönetici uyarıları, zamanlanmış raporlar; velilere e-posta yalnızca veri paketi gibi istisnalarda.

**Tercihler ve sessiz saatler**

7. Kullanıcı tercihi: kanal açık veya kapalı (acil hariç), kişisel sessiz saat, özet saati (varsayılan 17:30, sessiz saat başlamadan önce). Okul sessiz saati ile kişisel sessiz saat birleşir; geniş olan geçerlidir.
8. Günlük özet, bilgi öncelikli olayları tek bildirimde toplar (“Bugün: 2 gözlem notu, 1 duyuru”). Olay yoksa özet gönderilmez.

**Teslim ve kalite**

9. Her bildirim kaydı: olay, alıcı, kanal, gönderim, teslim, açılma. Üç başarısız teslimden sonra cihaz belirteci pasife alınır.
10. Aynı olay aynı alıcıya aynı kanaldan 5 dakika içinde tekrar gönderilmez.
11. Şablonlar değişken alır (çocuk adı, sınıf, tarih); SMS'te Türkçe karakter ve uzunluk sınırı gözetilir.
12. Tüm zamanlamalar Europe/Istanbul saat dilimindedir.

**Raporlar**

13. MVP rapor seti: günlük yoklama durumu; devam oranları (çocuk, sınıf, okul, marka; aylık); duyuru okunma ve onay; mesaj yanıt süresi ve eşik aşımları; gelişim raporu tamamlanma; veli aktivasyonu ve haftalık aktif veli; doluluk (kapasite ve kayıt); mezuniyet denetimi (08).
14. Her rapor okul ve marka düzeyinde süzülür; tarih aralığı ve dönem filtresi; CSV ve PDF dışa aktarma.
15. Raporlar gece toplanan özet tablolardan üretilir; günlük yoklama paneli ve sabah paneli anlıktır.
16. Faz 2: dönem ve yıl trendleri, okullar arası karşılaştırma görselleri, zamanlanmış e-posta raporları, öğretmen bazında operasyonel etkinlik (gözlem notu sayısı, yanıt süresi). Bu veriler performans değerlendirmesi için değil, operasyon takibi içindir (açık soru).

## Veri, ekranlar ve bildirimler

**Varlıklar**

| Varlık | Anahtar alanlar | Not |
| --- | --- | --- |
| Olay | tür, kaynak modül, kapsam, veri, zaman | Modüller üretir |
| Olay kuralı | olay türü, alıcı kümesi, kanal, öncelik, zamanlama | Marka düzeyinde |
| Bildirim | olay, alıcı, kanal, şablon, durum, gönderim, teslim, açılma | Teslim takibi |
| Şablon | olay türü, dil, başlık, metin, değişkenler | Türkçe; İngilizce altyapı |
| Özet kuyruğu | alıcı, biriken olaylar, planlanan saat | Günlük ve haftalık |
| Rapor özeti | rapor türü, kapsam, tarih, değerler | Gece işiyle dolar |
| Rapor dışa aktarma | rapor, kullanıcı, filtre, dosya, zaman | Denetim izli |
| Cihaz belirteci ve tercih | cihaz, bildirim belirteci, kanal tercihleri, sessiz saat, özet saati | 02 Kullanıcılar'da tanımlı |

**Ekranlar**

| Ekran | Platform | Rol | İçerik |
| --- | --- | --- | --- |
| Gelen kutusu | Mobil | Veli, personel | Bildirim listesi, okunmamış, ilgili kayda geçiş |
| Bildirim tercihleri | Mobil | Veli, personel | Kanallar, sessiz saat, özet saati |
| Sabah paneli | Web, mobil özet | Okul müdürü | Girilmemiş yoklama, yanıtsız mesaj, acil duyuru okunmamış, bekleyen onay |
| Raporlar | Web | Müdür, marka yöneticisi | Rapor listesi, filtreler, dışa aktarma |
| Okullar arası karşılaştırma | Web | Marka yöneticisi | Aynı metriklerle okullar tablosu (MVP); trend görselleri (Faz 2) |
| Olay kataloğu ve şablonlar | Web | Marka yöneticisi | Olay listesi, kanal ve öncelik, şablon düzenleme |
| Teslim izleme | Web | Marka yöneticisi | Teslim oranı, başarısız belirteçler, SMS kullanımı ve maliyet |

**Sistem bildirimleri**

| Olay | Alıcı | Kanal | Zamanlama |
| --- | --- | --- | --- |
| Teslim oranı %90'ın altına düştü | Marka yöneticisi | E-posta | Günlük kontrol |
| SMS günlük sınırı aşıldı | Marka yöneticisi, okul müdürü | E-posta | Anında |
| Zamanlanmış rapor hazır | Abone yöneticiler | E-posta | Planlanan saatte (Faz 2) |
| Gece toplama işi başarısız | Teknik ekip | E-posta, izleme aracı | Anında |

## Uç durumlar, kabul kriterleri ve açık sorular

**Uç durumlar**

- Cihazda bildirim izni kapalı: gelen kutusu ve rozet çalışır; uygulama ayda bir izin hatırlatır.
- Velinin iki telefonu: bildirim her cihaza gider; açılma bir cihazda olunca diğerinde okundu sayılır.
- Özet saati sessiz saatin içinde (kişisel tercih): özet sessiz saat bitiminde gönderilir; varsayılan 17:30 sessiz saatin dışındadır.
- Acil olayda SMS yedeği: anlık bildirim 5 dakika içinde açılmazsa SMS gider; açıldıysa gitmez.
- Alıcı hesabı kapanmış: bildirim üretilmez, olay kaydı kalır.
- Okul kapatıldı: tarihsel raporlar marka düzeyinde okunur.
- Huawei gibi Google servisleri olmayan cihazlar: anlık bildirim ulaşmaz; uygulama içi gelen kutusu ve SMS özeti devreye girer (açık soru).

**Kabul kriterleri**

- Anlık bildirim teslim süresi p95 10 saniyenin altındadır (test ortamı ölçümü).
- Günlük özet tek bildirim olarak gider; içinde bilgi olayları sayısıyla listelenir.
- Acil olay sessiz saatte 1 dakika içinde ulaşır; bilgi olayı sessiz saatte bekler (zaman ilerletmeli test).
- Aynı olay aynı alıcıya 5 dakika içinde ikinci kez gitmez (otomatik test).
- 1.200 öğrencilik marka için aylık raporlar 5 saniyede üretilir ve CSV ile PDF olarak indirilir.
- Teslim izleme ekranı başarısız belirteçleri ve SMS kullanımını günlük gösterir.

**Açık sorular**

- [ ] Okul başına günlük SMS üst sınırı ve aylık bütçe? (S13)
- [ ] “Uygulama kullanmıyor” velilere SMS özeti hangi olayları kapsasın?
- [ ] Öğretmen bazında etkinlik raporu (Faz 2) performans algısı yaratabilir; öğretmen temsilcisiyle konuşulmalı.
- [ ] Hangi raporlar müdürün mobil özetinde yer alsın?
- [ ] Google servisleri olmayan Android cihazlar için ayrı bildirim altyapısı gerekli mi? (Veli cihaz dağılımı pilotta ölçülür)
