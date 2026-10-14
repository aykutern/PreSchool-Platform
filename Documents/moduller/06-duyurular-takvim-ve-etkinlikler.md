# 06 Duyurular, Takvim ve Etkinlikler

Duyurular marka, okul, sınıf veya yaş grubu kapsamında yayınlanır ve okunma takibi yapılır; etkinlikler takvimde yer alır, geziler uygulama içi izin formuyla onaylanır.

## Amaç, kapsam ve aktörler

Modül okulun velilere tek yönlü bilgilendirmesini (duyuru) ve zamana bağlı olayları (takvim, etkinlik, izin formu, görüşme randevusu) tek yerde toplar. Duyurular ve okul takviminin gün türleri (01) MVP'dedir; etkinlik takvimi, izin formu ve randevu Faz 2'dedir.

**Kapsam içi**

- Duyuru: marka, okul, yaş grubu, sınıf veya özel segment kapsamında; başlık, içerik, ekler, bağlantı.
- Duyuru türleri: bilgi, onay gerektiren, acil; zamanlanmış yayın, sabitleme, son geçerlilik.
- Okundu takibi ve “okudum” onayı; okumayanlara hatırlatma; okunma raporu.
- Öğretmen duyuruları için isteğe bağlı müdür onayı.
- Etkinlik takvimi: etkinlikler, ICS aktarımı, yıllık plan içe aktarma (Faz 2); gün türleri (okul günü, tatil, yarım gün, kapalı) 01'deki okul takviminde MVP'dedir.
- Etkinlik: gezi, tören, kutlama, veli toplantısı; kapsam, katılım, kapasite, hatırlatma (Faz 2).
- İzin formu: uygulama içi onay, zaman damgası, onaylayan veli, metin sürümü; onaysız çocuk listesi (Faz 2).
- Veli görüşme randevusu: öğretmen saat aralığı açar, veli seçer (Faz 2).
- Takvimi telefona aktarma (ICS) (Faz 2).

**Kapsam dışı**

- Çift yönlü yazışma (05 Mesajlaşma); duyuruya yorum yoktur.
- Etkinlik ücretleri ve tahsilat (14 İleri Faz).
- Haftalık eğitim planı paylaşımı (07 Gelişim).
- Yemek menüsü yayını (13).

**Aktörler**

| Aktör | Modüldeki işi |
| --- | --- |
| Okul müdürü / ofis | Duyuru yazar ve onaylar, takvimi yönetir, etkinlik ve izin formu açar, okunma raporunu izler |
| Marka yöneticisi | Marka duyurusu gönderir, standart takvimi tanımlar |
| Öğretmen | Sınıf duyurusu yazar, görüşme saatleri açar, izin formu durumunu görür |
| Veli | Duyuru okur ve onaylar, etkinliğe katılım bildirir, izin formunu onaylar, randevu alır |

## Kullanıcı hikayeleri

