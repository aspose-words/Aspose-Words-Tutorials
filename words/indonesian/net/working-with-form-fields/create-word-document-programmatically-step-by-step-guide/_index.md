---
category: general
date: 2026-08-04
description: Buat dokumen Word secara programatis menggunakan C#. Pelajari cara menambahkan
  tombol perintah secara programatis dengan Aspose.Words dalam beberapa langkah saja.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- programmatically add command button
- Aspose.Words InsertForms2OleControl
- C# Word automation
- OLE command button in Word
language: id
lastmod: 2026-08-04
og_description: Buat dokumen Word secara programatis dengan Aspose.Words. Panduan
  ini menunjukkan cara menambahkan tombol perintah secara programatis, mengkonfigurasinya,
  dan menyimpan file.
og_image_alt: Screenshot of a Word document that contains a Command Button added programmatically
og_title: Buat dokumen Word secara programatis – tutorial lengkap C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  headline: Create word document programmatically – step‑by‑step guide
  type: TechArticle
- description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  name: Create word document programmatically – step‑by‑step guide
  steps:
  - name: The `ControlType` enum value (here `CommandButton`).
    text: The `ControlType` enum value (here `CommandButton`).
  - name: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
    text: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
  - name: Optionally, additional OLE properties (not needed for the basic button).
    text: Optionally, additional OLE properties (not needed for the basic button).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Buat dokumen Word secara programatis – panduan langkah demi langkah
url: /id/net/working-with-form-fields/create-word-document-programmatically-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat dokumen Word secara programatis – tutorial lengkap C# 

Jika Anda perlu **membuat dokumen Word secara programatis**, panduan ini menunjukkan secara tepat cara melakukannya dengan Aspose.Words untuk .NET. Dalam beberapa baris kode C# saja Anda dapat menghasilkan file `.docx` kosong, **menambahkan kontrol tombol perintah secara programatis**, mengatur propertinya, dan menyimpan hasilnya.  

Langkah-langkah di bawah ini mencakup semua hal mulai dari penyiapan proyek hingga penanganan kasus tepi, sehingga Anda dapat menyalin kode ke dalam aplikasi Anda sendiri dan menjalankannya tanpa modifikasi.

## Apa yang akan Anda capai

* Menginisialisasi dokumen Word baru sepenuhnya di memori.  
* **Menambahkan kontrol OLE tombol perintah secara programatis** di lokasi dan ukuran mana pun.  
* Mengonfigurasi caption tombol, nama internal, dan properti OLE lainnya.  
* Menyimpan dokumen yang dihasilkan ke disk atau ke stream untuk pemrosesan lebih lanjut.

### Prasyarat

* .NET 6.0 atau yang lebih baru (kode ini juga berfungsi dengan .NET Framework 4.6+).  
* Lisensi Aspose.Words untuk .NET yang valid (atau evaluasi gratis).  
* Familiaritas dasar dengan C# dan Visual Studio (atau IDE pilihan Anda).  

> **Pro tip:** Jika Anda menjalankan contoh tanpa lisensi, Aspose.Words akan menambahkan watermark evaluasi kecil pada halaman pertama.

## Langkah 1: Siapkan proyek dan impor namespace yang diperlukan

Buat aplikasi Console baru (atau integrasikan ke dalam layanan yang ada) dan tambahkan paket NuGet Aspose.Words:

```bash
dotnet add package Aspose.Words
```

Kemudian sertakan namespace penting di bagian atas file `.cs` Anda:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Impor ini memberi Anda akses ke `Document`, `DocumentBuilder`, `Forms2OleControl`, dan struct `RectangleF` yang digunakan untuk penempatan.

## Langkah 2: Inisialisasi dokumen Word baru

Operasi pertama dalam alur kerja **membuat dokumen Word secara programatis** apa pun adalah membuat instance objek `Document`. Objek ini hanya berada di memori sampai Anda menyimpannya secara eksplisit.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Attach a DocumentBuilder to simplify content insertion
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` berfungsi seperti kursor yang melacak di mana elemen berikutnya akan ditempatkan. Menggunakannya membuat kode tetap singkat dan meniru cara Anda mengetik langsung di Word.

## Langkah 3: Sisipkan kontrol OLE tombol perintah

Aspose.Words menyediakan metode `InsertForms2OleControl` untuk menyematkan objek OLE seperti tombol perintah, kotak centang, atau kotak kombo. Metode ini memerlukan tiga argumen:

1. Nilai enum `ControlType` (di sini `CommandButton`).  
2. `RectangleF` yang mendefinisikan posisi X‑Y serta lebar‑tinggi kontrol (diukur dalam poin, di mana 72 pt = 1 inci).  
3. Opsional, properti OLE tambahan (tidak diperlukan untuk tombol dasar).

```csharp
// Step 3: Programmatically add command button at (100,100) with size 120×30 points
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Mengapa ini berhasil:** `InsertForms2OleControl` membuat kontainer OLE dalam dokumen dan mengembalikan pembungkus `Forms2OleControl`. Pembungkus ini memungkinkan Anda memanipulasi objek OLE yang mendasarinya (tombol sebenarnya) tanpa harus berurusan dengan interop COM tingkat rendah.

## Langkah 4: Konfigurasikan caption dan nama internal tombol

