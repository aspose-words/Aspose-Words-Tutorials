---
category: general
date: 2026-09-27
description: إنشاء مخطط قطري في جافا وإدراجه في مستند وورد. تعلم كيفية ضبط حجم المخطط،
  إضافة سلسلة بيانات، وإنشاء مستند وورد فارغ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- insert chart into word
- create blank word document
- how to set chart size
- add data series chart
language: ar
lastmod: 2026-09-27
og_description: إنشاء مخطط شعاعي في جافا، ثم إدراج المخطط في وورد. يوضح هذا الدليل
  كيفية ضبط حجم المخطط، إضافة سلسلة بيانات، وإنشاء مستند وورد فارغ.
og_image_alt: Screenshot showing a radial chart inserted into a Word document created
  with Java
og_title: إنشاء مخطط شعاعي وإدراج المخطط في Word باستخدام Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create radial chart in Java and insert chart into Word. Learn how to
    set chart size, add data series, and generate a blank Word document.
  headline: Create radial chart and insert chart into Word with Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart generation
title: إنشاء مخطط شعاعي وإدراج المخطط في Word باستخدام Java
url: /ar/java/word-processing/create-radial-chart-and-insert-chart-into-word-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مخطط قطري وإدراج المخطط في Word باستخدام Java

إذا كنت بحاجة إلى **إنشاء مخطط قطري** في ملف Word باستخدام Java، فإن هذا الدليل يوضح لك بالضبط كيفية ذلك. ستتعرف على كيفية **إدراج المخطط في Word**، وضبط أبعاد المخطط، وإنشاء **مستند Word فارغ** من الصفر.

سنستعرض كل خطوة مطلوبة، بدءًا من تهيئة المستند إلى إضافة سلسلة بيانات وحفظ ملف `.docx` النهائي. في النهاية ستحصل على ملف Word يعمل بالكامل يحتوي على مخطط قطري، وستفهم **كيفية ضبط حجم المخطط** و**إضافة سلسلة بيانات إلى المخطط** للتخصيصات المستقبلية.

## المتطلبات المسبقة

* Java 17 أو أحدث (الكود يُترجم مع أي JDK حديث)
* Aspose.Words for Java 24.9 أو أحدث – طريقة `setShowGraduations` متاحة فقط من هذا الإصدار
* بيئة تطوير متكاملة أو أداة بناء (Maven/Gradle) يمكنها تضمين ملف JAR الخاص بـ Aspose.Words
* إلمام أساسي بصياغة Java وإدارة الاعتمادات في Maven/Gradle

> **نصيحة احترافية:** إذا كنت تستخدم Maven، أضف ما يلي إلى ملف `pom.xml` الخاص بك:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## الخطوة 1: إنشاء مستند Word فارغ

المستند الفارغ هو القماش الذي سيُوضع عليه المخطط. تمثل فئة `Document` الملف `.docx` بالكامل.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank Word document
```

إنشاء مستند فارغ يضمن عدم تداخل أي محتوى موجود مسبقًا مع تخطيط المخطط.

## الخطوة 2: تهيئة DocumentBuilder

`DocumentBuilder` يوفر طرقًا مريحة لإدراج الكائنات والنصوص والعناصر الأخرى في المستند.

```java
        // Step 2: Initialise a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

سيتم لاحقًا استخدام الـ builder لـ **إدراج المخطط في Word**.

## الخطوة 3: بناء المخطط القطري

يدعم Aspose.Words العديد من أنواع المخططات؛ `ChartType.RADIAL` ينشئ مخططًا قطريًا (قطبيًا).

```java
        // Step 3: Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);
```

في هذه المرحلة يوجد المخطط لكنه لا يحتوي على بيانات أو حجم أو خيارات بصرية.

## الخطوة 4: إضافة سلسلة بيانات إلى المخطط

المخطط بدون سلسلة بيانات يكون فارغًا. طريقة `add` تأخذ اسم السلسلة ومصفوفة من القيم.

```java
        // Step 4: Add a data series to the chart
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});
```

يمكنك إضافة سلاسل متعددة عن طريق استدعاء `add` بشكل متكرر. هذا يلبي متطلب **إضافة سلسلة بيانات إلى المخطط**.

## الخطوة 5: تمكين التدرجات (اختياري)

التدرجات هي خطوط الشبكة القطرية التي تحسن قابلية القراءة. وهي متاحة فقط بدءًا من الإصدار 24.9.

```java
        // Step 5: Enable graduations on the chart (available from version 24.9)
        chart.getChartObject().setShowGraduations(true);
```

إذا كنت تستخدم نسخة أقدم من Aspose.Words، سيتسبب هذا السطر في رمي استثناء—لذا تحقق من نسخة المكتبة أولًا.

## الخطوة 6: ضبط أبعاد المخطط

التحكم في حجم المخطط يتيح لك ملاءمته بشكل جيد داخل هوامش الصفحة. هذا يجيب على **كيفية ضبط حجم المخطط**.

