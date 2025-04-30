---
"description": "Java için Aspose.Words ile Ana Belge Oluşturma. Metin, Tablo, Resim ve Daha Fazlasını Eklemek İçin Adım Adım Kılavuz. Zahmetsizce Çarpıcı Word Belgeleri Oluşturun."
"linktitle": "DocumentBuilder'ı kullanarak İçerik Ekleme"
"second_title": "Aspose.Words Java Belge İşleme API'si"
"title": "Aspose.Words for Java'da DocumentBuilder Kullanarak İçerik Ekleme"
"url": "/tr/java/document-manipulation/adding-content-using-documentbuilder/"
"weight": 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java'da DocumentBuilder Kullanarak İçerik Ekleme


## Aspose.Words for Java'da DocumentBuilder Kullanarak İçerik Eklemeye Giriş

Bu adım adım kılavuzda, Aspose.Words for Java'nın DocumentBuilder'ını kullanarak Word belgesine çeşitli içerik türlerinin nasıl ekleneceğini inceleyeceğiz. Metin, tablolar, yatay çizgiler, form alanları, HTML, köprüler, içerik tablosu, satır içi ve kayan resimler, paragraflar ve daha fazlasını eklemeyi ele alacağız. Hadi başlayalım!

## Ön koşullar

Başlamadan önce projenizde Aspose.Words for Java kütüphanesinin kurulu olduğundan emin olun. Bunu şu adresten indirebilirsiniz: [Burada](https://releases.aspose.com/words/java/).

## Metin Ekleme

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Basit bir metin paragrafı ekle
builder.write("This is a simple text paragraph.");

// Belgeyi kaydet
doc.save("path/to/your/document.docx");
```

## Tablo Ekleme

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Bir tablo başlat
Table table = builder.startTable();

// Hücreleri ve içeriği ekle
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// Masanın sonu
builder.endTable();

// Belgeyi kaydet
doc.save("path/to/your/document.docx");
```

## Yatay Kural Ekleme

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Yatay bir kural ekle
builder.insertHorizontalRule();

// Belgeyi kaydet
doc.save("path/to/your/document.docx");
```

## Form Alanları Ekleme

### Metin Giriş Formu Alanı

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Bir metin girişi form alanı ekleyin
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Belgeyi kaydet
doc.save("path/to/your/document.docx");
```

### Onay Kutusu Form Alanı

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Bir onay kutusu form alanı ekleyin
builder.insertCheckBox("CheckBox", true, true, 0);

// Belgeyi kaydet
doc.save("path/to/your/document.docx");
```

### Combo Box Form Alanı

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Birleşik kutu için öğeleri tanımlayın
String[] items = { "Option 1", "Option 2", "Option 3" };

// Bir birleşik kutu form alanı ekleyin
builder.insertComboBox("DropDown", items, 0);

// Belgeyi kaydet
doc.save("path/to/your/document.docx");
```

## HTML ekleme

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// HTML içeriğini ekle
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Belgeyi kaydet
doc.save("path/to/your/document.docx");
```

## Köprü Bağlantıları Ekleme

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Bir köprü metni ekle
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", yanlış);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Belgeyi kaydet
doc.save("path/to/your/document.docx");
```

## İçindekiler Tablosu Ekleme

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// İçindekiler tablosunu ekle
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Belge içeriği ekle
// ...

// İçindekiler tablosunu güncelle
doc.updateFields();

// Belgeyi kaydet
doc.save("path/to/your/document.docx");
```

## Resim Ekleme

### Satır içi Görüntü

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Satır içi bir resim ekle
builder.insertImage("path/to/your/image.png");

// Belgeyi kaydet
doc.save("path/to/your/document.docx");
```

### Yüzen Görüntü

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Yüzen bir resim ekle
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Belgeyi kaydet
doc.save("path/to/your/document.docx");
```

## Paragraf Ekleme

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Paragraf biçimlendirmesini ayarla
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

// Bir paragraf ekle
builder.writeln("This is a formatted paragraph.");

// Belgeyi kaydet
doc.save("path/to/your/document.docx");
```

## Adım 10: İmleci Taşıma

Belgedeki imleç konumunu çeşitli yöntemler kullanarak kontrol edebilirsiniz: `moveToParagraph`, `moveToCell`ve daha fazlası. İşte bir örnek:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// İmleci belirli bir paragrafa taşıyın
builder.moveToParagraph(2, 0);

// Yeni imleç konumuna içerik ekle
builder.writeln("This is the 3rd paragraph.");
```

Bunlar Aspose.Words for Java'nın DocumentBuilder'ını kullanarak gerçekleştirebileceğiniz bazı genel işlemlerdir. Daha gelişmiş özellikler ve özelleştirme seçenekleri için kütüphanenin belgelerini inceleyin. Mutlu belge oluşturma!


## Çözüm

Bu kapsamlı kılavuzda, Aspose.Words for Java'nın DocumentBuilder'ının Word belgelerine çeşitli içerik türleri ekleme yeteneklerini inceledik. Metin, tablolar, yatay çizgiler, form alanları, HTML, köprüler, içerik tablosu, resimler, paragraflar ve imleç hareketini ele aldık.

## SSS

### S: Java için Aspose.Words nedir?

A: Aspose.Words for Java, geliştiricilerin Microsoft Word belgelerini programatik olarak oluşturmasına, değiştirmesine ve işlemesine olanak tanıyan bir Java kütüphanesidir. Belge oluşturma, biçimlendirme ve içerik ekleme için çok çeşitli özellikler sunar.

### S: Belgeme içindekiler tablosunu nasıl ekleyebilirim?

A: İçindekiler tablosu eklemek için şunu kullanın: `DocumentBuilder` belgenize bir içerik tablosu alanı eklemek için. İçerik tablosunu doldurmak için içerik ekledikten sonra belgedeki alanları güncellediğinizden emin olun. İşte bir örnek:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// İçindekiler alanı ekle
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Belge içeriği ekle
// ...

// İçindekiler tablosunu güncelle
doc.updateFields();
```

### S: Aspose.Words for Java kullanarak bir belgeye nasıl resim eklerim?

A: Hem satır içi hem de kayan resimleri ekleyebilirsiniz. `DocumentBuilder`İşte her ikisine de örnekler:

#### Satır İçi Resim:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Satır içi bir resim ekle
builder.insertImage("path/to/your/image.png");
```

#### Yüzen Resim:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Yüzen bir resim ekle
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### S: İçerik eklerken metin ve paragrafları biçimlendirebilir miyim?

A: Evet, metni ve paragrafları kullanarak biçimlendirebilirsiniz. `DocumentBuilder`. Yazı tipi özelliklerini, paragraf hizalamasını, girintiyi ve daha fazlasını ayarlayabilirsiniz. İşte bir örnek:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Yazı tipi ve paragraf biçimlendirmesini ayarla
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

// Biçimlendirilmiş bir paragraf ekle
builder.writeln("This is a formatted paragraph.");
```

### S: İmleci belge içerisinde belirli bir konuma nasıl taşıyabilirim?

A: İmleç konumunu şu yöntemler kullanarak kontrol edebilirsiniz: `moveToParagraph`, `moveToCell`ve daha fazlası. İşte bir örnek:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// İmleci belirli bir paragrafa taşıyın
builder.moveToParagraph(2, 0);

// Yeni imleç konumuna içerik ekle
builder.writeln("This is the 3rd paragraph.");
```

Bunlar, Aspose.Words for Java'nın DocumentBuilder'ını kullanmaya başlamanıza yardımcı olacak bazı genel sorular ve yanıtlardır. Daha fazla sorunuz varsa veya daha fazla yardıma ihtiyacınız varsa, şuraya bakın: [kütüphanenin dokümantasyonu](https://reference.aspose.com/words/java/) veya Aspose.Words topluluğundan ve destek kaynaklarından yardım isteyin.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}