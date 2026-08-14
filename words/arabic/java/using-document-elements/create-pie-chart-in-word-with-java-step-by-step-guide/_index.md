---
category: general
date: 2026-08-14
description: إنشاء مخطط دائري في Word باستخدام Java و Aspose.Words. تعلّم كيفية إضافة
  بيانات السلسلة إلى المخطط وتدوير شريحة المخطط الدائري في بضع أسطر فقط.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart in word
- how to add series data to chart
- rotate pie chart slice
- Aspose.Words chart API
- Java document automation
language: ar
lastmod: 2026-08-14
og_description: إنشاء مخطط دائري في Word باستخدام Java و Aspose.Words. يوضح هذا الدرس
  كيفية إضافة بيانات السلسلة إلى المخطط وتدوير شريحة المخطط الدائري بسرعة.
og_image_alt: Screenshot of a Word document containing a colorful pie chart generated
  by Java code
og_title: إنشاء مخطط دائري في Word باستخدام Java – دليل البرمجة الكامل
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  headline: Create pie chart in Word with Java – step-by-step guide
  type: TechArticle
- description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  name: Create pie chart in Word with Java – step-by-step guide
  steps:
  - name: Why use Aspose.Words?
    text: '* **No Microsoft Office required** – the library works on any server or
      CI environment. * **Full .docx fidelity** – the generated chart looks identical
      to one created manually in Word. * **Single‑file dependency** – just add the
      JAR and you’re ready to go.'
  - name: Expected output
    text: '* A file named **PieChart.docx** appears in the `output` folder. * Opening
      the file in Microsoft Word shows a colorful pie chart with three slices (40
      %, 30 %, 30 %). * The chart is rotated 45° clockwise, so the first slice starts
      slightly to the right of the vertical axis.'
  - name: Tips for production use
    text: '* **Reuse the `DocumentBuilder`** – you can insert multiple charts in the
      same document by calling `insertChart` repeatedly. * **Styling** – use `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`
      to display percentages directly on the chart. * **Performance** – generate the
      chart on'
  - name: What’s next?
    text: '* Explore other chart types (`ChartType.BAR`, `ChartType.LINE`) to broaden
      your automation toolkit. * Combine chart generation with **mail merge** to produce
      personalized reports for each recipient. * Dive into the **Styling API** (`ChartFormat`,
      `DataLabel`, `ChartTitle`) to match your corporate br'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: إنشاء مخطط دائري في Word باستخدام Java – دليل خطوة بخطوة
url: /ar/java/using-document-elements/create-pie-chart-in-word-with-java-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مخطط دائري في Word باستخدام Java – دليل خطوة‑بخطوة

إذا كنت بحاجة إلى **إنشاء مخطط دائري في Word** برمجياً، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك باستخدام Java و Aspose.Words. ستتعلم سير العمل الكامل، من إدراج المخطط إلى إضافة نقاط البيانات وتدوير الشريحة الأولى.

إنشاء مخطط مباشرةً في ملف `.docx` يزيل خطوة النسخ‑اللصق اليدوية ويسمح لك بأتمتة التقارير، الفواتير، أو لوحات المعلومات. خلال الشرح سنغطي أيضاً **كيفية إضافة بيانات السلسلة إلى المخطط** وكيفية **تدوير شريحة المخطط الدائري** للحصول على إبراز بصري أفضل.

## إنشاء مخطط دائري في Word – نظرة عامة

توفر Aspose.Words for Java واجهة برمجة تطبيقات `DocumentBuilder` السلسة التي يمكنها إدراج كائن مخطط في مستند Word. نوع المخطط الذي تختاره يحدد التخطيط الافتراضي، ويمكنك تخصيص السلاسل، الألوان، الزوايا، وحتى التحويل إلى شكل الدونات بنقرة واحدة على طريقة.

### لماذا تستخدم Aspose.Words؟

