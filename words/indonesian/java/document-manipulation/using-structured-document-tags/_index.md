---
title: Menggunakan Structured Document Tags (SDT) di Aspose.Words untuk Java
linktitle: Menggunakan Tag Dokumen Terstruktur (SDT)
second_title: API Pemrosesan Dokumen Java Aspose.Words
description: Pelajari cara menggunakan Structured Document Tags (SDT) di Aspose.Words untuk Java dengan panduan lengkap ini. Buat, ubah, dan ikat SDT ke data XML kustom.
weight: 19
url: /id/java/document-manipulation/using-structured-document-tags/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menggunakan Structured Document Tags (SDT) di Aspose.Words untuk Java


## Pengantar Penggunaan Structured Document Tags (SDT) di Aspose.Words untuk Java

Structured Document Tags (SDT) merupakan fitur hebat di Aspose.Words untuk Java yang memungkinkan Anda membuat dan memanipulasi konten terstruktur dalam dokumen Anda. Dalam panduan lengkap ini, kami akan memandu Anda melalui berbagai aspek penggunaan SDT di Aspose.Words untuk Java. Baik Anda seorang pemula atau pengembang berpengalaman, Anda akan menemukan wawasan berharga dan contoh praktis dalam artikel ini.

## Memulai

Sebelum kita menyelami detailnya, mari kita siapkan lingkungan kita dan buat SDT dasar. Di bagian ini, kita akan membahas topik-topik berikut:

- Membuat dokumen baru
- Menambahkan Tag Dokumen Terstruktur
- Menyimpan dokumen

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Buat Tag Dokumen Terstruktur bertipe CHECKBOX
StructuredDocumentTag sdtCheckBox = new StructuredDocumentTag(doc, SdtType.CHECKBOX, MarkupLevel.INLINE);
builder.insertNode(sdtCheckBox);

// Simpan dokumen
doc.save("WorkingWithSDT.docx");
```

## Memeriksa Status Kotak Centang SDT Saat Ini

Setelah Anda menambahkan kotak centang SDT ke dokumen Anda, Anda mungkin ingin memeriksa statusnya saat ini secara terprogram. Ini dapat berguna saat Anda perlu memvalidasi masukan pengguna atau melakukan tindakan tertentu berdasarkan status kotak centang.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtCheckBox = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtCheckBox.getSdtType() == SdtType.CHECKBOX) {
    // Kotak centang dicentang
    sdtCheckBox.setChecked(true);
}

doc.save("UpdatedDocument.docx");
```

## Mengubah Kontrol Konten

Di bagian ini, kita akan membahas cara mengubah kontrol konten dalam dokumen Anda. Kita akan membahas tiga jenis kontrol konten: Teks Biasa, Daftar Drop-Down, dan Gambar.

### Mengubah Kontrol Konten Teks Biasa

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPlainText = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtPlainText.getSdtType() == SdtType.PLAIN_TEXT) {
    // Hapus konten yang ada
    sdtPlainText.removeAllChildren();

    // Tambahkan teks baru
    Paragraph para = (Paragraph) sdtPlainText.appendChild(new Paragraph(doc));
    Run run = new Run(doc, "New text goes here");
    para.appendChild(run);
}

doc.save("ModifiedDocument.docx");
```

### Mengubah Kontrol Konten Daftar Drop-Down

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtDropDown = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtDropDown.getSdtType() == SdtType.DROP_DOWN_LIST) {
    // Pilih item kedua dari daftar
    SdtListItem secondItem = sdtDropDown.getListItems().get(2);
    sdtDropDown.getListItems().setSelectedValue(secondItem);
}

doc.save("ModifiedDocument.docx");
```

### Mengubah Kontrol Konten Gambar

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPicture = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);
Shape shape = (Shape) sdtPicture.getChild(NodeType.SHAPE, 0, true);

if (shape.hasImage()) {
    // Ganti gambar dengan yang baru
    shape.getImageData().setImage("Watermark.png");
}

doc.save("ModifiedDocument.docx");
```

## Membuat Kontrol Konten ComboBox

Kontrol Konten ComboBox memungkinkan pengguna untuk memilih dari daftar opsi yang telah ditetapkan. Mari kita buat satu di dokumen kita.

```java
Document doc = new Document();
StructuredDocumentTag sdtComboBox = new StructuredDocumentTag(doc, SdtType.COMBO_BOX, MarkupLevel.BLOCK);
sdtComboBox.getListItems().add(new SdtListItem("Choose an item", "-1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 1", "1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 2", "2"));
doc.getFirstSection().getBody().appendChild(sdtComboBox);

