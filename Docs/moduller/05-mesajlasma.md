# 05 Mesajlaşma

Mesajlaşma çocuk bazlı veli–öğretmen kanalı, veli–okul ofisi kanalı ve iç yazışma kanalıyla sınırlıdır; veliler birbirine yazamaz, sessiz saat ve acil işareti kuralları geçerlidir.

## Amaç, kapsam ve aktörler

Modül veli ile okul arasındaki tüm yazışmayı uygulama içine taşır; kişisel telefon numarası paylaşımını ve WhatsApp gruplarını ortadan kaldırır. Her yazışma bir çocuğa veya bir okul birimine bağlıdır, kayıt altındadır ve okulun saat ve kanal kurallarına uyar.

**Kapsam içi**

- Üç kanal türü: çocuk kanalı (velileri ile sınıf öğretmenleri), ofis kanalı (veli ile okul ofisi ve yönetimi), iç kanal (öğretmen ile yönetim).
- Sınıf toplu mesajı: öğretmenden sınıfın tüm velilerine; yanıt isteğe bağlı, veliler birbirini görmez.
- Metin, fotoğraf ve belge ekleri; hazır yanıt şablonları; okundu bilgisi.
- Sessiz saatler, “acil” işareti ve mesai dışı otomatik yanıt.
- Yönetim görünürlüğü ve denetim: müdür okulundaki kanalları görüntüleyebilir (kullanıcılara bildirilir); ihtilafta dışa aktarma.
- Arama, arşiv ve saklama.

**Kapsam dışı**

- Veli–veli mesajlaşma ve grup sohbetleri (bilinçli olarak yok).
- Sesli ve görüntülü arama.
- Okul geneli duyurular (06 Duyurular).
- Otomatik çeviri.

**Aktörler**

| Aktör | Modüldeki işi |
| --- | --- |
| Veli | Çocuk kanalında öğretmene, ofis kanalında okula yazar; okundu bilgisini görür; acil işareti kullanır |
| Öğretmen / yardımcı öğretmen | Öğretmen çocuk kanallarını yanıtlar, sınıfa toplu mesaj gönderir, şablon kullanır; yardımcı öğretmen kanalları okur, okul ayarı açıksa yanıtlar (Roller ve Yetkiler, kural 5) |
| Ofis | Ofis kanalını yanıtlar, otomatik yanıtı tanımlar |
| Okul müdürü | Yanıtsız mesajları izler, ihtilafta kanalı inceler ve dışa aktarır, sessiz saatleri ayarlar |
| Marka yöneticisi | Yanıt süresi raporlarını görür; mesaj içeriğini görmez |

## Kullanıcı hikayeleri

| ID | Rol | Hikaye | Öncelik | Faz |
| --- | --- | --- | --- | --- |
| MS-01 | Veli | Çocuğumun öğretmenine uygulamadan yazmak istiyorum, böylece kişisel numarasını istemem gerekmesin. | Must | MVP |
| MS-02 | Veli | Mesajımın okunup okunmadığını görmek istiyorum, böylece tekrar yazıp yazmayacağımı bileyim. | Should | MVP |
| MS-03 | Veli | Ofise (kayıt, belge, sorular) ayrı bir kanaldan yazmak istiyorum, böylece öğretmeni meşgul etmeyeyim. | Must | MVP |
| MS-04 | Öğretmen | Sınıfımın tüm velilerine tek mesajla “yarın bot getirin” demek istiyorum, böylece 20 kişiye ayrı ayrı yazmayayım. | Must | MVP |
| MS-05 | Öğretmen | Sık yazdığım mesajları şablon olarak saklamak istiyorum, böylece hızlı yanıt vereyim. | Should | MVP |
| MS-06 | Öğretmen | Mesai dışında gelen mesajların bildirimi sabaha kalsın istiyorum, böylece akşam telefonum susmasın. | Must | MVP |
| MS-07 | Öğretmen | Yardımcı öğretmenimin de sınıf kanallarını görmesini istiyorum, böylece ben yokken yanıt verebilsin. | Should | MVP |
| MS-08 | Okul müdürü | Bir veli şikâyetinde yazışma geçmişini görmek istiyorum, böylece durumu belgeyle değerlendireyim. | Must | MVP |
| MS-09 | Okul müdürü | Okulumda yanıtsız kalan veli mesajlarını görmek istiyorum, böylece gecikmeleri önleyeyim. | Should | MVP |
| MS-10 | Veli | Acil bir durumda mesajımın sessiz saatte de öğretmene ulaşmasını istiyorum, böylece beklemeyeyim. | Should | MVP |
| MS-11 | Ofis | Mesai dışı gelen mesajlara otomatik yanıt tanımlamak istiyorum, böylece veli ne zaman dönüş alacağını bilsin. | Could | MVP |
| MS-12 | Veli | Yanlış gönderdiğim mesajı 5 dakika içinde geri almak istiyorum, böylece hatamı düzelteyim. | Should | MVP |
| MS-13 | Öğretmen | Veli mesajındaki belgeyi çocuğun dosyasına kaydetmek istiyorum, böylece rapor ve belgeler kaybolmasın. | Could | Faz 2 |
| MS-14 | Marka yöneticisi | Okullar arası yanıt süresi karşılaştırması görmek istiyorum, böylece iletişim kalitesini izleyeyim. | Should | MVP |

