---
category: general
date: 2026-01-03
description: Buat bentuk persegi panjang di Word dengan C# dan tambahkan bayangan
  pada bentuk. Pelajari cara menyisipkan bentuk di Word, menambahkan bayangan pada
  bentuk, dan menghasilkan dokumen Word secara programatis.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- insert shape in word
- how to add shape
- c# generate word document
language: id
og_description: Buat bentuk persegi panjang di Word dengan C# dan tambahkan bayangan
  pada bentuk. Ikuti panduan ini untuk menyisipkan bentuk di Word, mengatur bayangan,
  dan menghasilkan dokumen secara programatis.
og_title: Membuat bentuk persegi panjang di Word menggunakan C# – Tutorial Lengkap
tags:
- C#
- Word Automation
- Aspose.Words
title: Buat bentuk persegi panjang di Word menggunakan C# – Panduan Langkah demi Langkah
url: /id/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat bentuk persegi panjang di Word menggunakan C# – Tutorial Lengkap

Pernah membutuhkan untuk **create rectangle shape** dalam dokumen Word tetapi tidak yakin harus mulai dari mana? Anda tidak sendirian—banyak pengembang mengalami kendala yang sama ketika mereka ingin **add shadow to shape** untuk tampilan yang halus. Dalam tutorial ini kami akan membahas langkah‑langkah tepat untuk **insert shape in Word**, menerapkan bayangan halus, dan akhirnya **c# generate word document** yang dapat Anda kirim ke pengguna.

Kami akan membahas semuanya mulai dari menyiapkan proyek hingga menyesuaikan properti bayangan, dan kami akan mengakhiri dengan contoh kode yang siap dijalankan. Tanpa basa‑basi, hanya bagian praktis yang menyelesaikan tugas.

## Apa yang Akan Anda Pelajari

- Cara **create rectangle shape** dengan Aspose.Words (atau Open XML) di C#
- Properti tepat yang Anda perlukan untuk **add shadow to shape** agar memiliki kedalaman
- Di mana menempatkan bentuk menggunakan `DocumentBuilder`
- Cara menyimpan file sehingga terbuka dengan benar di Microsoft Word
- Tips, jebakan, dan variasi untuk skenario dunia nyata

### Prasyarat

- .NET 6.0 atau lebih baru (kode ini bekerja pada .NET Core dan .NET Framework)
- Paket NuGet yang dapat memanipulasi file Word – kami akan menggunakan **Aspose.Words for .NET** karena API‑nya ringkas. Jika Anda lebih suka Open XML SDK, konsepnya sama, hanya kelasnya yang berbeda.
- Visual Studio, VS Code, atau IDE C# apa pun yang Anda suka

> **Pro tip:** Jika Anda memiliki anggaran terbatas, Aspose menawarkan trial gratis yang sempurna untuk belajar. Cukup ganti baris lisensi dengan komentar saat Anda menguji.

## Langkah 1: Instal Perpustakaan Pengolahan Word

Pertama, tambahkan perpustakaan ke proyek Anda. Buka terminal di folder solusi Anda dan jalankan:

```bash
dotnet add package Aspose.Words
```

Jika Anda menggunakan Open XML SDK, perintahnya adalah `dotnet add package DocumentFormat.OpenXml`. Sisanya panduan ini mengasumsikan Aspose.Words, tetapi mengganti pemanggilan API sangat mudah.

## Langkah 2: Buat Dokumen Kosong Baru

Sekarang perpustakaan siap, kita dapat **create rectangle shape** dengan memulai dari objek `Document` yang bersih. Anggap ini sebagai kanvas baru.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 2: Initialize a blank Word document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` memberi kita cara tingkat tinggi untuk menyisipkan konten tanpa harus menyelam ke dalam pohon node tingkat rendah.

## Langkah 3: Sisipkan Bentuk Persegi Panjang

Dengan builder di tangan, kita dapat **insert shape in Word**. Metode `InsertShape` menerima tipe bentuk dan dimensinya (lebar, tinggi) dalam poin.

```csharp
// Step 3: Insert a rectangle shape – 150pt wide, 80pt high
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Pada titik ini persegi panjang muncul di dokumen, tetapi terlihat agak datar. Di sinilah langkah berikutnya berperan.

## Langkah 4: Tambahkan Bayangan ke Bentuk

Bayangan memberi bentuk rasa kedalaman. Objek `Shadow` memungkinkan kita menyesuaikan blur, distance, angle, color, dan transparency secara detail. Di bawah ini konfigurasi lengkap yang bekerja baik untuk kebanyakan laporan.

```csharp
// Step 4: Configure a subtle shadow
rectangle.Shadow = new Shadow
{
    BlurRadius = 5.0,          // Soft edges
    Distance = 4.0,            // How far the shadow is offset
    Angle = 45,                // Direction in degrees (45° = down‑right)
    Color = Color.Black,       // Shadow color
    Transparency = 0.3         // 30 % transparent for a gentle look
};
```

**Mengapa nilai‑nilai ini?**  
- **BlurRadius** `5.0` menjaga tepi tetap halus tanpa terlihat kabur.  
- **Distance** `4.0` menggeser bayangan cukup untuk terlihat.  
- **Angle** `45` meniru pencahayaan alami dari atas‑kiri, konvensi UI yang umum.  
- **Transparency** `0.3` mencegah bayangan menguasai isi bentuk.