doc.save("ComboBoxDocument.docx");
```

## Bekerja dengan Kontrol Konten Teks Kaya

Kontrol Konten Rich Text sangat cocok untuk menambahkan teks berformat ke dokumen Anda. Mari buat satu dan atur kontennya.

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

## Mengatur Gaya Kontrol Konten

Anda dapat menerapkan gaya pada kontrol konten untuk meningkatkan tampilan visual dokumen Anda. Mari kita lihat cara mengatur gaya kontrol konten.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdt = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

// Terapkan gaya khusus
Style style = doc.getStyles().getByStyleIdentifier(StyleIdentifier.QUOTE);
sdt.setStyle(style);

doc.save("StyledDocument.docx");
```

## Mengikat SDT ke Data XML Kustom

Dalam beberapa skenario, Anda mungkin perlu mengikat SDT ke data XML khusus untuk pembuatan konten dinamis. Mari kita bahas cara mencapainya.

```java
Document doc = new Document();
CustomXmlPart xmlPart = doc.getCustomXmlParts().add(UUID.randomUUID().toString(), "<root><text>Hello, World!</text></root>");
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.BLOCK);
doc.getFirstSection().getBody().appendChild(sdt);
sdt.getXmlMapping().setMapping(xmlPart, "/root[1]/text[1]", "");

doc.save("CustomXMLBinding.docx");
```

## Membuat Tabel dengan Bagian Berulang yang Dipetakan ke Data XML Kustom

Tabel dengan bagian yang berulang dapat sangat berguna untuk menyajikan data terstruktur. Mari buat tabel seperti itu dan petakan ke data XML khusus.

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

## Bekerja dengan Tag Dokumen Terstruktur Multi-Bagian

Tag Dokumen Terstruktur dapat mencakup beberapa bagian dalam satu dokumen. Di bagian ini, kita akan membahas cara bekerja dengan SDT multi-bagian.

```java
Document doc = new Document("MultiSectionDocument.docx");
NodeCollection tags = doc.getChildNodes(NodeType.STRUCTURED_DOCUMENT_TAG_RANGE_START, true);

for (StructuredDocumentTagRangeStart tag : tags) {
    System.out.println(tag.getTitle());
}

doc.save("ModifiedMultiSectionDocument.docx");
```

## Kesimpulan

Tag Dokumen Terstruktur di Aspose.Words untuk Java menyediakan cara serbaguna untuk mengelola dan memformat konten dalam dokumen Anda. Baik Anda perlu membuat templat, formulir, atau dokumen dinamis, SDT menawarkan fleksibilitas dan kontrol yang Anda perlukan. Dengan mengikuti contoh dan panduan yang diberikan dalam artikel ini, Anda dapat memanfaatkan kekuatan SDT untuk meningkatkan tugas pemrosesan dokumen Anda.

## Pertanyaan yang Sering Diajukan

### Apa tujuan dari Structured Document Tags (SDT)?

Tag Dokumen Terstruktur (SDT) berfungsi untuk mengatur dan memformat konten dalam dokumen, sehingga memudahkan pembuatan templat, formulir, dan dokumen terstruktur.

### Bagaimana cara memeriksa status Checkbox SDT saat ini?

 Anda dapat memeriksa status Checkbox SDT saat ini menggunakan`setChecked` metode, seperti yang ditunjukkan dalam artikel.

### Dapatkah saya menerapkan gaya ke Kontrol Konten?

Ya, Anda dapat menerapkan gaya ke Kontrol Konten untuk menyesuaikan tampilannya dalam dokumen.

### Apakah mungkin untuk mengikat SDT ke data XML khusus?

Ya, Anda dapat mengikat SDT ke data XML khusus, yang memungkinkan pembuatan konten dinamis dan pemetaan data.

### Apa itu Bagian Berulang dalam SDT?

Bagian Berulang dalam SDT memungkinkan Anda membuat tabel dengan data dinamis, di mana baris dapat diulang berdasarkan data XML yang dipetakan.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