## İş kuralları ve işlevsel gereksinimler

**Kanallar**

1. Çocuk kanalı, çocuk aktif bir sınıfa atandığında kendiliğinden açılır. Üyeleri: çocuğun tam ve sınırlı yetkili velileri ile sınıfın sorumlu ve yardımcı öğretmenleri. Kısıtlı veli kanalda yer almaz.
2. Ofis kanalı veli hesabı ve okul başına birdir; üyeleri veli ile okulun ofis ve yönetici rolleri.
3. İç kanal okul başına bir personel kanalıdır (müdür, ofis ve öğretmenler; okul ayarıyla öğretmen başına müdür–öğretmen kanalı da açılabilir); veli görmez. Mesaj ve denetim kuralları aynıdır.
4. Sınıf toplu mesajını sınıfın sorumlu öğretmeni veya okul müdürü gönderir; her veliye ayrı kopya düşer, yanıt yalnızca gönderene gider. “Yanıt kapalı” seçeneği vardır.
5. Veli–veli mesaj yolu yoktur; sistem böyle bir kanal oluşturmaz.
6. Sınıf değişikliği, nakil veya yıl sonu devrinde eski kanal salt-okunur arşive geçer, yeni kanal yeni sınıfla açılır; veli arşiv kanalı okul ayarındaki arşiv görünürlük süresi boyunca (varsayılan bir sonraki eğitim yılının sonuna kadar) okuyabilir. Mezuniyet ve ayrılışta kanal 08 Mezuniyet kuralına göre kapanır.

**Mesaj kuralları**

7. İçerik: en çok 2.000 karakter metin; en çok 5 görsel veya belge, toplam 25 MB. Görseller cihazda sıkıştırılır, konum bilgisi (EXIF) silinir.
8. Okundu bilgisi kanal üyesi her kullanıcı için ayrıdır: veli öğretmenin okuduğunu, öğretmen hangi velinin okuduğunu görür.
9. Düzenleme gönderimden sonra 5 dakika içinde yapılabilir; silme “mesaj geri alındı” izi bırakır. Özgün metin mesaj deposunda sürüm olarak kalır (yumuşak silme); denetim kaydı yalnızca mesaj kimliğini ve işlemi tutar.
10. Şablonlar kişisel (öğretmen) ve okul geneli (müdür tanımlar) olabilir; değişkenler: çocuk adı, tarih.

**Sessiz saatler ve acil**

11. Sessiz saatler okul ayarıdır (varsayılan 18:00–08:00 ve hafta sonu). Bu saatlerde gönderilen mesaj iletilir, bildirimi sessiz saat bitince gider; gönderen bunu görür.
12. Veli “acil” işaretlerse mesaj anında bildirilir ve ofis kanalına kopyalanır. Kötüye kullanımda müdür o veli için acil hakkını kapatabilir.
13. Mesai dışı otomatik yanıt okul ayarıdır; her kanalda günde en çok bir kez gönderilir.

**Yönetim görünürlüğü ve denetim**

14. Okul müdürü okulundaki tüm kanalları okuyabilir; bu kural aydınlatma metninde ve kanal üst bilgisinde yazar. Marka yöneticisi yalnızca raporları görür, içeriği görmez (marka ayarıyla açılabilir).
15. Silinen ve düzenlenen mesajların özgün metni mesaj deposunda sürüm olarak saklanır; denetim kaydı içerik kopyalamaz. Saklama süresi Kesişen Konular'daki KVKK tablosundaki mesaj süresiyle aynıdır.
16. Dışa aktarma: müdür bir kanalı tarih aralığıyla PDF olarak alabilir; işlem denetim izine düşer.

**Yanıt süresi**

17. Çalışma saatleri içinde yanıtsız kalan veli mesajı 2 saat sonra öğretmene hatırlatılır, 4 saat sonra müdür panelinde listelenir. Eşikler okul ayarıdır.
18. Öğretmen de veliye ilk mesajı başlatabilir; kanal her zaman açıktır.

## Veri, ekranlar ve bildirimler

**Varlıklar**

