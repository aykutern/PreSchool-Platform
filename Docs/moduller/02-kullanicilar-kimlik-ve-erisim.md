# 02 Kullanıcılar, Kimlik ve Erişim

Veliler telefon numarası ve SMS doğrulama koduyla, personel e-posta ve parolayla (yöneticilerde ek doğrulama ile) giriş yapar; hesaplar davetle açılır, erişim kapsamla sınırlanır.

## Amaç, kapsam ve aktörler

Modül platforma kimin, nasıl ve hangi kapsamla girdiğini belirler: veli hesapları telefon numarasına bağlıdır ve davetle açılır; personel hesapları e-posta ile açılır, yöneticilerde ek doğrulama zorunludur. Yetkinin ne olduğu Roller ve Yetkiler sekmesinde, burada hesabın yaşam döngüsü, kimlik doğrulama ve cihaz yönetimi anlatılır.

**Kapsam içi**

- Veli hesabı: SMS davet bağlantısı, telefon doğrulama (tek kullanımlık kod), profil, çocuk bağlantıları (03), tercihler.
- Personel hesabı: ofis veya müdür tarafından açma, e-posta doğrulama, parola politikası, yöneticilere çok faktörlü doğrulama (TOTP).
- Oturum yönetimi: kısa ömürlü erişim belirteci, yenileme belirteci, cihaz listesi, uzaktan çıkış.
- Rol ve kapsam ataması (marka, okul, sınıf) ve denetim izi.
- Hesap durumları: davet edildi, aktif, askıda, kapalı; personel ayrılışında kapatma.
- Telefon ve e-posta değişikliği, hesap kurtarma, kilitlenme.
- Çok rollü kullanıcı (öğretmen ve veli) ve mod geçişi.
- Güvenlik olayları: başarısız giriş serisi, yeni cihaz, kod kötüye kullanımı.

**Kapsam dışı**

- Sosyal giriş (Google, Apple); isteğe bağlı Faz 3.
- e-Devlet kimlik doğrulama.
- Kurumsal dizinle tek oturum açma (SSO); ileride marka İK sistemiyle değerlendirilir.

**Aktörler**

| Aktör | Modüldeki işi |
| --- | --- |
| Ofis | Veli daveti gönderir, kabul etmeyenleri izler, öğretmen hesabı açar |
| Okul müdürü | Personel rollerini atar, hesapları askıya alır veya kapatır |
| Marka yöneticisi | Yönetici hesaplarını ve güvenlik politikalarını yönetir, güvenlik olaylarını izler |
| Veli | Telefon ve kodla girer, cihazlarını ve tercihlerini yönetir |
| Personel | E-posta ve parolayla girer, yöneticiyse TOTP kullanır |
| Sistem | Kilitleme, belirteç yenileme, kapatma işlemlerini uygular |

## Kullanıcı hikayeleri

| ID | Rol | Hikaye | Öncelik | Faz |
| --- | --- | --- | --- | --- |
| KU-01 | Ofis | Kayıt anında veliye SMS daveti göndermek istiyorum, böylece veli uygulamayı indirip 2 dakikada girsin. | Must | MVP |
| KU-02 | Veli | Telefon numaram ve SMS koduyla, parola ezberlemeden giriş yapmak istiyorum, böylece giriş sorunu yaşamayayım. | Must | MVP |
| KU-03 | Veli | Yeni telefona geçtiğimde aynı numarayla girip eski cihazı düşürmek istiyorum, böylece hesabım açıkta kalmasın. | Must | MVP |
| KU-04 | Veli | Numaramı değiştirdiğimde hesabımı kaybetmeden yeni numaraya taşımak istiyorum, böylece geçmişim kalsın. | Should | MVP |
| KU-05 | Öğretmen | E-posta ve parolayla giriş yapmak, unuttuğumda parolamı sıfırlamak istiyorum, böylece ofise bağımlı olmayayım. | Must | MVP |
| KU-06 | Okul müdürü | Yönetici hesaplarında ek doğrulama zorunlu olsun istiyorum, böylece parola sızsa bile panel korunsun. | Must | MVP |
| KU-07 | Okul müdürü | Ayrılan personelin hesabını anında kapatıp oturumlarını düşürmek istiyorum, böylece veri erişimi kalmasın. | Must | MVP |
| KU-08 | Marka yöneticisi | Hangi kullanıcının hangi okul ve sınıfa erişimi olduğunu tek listede görmek istiyorum, böylece denetim yapabileyim. | Should | MVP |
| KU-09 | Öğretmen | Aynı okulda çocuğum varsa tek hesapla hem öğretmen hem veli olarak kullanmak istiyorum, böylece iki hesap taşımayayım. | Should | MVP |
| KU-10 | Veli | Hesabımın hangi cihazlarda açık olduğunu görüp kapatmak istiyorum, böylece kaybolan telefon risk olmasın. | Should | MVP |
| KU-11 | Marka yöneticisi | Şüpheli girişleri görmek ve hesabı geçici kilitlemek istiyorum, böylece saldırıları erken durdurayım. | Should | MVP |
| KU-12 | Veli | Uygulamayı parmak izi veya yüzle açmak istiyorum, böylece her seferinde kod beklemeyeyim. | Could | Faz 2 |
| KU-13 | Ofis | Kabul edilmeyen davetleri listeleyip yeniden göndermek istiyorum, böylece hiçbir veli dışarıda kalmasın. | Must | MVP |
| KU-14 | Veli | Bildirim, dil ve sessiz saat tercihlerimi yönetmek istiyorum, böylece uygulama beni rahatsız etmesin. | Should | MVP |

