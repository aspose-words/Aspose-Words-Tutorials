---
category: general
date: 2026-08-07
description: كيفية إبراز شريحة الفطيرة في Java باستخدام Aspose.Words. تعلم إضافة خطوط
  ربط إلى الفطيرة، إنشاء مخطط Word، وتخصيص شرائح مخطط الفطيرة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode pie slice
- add leader lines to pie
- java create word chart
- customize pie chart slices
language: ar
lastmod: 2026-08-07
og_description: كيفية تفجير شريحة الفطيرة في جافا باستخدام Aspose.Words. يوضح لك هذا
  الدليل كيفية إضافة خطوط ربط إلى الفطيرة، وإنشاء مخططات Word، وتخصيص شرائح مخطط الفطيرة
  لتحقيق تأثير بصري واضح.
og_image_alt: Screenshot of a Word document with an exploded pie chart created using
  Java Aspose.Words
og_title: كيفية تفجير شريحة الفطيرة في جافا – دليل Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to explode pie slice in Java using Aspose.Words. Learn to add leader
    lines to pie, create Word chart, and customize pie chart slices.
  headline: How to explode pie slice in Java – Aspose.Words chart tutorial
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Pie Chart
title: كيفية تفجير شريحة الفطيرة في جافا – دليل مخطط Aspose.Words
url: /ar/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تفجير شريحة الفطيرة في Java – دليل مخطط Aspose.Words

إذا كنت بحاجة إلى معرفة **how to explode pie slice** في مستند Word باستخدام Java، فإن هذا الدليل يغطي ذلك. سنظهر لك أيضًا **how to add leader lines to pie** المخططات، **java create word chart** objects، و **customize pie chart slices** للحصول على نتيجة مصقولة. في نهاية هذا الدليل ستحصل على مثال كامل قابل للتنفيذ يمكنك إدراجه في أي مشروع Java.

![كيفية تفجير شريحة الفطيرة في Java – مخطط Aspose.Words](/images/pie-chart-exploded.png)

## المتطلبات المسبقة

* مجموعة تطوير Java (JDK) 8 أو أعلى.  
* Maven أو Gradle لإدارة التبعيات.  
* رخصة Aspose.Words for Java (التقييم المجاني يعمل لأغراض التعلم).  
* إلمام أساسي بتركيب Java ومفاهيم البرمجة الكائنية.

> **نصيحة احترافية:** على الرغم من أن Aspose.Words يقدم تجربة مجانية، فإن شراء رخصة يزيل علامة التقييم المائية من المستندات المولدة.

## ما يغطيه هذا الدليل

* إنشاء مستند Word جديد من الصفر.  
* إدراج **pie chart** باستخدام `DocumentBuilder`.  
* **Exploding a pie slice** لتسليط الضوء على نقطة البيانات.  
* **Adding leader lines to pie** لتسمية أوضح.  
* تخصيص مظهر الشريحة، مثل الألوان والحدود.  
* حفظ المستند على القرص والتحقق من النتيجة.

---

## كيفية تفجير شريحة الفطيرة باستخدام Aspose.Words في Java

الخطوة الأولى هي إعداد كائن المخطط وتفجير الشريحة المطلوبة. Aspose.Words يعرض المخطط عبر الفئة `Shape`، وكل شريحة هي `ChartPoint`. من خلال ضبط الخاصية `Explosion` يمكنك التحكم في مدى تحرك الشريحة إلى الخارج.

```java
// Step 1: Create a blank document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a pie chart (400x300 points)
Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
Chart chart = pieChart.getChart();

// Step 3: Explode the first slice (index 0) by 20 points
chart.getSeries().get(0).getPoints().get(0).setExplosion(20);
```

**لماذا يعمل:**  
`setExplosion(20)` يخبر محرك المخطط بتحريك الشريحة بمقدار 20 نقطة من مركز المخطط. القيمة نسبية؛ الأرقام الأكبر تخلق تأثيرًا أكثر دراماتيكية. يمكنك تفجير أي شريحة بتغيير الفهرس (`get(1)`, `get(2)`, …).

## إضافة خطوط ربط إلى الفطيرة لتسميات أوضح

خطوط الربط تربط تسمية الشريحة بحافتها، وهو مفيد بشكل خاص عندما تكون الشرائح منفجرة أو عندما يحتوي المخطط على العديد من الأقسام الصغيرة. استدعاء `setLeaderLines(true)` يفعّل هذه الميزة للسلسلة بأكملها.

```java
// Step 4: Enable leader lines for the series
chart.getSeries().get(0).setLeaderLines(true);
```

**لماذا تحتاج خطوط الربط:**  
عندما تكون الشريحة منفجرة، قد يتداخل التسمية الافتراضية مع عناصر أخرى. خطوط الربط تحافظ على قابلية قراءة التسمية عن طريق رسم خط قصير من الشريحة إلى صندوق النص.

