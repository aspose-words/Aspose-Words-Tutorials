---
title: جدول منسق
linktitle: جدول منسق
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إنشاء الجداول وتنسيقها في مستندات Word باستخدام Aspose.Words for .NET باستخدام هذا الدليل التفصيلي خطوة بخطوة.
weight: 10
url: /ar/net/programming-with-tables/formatted-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# جدول منسق

## مقدمة

قد يبدو إنشاء الجداول وتنسيقها في مستندات Word برمجيًا مهمة شاقة، ولكن مع Aspose.Words for .NET، تصبح هذه المهمة سهلة ومباشرة. في هذا البرنامج التعليمي، سنوضح لك كيفية إنشاء جدول منسق في مستند Word باستخدام Aspose.Words for .NET. سنغطي كل شيء من إعداد البيئة الخاصة بك إلى حفظ مستندك بجدول منسق بشكل جميل.

## المتطلبات الأساسية

قبل الغوص في الكود، دعنا نتأكد من أن لديك كل ما تحتاجه:

1. مكتبة Aspose.Words لـ .NET: قم بتنزيلها من[هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: بيئة تطوير متكاملة مثل Visual Studio.
3. .NET Framework: تأكد من تثبيت .NET Framework على جهازك.

## استيراد مساحات الأسماء

قبل كتابة الكود الفعلي، يجب عليك استيراد المساحات الأساسية الضرورية:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

## الخطوة 1: إعداد دليل المستندات الخاص بك

أولاً، عليك تحديد المسار الذي سيتم حفظ مستندك فيه.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 يستبدل`"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي الذي تريد حفظ المستند فيه.

## الخطوة 2: تهيئة المستند وDocumentBuilder

الآن، قم بإنشاء مستند جديد وكائن DocumentBuilder.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 ال`DocumentBuilder` هي فئة مساعدة تعمل على تبسيط عملية بناء المستندات.

## الخطوة 3: ابدأ الجدول

 بعد ذلك، ابدأ في إنشاء الجدول باستخدام`StartTable` طريقة.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

إن إدراج خلية أمر ضروري لبدء الجدول.

## الخطوة 4: تطبيق التنسيق على مستوى الجدول

يمكنك تطبيق التنسيق الذي يؤثر على الجدول بأكمله. على سبيل المثال، ضبط المسافة البادئة اليسرى:

```csharp
table.LeftIndent = 20.0;
```

## الخطوة 5: تنسيق صف الرأس

قم بتعيين الارتفاع والمحاذاة والخصائص الأخرى لصف الرأس.

```csharp
builder.RowFormat.Height = 40.0;
builder.RowFormat.HeightRule = HeightRule.AtLeast;
builder.CellFormat.Shading.BackgroundPatternColor = Color.FromArgb(198, 217, 241);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Font.Size = 16;
builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.CellFormat.Width = 100.0;
builder.Write("Header Row,\n Cell 1");
```

في هذه الخطوة، نجعل صف الرأس بارزًا من خلال تعيين لون الخلفية وحجم الخط والمحاذاة.

## الخطوة 6: إدراج خلايا رأسية إضافية

إدراج المزيد من الخلايا لصف الرأس:

```csharp
builder.InsertCell();
builder.Write("Header Row,\n Cell 2");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Header Row,\n Cell 3");
builder.EndRow();
```

## الخطوة 7: تنسيق صفوف النص

بعد إعداد الرأس، قم بتنسيق نص الجدول:

```csharp
builder.CellFormat.Shading.BackgroundPatternColor = Color.White;
builder.CellFormat.Width = 100.0;
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.RowFormat.Height = 30.0;
builder.RowFormat.HeightRule = HeightRule.Auto;
```

## الخطوة 8: إدراج صفوف النص

أدخل صفوف النص مع المحتوى:

```csharp
builder.InsertCell();
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Write("Row 1, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 1, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 1, Cell 3 Content");
builder.EndRow();
```

كرر ذلك للصفوف الإضافية:

```csharp
builder.InsertCell();
builder.CellFormat.Width = 100.0;
builder.Write("Row 2, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 2, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 2, Cell 3 Content.");
builder.EndRow();
builder.EndTable();
```

## الخطوة 9: حفظ المستند

وأخيرًا، قم بحفظ المستند في الدليل المحدد:

```csharp
doc.Save(dataDir + "WorkingWithTables.FormattedTable.docx");
```

سيؤدي هذا إلى إنشاء مستند Word وحفظه بالجدول المنسق.

## خاتمة

والآن، إليك ما تحتاج إليه! باتباع الخطوات التالية، يمكنك إنشاء جدول بتنسيق جيد في مستند Word باستخدام Aspose.Words for .NET. تسهل هذه المكتبة القوية التعامل مع مستندات Word برمجيًا، مما يوفر لك الوقت والجهد.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟
Aspose.Words for .NET عبارة عن مكتبة قوية لإنشاء مستندات Word وتحريرها وتحويلها برمجيًا.

### هل يمكنني استخدام ألوان مختلفة لصفوف مختلفة؟
نعم، يمكنك تطبيق تنسيقات مختلفة، بما في ذلك الألوان، على صفوف أو خلايا مختلفة.

### هل Aspose.Words لـ .NET مجاني؟
 Aspose.Words for .NET هي مكتبة مدفوعة، ولكن يمكنك الحصول عليها[نسخة تجريبية مجانية](https://releases.aspose.com/).

### كيف أحصل على الدعم لـ Aspose.Words لـ .NET؟
 يمكنك الحصول على الدعم من[منتديات مجتمع Aspose](https://forum.aspose.com/c/words/8).

### هل يمكنني إنشاء أنواع أخرى من المستندات باستخدام Aspose.Words لـ .NET؟
نعم، يدعم Aspose.Words for .NET تنسيقات المستندات المختلفة، بما في ذلك PDF، وHTML، وTXT.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
