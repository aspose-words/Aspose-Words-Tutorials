---
category: general
date: 2026-11-22
description: إنشاء مخطط دائري في جافا وتعلم كيفية ضبط حجم المخطط، إضافة تسميات البيانات،
  إظهار النسب المئوية، وتدوير الشريحة الأولى لتحقيق تأثير بصري واضح.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- set chart size
- show percentages pie chart
- add data labels pie chart
- rotate pie chart slice
language: ar
lastmod: 2026-11-22
og_description: إنشاء مخطط دائري في جافا، ثم ضبط حجم المخطط، إظهار النسب المئوية على
  تسميات البيانات، وتدوير الشريحة الأولى—كل ذلك في مثال واحد قابل للتنفيذ.
og_image_alt: Screenshot of a created pie chart showing custom size, percentage labels,
  and a rotated first slice
og_title: إنشاء مخطط دائري بحجم مخصص، وعناوين، وتدوير في جافا
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  headline: Create pie chart with custom size, data labels, and rotation in Java
  type: TechArticle
- description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  name: Create pie chart with custom size, data labels, and rotation in Java
  steps:
  - name: Why each step matters
    text: '| Step | Purpose | How it relates to the keywords | |------|---------|--------------------------------|
      | **Insert chart** | **Create pie chart** – the core object that will render
      the visual. | Directly satisfies the *create pie chart* requirement. | | **Set
      dimensions** | The `addChart(..., 400, 3'
  - name: 1. Insert a pie chart and set chart size
    text: '```java IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50,
      400, 300); ```'
  - name: 2. Populate the chart with data
    text: The demo adds three categories and a single series. Replace the hard‑coded
      numbers with data from a database, CSV, or user input as needed.
  - name: 3. Show percentages on each slice
    text: '```java series.getDataLabelFormat().setShowPercentage(true); ```'
  - name: 4. Add detailed data labels
    text: '```java series.getDataLabelFormat().setShowCategoryName(false); series.getDataLabelFormat().setShowLeaderLines(false);
      ```'
  - name: 5. Rotate the first slice
    text: '```java chart.setFirstSliceAngle(45); ```'
  - name: 6. Save and view the result
    text: 'Running the program produces `output/PieChartDemo.pptx`. Open it in PowerPoint
      or any compatible viewer to see the final pie chart:'
  - name: What’s next?
    text: '* Explore other chart types (Bar, Line, Area) using the same `ChartType`
      enum. * Combine multiple charts on a single slide for dashboards. * Export charts
      to PNG or SVG for use in web applications.'
  type: HowTo
tags:
- Java
- charts
- Aspose.Slides
- data‑visualization
title: إنشاء مخطط دائري بحجم مخصص، وعلامات بيانات، وتدوير في جافا
url: /ar/java/getting-started/create-pie-chart-with-custom-size-data-labels-and-rotation-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مخطط دائري بحجم مخصص، تسميات البيانات، وتدوير في جافا

إذا كنت بحاجة إلى **إنشاء مخطط دائري** في جافا، فإن هذا الدليل يشرح لك العملية بالكامل. ستتعلم كيفية **تحديد حجم المخطط**، تمكين **إظهار النسب في المخطط الدائري**، إضافة **تسميات البيانات للمخطط الدائري**، و**تدوير شريحة المخطط الدائري** بحيث تبدأ الشريحة الأولى بزاوية 45 درجة.

يستخدم المثال **Aspose.Slides for Java**، مكتبة شائعة الاستخدام لمعالجة ملفات PowerPoint. تنطبق نفس المفاهيم على مكتبات الرسم البياني الأخرى؛ فقط استبدل استدعاءات الـ API بما يعادلها في مجموعة أدواتك.

## المتطلبات المسبقة

* تثبيت Java 17 أو أحدث  
* Maven 3.8+ (أو Gradle) لإدارة الاعتمادات  
* فهم أساسي لصياغة Java  
* الوصول إلى ملف Aspose.Slides for Java الثنائي (يمكنك الحصول على نسخة تجريبية مجانية من الموقع الرسمي)

أضف الاعتماد إلى ملف `pom.xml` الخاص بك:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-slides</artifactId>
    <version>24.9</version> <!-- latest version as of November 2026 -->
</dependency>
```

