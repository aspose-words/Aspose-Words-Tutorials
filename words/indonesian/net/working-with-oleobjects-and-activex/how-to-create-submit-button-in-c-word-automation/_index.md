---
category: general
date: 2026-08-23
description: Buat tombol submit dalam otomatisasi Word menggunakan C#. Pelajari cara
  menambahkan tombol ActiveX, mengatur nama tombol, caption, dan teks secara programatik.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create submit button
- set button text
- set button name
- add activex button
- set button caption
language: id
lastmod: 2026-08-23
og_description: Buat tombol submit dalam otomatisasi Word C#. Panduan ini menunjukkan
  cara menambahkan tombol ActiveX, mengatur nama, caption, dan teksnya menggunakan
  Aspose.Words.
og_image_alt: Screenshot of a Word document showing a created submit button
og_title: Buat tombol kirim dalam otomatisasi Word C#
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  headline: How to create submit button in C# Word automation
  type: TechArticle
- description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  name: How to create submit button in C# Word automation
  steps:
  - name: Expected output
    text: 'Running the program creates `SubmitButton.docx`. When you open the file
      in Microsoft Word:'
  - name: Handling naming collisions
    text: 'If you run the routine multiple times on the same document, Word may auto‑rename
      duplicate controls. To guarantee uniqueness, you can prepend a GUID:'
  - name: Localizing the button caption
    text: 'For multilingual documents, store captions in a resource file and assign
      them at runtime:'
  - name: Responding to the button click
    text: 'The button itself does not contain click logic in C#. You typically attach
      a VBA macro:'
  type: HowTo
tags:
- C#
- Word automation
- ActiveX
- Aspose.Words
title: Cara membuat tombol kirim dalam otomatisasi Word C#
url: /id/net/working-with-oleobjects-and-activex/how-to-create-submit-button-in-c-word-automation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat tombol submit di otomatisasi Word dengan C#

Jika Anda perlu **membuat tombol submit** di dalam dokumen Word menggunakan C#, panduan ini akan memandu Anda melalui seluruh proses. Anda akan melihat cara menambahkan tombol ActiveX, memberi nama programatik, dan mengatur caption tombol sehingga terlihat seperti kontrol *Submit* biasa.

Mengotomatisasi kontrol formulir di Word dapat menggantikan pekerjaan tata letak manual dan memastikan konsistensi di ratusan dokumen. Pada langkah‑langkah di bawah ini Anda juga akan belajar cara **mengatur teks tombol**, **mengatur nama tombol**, dan **mengatur caption tombol**—semua penting ketika tombol berpartisipasi dalam alur kerja berbasis makro.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* .NET 6.0 (atau lebih baru) terpasang.
* Referensi ke **Aspose.Words for .NET** (perpustakaan yang menyediakan `DocumentBuilder.InsertForms2OleControl`).
* Pengetahuan dasar tentang C# dan kontrol formulir ActiveX di Word.

Anda dapat menginstal Aspose.Words melalui NuGet:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Gunakan versi stabil terbaru Aspose.Words untuk mendapatkan perbaikan bug dan fitur baru terkait kontrol ActiveX.

## Ikhtisar solusi

Tutorial ini dibagi menjadi tiga langkah jelas:

1. **Tambahkan tombol ActiveX** – gunakan metode `InsertForms2OleControl` untuk menempatkan tombol perintah di dokumen.  
2. **Atur nama tombol** – berikan pengidentifikasi programatik unik dengan properti `Name`.  
3. **Atur caption tombol** – tentukan teks yang terlihat pada tombol melalui properti `Caption` (yang juga mengontrol **set button text** yang Anda lihat di UI).

Pada akhir panduan Anda akan memiliki rutinitas **create submit button** yang berfungsi penuh dan dapat digunakan kembali dalam proyek otomatisasi Word apa pun.

## Langkah 1: Tambahkan tombol ActiveX ke dokumen

