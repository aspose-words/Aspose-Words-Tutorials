---
category: general
date: 2026-03-01
description: Simpan dokumen sebagai TXT dengan persamaan LaTeX menggunakan Aspose.Words.
  Pelajari cara mengonversi Word ke LaTeX dan mengekspor persamaan dengan mudah.
draft: false
keywords:
- save document as txt
- convert word to latex
- how to save txt
- how to export equations
- export equations to latex
language: id
og_description: Simpan dokumen sebagai TXT dengan persamaan LaTeX menggunakan Aspose.Words.
  Pelajari cara mengonversi Word ke LaTeX dan mengekspor persamaan dengan mudah.
og_title: Simpan Dokumen sebagai TXT – Ekspor Persamaan Word ke LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
- Text Export
title: Simpan Dokumen sebagai TXT – Ekspor Persamaan Word ke LaTeX
url: /id/net/programming-with-txtsaveoptions/save-document-as-txt-export-word-equations-to-latex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Simpan Dokumen sebagai TXT – Ekspor Persamaan Word ke LaTeX

Pernah perlu **save document as txt** tetapi khawatir persamaan Word Anda yang indah akan hilang? Anda bukan satu‑satunya. Banyak pengembang mengalami hal ini ketika mencoba mengekstrak plain‑text dari .docx yang berisi objek Office Math. Kabar baiknya? Dengan Aspose.Words Anda dapat **save document as txt** *dan* mempertahankan setiap persamaan dalam sintaks LaTeX yang bersih.

Dalam tutorial ini kami akan menjelaskan cara mengonversi file Word menjadi file plain‑text yang berisi persamaan berformat LaTeX. Sepanjang proses kami akan menjawab “how to export equations”, menunjukkan **how to save txt** secara programatis, dan bahkan membahas sudut “convert word to latex” bagi mereka yang membutuhkan matematika dalam makalah ilmiah. Tanpa basa‑basi—hanya solusi lengkap yang dapat dijalankan dan dapat Anda masukkan ke proyek .NET mana pun.

## Apa yang Akan Anda Dapatkan

- Panduan langkah‑demi‑langkah yang dimulai dengan aplikasi konsol .NET baru dan berakhir dengan file `Equations.txt` yang penuh LaTeX.
- Pemahaman *mengapa* `OfficeMathExportMode.LaTeX` adalah pilihan tepat untuk mempertahankan matematika.
- Tips untuk menangani banyak persamaan, tata letak kompleks, dan jebakan umum seperti font yang hilang.
- Contoh kode siap‑jalankan yang dapat Anda salin, tempel, dan eksekusi segera.

> **Prerequisite checklist**  
> - .NET 6.0 atau lebih baru (Anda juga dapat menggunakan .NET Framework 4.8, tetapi semakin baru semakin baik).  
> - Paket NuGet Aspose.Words untuk .NET (`Install-Package Aspose.Words`).  
> - Dokumen Word yang berisi setidaknya satu persamaan (kami akan menyebutnya `Sample.docx`).  

![contoh menyimpan dokumen sebagai txt](image.png "contoh menyimpan dokumen sebagai txt")

## Langkah 1 – Instal Aspose.Words dan Buat Proyek Konsol

Hal pertama yang harus dilakukan. Buka IDE favorit Anda (Visual Studio, Rider, atau bahkan VS Code) dan buat proyek konsol baru:

```bash
dotnet new console -n TxtExportDemo
cd TxtExportDemo
dotnet add package Aspose.Words
```

Baris satu itu mengambil binari Aspose.Words terbaru dan menambahkannya ke file proyek Anda. Menurut pengalaman saya, menggunakan versi terbaru (saat ini 24.10) menghindari sejumlah bug obscure terkait penanganan Office Math.

## Langkah 2 – Muat Dokumen Word

Sekarang kita memerlukan objek `Document` yang mewakili .docx yang ingin kita ubah. Pernyataan `using` memastikan file dibuang dengan bersih.

```csharp
using Aspose.Words;

class Program
{
    static void Main()
    {
        // Load the source Word file – make sure the path is correct.
        Document doc = new Document(@"C:\Path\To\Sample.docx");
        // The rest of the code follows…
    }
}
```

Mengapa memuatnya dengan cara ini? `Document` mengurai seluruh paket OpenXML, menampilkan gambar, tabel, dan—yang paling penting—node `OfficeMath` yang menyimpan persamaan Anda. Tanpa memuat dokumen terlebih dahulu, tidak ada yang dapat diekspor.

## Langkah 3 – Konfigurasikan Opsi Penyimpanan TXT untuk Mengekspor Persamaan sebagai LaTeX

Inilah inti tutorial. Secara default, menyimpan sebagai plain‑text menghapus semua kecuali karakter mentah. Menetapkan `OfficeMathExportMode` ke `LaTeX` memberi tahu Aspose.Words untuk mengganti setiap node `OfficeMath` dengan representasi LaTeX-nya.

```csharp
// Step 3: Configure TXT save options to export Office Math as LaTeX
TxtSaveOptions txtSaveOptions = new TxtSaveOptions
{
    // This converts every equation into LaTeX syntax.
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
};
```

