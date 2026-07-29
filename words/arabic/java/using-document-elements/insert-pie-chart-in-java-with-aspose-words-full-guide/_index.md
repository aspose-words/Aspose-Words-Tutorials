---
category: general
date: 2026-07-29
description: إدراج مخطط دائري باستخدام Aspose.Words للغة Java وتعلم كيفية إنشاء مخطط
  حلقي، تنسيق المخطط الدائري، تنسيق المخطط في Word، وتخصيص حجم المخطط.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- generate doughnut chart
- format pie chart
- format chart word
- customize chart size
language: ar
lastmod: 2026-07-29
og_description: أدرج مخططًا دائريًا باستخدام Aspose.Words for Java وتعلم بسرعة إنشاء
  مخطط حلقي، تنسيق المخطط الدائري، تنسيق مخطط Word، وتخصيص حجم المخطط للمستندات المهنية.
og_image_alt: Screenshot showing a Word document with an inserted pie chart created
  by Aspose.Words Java API
og_title: إدراج مخطط دائري في جافا – دليل Aspose.Words الكامل
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Insert pie chart using Aspose.Words for Java and learn how to generate
    doughnut chart, format pie chart, format chart Word, and customize chart size.
  headline: Insert pie chart in Java with Aspose.Words – Full Guide
  type: TechArticle
- questions:
  - answer: The evaluation version works fine for testing, but it adds a watermark.
      Drop your `aspose.words.lic` file in the classpath for a clean output.
    question: Do I need a license?
  - answer: 'Absolutely. Add the following dependency to your `pom.xml`:'
    question: Can I use this with Maven?
  - answer: Loop over `pieChart.getSeries()` and apply `setExplosion`, `setFillColor`,
      or other formatting per series. That’s the way to **format pie chart** for multi‑dimensional
      data.
    question: What if I have more than one series?
  - answer: Yes—once saved, you can open the document and manually adjust colors,
      fonts, or even convert the pie to a bar chart if you need to.
    question: Is the chart editable in Word after generation?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Chart
- Document Generation
- Word Automation
title: إدراج مخطط دائري في جافا باستخدام Aspose.Words – دليل كامل
url: /ar/java/using-document-elements/insert-pie-chart-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إدراج مخطط دائري في Java باستخدام Aspose.Words – دليل كامل

هل تساءلت يومًا كيف **insert pie chart** في مستند Word من خلال كود Java؟ لست وحدك—العديد من المطورين يواجهون هذه العقبة عندما يحتاجون إلى طريقة سريعة برمجية لتصوير البيانات. الخبر السار؟ باستخدام Aspose.Words for Java يمكنك القيام بذلك في بضع أسطر فقط، وخلال ذلك يمكنك أيضًا **generate doughnut chart**، **format pie chart**، **format chart Word**، و **customize chart size** لتتناسب مع علامتك التجارية.

في هذا الدرس سنستعرض مثالًا واقعيًا يبدأ بإنشاء مستند فارغ، وإدراج مخطط دائري، وتعديل بعض الخصائص البصرية، وأخيرًا حفظ الملف. في النهاية ستحصل على قطعة شفرة قابلة لإعادة الاستخدام يمكنك لصقها في أي مشروع Java يحتاج إلى أتمتة المخططات. لا مكتبات إضافية، ولا تعديل يدوي مع Office interop—فقط Java نظيفة ومُجمَّعة.

## ما ستحتاجه

- **Java 17** (أو أي JDK حديث؛ الـ API متوافق مع الإصدارات السابقة)
- **Aspose.Words for Java** 22.12 أو أحدث – يمكنك الحصول على حزمة Maven أو ملف .jar من موقع Aspose.
- بيئة تطوير متوسطة (IntelliJ IDEA، Eclipse، VS Code…) – أي شيء يتيح لك تشغيل طريقة `main`.
- اختياري: ملف ترخيص إذا كنت لا تريد علامة التقييم المائية.

إذا كان لديك هذه المتطلبات، يمكننا القفز مباشرة إلى الكود.

## الخطوة 1: إدراج مخطط دائري باستخدام Aspose.Words

