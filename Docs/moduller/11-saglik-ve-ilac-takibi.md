# 11 Sağlık ve İlaç Takibi

Alerji ve kronik durumlar sınıf listesinde görünür, ilaç uygulaması veli talebi → onay → uygulama kaydı zinciriyle izlenir; sağlık verisi özel nitelikli veri olarak sınırlı rollerle işlenir.

## Amaç, kapsam ve aktörler

Modül çocuğun sağlık profilini (alerji, kronik durum, diyet, doktor, acil kişiler), ilaç uygulamasını (veli talebi, onay, uygulama kaydı) ve kaza bildirimini kayıt altına alır. Sağlık verisi özel nitelikli kişisel veridir: hukuki dayanağı hukuk görüşüyle belirlenir (S21), sınırlı roller ve ayrı saklama kuralı geçerlidir. Modül Faz 2'dedir; MVP'de yalnızca 03'teki alerji ve diyet işareti vardır.

**Kapsam içi**

- Sağlık profili ve alerji rozetinin ayrıntısı (03'teki işaretin genişlemesi).
- İlaç talebi ve uygulama zinciri: veli talebi, sağlık sorumlusu veya müdür onayı, öğretmen uygulama kaydı, veli bildirimi.
- Kaza ve olay raporu, veli bildirimi, müdür kapanışı.
- Günlük ateş veya sağlık kontrolü (isteğe bağlı, okul ayarı).
- Sağlık belgeleri (aşı kartı gibi) yalnızca dosya olarak (isteğe bağlı).
- Sağlık sorumlusu rolü ve kronik durum listesi.

**Kapsam dışı**

- Tanı, tıbbi tavsiye veya tedavi takibi; uygulama tıbbi cihaz değildir.
- İlaç stoku, sigorta, okul doktoru sistem entegrasyonu.
- Aşı takvimi hatırlatıcısı (Faz 3 adayı).

**Aktörler**

| Aktör | Modüldeki işi |
| --- | --- |
| Veli (tam yetkili) | Profili girer, rıza verir, ilaç talep eder, kaza bildirimini okur |
| Sağlık sorumlusu / okul müdürü | Profili doğrular, ilaç talebini onaylar, kaza raporunu kapatır, kronik durum listesini izler |
| Öğretmen | Alerji özetini görür, ilaç uygulamasını kaydeder, kaza bildirir |
| Yardımcı öğretmen | Yalnızca alerji rozetini görür |
| Ofis | MVP'de alerji ve diyet işaretini girer (03); belgeleri yükler, rıza durumunu izler |

## Kullanıcı hikayeleri

| ID | Rol | Hikaye | Öncelik | Faz |
| --- | --- | --- | --- | --- |
| SG-01 | Veli | Çocuğumun alerjilerini ve şiddetini kaydetmek istiyorum, böylece yemekte ve etkinlikte dikkate alınsın. | Must | Faz 2 |
| SG-02 | Öğretmen | Sınıf listesinde alerji rozetini ve dokununca ayrıntısını görmek istiyorum, böylece yemekte hata yapmayayım. | Must | Faz 2 |
| SG-03 | Veli | Belirli saatlerde verilecek ilacı dozuyla talep etmek istiyorum, böylece telefonla anlatmak zorunda kalmayayım. | Must | Faz 2 |
| SG-04 | Sağlık sorumlusu | İlaç talebini onaylamak, reddetmek veya reçete istemek istiyorum, böylece okul politikası uygulansın. | Must | Faz 2 |
| SG-05 | Öğretmen | İlacı verdiğimde saati ve dozu tek dokunuşla kaydetmek istiyorum, böylece kayıt ve veli bilgisi oluşsun. | Must | Faz 2 |
| SG-06 | Veli | İlacın verildiğini bildirim olarak almak istiyorum, böylece içim rahat olsun. | Should | Faz 2 |
| SG-07 | Öğretmen | Küçük bir kazada ne olduğunu ve ne yapıldığını kaydedip veliye bildirmek istiyorum, böylece söz yerine kayıt olsun. | Must | Faz 2 |
| SG-08 | Okul müdürü | Kaza raporlarını görüp kapatmak ve dönem istatistiğini almak istiyorum, böylece tekrar eden riskleri göreyim. | Should | Faz 2 |
| SG-09 | Veli | Acil durumda aranacak kişileri ve doktoru güncel tutmak istiyorum, böylece okul doğru kişiye ulaşsın. | Must | Faz 2 |
| SG-10 | Sağlık sorumlusu | Kronik durumu olan çocukların listesini ve eylem planlarını görmek istiyorum, böylece hazırlıklı olayım. | Should | Faz 2 |
| SG-11 | Veli | Sağlık verisi rızamı geri aldığımda verinin işlenmemesini istiyorum, böylece kararım uygulansın. | Must | Faz 2 |
| SG-12 | Öğretmen | Ateş ölçümünü kaydedip eşiği aşınca veliye bildirmek istiyorum, böylece erken haber verilsin. | Could | Faz 3 |

## İş kuralları ve işlevsel gereksinimler

**Sağlık profili**

1. Alanlar: alerjiler (tür, şiddet: hafif / orta / ağır, tepki, önlem), kronik durumlar (ad, eylem planı metni, sürekli ilaç), diyet kısıtı (tıbbi / tercih; inanç bilgisi ayrıca tutulmaz, hukuk görüşü), kan grubu (isteğe bağlı), doktor (ad, telefon), acil kişiler (03), sağlık belgeleri (dosya, isteğe bağlı).
2. MVP'de alerji ve diyet işaretini ofis girer (03 kural 16). Faz 2'de profili tam yetkili veli tamamlar; sağlık sorumlusu “doğrulandı” işareti koyar; öğretmen görür ama değiştiremez, 05'teki kısayolla yalnızca “doğrulama bekleyen öneri” oluşturur.
3. Sağlık verisinin hukuki dayanağı (açık rıza mı, yaşamın korunması veya yasal yükümlülük mü) hukuk görüşüyle belirlenir (S21). Dayanak rıza ise rızasız profil doldurulamaz; rıza geri alınırsa alanlar kilitlenir ve görünmez olur. Alerji gibi güvenlik bilgisinin rıza dışı bir dayanakla tutulup tutulamayacağı ve geri almanın işlevsel sonucu (okul politikası) aynı görüşle karara bağlanır.
4. Alerji rozeti sınıf listesi, yoklama, menü ve günlük rapor ekranlarında görünür; ayrıntı yalnızca yetkili rollere açılır.

**İlaç talebi ve uygulama**

5. Talep alanları: ilaç adı, doz, saatler, başlangıç ve bitiş, reçete fotoğrafı (okul ayarına göre zorunlu), veli onayı ve sorumluluk metni.
6. Onay: sağlık sorumlusu, yoksa müdür; ofis onaylamaz. Reddetme nedeni zorunlu; onaysız talep uygulanmaz.
7. Uygulama: öğretmenin ilaç vermesi kurum politikasının ve ilgili mevzuatın (MEB ve Sağlık Bakanlığı okul sağlığı kuralları; doğrulanmalı) izin verdiği ölçüde yapılır; öğretmen “bugünkü ilaçlar” listesinden verdiği dozu saatiyle işaretler; atlanan doz nedeniyle kaydedilir; veli anında bildirim alır.
8. Sabah 08:00'de o günün ilaç listesi sınıf öğretmenine gider; uygulanmamış doz saati geçince hatırlatılır.
9. Talep bitiş tarihinde kendiliğinden kapanır; uzatma yeni talep gerektirir.

**Kaza ve olay raporu**

10. Rapor alanları: zaman, yer, ne oldu, yapılan müdahale, tanık personel, fotoğraf (isteğe bağlı), veliye bildirim saati ve yöntemi.
11. Veli bildirimi acil önceliklidir (sessiz saati aşar; anlık bildirim 5 dakika içinde açılmazsa SMS yedeği, 09); veli “okudum” onayı verir. Ciddi olayda müdür telefonla arar; uygulama kaydı tamamlayıcıdır.
12. Müdür raporu kapatır; kapatılan rapor değiştirilemez, ek not eklenebilir. Dönem istatistiği tür ve yer bazında çıkar.

**Erişim ve saklama**

13. Roller, Roller ve Yetkiler sekmesindedir; yardımcı öğretmen yalnızca rozeti görür, marka yöneticisi ayrıntı görmez.
14. Her erişim denetim izine düşer; saklama süreleri KVKK tablosundadır, kaza kayıtları yasal süreye tabidir (doğrulanmalı).
15. Veli sağlık kayıtlarını PDF olarak alabilir; veri paketine (08) dahildir.

## Veri, ekranlar ve bildirimler

**Varlıklar**

| Varlık | Anahtar alanlar | Not |
| --- | --- | --- |
| Sağlık profili | öğrenci, kan grubu, doktor, doğrulayan, rıza durumu | Özel nitelikli |
| Alerji | profil, tür, şiddet, tepki, önlem | Rozeti besler |
| Kronik durum | profil, ad, eylem planı, sürekli ilaç | Eylem planı serbest metin |
| Diyet kısıtı | profil, tür, açıklama | 13 Menü kullanır |
| İlaç talebi | öğrenci, ilaç, doz, saatler, tarihler, reçete, durum, onaylayan | Bitiş tarihinde kendiliğinden kapanır |
| İlaç uygulama kaydı | talep, tarih, saat, doz, uygulayan, atlandı mı, neden | Veliye bildirilir |
| Kaza raporu | öğrenci, zaman, yer, olay, müdahale, tanık, fotoğraf, veli bildirimi, durum, kapatan | Kapatılınca değiştirilemez |
| Sağlık kontrolü | öğrenci, tarih, ateş, not | İsteğe bağlı |
| Sağlık belgesi | öğrenci, tür, dosya, yükleyen | İsteğe bağlı dosya |

**Ekranlar**

| Ekran | Platform | Rol | İçerik |
| --- | --- | --- | --- |
| Sağlık profili | Mobil (veli); web (sağlık, ofis) | Veli, sağlık sorumlusu, ofis | Alerji, kronik durum, diyet, doktor, belgeler, rıza |
| Alerji ayrıntısı | Mobil | Öğretmen | Rozetten açılır; tepki ve önlem |
| İlaç talebi | Mobil | Veli | Form, reçete fotoğrafı, onay metni |
| İlaç onay kuyruğu | Web, mobil | Sağlık sorumlusu, müdür | Bekleyen talepler, onayla veya reddet |
| Bugünkü ilaçlar | Mobil | Öğretmen | Sınıf listesi, saat, verildi veya atlandı |
| Kaza bildirimi | Mobil | Öğretmen | Form, fotoğraf, veliye gönder |
| Kaza raporları | Web | Okul müdürü | Liste, kapat, istatistik |
| Kronik durum listesi | Web | Sağlık sorumlusu | Sınıf bazında eylem planları |

**Bildirimler**

| Olay | Alıcı | Kanal | Zamanlama |
| --- | --- | --- | --- |
| İlaç talebi geldi | Sağlık sorumlusu, müdür | Uygulama içi | Anında |
| Talep onaylandı veya reddedildi | Veli | Anlık bildirim | Anında |
| Bugün verilecek ilaçlar | Sınıf öğretmeni | Anlık bildirim | 08:00 |
| İlaç verildi veya atlandı | Veli | Anlık bildirim | Anında |
| Doz saati geçti, uygulanmadı | Öğretmen, sağlık sorumlusu | Uygulama içi | 30 dakika sonra |
| Kaza raporu | Tam ve sınırlı veliler | Anlık bildirim, SMS | Anında, acil öncelik |
| Kaza raporu kapatıldı | Veli | Uygulama içi | Anında |
| Sağlık rızası geri alındı | Sağlık sorumlusu, ofis | Uygulama içi | Anında |

## Uç durumlar, kabul kriterleri ve açık sorular

**Uç durumlar**

- Veli sağlık rızası vermiyor ama çocuğun alerjisi var: ofis veliyle görüşür; sistem rızasız alan açmaz; alerji bilgisinin rıza dışı dayanakla tutulması kararı hukuk görüşüne göre verilir (S21).
- Reçetesiz ilaç talebi: okul ayarı reçete zorunluysa talep bekler; sağlık sorumlusu veliden reçete ister.
- Öğretmen izinli: geçici öğretmen o günün ilaç listesini görür ve uygulama kaydı yapar.
- Kaza anında veliye ulaşılamıyor: acil kişiler sırayla aranır; aramalar raporda kaydedilir.
- İki velinin farklı ilaç talebi: talepler “çelişkili talep” olarak sağlık sorumlusuna düşer; çözülene kadar hiçbiri uygulanmaz, iki veli de bilgilendirilir.
- Mesajda sağlık bilgisi: 05'teki kısayol “doğrulama bekleyen öneri” oluşturur; sağlık sorumlusu veya ofis doğrulayınca profile işlenir; mesaj saklanır.
- Çocuk nakil oldu: profil kişi kaydıyla taşınır; rıza hedef okulda geçerliliğini korur (aynı veri sorumlusu).

**Kabul kriterleri**

- Alerji rozeti sınıf listesi, yoklama, menü ve günlük rapor ekranlarında görünür (otomatik test).
- Yardımcı öğretmen API'si alerji ayrıntısı ve ilaç verisi döndürmez (otomatik test).
- Rıza geri alınınca sağlık alanları 60 saniye içinde tüm ekranlardan kalkar (otomatik test).
- İlaç verildi bildirimi 1 dakika içinde veliye ulaşır.
- Kaza raporu gönderildikten sonra anlık bildirim 1 dakika içinde veliye ulaşır; 5 dakika içinde açılmazsa SMS gider (09 acil kuralı).

**Açık sorular**

- [ ] Her okulda sağlık sorumlusu var mı? Yoksa müdür mü onaylar?
- [ ] Reçete zorunlu mu? (Öneri: reçeteli ilaçlarda evet)
- [ ] Alerji bilgisi rıza dışı bir hukuki dayanakla işlenebilir mi? (hukuk görüşü; S21)
- [ ] Ateş ölçüm kaydı kullanılacak mı, eşik kaç derece?
- [ ] Sağlık verisi saklama süreleri ve kaza kayıtlarının yasal süresi.