## Java create Word chart – إدراج سلسلة البيانات

المخطط بدون بيانات ليس مفيدًا كثيرًا. يجب ملء السلسلة بالفئات والقيم. أدناه نضيف ثلاث فئات تمثل حصة السوق.

```java
// Step 5: Populate the chart with data
ChartSeries series = chart.getSeries().get(0);
series.getDataLabel().setShowCategoryName(true); // show labels
series.getDataLabel().setShowPercentage(true);   // show percentages

// Add categories and values
series.getCategories().add("Product A");
series.getCategories().add("Product B");
series.getCategories().add("Product C");

series.getValues().add(45); // Product A = 45%
series.getValues().add(30); // Product B = 30%
series.getValues().add(25); // Product C = 25%
```

**شرح:**  
`ChartSeries` يحتوي على كل من الفئات (أسماء الشرائح) والقيم الرقمية. تمكين `ShowCategoryName` و `ShowPercentage` يجعل المخطط ذاتيًا توضيحيًا، وهو يتناغم جيدًا مع خطوط الربط التي أضفناها سابقًا.

## تخصيص شرائح مخطط الفطيرة بخلاف التفجير

إلى جانب تفجير شريحة، غالبًا ما تريد تعديل الألوان، الحدود، أو حتى إخفاء شريحة بالكامل. المقتطف التالي يوضح ثلاث تخصيصات شائعة:

```java
// Step 6: Change slice colors and borders
ChartPoint pointA = series.getPoints().get(0); // Product A
ChartPoint pointB = series.getPoints().get(1); // Product B
ChartPoint pointC = series.getPoints().get(2); // Product C

// Set custom fill colors
pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50")); // green
pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3")); // blue
pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800")); // orange

// Add a thin border to each slice
for (ChartPoint pt : series.getPoints()) {
    pt.getFormat().getLine().setWeight(0.5);
    pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
}

// Optional: hide a slice (e.g., Product C) without removing data
pointC.setIsHidden(true);
```

**لماذا تخصيص الشرائح:**  
الألوان المخصصة تجعل المخطط يتماشى مع هوية الشركة، بينما الحدود تحسن قابلية القراءة على الصفحات المطبوعة. إخفاء شريحة مفيد عندما تريد الحفاظ على نموذج البيانات intact ولكن تستبعد فئة مؤقتًا من المخرجات البصرية.

## حفظ المستند والتحقق من النتيجة

أخيرًا، احفظ المستند على القرص. يمكنك فتح ملف `.docx` المُولد في Microsoft Word أو LibreOffice أو أي عارض يدعم هذا التنسيق.

```java
// Step 7: Save the document
String outputPath = "output/PieChartDemo.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

**الناتج المتوقع:**  
عند فتح `PieChartDemo.docx`، سترى مخطط فطيرة حيث الشريحة الأولى (Product A) منفجرة إلى الخارج، خطوط الربط تشير من كل شريحة إلى تسميتها، وتظهر الشرائح بالألوان المخصصة الأخضر، الأزرق، والبرتقالي. الشريحة المخفية (Product C) لن تكون مرئية، لكن النسب المئوية ستظل مجموعها 100 % لأن البيانات لا تزال في سلسلة المخطط.

---

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه، لصقه، وتشغيله بعد إضافة تبعية Aspose.Words إلى مشروعك.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a pie chart (400x300 points)
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = pieChart.getChart();

        // Explode the first slice to highlight it
        chart.getSeries().get(0).getPoints().get(0).setExplosion(20);

        // Enable leader lines for clearer labeling
        chart.getSeries().get(0).setLeaderLines(true);

        // Populate the chart with data
        ChartSeries series = chart.getSeries().get(0);
        series.getDataLabel().setShowCategoryName(true);
        series.getDataLabel().setShowPercentage(true);

        series.getCategories().add("Product A");
        series.getCategories().add("Product B");
        series.getCategories().add("Product C");

        series.getValues().add(45);
        series.getValues().add(30);
        series.getValues().add(25);

        // Customize slice colors and borders
        ChartPoint pointA = series.getPoints().get(0);
        ChartPoint pointB = series.getPoints().get(1);
        ChartPoint pointC = series.getPoints().get(2);

        pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50"));
        pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3"));
        pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800"));

        for (ChartPoint pt : series.getPoints()) {
            pt.getFormat().getLine().setWeight(0.5);
            pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
        }

        // Hide the third slice (optional)
        pointC.setIsHidden(true);

        // Save the document
        document.save("output/PieChartDemo.docx");
        System.out.println("Pie chart Word document created successfully.");
    }
}
```

**التبعية (Maven)**  

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شاملة من الشيفرة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء مخطط عمودي باستخدام Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [كيفية تحميل مستندات Word باستخدام Aspose.Words Java: دليل شامل](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [كيفية إنشاء حقول نموذج وإضافة محتوى باستخدام DocumentBuilder في Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}