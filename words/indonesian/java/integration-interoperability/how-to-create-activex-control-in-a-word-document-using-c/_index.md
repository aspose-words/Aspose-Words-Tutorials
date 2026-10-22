---
category: general
date: 2026-08-20
description: Pelajari cara membuat kontrol ActiveX, mengatur ukuran tombol, dan menambahkan
  tombol ke Word dengan contoh lengkap C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- set button size
- add button to word
- how to insert button
- create clickable button
language: id
lastmod: 2026-08-20
og_description: Buat kontrol ActiveX dalam file Word dengan C#. Tutorial ini menunjukkan
  cara mengatur ukuran tombol, menambahkan tombol ke Word, dan membuat tombol yang
  dapat diklik.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX control
  button
og_title: Buat kontrol ActiveX di Word – panduan langkah demi langkah C#
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  headline: How to create ActiveX control in a Word document using C#
  type: TechArticle
- description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  name: How to create ActiveX control in a Word document using C#
  steps:
  - name: Why this works
    text: '* `InsertForms2OleControl` tells Word to embed an OLE object of type **CommandButton**,
      which is the classic ActiveX button class. * The width and height arguments
      directly **set button size**; Word translates the values from points (1 pt ≈
      1/72 in). * Naming the control (`Name = "btnSubmit"`) makes'
  - name: Pro tip
    text: 'If you want a square button, set both dimensions to the same value:'
  - name: 1. What if the button does not appear after saving?
    text: '* Verify that the Aspose.Words version supports `InsertForms2OleControl`.
      Versions prior to 22.5 lack this feature. * Ensure the target file format is
      `.docx` or `.doc`. Older formats like `.rtf` cannot store ActiveX objects.'
  - name: 2. Can I insert the button at a specific bookmark?
    text: 'Yes. Move the builder to the bookmark before calling `InsertForms2OleControl`:'
  - name: 3. How to **set button size** dynamically based on text length?
    text: Calculate the required width using the `Graphics.MeasureString` method (from
      `System.Drawing`) and convert pixels to points (`points = pixels * 72 / DPI`).
      Then pass the computed width to `InsertForms2OleControl`.
  - name: 4. Is there a way to add multiple buttons in a loop?
    text: 'Absolutely. Wrap the insertion logic in a `for` loop and adjust the `Left`
      and `Top` properties for each iteration:'
  type: HowTo
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
title: Cara membuat kontrol ActiveX dalam dokumen Word menggunakan C#
url: /id/java/integration-interoperability/how-to-create-activex-control-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat kontrol ActiveX dalam dokumen Word menggunakan C#

Jika Anda perlu **membuat kontrol ActiveX** di dalam file Microsoft Word, panduan ini menunjukkan secara tepat cara melakukannya. Anda akan melihat cara **menambahkan tombol ke Word**, mengatur dimensi tombol, dan membuat kontrol dapat diklik—semua dengan program C# singkat yang berdiri sendiri.

Dalam tutorial ini Anda akan:

* Memahami mengapa kontrol ActiveX berguna untuk dokumen Word yang interaktif.  
* Mempelajari kode tepat untuk **mengatur ukuran tombol** dan menetapkan caption.  
* Melihat cara **membuat tombol yang dapat diklik** yang kemudian dapat dihubungkan ke macro atau logika eksternal.  

Langkah‑langkah ini bekerja dengan Aspose.Words .NET 23.12 atau yang lebih baru dan hanya memerlukan lingkungan pengembangan .NET.

> **Prasyarat** – Anda memiliki lisensi Aspose.Words yang valid (atau menggunakan versi evaluasi) dan Visual Studio 2022 atau IDE C# apa pun.

---

## Cara membuat kontrol ActiveX dalam dokumen Word

Langkah pertama adalah menginstansiasi `Document` kosong dan `DocumentBuilder`. Builder menyediakan API tingkat tinggi untuk menyisipkan objek seperti kontrol ActiveX.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document and obtain a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // The rest of the steps are explained in the following sections.
            InsertActiveXButton(builder);

            // Save the result so you can open it in Word.
            doc.Save("ActiveXButton.docx");
            Console.WriteLine("Document saved as ActiveXButton.docx");
        }