## İş kuralları ve işlevsel gereksinimler

**Veli hesabı**

1. Veli kimliği uluslararası biçimde (E.164) telefon numarasıdır; bir numara bir hesaptır. Davet SMS'i kayıt anında (03) veya ofis tarafından gönderilir; bağlantı 7 gün geçerlidir ve yeniden gönderilebilir.
2. Giriş: numara, 6 haneli tek kullanımlık kod (5 dakika geçerli), cihaz kaydı. Cihaz başına yenileme belirteci 90 gün (kullanımda uzar); erişim belirteci 15 dakika.
3. Kod sınırları: numara başına saatte 5 kod, cihaz başına saatte 10 deneme; aşımda 1 saat kilit ve güvenlik olayı. Kodlar tek kullanımlıktır.
4. Numara değişikliği: uygulama içinden yeni numaraya kod gönderilir. Eski numaraya ulaşılamıyorsa ofis yüz yüze kimlik doğrulamasıyla değiştirir ve işlem denetim izine yazılır (SIM değişimi riski).
5. Veli hesabı, bağlı çocuklarından en az birinin kaydı mezun veya ayrıldı dışında bir durumda (aday, kayıtlı, aktif, dondurulmuş) olduğu sürece aktiftir; son çocuk mezun olunca veya ayrılınca 08 kuralıyla kapanır.

**Personel hesabı**

6. Personel kimliği e-postadır; ofis veya müdür açar, davet e-postasıyla parola belirlenir. Parola en az 10 karakter, sızmış parola listesine karşı kontrol edilir; 5 başarısız denemede 15 dakika kilit.
7. Yönetici rollerinde (marka yöneticisi, okul müdürü, ofis) TOTP zorunludur; öğretmende isteğe bağlıdır. Web paneli oturumu 60 dakika hareketsizlikte düşer; hassas işlemlerde (KVKK talebi, dışa aktarma, rol değişikliği) yeniden doğrulama istenir.
8. Personel durumu: davet edildi, aktif, askıda (izin, soruşturma), kapalı (ayrılış). Kapatmada tüm oturumlar ve bildirim belirteçleri anında iptal edilir; sınıf atamaları kapanır (01).

**Rol ve kapsam**

9. Her kullanıcının bir veya daha fazla rol–kapsam çifti vardır: rol ile marka, okul veya sınıf. Yetki kuralları Roller ve Yetkiler'dedir; bu modül atamayı ve denetim izini tutar.
10. Çok rollü kullanıcı: aynı hesapta öğretmen ve veli rolleri; uygulama mod geçişi sunar, veri kapsamı moda göre süzülür. Öğretmen kendi çocuğunun sınıfında görevliyse o çocuğun değerlendirmesini müdür onaylar; bu, MVP'deki tek onay istisnasıdır, genel onay akışı Faz 2'dedir (07).

**Cihaz ve oturum**

11. Cihaz listesi: ad, platform, son kullanım; uzaktan çıkış o cihazın tüm belirteçlerini iptal eder.
12. Yeni cihazdan girişte kullanıcıya bildirim gider; “ben değilim” yanıtı hesabı kilitler ve ofise düşer.
13. Biyometrik kilit (Faz 2) cihazın yerel kilididir; sunucu kimliğini değiştirmez.

**Güvenlik olayları ve denetim**

14. Olaylar: başarısız giriş serisi, kod aşımı, yeni cihaz, rol değişikliği, hesap kapatma. Marka yöneticisi panelde görür; kritik olaylar e-postayla gider.
15. Tüm kimlik işlemleri denetim izine düşer (Kesişen Konular, denetim izi).

## Veri, ekranlar ve bildirimler

**Varlıklar**

