---
category: general
date: 2026-10-07
description: تعلم كيفية إنشاء مخطط دائري في Word، وإضافة سلاسل البيانات، وحفظ المخطط
  بصيغة PNG باستخدام Java. اتبع الدليل خطوة بخطوة للحصول على نتائج سريعة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add data series
- save chart as png
- generate pie chart in word
- save word chart as image
language: ar
lastmod: 2026-10-07
og_description: 'إنشاء مخطط دائري في Word بسرعة: يوضح هذا الدرس كيفية إضافة سلسلة
  بيانات، إنشاء المخطط، وحفظ مخطط Word كصورة (PNG). اتبع مثال الشيفرة الكامل.'
og_image_alt: Screenshot of a create pie chart result in a Word document
og_title: إنشاء مخطط دائري في Word وتصديره كملف PNG – دليل
schemas:
- author: GroupDocs
  dateModified: '2026-10-07'
  description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  headline: How to create a pie chart in Word and save it as PNG
  type: TechArticle
- description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  name: How to create a pie chart in Word and save it as PNG
  steps:
  - name: Load the source document
    text: You must open the Word file that will host the chart. The `Document` class
      reads the `.docx` content into memory.
  - name: Add data series to the chart
    text: Creating a **pie chart** starts with a `Chart` instance. The constructor
      receives the parent `Document` and the chart type (`ChartType.PIE`). After the
      chart object exists, you populate it with numeric values and optional labels.
  - name: Save chart as PNG
    text: Once the chart is part of the document, you can export the visual representation.
      The `save` method on the underlying chart object writes a PNG file to the file
      system.
  type: HowTo
tags:
- Java
- Word automation
- Chart generation
title: كيفية إنشاء مخطط دائري في Word وحفظه بصيغة PNG
url: /ar/java/document-conversion-and-export/how-to-create-a-pie-chart-in-word-and-save-it-as-png/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مخطط دائري في Word وحفظه كملف PNG

إذا كنت بحاجة إلى **إنشاء مخطط دائري** داخل ملف Microsoft Word، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك باستخدام Java. ستتعلم أيضًا كيفية **إضافة سلسلة بيانات** إلى المخطط و**حفظ المخطط كملف PNG** حتى يمكن إعادة استخدام الصورة خارج Word.

إنشاء مخطط مباشرةً داخل المستند يوفر عليك الحاجة إلى تصدير البيانات إلى أداة رسومية منفصلة. بنهاية هذا الدرس ستحصل على ملف Word يعمل بالكامل يحتوي على مخطط دائري وصورة PNG مطابقة مخزنة على القرص.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من أن لديك:

* Java 17 أو أحدث مثبت.
* مكتبة **GroupDocs.Viewer for Java** (أو مكتبة متوافقة توفر الفئات `Document`، `Chart`، `ChartType`، و`ImageSaveOptions`).
* مشروع Maven أو Gradle حيث يمكنك إضافة تبعية المكتبة.
* مستند Word إدخال (`input.docx`) موجود في مجلد يمكنك الإشارة إليه من الشيفرة.

إذا كنت تستخدم Maven، أضف التبعية (استبدل `VERSION` بأحدث إصدار):

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>VERSION</version>
</dependency>
```

## كيفية إنشاء مخطط دائري في Word

تكمن جوهر الحل حول ثلاث عمليات:

1. تحميل ملف `.docx` المصدر.
2. **إضافة سلسلة بيانات** إلى كائن `Chart` جديد من النوع `PIE`.
3. **حفظ المخطط كملف PNG** للحصول على ملف صورة بجوار مستند Word.

فيما يلي شرح مفصل لكل خطوة، يليه الشيفرة Java الدقيقة التي تحتاجها.

### الخطوة 1: تحميل المستند المصدر

يجب فتح ملف Word الذي سيستضيف المخطط. تقوم الفئة `Document` بقراءة محتوى `.docx` إلى الذاكرة.

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*لماذا هذا مهم*: تحميل المستند ينشئ نموذجًا قابلًا للتعديل. جميع عمليات المخطط اللاحقة تعدل هذا التمثيل في الذاكرة، والذي تقوم لاحقًا بحفظه مرة أخرى على القرص.

### الخطوة 2: إضافة سلسلة بيانات إلى المخطط

إنشاء **مخطط دائري** يبدأ بإنشاء كائن `Chart`. يتلقى المُنشئ المستند الأب `Document` ونوع المخطط (`ChartType.PIE`). بعد وجود كائن المخطط، تقوم بملئه بالقيم الرقمية والملصقات الاختيارية.

```java
// Step 2: Create a pie chart and configure its data series
Chart chart = new Chart(doc, ChartType.PIE);

