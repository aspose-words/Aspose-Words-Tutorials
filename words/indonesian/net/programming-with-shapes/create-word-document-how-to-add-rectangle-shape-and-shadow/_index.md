---
category: general
date: 2026-03-19
description: Buat dokumen Word di C# dengan Aspose.Words, pelajari cara menambahkan
  bentuk, menambahkan bentuk persegi panjang, menerapkan bayangan, dan menyimpan dokumen
  sebagai docx dalam hitungan menit.
draft: false
keywords:
- create word document
- how to add shape
- add rectangle shape
- save document as docx
- add shadow to shape
language: id
og_description: Buat dokumen Word dengan Aspose.Words, tambahkan bentuk persegi panjang,
  terapkan bayangan luar, dan simpan dokumen sebagai docx. Panduan langkah demi langkah.
og_title: Buat Dokumen Word – Tambahkan Bentuk Persegi Panjang & Bayangan
tags:
- Aspose.Words
- C#
- Document Automation
title: Buat Dokumen Word – Cara Menambahkan Bentuk Persegi Panjang dan Bayangan
url: /id/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat Dokumen Word – Cara Menambahkan Bentuk Persegi Panjang dan Bayangan

Pernah membutuhkan untuk **create word document** secara programatis dan bertanya‑tanya dari mana harus memulai? Anda tidak sendirian. Banyak pengembang mengalami hal yang sama ketika pertama kali mencoba menghasilkan file .docx yang berisi grafik khusus. Dalam tutorial ini kami akan membahas seluruh proses—cara menambahkan bentuk, khususnya **add rectangle shape**, memberi gaya **add shadow to shape**, dan akhirnya **save document as docx**.  

Pada akhir panduan Anda akan memiliki potongan kode C# siap pakai yang dapat Anda sisipkan ke proyek .NET mana pun. Tanpa referensi yang samar, hanya contoh lengkap yang dapat dijalankan.  

## Prasyarat

- .NET 6.0 atau lebih baru (kode ini juga bekerja dengan .NET Framework).  
- Aspose.Words untuk .NET terpasang (paket NuGet `Aspose.Words`).  
- Pemahaman dasar tentang sintaks C#—tidak diperlukan hal yang rumit.  

Jika Anda belum memiliki pustaka tersebut, jalankan:

```bash
dotnet add package Aspose.Words
```

Itu saja—tanpa SDK tambahan, tanpa interop COM, hanya satu referensi NuGet.

---

## Langkah 1: Buat Dokumen Word (Tujuan Utama)

Hal pertama yang kita butuhkan adalah kanvas bersih. Anggap kelas `Document` sebagai halaman baru di Microsoft Word; ia menampung bagian, paragraf, dan semua hal lain yang akan Anda tambahkan nanti.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Step 1: Initialize a new blank document
Document doc = new Document();               // This creates an empty .docx in memory
```

Mengapa memulai dengan `Document` kosong? Karena hal ini menjamin tidak ada format tersembunyi yang masuk dari templat. Berdasarkan pengalaman saya, memulai dari nol menghindari pergeseran tata letak misterius ketika Anda kemudian menyisipkan bentuk.

---

## Langkah 2: Sisipkan Bentuk Persegi Panjang – Menambahkan Elemen Visual

Sekarang kita sudah memiliki dokumen, mari **add rectangle shape** ke paragraf pertama. Objek `Shape` sangat fleksibel; Anda dapat memilih `ShapeType.Rectangle`, `Ellipse`, atau bahkan gambar khusus. Berikut kode minimalnya:

```csharp
// Step 2: Create a rectangle and attach it to the first paragraph
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.78 inches)
    Height = 100,              // Height in points (≈1.39 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};

