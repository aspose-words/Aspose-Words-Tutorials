---
category: general
date: 2026-09-18
description: تعلم كيفية إنشاء مخطط شعاعي في مستند Word باستخدام Java، وإضافة تسميات
  بيانات المخطط، وإدراج بيانات السلسلة مع مثال كامل للكود.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- add chart data labels
- add series data
- create blank word
- how to insert chart
language: ar
lastmod: 2026-09-18
og_description: إنشاء مخطط شعاعي في مستند Word باستخدام Java، إضافة تسميات بيانات
  المخطط، وإدراج بيانات السلسلة في دليل واحد.
og_image_alt: Radial chart displayed inside a generated Word document
og_title: إنشاء مخطط قطري في Word باستخدام Java – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn how to create radial chart in a Word document using Java, add
    chart data labels, and insert series data with a complete code example.
  headline: How to create radial chart in a Word document with Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- Word automation
title: كيفية إنشاء مخطط شعاعي في مستند Word باستخدام Java
url: /ar/java/using-document-elements/how-to-create-radial-chart-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مخطط قطري في مستند Word باستخدام Java

إذا كنت بحاجة إلى إنشاء مخطط قطري في مستند Word، يوضح لك هذا الدليل الخطوات الدقيقة. ستتعلم أيضًا كيفية إضافة تسميات بيانات المخطط وإدراج بيانات السلسلة بحيث يكون المخطط جاهزًا للعرض.

إنشاء المخطط برمجيًا يزيل الحاجة إلى التنسيق اليدوي ويضمن التناسق عبر التقارير. يفترض هذا البرنامج التعليمي أن لديك معرفة أساسية بـ Java وإصدار حديث من مكتبة Aspose.Words for Java مثبتًا.

## ما ستحتاجه

* Java 17 أو أحدث  
* Aspose.Words for Java (الإصدار 23.12 أو أحدث)  
* بيئة تطوير متكاملة أو أداة بناء يمكنها حل تبعيات Maven/Gradle  

إن وجود هذه المتطلبات مسبقًا يتيح لك تشغيل المثال دون أي إعداد إضافي.

## كيفية إنشاء مخطط قطري في مستند Word

الخطوة الأولى هي إنشاء ملف Word فارغ سيستضيف المخطط. يوفر المستند الفارغ مساحة عمل نظيفة ويتجنب الأنماط غير المقصودة.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

/* Step 1: Create a new blank Word document */
Document doc = new Document();

/* Step 2: Open a builder to add content */
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` يمثل ملف .docx بالكامل، بينما `DocumentBuilder` يوفر طرقًا لإدراج عناصر مثل الفقرات والجداول والمخططات.

## كيفية إدراج المخطط

بعد ذلك تقوم بإدراج المخطط نفسه. تُنشئ طريقة `insertChart` كائن مخطط وتضعه في موضع المؤشر الحالي للـ builder.

```java
import com.aspose.words.Chart;
import com.aspose.words.ChartType;

/* Step 3: Insert a polar (radial) chart with a width of 400 pt and height of 300 pt */
Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);
```

المخطط القطبي يعرض نقاط البيانات حول محور مركزي، وهو مثالي لعرض المعلومات الدورية. تُعبّر الأبعاد بالنقاط (1 pt ≈ 1/72 inch).

## إضافة بيانات السلسلة إلى المخطط

المخطط بدون بيانات سلسلة يكون فارغًا. يمكنك إضافة سلسلة يدويًا أو ربطها بمصدر بيانات. يضيف المثال أدناه سلسلة واحدة تحتوي على ثلاث نقاط بيانات.

```java
import com.aspose.words.ChartSeries;
import java.util.Arrays;

/* Step 4: Add a series and populate it with values */
ChartSeries series = chart.getSeries().add("Sample Series",
        Arrays.asList("Jan", "Feb", "Mar"),
        Arrays.asList(30.0, 45.0, 25.0));
