---
category: general
date: 2026-09-11
description: Pelajari cara membuat forms2olecontrol dalam kode menggunakan Aspose.Words
  DocumentBuilder. Panduan langkah demi langkah ini mencakup penyisipan tombol perintah
  ActiveX, penggunaan setOleClassName, dan pengaturan ukuran.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create forms2olecontrol in code
- ActiveX command button
- Aspose.Words DocumentBuilder
- setOleClassName method
- Forms2OleControl size
language: id
lastmod: 2026-09-11
og_description: Buat forms2olecontrol dalam kode dengan Aspose.Words. Ikuti panduan
  ini untuk menyisipkan tombol perintah ActiveX, mengatur nama kelasnya, dan menyesuaikan
  ukurannya.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX command
  button inserted via code
og_title: Buat forms2olecontrol dalam kode – panduan lengkap Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  headline: How to create forms2olecontrol in code with Aspose.Words
  type: TechArticle
- description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  name: How to create forms2olecontrol in code with Aspose.Words
  steps:
  - name: Initialise the DocumentBuilder
    text: The `DocumentBuilder` class is the entry point for most document‑generation
      tasks in Aspose.Words. It gives you methods to add text, images, tables, and,
      importantly for this tutorial, OLE controls.
  - name: Insert the Forms2OleControl
    text: The `insertForms2OleControl` method returns a `Forms2OleControl` object.
      This object represents the OLE control placeholder that Word will render as
      an ActiveX button.
  - name: Specify the ActiveX class with setOleClassName
    text: Word needs to know which type of ActiveX control to render. The class name
      for a standard command button is `"Forms.CommandButton.1"`.
  - name: Adjust the Forms2OleControl size
    text: A button that is too small or too large looks unprofessional. You can control
      its dimensions with `setWidth` and `setHeight`.
  - name: Save the document and test
    text: After configuring the control, save the document to a location of your choice.
  - name: When to use Forms2OleControl vs. Content Controls
    text: If you only need simple data entry (e.g., a plain text field), Word’s built‑in
      content controls are lighter weight. Use `Forms2OleControl` when you require
      full ActiveX functionality such as event handling or custom VBA interaction.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Cara membuat forms2olecontrol dalam kode dengan Aspose.Words
url: /id/java/using-document-elements/how-to-create-forms2olecontrol-in-code-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat forms2olecontrol dalam kode dengan Aspose.Words

Jika Anda perlu **membuat forms2olecontrol dalam kode**, panduan ini menunjukkan secara tepat cara melakukannya menggunakan Aspose.Words .NET API. Baik Anda mengotomatisasi template yang memerlukan tombol perintah ActiveX atau sekadar ingin memperkaya dokumen Word secara programatis, langkah‑langkah di bawah ini mencakup semuanya mulai dari menyisipkan kontrol hingga mengonfigurasi tampilannya.

Dalam tutorial ini Anda akan belajar cara menggunakan **Aspose.Words DocumentBuilder** untuk menyisipkan **ActiveX command button**, mengatur kelasnya dengan **setOleClassName method**, dan menyesuaikan **Forms2OleControl size**-nya. Tidak diperlukan alat eksternal—hanya lingkungan pengembangan .NET dan pustaka Aspose.Words.

## Prasyarat

* .NET 6.0 atau yang lebih baru terpasang (kode juga berfungsi dengan .NET Framework 4.7+)
* Versi terbaru paket NuGet Aspose.Words untuk .NET
* Familiaritas dasar dengan C# dan konsep kontrol ActiveX dalam dokumen Word

Jika ada yang belum terpasang, instal paket NuGet dengan:

```bash
dotnet add package Aspose.Words
```

## Apa yang dibahas dalam tutorial ini

* Membuat instance `DocumentBuilder`
* Menyisipkan `Forms2OleControl` (objek dasar untuk tombol perintah ActiveX)
* Menetapkan nama kelas yang tepat dengan `setOleClassName`
* Mengatur lebar dan tinggi visual menggunakan properti **Forms2OleControl size**
* Menyimpan dokumen dan memverifikasi hasilnya

Pada akhir panduan, Anda akan memiliki file Word yang berfungsi penuh berisi tombol yang dapat diklik, yang dapat Anda sesuaikan lebih lanjut atau hubungkan ke makro VBA.

---

## Cara membuat forms2olecontrol dalam kode – langkah demi langkah

### Langkah 1: Inisialisasi DocumentBuilder

