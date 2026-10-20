---
category: general
date: 2026-03-28
description: Cara menambahkan bayangan pada shape di C# dengan Aspose.Words – menambahkan
  bayangan ke shape, menerapkan bayangan, dan menyesuaikan tampilannya.
draft: false
keywords:
- how to set shadow
- add shadow to shape
- apply shadow to shape
- how to add shadow
language: id
og_description: Cara cepat menambahkan bayangan pada bentuk di C#. Pelajari cara menambahkan
  bayangan ke bentuk, menerapkan bayangan, serta mengatur blur, jarak, dan sudut.
og_title: Cara Menambahkan Bayangan pada Bentuk di C# – Panduan Lengkap
tags:
- Aspose.Words
- C#
- Document Automation
- Graphics
title: Cara Menambahkan Bayangan pada Bentuk di C# – Panduan Langkah demi Langkah
url: /id/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menetapkan Bayangan pada Bentuk di C# – Panduan Pemrograman Lengkap

Pernah bertanya-tanya **bagaimana cara menambahkan bayangan** pada sebuah bentuk saat Anda membuat dokumen Word secara programatik? Anda bukan satu-satunya. Dalam banyak laporan, presentasi, atau selebaran, bayangan drop‑shadow yang halus dapat membuat grafik menonjol tanpa terlihat norak. Kabar baiknya? Dengan Aspose.Words untuk .NET Anda dapat menambahkan bayangan ke bentuk hanya dengan beberapa baris kode.

Dalam tutorial ini kami akan membahas seluruh proses: memuat DOCX, mengambil bentuk pertama, dan kemudian **menerapkan bayangan pada bentuk** — termasuk warna, blur, jarak, dan sudut. Pada akhir tutorial Anda akan memiliki potongan kode siap‑jalankan yang dapat Anda sisipkan ke proyek C# mana pun. Tanpa pustaka tambahan, tanpa sihir tersembunyi.

## Apa yang Anda Butuhkan

- **Aspose.Words for .NET** (versi 23.9 atau lebih baru) – pustaka yang membuat manipulasi Word menjadi mudah.  
- Lingkungan pengembangan .NET (Visual Studio 2022, Rider, atau CLI).  
- Contoh DOCX yang sudah berisi setidaknya satu bentuk (sebuah persegi panjang, gambar, atau SmartArt sudah cukup).  

Jika Anda kekurangan salah satu dari itu, dapatkan paket NuGet dengan `Install-Package Aspose.Words` dan buat file Word sederhana dengan bentuk yang dimasukkan secara manual—hanya untuk demo.

## Langkah 1: Muat Dokumen (Siapkan untuk Menambahkan Bayangan)

Hal pertama yang harus dilakukan adalah membuka file sumber. Di sinilah operasi **menambahkan bayangan ke bentuk** akan dimulai.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the DOCX that holds the shape you want to enhance
        Document doc = new Document("input.docx");
```

> **Mengapa ini penting:** Memuat dokumen memberi Anda objek `Document` yang memiliki semua node, termasuk bentuk. Tanpa itu, tidak ada yang dapat dimodifikasi.

## Langkah 2: Ambil Bentuk Target (Pilih yang Tepat)

Selanjutnya kami menemukan bentuk yang ingin kami gaya. Dalam contoh ini kami mengambil bentuk pertama di paragraf pertama, tetapi Anda dapat menyesuaikan kueri ke koleksi node mana pun.

```csharp
        // Grab the first shape inside the first paragraph of the first section
        Shape targetShape = doc.FirstSection.Body.FirstParagraph
            .GetChildNodes(NodeType.Shape, true)[0] as Shape;

        if (targetShape == null)
        {
            Console.WriteLine("No shape found – check your input file.");
            return;
        }
```

> **Tips profesional:** `GetChildNodes(NodeType.Shape, true)` menelusuri subtree secara rekursif, memastikan Anda tidak melewatkan bentuk bersarang seperti WordArt.

## Langkah 3: Akses Objek Pengaturan Bayangan (Tempat Keajaiban Berada)

Setiap `Shape` memiliki properti `ShadowFormat`. Objek ini mengontrol visibilitas, warna, blur, jarak, dan sudut—semua pengaturan yang Anda perlukan untuk **menerapkan bayangan pada bentuk**.

```csharp
        // The ShadowFormat object holds all shadow‑related settings
        ShadowFormat shadow = targetShape.ShadowFormat;
```

> **Mengapa kami menggunakan `ShadowFormat`:** Ini mengabstraksi representasi XML yang mendasarinya, sehingga Anda dapat mengatur bayangan tanpa harus berurusan dengan OpenXML mentah.

## Langkah 4: Buat Bayangan Terlihat dan Pilih Warna (Tambahkan Bayangan ke Bentuk)

Bayangan tidak akan muncul sampai Anda mengatur `Visible` ke `true`. Setelah itu, Anda dapat memilih warna `System.Drawing.Color` apa saja. Di sini kami menggunakan abu-abu sedang, tetapi silakan bereksperimen.

```csharp
        // Turn the shadow on and give it a subtle gray tone
        shadow.Visible = true;
        shadow.Color = Color.FromArgb(80, 80, 80);   // dark gray
