---
category: general
date: 2026-09-11
description: كيفية تعيين الظل على مخطط Word باستخدام Aspose.Words للـ Java – تعلم
  تحميل مستند Word، تغيير الحدود، وتخصيص مظهر المخطط.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set shadow
- how to change border
- modify word chart
- load word document
- set chart border
language: ar
lastmod: 2026-09-11
og_description: كيفية تعيين الظل على مخطط Word باستخدام Aspose.Words للغة Java. اتبع
  هذا الدليل خطوة بخطوة لتحميل مستند Word، وتغيير الحدود، وتطبيق تأثير الظل.
og_image_alt: Screenshot of a Word chart with a gray border and a soft shadow applied
og_title: كيفية ضبط الظل على مخطط Word – دليل Java كامل
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: How to set shadow on a Word chart with Aspose.Words for Java – learn
    to load a Word document, change borders, and customize chart appearance.
  headline: How to set shadow on a Word chart with Aspose.Words for Java
  type: TechArticle
- description: How to set shadow on a Word chart with Aspose.Words for Java – learn
    to load a Word document, change borders, and customize chart appearance.
  name: How to set shadow on a Word chart with Aspose.Words for Java
  steps:
  - name: Expected result
    text: 'Open `output.docx` in Microsoft Word:'
  - name: What if the document contains multiple charts?
    text: 'The example retrieves the **first** chart. To modify all charts, iterate
      over the filtered list:'
  - name: Does the shadow work for all chart types?
    text: Yes. Aspose.Words applies the shadow at the chart container level, so bar,
      line, and pie charts all receive the effect. However, 3‑D charts may render
      the shadow slightly differently because of their built‑in lighting model.
  - name: How to set a custom shadow color?
    text: The API currently supports a simple on/off toggle (`setShadow(true)`). For
      more advanced shadow styling (color, blur, offset), you would need to convert
      the chart to an image and use a graphics library, which is beyond the scope
      of this tutorial.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: كيفية تعيين الظل على مخطط Word باستخدام Aspose.Words للـ Java
url: /ar/java/document-styling/how-to-set-shadow-on-a-word-chart-with-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إضافة ظل إلى مخطط Word باستخدام Aspose.Words for Java

إذا كنت بحاجة إلى **كيفية إضافة ظل إلى مخطط Word** بسرعة، فإن هذا الدليل يوضح لك الخطوات الدقيقة باستخدام Aspose.Words for Java. ستتعلم كيفية **تحميل مستند Word**، استرجاع المخطط الأول، ثم تطبيق كل من تأثير الظل وإطار مخصص.

تحسين النمط البصري للمخطط مفيد للتقارير، العروض التقديمية، أو خطوط أنابيب توليد المستندات الآلية. بنهاية هذا البرنامج التعليمي ستكون قادرًا على **تعديل كائنات مخطط Word**، تغيير لون الإطار الخاص بها، والإجابة على السؤال الشائع **كيفية تغيير الإطار** دون مغادرة كود Java الخاص بك.

## المتطلبات المسبقة وما ستقوم ببنائه

قبل أن تبدأ، تأكد من أن لديك:

* Java 17 (أو أي JDK حديث) مثبت.
* Maven أو Gradle لإدارة التبعيات.
* ترخيص Aspose.Words for Java (الإصدار التجريبي المجاني يعمل للتطوير).
* ملف Word تجريبي (`input.docx`) يحتوي على مخطط واحد على الأقل.

البرنامج النهائي سيفعل:

1. **تحميل مستند Word** (`load word document`).
2. استرجاع شكل المخطط الأول (`modify word chart`).
3. **تعيين إطار المخطط** إلى اللون الرمادي (`set chart border`).
4. تطبيق **تأثير الظل** (`how to set shadow`).
5. حفظ المستند المعدل باسم `output.docx`.

## الخطوة 1: إعداد المشروع وإضافة Aspose.Words

أنشئ مشروع Maven جديد (أو ما يعادله في Gradle) وأضف تبعية Aspose.Words:

```xml
<!-- pom.xml -->
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- use the latest version -->
    </dependency>
</dependencies>
```

> **نصيحة احترافية:** إذا كنت تستخدم Gradle، فإن المكافئ هو `implementation 'com.aspose:aspose-words:24.9'`.

## الخطوة 2: كيفية تحميل مستند Word واسترجاع المخطط

تحميل مستند هو سطر واحد من الكود، لكن فهم تسلسل العقد يساعد عندما تحتاج إلى **تعديل مخطط Word** لاحقًا.

```java
import com.aspose.words.*;

public class ChartShadowDemo {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Retrieve the first Shape that is a chart
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                                    .stream()
                                    .filter(node -> ((Shape) node).getShapeType() == ShapeType.CHART)
                                    .findFirst()
                                    .orElseThrow(() -> new IllegalArgumentException("No chart found"));
        
        // Cast the Shape to a Chart object
        Chart chart = chartShape.getChart();
```

*لماذا هذا مهم*: قد تحتوي مجموعة `NodeType.SHAPE` على صور، صناديق نصية، أو مخططات. الفلترة باستخدام `ShapeType.CHART` تضمن أنك تعمل مع مخطط، وهو أمر أساسي لـ **كيفية إضافة ظل** بشكل صحيح.

## الخطوة 3: كيفية إضافة ظل إلى مخطط Word

تُظهر Aspose.Words طريقة `setShadow(boolean)` في فئة `Chart`. تمكين الظل يمنح المخطط تأثير عمق خفيف.

