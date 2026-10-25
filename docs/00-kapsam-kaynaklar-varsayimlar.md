# Ortak kapsam, kaynaklar ve varsayımlar

**Makine:** Karmetal VEGA 650×650 S-LINE. **Yöntem:** Açık kaynaklara dayalı kör analiz. **Hazırlama tarihi:** 25 Ekim 2026.

Bu dosya, üç çalışma kağıdının ortak kabul defteridir. Sahada tarama, port kontrolü, kimlik bilgisi denemesi, fiziksel inceleme veya safety testi yapılmamıştır. “Mevcut” ifadesi aşağıdaki **eğitim senaryosunun başlangıç durumudur**; üreticide veya müşteride tespit edilmiş bir zafiyet anlamına gelmez.

## 1. Sistem sınırı

Kapsam; makinenin endüstriyel PC'si, varsayılan kontrolörleri, sürücüleri, hidrolik kontrolü, safety giriş/çıkışları, yerel bakım istasyonu ve uzaktan bakım yoludur. İşletme ağı ve servis sağlayıcı bilgisayarı güvenilmeyen dış sınır olarak ele alınır. SCADA, robot ve üretim hattı entegrasyonu eklenmemiştir. Opsiyonel ICS ve tam otomatik yükleme sistemi kurulu kabul edilmemiştir.

İlk haftanın [normal/safety şeması](01-sistem-semasi.md) işlevsel temeldir. İkinci haftadaki ağ çizimi, bu şemadaki blokların haberleşme ve bakım sınırlarını ayrıntılandırır; farklı bir makine değildir.

## 2. Bilgi türleri

| İşaret | Anlam | Kullanım |
|---|---|---|
| D | Üretici kaynağında belirtilen | Özelliğin varlığı doğrulanır; ağ bağlantısı veya güvenlik yeterliliği otomatik doğrulanmaz. |
| V | Analiz için varsayılan | Eksik teknik ayrıntı veya çalışma kağıdından alınan başlangıç zayıflığıdır. |
| H | Hedef öneri | Uygulandığı/test edildiği iddia edilmeyen iyileştirmedir. |

## 3. Doğrulanan bilgiler

| Kod | Üreticide belirtilen özellik | Analizdeki kullanım | Kaynak |
|---|---|---|---|
| D01 | 15,6 inç endüstriyel PC ve IPS | Operatör arayüzü ve kesim verileri | K01 |
| D02 | Servo gövde ve malzeme sürme | Hareket kontrolü | K01 |
| D03 | Hidrolik mengeneler ve şerit germe | Tutma ve hidrolik tehlikeler | K01 |
| D04 | Kabin ve temassız dönme sensörü | Koruyucu yapı ve proses geri bildirimi | K01 |
| D05 | Soğutma ve talaş konveyörü | Yardımcı ekipman | K01 |
| D06 | Wi-Fi ile uzaktan bağlantı; ayrıca LAN | Bağlantı sınırları | K01, K02 |
| D07 | Ön tanımlı malzeme kütüphanesiyle otomatik parametre ayarı | Reçete/veri bütünlüğü | K02 |

## 4. Ortak varsayım defteri

V01–V08 ilk haftadan korunmuştur. Sonraki kabuller şablonları VEGA'ya uyarlamak içindir.

| Kod | Kabul ve kapsam | Doğrulamak için gereken kanıt |
|---|---|---|
| V01 | Endüstriyel PC, ayrı standart PLC/kontrolör ile haberleşir. | Elektrik şeması, cihaz envanteri. |
| V02 | Kontrolör, motor/servo sürücülerini, hidrolik çıkışları ve proses geri bildirimlerini yönetir. | I/O listesi ve ağ çizimi. |
| V03 | Ayrı Safety PLC, güvenli I/O, çift kanallı acil durdurma ve kapı emniyet kilidi vardır. | Safety projesi, devre ve cihaz bilgileri. |
| V04 | İlgili sürücüler uygun güvenli duruş/STO yeteneğine sahiptir. | Sürücü kılavuzu ve safety ayarları. |
| V05 | Gövde ve malzeme için uygun mekanik/hidrolik tutma düzeni vardır. | Fren/valf şeması ve test kayıtları. |
| V06 | Safety duruş, kilit ve çıkış geri bildirimlerini izler; proses sensörü safety sensörü yerine sayılmaz. | Güvenli giriş/çıkış eşleştirmesi. |
| V07 | Reset yereldir ve otomatik yeniden başlatmaz. | İşlev tanımı ve doğrulama testi. |
| V08 | Safety durdurma kararı HMI, normal PLC ve uzak bağlantı onayından bağımsızdır. | Safety proje incelemesi ve bağımsızlık testi. |
| V09 | Başlangıç senaryosunda servis erişimi internete doğrudan açıktır ve ortak servis hesabı kullanılır; MFA yoktur. | Gerçekte böyle olduğu bilinmiyor; güvenlik duvarı ve hesap kayıtları gerekir. |
| V10 | Bir bakım mühendislik istasyonu bulunur; başlangıçta normal kontrol ve safety programlama araçlarına erişebilir. Safety yazma yolu, üretim komut yolundan ayrıdır fakat yeterince kısıtlı değildir. | Bakım topolojisi ve yazma yetkileri. V08 ile çelişmez: çalışma bağımsızlığı, programın değiştirilemezliği değildir. |
| V11 | Şablonu uygulamak için PC/HMI üzerinde port 80 HTTP servis arayüzü ve varsayılan ortak servis hesabı riski kabul edilir. “admin/admin” gerçek parola bulgusu değildir. | Ürün/sürüm ve yapılandırma incelemesi; herhangi bir giriş denemesi yapılmadı. |
| V12 | Şablondaki iki kilitsiz USB portu, PC/bakım bilgisayarı için eğitim kabulüdür; gerçek port sayısı bilinmiyor. | Fiziksel envanter ve cihaz kontrol politikası. |
| V13 | Wi-Fi erişim altyapısı varsayılır; şablondaki görünür/paylaşılan parola başlangıç zayıflığı kabulüdür. AP'nin makineye gömülü mü haricî mi olduğu bilinmiyor. | Kablosuz tasarım ve erişim politikası. |
| V14 | Bulut telemetrisi doğrulanmadığından temel kurulumda yoktur. Yalnız şablonun bulut maddesini cevaplamak için koşullu varlık olarak değerlendirilir. | Entegrasyon sözleşmesi ve veri akışı. |
| V15 | Başlangıçta OT bakım segmentasyonu, oturum kaydı ve değişiklik onayı yetersizdir. PLC'den safety'ye üretim yazması kabul edilmez; risk bakım/programlama yoludur. | ACL, kayıt ve değişiklik süreci incelemesi. |
| V16 | Operatör yükleme, parça çıkarma ve sıkışma giderme sırasında makine çevresinde bulunur. Gerçek sıklık bilinmediğinden E puanı senaryo bazında varsayılır. | İş analizi ve vardiya gözlemi. |

