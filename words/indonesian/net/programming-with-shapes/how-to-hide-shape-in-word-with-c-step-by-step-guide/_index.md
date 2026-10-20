---
category: general
date: 2026-07-19
description: Cara menyembunyikan bentuk di Word menggunakan Aspose.Words C#. Pelajari
  cara membuat bentuk menjadi tidak terlihat secara instan dan mengotomatiskan pembersihan
  dokumen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- make shape invisible
language: id
lastmod: 2026-07-19
og_description: Cara menyembunyikan shape di Word dengan Aspose.Words C#. Ikuti panduan
  ini untuk membuat shape tidak terlihat dan menyederhanakan dokumen Anda.
og_image_alt: Screenshot showing a Word document where a shape has been hidden using
  C#
og_title: Cara Menyembunyikan Bentuk di Word – Tutorial Lengkap C#
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: How to hide shape in Word using Aspose.Words C#. Learn to make shape
    invisible instantly and automate document cleanup.
  headline: How to Hide Shape in Word with C# – Step‑by‑Step Guide
  type: TechArticle
- description: How to hide shape in Word using Aspose.Words C#. Learn to make shape
    invisible instantly and automate document cleanup.
  name: How to Hide Shape in Word with C# – Step‑by‑Step Guide
  steps:
  - name: Does the hidden flag survive conversion to PDF?
    text: Yes. When you export the document to PDF (`doc.Save("out.pdf")`), any shape
      marked as hidden is omitted from the PDF rendering. This makes the technique
      handy for creating “clean” PDFs from templates that contain optional graphics.
  - name: What if the shape is inside a header or footer?
    text: 'The same approach works. You just need to navigate to the header/footer’s
      child nodes:'
  - name: Can I toggle visibility at runtime based on user input?
    text: 'Absolutely. Since `Hidden` is a regular Boolean, you can set it conditionally:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shape manipulation
title: Cara Menyembunyikan Bentuk di Word dengan C# – Panduan Langkah demi Langkah
url: /id/net/programming-with-shapes/how-to-hide-shape-in-word-with-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menyembunyikan Bentuk di Word – Tutorial C# Lengkap

Pernah bertanya-tanya **cara menyembunyikan bentuk** dalam file Word tanpa harus menghapusnya secara manual? Anda tidak sendirian. Dalam banyak skenario pelaporan otomatis, Anda ingin mempertahankan grafik placeholder untuk tujuan tata letak tetapi mencegahnya muncul di PDF atau DOCX akhir yang Anda kirim ke klien.  

Dalam panduan ini kami akan membahas solusi singkat yang siap produksi menggunakan **Aspose.Words for .NET** yang memungkinkan Anda **menyembunyikan bentuk di Word** secara programatis. Pada akhir tutorial Anda akan mengetahui cara membuat bentuk tidak terlihat, mengapa flag tersembunyi penting, dan cara memverifikasi hasilnya dengan satu baris kode.

> **Pro tip:** Properti hidden bekerja untuk objek gambar apa pun—gambar, kotak teks, atau bahkan WordArt—sehingga teknik ini dapat diterapkan jauh melampaui contoh sederhana yang akan kami gunakan.

---

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

- Versi terbaru **.NET 6** atau yang lebih baru (API juga berfungsi di .NET Framework).
- **Aspose.Words for .NET** terpasang via NuGet (`Install-Package Aspose.Words`).
- Dokumen Word (`WithShape.docx`) yang sudah berisi setidaknya satu bentuk.
- Visual Studio, Rider, atau editor C# apa pun yang Anda sukai.

Tidak ada pustaka tambahan yang diperlukan; semua yang lain berada di dalam assembly Aspose.Words.

---

## Langkah 1: Memuat Dokumen – Titik Awal untuk Menyembunyikan Bentuk

