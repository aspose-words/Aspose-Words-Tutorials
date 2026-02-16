---
date: 2026-02-16
description: Aspose.Words for Java'da grafiklere birden fazla seri eklemeyi, eksen
  işaretçilerini değiştirmeyi, özel sayı formatı uygulamayı ve çizgi ile sütun grafiklerini
  içeren Word belgeleri oluşturmayı öğrenin.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java'da Grafiklere Birden Çok Seri Ekle
url: /tr/java/document-conversion-and-export/using-charts/
weight: 12
---

 `chart.getSeries().add()` ...

So Q is bold, A not bold. We'll translate similarly: **S:** (question) and C: (answer) maybe keep same pattern? Should we keep **Q:**? The translation says "S:" for soru, but we could keep **S:** bold. Keep same formatting: **S:** ... then line break, C: ... (no bold). That matches original style.

Make sure we keep line breaks.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java'da Grafiklere Birden Çok Seri Ekleme

## Aspose.Words for Java'da Grafik Kullanımına Giriş

Bu öğreticide Aspose.Words for Java kullanarak bir grafiğe **birden çok seri eklemeyi**, eksen işaretçilerini özelleştirmenin ve özel bir sayı formatı uygulamanın neden önemli olduğunu ve grafik‑zengin bir Word belgesi oluşturmayı öğreneceksiniz. Finansal veriler için bir çizgi grafiği ya da satış rakamları için bir sütun grafiği ihtiyacınız olsun, aşağıdaki adımlar grafik oluşturma, stil verme ve programlı olarak ince ayar yapma sürecinde size rehberlik edecektir.

## Hızlı Yanıtlar
- **Birden çok seri nasıl eklenir?** Görüntülemek istediğiniz her seri için `chart.getSeries().add(...)` kullanın.  
- **Eksen işaretçilerini değiştirebilir miyim?** Evet – eksen nesnelerinde `setMajorTickMark()` ve `setMinorTickMark()` kullanın.  
- **Veri etiketlerine hangi format uygulanabilir?** Excel uyumlu herhangi bir sayı formatı, örneğin `"$"#,##0.00` veya `0.00%`.  
- **Hangi grafik tipleri desteklenir?** Çizgi, sütun, alan, balon, dağılım ve `ChartType` aracılığıyla daha birçok tip.  
- **Üretim ortamında lisans gerekli mi?** Tam işlevsellik için geçerli bir Aspose.Words for Java lisansı gereklidir.

## Grafikte “birden çok seri ekleme” nedir?

Birden çok seri eklemek, aynı grafik alanına birden fazla veri kümesi eklemek anlamına gelir; bu sayede farklı kategorileri veya zaman dilimlerini yan yana karşılaştırabilirsiniz. Her seri kendi çizgi, sütun veya işaretçi seti olarak görünür ve okuyucuya daha zengin bir görsel anlatım sunar.

## Neden Aspose.Words for Java ile grafik içeren Word belgeleri oluşturmalısınız?

- **Tam kontrol** grafik tipi, düzeni ve stil üzerinde, Word'ü manuel olarak açmadan.  
- **Programatik oluşturma** otomatik raporlama hatlarına uyum sağlar.  
- **Çapraz platform** – herhangi bir Java uyumlu ortamda çalışır.  
- **Zengin API** eksen, veri etiketleri ve sayı formatlarını özelleştirmek için.

## Önkoşullar
- Java Development Kit (JDK) 8 veya üzeri.  
- Projenize eklenmiş Aspose.Words for Java kütüphanesi (Maven/Gradle ya da JAR).  
- Üretim için geçerli bir Aspose lisansı (değerlendirme için isteğe bağlı).

## Adım‑Adım Kılavuz

### Adım 1: Bir çizgi grafiği oluşturun ve **birden çok seri ekleyin**
Aşağıda, bir çizgi grafiği oluşturan, varsayılan seriyi temizleyen ve ardından üç ayrı seri ekleyen temel kod yer almaktadır; seriler özel veri etiketleriyle birlikte.

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

> **Pro tip:** `chart.getSeries().add(...)` metodunu ihtiyacınız kadar çağırarak **birden çok seri ekleyin** – her çağrı aynı grafikte yeni bir çizgi (veya sütun, vb.) oluşturur.