- **No Microsoft Office required** – المكتبة تعمل على أي خادم أو بيئة CI.  
- **Full .docx fidelity** – المخطط المُولد يبدو مطابقاً تماماً للمخطط الذي يُنشأ يدوياً في Word.  
- **Single‑file dependency** – فقط أضف ملف JAR وستكون جاهزاً للبدء.

## كيفية إضافة بيانات السلسلة إلى المخطط

المخطط بدون بيانات هو مجرد عنصر نائب. كائن `Chart` يعرّف مجموعة `Series`؛ كل سلسلة تحتفظ بقائمة من القيم الرقمية التي ترتبط بالشرائح (للمخطط الدائري) أو النقاط (للمخطط الخطي). إضافة البيانات أمر بسيط:

```java
// Add three values to the first (and only) series of the pie chart
chart.getSeries().get(0).add(40); // 40 % of the whole
chart.getSeries().get(0).add(30); // 30 %
chart.getSeries().get(0).add(30); // remaining 30 %
```

**ما يفعله الكود:**  
* `chart.getSeries()` تُعيد `List<ChartSeries>`.  
* `get(0)` يختار السلسلة الأولى لأن المخطط الدائري يحتوي على سلسلة واحدة فقط حسب التعريف.  
* `add(double)` يضيف نقطة بيانات. القيم تُحوَّل تلقائياً إلى نسب مئوية تُجمع لتصل إلى 100 % عند عرض المخطط.

> **نصيحة احترافية:** إذا كان مصدر البيانات يحتوي على أكثر من ثلاث فئات، استمر في إضافة القيم بنفس الطريقة. ستقوم Aspose.Words بإنشاء شرائح إضافية تلقائياً.

## تدوير شريحة المخطط الدائري

أحياناً قد ترغب في أن تبدأ شريحة معينة بزاوية محددة بحيث يواجه أهم جزء المشاهد. طريقة `setFirstSliceAngle(double)` تدور المخطط بأكمله، مما ينقل فعلياً بداية الشريحة الأولى:

```java
// Rotate the chart so that the first slice starts at 45 degrees
chart.setFirstSliceAngle(45);
```

الزاوية تُقاس بالدرجات في اتجاه عقارب الساعة من المحور العمودي. ضبطها على `0` (القيمة الافتراضية) يضع الشريحة الأولى في الأعلى. عدّل القيمة لتسليط الضوء على شريحة أو لتتوافق مع دليل التصميم.

> **سؤال شائع:** *هل يؤثر التدوير على ترتيب البيانات؟*  
> لا. يبقى ترتيب البيانات كما هو؛ فقط يتغير موقع البداية البصري.

## مثال كامل بلغة Java

