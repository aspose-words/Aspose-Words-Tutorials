---
category: general
date: 2026-02-18
description: Buat bentuk persegi panjang menggunakan Aspose.Words dan pelajari cara
  menambahkan bayangan, mengatur ukuran bentuk, serta menyimpan dokumen Word dalam
  beberapa menit.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- save word document
- set shape size
- how to create document
language: id
og_description: Buat bentuk persegi panjang dalam file Word, pelajari cara menambahkan
  bayangan, mengatur ukuran bentuk, dan menyimpan dokumen dengan Aspose.Words di C#.
og_title: Buat bentuk persegi panjang di Word – Tutorial Lengkap Aspose.Words
tags:
- Aspose.Words
- C#
- Word automation
title: Membuat bentuk persegi panjang di Word dengan Aspose.Words – Panduan Langkah
  demi Langkah
url: /id/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat bentuk persegi panjang di Word dengan Aspose.Words – Panduan Langkah‑per‑Langkah

Pernah perlu **membuat bentuk persegi panjang** dalam file Word tetapi tidak yakin harus mulai dari mana? Anda tidak sendirian—para pengembang sering bertanya, “bagaimana cara menambahkan bayangan ke sebuah bentuk dan tetap menjaga dokumen dapat diedit?” Dalam tutorial ini kami akan menjawab pertanyaan itu serta menunjukkan **cara menambahkan bayangan**, **mengatur ukuran bentuk**, dan **menyimpan dokumen Word** semuanya dalam satu alur yang mulus.

Kami akan membahas semua yang Anda perlukan, mulai dari menginisialisasi dokumen baru (ya, itu langkah pertama untuk **cara membuat dokumen**) hingga menyimpan *.docx* akhir ke disk. Tanpa referensi eksternal, hanya contoh mandiri yang dapat Anda salin‑tempel ke Visual Studio dan jalankan hari ini.

---

## Prasyarat

- .NET 6+ (atau .NET Framework 4.7+). Aspose.Words bekerja dengan runtime .NET terbaru apa pun.
- Lisensi Aspose.Words yang valid (atau kunci evaluasi gratis) – jika tidak, Anda akan melihat watermark.
- Visual Studio, Rider, atau editor C# apa pun yang Anda sukai.
- Pengetahuan dasar C#—tidak perlu hal yang rumit, cukup kemampuan menjalankan aplikasi konsol.

> **Pro tip:** Jika Anda menggunakan Mac, kode yang sama dapat dijalankan di .NET 6 dengan VS Code—pastikan Anda menambahkan paket NuGet `Aspose.Words`.

---

## Langkah 1: Inisialisasi dokumen – fondasi dari **cara membuat dokumen**

Sebelum kita dapat menggambar apa pun, kita membutuhkan kanvas kosong. Aspose.Words menyebutnya `Document`.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

> **Mengapa ini penting:** Objek `Document` mewakili seluruh file *.docx*. Semua bentuk, paragraf, dan bagian yang Anda tambahkan menjadi anak dari objek ini. Memulai dengan dokumen bersih memastikan tidak ada gaya tersembunyi yang mengganggu persegi panjang Anda.

---

## Langkah 2: Definisikan persegi panjang dan **atur ukuran bentuk**

Sebuah persegi panjang hanyalah `Shape` dengan `ShapeType.Rectangle`. Kami akan memberi dimensi eksplisit sehingga tampil persis seperti yang diinginkan.

```csharp
// Step 2: Create a rectangular shape and define its size
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points (≈2.78 inches)
rectangleShape.Height = 100; // height in points (≈1.39 inches)
```

> **Apa arti angka‑angka tersebut:** Aspose.Words menggunakan satuan poin (1 pt = 1/72 in). Sesuaikan nilai‑nilai tersebut agar cocok dengan tata letak Anda; untuk halaman A4 standar, 200 pt adalah lebar yang nyaman.

---

## Langkah 3: **Cara menambahkan bayangan** – membuat bentuk lebih menonjol

Bayangan memberikan petunjuk visual bahwa bentuk “terangkat” dari halaman. Properti `Shadow` memungkinkan Anda menyesuaikan warna, jarak, transparansi, dan blur.

```csharp
// Step 3: Apply a shadow to the shape
rectangleShape.Shadow.Color        = Color.Black; // Shadow color
rectangleShape.Shadow.Distance    = 5;           // Offset distance in points
rectangleShape.Shadow.Transparency = 0.4;        // 40 % transparent
rectangleShape.Shadow.BlurRadius  = 8;           // Soft edge radius
```

> **Mengapa menggunakan transparansi?** Bayangan yang sepenuhnya pekat dapat terlihat keras. Menetapkannya ke 0.4 membuat efek menjadi halus dan profesional.

---

## Langkah 4: Posisi persegi panjang – aliran inline dengan teks di sekitarnya

Jika Anda ingin bentuk berperilaku seperti karakter dalam paragraf, atur `WrapType` menjadi `Inline`. Ini menjaga tata letak tetap dapat diprediksi, terutama ketika dokumen diedit kemudian.

```csharp
// Step 4: Set the shape to flow inline with the surrounding text
rectangleShape.WrapType = WrapType.Inline;
```

