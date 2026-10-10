---
category: general
date: 2026-10-10
description: تعلم كيفية تدوير المخطط في ملف Word وتعديل المخطط في Word لتغيير حجم
  مخطط الدونات مع مثال كامل بلغة Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to rotate chart
- modify chart in word
- change doughnut chart size
- Aspose.Words chart manipulation
- Java chart API
language: ar
lastmod: 2026-10-10
og_description: كيفية تدوير المخطط في ملف Word وتعديل المخطط في Word لتغيير حجم مخطط
  الدونات باستخدام Aspose.Words للغة Java.
og_image_alt: Screenshot showing a rotated doughnut chart after applying how to rotate
  chart steps
og_title: كيفية تدوير المخطط في مستند Word – دليل Java خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Learn how to rotate chart in a Word file and modify chart in Word to
    change doughnut chart size with a complete Java example.
  headline: How to rotate chart in a Word document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: كيفية تدوير المخطط في مستند Word باستخدام Aspose.Words
url: /ar/java/document-manipulation/how-to-rotate-chart-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تدوير المخطط في مستند Word باستخدام Aspose.Words

إذا كنت بحاجة إلى **كيفية تدوير المخطط** داخل ملف Microsoft Word، فإن هذا الدليل يوضح لك الخطوات الدقيقة. ستتعلم أيضًا كيفية **تعديل المخطط في Word** لت **تغيير حجم مخطط الدونات** دون مغادرة شفرة Java الخاصة بك.

غالبًا ما يبدو أتمتة Word كسلسلة من استدعاءات API غير المتصلة، ولكن مع Aspose.Words يمكنك التعامل مع المخطط كأي عقدة أخرى في المستند. بنهاية هذا البرنامج التعليمي ستحصل على برنامج قابل للتنفيذ يقوم بتحميل ملف `.docx` موجود، يدور مخطط الدونات بزاوية 45°، يقلل حجم الفتحة إلى 50 % من نصف القطر، ويحفظ النتيجة كملف جديد.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* Java 17 أو أحدث مثبتة.
* Maven (أو Gradle) لإدارة التبعيات.
* مستند Word إدخالي (`input.docx`) يحتوي بالفعل على مخطط دونات.
* ترخيص صالح لـ Aspose.Words for Java (أو استخدم وضع التقييم).

## الخطوة 1: إعداد مشروع Maven

أنشئ مشروع Maven جديد أو أضف التبعية التالية إلى ملف `pom.xml` الحالي الخاص بك:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

تشغيل `mvn clean install` سيقوم بتنزيل المكتبة وجعل الفئات متاحة في مسار الفئات الخاص بك.

## الخطوة 2: تحميل مستند Word الذي يحتوي على مخطط

العملية الأولى هي فتح المستند الموجود. تمثل الفئة `Document` الملف بالكامل.

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

تحميل الملف **لا** يعدله؛ فهو ببساطة ينشئ تمثيلًا في الذاكرة يمكنك الاستعلام عنه وتعديله.

## الخطوة 3: إنشاء DocumentBuilder للتنقل

`DocumentBuilder` يمنحك واجهة شبيهة بالمؤشر للتجول عبر شجرة المستند. سنستخدمه لتحديد أول شكل مخطط.

```java
        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

يبدأ الـ builder في بداية المستند، لكن يمكنك تحريكه إلى أي عقدة لاحقًا إذا لزم الأمر.

## الخطوة 4: استرجاع أول شكل مخطط

يتم تخزين المخططات كعقد `Shape`. من خلال تصفية العقد الفرعية من النوع `NodeType.SHAPE` يمكننا استخراج كائن المخطط.

```java
        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();
```

إذا كان المستند يحتوي على مخططات متعددة، يمكنك التكرار عبر `getChildNodes` والتحقق من كل `Shape` باستخدام `hasChart()` قبل التحويل.

## الخطوة 5: تدوير المخطط (how to rotate chart)

مخطط الدونات هو في الأساس مخطط دائري مع فتحة. تدويره يغيّر زاوية البداية للقطاع الأول.

```java
        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);
```

طريقة `setStartAngle` تتوقع قيمة مزدوجة تمثل الدرجات. القيم الموجبة تدور باتجاه عقارب الساعة، بينما القيم السالبة تدور عكس اتجاه عقارب الساعة.

## الخطوة 6: تغيير حجم فتحة الدونات (change doughnut chart size)

حجم الفتحة يُعبّر عنه ككسر من نصف قطر المخطط. القيمة `0.5` تعني أن الفتحة تشغل 50 % من نصف القطر الكلي.

```java
        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);
