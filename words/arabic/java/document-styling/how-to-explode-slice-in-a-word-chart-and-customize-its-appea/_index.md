---
category: general
date: 2026-10-04
description: تعلم كيفية تفجير شريحة في مخطط Word، وتفجير شريحة مخطط دائري، وتغيير
  حجم مخطط الدونات باستخدام مثال Java خطوة بخطوة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode slice
- modify chart in word
- explode pie chart slice
- change doughnut chart size
- customize pie chart word
language: ar
lastmod: 2026-10-04
og_description: كيفية تفجير شريحة في مخطط Word وتخصيص مخططات الفطيرة أو الدونات باستخدام
  Java. اتبع المثال الكامل لتعديل المخطط في Word.
og_image_alt: Screenshot showing an exploded pie chart slice inside a Word document
og_title: كيفية تفجير قطعة في مخطط Word – دليل Java كامل
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to explode slice in a Word chart, explode pie chart slice
    and change doughnut chart size with a step‑by‑step Java example.
  headline: How to explode slice in a Word chart and customize its appearance
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart manipulation
title: كيفية تفجير شريحة في مخطط Word وتخصيص مظهرها
url: /ar/java/document-styling/how-to-explode-slice-in-a-word-chart-and-customize-its-appea/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تفجير شريحة في مخطط Word وتخصيص مظهره

إذا كنت بحاجة إلى **how to explode slice** في مخطط Word، فإن هذا الدليل يوضح لك بالضبط كيفية القيام بذلك. سواء كنت تُعد عرض مبيعات أو تقريرًا ماليًا، فإن تفجير شريحة مخطط دائري أو تعديل فتحة الدونات يمكن أن يجعل أهم البيانات بارزة. في الأقسام التالية ستتعلم أيضًا كيفية **modify chart in Word**، **explode pie chart slice**، **change doughnut chart size**، و **customize pie chart word** باستخدام Aspose.Words for Java.

ستنتهي من هذا الدرس ببرنامج Java كامل وجاهز للتنفيذ يقوم بتحميل ملف `.docx`، يفجر الشريحة الأولى من مخطط دائري، يغيّر حجم فتحة الدونات، ويحفظ النتيجة. لا تحتاج إلى أي سكريبتات خارجية أو تحرير يدوي.

## المتطلبات المسبقة

- Java 17 أو أحدث مثبت على جهاز التطوير الخاص بك.  
- Maven 3.6+ (أو Gradle) لإدارة الاعتمادات.  
- مكتبة Aspose.Words for Java (الإصدار التجريبي المجاني يكفي للتطوير).  
- مستند Word (`input.docx`) يحتوي على مخطط واحد على الأقل (دائري أو دونات).

## الخطوة 1: إضافة Aspose.Words إلى مشروعك

إذا كنت تستخدم Maven، أضف الاعتماد التالي إلى ملف `pom.xml` الخاص بك:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

لـ Gradle، ضع هذا في `build.gradle`:

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

> **نصيحة احترافية:** حافظ على تحديث نسخة المكتبة؛ الإصدارات الأحدث تضيف دعمًا لأنواع مخططات إضافية وتحسن الأداء.

## الخطوة 2: تحميل مستند Word الذي يحتوي على مخطط

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // Path to the source .docx file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – this step is required before any chart manipulation.
        Document doc = new Document(inputPath);
```

**لماذا هذا مهم:** تحميل المستند يُنشئ تمثيلًا في الذاكرة يمكن لـ Aspose.Words استكشافه. بدون هذا الكائن لا يمكنك الوصول إلى عقد المخطط.

## الخطوة 3: استرجاع أول مخطط في المستند

```java
        // Locate the first Shape node that contains a chart.
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);

        // Cast the Shape to a Chart object.
        Chart chart = chartShape.getChart();
```

> **توضيح:** `NodeType.SHAPE` يغطي جميع كائنات الرسم، بما في ذلك المخططات. الوسيط `true` يُخبر Aspose بالبحث بشكل متكرر، مما يضمن العثور على أول مخطط حتى لو كان متداخلًا داخل جدول.

## الخطوة 4: تفجير الشريحة الأولى من مخطط دائري

```java
        // Verify the chart type before exploding.
        if (chart.getChartType() == ChartType.PIE) {
            // Explode the first series (slice) by 20 points.
            chart.getSeries().get(0).setExplosion(20);
        } else {
            System.out.println("The first chart is not a pie chart; explosion skipped.");
        }
```

**كيف يعمل:** طريقة `setExplosion` تأخذ قيمة رقمية تحدد المسافة التي تتحرك بها الشريحة بعيدًا عن المركز. قيمة `20` تكون ملحوظة بصريًا دون كسر تخطيط المخطط.

## الخطوة 5: تعديل حجم فتحة الدونات لمخطط الدونات

```java
        // If the chart is a doughnut, change the hole size.
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            // Set the doughnut hole size to 40% of the chart radius.
            chart.setDoughnutHoleSize(40);
        } else {
            System.out.println("The first chart is not a doughnut chart; hole size unchanged.");
        }
