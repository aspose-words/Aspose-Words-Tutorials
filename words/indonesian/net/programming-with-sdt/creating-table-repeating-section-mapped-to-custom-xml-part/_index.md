---
"description": "Pelajari cara membuat tabel dengan bagian berulang yang dipetakan ke CustomXmlPart dalam dokumen Word menggunakan Aspose.Words untuk .NET."
"linktitle": "Membuat Bagian Pengulangan Tabel yang Dipetakan ke Bagian XML Kustom"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Membuat Bagian Pengulangan Tabel yang Dipetakan ke Bagian XML Kustom"
"url": "/id/net/programming-with-sdt/creating-table-repeating-section-mapped-to-custom-xml-part/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Membuat Bagian Pengulangan Tabel yang Dipetakan ke Bagian XML Kustom

## Perkenalan

Dalam tutorial ini, kita akan membahas proses pembuatan tabel dengan bagian berulang yang dipetakan ke bagian XML kustom menggunakan Aspose.Words untuk .NET. Ini sangat berguna untuk membuat dokumen secara dinamis berdasarkan data terstruktur.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:
1. Pustaka Aspose.Words untuk .NET telah terinstal. Anda dapat mengunduhnya dari [Situs web Aspose](https://releases.aspose.com/words/net/).
2. Pemahaman dasar tentang C# dan XML.

## Mengimpor Ruang Nama

Pastikan untuk menyertakan namespace yang diperlukan dalam proyek Anda:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Tables;
```

## Langkah 1: Inisialisasi Dokumen dan DocumentBuilder

Pertama, buat dokumen baru dan inisialisasi `DocumentBuilder`:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Langkah 2: Tambahkan Bagian XML Kustom

Tambahkan bagian XML khusus ke dokumen. XML ini berisi data yang ingin kita petakan ke tabel kita:

```csharp
CustomXmlPart xmlPart = doc.CustomXmlParts.Add("Books",
    "<books><book><title>Everyday Italian</title><author>Giada De Laurentiis</author></book>" +
    "<book><title>Harry Potter</title><author>J K. Rowling</author></book>" +
    "<book><title>Learning XML</title><author>Erik T. Ray</author></book></books>");
```

## Langkah 3: Buat Struktur Tabel

Selanjutnya, gunakan `DocumentBuilder` untuk membuat tajuk tabel:

```csharp
Table table = builder.StartTable();
builder.InsertCell();
builder.Write("Title");
builder.InsertCell();
builder.Write("Author");
builder.EndRow();
builder.EndTable();
```

## Langkah 4: Buat Bagian Berulang

Membuat sebuah `StructuredDocumentTag` (SDT) untuk bagian yang berulang dan memetakannya ke data XML:

```csharp
StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSection, MarkupLevel.Row);
repeatingSectionSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book", "");
table.AppendChild(repeatingSectionSdt);
```

## Langkah 5: Buat Item Bagian Berulang

Buat SDT untuk item bagian berulang dan tambahkan ke bagian berulang:

```csharp
StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSectionItem, MarkupLevel.Row);
repeatingSectionSdt.AppendChild(repeatingSectionItemSdt);
Row row = new Row(doc);
repeatingSectionItemSdt.AppendChild(row);
```

## Langkah 6: Memetakan Data XML ke Sel Tabel

Buat SDT untuk judul dan penulis, petakan ke data XML, dan tambahkan ke baris:

```csharp
StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
titleSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.AppendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
authorSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.AppendChild(authorSdt);
```

## Langkah 7: Simpan Dokumen

Terakhir, simpan dokumen ke direktori yang ditentukan:

```csharp
doc.Save(dataDir + "WorkingWithSdt.CreatingTableRepeatingSectionMappedToCustomXmlPart.docx");
```

## Kesimpulan

Dengan mengikuti langkah-langkah ini, Anda telah berhasil membuat tabel dengan bagian berulang yang dipetakan ke bagian XML kustom menggunakan Aspose.Words untuk .NET. Hal ini memungkinkan pembuatan konten dinamis berdasarkan data terstruktur, sehingga pembuatan dokumen menjadi lebih fleksibel dan canggih.

## Pertanyaan yang Sering Diajukan

### Apa itu StructuredDocumentTag (SDT)?
SDT, juga dikenal sebagai kontrol konten, adalah wilayah terbatas dalam dokumen yang digunakan untuk memuat data terstruktur.

### Bisakah saya menggunakan tipe data lain di bagian XML khusus?
Ya, Anda dapat menyusun bagian XML khusus Anda dengan tipe data apa pun dan memetakannya sebagaimana mestinya.

### Bagaimana cara menambahkan lebih banyak baris ke bagian yang berulang?
Bagian yang berulang secara otomatis mereplikasi struktur baris untuk setiap item di jalur XML yang dipetakan.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}