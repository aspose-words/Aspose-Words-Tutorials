---
title: تنسيق الجدول والخلايا باستخدام حدود مختلفة
linktitle: تنسيق الجدول والخلايا باستخدام حدود مختلفة
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية تنسيق الجداول والخلايا باستخدام حدود مختلفة باستخدام Aspose.Words for .NET. قم بتعزيز مستندات Word الخاصة بك باستخدام أنماط الجداول المخصصة وتظليل الخلايا.
weight: 10
url: /ar/net/programming-with-table-styles-and-formatting/format-table-and-cell-with-different-borders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تنسيق الجدول والخلايا باستخدام حدود مختلفة

## مقدمة

هل سبق لك أن حاولت جعل مستندات Word الخاصة بك تبدو أكثر احترافية من خلال تخصيص حدود الجداول والخلايا؟ إذا لم تفعل ذلك، فأنت على موعد مع متعة لا تُنسى! سيرشدك هذا البرنامج التعليمي خلال عملية تنسيق الجداول والخلايا بحدود مختلفة باستخدام Aspose.Words for .NET. تخيل أن لديك القدرة على تغيير مظهر الجداول الخاصة بك باستخدام بضعة أسطر فقط من التعليمات البرمجية. هل أنت مهتم؟ دعنا نتعمق في الأمر ونستكشف كيف يمكنك تحقيق ذلك بسهولة.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:
- فهم أساسي لبرمجة C#.
- تم تثبيت Visual Studio على جهاز الكمبيوتر الخاص بك.
-  مكتبة Aspose.Words لـ .NET. إذا لم تقم بتثبيتها بعد، يمكنك تنزيلها[هنا](https://releases.aspose.com/words/net/).
-  ترخيص Aspose صالح. يمكنك الحصول على نسخة تجريبية مجانية أو ترخيص مؤقت من[هنا](https://purchase.aspose.com/temporary-license/).

## استيراد مساحات الأسماء

للعمل مع Aspose.Words لـ .NET، تحتاج إلى استيراد المساحات الأساسية اللازمة إلى مشروعك. أضف التعليمات التالية باستخدام التعليمات البرمجية في أعلى ملف التعليمات البرمجية الخاص بك:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;
```

## الخطوة 1: تهيئة المستند وDocumentBuilder

أولاً، يتعين عليك إنشاء مستند جديد وتهيئة DocumentBuilder، مما يساعد في بناء محتوى المستند. 

```csharp
// المسار إلى دليل المستند الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## الخطوة 2: البدء في إنشاء جدول

بعد ذلك، استخدم DocumentBuilder لبدء إنشاء جدول وإدراج الخلية الأولى.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

## الخطوة 3: تعيين حدود الجدول

قم بتعيين حدود الجدول بأكمله. تضمن هذه الخطوة أن جميع الخلايا داخل الجدول لها نمط حدود متسق ما لم يتم تحديد خلاف ذلك.

```csharp
// تعيين حدود الجدول بأكمله.
table.SetBorders(LineStyle.Single, 2.0, Color.Black);
```

## الخطوة 4: تطبيق تظليل الخلايا

قم بتطبيق التظليل على الخلايا لجعلها مميزة بصريًا. في هذا المثال، سنقوم بتعيين لون خلفية الخلية الأولى إلى اللون الأحمر.


```csharp
// تعيين تظليل الخلية لهذه الخلية.
builder.CellFormat.Shading.BackgroundPatternColor = Color.Red;
builder.Writeln("Cell #1");
```

## الخطوة 5: إدراج خلية أخرى بتظليل مختلف

أدخل الخلية الثانية وقم بتطبيق لون تظليل مختلف. سيؤدي هذا إلى جعل الجدول أكثر لونًا وأسهل للقراءة.

```csharp
builder.InsertCell();
// حدد تظليل خلية مختلف للخلية الثانية.
builder.CellFormat.Shading.BackgroundPatternColor = Color.Green;
builder.Writeln("Cell #2");
builder.EndRow();
```

## الخطوة 6: مسح تنسيق الخلية

قم بمسح تنسيق الخلية من العمليات السابقة للتأكد من أن الخلايا التالية لا ترث نفس الأنماط.


```csharp
// مسح تنسيق الخلية من العمليات السابقة.
builder.CellFormat.ClearFormatting();
```

## الخطوة 7: تخصيص الحدود لخلايا محددة

قم بتخصيص حدود خلايا معينة لجعلها بارزة. هنا، سنقوم بتعيين حدود أكبر للخلية الأولى في الصف الجديد.

```csharp
builder.InsertCell();
// إنشاء حدود أكبر للخلية الأولى من هذا الصف. سيكون هذا مختلفًا
// مقارنة بالحدود المحددة للجدول.
builder.CellFormat.Borders.Left.LineWidth = 4.0;
builder.CellFormat.Borders.Right.LineWidth = 4.0;
builder.CellFormat.Borders.Top.LineWidth = 4.0;
builder.CellFormat.Borders.Bottom.LineWidth = 4.0;
builder.Writeln("Cell #3");
```

## الخطوة 8: إدراج الخلية النهائية

قم بإدراج الخلية الأخيرة وتأكد من مسح تنسيقها، حتى تستخدم أنماط الجدول الافتراضية.

```csharp
builder.InsertCell();
builder.CellFormat.ClearFormatting();
builder.Writeln("Cell #4");
```

## الخطوة 9: حفظ المستند

وأخيرًا، قم بحفظ المستند في الدليل المحدد.

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.FormatTableAndCellWithDifferentBorders.docx");
```

## خاتمة

والآن، لقد تعلمت للتو كيفية تنسيق الجداول والخلايا باستخدام حدود مختلفة باستخدام Aspose.Words for .NET. من خلال تخصيص حدود الجدول وتظليل الخلايا، يمكنك تحسين المظهر المرئي لمستنداتك بشكل كبير. لذا، امض قدمًا، وجرِّب أنماطًا مختلفة، واجعل مستنداتك مميزة!

## الأسئلة الشائعة

### هل يمكنني استخدام أنماط حدود مختلفة لكل خلية؟
 نعم، يمكنك تعيين أنماط حدود مختلفة لكل خلية باستخدام`CellFormat.Borders` ملكية.

### كيف يمكنني إزالة جميع الحدود من جدول؟
 يمكنك إزالة جميع الحدود عن طريق ضبط نمط الحدود على`LineStyle.None`.

### هل من الممكن تعيين ألوان حدود مختلفة لكل خلية؟
 بالتأكيد! يمكنك تخصيص لون الحدود لكل خلية باستخدام`CellFormat.Borders.Color` ملكية.

### هل يمكنني استخدام الصور كخلفيات للخلية؟
رغم أن Aspose.Words لا يدعم الصور كخلفيات للخلايا بشكل مباشر، إلا أنه يمكنك إدراج صورة في خلية وضبط حجمها لتغطية مساحة الخلية.

### كيف أقوم بدمج الخلايا في جدول؟
 يمكنك دمج الخلايا باستخدام`CellFormat.HorizontalMerge` و`CellFormat.VerticalMerge` ملكيات.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
