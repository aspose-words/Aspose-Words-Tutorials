---
date: '2025-11-12'
description: Aspose.Words for Java kullanarak sayfa sonları, sekmeler, bölünmez boşluklar
  ve çok sütunlu düzenler eklemeyi adım adım öğrenin – belge otomasyonunuzu bugün
  artırın.
keywords:
- how to insert control characters
- add page break java
- manage carriage return aspose
- insert non breaking space
- create multi column layout
- Aspose.Words control characters
- Java document formatting
- text layout automation
- document generation Java
- Aspose.Words API
language: tr
title: Aspose.Words for Java ile Kontrol Karakterlerini Ekle
url: /java/advanced-text-processing/aspose-words-java-control-characters-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insert Control Characters with Aspose.Words for Java

## Why Control Characters Matter in Java Documents
Programlı olarak fatura, rapor veya bülten oluşturduğunuzda, metin yerleşiminin kesinliği tartışılmaz bir gerekliliktir. **Sayfa sonları**, **sekme** ve **bölünemez boşluklar** gibi kontrol karakterleri, içeriğin tam olarak nerede görüneceğini manuel düzenleme yapmadan belirlemenizi sağlar. Bu öğreticide, Aspose.Words for Java API'si ile bu karakterleri nasıl yöneteceğinizi göreceksiniz; böylece belgeleriniz ilk oluşturulduklarında bile profesyonel görünür.

**Bu rehberde neler başaracaksınız**
1. Satır başı, satır sonu ve sayfa sonlarını ekleyin ve doğrulayın.  
2. Metni hizalamak için boşluk, sekme ve bölünemez boşluk ekleyin.  
3. Sütun sonları kullanarak çok sütunlu düzenler oluşturun.  
4. Büyük belgeler için en iyi performans ipuçlarını uygulayın.

## Prerequisites
Başlamadan önce aşağıdakilerin hazır olduğundan emin olun:

| Requirement | Details |
|-------------|---------|
| **Aspose.Words for Java** | Versiyon 25.3 ve üzeri (API geriye dönük uyumludur). |
| **JDK** | 8 ve üzeri. |
| **IDE** | IntelliJ IDEA, Eclipse veya tercih ettiğiniz herhangi bir Java IDE. |
| **Build Tool** | Bağımlılık yönetimi için Maven **or** Gradle. |
| **License** | Geçici veya satın alınmış bir Aspose.Words lisans dosyası (`aspose.words.lic`). |

### Environment Setup Checklist
1. Maven **or** Gradle kurun.  
2. Aspose.Words bağımlılığını ekleyin (sonraki bölüme bakın).  
3. Lisans dosyanızı güvenli bir konuma koyun ve yolunu not edin.

## Adding Aspose.Words to Your Project

### Maven
Aşağıdaki snippet'i `pom.xml` dosyanıza ekleyin:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle
`build.gradle` dosyanıza bu satırı ekleyin:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### License Initialization
Bir lisans edindikten sonra, uygulamanızın başlangıcında lisansı başlatın:

```java
License license = new License();
license.setLicense("path/to/aspose.words.lic");
```

> **Note:** Lisans olmadan kütüphane değerlendirme modunda çalışır ve filigran ekler.

## Implementation Guide

İki temel özelliği ele alacağız: **satır başı (carriage‑return) işleme** ve **çeşitli kontrol karakterlerinin eklenmesi**. Her özellik numaralı adımlara bölünmüş olup, her kod bloğundan önce kısa bir açıklama bulunur.

### Feature 1 – Carriage Return & Page Break Handling
`ControlChar.CR` (satır başı) ve `ControlChar.PAGE_BREAK` gibi kontrol karakterleri, bir belgenin mantıksal akışını tanımlar. Aşağıdaki örnek, bu karakterlerin doğru konumlandırıldığını nasıl doğrulayacağınızı gösterir.

#### Step‑by‑Step

1. **Create a new Document and DocumentBuilder**  
   `Document` nesnesi tüm içeriğin konteyneridir; `DocumentBuilder` ise metin eklemek için akıcı bir API sağlar.

   ```java
   Document doc = new Document();
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```

2. **Insert two simple paragraphs**  
   Her `writeln` çağrısı otomatik olarak bir paragraf sonu ekler.

   ```java
   builder.writeln("Hello world!");
   builder.writeln("Hello again!");
   ```

3. **Build the expected string with control characters**  
   `MessageFormat` kullanarak `ControlChar.CR` ve `ControlChar.PAGE_BREAK` karakterlerini beklenen metne gömeriz.

   ```java
   String expectedTextWithCR = MessageFormat.format("Hello world!{0}", ControlChar.CR) +
           MessageFormat.format("Hello again!{0}", ControlChar.CR) +
           ControlChar.PAGE_BREAK;
   assert doc.getText().equals(expectedTextWithCR) :
           "Text does not match expected value with control characters.";
   ```

