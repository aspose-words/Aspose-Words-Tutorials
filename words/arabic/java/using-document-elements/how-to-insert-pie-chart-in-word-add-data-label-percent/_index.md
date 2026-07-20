---
category: general
date: 2026-07-20
description: كيفية إدراج مخطط دائري في Word باستخدام Aspose.Words. تعلم إضافة نسبة
  تسمية البيانات وعرض النسب المئوية على المخطط للمستندات الاحترافية.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- add data label percent
- display percentages on chart
- add pie chart to word
- show percent on pie chart
language: ar
lastmod: 2026-07-20
og_description: كيفية إدراج مخطط دائري في Word باستخدام Aspose.Words. يوضح هذا الدليل
  كيفية إضافة نسبة تسمية البيانات وعرض النسب المئوية على المخطط في بضع أسطر فقط.
og_image_alt: Screenshot showing how to insert pie chart in Word with percentage labels
og_title: كيفية إدراج مخطط دائري في Word – دليل سريع
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: how to insert pie chart in Word with Aspose.Words. Learn to add data
    label percent and display percentages on chart for professional documents.
  headline: how to insert pie chart in Word – add data label percent
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Word Automation
title: كيفية إدراج مخطط دائري في Word – إضافة نسبة تسمية البيانات
url: /ar/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إدراج مخطط دائري في Word – إضافة نسبة تسمية البيانات

هل تساءلت يومًا **how to insert pie chart** في مستند Word دون الحاجة إلى التعامل مع الواجهة؟ لست وحدك. في العديد من سيناريوهات التقارير تحتاج إلى *add pie chart to Word*، والأهم من ذلك **show percent on pie chart** حتى يتمكن القراء من فهم توزيع البيانات فورًا.

في هذا الدرس سنستعرض العملية الكاملة باستخدام Aspose.Words for Java. بحلول النهاية ستعرف بالضبط كيف **add data label percent**، **display percentages on chart**، وستحصل على مخطط دائري مصقول يبدو صحيحًا من المرة الأولى. لا إضافات خارجية، ولا تعديلات يدوية—فقط شفرة نظيفة يمكنك إدراجها في أي مشروع.

---

## المتطلبات المسبقة

- Java 17 (أو أحدث) – الإصدار الحالي LTS الذي تدعمه Aspose.Words.
- Aspose.Words for Java 24.x (الأحدث وقت كتابة هذا الدليل، يوليو 2026).
- إعداد أساسي لـ Maven أو Gradle لسحب المكتبة.
- بيئة تطوير تحبها (IntelliJ IDEA، Eclipse، VS Code… أيًا كان).

إذا كان لديك هذه بالفعل، رائع—لنبدأ.

---

## الخطوة 1: إعداد المشروع واستيراد المكتبة

أولاً، أضف تبعية Aspose.Words إلى ملف `pom.xml` (Maven) أو `build.gradle` (Gradle). سيمنحك ذلك الوصول إلى الفئات `Document`، `DocumentBuilder`، وفئات المخطط.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **نصيحة احترافية:** حافظ على تحديث رقم الإصدار؛ الإصدارات الأحدث غالبًا ما تضيف إصلاحات متعلقة بالمخططات تجعل **display percentages on chart** أكثر موثوقية.

---

## الخطوة 2: إنشاء مستند Word جديد ومُنشئ

المُنشئ هو أداة متعددة الاستخدامات لإدراج المحتوى. هنا نقوم بإنشاء مستند جديد وربط `DocumentBuilder` به.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

لماذا نحتاج إلى مُنشئ؟ فهو يُجرد هياكل OpenXML منخفضة المستوى، مما يسمح لنا بالتركيز على *ما* نريد—مثل **add pie chart to word**—بدلاً من *كيف* يبدو XML.

---

## الخطوة 3: إدراج المخطط الدائري

الآن يأتي جوهر **how to insert pie chart**. نطلب من المُنشئ وضع مخطط دائري بحجم محدد. الأبعاد بوحدات النقاط (1 pt ≈ 1/72 in).

```java
        // Step 3: Insert a pie chart – width 400pt, height 300pt
        Chart pieChart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);
```

في هذه المرحلة يكون المخطط فارغًا، لكن العنصر النائب موجود بالفعل في المستند. لقد قمت بـ **add pie chart to word** برمجيًا.

---

## الخطوة 4: تعبئة المخطط بالبيانات

المخطط الدائري يحتاج على الأقل إلى سلسلة واحدة من القيم. لنزوده ببعض البيانات التجريبية التي تمثل حصة السوق.

```java
        // Step 4: Add a data series with sample values
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataPoints().add(30); // Product A
        series.getDataPoints().add(45); // Product B
        series.getDataPoints().add(25); // Product C
```

إذا احتجت إلى سلاسل متعددة (دوائر مكدسة، دوائر دونات، إلخ) يمكنك استدعاء `pieChart.getSeries().add()` وتكرار الخطوات. نفس المنطق ينطبق عندما تريد **display percentages on chart** لكل شريحة.

---

## الخطوة 5: **add data label percent** – عرض النسب المئوية على الشرائح

هذا هو الجزء الذي ينساه معظم المطورين: ضبط تسميات البيانات لعرض النسب المئوية. بدون ذلك، يعرض المخطط الأرقام الخام فقط، مما قد يكون غامضًا.

