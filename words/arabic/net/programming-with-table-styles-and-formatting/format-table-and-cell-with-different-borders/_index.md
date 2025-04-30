---
"description": "تعلّم كيفية تنسيق الجداول والخلايا بحدود مختلفة باستخدام Aspose.Words لـ .NET. حسّن مستندات Word الخاصة بك باستخدام أنماط جداول وتظليل خلايا مخصصة."
"linktitle": "تنسيق الجدول والخلايا باستخدام حدود مختلفة"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "تنسيق الجدول والخلايا باستخدام حدود مختلفة"
"url": "/ar/net/programming-with-table-styles-and-formatting/format-table-and-cell-with-different-borders/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تنسيق الجدول والخلايا باستخدام حدود مختلفة

## مقدمة

هل سبق لك أن حاولتَ جعل مستندات Word الخاصة بك تبدو أكثر احترافية من خلال تخصيص حدود الجداول والخلايا؟ إن لم تفعل، فأنتَ على موعد مع متعة حقيقية! سيرشدك هذا البرنامج التعليمي خلال عملية تنسيق الجداول والخلايا بحدود مختلفة باستخدام Aspose.Words لـ .NET. تخيّل أن لديك القدرة على تغيير مظهر جداولك ببضعة أسطر برمجية فقط. هل أثار اهتمامك؟ لنبدأ ونستكشف كيف يمكنك تحقيق ذلك بسهولة.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:
- فهم أساسي لبرمجة C#.
- تم تثبيت Visual Studio على جهاز الكمبيوتر الخاص بك.
- مكتبة Aspose.Words لـ .NET. إذا لم تُثبّتها بعد، يُمكنك تنزيلها. [هنا](https://releases.aspose.com/words/net/).
- ترخيص Aspose ساري المفعول. يمكنك الحصول على نسخة تجريبية مجانية أو ترخيص مؤقت من [هنا](https://purchase.aspose.com/temporary-license/).

## استيراد مساحات الأسماء

للعمل مع Aspose.Words لـ .NET، عليك استيراد مساحات الأسماء اللازمة إلى مشروعك. أضف توجيهات الاستخدام التالية في أعلى ملف الكود:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;
```

## الخطوة 1: تهيئة المستند وDocumentBuilder

أولاً، عليك إنشاء مستند جديد وتهيئة DocumentBuilder، مما يساعد في بناء محتوى المستند. 

```csharp
// المسار إلى دليل المستندات الخاص بك 
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

عيّن حدود الجدول بأكمله. تضمن هذه الخطوة أن يكون لجميع خلايا الجدول نمط حدود متناسق، ما لم يُنص على خلاف ذلك.

```csharp
// تعيين حدود الجدول بأكمله.
table.SetBorders(LineStyle.Single, 2.0, Color.Black);
```

## الخطوة 4: تطبيق تظليل الخلايا

أضف تظليلًا إلى الخلايا لجعلها مميزة بصريًا. في هذا المثال، سنضبط لون خلفية الخلية الأولى إلى الأحمر.


```csharp
// تعيين تظليل الخلية لهذه الخلية.
builder.CellFormat.Shading.BackgroundPatternColor = Color.Red;
builder.Writeln("Cell #1");
```

## الخطوة 5: إدراج خلية أخرى بتظليل مختلف

أدخل الخلية الثانية، ثم طبّق لون تظليل مختلف. هذا يجعل الجدول أكثر تنوعًا وأسهل قراءة.

```csharp
builder.InsertCell();
// حدد تظليل خلية مختلف للخلية الثانية.
builder.CellFormat.Shading.BackgroundPatternColor = Color.Green;
builder.Writeln("Cell #2");
builder.EndRow();
```

## الخطوة 6: مسح تنسيق الخلايا

قم بمسح تنسيق الخلية من العمليات السابقة للتأكد من أن الخلايا التالية لا ترث نفس الأنماط.


```csharp
// مسح تنسيق الخلية من العمليات السابقة.
builder.CellFormat.ClearFormatting();
```

## الخطوة 7: تخصيص الحدود لخلايا محددة

خصّص حدود خلايا محددة لإبرازها. هنا، سنضع حدودًا أكبر للخلية الأولى من الصف الجديد.

```csharp
builder.InsertCell();
// أنشئ حدودًا أكبر للخلية الأولى من هذا الصف. سيكون هذا مختلفًا.
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

ها قد انتهيت! لقد تعلمت للتو كيفية تنسيق الجداول والخلايا بحدود مختلفة باستخدام Aspose.Words لـ .NET. بتخصيص حدود الجداول وتظليل الخلايا، يمكنك تحسين المظهر البصري لمستنداتك بشكل ملحوظ. لذا، جرّب أنماطًا مختلفة، واجعل مستنداتك مميزة!

## الأسئلة الشائعة

### هل يمكنني استخدام أنماط حدود مختلفة لكل خلية؟
نعم، يمكنك تعيين أنماط حدود مختلفة لكل خلية باستخدام `CellFormat.Borders` ملكية.

### كيف يمكنني إزالة كافة الحدود من جدول؟
يمكنك إزالة جميع الحدود عن طريق ضبط نمط الحدود إلى `LineStyle.None`.

### هل من الممكن تعيين ألوان حدود مختلفة لكل خلية؟
بالتأكيد! يمكنك تخصيص لون حدود كل خلية باستخدام `CellFormat.Borders.Color` ملكية.

### هل يمكنني استخدام الصور كخلفيات للخلية؟
على الرغم من أن Aspose.Words لا يدعم الصور كخلفيات للخلايا بشكل مباشر، إلا أنه يمكنك إدراج صورة في خلية وضبط حجمها لتغطية مساحة الخلية.

### كيف أقوم بدمج الخلايا في جدول؟
يمكنك دمج الخلايا باستخدام `CellFormat.HorizontalMerge` و `CellFormat.VerticalMerge` ملكيات.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}