| Varlık | Anahtar alanlar | Not |
| --- | --- | --- |
| Kullanıcı | marka, roller (veli ve/veya personel), telefon, e-posta, ad, durum, dil, oluşturma | Marka kapsamlı |
| Kimlik bilgisi | kullanıcı, parola özeti, TOTP sırrı, güncelleme | Yalnızca personel |
| Kod talebi | telefon, kod özeti, geçerlilik, deneme sayısı, cihaz | Sınırlar için sayılır |
| Davet | hedef, kanal, bağlantı belirteci, gönderim, kabul, geçerlilik | 7 gün |
| Rol ataması | kullanıcı, rol, kapsam türü, kapsam kimliği, başlangıç, bitiş, veren | Denetim izli |
| Cihaz | kullanıcı, platform, ad, bildirim belirteci, son kullanım | Bildirim belirteci 09'da kullanılır |
| Oturum | cihaz, yenileme belirteci özeti, oluşturma, bitiş, iptal | Yenileme belirteci 90 gün |
| Güvenlik olayı | kullanıcı, tür, zaman, cihaz, sonuç | Marka yöneticisi panelde görür |
| Tercih | kullanıcı, bildirim kanalları, dil, sessiz saat | 09 Bildirimler kullanır |

**Ekranlar**

| Ekran | Platform | Rol | İçerik |
| --- | --- | --- | --- |
| Giriş | Mobil | Veli | Numara, kod, cihaz adı |
| Davet kabul | Mobil | Veli | Bağlantıdan açılış, aydınlatma metni onayı, giriş |
| Profil ve tercihler | Mobil | Veli, personel | Ad, fotoğraf, dil, bildirim ve sessiz saat tercihleri |
| Cihazlarım | Mobil | Tüm kullanıcılar | Cihaz listesi, uzaktan çıkış |
| Mod geçişi | Mobil | Çok rollü kullanıcı | Üst barda Öğretmen / Veli |
| Personel girişi | Web, mobil | Personel | E-posta, parola, TOTP |
| Kullanıcı yönetimi | Web | Müdür, marka yöneticisi, ofis | Liste, rol ve kapsam, durum, davet yeniden gönder |
| Davet durumu | Web | Ofis | Kabul etmeyen veliler, hatırlatma |
| Güvenlik olayları | Web | Marka yöneticisi | Olay listesi, kilitle, kilidi aç |
| Parola sıfırlama | Web (e-posta bağlantısı) | Personel | Yeni parola, TOTP doğrulama |

**Bildirimler**

| Olay | Alıcı | Kanal | Zamanlama |
| --- | --- | --- | --- |
| Davet | Veli; personel | SMS; e-posta | Anında |
| Giriş kodu | Veli | SMS | Anında |
| Yeni cihazdan giriş | Kullanıcı | Anlık bildirim, SMS | Anında |
| Hesap kilitlendi | Kullanıcı, ofis | SMS, uygulama içi | Anında |
| Rol değişti | Kullanıcı | Uygulama içi | Anında |
| Davet kabul edilmedi | Ofis | Uygulama içi | 3 gün sonra |
| Hesap kapatıldı | Kullanıcı | E-posta veya SMS | Anında |

## Uç durumlar, kabul kriterleri ve açık sorular

**Uç durumlar**

- İki veli aynı telefonu kullanıyor: tek hesap, çocuklar bağlı; ikinci veli için ayrı numara önerilir, ofis bilgilendirir.
- Yurt dışı numara: desteklenir; SMS maliyeti yüksektir, e-posta kodu yedeği (Faz 2).
- SMS gelmiyor (operatör sorunu): ofis geçici giriş kodu üretir (15 dakika geçerli, denetim izine yazılır); sesli arama kodu Faz 2.
- Velinin telefonu çalındı: ofis hesabı kilitler; veli yeni cihazla kod alıp eski cihazı düşürür.
- Personel iki okulda görevli: tek hesap, iki rol–kapsam çifti; uygulamada okul seçici.
- Öğretmenin çocuğu kendi sınıfında: mod geçişi, değerlendirmede müdür onayı istisnası.
- Kullanıcıların tamamı yetişkindir; uygulama çocuk kullanıcı barındırmaz, mağaza yaş sınıflandırması ve gizlilik etiketleri buna göre doldurulur.

**Kabul kriterleri**

- Davetten ilk girişe kadar süre 2 dakikanın altındadır (5 veliyle saha testi).
- Kod SMS'i gönderimden sonra en geç 30 saniyede ulaşır (p95, test ortamı ölçümü).
- Kapatılan personel hesabı 60 saniye içinde tüm API çağrılarında reddedilir (otomatik test).
- Yönetici rolü TOTP olmadan web paneline giremez (otomatik test).
- Uzaktan çıkış 60 saniye içinde o cihazı düşürür.
- Kod sınırları aşıldığında API 429 döner ve güvenlik olayı yazılır (otomatik test).

**Açık sorular**

- [ ] SMS sağlayıcısı seçimi ve kod başına maliyet (Teknik Mimari, açık soru).
- [ ] Yönetici ek doğrulaması TOTP mi, SMS mi? (Öneri: TOTP)
- [ ] Veli için e-posta zorunlu mu? (Öneri: isteğe bağlı)
- [ ] Ofis geçici giriş kodu yetkisi kimde olsun?
- [ ] Mağaza yaş sınıfı ve gizlilik beyanları kim tarafından hazırlanacak?
