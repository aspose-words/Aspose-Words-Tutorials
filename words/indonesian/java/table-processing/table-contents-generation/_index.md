---
title: Daftar Isi Generasi
linktitle: Daftar Isi Generasi
second_title: API Pemrosesan Dokumen Java Aspose.Words
description: Pelajari cara membuat Daftar Isi dinamis menggunakan Aspose.Words untuk Java. Kuasai pembuatan Daftar Isi dengan panduan langkah demi langkah dan contoh kode sumber.
weight: 14
url: /id/java/table-processing/table-contents-generation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Daftar Isi Generasi

## Perkenalan

Pernahkah Anda kesulitan membuat Daftar Isi (TOC) yang dinamis dan tampak profesional dalam dokumen Word Anda? Tidak perlu mencari lebih jauh! Dengan Aspose.Words untuk Java, Anda dapat mengotomatiskan seluruh proses, menghemat waktu, dan memastikan keakuratan. Baik Anda sedang membuat laporan komprehensif atau makalah akademis, tutorial ini akan memandu Anda membuat TOC secara terprogram dengan Java. Siap untuk mencobanya? Mari kita mulai!

## Prasyarat

Sebelum kita memulai pengkodean, pastikan Anda memiliki hal berikut:

1.  Java Development Kit (JDK): Terpasang di sistem Anda. Anda dapat mengunduhnya dari[Situs web Oracle](https://www.oracle.com/java/technologies/javase-downloads.html).
2.  Aspose.Words untuk Perpustakaan Java: Unduh versi terbaru dari[halaman rilis](https://releases.aspose.com/words/java/).
3. Lingkungan Pengembangan Terpadu (IDE): Seperti IntelliJ IDEA, Eclipse, atau NetBeans.
4.  Aspose Lisensi Sementara: Untuk menghindari batasan evaluasi, dapatkan[lisensi sementara](https://purchase.aspose.com/temporary-license/).

## Paket Impor

Untuk menggunakan Aspose.Words for Java secara efektif, pastikan Anda mengimpor kelas yang diperlukan. Berikut ini adalah kelas yang diimpor:

```java
import com.aspose.words.*;
```

Ikuti langkah-langkah ini untuk membuat Daftar Isi dinamis pada dokumen Word Anda.

## Langkah 1: Inisialisasi Dokumen dan DocumentBuilder

 Langkah pertama adalah membuat dokumen baru dan menggunakan`DocumentBuilder` kelas untuk memanipulasinya.


```java
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document`: Mewakili dokumen Word.
- `DocumentBuilder`: Kelas pembantu yang memungkinkan manipulasi dokumen dengan mudah.

## Langkah 2: Masukkan Daftar Isi

Sekarang, mari masukkan TOC di awal dokumen.


```java
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");
builder.insertBreak(BreakType.PAGE_BREAK);
```

- `insertTableOfContents`: Menyisipkan kolom TOC. Parameter menentukan:
  - `\o "1-3"`: Sertakan judul level 1 hingga 3.
  - `\h`: Buat entri hyperlink.
  - `\z`: Menekan nomor halaman untuk dokumen web.
  - `\u`: Pertahankan gaya untuk hyperlink.
- `insertBreak`: Menambahkan jeda halaman setelah Daftar Isi.

## Langkah 3: Tambahkan Judul untuk Mengisi Daftar Isi

UNTUK mengisi Daftar Isi, Anda perlu menambahkan paragraf dengan gaya judul.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 1");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_2);
builder.writeln("Heading 1.1");
builder.writeln("Heading 1.2");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 2");
```

- `setStyleIdentifier` : Mengatur gaya paragraf ke tingkat judul tertentu (misalnya,`HEADING_1`, `HEADING_2`).
- `writeln`: Menambahkan teks ke dokumen dengan gaya yang ditentukan.

## Langkah 4: Tambahkan Judul Bersarang

Untuk menunjukkan tingkat Daftar Isi, sertakan judul bertingkat.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_3);
builder.writeln("Heading 3.1.1");
builder.writeln("Heading 3.1.2");
builder.writeln("Heading 3.1.3");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_4);
builder.writeln("Heading 3.1.3.1");
builder.writeln("Heading 3.1.3.2");
```

- Tambahkan judul pada tingkat yang lebih dalam untuk menunjukkan hierarki dalam Daftar Isi.

## Langkah 5: Perbarui Bidang Daftar Isi

Kolom TOC harus diperbarui untuk menampilkan judul terkini.


```java
doc.updateFields();
```

- `updateFields`: Menyegarkan semua bidang dalam dokumen, memastikan TOC mencerminkan judul yang ditambahkan.

## Langkah 6: Simpan Dokumen

Terakhir, simpan dokumen ke format yang Anda inginkan.


```java
doc.save(dataDir + "DocumentBuilder.InsertToc.docx");
```

- `save` : Mengekspor dokumen ke`.docx` file. Anda dapat menentukan format lain seperti`.pdf` atau`.txt` jika diperlukan.

## Kesimpulan

Selamat! Anda telah berhasil membuat Daftar Isi dinamis dalam dokumen Word menggunakan Aspose.Words untuk Java. Hanya dengan beberapa baris kode, Anda telah mengotomatiskan tugas yang seharusnya memakan waktu berjam-jam. Jadi, apa selanjutnya? Cobalah bereksperimen dengan berbagai gaya dan format judul untuk menyesuaikan Daftar Isi dengan kebutuhan spesifik.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menyesuaikan format TOC lebih lanjut?
Tentu saja! Anda dapat menyesuaikan parameter TOC seperti menyertakan nomor halaman, menyelaraskan teks, atau menggunakan gaya judul khusus.

### Apakah lisensi wajib untuk Aspose.Words untuk Java?
 Ya, lisensi diperlukan untuk fungsionalitas penuh. Anda dapat memulai dengan[lisensi sementara](https://purchase.aspose.com/temporary-license/).

### Bisakah saya membuat TOC untuk dokumen yang sudah ada?
 Ya! Muat dokumen ke dalam`Document` objek dan ikuti langkah yang sama untuk memasukkan dan memperbarui TOC.

### Apakah ini berfungsi untuk ekspor PDF?
 Ya, TOC akan muncul dalam PDF jika Anda menyimpan dokumen di`.pdf` format.

### Di mana saya dapat menemukan dokumentasi lebih lanjut?
 Lihat di sini[Dokumentasi Aspose.Words untuk Java](https://reference.aspose.com/words/java/) untuk contoh dan detail lebih lanjut.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
