---
date: 2026-02-16
description: Pelajari cara menambahkan beberapa seri ke diagram di Aspose.Words untuk
  Java, mengubah tanda pada sumbu, menerapkan format angka khusus, dan menghasilkan
  dokumen Word berisi grafik garis dan kolom.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Tambahkan Beberapa Seri ke Grafik di Aspose.Words untuk Java
url: /id/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tambahkan Beberapa Seri ke Grafik di Aspose.Words untuk Java

## Pengantar Penggunaan Grafik di Aspose.Words untuk Java

Dalam tutorial ini Anda akan mempelajari **cara menambahkan beberapa seri** ke sebuah grafik menggunakan Aspose.Words untuk Java, mengapa menyesuaikan tanda centang sumbu dan menerapkan format angka khusus penting, serta cara menghasilkan dokumen Word yang kaya grafik. Baik Anda memerlukan grafik garis untuk data keuangan atau grafik kolom untuk angka penjualan, langkah‑langkah di bawah ini akan memandu Anda dalam membuat, menata, dan menyempurnakan grafik secara programatis.

## Jawaban Cepat
- **Bagaimana cara menambahkan beberapa seri?** Gunakan `chart.getSeries().add(...)` untuk setiap seri yang ingin Anda tampilkan.  
- **Apakah saya dapat mengubah tanda centang sumbu?** Ya – gunakan `setMajorTickMark()` dan `setMinorTickMark()` pada objek sumbu.  
- **Format apa yang dapat saya terapkan pada label data?** Format angka apa pun yang kompatibel dengan Excel, misalnya `"$"#,##0.00` atau `0.00%`.  
- **Jenis grafik apa yang didukung?** Garis, kolom, area, gelembung, sebar, dan banyak lagi melalui `ChartType`.  
- **Apakah lisensi diperlukan untuk produksi?** Lisensi Aspose.Words untuk Java yang valid diperlukan untuk fungsi penuh.

## Apa itu “menambahkan beberapa seri” dalam sebuah grafik?
Menambahkan beberapa seri berarti menyisipkan lebih dari satu set data ke dalam area grafik yang sama, memungkinkan Anda membandingkan kategori atau periode waktu yang berbeda berdampingan. Setiap seri muncul sebagai garis, kolom, atau set penanda tersendiri, memberikan pembaca cerita visual yang lebih kaya.

## Mengapa menggunakan Aspose.Words untuk Java untuk menghasilkan dokumen Word berisi grafik?
- **Kontrol penuh** atas jenis grafik, tata letak, dan gaya tanpa harus membuka Word secara manual.  
- **Pembuatan secara programatis** cocok untuk alur kerja pelaporan otomatis.  
- **Lintas platform** – berfungsi pada lingkungan apa pun yang kompatibel dengan Java.  
- **API lengkap** untuk menyesuaikan sumbu, label data, dan format angka.

## Prasyarat
- Java Development Kit (JDK) 8 atau lebih tinggi.  
- Perpustakaan Aspose.Words untuk Java ditambahkan ke proyek Anda (Maven/Gradle atau JAR).  
- Lisensi Aspose yang valid untuk produksi (opsional untuk evaluasi).

## Panduan Langkah‑per‑Langkah

### Langkah 1: Buat grafik garis dan **tambahkan beberapa seri**
Berikut adalah kode inti yang membuat grafik garis, menghapus seri default, dan kemudian menambahkan tiga seri berbeda dengan label data khusus.

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

> **Tip pro:** Panggil `chart.getSeries().add(...)` sebanyak yang diperlukan untuk **menambahkan beberapa seri** – setiap pemanggilan membuat garis baru (atau kolom, dll.) pada grafik yang sama.

### Langkah 2: **Buat grafik kolom** (create column chart java)
Potongan kode berikut menunjukkan cara menyisipkan grafik kolom sederhana, yang berguna untuk membandingkan kategori berdampingan.

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

### Langkah 3: **Ubah tanda centang sumbu** (change axis tick marks)
Menyesuaikan sumbu X dan Y meningkatkan keterbacaan. Kode berikut menunjukkan cara mengubah tanda centang, membalik urutan, dan menetapkan titik pertemuan khusus.

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

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### Langkah 4: **Terapkan format angka khusus** (apply custom number format)
Anda dapat memformat angka sumbu atau label data dengan pola apa pun yang didukung Excel. Berikut contoh singkat yang memformat sumbu Y dengan pola pemisah ribuan.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

### Langkah 5: Hasilkan dokumen Word akhir (generate chart word document)
Setelah mengonfigurasi seri, sumbu, dan label, cukup panggil `doc.save(...)` seperti yang ditunjukkan pada potongan kode di atas. File `.docx` yang dihasilkan berisi grafik yang berfungsi penuh dan dapat dibuka serta diedit di Microsoft Word.

## Kasus Penggunaan Umum
- **Dasbor keuangan** – grafik garis dengan beberapa seri untuk pendapatan, pengeluaran, dan keuntungan.  
- **Laporan penjualan** – grafik kolom yang membandingkan penjualan kuartalan di berbagai wilayah.  
- **Pelacakan proyek** – grafik area atau sebar yang memvisualisasikan kemajuan seiring waktu.  

## Kustomisasi Grafik Tambahan
Selain dasar-dasar, Anda dapat menyesuaikan batas, menyembunyikan sumbu (`axis.setHidden(true)`), mengubah warna, menambahkan legenda, dan lainnya. Lihat referensi API Aspose.Words untuk Java untuk daftar lengkap opsi.

## Kesimpulan
Dalam panduan ini kami membahas cara **menambahkan beberapa seri** ke grafik, membuat grafik garis dan kolom, **mengubah tanda centang sumbu**, **menerapkan format angka khusus**, dan akhirnya **menghasilkan dokumen Word yang kaya grafik**. Dengan Aspose.Words untuk Java Anda memiliki cara yang kuat dan berorientasi kode untuk menyematkan visualisasi data profesional langsung ke dalam dokumen Anda.

## Pertanyaan yang Sering Diajukan

**Q: Bagaimana cara menambahkan beberapa seri ke sebuah grafik?**  
A: Panggil `chart.getSeries().add()` untuk setiap seri yang ingin Anda tampilkan. Setiap pemanggilan membuat set data baru yang muncul sebagai garis, kolom, atau grup penanda tersendiri.

**Q: Bagaimana cara memformat label data dengan format angka khusus?**  
A: Akses objek `DataLabels` pada seri dan gunakan `getNumberFormat().setFormatCode("pola Anda")`. Anda juga dapat menautkan format ke sel sumber dengan `isLinkedToSource(true)`.

**Q: Bagaimana cara mengubah tanda centang sumbu?**  
A: Gunakan `setMajorTickMark()` dan `setMinorTickMark()` pada `ChartAxis`. Pilihan termasuk `CROSS`, `INSIDE`, `OUTSIDE`, dan `NONE`.

**Q: Apakah saya dapat membuat jenis grafik lain seperti grafik sebar atau area?**  
A: Ya – tentukan `ChartType` yang diinginkan (misalnya `ChartType.SCATTER`, `ChartType.AREA`) saat memanggil `builder.insertChart(...)`.

**Q: Bagaimana cara menyembunyikan sumbu yang tidak saya perlukan?**  
A: Panggil `axis.setHidden(true)` pada `ChartAxis` yang ingin Anda sembunyikan.

---

**Terakhir Diperbarui:** 2026-02-16  
**Diuji Dengan:** Aspose.Words for Java 24.11  
**Penulis:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}