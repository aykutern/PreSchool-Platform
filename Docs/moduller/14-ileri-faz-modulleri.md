# 14 İleri Faz Modülleri

Aidat ve ödemeler, ön kayıt ve İK gibi modüller bilinçli olarak ertelenmiştir; aşağıda her biri için gerekçe, bağımlılık ve hedef faz yer alır.

## Aday modüller

Yedi ana aday (Genel Bakış ve Modüller'deki liste) ile üç ek aday (dış uzman erişimi, kütüphane, etkinlik ödemeleri) bilinçli olarak kapsam dışında tutulmuştur; her biri için gerekçe, bağımlılık ve hedef faz aşağıdadır. Bir adayı öne çekmek faz kapısında değişiklik kurulu kararı gerektirir. Hedef faz değerleri: Faz 3 (yol haritasında planlı), Faz 4+ (yol haritası sonrası), Karar yok (henüz değerlendirilmedi).

| Aday modül | Ne sağlar | Neden ertelendi | Bağımlılık | Hedef faz |
| --- | --- | --- | --- | --- |
| Aidat ve ödemeler | Ücret planı, taksit, makbuz, ödeme durumu, hatırlatma, online ödeme | Proje sahibi kararı (K4); muhasebe ve ödeme sağlayıcı kararı bekliyor; finansal veri yükümlülükleri | 03, 09, muhasebe sistemi | Faz 3 |
| Ön kayıt ve aday takibi | Başvuru formu, bekleme listesi, tanıtım randevusu, dönüşüm raporu | MVP değer odağı dışında; mevcut süreç telefon ve Excel ile sürüyor | 01, 02, 03 (aday durumu), 06 (randevu) | Faz 3 |
| Personel ve İK | Vardiya, izin, personel devamı, özlük belgeleri, eğitim kayıtları | Ayrı iş alanı; mevcut İK yazılımı olabilir | 01, 02 | Faz 4+ |
| Anket ve geri bildirim | Veli memnuniyeti, etkinlik sonrası anket, öneri kutusu | Erken aşamada basit form yeterli | 06, 09 | Faz 4+ |
| Envanter ve demirbaş | Sınıf materyali, oyuncak, sarf takibi | Operasyonel; veli değeri yok | 01 | Faz 4+ |
| MEB veri uyumu | Resmi sistemlere aktarılacak veriler için dışa aktarma dosyaları | Resmi entegrasyon API'si bilinmiyor; gereklilik belirsiz (doğrulanmalı) | 03, 04 | Faz 4+ (doğrulama sonrası) |
| Servis canlı konum | Araç GPS, tahmini varış, veli haritası | Donanım veya telefon GPS, pil, konum verisi KVKK, maliyet | 13 | Faz 4+ |
| Dış uzman erişimi | Psikolog veya terapist için sınırlı rol | Rıza ve hukuki karmaşıklık | Roller, 07, 11 | Karar yok |
| Kütüphane ve kitap ödünç | Kitap takibi, eve gönderilen kitap | Düşük öncelik | 03 | Karar yok |
| Etkinlik ödemeleri | Gezi ücreti tahsilatı | Aidat modülüyle birlikte | Aidat | Faz 3 (aidat ile) |

## Aidat ve ödemeler: kapsam taslağı

Aidat modülü tahsilatı değil takibi hedefler: ücret planı, taksit takvimi, ödeme kaydı ve hatırlatma uygulamada; muhasebe ve e-fatura mevcut sistemde kalır. Online ödeme eklenirse kart verisi ödeme sağlayıcıda kalır, uygulama saklamaz.

- **Ücret planı**: yıllık veya aylık, kardeş indirimi, burs, servis ve yemek ek ücretleri; okul bazında tanım.
- **Sözleşme ve taksit takvimi**: kayıtla bağlantılı; tahakkuk otomatik; ayrılışta kesinti kuralı (08).
- **Ödeme kaydı**: havale, kart, online ödeme (örneğin iyzico veya PayTR gibi yerli sağlayıcı; teklif alınır); makbuz PDF.
- **Hatırlatma**: vade öncesi ve sonrası bildirimler (09); gecikme listesi ofiste.
- **Veli ekranı**: borç, ödeme geçmişi, makbuz indirme.
- **Raporlar**: tahsilat oranı, gecikme yaşlandırması, okul karşılaştırması.
- **Kararlar**: muhasebe sistemiyle entegrasyon mu, yalnızca takip mi; online ödeme olacak mı; finansal veri saklama süresi (hukuk ve mali müşavir görüşü).
- **Riskler**: ödeme sağlayıcı sözleşmesi, mutabakat farkları, veli şikâyetleri; büyüklük L.

## Ön kayıt ve aday takibi: kapsam taslağı

Aday takibi, 03'teki “aday” durumunu bir başvuru akışıyla besler: web formu, bekleme listesi, tanıtım randevusu ve teklif; kayıt gerçekleşince mevcut kayıt sürecine devredilir.

- **Başvuru formu**: okul web sitesinden; çocuk, veli iletişim, yaş grubu, tercih edilen okul; KVKK aydınlatma ve rıza (aday verisi için ayrı).
- **Bekleme listesi**: yaş grubu ve okul bazında sıra, öncelik (kardeş, personel çocuğu), kapasite ile eşleşme (01 doluluk).
- **Tanıtım ve görüşme randevusu**: 06'daki randevu zaman dilimi mekanizmasıyla.
- **Teklif ve sözleşme**: PDF gönderimi, kabul takibi; kayıt sihirbazına aktarım (03).
- **Dönüşüm raporu**: başvuru, görüşme, teklif, kayıt aşamaları; kaynak (tavsiye, web, reklam).
- **Saklama**: kayıt olmayan adayların verisi kısa sürede silinir (hukuk görüşü); pazarlama iletişimi için ayrı rıza.
- **Büyüklük**: M; bağımlılıklar 01, 02, 03, 06.

## Diğer adaylar

Aşağıdaki adaylar yalnızca başlık düzeyinde tanımlanmıştır; her biri ancak Faz 3 kapısında öncelik alırsa ayrıntılı analiz edilir.

- **Personel ve İK**: vardiya ve nöbet planları, izin talepleri, personel devamı, özlük belgeleri; 01'deki öğretmen atamalarıyla bağlantılı. Mevcut İK yazılımı varsa entegrasyon tercih edilir.
- **Anket ve geri bildirim**: veli memnuniyeti (dönemlik), etkinlik sonrası kısa anket, öneri kutusu; isimli veya anonim; sonuçlar okul ve marka raporunda.
- **Envanter ve demirbaş**: sınıf materyali ve sarf takibi, zimmet; yönetim içi, veli görmez.
- **MEB veri uyumu**: resmi sistemlere girilmesi gereken öğrenci ve devam verisi için dışa aktarma dosyaları; resmi bir entegrasyon API'si bilinmediği için kapsam, okulların mevcut yükümlülükleri netleştikten sonra belirlenir (doğrulanmalı).
- **Servis canlı konum**: araç takip cihazı veya hostes telefonu GPS'i; tahmini varış; konum verisi için ayrı aydınlatma ve saklama kuralı; pil ve maliyet etkisi.
- **Dış uzman erişimi**: okulla çalışan psikolog veya terapist için yalnızca atanan çocukları gören sınırlı rol; veli rızası ve sözleşme gerektirir.
- **Kütüphane ve kitap ödünç**: eve gönderilen kitapların takibi, iade hatırlatması.
- **Etkinlik ödemeleri**: gezi ve etkinlik ücretlerinin tahsilatı; aidat modülünün parçası olarak ele alınır.
