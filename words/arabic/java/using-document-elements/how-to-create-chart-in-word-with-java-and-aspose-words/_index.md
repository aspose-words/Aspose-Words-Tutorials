---
category: general
date: 2026-09-24
description: تعلم كيفية إنشاء مخطط في Word باستخدام Java، وإدراج مخطط قطري، وحفظ المستند
  بصيغة docx باستخدام Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create chart in word
- save document as docx
- add chart to word
- create word document java
- insert radial chart
language: ar
lastmod: 2026-09-24
og_description: إنشاء مخطط في Word باستخدام Java و Aspose.Words. يوضح هذا البرنامج
  التعليمي كيفية إضافة مخطط شعاعي، تخصيص البيانات، وحفظ المستند بصيغة docx.
og_image_alt: Radial chart inserted in a Word document using Java code
og_title: إنشاء مخطط في Word باستخدام Java – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  headline: How to create chart in Word with Java and Aspose.Words
  type: TechArticle
- description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  name: How to create chart in Word with Java and Aspose.Words
  steps:
  - name: You should see a single page with a centered radial chart.
    text: You should see a single page with a centered radial chart.
  - name: If you added series data, the chart displays four slices labeled Q1‑Q4.
    text: If you added series data, the chart displays four slices labeled Q1‑Q4.
  - name: Right‑click the chart → **Edit Data** to confirm the underlying data table.
    text: Right‑click the chart → **Edit Data** to confirm the underlying data table.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Chart
- DOCX
title: كيفية إنشاء مخطط في Word باستخدام Java و Aspose.Words
url: /ar/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مخطط في Word باستخدام Java و Aspose.Words

إذا كنت بحاجة إلى **إنشاء مخطط في Word** من تطبيق Java، فإن هذا الدليل يوضح لك العملية بالكامل. ستتعرف على كيفية إضافة مخطط قطري، وإمكانية تعبئة سلسلة البيانات الخاصة به، وأخيرًا **حفظ المستند كملف docx** باستخدام مكتبة Aspose.Words for Java.

إنشاء بيانات مرئية داخل ملف Word هو طلب شائع للتقارير، الفواتير، أو توليد المستندات تلقائيًا. بنهاية هذا الدرس ستتمكن من **إنشاء مستند Word باستخدام Java** لمشاريع **إضافة مخطط إلى ملفات Word** دون أي تعديل يدوي.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* مجموعة تطوير جافا (JDK) 8 أو أحدث.
* Maven أو Gradle لإدارة الاعتمادات.
* بيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse أو VS Code.
* ترخيص صالح لـ Aspose.Words for Java (الإصدار التجريبي المجاني يكفي للتطوير).

توفر هذه الأدوات الأساس لأمثلة الشيفرة التي ستظهر لاحقًا.

## الخطوة 1: إعداد مشروع Maven

أنشئ مشروع Maven جديد (أو حدّث مشروعًا موجودًا) وأضف اعتماد Aspose.Words إلى ملف `pom.xml` الخاص بك:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word‑chart‑demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

تشغيل الأمر `mvn clean install` يقوم بتحميل المكتبة ويجعل الفئات مثل `Document` و `DocumentBuilder` و `ChartType` متاحة في مسار الفئة.

> **نصيحة احترافية:** حافظ على تحديث نسخة المكتبة. الإصدارات الجديدة تضيف أنواع مخططات وتحسن أداء العرض.

## الخطوة 2: إنشاء مستند Word جديد

الخطوة البرمجية الأولى لـ **إنشاء مخطط في Word** هي إنشاء كائن `Document` فارغ. هذا الكائن يمثل حزمة `.docx` بالكامل.

```java
import com.aspose.words.*;

public class RadialChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a blank Word document
        Document doc = new Document();

        // Step 2.2: Obtain a DocumentBuilder to insert content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

يعمل `DocumentBuilder` كالمؤشر؛ فهو يعرف نقطة الإدراج الحالية ويوفر طرقًا لإضافة نصوص، جداول، ومخططات. في هذه المرحلة تكون قد **أنشأت مستند Word باستخدام Java** – لوحة نظيفة جاهزة للمحتوى.

## الخطوة 3: إدراج مخطط قطري

يدعم Aspose.Words العديد من أنواع المخططات. لإ **إدراج مخطط قطري**، استدعِ `insertChart` مع `ChartType.RADIAL`. الطريقة تتطلب أيضًا عرض وارتفاع بالمقاسات النقطية (1 نقطة ≈ 1/72 بوصة).

```java
        // Step 3: Insert a radial chart (400 × 300 points)
        Shape chart = builder.insertChart(ChartType.RADIAL, 400, 300);
