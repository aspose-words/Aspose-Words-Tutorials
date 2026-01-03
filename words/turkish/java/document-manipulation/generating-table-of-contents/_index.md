---
date: 2026-01-03
description: Aspose.Words for Java kullanarak bir içindekiler tablosu eklerken sayfa
  numaralarını nasıl ayarlayacağınızı öğrenin. TOC stillerini özelleştirin ve belgeleri
  zahmetsizce oluşturun.
linktitle: Generating Table of Contents
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java ile Sayfa Numaralarını Ayarlayın ve İçindekiler Tablosu
  Oluşturun
url: /tr/java/document-manipulation/generating-table-of-contents/
weight: 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java'da Sayfa Numaralarını Ayarlama ve İçindekiler Tablosu Oluşturma

Bu öğreticide **sayfa numaralarını ayarlamayı** ve **bir içindekiler tablosu (TOC) eklemeyi** Aspose.Words for Java ile keşfedeceksiniz. İyi yapılandırılmış bir TOC, uzun belgelerin gezinmesini kolaylaştırır ve sayfa numarası hizalamasını ince ayar yapmak, okuyucularınıza profesyonel bir deneyim sunar. Bir belge oluşturma, TOC stillerini özelleştirme ve sekme duraklarını ayarlama adımlarını, sayfa numaralarının tam istediğiniz yerde hizalanmasını sağlayarak göstereceğiz.

## Hızlı Yanıtlar
- **“Sayfa numaralarını ayarlama” ne anlama geliyor?** TOC içinde sayfa numaralarını hizalayan sekme duraklarını değiştirmektir.  
- **İçindekiler tablosunu otomatik olarak ekleyebilir miyim?** Evet – `FieldToc` sınıfını kullanın.  
- **Kodu çalıştırmak için lisansa ihtiyacım var mı?** Geliştirme için ücretsiz deneme sürümü yeterlidir; üretim için lisans gereklidir.  
- **Hangi Aspose sürümü destekleniyor?** Örnekler, en son Aspose.Words for Java sürümüyle çalışır.  
- **TOC stillerini özelleştirmek mümkün mü?** Kesinlikle – yazı tiplerini, kalınlığı ve daha fazlasını değiştirebilirsiniz.

## Aspose.Words'ta İçindekiler Tablosu Nedir?
Bir TOC, belgeyi başlık stillerine (ör. Heading 1, Heading 2) göre tarayan ve sayfa numaralarıyla birlikte bir giriş listesi oluşturan bir alandır. Aspose.Words, bu alanı programlı olarak eklemenize ve görünümünü tam kontrol etmenize olanak tanır.

## TOC'de Sayfa Numaralarını Neden Ayarlamalıyız?
Sekme duraklarını ayarlamak, sayfa numaralarının nerede görüneceği üzerinde kesin kontrol sağlar; bu da aşağıdakiler için kritiktir:

- Temiz, sütun‑hizalı bir düzen sürdürmek.  
- Kurumsal stil kılavuzlarına uymak.  
- Basılı ve dijital belgelerde okunabilirliği artırmak.

## Önkoşullar
- Projenize eklenmiş Aspose.Words for Java (Maven/Gradle).  
- Java sözdizimine temel aşinalık.

## Adım‑Adım Kılavuz

### Adım 1: Yeni bir belge oluşturun
İçeriğinizi ve TOC'nizi tutacak boş bir `Document` nesnesi örnekleyin.

```java
Document doc = new Document();
```

### Adım 2: TOC stillerini özelleştirin
Her TOC seviyesinin görünümünü değiştirebilirsiniz. Bu örnekte, birinci‑seviye girişleri kalın yapıyoruz; bu yaygın bir biçimlendirme isteğidir.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

### Adım 3: Belgenize içerik ekleyin
Başlıkları (ör. `Heading1`, `Heading2`) ve normal paragrafları ekleyin. TOC alanı daha sonra bu başlıkları otomatik olarak yakalayacaktır. *(Kod, uzunluk nedeniyle atlanmıştır – odak TOC oluşturma üzerinedir.)*

### Adım 4: TOC alanını ekleyin
TOC'yi istediğiniz yere yerleştirin—genellikle belgenin başına.

```java
// Insert a TOC field at the desired location in your document.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

### Adım 5: Belgeyi kaydedin
Belgeyi diske kalıcı olarak yazın. DOCX, PDF veya HTML gibi desteklenen herhangi bir formatı seçebilirsiniz.

```java
doc.save("your_output_path_here");
```

## TOC'de Sekme Duraklarını Özelleştirme (Sayfa Numaralarını Ayarlama)
Varsayılan sekme durakları sayfa numaralarını istediğiniz gibi hizalamıyorsa, tüm TOC paragraflarını dolaşarak sekme konumlarını değiştirebilirsiniz.

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Get the first tab used in this paragraph, which aligns the page numbers.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Remove the old tab.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // Insert a new tab at a modified position (e.g., 50 units to the left).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Artık TOC girişleri, sayfa numaralarını tam istediğiniz yerde gösterir ve belgenize cilalı bir görünüm kazandırır.

## Yaygın Sorunlar ve İpuçları
- **TOC'de başlıklar eksik:** Başlıklarınızın yerleşik stilleri (`Heading1`, `Heading2` vb.) kullandığından veya özel stillerin TOC seviyelerine eşlendiğinden emin olun.  
- **Sekme durakları uygulanmadı:** Paragrafın gerçekten bir TOC stiline (`TOC_1`‑`TOC_9`) ait olduğunu doğrulayın.  
- **Büyük belgelerde performans:** TOC'yi ekledikten sonra `doc.updateFields()` çağırarak girişleri tek bir geçişte yenileyin.

## Sık Sorulan Sorular

**S: TOC girişlerinin biçimini nasıl değiştiririm?**  
C: `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)` ifadesini kullanın; burada *X* seviye (1‑9) ve yazı tipi, renk veya paragraf ayarlarını değiştirin.

**S: TOC'ye daha fazla seviye ekleyebilir miyim?**  
C: `FieldToc` anahtarını `\o "1-3"` gibi (örnek) ekleyerek daha fazla başlık seviyesini dahil edin, ardından ilgili `TOC_X` stillerini güncelleyin.

**S: Belirli TOC girişleri için sekme duraklarını değiştirebilir miyim?**  
C: Evet – “Sekme Duraklarını Özelleştirme” bölümünde gösterildiği gibi paragrafları dolaşarak her bir sekme durakını ayrı ayrı değiştirin.

**S: PDF çıktısında TOC oluşturmak mümkün mü?**  
C: Kesinlikle. TOC oluşturulduktan sonra belgeyi PDF olarak kaydedin (`doc.save("output.pdf")`); alan otomatik olarak işlenir.

**S: `updateFields()` metodunu manuel olarak çağırmam gerekiyor mu?**  
C: `FieldToc` eklediğinizde Aspose.Words kaydetme sırasında alanı günceller, ancak `doc.updateFields()` çağrısı, hata ayıklama için anlık sonuç almanızı sağlar.

## Sonuç
Aspose.Words for Java kullanarak **sayfa numaralarını ayarlamayı**, **bir içindekiler tablosu eklemeyi** ve **TOC stillerini özelleştirmeyi** öğrendiniz. Bu teknikler, temiz, gezilebilir ve profesyonel biçimlendirilmiş belgeler oluşturmanıza olanak tanır ve her türlü yayın standardını karşılar.

---  

**Son Güncelleme:** 2026-01-03  
**Test Edilen Sürüm:** Aspose.Words for Java (en son sürüm)  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}