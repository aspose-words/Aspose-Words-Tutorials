---
date: 2025-12-13
description: تعلم كيفية إنشاء مخطط عمودي وتنسيق تسميات بيانات المخطط باستخدام Aspose.Words
  for Java. استكشف إضافة سلاسل متعددة، وتغيير نوع المحور، وإخفاء محور المخطط.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: كيفية إنشاء مخطط عمودي باستخدام Aspose.Words للـ Java
url: /ar/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مخطط عمودي باستخدام Aspose.Words for Java

في هذا البرنامج التعليمي ستقوم **بإنشاء مخطط عمودي** داخل مستندات Word مباشرةً باستخدام Aspose.Words for Java. سنستعرض إنشاء أنواع مختلفة من المخططات، إضافة سلاسل متعددة، تنسيق تسميات بيانات المخطط، تغيير نوع المحور، وحتى إخفاء محور المخطط عندما تحتاج إلى مظهر أنظف. في النهاية ستحصل على نهج جاهز للإنتاج لتضمين مخططات غنية في مستنداتك.

## إجابات سريعة
- **ما هو الصنف الأساسي لإنشاء مخطط؟** `DocumentBuilder` مع `insertChart`.
- **أي طريقة تُضيف سلسلة جديدة؟** `chart.getSeries().add(...)`.
- **كيف أقوم بتنسيق تسميات بيانات المخطط؟** استخدم `getDataLabels().get(...).getNumberFormat().setFormatCode(...)`.
- **هل يمكنني إخفاء محور؟** نعم، استدعِ `setHidden(true)` على كائن المحور.
- **هل أحتاج إلى ترخيص لـ Aspose.Words؟** الترخيص مطلوب للاستخدام الإنتاجي؛ تتوفر نسخة تجريبية مجانية.

## ما هو المخطط العمودي ولماذا نستخدمه؟

يعرض المخطط العمودي البيانات الفئوية كأعمدة رأسية، مما يجعله مثالياً لمقارنة القيم عبر المجموعات (المبيعات حسب المنطقة، المصاريف الشهرية، إلخ). في تطبيقات Java، يتيح لك إنشاء مخطط عمودي باستخدام Aspose.Words تضمين هذه الرسوم مباشرةً في ملفات Word / DOCX دون الحاجة إلى Excel أو أدوات خارجية.

## كيفية إنشاء مخطط عمودي

فيما يلي مثال بسيط ينشئ مخططًا عموديًا بسيطًا. الشيفرة مطابقة تمامًا للمقتطف الأصلي – أضفنا فقط تعليقات توضيحية لتسهيل الفهم.

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

### إضافة سلاسل متعددة

يمكنك **إضافة سلاسل متعددة** إلى مخطط عمودي عن طريق استدعاء `chart.getSeries().add(...)` بشكل متكرر، كما هو موضح أعلاه. يمكن لكل سلسلة أن تحتوي على مجموعة خاصة من الفئات والقيم، مما يتيح لك مقارنة عدة مجموعات بيانات جنبًا إلى جنب.

## كيفية إنشاء مخطط خط مع تسميات بيانات مخصصة

إذا كنت بحاجة إلى مخطط خط بدلاً من المخطط العمودي، فإن النمط نفسه ينطبق. يوضح هذا المثال أيضًا **تنسيق تسميات بيانات المخطط** باستخدام تنسيقات رقمية مختلفة.

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

### إضافة تسميات البيانات

النداء `series1.hasDataLabels(true)` **يضيف تسميات البيانات** إلى السلسلة، بينما يجعل `setShowValue(true)` القيم الفعلية مرئية على المخطط.

## كيفية تغيير نوع المحور وتخصيص خصائص المحور

تغيير نوع المحور (مثلاً من تاريخ إلى فئة) يتيح لك التحكم في طريقة رسم نقاط البيانات. يوضح هذا المقتطف أيضًا كيفية **إخفاء محور المخطط** إذا كنت تفضل تصميمًا بسيطًا.

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

### تغيير نوع المحور

`xAxis.setCategoryType(AxisCategoryType.CATEGORY)` **يغير نوع المحور** من محور يعتمد على التاريخ إلى محور فئوي، مما يمنحك السيطرة الكاملة على موضع التسميات.

## كيفية تنسيق تسميات بيانات المخطط (تنسيقات رقمية)

يمكنك تطبيق تنسيق رقمي مباشرةً على المحور أو تسميات البيانات. يوضح هذا المثال تنسيق أرقام المحور Y بفاصل آلاف.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## تخصيصات إضافية للمخطط

بعيدًا عن الأساسيات، يمكنك تعديل الحدود، ضبط وحدات الفاصل بين التسميات، إخفاء محاور معينة، والمزيد. راجع وثائق Aspose.Words for Java API للحصول على القائمة الكاملة للخصائص.

## الأسئلة المتكررة

**س: كيف يمكنني إضافة سلاسل متعددة إلى مخطط؟**  
ج: استخدم `chart.getSeries().add()` لكل سلسلة تريد عرضها. يمكن لكل استدعاء توفير اسم فريد، ومصفوفة فئات، ومصفوفة قيم.

**س: كيف أقوم بتنسيق تسميات بيانات المخطط باستخدام تنسيقات رقمية مخصصة؟**  
ج: احصل على كائن `DataLabels` الخاص بالسلسلة واستدعِ `getNumberFormat().setFormatCode("your format")`. يمكنك أيضًا ربط التنسيق بخلية مصدر باستخدام `isLinkedToSource(true)`.

**س: كيف يمكنني إخفاء محور المخطط؟**  
ج: استدعِ `setHidden(true)` على كائن `ChartAxis` الذي تريد إخفائه (مثال: `chart.getAxisY().setHidden(true)`).

**س: ما هي الطريقة الأفضل لتغيير نوع المحور؟**  
ج: استخدم `setCategoryType(AxisCategoryType.CATEGORY)` للمحاور الفئوية أو `AxisCategoryType.DATE` للمحاور التاريخية.

**س: كيف أضيف تسميات بيانات إلى سلسلة؟**  
ج: فعّلها باستخدام `series.hasDataLabels(true)` ثم اضبط الرؤية عبر `series.getDataLabels().setShowValue(true)`.

## الخلاصة

لقد غطينا كل ما تحتاجه **لإنشاء مخططات عمودية** باستخدام Aspose.Words for Java—من إدراج مخططات أساسية وإضافة سلاسل متعددة، إلى تنسيق تسميات بيانات المخطط، تغيير نوع المحور، وإخفاء محاور المخطط للحصول على مظهر نظيف. دمج هذه التقنيات في خطوط تقاريرك أو عمليات توليد المستندات سيمنحك مستندات Word احترافية مدعومة بالبيانات.

---

**آخر تحديث:** 2025-12-13  
**تم الاختبار مع:** Aspose.Words for Java 24.12 (الأحدث)  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}