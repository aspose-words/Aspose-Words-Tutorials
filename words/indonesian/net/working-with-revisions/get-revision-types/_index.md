---
"description": "Pelajari cara mendapatkan jenis revisi kata dalam dokumen Word menggunakan Aspose.Words untuk .NET. Panduan langkah demi langkah ini membantu Anda menangani revisi dokumen secara efisien."
"linktitle": "Dapatkan Jenis Kata Revisi"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Dapatkan Jenis Kata Revisi"
"url": "/id/net/working-with-revisions/get-revision-types/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dapatkan Jenis Kata Revisi

## Perkenalan

Pernahkah Anda mendapati diri Anda tenggelam dalam lautan revisi dokumen, bertanya-tanya siapa yang memindahkan apa dan kapan? Anda tidak sendirian. Menangani revisi dokumen bisa menjadi tugas yang membosankan, terutama saat menangani dokumen yang ekstensif. Namun, jangan khawatir! Dengan Aspose.Words untuk .NET, Anda dapat dengan mudah mengidentifikasi dan mengelola revisi ini. Dalam panduan ini, kami akan memandu Anda melalui proses langkah demi langkah tentang cara mendapatkan jenis kata revisi dalam dokumen Word menggunakan Aspose.Words untuk .NET. Jadi, kencangkan sabuk pengaman, dan mari kita mulai!

## Prasyarat

Sebelum kita mulai membuat kode, ada beberapa hal yang Anda perlukan:

1. Pustaka Aspose.Words untuk .NET: Jika Anda belum memilikinya, unduh dari [Di Sini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Visual Studio atau IDE lain yang kompatibel dengan .NET.
3. Pengetahuan Dasar C#: Pemahaman tentang bahasa pemrograman C# akan bermanfaat.
4. Dokumen Word dengan Revisi: Pastikan Anda memiliki `.docx` file dengan perubahan yang dilacak untuk menguji kode.

## Mengimpor Ruang Nama

Untuk memulai, Anda perlu mengimpor namespace yang diperlukan dalam proyek C# Anda. Ini akan memungkinkan Anda mengakses fungsionalitas yang disediakan oleh Aspose.Words untuk .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Revision;
using System;
```

Mari kita uraikan contoh tersebut menjadi beberapa langkah agar lebih mudah dipahami dan diterapkan.

## Langkah 1: Siapkan Direktori Dokumen Anda

Pertama-tama, Anda perlu menentukan jalur ke direktori dokumen Anda. Di sinilah dokumen Word Anda beserta revisinya akan ditempatkan.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Mengganti `"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya ke folder dokumen Anda.

## Langkah 2: Muat Dokumen Word Anda

Selanjutnya, Anda perlu memuat dokumen Word ke dalam proyek Anda. Dokumen ini harus memiliki revisi yang ingin Anda analisis.

```csharp
Document doc = new Document(dataDir + "Revisions.docx");
```

Pastikan file tersebut `Revisions.docx` ada di direktori yang ditentukan.

## Langkah 3: Akses Koleksi Paragraf

Setelah dokumen Anda dimuat, Anda perlu mengakses paragraf-paragraf dalam bagian pertama isi dokumen. Ini akan membantu Anda mengulangi setiap paragraf untuk memeriksa revisi.

```csharp
ParagraphCollection paragraphs = doc.FirstSection.Body.Paragraphs;
```

## Langkah 4: Ulangi Paragraf dan Periksa Revisi

Di sinilah keajaiban terjadi. Anda akan mengulangi setiap paragraf dan memeriksa apakah paragraf tersebut telah dipindahkan (dihapus atau disisipkan).

```csharp
for (int i = 0; i < paragraphs.Count; i++)
{
    if (paragraphs[i].IsMoveFromRevision)
        Console.WriteLine("Paragraph {0} has been moved (deleted).", i);
    if (paragraphs[i].IsMoveToRevision)
        Console.WriteLine("Paragraph {0} has been moved (inserted).", i);
}
```

Loop ini melewati setiap paragraf dan menggunakan `IsMoveFromRevision` Dan `IsMoveToRevision` properti untuk menentukan apakah paragraf dipindahkan (dihapus) atau dipindahkan (dimasukkan).

## Kesimpulan

Nah, itu dia! Hanya dengan beberapa baris kode, Anda dapat dengan mudah mengidentifikasi jenis revisi dalam dokumen Word Anda menggunakan Aspose.Words for .NET. Pustaka canggih ini memudahkan penanganan revisi dokumen, sehingga Anda dapat fokus pada tugas yang lebih penting. 

## Pertanyaan yang Sering Diajukan

### Dapatkah saya menggunakan Aspose.Words untuk .NET untuk melacak perubahan yang dibuat oleh pengguna tertentu?

Ya, Aspose.Words untuk .NET menyediakan fungsionalitas untuk mengakses detail revisi, termasuk pembuat perubahan.

### Apakah ada uji coba gratis yang tersedia untuk Aspose.Words untuk .NET?

Tentu saja! Anda bisa mendapatkan uji coba gratis [Di Sini](https://releases.aspose.com/).

### Bagaimana cara mengajukan lisensi sementara untuk Aspose.Words untuk .NET?

Anda dapat meminta dan mengajukan lisensi sementara dari [Di Sini](https://purchase.aspose.com/temporary-license/).

### Di mana saya dapat menemukan dokumentasi yang lebih rinci untuk Aspose.Words untuk .NET?

Dokumentasi terperinci tersedia di [Situs web Aspose](https://reference.aspose.com/words/net/).

### Dapatkah saya menggunakan Aspose.Words untuk .NET dalam proyek nonkomersial?

Ya, Aspose.Words untuk .NET dapat digunakan dalam proyek komersial dan nonkomersial, tetapi pastikan untuk memeriksa ketentuan lisensi.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}