// Append the shape to the first paragraph (creates one if missing)
Paragraph firstPara = doc.FirstSection.Body.FirstParagraph;
firstPara.AppendChild(rect);
```

**Apa yang terjadi di balik layar?**  
- `ShapeType.Rectangle` memberi tahu Aspose bahwa kita menginginkan kotak sederhana.  
- `WrapType.Inline` memastikan persegi panjang bergerak bersama alur teks, yang biasanya diharapkan dalam skenario pengolah kata.  
- Dengan menambahkan ke `FirstParagraph`, kita menghindari kebutuhan menyisipkan paragraf baru secara manual; Aspose akan membuatnya untuk kita jika dokumen benar‑benar kosong.

> **Pro tip:** Jika Anda membutuhkan bentuk berada *di belakang* teks, ubah `WrapType` menjadi `WrapType.Transparent`. Perubahan kecil ini dapat menghasilkan perbedaan visual yang besar.

---

## Langkah 3: Terapkan Bayangan Luar – Meningkatkan Tampilan

Persegi panjang datar memang… datar. Menambahkan **add shadow to shape** memberikan kedalaman tanpa gambar tambahan. `ShadowFormat` milik Aspose membuat ini menjadi satu baris kode.

```csharp
// Step 3: Configure an outer shadow for the rectangle
rect.ShadowFormat.Type = ShadowType.OuterShadow;
rect.ShadowFormat.Blur = 5.0;           // Softness of the shadow edge
rect.ShadowFormat.Distance = 3.0;      // How far the shadow is offset
rect.ShadowFormat.Angle = 45;          // Direction in degrees (45° = bottom‑right)
rect.ShadowFormat.Color = Color.Gray; // Classic gray shadow
```

Mengapa menggunakan nilai‑nilai spesifik tersebut?  
- **Blur** sebesar `5.0` memberikan tepi berbulu halus yang tampak profesional pada kebanyakan monitor.  
- **Distance** sebesar `3.0` dan **Angle** `45` menciptakan sumber cahaya alami dari kiri‑atas, konvensi desain yang umum.  
- **Color.Gray** bekerja baik pada tema terang maupun gelap; Anda dapat menggantinya dengan `Color.Black` bila memerlukan kontras yang lebih kuat.

Jika Anda pernah membutuhkan bayangan *inner* (seperti tombol yang tertekan), cukup ubah `ShadowType.OuterShadow` menjadi `ShadowType.InnerShadow`. Properti yang sama tetap berlaku.

---

## Langkah 4: Simpan Dokumen sebagai DOCX – Menyimpan Pekerjaan Anda

Semua kesenangan itu bagus, tetapi pada akhirnya Anda ingin file tersimpan di disk. Langkah **save document as docx** sangat sederhana:

```csharp
// Step 4: Persist the document to a .docx file
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
doc.Save(outputPath, SaveFormat.Docx);
```

Beberapa catatan:  
- Enum `SaveFormat.Docx` menjamin format Office Open XML modern, yang kompatibel dengan Word 2007+.  
- Jika Anda perlu men-stream file langsung ke respons web, ganti path file dengan `MemoryStream` dan tulis ke respons HTTP.

Setelah menjalankan kode, buka `ShadowedRectangle.docx` di Microsoft Word. Anda akan melihat persegi panjang abu‑abu dengan bayangan lembut, berada inline dengan paragraf pertama—tepat seperti yang kami harapkan.

---

## Cara Menambahkan Bentuk – Pendekatan Alternatif

Contoh di atas menggunakan pendekatan *inline*, tetapi kadang‑kadang Anda menginginkan bentuk yang mengambang di atas teks. Di sinilah **how to add shape** dengan pembungkus berbeda berperan.

```csharp
Shape floatingRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 250,
    Height = 120,
    WrapType = WrapType.Square, // Allows text to wrap around the shape
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    HorizontalAlignment = HorizontalAlignment.Center
};

