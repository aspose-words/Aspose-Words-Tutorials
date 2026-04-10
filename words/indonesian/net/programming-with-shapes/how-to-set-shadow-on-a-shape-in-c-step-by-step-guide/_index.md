---
category: general
date: 2026-04-10
description: cara mengatur bayangan pada bentuk di C# – pelajari cara menerapkan bayangan
  jatuh, mengubah transparansi, menyesuaikan blur, dan menambahkan bayangan bentuk
  menggunakan Aspose.Words.
draft: false
keywords:
- how to set shadow
- apply drop shadow
- how to change transparency
- how to adjust blur
- add shape shadow
language: id
og_description: cara mengatur bayangan pada bentuk di C# – tutorial ini menunjukkan
  cara menerapkan bayangan jatuh, mengubah transparansi, menyesuaikan blur, dan menambahkan
  bayangan bentuk dengan contoh kode yang jelas.
og_title: Cara mengatur bayangan pada bentuk di C# – Panduan Lengkap
tags:
- Aspose.Words
- C#
- Document Automation
title: Cara menambahkan bayangan pada bentuk di C# – Panduan Langkah demi Langkah
url: /id/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cara menambahkan bayangan pada shape di C# – Panduan Lengkap

Pernah bertanya-tanya **cara menambahkan bayangan** pada sebuah shape ketika Anda secara program membangun dokumen Word? Anda tidak sendirian. Banyak pengembang menemui kesulitan ketika mereka membutuhkan drop shadow yang halus untuk textbox, logo, atau call‑out box, dan dokumentasi API terasa kurang.  

Dalam tutorial ini kami akan membahas seluruh proses: mulai dari memuat file `.docx`, mengambil `Shape` pertama, menerapkan drop shadow, menyesuaikan transparansinya, mengatur radius blur, dan akhirnya menempatkannya dengan tepat. Pada akhir tutorial Anda akan memiliki potongan kode yang dapat digunakan kembali dan bekerja dengan Aspose.Words .NET 2023 atau yang lebih baru, serta memahami *mengapa* setiap properti penting.

## Apa yang Anda Butuhkan

- **Aspose.Words for .NET** (paket NuGet `Aspose.Words`) – perpustakaan yang menyediakan kelas `Document`, `Shape`, dan `ShadowFormat`.  
- **.NET 6+** (atau .NET Framework 4.7.2) – runtime terbaru apa pun dapat digunakan.  
- Sebuah file Word sederhana (`input.docx`) yang sudah berisi setidaknya satu shape, seperti textbox.  
- Visual Studio, VS Code, atau IDE favorit Anda.

Itu saja. Tanpa alat pihak ketiga tambahan, tanpa COM interop, hanya C# biasa.

![how to set shadow example](image-placeholder.png){:alt="cara menambahkan bayangan pada shape di dokumen Word"}

## Cara Menambahkan Bayangan – Gambaran Umum

Ide utama di balik **cara menambahkan bayangan** adalah memanipulasi objek `ShadowFormat` yang berada pada sebuah `Shape`. Anggaplah `ShadowFormat` sebagai “lembar gaya” mini untuk bayangan itu sendiri: ia memberi tahu renderer apakah bayangan terlihat, warna apa yang harus dipakai, seberapa transparan, seberapa blur, dan di mana posisinya relatif terhadap shape.  

Di bawah ini adalah program *lengkap* yang dapat dijalankan. Silakan salin‑tempel ke aplikasi console, tekan **F5**, dan saksikan bayangan muncul di file `output.docx` yang disimpan.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;                 // Core document classes
using Aspose.Words.Drawing;         // Shape & ShadowFormat

