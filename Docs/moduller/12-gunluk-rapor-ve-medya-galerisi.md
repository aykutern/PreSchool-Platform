# 12 Günlük Rapor ve Medya Galerisi

Günlük rapor ve galeri, acil olmadığı için sonraki fazlara bırakılmıştır; öğretmen sınıfın gününü toplu girip çocuk bazında düzenler, veli yemek, uyku, etkinlik ve fotoğrafları tek zaman akışında görür, fotoğraf görünürlüğü rızaya bağlıdır.

## Amaç, kapsam ve aktörler

Modül her çocuğun gününü (yemek, uyku, tuvalet, ruh hali, etkinlik, not) öğretmenin toplu girip yayınladığı bir akışla veliye iletir; sınıf fotoğrafları rıza modeline göre paylaşılır. Proje sahibi kararıyla Faz 3'tedir (K3); MVP'de günlük iletişim 05 ve 06 ile sağlanır.

**Kapsam içi**

- Yaş grubuna göre günlük rapor şablonları (bez veya tuvalet, öğün sayısı, uyku).
- Toplu giriş ve çocuk bazında düzenleme; gün sonu yayınlama; sonradan düzeltme.
- Veli zaman akışı: gün bazında rapor, fotoğraflar, öğretmen notu.
- İhtiyaç listesi (bez, yedek kıyafet) ve velinin sabah notu.
- Fotoğraf ve kısa video: çekim, sıkıştırma, etiketleme, rızaya bağlı görünürlük, indirme, sınıf albümleri.
- Veli teşekkür veya beğeni işareti (yorum yok).

**Kapsam dışı**

- Canlı kamera yayını; uzun video; okul sosyal medyasına otomatik paylaşım.
- İki yönlü yazışma (05 Mesajlaşma).
- Gelişim değerlendirmesi (07); günlük rapor gözlem notu değildir.

**Aktörler**

| Aktör | Modüldeki işi |
| --- | --- |
| Öğretmen / yardımcı öğretmen | Günü girer, fotoğraf çeker ve etiketler, yayınlar, ihtiyaç ister |
| Veli | Akışı okur, fotoğrafları indirir, sabah notu bırakır, ihtiyaç isteğine yanıt verir |
| Okul müdürü | Şablonları düzenler, yayınlanmamış raporları izler, albümleri denetler |
| Marka yöneticisi | Fotoğraf rıza politikasını ve medya saklama süresini belirler |

## Kullanıcı hikayeleri

| ID | Rol | Hikaye | Öncelik | Faz |
| --- | --- | --- | --- | --- |
| GR-01 | Öğretmen | Sınıfın öğle yemeğini tek ekranda “hepsi yedi” deyip istisnaları işaretlemek istiyorum, böylece giriş 1 dakikada bitsin. | Must | Faz 3 |
| GR-02 | Öğretmen | Uyku başlangıç ve bitiş saatini toplu girmek istiyorum, böylece her çocuk için ayrı yazmayayım. | Must | Faz 3 |
| GR-03 | Öğretmen | Günün fotoğraflarını çekip çocukları etiketlemek ve rızasız çocukta uyarı almak istiyorum, böylece yanlış paylaşım olmasın. | Must | Faz 3 |
| GR-04 | Öğretmen | Günü 16:00'da yayınlamak istiyorum; veliye tek bildirim gitsin, böylece gün boyu bildirim yağmasın. | Must | Faz 3 |
| GR-05 | Veli | Çocuğumun gününü tek akışta (yemek, uyku, tuvalet, etkinlik, fotoğraf) görmek istiyorum, böylece akşam sohbeti kurabileyim. | Must | Faz 3 |
| GR-06 | Veli | Fotoğrafları telefonuma indirmek istiyorum, böylece anı saklayayım. | Should | Faz 3 |
| GR-07 | Öğretmen | Veliden ihtiyaç (bez, yedek kıyafet) istemek ve velinin “getirdim” demesini istiyorum, böylece eksik kalmasın. | Should | Faz 3 |
| GR-08 | Veli | Sabah not bırakmak istiyorum (az uyudu, ilaç aldı), böylece öğretmen güne hazır başlasın. | Should | Faz 3 |
| GR-09 | Okul müdürü | Yaş grubuna göre rapor şablonunu düzenlemek istiyorum, böylece bez ve tuvalet alanları doğru sınıfta çıksın. | Must | Faz 3 |
| GR-10 | Okul müdürü | Yayınlanmamış günlük raporu olan sınıfları görmek istiyorum, böylece veliler boş ekran görmesin. | Should | Faz 3 |
| GR-11 | Veli | Çocuğumun fotoğrafının sınıf albümünde görünmesini istemiyorum, böylece yalnızca bana gelsin. | Must | Faz 3 |
| GR-12 | Öğretmen | Sınıf albümü oluşturup gezi fotoğraflarını eklemek istiyorum, böylece etkinlik anıları bir arada olsun. | Could | Faz 3 |

