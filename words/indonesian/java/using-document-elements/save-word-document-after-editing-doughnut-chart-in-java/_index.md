---
category: general
date: 2026-09-11
description: Simpan dokumen Word setelah mengedit diagram donat dengan Aspose.Words
  for Java. Pelajari cara mengubah ukuran lubang donat, memutar diagram donat, dan
  mengedit properti diagram donat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word document
- rotate doughnut chart
- edit doughnut chart
- change doughnut hole
- change chart hole size
language: id
lastmod: 2026-09-11
og_description: Simpan dokumen Word setelah mengedit diagram donat menggunakan Aspose.Words
  for Java. Tutorial ini menunjukkan cara mengubah ukuran lubang donat, memutar diagram
  donat, dan menyesuaikan tampilan diagram.
og_image_alt: Java code editing a doughnut chart before saving Word document
og_title: Simpan Dokumen Word Setelah Mengedit Diagram Donat – Panduan Java
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Save Word document after editing a doughnut chart with Aspose.Words
    for Java. Learn how to change doughnut hole size, rotate doughnut chart, and edit
    doughnut chart properties.
  headline: Save Word document after editing doughnut chart in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word
- Chart
- Doughnut
title: Simpan dokumen Word setelah mengedit diagram donat di Java
url: /id/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Simpan dokumen Word setelah mengedit diagram donat di Java

Jika Anda perlu **save Word document** yang berisi diagram donat yang disesuaikan, panduan ini menunjukkan cara melakukannya secara tepat. Dalam beberapa baris kode Java saja Anda dapat mengubah lubang donat, memutar diagram donat, dan kemudian menulis hasilnya kembali ke disk.

Anda akan melihat contoh lengkap yang dapat dijalankan yang menggunakan Aspose.Words for Java, serta tips untuk menangani beberapa diagram, memverifikasi tipe node, dan menghindari jebakan umum. Tidak diperlukan referensi eksternal—semua yang Anda butuhkan sudah disertakan.

## Prasyarat

- Java 17 atau yang lebih baru terpasang
- Maven atau Gradle untuk mengelola dependensi
- Aspose.Words for Java (versi 23.9 atau lebih baru) ditambahkan ke proyek Anda  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.9</version>
  </dependency>
  ```
- File Word (`input.docx`) yang berisi satu diagram donat

## Langkah 1: Muat dokumen Word

Langkah pertama adalah membuka file sumber. Langkah ini penting karena setiap operasi berikutnya bekerja pada objek `Document` yang berada di memori.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a doughnut chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Why?** Memuat dokumen membuat representasi DOM yang memungkinkan Anda menelusuri shape, tabel, dan diagram. Jika file tidak dapat dibuka, Aspose.Words akan melemparkan pengecualian, sehingga Anda langsung tahu bahwa jalurnya salah.

## Langkah 2: Temukan shape diagram donat

Diagram disimpan di dalam node `Shape`. Kami mengambil shape pertama yang berisi diagram dan meng‑cast renderer‑nya ke `Chart`.

```java
        // Find the first shape that contains a chart
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        // Ensure the shape actually holds a chart
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        // Get the Chart object for further manipulation
        Chart chart = chartShape.getChart();
```

> **Why?** Memeriksa `isChart()` mencegah `ClassCastException` ketika dokumen berisi gambar atau shape lain sebelum diagram. Ini membuat kode lebih tahan banting untuk dokumen dengan konten campuran.

## Langkah 3: Ubah ukuran lubang donat  

Sekarang kita mengedit lubang donat. Metode `setHoleSize` mengharapkan persentase dari radius diagram (10 – 90).

```java
        // Adjust the size of the doughnut hole (percentage of the chart radius)
        chart.setHoleSize(30);   // The hole occupies 30 % of the radius
```

> **Why?** Mengubah lubang donat (`change doughnut hole` / `change chart hole size`) memungkinkan Anda menekankan atau mengurangi penekanan pada area pusat. Nilai di luar 10‑90 % diabaikan oleh API.

## Langkah 4: Putar diagram donat  

Untuk mengontrol di mana irisan pertama dimulai, atur sudut irisan pertama. Ini secara efektif **rotate doughnut chart**.

```java
        // Rotate the chart so that the first slice starts at a custom angle
        chart.setFirstSliceAngle(45);   // Starts the first slice at 45 degrees
```

> **Why?** Memutar diagram berguna ketika Anda ingin irisan tertentu muncul di bagian atas atau sesuai dengan spesifikasi desain.

## Langkah 5: Simpan dokumen yang diperbarui  

Akhirnya, tulis perubahan kembali ke file baru. Ini adalah momen di mana Anda **save Word document** dengan diagram yang telah diedit.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Expected result:** `output.docx` berisi konten asli, tetapi diagram donat kini memiliki lubang 30 % dan irisan pertamanya dimulai pada 45 °. Membuka file di Microsoft Word akan menampilkan diagram yang telah diubah.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke IDE Anda. Program ini mencakup semua impor dan penanganan error yang diperlukan untuk **edit doughnut chart** dan **save Word document** dengan aman.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Locate the first chart shape
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        Chart chart = chartShape.getChart();

        // 3. Change the doughnut hole size
        chart.setHoleSize(30); // 30 % hole

        // 4. Rotate the doughnut chart
        chart.setFirstSliceAngle(45); // start at 45°

        // 5. Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Output yang diharapkan

Ketika Anda membuka `output.docx`:

- Lubang pusat diagram donat menempati kira‑kira sepertiga radius diagram.  
- Irisan pertama dimulai pada posisi 45‑derajat, menggeser seluruh diagram searah jarum jam.  

Kedua perubahan visual tersebut langsung terlihat di Word.

## Variasi umum dan kasus tepi

| **Situasi** | **Cara menangani** |
|-------------|--------------------|
| **Beberapa diagram** | Iterasi melalui `doc.getChildNodes(NodeType.SHAPE, true)` dan filter `shape.isChart()`; terapkan `setHoleSize` / `setFirstSliceAngle` pada setiap `Chart`. |
| **Diagram bukan donat** | Periksa `chart.getType()`; hanya panggil `setHoleSize` ketika `chart.getType() == ChartType.DOUGHNUT`. |
| **Perlu mengubah ukuran lubang secara dinamis** | Hitung persentase yang diinginkan berdasarkan nilai data, lalu panggil `setHoleSize(computedValue)`. |
| **Menyimpan ke stream** | Use |

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang dapat dijalankan dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Cara membuat diagram kolom menggunakan Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Cara menyimpan dokumen sebagai pdf dengan Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Simpan Word dengan Password menggunakan Aspose.Words for Java](/words/english/java/document-loading-and-saving/advance-saving-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}