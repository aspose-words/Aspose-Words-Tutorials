---
title: Izinkan Hanya Bidang Formulir yang Dilindungi di Dokumen Word
linktitle: Izinkan Hanya Bidang Formulir yang Dilindungi di Dokumen Word
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara melindungi dokumen Word, dengan hanya mengizinkan kolom formulir untuk diedit menggunakan Aspose.Words untuk .NET. Ikuti panduan kami untuk memastikan dokumen Anda aman dan mudah diedit.
weight: 10
url: /id/net/document-protection/allow-only-form-fields-protect/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Izinkan Hanya Bidang Formulir yang Dilindungi di Dokumen Word

## Perkenalan

Hai! Pernahkah Anda perlu melindungi bagian tertentu dari dokumen Word sambil membiarkan bagian lain tetap dapat diedit? Aspose.Words untuk .NET mempermudah hal ini. Dalam tutorial ini, kami akan membahas cara mengizinkan perlindungan hanya pada kolom formulir dalam dokumen Word. Di akhir panduan ini, Anda akan memiliki pemahaman yang sangat baik tentang perlindungan dokumen menggunakan Aspose.Words untuk .NET. Siap? Mari kita mulai!

## Prasyarat

Sebelum kita masuk ke bagian pengkodean, mari pastikan Anda memiliki semua yang Anda butuhkan:

1.  Pustaka Aspose.Words untuk .NET: Anda dapat mengunduhnya dari[Di Sini](https://releases.aspose.com/words/net/).
2. Visual Studio: Versi terbaru apa pun akan berfungsi dengan baik.
3. Pengetahuan Dasar C#: Memahami dasar-dasar akan membantu Anda mengikuti tutorial.

## Mengimpor Ruang Nama

Pertama-tama, kita perlu mengimpor namespace yang diperlukan. Ini akan menyiapkan lingkungan kita untuk menggunakan Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Langkah 1: Siapkan Proyek Anda

Buat proyek baru di Visual Studio  
Buka Visual Studio dan buat proyek Aplikasi Konsol (.NET Core) baru. Beri nama yang bermakna, seperti "AsposeWordsProtection".

## Langkah 2: Instal Aspose.Words untuk .NET

Instal melalui Manajer Paket NuGet  
Klik kanan pada proyek Anda di Solution Explorer, pilih "Kelola Paket NuGet", dan cari`Aspose.Words`Instal itu.

## Langkah 3: Inisialisasi Dokumen

Buat objek Dokumen baru  
Mari kita mulai dengan membuat dokumen baru dan pembuat dokumen untuk menambahkan beberapa teks.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Inisialisasi Dokumen dan DocumentBuilder baru
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.Writeln("Text added to a document.");
```

 Di sini, kita membuat yang baru`Document` Dan`DocumentBuilder` contoh.`DocumentBuilder` memungkinkan kita menambahkan teks ke dokumen kita.

## Langkah 4: Lindungi Dokumen

Terapkan perlindungan yang hanya mengizinkan pengeditan bidang formulir  
Sekarang, mari tambahkan proteksi pada dokumen kita.

```csharp
// Lindungi dokumen, izinkan hanya bidang formulir yang dapat diedit
doc.Protect(ProtectionType.AllowOnlyFormFields, "password");
```

Baris kode ini melindungi dokumen dan hanya mengizinkan kolom formulir untuk diedit. Kata sandi "password" digunakan untuk menegakkan perlindungan.

## Langkah 5: Simpan Dokumen

Simpan dokumen yang dilindungi  
Terakhir, mari simpan dokumen kita ke direktori yang ditentukan.

```csharp
// Simpan dokumen yang dilindungi
doc.Save(dataDir + "DocumentProtection.AllowOnlyFormFieldsProtect.docx");
```

Ini menyimpan dokumen dengan perlindungan yang diterapkan.

## Kesimpulan

Nah, itu dia! Anda baru saja mempelajari cara melindungi dokumen Word sehingga hanya kolom formulir yang dapat diedit menggunakan Aspose.Words untuk .NET. Ini adalah fitur yang berguna saat Anda perlu memastikan bahwa bagian tertentu dari dokumen Anda tetap tidak berubah, tetapi tetap mengizinkan kolom tertentu untuk diisi.

## Pertanyaan yang Sering Diajukan

###	 Bagaimana cara menghapus proteksi dari sebuah dokumen?  
 Untuk menghapus perlindungan, gunakan`doc.Unprotect("password")` metode, di mana "password" adalah kata sandi yang digunakan untuk melindungi dokumen.

###	 Dapatkah saya menerapkan jenis perlindungan yang berbeda menggunakan Aspose.Words untuk .NET?  
 Ya, Aspose.Words mendukung berbagai jenis perlindungan seperti`ReadOnly`, `NoProtection` , Dan`AllowOnlyRevisions`.

###	 Apakah mungkin untuk menggunakan kata sandi yang berbeda untuk bagian yang berbeda?  
Tidak, perlindungan tingkat dokumen di Aspose.Words berlaku untuk seluruh dokumen. Anda tidak dapat menetapkan kata sandi yang berbeda untuk bagian yang berbeda.

###	 Apa yang terjadi jika kata sandi yang digunakan salah?  
Jika kata sandi yang digunakan salah, dokumen akan tetap terlindungi, dan perubahan yang ditentukan tidak akan diterapkan.

###	 Dapatkah saya memeriksa secara terprogram apakah suatu dokumen dilindungi?  
 Ya, Anda bisa menggunakan`doc.ProtectionType` properti untuk memeriksa status perlindungan suatu dokumen.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
