---
title: Masukkan ASKField Tanpa Pembuat Dokumen
linktitle: Masukkan ASKField Tanpa Pembuat Dokumen
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menyisipkan kolom ASK tanpa menggunakan Document Builder di Aspose.Words untuk .NET. Ikuti panduan ini untuk menyempurnakan dokumen Word Anda secara dinamis.
weight: 10
url: /id/net/working-with-fields/insert-askfield-with-out-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Masukkan ASKField Tanpa Pembuat Dokumen

## Perkenalan

Apakah Anda ingin menguasai otomatisasi dokumen dengan Aspose.Words untuk .NET? Anda telah datang ke tempat yang tepat! Hari ini, kami akan memandu Anda melalui cara memasukkan kolom ASK tanpa menggunakan Pembuat Dokumen. Ini adalah fitur yang praktis saat Anda ingin dokumen Anda meminta masukan tertentu kepada pengguna, sehingga dokumen Word Anda menjadi lebih interaktif dan dinamis. Jadi, mari kita mulai dan buat dokumen Anda lebih cerdas!

## Prasyarat

Sebelum kita mulai mengerjakan beberapa kode, mari pastikan kita sudah menyiapkan semuanya:

1.  Aspose.Words untuk .NET: Pastikan Anda telah menginstal pustaka ini. Jika belum, Anda dapat mengunduhnya dari[Di Sini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: IDE yang cocok seperti Visual Studio.
3. .NET Framework: Pastikan Anda telah menginstal .NET Framework.

Bagus! Sekarang setelah semuanya siap, mari kita mulai dengan mengimpor namespace yang diperlukan.

## Mengimpor Ruang Nama

Pertama-tama, kita perlu mengimpor namespace Aspose.Words untuk mengakses semua fitur Aspose.Words untuk .NET. Berikut cara melakukannya:

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

## Langkah 1: Buat Dokumen Baru

Sebelum kita dapat memasukkan kolom ASK, kita memerlukan dokumen untuk digunakan. Berikut cara membuat dokumen baru:

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Pembuatan dokumen.
Document doc = new Document();
```

Potongan kode ini menyiapkan dokumen Word baru tempat kita akan menambahkan kolom ASK.

## Langkah 2: Akses Node Paragraf

Dalam dokumen Word, konten disusun ke dalam node. Kita perlu mengakses node paragraf pertama tempat kita akan memasukkan kolom ASK:

```csharp
Paragraph para = (Paragraph)doc.GetChild(NodeType.Paragraph, 0, true);
```

Baris kode ini mengambil paragraf pertama dalam dokumen, siap untuk penyisipan bidang ASK kita.

## Langkah 3: Masukkan Bidang ASK

Sekarang, mari kita masuk ke acara utama – memasukkan kolom ASK. Kolom ini akan meminta masukan dari pengguna saat dokumen dibuka.

```csharp
// Masukkan kolom ASK.
FieldAsk field = (FieldAsk)para.AppendField(FieldType.FieldAsk, false);
```

Di sini, kami menambahkan kolom ASK ke paragraf. Sederhana, bukan?

## Langkah 4: Konfigurasikan Bidang ASK

Kita perlu mengatur beberapa properti untuk menentukan bagaimana bidang ASK berperilaku. Mari konfigurasikan nama penanda, teks perintah, respons default, dan perilaku gabungan surat:

```csharp
field.BookmarkName = "Test1";
field.PromptText = "Please enter your response:";
field.DefaultResponse = "Default response";
field.PromptOnceOnMailMerge = true;
```

- BookmarkName: Pengidentifikasi unik untuk bidang ASK.
- PromptText: Teks yang meminta masukan kepada pengguna.
- DefaultResponse: Respons yang telah diisi sebelumnya yang dapat diubah oleh pengguna.
- PromptOnceOnMailMerge: Menentukan apakah prompt hanya muncul satu kali selama gabungan surat.

## Langkah 5: Perbarui Bidang

Setelah mengonfigurasi bidang ASK, kita perlu memperbaruinya untuk memastikan semua pengaturan diterapkan dengan benar:

```csharp
field.Update();
```

Perintah ini memastikan kolom ASK kita siap dan diatur dengan benar dalam dokumen.

## Langkah 6: Simpan Dokumen

Terakhir, mari simpan dokumen ke direktori yang kita tentukan:

```csharp
doc.Save(dataDir + "InsertionChampASKSansDocumentBuilder.docx");
```

Baris ini menyimpan dokumen dengan kolom ASK yang disisipkan. Dan begitulah – dokumen Anda kini dilengkapi dengan kolom ASK yang dinamis!

## Kesimpulan

Selamat! Anda baru saja menambahkan kolom ASK ke dokumen Word menggunakan Aspose.Words untuk .NET tanpa Document Builder. Fitur ini dapat meningkatkan interaksi pengguna dengan dokumen Anda secara signifikan, membuatnya lebih fleksibel dan mudah digunakan. Teruslah bereksperimen dengan berbagai kolom dan properti untuk membuka potensi penuh Aspose.Words. Selamat membuat kode!

## Pertanyaan yang Sering Diajukan

### Apa itu kolom ASK di Aspose.Words?
Kolom ASK di Aspose.Words adalah kolom yang meminta input spesifik kepada pengguna saat dokumen dibuka, yang memungkinkan entri data dinamis.

### Bisakah saya menggunakan beberapa kolom ASK dalam satu dokumen?
Ya, Anda dapat menyisipkan beberapa kolom ASK dalam satu dokumen, masing-masing dengan perintah dan respons yang unik.

###  Apa tujuan dari`PromptOnceOnMailMerge` property?
 Itu`PromptOnceOnMailMerge` Properti menentukan apakah prompt ASK hanya muncul satu kali selama operasi gabungan surat atau setiap waktu.

### Apakah saya perlu memperbarui bidang ASK setelah mengatur propertinya?
Ya, memperbarui bidang ASK memastikan bahwa semua properti diterapkan dengan benar dan bidang berfungsi seperti yang diharapkan.

### Bisakah saya menyesuaikan teks perintah dan respons default?
Tentu saja! Anda dapat mengatur teks permintaan khusus dan respons default untuk menyesuaikan kolom ASK dengan kebutuhan spesifik Anda.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
