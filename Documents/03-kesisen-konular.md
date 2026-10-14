# Kesişen Konular

Çok okullu veri izolasyonu, KVKK uyumu, güvenlik ve çevrimdışı çalışma her modülün ortak gereksinimidir; modül sayfaları bu sekmedeki ortak kurallara dayanır.

## Çok kiracılı yapı ve veri izolasyonu

Platform tek markaya aittir; yine de her kayıt marka ve okul kimliği taşır ve izolasyon bir uygulama alışkanlığı değil, veritabanı düzeyinde zorunluluktur.

1. Her iş tablosunda marka kimliği ve okula bağlı verilerde okul kimliği sütunu bulunur; birincil anahtarlar küresel benzersizdir (UUID), böylece okullar arası nakil kimlik çakışması yaratmaz.
2. Yetkilendirme iki katmanlıdır: servis katmanı rol–kapsam kontrolü yapar (birincil savunma); veritabanında satır düzeyi güvenlik (PostgreSQL RLS) oturumun marka ve okul bağlamına göre süzer ve okul düzeyinde ikinci savunma hattıdır. Veli–veli izolasyonu (“başka velinin çocuğu”) servis katmanının işidir; veliye açık tablolarda oturum kullanıcı kimliğine ve veli bağlantısına dayanan ek bir RLS politikası uygulanır. Uygulama kısıtları: bağlam her işlemde SET LOCAL ile verilir (bağlantı havuzu), politika bağlam yoksa reddeder (kapalı başarısızlık), uygulama veritabanı rolü tablo sahibi olamaz ve BYPASSRLS taşıyamaz, okullar arası servisler ayrı rolle çalışır.
3. Marka düzeyi veriler (yaş grupları, gösterge kataloğu, şablonlar, politikalar) okullara miras kalır; okul düzeyinde değer varsa onu geçersiz kılar (01 ayar katmanları).
4. Okullar arası işlemler (nakil, marka raporları) açık yetkiyle çalışan ayrı servisler üzerinden yapılır; olağan sorgular tek okul bağlamındadır.
5. Dosya depolamada nesne yolu marka, okul, yıl ve medya kimliğini taşır; çocuk bağı yalnızca medya etiketi kaydıyla kurulur (grup medyası ve nakil için); erişim imzalı ve süreli bağlantılarla verilir.
6. Her API uç noktası için “başka okulun kaydı” ve “başka velinin çocuğu” testleri zorunludur; bu testler tüm modüllerin kabul kriteridir.
7. İkinci marka eklemek yalnızca yönetim ekranı ve kullanıcı daveti işi olur; veri taşıma gerekmez. Markalar arası kullanıcı veya katalog paylaşımı yoktur (K1).

## KVKK ve çocuk verisi

Platform çocuklara ait kişisel veriyi ve velilerin iletişim verisini işler; sağlık, alerji ve özel gereksinim alanları 6698 sayılı Kişisel Verilerin Korunması Kanunu kapsamında özel nitelikli kişisel veridir. Bu bölüm tasarım ilkelerini verir; metinler, hukuki dayanaklar ve saklama süreleri hukuk danışmanıyla doğrulanmalıdır (K14). “Uygulamayla ilişkinin kalmaması” erişimin kapanması demektir; veri yasal süre boyunca kapalı tutulur, sonra anonimleştirilir (08).

**İlkeler**

