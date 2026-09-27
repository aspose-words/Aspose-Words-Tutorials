---
category: general
date: 2026-09-27
description: تعرّف على كيفية إدراج مخطط دائري في مستند Word باستخدام Java، وإنشاء
  مخطط دائري في Word، وعرض النسب المئوية على المخطط الدائري للحصول على رؤى واضحة للبيانات.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- create pie chart in word
- show percentages on pie chart
- add chart to word document
- how to add leader lines
language: ar
lastmod: 2026-09-27
og_description: كيفية إدراج مخطط دائري في مستند Word باستخدام Java. يوضح لك هذا الدليل
  كيفية إنشاء مخطط دائري في Word، وعرض النسب المئوية على المخطط الدائري، وإضافة خطوط
  ربط.
og_image_alt: Screenshot of a formatted pie chart inserted into a Word document
og_title: كيفية إدراج مخطط دائري في مستند Word باستخدام Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  headline: How to insert a pie chart into a Word document using Java
  type: TechArticle
- description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  name: How to insert a pie chart into a Word document using Java
  steps:
  - name: Expected output
    text: '![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image
      alt="Formatted pie chart inserted into a Word document"}'
  - name: Changing slice values
    text: 'If you need custom data, replace the default series values:'
  - name: Multiple series (donut chart)
    text: While a simple pie chart has one series, Aspose.Words also supports donut
      charts with multiple series. Switch `ChartType.PIE` to `ChartType.DONUT` and
      repeat the series‑configuration steps.
  - name: Exporting to PDF
    text: If your downstream workflow requires PDF, call `doc.save("output/PieFormatted.pdf");`
      after the chart is built. The visual layout remains identical.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word automation
- Chart
title: كيفية إدراج مخطط دائري في مستند Word باستخدام Java
url: /ar/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إدراج مخطط دائري في مستند Word باستخدام Java

إذا كنت بحاجة إلى **how to insert pie chart** في ملف Word، فإن هذا الدليل سيقودك عبر العملية بالكامل. سترى كيف **create pie chart in Word**، وعرض النسب المئوية على كل شريحة، وإضافة خطوط ربط للحصول على مظهر مصقول.

غالبًا ما يبدو أتمتة Word ثقيلة، ولكن باستخدام Aspose.Words for Java يمكنك إنشاء مستندات منسقة بالكامل برمجيًا. بحلول نهاية هذا الدليل ستحصل على مقتطف Java قابل للتنفيذ ينتج مستند Word يحتوي على مخطط دائري منسق.

## المتطلبات المسبقة

- Java 17 أو أحدث مثبت
- Maven أو Gradle لإدارة التبعيات
- Aspose.Words for Java (الإصدار 23.11 أو أحدث) مضاف إلى مشروعك
- إلمام أساسي بصياغة Java

ليس عليك أن تكون لديك أي خبرة سابقة مع واجهات برمجة المخططات؛ الخطوات أدناه تغطي كل شيء من إعداد المشروع حتى المخرجات النهائية.

## الخطوة 1: إعداد تبعية Maven

أضف مكتبة Aspose.Words إلى ملف `pom.xml`. هذه التبعية الوحيدة تمنحك الوصول إلى `Document` و `DocumentBuilder` وفئات المخططات.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version>
</dependency>
```

إذا كنت تستخدم Gradle، فإن المكافئ هو:

```groovy
implementation 'com.aspose:aspose-words:23.11'
```

> **نصيحة احترافية:** استخدم أحدث نسخة مستقرة للاستفادة من إصلاحات الأخطاء والميزات الجديدة للمخططات.

## الخطوة 2: إنشاء مستند جديد ومُنشئ

كائن `Document` يمثل ملف Word، بينما يتيح لك `DocumentBuilder` إدراج المحتوى. هذا هو الأساس لـ **add chart to word document**.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

المُنشئ الآن جاهز لوضع الكائنات في أي مكان داخل المستند.

## الخطوة 3: إدراج مخطط دائري

يدعم Aspose.Words عدة أنواع من المخططات؛ نختار `ChartType.PIE`. يتم التعبير عن الحجم بالنقاط (1 نقطة = 1/72 بوصة).

```java
        // Step 3: Insert a pie chart with a size of 400x300 points
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

في هذه المرحلة يحتوي المخطط على سلسلة بيانات افتراضية بقيم placeholder. يمكنك استبدال تلك القيم لاحقًا إذا لزم الأمر.

## الخطوة 4: الوصول إلى سلسلة المخطط

يحتوي المخطط الدائري على سلسلة واحدة تحمل قيم الشرائح. استخرجها لتطبيق التنسيق.

```java
        // Step 4: Get the first (and only) series
        ChartSeries series = chart.getSeries().get(0);
```

## الخطوة 5: تفجير الشريحة الأولى

