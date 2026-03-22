---
category: general
date: 2026-03-22
description: Buat bentuk persegi panjang di C# dan tambahkan bayangan ke bentuk dengan
  Aspose.Words. Pelajari cara menambahkan bayangan, cara membuat persegi panjang,
  dan cara mengatur properti bayangan.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- how to add shadow
- how to create rectangle
- how to set shadow
language: id
og_description: Buat bentuk persegi panjang di C# dan tambahkan bayangan ke bentuk
  menggunakan Aspose.Words. Panduan langkah demi langkah yang mencakup cara menambahkan
  bayangan, cara membuat persegi panjang, dan cara mengatur bayangan.
og_title: Buat bentuk persegi panjang dengan bayangan di C# – Panduan Lengkap
tags:
- Aspose.Words
- C#
- Document Automation
title: Buat bentuk persegi panjang dengan bayangan di C# menggunakan Aspose.Words
url: /id/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat bentuk persegi panjang dengan bayangan di C# menggunakan Aspose.Words

Pernah perlu **membuat bentuk persegi panjang** dalam dokumen Word tetapi tidak yakin cara memberi bayangan drop‑shadow yang halus? Anda tidak sendirian—banyak pengembang mengalami hal ini saat pertama kali mencoba otomatisasi dokumen. Dalam panduan ini kami akan menunjukkan cara **menambahkan bayangan ke bentuk** menggunakan Aspose.Words, dan kami juga akan menjawab “**cara menambahkan bayangan**”, “**cara membuat persegi panjang**”, dan “**cara mengatur bayangan**” sepanjang jalan.

Kami akan memulai dengan `Document` kosong, menggambar persegi panjang, mengaktifkan bayangannya, menyesuaikan blur, jarak, sudut, dan warna, lalu menyimpan file. Pada akhir tutorial Anda akan memiliki file `.docx` siap pakai yang menampilkan persegi panjang berwarna abu‑abu mengambang tepat di atas halaman. Tidak ada misteri, hanya kode sederhana yang dapat Anda salin‑tempel ke proyek .NET mana pun.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki:

* **Aspose.Words for .NET** (versi terbaru per Maret 2026). Anda dapat mengunduhnya dari NuGet dengan `Install-Package Aspose.Words`.
* Lingkungan pengembangan .NET – Visual Studio, Rider, atau bahkan VS Code dengan ekstensi C# sudah cukup.
* Pengetahuan dasar C# – tidak perlu hal yang rumit, cukup kemampuan membuat aplikasi console atau WinForms.

Itu saja. Tidak ada pustaka tambahan, tidak ada langkah tersembunyi. Siap? Mari kita mulai.

## Langkah 1: Inisialisasi dokumen kosong baru

Untuk **membuat bentuk persegi panjang**, pertama‑tama kita memerlukan sebuah wadah – objek `Document` – yang mewakili file Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new empty document
Document document = new Document();
```

Kelas `Document` adalah titik masuk untuk semua yang dilakukan Aspose.Words. Anggaplah sebagai kanvas kosong; tanpa itu Anda tidak dapat menambahkan bentuk, tabel, atau teks apa pun.

## Langkah 2: Buat persegi panjang yang akan menampung bayangan

Sekarang kita akan **cara membuat persegi panjang** dengan menginstansiasi `Shape` bertipe `Rectangle`. Kami juga mengatur ukurannya dalam poin (1 poin ≈ 1/72 inci).

```csharp
// Step 2: Create a rectangular shape that will hold the shadow
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points
rectangleShape.Height = 100; // height in points
```

Mengapa memilih 200 × 100 poin? Itu ukuran yang cukup untuk demo – cukup besar untuk melihat bayangan dengan jelas, namun tidak terlalu besar sehingga memenuhi halaman. Silakan sesuaikan angka‑angka ini sesuai tata letak Anda.

## Langkah 3: Aktifkan efek bayangan dan konfigurasikan tampilannya

Berikut inti tutorial: **cara menambahkan bayangan** dan **cara mengatur bayangan**. Aspose.Words menyediakan objek `Shadow` pada setiap bentuk, memungkinkan Anda mengaktifkan efek dan menyesuaikan parameter visual.

```csharp
// Step 3: Enable the shadow effect and configure its appearance
rectangleShape.Shadow.Enabled    = true;                     // turn the shadow on
rectangleShape.Shadow.BlurRadius = 5;                       // blur radius in pixels
rectangleShape.Shadow.Distance   = 8;                       // distance from the shape in pixels
rectangleShape.Shadow.Angle      = 45;                      // direction of the light source (degrees)
rectangleShape.Shadow.Color      = System.Drawing.Color.Gray; // shadow color
```

* **BlurRadius** melunakkan tepi – nilai yang lebih tinggi membuat bayangan tampak lebih tersebar.
* **Distance** memindahkan bayangan lebih jauh dari persegi panjang.
* **Angle** menentukan arah cahaya; 45° memberikan bayangan diagonal yang alami.
* **Color** memungkinkan Anda memilih warna `System.Drawing.Color` apa pun. Abu‑abu adalah nilai default yang aman, tetapi Anda dapat menggunakan `Color.Black` untuk tampilan tegas atau `Color.LightGray` untuk kesan lembut.

Tips profesional: Jika Anda mengatur `Enabled = false`, semua pengaturan bayangan lainnya diabaikan, jadi selalu periksa flag tersebut.

## Langkah 4: Sisipkan bentuk ke dalam badan dokumen

Setelah persegi panjang siap dan bayangannya dikonfigurasi, kita perlu menempatkannya ke dalam dokumen. Cara termudah adalah menambahkan bentuk ke paragraf pertama pada bagian pertama.

```csharp
// Step 4: Insert the shape into the first paragraph of the document body
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

