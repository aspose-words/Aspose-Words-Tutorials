---
"description": "Pelajari cara agar tabel tidak terputus di beberapa halaman dalam dokumen Word menggunakan Aspose.Words untuk .NET. Ikuti panduan kami untuk menjaga dokumen tetap profesional dan mudah dibaca."
"linktitle": "Jaga Meja Tetap Bersama"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Jaga Meja Tetap Bersama"
"url": "/id/net/programming-with-tables/keep-table-together/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jaga Meja Tetap Bersama

## Perkenalan

Pernahkah Anda merasa frustrasi ketika tabel dalam dokumen Word Anda terbagi menjadi dua halaman? Rasanya seperti informasi yang Anda tata dengan saksama tiba-tiba memutuskan untuk berhenti di tengah jalan! Menyatukan tabel dalam satu halaman sangat penting untuk keterbacaan dan penyajian. Baik untuk laporan, proposal proyek, atau sekadar dokumen pribadi, tabel yang terpisah bisa sangat mengganggu. Beruntung bagi kita, Aspose.Words for .NET memiliki cara yang bagus untuk mengatasi masalah ini. Dalam tutorial ini, kami akan memandu Anda melalui langkah-langkah untuk menjaga tabel Anda tetap utuh dan tampak menarik. Mari kita bahas!

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

1. Aspose.Words untuk .NET - Jika Anda belum menginstalnya, Anda dapat mengunduhnya dari [Di Sini](https://releases.aspose.com/words/net/).
2. Dokumen Word dengan Tabel - Kita akan bekerja dengan dokumen contoh yang memiliki tabel yang mencakup beberapa halaman.
3. Pengetahuan Dasar C# - Tutorial ini mengasumsikan Anda memiliki pemahaman dasar tentang pemrograman C#.

## Mengimpor Ruang Nama

Pertama-tama, mari impor namespace yang diperlukan. Ini akan memberi kita akses ke kelas dan metode yang kita butuhkan dari Aspose.Words untuk .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Mari kita uraikan prosesnya menjadi beberapa langkah yang mudah dipahami. Kita akan mulai dengan memuat dokumen kita dan mengakhirinya dengan menyimpan dokumen yang telah diperbarui di mana tabel tetap menyatu.

## Langkah 1: Muat Dokumen

Untuk bekerja dengan dokumen Word, pertama-tama kita perlu memuatnya. Kita akan menggunakan `Document` kelas untuk ini.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Langkah 2: Akses Tabel

Berikutnya, kita perlu mendapatkan tabel yang ingin kita simpan bersama. Kita akan berasumsi bahwa itu adalah tabel pertama dalam dokumen.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Langkah 3: Atur KeepWithNext untuk Paragraf

Untuk mencegah tabel terpecah di beberapa halaman, kita perlu mengatur `KeepWithNext` properti untuk setiap paragraf dalam tabel, kecuali paragraf terakhir di baris terakhir.

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
    foreach (Paragraph para in cell.Paragraphs)
    {
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
    }
}
```

## Langkah 4: Simpan Dokumen

Terakhir, kita simpan dokumen yang sudah diperbarui. Ini akan menerapkan perubahan dan memastikan tabel tetap menyatu pada satu halaman.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

## Kesimpulan

Nah, itu dia! Hanya dengan beberapa baris kode, Anda dapat mencegah tabel Anda terbagi di beberapa halaman dalam dokumen Word Anda. Solusi sederhana namun efektif ini memastikan tabel Anda tetap rapi dan profesional, sehingga meningkatkan keterbacaan dokumen Anda. Aspose.Words untuk .NET memudahkan penanganan masalah pemformatan tersebut, sehingga Anda dapat fokus membuat konten yang hebat.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menyatukan beberapa tabel menggunakan metode ini?  
Ya, Anda dapat menerapkan logika yang sama ke beberapa tabel dengan mengulangi setiap tabel dalam dokumen Anda.

### Bagaimana jika tabel saya terlalu besar untuk dimuat di satu halaman?  
Jika tabel terlalu besar untuk dimuat dalam satu halaman, tabel tersebut akan tetap tersebar di beberapa halaman. Metode ini memastikan tabel yang lebih kecil tetap utuh tanpa terbagi.

### Apakah ada cara untuk mengotomatiskan ini untuk semua tabel dalam dokumen?  
Ya, Anda dapat mengulang semua tabel di dokumen Anda dan menerapkannya `KeepWithNext` properti untuk setiap paragraf.

### Apakah saya memerlukan lisensi berbayar untuk Aspose.Words untuk .NET?  
Anda dapat memulai dengan uji coba gratis dari [Di Sini](https://releases.aspose.com/), tetapi untuk fungsionalitas penuh, lisensi berbayar direkomendasikan.

### Bisakah saya menerapkan format lain ke tabel sembari tetap menyatukannya?  
Tentu saja! Anda dapat memformat tabel sesuai kebutuhan sambil memastikannya tetap menyatu dalam satu halaman.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}