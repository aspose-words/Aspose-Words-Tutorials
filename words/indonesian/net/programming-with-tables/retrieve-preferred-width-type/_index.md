---
title: Ambil Jenis Lebar Pilihan
linktitle: Ambil Jenis Lebar Pilihan
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara mengambil jenis lebar sel tabel yang diinginkan dalam dokumen Word menggunakan Aspose.Words untuk .NET dengan panduan langkah demi langkah kami.
weight: 10
url: /id/net/programming-with-tables/retrieve-preferred-width-type/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ambil Jenis Lebar Pilihan

## Perkenalan

Pernahkah Anda bertanya-tanya bagaimana cara mengambil jenis lebar sel tabel yang diinginkan dalam dokumen Word Anda menggunakan Aspose.Words untuk .NET? Nah, Anda berada di tempat yang tepat! Dalam tutorial ini, kami akan menguraikan prosesnya langkah demi langkah, membuatnya semudah membalik telapak tangan. Apakah Anda seorang pengembang berpengalaman atau baru memulai, Anda akan merasa panduan ini bermanfaat dan menarik. Jadi, mari selami dan temukan rahasia di balik pengelolaan lebar sel tabel dalam dokumen Word.

## Prasyarat

Sebelum kita mulai, ada beberapa hal yang Anda perlukan:

1.  Aspose.Words untuk .NET: Pastikan Anda telah menginstal versi terbaru. Anda dapat mengunduhnya dari[Di Sini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Anda memerlukan IDE seperti Visual Studio.
3. Pengetahuan Dasar C#: Memahami dasar-dasar C# akan membantu Anda mengikutinya.
4.  Contoh Dokumen: Siapkan dokumen Word dengan tabel yang dapat Anda gunakan. Anda dapat menggunakan dokumen apa pun, tetapi kami akan menyebutnya sebagai`Tables.docx` dalam tutorial ini.

## Mengimpor Ruang Nama

Pertama-tama, mari impor namespace yang diperlukan. Langkah ini penting karena menyiapkan lingkungan kita untuk menggunakan fitur Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Langkah 1: Siapkan Direktori Dokumen Anda

Sebelum kita memanipulasi dokumen, kita perlu menentukan direktori tempat dokumen itu berada. Ini adalah langkah sederhana namun penting.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Mengganti`"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya ke direktori dokumen Anda. Ini memberi tahu program kita di mana menemukan berkas yang ingin kita gunakan.

## Langkah 2: Muat Dokumen

Selanjutnya, kita memuat dokumen Word ke dalam aplikasi kita. Ini memungkinkan kita berinteraksi dengan isinya secara terprogram.

```csharp
Document doc = new Document(dataDir + "Tables.docx");
```

 Baris kode ini membuka`Tables.docx` dokumen dari direktori yang ditentukan. Sekarang, dokumen kita siap untuk operasi selanjutnya.

## Langkah 3: Akses Tabel

Setelah dokumen kita dimuat, kita perlu mengakses tabel yang ingin kita gunakan. Untuk mempermudah, kita akan menargetkan tabel pertama dalam dokumen.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

Baris ini mengambil tabel pertama dari dokumen. Jika dokumen Anda berisi beberapa tabel, Anda dapat menyesuaikan indeks untuk memilih tabel yang berbeda.

## Langkah 4: Aktifkan Penyesuaian Otomatis untuk Tabel

Untuk memastikan tabel menyesuaikan kolomnya secara otomatis, kita perlu mengaktifkan properti AutoFit.

```csharp
table.AllowAutoFit = true;
```

 Pengaturan`AllowAutoFit` ke`true` memastikan kolom tabel diubah ukurannya berdasarkan isinya, memberikan nuansa dinamis pada tabel kita.

## Langkah 5: Ambil Jenis Lebar Pilihan Sel Pertama

Sekarang tibalah pada inti tutorial kita—mengambil jenis lebar yang diinginkan pada sel pertama dalam tabel.

```csharp
Cell firstCell = table.FirstRow.FirstCell;
PreferredWidthType type = firstCell.CellFormat.PreferredWidth.Type;
double value = firstCell.CellFormat.PreferredWidth.Value;
```

 Baris kode ini mengakses sel pertama di baris pertama tabel dan mengambil jenis dan nilai lebar yang diinginkan.`PreferredWidthType` bisa jadi`Auto`, `Percent` , atau`Point`, yang menunjukkan bagaimana lebarnya ditentukan.

## Langkah 6: Menampilkan Hasilnya

Terakhir, mari tampilkan informasi yang diambil ke konsol.

```csharp
Console.WriteLine("Preferred Width Type: " + type);
Console.WriteLine("Preferred Width Value: " + value);
```

Baris ini akan mencetak jenis dan nilai lebar yang diinginkan ke konsol, sehingga Anda dapat melihat hasil eksekusi kode Anda.

## Kesimpulan

Nah, itu dia! Mengambil tipe lebar sel tabel yang diinginkan dalam dokumen Word menggunakan Aspose.Words untuk .NET mudah dilakukan jika dipecah menjadi beberapa langkah yang mudah dikelola. Dengan mengikuti panduan ini, Anda dapat dengan mudah memanipulasi properti tabel dalam dokumen Word, sehingga tugas pengelolaan dokumen Anda menjadi jauh lebih efisien.

## Pertanyaan yang Sering Diajukan

### Bisakah saya mengambil jenis lebar yang disukai untuk semua sel dalam tabel?

Ya, Anda dapat melakukan pengulangan pada setiap sel dalam tabel dan mengambil jenis lebar pilihannya satu per satu.

###  Apa saja nilai yang mungkin untuk`PreferredWidthType`?

`PreferredWidthType` bisa jadi`Auto`, `Percent` , atau`Point`.

### Apakah mungkin untuk mengatur jenis lebar yang disukai secara terprogram?

 Tentu saja! Anda dapat mengatur jenis dan nilai lebar yang diinginkan menggunakan`PreferredWidth` milik`CellFormat` kelas.

### Bisakah saya menggunakan metode ini untuk tabel di dokumen selain Word?

Tutorial ini secara khusus membahas dokumen Word. Untuk jenis dokumen lain, Anda perlu menggunakan pustaka Aspose yang sesuai.

### Apakah saya memerlukan lisensi untuk menggunakan Aspose.Words untuk .NET?

 Ya, Aspose.Words untuk .NET adalah produk berlisensi. Anda bisa mendapatkan uji coba gratis[Di Sini](https://releases.aspose.com/) atau lisensi sementara[Di Sini](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
