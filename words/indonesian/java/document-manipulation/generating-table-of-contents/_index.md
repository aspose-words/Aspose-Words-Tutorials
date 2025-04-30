---
"description": "Pelajari cara membuat dan menyesuaikan Daftar Isi (TOC) menggunakan Aspose.Words untuk Java. Buat dokumen yang terorganisir dan profesional dengan mudah."
"linktitle": "Membuat Daftar Isi"
"second_title": "API Pemrosesan Dokumen Java Aspose.Words"
"title": "Membuat Daftar Isi di Aspose.Words untuk Java"
"url": "/id/java/document-manipulation/generating-table-of-contents/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Membuat Daftar Isi di Aspose.Words untuk Java


## Pengantar Pembuatan Daftar Isi di Aspose.Words untuk Java

Dalam tutorial ini, kami akan memandu Anda melalui proses pembuatan Daftar Isi (TOC) menggunakan Aspose.Words untuk Java. TOC merupakan fitur penting untuk membuat dokumen yang terorganisasi. Kami akan membahas cara menyesuaikan tampilan dan tata letak TOC.

## Prasyarat

Sebelum memulai, pastikan Anda telah menginstal dan mengatur Aspose.Words untuk Java di proyek Java Anda.

## Langkah 1: Buat Dokumen Baru

Pertama, mari buat dokumen baru untuk digunakan.

```java
Document doc = new Document();
```

## Langkah 2: Sesuaikan Gaya Daftar Isi

Untuk menyesuaikan tampilan TOC, Anda dapat mengubah gaya yang terkait dengannya. Dalam contoh ini, kita akan membuat entri TOC tingkat pertama menjadi tebal.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

## Langkah 3: Tambahkan Konten ke Dokumen Anda

Anda dapat menambahkan konten ke dalam dokumen. Konten ini akan digunakan untuk membuat Daftar Isi.

## Langkah 4: Buat Daftar Isi

Untuk membuat TOC, masukkan kolom TOC di lokasi yang diinginkan dalam dokumen Anda. Kolom ini akan otomatis terisi berdasarkan judul dan gaya dalam dokumen Anda.

```java
// Masukkan bidang TOC di lokasi yang diinginkan dalam dokumen Anda.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

## Langkah 5: Simpan Dokumen

Terakhir, simpan dokumen dengan TOC.

```java
doc.save("your_output_path_here");
```

## Menyesuaikan Tab Stop di TOC

Anda juga dapat menyesuaikan tab stop di TOC untuk mengontrol tata letak nomor halaman. Berikut cara mengubah tab stop:

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Dapatkan tab pertama yang digunakan dalam paragraf ini, yang menyelaraskan nomor halaman.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Lepaskan tab lama.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // Masukkan tab baru pada posisi yang dimodifikasi (misalnya, 50 unit ke kiri).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Sekarang Anda memiliki Daftar Isi yang disesuaikan dalam dokumen Anda dengan penghentian tab yang disesuaikan untuk perataan nomor halaman.


## Kesimpulan

Dalam tutorial ini, kami telah mempelajari cara membuat Daftar Isi (TOC) menggunakan Aspose.Words untuk Java, pustaka yang hebat untuk bekerja dengan dokumen Word. TOC yang terstruktur dengan baik sangat penting untuk mengatur dan menavigasi dokumen yang panjang, dan Aspose.Words menyediakan alat untuk membuat dan menyesuaikan TOC dengan mudah.

## Pertanyaan yang Sering Diajukan

### Bagaimana cara mengubah format entri TOC?

Anda dapat mengubah gaya yang terkait dengan level TOC menggunakan `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`, di mana X adalah tingkat TOC.

### Bagaimana cara menambahkan lebih banyak level ke Daftar Isi saya?

Untuk menyertakan lebih banyak level dalam TOC Anda, Anda dapat mengubah kolom TOC dan menentukan jumlah level yang diinginkan.

### Dapatkah saya mengubah posisi penghentian tab untuk entri TOC tertentu?

Ya, seperti ditunjukkan dalam contoh kode di atas, Anda dapat mengubah posisi tab stop untuk entri TOC tertentu dengan mengulangi paragraf dan memodifikasi tab stop sebagaimana mestinya.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}