- Veri sorumlusu markanın tüzel kişiliğidir (varsayım). SMS, bulut ve bildirim sağlayıcıları veri işleyendir ve sözleşmeyle bağlanır.
- Aydınlatma metni veli daveti kabulünde gösterilir; görüntülenen sürüm ve zaman kaydedilir (bilgilendirme kanıtı, onay değil); metin değişince yeni sürüm bir sonraki açılışta gösterilir. Açık rıza ayrı alınır (10).
- Açık rıza, dayanağın rıza olduğu işlemler için ayrı ayrı alınır: fotoğraf paylaşımı (üç kapsam), sağlık verisi işleme, iletişim tercihleri. Rıza her an geri alınabilir ve geri alma anında etkilidir. Sağlık ve alerji verisinin hukuki dayanağı (açık rıza mı, yaşamın korunması veya yasal yükümlülük mü) hukuk görüşüyle belirlenir; geri almanın işlevsel sonucu (alerji uyarısının kalıp kalmayacağı) okul politikasıdır (S21, doğrulanmalı). Rıza hizmetin ön koşulu yapılmaz; rıza vermeyen veli yalnızca rızaya bağlı özellikleri kaybeder (10).
- Veri minimizasyonu: kimlik numarası isteğe bağlı, adres yalnızca ofis için, sağlık ayrıntısı yalnızca ilgili roller için; öğretmen API'leri yalnızca güvenlik için gerekli sağlık işaretlerini (alerji, diyet, acil durum, günün ilaçları) döndürür; tanı, rapor ve ayrıntı dönmez.
- Amaçla sınırlılık: veriler yalnızca eğitim ve okul operasyonu için işlenir; mezun çocuk ve velisine pazarlama yapılmaz (K9).
- Çocuğun kendisi kullanıcı değildir; tüm işlemleri veli veya personel yapar.
- Veri sahibi hakları (erişim, düzeltme, silme, itiraz) web panelindeki talep akışıyla yasal süre içinde yanıtlanır (10).
- Veri işleme envanteri ve VERBİS kayıt yükümlülüğü eşiklere göre hukuk danışmanıyla değerlendirilir.
- Yurt dışına aktarım: barındırma Türkiye'de önerilir (K11). Yurt dışı sağlayıcı (örneğin bildirim servisi) kullanıldığında kanunun yurt dışı aktarım hükümleri (2024 değişikliği sonrası standart sözleşme ve Kurul'a bildirim gibi yollar) hukuk görüşüyle uygulanır (doğrulanmalı).
- Anlık bildirim metinlerinde çocuğun adı dışında hassas bilgi (sağlık, devamsızlık nedeni) bulunmaz; ayrıntı uygulama içinde görülür. Bildirim yükü FCM üzerinden (yurt dışı) geçtiği için ad içeren metinler yurt dışına aktarım sayılır; mekanizması hukuk görüşüyle belirlenir, görüş olumsuzsa metinler adsız şablona döner ve içerik uygulama açılınca sunucudan alınır (S22, doğrulanmalı).

