---
category: general
date: 2026-08-20
description: أضف خطوط ربط إلى مخطط الفطيرة في جافا بسرعة. تعلم كيفية إدراج، تفجير،
  إعادة تلوين، ووضع تسميات للشرائح باستخدام واجهة برمجة التطبيقات Chart.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add leader lines to pie chart
- pie chart explosion Java
- set sector color Chart API
- builder.insertChart usage
- ChartType.PIE example
language: ar
lastmod: 2026-08-20
og_description: أضف خطوط ربط إلى مخطط دائري في جافا مع مثال مختصر. اتبع هذا الدليل
  لإدراج، تفجير، إعادة تلوين، ووضع تسميات للشرائح باستخدام واجهة برمجة التطبيقات Chart.
og_image_alt: Screenshot showing a pie chart with an exploded slice and leader lines
  – add leader lines to pie chart
og_title: إضافة خطوط ربط إلى مخطط دائري في جافا – دليل خطوة بخطوة لواجهة برمجة التطبيقات
  Chart
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Add leader lines to pie chart in Java quickly. Learn to insert, explode,
    recolor, and label slices using the Chart API.
  headline: How to add leader lines to pie chart in Java with the Chart API
  type: TechArticle
tags:
- pie chart
- Java
- Chart API
- data visualization
title: كيفية إضافة خطوط الربط إلى مخطط دائري في جافا باستخدام واجهة برمجة التطبيقات
  Chart
url: /ar/java/using-document-elements/how-to-add-leader-lines-to-pie-chart-in-java-with-the-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إضافة خطوط القائد إلى مخطط دائري في Java باستخدام Chart API

إذا كنت بحاجة إلى **إضافة خطوط القائد إلى مخطط دائري** في Java، فإن هذا الدليل يشرح لك العملية بالكامل. سترى كيفية إدراج مخطط دائري، تفجير شريحة للتأكيد، تغيير لونها، وأخيرًا تمكين خطوط القائد التي تُظهر تسمية الجزء المفجر.

يستخدم المثال Chart API القياسي الموجود في العديد من مكتبات تقارير Java. لا توجد أدوات خارجية مطلوبة، ويعمل الكود على أي بيئة JDK 8+.

## ما ستحققه

* إنشاء كائن `Chart` من النوع `ChartType.PIE` بحجم مخصص.  
* تفجير الشريحة الأولى لجذب الانتباه.  
* تعيين لون قطاع الشريحة المفجرة إلى اللون الأزرق.  
* **إضافة خطوط القائد إلى مخطط دائري** بحيث يكون تسمية الشريحة موصلة بوضوح.

يجب أن يكون لديك مشروع Java يحتوي على مكتبة Chart في مسار الفئة. إذا كنت تستخدم Maven، أضف التبعية الموضحة في قسم المتطلبات المسبقة.

## المتطلبات المسبقة

* تثبيت JDK 8 أو أحدث.  
* مكتبة Chart (مثال: `com.example.chart:chart-api:2.5.0`).  
* إلمام أساسي بفئات Java واستدعاءات الطرق.

---

## كيفية إضافة خطوط القائد إلى مخطط دائري

فيما يلي برنامج كامل قابل للتنفيذ يوضح كل خطوة. الكود مُصمم بشكل مستقل بحيث يمكنك نسخه، لصقه، وتشغيله دون تعديل.

```java
// File: AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Demonstrates adding leader lines to a pie chart in Java.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // 1️⃣ Insert a pie chart with the desired size
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 2️⃣ Pull out the first slice for emphasis (explosion)
        chart.getSeries().get(0).setExplosion(20);

        // 3️⃣ Change the color of the first slice to blue
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // 4️⃣ Show leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional: Save the chart as an image file
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart saved to pie-with-leader-lines.png");
    }
}
```

### شرح كل خطوة

| الخطوة | ما يفعله الكود | لماذا يهم |
|------|-------------------|----------------|
| **1️⃣ إدراج مخطط دائري** | `builder.insertChart(ChartType.PIE, 400, 300)` ينشئ مخططًا دائريًا بحجم 400 × 300 بكسل. | يحدد حاوية المخطط وأبعاده، مما يؤثر على موضع التسمية وطول خطوط القائد. |
| **2️⃣ تفجير الشريحة الأولى** | `setExplosion(20)` يبعد الشريحة بنسبة 20 % من نصف القطر. | الشريحة المفجرة تجذب نظر المشاهد وتظهر خط القائد. |
| **3️⃣ تعيين لون القطاع** | `setSectorColor(Color.BLUE)` يغيّر تعبئة الشريحة إلى اللون الأزرق. | التباين اللوني يحسّن قابلية القراءة، خاصةً عندما تكون الشريحة مميزة. |
| **4️⃣ تمكين خطوط القائد** | `setLeaderLines(true)` يشغّل خطوط الربط التي تربط الشريحة بتسميتها. | خطوط القائد تضمن بقاء التسمية قابلة للقراءة حتى عندما تُبعد الشريحة إلى الخارج. |

