---
category: general
date: 2026-09-24
description: إدراج مخطط دائري في ملف DOCX باستخدام Aspose.Words للغة Java. تعلّم كيفية
  ضبط حجم الفتحة، تفجير شريحة الدائرة، تمييز شريحة المخطط الدائري، وإنشاء مخطط DOCX
  بسهولة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart word
- set hole size
- explode pie slice
- highlight pie chart slice
- create docx chart
language: ar
lastmod: 2026-09-24
og_description: إدراج مخطط دائري في مستند DOCX باستخدام Aspose.Words للغة Java. التحكم
  الكامل في حجم الفتحة، تفجير شريحة الدائرة، تمييز شريحة المخطط الدائري، وإنشاء مخطط
  DOCX في دقائق.
og_image_alt: Screenshot of a Word document displaying a formatted pie chart created
  with Java
og_title: إدراج كلمة مخطط دائري في جافا – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  headline: Insert pie chart word in Java – complete guide
  type: TechArticle
- description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  name: Insert pie chart word in Java – complete guide
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well) * Aspose.Words
      for Java library (version 23.9 or newer) * An IDE or build tool (Maven/Gradle)
      that can resolve the Aspose.Words dependency'
  - name: Why this matters
    text: '`Document` represents the whole Word file, while `DocumentBuilder` is the
      high‑level API that lets you insert paragraphs, tables, and charts without dealing
      with low‑level XML. Starting with a clean document ensures that the chart you
      add is the only content, which is perfect for learning or for gen'
  - name: Practical tip
    text: If you later decide to switch to a doughnut chart, simply change the `holeSize`
      value to a percentage (e.g., `30`). The same API works for both chart types.
  - name: Why explode?
    text: An exploded slice draws the reader’s eye to the most important data point—perfect
      for dashboards or executive summaries. The value `20` means 20 % of the radius;
      you can adjust it between `0` (no explosion) and `100` (fully detached).
  - name: Expert note
    text: Changing the fill color of a specific slice requires accessing the `DataPoint`
      object. If you have multiple series, iterate through `series.getDataPoints()`
      and apply styles conditionally.
  - name: Pro tip
    text: Always call `setHoleSize(0)` **after** `insertChart`. If you set it before
      insertion, Aspose.Words will revert to the default doughnut size once the chart
      is created.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart formatting
title: إدراج مخطط دائري في جافا – دليل كامل
url: /ar/java/using-document-elements/insert-pie-chart-word-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إدراج مخطط دائري في Java – دليل كامل

إذا كنت بحاجة إلى **إدراج مخطط دائري** في ملف DOCX، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك باستخدام Aspose.Words for Java. سترى سير العمل الكامل من إنشاء المستند إلى تخصيص المخطط بحيث يتم تفجير الشريحة، وتعيين حجم الفتحة إلى صفر، وتحديد الشريحة.

التعامل مع المخططات في مستندات Word غالبًا ما يبدو كمسألة منفصلة عن معالجة النص العادية، لكن Aspose.Words يوحدهما. في الخطوات أدناه ستتعلم أيضًا كيفية **إنشاء مخطط docx** جاهز للفتح في Microsoft Word أو Google Docs أو أي عارض متوافق مع DOCX.

## ما ستحققه

* **إدراج مخطط دائري** في مستند فارغ  
* **تعيين حجم الفتحة** لجعل المخطط دائرة كاملة (بدون دونات)  
* **تفجير شريحة المخطط** لجذب الانتباه إلى جزء محدد  
* **تمييز شريحة المخطط** بتنسيق مخصص  
* **إنشاء مخطط docx** يمكن مشاركته أو تحريره لاحقًا  

### المتطلبات المسبقة

* Java 17 أو أحدث (الكود يُترجم أيضًا مع Java 8)  
* مكتبة Aspose.Words for Java (الإصدار 23.9 أو أحدث)  
* بيئة تطوير متكاملة أو أداة بناء (Maven/Gradle) يمكنها حل تبعية Aspose.Words  

```xml
<!-- Example Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

---

## كيفية إدراج مخطط دائري في DOCX باستخدام Aspose.Words

الخطوة الأولى هي إنشاء مستند فارغ جديد والحصول على `DocumentBuilder`. يمنحك الـ builder وصولًا مباشرًا إلى تدفق محتوى المستند، مما يجعل من السهل **إدراج مخطط دائري**.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

### لماذا هذا مهم
`Document` يمثل ملف Word بالكامل، بينما `DocumentBuilder` هو API عالي المستوى يتيح لك إدراج فقرات وجداول ومخططات دون التعامل مع XML منخفض المستوى. بدءًا من مستند نظيف يضمن أن المخطط الذي تضيفه هو المحتوى الوحيد، وهو مثالي للتعلم أو لإنشاء تقارير مبنية على القوالب.

## تعيين حجم الفتحة لإنشاء دائرة كاملة

بشكل افتراضي، يقوم Aspose.Words بإنشاء مخطط دونات عندما تطلب مخططًا دائريًا. لجعل المخطط دائرة حقيقية، يجب عليك **تعيين حجم الفتحة** إلى `0`. هذا يزيل الفتحة الداخلية ويعطي مظهرًا كلاسيكيًا للمخطط الدائري.

```java
        // Step 2: Insert a pie chart with a specific size
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Step 4: Ensure the chart is a full pie (no doughnut hole)
        pieChart.getChart().setHoleSize(0);   // set hole size to zero
