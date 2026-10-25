# Karmetal VEGA 650×650 S-LINE - Endüstriyel Siber Güvenlik Analizi

VEGA şerit testere makinesinin, üreticinin internetten erişilebilen bilgileri ve açıkça belirtilen varsayımlar üzerinden hazırlanan eğitim amaçlı **kör analizi**. Üreticinin doğrulanmış ağ/elektrik projesi veya makinede tespit edilmiş zafiyet raporu değildir.

## Okuma sırası

| Bölüm | İçerik |
|---|---|
| [00 - Kapsam, kaynaklar ve varsayımlar](docs/00-kapsam-kaynaklar-varsayimlar.md) | D: doğrulanan bilgi; V: varsayım; H: hedef öneri. Bütün haftaların ortak kabulleri. |
| [01 - Normal kontrol ve safety şeması](docs/01-sistem-semasi.md) | Önceden hazırlanan ilk hafta sistem modeli. |
| [02 - Hafta 2: Zone / conduit](docs/02-hafta-zone-conduit.md) | Varlık grupları, geçiş kontrolleri, diyagramlar ve altı uzak erişim kararı. |
| [03 - Hafta 3: Risk değerlendirmesi](docs/03-hafta-risk-degerlendirmesi.md) | Üç siber-fiziksel senaryo, L×S×E, risk matrisi ve öncelik cevapları. |
| [04 - Hafta 4: Güvenli uzaktan erişim](docs/04-hafta-guvenli-uzaktan-erisim.md) | Mevcut/hedef, beş tasarım ilkesi ve üç safety gereksinimi. |
| [05 - İzlenebilirlik ve kanıt planı](docs/05-izlenebilirlik-ve-kanit-plani.md) | Şablon/EP eşleştirmesi, önlem kodları ve yapılması gereken doğrulamalar. |

## Kapsam ve sınırlar

Makineye saha erişimi, aktif tarama, parola denemesi veya safety testi yapılmamıştır. İnternete açık servis, ortak hesap, HTTP arayüzü ve USB zayıflıkları öğretmenin şablonunu uygulamak için kabul edilen başlangıç koşullarıdır; Karmetal hakkında bulgu değildir. PLC/Safety PLC ve güvenli tutma mimarisi varsayımsaldır. Opsiyonel ICS ve otomatik yükleme ana modele dahil değildir; bulut yalnız koşullu değerlendirilir.

Safety hedefi: tehlikeli hareketin durması, gövde/malzemenin güvenle tutulması ve beklenmedik yeniden başlatmanın engellenmesi. STO tek başına tutma veya enerji izolasyonu sağlamaz. PLr, SIL veya IEC 62443 uygunluk seviyesi atanmaz. Önerilen kontroller uygulanmış sayılmaz; riskler doğrulama beklemektedir.

Üç çalışma kağıdındaki PaketPro ifadeleri VEGA'ya uyarlanmış; Görev A/B sırası ve teslim başlıkları korunmuştur. İlk hafta için önceden hazırlanan sistem şeması korunmuştur. GitHub, Mermaid diyagramlarını doğrudan görüntüleyebilir. VS Code'da Markdown dosyaları Ctrl+Shift+V ile önizlenebilir.

## Temel kaynaklar

- [Üretici ürün sayfası](https://www.karmetal.com.tr/urun/45/vega-650x650-s-line.html)
- [Üretici S-LINE tanıtımı](https://www.karmetal.com.tr/haber/4/vega-650x650-s-line.html)
- [NIST SP 800-82 Rev.3](https://csrc.nist.gov/pubs/sp/800/82/r3/final)

Kaynak ayrıntıları ve kabulleri doğrulamak için gereken belgeler 00 numaralı dosyadadır. Hazırlama: 25 Ekim 2026.
