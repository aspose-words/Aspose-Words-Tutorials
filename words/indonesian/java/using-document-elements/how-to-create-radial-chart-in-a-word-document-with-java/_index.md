---
category: general
date: 2026-09-18
description: Pelajari cara membuat grafik radial dalam dokumen Word menggunakan Java,
  menambahkan label data grafik, dan menyisipkan data seri dengan contoh kode lengkap.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- add chart data labels
- add series data
- create blank word
- how to insert chart
language: id
lastmod: 2026-09-18
og_description: Buat diagram radial dalam dokumen Word menggunakan Java, tambahkan
  label data diagram, dan sisipkan data seri dalam satu tutorial.
og_image_alt: Radial chart displayed inside a generated Word document
og_title: Buat diagram radial di Word dengan Java – panduan langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn how to create radial chart in a Word document using Java, add
    chart data labels, and insert series data with a complete code example.
  headline: How to create radial chart in a Word document with Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- Word automation
title: Cara membuat diagram radial dalam dokumen Word dengan Java
url: /id/java/using-document-elements/how-to-create-radial-chart-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat diagram radial di dokumen Word dengan Java

Jika Anda perlu membuat diagram radial di dokumen Word, panduan ini menunjukkan langkah‑langkah tepatnya. Anda juga akan belajar cara menambahkan label data diagram dan menyisipkan data seri sehingga diagram siap untuk dipresentasikan.

Membuat diagram secara programatik menghilangkan pekerjaan pemformatan manual dan menjamin konsistensi antar laporan. Tutorial ini mengasumsikan Anda memiliki pengetahuan dasar Java dan versi terbaru dari pustaka Aspose.Words for Java terpasang.

## Apa yang Anda perlukan

* Java 17 atau lebih baru  
* Aspose.Words for Java (versi 23.12 atau lebih baru)  
* IDE atau alat build yang dapat menyelesaikan dependensi Maven/Gradle  

Memiliki prasyarat ini terpasang memungkinkan Anda menjalankan contoh tanpa konfigurasi tambahan.

## Cara membuat diagram radial di dokumen Word

Langkah pertama adalah membuat file Word kosong yang akan menampung diagram. Dokumen kosong menyediakan kanvas bersih dan menghindari gaya yang tidak diinginkan.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

/* Step 1: Create a new blank Word document */
Document doc = new Document();

/* Step 2: Open a builder to add content */
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` mewakili seluruh file .docx, sementara `DocumentBuilder` menyediakan metode untuk menyisipkan elemen seperti paragraf, tabel, dan diagram.

## Cara menyisipkan diagram

Selanjutnya Anda menyisipkan diagram itu sendiri. Metode `insertChart` membuat objek diagram dan menempatkannya pada posisi kursor builder saat ini.

```java
import com.aspose.words.Chart;
import com.aspose.words.ChartType;

/* Step 3: Insert a polar (radial) chart with a width of 400 pt and height of 300 pt */
Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);
```

Diagram polar menampilkan titik data di sekitar sumbu pusat, yang ideal untuk menampilkan informasi siklik. Dimensi diukur dalam poin (1 pt ≈ 1/72 inci).

## Menambahkan data seri ke diagram

Diagram tanpa data seri kosong. Anda dapat menambahkan seri secara manual atau mengikatnya ke sumber data. Contoh di bawah menambahkan satu seri dengan tiga titik data.

```java
import com.aspose.words.ChartSeries;
import java.util.Arrays;

/* Step 4: Add a series and populate it with values */
ChartSeries series = chart.getSeries().add("Sample Series",
        Arrays.asList("Jan", "Feb", "Mar"),
        Arrays.asList(30.0, 45.0, 25.0));
