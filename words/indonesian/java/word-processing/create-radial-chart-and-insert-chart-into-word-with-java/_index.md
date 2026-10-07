---
category: general
date: 2026-09-27
description: Buat diagram radial di Java dan sisipkan diagram ke dalam Word. Pelajari
  cara mengatur ukuran diagram, menambahkan seri data, dan menghasilkan dokumen Word
  kosong.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- insert chart into word
- create blank word document
- how to set chart size
- add data series chart
language: id
lastmod: 2026-09-27
og_description: Buat diagram radial di Java, lalu sisipkan diagram ke Word. Panduan
  ini menunjukkan cara mengatur ukuran diagram, menambahkan seri data, dan membuat
  dokumen Word kosong.
og_image_alt: Screenshot showing a radial chart inserted into a Word document created
  with Java
og_title: Buat diagram radial dan sisipkan diagram ke Word dengan Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create radial chart in Java and insert chart into Word. Learn how to
    set chart size, add data series, and generate a blank Word document.
  headline: Create radial chart and insert chart into Word with Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart generation
title: Buat diagram radial dan sisipkan diagram ke Word dengan Java
url: /id/java/word-processing/create-radial-chart-and-insert-chart-into-word-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat diagram radial dan sisipkan diagram ke Word dengan Java

Jika Anda perlu **membuat diagram radial** dalam file Word menggunakan Java, tutorial ini akan menunjukkan secara tepat caranya. Anda akan melihat cara **menyisipkan diagram ke Word**, mengatur dimensi diagram, dan membuat **dokumen Word kosong** dari awal.

Kami akan membahas setiap langkah yang diperlukan, mulai dari menginisialisasi dokumen hingga menambahkan seri data dan menyimpan `.docx` akhir. Pada akhir tutorial Anda akan memiliki file Word yang berfungsi penuh berisi diagram radial, dan Anda akan memahami **cara mengatur ukuran diagram** dan **menambahkan seri data diagram** untuk penyesuaian di masa mendatang.

## Prasyarat

* Java 17 atau lebih baru (kode dapat dikompilasi dengan JDK modern apa pun)
* Aspose.Words for Java 24.9 atau yang lebih baru – metode `setShowGraduations` hanya tersedia mulai versi ini
* IDE atau alat build (Maven/Gradle) yang dapat menyertakan JAR Aspose.Words
* Familiaritas dasar dengan sintaks Java dan manajemen dependensi Maven/Gradle

> **Tips pro:** Jika Anda menggunakan Maven, tambahkan berikut ke `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Langkah 1: Buat dokumen Word kosong

Dokumen kosong adalah kanvas tempat diagram akan ditempatkan. Kelas `Document` mewakili seluruh file `.docx`.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank Word document
```

Membuat dokumen kosong memastikan tidak ada konten yang sudah ada sebelumnya mengganggu tata letak diagram.

## Langkah 2: Inisialisasi DocumentBuilder

`DocumentBuilder` menyediakan metode yang nyaman untuk menyisipkan objek, teks, dan elemen lain ke dalam dokumen.

```java
        // Step 2: Initialise a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder nanti akan digunakan untuk **menyisipkan diagram ke Word**.

## Langkah 3: Bangun diagram radial

Aspose.Words mendukung banyak tipe diagram; `ChartType.RADIAL` membuat diagram radial (polar).

```java
        // Step 3: Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);
```

Pada titik ini diagram sudah ada tetapi belum memiliki data, ukuran, atau opsi visual.

## Langkah 4: Tambahkan seri data ke diagram

Diagram tanpa seri data kosong. Metode `add` menerima nama seri dan array nilai.

```java
        // Step 4: Add a data series to the chart
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});
```

Anda dapat menambahkan beberapa seri dengan memanggil `add` berulang kali. Ini memenuhi persyaratan **menambahkan seri data diagram**.

## Langkah 5: Aktifkan graduasi (opsional)

Graduasi adalah garis kisi radial yang meningkatkan keterbacaan. Mereka hanya tersedia mulai versi 24.9.

```java
        // Step 5: Enable graduations on the chart (available from version 24.9)
        chart.getChartObject().setShowGraduations(true);
```

Jika Anda menggunakan versi Aspose.Words yang lebih lama, baris ini akan melempar pengecualian—jadi pastikan versi perpustakaan Anda terlebih dahulu.

## Langkah 6: Atur dimensi diagram

Mengontrol ukuran diagram memungkinkan Anda menyesuaikannya dengan baik dalam margin halaman. Ini menjawab **cara mengatur ukuran diagram**.

```java
        // Step 6: Define the chart's dimensions
        chart.setWidth(400);   // width in points (≈5.5 inches)
        chart.setHeight(300);  // height in points (≈4.2 inches)
