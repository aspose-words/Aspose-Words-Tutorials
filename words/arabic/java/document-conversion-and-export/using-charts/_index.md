---
date: 2026-02-16
description: تعرّف على كيفية إضافة سلاسل متعددة إلى المخططات في Aspose.Words for Java،
  وتغيير علامات الفواصل على المحاور، وتطبيق تنسيق رقم مخصص، وإنشاء مستندات Word تحتوي
  على مخططات بخطوط وأعمدة.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: إضافة سلاسل متعددة إلى المخططات في Aspose.Words للـ Java
url: /ar/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إضافة سلاسل متعددة إلى المخططات في Aspose.Words for Java

## مقدمة لاستخدام المخططات في Aspose.Words for Java

في هذا الدرس ستتعلم **كيفية إضافة سلاسل متعددة** إلى مخطط باستخدام Aspose.Words for Java، ولماذا يُعد تخصيص علامات التدرج للمحاور وتطبيق تنسيق رقم مخصص أمرًا مهمًا، وكيفية إنشاء مستند Word غني بالمخططات. سواء كنت بحاجة إلى مخطط خطي للبيانات المالية أو مخطط عمودي لأرقام المبيعات، فإن الخطوات أدناه ستوجهك خلال إنشاء المخططات وتنسيقها وضبطها برمجيًا.

## إجابات سريعة
- **كيف يمكنني إضافة سلاسل متعددة؟** استخدم `chart.getSeries().add(...)` لكل سلسلة تريد عرضها.  
- **هل يمكنني تغيير علامات التدرج للمحاور؟** نعم – استخدم `setMajorTickMark()` و `setMinorTickMark()` على كائنات المحور.  
- **ما التنسيق الذي يمكنني تطبيقه على تسميات البيانات؟** أي تنسيق رقم متوافق مع Excel، مثل `"$"#,##0.00` أو `0.00%`.  
- **ما أنواع المخططات المدعومة؟** الخطية، العمودية، المساحية، الفقاعية، النقطية، والعديد غيرها عبر `ChartType`.  
- **هل يلزم وجود ترخيص للإنتاج؟** يلزم وجود ترخيص صالح لـ Aspose.Words for Java للحصول على كامل الوظائف.

## ما معنى “إضافة سلاسل متعددة” في المخطط؟

إضافة سلاسل متعددة تعني إدراج أكثر من مجموعة بيانات واحدة في نفس مساحة المخطط، مما يتيح لك مقارنة فئات أو فترات زمنية مختلفة جنبًا إلى جنب. تظهر كل سلسلة كخط أو عمود أو مجموعة علامات خاصة بها، مما يمنح القارئ قصة بصرية أغنى.

## لماذا تستخدم Aspose.Words for Java لإنشاء مستندات Word تحتوي على مخططات؟

- **تحكم كامل** في نوع المخطط، التخطيط، والتنسيق دون الحاجة لفتح Word يدويًا.  
- **إنشاء برمجي** يتناسب مع خطوط الأنابيب الآلية للتقارير.  
- **متعدد المنصات** – يعمل على أي بيئة متوافقة مع Java.  
- **API غني** لتخصيص المحاور، تسميات البيانات، وتنسيقات الأرقام.

## المتطلبات المسبقة
- مجموعة تطوير جافا (JDK) الإصدار 8 أو أعلى.  
- مكتبة Aspose.Words for Java مضافة إلى مشروعك (Maven/Gradle أو JAR).  
- ترخيص Aspose صالح للإنتاج (اختياري للتقييم).

## دليل خطوة بخطوة

### الخطوة 1: إنشاء مخطط خطي و**إضافة سلاسل متعددة**
فيما يلي الكود الأساسي الذي ينشئ مخططًا خطيًا، يمسح السلسلة الافتراضية، ثم يضيف ثلاث سلاسل متميزة مع تسميات بيانات مخصصة.

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

> **نصيحة احترافية:** استدعِ `chart.getSeries().add(...)` عدد المرات التي تحتاجها **لإضافة سلاسل متعددة** – كل استدعاء ينشئ خطًا جديدًا (أو عمودًا، إلخ) على نفس المخطط.

