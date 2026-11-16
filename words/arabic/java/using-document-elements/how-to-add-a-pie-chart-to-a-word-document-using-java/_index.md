---
category: general
date: 2026-11-15
description: تعلم كيفية إضافة مخطط دائري إلى مستند Word باستخدام Aspose.Words للغة
  Java. يتضمن تحويل إلى مخطط حلقي، شريحة منفصلة، وعينة كاملة من الشيفرة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart to word document
- Aspose.Words chart example
- Java pie chart tutorial
- create doughnut chart in Word
- explode pie slice Java
language: ar
lastmod: 2026-11-15
og_description: أضف مخططًا دائريًا إلى مستند Word باستخدام Aspose.Words for Java.
  يوضح هذا الدرس كيفية إبراز شريحة وتحويل المخطط إلى شكل دونات.
og_image_alt: Screenshot of a Word document containing an exploded pie chart transformed
  into a doughnut
og_title: إضافة مخطط دائري إلى مستند Word باستخدام Java – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  headline: How to add a pie chart to a Word document using Java
  type: TechArticle
- description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  name: How to add a pie chart to a Word document using Java
  steps:
  - name: Expected output
    text: 'Open `final-pie-doughnut.docx` in Microsoft Word:'
  - name: Adding multiple series
    text: 'If you need several series (e.g., stacked doughnut), add them sequentially:'
  - name: Custom colors
    text: 'You can assign a color to each slice via `ChartDataPoint.setFillFormat().setSolidFillColor()`:'
  - name: Working with an existing chart
    text: 'If the document already contains a chart and you only want to modify it,
      locate the chart shape:'
  - name: License handling
    text: 'Aspose.Words requires a license for production use. Place your `Aspose.Words.lic`
      file in the classpath and load it at application start:'
  - name: What to explore next
    text: '* **add bar chart to Word document** – similar steps but use `ChartType.BAR`.
      * **customize chart legends and titles** – use `pieChart.getTitle().setText("...")`
      and `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`. * **export the
      Word document as PDF** – change the `SaveFormat` to `PDF` for'
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: كيفية إضافة مخطط دائري إلى مستند Word باستخدام Java
url: /ar/java/using-document-elements/how-to-add-a-pie-chart-to-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة مخطط دائري إلى مستند Word – دليل Java كامل

إذا كنت بحاجة إلى **إضافة مخطط دائري إلى مستند Word** برمجياً، يوضح لك هذا الدرس خطوة بخطوة كيفية القيام بذلك باستخدام Aspose.Words for Java. ستشاهد سير العمل الكامل: تحميل ملف DOCX، إنشاء مخطط دائري، تفجير الشريحة الأولى، وتحويل المخطط إلى مخطط حلقة عن طريق ضبط حجم الفتحة.

الدليل يغطي أيضاً التغييرات الشائعة—مثل إضافة سلاسل متعددة، تخصيص الألوان، ومعالجة المستندات التي تحتوي بالفعل على مخططات—حتى تتمكن من تعديل الكود لمشاريع العالم الحقيقي مثل التقارير الآلية أو العروض التقديمية الديناميكية.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* Java 17 أو أحدث (الكود يُجمّع أيضاً مع JDK 11+)
* Maven 3.6+ أو Gradle لإدارة التبعيات
* رخصة Aspose.Words for Java (الإصدار التجريبي المجاني يكفي للاختبار)
* فهم أساسي لصياغة Java وبنية مشروع Maven

## الخطوة 1: إعداد مشروع Maven واستيراد Aspose.Words

أنشئ مشروع Maven جديد (أو أضف إلى مشروع موجود) وضمّن تبعية Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-chart-demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest stable at time of writing -->
        </dependency>
    </dependencies>
</project>
```

> **نصيحة محترف:** إذا كنت تستخدم Gradle، فإن الإدخال المكافئ هو `implementation 'com.aspose:aspose-words:24.9'`.

التبعية تجلب الفئات `Document`، `Chart`، و `ChartType` التي ستحتاجها لمعالجة المخططات.

## الخطوة 2: تحميل المستند الهدف

يمكنك البدء من ملف `.docx` موجود أو إنشاء مستند فارغ جديد. المثال أدناه يحمل قالبًا يُدعى `input.docx` موجودًا في مجلد `src/main/resources`.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load the Word document that will receive the chart
        Document doc = new Document("src/main/resources/input.docx");
        // Continue with chart creation...
    }
}
```

