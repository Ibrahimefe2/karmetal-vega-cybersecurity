# Hafta 3 - Tehdit senaryoları ve risk değerlendirmesi

**Şablon:** T03 / 193155. **Makine:** VEGA 650×650 S-LINE. **Tarih:** 25 Ekim 2026.

[Ortak kabuller](00-kapsam-kaynaklar-varsayimlar.md) ve [zone/conduit](02-hafta-zone-conduit.md) geçerlidir. Olaylar gerçek zafiyet bulgusu değil, başlangıç varsayımlarına dayalı senaryolardır. Hedef kontroller puanlamada uygulanmış sayılmamıştır.

## Ölçek: L × S × E

Şablonun 1–3 ölçeği aşağıdaki çalışma tanımlarıyla kullanılmıştır. Gerçek olay sıklığı ve maruziyet ölçülmemiştir.

| Puan | L - Bütün olay zincirinin olasılığı | S - Fiziksel sonuç şiddeti | E - İnsan maruziyeti |
|---|---|---|---|
| 1 | Birden fazla ek koşul ve dar fırsat gerektirir. | Hafif yaralanma veya yaralanmasız sonuç. | Seyrek özel bakım. |
| 2 | Ek erişim/süreç koşullarıyla mümkün. | Tıbbi müdahale gerektirebilen yaralanma. | Aralıklı yükleme veya müdahale. |
| 3 | Varsayılan zayıflıkta erişim belirgin ve tekrar kullanılabilir. | Kalıcı hasar, uzuv kaybı veya ölüm. | Sık veya uzun süreli tehlikeye yakınlık. |

L yalnız ilk girişin kolaylığı değildir; E saldırı sıklığı değildir. **S=3 olan senaryo toplamı düşük olsa bile ayrıca öncelikli incelenir.** Bu eğitim ölçeği PLr/SIL hesabı veya nicel kaza olasılığı değildir.

## Görev - Üç senaryo kurun ve puanlayın

### R01 - IPS malzeme kütüphanesinin sinsi değiştirilmesi

**Kim / hangi kapı:** Ortak servis hesabını ele geçiren dış saldırgan, V09/V11 kapsamındaki doğrudan uzak servis yolundan A05 PC/HMI'ya erişir.

**Ne yapar:** Belirli bir malzemenin kesim parametrelerini değiştirir; ekranda normal malzeme adı kalır. Uygulamanın bu veriye yazma yetkisi verdiği ayrıca senaryo kabulüdür; gerçek veri biçimi ve izinler bilinmiyor.

**Zincir:** Bozuk reçete seçilir → normal PLC genel hareket sınırları içinde fakat malzemeye uygunsuz hız/ilerleme uygular → titreşim, sıkışma veya şerit hasarı oluşur → operatör sıkışma giderme ve keskin artık temizleme ihtiyacı duyar.

**Fiziksel sonuç:** Bu senaryoda safety ve kapı koruması çalışır; hareketli bölgeye erişim güvenli duruşla engellenir. Ancak keskin talaş veya hasarlı şeritle müdahalede tıbbi müdahale gerektiren el kesilmesi mümkündür. Koruyucuyu aşan parça fırlaması veya hareketli testereye temas için ek koşul kurulmadığından bu sonuçlar senaryoya eklenmemiştir.

**Varlık / yol:** A05, A07–A10; başlangıçta Z0→Z3, ardından C04. **Kabuller:** V01–V02, V09, V11, V15–V16; V03–V08 geçerli kalır.

**L=3, S=2, E=2 → 12.** Servis yolu tekrar kullanılabilir; tehlikeye yaklaşma sürekli değil, müdahale sırasında aralıklıdır.

**Önlemler:** H01 güvenli servis erişimi; H02 reçete sürümü/onayı/bütünlüğü; H03 normal kontrolde uygun proses sınırları; H04 sıkışmada izolasyon ve keskin parça prosedürü. Proses sınırı tek başına safety işlevi değildir.

### R02 - Bakım projesinden kapı korumasının etkisizleştirilmesi

**Kim / hangi kapı:** Ele geçirilmiş bakım oturumu veya zararlı proje taşıyan USB üzerinden A04'e erişen saldırgan; V10/V12/V15 nedeniyle yeterince sınırlanmamış C07 programlama yolunu kullanır.

**Ne yapar:** Kapı kilidi, duruş ve kapı açma koşullarının ilişkisini bozan yetkisiz safety projesinin yüklenmesini sağlar.

**Ek koşul:** A04'ü ele geçirmek yeterli değildir. Safety yazma yetkisi, gerekli cihaz modu/yerel izin ve proje kabul koşullarının da aşılması veya kötüye kullanılması gerekir. Bunlar korunuyorsa zincir kesilir. Bu korumaların yetersizliği yalnız başlangıç senaryosu kabulüdür.

**Zincir:** Bakım istasyonu ele geçirilir → yetkisiz safety projesi kabul edilir → kapı tehlike bitmeden açılabilir ve açılması hareketi güvenle durdurmaz → operatör parça çıkarma/sıkışma müdahalesinde bölgeye yaklaşır → hareketli testere/beslemeyle temas oluşabilir.

**Fiziksel sonuç:** Derin kesilme, uzuv kaybı veya ölüm. Ağır sonuç sıradan HMI komutundan değil, ek koşullarla safety uygulamasının değiştirilmesinden doğar. V08 çalışma sırasındaki karar bağımsızlığıdır; yeniden programlamaya bağışıklık değildir.

