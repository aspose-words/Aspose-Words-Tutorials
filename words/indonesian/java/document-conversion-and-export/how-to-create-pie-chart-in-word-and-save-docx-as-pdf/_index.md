---
category: general
date: 2026-11-15
description: Pelajari cara membuat diagram lingkaran dalam dokumen Word dan menyimpan
  file docx sebagai PDF menggunakan Java. Panduan ini juga mencakup cara mengonversi
  Word ke PDF dan cara menambahkan diagram.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save docx as pdf
- convert word to pdf
- how to add chart
- how to create chart
language: id
lastmod: 2026-11-15
og_description: Buat diagram lingkaran dalam file Word dan simpan docx sebagai PDF
  dengan Java. Ikuti tutorial langkah demi langkah ini untuk mengonversi Word ke PDF
  dan menambahkan diagram.
og_image_alt: Screenshot showing a pie chart created in a Word document
og_title: Buat diagram lingkaran di Word dan simpan docx sebagai PDF – Panduan Java
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to create pie chart in a Word document and save docx as PDF
    using Java. This guide also covers convert word to pdf and how to add chart.
  headline: How to create pie chart in Word and save docx as PDF
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- PDF
title: Cara membuat diagram lingkaran di Word dan menyimpan docx sebagai PDF
url: /id/java/document-conversion-and-export/how-to-create-pie-chart-in-word-and-save-docx-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat diagram pai di Word dan menyimpan docx sebagai PDF

Jika Anda perlu **create pie chart** di dalam dokumen Word dan kemudian **save docx as PDF**, tutorial ini menunjukkan secara tepat caranya. Anda akan melihat contoh lengkap yang dapat dijalankan yang mengonversi file .docx menjadi PDF sambil menyisipkan diagram pai, sehingga Anda dapat menjawab “how to add chart” tanpa harus mencari potongan kode yang tersebar.

Dalam panduan ini Anda akan belajar untuk:

* Muat file *.docx* yang sudah ada (atau mulai dari awal)  
* Gunakan Aspose.Words for Java untuk **create pie chart** dan mengisi data  
* **Save docx as PDF** dengan diagram yang dirender dengan benar  
* Pahami nuansa **convert word to pdf** ketika diagram terlibat  

Langkah-langkah ini bekerja dengan Aspose.Words 2024‑x.x dan Java 17, tetapi konsepnya berlaku untuk perpustakaan apa pun yang mendukung manipulasi diagram Word.

## Prasyarat

Sebelum Anda memulai, pastikan Anda memiliki:

| Persyaratan | Mengapa penting |
|-------------|----------------|
| Java 17 (or later) | Required by the latest Aspose.Words JAR |
| Maven or Gradle build tool | Simplifies dependency management |
| Aspose.Words for Java (latest version) | Provides `Document`, `Chart`, and `ChartType` classes |
| An input **.docx** file (or a blank document) | The chart will be inserted into this file |

Tambahkan dependensi Aspose.Words ke `pom.xml` Anda (Maven) atau `build.gradle` (Gradle). Contoh untuk Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Langkah 1: Muat dokumen Word (atau buat yang baru)

Tindakan pertama adalah mendapatkan instance `Document`. Jika Anda sudah memiliki templat, berikan jalurnya; jika tidak, buat dokumen kosong.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Load an existing .docx or create a new blank document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // If you prefer a new file, uncomment the next line:
        // Document doc = new Document();
```

*Mengapa langkah ini?* Objek `Document` adalah wadah untuk semua konten Word, termasuk diagram. Memuat file yang ada memungkinkan Anda mempertahankan teks dan gaya di sekitarnya sambil menambahkan elemen visual baru.

## Langkah 2: **Create pie chart** – inti dari “how to create chart”

Sekarang kita menginstansiasi objek `Chart` dengan `ChartType.PIE`. Ini secara otomatis membuat placeholder diagram pai yang kemudian dapat Anda isi dengan data.

```java
        // Step 2: Insert a pie chart into the document
        Chart chart = new Chart(doc, ChartType.PIE);
        // Place the chart at the end of the document body
        doc.getFirstSection().getBody().appendChild(chart);
```

*Penjelasan*: `ChartType.PIE` memberi tahu Aspose.Words untuk menggunakan templat diagram pai. Diagram ditambahkan ke badan dokumen, sehingga muncul di tempat yang Anda butuhkan. Ini memenuhi persyaratan “how to add chart” dalam satu panggilan.

## Langkah 3: Isi diagram – menjawab “how to add chart” dengan data

Diagram pai tidak berarti tanpa data seri. Gunakan koleksi `Series` untuk menambahkan kategori dan nilai.

```java
        // Step 3: Populate the chart with sample data
        chart.getSeries().add("Category A", 40);
        chart.getSeries().add("Category B", 30);
        chart.getSeries().add("Category C", 30);