```

> **Kesalahan umum:** Lupa mengaktifkan `Visible` menghasilkan kegagalan diam—bentuk Anda tampak tidak berubah meskipun Anda telah mengatur properti lain.

## Langkah 5: Konfigurasi Penampilan – Blur, Jarak, dan Sudut (Sesuaikan Tampilan)

Sekarang kami membentuk dampak visual. `BlurRadius` melunakkan tepi, `Distance` menggeser bayangan menjauh dari bentuk, dan `Angle` menentukan arah sumber cahaya.

```csharp
        // Adjust how the shadow looks
        shadow.BlurRadius = 5.0;   // in points – higher = softer
        shadow.Distance   = 3.0;   // how far the shadow is offset
        shadow.Angle      = 45.0;  // degrees clockwise from the horizontal
```

> **Kasus khusus:** Jika Anda mengatur jarak negatif, bayangan akan muncul *di dalam* bentuk, yang dapat berguna untuk efek timbul.

## Langkah 6: Simpan Dokumen yang Diperbarui (Lihat Hasilnya)

Akhirnya, tulis perubahan kembali ke disk. Anda dapat menimpa file asli atau membuat file baru.

```csharp
        // Persist the changes – you’ll see the shadow in Word or any viewer
        doc.Save("output-with-shadow.docx");
        Console.WriteLine("Shadow applied successfully! Check output-with-shadow.docx");
    }
}
```

Menjalankan program menghasilkan `output-with-shadow.docx`. Buka di Microsoft Word, dan Anda akan melihat bentuk yang dipilih kini memiliki bayangan abu-abu lembut dengan sudut 45°, blur sebesar 5 pt dan offset sebesar 3 pt.

![Diagram yang menunjukkan bayangan diterapkan pada sebuah bentuk](https://example.com/images/shadow-diagram.png "Diagram yang menunjukkan bayangan diterapkan pada sebuah bentuk")

*Teks alternatif: Diagram yang menunjukkan bayangan diterapkan pada sebuah bentuk* – gambar ini mengilustrasikan efek sebelum/setelah.

## Cara Menambahkan Bayangan – Variasi Umum dan Kasus Khusus

Meskipun langkah inti sederhana, skenario dunia nyata sering memerlukan penyesuaian. Berikut beberapa situasi “bagaimana jika” yang mungkin Anda temui.

### 1. Beberapa Bentuk, Bayangan Berbeda

Jika dokumen Anda berisi beberapa grafik, lakukan loop melalui koleksi bentuk dan tetapkan pengaturan bayangan unik untuk setiap bentuk.

```csharp
        NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
        foreach (Shape shp in shapes)
        {
            ShadowFormat sf = shp.ShadowFormat;
            sf.Visible = true;
            sf.Color = Color.FromArgb(100, 100, 150); // bluish tint
            sf.BlurRadius = 3.0;
            sf.Distance = 2.0;
            sf.Angle = 30.0;
        }
```

### 2. Bayangan Transparan

Aspose.Words memungkinkan Anda mengatur saluran alfa melalui `Color.FromArgb(alpha, r, g, b)`. Gunakan alfa rendah (mis., 50) untuk efek halus, semi‑transparan.

```csharp
        shadow.Color = Color.FromArgb(50, 0, 0, 0); // 20% opacity black
```

### 3. Menghapus Bayangan

Terkadang Anda perlu mematikan bayangan setelah diterapkan. Cukup atur `Visible` ke `false`.

```csharp
        shadow.Visible = false;
```

### 4. Kekhawatiran Kompatibilitas

Fitur bayangan yang digunakan di sini didukung di Word 2007 + (format DOCX). Jika Anda menargetkan format biner `.doc` yang lebih lama, bayangan mungkin diabaikan karena format tersebut tidak memiliki elemen XML yang diperlukan. Dalam kasus seperti itu, pertimbangkan menyimpan sebagai DOCX atau menggunakan petunjuk visual alternatif.

## Ringkasan: Apa yang Telah Kita Capai

- **Memuat** sebuah DOCX dengan Aspose.Words.  
- **Mengambil** bentuk pertama dari dokumen.  
- **Mengakses** objek `ShadowFormat`‑nya.  
- **Mengaktifkan** bayangan, mengatur warna, radius blur, jarak, dan sudut.  
- **Menyimpan** file baru yang secara jelas menunjukkan efek tersebut.  

Semua langkah tersebut bersama‑sama menjawab **bagaimana cara menambahkan bayangan** pada sebuah bentuk, sekaligus menunjukkan cara **menambahkan bayangan ke bentuk**, **menerapkan bayangan pada bentuk**, dan bahkan **bagaimana cara menambahkan bayangan** dalam skenario yang lebih kompleks.

## Langkah Selanjutnya dan Topik Terkait

Setelah Anda menguasai gaya bayangan, Anda mungkin ingin menjelajahi:

- **Isian gradien** untuk bentuk (`Shape.FillFormat.GradientFill`).  
- **Efek teks** seperti cahaya atau refleksi (`TextEffect`).  
- **Penyisipan bentuk baru secara programatik** (`doc.FirstSection.Body.AppendChild(new Shape(...))`).  
- **Ekspor ke PDF** sambil mempertahankan bayangan (`doc.Save("output.pdf")`).  

Setiap topik tersebut dibangun di atas prinsip model‑objek yang sama yang kami gunakan di sini, sehingga Anda akan merasa nyaman.

---

*Selamat coding! Jika Anda mengalami kendala, tinggalkan komentar di bawah atau periksa dokumentasi API Aspose.Words untuk wawasan lebih mendalam.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}