```

`add` تستقبل اسم السلسلة، قائمة بتسميات الفئات، وقائمة بالقيم الرقمية المقابلة. يمكنك تكرار هذا الجزء لإضافة سلاسل إضافية (`addSeriesData`).

## إضافة تسميات بيانات المخطط إلى السلسلة الأولى

تجعل تسميات البيانات المخطط قابلًا للقراءة دون الحاجة إلى التحويم فوق النقاط. السطر التالي يفعّل تسميات القيم للسلسلة الأولى.

```java
/* Step 5: Show the numeric values as data labels */
chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);
```

تعيين `showValue` إلى `true` يعرض قيمة كل نقطة مباشرةً على المخطط. يمكنك أيضًا تمكين أسماء الفئات أو النسب المئوية أو خطوط الربط عبر نفس كائن `DataLabelFormat`.

## حفظ ملف Word

بعد ضبط المخطط، اكتب المستند إلى القرص. اختر موقعًا يمكن لتطبيقك الوصول إليه.

```java
/* Step 6: Save the document containing the radial chart */
doc.save("output/RadialChart.docx");
```

الملف `RadialChart.docx` الآن يحتوي على مخطط قطري كامل الوظائف مع تسميات البيانات.

## مثال كامل يعمل

فيما يلي برنامج مستقل يمكنك نسخه، تجميعه، وتشغيله. يوضح سير العمل الكامل من إنشاء مستند Word فارغ إلى حفظ مخطط قطري مع تسميات البيانات.

```java
import com.aspose.words.*;

import java.util.Arrays;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank Word document
        Document doc = new Document();

        // Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a polar (radial) chart with the desired dimensions
        Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);

        // Add a series and populate it with sample data
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                Arrays.asList("Q1", "Q2", "Q3", "Q4"),
                Arrays.asList(15000.0, 23000.0, 18000.0, 21000.0));

        // Show the numeric values as data labels for the first series
        chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);

        // Save the document containing the chart
        doc.save("output/RadialChart.docx");
    }
}
```

**النتيجة المتوقعة**

عند فتح `output/RadialChart.docx` في Microsoft Word، سترى مخططًا قطريًا بعنوان *Quarterly Sales*. كل نقطة تعرض قيمتها الرقمية (مثلاً “15000”) بجوار العلامة.

## الاختلافات الشائعة وحالات الحافة

| الحالة | التغيير الموصى به |
|-----------|--------------------|
| تحتاج إلى نوع مخطط مختلف | استبدل `ChartType.POLAR` بأي قيمة أخرى من تعداد `ChartType` (مثال: `ChartType.COLUMN`). |
| يجب أن يستخدم المخطط نطاق Excel خارجي | استخدم `chart.setDataRange("Sheet1!A1:B5")` بعد إنشاء المخطط وتحميل المصنف. |
| تريد إخفاء المفتاح | `chart.getLegend().setVisible(false);` |
| يجب حفظ المستند كملف PDF | استدعِ `doc.save("RadialChart.pdf");` – تقوم Aspose.Words بتحويل المخطط تلقائيًا. |

هذه التعديلات تحافظ على منطق البرنامج الأساسي مع تكييف الناتج وفق المتطلبات المحددة.

## نصائح احترافية

* **إعادة استخدام الـ builder** – يمكنك إدراج مخططات متعددة في نفس المستند عبر استدعاء `builder.insertChart` بشكل متكرر.  
* **الأداء** – عند إنشاء العديد من المخططات، أنشئ كائن `DocumentBuilder` واحد وأعد استخدامه لتقليل عبء تخصيص الكائنات.  
* **التنسيق** – مظهر المخطط (الألوان، سمك الخط) يتحكم فيه عبر طرق كائن `Chart` مثل `getSeries().get(i).getFormat()`. جرّب هذه الإعدادات لتطابق هوية الشركة.

## الخلاصة

أصبحت الآن تعرف كيفية إنشاء مخطط قطري في مستند Word باستخدام Java، إضافة بيانات السلسلة، وإضافة تسميات بيانات المخطط قبل حفظ الملف. يمكن توسيع المثال الكامل للتعامل مع سلاسل إضافية، أنماط مخصصة، أو صيغ إخراج بديلة.

استكشف المواضيع ذات الصلة مثل **كيفية إدراج مخطط** من مصادر بيانات خارجية، **إنشاء مستند Word فارغ** باستخدام قوالب مسبقة التعريف، و**إضافة بيانات السلسلة** بشكل ديناميكي من قواعد البيانات. جرّب أنواع مخططات مختلفة لاكتشاف أي تصور يوضح بياناتك بأفضل شكل.

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء مخطط عمودي باستخدام Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [إنشاء مستند Word باستخدام Java – إضافة شكل مستطيل مع تأثير الظل](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [تعيين الخيارات الافتراضية لتسميات البيانات في المخطط](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}