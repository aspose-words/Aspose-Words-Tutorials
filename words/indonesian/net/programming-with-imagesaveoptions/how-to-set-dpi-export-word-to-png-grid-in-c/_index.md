---
category: general
date: 2026-04-10
description: cara mengatur dpi saat mengonversi Word ke PNG. Pelajari cara mengekspor
  Word ke PNG dengan tata letak grid khusus dan resolusi tinggi.
draft: false
keywords:
- how to set dpi
- convert word to png
- how to export word
- export word to png
- create png grid
language: id
og_description: cara mengatur dpi saat mengekspor dokumen Word. tutorial ini menunjukkan
  cara mengonversi Word ke PNG, mengekspor Word ke PNG, dan membuat grid PNG dengan
  C#.
og_title: Cara Mengatur DPI – Panduan Lengkap Mengekspor Word ke PNG
tags:
- C#
- Aspose.Words
- ImageExport
title: cara mengatur dpi – Ekspor Word ke Grid PNG dalam C#
url: /id/net/programming-with-imagesaveoptions/how-to-set-dpi-export-word-to-png-grid-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cara mengatur dpi – Ekspor Word ke PNG Grid dalam C#

Pernah bertanya‑tanya **bagaimana cara mengatur dpi** untuk konversi Word‑ke‑PNG tanpa membuat rambut rontok? Anda tidak sendirian. Dalam banyak proyek—seperti generator laporan otomatis atau pipeline thumbnail—Anda memerlukan PNG yang tajam dengan DPI tertentu, dan seringkali Anda juga ingin beberapa halaman digabungkan menjadi satu gambar grid. Dalam panduan ini kami akan membahas solusi lengkap yang siap dijalankan yang **mengonversi Word ke PNG**, memungkinkan Anda **mengekspor Word ke PNG** dengan pengaturan 300 DPI, dan bahkan **membuat PNG grid** dalam satu langkah.

> **Keuntungan cepat:** Pada akhir artikel ini Anda akan memiliki satu baris kode C# yang mengambil `input.docx` dan menghasilkan `output.png` pada 300 DPI, tersusun dalam grid 2 × 2. Tanpa alat tambahan, tanpa penyuntingan gambar manual.

## Apa yang Akan Anda Pelajari

- Cara **mengatur DPI** menggunakan `Aspose.Words` `ImageSaveOptions`.
- Langkah‑langkah tepat untuk **mengekspor Word ke PNG** dengan tata letak halaman khusus.
- Cara **membuat PNG grid** (empat halaman per baris/kolom) dalam satu berkas.
- Kesulitan umum saat mengonversi dokumen besar dan cara menghindarinya.
- Beberapa variasi: mengekspor halaman individual, mengubah ukuran grid, dan mengganti PNG dengan JPEG.

### Prasyarat

| Persyaratan | Mengapa penting |
|-------------|----------------|
| **Aspose.Words for .NET** (v23.12 atau lebih baru) | Menyediakan kelas `Document` dan `ImageSaveOptions` yang kami gunakan. |
| **.NET 6+** (atau .NET Framework 4.7.2) | Menjamin kompatibilitas dengan API terbaru. |
| **Pengetahuan dasar C#** | Anda perlu memahami namespace dan jalur berkas. |
| **File Word** (`input.docx`) | Dokumen sumber yang akan kami konversi. |

Jika Anda belum menginstal Aspose.Words, jalankan:

```bash
dotnet add package Aspose.Words
```

Setelah semua siap, mari kita selami kodenya.

## Langkah 1 – Muat Dokumen Sumber (cara mengekspor word)

Hal pertama yang Anda lakukan adalah memuat file Word ke memori. Di sinilah **cara mengekspor word** dimulai.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source .docx
Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

> **Tips pro:** Gunakan jalur absolut atau `Path.Combine` untuk menghindari kejutan pada sistem operasi yang berbeda.

## Langkah 2 – Konfigurasikan Image Save Options (cara mengatur dpi & membuat png grid)

