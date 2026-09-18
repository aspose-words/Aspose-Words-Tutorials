---
date: 2025-11-28
description: Pelajari cara mengubah batas sel dan memformat tabel menggunakan Aspose.Words
  untuk Java. Panduan langkah demi langkah ini mencakup pengaturan batas, penerapan
  gaya kolom pertama, penyesuaian otomatis isi tabel, dan penerapan gaya tabel.
linktitle: How to Change Cell Borders in Tables – Aspose.Words for Java
second_title: Aspose.Words Java Document Processing API
title: Cara Mengubah Garis Sel dalam Tabel – Aspose.Words untuk Java
url: /id/java/document-conversion-and-export/formatting-tables-and-table-styles/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cara Mengubah Garis Batas Sel pada Tabel – Aspose.Words untuk Java

## Pendahuluan

Ketika berbicara tentang pemformatan dokumen, tabel memainkan peran penting, dan **mengetahui cara mengubah garis batas sel** sangat penting untuk membuat tata letak yang jelas dan profesional. Jika Anda mengembangkan dengan Java dan Aspose.Words, Anda sudah memiliki toolkit yang kuat di tangan. Pada tutorial ini kami akan membimbing Anda melalui proses lengkap pemformatan tabel, mengubah garis batas sel, menerapkan *gaya kolom pertama*, dan menggunakan *auto‑fit isi tabel* agar dokumen Anda tampak rapi.

## Jawaban Cepat
- **Kelas utama untuk membangun tabel apa?** `DocumentBuilder` membuat tabel dan sel secara programatis.  
- **Bagaimana cara mengubah ketebalan garis batas satu sel?** Gunakan `builder.getCellFormat().getBorders().getLeft().setLineWidth(value)`.  
- **Apakah saya dapat menerapkan gaya tabel yang telah ditentukan?** Ya – panggil `table.setStyleIdentifier(StyleIdentifier.YOUR_STYLE)`.  
- **Metode apa yang melakukan auto‑fit tabel ke isinya?** `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`.  
- **Apakah saya memerlukan lisensi untuk produksi?** Lisensi Aspose.Words yang valid diperlukan untuk penggunaan non‑trial.

## Apa itu “cara mengubah garis batas sel” di Aspose.Words?

Mengubah garis batas sel berarti menyesuaikan garis visual yang memisahkan sel—warna, lebar, dan gaya garis. Aspose.Words menyediakan API yang kaya yang memungkinkan Anda mengatur properti ini pada tingkat tabel, baris, atau sel individual, memberi Anda kontrol detail atas tampilan dokumen Anda.

## Mengapa menggunakan Aspose.Words untuk Java dalam penataan tabel?

- **Tampilan konsisten di semua platform** – kode penataan yang sama bekerja di Windows, Linux, dan macOS.  
- **Tidak bergantung pada Microsoft Word** – menghasilkan atau memodifikasi dokumen di sisi server.  
- **Perpustakaan gaya yang lengkap** – gaya tabel bawaan (misalnya *gaya kolom pertama*) dan kemampuan auto‑fit penuh.  

## Prasyarat

