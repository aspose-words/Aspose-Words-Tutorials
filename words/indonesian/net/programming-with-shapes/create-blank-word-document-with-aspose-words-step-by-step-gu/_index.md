---
category: general
date: 2026-02-23
description: Buat dokumen Word kosong menggunakan C# dan Aspose.Words. Pelajari cara
  menambahkan bentuk persegi panjang, menambahkan bayangan pada teks, dan menyimpan
  Word dengan bentuk dalam hitungan menit.
draft: false
keywords:
- create blank word document
- add rectangle shape
- how to add shape
- add shadow word
- save word with shape
language: id
og_description: Buat dokumen Word kosong dengan cepat. Panduan ini menunjukkan cara
  menambahkan bentuk persegi panjang, menambahkan bayangan pada kata, dan menyimpan
  Word dengan bentuk menggunakan Aspose.Words.
og_title: Buat dokumen Word kosong – Tutorial C# Lengkap
tags:
- Aspose.Words
- C#
- Document Automation
title: Buat dokumen Word kosong dengan Aspose.Words – Panduan Langkah demi Langkah
url: /id/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen Word kosong – Tutorial C# Lengkap

Pernah bertanya-tanya bagaimana cara **create blank word document** secara programatis tanpa membuka Microsoft Word? Anda tidak sendirian. Dalam banyak proyek otomasi kami membutuhkan file .docx baru, menambahkan sebuah shape di dalamnya, memberi shape tersebut bayangan yang bagus, dan kemudian **save word with shape** untuk penggunaan selanjutnya.  

Dalam panduan ini kami akan membahas langkah demi langkah—dimulai dari dokumen kosong, **adding a rectangle shape**, mengonfigurasi efek **add shadow word**, dan akhirnya menyimpan file. Pada akhir tutorial Anda akan memiliki potongan kode lengkap yang dapat ditempelkan ke aplikasi console .NET apa pun. Tanpa misteri, tanpa bagian yang hilang.

## Apa yang Anda Butuhkan

- **Aspose.Words for .NET** (versi terbaru apa pun, misalnya 24.10).  
- .NET 6 atau yang lebih baru (kode ini juga bekerja dengan .NET Framework 4.7+).  
- IDE C# dasar—Visual Studio, Rider, atau bahkan VS Code dengan ekstensi C#.  

Itu saja. Tidak ada paket NuGet tambahan selain Aspose.Words, dan tidak memerlukan instalasi Word.

---

## Langkah 1: Buat dokumen Word kosong

Hal pertama yang Anda lakukan ketika ingin **create blank word document** adalah menginstansiasi kelas `Document`. Anggap saja ini sebagai kanvas bersih yang disediakan Aspose.Words untuk Anda.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1 – initialize an empty document
Document document = new Document();   // this is a brand‑new, blank Word file
```

> **Mengapa ini penting:** Objek `Document` menyimpan semua section, paragraph, dan shape. Memulai dengan instance kosong menjamin Anda mengendalikan setiap elemen yang akan ditambahkan kemudian.

---

## Langkah 2: Tambahkan shape persegi panjang ke dokumen

Sekarang kita memiliki dokumen bersih, mari **add rectangle shape**. Sebuah persegi panjang adalah `Shape` sederhana dengan `ShapeType.Rectangle`. Tentu saja Anda dapat memilih tipe lain, tetapi persegi panjang cocok untuk demonstrasi.

```csharp
// Step 2 – create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width = 200,   // width in points (≈2.78 inches)
    Height = 100   // height in points (≈1.39 inches)
};
```

> **Pro tip:** Jika Anda pernah bertanya-tanya **how to add shape** yang bukan persegi panjang, cukup ubah `ShapeType.Rectangle` ke nilai enum lain seperti `ShapeType.Ellipse` atau `ShapeType.Polygon`. Sisanya tetap sama.

---

## Langkah 3: Konfigurasikan bayangan khusus untuk shape

Persegi panjang biasa terlihat agak datar, jadi kami akan **add shadow word** untuk membuatnya lebih hidup. Aspose.Words menyediakan objek `ShadowFormat` dengan banyak properti.

```csharp
// Step 3 – enable and style the shadow
rectangleShape.ShadowFormat.Enabled = true;                // turn on the shadow
rectangleShape.ShadowFormat.Color = Color.Gray;           // shadow color
rectangleShape.ShadowFormat.OffsetX = 5;                  // horizontal offset (points)
rectangleShape.ShadowFormat.OffsetY = 5;                  // vertical offset (points)
rectangleShape.ShadowFormat.Transparency = 0.3;           // 30 % transparent
rectangleShape.ShadowFormat.BlurRadius = 4;               // soft edge blur
```

> **Mengapa ini penting:** Bayangan memberikan kesan kedalaman halus, terutama ketika dokumen akan dilihat di layar. Sesuaikan `OffsetX`, `OffsetY`, dan `BlurRadius` sesuai bahasa desain Anda.

---

## Langkah 4: Sisipkan shape ke dalam dokumen

Setelah shape siap, kita perlu menempatkannya di suatu tempat. Titik paling sederhana adalah paragraf pertama pada section pertama. Jika dokumen belum memiliki paragraf, Aspose secara otomatis membuatnya.

```csharp
// Step 4 – put the rectangle into the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **Edge case:** Jika Anda berencana menyisipkan shape ke lokasi tertentu (misalnya setelah heading tertentu), temukan `Paragraph` target melalui `document.GetChildNodes(NodeType.Paragraph, true)` dan gunakan `InsertAfter` atau `InsertBefore` sesuai kebutuhan.

