# Roller ve Yetkiler

Yetki, rol ile kapsamın (marka, okul, sınıf, güzergah, çocuk) birleşiminden doğar; her kullanıcı yalnızca kendi kapsamındaki veriyi görür ve değiştirir.

## Rol tanımları

Sekiz rol ve bir sistem aktörü vardır; her rol bir kapsam düzeyine bağlanır (marka, okul, sınıf, güzergah (Faz 3), çocuk) ve bir kullanıcı birden çok rol taşıyabilir. Veli rolü üç yetki düzeyine ayrılır.

| Rol | Kapsam düzeyi | Platform | Görevi | Kim olur |
| --- | --- | --- | --- | --- |
| Marka yöneticisi | Marka | Web, mobilde özet | Okullar, standartlar, politikalar, okullar arası raporlar | Kurucu, genel müdür, marka koordinatörü |
| Okul müdürü | Okul | Web, mobil | Okulun tüm operasyonu, onaylar, okul raporları | Müdür, müdür yardımcısı |
| Ofis | Okul | Web | Kayıt, veli davetleri, belgeler, yoklama düzeltme, veli–ofis kanalı | Sekreter, kayıt sorumlusu |
| Öğretmen | Sınıf(lar) | Mobil; web (Faz 2, S16) | Yoklama, gözlem, rapor, mesaj, sınıf duyurusu | Sınıf öğretmeni |
| Yardımcı öğretmen | Sınıf(lar) | Mobil | Yoklama ve teslim, gözlem notu, kanal okuma (yazma okul ayarı) | Yardımcı öğretmen, stajyer (kısıtlı alt tür) |
| Sağlık sorumlusu | Okul | Mobil, web | Sağlık profili, ilaç onayı, kaza kaydı (Faz 2) | Hemşire |
| Servis hostesi | Güzergah | Mobil | Biniş ve iniş kaydı (Faz 3) | Hostes |
| Veli, tam yetkili | Çocuk | Mobil | Her şeyi görür, rıza verir, teslim alır, mesaj yazar | Anne, baba, yasal vasi |
| Veli, sınırlı | Çocuk | Mobil | Görür ve mesaj yazar; rıza veremez | Büyükanne, büyükbaba, bakıcı (aile kararıyla) |
| Veli, kısıtlı | Çocuk | Mobil | Yalnızca ofisin açtığı başlıkları görür | Mahkeme kararı gibi durumlar |
| Sistem | – | – | Zamanlanmış işler: kilitleme, süre bitimleri, anonimleştirme | – |

## Yetki matrisi

Y = yapar, G = yalnızca görür, O = onaylar, – = erişimi yok. Parantez içi kapsamı veya ayarı belirtir. Sağlık sorumlusu ve servis hostesi yalnızca kendi modüllerinde yer aldığı için burada gösterilmez (11, 13). Kısıtlı veli sütunu yoktur: kısıtlı veli yalnızca ofisin tek tek açtığı başlıkları görür (03, kural 6).

**Mobil ve sınıf işlemleri**

| İşlem | Marka yön. | Müdür | Ofis | Öğretmen | Yrd. öğr. | Veli tam | Veli sınırlı |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Sınıf listesi ve çocuk profili (öğretmen görünümü) | G | G | G | G (kendi sınıfı) | G (kendi sınıfı) | – | – |
| Çocuğum profili (veli görünümü) | – | – | – | – | – | Y | G |
| Yoklama alma | – | G | Y (düzeltme) | Y | Y | – | – |
| Devamsızlık bildirme | – | – | Y (veli adına) | – | – | Y | Y |
| Teslim kaydı | – | – | – | Y | Y | – | – |
| Çocuk kanalı (mesaj) | G (marka ayarı) | G | – | Y | G / Y (okul ayarı) | Y | Y |
| Ofis kanalı (mesaj) | – | Y | Y | – | – | Y | Y |
| Sınıf toplu mesajı | – | Y | – | Y | – | G | G |
| Duyuru yazma | Y (marka) | Y (okul) | Y (okul) | Y (sınıf, onay ayarı) | – | – | – |
| Duyuru okuma ve okudum onayı | G | G | G | G | G | Y | Y |
| Gözlem notu | – | G | – | Y | Y | G (paylaşılanlar) | G (paylaşılanlar) |
| Gelişim raporu yazma ve yayınlama | – | O (Faz 2) | – | Y | – | – | – |
| Gelişim raporu okuma ve indirme | G | G | – | G | – | Y | G |
| Rıza verme ve değiştirme | – | – | Y (kâğıt form girişi) | – | – | Y | – |
| Teslim yetkilisi ekleme | – | – | Y | – | – | Y | – |
| İzin formu onayı (Faz 2) | – | – | G | G | – | Y | – |
| Sağlık profili (Faz 2) | – | G | G | G (alerji özeti) | G (alerji rozeti) | Y | G |
| İlaç talebi ve uygulama (Faz 2) | – | O | G | Y (uygulama kaydı) | – | Y (talep) | – |

**Yönetim işlemleri (web)**