Berikut inti tutorial. Kami memberi tahu Aspose.Words secara tepat bagaimana PNG harus terlihat: 300 DPI, format PNG, dan **tata letak grid** yang menampung empat halaman dalam satu gambar.

```csharp
// Create PNG save options with a grid layout
ImageSaveOptions imgOptions = new ImageSaveOptions(SaveFormat.Png)
{
    // Arrange pages in a grid (2 columns × 2 rows = 4 pages)
    PageLayout = ImageSaveOptions.PageLayoutType.Grid,
    
    // Number of columns in the grid – 2 columns => 2 rows for 4 pages
    PageCount = 4,
    
    // Set the DPI – this is where we *how to set dpi*
    HorizontalResolution = 300,
    VerticalResolution = 300
};
```

### Mengapa Pengaturan Ini Penting

- **`PageLayout = Grid`** – Tanpa ini, setiap halaman akan disimpan sebagai PNG terpisah. Opsi grid menggabungkannya, menghemat langkah pasca‑pemrosesan.
- **`PageCount = 4`** – Mengontrol berapa banyak halaman yang akan dimasukkan ke dalam grid. Jika dokumen Anda memiliki lebih dari empat halaman, Aspose akan membuat baris tambahan secara otomatis.
- **Pengaturan DPI** – `HorizontalResolution` dan `VerticalResolution` adalah pengatur yang menjawab pertanyaan **cara mengatur dpi**. Gambar 300 DPI siap cetak dan tampak tajam pada layar retina.

## Langkah 3 – Simpan Dokumen sebagai PNG Tunggal (ekspor word ke png)

Sekarang kita jalankan operasi penyimpanan. Satu baris ini melakukan pekerjaan berat.

```csharp
// Save the document pages as one PNG image
doc.Save(@"YOUR_DIRECTORY\output.png", imgOptions);
```

Setelah baris ini dijalankan, Anda akan menemukan `output.png` di folder yang ditentukan. Buka berkas tersebut, dan Anda akan melihat grid 2 × 2 dari empat halaman pertama, masing‑masing dirender pada 300 DPI.

