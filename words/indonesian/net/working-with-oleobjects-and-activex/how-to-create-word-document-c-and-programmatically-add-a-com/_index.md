---
category: general
date: 2026-09-11
description: Pelajari cara membuat dokumen Word dengan C# dan menambahkan tombol perintah
  secara programatis menggunakan Aspose.Words dalam beberapa langkah sederhana.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- programmatically add command button
language: id
lastmod: 2026-09-11
og_description: Buat dokumen Word C# dan secara programatis tambahkan tombol perintah
  dengan Aspose.Words. Ikuti panduan lengkap ini untuk solusi yang berfungsi.
og_image_alt: Screenshot of a Word document containing a Submit command button created
  with C#
og_title: Buat dokumen Word C# – tambahkan tombol perintah secara programatik
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  headline: How to create word document c# and programmatically add a command button
  type: TechArticle
- description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  name: How to create word document c# and programmatically add a command button
  steps:
  - name: Launch Word and open `CommandButton.docx`.
    text: Launch Word and open `CommandButton.docx`.
  - name: You should see a button labeled **Submit** in the document body.
    text: You should see a button labeled **Submit** in the document body.
  - name: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
    text: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
title: Cara membuat dokumen Word dengan C# dan menambahkan tombol perintah secara
  programatis
url: /id/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-and-programmatically-add-a-com/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat dokumen Word c# dan menambahkan tombol perintah secara programatik

Jika Anda perlu **create word document c#** dan menyematkan tombol interaktif, panduan ini menunjukkan secara tepat cara melakukannya. Dengan menggunakan Aspose.Words Anda dapat menambahkan tombol perintah secara programatik hanya dengan beberapa baris kode, menghilangkan kebutuhan kerja UI manual di Word.

Dalam tutorial ini Anda akan belajar cara:

* Menginisialisasi file Word kosong dengan C#.
* Menyisipkan kontrol **CommandButton** ActiveX.
* Mengatur properti tombol seperti nama dan caption.
* Menyimpan dokumen sehingga tombol muncul saat file dibuka di Microsoft Word.

Tidak ada alat eksternal yang diperlukan selain pustaka Aspose.Words untuk .NET, dan langkah‑langkah ini bekerja dengan .NET 6+ atau .NET Framework 4.6.2 dan yang lebih baru.

## Prasyarat

Sebelum Anda memulai, pastikan Anda memiliki:

