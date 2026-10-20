---
category: general
date: 2026-08-04
description: Buat dokumen Word kosong dan sisipkan tombol perintah menggunakan Aspose.Words.
  Pelajari cara mengatur ukuran tombol dan menambahkan tombol yang dapat diklik di
  C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert command button
- add clickable button
- set button size
- create command button
language: id
lastmod: 2026-08-04
og_description: Buat dokumen Word kosong dengan Aspose.Words dan sisipkan tombol perintah.
  Panduan ini menunjukkan cara mengatur ukuran tombol, menambahkan tombol yang dapat
  diklik, dan menyimpan file.
og_image_alt: Screenshot of a Word document containing a clickable command button
  created with C#
og_title: Buat dokumen Word kosong dan tambahkan tombol perintah – tutorial lengkap
  C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  headline: Create blank word document with a command button – step‑by‑step guide
  type: TechArticle
- description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  name: Create blank word document with a command button – step‑by‑step guide
  steps:
  - name: The ProgID of the OLE control – `"CommandButton"` for a standard button.
    text: The ProgID of the OLE control – `"CommandButton"` for a standard button.
  - name: A `Rectangle` that defines the **set button size** and position.
    text: A `Rectangle` that defines the **set button size** and position.
  - name: The caption that appears on the button.
    text: The caption that appears on the button.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Buat dokumen Word kosong dengan tombol perintah – panduan langkah demi langkah
url: /id/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen Word kosong dengan tombol perintah – panduan langkah demi langkah

Jika Anda perlu **membuat dokumen Word kosong** yang berisi tombol interaktif, tutorial ini menunjukkan cara melakukannya dengan Aspose.Words untuk .NET. Anda akan belajar **menyisipkan tombol perintah**, menyesuaikan tampilannya, dan membuatnya dapat diklik—semua dalam beberapa baris C#.

Panduan ini mencakup semua hal mulai dari penyiapan proyek hingga menyimpan file akhir, sehingga Anda dapat menyalin‑tempel solusi lengkap ke dalam aplikasi Anda sendiri. Sepanjang proses kami juga akan menjelaskan cara **menambahkan tombol yang dapat diklik**, **mengatur ukuran tombol**, dan **membuat tombol perintah** secara programatik.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* .NET 6.0 SDK atau yang lebih baru terpasang.
* Visual Studio 2022 (atau IDE apa pun yang mendukung .NET).
* Paket NuGet Aspose.Words untuk .NET (`Aspose.Words` versi 23.12 atau lebih baru).
* Familiaritas dasar dengan C# dan pemrograman berorientasi objek.

Tidak diperlukan assembly interop Office tambahan karena Aspose.Words berfungsi secara independen dari Microsoft Word.

## Langkah 1: Siapkan proyek .NET

Buat aplikasi konsol yang akan menampung kode otomatisasi Word.

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

Perintah ini membuat folder baru `WordButtonDemo` dengan file `Program.cs` yang siap dijalankan dan menambahkan pustaka Aspose.Words.

## Langkah 2: Buat dokumen Word kosong

Operasi pertama adalah **membuat dokumen Word kosong**. Aspose.Words menyediakan kelas `Document` yang mewakili file Word kosong secara langsung.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a new, empty Word document.
Document doc = new Document();
```

Membuat dokumen kosong memberi Anda kanvas bersih untuk menambahkan paragraf, tabel, atau, dalam kasus ini, tombol perintah OLE.

## Langkah 3: Inisialisasi DocumentBuilder

`DocumentBuilder` adalah pembantu yang memungkinkan Anda menyisipkan konten ke dalam dokumen. Anda perlu mengaitkannya dengan dokumen yang baru saja dibuat.

```csharp
// Attach a DocumentBuilder to the empty document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder menjaga posisi kursor saat ini, sehingga penyisipan selanjutnya terjadi tepat di tempat yang Anda inginkan.

## Langkah 4: Sisipkan tombol perintah

Sekarang kita **menyisipkan tombol perintah** (OLE `Forms2OleControl`) ke dalam dokumen. Metode `InsertForms2OleControl` memerlukan tiga argumen:

1. ProgID dari kontrol OLE – `"CommandButton"` untuk tombol standar.
2. `Rectangle` yang mendefinisikan **mengatur ukuran tombol** dan posisinya.
3. Caption yang muncul pada tombol.

```csharp
// Define the button's position (x, y) and size (width, height).
Rectangle buttonRect = new Rectangle(0, 0, 120, 30); // 120 px wide, 30 px high

// Insert the command button with the desired caption.
Forms2OleControl cmdButton = builder.InsertForms2OleControl(
    "CommandButton",   // ProgID for a CommandButton control
    buttonRect,        // Position and size
    "Click Me");       // Caption displayed on the button
```

Saat dokumen dibuka di Word, tombol berperilaku seperti kontrol formulir native—Anda dapat mengkliknya, dan Word akan mengeksekusi makro yang terkait (jika ada). Ini memenuhi kebutuhan **menambahkan tombol yang dapat diklik**.

### Mengapa menggunakan Forms2OleControl?