---

## Langkah 5: Simpan dokumen Word dengan shape

Akhirnya, kami **save word with shape** ke disk. Metode `Save` secara otomatis menentukan format berdasarkan ekstensi file.

```csharp
// Step 5 – persist the document
string outputPath = @"C:\Temp\shadowedRectangle.docx";
document.Save(outputPath);
```

> **Apa yang akan Anda lihat:** Buka `shadowedRectangle.docx` di Word (atau penampil kompatibel lainnya) dan Anda akan melihat persegi panjang abu-abu dengan bayangan lembut di bagian atas halaman pertama.

---

## Contoh Lengkap yang Berfungsi

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke aplikasi console. Program ini mencakup semua directive `using`, komentar, dan langkah-langkah persis yang telah dibahas.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeWordShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank word document
            Document document = new Document();

            // 2️⃣ Add a rectangle shape
            Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100
            };

            // 3️⃣ Configure a custom shadow (add shadow word)
            rectangleShape.ShadowFormat.Enabled = true;
            rectangleShape.ShadowFormat.Color = Color.Gray;
            rectangleShape.ShadowFormat.OffsetX = 5;
            rectangleShape.ShadowFormat.OffsetY = 5;
            rectangleShape.ShadowFormat.Transparency = 0.3;
            rectangleShape.ShadowFormat.BlurRadius = 4;

            // 4️⃣ Insert the shape into the first paragraph
            document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

            // 5️⃣ Save the document (save word with shape)
            string outputFile = @"YOUR_DIRECTORY\shadow.docx";
            document.Save(outputFile);

            // Confirmation
            System.Console.WriteLine($"Document saved to {outputFile}");
        }
    }
}
```

Jalankan program, buka folder `YOUR_DIRECTORY`, dan buka `shadow.docx` yang dihasilkan. Anda akan melihat persegi panjang dengan bayangan abu-abu halus—tepat seperti yang kami inginkan.

---

## Pertanyaan yang Sering Diajukan & Tips

### Bagaimana cara mengubah warna shape?
```csharp
rectangleShape.FillColor = Color.LightBlue;
```
Cukup set `FillColor` sebelum menambahkan shape.

### Bagaimana jika saya membutuhkan beberapa shape pada halaman yang sama?
Buat objek `Shape` tambahan dan tambahkan masing‑masing ke paragraf yang sama atau ke paragraf yang berbeda. Anda juga dapat mengontrol tata letak menggunakan `WrapType` dan `RelativeHorizontalPosition`.

### Bisakah saya mengekspor ke PDF sambil mempertahankan bayangan?
Tentu saja. Gunakan `document.Save("output.pdf")`—Aspose.Words mempertahankan efek bayangan dalam konversi PDF.

### Apakah ini bekerja di .NET Core?
Ya. Aspose.Words bersifat lintas‑platform; kode yang sama berjalan di .NET Core, .NET 5+, dan .NET Framework.

### Bagaimana menambahkan shape tanpa paragraf?
Anda dapat menambahkan shape langsung ke `Run` atau ke `Story`. Untuk penempatan yang lebih tepat, set `rectangleShape.RelativeHorizontalPosition = RelativeHorizontalPosition.Page` dan sesuaikan properti `Left`/`Top`.

---

## Hasil Visual

![Bentuk persegi panjang dengan bayangan abu-abu dalam dokumen Word – add shadow word example](https://example.com/placeholder-image.png "add shadow word example")

*Teks alt gambar mencakup kata kunci sekunder **add shadow word** untuk memenuhi kebutuhan SEO.*

---

## Kesimpulan

Kami baru saja mendemonstrasikan cara **create blank word document**, **add rectangle shape**, menerapkan efek **add shadow word**, dan akhirnya **save word with shape** menggunakan Aspose.Words untuk .NET. Prosesnya sederhana: instansiasi `Document`, buat `Shape`, sesuaikan `ShadowFormat`, sisipkan, dan panggil `Save`.  

Dari sini Anda dapat bereksperimen—coba tipe shape lain, bermain dengan warna, atau menumpuk beberapa shape. Jika Anda perlu menggabungkan dokumen ini dengan konten yang sudah ada, cukup muat file yang ada lewat `new Document("existing.docx")` dan ikuti langkah yang sama.  

Ada pertanyaan lain? Tinggalkan komentar, dan selamat coding!

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}