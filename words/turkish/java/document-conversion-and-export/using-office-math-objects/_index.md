---
date: 2026-02-14
description: Aspose.Words for Java ile matematiği satır içinde nasıl görüntüleyeceğinizi,
  matematik denklemi ekleyeceğinizi ve Office Math nesnelerini zahmetsizce nasıl yöneteceğinizi
  öğrenin.
linktitle: Using Office Math Objects
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java'da Office Math ile Matematiği Satır İçi Görüntüleme
url: /tr/java/document-conversion-and-export/using-office-math-objects/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java'da Office Math ile Satır İçi Matematik Görüntüleme

Bu kapsamlı öğreticide, Aspose.Words for Java'da Office Math nesnelerini kullanarak **satır içi matematik görüntüleme** nasıl yapılacağını keşfedeceksiniz. Bir rapora **matematik denklemi eklemeniz** gerekse karmaşık formüllerin biçimlendirmesini ince ayar yapmanız gerektiğinde, bu kılavuz sizi her adımda yönlendirecek—Word belgesini yüklemekten son sonucu kaydetmeye kadar.

## Hızlı Yanıtlar
- **“display math inline” ne anlama geliyor?** Denklem, ayrı bir satırda değil, metin akışı içinde görünür.  
- **Hangi sınıf bir matematik nesnesini temsil eder?** Aspose.Words API'sinde `OfficeMath`.  
- **Hizalamayı değiştirebilir miyim?** Evet, `setJustification` metodunu LEFT, CENTER veya RIGHT ile kullanabilirsiniz.  
- **Bu özellik için lisansa ihtiyacım var mı?** Üretim kullanımında geçerli bir Aspose.Words for Java lisansı gereklidir.  
- **Hangi sürüm gösteriliyor?** Kod, en son Aspose.Words for Java sürümü (2026) ile çalışır.  

## “display math inline” nedir?
Satır içi matematik görüntüleme, denklemin paragraf metninin bir parçası gibi ele alınması ve çevredeki kelimelerle doğal olarak satır sonu alması anlamına gelir. Bu, okuma akışını kesmemesi gereken kısa formüller için faydalıdır.

## Aspose.Words for Java'da Office Math nesnelerini neden kullanmalısınız?
- **Denklik düzeni üzerinde hassas kontrol** (satır içi vs. görüntü).  
- **Word'ü manuel olarak açmadan** denklemlerin programatik olarak manipülasyonu.  
- **Platformlar arasında tutarlı render**; otomatik rapor oluşturma için mükemmel.  

## Önkoşullar
Başlamadan önce şunların olduğundan emin olun:

- Projenizde yüklü ve referans verilen Aspose.Words for Java.  
- Zaten bir Office Math denklemi içeren bir Word dosyası (ör. `OfficeMath.docx`).  
- Değerlendirme modunun dışında kodu çalıştıracaksanız geçerli bir lisans.  

## Adım‑Adım Kılavuz

### Belgeyi Yükleme
İlk olarak, üzerinde çalışmak istediğiniz Office Math denklemini içeren belgeyi yükleyin:

```java
Document doc = new Document("Your Directory Path" + "OfficeMath.docx");
```

### Office Math Nesnesine Erişim
Belgeden ilk Office Math düğümünü alın:

```java
OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
```

### Görüntü Tipini Ayarla (Inline vs. Display)
Denklemin çevredeki metinle satır içinde mi yoksa ayrı bir satırda mı görüneceğini kontrol edin. **display math inline** için `INLINE` enum'ını, ayrı bir satır için `DISPLAY` kullanın:

```java
officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
```

*Denklemin satır içinde kalmasını istiyorsanız, `DISPLAY` yerine `INLINE` yazın.*

### Hizalamayı Ayarla
Denklemin hizalamasını ayarlayın. Aşağıda sola hizalıyoruz, ancak `CENTER` veya `RIGHT` da seçebilirsiniz:

```java
officeMath.setJustification(OfficeMathJustification.LEFT);
```

### Değiştirilen Belgeyi Kaydet
Son olarak, değişiklikleri yeni bir dosyaya kaydedin:

```java
doc.save("Your Directory Path" + "ModifiedOfficeMath.docx");
```

## Aspose.Words for Java'da Office Math Nesnelerini Kullanmak için Tam Kaynak Kodu

```java
        Document doc = new Document("Your Directory Path" + "Office math.docx");
        OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
        // OfficeMath display type represents whether an equation is displayed inline with the text or displayed on its line.
        officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
        officeMath.setJustification(OfficeMathJustification.LEFT);
        doc.save("Your Directory Path" + "WorkingWithOfficeMath.MathEquations.docx");
```

## Yaygın Sorunlar ve Çözüm Yolları
- **Denklem bulunamadı:** Belgenin gerçekten bir Office Math nesnesi içerdiğinden emin olun; aksi takdirde `doc.getChild` `null` döner.  
- **Görüntü tipi etkili değil:** Aspose.Words'ün güncel bir sürümünü kullandığınızı doğrulayın; eski sürümler `OfficeMathDisplayType` için sınırlı destek sağlayabilir.  
- **Lisans istisnası:** Lisans hatası alıyorsanız, `Document` örneğini oluşturmadan önce lisans dosyanızın doğru yüklendiğini iki kez kontrol edin.  

## Sıkça Sorulan Sorular

**S: Aspose.Words for Java'da Office Math nesnelerinin amacı nedir?**  
C: Office Math nesneleri, matematiksel denklemleri programatik olarak temsil etmenizi ve manipüle etmenizi sağlar; böylece görüntüleme ve biçimlendirme üzerinde tam kontrol elde edersiniz.

**S: Belgemde Office Math denklemlerini farklı şekilde hizalayabilir miyim?**  
C: Evet, `setJustification` metodunu kullanarak sola, sağa veya ortaya hizalayabilirsiniz.

**S: Aspose.Words for Java karmaşık matematiksel belgelerle çalışmak için uygun mu?**  
C: Kesinlikle. Kütüphane, karmaşık denklemler, iç içe kesirler, matrisler ve daha fazlasını tam olarak destekler.

**S: Aspose.Words for Java hakkında daha fazla nasıl bilgi edinebilirim?**  
C: Kapsamlı dokümantasyon ve indirmeler için [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/) adresini ziyaret edin.

**S: Aspose.Words for Java'ı nereden indirebilirim?**  
C: Aspose.Words for Java'ı web sitesinden indirebilirsiniz: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

---

**Son Güncelleme:** 2026-02-14  
**Test Edilen Sürüm:** Aspose.Words for Java 24.12 (Şubat 2026 itibarıyla en yeni)  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}