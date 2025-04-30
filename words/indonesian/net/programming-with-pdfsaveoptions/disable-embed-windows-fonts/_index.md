---
"description": "Kurangi ukuran PDF dengan menonaktifkan font yang tertanam menggunakan Aspose.Words untuk .NET. Ikuti panduan langkah demi langkah kami untuk mengoptimalkan dokumen Anda agar dapat disimpan dan dibagikan secara efisien."
"linktitle": "Kurangi Ukuran PDF dengan Menonaktifkan Font yang Disematkan"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Kurangi Ukuran PDF dengan Menonaktifkan Font yang Disematkan"
"url": "/id/net/programming-with-pdfsaveoptions/disable-embed-windows-fonts/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Kurangi Ukuran PDF dengan Menonaktifkan Font yang Disematkan

## Perkenalan

Mengurangi ukuran file PDF dapat menjadi hal yang penting untuk penyimpanan yang efisien dan berbagi dengan cepat. Salah satu cara efektif untuk melakukannya adalah dengan menonaktifkan font yang disematkan, terutama jika font standar sudah tersedia di sebagian besar sistem. Dalam tutorial ini, kita akan membahas cara mengurangi ukuran PDF dengan menonaktifkan font yang disematkan menggunakan Aspose.Words untuk .NET. Kami akan memandu Anda melalui setiap langkah untuk memastikan Anda dapat menerapkannya dengan mudah dalam proyek Anda sendiri.

## Prasyarat

Sebelum menyelami kode, pastikan Anda memiliki hal berikut:

- Aspose.Words untuk .NET: Jika Anda belum melakukannya, unduh dan instal dari [Tautan unduhan](https://releases.aspose.com/words/net/).
- Lingkungan Pengembangan .NET: Visual Studio adalah pilihan yang populer.
- Contoh Dokumen Word: Siapkan file DOCX yang ingin Anda ubah ke PDF.

## Mengimpor Ruang Nama

Untuk memulai, pastikan Anda telah mengimpor namespace yang diperlukan ke dalam proyek Anda. Ini memungkinkan Anda untuk mengakses kelas dan metode yang diperlukan untuk tugas kita.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Mari kita uraikan prosesnya menjadi beberapa langkah yang sederhana dan mudah dikelola. Setiap langkah akan memandu Anda melalui tugas tersebut, memastikan Anda memahami apa yang terjadi di setiap tahap.

## Langkah 1: Inisialisasi Dokumen Anda

Pertama, kita perlu memuat dokumen Word yang ingin Anda ubah menjadi PDF. Di sinilah perjalanan Anda dimulai.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

Di Sini, `dataDir` adalah tempat penampung untuk direktori tempat dokumen Anda berada. Ganti `"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya.

## Langkah 2: Konfigurasikan Opsi Penyimpanan PDF

Selanjutnya, kita akan mengatur opsi penyimpanan PDF. Di sinilah kita menentukan bahwa kita tidak ingin menyematkan font Windows standar.

```csharp
// Output PDF akan disimpan tanpa menyertakan font Windows standar.
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedNone
};
```

Dengan pengaturan `FontEmbeddingMode` ke `EmbedNone`, kami menginstruksikan Aspose.Words untuk tidak menyertakan font ini dalam PDF, sehingga mengurangi ukuran file.

## Langkah 3: Simpan Dokumen sebagai PDF

Terakhir, kami menyimpan dokumen sebagai PDF menggunakan opsi penyimpanan yang dikonfigurasi. Inilah saat yang tepat saat DOCX Anda berubah menjadi PDF yang ringkas.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.DisableEmbedWindowsFonts.pdf", saveOptions);
```

Mengganti `"YOUR DOCUMENT DIRECTORY"` dengan jalur direktori Anda yang sebenarnya sekali lagi. PDF keluaran sekarang akan disimpan di direktori yang ditentukan tanpa font standar yang disematkan.

## Kesimpulan

Dengan mengikuti langkah-langkah ini, Anda dapat mengurangi ukuran file PDF secara signifikan. Menonaktifkan font yang disematkan adalah cara yang mudah namun efektif untuk membuat dokumen Anda lebih ringan dan mudah dibagikan. Aspose.Words untuk .NET membuat proses ini lancar, memastikan Anda dapat mengoptimalkan file Anda dengan upaya minimal.

## Pertanyaan yang Sering Diajukan

### Mengapa saya harus menonaktifkan font yang tertanam dalam PDF?
Menonaktifkan font yang tertanam dapat mengurangi ukuran file PDF secara signifikan, membuatnya lebih efisien dalam penyimpanan dan lebih cepat untuk dibagikan.

### Apakah PDF akan tetap ditampilkan dengan benar tanpa font yang tertanam?
Ya, selama fontnya standar dan tersedia pada sistem tempat PDF dilihat, PDF akan ditampilkan dengan benar.

### Bisakah saya secara selektif menanamkan hanya font tertentu dalam PDF?
Ya, Aspose.Words untuk .NET memungkinkan Anda menyesuaikan font mana yang disematkan, memberikan fleksibilitas dalam cara Anda mengurangi ukuran file.

### Apakah saya perlu Aspose.Words untuk .NET untuk menonaktifkan font yang tertanam dalam PDF?
Ya, Aspose.Words untuk .NET menyediakan fungsionalitas yang dibutuhkan untuk mengonfigurasi opsi penyematan font dalam PDF.

### Bagaimana cara mendapatkan dukungan jika saya mengalami masalah?
Anda dapat mengunjungi [Forum dukungan](https://forum.aspose.com/c/words/8) untuk bantuan terkait masalah yang Anda hadapi.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}