```

الكائن `Shape` المرتجع يحتوي على كائن المخطط الأساسي. يقوم المخطط تلقائيًا برسم التدرجات لتخطيط 24.9°، وهو الإعداد الافتراضي للمخططات القطرية في Word.

### لماذا نستخدم مخططًا قطريًا؟

المخطط القطري يعرض البيانات التي تدور حول دائرة، مما يجعله مثاليًا لإظهار الأنماط الدورية (مثل مبيعات الشهر، مؤشرات الساعة). يمكن لنفس الـ API إدراج مخططات شريطية أو دائرية أو خطية، لكن النوع القطري يضيف مظهرًا مميزًا دون الحاجة إلى كود تنسيق إضافي.

## الخطوة 4: (اختياري) تعبئة بيانات سلسلة المخطط

إذا رغبت في أن يعرض المخطط قيمًا حقيقية، عليك إضافة سلاسل ونقاط. المقتطف التالي يضيف سلسلة واحدة تحتوي على ثلاث نقاط بيانات:

```java
        // Optional: add data to the chart
        Chart chartObj = chart.getChart();
        chartObj.getSeries().clear(); // remove any default series

        // Create a new series
        ChartSeries series = chartObj.getSeries().add("Quarterly Revenue");

        // Add data points (value, category)
        series.getDataPoints().add(15000, "Q1");
        series.getDataPoints().add(21000, "Q2");
        series.getDataPoints().add(18000, "Q3");
        series.getDataPoints().add(24000, "Q4");
```

يمكنك تكرار استدعاءات `add` لعدد النقاط الذي تحتاجه. يقوم Aspose.Words تلقائيًا بتحديث التمثيل البصري، لذا ستلاحظ تعديل شرائح المخطط القطري وفق القيم الجديدة.

> **سؤال شائع:** *ماذا لو أردت ربط البيانات بقاعدة بيانات؟*  
> استرجع الصفوف، كرر عبرها، واستدعِ `series.getDataPoints().add(value, label)` داخل الحلقة. الـ API آمن للاستخدام المتعدد الخيوط ويعمل مع أي `ResultSet` تقدمه.

## الخطوة 5: حفظ المستند كملف DOCX

عند جاهزية المخطط، الخطوة النهائية هي **حفظ المستند كملف docx**. تحدد طريقة `save` صيغة الإخراج بناءً على امتداد الملف.

```java
        // Step 5: Persist the document
        String outputPath = "output/RadialChartDemo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

الملف الناتج يحتوي على مخطط قطري كامل الوظائف يمكن فتحه في Microsoft Word أو LibreOffice أو أي عارض يدعم صيغة DOCX. لأننا استخدمنا امتداد `.docx`، فإن Word يحفظ الملف بصيغة Open XML، وهي المعيار الحديث لمستندات Word.

### التحقق من النتيجة

افتح `RadialChartDemo.docx` في Word:

1. يجب أن ترى صفحة واحدة تحتوي على مخطط قطري مركزي.
2. إذا أضفت بيانات السلسلة، سيظهر المخطط بأربع شرائح معنونة Q1‑Q4.
3. انقر بزر الفأرة الأيمن على المخطط → **Edit Data** لتأكيد جدول البيانات الأساسي.

إذا ظهر المخطط فارغًا، تحقق من أنك استدعيت `chart.getChart()` قبل إضافة السلاسل، وتأكد من أن مؤشر `DocumentBuilder` موضعه في المكان الذي تريد إدراج المخطط فيه.

## الخطوة 6: نصائح متقدمة للعمل مع المخططات

| النصيحة | لماذا تهم |
|-----|----------------|
| **تعيين نمط المخطط** – `chart.getChart().setStyle(ChartStyle.STYLE_PRESET_5);` | يحسن التناسق البصري دون الحاجة لتنسيق كل عنصر يدويًا. |
| **تغيير الحجم بعد الإدراج** – `chart.setWidth(500); chart.setHeight(350);` | يتيح لك ضبط حجم المخطط بدقة وفق تخطيط الصفحة. |
| **إضافة عنوان** – `chart.getChart().getTitle().setText("Revenue Overview");` | يمنح القارئ سياقًا عند مشاهدة المستند بدون النص المحيط. |
| **تصدير إلى PDF** – `doc.save("RadialChartDemo.pdf");` | مفيد عندما تحتاج نسخة غير قابلة للتعديل للتوزيع. |
| **معالجة الترخيص** – `License lic = new License(); lic.setLicense("Aspose.Words.lic");` | يمنع ظهور علامة التقييم في الإصدارات الإنتاجية. |

هذه التحسينات اختيارية لكنها توضح كيف يمكنك تخصيص المخطط أكثر بعد أن تعلمت **إضافة مخطط إلى Word**.

## الخلاصة

أصبح لديك الآن مثال كامل ومستقل يوضح كيفية **إنشاء مخطط في Word** باستخدام Java، **إدراج مخطط قطري**، تعبئته اختياريًا بالبيانات، و**حفظ المستند كملف docx**. النمط نفسه يعمل مع أنواع مخططات أخرى، لذا يمكنك توسيع هذا الدرس لتشمل مخططات شريطية أو خطية أو دائرية حسب الحاجة.

ما يمكنك استكشافه لاحقًا:

* مشاريع **إنشاء مستند Word باستخدام Java** تجمع بين الجداول، الصور، ومخططات متعددة.
* استخدام **حفظ المستند كملف docx** مع **حفظ المستند كملف pdf** لتقارير متعددة الصيغ.
* إضافة بيانات ديناميكية من واجهات REST أو قواعد البيانات إلى مخططاتك.

لا تتردد في تجربة خيارات التنسيق، أبعاد المخطط، ومصادر البيانات. نتمنى لك برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}