**Veri sınıfları ve saklama** (süreler yer tutucudur; hukuk görüşüyle doldurulur ve 08'deki politika ekranından ayarlanır)

| Veri sınıfı | Örnek | Hassasiyet | Saklama (yer tutucu) | Süre sonu işlemi |
| --- | --- | --- | --- | --- |
| Kimlik ve kayıt | ad, doğum tarihi, veliler, sınıf geçmişi | Kişisel | Ayrılıştan sonra yasal süre (yer tutucu 2 yıl) | Anonimleştir |
| Devam kayıtları | yoklama, teslim | Kişisel | Eğitim yılı + yer tutucu 2 yıl | Anonimleştir |
| Gelişim raporları ve gözlem | değerlendirme, notlar | Kişisel | Ayrılıştan sonra yer tutucu 2 yıl | Anonimleştir |
| Mesajlar | kanal içerikleri, ekler | Kişisel | Ayrılıştan sonra yer tutucu 1 yıl | Sil |
| Fotoğraf ve medya | albüm, portfolyo | Kişisel, rızaya bağlı | Salt-okunur süre bitimi + 30 gün (etiketler süre bitiminde kaldırılır) | Sil |
| Sağlık ve özel gereksinim | alerji, ilaç, kaza, destek işareti | Özel nitelikli | Ayrılıştan sonra yer tutucu 1 yıl; kaza kayıtları yasal süre | Sil veya anonimleştir |
| Rıza ve onay kayıtları | rıza, metin onayları, izin formları | Kanıt | İşleme süresi + yasal zamanaşımı (yer tutucu 3 yıl) | Sil |
| Denetim izi | erişim ve işlem logları | Güvenlik | Yer tutucu 2 yıl | Sil |
| Kimlik doğrulama verisi | kod talepleri, oturumlar | Güvenlik | 90 gün | Sil |

**Uygulamadaki kontroller**: rıza ekranları (03), veri paketi ve anonimleştirme işi (08), KVKK talep akışı ve metin sürümleme (10), sağlayıcı sözleşme listesi (Faz 0 çıktısı), veri ihlali bildirim prosedürü (Güvenlik).

## Güvenlik

Güvenlik hedefi, çocuk verisi işleyen bir sistem için OWASP ASVS seviye 2'dir; kontroller aşağıda katman katman verilmiştir ve canlıya çıkmadan önce bağımsız sızma testiyle doğrulanır.

- **Kimlik**: veli için SMS kodu, personel için parola ve TOTP; kısa ömürlü erişim belirteci, cihaz listesi, uzaktan çıkış (02).
- **Yetki**: her istekte sunucu tarafı rol–kapsam kontrolü ve satır düzeyi güvenlik; her yetki reddi denetim izine yazılır.
- **Aktarım ve depolama**: TLS 1.2 ve üzeri; veritabanı, nesne depolama ve yedekler şifreli; kimlik numarası gibi alanlar uygulama düzeyinde ayrıca şifrelenir.
- **Medya**: özel depolama alanları, 15 dakikalık imzalı bağlantılar (yükleme başlarken alınır, süresi dolarsa yenilenir), EXIF temizleme, görüntünün yeniden kodlanması, boyut sınırları.
- **Uygulama**: girdi doğrulama, hız sınırlama (kod, giriş, mesaj gönderimi), bağımlılık taraması, sır yönetimi, CI'da statik analiz.
- **Mobil**: belirteçler cihazın güvenli deposunda. Ekran görüntüsünü engelleme güvenilir değildir ve vaat edilmez: Android'de kısmen mümkün, iOS'ta değil. Root ve jailbreak tespiti düşük değer taşıdığı için uygulanmaz.
- **İzleme ve olay yönetimi**: merkezi log, anomali uyarıları (başarısız giriş serisi, olağandışı dışa aktarma), olay müdahale planı, veri ihlali bildirim prosedürü (Kurul'a ve ilgililere bildirim süresi hukuk görüşüyle; doğrulanmalı).
- **Yedekleme ve kurtarma**: günlük tam yedek ve sürekli işlem günlüğü (PITR), 30 gün saklama, aylık geri yükleme tatbikatı; hedef RPO 15 dakika, RTO 4 saat. Silme ve anonimleştirme yedeklerde 30 günlük döngüyle tamamlanır; periyodik imha kaydı tutulur (hukuk görüşü).
- **Denetim**: canlı öncesi bağımsız sızma testi, yıllık tekrar; bulguların kritik olanları kapanmadan yayın yok.
- **Tedarikçiler**: SMS, bulut, bildirim ve e-posta sağlayıcılarıyla veri işleme sözleşmesi; erişim anahtarları en az yetkiyle ve dönemsel yenilemeyle.

## Çevrimdışı çalışma ve senkronizasyon

Çevrimdışı çalışma öğretmen modunun yoklama, teslim, gözlem notu, değerlendirme taslağı ve mesaj gönderme kuyruğu işlerini kapsar; veli modu çevrimiçi çalışır ve son görülen veriyi önbellekte tutar.

1. Yerel depo: cihazda şifreli SQLite; sınıf listesi, teslim yetkilileri, bugünkü yoklama ve gözlem önbelleği; medya yükleme kuyruğu.
2. Kuyruk: işlemler zaman damgasıyla kuyruğa alınır; bağlantı gelince sırayla gönderilir; başarısızlıkta üstel bekleme ile yeniden deneme.
3. Çakışma: alan bazında, sunucu saatine göre düzeltilmiş giriş zamanı en yeni olan kazanır (varış sırası değil); her işlem idempotency anahtarı taşır, önceki değer değişiklik geçmişinde kalır ve ilgili kullanıcılara bildirilir. Kilitli yoklama gününe çevrimdışı değişiklik reddedilir ve öğretmene gösterilir; ofis, gün boyu kesinti gibi durumlarda kilitli günü geç senkron için açabilir (04).
4. Zaman: cihaz saati yerine sunucu saatine göre düzeltilmiş zaman damgası kullanılır; giriş saati korunur, gönderim saati ayrıca tutulur.
5. Görünürlük: kullanıcı çevrimdışı olduğunu ve bekleyen işlem sayısını görür; 24 saatten eski bekleyen işlem uyarı verir.
6. Sınırlar: mesaj gönderimi çevrimdışı kuyruğa alınabilir, okundu bilgisi yalnızca çevrimiçi işlenir; medya yükleme Wi-Fi tercihli ayarı vardır.
7. Test: uçak modu senaryoları (yoklama ortasında bağlantı kopması, iki cihazdan aynı sınıf) pilot öncesi saha testinde zorunludur.

## Yerelleştirme, erişilebilirlik ve cihaz desteği

Arayüz Türkçedir ve Türkçe harf kurallarıyla çalışır; İngilizce altyapıda hazır ama içerik çevirisi kapsam dışıdır.

- **Dil**: tüm metinler kaynak dosyalarında (i18n); Türkçe varsayılan, kullanıcı dil tercihi (02); İngilizce ikinci dil olarak altyapıda.
- **Tarih, saat, sayı**: Türkçe biçim; saat dilimi Europe/Istanbul; eğitim yılı ve dönem adları Türkçe.
- **Türkçe karakter**: arama ve sıralama Türkçe harf kurallarına göre (İ ve ı, Ş, Ğ); SMS'te Türkçe karakter uzunluk etkisi gözetilir (09).
- **Erişilebilirlik**: WCAG 2.1 AA hedefi; dinamik yazı boyutu, yeterli kontrast, ekran okuyucu etiketleri, en az 44 piksel dokunma hedefi; anlam yalnızca renkle verilmez.
- **Mobil cihazlar**: iOS son iki büyük sürüm; Android 8.0 ve üzeri (pilotta cihaz dağılımı ölçülür); düşük bellekli cihazlarda medya sıkıştırma; tablet düzeni öğretmen modu için Faz 2.
- **Web**: Chrome, Edge, Safari, Firefox son iki sürüm; 1280 piksel tasarım, 1024'te çalışır.
- **İçerik dili**: veli kitlesinin çeşitliliği için sade cümleler, simge ile metin birlikte, kısa bildirim metinleri.

## Performans ve ölçek hedefleri

Ölçek varsayımı (K10): 5 okul, okul başına 12 sınıf, sınıf başına 20 çocuk; yaklaşık 1.200 öğrenci, 2.400 veli, 150 personel. Tasarım 10 katına (12.000 öğrenci) göre yapılır; günlük yük yaklaşık 1.200 yoklama kaydı, 3.000 mesaj ve 5.000 bildirimdir. Faz 3'te medya günde en çok 2.400 fotoğraf (sınıf başına 40 kota; yaklaşık 0,7 GB) ve yılda yaklaşık 150 GB depolama demektir; rakamlar yaklaşıktır.

| Alan | Hedef | Nasıl ölçülür |
| --- | --- | --- |
| API yanıt süresi | Okuma p95 300 ms, yazma p95 600 ms altında | Uygulama performans izleme |
| Mobil ana ekran açılışı | 4G'de 2 saniyenin altında | Mobil izleme |
| Anlık bildirim teslimi | p95 10 saniyenin altında | Teslim izleme (09) |
| Kullanılabilirlik | Aylık %99,5; okul saatlerinde (07:30–18:30) %99,9 hedefi | Çalışma süresi izleme |
| Eşzamanlı kullanıcı | Sabah 08:30–09:30 zirvesinde 1.000 eşzamanlı; 10 katına ölçeklenebilir | Yük testi |
| Rapor üretimi | Aylık raporlar 5 saniye, CSV 10 saniye altında | Otomatik test |
| Veri paketi | Talepten sonra 24 saat içinde | İş kuyruğu izleme |
| Yedek ve kurtarma | RPO 15 dakika (PITR), RTO 4 saat | Geri yükleme tatbikatı |
| Medya yükleme | 5 MB fotoğraf 4G'de 10 saniye altında, arka planda | Mobil izleme |
| Çevrimdışı senkron | Bağlantıdan sonra 1 dakika içinde | Saha testi |

## Denetim izi ve loglama

Denetim izi, çocuk verisine kimin ne zaman ve neden eriştiğini sorulabilir kılar; yazma işlemleriyle birlikte hassas okuma erişimlerini de kapsar.

- **Kapsam**: tüm yazma işlemleri (kim, ne, eski ve yeni değer); hassas okuma erişimleri (öğrenci kartı, sağlık, mesaj inceleme, arşiv); kimlik olayları; yetki reddi; dışa aktarma; politika ve ayar değişiklikleri.
- **Biçim**: yalnızca eklenen (append-only) kayıt; kullanıcı, zaman (UTC ve yerel), kaynak (web, mobil, sistem), kayıt türü ve kimliği, işlem, kısa özet.
- **Kişisel veri**: denetim kaydı içerik kopyalamaz ve ad tutmaz; yalnızca kullanıcı ve kayıt kimliklerini saklar, adlar gösterim anında çözülür. Böylece kişi kaydı anonimleşince denetim görünümü de anonimleşir; kayıt kendisi değişmez (yalnızca eklenen yapı korunur).
- **Erişim**: marka yöneticisi tümünü, müdür okul kapsamını görür; ofis görmez. Denetim izini görüntülemek de loglanır.
- **Saklama**: KVKK tablosundaki süre (yer tutucu 2 yıl); 12 aydan eski kayıtlar soğuk depoya taşınır.
- **Teknik loglar**: uygulama logları kişisel veri içermez (maskeleme); hata izleme aracı kişisel alanları süzer; teknik log saklama 90 gün (5651 sayılı Kanun'un trafik kaydı yükümlülüğü kapsamına girip girmediği hukuk görüşüyle doğrulanmalı).
- **Uyarılar**: olağandışı dışa aktarma, mesai dışı yönetici erişimi, toplu okuma marka yöneticisine bildirilir.
