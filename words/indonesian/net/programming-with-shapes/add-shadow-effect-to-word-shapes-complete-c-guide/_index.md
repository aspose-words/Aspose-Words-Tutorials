---
category: general
date: 2026-02-10
description: Tambahkan efek bayangan ke bentuk di Word menggunakan C#. Pelajari cara
  mengubah warna bayangan, mengatur transparansi, dan menerapkan bayangan bentuk dalam
  beberapa langkah saja.
draft: false
keywords:
- add shadow effect
- change shadow color
- how to set transparency
- add shape shadow
- apply shadow color
language: id
og_description: Tambahkan efek bayangan pada bentuk di Word menggunakan C#. Pelajari
  cara mengubah warna bayangan, mengatur transparansi, dan menerapkan bayangan bentuk
  dalam beberapa langkah saja.
og_title: Tambahkan Efek Bayangan pada Bentuk Word – Panduan Lengkap C#
tags:
- Aspose.Words
- C#
- Document Automation
title: Tambahkan Efek Bayangan pada Bentuk Word – Panduan Lengkap C#
url: /id/net/programming-with-shapes/add-shadow-effect-to-word-shapes-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menambahkan Efek Bayangan pada Bentuk Word – Panduan Lengkap C#

Pernahkah Anda perlu **menambahkan efek bayangan** pada sebuah bentuk Word tetapi tidak yakin harus mulai dari mana? Anda tidak sendirian—para pengembang sering bertanya, “Bagaimana cara membuat sebuah bentuk terlihat sedikit lebih tiga‑dimensi?” Kabar baiknya, dengan beberapa baris C# Anda dapat mengubah warna bayangan, mengatur transparansi, dan menyesuaikan tampilan setiap bentuk. Dalam tutorial ini kami akan membahas contoh lengkap yang dapat dijalankan yang melakukan hal tersebut, plus beberapa tip yang Anda harapkan sudah tahu sebelumnya.

Kami akan membahas:

* Memuat file DOCX yang sudah berisi sebuah bentuk.  
* Menemukan bentuk tersebut (bahkan jika berada di dalam grup).  
* Menerapkan bayangan—jarak, blur, warna, dan transparansi.  
* Memverifikasi hasil dengan menyimpan dokumen.  

Tidak ada dokumentasi eksternal yang diperlukan; semua yang Anda butuhkan ada di sini. Prasyarat satu‑satunya adalah referensi ke **Aspose.Words for .NET** (atau perpustakaan kompatibel lain yang menyediakan `Shape.ShadowFormat`). Jika Anda menggunakan NuGet, cukup jalankan `Install-Package Aspose.Words`. Siap? Mari kita mulai.

---

## Prerequisites

| Persyaratan | Mengapa penting |
|-------------|-----------------|
| .NET 6.0 atau lebih baru | API modern, kinerja lebih baik |
| Aspose.Words for .NET (atau setara) | Menyediakan kelas `Document`, `Shape`, dan `ShadowFormat` |
| File DOCX (`input.docx`) yang berisi setidaknya satu bentuk | Tutorial ini memanipulasi bentuk yang sudah ada; Anda dapat membuatnya secara manual di Word jika diperlukan |

> **Pro tip:** Jika Anda belum memiliki bentuk, buka Word, sisipkan sebuah persegi panjang sederhana, simpan file sebagai `input.docx`, dan letakkan di folder `Resources` proyek Anda.

## Step 1 – Load the Word Document and Locate the Shape {#add-shadow-effect-step1}

Pertama‑tama: kita membutuhkan objek `Document` yang menunjuk ke file sumber kita. Kemudian kita akan mengambil bentuk pertama menggunakan pencarian rekursif sehingga tetap berfungsi meskipun bentuk berada di dalam grup.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Step 1: Load the Word document that contains a shape
        Document doc = new Document("Resources/input.docx");

        // Step 2: Retrieve the first shape in the document (searches recursively)
        Shape targetShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (targetShape == null)
        {
            Console.WriteLine("No shape found in the document.");
            return;
        }

        // Continue with shadow settings...
