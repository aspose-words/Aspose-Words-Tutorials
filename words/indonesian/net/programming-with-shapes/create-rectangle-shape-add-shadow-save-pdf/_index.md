---
category: general
date: 2026-02-24
description: Buat bentuk persegi panjang di C# menggunakan Aspose.Words, tambahkan
  bayangan pada bentuk, dan simpan dokumen sebagai PDF. Pelajari cara menambahkan
  bayangan dan cara menyimpan PDF dalam hitungan menit.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- how to save pdf
language: id
og_description: Buat bentuk persegi panjang di C# dengan Aspose.Words, kemudian tambahkan
  bayangan pada bentuk tersebut dan simpan dokumen sebagai PDF – panduan lengkap langkah
  demi langkah.
og_title: Buat bentuk persegi panjang, tambahkan bayangan, dan simpan PDF
tags:
- Aspose.Words
- C#
- PDF generation
title: Buat bentuk persegi panjang, tambahkan bayangan & simpan PDF
url: /id/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat bentuk persegi panjang, tambahkan bayangan & simpan sebagai PDF

Pernah membutuhkan untuk **membuat bentuk persegi panjang** dalam dokumen Word tetapi juga menginginkan bayangan jatuh yang bagus dan output PDF? Anda bukan satu-satunya. Dalam banyak proyek pelaporan atau pembuatan faktur, sentuhan visual—seperti bayangan halus—menjadi perbedaan antara “hanya file lain” dan “dokumen kelas profesional.”  

Dalam tutorial ini kami akan membahas langkah demi langkah: menggunakan **Aspose.Words for .NET** untuk membuat bentuk persegi panjang, menambahkan bayangan ke bentuk, dan akhirnya **menyimpan dokumen sebagai PDF**. Pada akhir tutorial Anda akan memiliki aplikasi konsol C# siap‑jalankan yang menghasilkan PDF dengan persegi panjang berbayangan, dan Anda akan memahami cara menyesuaikan bayangan atau mengubah opsi ekspor.

## Apa yang Anda butuhkan

- .NET 6 SDK (atau versi .NET terbaru lainnya) – API berfungsi sama pada .NET Framework 4.x juga.  
- Aspose.Words for .NET NuGet package (`Aspose.Words`) – instal dengan `dotnet add package Aspose.Words`.  
- Editor kode – Visual Studio, VS Code, atau Rider sudah cukup.  

Tidak ada langkah lisensi tambahan untuk contoh ini; mode evaluasi gratis sudah cukup untuk melihat output PDF.

## Langkah 1: Siapkan proyek dan impor namespace

Langkah pertama, mari buat proyek konsol dan impor kelas-kelas yang akan kita gunakan.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code lives here – see the following steps.
        }
    }
}
```

*Mengapa ini penting:* `Document` dan `DocumentBuilder` memberi kami kanvas, sementara `Shape` dan `ShadowFormat` memungkinkan kami menggambar dan menata persegi panjang. Mengimpornya di awal membuat kode selanjutnya lebih rapi.

## Langkah 2: **Buat bentuk persegi panjang** dengan dimensi yang diinginkan

Sekarang kita benar-benar membuat dokumen kosong dan menyisipkan persegi panjang. Perhatikan bagaimana metode `InsertShape` mengembalikan objek `Shape` yang dapat langsung kita beri gaya.

```csharp
// Inside Main()
Document document = new Document();               // blank Word document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle of 200x100 points (≈2.78" × 1.39")
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rectangle.FillColor = System.Drawing.Color.LightBlue;
```

*Penjelasan*: Ukuran dinyatakan dalam poin (1 pt = 1/72 in). Sesuaikan angka-angka tersebut agar cocok dengan tata letak Anda. Kami juga memberi bentuk isian biru muda agar bayangan lebih menonjol.

## Langkah 3: **Tambahkan bayangan ke bentuk** – sesuaikan efeknya

Bayangan bukan sekadar “hidup/mati.” Anda dapat mengontrol warna, keburaman, jarak, arah, bahkan transparansi. Berikut konfigurasi praktis yang bekerja baik untuk kebanyakan laporan.

```csharp
// Access the shape's shadow format
ShadowFormat shadow = rectangle.ShadowFormat;
shadow.Visible = true;                     // turn the shadow on
shadow.Color = System.Drawing.Color.Gray;  // shadow colour
shadow.BlurRadius = 5.0;                    // soft edges (higher = blurrier)
shadow.Distance = 4.0;                      // how far the shadow is from the shape
shadow.Direction = 45;                     // angle in degrees (45° = down‑right)
shadow.Transparency = 0.3;                  // 30 % transparent for a subtle look
```

*Mengapa Anda mungkin mengubah nilai-nilai ini:*  
- **BlurRadius** – tingkatkan untuk efek dreamy, turunkan untuk tepi yang tajam.  
- **Direction** – 0° mengarah ke kanan, 90° ke bawah, 180° ke kiri, dll. Putar sesuai tata letak halaman Anda.  
- **Transparency** – atur ke `0` untuk bayangan solid, `0.5` untuk setengah transparan, dll.

### Cara menambahkan bayangan – pendekatan alternatif

Jika Anda membutuhkan **bayangan berlapis‑ganda** (mis., bayangan luar yang lebih gelap ditambah bayangan dalam yang lebih terang), Anda dapat membuat bentuk kedua, menggesernya, dan mengatur `ShadowFormat` yang berbeda. Atau, untuk tampilan “tanpa keburaman” cepat, atur `BlurRadius = 0`.

## Langkah 4: **Simpan dokumen sebagai PDF** – ekspor akhir

Dengan persegi panjang dan bayangannya siap, langkah terakhir adalah menulis file sebagai PDF. Aspose.Words menangani konversi secara internal; Anda cukup memanggil `Save` dengan format yang diinginkan.

```csharp
// Define the output path – adjust to your environment
string outputPath = @"C:\Temp\ShadowRectangle.pdf";

