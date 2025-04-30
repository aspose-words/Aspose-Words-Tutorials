---
"description": "Pelajari cara membuat dan menyesuaikan bagan di Aspose.Words untuk Java. Jelajahi jenis bagan, pemformatan, dan properti sumbu untuk visualisasi data."
"linktitle": "Menggunakan Grafik"
"second_title": "API Pemrosesan Dokumen Java Aspose.Words"
"title": "Menggunakan Bagan di Aspose.Words untuk Java"
"url": "/id/java/document-conversion-and-export/using-charts/"
"weight": 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Menggunakan Bagan di Aspose.Words untuk Java


## Pengantar Penggunaan Grafik di Aspose.Words untuk Java

Dalam tutorial ini, kita akan mempelajari cara bekerja dengan grafik menggunakan Aspose.Words untuk Java. Anda akan mempelajari cara membuat berbagai jenis grafik, menyesuaikan properti sumbu, memformat label data, dan banyak lagi. Mari kita mulai!

## Membuat Diagram Garis

Untuk membuat diagram garis, gunakan kode berikut:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Hapus seri yang dihasilkan secara default.
chart.getSeries().clear();

// Menambahkan seri dengan data dan label data.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Atau tautan kode format ke sel sumber.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

## Membuat Jenis Grafik Lainnya

Anda dapat membuat berbagai jenis bagan seperti kolom, area, gelembung, sebaran, dan lainnya menggunakan teknik yang serupa. Berikut ini contoh penyisipan bagan kolom sederhana:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Hapus seri yang dihasilkan secara default.
chart.getSeries().clear();

// Membuat kategori dan menambahkan data.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

## Menyesuaikan Properti Sumbu

Anda dapat menyesuaikan properti sumbu, seperti mengubah jenis sumbu, menetapkan tanda centang, memformat label, dan banyak lagi. Berikut ini contoh penetapan properti sumbu XY:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Hapus seri default dan tambahkan data Anda.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Ubah sumbu X menjadi kategori, bukan tanggal.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Diukur dalam satuan tampilan sumbu Y (ratusan).
xAxis.setReverseOrder(true);
xAxis.setMajorTickMark(AxisTickMark.CROSS);
xAxis.setMinorTickMark(AxisTickMark.OUTSIDE);
xAxis.setTickLabelOffset(200);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

## Memformat Label Data

Anda dapat memformat label data dengan format angka yang berbeda. Berikut contohnya:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Hapus seri default dan tambahkan data Anda.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Kustomisasi Bagan Tambahan

Anda dapat menyesuaikan diagram lebih lanjut dengan menyesuaikan batas, satuan interval antara label, menyembunyikan sumbu diagram, dan banyak lagi. Jelajahi cuplikan kode yang disediakan untuk mempelajari lebih lanjut tentang opsi ini.

## Kesimpulan

Dalam tutorial ini, kami telah mempelajari cara bekerja dengan bagan menggunakan Aspose.Words untuk Java. Anda telah mempelajari cara membuat berbagai jenis bagan, menyesuaikan properti sumbu, memformat label data, dan banyak lagi. Aspose.Words untuk Java menyediakan alat yang hebat untuk menambahkan representasi visual data ke dokumen Anda, meningkatkan cara Anda menyajikan informasi.

## Pertanyaan yang Sering Diajukan

### Bagaimana cara menambahkan beberapa seri ke bagan?

Anda dapat menambahkan beberapa seri ke bagan menggunakan `chart.getSeries().add()` metode. Pastikan untuk menentukan nama seri, kategori, dan nilai data.

### Bagaimana cara memformat label data dengan format angka khusus?

Anda dapat memformat label data dengan mengakses `DataLabels` properti seri dan pengaturan kode format yang diinginkan menggunakan `getNumberFormat().setFormatCode()`.

### Bagaimana cara menyesuaikan properti sumbu dalam bagan?

Anda dapat menyesuaikan properti sumbu seperti jenis, tanda centang, label, dan lainnya dengan mengakses `ChartAxis` properti seperti `setCategoryType()`Bahasa Indonesia: `setCrosses()`, Dan `setMajorTickMark()`.

### Bagaimana cara membuat jenis grafik lain seperti grafik sebar atau area?

Anda dapat membuat berbagai jenis grafik dengan menentukan jenis yang sesuai `ChartType` saat memasukkan grafik menggunakan `builder.insertChart(ChartType.TYPE, width, height)`.

### Bagaimana cara menyembunyikan sumbu grafik?

Anda dapat menyembunyikan sumbu grafik dengan mengatur `setHidden(true)` properti sumbu.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}