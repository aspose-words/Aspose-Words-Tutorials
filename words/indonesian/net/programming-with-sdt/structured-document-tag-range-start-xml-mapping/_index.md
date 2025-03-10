---
title: Rentang Tag Dokumen Terstruktur Mulai Pemetaan XML
linktitle: Rentang Tag Dokumen Terstruktur Mulai Pemetaan XML
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara mengikat data XML secara dinamis ke tag dokumen terstruktur di Word menggunakan Aspose.Words untuk .NET. Ikuti panduan langkah demi langkah kami.
weight: 10
url: /id/net/programming-with-sdt/structured-document-tag-range-start-xml-mapping/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rentang Tag Dokumen Terstruktur Mulai Pemetaan XML

## Perkenalan

Pernahkah Anda ingin memasukkan data XML secara dinamis ke dalam dokumen Word? Nah, Anda beruntung! Aspose.Words untuk .NET membuat tugas ini mudah. Dalam tutorial ini, kita akan membahas lebih mendalam tentang pemetaan XML awal rentang tag dokumen terstruktur. Fitur ini memungkinkan Anda untuk mengikat bagian XML kustom ke kontrol konten, memastikan konten dokumen Anda diperbarui secara mulus dengan data XML Anda. Siap untuk mengubah dokumen Anda menjadi mahakarya yang dinamis.

## Prasyarat

Sebelum kita masuk ke bagian pengkodean, mari pastikan Anda memiliki semua yang Anda butuhkan:

1.  Aspose.Words untuk Pustaka .NET: Pastikan Anda memiliki versi terbaru. Anda dapat mengunduhnya[Di Sini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Visual Studio atau IDE lain yang mendukung C#.
3. Pengetahuan Dasar C#: Kemampuan dalam pemrograman C# adalah suatu keharusan.
4. Dokumen Word: Contoh dokumen Word yang dapat digunakan.

## Mengimpor Ruang Nama

Pertama-tama, mari impor namespace yang diperlukan. Ini akan memastikan kita memiliki akses ke semua kelas dan metode yang diperlukan di Aspose.Words untuk .NET.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using System.Text;
```

## Langkah 1: Siapkan Direktori Dokumen Anda

Setiap proyek memerlukan fondasi, bukan? Di sini, kami menyiapkan jalur ke direktori dokumen Anda.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Langkah 2: Muat Dokumen Word

Selanjutnya, kita memuat dokumen Word. Ini adalah dokumen tempat kita akan memasukkan data XML.

```csharp
Document doc = new Document(dataDir + "Multi-section structured document tags.docx");
```

## Langkah 3: Tambahkan Bagian XML Kustom

Kita perlu membuat bagian XML yang berisi data yang ingin kita masukkan dan menambahkannya ke koleksi CustomXmlPart dokumen. Bagian XML kustom ini akan berfungsi sebagai sumber data untuk tag dokumen terstruktur kita.

### Membuat Bagian XML

Pertama, buat ID unik untuk bagian XML dan tentukan kontennya.

```csharp
// Buat bagian XML yang berisi data dan tambahkan ke koleksi CustomXmlPart dokumen.
string xmlPartId = Guid.NewGuid().ToString("B");
string xmlPartContent = "<root><text>Text element #1</text><text>Text element #2</text></root>";
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(xmlPartId, xmlPartContent);
```

### Verifikasi Konten Bagian XML

Untuk memastikan bagian XML ditambahkan dengan benar, kami mencetak kontennya.

```csharp
Console.WriteLine(Encoding.UTF8.GetString(xmlPart.Data));
```

## Langkah 4: Buat Tag Dokumen Terstruktur

Structured Document Tag (SDT) adalah kontrol konten yang dapat dikaitkan dengan komponen XML. Di sini, kita membuat SDT yang akan menampilkan konten komponen XML kustom kita.

Pertama, temukan titik awal rentang SDT dalam dokumen.

```csharp
StructuredDocumentTagRangeStart sdtRangeStart = (StructuredDocumentTagRangeStart)doc.GetChild(NodeType.StructuredDocumentTagRangeStart, 0, true);
```

## Langkah 5: Mengatur Pemetaan XML untuk SDT

Sekarang, saatnya untuk mengikat bagian XML kita ke SDT. Dengan menetapkan pemetaan XML, kita menentukan bagian mana dari data XML yang akan ditampilkan di SDT.

 XPath menunjuk ke elemen tertentu di bagian XML yang ingin kita tampilkan. Di sini, kita menunjuk ke bagian kedua`<text>` elemen dalam`<root>` elemen.

```csharp
// Tetapkan pemetaan untuk StructuredDocumentTag kita
sdtRangeStart.XmlMapping.SetMapping(xmlPart, "/root[1]/text[2]", null);
```

## Langkah 6: Simpan Dokumen

Terakhir, simpan dokumen untuk melihat perubahan yang terjadi. SDT dalam dokumen Word sekarang akan menampilkan konten XML yang ditentukan.

```csharp
doc.Save(dataDir + "WorkingWithSdt.StructuredDocumentTagRangeStartXmlMapping.docx");
```

## Kesimpulan

Nah, itu dia! Anda telah berhasil memetakan bagian XML ke tag dokumen terstruktur dalam dokumen Word menggunakan Aspose.Words untuk .NET. Fitur canggih ini memungkinkan Anda membuat dokumen yang dinamis dan berbasis data dengan mudah. Baik Anda membuat laporan, faktur, atau jenis dokumen lainnya, pemetaan XML dapat menyederhanakan alur kerja Anda secara signifikan.

## Pertanyaan yang Sering Diajukan

### Apa itu tag dokumen terstruktur di Word?
Tag dokumen terstruktur, yang juga dikenal sebagai kontrol konten, adalah wadah untuk jenis konten tertentu dalam dokumen Word. Tag ini dapat digunakan untuk mengikat data, membatasi penyuntingan, atau memandu pengguna dalam pembuatan dokumen.

### Bagaimana saya dapat memperbarui konten bagian XML secara dinamis?
 Anda dapat memperbarui konten bagian XML dengan memodifikasi`xmlPartContent` string sebelum menambahkannya ke dokumen. Cukup perbarui string dengan data baru dan tambahkan ke`CustomXmlParts` koleksi.

### Bisakah saya mengikat beberapa bagian XML ke SDT yang berbeda dalam dokumen yang sama?
Ya, Anda dapat mengikat beberapa bagian XML ke SDT yang berbeda dalam dokumen yang sama. Setiap SDT dapat memiliki bagian XML dan pemetaan XPath yang unik.

### Apakah mungkin untuk memetakan struktur XML yang kompleks ke SDT?
Tentu saja! Anda dapat memetakan struktur XML yang kompleks ke SDT dengan menggunakan ekspresi XPath terperinci yang secara akurat menunjukkan elemen yang diinginkan dalam bagian XML.

### Bagaimana cara menghapus bagian XML dari sebuah dokumen?
 Anda dapat menghapus bagian XML dengan memanggil`Remove` metode pada`CustomXmlParts` koleksi, melewati`xmlPartId` bagian XML yang ingin Anda hapus.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