```

**نصيحة:** النطاق الصالح هو `0.0` (بدون فتحة، أي مخطط دائري عادي) إلى `0.9` (حلقة رقيقة جدًا). القيم خارج هذا النطاق ستؤدي إلى رمي `IllegalArgumentException`.

## الخطوة 7: حفظ المستند المعدل

أخيرًا، اكتب التغييرات إلى القرص.

```java
        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");
    }
}
```

عند فتح `DoughnutFormatted.docx` في Microsoft Word، سترى مخطط الدونات مدورًا بزاوية 45° والفتحة مُقلَّصة إلى نصف حجمها الأصلي.

## مثال كامل قابل للتنفيذ

بجمع كل الأجزاء معًا، إليك البرنامج الكامل الذي يمكنك نسخه‑ولصقه في بيئة التطوير المتكاملة الخاصة بك:

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Ensure the shape actually contains a chart
        if (!chartShape.hasChart()) {
            System.out.println("No chart found in the first shape.");
            return;
        }

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();

        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);

        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");

        System.out.println("Chart rotated and doughnut size changed successfully.");
    }
}
```

### النتيجة المتوقعة

تشغيل البرنامج يطبع:

```
Chart rotated and doughnut size changed successfully.
```

فتح `DoughnutFormatted.docx` يُظهر مخطط دونات يبدأ قطاعه الأول عند موضع 45° ويكون نصف القطر الداخلي نصف نصف القطر الخارجي.

## الاختلافات الشائعة وحالات الحافة

| الحالة | ما الذي يجب تعديله | لماذا يهم |
|-----------|----------------|----------------|
| **مخططات متعددة** | حلق عبر `getChildNodes(NodeType.SHAPE, true)` وتحقق من `shape.hasChart()` لكل منها | يضمن تعديل المخطط المقصود بدلاً من أول مخطط |
| **مخطط شريطي أو خطي** | `setStartAngle` لا ينطبق؛ استخدم `chart.getSeries().get(0).setFillFormat(...)` لتعديلات بصرية أخرى | ليست كل أنواع المخططات تدعم التدوير؛ فقط مخططات الدونات/الدائرة |
| **مخطط بدون فتحة دونات** | تخطّ `setDoughnutHoleSize` أو حوّل نوع المخطط إلى دونات عبر `chart.setChartType(ChartType.DONUT)` | تغيير حجم الفتحة على مخطط غير دونات يسبب استثناء |
| **مستندات كبيرة** | استخدم `DocumentBuilder.moveToDocumentStart()` و `builder.moveToNode(chartShape)` للتنقل المستهدف | يحسن الأداء بتجنب المرور عبر جميع العقد غير ذات الصلة |

## نصائح احترافية للتعامل الموثوق مع المخططات

* **احتفظ بمرجع المخطط في الذاكرة** – إذا كنت تخطط لتعديل عدة خصائص، احتفظ بمتغير `Chart` محلي بدلًا من استدعاء `chartShape.getChart()` مرارًا وتكرارًا.
* **تحقق من قيم الإدخال** – قبل استدعاء `setStartAngle` أو `setDoughnutHoleSize`، تأكد من أن القيم ضمن النطاق لتجنب الأخطاء أثناء التشغيل.
* **استخدم ترخيصًا** – وضع التقييم يضيف علامة مائية على الصفحة الأولى. تطبيق ترخيص (`License license = new License(); license.setLicense("Aspose.Words.lic");`) يزيلها.

## الخطوات التالية

الآن بعد أن عرفت **كيفية تدوير المخطط** و **تغيير حجم مخطط الدونات**، يمكنك استكشاف سيناريوهات أخرى لـ **تعديل المخطط في Word**:

* تغيير ألوان القطاعات باستخدام `chart.getSeries().get(0).getDataPoints().get(i).getFillFormat().setForeColor(Color.getRed())`.
* إضافة تسميات البيانات عبر استدعاء `chart.getSeries().get(0).setHasDataLabel(true)`.
* تصدير المخطط كصورة باستخدام `chart.toImage(300, 300, ImageType.PNG)`.

كل هذه الإضافات تتبع النمط نفسه: احصل على كائن `Chart`، استدعِ الدالة المناسبة، واحفظ المستند.

---

**لقد أتقنت الآن تدوير وتغيير حجم مخططات الدونات في Word باستخدام Java.** لا تتردد في تعديل الشيفرة لأنواع مخططات أخرى، دمجها في خط أنابيب توليد مستندات أكبر، أو الجمع بينها وبين Aspose.Slides لأتمتة PowerPoint. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء مخطط عمودي باستخدام Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [إخفاء محور المخطط في مستند Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [إدراج مخطط فقاعة في مستند Word](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}