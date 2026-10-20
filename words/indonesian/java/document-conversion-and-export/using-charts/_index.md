---
date: 2025-12-13
description: Pelajari cara membuat diagram kolom dan memformat label data diagram
  dengan Aspose.Words untuk Java. Jelajahi penambahan beberapa seri, mengubah tipe
  sumbu, dan menyembunyikan sumbu diagram.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Cara membuat diagram kolom menggunakan Aspose.Words untuk Java
url: /id/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cara Membuat Diagram Kolom Menggunakan Aspose.Words untuk Java

Dalam tutorial ini Anda akan **membuat visualisasi diagram kolom** langsung di dalam dokumen Word menggunakan Aspose.Words untuk Java. Kami akan membahas cara membuat berbagai tipe diagram, menambahkan beberapa seri, memformat label data diagram, mengubah tipe sumbu, dan bahkan menyembunyikan sumbu diagram ketika Anda memerlukan tampilan yang lebih bersih. Pada akhir tutorial Anda akan memiliki pendekatan yang solid dan siap produksi untuk menyematkan diagram kaya ke dalam dokumen Anda.

## Jawaban Cepat
- **Kelas utama apa yang digunakan untuk membuat diagram?** `DocumentBuilder` dengan `insertChart`.
- **Metode apa yang menambahkan seri baru?** `chart.getSeries().add(...)`.
- **Bagaimana cara memformat label data diagram?** Gunakan `getDataLabels().get(...).getNumberFormat().setFormatCode(...)`.
- **Bisakah saya menyembunyikan sebuah sumbu?** Ya, panggil `setHidden(true)` pada objek sumbu.
- **Apakah saya memerlukan lisensi untuk Aspose.Words?** Lisensi diperlukan untuk penggunaan produksi; versi percobaan gratis tersedia.

## Apa itu diagram kolom dan mengapa menggunakannya?

Diagram kolom menampilkan data kategorikal sebagai batang vertikal, menjadikannya ideal untuk membandingkan nilai antar grup (penjualan per wilayah, pengeluaran bulanan, dll.). Dalam aplikasi Java, menghasilkan diagram kolom dengan Aspose.Words memungkinkan Anda menyematkan visual ini langsung ke dalam file Word / DOCX tanpa memerlukan Excel atau alat eksternal.

## Cara membuat diagram kolom

Berikut adalah contoh sederhana yang membuat diagram kolom dasar. Kode ini identik dengan cuplikan asli – kami hanya menambahkan komentar penjelas agar lebih mudah diikuti.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Delete default generated series.
chart.getSeries().clear();

// Creating categories and adding data.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

### Menambahkan beberapa seri

Anda dapat **menambahkan beberapa seri** ke diagram kolom dengan memanggil `chart.getSeries().add(...)` berulang kali, seperti yang ditunjukkan di atas. Setiap seri dapat memiliki kumpulan kategori dan nilai masing‑masing, memungkinkan Anda membandingkan beberapa set data secara berdampingan.

## Cara membuat diagram garis dengan label data khusus

Jika Anda memerlukan diagram garis alih‑alih diagram kolom, pola yang sama dapat diterapkan. Contoh ini juga menunjukkan **memformat label data diagram** dengan format angka yang berbeda.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Delete default generated series.
chart.getSeries().clear();

// Adding a series with data and data labels.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Or link format code to a source cell.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

### Menambahkan label data

Pemanggilan `series1.hasDataLabels(true)` **menambahkan label data** ke seri, sementara `setShowValue(true)` membuat nilai aktual terlihat pada diagram.

## Cara mengubah tipe sumbu dan menyesuaikan properti sumbu

Mengubah tipe sumbu (misalnya, dari tanggal ke kategori) memberi Anda kontrol atas cara titik data dipetakan. Cuplikan ini juga menunjukkan cara **menyembunyikan sumbu diagram** jika Anda menginginkan desain minimalis.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Change the X axis to be a category instead of date.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Measured in display units of the Y axis (hundreds).
xAxis.setReverseOrder(true);
xAxis.setMajorTickMark(AxisTickMark.CROSS);
xAxis.setMinorTickMark(AxisTickMark.OUTSIDE);
xAxis.setTickLabelOffset(200);

// Example of hiding the Y axis.
yAxis.setHidden(true);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### Mengubah tipe sumbu

`xAxis.setCategoryType(AxisCategoryType.CATEGORY)` **mengubah tipe sumbu** dari sumbu berbasis tanggal menjadi sumbu kategorikal, memberi Anda kontrol penuh atas penempatan label.

## Cara memformat label data diagram (format angka)

Anda dapat menerapkan pemformatan angka langsung ke sumbu atau label data. Contoh ini memformat angka pada sumbu Y dengan pemisah ribuan.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Kustomisasi diagram tambahan

Selain dasar‑dasarnya, Anda dapat menyesuaikan batas, mengatur interval antar label, menyembunyikan sumbu tertentu, dan lain‑lain. Lihat dokumentasi API Aspose.Words untuk Java untuk daftar lengkap properti.

## Pertanyaan yang Sering Diajukan

**T: Bagaimana cara menambahkan beberapa seri ke sebuah diagram?**  
J: Gunakan `chart.getSeries().add()` untuk setiap seri yang ingin Anda tampilkan. Setiap pemanggilan dapat menyediakan nama unik, array kategori, dan array nilai.

**T: Bagaimana cara memformat label data diagram dengan format angka khusus?**  
J: Akses objek `DataLabels` pada seri dan panggil `getNumberFormat().setFormatCode("format Anda")`. Anda juga dapat menautkan format ke sel sumber dengan `isLinkedToSource(true)`.

**T: Bagaimana cara menyembunyikan sebuah sumbu diagram?**  
J: Panggil `setHidden(true)` pada `ChartAxis` yang ingin Anda sembunyikan (misalnya, `chart.getAxisY().setHidden(true)`).

**T: Apa cara terbaik untuk mengubah tipe sumbu?**  
J: Gunakan `setCategoryType(AxisCategoryType.CATEGORY)` untuk sumbu kategorikal atau `AxisCategoryType.DATE` untuk sumbu tanggal.

**T: Bagaimana cara menambahkan label data ke sebuah seri?**  
J: Aktifkan dengan `series.hasDataLabels(true)` lalu konfigurasikan visibilitas menggunakan `series.getDataLabels().setShowValue(true)`.

## Kesimpulan

Kami telah membahas semua yang Anda perlukan untuk **membuat visualisasi diagram kolom** dengan Aspose.Words untuk Java—dari menyisipkan diagram dasar dan menambahkan beberapa seri, hingga memformat label data diagram, mengubah tipe sumbu, dan menyembunyikan sumbu diagram untuk tampilan bersih. Terapkan teknik ini ke dalam pipeline pelaporan atau pembuatan dokumen Anda untuk menghasilkan dokumen Word profesional yang didorong oleh data.

---

**Terakhir Diperbarui:** 2025-12-13  
**Diuji Dengan:** Aspose.Words untuk Java 24.12 (terbaru)  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}