4. **Trim the document text and re‑validate**  
   Trim işlemi, kasıtlı satır sonlarını korurken sondaki boşlukları kaldırır.

   ```java
   String expectedTrimmedText = MessageFormat.format("Hello world!{0}", ControlChar.CR) + "Hello again!";
   assert doc.getText().trim().equals(expectedTrimmedText) :
           "Trimmed text does not match expected value.";
   ```

> **Result:** Doğrulamalar, belgenin iç metin temsilinde tam olarak beklediğiniz satır başı ve sayfa sonu karakterlerinin bulunduğunu onaylar.

### Feature 2 – Inserting Various Control Characters
Şimdi boşluklar, sekmeler, satır sonları, paragraf sonları ve sütun sonlarını doğrudan belgeye nasıl gömeceğinizi inceleyelim.

#### Step‑by‑Step

1. **Initialize a fresh DocumentBuilder**  
   Temiz bir belgeyle başlamak, örneklerin izole olmasını sağlar.

   ```java
   Document doc = new Document();
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```

2. **Insert space‑related characters**  

   *Space character (`ControlChar.SPACE_CHAR`)*  
   ```java
   builder.write("Before space." + ControlChar.SPACE_CHAR + "After space.");
   ```

   *Non‑breaking space (`ControlChar.NON_BREAKING_SPACE`)*  
   ```java
   builder.write("Before NBSP." + ControlChar.NON_BREAKING_SPACE + "After NBSP.");
   ```

   *Tab character (`ControlChar.TAB`)*  
   ```java
   builder.write("Before tab." + ControlChar.TAB + "After tab.");
   ```

3. **Add line and paragraph breaks**  

   *Line feed creates a new line within the same paragraph.*  
   ```java
   // Verify that we start with a single paragraph
   Assert.assertEquals(1, doc.getFirstSection().getBody()
           .getChildNodes(NodeType.PARAGRAPH, true).getCount());

   builder.write("Before line feed." + ControlChar.LINE_FEED + "After line feed.");

   // After inserting a line feed, a second paragraph should appear
   Assert.assertEquals(2, doc.getFirstSection().getBody()
           .getChildNodes(NodeType.PARAGRAPH, true).getCount());
   ```

   *Paragraph break (`ControlChar.PARAGRAPH_BREAK`)*  
   ```java
   builder.write("Before paragraph break." + ControlChar.PARAGRAPH_BREAK + "After paragraph break.");
   Assert.assertEquals(3, doc.getFirstSection().getBody()
           .getChildNodes(NodeType.PARAGRAPH, true).getCount());
   ```

   *Section break (`ControlChar.SECTION_BREAK`)*  
   ```java
   builder.write("Before section break." + ControlChar.SECTION_BREAK + "After section break.");
   assert doc.getSections().getCount() == 1 :
           "Section count mismatch after section break.";
   ```

4. **Create a multi‑column layout with a column break**  

   İlk olarak, ikinci bir bölüm ekleyin ve iki sütunu etkinleştirin:

   ```java
   doc.appendChild(new Section(doc));
   builder.moveToSection(1);
   builder.getCurrentSection().getPageSetup().getTextColumns().setCount(2);
   ```

   Ardından, içeriği sütun 1'den sütun 2'ye taşımak için bir sütun sonu ekleyin:

   ```java
   builder.write("Text at end of column 1." + ControlChar.COLUMN_BREAK + "Text at beginning of column 2.");
   ```

> **Result:** Kodu çalıştırdıktan sonra, belge doğru konumlandırılmış boşluklar, sekmeler, satır sonları, paragraf sonları, bölüm sonları ve iki sütunlu bir düzen içerir—hepsi Aspose.Words kontrol karakterleriyle sağlanmıştır.

## Real‑World Use Cases
| Scenario | How Control Characters Help |
|----------|-----------------------------|
| **Invoice Generation** | Toplamların yeni bir sayfada görünmesi için belirli sayıda satır öğesinden sonra sayfa sonları zorlayın. |
| **Financial Reports** | Sayısal formatlamanın tutarlı olmasını sağlamak için sekmeler ve bölünemez boşluklarla sütunları hizalayın. |
| **Newsletters & Brochures** | Manuel düzenleme yapmadan yan yana makaleler için sütun sonları kullanın. |
| **CMS‑Driven Docs** | Kullanıcı tarafından oluşturulan içeriğe göre dinamik olarak satır sonları ve paragraf sonları ekleyin. |
| **Batch Document Creation** | İşlem yükünü azaltmak için kontrol karakterlerini toplu olarak ekleyin. |

## Performance Tips for Large Documents
- **Batch Inserts:** Müm