استدعاء `saveAsPng` اختياري لكنه مفيد للتحقق من النتيجة البصرية. بعد تشغيل البرنامج، يجب أن ترى صورة مشابهة للتي أدناه.

![إضافة خطوط القائد إلى مخطط دائري](https://example.com/assets/pie-leader-lines.png "إضافة خطوط القائد إلى مخطط دائري – شريحة مفجرة باللون الأزرق وخطوط القائد")

*الشكل: مخطط دائري حيث تم تفجير الشريحة الأولى، لونها أزرق، ومتصلة بتسميتها عبر خط قائد.*

## تخصيص خطوط القائد (متقدم)

استدعاء `setLeaderLines(true)` الأساسي يستخدم النمط الافتراضي للمكتبة. يمكنك التحكم في المظهر بشكل إضافي:

```java
// Change leader line color to dark gray
chart.setLeaderLineColor(Color.DARK_GRAY);

// Increase line thickness for better visibility
chart.setLeaderLineWidth(2);

// Position labels outside the chart area
chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);
```

هذه الخيارات مفيدة عندما تحتاج إلى مطابقة هوية الشركة أو تحسين إمكانية الوصول.

### التعامل مع سلاسل متعددة

إذا كان مخططك الدائري يحتوي على أكثر من سلسلة واحدة، قد ترغب في خطوط القائد فقط لشريحة معينة. استخدم فهرس السلسلة لاستهداف العنصر الصحيح:

```java
// Enable leader lines only for the second series, third slice
chart.getSeries().get(1).get(2).setExplosion(15);
chart.getSeries().get(1).get(2).setLeaderLineEnabled(true);
```

عندما لا تكون الشريحة مفجرة، عادةً ما يكون خط القائد مخفيًا تلقائيًا، لكن يمكنك فرض ظهوره باستخدام `setLeaderLineEnabled(true)`.

## المشكلات الشائعة وكيفية تجنبها

| المشكلة | العرض | الحل |
|--------|---------|-----|
| **خطوط القائد غير مرئية** | المخطط يُظهر بدون خطوط ربط. | تأكد من أن الشريحة مفجرة (`setExplosion` > 0) أو فعّل خطوط القائد صراحةً على الشريحة. |
| **تداخل التسميات** | التسميات تتصادم مع بعضها البعض. | زد حجم المخطط أو اضبط `setLabelPlacement(Chart.LabelPlacement.OUTSIDE)`. |
| **عدم تطبيق اللون** | الشريحة تبقى باللون الافتراضي. | تحقق من أنك تستهدف الفهرس الصحيح للسلسلة (`getSeries().get(0)`). |
| **فشل حفظ الصورة** | `saveAsPng` يرمي استثناءً. | تحقق من أذونات الكتابة للمجلد الهدف وأن المكتبة تدعم تصدير PNG. |

## قائمة المصدر الكاملة

للتسهيل، إليك ملف المصدر الكامل مرة أخرى، بما في ذلك الاستيرادات والتعليقات:

```java
// AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Complete example that adds leader lines to a pie chart.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // Create a builder and insert a 400×300 pie chart
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // Explode the first slice (20% offset) and color it blue
        chart.getSeries().get(0).setExplosion(20);
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // Turn on leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional styling
        chart.setLeaderLineColor(Color.DARK_GRAY);
        chart.setLeaderLineWidth(2);
        chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);

        // Export the chart as a PNG image
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart generated successfully.");
    }
}
```

تشغيل هذا البرنامج يولد `pie-with-leader-lines.png`، الذي يعرض مخططًا دائريًا بشريحة زرقاء مفجرة وخطوط قائد واضحة تشير إلى تسمية الشريحة.

## الخلاصة

أنت الآن تعرف كيفية **إضافة خطوط القائد إلى مخطط دائري** في Java باستخدام Chart API. تتكون العملية من إدراج `ChartType.PIE`، تفجير الشريحة المطلوبة، تخصيص لونها، وتمكين خطوط القائد. باستخدام خيارات التنسيق الاختيارية يمكنك ضبط لون الخط، سمكه، وموضع التسمية لتلبية أي متطلبات بصرية.

بعد ذلك، فكر في استكشاف المواضيع ذات الصلة مثل **تفجير المخطط الدائري Java**، **تعيين لون القطاع Chart API**، و**استخدام builder.insertChart** لإنشاء تصورات أكثر تعقيدًا مثل المخططات الدائرية المجوفة، المخططات الدائرية المتراكمة، أو لوحات التحكم التفاعلية.

لا تتردد في تجربة فهارس شرائح مختلفة، ألوان، وأنماط خطوط القائد—ستصبح مخططاتك أكثر إفادة وجاذبية بصريًا مع كل تعديل. برمجة سعيدة!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك الخاصة.

- [كيفية إنشاء مخطط عمودي باستخدام Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [إضافة قيم التاريخ والوقت إلى محور المخطط](/words/english/net/programming-with-charts/date-time-values-to-axis/)
- [إدراج مخطط عمودي في Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}