## إنشاء مخطط دائري – مثال كامل

البرنامج التالي ينشئ شريحة PowerPoint تحتوي على مخطط دائري بحجم مخصص، تسميات بيانات النسبة المئوية، وشريحة أولى مدورة.

```java
package com.example.piechart;

import com.aspose.slides.*;
import com.aspose.slides.charts.*;

public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a presentation
        Presentation pres = new Presentation();

        // 2️⃣ Add a blank slide
        ISlide slide = pres.getSlides().addEmptySlide(pres.getLayoutSlides().get_Item(0));

        // 3️⃣ Insert a pie chart (create pie chart)
        IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
        // The dimensions above also demonstrate set chart size

        // 4️⃣ Populate the chart with sample data
        IChartDataWorkbook workbook = chart.getChartData().getChartDataWorkbook();

        // Clear the default series & categories
        chart.getChartData().getSeries().clear();
        chart.getChartData().getCategories().clear();

        // Add categories (slices)
        chart.getChartData().getCategories().add(workbook.getCell(0, "A1", "Category A"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A2", "Category B"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A3", "Category C"));

        // Add a series and assign values
        IChartSeries series = chart.getChartData().getSeries().add(
                workbook.getCell(0, "B1", "Series 1"),
                chart.getType());

        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B1", 30));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B2", 45));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B3", 25));

        // 5️⃣ Enable percentage display on data labels (show percentages pie chart)
        series.getDataLabelFormat().setShowPercentage(true);
        series.getDataLabelFormat().setShowCategoryName(false);
        series.getDataLabelFormat().setShowLegendKey(false);
        series.getDataLabelFormat().setShowSeriesName(false);
        series.getDataLabelFormat().setShowValue(false);
        series.getDataLabelFormat().setShowLeaderLines(false);

        // 6️⃣ Rotate the chart so the first slice starts at 45 degrees (rotate pie chart slice)
        chart.setFirstSliceAngle(45);

        // 7️⃣ Save the presentation
        String outPath = "output/PieChartDemo.pptx";
        pres.save(outPath, SaveFormat.Pptx);
        System.out.println("Presentation saved to " + outPath);
    }
}
```

### لماذا كل خطوة مهمة

| الخطوة | الغرض | كيف يرتبط بالكلمات المفتاحية |
|--------|-------|------------------------------|
| **إدراج مخطط** | **إنشاء مخطط دائري** – الكائن الأساسي الذي سيعرض الشكل البصري. | يفي مباشرة بمتطلب *إنشاء مخطط دائري*. |
| **تحديد الأبعاد** | استدعاء `addChart(..., 400, 300)` يوضح **تحديد حجم المخطط**. | يتحكم في العرض (400 px) والارتفاع (300 px). |
| **إظهار النسب** | `setShowPercentage(true)` يجعل المخطط **يظهر النسب في المخطط الدائري** على كل شريحة. | غالبًا ما يحتاج المستخدمون إلى النسب بدلاً من القيم الخام. |
| **إضافة تسميات البيانات** | تكوين `DataLabelFormat` يضيف **تسميات البيانات للمخطط الدائري** مع الرؤية المطلوبة. | تحسن التسميات قابلية القراءة ويمكن تخصيصها. |
| **تدوير الشريحة** | `setFirstSliceAngle(45)` يدور المخطط بحيث تبدأ الشريحة الأولى بزاوية 45 درجة، محققًا **تدوير شريحة المخطط الدائري**. | يحسن التركيز البصري على شريحة معينة. |

## تحليل خطوة بخطوة

### 1. إدراج مخطط دائري وتحديد حجم المخطط

```java
IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
```

*طريقة `addChart` تنشئ المخطط وتحدد **حجم المخطط** في آنٍ واحد إلى 400 × 300 نقطة.*  
إذا كنت بحاجة إلى حجم مختلف، عدل الوسيطين الأخيرين.

### 2. ملء المخطط بالبيانات

يعرض المثال ثلاثة فئات وسلسلة واحدة. استبدل الأرقام المضمنة ببيانات من قاعدة بيانات، CSV، أو إدخال المستخدم حسب الحاجة.

### 3. إظهار النسب على كل شريحة

