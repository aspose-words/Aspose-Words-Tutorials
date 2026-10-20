---
category: general
date: 2026-07-16
description: إنشاء مخطط دائري في Java باستخدام Aspose.Words. تعلّم كيفية إضافة خطوط
  ربط، إظهار وسيلة إيضاح المخطط، وإخراج شريحة في دليل واحد.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add leader lines
- show chart legend
- how to explode slice
- how to add legend
language: ar
lastmod: 2026-07-16
og_description: إنشاء مخطط دائري في جافا باستخدام Aspose.Words. يوضح هذا الدليل كيفية
  إضافة خطوط ربط، وعرض مفتاح المخطط، وتفجير شريحة، مما يمنحك تصورًا مصقولًا في دقائق.
og_image_alt: Screenshot of a Java‑generated pie chart with an exploded slice and
  visible legend
og_title: إنشاء مخطط دائري باستخدام Aspose.Words Java – دليل كامل للتنسيق
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  headline: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  name: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  steps:
  - name: Java 17 (or later) installed.
    text: Java 17 (or later) installed.
  - name: Aspose.Words for Java JAR on your classpath.
    text: Aspose.Words for Java JAR on your classpath.
  - name: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
    text: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart Formatting
- Data Visualization
title: إنشاء مخطط دائري باستخدام Aspose.Words Java – دليل شامل خطوة بخطوة
url: /ar/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مخطط دائري باستخدام Aspose.Words Java – دليل خطوة‑بخطوة كامل

هل تساءلت يومًا كيف **إنشاء مخطط دائري** برمجيًا في Java دون التعامل مع واجهات برمجة التطبيقات منخفضة المستوى للرسم؟ لست الوحيد. يحتاج العديد من المطورين إلى تمثيل بصري سريع للتقارير أو لوحات المعلومات أو المستندات الآلية، ويتجهون إلى Aspose.Words لأنها تتولى الجزء الأكبر من العمل.  

في هذا الدرس سنستعرض مثالًا كاملًا جاهزًا للتنفيذ لا يقتصر فقط على **إنشاء مخطط دائري** بل يوضح لك أيضًا كيفية **إضافة خطوط ربط**، **إظهار أسطورة المخطط**، وحتى **تفجير شريحة** للتأكيد. في النهاية ستحصل على ملف `.docx` يبدو مصقولًا بما يكفي لإبهار العميل.

> **فوز سريع:** المقتطف البرمجي أدناه يعمل مباشرةً مع Aspose.Words for Java 23.9 (أو أي إصدار أحدث). لا توجد تبعيات إضافية، مجرد ملف JAR.

## ما ستتعلمه

- إعداد مستند Word فارغ باستخدام `DocumentBuilder`.
- إدراج **مخطط دائري** بحجم مخصص.
- استخدام ميزة **تفجير الشريحة** لتسليط الضوء على نقطة بيانات.
- تمكين **خطوط الربط** بحيث تظل الشريحة المفجرة متصلة بالعلامة.
- تشغيل **أسطورة المخطط** حتى يتمكن القارئ من التعرف فورًا على كل شريحة.
- حفظ النتيجة في ملف `.docx` يمكنك فتحه في Microsoft Word أو LibreOffice.

**المتطلبات المسبقة** – ستحتاج إلى:

1. Java 17 (أو أحدث) مثبتة.
2. ملف JAR الخاص بـ Aspose.Words for Java على مسار الـ classpath.
3. بيئة تطوير متكاملة أو محرر نصوص بسيط—IntelliJ IDEA، Eclipse، VS Code، أو أي أداة تفضلها.

الآن، لنبدأ.

## الخطوة 1: تهيئة المستند والباني – التحضير لـ **إنشاء مخطط دائري**

أولاً، نحتاج إلى لوحة مستند نظيفة. `Document` تمثل ملف Word بالكامل، بينما `DocumentBuilder` هو المساعد الذي يتيح لنا إضافة المحتوى.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();               // the container for our Word file
        DocumentBuilder builder = new DocumentBuilder(doc); // convenient API for adding elements
```

> **لماذا هذا مهم:** بدءًا بـ `Document` جديد يضمن عدم وجود أنماط مخفية أو كائنات متبقية قد تتداخل مع رسم المخطط.

## الخطوة 2: إدراج **المخطط الدائري** – الحجم مهم

Aspose.Words تجعل إدراج المخطط سطرًا واحدًا. هنا نطلب مخططًا دائريًا بحجم 400 × 300 نقطة—ما يعادل تقريبًا 5.5 × 4.2 بوصة على الشاشة المعتادة.

```java
        // Step 2: Insert a pie chart of size 400x300 points
        Shape chartShape = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = chartShape.getChart(); // the underlying chart object we will format
```

> **نصيحة احترافية:** إذا كنت بحاجة إلى حجم مختلف، ما عليك سوى تعديل القيمتين الرقميتين. تعمل الـ API بالنقاط، حيث 72 نقطة = 1 بوصة.

## الخطوة 3: **كيفية تفجير الشريحة** – إبراز نقطة بيانات رئيسية

تفجير الشريحة يخرجها من باقي الدائرة، مما يجذب انتباه القارئ. طريقة `setExplosion` تأخذ عددًا صحيحًا يمثل المسافة بالنقاط.

```java
        // Step 3: Explode the first slice to emphasize it
        chart.getSeries().get(0).setExplosion(10); // 10 points outward
