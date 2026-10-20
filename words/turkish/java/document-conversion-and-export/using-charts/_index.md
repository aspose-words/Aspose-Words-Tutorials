---
date: 2025-12-13
description: Aspose.Words for Java ile sütun grafiği oluşturmayı ve grafik veri etiketlerini
  biçimlendirmeyi öğrenin. Birden fazla seri eklemeyi, eksen tipini değiştirmeyi ve
  grafik eksenini gizlemeyi keşfedin.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java kullanarak sütun grafik nasıl oluşturulur
url: /tr/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java ile sütun grafik nasıl oluşturulur

Bu öğreticide **sütun grafik** görselleştirmelerini doğrudan Word belgelerinde Aspose.Words for Java kullanarak oluşturacaksınız. Farklı grafik tipleri oluşturma, birden fazla seri ekleme, grafik veri etiketlerini biçimlendirme, eksen tipini değiştirme ve daha temiz bir görünüm için bir ekseni gizleme konularını adım adım inceleyeceğiz. Sonunda belgelerinize zengin grafikler yerleştirmek için üretim‑hazır bir yaklaşıma sahip olacaksınız.

## Hızlı Yanıtlar
- **Grafik oluşturmak için temel sınıf nedir?** `DocumentBuilder` ve `insertChart`.
- **Yeni bir seri ekleyen yöntem hangisidir?** `chart.getSeries().add(...)`.
- **Grafik veri etiketlerini nasıl biçimlendiririm?** `getDataLabels().get(...).getNumberFormat().setFormatCode(...)` kullanın.
- **Bir ekseni gizleyebilir miyim?** Evet, eksen nesnesinde `setHidden(true)` çağırın.
- **Aspose.Words için lisansa ihtiyacım var mı?** Üretim kullanımı için lisans gereklidir; ücretsiz deneme sürümü mevcuttur.

## Sütun grafik nedir ve neden kullanılır?

Sütun grafik, kategorik verileri dikey çubuklar halinde gösterir ve gruplar arasındaki değerleri karşılaştırmak için idealdir (bölge bazında satış, aylık harcamalar vb.). Java uygulamalarında Aspose.Words ile bir sütun grafik oluşturmak, bu görselleri Excel veya dış araçlar kullanmadan doğrudan Word / DOCX dosyalarına yerleştirmenizi sağlar.

## Sütun grafik nasıl oluşturulur

Aşağıda basit bir sütun grafik oluşturan doğrudan örnek kod yer alıyor. Kod orijinal snippet ile aynı – sadece anlaşılmasını kolaylaştırmak için açıklayıcı yorumlar ekledik.

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

### Birden fazla seri ekleme

Yukarıda gösterildiği gibi `chart.getSeries().add(...)` metodunu tekrar tekrar çağırarak **birden fazla seri** ekleyebilirsiniz. Her seri kendi kategori ve değer setine sahip olabilir, bu da birden çok veri kümesini yan‑yana karşılaştırmanıza olanak tanır.

## Özel veri etiketli çizgi grafik nasıl oluşturulur

Sütun grafik yerine bir çizgi grafik ihtiyacınız varsa aynı desen geçerlidir. Bu örnek ayrıca **grafik veri etiketlerini** farklı sayı formatlarıyla biçimlendirmeyi de gösterir.

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

### Veri etiketleri ekleme

`series1.hasDataLabels(true)` çağrısı **veri etiketlerini** seriye ekler, `setShowValue(true)` ise gerçek değerlerin grafikte görünür olmasını sağlar.

## Eksen tipini değiştirme ve eksen özelliklerini özelleştirme

Eksen tipini (ör. tarih‑tabanlıdan kategori‑tabanlıya) değiştirmek, veri noktalarının nasıl çizileceğini kontrol etmenizi sağlar. Bu snippet ayrıca **grafik eksenini gizleme** yöntemini de gösterir.

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

### Eksen tipini değiştirme

`xAxis.setCategoryType(AxisCategoryType.CATEGORY)` **ekseni tarih‑tabanlı bir eksenden kategori eksenine** değiştirir ve etiket yerleşimi üzerinde tam kontrol sağlar.

## Grafik veri etiketlerini (sayı formatları) biçimlendirme

Sayı formatlamasını doğrudan eksene veya veri etiketlerine uygulayabilirsiniz. Bu örnek Y‑ekseni sayılarını binlik ayırıcı ile biçimlendirir.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Ek grafik özelleştirmeleri

Temel konuların ötesinde sınırları ayarlayabilir, etiketler arasındaki aralık birimlerini belirleyebilir, belirli eksenleri gizleyebilir ve daha fazlasını yapabilirsiniz. Tam özellik listesi için Aspose.Words for Java API dokümantasyonuna bakın.

## Sık Sorulan Sorular

**S: Bir grafiğe birden fazla seri nasıl eklenir?**  
C: Görüntülemek istediğiniz her seri için `chart.getSeries().add()` kullanın. Her çağrı benzersiz bir ad, kategori dizisi ve değer dizisi sağlayabilir.

**S: Grafik veri etiketlerini özel sayı formatlarıyla nasıl biçimlendiririm?**  
C: Bir serinin `DataLabels` nesnesine erişin ve `getNumberFormat().setFormatCode("your format")` çağırın. Ayrıca `isLinkedToSource(true)` ile formatı kaynak hücreye bağlayabilirsiniz.

**S: Bir grafik eksenini nasıl gizleyebilirim?**  
C: Gizlemek istediğiniz `ChartAxis` üzerinde `setHidden(true)` çağırın (ör. `chart.getAxisY().setHidden(true)`).

**S: Eksen tipini değiştirmek için en iyi yol nedir?**  
C: Kategorik eksenler için `setCategoryType(AxisCategoryType.CATEGORY)`, tarih eksenleri için `AxisCategoryType.DATE` kullanın.

**S: Bir seriye veri etiketleri nasıl eklenir?**  
C: `series.hasDataLabels(true)` ile etkinleştirin ve ardından `series.getDataLabels().setShowValue(true)` ile görünürlüğü ayarlayın.

## Sonuç

Aspose.Words for Java ile **sütun grafik** görselleştirmeleri oluşturmak için temel grafik ekleme, birden fazla seri ekleme, grafik veri etiketlerini biçimlendirme, eksen tipini değiştirme ve temiz bir görünüm için eksenleri gizleme konularını ele aldık. Bu teknikleri raporlama veya belge‑oluşturma süreçlerinize entegre ederek profesyonel, veri‑odaklı Word belgeleri sunabilirsiniz.

---

**Son Güncelleme:** 2025-12-13  
**Test Edilen:** Aspose.Words for Java 24.12 (en son)  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}