```

*Mengapa ini penting*: Setiap panggilan ke `add` membuat irisan pada diagram pai. Argumen pertama adalah label, argumen kedua adalah nilai numerik. Anda dapat mengganti ini dengan data dinamis dari basis data atau file CSV.

### Opsional: Sesuaikan tampilan (tidak wajib tetapi berguna)

```java
        // Set a title for the chart
        chart.setTitle("Sales Distribution Q1");
        // Change the legend position
        chart.getLegend().setPosition(LegendPosition.RIGHT);
```

Penyesuaian ini menggambarkan bagaimana Anda dapat **how to create chart** dengan tampilan profesional, tanpa meninggalkan kode Java.

## Langkah 4: **Save docx as PDF** – bagian akhir dari “convert word to pdf”

Setelah diagram disisipkan, ekspor dokumen ke PDF. Aspose.Words merender diagram sebagai grafik vektor, mempertahankan kualitas.

```java
        // Step 4: Save the document as PDF – the chart will be rendered with graduations
        doc.save("YOUR_DIRECTORY/output.pdf", SaveFormat.PDF);
    }
}
```

*Poin penting*: Metode `save` secara otomatis mengonversi file Word ke PDF, menangani rasterisasi diagram, penyematan font, dan tata letak halaman. Ini memenuhi tujuan **save docx as pdf** dan menunjukkan cara yang andal untuk **convert word to pdf** ketika diagram ada.

### Output yang diharapkan

Menjalankan program menghasilkan `output.pdf` yang berisi:

* Konten asli dari `input.docx` (jika ada)  
* Diagram pai yang sepenuhnya dirender dengan judul *Sales Distribution Q1*  
* Persentase irisan yang akurat sesuai data (40 %, 30 %, 30 %)

Buka PDF di penampil apa pun dan Anda akan melihat diagram pai yang tajam, identik dengan yang Anda lihat di file Word.

## Kesalahan umum dan cara menghindarinya

| Masalah | Penyebab | Solusi |
|---------|----------|--------|
| Diagram muncul kosong di PDF | Pengaturan font atau rendering diagram tidak ada | Pastikan Anda menggunakan versi Aspose.Words terbaru; ia menyertakan perpustakaan rendering yang diperlukan. |
| Nilai data dibulatkan secara tidak tepat | Menggunakan nilai integer dengan angka besar | Berikan nilai `double` atau skala angka sebelum menambahkannya ke seri. |
| PDF output sangat besar | Gambar disisipkan dengan DPI tinggi | Setel `PdfSaveOptions.setImageCompressionLevel(CompressionLevel.MAXIMUM)` jika Anda juga menyisipkan gambar. |
| “convert word to pdf” melempar `UnsupportedOperationException` | Menggunakan versi Java lama (< 11) | Upgrade ke Java 17 atau lebih baru, yang diperlukan oleh Aspose.Words 24.x. |

## Tips profesional: Gunakan kembali logika pembuatan diagram

Jika Anda perlu menambahkan beberapa diagram ke dokumen yang sama, ekstrak kode pembuatan diagram ke dalam metode pembantu:

```java
private static Chart createPieChart(Document doc, Map<String, Double> data, String title) {
    Chart chart = new Chart(doc, ChartType.PIE);
    data.forEach(chart.getSeries()::add);
    chart.setTitle(title);
    return chart;
}
```

Sekarang Anda dapat memanggil `doc.getFirstSection().getBody().appendChild(createPieChart(...));` untuk setiap set data, menjaga kode Anda tetap DRY (Don’t Repeat Yourself).

## Kesimpulan

Anda sekarang tahu cara **create pie chart** di dalam dokumen Word, mengisinya dengan data, dan **save docx as PDF** menggunakan Java. Contoh end‑to‑end ini mencakup seluruh alur kerja **convert word to pdf**, menjawab **how to add chart**, dan mendemonstrasikan **how to create chart** secara programatis.

Dari sini Anda dapat mengeksplorasi:

* Menambahkan diagram batang atau garis (`ChartType.BAR`, `ChartType.LINE`) – skenario **how to create chart** lainnya.  
* Mengekspor ke format lain seperti PNG atau HTML (`SaveFormat.PNG`, `SaveFormat.HTML`).  
* Membuat dokumen input secara dinamis dengan tabel atau placeholder sebelum menyisipkan diagram.

Silakan bereksperimen dengan set data yang berbeda, opsi styling, atau bahkan menyisipkan beberapa diagram per halaman. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara menyisipkan diagram pai ke dalam dokumen Word menggunakan Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [Cara menyimpan word sebagai pdf dan membuat PDF yang dapat diakses di Java](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-docx-in-java-full-guide/)
- [Cara membuat diagram di Word dengan Java dan Aspose.Words](/words/english/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}