| ID | Rol | Hikaye | Öncelik | Faz |
| --- | --- | --- | --- | --- |
| DY-01 | Okul müdürü | Tüm okula veya tek sınıfa duyuru göndermek istiyorum, böylece bilgi herkese aynı anda ulaşsın. | Must | MVP |
| DY-02 | Okul müdürü | Önemli duyuruda kimlerin okumadığını görüp onlara hatırlatma göndermek istiyorum, böylece kimse “görmedim” demesin. | Must | MVP |
| DY-03 | Veli | Duyuruları tek listede, sabitlenmişler üstte görmek istiyorum, böylece önemli olanı kaçırmayayım. | Must | MVP |
| DY-04 | Veli | “Okudum” onayı gereken duyuruyu tek dokunuşla onaylamak istiyorum, böylece okul benden emin olsun. | Must | MVP |
| DY-05 | Öğretmen | Sınıfıma duyuru yazmak istiyorum; okul isterse müdür onayından geçsin, böylece dil ve içerik standardı korunsun. | Should | MVP |
| DY-06 | Marka yöneticisi | Tüm okullara aynı anda marka duyurusu göndermek istiyorum, böylece her okul ayrı yazmasın. | Should | MVP |
| DY-07 | Ofis | Duyuruyu ileri tarihe zamanlamak istiyorum, böylece sabah 08:00'de gitsin. | Should | MVP |
| DY-08 | Veli | Okulun tatil ve etkinlik takvimini telefonumun takvimine eklemek istiyorum, böylece tarihleri unutmayayım. | Could | Faz 2 |
| DY-09 | Ofis | Gezi için izin formu gönderip onayları toplamak istiyorum, böylece onaysız çocuğu listede göreyim. | Must | Faz 2 |
| DY-10 | Veli | Çocuğumun gezi izin formunu uygulamadan onaylamak istiyorum, böylece kâğıt imzalamayayım. | Must | Faz 2 |
| DY-11 | Öğretmen | Veli görüşme günü için saat aralıkları açmak istiyorum, böylece veliler kendileri seçsin. | Should | Faz 2 |
| DY-12 | Veli | Görüşme için uygun saati seçip hatırlatma almak istiyorum, böylece randevuyu kaçırmayayım. | Should | Faz 2 |
| DY-13 | Ofis | Etkinlik için katılım bilgisi toplamak istiyorum, böylece kapasiteyi planlayayım. | Could | Faz 2 |
| DY-14 | Okul müdürü | Duyuru okunma oranlarını sınıf bazında görmek istiyorum, böylece iletişimin işleyip işlemediğini bileyim. | Should | MVP |

## İş kuralları ve işlevsel gereksinimler

**Duyuru (MVP)**