```

### نصيحة عملية
إذا قررت لاحقًا التحويل إلى مخطط دونات، ما عليك سوى تغيير قيمة `holeSize` إلى نسبة مئوية (مثال: `30`). نفس الـ API يعمل لكلا نوعي المخطط.

## تفجير شريحة المخطط لتسليط الضوء على جزء

تفجير شريحة يجعلها بارزة بصريًا. عملية **تفجير شريحة المخطط** تحرك الشريحة المختارة إلى الخارج بنسبة مئوية من نصف قطر المخطط.

```java
        // Step 3: Explode the first slice to highlight it
        pieChart.getChart().getSeries().get(0).setExplosion(20); // explode pie slice
```

### لماذا التفجير؟
الشريحة المتفجرة تجذب انتباه القارئ إلى أهم نقطة بيانات—مثالي للوحة التحكم أو الملخصات التنفيذية. القيمة `20` تعني 20 % من نصف القطر؛ يمكنك تعديلها بين `0` (بدون تفجير) و`100` (منفصلة تمامًا).

## تمييز شريحة المخطط بتنسيق مخصص

إلى جانب التفجير، قد ترغب في **تمييز شريحة المخطط** عن طريق تغيير لون التعبئة أو الحدود. بينما يركز كود العرض على التفجير، يمكنك توسيعه كما يلي:

```java
        // Optional: Change fill color of the exploded slice
        ChartSeries series = pieChart.getChart().getSeries().get(0);
        series.getDataPoints().get(0).getFormat().setFillColor(java.awt.Color.RED);
```

### ملاحظة خبير
تغيير لون التعبئة لشريحة معينة يتطلب الوصول إلى كائن `DataPoint`. إذا كان لديك عدة سلاسل، قم بالتكرار عبر `series.getDataPoints()` وطبق الأنماط بشكل شرطي.

## حفظ والتحقق من المخطط docx المُنشأ

أخيرًا، تقوم **بإنشاء مخطط docx** عن طريق حفظ الـ `Document`. يمكن فتح الملف الناتج في Microsoft Word لرؤية المخطط الدائري المُنسق.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartFormatted.docx");
    }
}
```

#### النتيجة المتوقعة
فتح `PieChartFormatted.docx` يظهر مخططًا دائريًا واحدًا:

* المخطط يشغل مساحة 400 × 300 pt.  
* حجم الفتحة هو `0`، لذا المخطط دائرة كاملة.  
* الشريحة الأولى متفجرة بنسبة 20 % وملوَّنة بالأحمر (إذا أضفت التنسيق الاختياري).  

الآن لديك **مخطط docx** يمكن توزيعه، أو تضمينه في رسائل البريد الإلكتروني، أو تحريره برمجيًا.

---

## الاختلافات الشائعة وحالات الحافة

| السيناريو | كيفية تعديل الكود |
|----------|----------------------|
| **سلاسل متعددة** | التكرار عبر `pieChart.getChart().getSeries()` وتعيين `Explosion` أو `FillColor` لكل سلسلة. |
| **بيانات ديناميكية** | ملء السلاسل بالقيم من قاعدة بيانات أو ملف CSV قبل استدعاء `setExplosion`. |
| **حجم مخطط مختلف** | تغيير معاملات العرض/الارتفاع في `insertChart(ChartType.PIE, width, height)`. |
| **تصدير إلى PDF** | بعد حفظ الـ DOCX، استدعِ `doc.save("output.pdf")` لإنشاء نسخة PDF من نفس المخطط. |
| **التعريب** | استخدام `DocumentBuilder.insertChart` مع تنسيق أرقام مخصص للمنطقة المحلية للملصقات. |

### نصيحة احترافية
دائمًا استدعِ `setHoleSize(0)` **بعد** `insertChart`. إذا قمت بتعيينه قبل الإدراج، سيعيد Aspose.Words ضبط الحجم إلى حجم الدونات الافتراضي بمجرد إنشاء المخطط.

---

## ملخص

أنت الآن تعرف كيف **إدراج مخطط دائري** في مستند Word باستخدام Java، وكيف **تعيين حجم الفتحة** للحصول على مظهر دائرة كاملة، وكيف **تفجير شريحة المخطط** لجذب الانتباه، وكيف **تمييز شريحة المخطط** بألوان مخصصة. يوضح المثال الكامل أيضًا كيفية **إنشاء مخطط docx** جاهز للتوزيع.

---

## الخطوات التالية

* استكشاف أنواع مخططات أخرى (`BAR`, `LINE`, `SCATTER`) باستخدام `ChartType`.  
* دمج إنشاء المخطط مع دمج البريد لإنتاج تقارير مخصصة.  
* دمج الـ DOCX المُولد في خدمة ويب تُعيد الملف عند الطلب.  

إذا واجهت مشاكل، تذكر التحقق من أنك تستخدم نسخة متوافقة من Aspose.Words وأن دليل الإخراج موجود وقابل للكتابة.

برمجة سعيدة!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء مخطط عمودي باستخدام Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [استخدام واجهة برمجة تطبيقات مخططات Word](/words/english/net/programming-with-charts/)
- [إدراج مخطط فقاعة في Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}