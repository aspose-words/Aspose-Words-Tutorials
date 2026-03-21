---
category: general
date: 2026-03-21
description: Buat folder aset saat mengonversi DOCX ke Markdown. Pelajari cara mengekstrak
  gambar dari Word dan menyimpan Word sebagai Markdown dalam C#.
draft: false
keywords:
- create assets folder
- convert docx to markdown
- extract images from word
- extract embedded images
- save word as markdown
language: id
og_description: Buat folder aset saat mengonversi DOCX ke Markdown. Tutorial ini menunjukkan
  cara mengekstrak gambar dari Word dan menyimpan Word sebagai Markdown menggunakan
  C#.
og_title: Buat folder aset dan konversi DOCX ke Markdown – Panduan Lengkap
tags:
- Aspose.Words
- C#
- Document Conversion
title: Buat folder aset dan konversi DOCX ke Markdown dengan Aspose.Words
url: /id/net/programming-with-markdownsaveoptions/create-assets-folder-and-convert-docx-to-markdown-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat folder assets dan konversi DOCX ke Markdown dengan Aspose.Words

Pernah perlu **membuat folder assets** saat mengubah file Word menjadi Markdown? Anda bukan satu‑satunya—para pengembang terus menanyakan cara menjaga gambar tetap rapi saat mereka *mengonversi docx ke markdown*. Kabar baiknya, Aspose.Words memberi Anda cara bersih dan programatik untuk melakukan keduanya dalam satu proses.

Dalam tutorial ini kita akan melangkah melalui seluruh proses: memuat `.docx`, mengonfigurasi exporter Markdown, mengekstrak gambar yang disematkan, dan akhirnya menyimpan hasilnya sebagai file `.md` yang merujuk ke direktori `assets`. Pada akhir tutorial Anda akan memiliki potongan kode yang dapat digunakan kembali untuk *mengekstrak gambar dari Word* dan *menyimpan Word sebagai markdown* tanpa menyalin‑tempel manual.

## Apa yang Anda Butuhkan

- **Aspose.Words untuk .NET** (versi terbaru, misalnya 24.10).  
- Lingkungan pengembangan .NET (Visual Studio, Rider, atau VS Code).  
- Contoh `input.docx` yang berisi setidaknya satu gambar—jika tidak, Anda tidak akan melihat langkah *ekstrak gambar yang disematkan* beraksi.

Tidak ada pustaka pihak ketiga lain yang diperlukan; semuanya berada di dalam Aspose.Words.

---

## Buat folder assets dan siapkan konversi Markdown

Hal pertama yang kita inginkan adalah folder khusus tempat setiap gambar yang diekstrak dari dokumen Word akan disimpan. Anggap saja ini sebagai “bucket assets” yang sering Anda lihat pada generator situs statis. Kita biarkan Aspose.Words menentukan nama file, lalu kita tambahkan jalur folder.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// 1️⃣ Load the source Word document
Document document = new Document("YOUR_DIRECTORY/input.docx");

// 2️⃣ Prepare Markdown save options with a callback that decides where resources go
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new ResourceSavingCallback(info =>
    {
        // 👉 Define the folder that will hold every extracted image
        string assetsFolder = Path.Combine("YOUR_DIRECTORY", "assets");
        Directory.CreateDirectory(assetsFolder); // creates it if it doesn't exist

        // 👉 Tell Aspose to place the current resource inside that folder
        info.FileName = Path.Combine(assetsFolder, info.FileName);
    })
};
```

> **Mengapa callback?**  
> `ResourceSavingCallback` dipicu untuk setiap objek yang disematkan (gambar, objek OLE, dll.). Dengan menangkapnya kita dapat **mengekstrak gambar dari Word** secara langsung, alih‑alih menyimpannya di tempat lain lalu memindahkannya kemudian. Ini membuat langkah *save word as markdown* menjadi atomik dan mengurangi beban I/O.

---

## Langkah 1: Muat dokumen DOCX  

Sebelum kita dapat *mengonversi docx ke markdown*, kita memerlukan instance `Document`. Konstruktornya menerima path, stream, atau bahkan byte array—pilih yang paling cocok dengan alur kerja Anda.

```csharp
// Example using a relative path; adjust for your environment
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

