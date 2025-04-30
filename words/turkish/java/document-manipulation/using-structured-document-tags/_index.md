---
"description": "Bu kapsamlı kılavuzla Aspose.Words for Java'da Yapılandırılmış Belge Etiketlerini (SDT) nasıl kullanacağınızı öğrenin. SDT'leri oluşturun, değiştirin ve özel XML verilerine bağlayın."
"linktitle": "Yapılandırılmış Belge Etiketlerini (SDT) Kullanma"
"second_title": "Aspose.Words Java Belge İşleme API'si"
"title": "Java için Aspose.Words'de Yapılandırılmış Belge Etiketlerini (SDT) Kullanma"
"url": "/tr/java/document-manipulation/using-structured-document-tags/"
"weight": 19
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java için Aspose.Words'de Yapılandırılmış Belge Etiketlerini (SDT) Kullanma


## Java için Aspose.Words'de Yapılandırılmış Belge Etiketlerini (SDT) Kullanmaya Giriş

Yapılandırılmış Belge Etiketleri (SDT), Aspose.Words for Java'da belgelerinizde yapılandırılmış içerik oluşturmanıza ve düzenlemenize olanak tanıyan güçlü bir özelliktir. Bu kapsamlı kılavuzda, Aspose.Words for Java'da SDT'leri kullanmanın çeşitli yönlerini ele alacağız. İster yeni başlayan ister deneyimli bir geliştirici olun, bu makalede değerli içgörüler ve pratik örnekler bulacaksınız.

## Başlarken

Ayrıntılara dalmadan önce, ortamımızı ayarlayalım ve temel bir SDT oluşturalım. Bu bölümde, aşağıdaki konuları ele alacağız:

- Yeni bir belge oluşturma
- Yapılandırılmış Belge Etiketi Ekleme
- Belgeyi kaydetme

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// CHECKBOX türünde Yapılandırılmış Belge Etiketi Oluşturun
StructuredDocumentTag sdtCheckBox = new StructuredDocumentTag(doc, SdtType.CHECKBOX, MarkupLevel.INLINE);
builder.insertNode(sdtCheckBox);

// Belgeyi kaydet
doc.save("WorkingWithSDT.docx");
```

## Bir Onay Kutusunun Mevcut Durumunu Kontrol Etme SDT

Belgenize bir onay kutusu SDT ekledikten sonra, geçerli durumunu programatik olarak kontrol etmek isteyebilirsiniz. Bu, kullanıcı girdisini doğrulamanız veya onay kutusu durumuna göre belirli eylemler gerçekleştirmeniz gerektiğinde yararlı olabilir.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtCheckBox = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtCheckBox.getSdtType() == SdtType.CHECKBOX) {
    // Onay kutusu işaretli
    sdtCheckBox.setChecked(true);
}

doc.save("UpdatedDocument.docx");
```

## İçerik Denetimlerini Değiştirme

Bu bölümde, belgenizdeki içerik denetimlerini nasıl değiştireceğinizi inceleyeceğiz. Üç tür içerik denetimini ele alacağız: Düz Metin, Açılır Liste ve Resim.

### Düz Metin İçerik Denetimini Değiştirme

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPlainText = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtPlainText.getSdtType() == SdtType.PLAIN_TEXT) {
    // Mevcut içeriği temizle
    sdtPlainText.removeAllChildren();

    // Yeni metin ekle
    Paragraph para = (Paragraph) sdtPlainText.appendChild(new Paragraph(doc));
    Run run = new Run(doc, "New text goes here");
    para.appendChild(run);
}

doc.save("ModifiedDocument.docx");
```

### Açılır Liste İçerik Denetimini Değiştirme

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtDropDown = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtDropDown.getSdtType() == SdtType.DROP_DOWN_LIST) {
    // Listeden ikinci öğeyi seçin
    SdtListItem secondItem = sdtDropDown.getListItems().get(2);
    sdtDropDown.getListItems().setSelectedValue(secondItem);
}

doc.save("ModifiedDocument.docx");
```

### Resim İçerik Kontrolünü Değiştirme

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPicture = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);
Shape shape = (Shape) sdtPicture.getChild(NodeType.SHAPE, 0, true);

if (shape.hasImage()) {
    // Resmi yenisiyle değiştirin
    shape.getImageData().setImage("Watermark.png");
}

doc.save("ModifiedDocument.docx");
```

## Bir ComboBox İçerik Denetimi Oluşturma

Bir ComboBox İçerik Denetimi, kullanıcıların önceden tanımlanmış bir seçenekler listesinden seçim yapmalarına olanak tanır. Belgemizde bir tane oluşturalım.

```java
Document doc = new Document();
StructuredDocumentTag sdtComboBox = new StructuredDocumentTag(doc, SdtType.COMBO_BOX, MarkupLevel.BLOCK);
sdtComboBox.getListItems().add(new SdtListItem("Choose an item", "-1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 1", "1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 2", "2"));
doc.getFirstSection().getBody().appendChild(sdtComboBox);