Tugas pertama adalah **add activex button** ke file Word. Aspose.Words menyediakan enum `Forms2OleControlType.CommandButton` untuk tujuan ini.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load or create a new document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a CommandButton ActiveX control at the cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton);
```

**Mengapa langkah ini penting:**  
Kontrol ActiveX adalah satu‑satunya elemen formulir Word yang dapat mengeksekusi makro VBA atau berinteraksi dengan kode eksternal. Menambahkan kontrol menciptakan placeholder yang dapat dikonfigurasi pada langkah selanjutnya.

> **Edge case:** Jika dokumen sudah berisi kontrol dengan nama yang sama, Word akan secara otomatis mengganti nama yang baru (misalnya, `CommandButton1`). Menetapkan nama secara eksplisit pada langkah berikut menghindari benturan semacam itu.

## Langkah 2: Atur nama tombol

**Set button name** yang dapat diandalkan sangat penting ketika Anda perlu merujuk kontrol dari VBA atau bagian lain kode C# Anda. Properti `Name` memberikan tombol pengidentifikasi programatik.

```csharp
// Assign a unique programmatic name
commandBtn.Name = "btnSubmit";
```

**Mengapa Anda harus mengatur nama:**  
Saat dokumen dibuka, VBA dapat mengambil tombol melalui `ActiveDocument.InlineShapes("btnSubmit")`. Nama yang bermakna seperti `btnSubmit` juga memperjelas maksud saat Anda memeriksa XML dokumen.

> **Pro tip:** Jaga nama tetap pendek, alfanumerik, dan dimulai dengan huruf agar kompatibel dengan aturan penamaan VBA.

## Langkah 3: Atur caption tombol (teks yang terlihat)

Teks yang dilihat pengguna pada tombol dikendalikan oleh properti **set button caption**. Di UI Word ini muncul sebagai label tombol, yang juga merupakan **set button text** yang ingin Anda tampilkan.

```csharp
// Define the text shown on the button
commandBtn.Caption = "Submit";
```

**Mengapa caption penting:**  
Caption adalah label yang dihadapkan ke pengguna. Mengubahnya nanti tidak memengaruhi nama tombol, sehingga Anda dapat melokalisasi UI tanpa merusak kode yang bergantung pada `btnSubmit`.

> **Pertanyaan umum:** *Bisakah saya mengatur sekaligus Caption dan Value?*  
> Untuk `CommandButton`, `Caption` mengontrol label, sementara `Value` tidak digunakan. Jika Anda memerlukan nilai tersembunyi, simpan dalam properti dokumen khusus.

## Contoh lengkap yang berfungsi

Menggabungkan ketiga langkah memberikan Anda rutinitas lengkap yang dapat ditempatkan di aplikasi console atau Windows apa pun:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert the ActiveX command button
        Forms2OleControl commandBtn = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton);

        // 3. Set a meaningful name for later reference
        commandBtn.Name = "btnSubmit";

        // 4. Set the visible caption (this is the button text)
        commandBtn.Caption = "Submit";

        // Optional: position the button (in points)
        commandBtn.Left = 100;   // distance from left margin
        commandBtn.Top = 200;    // distance from top margin
        commandBtn.Width = 80;
        commandBtn.Height = 30;

        // Save the document
        doc.Save("SubmitButton.docx");
        Console.WriteLine("Document with submit button created successfully.");
    }
}
```

### Output yang diharapkan

Menjalankan program akan membuat `SubmitButton.docx`. Saat Anda membuka file tersebut di Microsoft Word:

* Sebuah tombol **Submit** muncul pada lokasi yang ditentukan.
* Nama tombol adalah `btnSubmit` (periksa melalui *Developer → Design Mode → Properties*).
* Mengklik tombol dalam mode desain menampilkan caption *Submit*.

Anda kini memiliki blok bangunan yang dapat dipakai ulang untuk solusi Word berbasis formulir apa pun.

## Pertimbangan tambahan

### Menangani benturan penamaan

Jika Anda menjalankan rutinitas berulang kali pada dokumen yang sama, Word mungkin secara otomatis mengganti nama kontrol duplikat. Untuk menjamin keunikan, Anda dapat menambahkan GUID di depan:

```csharp
commandBtn.Name = $"btnSubmit_{Guid.NewGuid():N}";
```

### Melokalisasi caption tombol

Untuk dokumen multibahasa, simpan caption dalam file sumber daya dan tetapkan pada waktu runtime:

```csharp
commandBtn.Caption = Resources.SubmitButtonLabel;
```

### Menanggapi klik tombol

Tombol itu sendiri tidak berisi logika klik dalam C#. Biasanya Anda melampirkan makro VBA:

```vba
Sub btnSubmit_Click()
    MsgBox "Form submitted!"
End Sub
```

Karena Anda telah **set button name** menjadi `btnSubmit`, nama makro mengikuti konvensi `<Name>_Click` secara otomatis.

## FAQ Pemecahan Masalah

| Question | Answer |
|----------|--------|
| **Mengapa tombol muncul kosong?** | Pastikan Anda mengatur properti `Caption`; tanpa itu tombol tidak menampilkan teks. |
| **Bisakah saya menggunakan kontrol ActiveX lain?** | Ya. Ganti `Forms2OleControlType.CommandButton` dengan `CheckBox`, `OptionButton`, dll., tetapi propertinya berbeda. |
| **Apakah ini kompatibel dengan .NET Core?** | Aspose.Words for .NET mendukung .NET 6+, jadi kode yang sama berfungsi di .NET Core dan .NET Framework. |
| **Bagaimana jika dokumen sudah memiliki tombol?** | Gunakan `Name` yang unik (misalnya tambahkan GUID) untuk menghindari konflik. |

## Kesimpulan

Anda kini tahu cara **create submit button** secara programatis di dokumen Word menggunakan C#. Dengan mengikuti tiga langkah—**add activex button**, **set button name**, dan **set button caption**—Anda dapat secara andal **set button text**, **set button name**, dan **set button caption** untuk solusi formulir otomatis apa pun.  

Selanjutnya Anda dapat mengeksplor:

* Menambahkan makro VBA yang merespons klik **submit button**.
* Menata tombol dengan font atau warna khusus melalui XML yang mendasarinya.
* Menghasilkan beberapa tombol dalam loop untuk formulir dinamis.

Silakan bereksperimen dengan caption, nama, dan posisi yang berbeda agar sesuai dengan alur kerja spesifik Anda. Selamat mengotomatisasi!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}