```

**Why we do this:**  
* `Document` adalah titik masuk ke setiap file Word.  
* `GetChild(NodeType.Shape, 0, true)` menelusuri seluruh pohon node, memastikan kita tidak melewatkan bentuk yang bersarang.  
* Pemeriksaan null mencegah `NullReferenceException` jika file tidak memiliki bentuk—kasus tepi yang sering diabaikan pemula.

## Step 2 – Set the Shadow Distance and Blur {#add-shadow-effect-step2}

Bayangan bukan hanya sekadar warna; offset dan kelembutannya sama pentingnya. Mari geser bayangan beberapa poin dan beri sedikit blur.

```csharp
        // Step 3: Set how far the shadow is offset from the shape
        targetShape.ShadowFormat.Distance = 4.0;   // 4 points offset

        // Step 4: Define the softness of the shadow edges
        targetShape.ShadowFormat.BlurRadius = 2.0; // 2 points blur
```

**Explanation:**  
* **Distance** mengontrol offset X/Y. Nilai `4.0` memindahkan bayangan ke bawah dan ke kanan, meniru sumber cahaya dari kiri‑atas.  
* **BlurRadius** menentukan seberapa halus tepinya. Angka rendah membuat bayangan tajam; angka tinggi memberi kesan cahaya lembut.

Jika Anda memerlukan arah cahaya yang berbeda, Anda juga dapat menyesuaikan `ShadowFormat.Angle` (default 45°).

## Step 3 – Change Shadow Color and Set Transparency {#add-shadow-effect-step3}

Sekarang bagian yang menyenangkan—mengubah warna dan membuat bayangan sebagian tembus. Di sinilah kata kunci sekunder **change shadow color** dan **how to set transparency** berperan.

```csharp
        // Step 5: Choose a colour for the shadow
        targetShape.ShadowFormat.Color = Color.DarkGray; // Change shadow color here

        // Step 6: Make the shadow partially transparent (30 % transparent)
        targetShape.ShadowFormat.Transparency = 0.3; // Value between 0 (opaque) and 1 (fully transparent)
```

**Why it matters:**  
* `Color.DarkGray` adalah nilai default yang aman dan bekerja baik pada latar belakang terang maupun gelap. Ganti dengan `Color.FromArgb(255, 0, 0, 0)` untuk hitam murni atau nilai ARGB kustom lainnya.  
* Menetapkan `Transparency` ke `0.3` memberikan efek tembus 30 %—cukup untuk menambah kedalaman tanpa menutupi bentuk di bawahnya.  

**Edge case:** Beberapa versi Word yang lebih lama mengabaikan transparansi pada tipe bentuk tertentu (misalnya WordArt). Jika bayangan tetap sepenuhnya tidak tembus, coba konversi bentuk menjadi gambar terlebih dahulu.

## Step 4 – Save and Verify the Result {#add-shadow-effect-step4}

Setelah menyesuaikan bayangan, kami menulis dokumen kembali ke disk. Membuka file di Word seharusnya menampilkan bayangan berwarna, semi‑transparent yang halus di sekitar bentuk.

```csharp
        // Step 7: Save the modified document
        doc.Save("Resources/output_with_shadow.docx");
        Console.WriteLine("Shadow effect applied successfully. Check output_with_shadow.docx.");
    }
}
```

**Verification checklist:**

1. Buka `output_with_shadow.docx` di Microsoft Word.  
2. Klik bentuk → Format → Shape Effects → Shadow.  
3. Anda harus melihat bayangan abu‑abu gelap, bergeser sekitar ~4 pt, blur, dan 30 % transparan.

Jika ada yang tampak tidak tepat, periksa kembali properti `ShadowFormat`—khususnya `Distance` dan `Transparency`.

## Common Variations and What‑If Scenarios {#add-shadow-effect-variations}

### Adding a Shadow to Multiple Shapes

Jika Anda perlu **add shape shadow** ke setiap bentuk dalam dokumen, ganti pengambilan satu bentuk dengan loop:

```csharp
        NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
        foreach (Shape shp in shapes)
        {
            shp.ShadowFormat.Distance = 5.0;
            shp.ShadowFormat.BlurRadius = 3.0;
            shp.ShadowFormat.Color = Color.Black;
            shp.ShadowFormat.Transparency = 0.4;
        }
