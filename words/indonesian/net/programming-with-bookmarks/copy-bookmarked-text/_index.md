---
title: Menyalin Teks yang Ditandai di Dokumen Word
linktitle: Menyalin Teks yang Ditandai di Dokumen Word
second_title: API Pemrosesan Dokumen Aspose.Words
description: Salin teks yang ditandai di antara dokumen Word dengan mudah menggunakan Aspose.Words untuk .NET. Pelajari caranya dengan panduan langkah demi langkah ini.
weight: 10
url: /id/net/programming-with-bookmarks/copy-bookmarked-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menyalin Teks yang Ditandai di Dokumen Word

## Perkenalan

Pernahkah Anda merasa perlu menyalin bagian tertentu dari satu dokumen Word ke dokumen lain? Nah, Anda beruntung! Dalam tutorial ini, kami akan memandu Anda untuk menyalin teks yang diberi bookmark dari satu dokumen Word ke dokumen lain menggunakan Aspose.Words untuk .NET. Baik Anda sedang membuat laporan dinamis atau mengotomatiskan pembuatan dokumen, panduan ini akan menyederhanakan prosesnya untuk Anda.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

-  Pustaka Aspose.Words untuk .NET: Anda dapat mengunduhnya dari[Di Sini](https://releases.aspose.com/words/net/).
- Lingkungan Pengembangan: Visual Studio atau lingkungan pengembangan .NET lainnya.
- Pengetahuan Dasar C#: Keakraban dengan pemrograman C# dan kerangka kerja .NET.

## Mengimpor Ruang Nama

Untuk memulai, pastikan Anda telah mengimpor namespace yang diperlukan ke proyek Anda:

```csharp
using Aspose.Words;
using Aspose.Words.Import;
using Aspose.Words.Bookmark;
```

## Langkah 1: Muat Dokumen Sumber

Hal pertama yang harus dilakukan, Anda perlu memuat dokumen sumber yang berisi teks yang ditandai yang ingin Anda salin.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Bookmarks.docx");
```

 Di Sini,`dataDir` adalah jalur ke direktori dokumen Anda, dan`Bookmarks.docx` adalah dokumen sumber.

## Langkah 2: Identifikasi Bookmark

Berikutnya, identifikasi penanda buku yang ingin Anda salin dari dokumen sumber.

```csharp
Bookmark srcBookmark = srcDoc.Range.Bookmarks["MyBookmark1"];
```

 Mengganti`"MyBookmark1"` dengan nama sebenarnya dari penanda buku Anda.

## Langkah 3: Buat Dokumen Tujuan

Sekarang, buat dokumen baru di mana teks yang ditandai akan disalin.

```csharp
Document dstDoc = new Document();
CompositeNode dstNode = dstDoc.LastSection.Body;
```

## Langkah 4: Impor Konten yang Ditandai

 Untuk memastikan gaya dan format dipertahankan, gunakan`NodeImporter` untuk mengimpor konten yang ditandai dari dokumen sumber ke dokumen tujuan.

```csharp
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);
AppendBookmarkedText(importer, srcBookmark, dstNode);
```

## Langkah 5: Tentukan Metode AppendBookmarkedText

Di sinilah keajaiban terjadi. Tetapkan metode untuk menangani penyalinan teks yang ditandai:

```csharp
private void AppendBookmarkedText(NodeImporter importer, Bookmark srcBookmark, CompositeNode dstNode)
{
    Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
    Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

    if (startPara == null || endPara == null)
        throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");

    if (startPara.ParentNode != endPara.ParentNode)
        throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");

    Node endNode = endPara.NextSibling;

    for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
    {
        Node newNode = importer.ImportNode(curNode, true);
        dstNode.AppendChild(newNode);
    }
}
```

## Langkah 6: Simpan Dokumen Tujuan

Terakhir, simpan dokumen tujuan untuk memverifikasi konten yang disalin.

```csharp
dstDoc.Save(dataDir + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

## Kesimpulan

Selesai! Anda telah berhasil menyalin teks yang ditandai dari satu dokumen Word ke dokumen lain menggunakan Aspose.Words untuk .NET. Metode ini ampuh untuk mengotomatiskan tugas manipulasi dokumen, membuat alur kerja Anda lebih efisien dan lancar.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menyalin beberapa penanda buku sekaligus?
Ya, Anda dapat mengulangi beberapa penanda dan menggunakan metode yang sama untuk menyalin masing-masing penanda.

### Apa yang terjadi jika penanda buku tidak ditemukan?
 Itu`Range.Bookmarks` properti akan kembali`null`, jadi pastikan Anda menangani kasus ini untuk menghindari pengecualian.

### Bisakah saya mempertahankan format penanda buku asli?
 Tentu saja! Menggunakan`ImportFormatMode.KeepSourceFormatting` memastikan format asli dipertahankan.

### Apakah ada batasan ukuran teks yang diberi tanda buku?
Tidak ada batasan khusus, tetapi kinerjanya dapat bervariasi pada dokumen yang sangat besar.

### Bisakah saya menyalin teks antar format dokumen Word yang berbeda?
Ya, Aspose.Words mendukung berbagai format Word, dan metode ini berfungsi di semua format tersebut.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