> **Tip:** Jika Anda memproses unggahan di API web, lewati file sementara dengan langsung memberikan `Stream` yang di‑upload ke konstruktor.

---

## Langkah 2: Konfigurasikan MarkdownSaveOptions – inti dari ekstraksi  

`MarkdownSaveOptions` memberi Anda kontrol detail atas perilaku konversi. Properti terpenting untuk tujuan kita adalah `ResourceSavingCallback`, yang sudah kita siapkan. Anda juga dapat menyesuaikan format gambar, gaya tautan, dan lain‑lain.

```csharp
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    // Ensure images are saved as PNG by default (you can change this)
    ImageSavingFormat = ImageSaveOptions.SaveFormat.Png,

    // The callback defined earlier handles the assets folder creation
    ResourceSavingCallback = new ResourceSavingCallback(info =>
    {
        string assetsFolder = Path.Combine("YOUR_DIRECTORY", "assets");
        Directory.CreateDirectory(assetsFolder);
        info.FileName = Path.Combine(assetsFolder, info.FileName);
    })
};
```

> **Bagaimana jika dua gambar memiliki nama yang sama?**  
> Aspose secara otomatis menambahkan sufiks numerik (`image.png`, `image_1.png`, …) sehingga tidak ada file yang hilang.

---

## Langkah 3: Definisikan folder assets dan tangani jalur gambar  

Callback dijalankan *sekali per sumber daya*. Di dalamnya kita:

1. Membuat jalur absolut ke folder `assets` menggunakan `Path.Combine`.  
2. Memanggil `Directory.CreateDirectory`—ini aman dipanggil berulang kali; folder hanya dibuat pada pemanggilan pertama.  
3. Menimpa `info.FileName` dengan jalur lengkap, memastikan penulis Markdown menulis tautan relatif yang benar.

```csharp
ResourceSavingCallback = new ResourceSavingCallback(info =>
{
    string assetsFolder = Path.Combine("YOUR_DIRECTORY", "assets");
    Directory.CreateDirectory(assetsFolder);
    info.FileName = Path.Combine(assetsFolder, info.FileName);
})
```

> **Pro tip:** Jika Anda ingin file Markdown merujuk gambar dengan URL yang ramah web (misalnya `/static/assets/`), ganti `Path.Combine` dengan string yang membangun URL relatif yang diinginkan.

---

## Langkah 4: Simpan dokumen sebagai Markdown  

Setelah semuanya terhubung, baris terakhir cukup dengan `Save`. Aspose akan menelusuri DOM Word, menulis sintaks Markdown ke `output.md`, dan menaruh setiap gambar ke dalam direktori `assets` yang telah kita buat.

```csharp
// 5️⃣ Perform the conversion – this writes both the .md file and the images
document.Save("YOUR_DIRECTORY/output.md", markdownSaveOptions);
```

Saat proses selesai Anda akan melihat struktur folder serupa dengan:

```
YOUR_DIRECTORY/
├─ input.docx
├─ output.md
└─ assets/
   ├─ image1.png
   └─ image2.png
```

*Gambar 1: Tata letak folder setelah konversi (teks alternatif: “create assets folder diagram”).*  

File Markdown akan berisi tautan seperti `![](assets/image1.png)`, yang persis seperti yang diharapkan oleh kebanyakan generator situs statis.

---

## Contoh Lengkap yang Siap Pakai  

Berikut adalah program siap salin‑tempel yang dapat Anda jalankan sebagai aplikasi konsol. Ganti `YOUR_DIRECTORY` dengan jalur yang berisi file sumber Anda.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

