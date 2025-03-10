---
title: Java için Aspose.Words'de İçindekiler Tablosu Oluşturma
linktitle: İçindekiler Tablosu Oluşturuluyor
second_title: Aspose.Words Java Belge İşleme API'si
description: Aspose.Words for Java kullanarak İçindekiler Tablosu'nu (TOC) nasıl oluşturacağınızı ve özelleştireceğinizi öğrenin. Zahmetsizce düzenli ve profesyonel belgeler oluşturun.
weight: 21
url: /tr/java/document-manipulation/generating-table-of-contents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java için Aspose.Words'de İçindekiler Tablosu Oluşturma


## Java için Aspose.Words'de İçindekiler Tablosu Oluşturmaya Giriş

Bu eğitimde, Aspose.Words for Java kullanarak İçindekiler Tablosu (TOC) oluşturma sürecini adım adım anlatacağız. TOC, düzenli belgeler oluşturmak için önemli bir özelliktir. TOC'nin görünümünü ve düzenini nasıl özelleştireceğinizi ele alacağız.

## Ön koşullar

Başlamadan önce, Java projenizde Aspose.Words for Java'nın yüklü ve ayarlanmış olduğundan emin olun.

## Adım 1: Yeni Bir Belge Oluşturun

Öncelikle üzerinde çalışacağımız yeni bir belge oluşturalım.

```java
Document doc = new Document();
```

## Adım 2: İçindekiler Stillerini Özelleştirin

İçindekiler tablonuzun görünümünü özelleştirmek için, onunla ilişkili stilleri değiştirebilirsiniz. Bu örnekte, birinci seviye İçindekiler tablolarının girişlerini kalın yapacağız.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

## Adım 3: Belgenize İçerik Ekleyin

İçeriğinizi belgeye ekleyebilirsiniz. Bu içerik TOC'yi oluşturmak için kullanılacaktır.

## Adım 4: İçindekiler tablosunu oluşturun

İçindekiler tablosunu oluşturmak için belgenizde istediğiniz yere bir İçindekiler tablosu alanı ekleyin. Bu alan, belgenizdeki başlıklara ve stillere göre otomatik olarak doldurulacaktır.

```java
// Belgenizde istediğiniz yere bir İçindekiler alanı ekleyin.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

## Adım 5: Belgeyi Kaydedin

Son olarak belgeyi İçindekiler bölümüyle birlikte kaydedin.

```java
doc.save("your_output_path_here");
```

## İçindekiler'de Sekme Duraklarını Özelleştirme

Ayrıca sayfa numaralarının düzenini kontrol etmek için TOC'nizdeki sekme duraklarını özelleştirebilirsiniz. Sekme duraklarını şu şekilde değiştirebilirsiniz:

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Bu paragrafta kullanılan ilk sekmeyi alın; bu sekme sayfa numaralarını hizalar.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Eski sekmeyi çıkarın.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        //Değiştirilen konuma (örneğin, 50 birim sola) yeni bir sekme ekleyin.
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Artık belgenizde sayfa numarası hizalaması için ayarlanmış sekme duraklarına sahip özelleştirilmiş bir İçindekiler Tablonuz var.


## Çözüm

Bu eğitimde, Word belgeleriyle çalışmak için güçlü bir kütüphane olan Java için Aspose.Words kullanarak İçindekiler Tablosu (TOC) oluşturmayı inceledik. Uzun belgeleri düzenlemek ve gezinmek için iyi yapılandırılmış bir TOC olmazsa olmazdır ve Aspose.Words, TOC'leri zahmetsizce oluşturmak ve özelleştirmek için araçlar sağlar.

## SSS

### İçindekiler girişlerinin biçimlendirmesini nasıl değiştirebilirim?

 İçindekiler düzeyleriyle ilişkili stilleri şu şekilde değiştirebilirsiniz:`doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`Burada X, TOC seviyesini ifade eder.

### İçindekiler tabloma nasıl daha fazla seviye ekleyebilirim?

İçindekiler tablonuza daha fazla seviye eklemek için İçindekiler alanını değiştirebilir ve istediğiniz seviye sayısını belirtebilirsiniz.

### Belirli İçindekiler girişleri için sekme durağı konumlarını değiştirebilir miyim?

Evet, yukarıdaki kod örneğinde gösterildiği gibi, paragraflar arasında gezinerek ve sekme duraklarını buna göre düzenleyerek belirli İçindekiler girişleri için sekme durağı konumlarını değiştirebilirsiniz.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