class ShadowDemo
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Load the Word document that contains the shape.
        // -------------------------------------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // -------------------------------------------------
        // Step 2: Retrieve the first shape (e.g., a textbox) from the document.
        // -------------------------------------------------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx has a textbox.");
            return;
        }

        // -------------------------------------------------
        // Step 3: Make the shadow visible.
        // -------------------------------------------------
        shape.ShadowFormat.Visible = true;

        // -------------------------------------------------
        // Step 4: Set the shadow colour to a dark gray.
        // -------------------------------------------------
        shape.ShadowFormat.Color = Color.DarkGray;

        // -------------------------------------------------
        // Step 5: Define the shadow's transparency (30 % transparent).
        // -------------------------------------------------
        shape.ShadowFormat.Transparency = 0.3;   // 0 = opaque, 1 = fully transparent

        // -------------------------------------------------
        // Step 6: Configure the blur radius (size) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Size = 6;            // Larger value = softer edges

        // -------------------------------------------------
        // Step 7: Set the offset distance and direction (angle) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Distance = 2;        // How far the shadow is from the shape
        shape.ShadowFormat.Angle = 45;          // Angle in degrees (0 = right, 90 = down)

        // -------------------------------------------------
        // Save the modified document.
        // -------------------------------------------------
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Shadow applied successfully! Check output.docx.");
    }
}
```

### Mengapa Pengaturan Ini Penting

- **Visible** – Tanpa mengaktifkan flag ini, semua properti lain diabaikan.  
- **Color** – Abu-abu gelap meniru drop shadow UI tipikal; Anda dapat mengganti dengan `Color` apa saja.  
- **Transparency** – 0.3 memberikan tampilan *lembut* sambil tetap membuat shape dapat dibaca.  
- **Size** – Mengontrol blur; nilai 6 biasanya cukup untuk tampilan profesional.  
- **Distance & Angle** – Bersama-sama mereka menentukan *offset*; 2 pt pada 45° menghasilkan bayangan diagonal yang halus.

Itulah inti dari **cara menambahkan bayangan**. Selanjutnya, kami akan membahas setiap bagian sehingga Anda dapat **menerapkan drop shadow**, **mengubah transparansi**, **menyesuaikan blur**, dan **menambahkan bayangan shape** secara terpisah.

---

## Terapkan Drop Shadow pada Shape

Ketika orang bertanya “bagaimana cara **menerapkan drop shadow** di C#?”, mereka biasanya hanya membutuhkan toggle visibilitas dan sebuah warna. Potongan kode berikut mengisolasi dua baris tersebut:

```csharp
shape.ShadowFormat.Visible = true;          // Turns the shadow on
shape.ShadowFormat.Color   = Color.Black;   // Classic black drop shadow
```

> **Pro tip:** Jika Anda menargetkan versi Word lama (2003‑2007), gunakan warna standar. Beberapa nilai ARGB eksotis mungkin diabaikan oleh renderer lama.

---

## Cara Mengubah Transparansi Bayangan

Transparansi dinyatakan sebagai **float antara 0 dan 1**. Nilai **0** berarti bayangan sepenuhnya tidak tembus; **1** membuatnya tidak terlihat. Kebanyakan desainer memilih nilai sekitar **0.2‑0.4** untuk tampilan alami.

```csharp
shape.ShadowFormat.Transparency = 0.35; // 35 % transparent
```

### Kasus Tepi

- **Negative values** – Aspose.Words akan memaksa menjadi 0, tetapi lebih baik memvalidasi input.  
- **Values > 1** – Dipaksa menjadi 1, secara efektif menyembunyikan bayangan.  

Jika Anda perlu membiarkan pengguna memilih persentase, konversikan terlebih dahulu:

```csharp
float percent = 30;                     // User enters 30 %
shape.ShadowFormat.Transparency = percent / 100f;
```

---

## Cara Menyesuaikan Blur (Size) Bayangan

Properti **Size** mengontrol radius blur. Angka yang lebih besar menghasilkan bayangan yang lebih lembut dan tersebar. Diukur dalam poin (pt), bukan piksel.

```csharp
shape.ShadowFormat.Size = 10;  // A generous blur for a “soft” effect
```

#### Kapan Menggunakan Blur Kecil vs. Besar

- **Small blur (2‑4 pt)** – Baik untuk callout gaya UI yang menginginkan tepi tajam.  
- **Large blur (8‑12 pt)** – Cocok untuk laporan cetak atau ketika shape berada jauh dari latar belakang.

---

## Tambahkan Bayangan Shape – Penempatan dan Arah

Bagian akhir dari **add shape shadow** adalah offset. Dua properti bekerja bersama:

| Properti | Arti |
|----------|------|
| **Distance** | Seberapa jauh bayangan berada dari shape (dalam poin). |
| **Angle**    | Arah offset (0° = kanan, 90° = bawah, 180° = kiri, 270° = atas). |

Contoh yang membuat bayangan subtle di kanan‑bawah:

```csharp
shape.ShadowFormat.Distance = 1.5; // Slight lift
shape.ShadowFormat.Angle    = 135; // Down‑left direction (135°)
```

Anda dapat bereksperimen dengan sudut untuk mensimulasikan cahaya yang datang dari sumber berbeda. Trik umum adalah membiarkan pengguna memilih “sumber cahaya” dari dropdown dan memetakan ke nilai sudut.

---

## Contoh Lengkap yang Berfungsi (Semua Langkah Digabungkan)

Berikut adalah program yang sama seperti sebelumnya, tetapi dengan **komentar tambahan** yang membuat logika menjadi sangat jelas. Salin ke `Program.cs` dan jalankan; file output akan berisi textbox dengan bayangan yang disetel sempurna.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Load the source document (must contain at least one shape)
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Grab the first shape we encounter – usually a textbox or picture
            Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
            if (shape == null)
            {
                Console.WriteLine("No shape found in the document.");
                return;
            }

            // ---------- Apply Drop Shadow ----------
            shape.ShadowFormat.Visible = true;          // Turn it on
            shape.ShadowFormat.Color   = Color.DarkGray; // Soft dark colour

            // ---------- How to Change Transparency ----------
            shape.ShadowFormat.Transparency = 0.3; // 30 % transparent – looks natural

            // ---------- How to Adjust Blur ----------
            shape.ShadowFormat.Size = 6; // Moderate blur for a professional feel

            // ---------- Add Shape Shadow (position) ----------
            shape.ShadowFormat.Distance = 2; // Slight offset
            shape.ShadowFormat.Angle    = 45; // Diagonal down‑right

            // Save the result
            doc.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("Document saved with shadow. Open output.docx to verify.");
        }
    }
}
```

**Hasil yang diharapkan:** Buka `output.docx`. Textbox pertama akan menampilkan bayangan abu-abu gelap, 30 % transparan, sedikit blur (size = 6) dan offset 2 pt pada sudut 45°. Efeknya halus namun terlihat—tepat seperti yang diinginkan kebanyakan desainer UI.

---

## Pertanyaan Umum & Hal-hal yang Perlu Diwaspadai

- **“Apakah ini juga berfungsi dengan gambar?”**  
  Ya. Setiap `Shape`—baik textbox, gambar, atau auto‑shape—menyediakan `ShadowFormat`. Cukup ganti logika pengambilan shape dengan indeks atau nama yang sesuai.

- **“Bagaimana jika dokumen memiliki banyak shape?”**  
  Loop melalui `doc.GetChildNodes(NodeType.Shape, true)` dan terapkan pengaturan yang sama ke masing‑masing. Anda juga dapat memfilter berdasarkan `shape.Name` atau `shape

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}