class Program
{
    static void Main()
    {
        // 👉 Step 1 – Load the DOCX you want to convert
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 👉 Step 2 – Set up Markdown options and the assets folder callback
        MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
        {
            // Optional: force PNG output for all images
            ImageSavingFormat = ImageSaveOptions.SaveFormat.Png,

            // This callback runs for each extracted resource (image, etc.)
            ResourceSavingCallback = new ResourceSavingCallback(info =>
            {
                // 👉 Define where the extracted images will live
                string assetsFolder = Path.Combine("YOUR_DIRECTORY", "assets");
                Directory.CreateDirectory(assetsFolder);

                // 👉 Save each image inside that folder
                info.FileName = Path.Combine(assetsFolder, info.FileName);
            })
        };

        // 👉 Step 3 – Save as Markdown; assets are created automatically
        document.Save("YOUR_DIRECTORY/output.md", markdownSaveOptions);

        // 🎉 Done! Check YOUR_DIRECTORY for output.md and the assets folder.
    }
}
```

### Hasil yang Diharapkan

- `output.md` berisi teks Markdown yang mencerminkan heading, daftar berpoin, dan tabel Word asli.  
- Setiap gambar dari `input.docx` muncul sebagai `![](assets/<imageName>.png)` di dalam file Markdown.  
- Folder `assets` menyimpan file PNG sebenarnya, siap disajikan oleh host situs statis mana pun.

---

## Pertanyaan Umum & Kasus Tepi

| Pertanyaan | Jawaban |
|------------|---------|
| **Bagaimana jika DOCX tidak memiliki gambar?** | Callback tidak pernah dipanggil, sehingga folder `assets` tetap kosong. Tidak ada masalah. |
| **Bisakah saya mengubah format gambar menjadi JPEG?** | Ya—atur `ImageSavingFormat = ImageSaveOptions.SaveFormat.Jpeg` di dalam `MarkdownSaveOptions`. |
| **Apakah saya perlu membersihkan folder assets pada run berikutnya?** | Sebaiknya hapus atau timpa file lama jika Anda menghasilkan ulang file Markdown yang sama, agar tidak menumpuk gambar tak terpakai. |
| **Bagaimana cara kerja tautan relatif di OS yang berbeda?** | Karena kami menggunakan `Path.Combine` untuk jalur fisik dan Aspose menulis tautan *relatif* (`assets/image.png`), Markdown berfungsi di Windows, macOS, dan Linux. |
| **Bisakah saya mengemas folder assets ke dalam zip?** | Tentu—setelah konversi cukup zip `output.md` bersama direktori `assets`. Tautan Markdown tetap valid selama struktur folder dipertahankan. |

---

## Langkah Selanjutnya

Setelah Anda tahu cara **membuat folder assets**, **mengonversi docx ke markdown**, dan **mengekstrak gambar dari Word**, Anda mungkin ingin menjelajahi:

- **Menyesuaikan gaya Markdown** – aktifkan `ExportHeadersAsBold`, `ExportTableHeaders`, dan flag lain di `MarkdownSaveOptions`.  
- **Pemrosesan batch** – iterasi melalui direktori berisi file `.docx` dan hasilkan pasangan Markdown/asset yang cocok.  
- **Integrasi dengan generator situs statis** seperti Hugo atau Jekyll, yang mengharapkan tata letak folder persis seperti yang baru saja kita buat.  

Jika Anda tertarik pada skenario lanjutan—misalnya mempertahankan catatan kaki Word atau menangani objek OLE yang disematkan—lihat dokumentasi resmi Aspose.Words (cari “MarkdownSaveOptions” dan “ResourceSavingCallback”).

---

## Kesimpulan

Kita baru saja menelusuri solusi lengkap, end‑to‑end yang **membuat folder assets**, **mengekstrak gambar yang disematkan**, dan **menyimpan dokumen Word sebagai Markdown** menggunakan Aspose.Words untuk .NET. Inti pentingnya adalah `ResourceSavingCallback` yang memberi Anda kontrol penuh atas tempat setiap gambar disimpan, sehingga Markdown Anda tetap rapi dan siap dipublikasikan.

Cobalah, ubah format gambar, atau bungkus logika ini ke dalam layanan yang dapat dipakai kembali—apa pun yang Anda pilih, kini Anda memiliki fondasi yang kuat untuk alur kerja *convert docx to markdown* yang perlu *extract images from word* dan *save word as markdown*.

Selamat coding! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}