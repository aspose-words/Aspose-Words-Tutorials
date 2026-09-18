---
category: general
date: 2026-09-18
description: تعلم إنشاء مستند Word وإدراج مخطط دائري باستخدام Aspose.Words للغة Java.
  يتضمن تدوير المخطط الدائري وخطوات إنشاء ملف Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- rotate pie chart
- generate word file
- how to create pie chart
language: ar
lastmod: 2026-09-18
og_description: أنشئ مستند Word وأدرج مخططًا دائريًا باستخدام Java. اتبع هذا الدليل
  لتدوير المخطط الدائري، وتفجير الشرائح، وإنشاء ملف Word.
og_image_alt: Screenshot showing a Word document containing a pie chart created with
  Java
og_title: إنشاء مستند Word مع مخطط دائري – دليل Java خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  headline: How to create a Word document with a pie chart in Java
  type: TechArticle
- description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  name: How to create a Word document with a pie chart in Java
  steps:
  - name: Expected output
    text: 'After running the program, open `output/PieChart.docx`. You should see:'
  - name: Inserting multiple charts
    text: 'If you need more than one chart, call `builder.insertChart` again after
      moving the cursor:'
  - name: Changing chart colors
    text: 'You can customize slice colors via the series'' `getPoints()` collection:'
  - name: Handling large datasets
    text: For datasets with more than 10 slices, consider using a doughnut chart (`ChartType.DOUGHNUT`)
      to keep the visual clear.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: كيفية إنشاء مستند Word يحتوي على مخطط دائري في Java
url: /ar/java/images-shapes/how-to-create-a-word-document-with-a-pie-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مستند Word يحتوي على مخطط دائري في Java

إذا كنت بحاجة إلى **إنشاء مستند Word** يُظهر البيانات بصريًا، فإن هذا الدليل يوضح لك كيفية القيام بذلك باستخدام Aspose.Words for Java. ستتعلم كيفية إدراج مخطط دائري، تفجير شريحة، تدوير المخطط، وأخيرًا **إنشاء ملف Word** يمكنك فتحه في Microsoft Word.

إنشاء تقارير تجمع بين النص والمخططات لا يتطلب أداة رسومات منفصلة. بنهاية هذا البرنامج التعليمي ستحصل على برنامج كامل قابل للتنفيذ يُنشئ ملف .docx يحتوي على مخطط دائري مُكوَّن بالكامل.

## المتطلبات المسبقة

- Java 17 أو أحدث (الكود يُمكن تجميعه مع Java 8+ أيضًا)
- Maven أو Gradle لإدارة التبعيات
- ترخيص Aspose.Words for Java (الإصدار التجريبي المجاني يعمل لهذا المثال)
- إلمام أساسي بصياغة Java

## الخطوة 1: إعداد مشروع Maven

أنشئ مشروع Maven جديد وأضف تبعية Aspose.Words إلى `pom.xml`:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-pie-chart</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.12</version>
        </dependency>
    </dependencies>
</project>
```

> **نصيحة احترافية:** حافظ على تحديث رقم الإصدار؛ الإصدارات الأحدث تضيف تحسينات لأنواع المخططات وإصلاحات للأخطاء.

## الخطوة 2: إنشاء مستند Word جديد

أول عملية عند **إنشاء مستند Word** برمجيًا هي إنشاء كائن `Document`. هذا الكائن يمثل ملف .docx بالكامل في الذاكرة.

```java
import com.aspose.words.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a blank document
        Document doc = new Document();

        // Continue with chart insertion...
```

فئة `Document` هي نقطة الدخول لجميع ميزات معالجة Word. لا يتم كتابة أي ملف إلى القرص في هذه المرحلة؛ كل شيء يحدث في الذاكرة حتى تستدعي `save`.

## الخطوة 3: كيفية إدراج مخطط دائري

يتيح لك `DocumentBuilder` إضافة محتوى إلى المستند. باستخدام `insertChart` يمكنك **إدراج مخطط دائري** مباشرة.

```java
        // Step 3: Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with width=400pt, height=300pt
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

`ChartType.PIE` يخبر Aspose.Words بإنشاء مخطط دائري. الأبعاد تُعبَّر بالنقاط (1 pt ≈ 1/72 in). بعد هذا الاستدعاء يظهر المخطط في فقرة جديدة.

## الخطوة 4: تعبئة المخطط بالبيانات

