---
category: general
date: 2026-05-26
description: Buat dokumen Word di C# dengan Aspose.Words, sisipkan bentuk persegi
  panjang, atur warna isi, dan tambahkan efek bayangan – panduan langkah demi langkah.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- how to set fill
language: id
og_description: Buat dokumen Word di C# menggunakan Aspose.Words. Pelajari cara menyisipkan
  bentuk persegi panjang, mengatur warna isi, dan menambahkan efek bayangan.
og_title: Buat Dokumen Word – Sisipkan Bentuk Persegi Panjang & Bayangan di C#
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create Word document in C# with Aspose.Words, insert rectangle shape,
    set fill color, and add shadow effect – step‑by‑step guide.
  headline: Create Word Document – Insert Rectangle Shape & Shadow in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Buat Dokumen Word – Sisipkan Bentuk Persegi Panjang & Bayangan di C#
url: /id/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat Dokumen Word – Sisipkan Bentuk Persegi Panjang & Bayangan di C#

Pernah bertanya-tanya bagaimana cara **create Word document** secara programatis tanpa membuka Microsoft Word terlebih dahulu? Anda bukan satu-satunya. Dalam banyak skenario otomatisasi—pikirkan faktur, kontrak, atau pembuatan laporan massal—Anda memerlukan cara yang andal untuk membuat file .docx, menambahkan bentuk di dalamnya, memberi warna, dan mungkin bahkan bayangan untuk tampilan yang halus.

Di tutorial ini kami akan membahas tepat itu: menggunakan Aspose.Words untuk .NET untuk **create Word document**, **insert rectangle shape**, menerapkan isian, dan **add shadow**. Pada akhir tutorial Anda akan memiliki file siap‑simpan yang dapat Anda alirkan ke alur kerja downstream mana pun.

Kami juga akan menyentuh **how to insert shape** secara fleksibel, dan mengapa **how to set fill** penting untuk konsistensi visual. Tanpa basa‑basi, hanya kode yang dapat Anda salin‑tempel dan jalankan.

## Prasyarat

- .NET 6+ (atau .NET Framework 4.7+) terpasang.
- Lisensi Aspose.Words untuk .NET yang valid (atau kunci evaluasi sementara).
- Visual Studio, Rider, atau IDE C# apa pun yang Anda suka.
- Familiaritas dasar dengan sintaks C#—tidak memerlukan hal yang rumit.

Sudah siap? Bagus, mari kita mulai.

## Langkah 1 – Buat Dokumen Word

Hal pertama yang Anda butuhkan adalah objek dokumen kosong. Ini adalah kanvas tempat semua hal lainnya berada.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder.
Document doc = new Document();                 // The document itself.
DocumentBuilder builder = new DocumentBuilder(doc); // Helper to add content.
```

`Document` mewakili file .docx dalam memori, sementara `DocumentBuilder` memberikan API yang nyaman untuk menyisipkan teks, tabel, dan bentuk. **Creating the Word document** dengan cara ini instan—tanpa UI, tanpa interop COM, hanya .NET murni.

## Langkah 2 – Sisipkan Bentuk Persegi Panjang

Setelah kita memiliki dokumen, mari **insert rectangle shape**. Metode `InsertShape` menerima enum `ShapeType`, lebar, dan tinggi (dalam poin). Kita akan menggunakan persegi panjang berukuran 150 × 80 poin, yang kira‑kira setara dengan 2 × 1 inci.

```csharp
// Step 2: Insert a rectangle shape of the desired size.
Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Di balik layar, Aspose membuat objek `Shape`, menambahkannya ke paragraf saat ini, dan mengembalikan referensi yang dapat Anda gaya. Ini adalah inti dari **how to insert shape**—hanya satu baris kode, namun sangat kuat.

## Langkah 3 – Cara Mengatur Isian

Sebuah bentuk tanpa isian tidak terlihat pada halaman putih. Mari beri latar belakang biru‑muda yang menyenangkan.

```csharp
// Step 3: Apply a fill color to make the shape visible.
shape.FillColor = System.Drawing.Color.LightBlue; // Any System.Drawing.Color works.
```

Anda juga dapat menggunakan gradien, tekstur, atau bahkan isian gambar, tetapi warna solid membuat contoh tetap sederhana. Ini menunjukkan **how to set fill** pada bentuk apa pun yang Anda buat, memastikan isyarat visual yang diharapkan pembaca.

## Langkah 4 – Cara Menambahkan Bayangan

Bayangan menambah kedalaman dan membuat bentuk menonjol. Aspose.Words menyediakan objek `ShadowFormat` di mana Anda dapat mengaktifkan/menonaktifkan visibilitas, memilih warna, dan menyesuaikan blur, jarak, serta sudut.

```csharp
// Step 4: Configure the shadow effect – enable it, set color, blur, distance and angle.
shape.ShadowFormat.Visible = true;                     // Turn the shadow on.
shape.ShadowFormat.Color = System.Drawing.Color.Gray; // Shadow color.
shape.ShadowFormat.BlurRadius = 4.0;                  // Softness in pixels.
shape.ShadowFormat.Distance = 3.0;                    // How far the shadow is offset.
shape.ShadowFormat.Angle = 45;                        // Direction of the offset (degrees).
```