تفجير الشريحة يجذب الانتباه إلى نقطة بيانات معينة. هذا مؤشر بصري شائع عندما تريد إبراز مقياس رئيسي.

```java
        // Step 5: Explode the first slice
        series.setExploded(true);
```

## الخطوة 6: إظهار النسب المئوية على كل شريحة

عرض النسب المئوية مباشرة على المخطط يحسن فهم البيانات. هذا يفي بمتطلب **show percentages on pie chart**.

```java
        // Step 6: Show percentages on each slice
        series.setShowPercentage(true);
```

## الخطوة 7: إضافة خطوط ربط لتوضيح التسميات

خطوط الربط تربط تسميات الشرائح بأقسامها المقابلة، مما يزيل الغموض. هذا يحقق **how to add leader lines**.

```java
        // Step 7: Add leader lines so labels are clearly connected
        series.setShowLeaderLines(true);
```

## الخطوة 8: حفظ المستند

أخيرًا، احفظ المستند على القرص. يمكنك اختيار أي مجلد لديك صلاحية كتابة فيه.

```java
        // Step 8: Save the document with the formatted pie chart
        doc.save("output/PieFormatted.docx");
    }
}
```

تشغيل البرنامج ينشئ `output/PieFormatted.docx`. افتح الملف في Microsoft Word، وسترى مخططًا دائريًا حيث:

- الشريحة الأولى مُنفجرة.
- كل شريحة تظهر قيمتها النسبية.
- خطوط الربط تشير من النسب المئوية إلى الشرائح المقابلة.

### النتيجة المتوقعة

![مخطط دائري منسق في Word](/images/pie-formatted.png){: .center-image alt="مخطط دائري منسق تم إدراجه في مستند Word"}

توضح لقطة الشاشة (نص alt يستخدم الكلمة الرئيسية) المظهر النهائي: مخطط دائري نظيف، قائم على البيانات، جاهز للتقارير أو المقترحات أو لوحات التحكم.

## الاختلافات الشائعة وحالات الحافة

### تغيير قيم الشرائح

إذا كنت بحاجة إلى بيانات مخصصة، استبدل قيم السلسلة الافتراضية:

```java
double[] values = {30, 45, 25};
String[] categories = {"Apples", "Bananas", "Cherries"};
series.getDataLabelCollection().clear(); // remove placeholder labels

for (int i = 0; i < values.length; i++) {
    series.getData().add(values[i]);
    series.getCategory().add(categories[i]);
}
```

### سلاسل متعددة (مخطط دونات)

بينما يحتوي المخطط الدائري البسيط على سلسلة واحدة، يدعم Aspose.Words أيضًا مخططات الدونات ذات السلاسل المتعددة. غيّر `ChartType.PIE` إلى `ChartType.DONUT` وكرر خطوات تكوين السلسلة.

### التصدير إلى PDF

إذا كان سير العمل اللاحق يتطلب PDF، استدعِ `doc.save("output/PieFormatted.pdf");` بعد بناء المخطط. يبقى التخطيط البصري متطابقًا.

## قائمة المصدر الكاملة

فيما يلي ملف Java كامل ومستقل يمكنك نسخه‑ولصقه في بيئة التطوير المتكاملة الخاصة بك.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300‑point pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Access the single series in the pie chart
        ChartSeries series = chart.getSeries().get(0);

        // Explode the first slice for emphasis
        series.setExploded(true);

        // Show percentages on each slice
        series.setShowPercentage(true);

        // Add leader lines for clear label connections
        series.setShowLeaderLines(true);

        // Save the document
        doc.save("output/PieFormatted.docx");
    }
}
```

قم بتجميع وتشغيل البرنامج باستخدام `mvn compile exec:java -Dexec.mainClass=PieChartExample` (أو الأمر المكافئ في Gradle). سيحتوي ملف Word المُولد على المخطط الدائري المنسق بالكامل.

## الخلاصة

أنت الآن تعرف **how to insert pie chart** في مستند Word باستخدام Java، وكيفية **create pie chart in Word**، وكيفية **show percentages on pie chart**، وكيفية **add chart to word document** مع خطوط الربط. يوضح المثال الكامل كل خطوة، ويشرح سبب كتابة الكود بهذه الطريقة، ويقدم نصائح للتخصيص.

بعد ذلك، قد تستكشف:

- إضافة تسميات البيانات بخطوط مخصصة (تغييرات **show percentages on pie chart**)
- دمج مخططات متعددة في مستند واحد (حالة استخدام **add chart to word document**)
- أتمتة إنشاء التقارير مع الجداول والمخططات معًا

لا تتردد في تجربة الألوان، ترتيب الشرائح، أو التصدير إلى PDF. برمجة سعيدة!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء مخطط عمودي باستخدام Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [إخفاء محور المخطط في مستند Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [إنشاء مخطط خطي في Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}