### الخطوة 2: **إنشاء مخطط عمودي** (create column chart java)
المقتطف التالي يوضح كيفية إدراج مخطط عمودي بسيط، وهو مفيد لمقارنة الفئات جنبًا إلى جنب.

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

### الخطوة 3: **تغيير علامات التدرج للمحاور** (change axis tick marks)
تخصيص محوري X و Y يحسن قابلية القراءة. يوضح الكود التالي كيفية تغيير علامات التدرج، عكس الترتيب، وتعيين نقاط تقاطع مخصصة.

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

### الخطوة 4: **تطبيق تنسيق رقم مخصص** (apply custom number format)
يمكنك تنسيق أرقام المحور أو تسميات البيانات بأي نمط يدعمه Excel. أدناه مثال مختصر ينسق محور Y بنمط فاصل الآلاف.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

### الخطوة 5: إنشاء مستند Word النهائي (generate chart word document)
بعد تكوين السلاسل، المحاور، والتسميات، ما عليك سوى استدعاء `doc.save(...)` كما هو موضح في المقتطفات أعلاه. يحتوي ملف `.docx` الناتج على مخططات تعمل بالكامل يمكن فتحها وتعديلها في Microsoft Word.

## حالات الاستخدام الشائعة
- **لوحات معلومات مالية** – مخططات خطية بسلاسل متعددة للإيرادات، المصاريف، والربح.  
- **تقارير المبيعات** – مخططات عمودية تقارن المبيعات الفصلية عبر المناطق.  
- **متابعة المشاريع** – مخططات مساحية أو نقطية تصور التقدم عبر الزمن.

## تخصيصات إضافية للمخططات
إلى جانب الأساسيات، يمكنك تعديل الحدود، إخفاء المحاور (`axis.setHidden(true)`)، تغيير الألوان، إضافة وسيلة إيضاح، وأكثر. راجع مرجع Aspose.Words for Java API للحصول على القائمة الكاملة للخيارات.

## الخلاصة
في هذا الدليل غطينا كيفية **إضافة سلاسل متعددة** إلى المخططات، إنشاء كل من المخططات الخطية والعمودية، **تغيير علامات التدرج للمحاور**، **تطبيق تنسيقات رقم مخصصة**، وأخيرًا **إنشاء مستند Word غني بالمخططات**. مع Aspose.Words for Java لديك طريقة قوية تعتمد على الكود لإدراج تصورات بيانات احترافية مباشرة في مستنداتك.

## الأسئلة المتكررة

**س: كيف يمكنني إضافة سلاسل متعددة إلى مخطط؟**  
ج: استدعِ `chart.getSeries().add()` لكل سلسلة تريد عرضها. كل استدعاء ينشئ مجموعة بيانات جديدة تظهر كخط أو عمود أو مجموعة علامات خاصة بها.

**س: كيف أقوم بتنسيق تسميات البيانات باستخدام تنسيق رقم مخصص؟**  
ج: احصل على كائن `DataLabels` الخاص بالسلسلة واستخدم `getNumberFormat().setFormatCode("your pattern")`. يمكنك أيضًا ربط التنسيق بخلية مصدر باستخدام `isLinkedToSource(true)`.

**س: كيف يمكنني تغيير علامات التدرج للمحاور؟**  
ج: استخدم `setMajorTickMark()` و `setMinorTickMark()` على `ChartAxis`. تشمل الخيارات `CROSS`، `INSIDE`، `OUTSIDE`، و `NONE`.

**س: هل يمكنني إنشاء أنواع مخططات أخرى مثل المخططات النقطية أو المساحية؟**  
ج: نعم – حدد `ChartType` المطلوب (مثال: `ChartType.SCATTER`، `ChartType.AREA`) عند استدعاء `builder.insertChart(...)`.

**س: كيف يمكنني إخفاء محور لا أحتاجه؟**  
ج: استدعِ `axis.setHidden(true)` على `ChartAxis` الذي تريد إخفائه.

---

**آخر تحديث:** 2026-02-16  
**تم الاختبار مع:** Aspose.Words for Java 24.11  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}