Setelah penyisipan, biasanya Anda ingin memberikan tombol label yang terlihat oleh pengguna dan identifier internal yang dapat direferensikan oleh macro atau add‑in Anda nanti.

```csharp
// Step 4: Set caption and name of the button
commandButton.OleFormat.OleObject.Caption = "Click Me";
commandButton.OleFormat.OleObject.Name = "cmdClickMe";
```

* `Caption` adalah teks yang ditampilkan pada tombol di UI Word.  
* `Name` adalah identifier programatik yang digunakan oleh VBA atau skrip otomatisasi eksternal.

### Opsional: Tetapkan macro ke tombol

Jika Anda berencana menjalankan macro VBA ketika tombol diklik, Anda dapat melampirkan nama macro:

```csharp
commandButton.OleFormat.OleObject.MacroName = "MyMacro";
```

> **Kasus khusus:** Saat dokumen target dibuka di mesin tanpa macro tersebut, Word akan menampilkan peringatan keamanan. Selalu tanda tangani macro Anda atau beri tahu pengguna tentang pengaturan yang diperlukan.

## Langkah 5: Simpan dokumen

Anda dapat menulis file ke disk, `MemoryStream`, atau langsung ke objek respons dalam web API. Pendekatan paling sederhana untuk demo console adalah menyimpan ke folder lokal:

```csharp
// Step 5: Persist the document containing the button
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

`.docx` yang dihasilkan akan terbuka di Microsoft Word dengan tombol perintah yang berfungsi dan menampilkan “Click Me”. Mengklik tombol akan memicu macro yang ditetapkan (jika ada) atau hanya menampilkan pesan default.

## Contoh lengkap yang berfungsi

Salin program berikut ke dalam `Program.cs` dan jalankan. Program ini mendemonstrasikan seluruh alur **membuat dokumen Word secara programatis**, termasuk penanganan error.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        try
        {
            // 1️⃣ Initialise a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a CommandButton OLE control
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                new RectangleF(100, 100, 120, 30));

            // 3️⃣ Set button properties
            commandButton.OleFormat.OleObject.Caption = "Click Me";
            commandButton.OleFormat.OleObject.Name = "cmdClickMe";
            // Optional macro assignment (uncomment if needed)
            // commandButton.OleFormat.OleObject.MacroName = "MyMacro";

            // 4️⃣ Save the document
            string outputPath = @"C:\Temp\CommandButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document created successfully at {outputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ Error: {ex.Message}");
        }
    }
}
```

**Hasil yang diharapkan:** Membuka `CommandButton.docx` di Word menampilkan tombol dengan label “Click Me”. Mengarahkan kursor ke tombol memperlihatkan nama `cmdClickMe` di panel properti.

## Pertanyaan umum dan pemecahan masalah

| Pertanyaan | Jawaban |
|------------|---------|
| *Bisakah saya menambahkan tombol ke dokumen yang sudah ada?* | Ya. Muat file dengan `new Document("Existing.docx")`, lalu gunakan panggilan `InsertForms2OleControl` yang sama. |
| *Unit apa yang digunakan `RectangleF`?* | Poin (1 inci = 72 pt). Sesuaikan nilai untuk menempatkan tombol dengan tepat. |
| *Apakah tombol akan berfungsi di Word untuk Mac?* | Kontrol OLE hanya didukung di Word Windows. Di Mac tombol muncul sebagai gambar statis. |
| *Apakah saya memerlukan lisensi untuk penggunaan produksi?* | Lisensi komersial menghapus watermark evaluasi dan membuka semua fungsionalitas. |
| *Bagaimana cara mengubah ukuran tombol setelah disisipkan?* | Modifikasi `commandButton.Width` dan `commandButton.Height` atau sisipkan kembali dengan `RectangleF` baru. |

## Memperluas solusi

Sekarang Anda tahu cara **menambahkan kontrol tombol perintah secara programatis**, Anda dapat menjelajahi topik terkait berikut:

* **Menyisipkan kontrol formulir lain** – gunakan `ControlType.CheckBox`, `ControlType.OptionButton`, dll. (mencakup kata kunci sekunder *Aspose.Words InsertForms2OleControl*).  
* **Mengisi dokumen dengan data dinamis** – gabungkan data dari basis data ke dalam tabel atau bidang mail‑merge.  
* **Ekspor ke PDF** – setelah menambahkan tombol, panggil `doc.Save("output.pdf", SaveFormat.Pdf)` untuk menghasilkan versi PDF (relevan dengan *C# Word automation*).  

## Kesimpulan

Anda kini memiliki pola lengkap yang siap produksi untuk **membuat dokumen Word secara programatis** dan **menambahkan tombol perintah secara programatis** menggunakan Aspose.Words untuk .NET. Tutorial ini mencakup penyiapan proyek, inisialisasi dokumen, penyisipan tombol OLE, konfigurasi properti, dan penyimpanan file. Jangan ragu untuk menyesuaikan kode guna menyisipkan kontrol formulir lain, melampirkan macro, atau mengintegrasikan logika ke dalam layanan web atau pekerjaan latar belakang.

Selamat coding, dan nikmati mengotomatisasi dokumen Word!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Membuat Dokumen Word dengan Aspose.Words – Panduan Langkah‑per‑Langkah](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)
- [Membuat Dokumen Word dengan Tabel Menggunakan Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Membuat Group Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}