أول شيء نقوم به هو **insert pie chart** في مستند جديد. هذه الخطوة تمهيدية لكل ما يلي، لأن كائن المخطط يتيح لنا الوصول إلى السلاسل، ونقاط البيانات، وتعديلات بصرية.

```java
import com.aspose.words.*;

public class PieChartFormatting {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with a specific size (500x400 points)
        Chart pieChart = builder.insertChart(ChartType.PIE, 500, 400);
```

> **Why this matters:** `DocumentBuilder.insertChart` لا يخلق المخطط فقط بل يعيد كائن `Chart` يمكننا التلاعب به. تسمح لك معلمات العرض والارتفاع **customize chart size** عند الإنشاء، لذا لا تحتاج إلى تعديل الحجم لاحقًا.

## الخطوة 2: إنشاء مخطط حلقي (اختياري)

إذا كان تصميمك يتطلب وجود ثقب في الوسط—فكر في مخطط حلقي كلاسيكي—Aspose يجعل ذلك سطرًا واحدًا. يمكن تحويل نفس كائن `Chart` من مخطط دائري عادي إلى حلقي عن طريق تعديل حجم الثقب.

```java
        // Optional: Turn the pie into a doughnut by setting the hole size (0‑100%)
        pieChart.getChartData().setHoleSize(30); // 30% hole makes it a doughnut chart
```

> **Tip:** حجم الثقب لا يؤثر إلا على `ChartType.DONUT`. إذا أبقيت النوع كـ `PIE`، سيتم تجاهل النداء، لذا لا تتردد في التجربة.

## الخطوة 3: تنسيق شرائح المخطط الدائري

غالبًا ما يبرز التصور الجيد شريحة معينة. هنا نقوم **format pie chart** عن طريق انفجار الشريحة الأولى بمقدار 20 نقطة إلى الخارج. هذا يجذب انتباه القارئ إلى أهم نقطة بيانات.

```java
        // Explode the first slice to emphasize it
        pieChart.getSeries().get(0).setExplosion(20);
```

> **Pro tip:** يمكنك التكرار عبر `pieChart.getSeries()` إذا كان لديك عدة سلاسل وتعيين ألوان، حدود، أو تسميات بيانات فردية. هذه هي الطريقة لـ **format chart Word** المستندات مع تنسيق غني.

## الخطوة 4: إضافة بيانات إلى المخطط

المخطط بدون بيانات هو مجرد شكل زخرفي. لنزوده بمجموعة بيانات بسيطة—مثلاً أرقام المبيعات ربع السنوية.

```java
        // Populate the chart with sample data
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataLabels().setShowCategoryName(true);
        series.getDataLabels().setShowValue(true);

        // Clear any default points and add our own
        series.getPoints().clear();
        series.getPoints().add(new ChartPoint(30)); // Q1
        series.getPoints().add(new ChartPoint(45)); // Q2
        series.getPoints().add(new ChartPoint(15)); // Q3
        series.getPoints().add(new ChartPoint(10)); // Q4
```

> **Why we do this:** بإضافة كائنات `ChartPoint` صراحةً نضمن أن يعكس المخطط منطق أعمالنا. استدعاءات `setShowCategoryName` و `setShowValue` هي جزء من **formatting the pie chart** لعرض كل من التسميات والأرقام.

## الخطوة 5: ضبط المظهر بدقة (customize chart size & style)

إلى جانب الأبعاد الأولية، قد ترغب في تعديل وسيلة إيضاح المخطط، العنوان، أو حتى الخط المستخدم لتسميات البيانات. كل ذلك يندرج تحت **customize chart size** والتنسيق العام.

```java
        // Set a title for the chart
        ChartTitle title = pieChart.getTitle();
        title.setText("Quarterly Sales Distribution");
        title.getFont().setSize(14);
        title.getFont().setBold(true);

        // Move the legend to the right side
        ChartLegend legend = pieChart.getLegend();
        legend.setPosition(LegendPosition.RIGHT);
        legend.getFont().setSize(10);

        // Adjust the overall chart size again if needed
        pieChart.setWidth(600);   // width in points
        pieChart.setHeight(450);  // height in points
```

