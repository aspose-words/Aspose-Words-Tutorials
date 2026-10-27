---
category: general
date: 2026-10-26
description: إنشاء مخطط دونات وإدراج مخطط دائري في Java مع كود خطوة بخطوة. تعلم سير
  العمل الكامل لتصميمات مرئية مرنة للمخططات.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create doughnut chart
- insert pie chart
- Java chart library
- chart customization Java
- data visualization Java
language: ar
lastmod: 2026-10-26
og_description: أنشئ مخطط الدونات في جافا باستخدام هذا الدليل الذي يوضح أيضًا كيفية
  إدراج مخطط دائري لتصوير مرن.
og_image_alt: Java code snippet creating a doughnut chart and inserting a pie chart
og_title: إنشاء مخطط دونات وإدراج مخطط دائري – دليل جافا
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create doughnut chart and insert pie chart in Java with step‑by‑step
    code. Learn the full workflow for flexible chart visualizations.
  headline: How to create a doughnut chart and insert a pie chart
  type: TechArticle
tags:
- chart
- Java
- data‑visualization
title: كيفية إنشاء مخطط دونات وإدراج مخطط دائري
url: /ar/java/images-shapes/how-to-create-a-doughnut-chart-and-insert-a-pie-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مخطط دونات وإدراج مخطط دائري

إذا كنت بحاجة إلى **create doughnut chart** في Java، فإن هذا الدرس يشرح لك الخطوات الدقيقة. سنوضح أيضًا كيفية **insert pie chart** باستخدام نفس واجهة الـ builder API، بحيث يمكنك التبديل بين الأنماط البصرية بسهولة. في نهاية الدليل ستحصل على برنامج كامل قابل للتنفيذ ينتج كلا النوعين من المخططات ويظهر التخصيصات الشائعة.

يغطي الدرس:

* تهيئة منشئ المخطط المقدم من المكتبة المختارة.  
* إنشاء مخطط دونات وتكوين حجم الفتحة.  
* إدراج مخطط دائري وتفجير شريحة للتأكيد.  
* نصائح للتعامل مع الحالات الطرفية مثل السلاسل المفقودة أو أنواع المخططات غير المدعومة.

كل ما تحتاجه هو JDK حديث (8 أو أحدث) ومكتبة المخطط بصيغة JAR في مسار الفئة الخاص بك. لا توجد خدمات خارجية مطلوبة.

---

## المتطلبات المسبقة

| العنصر | السبب |
|------|--------|
| Java Development Kit (JDK) 8+ | مطلوب لتجميع وتشغيل المثال. |
| مكتبة المخطط (مثل **Aspose.Cells for Java** أو **JFreeChart**) | توفر `ChartBuilder`، `ChartType`، وطرق معالجة السلاسل المستخدمة في الكود. |
| بيئة تطوير متكاملة أو محرر نصوص | لكتابة وتنفيذ ملف مصدر Java. |

تأكد من إضافة ملف JAR الخاص بالمكتبة إلى مسار بناء مشروعك. إذا كنت تستخدم Maven، أضف الاعتماد المناسب؛ وإلا، ضع ملف JAR في مجلد `libs` وأشر إليه أثناء التجميع.

---

## الخطوة 1: إعداد منشئ المخطط

الخطوة الأولى هي إنشاء نسخة من `ChartBuilder` (أو ما يعادلها) التي ستولد كائنات المخطط. هذا الكائن يعمل كمصنع ويحمل ورقة العمل أو القماش حيث سيتم وضع المخطط.

```java
import com.aspose.cells.*;

public class DoughnutAndPieDemo {
    public static void main(String[] args) throws Exception {
        // Create a new workbook to host the charts
        Workbook workbook = new Workbook();
        Worksheet sheet = workbook.getWorksheets().get(0);

        // Initialize the chart builder with the worksheet
        ChartBuilder builder = new ChartBuilder(sheet);
```

**لماذا هذا مهم:**  
المنشئ يربط المخطط بورقة عمل محددة، مما يضمن أن جميع كائنات المخطط اللاحقة تشترك في نفس سطح الرسم. تخطي هذه الخطوة سيتركك بدون موقع هدف للعناصر البصرية.

---

## الخطوة 2: **Create doughnut chart**

الآن نقوم بإنشاء مخطط دونات بحجم محدد. حجم الفتحة يحدد مقدار الجزء المركزي من المخطط الذي يبقى فارغًا، محولًا مخططًا دائريًا عاديًا إلى دونات.

```java
        // Insert a doughnut chart with a width of 500 and height of 350
        Chart doughnutChart = builder.insertChart(ChartType.DOUGHNUT, 500, 350);

        // Set the hole size to 30% of the chart radius
        doughnutChart.getDoughnutChart().setHoleSize(30);

        // Add sample data series
        doughnutChart.getNSeries().add("{10, 20, 30, 40}", true);
```

**شرح:**  

