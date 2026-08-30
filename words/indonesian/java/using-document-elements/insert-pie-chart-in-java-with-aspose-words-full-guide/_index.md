---
category: general
date: 2026-07-29
description: Sisipkan diagram lingkaran menggunakan Aspose.Words untuk Java dan pelajari
  cara membuat diagram donat, memformat diagram lingkaran, memformat diagram Word,
  serta menyesuaikan ukuran diagram.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- generate doughnut chart
- format pie chart
- format chart word
- customize chart size
language: id
lastmod: 2026-07-29
og_description: Masukkan diagram lingkaran dengan Aspose.Words untuk Java dan pelajari
  dengan cepat cara membuat diagram donat, memformat diagram lingkaran, memformat
  diagram Word, serta menyesuaikan ukuran diagram untuk dokumen profesional.
og_image_alt: Screenshot showing a Word document with an inserted pie chart created
  by Aspose.Words Java API
og_title: Menyisipkan diagram lingkaran di Java – Tutorial Lengkap Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Insert pie chart using Aspose.Words for Java and learn how to generate
    doughnut chart, format pie chart, format chart Word, and customize chart size.
  headline: Insert pie chart in Java with Aspose.Words – Full Guide
  type: TechArticle
- questions:
  - answer: The evaluation version works fine for testing, but it adds a watermark.
      Drop your `aspose.words.lic` file in the classpath for a clean output.
    question: Do I need a license?
  - answer: 'Absolutely. Add the following dependency to your `pom.xml`:'
    question: Can I use this with Maven?
  - answer: Loop over `pieChart.getSeries()` and apply `setExplosion`, `setFillColor`,
      or other formatting per series. That’s the way to **format pie chart** for multi‑dimensional
      data.
    question: What if I have more than one series?
  - answer: Yes—once saved, you can open the document and manually adjust colors,
      fonts, or even convert the pie to a bar chart if you need to.
    question: Is the chart editable in Word after generation?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Chart
- Document Generation
- Word Automation
title: Menyisipkan diagram lingkaran di Java dengan Aspose.Words – Panduan Lengkap
url: /id/java/using-document-elements/insert-pie-chart-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menyisipkan diagram pai di Java dengan Aspose.Words – Panduan Lengkap

Pernah bertanya-tanya bagaimana cara **insert pie chart** ke dalam dokumen Word dari kode Java? Anda tidak sendirian—banyak pengembang mengalami kendala ini ketika mereka membutuhkan cara cepat dan programatis untuk memvisualisasikan data. Kabar baik? Dengan Aspose.Words for Java Anda dapat melakukannya hanya dalam beberapa baris kode, dan sekaligus Anda juga dapat **generate doughnut chart**, **format pie chart**, **format chart Word**, dan **customize chart size** agar sesuai dengan merek Anda.

Dalam tutorial ini kami akan membahas contoh dunia nyata yang dimulai dengan membuat dokumen kosong, menyisipkan diagram pai, menyesuaikan beberapa properti visual, dan akhirnya menyimpan file. Pada akhir tutorial Anda akan memiliki potongan kode yang dapat digunakan kembali dan dapat ditempelkan ke proyek Java mana pun yang membutuhkan otomatisasi diagram. Tanpa pustaka tambahan, tanpa mengutak‑atik Office interop secara manual—hanya Java yang bersih dan terkompilasi.

## Apa yang Anda Butuhkan

- **Java 17** (atau JDK terbaru; API kompatibel mundur)
- **Aspose.Words for Java** 22.12 atau lebih baru – Anda dapat mengambil artefak Maven atau .jar dari situs Aspose.
- IDE sederhana (IntelliJ IDEA, Eclipse, VS Code…) – apa saja yang memungkinkan Anda menjalankan metode `main`.
- Opsional: file lisensi jika Anda tidak menginginkan watermark evaluasi.

