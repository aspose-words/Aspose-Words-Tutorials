---
"description": "تعرّف على كيفية إدراج الجداول مباشرةً في مستندات Word باستخدام Aspose.Words لـ .NET. اتبع دليلنا المفصل خطوة بخطوة لتبسيط عملية إنشاء مستنداتك."
"linktitle": "إدراج الجدول مباشرة"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "إدراج الجدول مباشرة"
"url": "/ar/net/programming-with-tables/insert-table-directly/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إدراج الجدول مباشرة

## مقدمة
إنشاء الجداول برمجيًا قد يكون تحديًا كبيرًا، خاصةً عند التعامل مع هياكل مستندات معقدة. لكن لا تقلق، نحن هنا لشرحها لك بالتفصيل! في هذا الدليل، سنشرح خطوات إدراج جدول مباشرةً في مستند Word باستخدام Aspose.Words لـ .NET. سواء كنت مطورًا متمرسًا أو مبتدئًا، سيساعدك هذا البرنامج التعليمي على إتقان العملية بسهولة.

## المتطلبات الأساسية

قبل البدء بشرح الكود، تأكد من توفر كل ما تحتاجه للبدء. إليك قائمة مرجعية سريعة:

1. مكتبة Aspose.Words لـ .NET: تأكد من تنزيل مكتبة Aspose.Words لـ .NET وتثبيتها. يمكنك الحصول عليها من [صفحة التحميل](https://releases.aspose.com/words/net/).
2. بيئة التطوير: بيئة تطوير مثل Visual Studio.
3. المعرفة الأساسية بلغة C#: فهم أساسيات برمجة C#.
4. دليل المستندات: مسار الدليل الذي ستحفظ فيه مستنداتك.

مع توفر هذه المتطلبات الأساسية، فأنت جاهز لبدء الترميز!

## استيراد مساحات الأسماء

أولاً، لنستورد مساحات الأسماء اللازمة. ستوفر لنا هذه المساحات الفئات والأساليب اللازمة للعمل مع مستندات Word.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

الآن بعد أن أصبح لدينا مساحات الأسماء في مكانها، دعنا ننتقل إلى الجزء المثير للاهتمام - إنشاء الجداول وإدراجها مباشرة في مستند Word.

## الخطوة 1: إعداد المستند

لنبدأ بإعداد مستند وورد جديد. هنا سيتم إدراج جدولنا.

```csharp
// المسار إلى دليل المستندات الخاص بك 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

هذا الكود يُنشئ مستند وورد جديد. ستحتاج إلى استبداله `"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي إلى دليل المستند الخاص بك.

## الخطوة 2: إنشاء كائن الجدول

بعد ذلك، سننشئ كائن الجدول. هنا سنحدد بنية الجدول.

```csharp
// نبدأ بإنشاء كائن الجدول. لاحظ أنه يجب علينا تمرير كائن المستند
// إلى مُنشئ كل عقدة. وذلك لأن كل عقدة ننشئها يجب أن تنتمي إلى
// إلى بعض المستندات.
Table table = new Table(doc);
doc.FirstSection.Body.AppendChild(table);
```

هنا، نقوم بإنشاء جدول جديد وإضافته إلى نص القسم الأول من مستندنا.

## الخطوة 3: إضافة الصفوف والخلايا

يتكون الجدول من صفوف وخلايا. لنبدأ بإضافة هذه العناصر تدريجيًا.

### إضافة صف

```csharp
// هنا يمكننا استدعاء EnsureMinimum لإنشاء الصفوف والخلايا. تُستخدم هذه الطريقة
// للتأكد من صحة العقدة المحددة. في هذه الحالة، يجب أن يحتوي الجدول الصحيح على صف واحد وخلية واحدة على الأقل.
// بدلاً من ذلك، سنتعامل مع إنشاء الصف والجدول بأنفسنا.
// ستكون هذه هي الطريقة الأفضل للقيام بذلك إذا كنا نقوم بإنشاء جدول داخل خوارزمية.
Row row = new Row(doc);
row.RowFormat.AllowBreakAcrossPages = true;
table.AppendChild(row);
```

يقوم هذا الكود بإنشاء صف جديد وإضافته إلى جدولنا.

### إضافة خلايا إلى الصف

الآن، دعونا نضيف بعض الخلايا إلى صفنا. 

```csharp
Cell cell = new Cell(doc);
cell.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
cell.CellFormat.Width = 80;
cell.AppendChild(new Paragraph(doc));
cell.FirstParagraph.AppendChild(new Run(doc, "Row 1, Cell 1 Text"));
row.AppendChild(cell);
```

في هذا المقطع، ننشئ خلية، ونضبط لون خلفيتها على الأزرق الفاتح، ونحدد عرضها. ثم نضيف فقرة وامتدادًا إلى الخلية لاحتواء النص.

## الخطوة 4: استنساخ الخلايا

لتسريع عملية إضافة الخلايا، يمكننا استنساخ الخلايا الموجودة.

```csharp
// ثم نكرر العملية للخلايا والصفوف الأخرى في الجدول.
// يمكننا أيضًا تسريع الأمور عن طريق استنساخ الخلايا والصفوف الموجودة.
row.AppendChild(cell.Clone(false));
row.LastCell.AppendChild(new Paragraph(doc));
row.LastCell.FirstParagraph.AppendChild(new Run(doc, "Row 1, Cell 2 Text"));
```

يستنسخ هذا الكود الخلية الموجودة ويضيفها إلى الصف. ثم نضيف فقرة وسلسلة نصية إلى الخلية الجديدة.

## الخطوة 5: تطبيق إعدادات الملاءمة التلقائية

أخيرًا، دعنا نطبق إعدادات الملاءمة التلقائية على جدولنا للتأكد من أن الأعمدة لها عرض ثابت.

```csharp
// يمكننا الآن تطبيق أي إعدادات ملائمة تلقائياً.
table.AutoFit(AutoFitBehavior.FixedColumnWidths);
```

## الخطوة 6: حفظ المستند

بعد إعداد جدولنا بالكامل، حان الوقت لحفظ المستند.

```csharp
doc.Save(dataDir + "WorkingWithTables.InsertTableDirectly.docx");
```

يحفظ هذا الكود المستند مع الجدول المدرج.

## خاتمة

تهانينا! لقد نجحت في إدراج جدول مباشرةً في مستند Word باستخدام Aspose.Words for .NET. يمكن استخدام هذه العملية لإنشاء جداول معقدة برمجيًا، مما يُسهّل مهام أتمتة مستنداتك بشكل كبير. سواء كنت تُنشئ تقارير أو فواتير أو أي نوع آخر من المستندات، فإن فهم كيفية التعامل مع الجداول مهارة أساسية.

## الأسئلة الشائعة

### كيف يمكنني تنزيل Aspose.Words لـ .NET؟
يمكنك تنزيل Aspose.Words for .NET من [صفحة التحميل](https://releases.aspose.com/words/net/).

### هل يمكنني تجربة Aspose.Words لـ .NET قبل الشراء؟
نعم يمكنك طلب [نسخة تجريبية مجانية](https://releases.aspose.com/) لتقييم المكتبة قبل الشراء.

### كيف يمكنني شراء Aspose.Words لـ .NET؟
يمكنك شراء Aspose.Words لـ .NET من [صفحة الشراء](https://purchase.aspose.com/buy).

### أين يمكنني العثور على الوثائق الخاصة بـ Aspose.Words لـ .NET؟
الوثائق متاحة [هنا](https://reference.aspose.com/words/net/).

### ماذا لو كنت بحاجة إلى الدعم أثناء استخدام Aspose.Words لـ .NET؟
للحصول على الدعم، يمكنك زيارة [منتدى Aspose.Words](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}