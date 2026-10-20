---
category: general
date: 2026-07-29
description: Tambahkan tombol perintah ke dokumen Word menggunakan Aspose.Words. Pelajari
  cara mengatur properti kontrol ActiveX dan mengatur caption tombol perintah dalam
  beberapa langkah mudah.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button to word document
- set activex control properties
- set command button caption
- Aspose.Words ActiveX example
- C# insert ActiveX control
language: id
lastmod: 2026-07-29
og_description: Tambahkan tombol perintah ke dokumen Word dengan Aspose.Words. Tutorial
  ini menunjukkan cara mengatur properti kontrol ActiveX dan mengatur caption tombol
  perintah dengan cepat.
og_image_alt: Screenshot of a Word document with a Submit command button inserted
  via C#
og_title: Tambahkan Tombol Perintah ke Dokumen Word – Aspose.Words Langkah demi Langkah
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  headline: Add Command Button to Word Document with Aspose.Words – Complete Guide
  type: TechArticle
- description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  name: Add Command Button to Word Document with Aspose.Words – Complete Guide
  steps:
  - name: Setting the Caption
    text: 'The caption is the text that appears on the button itself. To **set command
      button caption**, simply assign a string to the `Caption` property:'
  - name: Naming the Control
    text: 'Giving the control a meaningful name makes it easier to reference later
      (for example, when automating Word macros). We’ll set the `Name` property:'
  - name: Positioning on the Page
    text: 'Word uses points (1/72 of an inch) for layout. Adjust the `Left` and `Top`
      properties to place the button where you need it:'
  - name: Expected Result
    text: 1. The Word document opens with a single page. 2. A rectangular button labeled
      **Submit** appears at the coordinates you specified. 3. If you right‑click the
      button and choose **Properties**, you’ll see the name `btnSubmit` and other
      properties you set.
  - name: Inserting Other ActiveX Types
    text: 'The `InsertForms2OleControl` method isn’t limited to command buttons. You
      can embed check boxes, option buttons, or even custom ActiveX objects:'
  - name: Handling Word Versions
    text: Older Word versions (pre‑2007) use the binary `.doc` format, which stores
      ActiveX controls differently. Aspose.Words automatically converts the control
      when you save as `.doc`, but some properties (like precise positioning) may
      shift. If you target legacy formats, test the output in the specific Wor
  - name: Security Settings
    text: 'Word may disable ActiveX controls on machines with strict macro security.
      To avoid a “Security Warning” dialog, consider:'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Menambahkan Tombol Perintah ke Dokumen Word dengan Aspose.Words – Panduan Lengkap
url: /id/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tambahkan Tombol Perintah ke Dokumen Word – Panduan Pemrograman Lengkap

Pernah perlu **menambahkan tombol perintah ke dokumen word** tetapi tidak yakin panggilan API mana yang harus digunakan? Anda tidak sendirian; banyak pengembang menemui kebuntuan ini saat pertama kali mencoba menyematkan kontrol interaktif dalam file DOCX. Kabar baiknya, Aspose.Words membuatnya terasa sangat mudah. Dalam panduan ini kami akan melangkah melalui pembuatan kontrol ActiveX CommandButton, **mengatur properti kontrol activex**, dan **mengatur caption tombol perintah**—semua dengan kode C# bersih yang dapat Anda salin‑tempel langsung sekarang.

Pada akhir tutorial ini Anda akan memiliki file Word yang berfungsi penuh berisi tombol “Submit” yang dapat diklik, siap dibuka di Microsoft Word. Tanpa skrip VBA eksternal, tanpa penyetelan UI manual—hanya kontrol programatik murni.

## Apa yang Akan Anda Pelajari

* Cara membuat dokumen Word kosong dan sebuah `DocumentBuilder`.
* Metode tepat untuk **menambahkan tombol perintah ke dokumen word** menggunakan Aspose.Words.
* Cara **mengatur properti kontrol activex** seperti ukuran, posisi, dan nama.
* Teknik yang tepat untuk **mengatur caption tombol perintah** sehingga tombol menampilkan teks yang Anda inginkan.
* Tips menangani kasus tepi seperti tipe tombol berbeda, skala DPI, dan kompatibilitas versi Word.

