---
category: general
date: 2026-07-23
description: Buat tombol dokumen Word menggunakan Aspose.Words – panduan langkah demi
  langkah untuk menyisipkan ActiveX CommandButton ke dalam file .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document button
- ActiveX CommandButton
- DocumentBuilder
- InsertForms2OleControl
- Aspose.Words
language: id
lastmod: 2026-07-23
og_description: 'Buat tombol dokumen Word dengan Aspose.Words: pelajari cara menyisipkan
  CommandButton ActiveX ke dalam file Word dalam hitungan menit.'
og_image_alt: Screenshot of a Word document showing an inserted CommandButton control
og_title: Tombol Buat Dokumen Word – Panduan Lengkap Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  headline: create word document button with Aspose.Words – Full Code Example
  type: TechArticle
- description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  name: create word document button with Aspose.Words – Full Code Example
  steps:
  - name: '**Creates** an OLE object inside the Word file.'
    text: '**Creates** an OLE object inside the Word file.'
  - name: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
    text: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
  - name: '**Positions** it according to the rectangle we supplied.'
    text: '**Positions** it according to the rectangle we supplied.'
  - name: Launch Microsoft Word.
    text: Launch Microsoft Word.
  - name: Navigate to **File → Open** and select `CommandButton.docx`.
    text: Navigate to **File → Open** and select `CommandButton.docx`.
  - name: You should see a rectangular button labeled “CommandButton1”.
    text: You should see a rectangular button labeled “CommandButton1”.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
- CommandButton
title: Tombol Membuat Dokumen Word dengan Aspose.Words – Contoh Kode Lengkap
url: /id/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# buat tombol dokumen word dengan Aspose.Words – Panduan Pemrograman Lengkap

Pernah membutuhkan **membuat tombol dokumen word** tetapi tidak yakin API mana yang harus digunakan? Anda tidak sendirian—banyak pengembang mengalami kebuntuan saat mencoba menyematkan kontrol interaktif ke dalam file .docx. Kabar baiknya? Dengan Aspose.Words for .NET Anda dapat menambahkan ActiveX CommandButton yang berfungsi penuh ke dalam dokumen Word hanya dengan beberapa baris kode.

Dalam tutorial ini kami akan membahas seluruh proses: mulai dari menyiapkan proyek, menginisialisasi `DocumentBuilder`, menyisipkan tombol dengan `InsertForms2OleControl`, dan akhirnya menyimpan file sehingga Word mengenali kontrol tersebut. Pada akhir tutorial Anda akan memiliki file Word siap pakai yang berisi tombol yang dapat diklik—tanpa perlu melakukan akrobatik COM interop.

## Apa yang Anda Butuhkan

- **.NET 6.0** atau lebih baru (kode ini juga bekerja dengan .NET Framework 4.6+).  
- Paket NuGet **Aspose.Words for .NET** (versi 23.9 atau lebih baru).  
- Pemahaman dasar tentang C# (kami akan menjaga sintaksnya ramah pemula).  
- Visual Studio 2022 atau IDE apa pun yang Anda sukai.

Itu saja—tanpa referensi COM tambahan, tanpa interop Office, hanya kode terkelola murni.

---

## Langkah 1: Siapkan Aspose.Words untuk **membuat tombol dokumen word**

Pertama-tama, tambahkan paket Aspose.Words ke proyek Anda:

```bash
dotnet add package Aspose.Words
```

Atau, jika Anda menggunakan UI NuGet di Visual Studio, cari “Aspose.Words” dan klik **Install**. Baris tunggal ini memberi Anda akses ke `Document`, `DocumentBuilder`, dan metode `InsertForms2OleControl` yang akan kami perlukan nanti.

> **Pro tip:** Jaga paket NuGet Anda tetap terbaru; rilis yang lebih baru sering menyertakan perbaikan bug untuk penanganan ActiveX.

## Langkah 2: Inisialisasi **DocumentBuilder** untuk **ActiveX CommandButton**

Sekarang kita membuat dokumen Word baru dan memulai `DocumentBuilder`. Anggap `DocumentBuilder` sebagai kuas cat yang memungkinkan Anda menggambar konten di kanvas.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 2.1: Create a new empty document
        Document document = new Document();

        // Step 2.2: Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

Perhatikan bagaimana kami mengimpor `System.Drawing`—struct `Rectangle` menentukan lokasi dan ukuran tombol. Di sinilah **ActiveX CommandButton** akan berada.

## Langkah 3: Gunakan **InsertForms2OleControl** untuk **menambahkan CommandButton**

Berikut inti tutorial: menyisipkan tombol itu sendiri. Metode `InsertForms2OleControl` menerima tiga argumen—tipe kontrol, sebuah `Rectangle`, dan opsional nama. Kami akan menggunakan `OleControlType.CommandButton` untuk menentukan kontrol yang tepat.

```csharp
        // Step 3: Insert an ActiveX CommandButton at (0,0) with width=100, height=30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));
```

Pemanggilan tunggal itu melakukan banyak hal:

1. **Membuat** objek OLE di dalam file Word.  
2. **Mendaftarkan**nya sebagai ActiveX CommandButton, yang akan ditampilkan Word sebagai elemen UI yang dapat diklik.  
3. **Menempatkan**nya sesuai dengan rectangle yang kami berikan.

Jika Anda perlu mengubah caption tombol atau properti lainnya, Anda dapat melakukannya setelah penyisipan dengan mengakses `OleFormat` yang mendasarinya. Untuk kebanyakan skenario, caption default (“CommandButton1”) sudah cukup.

## Langkah 4: Simpan Dokumen Word yang Memuat **CommandButton**

Menyimpan sangat sederhana—cukup arahkan ke folder yang Anda memiliki akses menulis. Ekstensi file harus `.docx` agar tombol tetap ada setelah proses round‑trip.

```csharp
        // Step 4: Save the document with the embedded button
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Saat Anda membuka `CommandButton.docx` di Microsoft Word, Anda akan melihat tombol kecil di pojok kiri atas halaman pertama. Mengkliknya tidak melakukan apa‑apa secara default (itu memerlukan VBA), tetapi kontrol tersebut berfungsi penuh dan dapat dihubungkan nanti.

> **Mengapa ini berhasil:** Aspose.Words menulis aliran OLE langsung ke dalam paket DOCX, melewati kebutuhan Word untuk menghasilkan kontrol pada saat runtime. Ini menjamin tombol muncul tepat di tempat Anda menempatkannya.

## Langkah 5: Verifikasi Tombol di Word

Buka file yang dihasilkan:

1. Buka Microsoft Word.  
2. Arahkan ke **File → Open** dan pilih `CommandButton.docx`.  
3. Anda harus melihat tombol berbentuk persegi panjang berlabel “CommandButton1”.

Jika Anda tidak melihat tombol, pastikan **Design Mode** diaktifkan (Developer → Design Mode). Ini mengubah tampilan visual kontrol ActiveX.

## Langkah 6: Opsi Lanjutan – Menyesuaikan **ActiveX CommandButton**

Berikut beberapa penyesuaian cepat yang mungkin berguna:

| Tujuan | Potongan Kode |
|------|--------------|
| Ubah caption | ```csharp<br/>OleFormat ole = builder.CurrentParagraph.Runs[0].OleFormat;<br/>ole.OleControlCaption = "Submit";``` |
| Atur nama macro (memerlukan dukungan macro Word) | ```csharp<br/>ole.OleControlMacroName = "MyMacro";``` |
| Ubah ukuran setelah penyisipan | ```csharp<br/>builder.MoveToDocumentEnd();<br/>builder.InsertForms2OleControl(OleControlType.CommandButton, new Rectangle(0,0,150,40));``` |

Potongan kode ini menunjukkan fleksibilitas `InsertForms2OleControl`. Anda bahkan dapat menyematkan kontrol ActiveX lain seperti `CheckBox` atau `ListBox` dengan mengganti enum `OleControlType`.

## Contoh Lengkap yang Berfungsi

Berikut adalah program lengkap yang siap disalin‑tempel yang **membuat tombol dokumen word** dari awal:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class CreateWordDocumentButton
{
    static void Main()
    {
        // 1️⃣ Create a new empty document
        Document document = new Document();

        // 2️⃣ Initialize DocumentBuilder – the tool that lets us edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert an ActiveX CommandButton at position (0,0) with size 100x30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));

        // 4️⃣ Save the .docx file – this is where the button lives
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);

        Console.WriteLine($"✅ Document with button saved to: {outputPath}");
    }
}
```

**Output yang diharapkan saat Anda menjalankan program:**

```
✅ Document with button saved to: C:\Temp\CommandButton.docx
```

Buka file yang dihasilkan dan Anda akan melihat tombol tepat di tempat yang ditentukan oleh kode.

## Kesalahan Umum & Cara Menghindarinya

- **Referensi `System.Drawing` hilang** – Struct `Rectangle` berada di sana; tanpa itu kompiler akan mengeluh.  
- **Menggunakan versi Aspose.Words yang lebih lama** – Rilis awal tidak sepenuhnya mendukung `InsertForms2OleControl`. Tingkatkan ke paket stabil terbaru.  
- **Menyimpan sebagai `.doc` bukan `.docx`** – Aliran OLE akan dihapus dalam format biner lama, menyebabkan tombol menghilang.  
- **Menjalankan di server tanpa tampilan (headless) tanpa Word terinstal** – Tombol tetap ada dalam file, tetapi Anda tidak dapat melihatnya tanpa Word. Ini tetap dapat diterima untuk pipeline pembuatan otomatis.

## Langkah Selanjutnya – Memperluas Alur Kerja **membuat tombol dokumen word**

Setelah Anda menguasai dasar-dasarnya, pertimbangkan ide-ide tingkat lanjut berikut:

- **Lampirkan makro VBA** ke tombol untuk logika bisnis khusus.  
- **Hasilkan beberapa tombol** dalam loop untuk formulir dinamis.  
- **Gabungkan dengan Aspose.PDF** untuk mengekspor dokumen yang sama ke PDF sambil mempertahankan tata letak visual (tombol menjadi gambar statis di PDF).  
- **

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}