---
title: Java için Aspose.Words'de Grafiklerin Kullanımı
linktitle: Grafikleri Kullanma
second_title: Aspose.Words Java Belge İşleme API'si
description: Java için Aspose.Words'de grafiklerin nasıl oluşturulacağını ve özelleştirileceğini öğrenin. Veri görselleştirme için grafik türlerini, biçimlendirmeyi ve eksen özelliklerini keşfedin.
weight: 12
url: /tr/java/document-conversion-and-export/using-charts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java için Aspose.Words'de Grafiklerin Kullanımı


## Java için Aspose.Words'de Grafiklerin Kullanımına Giriş

Bu eğitimde, Java için Aspose.Words kullanarak grafiklerle nasıl çalışılacağını keşfedeceğiz. Çeşitli grafik türleri oluşturmayı, eksen özelliklerini özelleştirmeyi, veri etiketlerini biçimlendirmeyi ve daha fazlasını öğreneceksiniz. Hadi başlayalım!

## Çizgi Grafiği Oluşturma

Çizgi grafiği oluşturmak için aşağıdaki kodu kullanın:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Varsayılan olarak oluşturulan seriyi sil.
chart.getSeries().clear();

// Veri ve veri etiketleriyle bir seri ekleme.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Veya biçim kodunu bir kaynak hücreye bağlayın.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

## Diğer Grafik Türlerinin Oluşturulması

Benzer teknikleri kullanarak sütun, alan, balon, dağılım ve daha fazlası gibi farklı grafik türleri oluşturabilirsiniz. İşte basit bir sütun grafiği eklemenin bir örneği:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Varsayılan olarak oluşturulan seriyi sil.
chart.getSeries().clear();

// Kategori oluşturma ve veri ekleme.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

## Eksen Özelliklerini Özelleştirme

Eksen türünü değiştirme, işaret çizgilerini ayarlama, etiketleri biçimlendirme ve daha fazlası gibi eksen özelliklerini özelleştirebilirsiniz. İşte XY eksen özelliklerini tanımlamanın bir örneği:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Varsayılan seriyi temizleyin ve verilerinizi ekleyin.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// X eksenini tarih yerine kategori olarak değiştirin.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // ekseninin (yüzlerce) gösterge birimleriyle ölçülmüştür.
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

## Veri Etiketlerini Biçimlendirme

Veri etiketlerini farklı sayı biçimleriyle biçimlendirebilirsiniz. İşte bir örnek:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Varsayılan seriyi temizleyin ve verilerinizi ekleyin.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Ek Grafik Özelleştirmeleri

Sınırları, etiketler arasındaki aralık birimlerini, grafik eksenlerini gizlemeyi ve daha fazlasını ayarlayarak grafiklerinizi daha da özelleştirebilirsiniz. Bu seçenekler hakkında daha fazla bilgi edinmek için sağlanan kod parçacıklarını inceleyin.

## Çözüm

Bu eğitimde, Aspose.Words for Java kullanarak grafiklerle nasıl çalışılacağını inceledik. Çeşitli grafik türlerinin nasıl oluşturulacağını, eksen özelliklerinin nasıl özelleştirileceğini, veri etiketlerinin nasıl biçimlendirileceğini ve daha fazlasını öğrendiniz. Aspose.Words for Java, belgelerinize verilerin görsel temsillerini eklemek ve bilgileri sunma şeklinizi geliştirmek için güçlü araçlar sağlar.

## SSS

### Bir grafiğe birden fazla seri nasıl ekleyebilirim?

 Bir grafiğe birden fazla seriyi kullanarak ekleyebilirsiniz.`chart.getSeries().add()` yöntem. Seri adını, kategorileri ve veri değerlerini belirttiğinizden emin olun.

### Veri etiketlerini özel sayı biçimleriyle nasıl biçimlendirebilirim?

Veri etiketlerini şuraya erişerek biçimlendirebilirsiniz:`DataLabels` bir serinin özelliklerini ve istenilen biçim kodunu kullanarak ayarlama`getNumberFormat().setFormatCode()`.

### Bir grafikteki eksen özelliklerini nasıl özelleştirebilirim?

 Tür, onay işaretleri, etiketler ve daha fazlası gibi eksen özelliklerini şuraya erişerek özelleştirebilirsiniz:`ChartAxis` gibi özellikler`setCategoryType()`, `setCrosses()` , Ve`setMajorTickMark()`.

### Dağılım veya alan grafikleri gibi diğer grafik türlerini nasıl oluşturabilirim?

 Uygun olanı belirterek çeşitli grafik türleri oluşturabilirsiniz.`ChartType` kullanarak grafik eklerken`builder.insertChart(ChartType.TYPE, width, height)`.

### Bir grafik eksenini nasıl gizleyebilirim?

 Bir grafik eksenini ayarlayarak gizleyebilirsiniz.`setHidden(true)` eksenin özelliği.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