```

Anda dapat menyesuaikan nilai lebar dan tinggi agar sesuai dengan kebutuhan tata letak Anda. Ingat bahwa 1 point ≈ 1/72 inci.

## Langkah 7: Sisipkan diagram ke dokumen Word

Sekarang diagram siap ditempatkan. Metode `insertChart` dari `DocumentBuilder` menangani penyisipan.

```java
        // Step 7: Insert the chart into the document
        builder.insertChart(chart);
```

Ini adalah inti dari operasi **menyisipkan diagram ke word**.

## Langkah 8: Simpan dokumen

Akhirnya, tulis dokumen ke disk. File akan berisi diagram radial yang baru saja Anda buat.

```java
        // Step 8: Save the document with the chart
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Menjalankan program menghasilkan `RadialChart.docx` di direktori kerja proyek. Membuka file di Microsoft Word menampilkan diagram radial dengan tiga titik data dan graduasi yang terlihat.

### Output yang diharapkan

* File Word bernama `RadialChart.docx`
* Di dalam file, satu halaman berisi diagram radial berukuran 400 × 300 point
* Diagram menampilkan satu seri berjudul **Series 1** dengan nilai **10, 20, 30**
* Graduasi (garis kisi radial) terlihat di sekitar diagram

## Variasi umum dan kasus tepi

| Situasi | Apa yang diubah | Alasan |
|-----------|----------------|--------|
| **Beberapa seri** | Panggil `chart.getSeries().add(...)` untuk setiap seri | Memungkinkan visualisasi data perbandingan |
| **Tipe diagram berbeda** | Ganti `ChartType.RADIAL` dengan `ChartType.COLUMN` (atau yang lain) | Gunakan tipe diagram yang paling tepat merepresentasikan data Anda |
| **Warna khusus** | Akses `chart.getSeries().get(i).getFormat().getFill().setForeColor(Color)` | Meningkatkan branding visual |
| **Versi Aspose.Words yang lebih lama** | Hapus baris `setShowGraduations` atau tingkatkan perpustakaan | Mencegah `NoSuchMethodError` |
| **Menyimpan ke format berbeda** | Gunakan `doc.save("RadialChart.pdf", SaveFormat.PDF)` | Menghasilkan PDF alih-alih DOCX |

## Contoh lengkap yang dapat dijalankan

Berikut adalah program Java lengkap yang berdiri sendiri. Salin ke file bernama `RadialChartExample.java`, tambahkan dependensi Aspose.Words, dan jalankan.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank Word document
        Document doc = new Document();

        // 2. Initialise a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);

        // 4. Add a data series (add data series chart)
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});

        // 5. Enable graduations (requires Aspose.Words 24.9+)
        chart.getChartObject().setShowGraduations(true);

        // 6. Set chart size (how to set chart size)
        chart.setWidth(400);
        chart.setHeight(300);

        // 7. Insert the chart into the document (insert chart into word)
        builder.insertChart(chart);

        // 8. Save the document (create blank word document with chart)
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

## Kesimpulan

Anda sekarang tahu cara **membuat diagram radial** secara programatik, **menambahkan seri data diagram**, mengontrol **cara mengatur ukuran diagram**, dan **menyisipkan diagram ke Word** sambil memulai dari **dokumen Word kosong**. Contoh ini menggunakan Aspose.Words for Java 24.9, tetapi konsep yang sama berlaku untuk perpustakaan diagram lain yang menyediakan API serupa.

### Langkah selanjutnya

* Jelajahi tipe diagram lain (`ChartType.PIE`, `ChartType.LINE`, dll.) – ini kembali ke kata kunci sekunder **menyisipkan diagram ke word**.
* Sesuaikan label sumbu, legenda, dan warna agar sesuai dengan panduan merek Anda.
* Hasilkan diagram secara dinamis dari kueri basis data atau file CSV.
* Konversi `.docx` yang dihasilkan ke PDF untuk distribusi (`doc.save("output.pdf", SaveFormat.PDF)`).

Silakan bereksperimen dengan dimensi, data seri, dan opsi styling untuk membuat visual yang tepat sesuai kebutuhan Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara membuat diagram kolom menggunakan Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Sisipkan Diagram Area ke Dokumen Word](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}