**Mengapa LaTeX?** LaTeX adalah bahasa universal penerbitan ilmiah. Ketika Anda kemudian memasukkan file `.txt` yang dihasilkan ke editor LaTeX atau prosesor markdown yang memahami `$…$`, persamaan akan ditampilkan dengan sempurna. Jika Anda lebih suka MathML atau Unicode biasa, Aspose.Words juga mendukung mode tersebut—cukup ganti nilai enum.

## Langkah 4 – Simpan Dokumen sebagai File Plain‑Text

Dengan opsi yang sudah diatur, panggilan save menjadi satu baris. Nama file dapat apa saja yang Anda suka; kami akan tetap menggunakan `Equations.txt` agar jelas.

```csharp
// Step 4: Save the document as a plain‑text file with the configured options
doc.Save(@"C:\Path\To\Equations.txt", txtSaveOptions);
```

Menjalankan program sekarang menghasilkan `Equations.txt` yang terlihat kira‑kira seperti ini:

```
This is a sample paragraph.

The quadratic formula is given by:
\[
x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
\]

Another equation:
\[
E = mc^2
\]
```

Perhatikan delimiter `\[` … `\]`—itu adalah penanda “display math” LaTeX yang dikenali secara otomatis oleh banyak editor.

## Langkah 5 – Verifikasi Output (dan Apa yang Harus Dilakukan Jika Terlihat Aneh)

Buka file yang dihasilkan di editor teks apa pun. Jika Anda melihat string LaTeX mentah, Anda berhasil. Jika persamaan muncul sebagai karakter kacau, periksa dua hal:

1. **OfficeMathExportMode** – pastikan diatur ke `LaTeX`.  
2. **Versi Dokumen** – file .doc lama kadang menyimpan persamaan dalam format proprietari; konversikan ke .docx terlebih dahulu.

Pemeriksaan cepat adalah menempelkan konten ke renderer LaTeX online (seperti Overleaf). Jika persamaan ditampilkan, Anda berhasil.

## Langkah 6 – Kasus Tepi & Tips Lanjutan

### Beberapa Persamaan dalam Satu Paragraf

Ketika beberapa objek `OfficeMath` berada berdampingan, Aspose.Words menyisipkan spasi di antara setiap blok LaTeX. Jika Anda memerlukan kontrol lebih ketat (misalnya, persamaan inline dipisahkan koma), lakukan pasca‑proses pada file txt:

```csharp
string txt = File.ReadAllText(@"C:\Path\To\Equations.txt");
txt = txt.Replace(@"\] \[", @"\]\,\[" ); // adds a thin space between display blocks
File.WriteAllText(@"C:\Path\To\Equations.txt", txt);
```

### Mempertahankan Pemformatan Non‑Matematika

Plain‑text tidak dapat menyimpan gaya tebal atau miring, tetapi Anda dapat meminta Aspose.Words menambahkan penanda markdown:

```csharp
txtSaveOptions.AdditionalExportOptions = TxtExportOptions.Markdown;
```

Sekarang teks tebal muncul sebagai `**bold**`, dan miring sebagai `_italic_`. Ini berguna jika Anda kemudian mengalirkan file ke generator situs statis.

### Mengekspor ke Format Matematika Lain

Jika alat hilir Anda lebih menyukai MathML, cukup ganti:

```csharp
txtSaveOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
```

Sisa alur kerja tetap identik—menunjukkan betapa mudahnya **convert word to latex** *atau* format lain dengan satu perubahan baris.

## Pertanyaan yang Sering Diajukan

**T: Apakah ini bekerja di .NET Core?**  
J: Tentu saja. Aspose.Words bersifat lintas‑platform, jadi kode yang sama berjalan di Windows, Linux, atau macOS.

**T: Bagaimana dengan file Word yang dilindungi kata sandi?**  
J: Muat mereka dengan `LoadOptions` yang menyertakan kata sandi, lalu lanjutkan seperti biasa.

```csharp
LoadOptions loadOpts = new LoadOptions { Password = "mySecret" };
Document protectedDoc = new Document(@"C:\Path\Protected.docx", loadOpts);
```

**T: Bisakah saya mengekspor hanya persamaan, melewatkan teks biasa?**  
J: Ya. Iterasi melalui `doc.GetChildNodes(NodeType.OfficeMath, true)` dan tulis LaTeX setiap node ke file secara manual. Itu cara yang bagus untuk **export equations to latex** ketika Anda tidak memerlukan teks di sekitarnya.

## Ringkasan – Simpan Dokumen sebagai TXT dengan Persamaan LaTeX dalam Satu Langkah

Kita memulai dengan pertanyaan sederhana: *bagaimana cara menyimpan file Word sebagai txt sambil mempertahankan matematika?* Dengan menginstal Aspose.Words, memuat dokumen, mengkonfigurasi `TxtSaveOptions` dengan `OfficeMathExportMode.LaTeX`, dan memanggil `doc.Save`, Anda kini memiliki pipeline handal yang **save document as txt** dan **export equations to latex**.  

Dari sini Anda dapat:

- **Convert Word to LaTeX** untuk seluruh manuskrip.  
- Menggunakan txt yang dihasilkan sebagai input untuk generator situs statis yang mendukung LaTeX.  
- Memperluas skrip untuk memproses batch folder file Word.  

Cobalah, bereksperimen dengan mode ekspor, dan biarkan file LaTeX plain‑text melakukan pekerjaan berat untuk makalah riset atau proyek dokumentasi Anda berikutnya.

*Selamat coding, semoga persamaan Anda selalu ditampilkan dengan indah!*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}