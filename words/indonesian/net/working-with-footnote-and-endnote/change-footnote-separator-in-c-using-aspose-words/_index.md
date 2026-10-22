---
category: general
date: 2026-08-04
description: Ubah pemisah catatan kaki di C# menggunakan Aspose.Words – pelajari cara
  mengedit pemisah catatan kaki dan mengubah pemisah catatan akhir dalam dokumen Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote separator
- edit footnote separator
- how to change footnote separator
- change endnote separator
language: id
lastmod: 2026-08-04
og_description: Ubah pemisah catatan kaki di C# dengan Aspose.Words. Panduan ini menunjukkan
  cara mengedit pemisah catatan kaki, menyesuaikan pemisah catatan akhir, dan menyimpan
  dokumen yang diperbarui.
og_image_alt: Screenshot showing the changed footnote separator in a Word document
og_title: Ubah pemisah catatan kaki di C# – panduan lengkap Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Change footnote separator in C# using Aspose.Words – learn how to edit
    footnote separator and change endnote separator in Word documents.
  headline: Change footnote separator in C# using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
- Document processing
title: Ubah pemisah catatan kaki di C# menggunakan Aspose.Words
url: /id/net/working-with-footnote-and-endnote/change-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ubah pemisah catatan kaki di C# menggunakan Aspose.Words

Jika Anda perlu **mengubah pemisah catatan kaki** dalam dokumen Word, tutorial ini akan memandu Anda melalui langkah‑langkah tepat dengan Aspose.Words untuk .NET. Baik Anda ingin mengganti garis default dengan simbol, atau menerapkan gaya berbeda pada pemisah catatan akhir, kode di bawah ini mencakup seluruh alur kerja.

Anda juga akan belajar cara **mengedit pemisah catatan kaki** dan operasi terkait **mengubah pemisah catatan akhir**, sehingga dokumen yang sama dapat memiliki gaya konsisten untuk catatan kaki dan catatan akhir. Tidak diperlukan alat eksternal—hanya beberapa baris C#.

## Apa yang akan Anda capai

* Memuat file *.docx* yang ada yang berisi catatan kaki dan catatan akhir.  
* Mengakses node pemisah untuk catatan kaki, kelanjutan catatan kaki, dan catatan akhir.  
* Mengganti karakter pemisah (misalnya, mengubah garis default menjadi tanda bintang).  
* Menyimpan dokumen yang telah dimodifikasi tanpa kehilangan konten lain.  

Tutorial ini mengasumsikan Anda memiliki pemahaman dasar tentang C# dan telah menginstal paket NuGet **Aspose.Words** (versi 24.9 atau lebih baru).  

---

## Prasyarat

| Requirement | Reason |
|-------------|--------|
| .NET 6.0+ atau .NET Framework 4.7.2+ | Runtime yang diperlukan untuk Aspose.Words |
| Pustaka Aspose.Words untuk .NET | Menyediakan API `Document` dan `FootnoteOptions` |
| File Word input (`input.docx`) dengan setidaknya satu catatan kaki atau catatan akhir | Menunjukkan perubahan pemisah |

Anda dapat menambahkan Aspose.Words ke proyek Anda dengan perintah CLI berikut:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

---

## Langkah 1: Muat dokumen yang berisi catatan kaki

Operasi pertama adalah membaca file sumber ke dalam objek `Document`. Objek ini mewakili seluruh file Word dalam memori dan memberi Anda akses ke semua node-nya.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Load the .docx file that contains footnotes and endnotes.
Document document = new Document(@"C:\Docs\input.docx");
```

**Mengapa ini penting:** Memuat dokumen adalah titik masuk untuk setiap manipulasi. Jika file tidak ditemukan, Aspose.Words akan melempar `FileNotFoundException`, jadi pastikan jalur file sudah benar sebelum melanjutkan.

---

## Langkah 2: Akses node pemisah catatan kaki dan catatan akhir

`Document.FootnoteOptions` menyediakan tiga node pemisah:

* `Separator` – garis yang muncul setelah kumpulan catatan kaki pada halaman pertama.  
* `ContinuationSeparator` – garis yang digunakan ketika catatan kaki berlanjut ke halaman berikutnya.  
* `EndnoteSeparator` – garis yang memisahkan teks utama dari daftar catatan akhir.

Anda mengambil node-node ini sebagai objek `Node` umum, kemudian meng-cast-nya ke `Run` untuk memodifikasi teks.

```csharp
// Retrieve the three separator nodes.
Node footnoteSeparator = document.FootnoteOptions.Separator;
Node footnoteContinuation = document.FootnoteOptions.ContinuationSeparator;
Node endnoteSeparator = document.FootnoteOptions.EndnoteSeparator;
```

**Mengapa ini penting:** Node-node ini adalah satu‑satunya tempat karakter pemisah visual berada. Mengubah node lain (misalnya, paragraf biasa) tidak akan memengaruhi format catatan kaki.

---

## Langkah 3: Ubah karakter pemisah catatan kaki

Kebutuhan paling umum adalah mengganti garis default dengan simbol seperti tanda bintang (`*`). Karena pemisah disimpan sebagai `Run`, Anda dapat dengan aman memodifikasi properti `Text`-nya.

```csharp
// Change the primary footnote separator to an asterisk.
if (footnoteSeparator is Run footnoteRun)
{
    footnoteRun.Text = "*";
}

