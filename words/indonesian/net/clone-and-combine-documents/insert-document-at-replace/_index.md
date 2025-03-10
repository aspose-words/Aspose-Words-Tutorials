---
title: Masukkan Dokumen Saat Ganti
linktitle: Masukkan Dokumen Saat Ganti
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara memasukkan satu dokumen Word ke dokumen lain dengan mudah menggunakan Aspose.Words untuk .NET dengan panduan terperinci langkah demi langkah kami. Sempurna bagi pengembang yang ingin menyederhanakan pemrosesan dokumen.
weight: 10
url: /id/net/clone-and-combine-documents/insert-document-at-replace/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Masukkan Dokumen Saat Ganti

## Perkenalan

Hai, para ahli dokumen! Pernahkah Anda merasa sangat sibuk dengan kode, mencoba mencari tahu cara memasukkan satu dokumen Word ke dokumen lain dengan mudah? Jangan khawatir, karena hari ini kita akan menyelami dunia Aspose.Words untuk .NET untuk mempermudah tugas tersebut. Kami akan memandu Anda melalui panduan terperinci langkah demi langkah tentang cara menggunakan pustaka yang hebat ini untuk memasukkan dokumen pada titik tertentu selama operasi cari dan ganti. Siap menjadi ahli Aspose.Words? Mari kita mulai!

## Prasyarat

Sebelum kita masuk ke kode, ada beberapa hal yang perlu Anda siapkan:

