---
category: general
date: 2026-08-07
description: Pelajari cara menambahkan kontrol ActiveX dalam dokumen Word menggunakan
  C#. Termasuk mengaitkan makro dengan tombol dan menambahkan contoh tombol yang dapat
  diklik di Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex control
- associate macro with button
- add clickable button word
- add command button word
language: id
lastmod: 2026-08-07
og_description: cara menambahkan kontrol activex dalam dokumen Word menggunakan Aspose.Words.
  Ikuti panduan ini untuk menyisipkan tombol, mengaitkan makro dengan tombol, dan
  menambahkan kata tombol yang dapat diklik.
og_image_alt: Screenshot showing a Word document with an ActiveX command button inserted
  via Aspose.Words
og_title: cara menambahkan kontrol ActiveX di Word – tutorial lengkap C#
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  headline: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  name: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  steps:
  - name: Why each line matters
    text: '| Line | Purpose | |------|---------| | `Document doc = new Document();`
      | Instantiates a fresh Word package in memory. | | `DocumentBuilder builder
      = new DocumentBuilder(doc);` | Provides a fluent API for inserting content,
      including ActiveX controls. | | `InsertForms2OleControl` | The only Aspose.'
  - name: Common pitfalls when associating a macro
    text: '* **Macro security settings** – If the document is opened on a machine
      with strict security policies, the macro may be blocked. Provide instructions
      to lower the security level or sign the macro. * **Naming conflicts** – The
      macro name must be unique within the document’s VBA project; otherwise Word'
  - name: 'Edge case: Long captions'
    text: Word truncates captions that exceed the button’s width. To avoid clipping,
      either increase the width argument in `InsertForms2OleControl` or shorten the
      text. Testing with different languages (e.g., German or Japanese) is advisable
      because character width varies.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Cara menambahkan kontrol ActiveX di Word dengan Aspose.Words – panduan langkah
  demi langkah
url: /id/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cara menambahkan kontrol activex di Word dengan Aspose.Words

Jika Anda perlu **cara menambahkan kontrol activex** dalam file Microsoft Word secara programatis, tutorial ini menunjukkan langkah‑langkah tepat menggunakan Aspose.Words untuk .NET. Anda akan melihat cara menyisipkan tombol perintah, mengatur caption‑nya, dan **mengaitkan makro dengan tombol** sehingga kontrol bereaksi ketika pengguna mengkliknya. Pada akhir tutorial Anda akan memiliki file `.docm` yang mendukung makro dan berisi tombol yang berfungsi penuh.

Menambahkan tombol ActiveX adalah kebutuhan umum saat membuat templat interaktif seperti formulir aplikasi pinjaman, formulir orientasi karyawan, atau laporan otomatis. Panduan ini menelusuri setiap baris kode, menjelaskan **mengapa** setiap langkah penting, dan mencakup jebakan umum yang mungkin Anda temui.

## Prasyarat

