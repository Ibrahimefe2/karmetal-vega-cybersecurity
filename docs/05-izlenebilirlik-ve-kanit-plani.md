# İzlenebilirlik ve kanıt planı

**Durum:** Eğitim amaçlı tasarım; teknik doğrulamalar yapılmadı. EP başlıkları teslim kodlarıdır; tamamlanmış saha kanıtı değildir.

| Şablon / çıktı | Cevap |
|---|---|
| Hafta 1 - Önceden hazırlanan model | [Normal/safety şeması](01-sistem-semasi.md). İlk kağıdın bütün cevaplarının tamamlandığı iddia edilmez. |
| T02 / EP-05 | [Hafta 2](02-hafta-zone-conduit.md): A1–A3, altı erişim kararı ve şema. |
| T03 / EP-04 | [Hafta 3](03-hafta-risk-degerlendirmesi.md): üç senaryo, puanlar, matris ve öncelik cevapları. |
| T04 / EP-02 + EP-06 | [Hafta 4](04-hafta-guvenli-uzaktan-erisim.md): mevcut/hedef, B1 ve üç gereksinim. |

## Önlem ve doğrulama eşleştirmesi

| Kod | Öneri | Risk / gereksinim | Toplanacak kanıt |
|---|---|---|---|
| H01 | VPN/MFA, jump server, kişisel hesap, süreli yetki ve kayıt | R01–R03 | ACL/akış, hesap matrisi, anonim oturum kaydı ve süre dolumu testi. |
| H02 | Reçete sürümü, bütünlüğü ve değişiklik onayı | R01 | Sürüm özeti, onay ve bozuk reçete reddi testi. |
| H03 | Uygun proses sınırları | R01 | Malzeme/parametre sınırları ve kontrollü sınır testi; safety iddiası yok. |
| H04 | Sıkışma ve keskin parça prosedürü | R01 | Talimat, eğitim ve izolasyon kaydı. |
| H05 | Uzak oturumda bütün safety yazma yollarının kapatılması | R02/R03, FS-02 | Rota/yetki incelemesi; istasyonun yerel yazma yolunun da kullanılamadığının testi. |
| H06 | Yerel fiziksel izin ve iki kişiyle onay | R02/R03, FS-02 | Yetki matrisi, fiziksel izin tasarımı ve değişiklik talebi. |
| H07 | Safety/sürücü sürüm kontrolü ve yeniden doğrulama | R02/R03, FS-01–03 | Proje farkları, yedek, bağımsız inceleme ve duruş/kilit/tutma raporu. |
| H08 | Bakım bilgisayarı ve USB kontrolü | R02/R03 | İzinli cihaz/dosya politikası ve kabul kaydı. |
| H09 | Tutma, izolasyon ve mekanik destek | R03, FS-01/03 | Fren/valf devresi, yük/tutma doğrulaması, depolanmış enerji ve destek yöntemi. |

**Bütün H kodları önerildi; uygulanmadı/doğrulanmadı.** Etkinlik kanıtı olmadan risk kapanmaz ve azaltılmış skor verilmez. Sorumlular önerilen rollerdir; kabul yetkisi öğrenci analizine ait değildir.

## Olay ve üretime dönüş

Şüpheli uzak erişimde oturum kesilir; yerel sorumlu fiziksel güvenliği değerlendirir. Kayıtlar korunur, hesap/izinler iptal edilir ve onaylı yedekle dönüş hazırlanır. Ağ bağlantısını kesmek tehlikeli enerjiyi izole etmez. Üretime dönüş öncesi safety proje kimliği, tutma ve yeniden başlama koşulları doğrulanır. Safety değişikliğinde yetkili safety incelemesi ayrıca gerekir.
