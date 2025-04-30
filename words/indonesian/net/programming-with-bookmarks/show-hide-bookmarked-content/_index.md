---
"description": "Pelajari cara menampilkan dan menyembunyikan konten yang ditandai dalam dokumen Word menggunakan Aspose.Words untuk .NET dengan panduan langkah demi langkah terperinci ini."
"linktitle": "Tampilkan Sembunyikan Konten yang Ditandai di Dokumen Word"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Tampilkan Sembunyikan Konten yang Ditandai di Dokumen Word"
"url": "/id/net/programming-with-bookmarks/show-hide-bookmarked-content/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tampilkan Sembunyikan Konten yang Ditandai di Dokumen Word

## Perkenalan

Siap menyelami dunia manipulasi dokumen dengan Aspose.Words untuk .NET? Baik Anda seorang pengembang yang ingin mengotomatiskan tugas dokumen atau sekadar ingin tahu tentang penanganan file Word secara terprogram, Anda berada di tempat yang tepat. Hari ini, kita akan menjelajahi cara menampilkan dan menyembunyikan konten yang diberi bookmark dalam dokumen Word menggunakan Aspose.Words untuk .NET. Panduan langkah demi langkah ini akan menjadikan Anda ahli dalam mengendalikan visibilitas konten berdasarkan bookmark. Mari kita mulai!

## Prasyarat

Sebelum kita masuk ke inti permasalahan, ada beberapa hal yang Anda perlukan:

1. Visual Studio: Versi apa pun yang kompatibel dengan .NET.
2. Aspose.Words untuk .NET: Unduh [Di Sini](https://releases.aspose.com/words/net/).
3. Pemahaman Dasar C#: Jika Anda dapat menulis program "Hello World" yang sederhana, Anda sudah siap melakukannya.
4. Dokumen Word dengan Bookmark: Kami akan menggunakan dokumen contoh dengan bookmark untuk tutorial ini.

## Mengimpor Ruang Nama

Pertama-tama, mari impor namespace yang diperlukan. Ini memastikan kita memiliki semua alat yang kita butuhkan untuk tugas kita.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

Dengan adanya ruang nama ini, kami siap memulai perjalanan.

## Langkah 1: Menyiapkan Proyek Anda

Baiklah, mari kita mulai dengan menyiapkan proyek kita di Visual Studio.

### Buat Proyek Baru

Buka Visual Studio dan buat proyek Aplikasi Konsol (.NET Core) baru. Beri nama yang menarik, seperti "BookmarkVisibilityManager".

### Tambahkan Aspose.Words untuk .NET

Anda perlu menambahkan Aspose.Words for .NET ke proyek Anda. Anda dapat melakukannya melalui NuGet Package Manager.

1. Buka Alat > Manajer Paket NuGet > Kelola Paket NuGet untuk Solusi.
2. Cari "Aspose.Words".
3. Instal paketnya.

Bagus! Sekarang proyek kita sudah siap, mari kita lanjutkan dengan memuat dokumen kita.

## Langkah 2: Memuat Dokumen

Kita perlu memuat dokumen Word yang berisi bookmark. Untuk tutorial ini, kita akan menggunakan contoh dokumen bernama "Bookmarks.docx".

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

Potongan kode ini mengatur jalur ke direktori dokumen Anda dan memuat dokumen ke dalam `doc` obyek.

## Langkah 3: Tampilkan/Sembunyikan Konten yang Ditandai

Sekarang tibalah bagian yang menyenangkan – menampilkan atau menyembunyikan konten berdasarkan bookmark. Kita akan membuat metode yang disebut `ShowHideBookmarkedContent` untuk menangani hal ini.

Berikut ini metode yang akan mengaktifkan/menonaktifkan visibilitas konten yang ditandai:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    Node currentNode = bm.BookmarkStart;
    while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
    {
        if (currentNode.NodeType == NodeType.Run)
        {
            Run run = currentNode as Run;
            run.Font.Hidden = isHidden;
        }
        currentNode = currentNode.NextSibling;
    }
}
```

### Rincian Metode

- Pengambilan Bookmark: `Bookmark bm = doc.Range.Bookmarks[bookmarkName];` mengambil penanda buku.
- Penelusuran Node: Kami menelusuri node-node yang ada di dalam penanda.
- Toggle Visibilitas: Jika node tersebut adalah `Run` (rangkaian teks yang berkesinambungan), kami mengaturnya `Hidden` milik.

## Langkah 4: Menerapkan Metode

Dengan metode yang sudah ada, mari terapkan untuk menampilkan atau menyembunyikan konten berdasarkan penanda buku.

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true);
```

Baris kode ini akan menyembunyikan konten dalam penanda bernama "MyBookmark1".

## Langkah 5: Menyimpan Dokumen

Terakhir, mari simpan dokumen kita yang sudah dimodifikasi.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

Ini akan menyimpan dokumen dengan perubahan yang telah kita buat.

## Kesimpulan

Nah, itu dia! Anda baru saja mempelajari cara menampilkan dan menyembunyikan konten yang di-bookmark dalam dokumen Word menggunakan Aspose.Words for .NET. Alat canggih ini memudahkan manipulasi dokumen, baik saat Anda mengotomatiskan laporan, membuat templat, atau sekadar mengutak-atik file Word. Selamat membuat kode!

## Pertanyaan yang Sering Diajukan

### Bisakah saya mengaktifkan beberapa penanda sekaligus?
Ya, Anda bisa menelepon `ShowHideBookmarkedContent` metode untuk setiap penanda yang ingin Anda alihkan.

### Apakah menyembunyikan konten memengaruhi struktur dokumen?
Tidak, menyembunyikan konten hanya memengaruhi visibilitasnya. Konten tetap ada di dalam dokumen.

### Bisakah saya menggunakan metode ini untuk jenis konten lainnya?
Metode ini secara khusus mengaktifkan teks yang dijalankan. Untuk jenis konten lain, Anda perlu mengubah logika traversal node.

### Apakah Aspose.Words untuk .NET gratis?
Aspose.Words menawarkan uji coba gratis [Di Sini](https://releases.aspose.com/), tetapi lisensi penuh diperlukan untuk penggunaan produksi. Anda dapat membelinya [Di Sini](https://purchase.aspose.com/buy).

### Bagaimana saya bisa mendapatkan dukungan jika saya mengalami masalah?
Anda bisa mendapatkan dukungan dari komunitas Aspose [Di Sini](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}