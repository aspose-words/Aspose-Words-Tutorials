---
category: general
date: 2026-07-03
description: Cara mengatur bayangan pada bentuk di C# menggunakan Aspose.Words. Pelajari
  cara menambahkan bayangan ke bentuk, mengubah blur, menyesuaikan transparansi, dan
  menyimpan dokumen sebagai PDF.
draft: false
keywords:
- how to set shadow
- add shadow to shape
- save document as pdf
- how to change blur
- how to adjust transparency
language: id
og_description: Cara mengatur bayangan pada bentuk di C# dengan Aspose.Words. Panduan
  ini menunjukkan cara menambahkan bayangan ke bentuk, mengubah blur, menyesuaikan
  transparansi, dan menyimpan dokumen sebagai PDF.
og_title: Cara Menambahkan Bayangan pada Bentuk di C# – Tutorial Lengkap Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: How to set shadow on a shape in C# using Aspose.Words. Learn to add
    shadow to shape, change blur, adjust transparency, and save document as PDF.
  headline: How to Set Shadow on Shapes in C# – Complete Aspose.Words Guide
  type: TechArticle
- description: How to set shadow on a shape in C# using Aspose.Words. Learn to add
    shadow to shape, change blur, adjust transparency, and save document as PDF.
  name: How to Set Shadow on Shapes in C# – Complete Aspose.Words Guide
  steps:
  - name: – Load the Word Document
    text: '```csharp using System; using System.Drawing; // For Color using Aspose.Words;
      using Aspose.Words.Drawing; // Shape and shadow types'
  - name: – Retrieve the Target Shape
    text: '```csharp // Grab the first shape in the document (index 0). Shape shape
      = (Shape)doc.GetChild(NodeType.Shape, 0, true); if (shape == null) { Console.WriteLine("No
      shape found – make sure your .docx contains a drawing."); return; } ```'
  - name: – Add Shadow to Shape (Core of “how to set shadow”)
    text: '```csharp // Enable shadow and set its basic properties. shape.ShadowFormat.Visible
      = true; // Turn the shadow on. shape.ShadowFormat.Distance = 4.0; // Distance
      from the shape (in points). shape.ShadowFormat.BlurRadius = 6.0; // Softness
      of the shadow. shape.ShadowFormat.Transparency = 0.3; // 30 %'
  - name: – How to Change Blur on the Shadow
    text: '```csharp // Increase blur for a softer look, or decrease for a crisp edge.
      shape.ShadowFormat.BlurRadius = 12.0; // Example of a heavier blur. ```'
  - name: – How to Adjust Transparency of the Shadow
    text: '```csharp // Make the shadow more subtle. shape.ShadowFormat.Transparency
      = 0.6; // 60 % transparent (more see‑through). ```'
  - name: – Save Document as PDF to View the Shadow Effect
    text: '```csharp // Export the modified document to PDF so you can see the shadow.
      doc.Save("YOUR_DIRECTORY/ShadowAdjusted.pdf", SaveFormat.Pdf); Console.WriteLine("PDF
      saved – open ShadowAdjusted.pdf to see the shadow."); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- PDF generation
title: Cara Menambahkan Bayangan pada Bentuk di C# – Panduan Lengkap Aspose.Words
url: /id/net/programming-with-shapes/how-to-set-shadow-on-shapes-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menetapkan Bayangan pada Bentuk di C# – Panduan Lengkap Aspose.Words

Pernah bertanya-tanya **cara menetapkan bayangan** pada sebuah bentuk saat menghasilkan dokumen secara programatis? Menurut pengalaman saya, sentuhan visual berupa bayangan halus dapat mengubah diagram yang membosankan menjadi sesuatu yang benar‑benar *menonjol* di halaman. Kabar baik? Dengan Aspose.Words Anda dapat **menambahkan bayangan ke bentuk** hanya dengan beberapa baris kode C#, menyesuaikan blur, mengontrol transparansi, dan kemudian **menyimpan dokumen sebagai PDF** untuk melihat efeknya secara langsung.

Dalam tutorial ini kami akan membahas setiap langkah yang Anda perlukan untuk menguasai penataan bayangan: memuat file Word, menemukan sebuah bentuk, mengonfigurasi `ShadowFormat`‑nya, dan akhirnya mengekspor hasilnya sebagai PDF. Pada akhir tutorial Anda akan mengetahui **cara mengubah blur**, memahami **cara menyesuaikan transparansi**, dan memiliki cuplikan kode siap‑jalankan yang dapat Anda sisipkan ke proyek .NET mana pun.

## Cara Menetapkan Bayangan pada Bentuk di Aspose.Words

Hal pertama yang Anda perlukan adalah referensi ke pustaka Aspose.Words. Jika Anda belum menginstalnya, jalankan:

```bash
dotnet add package Aspose.Words
```

Sekarang mari kita selami kode. Kami akan membagi proses menjadi langkah‑langkah kecil sehingga Anda dapat melihat dengan tepat mengapa setiap baris penting.

### Langkah 1 – Muat Dokumen Word

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;
using Aspose.Words.Drawing;        // Shape and shadow types

// Load a document that already contains at least one shape.
Document doc = new Document("YOUR_DIRECTORY/Shapes.docx");
```

*Mengapa ini penting:*  
`Document` adalah titik masuk untuk setiap operasi di Aspose.Words. Dengan memuat file yang sudah memiliki bentuk, kita menghindari boilerplate tambahan untuk membuat bentuk dari awal—sempurna untuk demo “cara menetapkan bayangan” yang terfokus.

### Langkah 2 – Ambil Bentuk Target

```csharp
// Grab the first shape in the document (index 0). 
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (shape == null)
{
    Console.WriteLine("No shape found – make sure your .docx contains a drawing.");
    return;
}
```

*Apa yang terjadi di sini?*  
`GetChild` menelusuri pohon DOM dan mengembalikan node pertama bertipe `Shape`. Flag `true` memberi tahu API untuk mencari secara rekursif, yang berguna ketika bentuk berada di dalam header, footer, atau kotak teks.

### Langkah 3 – Tambahkan Bayangan ke Bentuk (Inti dari “cara menetapkan bayangan”)

```csharp
// Enable shadow and set its basic properties.
shape.ShadowFormat.Visible = true;          // Turn the shadow on.
shape.ShadowFormat.Distance = 4.0;          // Distance from the shape (in points).
shape.ShadowFormat.BlurRadius = 6.0;        // Softness of the shadow.
shape.ShadowFormat.Transparency = 0.3;      // 30 % transparent.
shape.ShadowFormat.Color = Color.Black;    // Shadow color.
```

**Cara menambahkan bayangan ke bentuk** – itulah baris yang Anda cari. Menetapkan `Visible` ke `true` mengaktifkan efek; sisanya menyesuaikan tampilan secara halus. Jangan ragu bereksperimen dengan warna atau jarak lain untuk menyesuaikan dengan merek Anda.

#### Pro tip
Jika Anda membutuhkan drop shadow yang meniru sumber cahaya dari kiri‑atas, juga setel `shape.ShadowFormat.Angle = 45;` dan `shape.ShadowFormat.Distance = 2.0;`. Penyesuaian kecil ini menambah realisme tanpa kode tambahan.

### Langkah 4 – Cara Mengubah Blur pada Bayangan

```csharp
// Increase blur for a softer look, or decrease for a crisp edge.
shape.ShadowFormat.BlurRadius = 12.0;   // Example of a heavier blur.
```

Mengubah `BlurRadius` secara langsung menjawab **cara mengubah blur**. Nilainya diukur dalam poin; angka yang lebih besar menghasilkan bayangan yang lebih tersebar. Perlu diingat bahwa nilai blur yang sangat tinggi dapat sedikit meningkatkan ukuran file PDF karena renderer harus menyimpan lebih banyak informasi grafis.

### Langkah 5 – Cara Menyesuaikan Transparansi Bayangan

```csharp
// Make the shadow more subtle.
shape.ShadowFormat.Transparency = 0.6;   // 60 % transparent (more see‑through).
```

Properti `Transparency` menerima nilai double antara `0.0` (sepenuhnya opak) dan `1.0` (sepenuhnya tidak terlihat). Ini adalah jawaban tepat untuk **cara menyesuaikan transparansi** bayangan sebuah bentuk. Gunakan nilai lebih rendah untuk elemen UI yang tebal, nilai lebih tinggi untuk dekorasi latar belakang.

### Langkah 6 – Simpan Dokumen sebagai PDF untuk Melihat Efek Bayangan

```csharp
// Export the modified document to PDF so you can see the shadow.
doc.Save("YOUR_DIRECTORY/ShadowAdjusted.pdf", SaveFormat.Pdf);
Console.WriteLine("PDF saved – open ShadowAdjusted.pdf to see the shadow.");
```

Di sini kami akhirnya **menyimpan dokumen sebagai PDF**, yang merupakan cara paling dapat diandalkan untuk memverifikasi perubahan visual di berbagai platform. PDF mempertahankan rendering tepat dari Aspose.Words, tidak seperti pratinjau Word yang mungkin menyembunyikan efek halus.

## Menambahkan Bayangan ke Bentuk dengan Pengaturan Kustom (Lanjutan)

Terkadang Anda menginginkan bayangan yang cocok dengan palet warna merek. Anda dapat menggabungkan langkah‑langkah sebelumnya menjadi metode yang dapat digunakan kembali:

```csharp
/// <summary>
/// Applies a customized shadow to the provided shape.
/// </summary>
static void ApplyCustomShadow(Shape shape, double distance, double blur, double transparency, Color color)
{
    shape.ShadowFormat.Visible = true;
    shape.ShadowFormat.Distance = distance;
    shape.ShadowFormat.BlurRadius = blur;
    shape.ShadowFormat.Transparency = transparency;
    shape.ShadowFormat.Color = color;
}

// Usage example:
ApplyCustomShadow(shape, 5.0, 8.0, 0.25, Color.FromArgb(80, 0, 0, 0));
```

*Mengapa membungkusnya?*  
Enkapsulasi menjaga alur kerja utama tetap bersih dan memungkinkan Anda **menambahkan bayangan ke bentuk** dengan satu panggilan di mana pun Anda membutuhkannya—sempurna untuk memproses batch puluhan dokumen.

## Menyimpan Dokumen sebagai PDF – Kesalahan Umum

- **Masalah jalur file:** Selalu gunakan jalur absolut atau `Path.Combine` untuk menghindari error “file not found”.
- **Pembatasan lisensi:** Jika Anda menggunakan versi evaluasi gratis Aspose.Words, PDF yang dihasilkan akan berisi watermark. Beli lisensi untuk mendapatkan output bersih.
- **Penyematan font:** Pastikan font yang digunakan dalam `.docx` asli tersedia di server; jika tidak PDF dapat menggantinya, memengaruhi tampilan bayangan.

## Mengubah Radius Blur Secara Dinamis (Skenario Dunia Nyata)

Bayangkan Anda sedang membuat katalog di mana gambar produk memerlukan bayangan yang lebih kuat untuk penekanan. Anda dapat menghitung `BlurRadius` berdasarkan ukuran gambar:

```csharp
double ComputeBlur(double imageWidth)
{
    // Larger images get a softer shadow.
    return Math.Max(4.0, imageWidth / 50.0);
}

// Later in the pipeline:
double blur = ComputeBlur(shape.Width);
shape.ShadowFormat.BlurRadius = blur;
```

## Menyesuaikan Transparansi Berdasarkan Latar Belakang (Tip Praktis)

Jika latar belakang dokumen berwarna gelap, bayangan berwarna terang mungkin lebih terlihat. Berikut cara cepat untuk menentukan transparansi:

```csharp
double DetermineTransparency(Color background)
{
    // Dark backgrounds → lighter (more transparent) shadows.
    return background.GetBrightness() < 0.5 ? 0.5 : 0.2;
}

// Apply:
shape.ShadowFormat.Transparency = DetermineTransparency(Color.White);
```

## Contoh Lengkap yang Berfungsi

Berikut adalah program lengkap yang siap dijalankan yang menggabungkan semuanya. Salin‑tempel ke aplikasi console, ganti `YOUR_DIRECTORY` dengan folder yang nyata, dan lihat PDF muncul.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source document.
        Document doc = new Document("YOUR_DIRECTORY/Shapes.docx");

        // 2️⃣ Find the first shape.
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found in the document.");
            return;
        }

        // 3️⃣ Apply a custom shadow (how to set shadow).
        ApplyCustomShadow(shape, distance: 4.0, blur: 10.0, transparency: 0.35, color: Color.Black);

        // 4️⃣ Save as PDF (save document as pdf) to view the result.
        doc.Save("YOUR_DIRECTORY/ShadowAdjusted.pdf", SaveFormat.Pdf);
        Console.WriteLine("Shadow applied and PDF saved successfully.");
    }

    /// <summary>
    /// Configures shadow properties for a shape.
    /// </summary>
    static void ApplyCustomShadow(Shape shape, double distance, double blur, double transparency, Color color)
    {
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.Distance = distance;          // distance from shape
        shape.ShadowFormat.BlurRadius = blur;            // how to change blur
        shape.ShadowFormat.Transparency = transparency; // how to adjust transparency
        shape.ShadowFormat.Color = color;                // shadow color
    }
}
```

**Output yang diharapkan:** Buka `ShadowAdjusted.pdf`. Anda akan melihat bentuk asli (seringkali persegi panjang atau gambar) kini ditampilkan dengan bayangan hitam lembut, semi‑transparan yang dipindahkan 4 pt. Blur akan terlihat halus, dan PDF akan menampilkan tepat apa yang Anda lihat di pratinjau cetak Word.

## Kesimpulan

Kami telah membahas **cara menetapkan bayangan** pada sebuah bentuk menggunakan Aspose.Words, mendemonstrasikan **menambahkan bayangan ke bentuk**, menjelaskan **cara mengubah blur**, menunjukkan **cara menyesuaikan transparansi**, dan akhirnya **menyimpan dokumen sebagai PDF** untuk memverifikasi efeknya. Pendekatannya modular, sehingga Anda dapat menggunakan kembali helper `ApplyCustomShadow` di berbagai proyek, menyesuaikan parameter secara dinamis, bahkan memperluasnya untuk mendukung banyak bentuk per dokumen.

Langkah selanjutnya? Coba lapiskan beberapa bayangan, bereksperimen dengan warna berbeda, atau gabungkan teknik ini dengan penataan tabel untuk laporan yang rapi. Jika Anda tertarik pada manipulasi grafis yang lebih mendalam, selidiki properti `ShapeBase` Aspose.Words seperti `OutlineFormat` atau jelajahi opsi rendering PDF untuk kontrol yang lebih halus.

Selamat coding, semoga dokumen Anda selalu memiliki kedalaman yang tepat!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [How to Add Shadow in C# – Complete Programming Guide](/words/english/python-net/images-shapes/how-to-add-shadow-in-c-complete-programming-guide/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}