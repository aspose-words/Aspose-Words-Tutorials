---
category: general
date: 2026-10-20
description: Buat dokumen Word secara programatis dan tambahkan tombol perintah menggunakan
  Aspose.Words. Pelajari cara menyisipkan kontrol ActiveX dan mengatur caption tombol.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add command button
- add activex control
- insert activex button
- set button caption
language: id
lastmod: 2026-10-20
og_description: Buat dokumen Word secara programatis dan sematkan tombol perintah
  ActiveX. Tutorial ini menjelaskan cara menyisipkan kontrol dan mengatur caption‑nya
  dengan Aspose.Words.
og_image_alt: Word file showing an ActiveX command button inserted by Aspose.Words
og_title: Buat dokumen Word secara programatis – tambahkan tombol ActiveX
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  headline: Create Word document programmatically with an ActiveX button
  type: TechArticle
- description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  name: Create Word document programmatically with an ActiveX button
  steps:
  - name: 'Open a terminal or Visual Studio and create a new console project:'
    text: 'Open a terminal or Visual Studio and create a new console project:'
  - name: 'Add the Aspose.Words package:'
    text: 'Add the Aspose.Words package:'
  - name: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
    text: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
  - name: Open `ActiveXCommandButton.docx` in Microsoft Word.
    text: Open `ActiveXCommandButton.docx` in Microsoft Word.
  - name: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
    text: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
  - name: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
    text: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
  - name: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
    text: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Buat dokumen Word secara programatis dengan tombol ActiveX
url: /id/net/working-with-oleobjects-and-activex/create-word-document-programmatically-with-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat Dokumen Word secara programatis dengan tombol ActiveX

Buat dokumen Word secara programatis dengan Aspose.Words, lalu tambahkan tombol perintah yang dapat diklik oleh pengguna. Panduan ini memandu Anda melalui penyisipan kontrol ActiveX, mengonfigurasi propertinya, dan menyimpan hasilnya sebagai file **.docx**.

Anda akan melihat contoh lengkap yang dapat dijalankan yang dapat Anda salin ke aplikasi konsol. Pada akhir tutorial Anda dapat menghasilkan file Word yang berisi tombol perintah yang berfungsi penuh, dan Anda akan memahami cara **add command button**, **add activex control**, **insert activex button**, dan **set button caption** tanpa meninggalkan kode C# Anda.

## Prasyarat

* .NET 6.0 SDK atau yang lebih baru terinstal  
* Visual Studio 2022 (atau IDE kompatibel C# apa pun)  
* File lisensi Aspose.Words untuk .NET (versi percobaan gratis dapat digunakan untuk contoh ini)  
* Pemahaman dasar tentang C# dan sistem proyek .NET  

Tidak ada paket NuGet tambahan yang diperlukan selain **Aspose.Words** karena dukungan ActiveX sudah terintegrasi dalam pustaka.

## Langkah 1: Siapkan proyek dan tambahkan Aspose.Words

1. Buka terminal atau Visual Studio dan buat proyek konsol baru:

   ```bash
   dotnet new console -n WordActiveXDemo
   cd WordActiveXDemo
   ```

2. Tambahkan paket Aspose.Words:

   ```bash
   dotnet add package Aspose.Words
   ```

3. (Opsional) Jika Anda memiliki file lisensi, letakkan di root proyek dan tambahkan baris berikut di awal `Program.cs` untuk menghindari watermark evaluasi:

   ```csharp
   Aspose.Words.License license = new Aspose.Words.License();
   license.SetLicense("Aspose.Words.lic");
   ```

## Langkah 2: Buat dokumen Word secara programatis – inisialisasi dokumen

Operasi pertama adalah **create Word document programmatically**. Anda melakukannya dengan menginstansiasi objek `Document` dan `DocumentBuilder` yang memungkinkan Anda mengedit konten dokumen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;   // Provides ActiveX control types
using System.Drawing;        // For Point and Size structs

// Initialize a new blank document
Document document = new Document();

// DocumentBuilder gives a cursor‑based API for inserting elements
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` mewakili seluruh file, sementara `DocumentBuilder` menjaga kursor yang dapat Anda pindahkan ke lokasi mana pun dalam dokumen. Pemisahan ini menjaga kebersihan API dan memungkinkan Anda **add activex control** nanti tanpa harus mengelola struktur tingkat rendah secara manual.

## Langkah 3: Tambahkan tombol perintah – menyisipkan kontrol ActiveX

Sekarang Anda akan **add command button** dengan menyisipkan kontrol ActiveX tipe `OleControlType.CommandButton`. Metode `InsertForms2OleControl` memerlukan tipe kontrol, lokasi (`Point`), dan ukuran (`Size`).

```csharp
// Define where the button will appear (X = 100 pt, Y = 150 pt)
Point buttonPosition = new Point(100, 150);

// Define the button dimensions (width = 120 pt, height = 30 pt)
Size buttonSize = new Size(120, 30);

// Insert the ActiveX command button at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton, // control type
    buttonPosition,              // position
    buttonSize);                 // size