```

`add` menerima nama seri, daftar label kategori, dan daftar nilai numerik yang bersesuaian. Anda dapat mengulangi blok ini untuk menambahkan seri tambahan (`addSeriesData`).

## Menambahkan label data diagram ke seri pertama

Label data membuat diagram dapat dibaca tanpa harus mengarahkan kursor ke titik. Baris berikut mengaktifkan label nilai untuk seri pertama.

```java
/* Step 5: Show the numeric values as data labels */
chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);
```

Menetapkan `showValue` ke `true` menampilkan nilai setiap titik langsung pada diagram. Anda juga dapat mengaktifkan nama kategori, persentase, atau garis pemimpin melalui objek `DataLabelFormat` yang sama.

## Menyimpan file Word

Setelah diagram dikonfigurasi, tulis dokumen ke disk. Pilih lokasi yang dapat diakses aplikasi Anda.

```java
/* Step 6: Save the document containing the radial chart */
doc.save("output/RadialChart.docx");
```

File `RadialChart.docx` kini berisi diagram radial yang berfungsi penuh dengan label data.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program mandiri yang dapat Anda salin, kompilasi, dan jalankan. Program ini menunjukkan alur kerja lengkap mulai dari membuat dokumen Word kosong hingga menyimpan diagram radial dengan label data.

```java
import com.aspose.words.*;

import java.util.Arrays;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank Word document
        Document doc = new Document();

        // Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a polar (radial) chart with the desired dimensions
        Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);

        // Add a series and populate it with sample data
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                Arrays.asList("Q1", "Q2", "Q3", "Q4"),
                Arrays.asList(15000.0, 23000.0, 18000.0, 21000.0));

        // Show the numeric values as data labels for the first series
        chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);

        // Save the document containing the chart
        doc.save("output/RadialChart.docx");
    }
}
```

**Hasil yang diharapkan**

Saat Anda membuka `output/RadialChart.docx` di Microsoft Word, Anda akan melihat diagram radial berjudul *Quarterly Sales*. Setiap titik menampilkan nilai numeriknya (misalnya “15000”) di sebelah penanda.

## Variasi umum dan kasus tepi

| Situasi | Perubahan yang disarankan |
|-----------|--------------------|
| Anda memerlukan tipe diagram yang berbeda | Ganti `ChartType.POLAR` dengan nilai enum `ChartType` lain (misalnya `ChartType.COLUMN`). |
| Diagram harus menggunakan rentang Excel eksternal | Gunakan `chart.setDataRange("Sheet1!A1:B5")` setelah membuat diagram dan memuat workbook. |
| Anda ingin menyembunyikan legenda | `chart.getLegend().setVisible(false);` |
| Dokumen harus disimpan sebagai PDF | Panggil `doc.save("RadialChart.pdf");` – Aspose.Words secara otomatis mengonversi diagram. |

Penyesuaian ini menjaga logika inti tetap utuh sambil menyesuaikan output dengan kebutuhan spesifik.

## Tips profesional

* **Gunakan kembali builder** – Anda dapat menyisipkan beberapa diagram dalam dokumen yang sama dengan memanggil `builder.insertChart` berulang kali.  
* **Kinerja** – Saat menghasilkan banyak diagram, buat satu instance `DocumentBuilder` dan gunakan kembali untuk mengurangi beban alokasi objek.  
* **Pemformatan** – Penampilan diagram (warna, ketebalan garis) dikendalikan melalui metode `Chart` pada `getSeries().get(i).getFormat()`. Bereksperimenlah dengan pengaturan ini untuk menyesuaikan dengan identitas merek perusahaan.

## Kesimpulan

Sekarang Anda tahu cara membuat diagram radial di dokumen Word dengan Java, menambahkan data seri, dan menambahkan label data diagram sebelum menyimpan file. Contoh lengkap dapat diperluas untuk menangani seri tambahan, gaya khusus, atau format output alternatif.

Jelajahi topik terkait seperti **cara menyisipkan diagram** dari sumber data eksternal, **membuat dokumen Word kosong** dengan templat yang telah ditentukan, dan **menambahkan data seri** secara dinamis dari basis data. Bereksperimenlah dengan tipe diagram berbeda untuk menemukan visual yang paling efektif menyampaikan data Anda.

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait dan membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara membuat diagram kolom menggunakan Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Atur Opsi Default untuk Label Data dalam Diagram](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}