| İşlem | Marka yön. | Müdür | Ofis |
| --- | --- | --- | --- |
| Okul ekleme ve kapatma | Y (kapatma Faz 2) | – | – |
| Yaş grubu, standart ayarlar, kilitler | Y | G | – |
| Okul ayarları (kilitsiz olanlar) | Y | Y | – |
| Eğitim yılı, sınıf, öğretmen atama | G | Y | G |
| Yıl sonu devir | G | Y | Y (önizleme, onay müdürde) |
| Öğrenci kaydı, veli bağlantısı, toplu içe aktarma | G | Y | Y |
| Nakil (marka içi) | Y | Y (kaynak ve hedef onayı) | – |
| Mezuniyet ve ayrılış | G | Y | Y (ayrılış kaydı) |
| Veli yetkisini kısıtlama (mahkeme kararı) | G | O | Y |
| Personel hesabı açma ve kapatma | Y | Y | Y (öğretmen hesabı açma) |
| Rol atama | Y | Y (okul içi) | – |
| Mesaj kanalı inceleme ve dışa aktarma | – (marka ayarı) | Y | – |
| Okul raporları | G | Y | G |
| Okullar arası raporlar | Y | – | – |
| Saklama politikası ve KVKK talepleri | Y | G | Y (talep girişi) |
| Denetim izi görüntüleme | Y | Y (okul) | – |
| Bildirim şablonları | Y | G | – |

## Kapsam kuralları

Kapsam, rolün bağlandığı birimdir: marka, okul, sınıf veya çocuk. Her API isteği kullanıcının rol–kapsam çiftlerine göre sunucuda süzülür; mobil arayüz yalnızca gizler, kararı vermez.

1. Öğretmen yalnızca atandığı sınıfların aktif çocuklarını görür. Atama bitince erişim anında (en geç 60 saniye içinde) kalkar; önceki yılların sınıf verisine erişimi yoktur, müdür görür.
2. Veli yalnızca bağlı olduğu çocukları görür; kardeşler aynı hesaptadır. Başka çocuğun hiçbir verisi dönmez; grup fotoğraflarında diğer çocuklar rıza modeline göre görünür (12).
3. Okul müdürü ve ofis kendi okulunun tüm verisini görür; başka okulu görmez (nakil ekranı hariç).
4. Marka yöneticisi tüm okulları görür; mesaj içeriği ve sağlık ayrıntısı varsayılan olarak kapalıdır, marka ayarıyla açılır ve her erişim denetim izine yazılır.
5. Yardımcı öğretmenin kanal yazma yetkisi okul ayarıdır; varsayılan okur, yazamaz.
6. Sağlık verisi (11): sağlık sorumlusu, müdür, ofis ve sınıf öğretmeni (alerji özeti) görür; yardımcı öğretmen yalnızca alerji rozetini görür.
7. Mezun veya ayrılmış çocuk 08'e göre kapsamdan çıkar; personel için arşiv görünümü yalnızca müdür ve ofise açıktır.
8. Yetki değişiklikleri anında etkilidir; belirteç yenilemesi beklenmez, kontrol her istekte sunucuda yapılır.
9. Kimlik numarası, adres ve sağlık ayrıntısı gibi hassas alanlar öğretmen ve yardımcı öğretmen API'lerinde hiç bulunmaz; yalnızca güvenlik için gerekli sağlık işaretleri (alerji, diyet, acil durum, günün ilaçları) döner.
10. Her yetki reddi denetim izine yazılır; tekrarlayan retler güvenlik olayı üretir (02).

## Özel durumlar

- **Velayet kısıtı**: mahkeme kararıyla bir veli kısıtlı yapılır; ofis kararı girer ve veliyi kısıtlı işaretler, okul müdürü onaylar; işaretlendiği anda veli tüm bildirim listelerinden çıkar ve teslim yetkisi kalkar. Açılacak başlıklar (örneğin yalnızca gelişim raporu) ofis tarafından tek tek belirlenir.
- **Çok rollü kullanıcı**: öğretmen aynı okulda veli ise tek hesap, mod geçişi. Kendi çocuğunun raporunu kendisi yazıyorsa müdür onayı devreye girer; bu, MVP'deki tek onay istisnasıdır, genel onay akışı Faz 2'dedir (07).
- **Personel değişimi**: ayrılan personelin hesabı kapatılır, sınıf atamaları biter, kanallar yeni öğretmene geçer; geçmiş notlar yazar adıyla kalır.
- **Geçici öğretmen**: tarih aralıklı atama; süre bitince erişim kendiliğinden kalkar.
- **İki okulda görevli öğretmen**: iki rol–kapsam çifti, uygulamada okul seçici; raporlar okul bazında ayrışır.
- **Stajyer**: yardımcı öğretmenin kısıtlı alt türü (okul ayarı): yoklama girer, mesaj ve veli iletişim bilgisi göremez.
- **Üçüncü taraf uzman** (psikolog, fotoğrafçı): hesap verilmez; ihtiyaç doğarsa Faz 3'te sınırlı “dış uzman” rolü değerlendirilir. Benzer biçimde “teknik destek” (marka yöneticisinin sınırlı alt rolü) Faz 2 adayıdır (10); MVP'de ayrı rol yoktur.
- **Marka yöneticisinin okul işlemi yapması**: yapabilir; denetim izinde “marka düzeyinden” işaretlenir ve okul müdürüne bilgi gider.
- **Yetişkin olmayan kullanıcı yoktur**: öğrenciler uygulamayı kullanmaz; her hesap bir yetişkine aittir.
