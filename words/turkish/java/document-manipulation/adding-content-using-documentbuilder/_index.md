---
date: 2026-01-01
description: Aspose.Words for Java DocumentBuilder kullanarak form alanları oluşturmayı
  ve metin, tablo, resim, hiperlink ve daha fazlasını eklemeyi öğrenin. Geliştiriciler
  için adım adım bir rehber.
linktitle: Adding Content using DocumentBuilder
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java'da DocumentBuilder kullanarak form alanları oluşturma
  ve içerik ekleme
url: /tr/java/document-manipulation/adding-content-using-documentbuilder/
weight: 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# DocumentBuilder kullanarak Aspose.Words for Java'da İçerik Ekleme

## DocumentBuilder kullanarak Aspose.Words for Java'da İçerik Eklemeye Giriş

Bu adım‑adım rehberde, **create form fields** ve çeşitli içerikleri—metin, tablolar, yatay çizgiler, HTML, hiperlinkler, resimler ve daha fazlasını—Aspose.Words for Java ile bir Word belgesine ekleyeceksiniz. Rapor, sözleşme şablonu veya etkileşimli bir form oluşturuyor olun, `DocumentBuilder` sınıfı her öğe üzerinde ince ayarlı kontrol sağlar. Hadi başlayalım!

## Hızlı Yanıtlar
- **Form alanlarını nasıl oluştururum?** `DocumentBuilder` üzerinde `insertTextInput`, `insertCheckBox` veya `insertComboBox` kullanın.
- **Düz metin ekleyen yöntem hangisidir?** `builder.write("Your text")` veya `builder.writeln("Your text")` çağırın.
- **Yatay çizgi ekleyebilir miyim?** Evet—`builder.insertHorizontalRule()` bir satır ayırıcı ekler.
- **HTML nasıl gömülür?** `builder.insertHtml("<p>HTML content</p>")` kullanın.
- **Satır içi resim nasıl eklenir?** `builder.insertImage("path/to/image.png")` resmi metin akışına yerleştirir.

## DocumentBuilder nedir ve form alanları oluşturmak için neden kullanılır?

`DocumentBuilder`, Aspose.Words' programatik olarak Word belgeleri oluşturmak ve düzenlemek için akıcı API'sidir. Düşük seviyeli OpenXML yapısını soyutlayarak, *ne* eklemek istediğinize—örneğin **form fields**—odaklanmanızı sağlar, *XML'in nasıl göründüğüne* değil. Bu, dinamik formlar, sözleşmeler veya kullanıcı etkileşimi gerektiren herhangi bir belge üretmek için idealdir.

## Ön Koşullar

Başlamadan önce, projenizde Aspose.Words for Java kütüphanesinin yüklü olduğundan emin olun. Bunu [buradan](https://releases.aspose.com/words/java/) indirebilirsiniz.

## Metin Ekleme (metin nasıl eklenir)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a simple text paragraph
builder.write("This is a simple text paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Tabloları Ekleme

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start a table
Table table = builder.startTable();

// Insert cells and content
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// End the table
builder.endTable();

// Save the document
doc.save("path/to/your/document.docx");
```

## Yatay Çizgi Ekleme (yatay çizgi ekle)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a horizontal rule
builder.insertHorizontalRule();

// Save the document
doc.save("path/to/your/document.docx");
```

## Form Alanları Ekleme (form alanları oluştur)

### Metin Girişi Form Alanı

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a text input form field
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Onay Kutusu Form Alanı

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a check box form field
builder.insertCheckBox("CheckBox", true, true, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Açılır Kutu Form Alanı

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Define items for the combo box
String[] items = { "Option 1", "Option 2", "Option 3" };

// Insert a combo box form field
builder.insertComboBox("DropDown", items, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

## HTML Ekleme (html ekle)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert HTML content
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Save the document
doc.save("path/to/your/document.docx");
```

## Hiperlinkler Ekleme (hiperlink nasıl eklenir)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a hyperlink
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", false);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Save the document
doc.save("path/to/your/document.docx");
```

## İçindekiler Tablosu Ekleme

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();

// Save the document
doc.save("path/to/your/document.docx");
```

## Resimler Ekleme

### Satır İçi Resim (satır içi resim ekle)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");

// Save the document
doc.save("path/to/your/document.docx");
```

### Yüzen Resim

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Save the document
doc.save("path/to/your/document.docx");
```

## Paragraflar Ekleme

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a paragraph
builder.writeln("This is a formatted paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## İmleci Taşıma (Adım 10)

Belge içinde imleç konumunu `moveToParagraph`, `moveToCell` gibi yöntemlerle kontrol edebilirsiniz.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Bunlar, Aspose.Words for Java'nın `DocumentBuilder`'ı ile gerçekleştirebileceğiniz yaygın işlemlerdir. Daha gelişmiş özellikler ve özelleştirme seçenekleri için kütüphanenin belgelerini inceleyin. İyi belgeler oluşturun!

## Sonuç

Bu kapsamlı rehberde, Aspose.Words for Java'nın `DocumentBuilder`'ı kullanarak **create form fields** ve çeşitli içerik türlerini—metin, tablolar, yatay çizgiler, HTML, hiperlinkler, içindekiler tablosu, resimler, biçimlendirilmiş paragraflar ve imleç navigasyonu—eklemeyi gösterdik. Artık dinamik, etkileşimli Word belgelerini programatik olarak oluşturmak için sağlam bir temele sahipsiniz.

## SSS

### Q: Aspose.Words for Java nedir?

A: Aspose.Words for Java, geliştiricilerin Microsoft Word belgelerini programatik olarak oluşturmasına, değiştirmesine ve manipüle etmesine olanak tanıyan bir Java kütüphanesidir. Belge oluşturma, biçimlendirme ve içerik ekleme için geniş bir özellik yelpazesi sunar.

### Q: Belgeme bir içindekiler tablosu nasıl ekleyebilirim?

A: İçindekiler tablosu eklemek için, `DocumentBuilder` ile bir TOC alanı ekleyin ve içeriğinizi ekledikten sonra `doc.updateFields()` metodunu çağırın.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents field
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();
```

### Q: Aspose.Words for Java kullanarak bir belgeye nasıl resim ekleyebilirim?

A: `DocumentBuilder` kullanarak satır içi ve yüzen olmak üzere resimler ekleyebilirsiniz.

#### Satır İçi Resim:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");
```

#### Yüzen Resim:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Q: İçerik eklerken metin ve paragrafları biçimlendirebilir miyim?

A: Evet, `DocumentBuilder` ile metin ve paragrafları biçimlendirebilirsiniz. İçeriği yazmadan önce yazı tipi özelliklerini, paragraf hizalamasını, girintileri ve daha fazlasını ayarlayın.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set font and paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a formatted paragraph
builder.writeln("This is a formatted paragraph.");
```

### Q: Belge içinde imleci belirli bir konuma nasıl taşıyabilirim?

A: Yeni içerik eklemeden önce imleci konumlandırmak için `moveToParagraph`, `moveToCell` gibi yöntemleri kullanın.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Bu yanıtlar, Aspose.Words for Java'nın `DocumentBuilder`'ı ile çalışırken en yaygın senaryoları kapsar. Daha ayrıntılı bilgi için [kütüphanenin belgelerine](https://reference.aspose.com/words/java/) bakın veya destek için Aspose.Words topluluğuna katılın.

---

**Son Güncelleme:** 2026-01-01  
**Test Edilen Versiyon:** Aspose.Words for Java 24.12  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}