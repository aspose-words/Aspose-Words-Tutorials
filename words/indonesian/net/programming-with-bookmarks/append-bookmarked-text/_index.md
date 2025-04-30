---
"description": "Pelajari cara menambahkan teks yang diberi bookmark dalam dokumen Word menggunakan Aspose.Words untuk .NET dengan panduan langkah demi langkah ini. Sempurna untuk pengembang."
"linktitle": "Menambahkan Teks yang Ditandai di Dokumen Word"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Menambahkan Teks yang Ditandai di Dokumen Word"
"url": "/id/net/programming-with-bookmarks/append-bookmarked-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Menambahkan Teks yang Ditandai di Dokumen Word

## Perkenalan

Hai! Pernah mencoba menambahkan teks dari bagian yang ditandai di dokumen Word dan merasa kesulitan? Anda beruntung! Tutorial ini akan memandu Anda melalui proses menggunakan Aspose.Words untuk .NET. Kami akan menguraikannya menjadi beberapa langkah sederhana sehingga Anda dapat mengikutinya dengan mudah. Mari kita mulai dan tambahkan teks yang ditandai seperti seorang profesional!

## Prasyarat

Sebelum kita mulai, mari pastikan Anda memiliki semua yang Anda butuhkan:

- Aspose.Words untuk .NET: Pastikan Anda telah menginstalnya. Jika belum, Anda dapat [unduh disini](https://releases.aspose.com/words/net/).
- Lingkungan Pengembangan: Lingkungan pengembangan .NET seperti Visual Studio.
- Pengetahuan Dasar C#: Memahami konsep dasar pemrograman C# akan membantu.
- Dokumen Word dengan Penanda: Dokumen Word dengan penanda yang telah disiapkan, yang akan kita gunakan untuk menambahkan teks.

## Mengimpor Ruang Nama

Pertama-tama, mari impor namespace yang diperlukan. Ini akan memastikan kita memiliki semua alat yang kita butuhkan di ujung jari kita.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

Mari kita uraikan contoh tersebut ke dalam langkah-langkah terperinci.

## Langkah 1: Muat Dokumen dan Inisialisasi Variabel

Baiklah, mari kita mulai dengan memuat dokumen Word kita dan menginisialisasi variabel yang kita perlukan.

```csharp
// Muat dokumen sumber dan tujuan.
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

// Inisialisasi pengimpor dokumen.
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

// Temukan penanda buku di dokumen sumber.
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## Langkah 2: Identifikasi Paragraf Awal dan Akhir

Sekarang, mari kita cari paragraf tempat penanda dimulai dan berakhir. Ini penting karena kita perlu menangani teks dalam batasan ini.

```csharp
// Ini adalah paragraf yang memuat awal penanda buku.
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;

// Ini adalah paragraf yang berisi akhir penanda buku.
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

if (startPara == null || endPara == null)
    throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");
```

## Langkah 3: Validasi Induk Paragraf

Kita perlu memastikan paragraf awal dan akhir memiliki induk yang sama. Ini adalah skenario sederhana untuk menjaga semuanya tetap sederhana.

```csharp
// Batasi diri kita pada skenario yang cukup sederhana.
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");
```

## Langkah 4: Identifikasi Node yang Akan Dihentikan

Selanjutnya, kita perlu menentukan titik di mana kita akan berhenti menyalin teks. Ini akan menjadi titik tepat setelah paragraf terakhir.

```csharp
// Kami ingin menyalin semua paragraf dari paragraf awal hingga (dan termasuk) paragraf akhir,
// Oleh karena itu, simpul tempat kita berhenti adalah simpul setelah paragraf akhir.
Node endNode = endPara.NextSibling;
```

## Langkah 5: Tambahkan Teks yang Ditandai ke Dokumen Tujuan

Terakhir, mari kita mengulang simpul dari paragraf awal ke simpul setelah paragraf akhir, dan menambahkannya ke dokumen tujuan.

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // Ini membuat salinan dari node saat ini dan mengimpornya (membuatnya valid) dalam konteks
    // dari dokumen tujuan. Mengimpor berarti menyesuaikan gaya dan pengidentifikasi daftar dengan benar.
    Node newNode = importer.ImportNode(curNode, true);

    // Tambahkan simpul yang diimpor ke dokumen tujuan.
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// Simpan dokumen tujuan dengan teks terlampir.
dstDoc.Save("appended_document.docx");
```

## Kesimpulan

Nah, itu dia! Anda telah berhasil menambahkan teks dari bagian yang ditandai dalam dokumen Word menggunakan Aspose.Words for .NET. Alat canggih ini memudahkan manipulasi dokumen, dan kini Anda memiliki satu trik lagi. Selamat membuat kode!

## Pertanyaan yang Sering Diajukan

### Bisakah saya menambahkan teks dari beberapa penanda sekaligus?
Ya, Anda dapat mengulangi proses untuk setiap penanda buku dan menambahkan teks sebagaimana mestinya.

### Bagaimana jika paragraf awal dan akhir memiliki induk yang berbeda?
Contoh saat ini mengasumsikan bahwa mereka memiliki induk yang sama. Untuk induk yang berbeda, diperlukan penanganan yang lebih rumit.

### Bisakah saya mempertahankan format asli teks yang ditambahkan?
Tentu saja! `ImportFormatMode.KeepSourceFormatting` memastikan format asli dipertahankan.

### Apakah mungkin untuk menambahkan teks ke posisi tertentu dalam dokumen tujuan?
Ya, Anda dapat menambahkan teks ke posisi mana pun dengan menavigasi ke simpul yang diinginkan dalam dokumen tujuan.

### Bagaimana jika saya perlu menambahkan teks dari penanda halaman ke bagian baru?
Anda dapat membuat bagian baru di dokumen tujuan dan menambahkan teks di sana.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}