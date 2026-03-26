---
category: general
date: 2026-03-25
description: Buat dokumen PDF dalam C# dan pelajari cara menambahkan bentuk persegi
  panjang, mengatur warna isi, menyesuaikan ukuran bentuk, serta mengatur transparansi
  bentuk dalam beberapa langkah saja.
draft: false
keywords:
- create pdf document
- set shape transparency
- add rectangle shape
- set fill color
- set shape size
language: id
og_description: Buat dokumen PDF dengan C# dan pelajari cara menambahkan persegi panjang,
  mengatur warna isi, ukuran, serta transparansi untuk menghasilkan PDF yang halus.
og_title: Buat Dokumen PDF dengan Bentuk Persegi Panjang – Tutorial C#
tags:
- C#
- PDF
- Aspose.Words
title: Buat Dokumen PDF dengan Bentuk Persegi Panjang – Panduan Lengkap C#
url: /id/java/images-shapes/create-pdf-document-with-a-rectangle-shape-full-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat Dokumen PDF dengan Bentuk Persegi Panjang – Panduan Lengkap C#

Pernah perlu **membuat dokumen PDF** yang berisi bentuk dengan gaya khusus, tetapi tidak yakin harus mulai dari mana? Anda tidak sendirian. Baik Anda sedang membangun generator laporan atau selebaran pemasaran, kemampuan untuk menggambar persegi panjang secara programatik, mengatur warna isi, menyesuaikan ukuran, dan bahkan mengatur transparansi dapat membuat PDF Anda tampak jauh lebih profesional.

Dalam tutorial ini kami akan menelusuri contoh C# lengkap yang siap‑jalan yang **membuat dokumen PDF**, **menambahkan bentuk persegi panjang**, **mengatur warna isi**, **mendefinisikan ukuran bentuk**, dan **mengatur transparansi bentuk** untuk bayangan luar yang halus. Pada akhir tutorial Anda akan memiliki satu file PDF (`shadow.pdf`) yang dapat Anda buka untuk melihat hasilnya.

> **Pro tip:** Pendekatan yang sama bekerja dengan tipe bentuk lain (elips, garis, dll.)—cukup ganti `ShapeType.RECTANGLE` dengan tipe yang Anda butuhkan.

---

## Apa yang Anda Butuhkan

| Prasyarat | Mengapa penting |
|--------------|----------------|
| **.NET 6+** (atau .NET Framework 4.6+) | Perpustakaan Aspose.Words menargetkan runtime modern. |
| **Paket NuGet Aspose.Words for .NET** | Menyediakan kelas `Document`, `Shape`, `ShadowEffect`, dan kelas terkait lainnya. |
| **IDE C#** (Visual Studio, Rider, VS Code) | Memudahkan debugging dan menjalankan contoh. |
| **Pengetahuan dasar C#** | Anda akan memahami sintaks tanpa harus menyelam terlalu dalam. |

Anda dapat menginstal perpustakaan melalui baris perintah:

```bash
dotnet add package Aspose.Words
```

Itu saja—tidak ada DLL tambahan, tidak ada dependensi native. Setelah paket terpasang, kode di bawah ini akan dapat dikompilasi dan dijalankan.

---

## Implementasi Langkah‑per‑Langkah

Berikut kami membagi proses menjadi lima langkah logis. Setiap langkah memiliki judul yang jelas (agar model AI dapat mengindeksnya) dan blok kode singkat yang dapat Anda salin‑tempel langsung.

### ## 1. Buat Dokumen PDF dan Siapkan Kanvas

Hal pertama yang kami lakukan adalah menginstansiasi `Document`. Anggaplah ini sebagai kanvas kosong yang pada akhirnya akan menjadi file PDF Anda.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document – this is the PDF document we will build.
        Document document = new Document();

        // The rest of the steps follow inside this method.
```

> **Mengapa?** `Document` menyimpan semua bagian, paragraf, dan bentuk. Memulai dengan objek bersih menjamin tidak ada artefak tersembunyi dari eksekusi sebelumnya.

### ## 2. Tambahkan Bentuk Persegi Panjang – Atur Warna Isi dan Ukuran Bentuk

Sekarang kami membuat persegi panjang, memberi isian kuning cerah, dan mendefinisikan dimensinya. Ini mencakup **menambahkan bentuk persegi panjang**, **mengatur warna isi**, serta **mengatur ukuran bentuk**.

```csharp
        // Step 2: Create a rectangle shape.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Set the width and height – this is where we set the shape size.
        rectangle.Width = 200;   // 200 points (≈2.78 inches)
        rectangle.Height = 100;  // 100 points (≈1.39 inches)

        // Apply a fill color – here we use a vivid yellow.
        rectangle.FillColor = Color.Yellow;
```

> **Catatan:** Lebar/tinggi diukur dalam poin (1 poin = 1/72 inci). Sesuaikan angka-angka ini agar cocok dengan tata letak Anda.

### ## 3. Terapkan Bayangan Luar dan Atur Transparansi Bentuk

Bayangan menambah kedalaman, dan mengontrol opasitasnya adalah inti dari **mengatur transparansi bentuk**. Di bawah ini kami mengonfigurasi bayangan luar abu‑abu dengan transparansi 30 %.

```csharp
        // Step 3: Configure the outer shadow effect.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;          // Shadow hue
        shadow.BlurRadius = 5.0;            // How fuzzy the shadow appears
        shadow.DistanceX = 4;               // Horizontal offset
        shadow.DistanceY = 4;               // Vertical offset
        shadow.Transparency = 0.3;          // 0 = opaque, 1 = fully transparent
        shadow.Style = ShadowStyle.Outer;   // Make it an outer shadow