Kelas `DocumentBuilder` adalah titik masuk untuk sebagian besar tugas pembuatan dokumen di Aspose.Words. Ia menyediakan metode untuk menambahkan teks, gambar, tabel, dan, yang penting untuk tutorial ini, kontrol OLE.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Initialise the builder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Mengapa ini penting:**  
`DocumentBuilder` mempertahankan posisi kursor saat ini di dalam dokumen. Dengan membuatnya lebih awal, Anda memastikan bahwa setiap penyisipan berikutnya—seperti **ActiveX command button**—muncul tepat di tempat yang Anda inginkan.

### Langkah 2: Sisipkan Forms2OleControl

Metode `insertForms2OleControl` mengembalikan objek `Forms2OleControl`. Objek ini mewakili placeholder kontrol OLE yang akan dirender Word sebagai tombol ActiveX.

```csharp
// Insert the Forms2OleControl at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

**Mengapa ini penting:**  
Tanpa pemanggilan ini Anda tidak dapat memanipulasi properti kontrol. `Forms2OleControl` yang dikembalikan memberi Anda akses penuh ke **setOleClassName method**, atribut ukuran, dan pengaturan spesifik OLE lainnya.

### Langkah 3: Tentukan kelas ActiveX dengan setOleClassName

Word perlu mengetahui jenis kontrol ActiveX yang akan dirender. Nama kelas untuk tombol perintah standar adalah `"Forms.CommandButton.1"`.

```csharp
// Tell Word that this OLE control is a CommandButton
commandButton.SetOleClassName("Forms.CommandButton.1");
```

**Mengapa ini penting:**  
Metode `setOleClassName` adalah jembatan antara placeholder OLE generik dan **ActiveX command button** yang konkret. Menggunakan nama kelas yang salah menghasilkan objek kosong atau kesalahan runtime saat dokumen dibuka.

### Langkah 4: Sesuaikan ukuran Forms2OleControl

Tombol yang terlalu kecil atau terlalu besar terlihat tidak profesional. Anda dapat mengontrol dimensinya dengan `setWidth` dan `setHeight`.

```csharp
// Set the visual dimensions (points) of the button
commandButton.SetWidth(80);   // width in points
commandButton.SetHeight(30);  // height in points
```

**Mengapa ini penting:**  
Properti ini membentuk **Forms2OleControl size**. Mereka memengaruhi tampilan tombol di UI Word dan memastikan bahwa makro yang terlampir memiliki area yang cukup untuk diklik.

### Langkah 5: Simpan dokumen dan uji

Setelah mengonfigurasi kontrol, simpan dokumen ke lokasi pilihan Anda.

```csharp
// Save the document as a .docx file
doc.Save("ActiveXButton.docx");
```

Buka `ActiveXButton.docx` di Microsoft Word. Anda akan melihat tombol berlabel “CommandButton1” (caption default). Mengkliknya tidak akan melakukan apa‑apa kecuali Anda menambahkan makro VBA, tetapi kontrol itu sendiri berfungsi penuh.

**Output yang diharapkan:**  

![Dokumen Word dengan tombol perintah ActiveX yang disisipkan](/images/activeX-button.png "Tangkapan layar dokumen Word yang menampilkan tombol ActiveX baru yang disisipkan melalui kode")

*Teks alt gambar berisi kata kunci utama untuk aksesibilitas dan SEO.*

---

## Memahami kelas ActiveX Forms2OleControl

Kelas `Forms2OleControl` membungkus infrastruktur OLE tingkat rendah yang digunakan Word untuk elemen ActiveX. Ia mewarisi dari `Shape`, yang berarti Anda juga dapat menerapkan pemformatan shape tipikal (mis., border, rotasi) bila diperlukan.

* **ActiveX command button** – Kasus penggunaan paling umum; Anda dapat menghubungkannya ke makro melalui alat pengembang Word.
* **setOleClassName method** – Menentukan kelas COM mana yang dimuat Word; nilai valid lainnya termasuk `"Forms.TextBox.1"` dan `"Forms.ComboBox.1"`.
* **Forms2OleControl size** – Dikontrol melalui `SetWidth`/`SetHeight`. Metode ini menerima satuan poin (1 pt = 1/72 in).

### Kapan menggunakan Forms2OleControl vs. Content Controls

Jika Anda hanya membutuhkan entri data sederhana (mis., bidang teks biasa), kontrol konten bawaan Word lebih ringan. Gunakan `Forms2OleControl` ketika Anda memerlukan fungsionalitas ActiveX lengkap seperti penanganan event atau interaksi VBA khusus.

---

## Menetapkan properti tambahan (opsional)

Meskipun langkah‑langkah inti sudah cukup untuk **membuat forms2olecontrol dalam kode**, Anda sering ingin menyempurnakan tampilan atau perilaku tombol.

```csharp
// Change the button caption (requires a VBA macro to read it)
commandButton.SetOleData("Caption", "Submit");