Jika Anda menginginkan efek yang lebih dramatis, tingkatkan `BlurRadius` dan turunkan `Transparency`. Untuk efek halus, hampir tak terlihat, balikkan angka‑angka tersebut.

## Langkah 5: Simpan Dokumen

Akhirnya, tulis file ke disk. Metode `Save` mendeteksi format dari ekstensi file, sehingga `.docx` memberi Anda format Word modern.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\ShadowRectangle.docx";
document.Save(outputPath);
```

Buka `ShadowRectangle.docx` di Microsoft Word, dan Anda akan melihat persegi panjang tajam dengan bayangan lembut—tepat seperti yang Anda inginkan ketika menanyakan “**how to add shape**” dengan sentuhan profesional.

![Buat bentuk persegi panjang dengan bayangan di Word](placeholder-image.png "Buat bentuk persegi panjang dengan bayangan di Word")

*Teks alt gambar: buat bentuk persegi panjang dengan bayangan di Word*

## Contoh Kerja Lengkap

Menggabungkan semuanya, berikut program lengkap yang siap dijalankan. Salin‑tempel ke aplikasi konsol dan tekan **F5**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a rectangle shape (150pt × 80pt)
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Add a subtle shadow
            rect.Shadow = new Shadow
            {
                BlurRadius = 5.0,
                Distance = 4.0,
                Angle = 45,
                Color = Color.Black,
                Transparency = 0.3
            };

            // 4️⃣ Save the file
            string filePath = @"C:\Temp\ShadowRectangle.docx";
            doc.Save(filePath);

            System.Console.WriteLine($"Document saved to {filePath}");
        }
    }
}
```

### Hasil yang Diharapkan

- File `ShadowRectangle.docx` yang dihasilkan berisi **satu bentuk persegi panjang** yang terpusat di posisi kursor.
- Persegi panjang menampilkan **bayangan hitam lembut, 30 % transparan** dengan offset pada sudut 45°.
- Tidak ada konten lain yang ditambahkan, sehingga file tetap ringan dan mudah disisipkan dalam laporan yang lebih besar.

## Pertanyaan Umum & Kasus Tepi

### Bagaimana jika saya membutuhkan bentuk lain?

Ganti `ShapeType.Rectangle` dengan nilai enum `ShapeType` lainnya (mis., `Ellipse`, `Triangle`). API bayangan berfungsi sama, sehingga Anda dapat menggunakan kembali konfigurasi tersebut.

### Bagaimana cara mengubah warna isi?

```csharp
rect.FillColor = Color.LightBlue;   // or any System.Drawing.Color
```

### Bisakah saya menambahkan bentuk ke paragraf tertentu?

Ya. Pindahkan `DocumentBuilder` ke paragraf target dengan `builder.MoveToParagraph(index)` sebelum memanggil `InsertShape`. Ini memastikan bentuk muncul tepat di tempat yang Anda inginkan.

### Bagaimana dengan format Word lama (.doc)?

Cukup ubah ekstensi:

```csharp
doc.Save(@"C:\Temp\ShadowRectangle.doc", SaveFormat.Doc);
```

Fitur bayangan didukung di Word 2003 dan versi selanjutnya, jadi Anda tetap akan melihat efeknya.

### Menggunakan Open XML SDK alih-alih Aspose?

Langkah‑langkahnya tetap sama: buat `WordprocessingDocument`, tambahkan elemen `Drawing`, atur properti `<a:shadow>`. XML‑nya lebih panjang, tetapi konsep yang sama (ukuran, blur, distance, angle) tetap berlaku.

## Tips untuk Menghindari Kesalahan

- **Jangan lupa lisensi** jika Anda menggunakan versi Aspose berbayar; jika tidak, Anda akan mendapatkan watermark.
- **Satuan adalah poin**, bukan piksel. Satu piksel layar biasanya ≈ 0.75 pt, jadi sesuaikan dimensi sesuai kebutuhan.
- **Properti bayangan diabaikan** jika `WrapType` bentuk diatur ke `Inline`. Gunakan `WrapType = WrapType.Square` untuk bentuk mengambang yang menghormati render bayangan.
- **Menyimpan ke jaringan bersama** mungkin memerlukan izin yang tepat; selalu uji jalur terlebih dahulu.

## Kesimpulan

Sekarang Anda tahu cara **create rectangle shape** dalam dokumen Word menggunakan C#, **add shadow to shape**, dan **c# generate word document** yang tampak rapi langsung dari awal. Langkah‑langkah inti—menginstal perpustakaan, menginstansiasi `Document`, menyisipkan bentuk, mengonfigurasi bayangan, dan menyimpan—mudah diingat dan dapat disesuaikan untuk bentuk lain, warna, atau bahkan data dinamis.

Apa selanjutnya? Cobalah menumpuk beberapa bentuk, menyisipkan gambar, atau menghasilkan laporan lengkap dengan tabel dan diagram. Anda juga dapat mengeksplorasi pemformatan bersyarat—mengubah intensitas bayangan berdasarkan nilai data—untuk membuat dokumen Anda tidak hanya fungsional tetapi juga menarik secara visual.

Silakan bereksperimen, dan jika Anda menemukan kejanggalan, tinggalkan komentar di bawah. Selamat coding, semoga dokumen Word Anda selalu memiliki bayangan jatuh yang sempurna!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}