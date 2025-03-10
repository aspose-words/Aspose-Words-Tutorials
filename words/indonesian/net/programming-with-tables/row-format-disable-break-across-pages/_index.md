---
title: Nonaktifkan Format Baris, Jeda Antar Halaman
linktitle: Nonaktifkan Format Baris, Jeda Antar Halaman
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menonaktifkan jeda baris di seluruh halaman dalam dokumen Word menggunakan Aspose.Words untuk .NET untuk menjaga keterbacaan dan pemformatan tabel.
weight: 10
url: /id/net/programming-with-tables/row-format-disable-break-across-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nonaktifkan Format Baris, Jeda Antar Halaman

## Perkenalan

Saat bekerja dengan tabel dalam dokumen Word, Anda mungkin ingin memastikan bahwa baris tidak terputus di beberapa halaman, yang penting untuk menjaga keterbacaan dan pemformatan dokumen Anda. Aspose.Words untuk .NET menyediakan cara mudah untuk menonaktifkan pemisah baris di beberapa halaman.

Dalam tutorial ini, kami akan memandu Anda melalui proses menonaktifkan jeda baris di seluruh halaman dalam dokumen Word menggunakan Aspose.Words untuk .NET.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:
- Pustaka Aspose.Words untuk .NET terinstal.
- Dokumen Word dengan tabel yang mencakup beberapa halaman.

## Mengimpor Ruang Nama

Pertama, impor namespace yang diperlukan dalam proyek Anda:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Langkah 1: Muat Dokumen

Muat dokumen yang berisi tabel yang mencakup beberapa halaman.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Langkah 2: Akses Tabel

Akses tabel pertama dalam dokumen. Ini mengasumsikan bahwa tabel yang ingin Anda ubah adalah tabel pertama dalam dokumen.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Langkah 3: Nonaktifkan Pemecahan Antar Halaman untuk Semua Baris

 Ulangi setiap baris dalam tabel dan atur`AllowBreakAcrossPages`properti untuk`false`Ini memastikan bahwa baris tidak akan terputus di beberapa halaman.

```csharp
// Nonaktifkan pemisahan antar halaman untuk semua baris dalam tabel.
foreach (Row row in table.Rows)
    row.RowFormat.AllowBreakAcrossPages = false;
```

## Langkah 4: Simpan Dokumen

Simpan dokumen yang dimodifikasi ke direktori yang Anda tentukan.

```csharp
doc.Save(dataDir + "WorkingWithTables.RowFormatDisableBreakAcrossPages.docx");
```

## Kesimpulan

Dalam tutorial ini, kami menunjukkan cara menonaktifkan pemisah baris di seluruh halaman dalam dokumen Word menggunakan Aspose.Words untuk .NET. Dengan mengikuti langkah-langkah yang diuraikan di atas, Anda dapat memastikan bahwa baris tabel Anda tetap utuh dan tidak terbagi di seluruh halaman, sehingga dokumen tetap mudah dibaca dan diformat.

## Pertanyaan yang Sering Diajukan

### Dapatkah saya menonaktifkan pemisah baris di seluruh halaman untuk baris tertentu, bukan semua baris?  
 Ya, Anda dapat menonaktifkan pemisah baris untuk baris tertentu dengan mengakses baris yang diinginkan dan mengaturnya`AllowBreakAcrossPages`properti untuk`false`.

### Apakah metode ini berfungsi untuk tabel dengan sel yang digabungkan?  
 Ya, metode ini berfungsi untuk tabel dengan sel yang digabungkan. Properti`AllowBreakAcrossPages` berlaku untuk seluruh baris, terlepas dari penggabungan sel.

### Apakah metode ini akan berfungsi jika tabel bersarang di dalam tabel lain?  
Ya, Anda dapat mengakses dan mengubah tabel bersarang dengan cara yang sama. Pastikan Anda merujuk tabel bersarang dengan benar melalui indeks atau properti lainnya.

### Bagaimana saya dapat memeriksa apakah suatu baris dapat dipecah antarhalaman?  
 Anda dapat memeriksa apakah suatu baris memungkinkan pemisahan antar halaman dengan mengakses`AllowBreakAcrossPages` milik`RowFormat` dan memeriksa nilainya.

### Apakah ada cara untuk menerapkan pengaturan ini ke semua tabel dalam dokumen?  
Ya, Anda dapat melakukan pengulangan pada semua tabel dalam dokumen dan menerapkan pengaturan ini pada masing-masing tabel.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