`Forms2OleControl` menyematkan objek OLE langsung ke dalam file DOCX, mempertahankan properti kontrol tanpa memerlukan assembly Word Interop. Ini adalah cara paling dapat diandalkan untuk **membuat tombol perintah** yang berfungsi di semua versi Word.

## Langkah 5: Sesuaikan tombol (opsional)

Anda mungkin ingin **mengatur ukuran tombol** secara lebih tepat atau mengubah properti tambahan seperti font atau warna latar. Aspose.Words mengekspos objek OLE yang mendasarinya, memungkinkan penyesuaian lebih lanjut.

```csharp
// Example: change the button's background color (requires OLE automation).
// Note: This step is optional and demonstrates additional customization.
cmdButton.OleFormat.Icon = true; // Show an icon instead of the default appearance.
```

Jika Anda memerlukan ukuran berbeda, cukup sesuaikan nilai `Rectangle` pada Langkah 4. Koordinat diukur dalam poin (1 pt = 1/72 inci), sehingga `120` kira‑kira setara dengan lebar 1,67 inci.

## Langkah 6: Simpan dokumen

Akhirnya, tulis dokumen ke disk. File yang dihasilkan berisi **dokumen Word kosong** dengan tombol perintah yang berfungsi penuh.

```csharp
// Save the document as a .docx file.
doc.Save("CommandButtonDemo.docx");
```

Saat Anda membuka `CommandButtonDemo.docx` di Microsoft Word, Anda akan melihat tombol berlabel “Click Me”. Mengklik tombol akan menampilkan dialog makro default kecuali Anda menambahkan makro khusus.

## Kode sumber lengkap

Berikut adalah program lengkap yang dapat Anda salin ke dalam `Program.cs`. Program ini mencakup semua langkah yang dijelaskan di atas dan dapat dikompilasi tanpa modifikasi.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordButtonDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Create a blank word document.
            Document doc = new Document();

            // Step 3: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 4: Define button size and insert command button.
            Rectangle buttonRect = new Rectangle(0, 0, 120, 30);
            Forms2OleControl cmdButton = builder.InsertForms2OleControl(
                "CommandButton",
                buttonRect,
                "Click Me");

            // Optional: further customization (e.g., set icon).
            // cmdButton.OleFormat.Icon = true;

            // Step 6: Save the document.
            doc.Save("CommandButtonDemo.docx");

            System.Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Hasil yang diharapkan

Menjalankan program menghasilkan `CommandButtonDemo.docx`. Membuka file tersebut di Word menampilkan:

* Satu halaman berisi tombol berlabel **Click Me**.
* Tombol menghormati **mengatur ukuran tombol** (120 × 30 poin).
* Mengklik tombol memicu perilaku tombol perintah default Word, mengonfirmasi bahwa operasi **menambahkan tombol yang dapat diklik** berhasil.

## Pertanyaan umum dan kasus tepi

| Pertanyaan | Jawaban |
|------------|---------|
| **Apakah ini bekerja dengan file .doc?** | Ya. Ubah ekstensi file di `doc.Save("file.doc")`. Kontrol OLE juga disimpan dalam format biner legacy. |
| **Bagaimana jika saya membutuhkan beberapa tombol?** | Panggil `InsertForms2OleControl` berulang kali, sesuaikan `Rectangle` untuk setiap tombol baru agar tidak tumpang tindih. |
| **Bisakah saya menempelkan makro ke tombol?** | Tombol itu sendiri tidak berisi kode makro. Anda harus menambahkan makro VBA ke dokumen secara manual atau melalui koleksi `Modules` pada objek `Document`. |
| **Apakah tombol terlihat saat mengekspor ke PDF?** | Saat Anda mengekspor DOCX ke PDF menggunakan Aspose.Words, tombol dirender sebagai gambar statis, bukan kontrol interaktif. |
| **Versi Word apa yang didukung?** | Tombol perintah OLE berfungsi di Word 2007 dan yang lebih baru, karena mengikuti spesifikasi standar Forms2.0. |

## Kesimpulan

Anda kini tahu cara **membuat dokumen Word kosong**, **menyisipkan tombol perintah**, **menambahkan tombol yang dapat diklik**, dan **mengatur ukuran tombol** menggunakan Aspose.Words untuk .NET. Contoh lengkap ini memperlihatkan alur kerja **membuat tombol perintah** dari awal hingga akhir, memberi Anda dasar yang kuat untuk tugas otomatisasi Word yang lebih maju.

## Langkah selanjutnya

* Jelajahi kontrol OLE lain (misalnya `CheckBox`, `ListBox`) dengan mengubah ProgID pada `InsertForms2OleControl`.
* Gabungkan tombol dengan makro VBA untuk melakukan aksi khusus saat pengguna mengkliknya.
* Gunakan `DocumentBuilder` Aspose.Words untuk menambahkan konten tambahan seperti tabel, gambar, atau catatan kaki sebelum menyisipkan tombol.
* Bereksperimen dengan nilai **mengatur ukuran tombol** untuk menyesuaikan kebutuhan tata letak dokumen Anda.

Selamat coding, dan nikmati membangun dokumen Word yang lebih kaya dengan kontrol interaktif!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}