// Disable the button initially
commandButton.SetOleData("Enabled", false);

// Add a tooltip
commandButton.SetOleData("ToolTipText", "Click to submit the form");
```

**Mengapa ini penting:**  
`SetOleData` memungkinkan Anda menulis nilai properti sewenang-wenang langsung ke dalam aliran OLE. Ini adalah cara paling fleksibel untuk menyesuaikan **ActiveX command button** tanpa harus menggunakan VBA.

---

## Kesulitan umum dan pemecahan masalah

| Gejala | Penyebab kemungkinan | Solusi |
|--------|----------------------|--------|
| Tombol muncul sebagai kotak abu‑abu | Nama kelas yang salah diberikan ke `setOleClassName` | Pastikan string persis `"Forms.CommandButton.1"` (case‑sensitive) |
| Ukuran tidak berubah | Width/Height diatur sebelum menyisipkan kontrol | Selalu panggil `SetWidth`/`SetHeight` **setelah** `InsertForms2OleControl` |
| Dokumen menampilkan error “OLE object not found” saat dibuka | Lisensi Aspose.Words tidak ada (versi evaluasi mungkin membatasi OLE) | Terapkan lisensi yang valid atau gunakan trial gratis dengan dukungan OLE penuh |
| Caption tombol tetap “CommandButton1” | `SetOleData` tidak digunakan atau makro tidak membaca properti | Gunakan makro VBA untuk membaca properti `"Caption"` atau atur caption melalui UI Word |

---

## Contoh lengkap yang dapat dijalankan

Berikut adalah aplikasi konsol lengkap yang dapat Anda salin, tempel, dan jalankan. Ini mendemonstrasikan semua yang dibahas dalam tutorial ini.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace Forms2OleControlDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1. Create a new document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2. Insert the Forms2OleControl (ActiveX placeholder)
            Forms2OleControl commandButton = builder.InsertForms2OleControl();

            // 3. Set the ActiveX class to CommandButton
            commandButton.SetOleClassName("Forms.CommandButton.1");

            // 4. Define the visual size of the button
            commandButton.SetWidth(80);   // 80 points = ~1.11 inches
            commandButton.SetHeight(30);  // 30 points = ~0.42 inches

            // Optional: set a custom caption via OLE data (requires VBA to read)
            commandButton.SetOleData("Caption", "Submit");

            // 5. Save the document
            string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Penjelasan setiap bagian**

* **Using directives** – Mengimpor namespace Aspose.Words yang diperlukan untuk `Document`, `DocumentBuilder`, dan `Forms2OleControl`.
* **Document creation** – Membuat file Word kosong.
* **InsertForms2OleControl** – Menempatkan kontrol OLE pada kursor builder saat ini.
* **SetOleClassName** – Memberitahu Word bahwa kontrol tersebut adalah **ActiveX command button**.
* **SetWidth / SetHeight** – Menyesuaikan **Forms2OleControl size** untuk tampilan profesional.
* **SetOleData (optional)** – Menunjukkan cara menulis properti tambahan seperti caption.
* **Save** – Menulis file `.docx` akhir ke disk.

Jalankan program (`dotnet run`) dan buka `ActiveXButton.docx`. Anda akan melihat tombol yang kemudian dapat Anda hubungkan ke makro.

---

## Kesimpulan

Anda kini tahu cara **membuat forms2olecontrol dalam kode** menggunakan Aspose.Words, mulai dari menginisialisasi `DocumentBuilder` hingga mengonfigurasi **ActiveX command button** dengan `setOleClassName` dan mengendalikan **Forms2OleControl size**‑nya. Pendekatan ini memungkinkan Anda mengotomatisasi dokumen Word yang kompleks, menyematkan elemen UI interaktif, dan menjaga semua logika di dalam

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara membuat bidang formulir dan menambahkan konten menggunakan DocumentBuilder di Aspose.Words untuk Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Membuat Group Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Membuat shape persegi panjang di Word dengan Aspose.Words – Panduan langkah demi langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}