doc.save("ComboBoxDocument.docx");
```

## Zengin Metin İçerik Denetimi ile Çalışma

Zengin Metin İçerik Kontrolleri, belgelerinize biçimlendirilmiş metin eklemek için mükemmeldir. Bir tane oluşturalım ve içeriğini ayarlayalım.

```java
Document doc = new Document();
StructuredDocumentTag sdtRichText = new StructuredDocumentTag(doc, SdtType.RICH_TEXT, MarkupLevel.BLOCK);
Paragraph para = new Paragraph(doc);
Run run = new Run(doc);
run.setText("Hello World");
run.getFont().setColor(Color.GREEN);
para.getRuns().add(run);
sdtRichText.getChildNodes().add(para);
doc.getFirstSection().getBody().appendChild(sdtRichText);

doc.save("RichTextDocument.docx");
```

## İçerik Denetim Stillerini Ayarlama

Belgenizin görsel görünümünü geliştirmek için içerik denetimlerine stiller uygulayabilirsiniz. Bir içerik denetiminin stilinin nasıl ayarlanacağını görelim.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdt = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

// Özel bir stil uygulayın
Style style = doc.getStyles().getByStyleIdentifier(StyleIdentifier.QUOTE);
sdt.setStyle(style);

doc.save("StyledDocument.docx");
```

## Bir SDT'yi Özel XML Verilerine Bağlama

Bazı senaryolarda, dinamik içerik üretimi için bir SDT'yi özel XML verilerine bağlamanız gerekebilir. Bunu nasıl başaracağınızı inceleyelim.

```java
Document doc = new Document();
CustomXmlPart xmlPart = doc.getCustomXmlParts().add(UUID.randomUUID().toString(), "<root><text>Hello, World!</text></root>");
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.BLOCK);
doc.getFirstSection().getBody().appendChild(sdt);
sdt.getXmlMapping().setMapping(xmlPart, "/root[1]/text[1]", "");

doc.save("CustomXMLBinding.docx");
```

## Özel XML Verilerine Eşlenen Tekrarlayan Bölümlere Sahip Bir Tablo Oluşturma

Tekrarlayan bölümlere sahip tablolar yapılandırılmış verileri sunmak için son derece yararlı olabilir. Böyle bir tablo oluşturalım ve onu özel XML verilerine eşleyelim.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
CustomXmlPart xmlPart = doc.getCustomXmlParts().add("Books", "<books>...</books>");
Table table = builder.startTable();
builder.insertCell();
builder.write("Title");
builder.insertCell();
builder.write("Author");
builder.endRow();
builder.endTable();

StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.REPEATING_SECTION, MarkupLevel.ROW);
repeatingSectionSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book", "");
table.appendChild(repeatingSectionSdt);

StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.REPEATING_SECTION_ITEM, MarkupLevel.ROW);
repeatingSectionSdt.appendChild(repeatingSectionItemSdt);

Row row = new Row(doc);
repeatingSectionItemSdt.appendChild(row);

StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.CELL);
titleSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.appendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.CELL);
authorSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.appendChild(authorSdt);

doc.save("RepeatingTableDocument.docx");
```

## Çok Bölümlü Yapılandırılmış Belge Etiketleri ile Çalışma

Yapılandırılmış Belge Etiketleri bir belgedeki birden fazla bölümü kapsayabilir. Bu bölümde, çok bölümlü SDT'lerle nasıl çalışılacağını inceleyeceğiz.

```java
Document doc = new Document("MultiSectionDocument.docx");
NodeCollection tags = doc.getChildNodes(NodeType.STRUCTURED_DOCUMENT_TAG_RANGE_START, true);

for (StructuredDocumentTagRangeStart tag : tags) {
    System.out.println(tag.getTitle());
}

doc.save("ModifiedMultiSectionDocument.docx");
```

## Çözüm

Aspose.Words for Java'daki Yapılandırılmış Belge Etiketleri, belgelerinizdeki içerikleri yönetmek ve biçimlendirmek için çok yönlü bir yol sunar. Şablonlar, formlar veya dinamik belgeler oluşturmanız gerekip gerekmediğine bakılmaksızın, SDT'ler ihtiyaç duyduğunuz esnekliği ve kontrolü sunar. Bu makalede sağlanan örnekleri ve yönergeleri izleyerek, belge işleme görevlerinizi geliştirmek için SDT'lerin gücünden yararlanabilirsiniz.

## SSS

### Yapılandırılmış Belge Etiketlerinin (SDT) amacı nedir?

Yapılandırılmış Belge Etiketleri (SDT'ler), belgelerdeki içeriği düzenleme ve biçimlendirme amacına hizmet ederek şablonlar, formlar ve yapılandırılmış belgeler oluşturmayı kolaylaştırır.

### Checkbox SDT'nin mevcut durumunu nasıl kontrol edebilirim?

Bir Onay Kutusu SDT'sinin geçerli durumunu şu şekilde kontrol edebilirsiniz: `setChecked` Yöntem, makalede gösterildiği gibi.

### İçerik Denetimlerine stiller uygulayabilir miyim?

Evet, İçerik Denetimlerine stiller uygulayarak bunların belgedeki görünümünü özelleştirebilirsiniz.

### Bir SDT'yi özel XML verilerine bağlamak mümkün müdür?

Evet, bir SDT'yi özel XML verilerine bağlayabilir, böylece dinamik içerik üretimi ve veri eşlemesine olanak sağlayabilirsiniz.

### SDT’lerde Tekrarlayan Bölümler Nedir?

SDT'lerdeki Tekrarlanan Bölümler, eşlenen XML verilerine göre satırların tekrarlanabileceği dinamik veriler içeren tablolar oluşturmanıza olanak tanır.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}