## İş kuralları ve işlevsel gereksinimler

**Şablon ve giriş**

1. Rapor şablonu yaş grubuna bağlıdır: öğünler (kahvaltı, öğle, ikindi; yedi / az yedi / yemedi), uyku (başlangıç, bitiş), tuvalet veya bez (sayı, saat), ruh hali, etkinlikler (07'deki haftalık plandan seçilir), serbest not. Müdür alanları açıp kapatır.
2. Toplu giriş: her alan için sınıf varsayılanı (örneğin “hepsi yedi”) ve istisna işaretleme; çocuk ekranı yalnızca özel not için.
3. Yoklamada gelmeyen çocuk için rapor oluşmaz; erken ayrılan çocukta ayrılış sonrası alanlar kapalıdır.

**Yayınlama ve veli akışı**

4. Rapor öğretmen “yayınla” dediğinde veliye açılır; günde tek özet bildirim gider; akşam sohbeti için tasarlandığından bu bildirim sessiz saatten muaftır (veli tercihiyle kapatılabilir). Yayın hedef saati okul ayarıdır (varsayılan 16:00); geçilirse öğretmene, 30 dakika sonra müdüre hatırlatma.
5. Yayından sonra düzeltme “güncellendi” etiketiyle görünür; 48 saat sonra rapor kilitlenir.
6. Veli akışı gün bazında listelenir; son 30 gün hızlı erişimde, öncesi arşivde. Veli beğeni işareti bırakabilir; yorum yoktur, soru 05 kanalına gider.
7. İhtiyaç isteği (bez, yedek kıyafet, ıslak mendil): öğretmen listeden seçer, veli “getirdim” der; açık istekler ana ekranda görünür.
8. Sabah notu: veli 09:30'a kadar kısa not bırakır; öğretmenin yoklama ekranında çocuğun yanında görünür.

**Medya ve rıza**

9. Fotoğraf ve video uygulama içinden çekilir veya galeriden seçilir; uygulama içi çekim cihaz galerisine yazılmaz, yükleme kuyruğu şifreli uygulama alanında tutulur ve hesap kapanınca silinir (R15); cihazda sıkıştırılır, konum bilgisi silinir; video en çok 60 saniye.
10. Her medya en az bir çocukla etiketlenmeden yayınlanamaz; birden fazla çocuk etiketli medya “grup medyası”dır. Üç görünürlük kapsamı vardır (03 kural 15): yalnızca kendi velisi (tek çocuk etiketli medya), sınıf albümü (grup medyası; rızalı çocukların velileri) ve okul tanıtımı (uygulama dışı). Medya yalnızca etiketli çocukların velilerine gösterilir.
11. Sınıf albümü rızası (03) olmayan çocuk grup medyasında etiketlenemez; öğretmen etiketlemeye çalışınca uyarı alır ve medya yalnızca rızalı çocukların velilerine gider. Arka planda görünen rızasız çocuk için öğretmen eğitimi ve okul kuralı gerekir; sistem bunu teknik olarak engelleyemez.
12. Okul tanıtımı rızası ayrı bir kapsamdır; uygulama bu kapsamda paylaşım yapmaz, yalnızca ofise rızalı çocuk listesini verir.
13. İndirme rıza kapsamında serbesttir; velinin indirdiği içerik okulun kontrolü dışındadır ve aydınlatma metninde belirtilir. Ekran görüntüsü engellenemez (Kesişen Konular, Güvenlik).
14. Silme: öğretmen 24 saat içinde, sonra müdür; silinen medya 30 gün geri alınabilir, sonra kalıcı silinir.
15. Günlük medya kotası sınıf başına okul ayarıdır (varsayılan 40 fotoğraf); depolama maliyeti marka raporunda izlenir.
16. Rıza geri alındığında çocuğun etiketli olduğu grup medyası diğer velilerden kalkar; kendi velisine kalır.
17. Saklama ve mezuniyet: mezun veya ayrılan çocuğun medyası veri paketine girer; salt-okunur süre bitiminde çocuğun etiketleri kaldırılır ve grup medyası diğer velilere kapanır, dosyalar 30 gün sonra silinir (08, S12).

## Veri, ekranlar ve bildirimler

**Varlıklar**

| Varlık | Anahtar alanlar | Not |
| --- | --- | --- |
| Rapor şablonu | yaş grubu, alanlar, sıra, zorunlu mu | Okul düzeyinde |
| Günlük rapor | kayıt, tarih, durum (taslak / yayınlandı / kilitli), yayınlayan, yayın zamanı | Çocuk başına günde bir |
| Rapor kalemi | rapor, alan türü, değer, saat, not | Alan türü şablondan gelir |
| İhtiyaç isteği | kayıt, tür, isteyen, zaman, veli yanıtı | Açık istek ana ekranda |
| Sabah notu | kayıt, tarih, metin, yazan veli | 09:30'a kadar |
| Medya | sınıf, dosya, tür, çeken, zaman, albüm, durum | Nesne depolamada |
| Medya etiketi | medya, kayıt, etiketleyen | Görünürlüğü belirler |
| Albüm | sınıf, ad, tarih, etkinlik | Etkinlikle bağlanabilir (06) |
| Beğeni | medya veya rapor, veli, zaman | Yorum yok |

**Ekranlar**

| Ekran | Platform | Rol | İçerik |
| --- | --- | --- | --- |
| Günlük rapor girişi | Mobil | Öğretmen | Sınıf listesi, alan sekmeleri, toplu değer, istisnalar |
| Çocuk günü düzenle | Mobil | Öğretmen | Alanlar, not, fotoğraflar |
| Fotoğraf çek ve etiketle | Mobil | Öğretmen | Kamera, çoklu seçim, etiket, rıza uyarısı |
| Yayınla | Mobil | Öğretmen | Önizleme, eksik alan uyarısı, gönder |
| Gün akışı | Mobil | Veli | Günün raporu, fotoğraflar, not, beğeni, ihtiyaç isteği |
| Fotoğraf görüntüleyici | Mobil | Veli | Büyüt, indir |
| Sabah notu | Mobil | Veli | Kısa metin |
| Şablon yönetimi | Web | Okul müdürü | Yaş grubu başına alanlar |
| Yayın takibi | Web | Okul müdürü | Yayınlanmamış sınıflar, medya kotası, depolama |

**Bildirimler**

| Olay | Alıcı | Kanal | Zamanlama |
| --- | --- | --- | --- |
| Gün yayınlandı | Tam ve sınırlı veliler | Anlık bildirim (tek özet) | Yayın anında; sessiz saatten muaf (veli kapatabilir) |
| İhtiyaç isteği | Veliler | Anlık bildirim | Anında |
| Sabah notu geldi | Sınıf öğretmenleri | Uygulama içi | Anında |
| Yayın saati geçti | Öğretmen; 30 dakika sonra müdür | Uygulama içi | Hedef saatte |
| Rızasız etiket girişimi | Öğretmen | Anlık uyarı | Anında |
| Medya kotası doldu | Öğretmen, müdür | Uygulama içi | Anında |

## Uç durumlar, kabul kriterleri ve açık sorular

**Uç durumlar**

- Çocuk yarım gün kaldı: ayrılış saatinden sonraki alanlar kapalı, rapor kısmi yayınlanır.
- İki öğretmen aynı sınıfı giriyor: alanlar bölüşülür; çakışmada son yazan kazanır, geçmiş tutulur (04 ile aynı kural).
- Veli albüm rızasını geri aldı: geçmiş grup medyası diğer velilerden kalkar, kendi velisine kalır.
- Fotoğrafta rızasız çocuk arka planda: teknik engel yok; öğretmen kuralı ve eğitimi, müdür denetimi.
- Medya yükleme kuyruğu uzun (zayıf bağlantı): rapor medyasız yayınlanabilir, medya sonradan eklenir ve “güncellendi” görünür.
- Depolama maliyeti beklenenin üstünde: kota ve saklama süresi kısaltılır; marka raporu uyarır.
- Mezun çocuk grup fotoğraflarında: S12 kararına göre (öneri: etiket kaldırma ve 30 gün sonra silme; kural 17).

**Kabul kriterleri**

- 20 kişilik sınıfın günlük raporu (yemek, uyku, tuvalet, 10 fotoğraf) 10 dakikanın altında tamamlanır (kullanılabilirlik testi).
- Yayın velilere tek bildirim üretir; gün içi düzeltmeler bildirim üretmez.
- Rızasız çocuk grup medyasında etiketlenemez (otomatik test).
- Veli yalnızca çocuğunun etiketli olduğu medyayı görür; etiketsiz medya hiçbir veliye dönmez (otomatik test).
- 5 MB fotoğraf 4G'de 10 saniyede yüklenir ve EXIF konum bilgisi silinmiş olur (test).

**Açık sorular**

- [ ] Video gerekli mi, yoksa yalnızca fotoğraf mı? (Öneri: 60 saniyelik video)
- [ ] Günlük rapor her yaş grubunda zorunlu mu, yoksa yalnızca küçük gruplarda mı?
- [ ] Sınıf albümü ve etkinlik albümü Faz 3'te mi, daha sonra mı?
- [ ] Beğeni işareti istenir mi? (Öneri: evet, yorum yok)
- [ ] Medya saklama süresi ve depolama bütçesi.
