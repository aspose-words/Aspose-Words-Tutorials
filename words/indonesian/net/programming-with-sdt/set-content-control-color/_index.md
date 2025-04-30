---
"description": "Atur warna Tag Dokumen Terstruktur di Word dengan mudah menggunakan Aspose.Words untuk .NET. Sesuaikan SDT Anda untuk meningkatkan tampilan dokumen dengan panduan sederhana ini."
"linktitle": "Atur Warna Kontrol Konten"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Atur Warna Kontrol Konten"
"url": "/id/net/programming-with-sdt/set-content-control-color/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Atur Warna Kontrol Konten

## Perkenalan

Jika Anda bekerja dengan dokumen Word dan perlu menyesuaikan tampilan Structured Document Tags (SDT), Anda mungkin ingin mengubah warnanya. Ini sangat berguna saat Anda menangani formulir atau templat yang memerlukan pembedaan elemen secara visual. Dalam panduan ini, kami akan memandu Anda melalui proses pengaturan warna SDT menggunakan Aspose.Words untuk .NET.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:
- Aspose.Words untuk .NET: Anda perlu menginstal pustaka ini. Anda dapat mengunduhnya dari [Situs web Aspose](https://releases.aspose.com/words/net/).
- Pemahaman dasar tentang C#: Tutorial ini mengasumsikan Anda familier dengan konsep dasar pemrograman C#.
- Dokumen Word: Anda harus memiliki dokumen Word yang berisi setidaknya satu Tag Dokumen Terstruktur.

## Mengimpor Ruang Nama

Pertama, Anda perlu mengimpor namespace yang diperlukan dalam proyek C# Anda. Tambahkan perintah berikut di bagian atas berkas kode Anda:

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
using System.Drawing;
```

## Langkah 1: Siapkan Jalur Dokumen Anda

Tentukan jalur ke direktori dokumen Anda dan muat dokumen:

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Langkah 2: Muat Dokumen

Membuat sebuah `Document` objek dengan memuat file Word Anda:

```csharp
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## Langkah 3: Akses Tag Dokumen Terstruktur

Ambil Structured Document Tag (SDT) dari dokumen. Dalam contoh ini, kita mengakses SDT pertama:

```csharp
StructuredDocumentTag sdt = (StructuredDocumentTag) doc.GetChild(NodeType.StructuredDocumentTag, 0, true);
```

## Langkah 4: Mengatur Warna SDT

Ubah properti warna SDT. Di sini, kita atur warnanya menjadi merah:

```csharp
sdt.Color = Color.Red;
```

## Langkah 5: Simpan Dokumen

Simpan dokumen yang diperbarui ke file baru:

```csharp
doc.Save(dataDir + "WorkingWithSdt.SetContentControlColor.docx");
```

## Kesimpulan

Mengubah warna Tag Dokumen Terstruktur dalam dokumen Word menggunakan Aspose.Words untuk .NET sangatlah mudah. Dengan mengikuti langkah-langkah yang diuraikan di atas, Anda dapat dengan mudah menerapkan perubahan visual pada SDT Anda, meningkatkan tampilan dan fungsionalitas dokumen Anda.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menggunakan warna yang berbeda untuk SDT?

Ya, Anda dapat menggunakan warna apa pun yang tersedia di `System.Drawing.Color` kelas. Misalnya, Anda dapat menggunakan `Color.Blue`Bahasa Indonesia: `Color.Green`, dll.

### Bagaimana cara mengubah warna beberapa SDT dalam satu dokumen?

Anda perlu mengulang semua SDT dalam dokumen dan menerapkan perubahan warna pada masing-masing SDT. Anda dapat melakukannya dengan menggunakan pengulangan yang berulang pada semua SDT.

### Apakah mungkin untuk mengatur properti SDT lainnya selain warna?

Ya, itu `StructuredDocumentTag` class memiliki berbagai properti yang dapat Anda atur, termasuk ukuran font, gaya font, dan banyak lagi. Lihat dokumentasi Aspose.Words untuk detail lebih lanjut.

### Bisakah saya menambahkan acara ke SDT, seperti acara klik?

Aspose.Words tidak secara langsung mendukung penanganan peristiwa untuk SDT. Namun, Anda dapat mengelola interaksi SDT melalui kolom formulir atau menggunakan metode lain untuk menangani masukan dan interaksi pengguna.

### Apakah mungkin untuk menghapus SDT dari dokumen?

Ya, Anda dapat menghapus SDT dengan menelepon `Remove()` metode pada node induk SDT.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}