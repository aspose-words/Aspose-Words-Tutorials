---
"description": "تعرّف على كيفية إنشاء المخططات وتخصيصها في Aspose.Words لجافا. استكشف أنواع المخططات وتنسيقها وخصائص المحاور لتصور البيانات."
"linktitle": "استخدام المخططات البيانية"
"second_title": "واجهة برمجة تطبيقات معالجة مستندات Java Aspose.Words"
"title": "استخدام المخططات البيانية في Aspose.Words للغة Java"
"url": "/ar/java/document-conversion-and-export/using-charts/"
"weight": 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# استخدام المخططات البيانية في Aspose.Words للغة Java


## مقدمة لاستخدام المخططات البيانية في Aspose.Words للغة Java

في هذا البرنامج التعليمي، سنستكشف كيفية العمل مع المخططات البيانية باستخدام Aspose.Words لجافا. ستتعلم كيفية إنشاء أنواع مختلفة من المخططات البيانية، وتخصيص خصائص المحاور، وتنسيق تسميات البيانات، والمزيد. هيا بنا!

## إنشاء مخطط خطي

لإنشاء مخطط خطي، استخدم الكود التالي:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// حذف السلسلة المولدة افتراضيًا.
chart.getSeries().clear();

// إضافة سلسلة تحتوي على بيانات وعناوين بيانات.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// أو قم بربط كود التنسيق بخلية المصدر.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

## إنشاء أنواع أخرى من المخططات البيانية

يمكنك إنشاء أنواع مختلفة من المخططات البيانية، مثل المخطط العمودي، والمخطط المساحي، والمخطط الفقاعي، والمخطط المبعثر، وغيرها باستخدام تقنيات مشابهة. إليك مثال على إدراج مخطط بياني عمودي بسيط:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// حذف السلسلة المولدة افتراضيًا.
chart.getSeries().clear();

// إنشاء الفئات وإضافة البيانات.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

## تخصيص خصائص المحور

يمكنك تخصيص خصائص المحور، مثل تغيير نوع المحور، وتعيين علامات التجزئة، وتنسيق التسميات، وغيرها. إليك مثال على تعريف خصائص المحور X وY:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// مسح السلسلة الافتراضية وإضافة بياناتك.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// قم بتغيير المحور X ليكون فئة بدلاً من التاريخ.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // يتم قياسها بوحدات العرض على المحور Y (المئات).
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

## تنسيق تسميات البيانات

يمكنك تنسيق تسميات البيانات بتنسيقات أرقام مختلفة. إليك مثال:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// مسح السلسلة الافتراضية وإضافة بياناتك.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## تخصيصات إضافية للمخطط

يمكنك تخصيص مخططاتك بشكل أكبر عن طريق ضبط الحدود، ووحدات الفواصل بين التسميات، وإخفاء محاور المخطط، والمزيد. استكشف مقتطفات التعليمات البرمجية المُقدمة لمعرفة المزيد عن هذه الخيارات.

## خاتمة

في هذا البرنامج التعليمي، استكشفنا كيفية العمل مع المخططات البيانية باستخدام Aspose.Words لجافا. تعلمت كيفية إنشاء أنواع مختلفة من المخططات البيانية، وتخصيص خصائص المحاور، وتنسيق تسميات البيانات، والمزيد. يوفر Aspose.Words لجافا أدوات فعّالة لإضافة تمثيلات بصرية للبيانات إلى مستنداتك، مما يُحسّن طريقة عرض المعلومات.

## الأسئلة الشائعة

### كيف يمكنني إضافة سلاسل متعددة إلى الرسم البياني؟

يمكنك إضافة سلاسل متعددة إلى مخطط باستخدام `chart.getSeries().add()` الطريقة. تأكد من تحديد اسم السلسلة والفئات وقيم البيانات.

### كيف يمكنني تنسيق تسميات البيانات باستخدام تنسيقات الأرقام المخصصة؟

يمكنك تنسيق تسميات البيانات عن طريق الوصول إلى `DataLabels` خصائص السلسلة وتعيين رمز التنسيق المطلوب باستخدام `getNumberFormat().setFormatCode()`.

### كيف أقوم بتخصيص خصائص المحور في الرسم البياني؟

يمكنك تخصيص خصائص المحور مثل النوع وعلامات التجزئة والعلامات والمزيد عن طريق الوصول إلى `ChartAxis` خصائص مثل `setCategoryType()`، `setCrosses()`، و `setMajorTickMark()`.

### كيف يمكنني إنشاء أنواع أخرى من الرسوم البيانية مثل الرسوم البيانية المنتشرة أو الرسوم البيانية المساحية؟

يمكنك إنشاء أنواع مختلفة من المخططات عن طريق تحديد الأنواع المناسبة `ChartType` عند إدخال الرسم البياني باستخدام `builder.insertChart(ChartType.TYPE, width, height)`.

### كيف يمكنني إخفاء محور الرسم البياني؟

يمكنك إخفاء محور الرسم البياني عن طريق ضبط `setHidden(true)` خاصية المحور.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}