```java
        // Enable a shadow effect for the chart
        chart.setShadow(true);
```

عند فتح المستند في Microsoft Word، سيظهر المخطط الآن ظلًا رماديًا ناعمًا حول محيطه. هذا هو الجواب الأساسي على **كيفية إضافة ظل** إلى مخطط.

## الخطوة 4: كيفية تغيير إطار مخطط Word

تغيير الإطار يتضمن خاصيتين:

* `setBorderColor(Color)` – يحدد اللون.
* `setBorderWidth(double)` – اختياري، يحدد السماكة (الافتراضي 0.5 pt).

```java
        // Apply a gray border color to the chart
        chart.setBorderColor(java.awt.Color.GRAY);
        // Optionally increase the border width for better visibility
        chart.setBorderWidth(1.0);
```

هذه الأسطر تجيب على **كيفية تغيير الإطار** وتلبي أيضًا متطلب كلمة **set chart border**. سيظهر الإطار حول كل شريحة من مخطط الفطيرة أو حول كامل مساحة المخطط للأعمدة.

## الخطوة 5: كيفية تفجير شرائح المخطط (تحسين بصري اختياري)

على الرغم من أنه ليس جزءًا من مجموعة الكلمات المفتاحية الأساسية، فإن تفجير الشرائح هو تحسين بصري شائع يتناغم جيدًا مع الظلال.

```java
        // Explode the chart slices by 10 %
        chart.setExplode(10);
```

## الخطوة 6: حفظ المستند المعدل

بعد جميع التخصيصات، اكتب المستند مرة أخرى إلى القرص.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

تشغيل البرنامج ينتج `output.docx` حيث يصبح المخطط الأول الآن يحتوي على إطار رمادي، انفجار بنسبة 10 %، وتأثير ظل.

### النتيجة المتوقعة

افتح `output.docx` في Microsoft Word:

* يعرض المخطط ظلًا ناعمًا على الجانب الأيمن.
* إطار رمادي رفيع يحيط بالمخطط.
* إذا أضفت خطوة التفجير، فإن الشرائح تكون منفصلة قليلاً.

![Word chart with shadow and gray border](https://example.com/placeholder-image.png){alt="مخطط Word مع ظل وإطار رمادي"}

## أسئلة شائعة ومعالجة الحالات الخاصة

### ماذا لو كان المستند يحتوي على مخططات متعددة؟

المثال يسترجع المخطط **الأول**. لتعديل جميع المخططات، قم بالتكرار عبر القائمة المصفاة:

```java
List<Shape> charts = doc.getChildNodes(NodeType.SHAPE, true).stream()
    .filter(node -> ((Shape) node).getShapeType() == ShapeType.CHART)
    .map(node -> (Shape) node)
    .collect(Collectors.toList());

for (Shape shape : charts) {
    Chart c = shape.getChart();
    c.setShadow(true);
    c.setBorderColor(java.awt.Color.GRAY);
}
```

### هل يعمل الظل مع جميع أنواع المخططات؟

نعم. تقوم Aspose.Words بتطبيق الظل على مستوى حاوية المخطط، لذا فإن مخططات الأعمدة، الخطوط، والفطيرة جميعها تتلقى التأثير. ومع ذلك، قد تعرض المخططات ثلاثية الأبعاد الظل بشكل مختلف قليلاً بسبب نموذج الإضاءة المدمج.

### كيفية تعيين لون ظل مخصص؟

حاليًا يدعم الـ API تبديلًا بسيطًا تشغيل/إيقاف (`setShadow(true)`). للحصول على تنسيق ظل أكثر تقدمًا (لون، تمويه، إزاحة)، ستحتاج إلى تحويل المخطط إلى صورة واستخدام مكتبة رسومات، وهو خارج نطاق هذا الدرس.

## نصائح احترافية لكود الإنتاج

* **تفعيل الترخيص مبكرًا** – استدعِ `License license = new License(); license.setLicense("Aspose.Words.lic");` قبل تحميل المستند لتجنب علامات التقييم المائية.
* **إعادة استخدام كائنات Document** – إذا كنت تعالج ملفات متعددة دفعة واحدة، أعد استخدام نسخة واحدة من `Document` لتقليل ضغط الـ GC.
* **التحقق من وجود المخطط** – احرص دائمًا على الحماية من `NoSuchElementException` عندما لا يحتوي المستند على مخطط؛ فهذا يمنع الأعطال أثناء التشغيل.
* **سلامة الخيوط** – كائنات Aspose.Words غير آمنة للاستخدام المتعدد الخيوط. أنشئ نسخة منفصلة من `Document` لكل خيط عند المعالجة المتوازية.

## الخلاصة

أنت الآن تعرف **كيفية إضافة ظل إلى مخطط Word** باستخدام Aspose.Words for Java، بالإضافة إلى كيفية **تغيير الإطار**، **تحميل مستند Word**، و**تعيين إطار المخطط**. باتباع الخطوات أعلاه يمكنك تحسين مظهر المخططات برمجيًا، مما يجعل التقارير الآلية تبدو مصقولة ومهنية.

هل أنت مستعد للتحدي التالي؟ استكشف **كيفية إضافة تسميات البيانات**، **تخصيص ألوان المخطط**، أو **تصدير المخططات إلى صور** – كلها ممكنة باستخدام نفس API الخاص بـ Aspose.Words. برمجة سعيدة!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء مخطط عمودي باستخدام Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [إنشاء مستند Word Java – إضافة شكل مستطيل مع تأثير الظل](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [كيفية تعيين LoadOptions في Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}