* .NET 6 (atau .NET Core 3.1 / .NET Framework 4.8) terpasang.
* Lisensi Aspose.Words untuk .NET yang valid atau kunci evaluasi sementara.
* Visual Studio 2022 (atau IDE apa pun yang mendukung C#).
* Familiaritas dasar dengan makro Word (VBA) jika Anda berencana menulis makro yang akan dipicu oleh tombol.

> **Pro tip:** Saat menjalankan contoh, simpan output ke folder yang Anda miliki izin menulis, jika tidak `doc.Save` akan melempar pengecualian.

## Cara menambahkan kontrol ActiveX dalam dokumen Word menggunakan Aspose.Words

Inti solusi adalah program C# singkat yang membuat dokumen baru, menyisipkan kontrol ActiveX **CommandButton**, dan menyimpan file sebagai dokumen yang mendukung makro (`.docm`). Kode lengkap dan siap untuk disalin‑tempel.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert an ActiveX CommandButton control (Forms2OleControl)
        // Parameters: control type, left, top, width, height (in points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            0,   // left position (points)
            0,   // top position (points)
            150, // width (points)
            30   // height (points)
        );

        // Step 3: Set the button's visible caption – this is the add clickable button word
        commandButton.Caption = "Click Me";

        // Step 4 (optional): Associate a macro with the button's click action
        // This demonstrates how to associate macro with button
        commandButton.OnAction = "MyMacro";

        // Step 5: Save the document as a macro‑enabled file to preserve the button reference
        // The file extension .docm tells Word to keep ActiveX controls and macros
        doc.Save("CommandButton.docm");
    }
}
```

### Mengapa setiap baris penting

| Baris | Tujuan |
|------|--------|
| `Document doc = new Document();` | Membuat instance paket Word baru di memori. |
| `DocumentBuilder builder = new DocumentBuilder(doc);` | Menyediakan API fluent untuk menyisipkan konten, termasuk kontrol ActiveX. |
| `InsertForms2OleControl` | Satu‑satunya metode Aspose.Words yang membuat kontrol ActiveX; Anda menentukan tipe kontrol (`CommandButton`) dan geometri‑nya. |
| `commandButton.Caption = "Click Me";` | Mengatur **teks tombol yang dapat diklik** yang dilihat pengguna akhir. Tanpa caption tombol akan terlihat kosong. |
| `commandButton.OnAction = "MyMacro";` | **mengaitkan makro dengan tombol** – memberi tahu Word makro VBA mana yang dijalankan saat kontrol diklik. |
| `doc.Save("CommandButton.docm");` | Menyimpan dokumen sebagai file yang mendukung makro; file `.docx` biasa akan menghapus kontrol dan makro. |

> **Catatan:** Koordinat (kiri, atas) diukur dalam poin (1 pt ≈ 1/72 in). Sesuaikan untuk menempatkan tombol di lokasi yang Anda inginkan pada halaman.

## Cara mengaitkan makro dengan tombol

Properti `OnAction` menghubungkan tombol ke makro VBA bernama `MyMacro`. Anda tetap harus membuat makro tersebut di dalam file Word, baik secara manual maupun dengan menyuntikkan kode VBA secara programatis (Aspose.Words tidak menulis kode VBA). Berikut makro minimal yang dapat Anda tambahkan menggunakan editor **Developer → Visual Basic** di Word:

```vba
Sub MyMacro()
    MsgBox "Button clicked!", vbInformation, "ActiveX Demo"
End Sub
```

Saat pengguna membuka `CommandButton.docm` dan mengklik tombol, Word mengeksekusi `MyMacro` dan menampilkan kotak pesan. Jika keamanan makro diatur ke **Disable all macros without notification**, tombol akan muncul dalam keadaan non‑aktif. Sarankan pengguna untuk mengaktifkan makro pada dokumen atau menandatangani makro dengan sertifikat tepercaya.

### Kesulitan umum saat mengaitkan makro

* **Pengaturan keamanan makro** – Jika dokumen dibuka pada mesin dengan kebijakan keamanan ketat, makro dapat diblokir. Berikan instruksi untuk menurunkan tingkat keamanan atau menandatangani makro.
* **Konflik penamaan** – Nama makro harus unik dalam proyek VBA dokumen; jika tidak Word akan menampilkan error “duplicate procedure name”.
* **Word 64‑bit vs 32‑bit** – Kontrol ActiveX berfungsi sama, tetapi editor VBA mungkin menampilkan pesan peringatan yang berbeda tergantung versi Office.

## Cara menambahkan teks tombol yang dapat diklik ke formulir Word

Properti `Caption` adalah apa yang dilihat pengguna pada tombol. Anda dapat menyesuaikannya lebih lanjut:

```csharp
commandButton.Caption = "Submit Form";
commandButton.Font.Size = 10;      // Adjust font size
commandButton.Font.Name = "Arial"; // Choose a readable font
```

Jika Anda memerlukan caption yang berubah secara dinamis berdasarkan input pengguna, Anda dapat mengakses kontrol tersebut nanti melalui model objek Word:

```vba
Sub UpdateButtonCaption()
    Dim btn As InlineShape
    Set btn = ActiveDocument.InlineShapes(1).OLEFormat.Object
    btn.Caption = "Updated Text"
