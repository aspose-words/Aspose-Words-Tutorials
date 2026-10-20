---
date: 2026-10-17
description: تعلم كيفية تغيير الحدود في خلايا الجدول باستخدام Aspose.Words for Java،
  بما في ذلك ضبط أنماط حدود الخلية، وتطبيق نمط العمود الأول، وتكييف محتوى الجدول تلقائيًا.
keywords:
- how to change borders
- apply first column style
- Aspose.Words table styling
- Java document processing
lastmod: 2026-10-17
linktitle: كيفية تغيير الحدود في خلايا الجدول باستخدام Aspose.Words for Java
og_description: كيفية تغيير الحدود في خلايا الجدول باستخدام Aspose.Words for Java.
  يوضح هذا الدليل كيفية ضبط سمك حدود الخلية، وتطبيق نمط العمود الأول، وتكييف الجداول
  تلقائيًا لإنشاء مستندات احترافية.
og_image_alt: Screenshot of a Java table with customized cell borders using Aspose.Words
og_title: كيفية تغيير الحدود في خلايا الجدول – Aspose.Words for Java
schemas:
- author: Aspose
  dateModified: '2026-10-17'
  description: Learn how to change borders in table cells with Aspose.Words for Java,
    including setting cell border styles, applying first column style, and auto‑fit
    table contents.
  headline: How to change borders in table cells using Aspose.Words for Java
  type: TechArticle
