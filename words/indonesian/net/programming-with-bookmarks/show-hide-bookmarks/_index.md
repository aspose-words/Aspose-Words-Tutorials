---
title: Tampilkan Sembunyikan Bookmark Di Dokumen Word
linktitle: Tampilkan Sembunyikan Bookmark Di Dokumen Word
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menampilkan atau menyembunyikan bookmark secara dinamis di dokumen Word menggunakan Aspose.Words untuk .NET dengan panduan langkah demi langkah kami. Sempurna untuk pengembang.
weight: 10
url: /id/net/programming-with-bookmarks/show-hide-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tampilkan Sembunyikan Bookmark Di Dokumen Word

## Perkenalan

Pernahkah Anda merasa perlu menyembunyikan atau menampilkan bagian tertentu dari dokumen Word Anda secara dinamis? Nah, Anda beruntung! Dengan Aspose.Words untuk .NET, Anda dapat dengan mudah mengelola visibilitas konten yang ditandai di dokumen Anda. Tutorial ini akan memandu Anda melalui proses menampilkan dan menyembunyikan bookmark di dokumen Word menggunakan Aspose.Words untuk .NET. Kami akan menguraikan kodenya selangkah demi selangkah, jadi apakah Anda seorang pengembang berpengalaman atau pemula, panduan ini akan mudah diikuti.

## Prasyarat

Sebelum kita mendalami kodenya, pastikan Anda memiliki semua yang Anda perlukan:

1.  Aspose.Words for .NET: Pastikan Anda telah menginstal perpustakaan Aspose.Words for .NET. Jika belum, Anda dapat mendownloadnya[Di Sini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: IDE seperti Visual Studio.
3. Pengetahuan Dasar C#: Keakraban dengan pemrograman C# akan bermanfaat.
4. Dokumen Word: Contoh dokumen Word dengan penanda.

## Impor Namespace

Sebelum memulai dengan kode, Anda perlu mengimpor namespace yang diperlukan. Tambahkan yang berikut ini di awal file C# Anda:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

## Langkah 1: Muat Dokumen Anda

Hal pertama yang pertama, Anda perlu memuat dokumen Word yang berisi bookmark. Inilah cara Anda melakukannya:

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

### Penjelasan

- dataDir: Ini adalah jalur direktori tempat dokumen Word Anda berada.
-  Dokumen dokumen: Ini menginisialisasi instance baru dari`Document` kelas dengan file yang Anda tentukan.

## Langkah 2: Tampilkan atau Sembunyikan Konten yang Ditandai

Selanjutnya, kita akan menentukan metode untuk menampilkan atau menyembunyikan konten yang di-bookmark. Berikut cara lengkapnya:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool showHide)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.MoveToDocumentEnd();

    // {IF "{MERGEFIELD bookmark}" = "benar" "" ""}
    Field field = builder.InsertField("IF \"", null);
    builder.MoveTo(field.Start.NextSibling);
    builder.InsertField("MERGEFIELD " + bookmarkName + "", null);
    builder.Write("\" = \"true\" ");
    builder.Write("\"");
    builder.Write("\"");
    builder.Write(" \"\"");

    Node currentNode = field.Start;
    bool flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.Run)
            if (currentNode.ToString(SaveFormat.Text).Trim() == "\"")
                flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkStart.ParentNode.InsertBefore(currentNode, bm.BookmarkStart);
        currentNode = nextNode;
    }

    Node endNode = bm.BookmarkEnd;
    flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.FieldEnd)
            flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkEnd.ParentNode.InsertAfter(currentNode, endNode);
        endNode = currentNode;
        currentNode = nextNode;
    }

    doc.MailMerge.Execute(new[] { bookmarkName }, new object[] { showHide });
}
```

### Penjelasan

- Bookmark bm: Mengambil bookmark dari dokumen.
- Pembuat DocumentBuilder: Membantu dalam menavigasi dan memodifikasi dokumen.
- Bidang bidang: Menyisipkan bidang IF untuk memeriksa kondisi bookmark.
- Node currentNode: Melintasi node untuk menemukan bidang awal dan akhir.

## Langkah 3: Jalankan Fungsi Tampilkan/Sembunyikan

 Sekarang, Anda perlu menelepon`ShowHideBookmarkedContent` metode, meneruskan dokumen, nama bookmark, dan tanda visibilitas:

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", false);
```

### Penjelasan

- doc: Objek dokumen Anda.
- "MyBookmark1": Nama bookmark yang ingin Anda tampilkan/sembunyikan.
- false: Bendera visibilitas (benar untuk ditampilkan, salah untuk disembunyikan).

## Langkah 4: Simpan Dokumen Anda

Terakhir, simpan dokumen yang dimodifikasi:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Penjelasan

- dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx": Jalur dan nama dokumen baru tempat perubahan akan disimpan.

## Kesimpulan

Dan itu dia! Anda telah berhasil mempelajari cara menampilkan dan menyembunyikan bookmark di dokumen Word menggunakan Aspose.Words untuk .NET. Teknik ini bisa sangat berguna untuk menghasilkan dokumen dengan konten bersyarat secara dinamis.

## FAQ

### Apa itu Aspose.Words untuk .NET?
Aspose.Words untuk .NET adalah pustaka pemrosesan dokumen canggih yang memungkinkan pengembang membuat, memodifikasi, dan mengonversi dokumen Word secara terprogram.

### Bagaimana cara mendapatkan Aspose.Words untuk .NET?
 Anda dapat mengunduh Aspose.Words untuk .NET dari[Di Sini](https://releases.aspose.com/words/net/). Uji coba gratis juga tersedia.

### Bisakah saya menggunakan metode ini untuk jenis bookmark lainnya?
Ya, metode ini dapat diadaptasi untuk mengelola visibilitas setiap bookmark di dokumen Word Anda.

### Bagaimana jika dokumen saya tidak berisi penanda yang ditentukan?
Jika bookmark tidak ada, metode ini akan menimbulkan kesalahan. Pastikan bookmark ada sebelum mencoba menampilkan/menyembunyikannya.

### Bagaimana saya bisa mendapatkan dukungan jika saya mengalami masalah?
 Anda bisa mendapatkan dukungan dari komunitas Aspose[Di Sini](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