Jika dokumen Anda sudah berisi teks, Anda dapat menemukan `Paragraph` tertentu atau bahkan sel `Table` dan menyisipkan bentuk di sana. Metode `AppendChild` serbaguna – ia bekerja dengan tipe `Node` apa pun.

## Langkah 5: Simpan dokumen dan verifikasi hasilnya

Akhirnya, kita menulis file ke disk. Ubah jalur sesuai keinginan Anda; folder harus ada, jika tidak Anda akan mendapatkan pengecualian.

```csharp
// Step 5: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowedRectangle.docx");
```

Buka `ShadowedRectangle.docx` yang dihasilkan di Microsoft Word (atau LibreOffice) dan Anda akan melihat persegi panjang abu‑abu dengan bayangan diagonal yang tajam mengarah ke kanan‑bawah. Jika bayangan terlihat terlalu pudar, tingkatkan `BlurRadius` atau `Distance` dan jalankan kembali kode – bereksperimen adalah bagian dari kesenangan.

![Create rectangle shape with shadow example](rectangle-shadow.png){alt="Contoh bentuk persegi panjang dengan bayangan"}

### Output yang diharapkan

* Dokumen Word satu halaman.
* Persegi panjang abu‑abu berukuran 200 × 100 poin yang ditempatkan di kiri‑atas halaman.
* Bayangan abu‑abu halus dengan offset 8 piksel pada sudut 45°, blur sebesar 5 piksel.

## Cara menambahkan bayangan ke bentuk – penjelasan lebih dalam

Anda mungkin bertanya, *“Apakah saya dapat menganimasikan bayangan atau membuatnya berubah berdasarkan input pengguna?”* Meskipun Aspose.Words sendiri tidak mendukung animasi, Anda dapat menyesuaikan properti bayangan secara programatis sebelum menyimpan, sehingga secara efektif menghasilkan beberapa versi dokumen dengan tampilan berbeda. Misalnya, melakukan loop pada koleksi warna:

```csharp
Color[] shadowColors = { Color.Gray, Color.Black, Color.DarkSlateGray };
foreach (var col in shadowColors)
{
    rectangleShape.Shadow.Color = col;
    document.Save($@"C:\Temp\Shadow_{col.Name}.docx");
}
```

Potongan kode kecil ini memperlihatkan **cara mengatur bayangan** secara dinamis—ideal untuk menghasilkan laporan bertema.

## Cara membuat persegi panjang – bentuk alternatif

Jika Anda memerlukan persegi panjang dengan sudut melengkung, cukup ubah `ShapeType`:

```csharp
Shape rounded = new Shape(document, ShapeType.RoundRectangle);
rounded.Width  = 200;
rounded.Height = 100;
rounded.Shadow.Enabled = true; // shadow works the same way
```

Atau, untuk membuat persegi sempurna, setel `Width` sama dengan `Height`. Properti bayangan yang sama tetap berlaku, jadi Anda sudah siap untuk **cara menambahkan bayangan** pada bentuk apa pun yang Anda pilih.

## Kesalahan umum dan pemecahan masalah

| Gejala | Penyebab yang mungkin | Solusi |
|--------|-----------------------|--------|
| Bayangan tidak muncul | `Shadow.Enabled` masih `false` | Setel `rectangleShape.Shadow.Enabled = true;` |
| Bayangan terlalu tajam | `BlurRadius` diatur ke 0 | Tingkatkan `BlurRadius` minimal menjadi 3 |
| Dokumen melempar `FileNotFoundException` saat menyimpan | Folder tujuan tidak ada | Buat folder terlebih dahulu atau gunakan jalur yang valid |
| Bentuk tidak terlihat | Lebar/Tinggi diatur ke 0 | Pastikan kedua dimensi > 0 |

Memperhatikan hal‑hal ini akan menyelamatkan Anda dari momen “kenapa bentuk saya tidak muncul?”.

## Ringkasan – apa yang telah kita capai

* **Membuat bentuk persegi panjang** dalam dokumen Word baru menggunakan Aspose.Words.  
* **Menambahkan bayangan ke bentuk** dengan mengaktifkan flag `Shadow.Enabled` dan menyesuaikan blur, jarak, sudut, serta warna.  
* Menunjukkan **cara menambahkan bayangan**, **cara membuat persegi panjang**, dan **cara mengatur bayangan** dalam cuplikan kode yang bersih dan dapat digunakan kembali.  
* Menyediakan contoh lengkap yang siap dijalankan yang dapat Anda tempel ke proyek C# mana pun.

## Apa selanjutnya?

Setelah menguasai dasar‑dasarnya, pertimbangkan untuk menjelajahi:

* **Cara menambahkan bayangan ke gambar** – API `Shadow` yang sama bekerja untuk `ShapeType.Image`.
* **Menggabungkan beberapa bentuk** – buat diagram alur atau infografis langsung di Word.
* **Ekspor ke PDF** – panggil `document.Save("output.pdf")` setelah menambahkan bayangan untuk versi yang dapat dicetak.

Silakan bereksperimen dengan warna, sudut, atau bahkan isian gradien yang berbeda. API ini cukup fleksibel untuk memungkinkan Anda membuat dokumen berpenampilan profesional tanpa harus membuka Word secara manual.

---

Selamat coding! Jika Anda mengalami kendala, tinggalkan komentar di bawah atau periksa forum Aspose.Words – komunitasnya cepat membantu.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}