```

> **Mengapa mengatur transparansi?** Bayangan dengan transparansi 30 % terlihat halus, mencegah persegi panjang tampak “datar” di halaman.

### ## 4. Sisipkan Bentuk ke dalam Badan Dokumen

Kami kini menempatkan persegi panjang ke paragraf pertama pada bagian pertama dokumen. Langkah ini mengikat semua elemen bersama.

```csharp
        // Step 4: Insert the rectangle into the first paragraph.
        // If the document has no paragraphs yet, Aspose creates one automatically.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);
```

> **Kasus khusus:** Jika Anda memerlukan bentuk pada halaman baru, tambahkan `document.Sections[0].PageSetup.SectionStart = SectionStart.NewPage;` sebelum menambahkan bentuk.

### ## 5. Simpan Dokumen sebagai File PDF

Akhirnya, kami menyimpan struktur dalam memori ke file PDF fisik. File akan ditulis ke folder yang Anda tentukan.

```csharp
        // Step 5: Save the document as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF saved successfully to {outputPath}");
    }
}
```

Saat Anda menjalankan program, sebuah file bernama `shadow.pdf` akan muncul. Membukanya akan menampilkan persegi panjang kuning dengan bayangan abu‑abu lembut yang bergeser 4 poin—tepat seperti yang dijelaskan kode kami.

> **Output yang diharapkan:** PDF satu halaman di mana persegi panjang berada di sudut kiri‑atas halaman, berisi warna kuning, berukuran 200 × 100 poin, dan memiliki bayangan luar semi‑transparan.

---

## Contoh Lengkap yang Siap Pakai (Copy‑Paste)

Berikut seluruh file sumber, siap untuk Anda masukkan ke proyek konsol baru.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new empty document – this will become the PDF.
        Document document = new Document();

        // 2️⃣ Add a rectangle shape, set its size and fill color.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.Width = 200;          // shape size – width
        rectangle.Height = 100;         // shape size – height
        rectangle.FillColor = Color.Yellow; // set fill color

        // 3️⃣ Apply an outer shadow and adjust transparency.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;
        shadow.BlurRadius = 5.0;
        shadow.DistanceX = 4;
        shadow.DistanceY = 4;
        shadow.Transparency = 0.3;      // set shape transparency
        shadow.Style = ShadowStyle.Outer;

        // 4️⃣ Insert the shape into the first paragraph of the document.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);

        // 5️⃣ Save everything as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF created at: {outputPath}");
    }
}
```

> **Tip:** Ganti `YOUR_DIRECTORY` dengan path absolut seperti `C:\Temp` atau path relatif seperti `.\output`. Program akan membuat folder tersebut jika belum ada.

---

## Pertanyaan yang Sering Diajukan (FAQ)

**T: Bisakah saya mengubah posisi persegi panjang pada halaman?**  
J: Tentu saja. Atur `rectangle.Left` dan `rectangle.Top` (keduanya diukur dalam poin) sebelum menambahkannya ke paragraf.

**T: Bagaimana jika saya memerlukan isian transparan alih‑alih bayangan transparan?**  
J: Gunakan `rectangle.FillColor = Color.FromArgb(128, Color.Yellow);` – argumen pertama adalah kanal alfa (0‑255), di mana 128 menghasilkan ~50 % transparansi.

**T: Apakah ini bekerja dengan .NET Core?**  
J: Ya. Aspose.Words mendukung .NET Standard 2.0+, sehingga Anda dapat menjalankan kode yang sama pada .NET 6, .NET 7, atau .NET Framework 4.6+.

**T: Bagaimana cara menambahkan beberapa bentuk?**  
J: Cukup ulangi langkah 2‑4 untuk setiap bentuk, mungkin menyisipkannya ke paragraf atau bagian yang berbeda.

---

## Kesimpulan

Kami baru saja **membuat dokumen PDF** dari awal, **menambahkan bentuk persegi panjang**, **mengatur warna isi**, **mendefinisikan ukurannya**, dan **menyesuaikan transparansi bentuk** untuk menghasilkan efek bayangan yang halus. Kode contoh bersifat mandiri, berjalan dalam hitungan menit, dan memperlihatkan konsep inti yang Anda perlukan untuk tata letak PDF yang lebih kompleks.

Siap untuk tantangan berikutnya? Coba ganti persegi panjang dengan bentuk sudut melengkung, sematkan gambar di dalam bentuk, atau hasilkan daftar isi secara otomatis. API yang sama memungkinkan Anda menumpuk teks, gambar, dan vektor—jadi langit adalah batasnya.

Jika Anda merasa panduan ini berguna, beri bintang di GitHub, bagikan kepada rekan, atau tinggalkan komentar dengan variasi Anda sendiri. Selamat coding! 

---

![membuat dokumen pdf dengan contoh bentuk persegi panjang](/images/rectangle-shadow.png "Tangkapan layar yang menunjukkan PDF yang dibuat dengan persegi panjang kuning dan bayangan luar abu‑abu")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}