1. Kapsam seçenekleri: marka (tüm okullar), okul, yaş grubu, sınıf, özel segment (filtre: seçili sınıflar, yaş grupları; servis kullananlar Faz 3'te). Alıcılar kapsamdaki aktif kayıtların tam ve sınırlı velileri ile ilgili personeldir.
2. Türler: bilgi (günlük özete girer, sessiz saatlere uyar), onay gerektiren (“okudum” zorunlu; okumayanlara 24 saat sonra hatırlatma), acil (sessiz saati aşar, 5 dakika içinde açılmazsa SMS yedeği gider; okul duyurusunda müdür, marka duyurusunda ikinci bir marka yöneticisi veya bir okul müdürü onaylar: dört göz kuralı).
3. Yazarlar: marka yöneticisi (marka), müdür ve ofis (okul, sınıf), öğretmen (kendi sınıfı). Okul ayarı “öğretmen duyuruları onay gerektirir” açıksa öğretmen duyurusu müdür onayına düşer.
4. Zamanlama: yayın tarihi ve saati, son geçerlilik (dolunca listeden düşer, arşivde kalır), sabitleme (her kapsamda en çok 3 sabit duyuru).
5. Yayınlanmış duyuru düzenlenebilir; düzenleme “güncellendi” etiketi ve sürüm kaydı üretir. Silme arşive taşır; velide “kaldırıldı” görünür.
6. Okundu, duyuru uygulamada açılınca işlenir; “okudum” onayı ayrı ve zaman damgalı eylemdir. Onay oranı duyuru kartında görünür.
7. Ekler: en çok 5 dosya, toplam 25 MB; görseller sıkıştırılır; PDF önizlemesi vardır.
8. Duyuruya yorum veya yanıt yoktur; “soru sor” düğmesi ofis kanalını açar (05 Mesajlaşma).

**Takvim ve etkinlik (Faz 2)**

9. Gün türleri (okul günü, tatil, yarım gün, kapalı) 01'deki okul takviminde MVP'de tutulur; yoklama (04) ve menü (13) ona bağlıdır. Faz 2'de aynı takvime etkinlikler, ICS aktarımı ve yıllık plan içe aktarma eklenir.
10. Marka standart takvimi okullara kopyalanır; okul kendi farklarını ekler.
11. Etkinlik alanları: ad, tarih ve saat, yer, kapsam, açıklama, ekler, katılım toplama (evet / hayır / belki), kapasite, hatırlatma (1 gün ve 1 saat önce).
12. Yıl sonunda takvim ve etkinlikler arşive geçer; yeni yıl takvimi şablondan açılır.

**İzin formu (Faz 2)**

13. İzin formu bir etkinliğe bağlıdır ve metni sürümlüdür. Her çocuk için tam yetkili velinin uygulama içi onayı gerekir (yanıtlar: onayla / hayır; hayır da kaydedilir); onay zaman damgası, kullanıcı ve cihaz bilgisiyle kaydedilir.
14. Onaysız çocuk etkinlik listesinde “onay bekliyor” görünür; etkinlikten 1 gün önce velilere hatırlatma, ofise onaysız listesi gider.
15. Veli onayı etkinlik başlamadan geri alabilir; geri alma ofise bildirilir.
16. Dijital onayın hukuki yeterliliği kurumun hukuk görüşüne bağlıdır (doğrulanmalı). Gerekirse ıslak imzalı seçenek sunulur: PDF yazdır, imzala, yükle.

**Görüşme randevusu (Faz 2)**

17. Öğretmen gün ve zaman dilimi süresi (varsayılan 15 dakika) tanımlar; her çocuk için bir zaman dilimi. Veli seçer ve değiştirebilir; çakışma engellenir.
18. Randevu 1 gün ve 1 saat önce hatırlatılır; görüşme notu 07 Gelişim'e bağlanır.

## Veri, ekranlar ve bildirimler

**Varlıklar**

| Varlık | Anahtar alanlar | Not |
| --- | --- | --- |
| Duyuru | kapsam, tür, başlık, içerik, ekler, yazar, onay durumu, yayın zamanı, son geçerlilik, sabit mi, sürüm | MVP |
| Duyuru alıcısı | duyuru, kullanıcı, okundu zamanı, onay zamanı | Okunma raporunun kaynağı |
| Takvim günü | okul, tarih, gün türü, ad | 01'de MVP (Okul takvimi günü); 06 Faz 2'de etkinlik bağlar |
| Etkinlik | okul, ad, zaman, yer, kapsam, katılım toplama, kapasite, izin formu | Faz 2 |
| Katılım | etkinlik, kayıt, veli, yanıt, zaman | Faz 2 |
| İzin formu | etkinlik, metin sürümü, son onay tarihi | Faz 2 |
| İzin onayı | form, kayıt, veli, zaman, cihaz, geri alma | Faz 2; PDF'e aktarılabilir |
| Görüşme zaman dilimi | öğretmen, sınıf, zaman, kayıt, veli, durum | Faz 2 |

**Ekranlar**

| Ekran | Platform | Rol | İçerik |
| --- | --- | --- | --- |
| Duyurular | Mobil | Veli, öğretmen | Sabitler üstte, okunmamış işareti, tür etiketi |
| Duyuru detayı | Mobil | Veli | İçerik, ekler, “okudum”, “soru sor” |
| Duyuru yazma | Web; mobil (öğretmen) | Müdür, ofis, öğretmen | Kapsam, tür, içerik, ekler, zamanlama, önizleme |
| Onay kuyruğu | Web | Okul müdürü | Bekleyen öğretmen duyuruları, onayla veya geri gönder |
| Okunma raporu | Web | Müdür, marka yöneticisi | Duyuru bazında okundu ve onay oranı, okumayan listesi, hatırlat |
| Takvim | Mobil, web | Tüm roller | Ay görünümü, gün türleri, etkinlikler, ICS aktar |
| Etkinlik detayı | Mobil | Veli | Bilgi, katılım yanıtı, izin formu |
| İzin formu onayı | Mobil | Veli | Metin, çocuk seçimi, onayla |
| İzin formu durumu | Web; mobil (öğretmen) | Ofis, öğretmen | Onaylı ve onaysız çocuklar, hatırlat, PDF |
| Randevu zaman dilimleri | Mobil | Öğretmen | Gün, süre, zaman dilimleri, dolu/boş |
| Randevu seçimi | Mobil | Veli | Boş zaman dilimleri, seç, değiştir |

**Bildirimler**

| Olay | Alıcı | Kanal | Zamanlama |
| --- | --- | --- | --- |
| Yeni duyuru | Kapsamdaki veliler ve personel | Anlık bildirim; acilde SMS yedeği | Önemli ve acil yayın anında; bilgi türü günlük özete girer (09) |
| Okudum hatırlatması | Onaylamayan veliler | Anlık bildirim | 24 saat sonra, bir kez |
| Onay bekleyen duyuru | Okul müdürü | Uygulama içi | Anında |
| Etkinlik hatırlatması | Kapsamdaki veliler | Anlık bildirim | 1 gün ve 1 saat önce |
| İzin formu gönderildi | Tam yetkili veliler | Anlık bildirim | Anında |
| Onaysız izin hatırlatması | Onaylamayan veliler, ofis | Anlık bildirim, uygulama içi | Etkinlikten 1 gün önce |
| Randevu alındı veya değişti | Öğretmen, veli | Anlık bildirim | Anında |
| Randevu hatırlatması | Öğretmen, veli | Anlık bildirim | 1 gün ve 1 saat önce |

## Uç durumlar, kabul kriterleri ve açık sorular

**Uç durumlar**

- Duyurudan sonra sınıfa yeni çocuk geldi: velisi son 30 günün duyurularını görür, hatırlatma almaz.
- İki okulda çocuğu olan veli: marka duyurusunu bir kez görür; okul duyuruları okul etiketiyle ayrışır.
- Kısıtlı veli: duyuru görmez; ofis başlık bazında açabilir.
- Onay bekleyen öğretmen duyurusunun zamanı geçti: kendiliğinden iptal olur, öğretmene bilgi gider.
- İzin formundan sonra etkinlik tarihi değişti: küçük değişiklikte onaylar geçerli kalır (okul ayarı); yer veya kapsam değişirse yeniden onay istenir.
- İki velinin onayı farklı (biri evet, biri hayır): “hayır” yanıtı, ofis velilerle görüşüp çözene kadar katılımı engeller; çocuk onaysız listesinde kalır, ofise uyarı düşer.
- Etkinlik kapasitesi doldu: bekleme listesi; boşalan yer sırayla teklif edilir.
- Takvim içe aktarmada çakışma: önizlemede çakışan günler işaretlenir, ofis seçer.

**Kabul kriterleri**

- Marka geneli duyuru 1.000 alıcıya (10× yük testi) 2 dakika içinde ulaşır; okundu ve onay sayıları anlık güncellenir.
- Onay ayarı açıkken öğretmen duyurusu müdür onayından önce hiçbir veliye gitmez (otomatik test).
- Acil duyuru sessiz saatte de anında iletilir ve 5 dakika içinde açılmayan alıcılara SMS gider.
- İzin onayı zaman damgası, kullanıcı ve metin sürümüyle denetim izine yazılır; ofis PDF olarak alabilir.
- Aynı zaman dilimini iki veli aynı anda seçemez (eşzamanlılık testi).

**Açık sorular**

- [ ] Öğretmen duyuruları onay gerektirsin mi? (Öneri: ilk dönem evet, sonra okul kararı; S8)
- [ ] Acil duyuruda SMS yedeği maliyeti kabul ediliyor mu? (yaklaşık veli sayısı kadar SMS)
- [ ] Dijital izin onayı kurum hukukçusuna göre yeterli mi? (S19)
- [ ] Etkinlik katılım toplama MVP'ye çekilsin mi?
- [ ] Marka takvimi okulları ne kadar bağlasın: yalnızca tatiller mi, etkinlikler de mi?
