---
date: 2025-11-28
description: تعلم كيفية تغيير حدود الخلايا وتنسيق الجداول باستخدام Aspose.Words للغة
  Java. يغطي هذا الدليل خطوة بخطوة تعيين الحدود، وتطبيق نمط العمود الأول، وضبط محتوى
  الجدول تلقائيًا، وتطبيق أنماط الجداول.
linktitle: How to Change Cell Borders in Tables – Aspose.Words for Java
second_title: Aspose.Words Java Document Processing API
title: كيفية تغيير حدود الخلايا في الجداول – Aspose.Words for Java
url: /ar/java/document-conversion-and-export/formatting-tables-and-table-styles/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تغيير حدود الخلايا في الجداول – Aspose.Words for Java

## المقدمة

عند التعامل مع تنسيق المستندات، تلعب الجداول دورًا أساسيًا، و**معرفة كيفية تغيير حدود الخلايا** أمر ضروري لإنشاء تخطيطات واضحة ومهنية. إذا كنت تطور باستخدام Java وAspose.Words، فستمتلك مجموعة أدوات قوية بين يديك. في هذا الدرس سنستعرض العملية الكاملة لتنسيق الجداول، تغيير حدود الخلايا، تطبيق *نمط العمود الأول*، واستخدام *ملاءمة المحتوى تلقائيًا* لجعل مستنداتك تبدو مصقولة.

## إجابات سريعة
- **ما هو الصنف الأساسي لإنشاء الجداول؟** `DocumentBuilder` ينشئ الجداول والخلايا برمجيًا.  
- **كيف أغير سمك حد خلية واحدة؟** استخدم `builder.getCellFormat().getBorders().getLeft().setLineWidth(value)`.  
- **هل يمكنني تطبيق نمط جدول مسبق التعريف؟** نعم – استدعِ `table.setStyleIdentifier(StyleIdentifier.YOUR_STYLE)`.  
- **ما الطريقة التي تجعل الجدول يتلاءم تلقائيًا مع محتواه؟** `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`.  
- **هل أحتاج إلى ترخيص للاستخدام في الإنتاج؟** يلزم وجود ترخيص صالح لـ Aspose.Words للاستخدام غير التجريبي.

## ما المقصود بـ “كيفية تغيير حدود الخلايا” في Aspose.Words؟

تغيير حدود الخلايا يعني تخصيص الخطوط البصرية التي تفصل بين الخلايا—اللون، العرض، ونمط الخط. توفر Aspose.Words واجهة API غنية تتيح لك تعديل هذه الخصائص على مستوى الجدول، الصف، أو الخلية الفردية، مما يمنحك تحكمًا دقيقًا في مظهر مستنداتك.

## لماذا نستخدم Aspose.Words for Java لتنسيق الجداول؟

- **مظهر موحد عبر الأنظمة** – يعمل نفس كود التنسيق على Windows وLinux وmacOS.  
- **لا يعتمد على Microsoft Word** – يمكنك إنشاء أو تعديل المستندات من جانب الخادم.  
- **مكتبة أنماط غنية** – أنماط جداول مدمجة (مثل *نمط العمود الأول*) وإمكانيات ملاءمة تلقائية كاملة.  

## المتطلبات المسبقة

