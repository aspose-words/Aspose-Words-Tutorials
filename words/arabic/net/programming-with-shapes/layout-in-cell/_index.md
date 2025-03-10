---
title: التخطيط في الخلية
linktitle: التخطيط في الخلية
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية تعيين التخطيط في الخلية باستخدام Aspose.Words for .NET من خلال هذا الدليل الشامل. مثالي للمطورين الذين يتطلعون إلى تخصيص مستندات Word.
weight: 10
url: /ar/net/programming-with-shapes/layout-in-cell/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# التخطيط في الخلية

## مقدمة

إذا كنت ترغب في ضبط تخطيط خلايا الجدول في مستندات Word برمجيًا، فأنت في المكان المناسب. اليوم، سنتناول كيفية ضبط التخطيط في الخلية باستخدام Aspose.Words for .NET. سنستعرض مثالاً عمليًا، وسنشرحه خطوة بخطوة حتى تتمكن من متابعته بسهولة.

## المتطلبات الأساسية

قبل أن ننتقل إلى الكود، دعنا نتأكد من أن لديك كل ما تحتاجه:

1.  Aspose.Words for .NET: تأكد من تثبيت مكتبة Aspose.Words for .NET. إذا لم تكن قد قمت بذلك، يمكنك[تحميله هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: ستحتاج إلى بيئة تطوير مُجهزة بـ .NET. يُعد Visual Studio خيارًا رائعًا إذا كنت تبحث عن توصيات.
3. المعرفة الأساسية بلغة C#: على الرغم من أنني سأشرح كل خطوة، إلا أن الفهم الأساسي للغة C# سيساعدك على المتابعة بسهولة أكبر.
4.  دليل المستندات: قم بإعداد مسار الدليل الذي ستحفظ فيه مستنداتك. سنشير إلى هذا باسم`YOUR DOCUMENT DIRECTORY`.

## استيراد مساحات الأسماء

للبدء، تأكد من استيراد المساحات الأساسية الضرورية في مشروعك:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

دعونا نقسم العملية إلى خطوات قابلة للإدارة.

## الخطوة 1: إنشاء مستند جديد

 أولاً، سنقوم بإنشاء مستند Word جديد وبدء تشغيله`DocumentBuilder` كائن يساعدنا في إنشاء المحتوى الخاص بنا.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## الخطوة 2: إنشاء جدول وتعيين تنسيق الصف

سنبدأ بإنشاء جدول وتحديد الارتفاع وقاعدة الارتفاع للصفوف.

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## الخطوة 3: إدراج الخلايا وملئها بالمحتوى

بعد ذلك، نقوم بتكرار إدخال الخلايا في الجدول. لكل 7 خلايا، سنقوم بإنهاء الصف لإنشاء صف جديد.

```csharp
for (int i = 0; i < 31; i++)
{
    if (i != 0 && i % 7 == 0) builder.EndRow();
    builder.InsertCell();
    builder.Write("Cell contents");
}
builder.EndTable();
```

## الخطوة 4: إضافة شكل العلامة المائية

 الآن، دعنا نضيف علامة مائية إلى مستندنا. سننشئ علامة مائية`Shape` الكائن وتعيين خصائصه.

```csharp
Shape watermark = new Shape(doc, ShapeType.TextPlainText)
{
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    RelativeVerticalPosition = RelativeVerticalPosition.Page,
    IsLayoutInCell = true, // عرض الشكل خارج خلية الجدول إذا كان سيتم وضعه داخل خلية.
    Width = 300,
    Height = 70,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Rotation = -40
};
```

## الخطوة 5: تخصيص مظهر العلامة المائية

سنقوم بتخصيص مظهر العلامة المائية بشكل أكبر عن طريق ضبط خصائص اللون والنص.

```csharp
watermark.FillColor = Color.Gray;
watermark.StrokeColor = Color.Gray;
watermark.TextPath.Text = "watermarkText";
watermark.TextPath.FontFamily = "Arial";
watermark.Name = $"WaterMark_{Guid.NewGuid()}";
watermark.WrapType = WrapType.None;
```

## الخطوة 6: إدراج العلامة المائية في المستند

سنقوم بالبحث عن آخر تشغيل في المستند وإدراج العلامة المائية في هذا الموضع.

```csharp
Run run = doc.GetChildNodes(NodeType.Run, true)[doc.GetChildNodes(NodeType.Run, true).Count - 1] as Run;
builder.MoveTo(run);
builder.InsertNode(watermark);
```

## الخطوة 7: تحسين المستند لبرنامج Word 2010

لضمان التوافق، سنقوم بتحسين المستند لـ Word 2010.

```csharp
doc.CompatibilityOptions.OptimizeFor(MsWordVersion.Word2010);
```

## الخطوة 8: حفظ المستند

وأخيرًا، سنقوم بحفظ مستندنا في الدليل المحدد.

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## خاتمة

والآن، لقد نجحت في إنشاء مستند Word بتخطيط جدول مخصص وإضافة علامة مائية باستخدام Aspose.Words for .NET. يهدف هذا البرنامج التعليمي إلى تقديم دليل واضح خطوة بخطوة لمساعدتك على فهم كل جزء من العملية. باستخدام هذه المهارات، يمكنك الآن إنشاء مستندات Word أكثر تعقيدًا وتخصيصًا برمجيًا.

## الأسئلة الشائعة

### هل يمكنني استخدام خط مختلف لنص العلامة المائية؟
 نعم، يمكنك تغيير الخط عن طريق ضبط`watermark.TextPath.FontFamily` الخاصية للخط المطلوب.

### كيف أقوم بتعديل موضع العلامة المائية؟
 يمكنك تعديل`RelativeHorizontalPosition`, `RelativeVerticalPosition`, `HorizontalAlignment` ، و`VerticalAlignment` خصائص لتعديل موضع العلامة المائية.

### هل من الممكن استخدام صورة بدلاً من النص للعلامة المائية؟
 بالتأكيد! يمكنك إنشاء`Shape` مع النوع`ShapeType.Image` وضبط صورته باستخدام`ImageData.SetImage` طريقة.

### هل يمكنني إنشاء جداول ذات ارتفاعات صفوف مختلفة؟
نعم، يمكنك تعيين ارتفاعات مختلفة لكل صف عن طريق تغيير`RowFormat.Height` الخاصية قبل إدراج الخلايا في هذا الصف.

### كيف يمكنني إزالة العلامة المائية من المستند؟
 يمكنك إزالة العلامة المائية من خلال تحديد موقعها في مجموعة أشكال المستند واستدعاء`Remove` طريقة.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