doc.FirstSection.Body.FirstParagraph.AppendChild(floatingRect);
```

Di sini kami mengubah `WrapType` menjadi `Square` dan memusatkan bentuk di halaman. Pola ini berguna untuk halaman sampul atau spanduk dekoratif. Ingat: bentuk mengambang sedikit meningkatkan ukuran file karena Word menyimpan data posisi tambahan.

---

## Output yang Diharapkan & Verifikasi

Saat Anda membuka file yang dihasilkan, Anda harus melihat:

- Satu paragraf yang berisi persegi panjang abu‑abu.  
- Persegi panjang berukuran kira‑kira 2.8 × 1.4 inci.  
- Bayangan luar halus yang bergeser ke kanan‑bawah.  

Jika bentuk muncul *di luar* paragraf, periksa kembali `WrapType`. Jika bayangan terlihat terlalu keras, turunkan nilai `Blur` atau ubah `Color` ke nuansa yang lebih terang.

---

## Kesalahan Umum & Cara Menghindarinya

| Masalah | Mengapa Terjadi | Solusi |
|-------|----------------|-----|
| Bentuk menghilang setelah disimpan | `WrapType` diatur ke `Inline` tetapi paragraf dihapus | Pastikan paragraf ada; gunakan `doc.FirstSection.Body.FirstParagraph` untuk menjamin keberadaannya. |
| Bayangan terlihat piksel | Menggunakan nilai `Blur` yang sangat rendah | Tingkatkan `Blur` setidaknya ke `3.0` untuk tepi yang halus. |
| Ukuran file membengkak | Menambahkan banyak gambar resolusi tinggi bersama bentuk | Gunakan `doc.RemoveUnusedResources()` sebelum menyimpan jika Anda menambahkan gambar. |
| Warna tidak terlihat pada mode gelap | Menggunakan `Color` gelap untuk bentuk itu sendiri | Pilih warna kontras (misalnya `Color.White`) untuk visibilitas yang lebih baik. |

---

## Contoh Lengkap yang Berfungsi

Berikut adalah kode lengkap yang siap disalin‑tempel dan mencakup semua yang telah dibahas. Jalankan sebagai aplikasi konsol.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank Word document
        Document doc = new Document();

        // 2️⃣ Add a rectangle shape to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 200,
            Height = 100,
            WrapType = WrapType.Inline
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Apply an outer shadow to the rectangle
        rect.ShadowFormat.Type = ShadowType.OuterShadow;
        rect.ShadowFormat.Blur = 5.0;
        rect.ShadowFormat.Distance = 3.0;
        rect.ShadowFormat.Angle = 45;
        rect.ShadowFormat.Color = Color.Gray;

        // 4️⃣ Save the document as a .docx file
        string outPath = @"C:\Temp\ShadowShape.docx";
        doc.Save(outPath, SaveFormat.Docx);

        // Optional: Let the user know we’re done
        System.Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Penjelasan setiap blok** disertakan sebagai komentar inline, memenuhi kebutuhan pembaca SEO maupun asisten AI yang menyukai jawaban mandiri.

---

## Kesimpulan

Kami baru saja **create word document** dari awal, mempelajari **how to add shape**, khususnya **add rectangle shape**, memberi **add shadow to shape**, dan akhirnya **save document as docx**. Langkah‑langkahnya sederhana, kodenya ringkas, dan hasilnya tampak profesional.  

Jika Anda siap melangkah lebih jauh, coba ganti persegi panjang dengan gambar khusus, bereksperimen dengan warna bayangan yang berbeda, atau hasilkan laporan lengkap dengan banyak bagian berbentuk. API Aspose.Words cukup fleksibel untuk menangani segala hal mulai dari faktur hingga brosur pemasaran.

Ada pertanyaan tentang tipe bentuk lain atau butuh bantuan mengintegrasikan ini ke layanan ASP.NET Core? Tinggalkan komentar di bawah, dan selamat coding! 

![create word document with rectangle shape and shadow](placeholder-image.png "create word document with rectangle shape and shadow

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}