```java
        // Step 6: Define the chart's dimensions
        chart.setWidth(400);   // width in points (≈5.5 inches)
        chart.setHeight(300);  // height in points (≈4.2 inches)
```

يمكنك تعديل قيم العرض والارتفاع لتتناسب مع احتياجات تخطيطك. تذكر أن 1 نقطة ≈ 1/72 بوصة.

## الخطوة 7: إدراج المخطط في مستند Word

الآن المخطط جاهز للموضع. طريقة `insertChart` في `DocumentBuilder` تتعامل مع الإدراج.

```java
        // Step 7: Insert the chart into the document
        builder.insertChart(chart);
```

هذا هو جوهر عملية **إدراج المخطط في Word**.

## الخطوة 8: حفظ المستند

أخيرًا، احفظ المستند على القرص. سيحتوي الملف على المخطط القطري الذي أنشأته للتو.

```java
        // Step 8: Save the document with the chart
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

تشغيل البرنامج ينتج ملف `RadialChart.docx` في دليل العمل الخاص بالمشروع. فتح الملف في Microsoft Word يعرض مخططًا قطريًا بثلاث نقاط بيانات وتدرجات مرئية.

### النتيجة المتوقعة

* ملف Word باسم `RadialChart.docx`
* داخل الملف، صفحة واحدة تحتوي على مخطط قطري بحجم 400 × 300 نقطة
* يعرض المخطط سلسلة واحدة بعنوان **Series 1** بالقيم **10, 20, 30**
* التدرجات (خطوط الشبكة القطرية) مرئية حول المخطط

## الاختلافات الشائعة وحالات الحافة

| الحالة | ما الذي يجب تغييره | السبب |
|-----------|----------------|--------|
| **سلاسل متعددة** | استدعِ `chart.getSeries().add(...)` لكل سلسلة | يتيح تصورًا مقارنًا للبيانات |
| **نوع مخطط مختلف** | استبدل `ChartType.RADIAL` بـ `ChartType.COLUMN` (أو أي نوع آخر) | استخدم نوع المخطط الذي يمثل بياناتك بأفضل شكل |
| **ألوان مخصصة** | الوصول إلى `chart.getSeries().get(i).getFormat().getFill().setForeColor(Color)` | يحسن العلامة البصرية |
| **إصدار Aspose.Words أقدم** | احذف سطر `setShowGraduations` أو قم بترقية المكتبة | يمنع حدوث `NoSuchMethodError` |
| **الحفظ بصيغة مختلفة** | استخدم `doc.save("RadialChart.pdf", SaveFormat.PDF)` | يولد ملف PDF بدلاً من DOCX |

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل المستقل بلغة Java. انسخه إلى ملف باسم `RadialChartExample.java`، أضف اعتماد Aspose.Words، وشغّله.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank Word document
        Document doc = new Document();

        // 2. Initialise a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);

        // 4. Add a data series (add data series chart)
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});

        // 5. Enable graduations (requires Aspose.Words 24.9+)
        chart.getChartObject().setShowGraduations(true);

        // 6. Set chart size (how to set chart size)
        chart.setWidth(400);
        chart.setHeight(300);

        // 7. Insert the chart into the document (insert chart into word)
        builder.insertChart(chart);

        // 8. Save the document (create blank word document with chart)
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

## الخلاصة

أنت الآن تعرف كيفية **إنشاء مخطط قطري** برمجيًا، **إضافة سلسلة بيانات إلى المخطط**، التحكم في **كيفية ضبط حجم المخطط**، و**إدراج المخطط في Word** بدءًا من **مستند Word فارغ**. يستخدم المثال Aspose.Words for Java 24.9، لكن نفس المفاهيم تنطبق على مكتبات مخططات أخرى توفر واجهة برمجة تطبيقات مشابهة.

### الخطوات التالية

* استكشف أنواع مخططات أخرى (`ChartType.PIE`, `ChartType.LINE`, إلخ) – هذا يرتبط بالكلمة المفتاحية الثانوية **إدراج المخطط في Word**.
* خصص تسميات المحاور، الأساطير، والألوان لتتناسب مع إرشادات علامتك التجارية.
* أنشئ مخططات بشكل ديناميكي من استعلامات قاعدة البيانات أو ملفات CSV.
* حوّل ملف `.docx` الناتج إلى PDF للتوزيع (`doc.save("output.pdf", SaveFormat.PDF)`).

لا تتردد في تجربة الأبعاد، بيانات السلسلة، وخيارات التنسيق لإنشاء الشكل البصري الدقيق الذي تحتاجه. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شاملة من الشيفرة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء مخطط عمودي باستخدام Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [إنشاء مستند Word بـ Java – إضافة شكل مستطيل مع تأثير الظل](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [إدراج مخطط منطقة في مستند Word](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}