```

### Using a Custom Colour with Alpha

Kadang‑kadang Anda menginginkan warna bayangan itu sendiri semi‑transparent. Gabungkan `Color.FromArgb` dengan `Transparency` untuk efek berlapis:

```csharp
        // Semi‑transparent blue shadow
        targetShape.ShadowFormat.Color = Color.FromArgb(180, 0, 0, 255); // 180/255 ≈ 70% opacity
        targetShape.ShadowFormat.Transparency = 0.2; // Additional 20% transparency
```

### Handling Shapes Inside a Group

Bentuk yang dikelompokkan disimpan sebagai node `GroupShape`. Pencarian rekursif yang kami gunakan (`true` flag) sudah menelusuri grup, tetapi jika Anda ingin memperlakukan grup sebagai satu entitas, cast ke `GroupShape` dan iterasi `ChildNodes`‑nya.

```csharp
        GroupShape group = targetShape.ParentNode as GroupShape;
        if (group != null)
        {
            foreach (Shape inner in group.GetChildNodes(NodeType.Shape, true))
            {
                // Apply same shadow settings to each inner shape
                inner.ShadowFormat = targetShape.ShadowFormat.Clone();
            }
        }
```

## Pro Tips & Pitfalls {#add-shadow-effect-tips}

* **Pro tip:** Saat bereksperimen, set `ShadowFormat.Visible = true` secara eksplisit. Beberapa API menyembunyikan bayangan sampai properti berubah.  
* **Watch out for:** Pengaturan “No Outline” di Word dapat membuat bayangan tampak terlepas. Pastikan gaya garis bentuk terlihat jika Anda ingin bayangan melengkapinya.  
* **Performance note:** Memperbarui ribuan bentuk dalam dokumen besar dapat lambat. Kelompokkan perubahan dan panggil `doc.UpdatePageLayout()` sekali di akhir.  
* **Compatibility:** Aspose.Words 23.10+ sepenuhnya mendukung properti bayangan untuk DOCX, tetapi versi lebih lama mungkin mengabaikan `BlurRadius`. Selalu uji dengan versi perpustakaan yang Anda distribusikan.

## Full Working Example {#add-shadow-effect-complete}

Berikut adalah program lengkap yang siap disalin‑tempel. Program ini mencakup semua direktif `using`, penanganan error, dan komentar.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the document that already contains a shape.
        Document doc = new Document("Resources/input.docx");

        // Retrieve the first shape (recursively searches groups).
        Shape targetShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (targetShape == null)
        {
            Console.WriteLine("No shape found in the document.");
            return;
        }

        // Apply shadow distance and blur.
        targetShape.ShadowFormat.Distance = 4.0;      // Offset from shape
        targetShape.ShadowFormat.BlurRadius = 2.0;   // Soft edges

        // Change shadow color and set transparency.
        targetShape.ShadowFormat.Color = Color.DarkGray; // Change shadow color
        targetShape.ShadowFormat.Transparency = 0.3;     // How to set transparency (30%)

        // Save the modified document.
        doc.Save("Resources/output_with_shadow.docx");
        Console.WriteLine("Shadow effect applied successfully. Check output_with_shadow.docx.");
    }
}
```

Menjalankan program ini akan menghasilkan `output_with_shadow.docx` dengan **add shadow effect** yang Anda minta. Buka file tersebut, dan Anda akan melihat bayangan abu‑abu gelap yang halus, 30 % transparan—tepat seperti yang diharapkan dari presentasi profesional.

## Conclusion

Kami baru saja mendemonstrasikan cara **add shadow effect** pada bentuk Word menggunakan C#. Dengan memuat dokumen, menemukan bentuk, menyesuaikan properti `ShadowFormat`, dan menyimpan file, Anda memperoleh kontrol penuh atas **change shadow color**, **how to set transparency**, dan **add shape shadow** dalam hitungan menit.

Selanjutnya, Anda mungkin ingin **apply shadow color** secara kondisional—misalnya bayangan lebih gelap untuk bentuk yang lebih besar atau warna berbeda berdasarkan input pengguna. Atau jelajahi peningkatan visual lain seperti glow, reflection, atau bevel 3‑D. Pola `ShadowFormat` yang sama berlaku untuk fitur‑fitur tersebut, sehingga Anda siap memperluas tutorial ini lebih jauh.

Ada pertanyaan atau menemukan kasus tepi yang aneh? Tinggalkan komentar di bawah, dan mari kita selesaikan bersama. Selamat coding, semoga dokumen Anda selalu memiliki kedalaman ekstra!  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}