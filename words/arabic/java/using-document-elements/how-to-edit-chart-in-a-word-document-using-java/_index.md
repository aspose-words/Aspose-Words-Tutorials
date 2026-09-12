---
category: general
date: 2026-09-11
description: كيفية تعديل المخطط في مستند Word باستخدام Java – تعلم كيفية تحديث إعدادات
  المخطط، تمكين خطوط الشبكة للمخطط، تغيير خيارات المخطط، وحفظ المستند المحدث.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- update chart settings
- save updated document
- change chart options
- enable chart gridlines
language: ar
lastmod: 2026-09-11
og_description: كيفية تعديل المخطط في مستند Word باستخدام Java. اتبع هذا الدليل لتحديث
  إعدادات المخطط، وتمكين خطوط الشبكة للمخطط، وتغيير خيارات المخطط، وحفظ المستند المحدث.
og_image_alt: Screenshot of a Word document showing a chart with gridlines enabled
og_title: كيفية تعديل المخطط في مستند Word باستخدام Java – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  headline: How to edit chart in a Word document using Java
  type: TechArticle
- description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  name: How to edit chart in a Word document using Java
  steps:
  - name: Expected result
    text: 'When you open `output.docx`:'
  - name: What if the document has no chart?
    text: 'Attempting to cast a non‑chart shape will throw a `ClassCastException`.
      Guard against this by checking the shape type:'
  - name: How to edit a specific chart instead of the first one?
    text: 'Iterate through `shapes` and match a known title or an alternative identifier:'
  - name: Can I disable gridlines again later?
    text: 'Yes, simply set the property to `false`:'
  - name: Does this work with `.doc` (binary) files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. However, some newer chart features (like graduations) are only
      stored in the OOXML format, so you’ll see the effect only when saving as `.docx`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart manipulation
title: كيفية تعديل المخطط في مستند Word باستخدام Java
url: /ar/java/using-document-elements/how-to-edit-chart-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تعديل المخطط في مستند Word باستخدام Java

إذا كنت بحاجة إلى **كيفية تعديل المخطط** في ملف Word، فإن هذا الدليل يوضح لك الخطوات الدقيقة. ستتعلم كيفية تحديث إعدادات المخطط، تمكين خطوط الشبكة للمخطط، تغيير خيارات المخطط، وأخيرًا **حفظ المستند المحدث** دون فقدان أي تنسيق.

العمل مع المخططات برمجيًا غالبًا ما يشعر وكأنه عملية صندوق أسود، خاصة عندما تريد تعديل التفاصيل البصرية مثل التدرجات أو خطوط الشبكة. يغطي هذا الشرح كل ما تحتاج معرفته، من تحميل المستند إلى حفظ التغييرات. لا تحتاج إلى أدوات خارجية—فقط مكتبة Aspose.Words for Java (الإصدار 24.9 أو أحدث).

بنهاية هذه المقالة ستكون قادرًا على:

* تحميل ملف `.docx` يحتوي على مخطط.
* تحديد شكل المخطط وتعديل خصائصه.
* تمكين خطوط الشبكة للمخطط (التدرجات) وضبط خيارات أخرى.
* **حفظ المستند المحدث** إلى ملف جديد.

## المتطلبات المسبقة

* Java 17 أو أحدث مثبت على جهازك.  
* Maven أو Gradle لإدارة الاعتمادات.  
* Aspose.Words for Java 24.9+ (الإصدار الذي قدم `setShowGraduations`).  
* مستند Word (`input.docx`) يحتوي بالفعل على مخطط واحد على الأقل.

إذا لم تكن familiar مع Aspose.Words، فكر فيه كـ API متكامل يتيح لك قراءة، تعديل، وكتابة مستندات Word برمجيًا—مشابه للطريقة التي تتعامل بها مع DOM في متصفح الويب.

## الخطوة 1: إعداد المشروع واستيراد المكتبة