// Example: add a data series (replace with your actual data)
double[] values = { 30, 20, 50 };
String[] categories = { "A", "B", "C" };
chart.getSeries().add(values, categories);
```

*لماذا هذا مهم*: طريقة `add` **تضيف سلسلة بيانات** إلى المخطط. كل عنصر في `values` يصبح شريحة من الدائرة، بينما `categories` توفر تسميات الأسطورة. يمكنك توفير أي عدد من النقاط؛ ستحسب المكتبة زوايا الشرائح تلقائيًا.

### الخطوة 3: حفظ المخطط كملف PNG

بمجرد أن يصبح المخطط جزءًا من المستند، يمكنك تصدير التمثيل البصري. تقوم طريقة `save` على كائن المخطط الأساسي بكتابة ملف PNG إلى نظام الملفات.

```java
// Step 3: Save the chart as a PNG image (graduations are added automatically)
chart.getChartShape()
     .getChart()
     .save("YOUR_DIRECTORY/radial.png",
           ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

*لماذا هذا مهم*: حفظ المخطط كملف PNG يمنحك صورة نقطية يمكن تضمينها في صفحات الويب أو الرسائل الإلكترونية أو التقارير دون الحاجة إلى ملف Word الأصلي. تسمح لك كائن `ImageSaveOptions` بالتحكم في الصيغة والدقة وإعدادات التصدير الأخرى.

## إنشاء مخطط دائري في Word – تخصيص المظهر

إلى جانب الخطوات الأساسية، قد ترغب في تخصيص الألوان أو العناوين أو تسميات البيانات. معظم المكتبات تكشف عن كائن `ChartOptions` أو ما شابه. إليك مثالًا سريعًا يضيف عنوانًا ويغير ألوان الشرائح:

```java
chart.getChart().setTitle("Sales Distribution Q1");

// Set custom colors (RGB format)
chart.getSeries().get(0).setColors(new int[] {
    0xFF5733, // slice A – orange
    0x33FF57, // slice B – green
    0x3357FF  // slice C – blue
});
```

هذه التخصيصات اختيارية لكنها توضح كيف يمكنك **إنشاء مخطط دائري في Word** يتوافق مع هوية علامتك التجارية.

## حفظ مخطط Word كصورة – طرق بديلة

إذا كنت تحتاج فقط إلى الصورة وليس المخطط داخل المستند، يمكنك تخطي إدراج شكل المخطط في ملف Word واستدعاء طريقة `save` مباشرةً بعد إنشاء المخطط. يظل الكود كما هو؛ فقط تتخطى أي خطوة تضيف المخطط إلى جسم المستند.

```java
// Directly save the chart without embedding it in the document
chart.getChart().save("YOUR_DIRECTORY/pie_only.png",
                      ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

هذه التقنية مفيدة عندما تقوم بإنشاء العديد من المخططات في عملية دفعة وتهمك فقط مخرجات PNG.

## مثال كامل قابل للتنفيذ

انسخ الفئة التالية إلى مشروعك، عدل مسارات الملفات، وشغّلها. سيقوم البرنامج بـ:

1. تحميل `input.docx`.
2. **إنشاء مخطط دائري**، **إضافة سلسلة بيانات**، وتضمينه في المستند.
3. **حفظ المخطط كملف PNG** (`radial.png`).
4. حفظ ملف Word المعدل كـ `output.docx`.



## ماذا يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء مخطط عمودي باستخدام Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [إنشاء مخطط مبعثر في Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [إدراج مخطط عمودي في Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}