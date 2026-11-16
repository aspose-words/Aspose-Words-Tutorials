---
category: general
date: 2026-11-15
description: تعلم كيفية إنشاء مخطط دائري في مستند Word وحفظ ملف docx كملف PDF باستخدام
  Java. يغطي هذا الدليل أيضًا تحويل Word إلى PDF وكيفية إضافة المخطط.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save docx as pdf
- convert word to pdf
- how to add chart
- how to create chart
language: ar
lastmod: 2026-11-15
og_description: إنشاء مخطط دائري في ملف Word وحفظ ملف docx كـ PDF باستخدام Java. اتبع
  هذا الدليل خطوة بخطوة لتحويل Word إلى PDF وإضافة المخططات.
og_image_alt: Screenshot showing a pie chart created in a Word document
og_title: إنشاء مخطط دائري في Word وحفظ ملف docx كملف PDF – دليل Java
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to create pie chart in a Word document and save docx as PDF
    using Java. This guide also covers convert word to pdf and how to add chart.
  headline: How to create pie chart in Word and save docx as PDF
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- PDF
title: كيفية إنشاء مخطط دائري في Word وحفظ ملف docx كملف PDF
url: /ar/java/document-conversion-and-export/how-to-create-pie-chart-in-word-and-save-docx-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مخطط دائري في Word وحفظ ملف docx كـ PDF

إذا كنت بحاجة إلى **إنشاء مخطط دائري** داخل مستند Word ثم **حفظ ملف docx كـ PDF**، فإن هذا الدرس يوضح لك بالضبط كيفية القيام بذلك. سترى مثالًا كاملاً قابلاً للتنفيذ يحول ملف .docx إلى PDF مع تضمين مخطط دائري، بحيث يمكنك الإجابة على سؤال “كيفية إضافة مخطط” دون البحث عن شظايا متناثرة.

في هذا الدليل ستتعلم:

* تحميل ملف *.docx* موجود (أو البدء من الصفر)  
* استخدام Aspose.Words for Java لإنشاء **مخطط دائري** وتعبئة البيانات  
* **حفظ ملف docx كـ PDF** مع عرض المخطط بشكل صحيح  
* فهم تفاصيل **تحويل Word إلى PDF** عندما تكون المخططات متضمنة  

تعمل الخطوات مع Aspose.Words 2024‑x.x و Java 17، لكن المفاهيم تنطبق على أي مكتبة تدعم معالجة مخططات Word.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من أن لديك:

| المتطلب | لماذا يهم |
|-------------|----------------|
| Java 17 (أو أحدث) | مطلوب من قبل أحدث ملف JAR لـ Aspose.Words |
| أداة بناء Maven أو Gradle | تبسط إدارة التبعيات |
| Aspose.Words for Java (أحدث نسخة) | يوفر الفئات `Document` و `Chart` و `ChartType` |
| ملف **.docx** إدخال (أو مستند فارغ) | سيتم إدراج المخطط في هذا الملف |

أضف تبعية Aspose.Words إلى ملف `pom.xml` (Maven) أو `build.gradle` (Gradle). مثال لـ Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## الخطوة 1: تحميل مستند Word (أو إنشاء مستند جديد)

الإجراء الأول هو الحصول على نسخة من `Document`. إذا كان لديك قالب مسبقًا، مرّر مساره؛ وإلا أنشئ مستندًا فارغًا.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Load an existing .docx or create a new blank document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // If you prefer a new file, uncomment the next line:
        // Document doc = new Document();
```

*لماذا هذه الخطوة؟* كائن `Document` هو الحاوية لجميع محتويات Word، بما في ذلك المخططات. تحميل ملف موجود يتيح لك الحفاظ على النصوص والأنماط المحيطة أثناء إضافة عنصر بصري جديد.

## الخطوة 2: **إنشاء مخطط دائري** – جوهر “كيفية إنشاء مخطط”

الآن نقوم بإنشاء كائن `Chart` باستخدام `ChartType.PIE`. هذا ينشئ تلقائيًا عنصرًا نائبًا لمخطط دائري يمكنك ملؤه لاحقًا بالبيانات.

```java
        // Step 2: Insert a pie chart into the document
        Chart chart = new Chart(doc, ChartType.PIE);
        // Place the chart at the end of the document body
        doc.getFirstSection().getBody().appendChild(chart);
```

*شرح*: `ChartType.PIE` يخبر Aspose.Words باستخدام قالب مخطط دائري. يُضاف المخطط إلى جسم المستند، لذا سيظهر في المكان الذي تحتاجه. هذا يلبي متطلب “كيفية إضافة مخطط” في استدعاء واحد.

## الخطوة 3: تعبئة المخطط – الإجابة على “كيفية إضافة مخطط” بالبيانات

المخطط الدائري لا معنى له بدون بيانات السلسلة. استخدم مجموعة `Series` لإضافة الفئات والقيم.

```java
        // Step 3: Populate the chart with sample data
        chart.getSeries().add("Category A", 40);
        chart.getSeries().add("Category B", 30);
        chart.getSeries().add("Category C", 30);
