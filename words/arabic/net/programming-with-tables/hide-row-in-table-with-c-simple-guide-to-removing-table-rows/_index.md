---
category: general
date: 2026-02-21
description: إخفاء صف في جدول باستخدام C# و Aspose.Words. تعلم كيفية إخفاء صف، وكيفية
  إخفاء صف في Word، وإزالة الصف من الجدول بسرعة وأمان.
draft: false
keywords:
- hide row in table
- how to hide row
- remove row from table
- hide row in word
- hide row c#
language: ar
og_description: إخفاء صف في جدول باستخدام C# و Aspose.Words. يوضح هذا الدليل كيفية
  إخفاء الصف، إزالة الصف من الجدول، وإخفاء الصف في مستندات Word.
og_title: إخفاء صف في جدول باستخدام C# – طريقة سريعة وموثوقة
tags:
- C#
- Aspose.Words
- Word Automation
title: إخفاء صف في جدول باستخدام C# – دليل بسيط لإزالة صفوف الجدول
url: /ar/net/programming-with-tables/hide-row-in-table-with-c-simple-guide-to-removing-table-rows/
---

while generating a Word document programmatically? ..." translate.

Be careful with **bold**.

Also keep code block placeholders.

Proceed step by step.

Will produce final Arabic markdown.

Let's craft translation.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إخفاء صف في جدول – دليل C# كامل

هل احتجت يوماً إلى **إخفاء صف في جدول** أثناء إنشاء مستند Word برمجياً؟ لست وحدك—المطورون يسألون باستمرار *كيف يمكن إخفاء صف* دون كسر التخطيط. الخبر السار؟ ببضع أسطر من C# ومكتبة Aspose.Words القوية، يمكنك إخفاء صف، مما يجعله غير ظاهر في النتيجة النهائية، مع الحفاظ على نظافة الكود.

في هذا الدليل سنستعرض العملية بالكامل: تحميل ملف `.docx`، اختيار الصف المحدد، ضبط خاصية `Hidden`، ثم حفظ النتيجة. بنهاية القراءة ستعرف بالضبط كيف تُخفي صفًا في Word، وكيف تُزيل صفًا من الجدول إذا فضلت الحذف، وستحصل على مقتطف جاهز للتنفيذ يمكنك إدراجه في أي مشروع .NET. لا حاجة لمراجع خارجية—فقط الكود والشروحات الواضحة.

**ما ستحصل عليه**  
- شرح خطوة بخطوة لواجهة برمجة تطبيقات C#.  
- كود كامل قابل للتنفيذ (مع الاستيرادات).  
- نصائح لحالات الحافة مثل الصفوف المخفية في الخلايا المدمجة.  
- نصائح احترافية حول متى تستخدم *إخفاء صف* ومتى تستخدم *إزالة صف من الجدول*.