يحتاج المخطط الدائري إلى سلسلة من القيم. هنا نضيف ثلاث فئات: “Apples”، “Bananas”، و“Cherries”.

```java
        // Create a data series
        chart.getSeries().add("Fruits", new String[]{"Apples", "Bananas", "Cherries"},
                new double[]{30, 45, 25});
```

طريقة `add` تُنشئ السلسلة وتُضيف تلقائيًا عناصر الأسطورة. يمكنك إعادة استخدام هذا النمط لأي مجموعة بيانات رقمية.

## الخطوة 5: إبراز الشريحة الأولى

تفجير شريحة يجذب الانتباه إلى قيمة معينة. الشريحة الأولى (الفهرس 0) تُفجر بمقدار 20 نقطة.

```java
        // Step 5: Explode the first slice
        chart.getSeries().get(0).setExplode(20);
```

تعيين `explode` على السلسلة يؤثر على المخطط بأكمله، لذا فقط نقطة البيانات الأولى تُزاح.

## الخطوة 6: كيفية تدوير المخطط الدائري

تدوير المخطط يحسن التوازن البصري، خاصةً عندما لا تكون الشريحة الأكبر في الأعلى. طريقة `setRotationAngle` تتوقع درجة.

```java
        // Step 6: Rotate the chart 45 degrees
        chart.setRotationAngle(45);
```

تدوير 45° يحرك زاوية البدء باتجاه عقارب الساعة، مما يجعل المخطط أسهل للقراءة في العديد من التخطيطات.

## الخطوة 7: حفظ المستند وإنشاء ملف Word

أخيرًا، اكتب المستند إلى القرص. هذه الخطوة **generate word file** التي يمكن فتحها باستخدام Microsoft Word أو LibreOffice أو أي عارض متوافق.

```java
        // Step 7: Save the document
        String outputPath = "output/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

طريقة `save` تكتشف تلقائيًا امتداد .docx وتكتب حزمة متوافقة مع Word. يجب أن يكون المجلد `output` موجودًا أو يمكنك إنشاؤه برمجيًا.

### النتيجة المتوقعة

بعد تشغيل البرنامج، افتح `output/PieChart.docx`. يجب أن ترى:

- صفحة واحدة تحتوي على مخطط دائري بحجم 400 × 300 pt.
- شريحة “Apples” مُنفجرة إلى الخارج بمقدار 20 pt.
- المخطط بأكمله مُدوَّر 45° باتجاه عقارب الساعة.
- أسطورة تتطابق مع الفئات الثلاث للفواكه.

## الاختلافات الشائعة والحالات الطرفية

### إدراج مخططات متعددة

إذا كنت بحاجة إلى أكثر من مخطط واحد، استدعِ `builder.insertChart` مرة أخرى بعد تحريك المؤشر:

```java
builder.writeln();               // Add a line break
Chart secondChart = builder.insertChart(ChartType.PIE, 300, 200);
```

### تغيير ألوان المخطط

يمكنك تخصيص ألوان الشرائح عبر مجموعة `getPoints()` الخاصة بالسلسلة:

```java
chart.getSeries().get(0).getPoints().get(0).getFormat().getFill().setForeColor(Color.RED);
```

### التعامل مع مجموعات بيانات كبيرة

للمجموعات التي تحتوي على أكثر من 10 شرائح، فكر في استخدام مخطط الدونات (`ChartType.DOUGHNUT`) للحفاظ على وضوح الرؤية.

## الخلاصة

أنت الآن تعرف كيفية **إنشاء مستند Word**، **إدراج مخطط دائري**، **تدوير المخطط الدائري**، و**إنشاء ملف Word** باستخدام Aspose.Words for Java. الحل الكامل يُظهر سير العمل الكامل من تهيئة المستند إلى إخراج الملف النهائي، مع تغطية كل من “كيفية” و“لماذا” لكل خطوة.

بعد ذلك، استكشف المواضيع ذات الصلة مثل **كيفية إنشاء بيانات مخطط دائري** من قاعدة بيانات، إضافة تسميات البيانات، أو تصدير المخطط كصورة. جرّب أنواع مخططات مختلفة (شريط، خط، دونات) لتوسيع مجموعة أدوات أتمتة Word الخاصة بك.

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Track Changes in Word Documents Using Aspose.Words Java: A Complete Guide to Document Revisions](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}