| Persyaratan | Alasan |
|------------|--------|
| .NET 6 SDK (or .NET Framework 4.6.2+) | Menyediakan runtime untuk proyek C#. |
| Visual Studio 2022 (or any C# IDE) | Memudahkan penulisan, pembangunan, dan menjalankan kode. |
| Aspose.Words for .NET NuGet package | Menyediakan kelas `Document`, `DocumentBuilder`, dan `Forms2OleControl` yang digunakan dalam contoh. |
| Basic knowledge of C# syntax | Memungkinkan Anda mengikuti kode tanpa kurva belajar tambahan. |

Anda dapat menambahkan paket Aspose.Words melalui konsol NuGet:

```powershell
Install-Package Aspose.Words
```

## Langkah 1: Siapkan proyek konsol C# baru

Buat aplikasi konsol yang akan menghasilkan file Word. Buka terminal dan jalankan:

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

File `Program.cs` yang dihasilkan akan menampung kode yang ditunjukkan pada langkah‑langkah berikutnya.

## Langkah 2: Buat dokumen kosong dan DocumentBuilder

Operasi pertama adalah menginstansiasi objek `Document`, yang mewakili file `.docx` kosong, dan `DocumentBuilder` yang memungkinkan Anda mengedit isi dokumen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Step 2: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Mengapa ini penting:**  
`Document` adalah kontainer untuk semua elemen Word (paragraf, tabel, kontrol). `DocumentBuilder` menyediakan API yang fluently untuk menyisipkan objek pada lokasi kursor saat ini tanpa harus berurusan dengan koleksi node tingkat rendah.

## Langkah 3: Sisipkan kontrol CommandButton ActiveX

Aspose.Words mendukung penyisipan kontrol ActiveX lama melalui metode `InsertForms2OleControl`. Metode ini memerlukan tipe kontrol dan ukuran yang diinginkan dalam poin.

```csharp
        // Step 3: Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);
```

**Apa yang terjadi di balik layar:**  
Word memperlakukan kontrol ActiveX sebagai objek OLE (Object Linking and Embedding). Kelas `Forms2OleControl` membungkus data OLE dan mengekspos properti seperti `Name` dan `Caption`.

## Langkah 4: Konfigurasikan nama dan caption tombol

Setelah kontrol ditempatkan, Anda dapat menyesuaikan properti runtime‑nya. Menetapkan `Name` yang bermakna membantu Anda mengidentifikasi tombol nanti, sementara `Caption` menentukan teks yang ditampilkan pada tombol.

```csharp
        // Step 4: Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";
```

**Tips Pro:**  
Jika Anda berencana menangani peristiwa klik tombol dengan VBA, `Name` menjadi nama makro yang Anda referensikan, mis., `Sub btnSubmit_Click()`.

## Langkah 5: Simpan dokumen ke disk

Akhirnya, tulis dokumen ke file `.docx`. Pilih folder yang Anda miliki akses menulis; contoh ini menggunakan jalur relatif, yang akan ter‑resolve ke direktori output proyek.

```csharp
        // Step 5: Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Menjalankan program menghasilkan `CommandButton.docx`. Membuka file di Microsoft Word menampilkan tombol **Submit** yang dapat diklik:

![Dokumen Word dengan tombol Submit](/images/command-button.png "Tangkapan layar dokumen Word yang berisi tombol Submit yang dibuat dengan C#")

*Teks alt gambar (og_image_alt):* `Screenshot of a Word document containing a Submit command button created with C#`

## Memverifikasi hasil

1. Buka Word dan buka `CommandButton.docx`.  
2. Anda harus melihat tombol berlabel **Submit** di isi dokumen.  
3. Mengarahkan kursor ke tombol akan menampilkan nama `btnSubmit` di panel **Properties** (tab Developer → Properties).  

Jika tombol tidak muncul, pastikan tab **Developer** diaktifkan di Word (File → Options → Customize Ribbon → centang *Developer*). Kontrol ActiveX disembunyikan ketika tab tersebut dinonaktifkan.

## Menangani variasi umum dan kasus tepi

| Situasi | Penyesuaian yang disarankan |
|-----------|------------------------|
| **Ukuran tombol berbeda** | Ubah argumen lebar dan tinggi dalam `InsertForms2OleControl`. Misalnya, `150, 40` membuat tombol lebih besar. |
| **Beberapa tombol** | Panggil `InsertForms2OleControl` berulang kali, memindahkan kursor builder di antara pemanggilan (`builder.Writeln();`). |
| **Tombol tanpa ActiveX** | Gunakan `InsertFormField` untuk menambahkan field formulir lama (mis., kotak centang) jika Anda memerlukan kompatibilitas dengan versi Word lama yang memblokir ActiveX. |
| **Penggunaan lintas‑platform** | Kontrol ActiveX hanya berfungsi pada versi Word Windows. Untuk Mac atau penampil berbasis web, pertimbangkan menyisipkan hyperlink yang bergaya tombol sebagai gantinya. |
| **Peringatan keamanan** | Word mungkin menampilkan prompt keamanan saat membuka dokumen yang berisi kontrol ActiveX. Menandatangani dokumen dengan sertifikat tepercaya mengurangi gesekan ini. |

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke `Program.cs`. Program ini akan dikompilasi dan dijalankan tanpa modifikasi setelah menambahkan paket NuGet Aspose.Words.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);

        // Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Output yang diharapkan di konsol:**

```
Document saved to C:\Path\To\WordButtonDemo\bin\Debug\net6.0\CommandButton.docx
```

Membuka file yang dihasilkan menampilkan tombol **Submit** siap untuk interaksi.

## Kesimpulan

Anda kini tahu cara **create word document c#** dan **programmatically add command button** menggunakan Aspose.Words. Prosesnya menyederhanakan menjadi menginisialisasi `Document`, menyisipkan `Forms2OleControl`, mengonfigurasi propertinya, dan menyimpan file. Dari sini Anda dapat:

* Menambahkan lebih banyak kontrol (mis., kotak centang, bidang teks) dengan mengubah `ControlType`.
* Menyematkan makro VBA ke tombol untuk logika khusus.
* Menggabungkan teknik ini dengan fitur Aspose.Words lainnya seperti mail merge atau pengisian templat.

Eksperimen dengan ukuran, caption, dan beberapa tombol yang berbeda untuk menyesuaikan skenario otomatisasi Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang berhubungan erat dan membangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Dokumen Word dengan Header dan Footer Menggunakan Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Buat Dokumen Word dengan Aspose.Words untuk .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Buat Group Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}