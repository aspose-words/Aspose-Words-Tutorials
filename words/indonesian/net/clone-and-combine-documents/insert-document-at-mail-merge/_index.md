---
"description": "Pelajari cara menyisipkan dokumen di bidang gabungan surat menggunakan Aspose.Words untuk .NET dalam tutorial langkah demi langkah yang komprehensif ini."
"linktitle": "Sisipkan Dokumen di Mail Merge"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Sisipkan Dokumen di Mail Merge"
"url": "/id/net/clone-and-combine-documents/insert-document-at-mail-merge/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sisipkan Dokumen di Mail Merge

## Perkenalan

Selamat datang di dunia otomatisasi dokumen dengan Aspose.Words untuk .NET! Pernahkah Anda bertanya-tanya bagaimana cara memasukkan dokumen secara dinamis ke dalam bidang tertentu dalam dokumen utama selama operasi gabungan surat? Nah, Anda berada di tempat yang tepat. Tutorial ini akan memandu Anda langkah demi langkah melalui proses memasukkan dokumen di bidang gabungan surat menggunakan Aspose.Words untuk .NET. Ini seperti menyusun potongan puzzle, di mana setiap potongan jatuh pada tempatnya dengan sempurna. Jadi, mari kita mulai!

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

1. Aspose.Words untuk .NET: Anda dapat [unduh versi terbaru di sini](https://releases.aspose.com/words/net/)Jika Anda perlu membeli lisensi, Anda dapat melakukannya [Di Sini](https://purchase.aspose.com/buy)Atau, Anda bisa mendapatkan [lisensi sementara](https://purchase.aspose.com/temporary-license/) atau mencobanya dengan [uji coba gratis](https://releases.aspose.com/).
2. Lingkungan Pengembangan: Visual Studio atau IDE C# lainnya.
3. Pengetahuan Dasar C#: Keakraban dengan pemrograman C# akan membuat tutorial ini mudah.

## Mengimpor Ruang Nama

Pertama-tama, Anda perlu mengimpor namespace yang diperlukan. Namespace ini seperti blok penyusun proyek Anda.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.MailMerging;
using System.Linq;
```

Mari kita uraikan proses ini menjadi beberapa langkah yang dapat dikelola. Setiap langkah akan dibangun berdasarkan langkah sebelumnya, yang akan membawa Anda ke solusi yang lengkap.

## Langkah 1: Menyiapkan Direktori Anda

Sebelum Anda dapat mulai memasukkan dokumen, Anda perlu menentukan jalur ke direktori dokumen Anda. Di sinilah dokumen Anda disimpan.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Langkah 2: Memuat Dokumen Utama

Berikutnya, Anda akan memuat dokumen utama. Dokumen ini berisi kolom gabungan tempat dokumen lain akan disisipkan.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

## Langkah 3: Mengatur Panggilan Balik Penggabungan Bidang

Untuk menangani proses penggabungan, Anda perlu mengatur fungsi panggilan balik. Fungsi ini akan bertanggung jawab untuk memasukkan dokumen pada kolom penggabungan yang ditentukan.

```csharp
mainDoc.MailMerge.FieldMergingCallback = new InsertDocumentAtMailMergeHandler();
```

## Langkah 4: Menjalankan Gabungan Surat

Sekarang saatnya untuk menjalankan penggabungan surat. Di sinilah keajaiban terjadi. Anda akan menentukan bidang penggabungan dan dokumen yang harus disisipkan di bidang ini.

```csharp
mainDoc.MailMerge.Execute(new[] { "Document_1" }, new object[] { dataDir + "Document insertion 2.docx" });
```

## Langkah 5: Menyimpan Dokumen

Setelah penggabungan surat selesai, Anda akan menyimpan dokumen yang dimodifikasi. Dokumen baru ini akan memiliki konten yang disisipkan tepat di tempat yang Anda inginkan.

```csharp
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

## Langkah 6: Membuat Callback Handler

Callback handler adalah kelas yang melakukan pemrosesan khusus untuk bidang gabungan. Kelas ini memuat dokumen yang ditentukan dalam nilai bidang dan memasukkannya ke dalam bidang gabungan saat ini.

```csharp
private class InsertDocumentAtMailMergeHandler : IFieldMergingCallback
{
    void IFieldMergingCallback.FieldMerging(FieldMergingArgs args)
    {
        if (args.DocumentFieldName == "Document_1")
        {
            DocumentBuilder builder = new DocumentBuilder(args.Document);
            builder.MoveToMergeField(args.DocumentFieldName);

            Document subDoc = new Document((string)args.FieldValue);
            InsertDocument(builder.CurrentParagraph, subDoc);

            if (!builder.CurrentParagraph.HasChildNodes)
                builder.CurrentParagraph.Remove();

            args.Text = null;
        }
    }
}
```

## Langkah 7: Memasukkan Dokumen

Metode ini menyisipkan dokumen yang ditentukan ke dalam paragraf atau sel tabel saat ini.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        foreach (Node srcNode in srcSection.Body)
        {
            if (srcNode.NodeType == NodeType.Paragraph)
            {
                Paragraph para = (Paragraph)srcNode;
                if (para.IsEndOfSection && !para.HasChildNodes)
                    continue;
            }

            Node newNode = importer.ImportNode(srcNode, true);
            destinationParent.InsertAfter(newNode, insertionDestination);
            insertionDestination = newNode;
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}
```

## Kesimpulan

Nah, itu dia! Anda telah berhasil memasukkan dokumen ke dalam bidang tertentu selama operasi gabungan surat menggunakan Aspose.Words untuk .NET. Fitur hebat ini dapat menghemat banyak waktu dan tenaga Anda, terutama saat menangani dokumen dalam jumlah besar. Anggap saja seperti memiliki asisten pribadi yang akan mengurus semua pekerjaan berat untuk Anda. Jadi, silakan dan cobalah. Selamat membuat kode!

## Pertanyaan yang Sering Diajukan

### Bisakah saya menyisipkan beberapa dokumen pada kolom gabungan yang berbeda?
Ya, Anda bisa. Cukup tentukan bidang gabungan yang sesuai dan jalur dokumen yang sesuai di `MailMerge.Execute` metode.

### Apakah mungkin untuk memformat dokumen yang dimasukkan secara berbeda dari dokumen utama?
Tentu saja! Anda dapat menggunakan `ImportFormatMode` parameternya di dalam `NodeImporter` untuk mengontrol pemformatan.

### Bagaimana jika nama bidang gabungan bersifat dinamis?
Anda dapat menangani nama bidang gabungan dinamis dengan meneruskannya sebagai parameter ke pengendali panggilan balik.

### Bisakah saya menggunakan metode ini dengan format file yang berbeda?
Ya, Aspose.Words mendukung berbagai format file termasuk DOCX, PDF, dan banyak lagi.

### Bagaimana cara menangani kesalahan selama proses penyisipan dokumen?
Terapkan penanganan kesalahan dalam penangan panggilan balik Anda untuk mengelola pengecualian apa pun yang mungkin terjadi.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}