### Adım 2: **Bir sütun grafiği oluşturun** (create column chart java)
Aşağıdaki kod parçacığı, yan yana kategorileri karşılaştırmak için kullanışlı bir basit sütun grafiği eklemeyi göstermektedir.

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

### Adım 3: **Eksen işaretçilerini değiştirin** (change axis tick marks)
X ve Y eksenlerini özelleştirmek okunabilirliği artırır. Aşağıdaki kod, işaretçileri değiştirmeyi, sıralamayı ters çevirmeyi ve özel kesişim noktaları ayarlamayı gösterir.

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

### Adım 4: **Özel bir sayı formatı uygulayın** (apply custom number format)
Eksen sayılarını veya veri etiketlerini Excel tarafından desteklenen herhangi bir desenle biçimlendirebilirsiniz. Aşağıda, Y eksenini binlik ayırıcı deseniyle biçimlendiren kısa bir örnek yer almaktadır.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

### Adım 5: Son Word belgesini oluşturun (generate chart word document)
Serileri, eksenleri ve etiketleri yapılandırdıktan sonra, yukarıdaki kod parçacıklarında gösterildiği gibi `doc.save(...)` metodunu çağırmanız yeterlidir. Ortaya çıkan `.docx` dosyası, Microsoft Word'de açılıp düzenlenebilen tam işlevsel grafikler içerir.

## Yaygın Kullanım Senaryoları
- **Finansal panolar** – gelir, gider ve kar için birden çok serili çizgi grafikler.  
- **Satış raporları** – bölgeler arasındaki çeyrek satışları karşılaştıran sütun grafikler.  
- **Proje takibi** – zaman içinde ilerlemeyi görselleştiren alan veya dağılım grafikler.  

## Ek Grafik Özelleştirmeleri
Temel özelliklerin ötesinde, sınırları ayarlayabilir, eksenleri gizleyebilir (`axis.setHidden(true)`), renkleri değiştirebilir, lejand ekleyebilir ve daha fazlasını yapabilirsiniz. Tüm seçeneklerin tam listesi için Aspose.Words for Java API referansına bakın.

## Sonuç
Bu rehberde grafiklere **birden çok seri ekleme**, hem çizgi hem de sütun grafik oluşturma, **eksen işaretçilerini değiştirme**, **özel sayı formatları uygulama** ve nihayet **grafik‑zengin bir Word belgesi oluşturma** konularını ele aldık. Aspose.Words for Java ile belgelerinize doğrudan profesyonel veri görselleştirmeleri eklemenin güçlü, kod‑öncelikli bir yoluna sahip olursunuz.

## Sıkça Sorulan Sorular

**S: Bir grafiğe birden çok seri nasıl ekleyebilirim?**  
C: Görüntülemek istediğiniz her seri için `chart.getSeries().add()` metodunu çağırın. Her çağrı, kendi çizgi, sütun veya işaretçi grubunu oluşturan yeni bir veri seti oluşturur.

**S: Veri etiketlerini özel bir sayı formatıyla nasıl biçimlendirebilirim?**  
C: Serinin `DataLabels` nesnesine erişin ve `getNumberFormat().setFormatCode("your pattern")` metodunu kullanın. Formatı bir kaynak hücreye `isLinkedToSource(true)` ile bağlayabilirsiniz.

**S: Eksen işaretçilerini nasıl değiştirebilirim?**  
C: `ChartAxis` üzerinde `setMajorTickMark()` ve `setMinorTickMark()` metodlarını kullanın. Seçenekler `CROSS`, `INSIDE`, `OUTSIDE` ve `NONE` içerir.

**S: Dağılım veya alan gibi başka grafik tipleri oluşturabilir miyim?**  
C: Evet – `builder.insertChart(...)` çağrısında istediğiniz `ChartType` (örneğin `ChartType.SCATTER`, `ChartType.AREA`) belirtin.

**S: İhtiyacım olmayan bir ekseni nasıl gizleyebilirim?**  
C: Gizlemek istediğiniz `ChartAxis` üzerinde `axis.setHidden(true)` metodunu çağırın.

---

**Son Güncelleme:** 2026-02-16  
**Test Edilen Sürüm:** Aspose.Words for Java 24.11  
**Yazar:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}