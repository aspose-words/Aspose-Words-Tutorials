---
category: general
date: 2026-07-20
description: إدراج مخطط دائري في جافا مع دليل خطوة بخطوة. تعلّم كيفية تفجير الشريحة،
  وكيفية تدوير المخطط الدائري، وتحديد الشريحة المميزة وتخصيص شريحة المخطط الدائري.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to explode slice
- how to rotate pie chart
- highlight pie chart slice
- customize pie chart slice
language: ar
lastmod: 2026-07-20
og_description: أدرج مخططًا دائريًا في جافا وتعلم كيفية تفجير الشريحة، وتدوير المخطط
  الدائري، وتحديد الشريحة المميزة، وتخصيص شريحة المخطط الدائري لتقارير بصرية مصقولة.
og_image_alt: Screenshot showing an inserted pie chart with an exploded and rotated
  slice
og_title: إدراج مخطط دائري في جافا – تفجير، تدوير وتحديد
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Insert pie chart in Java with a step‑by‑step guide. Learn how to explode
    slice, how to rotate pie chart, highlight pie chart slice and customize pie chart
    slice.
  headline: Insert Pie Chart in Java – Explode, Rotate & Highlight Slices
  type: TechArticle
tags:
- Java
- charting
- visualization
title: إدراج مخطط دائري في جافا – تفجير، تدوير وتحديد القطاعات
url: /ar/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إدراج مخطط دائري في Java – تفجير، تدوير وتظليل الشرائح

هل احتجت يوماً إلى **إدراج مخطط دائري** في تقرير Java لكنك لم تكن متأكدًا من كيفية جعل شريحة واحدة تبرز؟ لست وحدك. سواءً كنت تبني لوحة معلومات، أو تُنشئ فاتورة، أو فقط تُصوّر نتائج استبيان، يمكن لمخطط دائري مُصمم جيدًا أن يحوّل الأرقام الخام إلى رؤى مفهومة فورًا.

في هذا الدرس ستشاهد مثالًا كاملًا جاهزًا للتنفيذ يُظهر لك كيفية **إدراج مخطط دائري**، **كيفية تفجير الشريحة**، **كيفية تدوير المخطط الدائري**، وحتى **تظليل شريحة المخطط الدائري** بألوان مخصصة. في النهاية ستحصل على قطعة شفرة قابلة لإعادة الاستخدام يمكنك إدراجها في أي مشروع Java يستخدم مكتبة *JFreeChart* الشهيرة (أو أي API مشابه).

## المتطلبات المسبقة

- Java 17 أو أحدث (الكود يُترجم مع إصدارات أقدم، لكننا سنستخدم صيغة `var` الحديثة للاختصار).  
- Maven أو Gradle لجلب الاعتماد `org.jfree:jfreechart`.  
- فهم أساسي لفئات Java ومفهوم مُنشئ المخططات.  

إذا لم تقم أبدًا بإضافة مكتبة إلى مشروع Maven، فقط ضع هذا في ملف `pom.xml` الخاص بك:

```xml
<dependency>
    <groupId>org.jfree</groupId>
    <artifactId>jfreechart</artifactId>
    <version>1.5.4</version>
</dependency>
```

هذا كل شيء—لا إعداد إضافي مطلوب.

## الخطوة 1: إدراج مخطط دائري – إنشاء المُنشئ وكائن المخطط

أولاً وقبل كل شيء: نحتاج إلى *مُنشئ* (فكر فيه كمصنع) يعرف كيف ينتج المخططات. في JFreeChart يقوم `ChartFactory` بهذه المهمة.

```java
import org.jfree.chart.ChartFactory;
import org.jfree.chart.JFreeChart;
import org.jfree.data.general.DefaultPieDataset;

public class PieChartDemo {

    public static JFreeChart createPieChart() {
        // Prepare the data set
        var dataset = new DefaultPieDataset();
        dataset.setValue("Apples", 40);
        dataset.setValue("Bananas", 30);
        dataset.setValue("Cherries", 20);
        dataset.setValue("Dates", 10);

        // Insert pie chart with a width of 400 and height of 300
        JFreeChart chart = ChartFactory.createPieChart(
                "Fruit Distribution", // chart title
                dataset,              // data
                true,                 // include legend
                true,                 // tooltips
                false                 // URLs
        );
        return chart;
    }
}
```

لماذا نبدأ بمجموعة البيانات؟ لأن المخطط نفسه هو مجرد غلاف بصري للأرقام. عبر **إدراج مخطط دائري** هنا نحصل بالفعل على لوحة قماش بحجم 400 × 300 (سيتم تطبيق الحجم لاحقًا عند تصديره إلى صورة).

## الخطوة 2: كيفية تفجير الشريحة – إبراز الجزء الأول

الآن بعد أن أصبح المخطط موجودًا، دعنا نجعل الشريحة الأولى تبرز. تفجير الشريحة يبعدها قليلًا عن الدائرة، مما يجذب انتباه القارئ.