إذا لم يكن الملف موجودًا، سيقوم Aspose.Words بإنشاء مستند فارغ جديد تلقائيًا عند استدعاء `new Document()` دون اسم ملف.

## الخطوة 3: إنشاء مخطط دائري وإدراجه في المستند

يتعامل Aspose.Words مع المخطط ككائن شكل يمكن وضعه في أي مكان يمكن أن يظهر فيه فقرة. الكود التالي ينشئ **مخططًا دائريًا**، يضيف سلسلة بيانات واحدة، ويُدرج المخطط بعد الفقرة الأولى.

```java
import com.aspose.words.*;
import java.util.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("src/main/resources/input.docx");

        // Create a new chart of type PIE
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // Prepare data for the series: categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // Add a new series to the chart
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // Insert the chart into the document after the first paragraph
        Paragraph firstParagraph = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);
        firstParagraph.appendChild(pieChart);
        
        // Save the document to verify the result
        doc.save("output/add-pie-chart.docx", SaveFormat.DOCX);
    }
}
```

**لماذا هذه الخطوة مهمة:**  
* `ChartType.PIE` يُخبر Aspose.Words برسم مخطط دائري تقليدي.  
* إضافة سلسلة تحتوي على تسميات الفئات والقيم الرقمية يملأ الشرائح تلقائيًا.  
* إدراج المخطط كطفل لـ `Paragraph` يحافظ على تدفق المستند دون انقطاع.

## الخطوة 4: تفجير الشريحة الأولى لتسليط الضوء عليها

*الشريحة المتفجرة* تجذب الانتباه إلى نقطة بيانات معينة. تُوفر API الطريقة `setExplode(boolean)` على كائن `ChartSeries`. ضبطها على السلسلة الأولى (الفهرس 0) يجعل الشريحة الأولى تبرز.

```java
// Explode the first slice (index 0) of the first series
pieChart.getSeries().get(0).setExplode(true);
```

> **سؤال شائع:** *ماذا لو كان لدي عدة سلاسل؟*  
> يمكنك استهداف سلسلة معينة بواسطة فهرسها، مثلاً `pieChart.getSeries().get(1).setExplode(true)` للسلسلة الثانية.

## الخطوة 5: تحويل المخطط الدائري إلى مخطط حلقة بضبط حجم الفتحة

المخطط الحلقي هو في الأساس مخطط دائري مع مركز مجوف. يتيح لك Aspose.Words تعريف حجم الفتحة كنسبة مئوية من نصف قطر المخطط.

```java
// Turn the pie chart into a doughnut with a 30% hole size
pieChart.setHoleSize(30);
```

طريقة `setHoleSize` تقبل قيمًا من **0** (دائري عادي) إلى **100** (فارغ تمامًا). قيمة تقريبًا **30‑40** تُنتج حلقة متوازنة بصريًا.

## الخطوة 6: حفظ النتيجة والتحقق منها

بعد جميع التعديلات، احفظ المستند. السطر التالي يكتب الملف إلى مجلد `output`.

```java
doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);
```

### النتيجة المتوقعة

افتح `final-pie-doughnut.docx` في Microsoft Word:

* يظهر مخطط حلقة في المكان الذي كانت فيه الفقرة الأولى.
* شريحة “Apples” متفجرة (مفصولة قليلًا عن البقية).
* المخطط يعرض أربع شرائح مسماة *Apples*، *Bananas*، *Cherries*، *Dates* مع النسب المئوية التي زودتها.

إذا كنت تفضّل إخراج PDF، غيّر `SaveFormat` إلى `SaveFormat.PDF`.

## معالجة الحالات الخاصة والتنوعات

### إضافة سلاسل متعددة

إذا كنت بحاجة إلى عدة سلاسل (مثلاً مخطط حلقة مكدس)، أضفها بالتتابع:

```java
double[] values2022 = {20, 30, 25, 25};
double[] values2023 = {25, 20, 30, 25};

ChartSeries s2022 = pieChart.getSeries().add("2022", categories, values2022);
ChartSeries s2023 = pieChart.getSeries().add("2023", categories, values2023);
```

### ألوان مخصصة

يمكنك تعيين لون لكل شريحة عبر `ChartDataPoint.setFillFormat().setSolidFillColor()`:

```java
ChartDataPoint point = series.getDataPoints().get(0); // first slice
point.getFillFormat().setSolidFillColor(java.awt.Color.RED);
```

### العمل مع مخطط موجود مسبقًا

إذا كان المستند يحتوي بالفعل على مخطط وتريد فقط تعديلّه، حدد شكل المخطط:

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node shapeNode : (Iterable<Node>) shapes) {
    Shape shape = (Shape) shapeNode;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart existingChart = shape.getChart();
        // Apply explode/holeSize changes here
    }
}
```

### معالجة الترخيص

يتطلب Aspose.Words ترخيصًا للاستخدام في الإنتاج. ضع ملف `Aspose.Words.lic` في مسار الـ classpath وحمّله عند بدء التطبيق:

```java
License license = new License();
license.setLicense("Aspose.Words.lic");
```

عدم ضبط الترخيص سيضيف علامة مائية إلى المستند المُنشأ.

## مثال كامل قابل للتنفيذ

فيما يلي الفئة Java الكاملة التي تضم جميع الخطوات التي نوقشت. انسخها إلى `src/main/java/com/example/AddPieChart.java` وشغّل `mvn compile exec:java`.

```java
package com.example;

import com.aspose.words.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load license (optional for trial)
        // new License().setLicense("Aspose.Words.lic");

        // 1️⃣ Load the base document
        Document doc = new Document("src/main/resources/input.docx");

        // 2️⃣ Create a pie chart
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // 3️⃣ Define categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // 4️⃣ Add a series with the data
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // 5️⃣ Explode the first slice
        pieChart.getSeries().get(0).setExplode(true);

        // 6️⃣ Convert to doughnut (30% hole)
        pieChart.setHoleSize(30);

        // 7️⃣ Insert the chart after the first paragraph
        Paragraph firstPara = (Paragraph) doc.getFirstSection()
                .getBody()
                .getChild(NodeType.PARAGRAPH, 0, true);
        firstPara.appendChild(pieChart);

        // 8️⃣ Save the final document
        doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);

        System.out.println("Chart added successfully. Check output/final-pie-doughnut.docx");
    }
}
```

تشغيل البرنامج ينتج مخطط الحلقة الموضح أعلاه. عدّل `categories`، `values`، أو `holeSize` لتتناسب مع بياناتك.

## الخلاصة

أصبحت الآن تعرف كيف **تضيف مخططًا دائريًا إلى مستند Word** باستخدام Java وAspose.Words. غطّى الدرس تحميل المستند، إنشاء مخطط دائري، تفجير شريحة، تحويل المخطط إلى حلقة، ومعالجة التنوعات الشائعة مثل السلاسل المتعددة، الألوان المخصصة، والمخططات الموجودة. باستخدام هذه الأساسيات يمكنك بناء أدوات تقارير آلية، توليد عروض تقديمية ديناميكية، أو دمج تصورات بصرية غنية مباشرةً في ملفات Word.

### ما الذي يمكنك استكشافه لاحقًا

* **إضافة مخطط شريطي إلى مستند Word** – خطوات مشابهة لكن باستخدام `ChartType.BAR`.  
* **تخصيص وسائط المخطط والعناوين** – استخدم `pieChart.getTitle().setText("...")` و `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`.  
* **تصدير مستند Word كملف PDF** – غيّر `SaveFormat` إلى `PDF` للحصول على ملفات جاهزة للتوزيع.  
* **ملء بيانات المخطط من قاعدة بيانات** – استبدل المصفوفات الثابتة بنتائج استعلام JDBC.

لا تتردد في تجربة أنواع مخططات مختلفة، مصادر بيانات متنوعة، وخيارات تنسيق متعددة. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide](/words/english/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}