فيما يلي برنامج كامل وجاهز للتنفيذ ينشئ مستند Word يحتوي على مخطط دائري، يضيف بيانات السلسلة، يدور الشريحة، ويحفظ الملف. جميع الاستيرادات المطلوبة مُدرجة، بحيث يمكنك نسخ الكود إلى أي بيئة تطوير متكاملة.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartInWord {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a PIE chart with a width of 400 points and a height of 300 points
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Add data points to the first (and only) series
        chart.getSeries().get(0).add(40); // Slice 1
        chart.getSeries().get(0).add(30); // Slice 2
        chart.getSeries().get(0).add(30); // Slice 3

        // 4️⃣ Rotate the start angle so the first slice begins at 45°
        chart.setFirstSliceAngle(45);

        // 5️⃣ (Optional) If you prefer a doughnut chart, uncomment the next line
        // chart.setHoleSize(0.5); // hole size between 0.0 (pie) and 1.0 (empty)

        // 6️⃣ Save the document – adjust the path as needed
        String outPath = "output/PieChart.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### النتيجة المتوقعة

* ملف باسم **PieChart.docx** يظهر في مجلد `output`.  
* فتح الملف في Microsoft Word يعرض مخططاً دائرياً ملوناً بثلاث شرائح (40 ٪، 30 ٪، 30 ٪).  
* المخطط مدور بزاوية 45° في اتجاه عقارب الساعة، لذا تبدأ الشريحة الأولى قليلاً إلى يمين المحور العمودي.

## المشكلات الشائعة وأفضل الممارسات

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| **المخطط يظهر فارغاً** | تم حفظ المستند قبل أن يتم عرض المخطط بالكامل. | استدعِ `doc.save()` **بعد** جميع تعديلات المخطط. |
| **قيم الشرائح لا تُجمع إلى 100 ٪** | إضافة أرقام خام لا تمثل نسب مئوية قد يؤدي إلى تحجيم غير متوقع. | قدِّم قيماً تمثل منطقياً أجزاءً من الكل، أو دع Aspose.Words تحسب النسب مئويًا تلقائيًا. |
| **التدوير لا يؤثر** | استخدام `ChartType.DOUGHNUT` دون ضبط `holeSize` قد يخفي تأثير التدوير. | احتفظ بالمخطط كـ `PIE` أو اضبط `holeSize` بعد ضبط الزاوية. |
| **أخطاء مسار الملف** | قد تُفسَّر المسارات النسبية بشكل مختلف على Windows مقارنةً بـ Linux. | استخدم `Paths.get("output", "PieChart.docx").toString()` أو مسارًا مطلقًا في كود الإنتاج. |

### نصائح للاستخدام في الإنتاج

* **Reuse the `DocumentBuilder`** – يمكنك إدراج مخططات متعددة في نفس المستند عن طريق استدعاء `insertChart` بشكل متكرر.  
* **Styling** – استخدم `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);` لعرض النسب مئويًا مباشرة على المخطط.  
* **Performance** – أنشئ المخطط مرة واحدة ونسّخه (`chart.deepClone()`) إذا كنت تحتاج إلى مخططات متطابقة في عدة مواضع.

## تدوير شريحة المخطط الدائري – سيناريوهات متقدمة

* **Dynamic angle** – احسب الزاوية بناءً على البيانات (مثلاً، اجعل أكبر شريحة تبدأ من الأعلى).  
  ```java
  double maxValue = Collections.max(chart.getSeries().get(0).getDataPoints());
  double total = chart.getSeries().get(0).getDataPoints().stream().mapToDouble(Double::doubleValue).sum();
  double startAngle = 360 * (maxValue / total) / 2; // Center the largest slice
  chart.setFirstSliceAngle(startAngle);
  ```
* **Multiple series** – بينما يحتوي المخطط الدائري عادةً على سلسلة واحدة، تسمح لك Aspose.Words بإضافة المزيد للمخططات المتكدسة. لا يزال التدوير يُطبق على السلسلة الأولى فقط.

## الخلاصة

أنت الآن تعرف كيف **تنشئ مخطط دائري في Word** باستخدام Java، وكيف **تضيف بيانات السلسلة إلى المخطط**، وكيف **تدوّر شريحة المخطط الدائري** لتسليط الضوء بصرياً. يوضح المثال الكامل سير العمل بالكامل—من تهيئة المستند إلى حفظ ملف `.docx` النهائي—حتى تتمكن من دمج إنشاء المخططات في أي خط أنابيب تقارير مؤتمت.

### ما التالي؟

* استكشف أنواع مخططات أخرى (`ChartType.BAR`, `ChartType.LINE`) لتوسيع مجموعة أدوات الأتمتة الخاصة بك.  
* دمج إنشاء المخططات مع **mail merge** لإنتاج تقارير مخصصة لكل مستلم.  
* تعمّق في **Styling API** (`ChartFormat`, `DataLabel`, `ChartTitle`) لتتناسب مع هوية علامتك التجارية.

لا تتردد في تجربة مجموعات بيانات مختلفة، وزوايا، وأنماط مخططات متنوعة. برمجة سعيدة!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف طرق تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء مخطط عمودي باستخدام Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [كيفية إنشاء حقول نموذج وإضافة محتوى باستخدام DocumentBuilder في Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [كيفية تحويل Word إلى PDF باستخدام Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}