> **Edge case:** إذا قررت لاحقًا تصدير المستند إلى PDF، تبقى بيانات المخطط المتجهة واضحة لأن الحجم معرف بالنقاط وليس بالبكسل. هذا فوز لـ **format chart Word** وللصيغ اللاحقة.

## الخطوة 6: حفظ وعرض المستند

الخطوة الأخيرة بسيطة مثل استدعاء `doc.save`. هذا يكتب ملف `.docx` يمكنك فتحه في Microsoft Word، LibreOffice، أو أي عارض يدعم صيغة OpenXML.

```java
        // Save the document containing the formatted chart
        doc.save("YOUR_DIRECTORY/PieChart.docx");
    }
}
```

> **Result:** افتح `PieChart.docx` وسترى مخططًا دائريًا (أو حلقيًا) بحجم مناسب مع شريحة منفجرة، عنوان، ووسيلة إيضاح—كل ذلك تم توليده دون الحاجة إلى الواجهة الرسومية.

### النتيجة المتوقعة

| العنصر | ما ستراه |
|--------|----------|
| نوع المخطط | مخطط دائري (أو حلقي إذا كان `holeSize` > 0) |
| انفجار الشريحة | الشريحة الأولى متباعدة 20 نقطة |
| وسيلة الإيضاح | موجودة على اليمين |
| العنوان | “Quarterly Sales Distribution” بخط عريض 14 نقطة |
| تسميات البيانات | اسم الفئة والقيمة معروضان على كل شريحة |
| المستند | ملف Word `.docx` قياسي جاهز للمشاركة |

## أسئلة شائعة ومشكلات محتملة

- **هل أحتاج إلى ترخيص؟**  
  الإصدار التجريبي يعمل جيدًا للاختبار، لكنه يضيف علامة مائية. ضع ملف `aspose.words.lic` في مسار الـ classpath للحصول على مخرجات نظيفة.

- **هل يمكنني استخدام هذا مع Maven؟**  
  بالطبع. أضف الاعتماد التالي إلى ملف `pom.xml` الخاص بك:

  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>22.12</version>
  </dependency>
  ```

- **ماذا لو كان لدي أكثر من سلسلة واحدة؟**  
  قم بالتكرار عبر `pieChart.getSeries()` وتطبيق `setExplosion`، `setFillColor`، أو تنسيقات أخرى لكل سلسلة. هذه هي الطريقة لـ **format pie chart** للبيانات متعددة الأبعاد.

- **هل يمكن تعديل المخطط في Word بعد الإنشاء؟**  
  نعم—بعد الحفظ، يمكنك فتح المستند وتعديل الألوان، الخطوط، أو حتى تحويل المخطط الدائري إلى مخطط شريطي إذا احتجت.

## الخلاصة

لقد **inserted pie chart** للتو في مستند Word باستخدام Aspose.Words for Java، وأظهرنا كيفية **generate doughnut chart**، وقدمنا عدة طرق لـ **format pie chart**، وتناولنا أفضل ممارسات **format chart Word**، وتعلمنا كيفية **customize chart size** للحصول على مظهر مصقول. المثال الكامل القابل للتنفيذ أعلاه يمكن إدراجه في أي مشروع Java، مما يمنحك أتمتة مخططات فورية دون عبء COM interop أو تثبيت Office.

ما الخطوة التالية؟ جرّب استبدال مصدر البيانات بقاعدة بيانات حية، أضف ألوانًا شرطية بناءً على العتبات، أو صدّر نفس المستند إلى PDF لتقرير جاهز للطباعة. كل من هذه الخطوات يبني على الأساس الذي وضعناه، لذا ستجد الانتقال سلسًا.

إذا واجهت أي مشاكل أو كان لديك أفكار لتحسينات إضافية—ربما مخطط شريطي مكدس أو مخطط خطي—اترك تعليقًا أدناه. نتمنى لك رسم مخططات سعيد!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء مخطط عمودي باستخدام Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [تنسيق عدد تسميات البيانات في مخطط](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [تنسيق الأرقام للمحور في مخطط](/words/english/net/programming-with-charts/number-format-for-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}