-  Visual Studio: Pastikan Anda telah menginstal Visual Studio di komputer Anda. Jika Anda belum memilikinya, Anda dapat mengunduhnya dari[Di Sini](https://visualstudio.microsoft.com/).
-  Aspose.Words untuk .NET: Anda memerlukan pustaka Aspose.Words. Anda bisa mendapatkannya dari[Situs web Aspose](https://releases.aspose.com/words/net/).
- Pengetahuan Dasar C#: Pemahaman dasar tentang C# dan .NET akan membantu Anda mengikuti tutorial ini.

Baiklah, setelah itu selesai, mari kita mulai dengan kode!

## Mengimpor Ruang Nama

Pertama-tama, kita perlu mengimpor namespace yang diperlukan untuk bekerja dengan Aspose.Words. Ini seperti mengumpulkan semua alat sebelum memulai proyek. Tambahkan ini menggunakan perintah di bagian atas berkas C# Anda:

```csharp
using System;
using System.Text.RegularExpressions;
using Aspose.Words;
using Aspose.Words.Replacing;
using Aspose.Words.Tables;
```

Sekarang setelah kita memiliki prasyarat yang diperlukan, mari kita bagi prosesnya menjadi beberapa langkah kecil. Setiap langkah sangat penting dan akan membawa kita lebih dekat ke tujuan kita.

## Langkah 1: Menyiapkan Direktori Dokumen

Pertama, kita perlu menentukan direktori tempat dokumen kita disimpan. Ini seperti menyiapkan panggung sebelum pertunjukan besar.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Mengganti`"YOUR DOCUMENT DIRECTORY"` dengan jalur ke direktori Anda. Di sinilah dokumen Anda akan hidup dan berkembang.

## Langkah 2: Muat Dokumen Utama

Selanjutnya, kita memuat dokumen utama yang ingin kita masukkan dokumen lain. Anggap ini sebagai panggung utama tempat semua tindakan akan terjadi.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

Kode ini memuat dokumen utama dari direktori yang ditentukan.

## Langkah 3: Atur Opsi Temukan dan Ganti

Untuk menemukan lokasi spesifik tempat kita ingin menyisipkan dokumen, kita menggunakan fungsi temukan dan ganti. Ini seperti menggunakan peta untuk menemukan lokasi pasti untuk penambahan baru kita.

```csharp
FindReplaceOptions options = new FindReplaceOptions
{
    Direction = FindReplaceDirection.Backward,
    ReplacingCallback = new InsertDocumentAtReplaceHandler()
};
```

Di sini, kita menetapkan arah ke belakang dan menentukan penangan panggilan balik khusus yang akan kita definisikan berikutnya.

## Langkah 4: Lakukan Operasi Penggantian

Sekarang, kita perintahkan dokumen utama kita untuk mencari teks pengganti tertentu dan menggantinya dengan apa pun, sembari menggunakan panggilan balik kustom kita untuk menyisipkan dokumen lain.

```csharp
mainDoc.Range.Replace(new Regex("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

Kode ini melakukan operasi pencarian dan penggantian, lalu menyimpan dokumen yang diperbarui.

## Langkah 5: Buat Penangan Panggilan Balik Penggantian Kustom

Penangan panggilan balik kustom kami adalah tempat keajaiban terjadi. Penangan ini akan menentukan bagaimana penyisipan dokumen dilakukan selama operasi pencarian dan penggantian.

```csharp
private class InsertDocumentAtReplaceHandler : IReplacingCallback
{
    ReplaceAction IReplacingCallback.Replacing(ReplacingArgs args)
    {
        Document subDoc = new Document(dataDir + "Document insertion 2.docx");

        // Sisipkan dokumen setelah paragraf yang berisi teks yang cocok.
        Paragraph para = (Paragraph)args.MatchNode.ParentNode;
        InsertDocument(para, subDoc);

        // Hapus paragraf dengan teks yang cocok.
        para.Remove();
        return ReplaceAction.Skip;
    }
}
```

Di sini, kita memuat dokumen yang akan disisipkan dan kemudian memanggil metode pembantu untuk melakukan penyisipan.

## Langkah 6: Tentukan Metode Penyisipan Dokumen

Bagian terakhir teka-teki kita adalah metode yang benar-benar memasukkan dokumen di lokasi yang ditentukan.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    // Periksa apakah tujuan penyisipan adalah Paragraf atau Tabel
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;

        // Buat NodeImporter untuk mengimpor node dari dokumen sumber
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        // Ulangi semua node tingkat blok di bagian dokumen sumber
        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        {
            foreach (Node srcNode in srcSection.Body)
            {
                // Lewati paragraf kosong terakhir dari suatu bagian
                if (srcNode.NodeType == NodeType.Paragraph)
                {
                    Paragraph para = (Paragraph)srcNode;
                    if (para.IsEndOfSection && !para.HasChildNodes)
                        continue;
                }

                // Impor dan masukkan node ke tujuan
                Node newNode = importer.ImportNode(srcNode, true);
                destinationParent.InsertAfter(newNode, insertionDestination);
                insertionDestination = newNode;
            }
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}

```

Metode ini menangani pengimporan simpul dari dokumen yang akan disisipkan dan penempatannya di tempat yang tepat dalam dokumen utama.

## Kesimpulan

Nah, itu dia! Panduan lengkap untuk memasukkan satu dokumen ke dokumen lain menggunakan Aspose.Words untuk .NET. Dengan mengikuti langkah-langkah ini, Anda dapat dengan mudah mengotomatiskan tugas perakitan dan manipulasi dokumen. Baik Anda sedang membangun sistem manajemen dokumen atau hanya perlu menyederhanakan alur kerja pemrosesan dokumen, Aspose.Words adalah pendamping terpercaya Anda.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?
Aspose.Words untuk .NET adalah pustaka yang hebat untuk memanipulasi dokumen Word secara terprogram. Pustaka ini memungkinkan Anda membuat, memodifikasi, mengonversi, dan memproses dokumen Word dengan mudah.

### Bisakah saya memasukkan beberapa dokumen sekaligus?
Ya, Anda dapat memodifikasi pengendali panggilan balik untuk menangani beberapa penyisipan dengan melakukan iterasi pada kumpulan dokumen.

### Apakah ada uji coba gratis yang tersedia?
 Tentu saja! Anda dapat mengunduh uji coba gratis dari[Di Sini](https://releases.aspose.com/).

### Bagaimana cara mendapatkan dukungan untuk Aspose.Words?
 Anda bisa mendapatkan dukungan dengan mengunjungi[Forum Aspose.Words](https://forum.aspose.com/c/words/8).

### Bisakah saya mempertahankan format dokumen yang disisipkan?
 Ya, itu`NodeImporter` kelas memungkinkan Anda menentukan bagaimana pemformatan ditangani saat mengimpor node dari satu dokumen ke dokumen lainnya.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
