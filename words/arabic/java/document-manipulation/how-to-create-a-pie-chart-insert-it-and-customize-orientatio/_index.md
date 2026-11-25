---
category: general
date: 2026-11-25
description: تعلم كيفية إنشاء مخطط دائري في جافا، وإدراج المخطط الدائري في مستند Word،
  وتفجير شريحة من المخطط وتغيير اتجاه المخطط مع أمثلة شفرة واضحة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- change chart orientation
- explode pie slice
- insert pie chart
- rotate pie chart
language: ar
lastmod: 2026-11-25
og_description: إنشاء مخطط دائري في جافا، إدراج المخطط الدائري في مستند، تفجير شريحة
  من المخطط وتغيير اتجاه المخطط باستخدام كود خطوة بخطوة.
og_image_alt: Screenshot of a created pie chart with an exploded slice and rotated
  orientation
og_title: إنشاء مخطط دائري في جافا – إدراج، تفجير الشريحة، وتدوير
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a pie chart in Java, insert pie chart into a Word
    document, explode pie slice and change chart orientation with clear code examples.
  headline: How to create a pie chart, insert it, and customize orientation in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Charting
title: كيفية إنشاء مخطط دائري، إدراجه، وتخصيص الاتجاه في جافا
url: /ar/java/document-manipulation/how-to-create-a-pie-chart-insert-it-and-customize-orientatio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مخطط دائري، إدراجه، وتخصيص الاتجاه في Java

إذا كنت بحاجة إلى **إنشاء مخطط دائري** داخل مستند Word، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك. ستتعرف على كيفية **إدراج مخطط دائري**، تفجير شريحة لتسليط الضوء، و**تغيير اتجاه المخطط** باستخدام تدوير بسيط.

يغطي الدرس كل ما تحتاجه—من إعداد مكتبة Aspose.Words for Java إلى إنتاج ملف `.docx` نهائي يعرض مخططًا دائريًا مدورًا ومتفجرًا. لا تحتاج إلى أي وثائق خارجية؛ فقط اتبع الخطوات وشغّل الكود.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من أن لديك:

* Java 17 أو أحدث مثبتة.
* Maven أو Gradle لإدارة التبعيات.
* ترخيص صالح لـ Aspose.Words for Java (أو استخدم وضع التقييم المجاني).

أضف تبعية Aspose.Words إلى ملف `pom.xml` (Maven) أو `build.gradle` (Gradle). مثال لـ Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

> **نصيحة احترافية:** حافظ على تحديث نسخة المكتبة؛ الإصدار الأخير (24.10 في وقت كتابة هذا الدليل) يتضمن إصلاحات للأخطاء المتعلقة برسم المخططات.

## الخطوة 1: إنشاء مخطط دائري وإدراجه في المستند

الخطوة الأولى هي **إنشاء مخطط دائري** وتضمينه في ملف Word. يبني الكود أدناه مستندًا بسيطًا، يضيف عنصرًا نائبيًا للمخطط، ويُدرج مخططًا دائريًا بحجم 400 × 300 بيكسل.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new Document and DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a pie chart of size 400x300
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Populate the chart with sample data
        chart.getSeries().clear(); // remove default series
        ChartSeries series = chart.getSeries().add("Sales", new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Save the document so far (optional)
        doc.save("Step1_InsertPieChart.docx");
    }
}
```

**لماذا هذا مهم:** `builder.insertChart` ينشئ عنصرًا نائبيًا للمخطط تقوم Aspose.Words بتحويله تلقائيًا إلى مخطط OOXML عند حفظ المستند. تُخبر الوسيطة `ChartType.PIE` المكتبة برسم مخطط دائري، مما يلبي متطلبات **إدراج مخطط دائري**.

## الخطوة 2: تفجير شريحة المخطط لتسليط الضوء على جزء

تفجير شريحة يجذب الانتباه إلى نقطة بيانات معينة. السطر التالي يفجر الشريحة الأولى (الفهرس 0) بمقدار 10 نقاط:

```java
// 4️⃣ Explode the first slice (index 0) by 10 points
chart.getSeries().get(0).setExplode(0, 10);
```

يمكنك تغيير الفهرس لاستهداف شريحة مختلفة، أو تعديل مسافة التفجير لتأثير أكثر رقة. تفجير الشريحة هو الطريقة القياسية لـ **تفجير شريحة مخطط دائري** في Aspose.Words.

## الخطوة 3: تغيير اتجاه المخطط عن طريق تدويره

تدوير المخطط يمنح منظورًا بصريًا جديدًا. استخدم `setRotationAngle` لتدوير المخطط بالكامل باتجاه عقارب الساعة (الزاوية تُقاس بالدرجات).

```java
// 5️⃣ Rotate the entire chart by 45 degrees
chart.setRotationAngle(45);
```

النداء أعلاه يحقق متطلبات **تدوير المخطط الدائري** و**تغيير اتجاه المخطط**. أي زاوية بين 0 و 360 درجة مقبولة.

## مثال كامل قابل للتنفيذ

بدمج كل ما سبق، إليك برنامج كامل ومستقل يُنشئ مخططًا دائريًا، يفجر شريحة، ويُدوّر المخطط. شغّله من بيئة التطوير المتكاملة أو من سطر الأوامر باستخدام `java -cp <classpath> PieChartDemo`.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300 pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Prepare data series (Sales per quarter)
        chart.getSeries().clear(); // remove default placeholder
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Explode the first slice (Q1) by 10 points
        chart.getSeries().get(0).setExplode(0, 10);

        // Rotate the chart 45 degrees clockwise
        chart.setRotationAngle(45);

        // Save the final document
        doc.save("CreatePieChartDemo.docx");
        System.out.println("Document created successfully: CreatePieChartDemo.docx");
    }
}
```