```java
import org.jfree.chart.plot.PiePlot;
import org.jfree.chart.plot.PiePlotState;

public static void explodeFirstSlice(JFreeChart chart) {
    // Grab the plot from the chart – this is where we tweak appearance
    PiePlot plot = (PiePlot) chart.getPlot();

    // Explode the first slice (index 0) to highlight it
    // The key "Apples" corresponds to the first entry we added
    plot.setExplodePercent("Apples", 0.15); // 15% outward
}
```

لاحظ أننا استخدمنا عبارة **كيفية تفجير الشريحة** في اسم الطريقة؛ هذا يجعل النية واضحة تمامًا. طريقة `setExplodePercent` تأخذ مفتاحًا (اسم الشريحة) ونسبة مئوية، بحيث يمكنك تعديل مسافة "الانفجار" حسب الحاجة.

## الخطوة 3: كيفية تدوير المخطط الدائري – تغيير زاوية البدء

المخطط الدائري الافتراضي يبدأ من موضع الساعة 12. أحيانًا تريد أن تبدأ الشريحة الأولى من موضع آخر—ربما لتتناسب مع تصميم مبدئي أو لتطابق مخطط آخر.

```java
public static void rotateChart(JFreeChart chart, double startAngle) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Rotate the chart so the first slice starts at the given angle (degrees)
    plot.setStartAngle(startAngle);
}
```

استدعاء `rotateChart(chart, 45)` يدور المخطط بأكمله بحيث تبدأ شريحة “Apples” بزاوية 45 درجة، وهو بالضبط ما يطلبه **كيفية تدوير المخطط الدائري**.

## الخطوة 4: تظليل شريحة المخطط الدائري – ألوان وعناوين مخصصة

إلى جانب التفجير، قد ترغب في إعطاء شريحة لونًا فريدًا أو عنوانًا بارزًا لتُـ **تظليل شريحة المخطط الدائري** فعليًا.

```java
import java.awt.Color;
import org.jfree.chart.labels.StandardPieSectionLabelGenerator;

public static void customizeSlice(JFreeChart chart) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Set a vivid color for the "Apples" slice
    plot.setSectionPaint("Apples", new Color(0xFF5722)); // deep orange

    // Make the label display both key and value in bold
    plot.setLabelGenerator(new StandardPieSectionLabelGenerator(
            "{0}: {1} ({2})")); // key: value (percent)
    plot.setLabelFont(plot.getLabelFont().deriveFont(java.awt.Font.BOLD));
}
```

هنا قمنا **بتخصيص شريحة المخطط الدائري** بتغيير لونها ونمط العنوان. لا تتردد في استبدال اللون أو الخط ليتماشى مع لوحة ألوان علامتك التجارية.

## الخطوة 5: تصدير المخطط إلى صورة (اختياري لكن مفيد)

معظم التطبيقات الواقعية تحتاج المخطط كملف PNG أو JPEG أو حتى PDF. أدناه طريقة سريعة لكتابة المخطط إلى ملف.

```java
import java.io.File;
import org.jfree.chart.ChartUtils;

public static void saveChart(JFreeChart chart, String filename) throws Exception {
    int width = 400;
    int height = 300;
    File outFile = new File(filename);
    ChartUtils.saveChartAsPNG(outFile, chart, width, height);
}
```

تشغيل التدفق الكامل سينتج صورة PNG بحجم 400 × 300 تشبه ما يلي:

![Insert pie chart example](image.png){: alt="مثال على إدراج مخطط دائري يظهر شريحة منفصلة ومدوَّرة"}

## مثال عملي كامل

بوضع كل الأجزاء معًا، إليك طريقة `main` يمكنك نسخها ولصقها في فئة Java جديدة وتشغيلها:

```java
public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Insert the pie chart
        JFreeChart chart = createPieChart();

        // 2️⃣ Explode the first slice
        explodeFirstSlice(chart);

        // 3️⃣ Rotate the chart 45° so the first slice starts at 45 degrees
        rotateChart(chart, 45);

        // 4️⃣ Highlight and customize the exploded slice
        customizeSlice(chart);

        // 5️⃣ Save to disk (optional)
        saveChart(chart, "fruit-pie.png");

        System.out.println("Pie chart generated: fruit-pie.png");
    }

    // ... (include the helper methods from steps 1‑4 here) ...
}
```

### النتيجة المتوقعة

تشغيل البرنامج ينشئ ملفًا باسم **fruit-pie.png**. افتحه وسترى:

- مخطط دائري بحجم 400 × 300 بعنوان “Fruit Distribution”.  
- شريحة “Apples” منفصلة إلى الخارج بنسبة 15 %.  
- المخطط بأكمله مدور بحيث تبدأ شريحة “Apples” من الموضع بزاوية 45 درجة.  
- الشريحة المنفصلة  

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء مخطط عمودي باستخدام Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [إدراج مخطط مبعثر](/words/hindi/net/programming-with-charts/insert-scatter-chart/)
- [إدراج مخطط مساحي](/words/hindi/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}