End Sub
```

### Kasus khusus: Caption panjang

Word memotong caption yang melebihi lebar tombol. Untuk menghindari pemotongan, tingkatkan argumen lebar pada `InsertForms2OleControl` atau perpendek teksnya. Pengujian dengan bahasa lain (misalnya Jerman atau Jepang) disarankan karena lebar karakter dapat bervariasi.

## Cara menambahkan teks tombol perintah untuk otomatisasi formulir

Selain caption visual, konsep **add command button word** mencakup nama programatik kontrol. Aspose.Words tidak menyediakan properti `Name` langsung untuk kontrol ActiveX, tetapi Anda dapat mengatur bidang `AltText`, yang diperlakukan Word sebagai identifier kontrol:

```csharp
commandButton.AltText = "SubmitButton";
```

Nanti di VBA Anda dapat merujuk tombol tersebut melalui nilai `AltText`‑nya:

```vba
Sub FindButton()
    Dim shp As Shape
    For Each shp In ActiveDocument.Shapes
        If shp.AlternativeText = "SubmitButton" Then
            MsgBox "Found the Submit button!"
        End If
    Next shp
End Sub
```

Teknik ini berguna ketika Anda memiliki banyak tombol dan perlu membedakannya secara programatik.

## Contoh lengkap yang berfungsi

Berikut program lengkap yang dapat Anda kompilasi dan jalankan sebagai aplikasi konsol. Program ini mencakup styling opsional, pengaitan makro, dan blok komentar yang menjelaskan setiap langkah.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class AddActiveXButton
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert an ActiveX CommandButton.
        //    left=50pt, top=100pt places the button away from the margin.
        Forms2OleControl btn = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            50,   // left
            100,  // top
            200,  // width
            40    // height
        );

        // 3️⃣ Add clickable button word (caption) and style it.
        btn.Caption = "Submit Form";
        btn.Font.Size = 11;
        btn.Font.Name = "Calibri";

        // 4️⃣ Associate macro with button – this is how to associate macro with button.
        btn.OnAction = "SubmitMacro";

        // 5️⃣ Give the control a friendly identifier (add command button word).
        btn.AltText = "SubmitButton";

        // 6️⃣ Save as macro‑enabled document.
        doc.Save("SubmitForm.docm");
    }
}
```

**Hasil yang diharapkan:** Membuka `SubmitForm.docm` di Microsoft Word menampilkan tombol berbingkai biru dengan label *Submit Form*. Mengklik tombol memicu makro VBA `SubmitMacro` (asalkan Anda telah menambahkan makro ke dokumen). Tombol dapat dipindahkan, diubah ukuran, atau diberi gaya lebih lanjut menggunakan objek `Forms2OleControl` yang sama.

## Menguji solusi

1. Bangun dan jalankan aplikasi konsol C#.
2. Buka `SubmitForm.docm` yang dihasilkan di Word.
3. Jika diminta, aktifkan makro.
4. Klik tombol *Submit Form* – Anda akan melihat kotak pesan yang didefinisikan dalam `SubmitMacro`.

Jika tombol muncul tetapi tidak berfungsi, periksa kembali bahwa nama makro persis sama (`SubmitMacro`) dan bahwa keamanan makro tidak memblokir eksekusi.

## Pertanyaan yang sering diajukan

| Pertanyaan | Jawaban |
|------------|---------|
| *Bisakah saya menambahkan lebih dari satu tombol ActiveX?* | Ya. Panggil `InsertForms2OleControl` beberapa kali dengan koordinat berbeda. Gunakan nilai `OnAction` dan `AltText` yang berbeda untuk membedakannya. |
| *Apakah kontrol ActiveX terlihat di Word Online?* | Tidak. |

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Tambahkan Konten Menggunakan Document Builder di Aspose.Words untuk .NET](/words/english/net/add-content-using-document-builder/)
- [Tutorial Bayangan Bentuk Aspose.Words – Tambahkan Bayangan ke Bentuk Word dalam C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Tambahkan Seksi Baru ke Dokumen Word | Aspose.Words untuk .NET](/words/english/net/document-sections/add-section/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}