Jika Anda sudah memiliki semuanya, kita dapat langsung masuk ke kode.

## Langkah 1: Insert pie chart dengan Aspose.Words

Hal pertama yang kami lakukan adalah **insert pie chart** ke dalam dokumen baru. Langkah ini menyiapkan panggung untuk semua hal lainnya, karena objek chart memberi kami akses ke series, data point, dan penyesuaian visual.

```java
import com.aspose.words.*;

public class PieChartFormatting {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with a specific size (500x400 points)
        Chart pieChart = builder.insertChart(ChartType.PIE, 500, 400);
```

> **Mengapa ini penting:** `DocumentBuilder.insertChart` tidak hanya membuat chart tetapi juga mengembalikan objek `Chart` yang dapat kami manipulasi. Argumen lebar dan tinggi memungkinkan Anda **customize chart size** tepat saat pembuatan, sehingga Anda tidak perlu mengubah ukuran nanti.

## Langkah 2: Generate doughnut chart (opsional)

Jika desain Anda memerlukan lubang di tengah—seperti diagram donat klasik—Aspose membuatnya menjadi satu baris kode. Instansi `Chart` yang sama dapat diubah dari pie biasa menjadi doughnut dengan menyesuaikan ukuran lubang.

```java
        // Optional: Turn the pie into a doughnut by setting the hole size (0‑100%)
        pieChart.getChartData().setHoleSize(30); // 30% hole makes it a doughnut chart
```

> **Tip:** Ukuran lubang hanya berpengaruh untuk `ChartType.DONUT`. Jika Anda tetap menggunakan tipe `PIE`, pemanggilan akan diabaikan, jadi silakan bereksperimen.

## Langkah 3: Format pie chart slices

Visual yang baik sering menyoroti irisan tertentu. Di sini kami **format pie chart** dengan meledakkan irisan pertama sejauh 20 poin ke luar. Ini menarik perhatian pembaca ke titik data yang paling penting.

```java
        // Explode the first slice to emphasize it
        pieChart.getSeries().get(0).setExplosion(20);
```

> **Pro tip:** Anda dapat melakukan loop melalui `pieChart.getSeries()` jika memiliki beberapa series dan mengatur warna, border, atau label data secara individual. Itulah cara **format chart Word** dokumen dengan gaya yang kaya.

## Langkah 4: Add data to the chart

Diagram tanpa data hanyalah bentuk dekoratif. Mari beri data sederhana—misalnya, angka penjualan kuartalan.

```java
        // Populate the chart with sample data
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataLabels().setShowCategoryName(true);
        series.getDataLabels().setShowValue(true);

        // Clear any default points and add our own
        series.getPoints().clear();
        series.getPoints().add(new ChartPoint(30)); // Q1
        series.getPoints().add(new ChartPoint(45)); // Q2
        series.getPoints().add(new ChartPoint(15)); // Q3
        series.getPoints().add(new ChartPoint(10)); // Q4
```

> **Mengapa kami melakukan ini:** Dengan secara eksplisit menambahkan objek `ChartPoint` kami menjamin diagram mencerminkan logika bisnis kami. Pemanggilan `setShowCategoryName` dan `setShowValue` merupakan bagian dari **formatting the pie chart** untuk menampilkan label dan angka.

## Langkah 5: Fine‑tune appearance (customize chart size & style)

Selain dimensi awal, Anda mungkin ingin menyesuaikan legenda diagram, judul, atau bahkan font yang digunakan untuk label data. Semua ini termasuk dalam **customize chart size** dan format keseluruhan.

```java
        // Set a title for the chart
        ChartTitle title = pieChart.getTitle();
        title.setText("Quarterly Sales Distribution");
        title.getFont().setSize(14);
        title.getFont().setBold(true);

        // Move the legend to the right side
        ChartLegend legend = pieChart.getLegend();
        legend.setPosition(LegendPosition.RIGHT);
        legend.getFont().setSize(10);

        // Adjust the overall chart size again if needed
        pieChart.setWidth(600);   // width in points
        pieChart.setHeight(450);  // height in points
```

