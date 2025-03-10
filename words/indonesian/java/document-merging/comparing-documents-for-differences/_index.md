---
title: Membandingkan Dokumen untuk Menemukan Perbedaan
linktitle: Membandingkan Dokumen untuk Menemukan Perbedaan
second_title: API Pemrosesan Dokumen Java Aspose.Words
description: Pelajari cara membandingkan dokumen untuk mengetahui perbedaannya menggunakan Aspose.Words di Java. Panduan langkah demi langkah kami memastikan manajemen dokumen yang akurat.
weight: 12
url: /id/java/document-merging/comparing-documents-for-differences/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membandingkan Dokumen untuk Menemukan Perbedaan

## Perkenalan

Pernahkah Anda bertanya-tanya bagaimana cara menemukan setiap perbedaan antara dua dokumen Word? Mungkin Anda sedang merevisi dokumen atau mencoba menemukan perubahan yang dibuat oleh kolaborator. Perbandingan manual bisa jadi membosankan dan rawan kesalahan, tetapi dengan Aspose.Words untuk Java, itu mudah! Pustaka ini memungkinkan Anda mengotomatiskan perbandingan dokumen, menyorot revisi, dan menggabungkan perubahan dengan mudah.

## Prasyarat

Sebelum masuk ke kode, pastikan Anda telah menyiapkan hal berikut:  
1. Java Development Kit (JDK) terinstal di sistem Anda.  
2.  Aspose.Words untuk pustaka Java. Anda dapat[unduh disini](https://releases.aspose.com/words/java/).  
3. Lingkungan pengembangan seperti IntelliJ IDEA atau Eclipse.  
4. Kemampuan dasar dalam pemrograman Java.  
5.  Lisensi Aspose yang valid. Jika Anda belum memilikinya, dapatkan lisensi[lisensi sementara di sini](https://purchase.aspose.com/temporary-license/).

## Paket Impor

Untuk menggunakan Aspose.Words, Anda perlu mengimpor kelas-kelas yang diperlukan. Berikut ini adalah impor yang diperlukan:

```java
import com.aspose.words.*;
import java.util.Date;
```

Pastikan paket-paket ini ditambahkan dengan benar ke dependensi proyek Anda.


Di bagian ini, kami akan menguraikan prosesnya menjadi beberapa langkah sederhana.


## Langkah 1: Siapkan Dokumen Anda

Untuk memulai, Anda memerlukan dua dokumen: satu yang mewakili dokumen asli dan satu lagi yang mewakili versi yang telah diedit. Berikut cara membuatnya:

```java
Document doc1 = new Document();
DocumentBuilder builder = new DocumentBuilder(doc1);
builder.writeln("This is the original document.");

Document doc2 = new Document();
builder = new DocumentBuilder(doc2);
builder.writeln("This is the edited document.");
```

 Ini menciptakan dua dokumen dalam memori dengan konten dasar. Anda juga dapat memuat dokumen Word yang ada menggunakan`new Document("path/to/document.docx")`.


## Langkah 2: Periksa Revisi yang Ada

Revisi dalam dokumen Word merupakan perubahan yang terlacak. Sebelum membandingkan, pastikan tidak ada dokumen yang memuat revisi yang sudah ada sebelumnya:

```java
if (doc1.getRevisions().getCount() == 0 && doc2.getRevisions().getCount() == 0) {
    System.out.println("No revisions found. Proceeding with comparison...");
}
```

Jika ada revisi, Anda mungkin ingin menerima atau menolaknya sebelum melanjutkan.


## Langkah 3: Bandingkan Dokumen

 Gunakan`compare` metode untuk menemukan perbedaan. Metode ini membandingkan dokumen target (`doc2`) dengan dokumen sumber (`doc1`):

```java
doc1.compare(doc2, "AuthorName", new Date());
```

Di Sini:
- AuthorName adalah nama orang yang membuat perubahan.
- Tanggal adalah stempel waktu perbandingan.


## Langkah 4: Revisi Proses

Setelah dibandingkan, Aspose.Words akan menghasilkan revisi pada dokumen sumber (`doc1`). Mari kita analisis revisi berikut:

```java
for (Revision r : doc1.getRevisions()) {
    System.out.println("Revision type: " + r.getRevisionType());
    System.out.println("Node type: " + r.getParentNode().getNodeType());
    System.out.println("Changed text: " + r.getParentNode().getText());
}
```

Putaran ini menyediakan informasi terperinci tentang setiap revisi, seperti jenis perubahan dan teks yang terpengaruh.


## Langkah 5: Terima Semua Revisi

Jika Anda menginginkan dokumen sumber (`doc1`) untuk mencocokkan dokumen target (`doc2`), terima semua revisi:

```java
doc1.getRevisions().acceptAll();
```

 Pembaruan ini`doc1` untuk mencerminkan semua perubahan yang dibuat di`doc2`.


## Langkah 6: Simpan Dokumen yang Diperbarui

Terakhir, simpan dokumen yang diperbarui ke disk:

```java
doc1.save("Document.Compare.docx");
```

Untuk mengonfirmasi perubahan, muat ulang dokumen dan verifikasi tidak ada revisi yang tersisa:

```java
doc1 = new Document("Document.Compare.docx");
if (doc1.getRevisions().getCount() == 0) {
    System.out.println("Documents are now identical.");
}
```


## Langkah 7: Verifikasi Kesetaraan Dokumen

Untuk memastikan dokumennya identik, bandingkan teksnya:

```java
if (doc1.getText().trim().equals(doc2.getText().trim())) {
    System.out.println("Documents are equal.");
}
```

Jika teksnya cocok, selamat—Anda telah berhasil membandingkan dan menyinkronkan dokumen!


## Kesimpulan

Membandingkan dokumen bukan lagi pekerjaan yang membosankan, berkat Aspose.Words untuk Java. Hanya dengan beberapa baris kode, Anda dapat menemukan perbedaan, memproses revisi, dan memastikan konsistensi dokumen. Baik Anda mengelola proyek penulisan kolaboratif atau mengaudit dokumen hukum, fitur ini akan mengubah segalanya.

## Pertanyaan yang Sering Diajukan

### Dapatkah saya membandingkan dokumen dengan gambar dan tabel?  
Ya, Aspose.Words mendukung perbandingan dokumen yang kompleks, termasuk dokumen yang berisi gambar, tabel, dan pemformatan.

### Apakah saya memerlukan lisensi untuk menggunakan fitur ini?  
 Ya, lisensi diperlukan untuk fungsionalitas penuh. Dapatkan lisensi[lisensi sementara di sini](https://purchase.aspose.com/temporary-license/).

### Apa yang terjadi jika ada revisi yang sudah ada sebelumnya?  
Anda harus menerima atau menolaknya sebelum membandingkan dokumen untuk menghindari konflik.

### Bisakah saya menyorot revisi dalam dokumen?  
Ya, Aspose.Words memungkinkan Anda menyesuaikan bagaimana revisi ditampilkan, seperti menyorot perubahan.

### Apakah fitur ini tersedia dalam bahasa pemrograman lain?  
Ya, Aspose.Words mendukung banyak bahasa, termasuk .NET dan Python.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