Mengapa nilai-nilai khusus ini? Sudut 45° memberikan sumber cahaya alami dari atas‑kanan, blur yang sedang menjaga bayangan tetap halus, dan jarak pendek mencegah bentuk terlihat terlepas. Silakan bereksperimen—mengubah sudut menjadi 135° akan membuat bayangan jatuh ke bawah‑kiri, misalnya.

## Langkah 5 – Simpan Dokumen

Semua pekerjaan selesai; sekarang kita menulis file ke disk. Pilih jalur apa pun yang Anda suka; pastikan foldernya ada.

```csharp
// Step 5: Save the document with the shaped shadow.
doc.Save("YOUR_DIRECTORY/ShadowShape.docx");
```

Saat Anda membuka `ShadowShape.docx` di Microsoft Word, Anda akan melihat persegi panjang biru‑muda dengan bayangan abu‑abu lembut—tepat seperti yang kami skrip.

## Contoh Lengkap yang Berfungsi

Menggabungkan semuanya, berikut program lengkap yang siap disalin‑tempel:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a rectangle shape (150 × 80 points).
        Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

        // 3️⃣ Set a solid fill color so the shape is visible.
        shape.FillColor = System.Drawing.Color.LightBlue;

        // 4️⃣ Add a subtle shadow for depth.
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.Color = System.Drawing.Color.Gray;
        shape.ShadowFormat.BlurRadius = 4.0;   // pixels
        shape.ShadowFormat.Distance = 3.0;     // pixels
        shape.ShadowFormat.Angle = 45;        // degrees

        // 5️⃣ Persist the document.
        doc.Save("ShadowShape.docx");
    }
}
```

### Hasil yang Diharapkan

- Sebuah file bernama **ShadowShape.docx** muncul di folder target.
- Membukanya di Word menampilkan persegi panjang biru‑muda yang terpusat pada halaman pertama.
- Persegi panjang tersebut menghasilkan bayangan abu‑abu dengan sudut 45°, memberikan efek 3‑D yang halus.

## Pertanyaan Umum & Kasus Tepi

**Bagaimana jika saya membutuhkan bentuk lain?**  
Ganti `ShapeType.Rectangle` dengan nilai enum lain (`Ellipse`, `Star`, `Arrow`, dll.). Sisanya tetap sama.

**Bisakah saya menambahkan teks di dalam bentuk?**  
Ya—setelah membuat bentuk, panggil `shape.AppendChild(new Paragraph(doc))` lalu sisipkan `Run` dengan teks Anda. Ingat untuk mengatur properti `shape.TextBox` jika Anda menginginkan pembungkus.

**Bagaimana dengan DPI atau satuan pengukuran?**  
Aspose bekerja dalam poin (1 pt = 1/72 inci). Jika Anda lebih suka sentimeter, kalikan dengan 28,35 (karena 1 cm ≈ 28,35 pt).

**Apakah saya memerlukan lisensi agar ini berfungsi?**  
Versi evaluasi menambahkan watermark pada halaman pertama. Lisensi yang tepat menghilangkannya dan membuka seluruh API.

## Tips & Hal yang Perlu Diwaspadai

- **Pro tip:** Panggil `builder.MoveToDocumentEnd()` sebelum menyisipkan bentuk jika Anda menginginkannya di akhir dokumen.
- **Waspadai:** Menyimpan ke folder hanya‑baca akan memunculkan `UnauthorizedAccessException`. Pastikan aplikasi Anda memiliki izin menulis.
- **Catatan kinerja:** Untuk pembuatan massal (ratusan dokumen), gunakan kembali satu instance `Document` sebagai templat dan kloning dengan `doc.Clone(true)` untuk menghindari overhead inisialisasi berulang.

## Kesimpulan

Anda kini tahu cara **create Word document**, **insert rectangle shape**, **set fill**, dan **add shadow** menggunakan Aspose.Words untuk .NET. Potongan kode di atas adalah solusi mandiri yang dapat Anda masukkan ke proyek C# apa pun, baik itu aplikasi konsol, API web, atau layanan latar belakang.

Dari sini Anda dapat menjelajahi:

- Menambahkan banyak bentuk dengan warna yang berbeda.
- Menggunakan gradien atau isian gambar (`shape.FillColor = ...` → `shape.FillPattern`).
- Menggabungkan bentuk dengan tabel untuk tata letak laporan yang kompleks.

Cobalah, ubah parameter-parameter, dan saksikan file Word otomatis Anda terlihat lebih profesional hanya dengan beberapa baris kode. Selamat coding!

## Tutorial Terkait

- [Buat bentuk persegi panjang di Word menggunakan C# – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tutorial Bayangan Bentuk Aspose.Words – Tambahkan Bayangan ke Bentuk Word di C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Buat Bentuk Grup dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}