**Varlık / yol:** A04, A11–A12, A08; C07 ve C06. **Kabuller:** V03–V04, V06, V10, V12, V15–V16.

**L=2, S=3, E=2 → 12.** Çok aşamalı erişim L'yi sınırlar; aralıklı operatör erişimi E=2'dir. **İlk müdahale önceliği.**

**Önlemler:** H05 uzak oturumda bütün safety yazma yollarını kapatma; H06 yerel fiziksel izin ve iki kişiyle onay; H07 proje kimliği, bağımsız inceleme ve yeniden doğrulama; H08 bakım bilgisayarı ve USB kontrolü.

### R03 - Bakım yedeğiyle gövde tutma sırasının bozulması

**Kim / hangi kapı:** Ele geçirilmiş A04 veya değiştirilmiş sürücü/safety yedeği üzerinden işlem yaptıran saldırgan.

**Ne yapar:** Gövde tutma/fren bırakma sırasını ve bunu denetleyen güvenli ayarı değiştirir. Yalnız normal PLC ayarının değişmesi V05 bağımsız tutmayı aşmak için yeterli sayılmaz.

**Ek koşul:** İlgili yapılandırma yazılabilir olmalı ve bağımsız tutma/izleme de aynı bakım değişikliğinden etkilenmelidir. Gerçek tasarım bilinmiyor; değiştirilemez mekanik ikinci koruma varsa bu sonuç yeniden değerlendirilir.

**Zincir:** Yetkisiz yedek geri yüklenir → tutma ve izleme ayarı birlikte bozulur → seyrek gövde altı bakımında kişi tehlikeli bölgede bulunur → tork kesilirken tutma beklenen sırada devreye girmez → gövde yerçekimiyle hareket edebilir.

**Fiziksel sonuç:** Ezilme, kalıcı yaralanma veya ölüm. Bunun için uygun enerji izolasyonu ve mekanik desteğin de uygulanmamış/yetersiz olması gerekir; doğru izolasyon ve destek zinciri keser.

**Varlık / yol:** A04, A08, A10–A12; C03/C07, C06. **Kabuller:** V04–V05, V10, V15–V16 ve yukarıdaki ek koşullar.

**L=1, S=3, E=1 → 3.** Birden çok koruma kusuru ve seyrek bakım birlikte gerekir. Düşük çarpım ağır sonucu kabul edilebilir yapmaz.

**Önlemler:** H06–H07 değişiklik kontrolü; H09 doğrulanmış tutma sırası, izolasyon, depolanmış enerji kontrolü ve uygun mekanik destek. Destek yerleştirme yöntemi dahil bakım işi yetkili uzman tarafından belirlenmelidir.

## İlk Risk Register

| Risk | L | S | E | Skor | S=3 bayrağı | Önerilen sorumlu / işlem |
|---|---:|---:|---:|---:|---|---|
| R01 - IPS verisi | 3 | 2 | 2 | 12 | Hayır | OT + proses; H01–H04. |
| R02 - Safety projesi | 2 | 3 | 2 | 12 | Evet | Safety + OT; H05–H08; ilk öncelik. |
| R03 - Gövde tutma | 1 | 3 | 1 | 3 | Evet | Bakım + safety; H06–H07/H09; tehlikeli bakım öncesi giderilmeli. |

Hepsi **açık / doğrulama bekliyor**. Sorumlular atanmış gerçek kişiler değil önerilen rollerdir. Önlemlerin etkinlik kanıtı olmadığı için azaltılmış risk puanı verilmemiştir.

## Risk matrisi

Satırlar L, sütunlar S; hücreler E ve toplamı gösterir. Boş hücre riskin yokluğunu kanıtlamaz.

| L / S | 1 | 2 | 3 - ayrıca öncelikli |
|---|---|---|---|
| 3 | — | R01: E=2, skor 12 | — |
| 2 | — | — | R02: E=2, skor 12 |
| 1 | — | — | R03: E=1, skor 3 |

### En yüksek öncelikli senaryonuz hangisi? Neden?

**R02**, R01 ile aynı skora rağmen uzuv kaybı/ölüm potansiyeli taşıdığı ve aralıklı operatör erişimiyle birleştiği için ilk sıradadır. R03 ayrıca S=3 önceliğinde tutulur.

### S=3 olup skoru düşük kalan var mı? Nasıl görünür kılacaksınız?

**R03, skor 3.** Risk kaydında S=3 bayrağı, matriste şiddet sütunu ve bakım öncesi kapatma koşulu bulunur. Düşük puan nedeniyle otomatik kabul verilmez; tutma/izolasyon kanıtı ve yetkili incelemesi gerekir.

### Siber giriş zincirinin neresini kesmek fiziksel riski azaltır?

H01 ilk erişimi; H02–H03 bozuk reçetenin uygulanmasını; H05–H08 yetkisiz safety değişikliğini sınırlar. Çalışan kapı/duruş/tutma işlevleri ve H09 fiziksel aşamada insanı korur. Tek kontrolün başarısına güvenilmez; zincir hem ağ girişinde hem fiziksel sonuca yaklaşan halkalarda kesilir.

**Çıktı:** EP-04. Genel kaynak K04; makine temeli K01–K02; ölçek T03. [Önlemler ve kanıt planı](05-izlenebilirlik-ve-kanit-plani.md).