Hal pertama yang harus Anda lakukan adalah membuka file Word yang berisi bentuk yang ingin Anda sembunyikan. Ini adalah fondasi untuk setiap operasi **menyembunyikan bentuk di Word** karena API bekerja terhadap model dokumen yang berada di memori.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load the existing document that already has a shape.
Document doc = new Document(@"C:\Docs\WithShape.docx");
```

> **Mengapa ini penting:** Memuat dokumen membuat objek `Document` yang mencerminkan struktur file (section, paragraph, drawing). Tanpa objek ini Anda tidak dapat mengakses node bentuk untuk mengatur visibilitasnya.

---

## Langkah 2: Mengambil Bentuk – Menargetkan Objek yang Tepat untuk Disembunyikan

Selanjutnya, temukan bentuk yang ingin Anda sembunyikan. Aspose.Words memperlakukan setiap elemen gambar sebagai node `Shape`, yang dapat Anda ambil berdasarkan indeks atau nama. Untuk kesederhanaan, kami akan mengambil bentuk pertama dalam dokumen.

```csharp
// Retrieve the first shape node (index 0) from the document tree.
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
```

> **Peringatan kasus tepi:** Jika dokumen Anda tidak berisi bentuk, `GetChild` mengembalikan `null` dan casting akan menimbulkan pengecualian. Selalu lindungi kode Anda di lingkungan produksi:

```csharp
if (shape == null)
{
    Console.WriteLine("No shape found – nothing to hide.");
    return;
}
```

---

## Langkah 3: Menyembunyikan Bentuk – Membuatnya Tidak Terlihat pada Output

Sekarang masuk ke inti tutorial: **membuat bentuk tidak terlihat**. Aspose.Words menyediakan properti Boolean `Hidden` pada kelas `Shape`. Menetapkannya ke `true` memberi tahu Word untuk memperlakukan gambar tersebut sebagai tersembunyi, yang berarti tidak akan muncul saat file dibuka di UI maupun saat disimpan ke format lain.

```csharp
// Mark the shape as hidden so it won't be displayed.
shape.Hidden = true;
```

> **Mengapa menggunakan `Hidden` daripada menghapus?** Menghapus menghilangkan node sepenuhnya, yang dapat merusak perhitungan tata letak yang bergantung pada dimensi bentuk. Bentuk tersembunyi tetap berada di DOM, mempertahankan spasi sambil tidak terlihat—ideal untuk konten bersyarat.

---

## Langkah 4: Menyimpan Dokumen – Memverifikasi Bentuk Tidak Lagi Terlihat

Akhirnya, tulis kembali dokumen yang telah dimodifikasi ke disk (atau ke stream). Saat Anda membuka file yang disimpan, Anda akan melihat bahwa bentuk telah menghilang, mengonfirmasi bahwa Anda berhasil **menjadikan bentuk tidak terlihat**.

```csharp
// Save the updated document; the shape will now be hidden.
doc.Save(@"C:\Docs\ShapeHidden.docx");
Console.WriteLine("Document saved – the shape is now hidden.");
```

> **Output yang diharapkan:** Buka `ShapeHidden.docx` di Microsoft Word. Area tempat bentuk sebelumnya berada akan kosong, tetapi teks di sekitarnya tetap mempertahankan tata letak aslinya.

---

## Bonus: Menyembunyikan Beberapa Bentuk Sekaligus

Seringkali Anda perlu menyembunyikan **semua bentuk** yang memenuhi kondisi tertentu (misalnya, bentuk dengan `AlternativeText` tertentu). Berikut contoh loop singkat yang menunjukkan pola tersebut:

```csharp
// Hide every shape whose AlternativeText contains "temp".
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape s in shapes)
{
    if (s.AlternativeText?.Contains("temp") == true)
        s.Hidden = true;
}
doc.Save(@"C:\Docs\AllTempShapesHidden.docx");
```

> **Buat bentuk tidak terlihat** secara menyeluruh tanpa harus mencari setiap indeks secara manual—sempurna untuk laporan besar.

---

## Konfirmasi Visual (Opsional)

Jika Anda lebih suka petunjuk visual, Anda dapat menyisipkan tangkapan layar dalam dokumentasi Anda. Di bawah ini adalah gambar placeholder yang menunjukkan keadaan sebelum/setelah.

![How to hide shape in Word](/images/hide-shape-word.png "How to hide shape in Word – before and after the hidden flag")

*Alt text:* *How to hide shape in Word – the shape disappears after setting the Hidden property.*

---

## Pertanyaan Umum & Hal-hal yang Perlu Diwaspadai

### Apakah flag hidden tetap ada saat konversi ke PDF?

Ya. Ketika Anda mengekspor dokumen ke PDF (`doc.Save("out.pdf")`), setiap bentuk yang ditandai sebagai tersembunyi tidak disertakan dalam rendering PDF. Ini membuat teknik tersebut berguna untuk membuat PDF “bersih” dari templat yang berisi grafik opsional.

### Bagaimana jika bentuk berada di header atau footer?

Pendekatan yang sama berlaku. Anda hanya perlu menavigasi ke node anak header/footer:

```csharp
HeaderFooter header = (HeaderFooter)doc.GetChild(NodeType.HeaderFooter, 0, true);
Shape headerShape = (Shape)header.GetChild(NodeType.Shape, 0, true);
headerShape.Hidden = true;
```

### Bisakah saya mengubah visibilitas secara dinamis berdasarkan input pengguna?

Tentu saja. Karena `Hidden` adalah Boolean biasa, Anda dapat mengaturnya secara kondisional:

```csharp
shape.Hidden = userWantsShape ? false : true;
```

---

## Ringkasan

Kami telah membahas **cara menyembunyikan bentuk** dalam dokumen Word menggunakan Aspose.Words for .NET:

1. Muat dokumen yang berisi bentuk.  
2. Ambil node `Shape` yang ditargetkan.  
3. Setel `shape.Hidden = true` untuk **menjadikan bentuk tidak terlihat**.  
4. Simpan file dan verifikasi hasilnya.

Keempat langkah ini memberikan cara yang andal dan dapat diulang untuk **menyembunyikan bentuk di Word** tanpa merusak tata letak atau kehilangan node yang mendasarinya.

---

## Langkah Selanjutnya

- **Jelajahi pemformatan bersyarat:** Gabungkan flag hidden dengan field mail‑merge untuk menampilkan atau menyembunyikan grafik berdasarkan data.  
- **Otomatisasi pemrosesan batch:** Loop melalui folder dokumen dan terapkan logika yang sama pada setiap file.  
- **Dalami Aspose.Words:** Pelajari properti `Shape` seperti `WrapType`, `Rotation`, dan `ImageData` untuk mengontrol objek gambar secara menyeluruh.

Jika tutorial ini membantu, pertimbangkan untuk membaca panduan kami tentang **cara mengganti gambar di Word dengan C#** atau artikel tentang **membuat tabel secara dinamis dengan Aspose.Words**. Kedua topik tersebut dibangun di atas konsep model objek dokumen yang sama yang kami gunakan di sini.

Selamat coding, dan nikmati dokumen Word Anda yang rapi dan profesional!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}