> **Edge case:** Jika Anda kemudian memutuskan mengekspor dokumen ke PDF, data vektor diagram tetap tajam karena ukuran didefinisikan dalam poin, bukan piksel. Itu merupakan keuntungan untuk **format chart Word** dan format turunannya.

## Langkah 6: Save and view the document

Langkah terakhir sesederhana memanggil `doc.save`. Ini menulis file `.docx` yang dapat Anda buka di Microsoft Word, LibreOffice, atau penampil apa pun yang mendukung format OpenXML.

```java
        // Save the document containing the formatted chart
        doc.save("YOUR_DIRECTORY/PieChart.docx");
    }
}
```

> **Hasil:** Buka `PieChart.docx` dan Anda akan melihat diagram pai (atau donat) berukuran rapi dengan irisan yang meledak, judul, dan legenda—semua dihasilkan tanpa menyentuh UI.

### Output yang Diharapkan

| Elemen | Apa yang akan Anda lihat |
|--------|--------------------------|
| Chart type | Pie chart (atau doughnut jika `holeSize` > 0) |
| Slice explosion | Irisan pertama dipindahkan 20 pts |
| Legend | Ditempatkan di sebelah kanan |
| Title | “Quarterly Sales Distribution” dalam bold 14 pt |
| Data labels | Nama kategori dan nilai ditampilkan pada setiap irisan |
| Document | File Word standar `.docx` siap dibagikan |

## Pertanyaan Umum & Gotchas

- **Apakah saya memerlukan lisensi?**  
  Versi evaluasi berfungsi baik untuk pengujian, tetapi menambahkan watermark. Letakkan file `aspose.words.lic` Anda di classpath untuk output bersih.

- **Bisakah saya menggunakan ini dengan Maven?**  
  Tentu saja. Tambahkan dependensi berikut ke `pom.xml` Anda:

  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>22.12</version>
  </dependency>
  ```

- **Bagaimana jika saya memiliki lebih dari satu series?**  
  Lakukan loop pada `pieChart.getSeries()` dan terapkan `setExplosion`, `setFillColor`, atau format lain per series. Itulah cara **format pie chart** untuk data multi‑dimensional.

- **Apakah diagram dapat diedit di Word setelah dibuat?**  
  Ya—setelah disimpan, Anda dapat membuka dokumen dan secara manual menyesuaikan warna, font, atau bahkan mengubah pie menjadi diagram batang jika diperlukan.

## Kesimpulan

Kami baru saja **inserted pie chart** ke dalam dokumen Word menggunakan Aspose.Words for Java, menunjukkan cara **generate doughnut chart**, mendemonstrasikan beberapa cara **format pie chart**, membahas praktik terbaik **format chart Word**, dan mempelajari cara **customize chart size** untuk tampilan yang halus. Contoh lengkap yang dapat dijalankan di atas dapat dimasukkan ke proyek Java mana pun, memberi Anda otomatisasi diagram instan tanpa beban COM interop atau instalasi Office.

Apa selanjutnya? Coba ganti sumber data dengan database live, tambahkan warna kondisional berdasarkan ambang, atau ekspor dokumen yang sama ke PDF untuk laporan siap cetak. Setiap langkah tersebut membangun di atas fondasi yang telah kami susun, sehingga transisinya akan mulus.

Jika Anda mengalami kendala atau memiliki ide untuk peningkatan lebih lanjut—mungkin bar bertumpuk atau diagram garis—tinggalkan komentar di bawah. Selamat membuat diagram!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara membuat diagram kolom menggunakan Aspose.Words untuk Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Format Jumlah Label Data dalam Diagram](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Format Angka untuk Sumbu dalam Diagram](/words/english/net/programming-with-charts/number-format-for-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}