| Varlık | Anahtar alanlar | Not |
| --- | --- | --- |
| Kanal | tür (çocuk / ofis / iç), okul, kayıt (çocuk kanalında), durum (açık / arşiv), oluşturma | Çocuk kanalı sınıf atamasıyla açılır |
| Kanal üyeliği | kanal, kullanıcı, rol, katılma, ayrılma | Öğretmen değişince güncellenir |
| Mesaj | kanal, gönderen, metin, ekler, acil mi, gönderim, düzenleme, geri alma | Sürümlü; özgün metin mesaj deposunda kalır |
| Okundu kaydı | mesaj, kullanıcı, zaman | Okuyan başına bir satır |
| Toplu mesaj | gönderen, sınıf, mesaj, yanıt açık mı, alıcı sayısı | Her veliye kopya |
| Şablon | sahip, kapsam (kişisel / okul), başlık, metin | Değişkenler: çocuk adı, tarih |
| Okul mesaj ayarı | sessiz saatler, otomatik yanıt metni, yanıt eşikleri, müdür görünürlüğü | 01 ayar katmanıyla yönetilir |

**Ekranlar**

| Ekran | Platform | Rol | İçerik |
| --- | --- | --- | --- |
| Mesajlar listesi | Mobil | Veli, öğretmen | Kanallar, okunmamış sayısı, son mesaj; veli çocuk başına kanal görür |
| Kanal görünümü | Mobil; web (ofis ve müdür için gelen kutusu) | Veli, öğretmen, ofis | Mesajlar, ekler, okundu bilgisi, acil işareti, sessiz saat uyarısı |
| Toplu mesaj gönder | Mobil | Öğretmen | Sınıf seç, metin, ek, yanıt açık/kapalı, zamanla |
| Şablonlar | Mobil; web (ofis) | Öğretmen, ofis | Liste, ekle, düzenle |
| Yanıtsız mesajlar paneli | Web | Okul müdürü | 2 ve 4 saat eşiğini aşan mesajlar, öğretmen bazında |
| Kanal inceleme ve dışa aktarma | Web | Okul müdürü | Kanal arama, tarih aralığı, PDF |
| Mesaj ayarları | Web | Okul müdürü | Sessiz saatler, otomatik yanıt, eşikler, acil hakkı |

**Bildirimler**

| Olay | Alıcı | Kanal | Zamanlama |
| --- | --- | --- | --- |
| Yeni mesaj | Kanal üyeleri | Anlık bildirim | Anında; sessiz saatte ertelenir |
| Acil mesaj | Sınıf öğretmenleri, ofis | Anlık bildirim, sessiz saati aşar | Anında |
| Toplu mesaj | Sınıf velileri | Anlık bildirim | Anında veya zamanlanmış |
| Yanıtsız 2 saat | Öğretmen | Uygulama içi | Eşikte |
| Yanıtsız 4 saat | Okul müdürü | Panel, e-posta | Eşikte |
| Kanal arşivlendi | Kanal üyeleri | Uygulama içi | Sınıf değişikliğinde |

## Uç durumlar, kabul kriterleri ve açık sorular

**Uç durumlar**

- Boşanmış veliler aynı çocuk kanalında: ikisi de yazar ve görür; biri kısıtlıysa kanalda değildir. İstenirse ofis, veli başına ayrı çocuk kanalı açabilir (okul ayarı).
- Öğretmen değişikliği: yeni öğretmen kanal geçmişini görür (okul ayarıyla kapatılabilir); eski öğretmen kanaldan çıkar.
- Öğretmen uzun izinde: müdür geçici öğretmeni kanala ekler; ayrılınca otomatik çıkar.
- Velinin iki okulda çocuğu: iki ayrı ofis kanalı, okul adıyla ayrışır.
- Mesajda sağlık bilgisi: mesaj saklanır; öğretmene “sağlık kaydına öneri gönder” kısayolu sunulur; öneri sağlık sorumlusu veya ofis doğrulayana kadar profile yazılmaz (11 Sağlık).
- Hakaret veya kötüye kullanım: müdür kanalı geçici olarak dondurabilir, veliye uyarı gider; işlem denetim izine düşer.
- Bildirim gelmeyen cihaz (izin kapalı): uygulama içi rozet ve günlük SMS özeti seçeneği (09 Bildirimler).

**Kabul kriterleri**

- Veli mesajı öğretmen cihazına çevrimiçiyken 5 saniye içinde ulaşır.
- Sessiz saatte gönderilen mesaj anında görünür, bildirimi sessiz saat bitiminde gider (test ortamında saat değiştirilerek doğrulanır).
- Veli–veli mesaj yolu yoktur: API, iki veli arasında kanal açma isteğini reddeder (otomatik test).
- Arşiv kanala yazılamaz; yazma isteği reddedilir.
- Müdür dışa aktarması denetim izinde kullanıcı, kanal ve tarih aralığıyla görünür.

**Açık sorular**

- [ ] Müdürün kanal görünürlüğü varsayılan açık mı? (Öneri: açık, aydınlatma metninde yazılı; S7)
- [ ] Sessiz saat aralığı ve hafta sonu kuralı markada standart mı?
- [ ] Acil işareti velide varsayılan açık mı, yoksa ofis mi açar?
- [ ] Yıl sonu arşivlenen kanalları veli ne kadar süre görebilsin? (Öneri: bir sonraki eğitim yılının sonuna kadar; okul ayarı, kural 6)
