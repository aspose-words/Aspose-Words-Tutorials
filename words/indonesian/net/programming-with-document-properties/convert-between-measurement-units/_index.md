---
title: Konversi Antar Satuan Pengukuran
linktitle: Konversi Antar Satuan Pengukuran
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara mengonversi satuan ukuran di Aspose.Words untuk .NET. Ikuti panduan langkah demi langkah kami untuk mengatur margin, header, dan footer dokumen dalam inci dan poin.
weight: 10
url: /id/net/programming-with-document-properties/convert-between-measurement-units/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Konversi Antar Satuan Pengukuran

## Perkenalan

Hai! Apakah Anda seorang pengembang yang bekerja dengan dokumen Word menggunakan Aspose.Words untuk .NET? Jika demikian, Anda mungkin sering merasa perlu mengatur margin, header, atau footer dalam satuan pengukuran yang berbeda. Mengonversi antarsatuan seperti inci dan poin bisa jadi sulit jika Anda tidak familier dengan fungsi pustaka tersebut. Dalam tutorial komprehensif ini, kami akan memandu Anda melalui proses konversi antarsatuan pengukuran menggunakan Aspose.Words untuk .NET. Mari kita bahas dan sederhanakan konversi tersebut!

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

1.  Pustaka Aspose.Words untuk .NET: Jika Anda belum memilikinya, unduhlah[Di Sini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Visual Studio atau IDE lain yang kompatibel dengan .NET.
3. Pengetahuan Dasar C#: Memahami dasar-dasar C# akan membantu Anda mengikutinya dengan mudah.
4.  Lisensi Aspose: Opsional tetapi direkomendasikan untuk fungsionalitas penuh. Anda dapat memperoleh lisensi sementara[Di Sini](https://purchase.aspose.com/temporary-license/).

## Mengimpor Ruang Nama

Pertama, Anda perlu mengimpor namespace yang diperlukan. Ini penting untuk mengakses kelas dan metode yang disediakan oleh Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Layout;
```

Mari kita bahas proses konversi satuan ukuran di Aspose.Words untuk .NET. Ikuti langkah-langkah terperinci berikut untuk mengatur dan menyesuaikan margin dan jarak dokumen Anda.

## Langkah 1: Buat Dokumen Baru

Pertama, Anda perlu membuat dokumen baru menggunakan Aspose.Words.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Ini menginisialisasi dokumen Word baru dan`DocumentBuilder` untuk memfasilitasi pembuatan dan pemformatan konten.

## Langkah 2: Akses Pengaturan Halaman

 Untuk mengatur margin, header, dan footer, Anda perlu mengakses`PageSetup` obyek.

```csharp
PageSetup pageSetup = builder.PageSetup;
```

Ini memberi Anda akses ke berbagai properti pengaturan halaman seperti margin, jarak header, dan jarak footer.

## Langkah 3: Ubah Inci ke Poin

 Aspose.Words menggunakan poin sebagai satuan pengukuran secara default. Untuk mengatur margin dalam inci, Anda perlu mengonversi inci ke poin menggunakan`ConvertUtil.InchToPoint` metode.

```csharp
pageSetup.TopMargin = ConvertUtil.InchToPoint(1.0);
pageSetup.BottomMargin = ConvertUtil.InchToPoint(1.0);
pageSetup.LeftMargin = ConvertUtil.InchToPoint(1.5);
pageSetup.RightMargin = ConvertUtil.InchToPoint(1.5);
pageSetup.HeaderDistance = ConvertUtil.InchToPoint(0.2);
pageSetup.FooterDistance = ConvertUtil.InchToPoint(0.2);
```

Berikut rincian fungsi masing-masing baris:
- Mengatur margin atas dan bawah menjadi 1 inci (dikonversi ke poin).
- Mengatur margin kiri dan kanan menjadi 1,5 inci (dikonversi ke poin).
- Mengatur jarak header dan footer ke 0,2 inci (dikonversi ke poin).

## Langkah 4: Simpan Dokumen

Terakhir, simpan dokumen Anda untuk memastikan semua perubahan diterapkan.

```csharp
doc.Save("ConvertedDocument.docx");
```

Ini menyimpan dokumen Anda dengan margin dan jarak yang ditentukan dalam poin.

## Kesimpulan

Nah, itu dia! Anda telah berhasil mengonversi dan mengatur margin dan jarak dalam dokumen Word menggunakan Aspose.Words untuk .NET. Dengan mengikuti langkah-langkah ini, Anda dapat dengan mudah menangani berbagai konversi satuan, sehingga proses kustomisasi dokumen Anda menjadi mudah. Teruslah bereksperimen dengan berbagai pengaturan dan jelajahi berbagai fungsi yang ditawarkan Aspose.Words. Selamat membuat kode!

## Pertanyaan yang Sering Diajukan

### Bisakah saya mengonversi satuan lain seperti sentimeter ke poin menggunakan Aspose.Words?
 Ya, Aspose.Words menyediakan metode seperti`ConvertUtil.CmToPoint` untuk mengonversi sentimeter ke poin.

### Apakah lisensi diperlukan untuk menggunakan Aspose.Words untuk .NET?
Meskipun Anda dapat menggunakan Aspose.Words tanpa lisensi, beberapa fitur lanjutan mungkin dibatasi. Memperoleh lisensi memastikan fungsionalitas penuh.

### Bagaimana cara menginstal Aspose.Words untuk .NET?
 Anda dapat mengunduhnya dari[situs web](https://releases.aspose.com/words/net/) dan ikuti petunjuk instalasi.

### Dapatkah saya menetapkan unit yang berbeda untuk bagian yang berbeda dalam suatu dokumen?
 Ya, Anda dapat menyesuaikan margin dan pengaturan lainnya untuk bagian yang berbeda menggunakan`Section` kelas.

### Fitur apa lagi yang ditawarkan Aspose.Words?
 Aspose.Words mendukung berbagai fitur termasuk konversi dokumen, gabungan surat, dan opsi pemformatan yang luas. Periksa[dokumentasi](https://reference.aspose.com/words/net/) untuk lebih jelasnya.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
