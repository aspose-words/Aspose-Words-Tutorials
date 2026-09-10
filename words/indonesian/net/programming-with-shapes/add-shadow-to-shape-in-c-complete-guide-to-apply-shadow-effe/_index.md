---
category: general
date: 2026-02-13
description: Tambahkan bayangan pada bentuk di C# dengan cepat. Pelajari cara menerapkan
  efek bayangan, mengubah warna bayangan, dan membuat bayangan 45 derajat dengan contoh
  kode yang mudah.
draft: false
keywords:
- add shadow to shape
- apply shadow effect
- change shadow color
- 45 degree shadow
- how to add shadow
language: id
og_description: Tambahkan bayangan ke bentuk di C# secara instan. Tutorial ini menunjukkan
  cara menerapkan efek bayangan, mengubah warna bayangan, dan mengatur bayangan dengan
  sudut 45 derajat.
og_title: Tambahkan bayangan pada bentuk di C# – Panduan Efek Bayangan Langkah demi
  Langkah
tags:
- Aspose.Words
- C#
- Document Automation
title: Menambahkan bayangan pada bentuk di C# – Panduan Lengkap untuk Menerapkan Efek
  Bayangan
url: /id/net/programming-with-shapes/add-shadow-to-shape-in-c-complete-guide-to-apply-shadow-effe/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menambahkan bayangan pada bentuk di C# – Panduan Lengkap

Pernah bertanya-tanya bagaimana cara **menambahkan bayangan pada bentuk** di dokumen Word menggunakan C#? Anda bukan satu‑satunya. Banyak pengembang menemui kebuntuan ketika mereka membutuhkan bayangan halus untuk membuat diagram menonjol, namun tidak menemukan contoh yang ringkas dan siap‑jalankan.  

Kabar baik: tutorial ini memberikan kode tepat yang Anda butuhkan untuk **menambahkan bayangan pada bentuk**, menjelaskan mengapa setiap baris penting, dan menunjukkan cara menyesuaikan efek—apakah Anda menginginkan kabut abu‑abu samar atau bayangan tebal 45 ° . Selama proses kami juga akan **menerapkan efek bayangan**, **mengubah warna bayangan**, dan bahkan membahas skenario klasik **bayangan 45 derajat**.

## Apa yang Akan Anda Pelajari

- Cara memuat DOCX, menemukan sebuah bentuk, dan mengaktifkan bayangannya.  
- Makna di balik setiap properti bayangan (visibility, color, transparency, size, distance, angle).  
- Cara **menerapkan efek bayangan** secara dinamis, seperti melakukan loop pada semua bentuk atau menangani objek yang dikelompokkan.  
- Tips untuk **mengubah warna bayangan** dengan aman dan menangani dokumen yang tidak memiliki bentuk.  
- Bagaimana mencapai **bayangan 45 derajat** yang tepat tanpa menebak‑tebak sudut.

Tidak ada dokumentasi eksternal yang diperlukan—cukup salin, tempel, dan jalankan. Pada akhir tutorial Anda akan memiliki program yang berfungsi menambahkan bayangan profesional pada bentuk apa pun.

## Prasyarat

- .NET 6.0 atau lebih baru (kode ini juga bekerja pada .NET Framework 4.7+).  
- Aspose.Words untuk .NET (versi percobaan gratis atau berlisensi). Instal melalui NuGet: `dotnet add package Aspose.Words`.  
- File Word dasar (`input.docx`) yang sudah berisi setidaknya satu bentuk (misalnya, persegi panjang atau gambar).

> **Pro tip:** Jika Anda belum memiliki bentuk, sisipkan satu secara manual di Word terlebih dahulu; tutorial ini mengasumsikan bentuk pertama adalah target.

---

## Langkah 1: Siapkan Proyek dan Muat Dokumen

