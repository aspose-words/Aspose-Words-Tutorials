---
"description": "Pelajari cara memulai ulang daftar di setiap bagian dalam dokumen Word menggunakan Aspose.Words untuk .NET. Ikuti panduan langkah demi langkah terperinci kami untuk mengelola daftar secara efektif."
"linktitle": "Daftar Mulai Ulang Di Setiap Bagian"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Daftar Mulai Ulang Di Setiap Bagian"
"url": "/id/net/working-with-list/restart-list-at-each-section/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Daftar Mulai Ulang Di Setiap Bagian

## Perkenalan

Membuat dokumen yang terstruktur dan terorganisasi dengan baik terkadang terasa seperti memecahkan teka-teki yang rumit. Salah satu bagian dari teka-teki itu adalah mengelola daftar secara efektif, terutama saat Anda ingin daftar tersebut dimulai ulang di setiap bagian. Dengan Aspose.Words untuk .NET, Anda dapat melakukannya dengan mudah. Mari kita bahas cara memulai ulang daftar di setiap bagian dalam dokumen Word Anda menggunakan Aspose.Words untuk .NET.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

1. Aspose.Words untuk .NET: Unduh dan instal versi terbaru dari [Rilis Aspose](https://releases.aspose.com/words/net/) halaman.
2. Lingkungan .NET: Siapkan lingkungan pengembangan Anda dengan .NET terinstal.
3. Pemahaman Dasar tentang C#: Disarankan untuk terbiasa dengan bahasa pemrograman C#.
4. Lisensi Aspose: Anda dapat memilih [lisensi sementara](https://purchase.aspose.com/temporary-license/) jika Anda tidak memilikinya.

## Mengimpor Ruang Nama

Sebelum menulis kode, pastikan Anda mengimpor namespace yang diperlukan:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

Sekarang, mari kita uraikan prosesnya menjadi beberapa langkah agar mudah diikuti.

## Langkah 1: Inisialisasi Dokumen

Pertama, Anda perlu membuat contoh dokumen baru.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
```

## Langkah 2: Tambahkan Daftar Bernomor

Selanjutnya, tambahkan daftar bernomor ke dokumen. Daftar ini akan mengikuti format penomoran default.

```csharp
doc.Lists.Add(ListTemplate.NumberDefault);
```

## Langkah 3: Akses Daftar dan Tetapkan Properti Restart

Ambil daftar yang baru saja Anda buat dan atur `IsRestartAtEachSection` properti untuk `true`Ini memastikan daftar memulai ulang penomoran di setiap bagian baru.

```csharp
List list = doc.Lists[0];
list.IsRestartAtEachSection = true;
```

## Langkah 4: Buat Pembuat Dokumen dan Kaitkan Daftar

Membuat sebuah `DocumentBuilder` untuk memasukkan konten ke dalam dokumen dan mengaitkannya dengan daftar.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.ListFormat.List = list;
```

## Langkah 5: Tambahkan Item Daftar dan Sisipkan Hentian Bagian

Sekarang, tambahkan item ke dalam daftar. Untuk mengilustrasikan fungsi restart, kita akan menyisipkan pemisah bagian setelah sejumlah item tertentu.

```csharp
for (int i = 1; i < 45; i++)
{
    builder.Writeln($"List item {i}");

    if (i == 15)
        builder.InsertBreak(BreakType.SectionBreakNewPage);
}
```

## Langkah 6: Simpan Dokumen

Terakhir, simpan dokumen dengan opsi yang sesuai untuk memastikan kepatuhan.

```csharp
OoxmlSaveOptions options = new OoxmlSaveOptions { Compliance = OoxmlCompliance.Iso29500_2008_Transitional };
doc.Save(dataDir + "WorkingWithList.RestartListAtEachSection.docx", options);		
```

## Kesimpulan

Nah, itu dia! Dengan mengikuti langkah-langkah ini, Anda dapat dengan mudah memulai ulang daftar di setiap bagian dalam dokumen Word Anda menggunakan Aspose.Words untuk .NET. Fitur ini sangat berguna untuk membuat dokumen terstruktur dengan baik yang memerlukan bagian-bagian terpisah dengan penomoran daftarnya sendiri. Dengan Aspose.Words, menangani tugas-tugas tersebut menjadi mudah, memungkinkan Anda untuk fokus pada pembuatan konten berkualitas tinggi.

## Pertanyaan yang Sering Diajukan

### Bisakah saya memulai ulang daftar di setiap bagian untuk tipe daftar yang berbeda?
Ya, Aspose.Words untuk .NET memungkinkan Anda memulai ulang berbagai jenis daftar, termasuk daftar berpoin dan bernomor.

### Bagaimana jika saya ingin menyesuaikan format penomoran?
Anda dapat menyesuaikan format penomoran dengan memodifikasi `ListTemplate` properti saat membuat daftar.

### Apakah ada batasan jumlah item dalam daftar?
Tidak, tidak ada batasan khusus untuk jumlah item yang dapat Anda miliki dalam daftar menggunakan Aspose.Words untuk .NET.

### Dapatkah saya menggunakan fitur ini dalam format dokumen lain seperti PDF?
Ya, Anda dapat menggunakan Aspose.Words untuk mengonversi dokumen Word ke format lain seperti PDF sambil mempertahankan struktur daftar.

### Bagaimana saya bisa mendapatkan uji coba gratis Aspose.Words untuk .NET?
Anda bisa mendapatkan uji coba gratis dari [Rilis Aspose](https://releases.aspose.com/) halaman.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}