// Save as PDF (the format is inferred from the extension)
document.Save(outputPath);
Console.WriteLine($"PDF saved to {outputPath}");
```

*Tip*: Jika Anda perlu mengontrol kepatuhan PDF (PDF/A, PDF/X) atau menyematkan font, gunakan overload:

```csharp
PdfSaveOptions options = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfA1b,
    EmbedFullFonts = true
};
document.Save(outputPath, options);
```

Itulah bagian **cara menyimpan pdf** secara singkat.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke `Program.cs`. Program ini dapat dikompilasi dan dijalankan apa adanya (pastikan folder output sudah ada).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document and a builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert a rectangle shape
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // 3️⃣ Add a shadow to the shape
            ShadowFormat shadow = rectangle.ShadowFormat;
            shadow.Visible = true;
            shadow.Color = System.Drawing.Color.Gray;
            shadow.BlurRadius = 5.0;
            shadow.Distance = 4.0;
            shadow.Direction = 45;
            shadow.Transparency = 0.3;

            // 4️⃣ Save the document as PDF
            string outputPath = @"C:\Temp\ShadowRectangle.pdf";
            document.Save(outputPath);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

### Hasil yang diharapkan

Buka `ShadowRectangle.pdf` yang dihasilkan. Anda akan melihat satu halaman dengan persegi panjang biru muda, bayangan abu‑abu lembut yang bergeser 45° ke kanan‑bawah, dan tepi yang bersih. PDF tersebut dapat dilihat di pembaca modern apa pun (Adobe Acrobat, Edge, Chrome).

![Buat bentuk persegi panjang dengan bayangan dalam PDF](/images/shadow-rectangle.png "Buat bentuk persegi panjang dengan bayangan")

*(Teks alt gambar mencakup kata kunci utama untuk SEO.)*

## Pertanyaan umum & penanganan kasus‑tepi

**Bagaimana jika bayangan menghilang di PDF?**  
Pastikan Anda menggunakan versi terbaru Aspose.Words (≥23.3). Versi lama memiliki bug di mana beberapa properti bayangan diabaikan selama konversi PDF.

**Bisakah saya mengubah warna bayangan agar sesuai dengan merek saya?**  
Tentu—ganti saja `System.Drawing.Color.Gray` dengan `Color` apa pun yang Anda suka, misalnya `Color.FromArgb(128, 0, 0, 255)` untuk biru semi‑transparan.

**Bagaimana cara menambahkan bayangan ke bentuk lain (elips, bintang, dll.)?**  
`ShadowFormat` yang sama bekerja untuk objek `Shape` apa pun. Setelah Anda membuat bentuk, ambil `ShadowFormat`-nya dan atur properti-propertinya.

**Bagaimana dengan masalah DPI atau skala?**  
Rendering PDF menghormati ukuran poin bentuk. Jika Anda membutuhkan output resolusi lebih tinggi (untuk pencetakan), sesuaikan dimensi bentuk atau atur `PdfSaveOptions.ImageResolution`.

**Bisakah saya mengekspor ke format lain, seperti PNG?**  
Ya—cukup panggil `document.Save("output.png", SaveFormat.Png)`. Bayangan akan dirender dengan cara yang sama.

## Tips profesional & praktik terbaik

- **Gunakan kembali builder**: Jika Anda menambahkan banyak bentuk, pertahankan satu instance `DocumentBuilder`; lebih murah daripada membuat banyak.  
- **Penyimpanan batch**: Saat menghasilkan banyak PDF dalam loop, gunakan kembali objek `PdfSaveOptions` untuk menghindari alokasi berulang.  
- **Pengujian**: Selalu buka PDF setelah menyimpan untuk memverifikasi bahwa bayangan muncul seperti yang diharapkan. Beberapa penampil PDF merender bayangan sedikit berbeda; Adobe Acrobat adalah referensi paling dapat diandalkan.  
- **Kinerja**: Untuk dokumen besar, nonaktifkan pemecahan halaman otomatis `DocumentBuilder.InsertShape` dengan mengatur `builder.PageSetup.DifferentFirstPageHeaderFooter = false` jika tidak diperlukan.

## Kesimpulan

Kami telah membahas semua yang Anda perlukan untuk **membuat bentuk persegi panjang**, **menambahkan bayangan ke bentuk**, dan **menyimpan dokumen sebagai PDF** menggunakan Aspose.Words for .NET. Kode ini ringkas, konsepnya dijelaskan, dan Anda kini memiliki dasar yang kuat untuk bereksperimen dengan bentuk lain, gaya bayangan, dan opsi ekspor.  

Langkah selanjutnya? Coba ganti persegi panjang dengan bentuk ber‑rounded‑

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}