```

Pemanggilan di atas **insert activex button** ke dalam dokumen pada koordinat tepat yang Anda tentukan. Koordinat diukur dalam poin (1 pt ≈ 1/72 in). Jika Anda memerlukan tombol pada paragraf tertentu, pindahkan dulu kursor builder:

```csharp
builder.Writeln("Click the button below:");
builder.MoveToDocumentEnd(); // places the cursor after the paragraph
```

## Langkah 4: Atur caption tombol – menyesuaikan teks tombol perintah

Tombol tanpa label membingungkan, jadi Anda akan **set button caption** ke sesuatu yang bermakna. Properti `Caption` menentukan teks yang ditampilkan pada tombol, sementara `Name` memberikan kontrol identifier programatik.

```csharp
// Give the button a unique name for later reference
commandButton.Name = "btnSubmit";

// Set the visible text on the button
commandButton.Caption = "Submit";

// Optional: assign a macro name that Word will call when the button is clicked
commandButton.OnClick = "SubmitForm()";
```

Jika Anda kemudian mengekspor dokumen ke format yang mendukung makro (`.docm`), nilai `OnClick` harus cocok dengan nama makro VBA. Untuk `.docx` biasa, properti tersebut disimpan tetapi tidak dijalankan, yang cukup untuk kebanyakan skenario otomasi.

## Langkah 5: Simpan dokumen yang berisi tombol ActiveX

Setelah mengonfigurasi kontrol, Anda dapat **save the document**. Pilih direktori yang Anda miliki akses menulis, dan gunakan ekstensi `.docx` untuk kompatibilitas maksimal.

```csharp
// Replace with your desired output folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ActiveXCommandButton.docx");

// Save the document to disk
document.Save(outputPath);
```

Saat Anda membuka file yang dihasilkan di Microsoft Word, Anda akan melihat tombol berlabel **Submit** pada koordinat yang Anda tentukan. Mengklik tombol di klien desktop akan mencoba menjalankan makro `SubmitForm` (jika ada).

## Langkah 6: Verifikasi hasil dan selesaikan masalah umum

1. Buka `ActiveXCommandButton.docx` di Microsoft Word.  
2. Beralih ke **Design Mode** (tab Developer → **Design Mode**) untuk melihat batas tombol.  
3. Jika tombol tidak muncul, periksa bahwa tab **Developer** diaktifkan dan versi Word Anda mendukung kontrol ActiveX.  
4. Untuk file yang mendukung makro (`.docm`), pastikan nama makro di `OnClick` cocok dengan prosedur VBA; jika tidak, Word akan menampilkan peringatan keamanan.

### Tips Pro

Kontrol ActiveX hanya tersedia di Windows. Jika Anda memerlukan interaktivitas lintas platform, pertimbangkan menggunakan **Content Controls** (`RichTextContentControl`) alih-alih tombol ActiveX.

## Kode sumber lengkap

Berikut adalah program lengkap yang siap dijalankan. Salin ke `Program.cs` dan jalankan `dotnet run`.



## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Dokumen Word dengan Tombol ActiveX – Panduan C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)
- [Tambahkan Tombol Perintah ke Dokumen Word dengan Aspose.Words – Panduan Lengkap](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)
- [buat tombol dokumen word dengan Aspose.Words – Contoh Kode Lengkap](/words/english/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}