### النتيجة المتوقعة

* يظهر ملف باسم **CreatePieChartDemo.docx** في دليل العمل.
* عند فتح الملف في Microsoft Word يُظهر مخططًا دائريًا بحجم 400 × 300 بيكسل.
* الشريحة الأولى (Q1) مُزاحة إلى الخارج بمقدار 10 نقاط، مُنتجة تأثير **تفجير شريحة مخطط دائري**.
* يُميل المخطط بالكامل بزاوية 45 درجة، مُظهرًا **تغيير اتجاه المخطط** و**تدوير المخطط الدائري**.

## الاختلافات الشائعة والحالات الخاصة

| الحالة | كيفية تعديل الكود |
|-----------|-----------------------|
| **حجم مخطط مختلف** | غيّر الوسيطين `400, 300` في `insertChart`. |
| **سلاسل متعددة** | أضف المزيد من كائنات `ChartSeries` إلى `chart.getSeries()`. |
| **تفجير شريحة مختلفة** | استخدم `setExplode(sliceIndex, distance)` مع `sliceIndex` المطلوب. |
| **لا حاجة للتدوير** | احذف نداء `setRotationAngle` أو اضبط الزاوية على `0`. |
| **تصدير إلى PDF بدلًا من DOCX** | بعد بناء المستند، استدعِ `doc.save("output.pdf")` مع صيغة PDF. |

> **احذر من:** استخدام مسافة تفجير سلبية يسبب استثناء `IllegalArgumentException`. يجب دائمًا توفير قيمة غير سلبية.

## نصيحة للأداء

إذا كنت تُنشئ العديد من المخططات داخل حلقة، أعد استخدام كائن `DocumentBuilder` واحد واستدعِ `insertChart` فقط لكل تكرار. هذا يقلل من استهلاك الذاكرة ويسرّع المعالجة.

## الخلاصة

أنت الآن تعرف كيف **تنشئ مخططًا دائريًا**، **تدرجه في المستند**، **تفجر شريحة مخطط**، و**تدوّر المخطط** باستخدام Aspose.Words for Java. يُظهر المثال الكامل سير العمل الكامل—من تهيئة المستند إلى حفظ ملف يُظهر مخططًا دائريًا مدورًا ومتفجرًا.

بعد ذلك، يمكنك استكشاف **تغيير اتجاه المخطط** أكثر عبر تطبيق تأثيرات ثلاثية الأبعاد، أو تجربة أنواع مخططات أخرى مثل **Bar** أو **Line**. أنماط API نفسها تُطبق، لذا توسيع هذا الدرس سهل.

لا تتردد في تعديل البيانات، فهرس الشريحة، أو زاوية التدوير لتتناسب مع احتياجات تقاريرك، وشارك نتائجك مع المجتمع!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تُبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [How to insert a pie chart into a Word document using Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}