```

**لماذا هذا مفيد:** فتحة دونات أكبر يمكن أن تحسن قابلية القراءة عندما يكون لديك العديد من نقاط البيانات. طريقة `setDoughnutHoleSize` تتوقع نسبة مئوية (0‑100).

## الخطوة 6: حفظ المستند المعدل

```java
        // Path for the output document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";

        // Save the changes – the file now contains the exploded slice and updated doughnut size.
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

### النتيجة المتوقعة

- الشريحة الأولى من أول مخطط دائري تُبعد إلى الخارج، مما يجعلها بارزة.  
- إذا كان المخطط دونات، فإن الفتحة المركزية تتوسع لتصبح 40 % من نصف قطر المخطط.  
- الملف الناتج `PieChart.docx` يمكن فتحه في Microsoft Word أو LibreOffice أو أي عارض متوافق، مع عرض التغييرات البصرية التي تم تطبيقها برمجيًا.

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج بالكامل في كتلة واحدة. انسخه إلى `ChartExploder.java`، عدل مسارات الملفات، وشغّله باستخدام `mvn compile exec:java` (أو إعداد تشغيل IDE الخاص بك).

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Find the first chart shape
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (chartShape == null) {
            System.out.println("No chart found in the document.");
            return;
        }

        // 3️⃣ Cast to Chart
        Chart chart = chartShape.getChart();

        // 4️⃣ Explode the first slice if it is a pie chart
        if (chart.getChartType() == ChartType.PIE) {
            chart.getSeries().get(0).setExplosion(20);
            System.out.println("Exploded first slice of the pie chart.");
        }

        // 5️⃣ Change doughnut hole size if it is a doughnut chart
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            chart.setDoughnutHoleSize(40);
            System.out.println("Set doughnut hole size to 40%.");
        }

        // 6️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Modified document saved as " + outputPath);
    }
}
```

تشغيل هذا الكود سيقوم **modify chart in Word**، **explode pie chart slice**، و **change doughnut chart size** تلقائيًا.

## أسئلة شائعة وحالات خاصة

| السؤال | الجواب |
|----------|--------|
| *ماذا لو كان المستند يحتوي على مخططات متعددة؟* | العينة تستهدف **أول** مخطط (`NodeType.SHAPE, 0`). للعمل مع مخططات أخرى، غيّر الفهرس أو كرّر عبر `doc.getChildNodes(NodeType.SHAPE, true)` وصَفِّ حسب `shape.getChart() != null`. |
| *هل يمكنني تفجير شريحة غير الأولى؟* | نعم. احصل على السلسلة المطلوبة عبر `chart.getSeries().get(seriesIndex)` واستدعِ `setExplosion(value)`. الفهارس تبدأ من الصفر. |
| *هل يعمل هذا مع ملفات Word 2007‑2021؟* | Aspose.Words يدعم `.doc`، `.docx`، `.dot`، و `.dotx`. نفس الكود يعمل عبر الإصدارات لأن المكتبة تُجرد تنسيق الملف. |
| *ماذا لو كان المخطط شريطًا أو خطًا؟* | `setExplosion` و `setDoughnutHoleSize` تنطبقان فقط على المخططات الدائرية. يتخطى الكود هذه العمليات بأمان عندما يكون نوع المخطط مختلفًا. |
| *هل أحتاج إلى ترخيص لـ Aspose.Words؟* | الترخيص التجريبي المجاني يزيل حد الـ 30 يومًا لكنه يضيف علامة مائية. للإنتاج، اشترِ ترخيصًا لإزالة العلامة المائية وإتاحة جميع الوظائف. |

## الخاتمة

أنت الآن تعرف **how to explode slice** في مخطط Word، وكيفية **modify chart in Word**، وكيفية **change doughnut chart size** باستخدام Aspose.Words for Java. يوضح المثال الكامل سير العمل بالكامل—من تحميل المستند، تحديد المخطط، تطبيق التعديلات البصرية، إلى حفظ النتيجة—حتى تتمكن من دمج هذه الخطوات في أي خط أنابيب تقارير أو توليد مستندات.

**الخطوات التالية**

- استكشف تخصيصات مخططات أخرى مثل تغيير الألوان، إضافة تسميات البيانات، أو تغيير نوع المخطط (`chart.setChartType(ChartType.BAR_CLUSTERED)`).  
- دمج هذه المنطق مع Aspose.PDF لإنشاء نسخة PDF من نفس التقرير.  
- أتمتة العملية لمجموعة من المستندات عبر حلقة تمر على الملفات في دليل.

لا تتردد في تجربة قيم تفجير مختلفة أو نسب فتحة الدونات لتتناسب مع إرشادات التصميم الخاصة بك. Happy coding!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء مخطط عمودي باستخدام Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [إخفاء محور المخطط في مستند Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [إدراج مخطط فقاعة في مستند Word](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}