// Optionally, change the continuation separator as well.
if (footnoteContinuation is Run continuationRun)
{
    continuationRun.Text = "*";
}
```

**Mengapa ini penting:** Mengedit langsung `Run.Text` memperbarui representasi visual dalam dokumen akhir tanpa memengaruhi konten catatan kaki lainnya. Pola yang sama dapat digunakan untuk menerapkan string apa pun, termasuk simbol Unicode.

---

## Langkah 4: Ubah pemisah catatan akhir (opsional)

Jika Anda juga perlu **mengubah pemisah catatan akhir**, prosesnya mirip dengan perubahan catatan kaki. Ganti teks `endnoteSeparator` dengan karakter yang Anda inginkan.

```csharp
// Change the endnote separator to a dash.
if (endnoteSeparator is Run endnoteRun)
{
    endnoteRun.Text = "-";
}
```

**Mengapa ini penting:** Catatan akhir sering memiliki gaya yang berbeda dari catatan kaki. Menyediakan pemisah terpisah memungkinkan Anda menjaga konsistensi visual dengan pedoman desain dokumen Anda.

---

## Langkah 5: Simpan dokumen yang telah dimodifikasi

Setelah semua modifikasi, simpan perubahan menggunakan `Document.Save`. Anda dapat menimpa file asli atau menulis ke lokasi baru.

```csharp
// Save the updated document.
document.Save(@"C:\Docs\ModifiedSeparators.docx");
```

**Mengapa ini penting:** `Save` menulis representasi dalam memori ke disk, mempertahankan semua elemen lain (gaya, gambar, tabel) tetap tidak berubah.

---

## Contoh lengkap yang dapat dijalankan

Menggabungkan semua bagian, berikut adalah aplikasi konsol mandiri yang mendemonstrasikan seluruh alur kerja:

```csharp
using System;
using Aspose.Words;

namespace FootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document.
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Access separator nodes.
            Node footnoteSep = doc.FootnoteOptions.Separator;
            Node footnoteCont = doc.FootnoteOptions.ContinuationSeparator;
            Node endnoteSep = doc.FootnoteOptions.EndnoteSeparator;

            // 3️⃣ Change footnote separator to an asterisk.
            if (footnoteSep is Run footnoteRun)
                footnoteRun.Text = "*";

            // Optional: also change the continuation separator.
            if (footnoteCont is Run contRun)
                contRun.Text = "*";

            // 4️⃣ Change endnote separator to a dash.
            if (endnoteSep is Run endnoteRun)
                endnoteRun.Text = "-";

            // 5️⃣ Save the result.
            string outputPath = @"C:\Docs\ModifiedSeparators.docx";
            doc.Save(outputPath);

            Console.WriteLine("Document saved to " + outputPath);
        }
    }
}
```

**Hasil yang diharapkan:** Buka *ModifiedSeparators.docx* di Microsoft Word. Garis pemisah catatan kaki di bagian bawah halaman catatan kaki pertama kini akan menjadi satu tanda bintang (`*`). Jika dokumen berisi catatan akhir, garis yang memisahkan teks utama dari daftar catatan akhir akan muncul sebagai tanda hubung (`-`). Semua konten lain (teks, gambar, tabel) tetap tidak tersentuh.

---

## Pertanyaan umum & penanganan kasus tepi

| Question | Answer |
|----------|--------|
| **Bagaimana jika dokumen tidak memiliki catatan kaki?** | `FootnoteOptions.Separator` tetap mengembalikan node `Run`, tetapi teksnya mungkin kosong. Kode memeriksa tipe node dengan aman sebelum memodifikasinya. |
| **Apakah saya dapat menggunakan string multi‑karakter (mis., "***")?** | Ya. Properti `Run.Text` menerima string apa pun, termasuk karakter Unicode. |
| **Apakah mengubah pemisah akan memengaruhi penomoran catatan kaki yang ada?** | Tidak. Pemisah bersifat terpisah dari skema penomoran. |
| **Apakah saya perlu membuang (dispose) objek `Document`?** | `Document` mengimplementasikan `IDisposable` secara implisit melalui `Node`. Pada aplikasi konsol yang singkat bersifat opsional, tetapi untuk layanan yang berjalan lama Anda dapat membungkusnya dalam blok `using`. |
| **Bagaimana cara kerja ini dengan .NET Core vs .NET Framework?** | API-nya identik di semua runtime; hanya versi target framework yang penting (harus didukung oleh paket Aspose.Words). |

**Tips pro:** Jika Anda perlu menerapkan pemisah yang berbeda untuk bagian yang berbeda, Anda dapat mengiterasi `doc.GetChildNodes(NodeType.Footnote, true)` dan menyesuaikan properti `Separator` setiap catatan kaki secara individual. Ini lebih lanjutan tetapi berguna untuk dokumen yang kompleks.

---

## Kesimpulan

Anda kini tahu cara **mengubah pemisah catatan kaki** dan **mengubah pemisah catatan akhir** dalam file Word menggunakan Aspose.Words untuk C#. Panduan ini mencakup memuat dokumen, mengakses node pemisah yang relevan, memodifikasi teksnya, dan menyimpan hasilnya—semua dalam satu program mandiri.

Mulai dari sini Anda dapat menjelajahi topik terkait seperti **mengedit gaya pemisah catatan kaki**, menyesuaikan penomoran catatan kaki, atau menerapkan pemformatan bersyarat berdasarkan tata letak halaman. Pola yang sama (mengambil node, cast ke `Run`, memodifikasi `Text`) bekerja untuk banyak skenario pemrosesan Word lainnya.

Selamat coding, dan jangan ragu untuk bereksperimen dengan simbol yang berbeda atau bahkan menyisipkan gambar sebagai pemisah untuk tata letak dokumen yang benar‑benar unik!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Pemrosesan Kata dengan Catatan Kaki dan Catatan Akhir](/words/english/net/working-with-footnote-and-endnote/)
- [Dapatkan Pemisah Gaya Paragraf dalam Dokumen Word](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Sisipkan Pemisah Gaya Dokumen di Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}