* `insertChart(ChartType.DOUGHNUT, 500, 350)` ينشئ كائن المخطط ويحجز مساحة على ورقة العمل.  
* `setHoleSize(30)` يحول الدائرة إلى دونات بفتحة فارغة بنسبة 30 ٪.  
* `add("{10, 20, 30, 40}", true)` يزود المخطط بأربع نقاط بيانات؛ العلامة `true` تخبر المكتبة بمعالجة القيم كسلسلة واحدة.

**حالة طرفية:** إذا كان نوع المخطط المحدد لا يدعم الفتحة (مثل مخطط شريطي)، فإن استدعاء `getDoughnutChart()` يطرح استثناء. تحقق دائمًا من نوع المخطط قبل تعديل حجم الفتحة.

---

## الخطوة 3: **Insert pie chart**

بعد أن يصبح مخطط الدونات جاهزًا، نوضح كيفية **insert pie chart** باستخدام نفس المنشئ. تُظهر هذه الخطوة التشابه بين نوعي المخطط وتوضح كيفية إبراز شريحة.

```java
        // Insert a pie chart next to the doughnut
        Chart pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Add the same data series for consistency
        pieChart.getNSeries().add("{10, 20, 30, 40}", true);

        // Explode the first slice by 10% to draw attention
        pieChart.getSeries().get(0).setExplode(10);
```

**شرح:**  

* `ChartType.PIE` يخبر المنشئ بإنشاء مخطط دائري كلاسيكي.  
* `setExplode(10)` يبعد الشريحة الأولى بنسبة 10 ٪ من نصف القطر، وهي تقنية شائعة لتسليط الضوء على نقطة بيانات رئيسية.  

**نصيحة:** طريقة `setExplode` تعمل فقط على السلسلة الأولى في مخطط دائري. إذا كان لديك عدة سلاسل، يجب استهداف الفهرس الصحيح.

---

## الخطوة 4: حفظ المصنف

أخيرًا، اكتب المصنف إلى ملف حتى تتمكن من عرض المخططات في Excel أو أي عارض متوافق.

```java
        // Save the workbook to a file
        workbook.save("DoughnutAndPieChart.xlsx");
        System.out.println("Workbook created with doughnut and pie charts.");
    }
}
```

**لماذا الحفظ الآن:** حفظ المصنف ينهى جميع عمليات الرسم. محاولة عرض الملف قبل الحفظ ينتج عنه مستند فارغ أو غير مكتمل.

**النتيجة:** فتح *DoughnutAndPieChart.xlsx* يُظهر مخطط دونات بفتحة 30 ٪ على اليسار ومخطط دائري مع شريحة أولى منفجرة على اليمين.

---

## الخطوة 5: التغييرات الشائعة واستكشاف الأخطاء وإصلاحها

| الحالة | التعديل |
|-----------|------------|
| **Different chart dimensions** | غيّر قيم العرض والارتفاع في `insertChart`. |
| **Multiple data series** | استدعِ `add` عدة مرات أو مرّر سلسلة مصفوفة ثنائية الأبعاد. |
| **Dynamic hole size** | احسب حجم الفتحة بناءً على نطاق البيانات، ثم استدعِ `setHoleSize`. |
| **Explode multiple slices** | كرّر عبر `chart.getSeries().get(i).setExplode(percent)` لكل شريحة تريد إزاحتها. |
| **Library not supporting doughnut** | استخدم مخططًا دائريًا وارسم دائرة بيضاء فوقه يدويًا، رغم أن هذه الطريقة أقل دقة. |

**نصيحة احترافية:** دائمًا استدعِ `builder.flush()` (إن كان متاحًا) بعد إدراج المخططات عند العمل مع مصنفات كبيرة. هذا يحرر المخازن الداخلية ويمنع تسرب الذاكرة.

![كود Java لإنشاء مخطط دونات وإدراج مخطط دائري](https://example.com/images/doughnut-pie-java.png "إنشاء مثال مخطط دونات في Java")

*الصورة توضح تخطيط المصنف النهائي مع كلا المخططين جنبًا إلى جنب.*

---

## الخاتمة

أنت الآن تعرف كيف **create doughnut chart** و **insert pie chart** في Java باستخدام واجهة builder السلسة. يغطي المثال الكامل التهيئة، تكوين الحجم، ضبط الفتحة، تفجير الشريحة، وإخراج الملف. من هنا يمكنك استكشاف تخصيصات إضافية مثل الألوان، الأساطير، وتسميات البيانات لتتناسب مع متطلبات تقاريرك.

**الخطوات التالية**

* جرّب ميزات **chart customization Java** مثل التعبئات المتدرجة وتسميات البيانات.  
* دمج توليد المخططات في خدمة ويب تُعيد المصنف عند الطلب.  
* قارن نهج builder مع مكتبات أخرى (مثل JFreeChart) لتختار الأنسب لمشروعك.

نتمنى لك رسمًا بيانيًا سعيدًا!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف طرق تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء مخطط دونات في مستند Word باستخدام Java](/words/english/java/images-shapes/how-to-create-doughnut-chart-in-a-word-document-with-java/)
- [حفظ مستند Word بعد تعديل مخطط الدونات في Java](/words/english/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/)
- [إدراج مخطط دائري في Java – تفجير، تدوير وتحديد الشرائح](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}