أنشئ مشروع Maven جديد أو أضف الاعتماد إلى مشروع موجود:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

> **نصيحة محترف:** استخدم أحدث إصدار ثابت لضمان توفر طريقة `setShowGraduations`. الإصدارات القديمة لن تُترجم.

## الخطوة 2: تحميل مستند Word الذي يحتوي على مخطط

الإجراء الأول في أي سير عمل **كيفية تعديل المخطط** هو تحميل الملف المصدر. تمثل Aspose.Words المستند بالكامل باستخدام الفئة `Document`.

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // Replace with the actual path to your input file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document into memory
        Document doc = new Document(inputPath);
```

كائن `Document` يمنحك الوصول إلى كل عقدة داخل الملف، بما في ذلك الأشكال، الجداول، والفقرات.

## الخطوة 3: تحديد أول شكل مخطط في المستند

يتم تخزين المخططات كعقد `Shape` يكون المُعالج الخاص بها هو `Chart`. لتعديل مخطط يجب أولاً استرجاع تلك العقدة.

```java
        // Find all shape nodes (including charts)
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);

        // Assume the first shape is a chart; adjust the index if needed
        Shape chartShape = (Shape) shapes.get(0);

        // Cast the shape renderer to Chart
        Chart chart = (Chart) chartShape.getChart();
```

إذا كان المستند يحتوي على مخططات متعددة، قم بالتكرار عبر `shapes` وتحقق من `chartShape.getChart() != null` قبل التحويل. هذا يمنع حدوث `ClassCastException` ويضمن أنك **تغير خيارات المخطط** فقط على كائنات مخطط صالحة.

## الخطوة 4: تمكين خطوط الشبكة للمخطط (التدرجات) – خاصية جديدة في الإصدار 24.9

الخاصية `setShowGraduations` تتحكم في إظهار خطوط الشبكة الصغرى على محور القيم. تمكينها غالبًا ما يحسن قابلية القراءة لمجموعات البيانات الكثيفة.

```java
        // Turn on gridlines (graduations) for the value axis
        chart.setShowGraduations(true);
```

> **لماذا هذا مهم:** خطوط الشبكة تعطي المشاهد مرجعًا بصريًا لكل نقطة بيانات، مما يجعل التعرف على الاتجاهات أسهل. القيمة الافتراضية هي `false`، لذا يجب تمكينها صراحةً عند الحاجة.

يمكنك أيضًا تخصيص جوانب أخرى، مثل خطوط الشبكة الكبرى، عناوين المحاور، أو موضع الأسطورة. أدناه مثال لتغيير عنوان المخطط وموقع الأسطورة—كلاهما جزء من **تغيير خيارات المخطط**.

```java
        // Change the chart title
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);

        // Move the legend to the bottom
        chart.getLegend().setPosition(LegendPosition.BOTTOM);
```

## الخطوة 5: حفظ المستند مع إعدادات المخطط المحدثة

بعد تعديل المخطط، احفظ التغييرات. هذه الخطوة تكمل مرحلة **حفظ المستند المحدث**.

```java
        // Replace with the desired output path
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // Save the modified document
        doc.save(outputPath);
        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

تشغيل البرنامج سينتج `output.docx` حيث يعرض المخطط الآن خطوط شبكة، عنوانًا جديدًا، وأسطورةً تم نقلها. افتح الملف في Microsoft Word للتحقق من التغييرات البصرية.

## الشيفرة الكاملة (قابلة للتنفيذ)

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the Word document that contains a chart
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Locate the first chart shape in the document
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
        Shape chartShape = (Shape) shapes.get(0);
        Chart chart = (Chart) chartShape.getChart();

        // 3️⃣ Enable chart gridlines (graduations)
        chart.setShowGraduations(true);

        // 4️⃣ Change chart options (title and legend)
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);
        chart.getLegend().setPosition(LegendPosition.BOTTOM);

        // 5️⃣ Save the document with the updated chart settings
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