> **المتطلبات المسبقة:** Visual Studio (أو أي بيئة تطوير C#) وحزمة NuGet الخاصة بـ Aspose.Words for .NET (الإصدار 23.9 أو أحدث). إذا كنت جديدًا على Aspose.Words، فالمكتبة حل مُدار بالكامل—لا تحتاج إلى تثبيت Office.

---

## إخفاء صف في جدول – تنفيذ خطوة بخطوة

فيما يلي المثال الكامل المستقل. يوضح المهمة **الرئيسية**—*إخفاء صف في جدول*—ويظهر أيضًا كيف يمكنك *إزالة صف من الجدول* إذا قررت حذفه بدلاً من إخفائه.

![Hide row in table example](hide-row-in-table.png "Screenshot showing a Word table with the third row hidden")

### 1. تحميل المستند المصدر  

أولاً، نحتاج إلى جلب ملف Word إلى الذاكرة. تمثل فئة `Document` الملف بالكامل.

```csharp
using Aspose.Words;

// Step 1: Load the source document
Document doc = new Document(@"C:\MyDocs\input.docx");
```

*لماذا هذا مهم:* تحميل المستند يمنحك الوصول إلى الأقسام، والجسم، والجداول. بدون هذه الخطوة لا يمكنك تعديل الصفوف على الإطلاق.

### 2. تحديد الجدول المطلوب  

للتبسيط نأخذ أول جدول في القسم الأول، لكن يمكنك البحث حسب الفهرس أو الاسم أو حتى المحتوى.

```csharp
// Step 2: Get the first table in the document body
Table table = doc.FirstSection.Body.Tables[0];
```

> **نصيحة:** إذا كان المستند يحتوي على جداول متعددة، استخدم `doc.GetChildNodes(NodeType.Table, true)` وتكرار النتائج لاختيار الجدول المناسب.

### 3. اختيار الصف الذي تريد إخفائه  

هنا نستهدف الصف الثالث (فهرس صفر‑مبني `2`). يمكنك أيضًا استخدام `Rows.Count` للتحقق من وجود الفهرس.

```csharp
// Step 3: Choose the row you want to hide (third row, index 2)
Row rowToHide = table.Rows[2];
```

*لماذا هذا مهم:* اختيار الصف الصحيح هو جوهر **كيفية إخفاء صف**. اختيار فهرس خاطئ سيؤدي إلى إخفاء محتوى غير مقصود.

### 4. إخفاء الصف المحدد  

ضبط `Hidden = true` يخبر Aspose.Words بتجاهل الصف عند حفظ المستند. يظل الصف موجودًا في نموذج الكائن، لذا يمكنك إلغاء إخفائه لاحقًا إذا لزم الأمر.

```csharp
// Step 4: Hide the selected row – it will be omitted from the output
rowToHide.Hidden = true;
```

> **نصيحة احترافية:** إذا كنت تريد حقًا *إزالة صف من الجدول* بدلاً من إخفائه، استدعِ `table.Rows.Remove(rowToHide);`. الإخفاء يحافظ على بيانات الصف، وهو مفيد للتنسيق الشرطي.

### 5. حفظ المستند المحدث  

أخيرًا، اكتب التغييرات إلى القرص.

```csharp
// Step 5: Save the document with the hidden row applied
doc.Save(@"C:\MyDocs\output.docx");
```

عند فتح `output.docx` في Word، سيصبح الصف الثالث غير مرئي—وهذا هو ما يعنيه **إخفاء صف في Word** عمليًا.

---

## كيفية إخفاء صف – تنويعات شائعة وحالات حافة

### إخفاء عدة صفوف  

إذا احتجت إلى إخفاء عدة صفوف، كرر عبر المجموعة:

```csharp
int[] rowsToHide = { 1, 3, 5 }; // zero‑based indexes
foreach (int i in rowsToHide)
{
    table.Rows[i].Hidden = true;
}
```

### التعامل مع الخلايا المدمجة  

صف مخفي يحتوي على خلية مدمجة عموديًا قد يسبب تحذيرات تخطيط. النهج الآمن هو فك الدمج قبل الإخفاء:

```csharp
Cell mergedCell = rowToHide.Cells[0];
if (mergedCell.CellFormat.VerticalMerge != CellMerge.None)
{
    // Break the merge to avoid Word warnings
    mergedCell.CellFormat.VerticalMerge = CellMerge.None;
}
rowToHide.Hidden = true;
```

### التوافق مع إصدارات Word القديمة  

Aspose.Words يكتب السمة `w:hideMark`، والتي تفهمها Word 2007+ وLibreOffice. إذا كنت تستهدف Word 97‑2003 (`.doc`)، سيظل الصف المخفي غير ظاهر، لكن الجداول المعقدة قد تُظهر اختلافًا في العرض. استخدم `.docx` للحصول على نتائج متوقعة.

### متى تستخدم *إخفاء صف* ومتى تستخدم *إزالة صف من الجدول*  

- **إخفاء صف** – احتفظ بالصف لإمكانية إظهاره لاحقًا، واحفظ ارتفاع الصف لحسابات فواصل الصفحات.  
- **إزالة صف** – قلل حجم الملف، واحذف البيانات نهائيًا. استخدم `table.Rows.Remove(row)` إذا كنت متأكدًا أن الصف لن يُحتاج مرة أخرى.

---

## نصائح احترافية وملاحظات

- **نصيحة احترافية:** دائمًا تحقق من `table.Rows.Count` قبل الوصول إلى فهرس لتجنب `ArgumentOutOfRangeException`.  
- **احذر من:** الصفوف المخفية لا تزال تشارك في حسابات الجدول مثل الارتفاع الكلي. إذا لاحظت مسافات غير متوقعة، فكر في ضبط `row.Height = 0` بعد الإخفاء.  
- **الأداء:** إخفاء الصفوف عملية خفيفة؛ إزالة الصفوف تتطلب إعادة تخطيط كامل للجدول، ما قد يكون أبطأ في المستندات الضخمة.  
- **الاختبار:** افتح الملف المحفوظ في Word واستخدم **Reveal Formatting** (`Shift+F1`) للتحقق من ضبط علامة `Hidden` للصف.

---

## مثال كامل جاهز للتنفيذ (انسخه‑ألصقه)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;

class HideRowInTableDemo
{
    static void Main()
    {
        // Load the source document (ensure the path exists)
        Document doc = new Document(@"C:\MyDocs\input.docx");

        // Get the first table – adapt if you have multiple tables
        Table table = doc.FirstSection.Body.Tables[0];

        // Verify we have at least three rows
        if (table.Rows.Count < 3)
        {
            Console.WriteLine("The table doesn't have a third row to hide.");
            return;
        }

        // Choose the third row (index 2) and hide it
        Row rowToHide = table.Rows[2];
        rowToHide.Hidden = true; // This hides the row in the output document

        // Save the modified document
        doc.Save(@"C:\MyDocs\output.docx");
        Console.WriteLine("Row hidden successfully. Check output.docx.");
    }
}
```

**النتيجة المتوقعة:** افتح `output.docx` وسترى الجدول بدون الصف الثالث، بينما يبقى باقي المحتوى دون تغيير. الصف المخفي لا يزال جزءًا من نموذج المستند، لذا يمكنك لاحقًا ضبط `row.Hidden = false` لجعله مرئيًا مرة أخرى.

---

## الخلاصة

لقد غطينا للتو **كيفية إخفاء صف** في جدول Word باستخدام C#. عبر تحميل المستند، تحديد الجدول، اختيار الصف المستهدف، تعيينه كمخفي، ثم حفظه، تحصل على عملية إخفاء صف نظيفة دون حذف البيانات. يمكنك أيضًا تطبيق نفس النمط لـ *إزالة صف من الجدول* إذا كنت تحتاج إلى تعديل دائم، وتضمن النصائح الإضافية تجنب المشكلات الشائعة مع الخلايا المدمجة أو إصدارات Word القديمة.

هل أنت مستعد للتحدي التالي؟ جرّب دمج هذه التقنية مع منطق شرطي—إخفاء الصفوف بناءً على مدخلات المستخدم، أو إنشاء تقارير ديناميكية حيث تختفي أقسام معينة تلقائيًا. يمكنك أيضًا استكشاف **إخفاء صف في Word** للرؤوس، التذييلات، أو حتى الأقسام الكاملة.

هل لديك أسئلة حول *إخفاء صف C#* أو تحتاج مساعدة في دمجه في سير عمل أكبر؟ اترك تعليقًا أدناه أو اطلع على دروسنا المرتبطة حول **معالجة الجداول في Word باستخدام Aspose.Words**. برمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}