> **Kasus khusus:** Jika Anda perlu persegi panjang mengambang di atas teks (misalnya, watermark), ubah `WrapType` menjadi `Square` atau `BehindText`.

---

## Langkah 5: Sisipkan bentuk ke dalam badan dokumen

Sekarang kita benar‑benar menempatkan persegi panjang ke paragraf pertama. Jika dokumen belum memiliki konten, `FirstParagraph` secara otomatis dibuat.

```csharp
// Step 5: Insert the shape into the first paragraph of the document
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **Tip:** Anda juga dapat membuat paragraf baru terlebih dahulu lalu menambahkan bentuk—berguna ketika Anda memerlukan teks di sekitarnya.

---

## Langkah 6: **Simpan dokumen Word** – langkah akhir

Dengan semua elemen sudah siap, menyimpan file cukup satu baris kode. Pilih jalur apa pun yang Anda suka; contoh ini menggunakan placeholder yang harus Anda ganti dengan direktori Anda sendiri.

```csharp
// Step 6: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowShape.docx");
```

> **Hasil:** Buka *.docx* yang dihasilkan di Microsoft Word. Anda akan melihat persegi panjang dengan bayangan hitam, lebar 200 pt dan tinggi 100 pt, berada inline dengan paragraf pertama.

---

## Output yang diharapkan

Saat Anda membuka **ShadowShape.docx**, dokumen akan menampilkan:

- Satu paragraf yang berisi sebuah bentuk persegi panjang.
- Persegi panjang memiliki bayangan hitam halus yang bergeser sebesar 5 pt.
- Ukuran bentuk sesuai dengan dimensi yang ditetapkan pada Langkah 2.
- Tidak ada teks tambahan muncul kecuali Anda menambahkannya secara manual.

Jika bentuk tidak muncul, periksa kembali bahwa Anda telah merujuk versi Aspose.Words yang tepat dan lisensi (atau trial) Anda aktif.

---

## Pertanyaan Umum & Variasi

| Pertanyaan | Jawaban |
|------------|---------|
| *Apakah saya dapat mengubah warna bayangan menjadi selain hitam?* | Tentu saja—atur `rectangleShape.Shadow.Color = Color.Blue;` atau warna apa pun dari `System.Drawing.Color`. |
| *Bagaimana jika saya membutuhkan persegi panjang yang lebih besar?* | Sesuaikan nilai `Width` dan `Height`. Ingat, satuannya dalam poin; 72 pt = 1 in. |
| *Apakah memungkinkan menempatkan bentuk pada posisi absolut?* | Ya—gunakan `WrapType = WrapType.Absolute` dan atur properti `Top`/`Left`. |
| *Apakah ini bekerja dengan .NET Core?* | Ya. Aspose.Words bersifat lintas‑platform; cukup instal paket NuGet untuk .NET Standard. |
| *Bisakah saya menambahkan teks di dalam persegi panjang?* | Tidak secara langsung; Anda perlu menyisipkan bentuk `TextBox` alih‑alih persegi panjang biasa. |

---

## Contoh Lengkap yang Siap Pakai (Copy‑Paste)

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize a new document
        Document document = new Document();

        // 2️⃣ Create rectangle and set its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 200;
        rectangleShape.Height = 100;

        // 3️⃣ Add a subtle black shadow
        rectangleShape.Shadow.Color         = Color.Black;
        rectangleShape.Shadow.Distance     = 5;
        rectangleShape.Shadow.Transparency = 0.4;
        rectangleShape.Shadow.BlurRadius   = 8;

        // 4️⃣ Make the shape flow inline with text
        rectangleShape.WrapType = WrapType.Inline;

        // 5️⃣ Insert the shape into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 6️⃣ Persist the file
        document.Save(@"C:\Temp\ShadowShape.docx");

        System.Console.WriteLine("Document saved successfully!");
    }
}
```

Jalankan program, buka `C:\Temp\ShadowShape.docx`, dan Anda akan melihat persegi panjang dengan bayangan persis seperti yang dijelaskan.

---

## Kesimpulan

Anda kini tahu cara **membuat bentuk persegi panjang** dalam file Word menggunakan Aspose.Words, cara **mengatur ukuran bentuk**, **menambahkan bayangan**, dan akhirnya **menyimpan dokumen Word** dengan perubahan tersebut. Seluruh proses—dari **cara membuat dokumen** hingga menyimpan hasil—termasuk dalam beberapa baris kode C# dan dapat dikembangkan untuk tata letak yang lebih kompleks.

Siap untuk tantangan berikutnya? Coba ganti persegi panjang dengan bentuk sudut melengkung, bereksperimen dengan warna bayangan yang berbeda, atau sematkan bentuk di dalam sel tabel. Setiap penyesuaian memperkuat konsep inti yang telah kami bahas di sini.

Jika Anda merasa panduan ini membantu, bagikan, tinggalkan komentar dengan variasi Anda, atau jelajahi tutorial lain kami tentang otomatisasi Word, seperti menyisipkan gambar atau menghasilkan tabel dengan Aspose.Words. Selamat coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}