Pertama, buat aplikasi console (atau proyek C# apa pun) dan tambahkan referensi Aspose.Words. Kemudian muat DOCX yang berisi bentuk yang ingin Anda tingkatkan.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;
using Aspose.Words.Drawing;          // For Shape and ShadowFormat

class Program
{
    static void Main()
    {
        // Load the Word document that contains the shape.
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

**Mengapa ini penting:** `Document` adalah titik masuk untuk semua tugas pemrosesan Word. Dengan memuat file di awal, Anda menjamin bahwa setiap operasi selanjutnya bekerja pada representasi memori yang tepat.

---

## Langkah 2: Ambil Bentuk Target

Selanjutnya, temukan bentuk yang ingin Anda ubah. Contoh ini mengambil bentuk pertama, tetapi Anda dapat menyesuaikan indeks atau menyaring berdasarkan tipe bentuk.

```csharp
        // Retrieve the first shape in the document (adjust the index if needed).
        Shape targetShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (targetShape == null)
        {
            Console.WriteLine("No shape found. Add a shape to input.docx and try again.");
            return;
        }
```

**Penjelasan:**  
- `GetChild(NodeType.Shape, 0, true)` menelusuri pohon dokumen secara depth‑first dan mengembalikan bentuk pertama yang ditemukannya.  
- Pemeriksaan null mencegah `NullReferenceException` ketika dokumen tidak memiliki bentuk—kasus tepi umum yang membuat pemula terjebak.

---

## Langkah 3: Aktifkan Bayangan

Bayangan sebuah bentuk dinonaktifkan secara default. Mengaktifkannya semudah mengubah flag Boolean.

```csharp
        // Turn on the shadow effect for the shape.
        targetShape.ShadowFormat.Visible = true;
```

**Apa yang terjadi:** Menetapkan `Visible` ke `true` memberi tahu Word untuk merender bayangan. Tanpa baris ini, pengaturan bayangan lain yang Anda ubah akan diabaikan.

---

## Langkah 4: Konfigurasikan Penampilan Bayangan

Sekarang kita mendefinisikan tampilan bayangan. Kode di bawah ini cocok dengan gaya “hitam, 30 % transparan, blur 5 pt, offset 3 pt, sudut 45°” yang umum.

```csharp
        // Configure the shadow's appearance.
        // • Black color
        // • 30 % transparent
        // • 5 pt blur radius (size)
        // • 3 pt offset distance
        // • 45° direction (angle)
        targetShape.ShadowFormat.Color = Color.Black;          // change shadow color
        targetShape.ShadowFormat.Transparency = 0.3;           // 30 % transparent
        targetShape.ShadowFormat.Size = 5;                     // blur radius
        targetShape.ShadowFormat.Distance = 3;                 // offset distance
        targetShape.ShadowFormat.Angle = 45;                   // 45 degree shadow
```

**Mengapa setiap properti penting:**

| Property | Effect | Typical use |
|----------|--------|-------------|
| `Visible` | Mengaktifkan atau menonaktifkan bayangan | Inti untuk **menerapkan efek bayangan** |
| `Color` | Menentukan warna bayangan | Ubah ke abu‑abu untuk kehalusan, merah untuk penekanan |
| `Transparency` | 0 = tidak tembus, 1 = sepenuhnya transparan | 0.3 memberikan tampilan lembut dan realistis |
| `Size` | Mengontrol radius blur (dalam poin) | Nilai lebih besar menciptakan tampilan “berbulu” |
| `Distance` | Seberapa jauh bayangan dipindahkan dari bentuk | Jarak kecil menjaga bentuk tetap “menempel” |
| `Angle` | Arah dalam derajat (0 = kanan, 90 = atas) | 45 memberi bayangan diagonal klasik |

Silakan bereksperimen—misalnya, setel `Color = Color.Gray` untuk **mengubah warna bayangan** menjadi nada yang lebih terang, atau gunakan `Angle = 135` untuk bayangan yang jatuh ke kiri‑bawah.

---

## Langkah 5: Simpan Dokumen yang Telah Dimodifikasi

Akhirnya, tulis perubahan kembali ke disk. Anda dapat menimpa file asli atau membuat file baru.

```csharp
        // Save the document with the new shadow.
        doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");
        Console.WriteLine("Shadow added successfully! Check output_with_shadow.docx");
    }
}
```

**Hasil:** Buka `output_with_shadow.docx` di Word, pilih bentuk, dan Anda akan melihat bayangan hitam tajam pada sudut 45 °, 30 % transparan, dengan blur lembut. Visualnya identik dengan apa yang akan Anda dapatkan jika menerapkan bayangan secara manual melalui UI Word.

---

## Bonus: Terapkan Bayangan pada Semua Bentuk di Dokumen

Jika Anda perlu **menerapkan efek bayangan** pada setiap bentuk, lakukan loop pada koleksi alih‑alih menargetkan satu node saja.

```csharp
        // Loop through every shape and add the same shadow.
        NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
        foreach (Shape shp in shapes)
        {
            shp.ShadowFormat.Visible = true;
            shp.ShadowFormat.Color = Color.Black;
            shp.ShadowFormat.Transparency = 0.3;
            shp.ShadowFormat.Size = 5;
            shp.ShadowFormat.Distance = 3;
            shp.ShadowFormat.Angle = 45;
        }
```

**Penanganan kasus tepi:** Beberapa bentuk (mis., WordArt) mungkin mengabaikan properti tertentu. Selalu uji pada sampel representatif.

---

## Konfirmasi Visual

Di bawah ini adalah tangkapan layar bentuk setelah bayangan diterapkan. Perhatikan offset 45 ° yang bersih dan transparansi yang halus.

![contoh menambahkan bayangan pada bentuk](add-shadow-to-shape.png){: .img alt="contoh menambahkan bayangan pada bentuk"}

---

## Pertanyaan yang Sering Diajukan

**Q: Bisakah saya menggunakan gradien warna khusus untuk bayangan?**  
A: Aspose.Words hanya mendukung warna solid untuk `ShadowFormat.Color`. Untuk gradien, Anda harus mengekspor bentuk sebagai gambar dan menerapkan efek pada tingkat grafis.

**Q: Bagaimana jika dokumen berisi bentuk yang dikelompokkan?**  
A: Setiap anggota grup adalah node `Shape` terpisah. Loop yang ditunjukkan pada bagian “Bonus” akan menangani mereka secara otomatis.

**Q: Apakah ini bekerja dengan file Word 2007‑2019?**  
A: Ya. Aspose.Words mengabstraksi format file, sehingga kode yang sama bekerja untuk `.doc`, `.docx`, dan bahkan `.rtf`.

**Q: Bagaimana cara membuat bayangan tidak terlihat lagi?**  
A: Setel `targetShape.ShadowFormat.Visible = false;` dan simpan kembali dokumen.

---

## Kesimpulan

Anda kini tahu persis cara **menambahkan bayangan pada bentuk** di C#. Dengan menyalakan `ShadowFormat.Visible` dan menyesuaikan warna, transparansi, ukuran, jarak, serta sudut, Anda dapat **menerapkan efek bayangan** yang sesuai dengan spesifikasi desain apa pun—termasuk **bayangan 45 derajat** yang presisi.  

Apakah Anda mengotomatisasi pembuatan laporan, membangun mesin templat, atau sekadar memoles satu diagram, pendekatan ini memberi Anda kontrol penuh secara programatik atas kedalaman visual bentuk. Selanjutnya, coba **mengubah warna bayangan** berdasarkan tema, atau gabungkan dengan logika isi‑bentuk untuk menciptakan visual dinamis berbasis data.

Selamat coding, dan jangan ragu untuk bereksperimen—bayangan murah untuk ditambahkan tetapi dapat secara dramatis meningkatkan keterbacaan. Jika Anda menemukan panduan ini berguna, bagikan kepada rekan tim atau tinggalkan komentar dengan modifikasi Anda sendiri!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}