```

*لماذا هذا مهم*: كل استدعاء لـ `add` ينشئ شريحة من الدائرة. الوسيط الأول هو التسمية، والوسيط الثاني هو القيمة الرقمية. يمكنك استبدالهما ببيانات ديناميكية من قاعدة بيانات أو ملف CSV.

### اختياري: تخصيص المظهر (ليس مطلوبًا لكن مفيد)

```java
        // Set a title for the chart
        chart.setTitle("Sales Distribution Q1");
        // Change the legend position
        chart.getLegend().setPosition(LegendPosition.RIGHT);
```

هذه التعديلات توضح كيف يمكنك **إنشاء مخطط** بمظهر احترافي، دون مغادرة كود Java.

## الخطوة 4: **حفظ ملف docx كـ PDF** – الجزء النهائي من “تحويل Word إلى PDF”

بعد تضمين المخطط، قم بتصدير المستند إلى PDF. Aspose.Words يرسم المخطط كرسمة متجهة، مما يحافظ على الجودة.

```java
        // Step 4: Save the document as PDF – the chart will be rendered with graduations
        doc.save("YOUR_DIRECTORY/output.pdf", SaveFormat.PDF);
    }
}
```

*نقطة أساسية*: طريقة `save` تقوم تلقائيًا بتحويل ملف Word إلى PDF، مع معالجة تصيير المخطط، تضمين الخطوط، وتخطيط الصفحات. هذا يحقق هدف **حفظ ملف docx كـ PDF** ويظهر طريقة موثوقة لـ **تحويل Word إلى PDF** عندما تكون المخططات موجودة.

### النتيجة المتوقعة

تشغيل البرنامج ينتج ملف `output.pdf` يحتوي على:

* المحتوى الأصلي لـ `input.docx` (إن وجد)  
* مخطط دائري مُظهر بالكامل بعنوان *Sales Distribution Q1*  
* نسب الشرائح الدقيقة المتطابقة مع البيانات (40 ٪، 30 ٪، 30 ٪)

افتح ملف PDF في أي عارض ويجب أن ترى مخططًا دائريًا واضحًا، مماثلًا لما تراه في ملف Word.

## المشكلات الشائعة وكيفية تجنّبها

| المشكلة | السبب | الحل |
|-------|-------|-----|
| المخطط يظهر فارغًا في PDF | إعدادات الخط أو عرض المخطط مفقودة | تأكد من أنك تستخدم أحدث نسخة من Aspose.Words؛ فهي تتضمن مكتبات العرض المطلوبة. |
| قيم البيانات تُقرب بشكل غير صحيح | استخدام قيم صحيحة (integer) مع أعداد كبيرة | قدم قيم `double` أو قم بتحجيم الأعداد قبل إضافتها إلى السلسلة. |
| حجم ملف PDF الناتج كبير | الصور مدمجة بدقة DPI عالية | اضبط `PdfSaveOptions.setImageCompressionLevel(CompressionLevel.MAXIMUM)` إذا كنت تدمج صورًا أيضًا. |
| “convert word to pdf” يطرح استثناء `UnsupportedOperationException` | استخدام نسخة Java أقدم (< 11) | قم بالترقية إلى Java 17 أو أحدث، حيث يتطلب ذلك Aspose.Words 24.x. |

## نصيحة احترافية: إعادة استخدام منطق إنشاء المخطط

إذا كنت بحاجة لإضافة مخططات متعددة إلى نفس المستند، استخرج كود بناء المخطط إلى طريقة مساعدة:

```java
private static Chart createPieChart(Document doc, Map<String, Double> data, String title) {
    Chart chart = new Chart(doc, ChartType.PIE);
    data.forEach(chart.getSeries()::add);
    chart.setTitle(title);
    return chart;
}
```

الآن يمكنك استدعاء `doc.getFirstSection().getBody().appendChild(createPieChart(...));` لكل مجموعة بيانات، مما يحافظ على كتابة كودك وفق مبدأ DRY (Don’t Repeat Yourself).

## الخلاصة

أنت الآن تعرف **كيفية إنشاء مخطط دائري** داخل مستند Word، تعبئته بالبيانات، و**حفظ ملف docx كـ PDF** باستخدام Java. يغطي هذا المثال المتكامل سير عمل **تحويل Word إلى PDF** بالكامل، يجيب على **كيفية إضافة مخطط**، ويظهر **كيفية إنشاء مخطط** برمجيًا.

من هنا قد ترغب في استكشاف:

* إضافة مخططات شريطية أو خطية (`ChartType.BAR`, `ChartType.LINE`) – سيناريو آخر لـ **how to create chart**.  
* التصدير إلى صيغ أخرى مثل PNG أو HTML (`SaveFormat.PNG`, `SaveFormat.HTML`).  
* إنشاء المستند الإدخالي ديناميكيًا باستخدام جداول أو عناصر نائبة قبل إدراج المخططات.

لا تتردد في تجربة مجموعات بيانات مختلفة، خيارات تنسيق، أو حتى تضمين مخططات متعددة في صفحة واحدة. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إدراج مخطط دائري في مستند Word باستخدام Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [كيفية حفظ Word كـ PDF وإنشاء PDF قابل للوصول في Java](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-docx-in-java-full-guide/)
- [كيفية إنشاء مخطط في Word باستخدام Java و Aspose.Words](/words/english/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}