1. **Java Development Kit (JDK) 8+** – pastikan `java` ada di PATH Anda.  
2. **IDE** – IntelliJ IDEA, Eclipse, atau editor apa pun yang Anda sukai.  
3. **Aspose.Words untuk Java** – unduh JAR terbaru dari [situs resmi](https://releases.aspose.com/words/java/).  
4. **Pengetahuan dasar Java** – Anda harus nyaman membuat proyek Maven/Gradle dan menambahkan JAR eksternal.

## Impor Paket

Untuk mulai bekerja dengan tabel Anda memerlukan kelas inti Aspose.Words:

```java
import com.aspose.words.*;
```

Impor tunggal ini memberi Anda akses ke `Document`, `DocumentBuilder`, `Table`, `StyleIdentifier`, dan banyak utilitas lainnya.

## Cara Mengubah Garis Batas Sel

Di bawah ini kami akan membuat tabel sederhana, mengubah garis batas keseluruhan, lalu menyesuaikan sel individual.

### Langkah 1: Muat Dokumen Baru

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Langkah 2: Buat Tabel dan Atur Garis Batas Global

```java
Table table = builder.startTable();
builder.insertCell();

// Set the borders for the entire table.
table.setBorders(LineStyle.SINGLE, 2.0, Color.BLACK);
        
// Set the cell shading for this cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.RED);
builder.writeln("Cell #1");

builder.insertCell();
        
// Specify a different cell shading for the second cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.GREEN);
builder.writeln("Cell #2");

builder.endRow();
```

### Langkah 3: Ubah Garis Batas Satu Sel

```java
// Clear the cell formatting from previous operations.
builder.getCellFormat().clearFormatting();

builder.insertCell();

// Create larger borders for the first cell of this row.
builder.getCellFormat().getBorders().getLeft().setLineWidth(4.0);
builder.getCellFormat().getBorders().getRight().setLineWidth(4.0);
builder.getCellFormat().getBorders().getTop().setLineWidth(4.0);
builder.getCellFormat().getBorders().getBottom().setLineWidth(4.0);
builder.writeln("Cell #3");

builder.insertCell();
builder.getCellFormat().clearFormatting();
builder.writeln("Cell #4");
        
doc.save("FormatTableAndCellWithDifferentBorders.docx");
```

#### Apa yang dilakukan kode ini
- **Garis batas global** – `table.setBorders` memberikan seluruh tabel garis hitam 2‑point.  
- **Pewarnaan sel** – Menunjukkan cara memberi warna pada sel individual (merah & hijau).  
- **Garis batas sel khusus** – Sel ketiga menerima garis batas 4‑point di semua sisi, sehingga menonjol.

## Menerapkan Gaya Tabel (termasuk Gaya Kolom Pertama)

Gaya tabel memungkinkan Anda menerapkan tampilan konsisten dengan satu panggilan. Kami juga akan menunjukkan cara mengaktifkan *gaya kolom pertama* dan auto‑fit tabel ke isinya.

### Langkah 4: Buat Dokumen Baru untuk Penataan

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// We must insert at least one row first before setting any table formatting.
builder.insertCell();
```

### Langkah 5: Terapkan Gaya yang Telah Ditentukan dan Aktifkan Pemformatan Kolom Pertama

```java
// Set the table style based on a unique style identifier.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Apply which features should be formatted by the style.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);

// Auto‑fit the table so columns shrink or expand to fit the content.
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### Langkah 6: Isi Tabel dengan Data

```java
builder.writeln("Item");
builder.getCellFormat().setRightPadding(40.0);
builder.insertCell();
builder.writeln("Quantity (kg)");
builder.endRow();

builder.insertCell();
builder.writeln("Apples");
builder.insertCell();
builder.writeln("20");
builder.endRow();

builder.insertCell();
builder.writeln("Bananas");
builder.insertCell();
builder.writeln("40");
builder.endRow();

builder.insertCell();
builder.writeln("Carrots");
builder.insertCell();
builder.writeln("50");
builder.endRow();

doc.save("BuildTableWithStyle.docx");
```

#### Mengapa ini penting
- **Pengidentifikasi gaya** – `MEDIUM_SHADING_1_ACCENT_1` memberi tabel tampilan bersih dengan bayangan.  
- **Gaya kolom pertama** – Menyorot kolom pertama meningkatkan keterbacaan, terutama dalam laporan.  
- **Band baris** – Warna baris bergantian membuat tabel besar lebih mudah dilihat.  
- **Auto‑fit** – Memastikan lebar tabel menyesuaikan dengan konten, mencegah teks terpotong.

## Masalah Umum & Pemecahan Masalah

| Masalah | Penyebab Umum | Solusi Cepat |
|---------|---------------|--------------|
| Garis batas tidak muncul | Menggunakan `clearFormatting()` setelah mengatur garis batas | Atur garis batas **setelah** membersihkan format, atau terapkan kembali. |
| Pewarnaan diabaikan pada sel yang digabung | Pewarnaan diterapkan sebelum penggabungan | Terapkan pewarnaan **setelah** menggabungkan sel. |
| Lebar tabel melebihi margin halaman | Tidak ada auto‑fit yang diterapkan | Panggil `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` atau tetapkan lebar tetap. |
| Gaya tidak diterapkan | Nilai `StyleIdentifier` salah | Pastikan pengidentifikasi ada dalam versi Aspose.Words yang Anda gunakan. |

## Pertanyaan yang Sering Diajukan

**T: Bisakah saya menggunakan gaya tabel kustom yang tidak termasuk dalam opsi default?**  
J: Ya, Anda dapat membuat dan menerapkan gaya kustom secara programatis. Lihat [dokumentasi Aspose.Words](https://reference.aspose.com/words/java/) untuk detailnya.

**T: Bagaimana cara menerapkan pemformatan bersyarat pada sel?**  
J: Gunakan logika Java standar untuk memeriksa nilai sel, lalu panggil metode pemformatan yang sesuai (misalnya, ubah warna latar belakang jika nilai melebihi ambang tertentu).

**T: Apakah memungkinkan memformat sel yang digabung dengan cara yang sama seperti sel biasa?**  
J: Tentu saja. Setelah menggabungkan sel, terapkan pewarnaan atau garis batas menggunakan API `CellFormat` yang sama.

**T: Bagaimana jika saya perlu tabel menyesuaikan ukuran secara dinamis berdasarkan input pengguna?**  
J: Sesuaikan lebar kolom atau panggil `autoFit` lagi setelah menambahkan data baru untuk menghitung ulang tata letak.

**T: Di mana saya dapat menemukan contoh lebih lanjut tentang penataan tabel?**  
J: [Dokumentasi API Aspose.Words resmi](https://reference.aspose.com/words/java/) berisi kumpulan contoh yang komprehensif.

## Kesimpulan

Anda kini memiliki kotak peralatan lengkap untuk **cara mengubah garis batas sel**, menerapkan *gaya kolom pertama*, dan **auto‑fit isi tabel** menggunakan Aspose.Words untuk Java. Dengan menguasai teknik-teknik ini, Anda dapat menghasilkan dokumen yang kaya data sekaligus menarik secara visual—sempurna untuk laporan, faktur, dan output bisnis penting lainnya.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Terakhir Diperbarui:** 2025-11-28  
**Diuji Dengan:** Aspose.Words untuk Java 24.12 (terbaru pada saat penulisan)  
**Penulis:** Aspose