```java
        // Step 5: Enable percentage labels on the first series
        series.getDataLabel().setShowPercent(true);
```

استدعاء `setShowPercent(true)` يخبر Aspose.Words بعرض التسمية كـ “30 %”، “45 %”، إلخ. هذا هو بالضبط ما تحتاجه لتقوم بـ **show percent on pie chart** دون أي عمل تنسيق إضافي.

---

## الخطوة 6: حفظ المستند

أخيرًا، احفظ المستند على القرص. يمكنك اختيار `.docx`، `.pdf`، أو حتى `.html`. في هذا الدليل سنستخدم تنسيق `.docx` الحديث.

```java
        // Step 6: Save the result
        doc.save("PieChartDemo.docx");
    }
}
```

شغّل البرنامج، افتح `PieChartDemo.docx`، وسترى مخططًا دائريًا مُصممًا بدقة مع تسميات النسب المئوية على كل شريحة.

---

## النتيجة المتوقعة

في الأسفل لقطة شاشة للملف Word المُولد. لاحظ كيف تعرض كل شريحة حصتها كنسبة مئوية—بالضبط ما أردنا عندما ضبطنا **add data label percent**.

![Screenshot of a Word document containing a pie chart with percentage labels](/images/pie-chart-percent.png){.center width=600px alt="Screenshot showing how to insert pie chart in Word with percentage labels"}

*نص alt يتضمن الكلمة المفتاحية الأساسية، مما يلبي كلًا من تحسين محركات البحث وإمكانية الوصول.*

---

## الأسئلة الشائعة ومعالجة الحالات الخاصة

| Question | Answer |
|----------|--------|
| **هل يمكنني تغيير خط تسميات النسب المئوية؟** | نعم. بعد تمكين `setShowPercent(true)`، احصل على كائن `DataLabel` وقم بضبط خاصية `Font` الخاصة به (`dataLabel.getFont().setSize(10);`). |
| **ماذا لو احتجت إلى مخطط دونات بدلًا من المخطط الدائري؟** | استبدل `ChartType.PIE` بـ `ChartType.DOUGHNUT` في استدعاء `insertChart`. نفس منطق **add data label percent** يعمل. |
| **هل تعرض إصدارات Word القديمة (2007‑2010) النسب المئوية بشكل صحيح؟** | يقوم Aspose.Words بكتابة XML الأساسي بطريقة لا تعتمد على الإصدار، لذا تظهر النسب المئوية في أي نسخة Word تدعم المخططات (2007+). |
| **كيف يمكن إضافة عنوان للمخطط؟** | استخدم `pieChart.getTitle().setText("Market Share");` قبل الحفظ. |
| **هل يمكنني إدراج المخطط في فقرة أو خلية جدول محددة؟** | بالطبع. انقل `DocumentBuilder` إلى الموقع المطلوب (`builder.moveToParagraph(index, true);` أو `builder.moveToCell(table, row, column, true);`) قبل استدعاء `insertChart`. |

---

## نصائح وحيل من الميدان

- **نصيحة احترافية:** إذا كنت تخطط لإنشاء العديد من المخططات في حلقة، أعد استخدام نسخة واحدة من `DocumentBuilder`؛ فهذا يقلل من استهلاك الذاكرة.
- **احذر من:** الشرائح الصغيرة جدًا (< 2 %). قد يتجاهل Aspose.Words التسمية لتجنب الفوضى؛ يمكنك فرضها باستخدام `dataLabel.setShowLabel(true);`.
- **ملاحظة أداء:** رسم المخططات يستهلك الكثير من وحدة المعالجة المركزية. لتوليد تقارير ضخمة، فكر في تعدد الخيوط لكن تأكد من أن كل خيط يعمل على نسخة `Document` خاصة به.
- **تحقق من الإصدار:** تم تقديم الطريقة `setShowPercent` في Aspose.Words 22.8. إذا كنت تستخدم إصدارًا أقدم، قم بالترقية أو احسب النسب يدويًا وضعها كعناوين مخصصة.

---

## ملخص

لقد غطينا **how to insert pie chart** في مستند Word باستخدام Aspose.Words، وأظهرنا لك كيفية **add data label percent**، وبيّنّا أسهل طريقة لـ **display percentages on chart**. ببضع أسطر من Java يمكنك **add pie chart to word** و**show percent on pie chart**، مما يحول الأرقام الخام إلى رسومات قابلة للقراءة فورًا.

---

## ما التالي؟

- جرّب أنواع مخططات أخرى (`BAR`، `LINE`، `AREA`) وانظر كيف ينطبق نفس منطق **add data label percent**.
- اجمع المخططات مع الجداول للحصول على تقارير أكثر غنى—Aspose.Words يجعل من السهل وضع مخطط بجوار جدول البيانات.
- استكشف تصدير نفس المستند إلى PDF أو HTML لترى كيف تُعرض النسب المئوية عبر الصيغ.

لا تتردد في تعديل الأبعاد أو الألوان أو مصدر البيانات (مثل استعلام قاعدة بيانات) وشاهد تقارير Word تنبض بالحياة. إذا واجهت مشكلة، اترك تعليقًا أدناه—نتمنى لك رسمًا موفقًا!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}