![contoh cara mengatur dpi](https://example.com/placeholder.png "cara mengatur dpi saat mengekspor Word ke PNG")

*Teks alt gambar: cara mengatur dpi saat mengekspor Word ke PNG – menampilkan PNG grid 2×2.*

## Langkah 4 – Verifikasi Hasil (buat png grid)

Pengecekan cepat dapat menghindarkan masalah di kemudian hari. Anda dapat memverifikasi DPI dan dimensi secara programatik:

```csharp
using System.Drawing;

// Load the generated PNG
using (Bitmap bmp = new Bitmap(@"YOUR_DIRECTORY\output.png"))
{
    Console.WriteLine($"Width: {bmp.Width}px, Height: {bmp.Height}px");
    Console.WriteLine($"Horizontal DPI: {bmp.HorizontalResolution}");
    Console.WriteLine($"Vertical DPI: {bmp.VerticalResolution}");
}
```

Jika konsol mencetak `300` untuk kedua nilai DPI, Anda telah berhasil **cara mengatur dpi**. Lebar dan tinggi akan mencerminkan ukuran gabungan dari empat halaman.

## Variasi Lanjutan

### Konversi Word ke PNG – Satu Berkas per Halaman

Kadang‑kadang Anda memerlukan file PNG terpisah alih‑alih grid. Cukup ubah `PageLayout` menjadi `SinglePage` dan lakukan loop pada halaman:

```csharp
for (int i = 0; i < doc.PageCount; i++)
{
    imgOptions.PageIndex = i;               // Export only this page
    imgOptions.PageLayout = ImageSaveOptions.PageLayoutType.SinglePage;
    doc.Save($@"YOUR_DIRECTORY\page_{i + 1}.png", imgOptions);
}
```

Sekarang Anda memiliki `page_1.png`, `page_2.png`, … – sempurna untuk galeri thumbnail.

### Ekspor Word ke PNG dengan Ukuran Grid Berbeda

Jika Anda membutuhkan grid 3 × 3 (sembilan halaman), cukup sesuaikan `PageCount`:

```csharp
imgOptions.PageCount = 9;          // 3 columns × 3 rows
imgOptions.PageLayout = ImageSaveOptions.PageLayoutType.Grid;
```

Aspose akan otomatis menghitung baris yang diperlukan.

### Ganti PNG dengan JPEG (jika ukuran berkas penting)

Mengubah format semudah mengganti `SaveFormat.Png` dengan `SaveFormat.Jpeg`. Anda juga dapat mengatur kualitas JPEG:

```csharp
ImageSaveOptions jpegOptions = new ImageSaveOptions(SaveFormat.Jpeg)
{
    PageLayout = ImageSaveOptions.PageLayoutType.Grid,
    PageCount = 4,
    HorizontalResolution = 300,
    VerticalResolution = 300,
    JpegQuality = 90   // 0‑100, higher = better quality
};

doc.Save(@"YOUR_DIRECTORY\output.jpg", jpegOptions);
```

### Menangani Dokumen Besar

Saat berurusan dengan dokumen lebih dari 100 halaman, pertimbangkan streaming output untuk menghindari tekanan memori:

```csharp
using (FileStream fs = new FileStream(@"YOUR_DIRECTORY\large_output.png", FileMode.Create))
{
    doc.Save(fs, imgOptions);
}
```

Streaming memastikan proses tetap ringan, bahkan pada server dengan sumber daya terbatas.

## Kesalahan Umum & Cara Menghindarinya

| Gejala | Penyebab | Solusi |
|--------|----------|--------|
| PNG terlihat buram | DPI tetap pada default 96 | **Setel `HorizontalResolution` dan `VerticalResolution` ke 300** (atau lebih tinggi). |
| Hanya halaman pertama yang muncul | `PageLayout` masih `SinglePage` | Ganti ke `ImageSaveOptions.PageLayoutType.Grid`. |
| Ukuran berkas output sangat besar | Format PNG dengan 300 DPI dapat besar | Gunakan JPEG dengan `JpegQuality` < 90, atau turunkan DPI bila kualitas cetak tidak diperlukan. |
| Grid memotong margin halaman | Penanganan margin default | Sesuaikan `ImageSaveOptions.PageMargins` bila diperlukan. |

## Ringkasan – Apa yang Telah Kita Bahas

- **cara mengatur dpi** – dengan mengonfigurasi `HorizontalResolution` dan `VerticalResolution`.
- **konversi word ke png** – menggunakan `ImageSaveOptions` dengan `SaveFormat.Png`.
- **cara mengekspor word** – memuat dokumen dengan `Document` dan memanggil `Save`.
- **ekspor word ke png** – satu baris kode yang menghasilkan PNG resolusi tinggi.
- **buat png grid** – mengatur `PageLayout = Grid` dan `PageCount` untuk mengontrol tata letak.

Semua ini dapat dimasukkan ke dalam potongan kode C# yang ringkas dan mandiri, siap ditempatkan di proyek .NET mana pun.

## Apa Selanjutnya?

- Bereksperimen dengan **nilai DPI berbeda** (150, 600) untuk melihat bagaimana ukuran berkas berubah.
- Gabungkan pendekatan ini dengan **Aspose.PDF** untuk menggabungkan grid PNG ke dalam laporan PDF.
- Jelajahi **konversi ruang warna** (RGB → CMYK) bila Anda mengirim PNG ke percetakan profesional.
- Pelajari **penyimpanan asynchronous** (`doc.SaveAsync`) untuk aplikasi yang responsif pada UI.

Punya pertanyaan tentang kasus khusus—seperti mengekspor file DOCX terenkripsi atau menangani font tersemat? Tinggalkan komentar, dan saya akan menggali lebih dalam.

---

*Selamat coding! Jika tutorial ini membantu Anda **cara mengatur dpi** dan mengekspor dokumen Word ke PNG grid yang elegan, beri bintang atau bagikan kepada rekan yang sedang berjuang dengan masalah serupa.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}