> **Prasyarat:** Visual Studio (atau IDE C# apa pun) dengan Aspose.Words untuk .NET terpasang (paket NuGet `Aspose.Words`). Tidak diperlukan pengalaman ActiveX sebelumnya.

---

## Langkah 1: Siapkan Proyek dan Impor Namespace

Sebelum kita dapat **menambahkan tombol perintah ke dokumen word**, kita memerlukan proyek C# yang mereferensikan Aspose.Words. Buat aplikasi konsol .NET baru, lalu tambahkan paket NuGet:

```bash
dotnet add package Aspose.Words
```

Sekarang bawa namespace yang diperlukan ke dalam file sumber Anda:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;
```

Ketiga `using` directive ini memberi Anda akses ke kelas `Document`, `DocumentBuilder`, dan `Forms2OleControl` yang menggerakkan penyisipan ActiveX.

*Tip profesional:* Jika Anda menggunakan Visual Studio, IDE akan menyarankan penambahan ini secara otomatis saat Anda mengetik nama kelas.

---

## Langkah 2: Buat Dokumen Kosong dan Builder

Objek `Document` baru mewakili file Word yang kosong. `DocumentBuilder` adalah “pena” handy kami yang memungkinkan menggambar, menyisipkan teks, dan—yang paling penting—menempatkan kontrol ActiveX.

```csharp
// Initialize a new, empty Word document.
Document doc = new Document();

// Attach a builder to the document for editing.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Pada titik ini dokumen hanyalah kanvas kosong—bayangkan seperti lembar kertas bersih yang menunggu tombol perintah Anda.

---

## Langkah 3: Sisipkan Kontrol ActiveX CommandButton

Sekarang kita akhirnya **menambahkan tombol perintah ke dokumen word**. Aspose.Words menyediakan metode `InsertForms2OleControl`, yang menerima tipe kontrol dan dimensi. Kita akan menggunakan `Forms2OleControlType.CommandButton` dan memberinya lebar nyaman 150 poin serta tinggi 30 poin.

```csharp
// Insert a CommandButton ActiveX control with a specific size.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton,
    width: 150,
    height: 30);
```

Metode ini mengembalikan instance `Forms2OleControl`, yang akan kita gunakan untuk **mengatur properti kontrol activex** pada langkah berikutnya.

---

## Langkah 4: Konfigurasikan Kontrol – Nama, Caption, dan Posisi

### Mengatur Caption

Caption adalah teks yang muncul pada tombol itu sendiri. Untuk **mengatur caption tombol perintah**, cukup tetapkan string ke properti `Caption`:

```csharp
commandButton.Caption = "Submit";
```

Anda dapat mengubah `"Submit"` menjadi apa saja—“Save”, “Export”, “Launch”, dll.—dan Word akan menampilkan teks persis itu.

### Menamai Kontrol

Memberi kontrol nama yang bermakna memudahkan referensi di kemudian hari (misalnya, saat mengotomatisasi makro Word). Kita akan mengatur properti `Name`:

```csharp
commandButton.Name = "btnSubmit";
```

### Menentukan Posisi pada Halaman

Word menggunakan poin (1/72 inci) untuk tata letak. Sesuaikan properti `Left` dan `Top` untuk menempatkan tombol di lokasi yang Anda inginkan:

```csharp
commandButton.Left = 100; // 100 points from the left margin
commandButton.Top  = 200; // 200 points from the top of the page
```

Jika Anda perlu meratakan tombol relatif terhadap paragraf, Anda dapat memindahkan kursor builder terlebih dahulu, lalu menyisipkan kontrol; koordinat akan relatif terhadap lokasi tersebut.

*Kasus tepi:* Pada monitor DPI tinggi ukuran visual mungkin terlihat sedikit berbeda di Word. Untuk menjaga ukuran fisik tombol tetap konsisten di semua perangkat, Anda dapat menghitung poin berdasarkan DPI target (biasanya 96 DPI untuk Word).

---

## Langkah 5: Simpan Dokumen

Dengan tombol yang sudah dikonfigurasi sepenuhnya, menyimpan file cukup satu baris kode:

```csharp
// Save the document; the ActiveX control is stored inside the DOCX.
doc.Save("CommandButton.docx");
```

File `CommandButton.docx` yang dihasilkan berisi tombol ActiveX yang berfungsi penuh. Buka di Microsoft Word, dan Anda akan melihat tombol “Submit” berada tepat pada posisi yang Anda tentukan.

### Hasil yang Diharapkan

1. Dokumen Word terbuka dengan satu halaman.
2. Sebuah tombol persegi panjang berlabel **Submit** muncul pada koordinat yang Anda tentukan.
3. Jika Anda klik kanan tombol dan pilih **Properties**, Anda akan melihat nama `btnSubmit` serta properti lain yang telah Anda atur.

---

## Langkah 6: Variasi Lanjutan dan Kesalahan Umum

### Menyisipkan Tipe ActiveX Lain

Metode `InsertForms2OleControl` tidak terbatas pada tombol perintah. Anda dapat menyematkan kotak centang, tombol pilihan, atau bahkan objek ActiveX khusus:

```csharp
// Example: Insert a CheckBox instead of a CommandButton.
Forms2OleControl checkBox = builder.InsertForms2OleControl(
    Forms2OleControlType.CheckBox,
    width: 20,
    height: 20);
checkBox.Name = "chkAgree";
checkBox.Caption = "I Agree";
```

Pola **mengatur properti kontrol activex** yang sama berlaku—hanya ganti enum tipe.

### Menangani Versi Word

Versi Word lama (sebelum 2007) menggunakan format biner `.doc`, yang menyimpan kontrol ActiveX secara berbeda. Aspose.Words secara otomatis mengonversi kontrol saat Anda menyimpan sebagai `.doc`, tetapi beberapa properti (seperti penempatan presisi) mungkin bergeser. Jika Anda menargetkan format legacy, uji output pada versi Word yang spesifik.

### Pengaturan Keamanan

Word dapat menonaktifkan kontrol ActiveX pada mesin dengan keamanan makro yang ketat. Untuk menghindari dialog “Security Warning”, pertimbangkan:

* Menandatangani dokumen dengan sertifikat tepercaya.
* Menginstruksikan pengguna untuk mengaktifkan konten ActiveX untuk lokasi file tersebut.
* Menggunakan alternatif tanpa makro (mis., kontrol konten biasa) jika keamanan menjadi perhatian.

---

## Langkah 7: Contoh Lengkap yang Siap Jalan

Berikut adalah program lengkap yang siap dijalankan, mencakup semua langkah yang telah dibahas. Salin ke `Program.cs`, sesuaikan jalur output bila perlu, dan tekan **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            width: 150,   // Width in points
            height: 30);  // Height in points

        // Step 3: Set the control's name and caption.
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Step 4: Position the control on the page.
        commandButton.Left = 100; // 100 points from left edge
        commandButton.Top  = 200; // 200 points from top edge

        // Optional: Add a paragraph above the button for context.
        builder.MoveToDocumentEnd();
        builder.Writeln("Click the button below to submit the form:");

        // Step 5: Save the document.
        string outputPath = "CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved successfully to {outputPath}");
    }
}
```

**Apa yang dilakukan kode ini:**

* Memulai dengan dokumen baru.
* Menyisipkan tombol perintah, **mengatur properti kontrol activex**, dan **mengatur caption tombol perintah**.
* Menambahkan paragraf penjelasan singkat.
* Menyimpan file sebagai `CommandButton.docx`.

Jalankan program, buka file yang dihasilkan, dan Anda akan melihat tombol berada di bawah teks penjelasan.

---

## Kesimpulan

Kami baru saja menunjukkan cara **menambahkan tombol perintah ke dokumen word** menggunakan Aspose.Words, cara **mengatur properti kontrol activex**, dan cara **mengatur caption tombol perintah**—semuanya dalam potongan kode C# yang singkat dan siap produksi. Pendekatan ini dapat diskalakan: ganti tipe kontrol, ubah dimensi, atau lakukan loop atas sumber data untuk menyematkan puluhan tombol secara otomatis.

Ingin melangkah lebih jauh? Coba:

* Mengaitkan tombol ke makro yang memicu ekspor data.
* Menambahkan gambar atau ikon khusus di dalam tombol menggunakan properti `Picture`.
* Membangun formulir lengkap dengan banyak kontrol ActiveX (textbox, combobox, dll.).

Eksperimen adalah cara terbaik untuk menguasai otomasi Word. Jika Anda menemui kendala, ingatlah untuk memeriksa kembali perhitungan DPI dan pengaturan keamanan Word Anda. Selamat coding, semoga dokumen Anda semakin interaktif!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}