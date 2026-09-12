---
category: general
date: 2026-09-11
description: احفظ مستند Word بعد تعديل مخطط الدونات باستخدام Aspose.Words للغة Java.
  تعلّم كيفية تغيير حجم فتحة الدونات، تدوير مخطط الدونات، وتعديل خصائص مخطط الدونات.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word document
- rotate doughnut chart
- edit doughnut chart
- change doughnut hole
- change chart hole size
language: ar
lastmod: 2026-09-11
og_description: احفظ مستند Word بعد تعديل مخطط الدونات باستخدام Aspose.Words for Java.
  يوضح هذا الدرس كيفية تغيير حجم فتحة الدونات، وتدوير مخطط الدونات، وتخصيص مظهر المخطط.
og_image_alt: Java code editing a doughnut chart before saving Word document
og_title: حفظ مستند Word بعد تعديل مخطط الدونات – دليل Java
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Save Word document after editing a doughnut chart with Aspose.Words
    for Java. Learn how to change doughnut hole size, rotate doughnut chart, and edit
    doughnut chart properties.
  headline: Save Word document after editing doughnut chart in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word
- Chart
- Doughnut
title: حفظ مستند Word بعد تعديل مخطط الدونات في Java
url: /ar/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ مستند Word بعد تعديل مخطط الدونات في Java

إذا كنت بحاجة إلى **حفظ مستند Word** يحتوي على مخطط دونات مخصص، فإن هذا الدليل يوضح لك بالضبط كيفية القيام بذلك. في بضع أسطر فقط من Java يمكنك تغيير حجم فتحة الدونات، تدوير مخطط الدونات، ثم كتابة النتيجة مرة أخرى إلى القرص.

سترى مثالًا كاملاً وقابلًا للتنفيذ يستخدم Aspose.Words for Java، بالإضافة إلى نصائح للتعامل مع مخططات متعددة، والتحقق من أنواع العقد، وتجنب الأخطاء الشائعة. لا توجد مراجع خارجية مطلوبة—كل ما تحتاجه مضمّن.

## المتطلبات المسبقة

- Java 17 أو أحدث مثبت
- Maven أو Gradle لإدارة التبعيات
- Aspose.Words for Java (الإصدار 23.9 أو أحدث) مضاف إلى مشروعك  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.9</version>
  </dependency>
  ```
- ملف Word (`input.docx`) يحتوي على مخطط دونات واحد

## الخطوة 1: تحميل مستند Word

الخطوة الأولى هي فتح ملف المصدر. هذه الخطوة أساسية لأن كل عملية تالية تعمل على كائن `Document` الموجود في الذاكرة.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a doughnut chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **لماذا؟** تحميل المستند ينشئ تمثيل DOM يتيح لك استعراض الأشكال والجداول والمخططات. إذا تعذر فتح الملف، فإن Aspose.Words يرمي استثناءً، وبالتالي تعرف فورًا أن المسار غير صحيح.

## الخطوة 2: تحديد شكل مخطط الدونات

يتم تخزين المخطط داخل عقدة `Shape`. نسترجع أول شكل يحتوي على مخطط ونحوّل معالجه إلى `Chart`.

```java
        // Find the first shape that contains a chart
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        // Ensure the shape actually holds a chart
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        // Get the Chart object for further manipulation
        Chart chart = chartShape.getChart();
```

> **لماذا؟** التحقق من `isChart()` يمنع حدوث `ClassCastException` عندما يحتوي المستند على صور أو أشكال أخرى قبل المخطط. هذا يجعل الكود قويًا للمستندات ذات المحتوى المختلط.

## الخطوة 3: تغيير حجم فتحة الدونات  

الآن نقوم بتحرير فتحة الدونات. طريقة `setHoleSize` تتوقع نسبة مئوية من نصف قطر المخطط (10 – 90).

```java
        // Adjust the size of the doughnut hole (percentage of the chart radius)
        chart.setHoleSize(30);   // The hole occupies 30 % of the radius
```

> **لماذا؟** تغيير فتحة الدونات (`change doughnut hole` / `change chart hole size`) يتيح لك إبراز أو تقليل التركيز على المنطقة المركزية. القيم خارج نطاق 10‑90 % يتم تجاهلها من قبل الـ API.

## الخطوة 4: تدوير مخطط الدونات  

للتحكم في مكان بدء الشريحة الأولى، قم بتعيين زاوية الشريحة الأولى. هذا يؤدي فعليًا إلى **تدوير مخطط الدونات**.

```java
        // Rotate the chart so that the first slice starts at a custom angle
        chart.setFirstSliceAngle(45);   // Starts the first slice at 45 degrees
```

> **لماذا؟** تدوير المخطط مفيد عندما تريد أن تظهر شريحة معينة في الأعلى أو لتطابق مواصفات التصميم.

## الخطوة 5: حفظ المستند المحدث  

أخيرًا، اكتب التغييرات مرة أخرى إلى ملف جديد. هذه هي اللحظة التي تقوم فيها **بحفظ مستند Word** مع المخطط المعدل.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **النتيجة المتوقعة:** يحتوي `output.docx` على المحتوى الأصلي، لكن مخطط الدونات الآن يحتوي على فتحة بنسبة 30 % وتبدأ شريحته الأولى عند 45 °. فتح الملف في Microsoft Word سيعرض المخطط المُحوَّل.

## مثال كامل يعمل

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑ولصقه في بيئة التطوير المتكاملة الخاصة بك. يتضمن جميع الاستيرادات ومعالجة الأخطاء اللازمة لـ **تحرير مخطط الدونات** و**حفظ مستند Word** بأمان.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Locate the first chart shape
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        Chart chart = chartShape.getChart();

        // 3. Change the doughnut hole size
        chart.setHoleSize(30); // 30 % hole

        // 4. Rotate the doughnut chart
        chart.setFirstSliceAngle(45); // start at 45°

        // 5. Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### النتيجة المتوقعة

عند فتح `output.docx`:

- فتحة المخطط الدونات المركزية تشغل تقريبًا ثلث نصف قطر المخطط.  
- تبدأ الشريحة الأولى عند موضع 45 درجة، مما يحرك المخطط بأكمله باتجاه عقارب الساعة.  

كلا التغييران البصريان ينعكسان فورًا في Word.

## الاختلافات الشائعة وحالات الحافة

| الحالة | كيفية المعالجة |
|-----------|----------------|
| **Multiple charts** | تكرار عبر `doc.getChildNodes(NodeType.SHAPE, true)` وتصفية `shape.isChart()`؛ تطبيق `setHoleSize` / `setFirstSliceAngle` على كل `Chart`. |
| **Chart is not a doughnut** | تحقق من `chart.getType()`؛ استدعِ `setHoleSize` فقط عندما يكون `chart.getType() == ChartType.DOUGHNUT`. |
| **Need to change hole size dynamically** | احسب النسبة المئوية المطلوبة بناءً على قيم البيانات، ثم استدعِ `setHoleSize(computedValue)`. |
| **Saving to a stream** | Use |

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك الخاصة.

- [كيفية إنشاء مخطط عمودي باستخدام Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [كيفية حفظ المستند كملف PDF باستخدام Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [حفظ Word مع كلمة مرور باستخدام Aspose.Words for Java](/words/english/java/document-loading-and-saving/advance-saving-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}