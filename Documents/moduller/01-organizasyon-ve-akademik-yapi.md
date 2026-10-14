# 01 Organizasyon ve Akademik Yapı

Marka → okul → eğitim yılı → sınıf → öğrenci hiyerarşisi tüm modüllerin omurgasıdır; okul ve sınıf sayısı sınırsızdır, ayarlar marka ve okul düzeyinde katmanlıdır.

## Amaç, kapsam ve aktörler

Modül markanın okul, eğitim yılı, yaş grubu ve sınıf yapısını tanımlar; diğer tüm modüller bu yapıya bağlanır. Yıl sonu devir (sınıfların bir üst yaş grubuna taşınması, mezuniyet grubunun 08'e devri) ve ayarların marka ile okul katmanları burada yönetilir.

**Kapsam içi**

- Marka: ad, logo, renkler (uygulama teması), marka varsayılan ayarları.
- Okul: ad, adres, iletişim, çalışma saatleri, okul ayarları (yoklama saati, yoklama kilit saati, sessiz saatler, kapanış saati), durum.
- Eğitim yılı: okul bazında başlangıç ve bitiş, dönem tarihleri (dönem sayısı marka ayarı, 07), okul takvimi (gün türü: okul günü, tatil, yarım gün, kapalı); bir aktif, bir planlanan yıl.
- Yaş grubu: marka standardı (örneğin 24–36 ay, 3 yaş, 4 yaş, 5 yaş, hazırlık), doğum tarihi kuralı, mezuniyet grubu işareti.
- Sınıf: okul, yıl, yaş grubu, ad, kapasite, sorumlu ve yardımcı öğretmenler, derslik, durum.
- Öğretmen–sınıf ataması: tarih aralıklı; izinde geçici atama.
- Yıl sonu devir sihirbazı: yeni yıl, sınıf şablonları, öğrenci taşıma ve mezuniyet önizlemesi, öğretmen atamaları.
- Ayar katmanları: marka varsayılanı, okul geçersiz kılması, markada kilit.

**Kapsam dışı**

- Ders programı ve derslik planlaması (okul öncesinde günlük akış 07 ve 12'de ele alınır).
- Personel özlük bilgileri (14 İleri Faz, İK).
- İkinci marka ekleme ekranı: model hazır, işlev kapsam dışı (K1).

**Aktörler**

| Aktör | Modüldeki işi |
| --- | --- |
| Marka yöneticisi | Okulları, yaş gruplarını, standart ayarları ve eğitim yılı şablonunu tanımlar; okullar arası doluluğu izler |
| Okul müdürü | Okul ayarlarını, sınıfları ve öğretmen atamalarını yönetir; yıl sonu devrini yürütür |
| Ofis | Sınıf listelerini görür; öğrenci atamasını 03'te yapar |
| Öğretmen | Atandığı sınıfları görür ve aralarında geçiş yapar |
| Sistem | Yıl başlangıcında durum geçişlerini ve geçici atama bitişlerini uygular |

## Kullanıcı hikayeleri

| ID | Rol | Hikaye | Öncelik | Faz |
| --- | --- | --- | --- | --- |
| OR-01 | Marka yöneticisi | Markaya yeni bir okul ekleyip müdürünü atamak istiyorum, böylece okul kendi kurulumunu yapabilsin. | Must | MVP |
| OR-02 | Marka yöneticisi | Yaş gruplarını ve doğum tarihi aralıklarını markada bir kez tanımlamak istiyorum, böylece tüm okullar aynı gruplamayı kullansın. | Must | MVP |
| OR-03 | Okul müdürü | Eğitim yılı için sınıfları (ad, yaş grubu, kapasite) oluşturmak istiyorum, böylece kayıtlar sınıfa atanabilsin. | Must | MVP |
| OR-04 | Okul müdürü | Her sınıfa sorumlu ve yardımcı öğretmen atamak, izinde geçici öğretmen eklemek istiyorum, böylece sınıf hiç sahipsiz kalmasın. | Must | MVP |
| OR-05 | Okul müdürü | Yoklama saati, sessiz saatler ve kapanış saati gibi okul ayarlarını değiştirmek istiyorum, böylece okulun düzenine uysun. | Must | MVP |
| OR-06 | Marka yöneticisi | Bazı ayarları markada kilitlemek istiyorum, böylece okullar standardı bozmasın. | Should | MVP |
| OR-07 | Okul müdürü | Yeni eğitim yılını önceki yılın sınıf yapısından kopyalayarak açmak istiyorum, böylece sıfırdan kurmayayım. | Must | MVP |
| OR-08 | Okul müdürü | Yıl sonunda sınıfları bir üst yaş grubuna, mezuniyet grubunu mezuniyete önizlemeli taşımak istiyorum, böylece Eylül'de tek tek uğraşmayayım. | Must | MVP |
| OR-09 | Marka yöneticisi | Okullar arası doluluk (kapasite ve kayıt) tablosunu görmek istiyorum, böylece kapasite kararı vereyim. | Should | MVP |
| OR-10 | Öğretmen | Birden fazla sınıfa atandığımda sınıflar arasında geçiş yapmak istiyorum, böylece doğru sınıfta işlem yapayım. | Should | MVP |
| OR-11 | Okul müdürü | Yıl ortasında sınıfı bölmek veya birleştirmek istiyorum, böylece geçmiş kayıtlar bozulmadan yeniden düzenleyeyim. | Could | Faz 2 |
| OR-12 | Marka yöneticisi | Bir okulu kapatmak (arşivlemek) istiyorum, böylece verileri saklama kuralına göre kalsın. | Could | Faz 2 |

## İş kuralları ve işlevsel gereksinimler

**Hiyerarşi**

1. Marka → Okul → Eğitim yılı → Sınıf → Kayıt (öğrenci). Her kayıt satırı marka ve okul kimliği taşır (Kesişen Konular, çok kiracılı yapı).
2. Okul sayısı ve okul başına sınıf sayısı sınırsızdır. Bir okulun aynı anda bir aktif eğitim yılı vardır; sonraki yıl “planlanan” durumda hazırlanır.
3. Eğitim yılı tarihleri okul bazındadır; dönem sayısı marka ayarıdır, dönem tarihleri ve rapor son tarihleri (07) yılın içinde okul tarafından tanımlanır. Okul takvimi her günün türünü tutar (okul günü, tatil, yarım gün, kapalı); yoklama (04) ve bildirim zamanlaması (09) bu takvime bağlıdır, etkinlik takvimi 06'da Faz 2'dir.

**Yaş grupları ve sınıflar**

4. Yaş grupları markada tanımlanır: ad, doğum tarihi kuralı (örneğin yılın 30 Eylül'ündeki yaş; marka ayarı), sıra, mezuniyet grubu işareti. Okul ekleyemez; kullanmadığını işaretleyebilir.
5. Sınıf = okul + eğitim yılı + yaş grubu; ad okulda benzersizdir; kapasite uyarı amaçlıdır, engel değildir; derslik serbest metindir.
6. Aktif sınıfta bir sorumlu öğretmen beklenir; eksikse sınıf “sorumlu yok” uyarısı alır ve yoklama yardımcı öğretmene açık kalır. Yardımcı öğretmen sıfır veya daha fazla olabilir. Bir öğretmen birden çok sınıfta olabilir; geçici atama tarih aralıklıdır ve kendiliğinden biter.
7. Sınıf durumu: planlanan, aktif (yıl başlayınca), arşiv (yıl bitince). Arşiv sınıf salt-okunurdur.

**Ayar katmanları**

8. Her ayarın tanımı: anahtar, değer tipi, marka varsayılanı, okul geçersiz kılabilir mi (kilit). Örnek ayarlar: yoklama saati, yoklama kilit saati (04), kapanış saati, sessiz saatler, salt-okunur süre (08), öğretmen duyuru onayı (06), müdür mesaj görünürlüğü (05), ardışık devamsızlık eşiği (04), dönem sayısı ve rapor onayı (07).
9. Ayar değişiklikleri denetim izine düşer ve ileri tarihli olabilir (yeni yıl için).

**Yıl sonu devir**

10. Devir sihirbazı adımları: yeni yıl tarihleri; sınıf şablonu (önceki yıldan kopya, yaş grubu bir üst); öğretmen atamaları; öğrenci taşıma önizlemesi (her çocuk için hedef sınıf); mezuniyet adımı (mezuniyet grubundaki çocuklar, mezuniyet tarihi varsayılan eğitim yılı bitişi; onayla 08'deki mezuniyet olayı üretilir, salt-okunur süre o tarihte başlar); onay. Önizleme Excel'e aktarılabilir.
11. Sınıf taşıma yeni yılın ilk gününde yürürlüğe girer; o güne kadar mevcut yıl aktif kalır. Mezuniyet seçilen mezuniyet tarihinde işlenir (08). Onay 72 saat içinde geri alınabilir.
12. Yıl ortasında eklenen sınıf anında aktif olur; kapatılan sınıfın öğrencileri önce başka sınıfa taşınır.

**Marka hazırlığı**

13. Marka kimliği her kayıtta bulunur; ikinci marka eklemek yalnızca yönetim ekranı işi olur. Kullanıcı hesapları marka kapsamlıdır; markalar arası kullanıcı paylaşımı yoktur (K1).

## Veri, ekranlar ve bildirimler

**Varlıklar**

| Varlık | Anahtar alanlar | Not |
| --- | --- | --- |
| Marka | ad, logo, tema renkleri, varsayılan ayarlar | Tek kayıt; model çoklu markaya hazır |
| Okul | marka, ad, adres, iletişim, çalışma saatleri, durum | Kendi takvimi ve ayarları vardır |
| Eğitim yılı | okul, ad, başlangıç, bitiş, durum (planlanan / aktif / arşiv) | Okul başına bir aktif |
| Okul takvimi günü | okul, eğitim yılı, tarih, gün türü (okul günü / tatil / yarım gün / kapalı), açıklama | 04 ve 09 bu takvimi kullanır; yıl şablonundan kopyalanır |
| Yaş grubu | marka, ad, doğum tarihi kuralı, sıra, mezuniyet grubu mu | Marka düzeyinde; mezuniyet işareti yalnızca burada |
| Sınıf | okul, yıl, yaş grubu, ad, kapasite, derslik, durum | Ad okulda benzersiz |
| Öğretmen ataması | sınıf, kullanıcı, rol (sorumlu / yardımcı / geçici), başlangıç, bitiş | Yetki kapsamını belirler |
| Ayar tanımı | anahtar, tip, marka varsayılanı, kilit | Kod tarafında tanımlı |
| Ayar değeri | kapsam (marka / okul), anahtar, değer, geçerlilik tarihi | Denetim izli |
| Devir işlemi | okul, kaynak yıl, hedef yıl, plan (çocuk → hedef sınıf), durum, onaylayan, geri alma süresi | 72 saat içinde geri alınabilir |

**Ekranlar**

| Ekran | Platform | Rol | İçerik |
| --- | --- | --- | --- |
| Marka ayarları | Web | Marka yöneticisi | Logo, tema, varsayılan ayarlar ve kilitler |
| Okullar | Web | Marka yöneticisi | Liste, okul kartı, müdür atama, durum |
| Yaş grupları | Web | Marka yöneticisi | Ad, doğum tarihi kuralı, sıra, mezuniyet işareti |
| Eğitim yılları | Web | Okul müdürü | Yıl listesi, tarihler, dönemler, durum |
| Okul takvimi | Web | Okul müdürü | Gün türleri, tatil aralıkları, yarım günler; önceki yıldan kopya |
| Sınıflar ve atamalar | Web | Okul müdürü | Sınıf kartı, kapasite ve doluluk, öğretmenler, geçici atama |
| Ayarlar | Web | Marka yöneticisi, okul müdürü | Katman göstergesi (marka / okul), kilitli ayarlar salt-okunur |
| Yıl sonu devir sihirbazı | Web | Okul müdürü | 5 adım, önizleme, Excel aktarımı, onay, geri al |
| Doluluk tablosu | Web | Marka yöneticisi | Okul ve sınıf bazında kapasite, kayıt, aday |
| Sınıflarım | Mobil | Öğretmen | Sınıf seçici, atama bilgisi |

**Bildirimler**

| Olay | Alıcı | Kanal | Zamanlama |
| --- | --- | --- | --- |
| Sınıfa atandınız veya atama bitti | Öğretmen | Anlık bildirim | Anında |
| Geçici atama başladı veya bitti | Öğretmen, müdür | Uygulama içi | Tarihinde |
| Yeni eğitim yılı planlandı | Ofis, öğretmenler | Uygulama içi | Anında |
| Devir tamamlandı | Müdür, marka yöneticisi, ofis | E-posta | İşlem sonunda |
| Marka kilitli ayarı değişti | Okul müdürleri | Uygulama içi | Anında |
| Kapasite aşıldı | Okul müdürü | Uygulama içi | Kayıt anında |

## Uç durumlar, kabul kriterleri ve açık sorular

**Uç durumlar**

- Okulların başlangıç tarihleri farklı: yıl ve devir okul bazında yürür; marka raporları eğitim yılı adıyla hizalanır.
- Yaş grubu kuralına uymayan çocuk: uyarı verilir, müdür onayıyla izin verilir, neden kaydedilir.
- Sorumlu öğretmen ayrıldı: sınıf “sorumlu yok” uyarısı alır; yoklama yardımcı öğretmene açık kalır.
- Devir önizlemesinde hedef sınıfı olmayan çocuk: “atanmadı” listesine düşer; müdür sınıf atar veya çocuğu sınıfsız kayıtlı bırakır.
- İki yılda aynı sınıf adı: yıl etiketiyle ayrışır; raporlar yıl filtresi taşır.
- Marka logosu veya teması değişti: uygulama bir sonraki açılışta yeni temayı alır.
- Okul kapatıldı: kayıtlar 08 kuralıyla kapanır, veriler saklama süresince kalır, personel hesapları kapatılır.
- Bir öğretmen iki okulda çalışıyor: tek hesap, okul bazında atama; uygulamada okul seçici.

**Kabul kriterleri**

- Yeni okul kurulumu (okul, 5 sınıf, 5 öğretmen) 15 dakikada tamamlanır.
- Markada kilitli ayar okul ekranında salt-okunurdur ve API değişiklik isteğini reddeder (otomatik test).
- Devir önizlemesi 300 çocuk için 10 saniyede üretilir ve Excel'e aktarılır.
- Devir sonrası eski yılın yoklama ve raporları değişmeden okunur (otomatik test).
- Öğretmen API'si yalnızca atanmış sınıfları döndürür (otomatik test).

**Açık sorular**

- [ ] Yaş grubu kesim tarihi (30 Eylül?) ve grup adları markada nasıl tanımlı?
- [ ] Mezuniyet grubu tek mi (hazırlık), yoksa 5 yaş da mezun olabilir mi?
- [ ] Kapasite engel mi, uyarı mı? (Öneri: uyarı)
- [ ] Okullar arası öğretmen paylaşımı var mı? (Model destekler)
- [ ] Okulun kendi logosu olacak mı, yoksa yalnızca marka logosu mu?