Hedefte V09, V11–V13 ve V15'teki zayıflıklar giderilir. V10'daki safety yazma yolu uzaktan erişime kapatılır; yalnız yerel ve yetkili değişiklik süreciyle kullanılır. Hedef önlemler, başlangıç risk puanları hesaplanırken uygulanmış sayılmaz.

## 5. Değişmeyen safety ilkesi

Tehlikeli testere/besleme hareketi durmalı; gövde düşmemeli, malzeme tehlikeli biçimde bırakılmamalı ve kendiliğinden yeniden başlama olmamalıdır. HMI veya internet bağlantısı kaybı bu işlevi geçersiz kılamaz. STO tek başına yük tutma, anında durma veya elektriksel izolasyon değildir. Bakımda enerji izolasyonu ve depolanmış enerjilerin kontrolü ayrıca gerekir.

Bu analiz PLr, PL, SIL veya IEC 62443 SL-T seviyesi atamaz; bunlar gerekli veri ve doğrulama olmadan kanıtlanamaz. L×S×E, hocanın eğitim ölçeğidir; safety güvenilirlik hesabı değildir.

## 6. Kaynaklar

| Kod | Kaynak | Neye dayanak? |
|---|---|---|
| K01 | [Karmetal ürün sayfası](https://www.karmetal.com.tr/urun/45/vega-650x650-s-line.html) | Makine özellikleri. |
| K02 | [Karmetal S-LINE tanıtımı](https://www.karmetal.com.tr/haber/4/vega-650x650-s-line.html) | LAN/Wi-Fi, otomatik parametre ayarı. |
| K03 | [ANSI/ISA-62443-3-2-2020 resmî önizleme, kapsam ve conduit tanımı](https://www.isa.org/getmedia/661c718f-8e64-446d-acf9-2c6286db1b33/isa-62443-3-2-preview.pdf) | Sistemi zone/conduit'e ayırma, risk ve gereksinimleri belgeleme yaklaşımı. |
| K04 | [NIST SP 800-82 Rev.3, OT Security](https://csrc.nist.gov/pubs/sp/800/82/r3/final) | OT segmentasyonu ve uzaktan erişim ilkeleri; özellikle 6.2.10. Rev.4 taslağı ile karıştırılmadan yayımlanmış Rev.3 kullanıldı. |
| K05 | [Siemens, Hanging loads, bölüm 2.4](https://cache.industry.siemens.com/dl/files/260/109807260/att_1104659/v1/109807260_HangingAxis_DOC_v11_en.pdf) | Yerçekimi etkisindeki eksende STO ve tutma ilişkisinin genel açıklaması. VEGA'nın Siemens kullandığını göstermez. |
| T02 | Öğretmenin 193127 isimli çalışma kağıdı | Varlıklar, zone/conduit ve altı uzak erişim kararı. |
| T03 | Öğretmenin 193155 isimli çalışma kağıdı | Üç senaryo, L×S×E, S=3 öncelik kuralı. |
| T04 | Öğretmenin 193213 isimli çalışma kağıdı | Mevcut–hedef uzak erişim ve functional safety köprüsü. |

Web kaynakları 25 Ekim 2026 tarihinde kontrol edilmiştir. Şablonlardaki PaketPro/çene/robot ifadeleri, VEGA'nın testere, gövde, besleme ve mengene işlevlerine uyarlanmıştır.