```java
series.getDataLabelFormat().setShowPercentage(true);
```

*تمكين `setShowPercentage(true)` يضمن أن المخطط **يظهر النسب في المخطط الدائري** ويحسب تلقائيًا حصة كل شريحة من الإجمالي.*

### 4. إضافة تسميات بيانات مفصلة

```java
series.getDataLabelFormat().setShowCategoryName(false);
series.getDataLabelFormat().setShowLeaderLines(false);
```

يمكنك تبديل خيارات التسميات الأخرى (`setShowValue`، `setShowSeriesName`، إلخ) لتخصيص تجربة **إضافة تسميات البيانات للمخطط الدائري**.

### 5. تدوير الشريحة الأولى

```java
chart.setFirstSliceAngle(45);
```

*استدعاء `setFirstSliceAngle(45)` **يدور شريحة المخطط الدائري** بحيث يبدأ الجزء الأول بزاوية 45 درجة، مما يجعله بارزًا.*

### 6. حفظ وعرض النتيجة

تشغيل البرنامج ينتج `output/PieChartDemo.pptx`. افتحه في PowerPoint أو أي عارض متوافق لرؤية المخطط الدائري النهائي:

![مثال إنشاء مخطط دائري](images/pie_chart_example.png){.align-center alt="لقطة شاشة لمخطط دائري تم إنشاؤه بحجم مخصص، تسميات النسبة المئوية، وشريحة أولى مدورة"}

الصورة أعلاه توضح نتيجة **إنشاء مخطط دائري**، مؤكدة أن الحجم، التسميات، النسب، والتدوير تم تطبيقها بشكل صحيح.

## الاختلافات الشائعة وحالات الحافة

| الحالة | التعديل |
|--------|----------|
| **أبعاد مخطط مختلفة** | غيّر معلمات العرض/الارتفاع في `addChart`. |
| **سلسلات متعددة** | أضف كائنات `IChartSeries` إضافية؛ يمكن لكل سلسلة أن تكون لها إعدادات التسميات الخاصة بها. |
| **تنسيق تسمية مخصص** | استخدم `series.getDataLabelFormat().setNumberFormat("0.0%")` للتحكم في عدد المنازل العشرية. |
| **التدوير إلى زاوية أخرى** | مرّر أي عدد صحيح (0‑360) إلى `setFirstSliceAngle`. |
| **تصدير كصورة** | بعد الحفظ، استدعِ `chart.writeAsSvg(outPath)` أو `chart.writeAsPng(outPath)` للحصول على نسخة نقطية. |

> **نصيحة احترافية:** إذا كنت تخطط لإنشاء العديد من المخططات في حلقة، أعد استخدام كائن `Presentation` نفسه واستبدل بيانات المخطط فقط. هذا يقلل من استهلاك الذاكرة ويسرّع المعالجة.

## الخلاصة

أنت الآن تعرف كيف **تنشئ مخططًا دائريًا** في جافا، **تحدد حجم المخطط**، تمكّن **إظهار النسب في المخطط الدائري**، **تضيف تسميات البيانات للمخطط الدائري**، و**تدوير شريحة المخطط الدائري** للحصول على تركيز بصري أفضل. المثال الكامل القابل للتنفيذ يوضح كل خطوة من التهيئة إلى حفظ ملف PowerPoint النهائي.

### ما التالي؟

* استكشف أنواع المخططات الأخرى (شريط، خط، مساحة) باستخدام نفس تعداد `ChartType`.  
* دمج مخططات متعددة في شريحة واحدة لإنشاء لوحات معلومات.  
* تصدير المخططات إلى PNG أو SVG للاستخدام في تطبيقات الويب.  

لا تتردد في تجربة الألوان، الأساطير، وتأثيرات الرسوم المتحركة—تصوراتك البيانية لا حدود لها سوى خيالك. نتمنى لك رسمًا ممتعًا!

## ما الذي ينبغي أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إدراج مخطط دائري في Word – إضافة نسبة تسمية البيانات](/words/english/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/)
- [كيفية تفجير شريحة مخطط دائري في Java – دليل مخطط Aspose.Words](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [إدراج مخطط دائري في Java – تفجير، تدوير وتحديد الشرائح](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}