- description: Learn how to change borders in table cells with Aspose.Words for Java,
    including setting cell border styles, applying first column style, and auto‑fit
    table contents.
  name: How to change borders in table cells using Aspose.Words for Java
  steps:
  - name: '**Java Development Kit (JDK) 8+** – ensure `java` is on your PATH.'
    text: '**Java Development Kit (JDK) 8+** – ensure `java` is on your PATH.'
  - name: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
    text: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
  - name: '**Aspose.Words for Java** – download the latest JAR from the [official
      site](https://releases.aspose.com/words/java/).'
    text: '**Aspose.Words for Java** – download the latest JAR from the [official
      site](https://releases.aspose.com/words/java/).'
  - name: '**Basic Java knowledge** – you should be comfortable creating a Maven/Gradle
      project and adding external JARs.'
    text: '**Basic Java knowledge** – you should be comfortable creating a Maven/Gradle
      project and adding external JARs.'
  type: HowTo
- questions:
  - answer: Yes, you can create and apply custom styles programmatically. See the
      [Aspose.Words documentation](https://reference.aspose.com/words/java/) for details.
    question: Can I use custom table styles not included in the default options?
  - answer: Use standard Java logic to inspect cell values, then call the appropriate
      formatting methods (e.g., change background colour if a value exceeds a threshold).
    question: How can I apply conditional formatting to cells?
  - answer: Absolutely. After merging cells, apply shading or borders using the same
      `CellFormat` APIs.
    question: Is it possible to format merged cells the same way as regular cells?
  - answer: Adjust column widths or call `autoFit` again after inserting new data
      to recalculate the layout.
    question: What if I need the table to resize dynamically based on user input?
  - answer: The official [Aspose.Words API documentation](https://reference.aspose.com/words/java/)
      contains a comprehensive set of samples.
    question: Where can I find more examples of table styling?
  type: FAQPage
second_title: Aspose.Words Java Document Processing API
tags:
- Aspose.Words
- Java tables
- document formatting
- border styling
title: كيفية تغيير الحدود في خلايا الجدول باستخدام Aspose.Words for Java
url: /ar/java/document-conversion-and-export/formatting-tables-and-table-styles/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تغيير الحدود في خلايا الجدول باستخدام Aspose.Words for Java

## مقدمة

عند الحاجة إلى عرض البيانات بتصميم نظيف ومهني، **تغيير حدود الخلايا** هو أحد أولى التعديلات البصرية التي ستطبقها. في Java، توفر لك Aspose.Words واجهة برمجة تطبيقات كاملة تسمح لك بتنسيق الجداول، وضبط حدود خلية واحدة، وتمكين نمط العمود الأول، وضبط المحتوى تلقائيًا بحيث لا يتجاوز الجدول الصفحة. يشرح هذا الدرس كل خطوة، من إنشاء المستند إلى ضبط كل حد، ويظهر لماذا هذه الميزات مهمة في التقارير والفواتير الواقعية.

## إجابات سريعة
يُستخدم الصنف `DocumentBuilder` لبناء المستندات والجداول برمجيًا.  
- **ما هو الصنف الأساسي لإنشاء الجداول؟** `DocumentBuilder` ينشئ الجداول والخلايا برمجيًا.  
- **كيف يمكنني تغيير سمك حد خلية واحدة؟** استخدم `builder.getCellFormat().getBorders().getLeft().setLineWidth(value)`.  
- **هل يمكنني تطبيق نمط جدول مُعرّف مسبقًا؟** نعم – استدعِ `table.setStyleIdentifier(StyleIdentifier.YOUR_STYLE)`.  
- **ما الطريقة التي تضبط الجدول تلقائيًا وفق محتواه؟** `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`.  
- **هل أحتاج إلى ترخيص للاستخدام في الإنتاج؟** يلزم وجود ترخيص صالح لـ Aspose.Words للاستخدام غير التجريبي.

## ما هو “كيفية تغيير حدود الخلايا” في Aspose.Words؟

تغيير حدود الخلايا يعني تخصيص الخطوط البصرية التي تفصل بين الخلايا—اللون، العرض، ونمط الخط. تُظهر Aspose.Words for Java واجهة برمجة تطبيقات دقيقة تسمح لك بتعيين هذه الخصائص على مستوى الجدول أو الصف أو الخلية الفردية، مما يمنحك تحكمًا دقيقًا في مظهر مستنداتك.

## لماذا تستخدم تنسيق الجداول في Aspose.Words for Java؟

تدعم Aspose.Words **أكثر من 35 تنسيقًا للإدخال والإخراج** (DOCX، PDF، HTML، ODT، إلخ) ويمكنها معالجة **مستندات تصل إلى 500 صفحة في أقل من 3 ثوانٍ** على خوادم عادية دون الحاجة إلى Microsoft Word. تعمل المكتبة بثبات على Windows وLinux وmacOS، مما يتيح لك إنشاء أو تعديل المستندات من جانب الخادم، وتطبيق أنماط الجداول المدمجة مثل *نمط العمود الأول*، وضبط الجداول تلقائيًا للمحتوى باستدعاء طريقة واحدة.

## المتطلبات المسبقة

1. **مجموعة تطوير جافا (JDK) 8+** – تأكد من أن `java` موجود في PATH.  
2. **بيئة تطوير متكاملة** – IntelliJ IDEA، Eclipse، أو أي محرر تفضله.  
3. **Aspose.Words for Java** – حمّل أحدث ملف JAR من [الموقع الرسمي](https://releases.aspose.com/words/java/).  
4. **معرفة أساسية بجافا** – يجب أن تكون قادرًا على إنشاء مشروع Maven/Gradle وإضافة ملفات JAR الخارجية.

## استيراد الحزم

الصنوف `Document`، `DocumentBuilder`، `Table`، `StyleIdentifier` وغيرها تتواجد في مساحة الاسم `com.aspose.words`. استيراد هذه الحزمة الواحدة يمنحك الوصول إلى مجموعة أدوات تنسيق الجداول بالكامل. يوفر الصنف `DocumentBuilder` طرقًا لإنشاء وتعديل المستند برمجيًا.

```java
import com.aspose.words.*;
```

## كيفية تغيير حدود الخلايا

فيما يلي دليل مختصر خطوة بخطوة ينشئ جدولًا، يطبق حدًا عالميًا، ثم يخصص حدود خلية واحدة.

### إجابة مباشرة
`Document` يمثل ملف Word، بينما `DocumentBuilder` ينشئ محتوى مثل الجداول. حمّل `Document` جديدًا، أدخل `Table` باستخدام `DocumentBuilder`، عيّن حدًا أسود بسمك نقطتين للجدول بأكمله، ثم زد حدود اليسار واليمين والأعلى والأسفل للخلية الثالثة إلى 4 نقاط. يتيح لك هذا النهج إبراز أي خلية مع الحفاظ على تنسيق موحد لبقية الجدول.

### الخطوة 1: تحميل مستند جديد

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### الخطوة 2: إنشاء الجدول وتعيين الحدود العامة

```java
Table table = builder.startTable();
builder.insertCell();

// Set the borders for the entire table.
table.setBorders(LineStyle.SINGLE, 2.0, Color.BLACK);
        
// Set the cell shading for this cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.RED);
builder.writeln("Cell #1");

builder.insertCell();
        
// Specify a different cell shading for the second cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.GREEN);
builder.writeln("Cell #2");

builder.endRow();
```

### الخطوة 3: تغيير حدود خلية واحدة

```java
// Clear the cell formatting from previous operations.
builder.getCellFormat().clearFormatting();

builder.insertCell();

// Create larger borders for the first cell of this row.
builder.getCellFormat().getBorders().getLeft().setLineWidth(4.0);
builder.getCellFormat().getBorders().getRight().setLineWidth(4.0);
builder.getCellFormat().getBorders().getTop().setLineWidth(4.0);
builder.getCellFormat().getBorders().getBottom().setLineWidth(4.0);
builder.writeln("Cell #3");

builder.insertCell();
builder.getCellFormat().clearFormatting();
builder.writeln("Cell #4");
        
doc.save("FormatTableAndCellWithDifferentBorders.docx");
```

#### ما يفعله الكود
- **الحدود العامة** – `table.setBorders` يمنح الجدول بأكمله خطًا أسود بسمك نقطتين.  
- **تظليل الخلايا** – يوضح كيفية تلوين خلايا فردية (أحمر وأخضر).  
- **حدود الخلية المخصصة** – الخلية الثالثة تحصل على حد بسمك 4 نقاط من جميع الجوانب، مما يجعلها بارزة.

## تطبيق أنماط الجداول (بما في ذلك نمط العمود الأول)

تسمح لك أنماط الجداول بتطبيق مظهر موحد باستدعاء واحد. سنقوم أيضًا بتمكين *نمط العمود الأول* وضبط الجدول تلقائيًا ليتناسب مع محتواه.

### إجابة مباشرة
`StyleIdentifier` يعدد الأنماط المدمجة للجداول، و`AutoFitBehavior` يتحكم في كيفية تعديل الجدول لمحتواه. أنشئ `Document` جديدًا، ابنِ `Table`، عيّن `StyleIdentifier` إلى `MEDIUM_SHADING_1_ACCENT_1`، فعّل `FirstColumn` و`RowBands`، ثم استدعِ `autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` لتقليص أو توسيع الأعمدة تلقائيًا لتناسب البيانات المدخلة.

### الخطوة 4: إنشاء مستند جديد للتنسيق

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// We must insert at least one row first before setting any table formatting.
builder.insertCell();
```

### الخطوة 5: تطبيق نمط مُعرّف مسبقًا وتمكين تنسيق العمود الأول

```java
// Set the table style based on a unique style identifier.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Apply which features should be formatted by the style.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);

// Auto‑fit the table so columns shrink or expand to fit the content.
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### الخطوة 6: ملء الجدول بالبيانات

```java
builder.writeln("Item");
builder.getCellFormat().setRightPadding(40.0);
builder.insertCell();
builder.writeln("Quantity (kg)");
builder.endRow();

builder.insertCell();
builder.writeln("Apples");
builder.insertCell();
builder.writeln("20");
builder.endRow();

builder.insertCell();
builder.writeln("Bananas");
builder.insertCell();
builder.writeln("40");
builder.endRow();

builder.insertCell();
builder.writeln("Carrots");
builder.insertCell();
builder.writeln("50");
builder.endRow();

doc.save("BuildTableWithStyle.docx");
```

#### لماذا هذا مهم
- **معرف النمط** – `MEDIUM_SHADING_1_ACCENT_1` يمنح الجدول مظهرًا نظيفًا ومظللاً.  
- **نمط العمود الأول** – إبراز العمود الأول يحسن القراءة، خاصة في التقارير.  
- **تظليل الصفوف** – ألوان الصفوف المتناوبة تجعل الجداول الكبيرة أسهل للعين.  
- **الضبط التلقائي** – يضمن أن عرض الجدول يتكيف مع المحتوى، مما يمنع قص النص.

## المشكلات الشائعة & استكشاف الأخطاء وإصلاحها

| Issue | Typical cause | Quick fix |
|-------|----------------|-----------|
| Borders not appearing | Using `clearFormatting()` after setting borders | Set borders **after** clearing formatting, or re‑apply them. |
| Shading ignored on merged cells | Shading applied before merging | Apply shading **after** merging the cells. |
| Table width exceeds page margins | No auto‑fit applied | Call `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` or set a fixed width. |
| Style not applied | Wrong `StyleIdentifier` value | Verify the identifier exists in the version of Aspose.Words you’re using. |

## الأسئلة المتكررة

**س: هل يمكنني استخدام أنماط جدول مخصصة غير موجودة في الخيارات الافتراضية؟**  
ج: نعم، يمكنك إنشاء وتطبيق أنماط مخصصة برمجيًا. راجع [توثيق Aspose.Words](https://reference.aspose.com/words/java/) للمزيد من التفاصيل.

**س: كيف يمكنني تطبيق تنسيق شرطي على الخلايا؟**  
ج: استخدم منطق جافا القياسي لفحص قيم الخلايا، ثم استدعِ طرق التنسيق المناسبة (مثل تغيير لون الخلفية إذا تجاوزت القيمة عتبة معينة).

**س: هل يمكن تنسيق الخلايا المدمجة بنفس طريقة الخلايا العادية؟**  
ج: بالتأكيد. بعد دمج الخلايا، طبّق التظليل أو الحدود باستخدام نفس واجهات `CellFormat`.

**س: ماذا لو أردت أن يتغير حجم الجدول ديناميكيًا بناءً على إدخال المستخدم؟**  
ج: عدّل عرض الأعمدة أو استدعِ `autoFit` مرة أخرى بعد إدخال بيانات جديدة لإعادة حساب التخطيط.

**س: أين يمكنني العثور على المزيد من أمثلة تنسيق الجداول؟**  
ج: يحتوي [توثيق Aspose.Words API الرسمي](https://reference.aspose.com/words/java/) على مجموعة شاملة من العينات.

## الخاتمة

أصبح لديك الآن مجموعة أدوات كاملة **لتغيير الحدود** في خلايا الجداول، وتطبيق *نمط العمود الأول*، و**ضبط محتوى الجدول تلقائيًا** باستخدام Aspose.Words for Java. من خلال إتقان هذه التقنيات يمكنك إنتاج مستندات غنية بالبيانات ومظهرها مصقول—مثالية للتقارير، الفواتير، وأي مخرجات تجارية حيوية.

---

**Last Updated:** 2026-10-17  
**Tested With:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Author:** Aspose

## دروس ذات صلة

- [دروس تنسيق الأنماط في Aspose.Words Java - تحسين مستنداتك](/words/java/formatting-styles/)
- [دليل شامل حول حدود المستند المتقدمة مع Aspose.Words for Java](/words/java/headers-footers-page-setup/advanced-document-borders-aspose-words-java/)
- [إضافة علامة مائية إلى مستند باستخدام Aspose.Words for Java](/words/java/document-conversion-and-export/using-watermarks-to-documents/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}