```

> **ماذا لو كان لديك عدة سلاسل؟** يمكنك استدعاء `setExplosion` على أي فهرس سلسلة (`get(1)`, `get(2)`, …) لتفجير شرائح مختلفة.

## الخطوة 4: **إضافة خطوط ربط** و **إظهار أسطورة المخطط** – ربط النقاط

عند تفجير شريحة، قد تبتعد العلامة. خطوط الربط تحافظ على ارتباط العلامة، مما يحافظ على قابلية القراءة. في الوقت نفسه، توفر الأسطورة مفتاحًا سريعًا لجميع الشرائح.

```java
        // Step 4: Enable leader lines for the exploded slice and show the legend
        chart.getSeries().get(0).setLeaderLines(true); // draws a line from slice to its label
        chart.setShowLegend(true);                     // makes the legend visible below the chart
```

> **لماذا تمكين خطوط الربط؟** بدونها قد تظهر العلامة عائمة، مما يربك المستخدمين حول الشريحة التي تنتمي إليها.  
> **هل تحتاج إلى موضع أسطورة مخصص؟** استخدم `chart.getLegend().setPosition(LegendPosition.TOP)` أو أي قيمة أخرى من الـ enum.

## الخطوة 5: حفظ المستند – الخطوة النهائية لـ **إنشاء مخطط دائري**

أخيرًا، نقوم بحفظ المستند على القرص. عدل المسار إلى مجلد لديك صلاحية كتابة فيه.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartDemo.docx");
    }
}
```

شغّل البرنامج، افتح الملف `PieChartDemo.docx` الذي تم إنشاؤه، وسترى مخططًا دائريًا منسقًا بشكل جيد مع شريحة أولى مفجرة، خطوط ربط، وأسطورة مرئية.

![مثال على مخطط دائري يظهر شريحة مفجرة وأسطر توضيحية](pie-chart-example.png){: .center-image alt="مثال على إنشاء مخطط دائري مع شريحة مفجرة، خطوط ربط، وأسطر توضيحية"}

### النتيجة المتوقعة

عند فتح ملف Word، سيظهر المخطط تقريبًا كما يلي:

- مخطط دائري بحجم 400 × 300 نقطة.
- الشريحة الأولى مُزاحة بمقدار 10 نقطة.
- خط ربط رفيع يربط الشريحة المفجرة بعلامتها.
- أسطورة تحت المخطط تسرد اسم كل سلسلة.

إذا لم تظهر خطوط الربط، تحقق من أن `setLeaderLines(true)` تم استدعاؤه *بعد* ضبط قيمة التفجير—ترتيب الاستدعاءات مهم.

## المشكلات الشائعة وكيفية تجنّبها

| المشكلة | لماذا يحدث | الحل |
|-------|------------|-----|
| **عدم ظهور الأسطورة** | تم إغفال `setShowLegend(true)` أو تم استدعاؤه على كائن مخطط خاطئ. | تأكد من استدعاء `chart.setShowLegend(true)` **بعد** الحصول على الـ `Chart` من الشكل. |
| **خط الربط مفقود** | لم يتم تفجير الشريحة، أو نوع المخطط لا يدعم خطوط الربط. | يدعم فقط `ChartType.PIE` (أو `PIE_3D`) خطوط الربط. استدعِ `setExplosion` أولًا، ثم `setLeaderLines(true)`. |
| **الشريحة لا تتحرك** | قيمة التفجير منخفضة جدًا (0‑2 نقطة). | زد العدد، مثلًا `setExplosion(10)` أو أعلى للحصول على تأثير أكثر وضوحًا. |
| **المخطط مشوّه** | استخدام حجم غير مربع (العرض ≠ الارتفاع) قد يضغط الدائرة. | حافظ على تساوي العرض والارتفاع أو تقريبًا؛ 400 × 300 يعمل لكن 400 × 400 يعطي دائرة مثالية. |

## تعديلات متقدمة (اختياري)

إذا رغبت في الذهاب إلى ما بعد الأساسيات، فكر في:

- **ألوان مخصصة**: `chart.getSeries().get(0).getDataPoints().get(i).getFormat().getFill().setForeColor(Color.RED);`
- **تسميات البيانات**: `chart.getSeries().get(0).setDataLabelType(ChartDataLabelType.CATEGORY);`
- **تأثير ثلاثي الأبعاد**: استبدل `ChartType.PIE` بـ `ChartType.PIE_3D`.

تتيح لك هذه الخيارات ضبط المظهر ليتماشى مع إرشادات العلامة التجارية للمؤسسة.

## ملخص – ما أنجزناه

بدأنا بمستند Word فارغ، **أنشأنا مخططًا دائريًا**، **فجرنا الشريحة الأولى**، **أضفنا خطوط ربط**، و**أظهرنا أسطورة المخطط**. يتضمن التدفق الكامل طريقة `main` مختصرة، مما يسهل دمجه في خطوط تقارير أكبر.

## الخطوات التالية

- **إضافة سلاسل أخرى**: ملء المخطط ببيانات حقيقية من قاعدة بيانات أو ملف CSV.
- **التصدير إلى PDF**: استخدم `doc.save("output.pdf", SaveFormat.PDF);` لإنشاء نسخة PDF.
- **دمج مع أشكال أخرى**: أدخل جداول، صور، أو مخططات إضافية لتكوين تقرير كامل.

إذا كنت مهتمًا بأنواع مخططات أخرى—عمود، شريط، خط—فقط استبدل `ChartType.PIE` بالـ enum المناسب واتبع نفس خطوات التنسيق.

---

*رسم مخططات سعيد!* لا تتردد في ترك تعليق إذا لم يعمل شيء كما توقعت، أو شارك كيف خصصت موضع الأسطورة. ملاحظاتك تساعدنا جميعًا على بناء مستندات آلية أفضل.

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء مخطط عمودي باستخدام Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [كيفية إنشاء مستندات PDF باستخدام Aspose.Words for Java | Document Processing API](/words/english/java/)
- [كيفية إضافة علامة مائية إلى المستندات باستخدام Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}