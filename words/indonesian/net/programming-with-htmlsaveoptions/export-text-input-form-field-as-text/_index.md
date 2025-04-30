---
"description": "Pelajari cara mengekspor bidang formulir input teks sebagai teks biasa menggunakan Aspose.Words untuk .NET dengan panduan langkah demi langkah yang komprehensif ini."
"linktitle": "Ekspor Bidang Formulir Input Teks Sebagai Teks"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Ekspor Bidang Formulir Input Teks Sebagai Teks"
"url": "/id/net/programming-with-htmlsaveoptions/export-text-input-form-field-as-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ekspor Bidang Formulir Input Teks Sebagai Teks

## Perkenalan

Jadi, Anda menyelami dunia Aspose.Words untuk .NET? Pilihan yang luar biasa! Jika Anda ingin mempelajari cara mengekspor kolom formulir input teks sebagai teks, Anda berada di tempat yang tepat. Baik Anda baru memulai atau sedang mengasah keterampilan, panduan ini akan memandu Anda melalui semua hal yang perlu Anda ketahui. Mari kita mulai, ya?

## Prasyarat

Sebelum kita masuk ke inti pembahasan, mari pastikan Anda memiliki semua yang dibutuhkan agar dapat mengikuti dengan lancar:

- Aspose.Words untuk .NET: Unduh dan instal versi terbaru dari [Di Sini](https://releases.aspose.com/words/net/).
- IDE: Visual Studio atau lingkungan pengembangan C# apa pun.
- Pengetahuan Dasar C#: Memahami sintaksis dasar C# dan konsep pemrograman berorientasi objek.
- Dokumen: Contoh dokumen Word (`Rendering.docx`) dengan kolom formulir masukan teks.

## Mengimpor Ruang Nama

Pertama-tama, Anda perlu mengimpor namespace yang diperlukan. Namespace ini seperti blok penyusun yang membuat semuanya berjalan lancar.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

Baiklah, sekarang setelah namespace kita siap, mari kita mulai aksinya!

## Langkah 1: Siapkan Proyek

Sebelum kita masuk ke kode, mari pastikan proyek kita telah disiapkan dengan benar.

## Membuat Proyek

1. Buka Visual Studio: Mulailah dengan membuka Visual Studio atau lingkungan pengembangan C# pilihan Anda.
2. Buat Proyek Baru: Navigasi ke `File > New > Project`Pilih `Console App (.NET Core)` atau jenis proyek relevan lainnya.
3. Beri Nama Proyek Anda: Berikan proyek Anda nama yang bermakna, seperti `AsposeWordsExportExample`.

## Menambahkan Aspose.Words

1. Kelola Paket NuGet: Klik kanan pada proyek Anda di Solution Explorer dan pilih `Manage NuGet Packages`.
2. Cari Aspose.Words: Di Pengelola Paket NuGet, cari `Aspose.Words`.
3. Instal Aspose.Words: Klik `Install` untuk menambahkan pustaka Aspose.Words ke proyek Anda.

## Langkah 2: Muat Dokumen Word

Sekarang proyek kita sudah disiapkan, mari muat dokumen Word yang berisi kolom formulir masukan teks.

1. Tentukan Direktori Dokumen: Tentukan jalur ke direktori tempat dokumen Anda disimpan.
2. Muat Dokumen: Gunakan `Document` kelas untuk memuat dokumen Word Anda.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Langkah 3: Siapkan Direktori Ekspor

Sebelum mengekspor, pastikan direktori ekspor kita sudah siap. Di sinilah berkas HTML dan gambar akan disimpan.

1. Tentukan Direktori Ekspor: Tentukan jalur tempat file yang diekspor akan disimpan.
2. Periksa dan Bersihkan Direktori: Pastikan direktori ada dan kosong.

```csharp
string imagesDir = Path.Combine(dataDir, "Images");

if (Directory.Exists(imagesDir))
    Directory.Delete(imagesDir, true);

Directory.CreateDirectory(imagesDir);
```

## Langkah 4: Konfigurasikan Opsi Penyimpanan

Di sinilah keajaiban terjadi. Kita perlu mengatur opsi penyimpanan untuk mengekspor kolom formulir input teks sebagai teks biasa.

1. Buat Opsi Simpan: Inisialisasi baru `HtmlSaveOptions` obyek.
2. Atur Opsi Teks Ekspor: Konfigurasikan `ExportTextInputFormFieldAsText` properti untuk `true`.
3. Atur Folder Gambar: Tentukan folder tempat gambar akan disimpan.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    ExportTextInputFormFieldAsText = true,
    ImagesFolder = imagesDir
};
```

## Langkah 5: Simpan Dokumen sebagai HTML

Terakhir, mari simpan dokumen Word sebagai berkas HTML menggunakan opsi penyimpanan yang telah dikonfigurasikan.

1. Tentukan Jalur Keluaran: Tentukan jalur tempat file HTML akan disimpan.
2. Simpan Dokumen: Gunakan `Save` metode dari `Document` kelas untuk mengekspor dokumen.

```csharp
doc.Save(dataDir + "ExportedDocument.html", saveOptions);
```

## Kesimpulan

Nah, itu dia! Anda telah berhasil mengekspor kolom formulir input teks sebagai teks biasa menggunakan Aspose.Words untuk .NET. Panduan ini seharusnya memberi Anda pendekatan yang jelas dan bertahap untuk mencapai tugas ini. Ingat, latihan membuat sempurna, jadi teruslah bereksperimen dengan berbagai opsi dan pengaturan untuk melihat apa lagi yang dapat Anda lakukan dengan Aspose.Words.

## Pertanyaan yang Sering Diajukan

### Bisakah saya mengekspor jenis bidang formulir lain menggunakan metode yang sama?

Ya, Anda dapat mengekspor jenis bidang formulir lainnya dengan mengonfigurasi properti yang berbeda `HtmlSaveOptions` kelas.

### Bagaimana jika dokumen saya memiliki gambar?

Gambar akan disimpan di folder gambar yang ditentukan. Pastikan untuk mengatur `ImagesFolder` properti di `HtmlSaveOptions`.

### Apakah saya memerlukan lisensi untuk Aspose.Words?

Ya, Anda bisa mendapatkan uji coba gratis [Di Sini](https://releases.aspose.com/) atau membeli lisensi [Di Sini](https://purchase.aspose.com/buy).

### Bisakah saya menyesuaikan HTML yang diekspor?

Tentu saja! Aspose.Words menyediakan berbagai pilihan untuk menyesuaikan output HTML. Lihat [dokumentasi](https://reference.aspose.com/words/net/) untuk lebih jelasnya.

### Apakah Aspose.Words kompatibel dengan .NET Core?

Ya, Aspose.Words kompatibel dengan .NET Core, .NET Framework, dan platform .NET lainnya.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}