```

Metode `InsertActiveXButton` (didefinisikan berikut) berisi logika **cara menyisipkan tombol** dan mengkonfigurasinya.

```csharp
        /// <summary>
        /// Inserts a CommandButton ActiveX control, sets its size, name, and caption.
        /// </summary>
        static void InsertActiveXButton(DocumentBuilder builder)
        {
            // Step 2: Insert a CommandButton ActiveX control with the desired size (width: 100, height: 30).
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                "CommandButton", 100, 30);

            // Step 3: Assign a name to the control for later reference.
            commandButton.Name = "btnSubmit";

            // Step 4: Set the caption that will be displayed on the button.
            commandButton.Caption = "Submit";

            // Optional: Position the button on the page (e.g., 100 points from the top left).
            commandButton.Left = 100;
            commandButton.Top = 150;
        }
    }
}
```

Menjalankan program akan membuat **ActiveXButton.docx**. Membuka file di Word menampilkan tombol berlabel **Submit**. Kontrol berfungsi penuh—mengkliknya akan memicu event standar `CommandButton_Click`, yang kemudian dapat Anda hubungkan ke macro VBA.

### Mengapa ini berhasil

* `InsertForms2OleControl` memberi tahu Word untuk menyematkan objek OLE tipe **CommandButton**, yang merupakan kelas tombol ActiveX klasik.  
* Argumen lebar dan tinggi langsung **mengatur ukuran tombol**; Word menerjemahkan nilai tersebut dari poin (1 pt ≈ 1/72 in).  
* Menamai kontrol (`Name = "btnSubmit"`) memudahkan pencarian dari VBA (`ActiveDocument.InlineShapes("btnSubmit")`).  

---

## Mengatur ukuran tombol dan caption

Jika Anda memerlukan tampilan yang berbeda, sesuaikan argumen numerik pada pemanggilan `InsertForms2OleControl`. Tanda tangan metodenya adalah:

```csharp
Forms2OleControl InsertForms2OleControl(string progId, double width, double height);
```

* **progId** – Identifier programatik kelas ActiveX (`"CommandButton"` untuk tombol standar).  
* **width / height** – Ukuran dalam poin. Untuk tombol lebar 2 cm, gunakan `width = 56.7` (2 cm ≈ 56.7 pt).  

Anda juga dapat mengubah caption setelah penyisipan:

```csharp
commandButton.Caption = "Send Request";
```

Mengubah caption tidak memengaruhi ukuran, tetapi memengaruhi umpan balik visual bagi pengguna.

### Tips profesional

Jika Anda menginginkan tombol berbentuk kotak, atur kedua dimensi ke nilai yang sama:

```csharp
Forms2OleControl squareBtn = builder.InsertForms2OleControl("CommandButton", 50, 50);
squareBtn.Caption = "OK";
```

---

## Menambahkan tombol ke Word dan membuatnya dapat diklik

Kode di atas sudah **menambahkan tombol ke Word**. Untuk membuat tombol melakukan aksi, Anda harus menulis macro VBA yang menangani event `Click`. Berikut macro minimal yang dapat Anda tempelkan ke editor VBA Word (`Alt+F11` → Insert → Module):

```vba
Sub btnSubmit_Click()
    MsgBox "You clicked the Submit button!", vbInformation
End Sub
```

Karena kontrol bernama `btnSubmit`, Word secara otomatis memetakan event `Click` ke `btnSubmit_Click`. Inilah cara standar untuk **membuat tombol yang dapat diklik** tanpa pustaka eksternal.

> **Catatan:** Pengaturan keamanan macro di Word dapat memblokir kontrol ActiveX. Pastikan “Enable all macros” atau “Enable VBA macros” dipilih untuk dokumen, atau tanda tangani macro secara digital untuk penggunaan produksi.

---

## Pertanyaan umum: cara menyisipkan tombol dan pemecahan masalah

### 1. Bagaimana jika tombol tidak muncul setelah disimpan?

* Pastikan versi Aspose.Words mendukung `InsertForms2OleControl`. Versi sebelum 22.5 tidak memiliki fitur ini.  
* Pastikan format file target adalah `.docx` atau `.doc`. Format lama seperti `.rtf` tidak dapat menyimpan objek ActiveX.

### 2. Bisakah saya menyisipkan tombol pada bookmark tertentu?

Ya. Pindahkan builder ke bookmark sebelum memanggil `InsertForms2OleControl`:

```csharp
builder.MoveToBookmark("InsertHere");
builder.InsertForms2OleControl("CommandButton", 100, 30);
```

### 3. Bagaimana cara **mengatur ukuran tombol** secara dinamis berdasarkan panjang teks?

Hitung lebar yang diperlukan menggunakan metode `Graphics.MeasureString` (dari `System.Drawing`) dan konversi piksel ke poin (`points = pixels * 72 / DPI`). Kemudian berikan lebar yang dihitung ke `InsertForms2OleControl`.

### 4. Apakah ada cara menambahkan beberapa tombol dalam loop?

Tentu. Bungkus logika penyisipan dalam `for` loop dan sesuaikan properti `Left` dan `Top` untuk setiap iterasi:

```csharp
for (int i = 0; i < 3; i++)
{
    Forms2OleControl btn = builder.InsertForms2OleControl("CommandButton", 80, 25);
    btn.Name = $"btnOption{i + 1}";
    btn.Caption = $"Option {i + 1}";
    btn.Left = 50;
    btn.Top = 100 + i * 40; // stagger vertically
}
```

---

## Output yang diharapkan

Saat Anda menjalankan program dan membuka **ActiveXButton.docx**:

* Sebuah tombol **Submit** tunggal muncul di dekat kiri‑atas halaman pertama.  
* Ukuran tombol sesuai dengan dimensi yang Anda berikan (`100 pt × 30 pt`).  
* Jika Anda menambahkan macro VBA, mengklik tombol akan menampilkan kotak pesan: “You clicked the Submit button!”.

Anda kini berhasil **membuat kontrol ActiveX**, **mengatur ukuran tombol**, dan **menambahkan tombol ke Word** sekaligus belajar **cara menyisipkan tombol** serta **membuat tombol yang dapat diklik** untuk tugas otomasi di masa mendatang.

---

## Kesimpulan

Dalam tutorial ini Anda belajar cara **membuat kontrol ActiveX** di dalam dokumen Word dengan C#. Dengan mengikuti langkah‑langkah tersebut Anda dapat **mengatur ukuran tombol**, memberi kontrol nama yang bermakna, dan **menambahkan tombol ke Word** sehingga menjadi **tombol yang dapat diklik** yang terhubung ke macro VBA.  

Selanjutnya Anda dapat menjelajahi:

* Menghubungkan tombol ke add‑in COM .NET alih‑alih VBA.  
* Menggunakan kelas ActiveX lain seperti `CheckBox` atau `ComboBox`.  
* Mengotomatiskan pembuatan formulir lengkap dengan banyak kontrol.

Silakan bereksperimen dengan ukuran yang berbeda


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Create Word Document with Floating Image in .NET](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Accessible PDF from Word – Complete Guide](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}