1. **مجموعة تطوير جافا (JDK) 8+** – تأكد من أن `java` موجود في PATH.  
2. **بيئة تطوير** – IntelliJ IDEA أو Eclipse أو أي محرر تفضله.  
3. **Aspose.Words for Java** – حمّل أحدث ملف JAR من [الموقع الرسمي](https://releases.aspose.com/words/java/).  
4. **معرفة أساسية بجافا** – يجب أن تكون مرتاحًا لإنشاء مشروع Maven/Gradle وإضافة ملفات JAR الخارجية.

## استيراد الحزم

لبدء العمل مع الجداول تحتاج إلى فئات Aspose.Words الأساسية:

```java
import com.aspose.words.*;
```

هذا الاستيراد الوحيد يمنحك الوصول إلى `Document`، `DocumentBuilder`، `Table`، `StyleIdentifier`، والعديد من الأدوات الأخرى.

## كيفية تغيير حدود الخلايا

فيما يلي سننشئ جدولًا بسيطًا، نغيّر حدوده العامة، ثم نخصص حدود خلايا فردية.

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
- **تظليل الخلية** – يوضح كيفية تلوين خلايا فردية (أحمر وأخضر).  
- **حدود خلية مخصصة** – الخلية الثالثة تحصل على حد بسمك 4 نقاط من جميع الجوانب، لتبرز بوضوح.

## تطبيق أنماط الجداول (بما في ذلك نمط العمود الأول)

تتيح أنماط الجداول تطبيق مظهر موحد بنقرة واحدة. سنظهر أيضًا كيفية تمكين *نمط العمود الأول* وملاءمة الجدول تلقائيًا مع محتواه.

### الخطوة 4: إنشاء مستند جديد للتنسيق

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// We must insert at least one row first before setting any table formatting.
builder.insertCell();
```

### الخطوة 5: تطبيق نمط مسبق وتمكين تنسيق العمود الأول

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
- **نمط العمود الأول** – إبراز العمود الأول يحسن القابلية للقراءة، خاصة في التقارير.  
- **أشرطة الصفوف** – ألوان الصفوف المتناوبة تجعل الجداول الكبيرة أسهل للعين.  
- **ملاءمة تلقائية** – تضمن أن عرض الجدول يتكيف مع المحتوى، مما يمنع قص النص.

## المشكلات الشائعة & استكشاف الأخطاء

| المشكلة | السبب الشائع | الحل السريع |
|-------|----------------|-----------|
| عدم ظهور الحدود | استخدام `clearFormatting()` بعد تعيين الحدود | عيّن الحدود **بعد** مسح التنسيق، أو أعد تطبيقها. |
| تجاهل التظليل في الخلايا المدمجة | تم تطبيق التظليل قبل الدمج | طبّق التظليل **بعد** دمج الخلايا. |
| عرض الجدول يتجاوز هوامش الصفحة | لم يتم تطبيق ملاءمة تلقائية | استدعِ `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` أو عيّن عرضًا ثابتًا. |
| عدم تطبيق النمط | قيمة `StyleIdentifier` غير صحيحة | تأكد من وجود المعرف في نسخة Aspose.Words التي تستخدمها. |

## الأسئلة المتكررة

**س: هل يمكنني استخدام أنماط جدول مخصصة غير المتوفرة في الخيارات الافتراضية؟**  
ج: نعم، يمكنك إنشاء وتطبيق أنماط مخصصة برمجيًا. راجع [توثيق Aspose.Words](https://reference.aspose.com/words/java/) للمزيد من التفاصيل.

**س: كيف يمكنني تطبيق تنسيق شرطي على الخلايا؟**  
ج: استخدم منطق جافا القياسي لفحص قيم الخلايا، ثم استدعِ طرق التنسيق المناسبة (مثل تغيير لون الخلفية إذا تجاوزت القيمة عتبة معينة).

**س: هل يمكن تنسيق الخلايا المدمجة بنفس طريقة الخلايا العادية؟**  
ج: بالتأكيد. بعد دمج الخلايا، طبّق التظليل أو الحدود باستخدام نفس واجهات `CellFormat`.

**س: ماذا لو أردت أن يتغير حجم الجدول ديناميكيًا بناءً على مدخلات المستخدم؟**  
ج: عدّل عرض الأعمدة أو استدعِ `autoFit` مرة أخرى بعد إدخال بيانات جديدة لإعادة حساب التخطيط.

**س: أين يمكنني العثور على المزيد من أمثلة تنسيق الجداول؟**  
ج: يحتوي [توثيق Aspose.Words API الرسمي](https://reference.aspose.com/words/java/) على مجموعة شاملة من العينات.

## الخلاصة

أصبح لديك الآن مجموعة أدوات كاملة لـ **كيفية تغيير حدود الخلايا**، تطبيق *نمط العمود الأول*، و**ملاءمة محتوى الجدول تلقائيًا** باستخدام Aspose.Words for Java. من خلال إتقان هذه التقنيات يمكنك إنتاج مستندات غنية بالبيانات ومظهرًا جذابًا—مثالية للتقارير، الفواتير، وأي مخرجات تجارية حيوية أخرى.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**آخر تحديث:** 2025-11-28  
**تم الاختبار مع:** Aspose.Words for Java 24.12 (أحدث نسخة وقت الكتابة)  
**المؤلف:** Aspose