### النتيجة المتوقعة

عند فتح `output.docx`:

* يعرض المخطط خطوط شبكة صغرى على محور القيم.  
* العنوان هو **“Sales Overview 2026”**.  
* تظهر الأسطورة في أسفل المخطط.

إذا كان المخطط الأصلي يحتوي بالفعل على خطوط شبكة، فإن المظهر البصري يبقى دون تغيير، مما يؤكد أن الشيفرة **متطابقة**.

## الأسئلة الشائعة ومعالجة الحالات الخاصة

### ماذا لو لم يحتوي المستند على مخطط؟

محاولة تحويل شكل غير مخطط ستؤدي إلى رمي `ClassCastException`. احمِ نفسك من ذلك بالتحقق من نوع الشكل:

```java
if (chartShape.getShapeType() == ShapeType.CHART) {
    Chart chart = (Chart) chartShape.getChart();
    // proceed with modifications
}
```

### كيف أعدل مخططًا محددًا بدلاً من أول مخطط؟

قم بالتكرار عبر `shapes` وتطابق عنوانًا معروفًا أو معرفًا بديلًا:

```java
for (Node node : shapes) {
    Shape shape = (Shape) node;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart c = (Chart) shape.getChart();
        if ("Revenue Q1".equals(c.getTitle().getText())) {
            // modify this chart
        }
    }
}
```

### هل يمكنني تعطيل خطوط الشبكة مرة أخرى لاحقًا؟

نعم، ببساطة عيّن الخاصية إلى `false`:

```java
chart.setShowGraduations(false);
```

### هل يعمل هذا مع ملفات `.doc` (ثنائية)؟

Aspose.Words يج abstracts تنسيق الملف، لذا تعمل الشيفرة نفسها مع `.doc` و `.docx`. ومع ذلك، بعض ميزات المخطط الأحدث (مثل التدرجات) تُخزن فقط في تنسيق OOXML، لذا ستظهر التأثيرات فقط عند الحفظ كـ `.docx`.

## نصائح لكتابة كود جاهز للإنتاج

* **تحقق من مسارات الإدخال** – استخدم `Files.exists(Paths.get(inputPath))` قبل التحميل.  
* **غلف استدعاءات API** بكتل try‑catch لعرض تفاصيل `Exception`، خاصة عند التعامل مع مستندات تالفة.  
* **تحرير الموارد** – رغم أن Aspose.Words يدير الذاكرة، فإن استدعاء `doc.close()` (أو استخدام try‑with‑resources إذا كان متاحًا) يمكن أن يحرر المقابض الأصلية أسرع.  
* **التحقق من الإصدار** – تأكد من أن نسخة المكتبة في وقت التشغيل ≥ 24.9 قبل استدعاء `setShowGraduations`. يمكنك الاستعلام عن `License.getVersion()` إذا احتجت إلى حماية برمجية.

## الخلاصة

أنت الآن تعرف **كيفية تعديل المخططات** في مستند Word باستخدام Java. العملية—تحميل المستند، تحديد المخطط، تمكين خطوط الشبكة للمخطط، تغيير خيارات المخطط، و**حفظ المستند المحدث**—تغطي أكثر السيناريوهات شيوعًا لتعديل المخططات برمجيًا.  

من هنا يمكنك استكشاف تخصيصات إضافية مثل تغيير ألوان سلاسل البيانات، تطبيق أنماط المخطط، أو تصدير المخطط كصورة. كل هذه المهام تتبع نفس النمط: استرجاع كائن `Chart`، تعديل خصائصه، و**حفظ المستند المحدث**.

برمجة سعيدة، ولا تتردد في تجربة إعدادات مخطط أخرى لتناسب احتياجات تقاريرك!

## ما الذي ينبغي أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء مخطط عمودي باستخدام Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [كيفية حفظ المستند كملف PDF باستخدام Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [تعيين الخيارات الافتراضية لتسميات البيانات في المخطط](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}