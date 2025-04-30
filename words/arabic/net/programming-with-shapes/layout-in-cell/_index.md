---
"description": "تعرّف على كيفية ضبط تخطيط الخلية باستخدام Aspose.Words لـ .NET من خلال هذا الدليل الشامل. مثالي للمطورين الذين يرغبون في تخصيص مستندات Word."
"linktitle": "التخطيط في الخلية"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "التخطيط في الخلية"
"url": "/ar/net/programming-with-shapes/layout-in-cell/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# التخطيط في الخلية

## مقدمة

إذا كنت ترغب في ضبط تخطيط خلايا جدولك في مستندات Word برمجيًا، فأنت في المكان المناسب. سنتناول اليوم كيفية ضبط تخطيط الخلايا باستخدام Aspose.Words لـ .NET. سنشرح مثالًا عمليًا خطوة بخطوة ليسهل عليك متابعته.

## المتطلبات الأساسية

قبل أن ننتقل إلى الكود، دعنا نتأكد من أن لديك كل ما تحتاجه:

1. Aspose.Words لـ .NET: تأكد من تثبيت مكتبة Aspose.Words لـ .NET. إذا لم تكن مثبتة، يمكنك [قم بتحميله هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: ستحتاج إلى بيئة تطوير مُعدّة باستخدام .NET. يُعدّ Visual Studio خيارًا ممتازًا إذا كنت تبحث عن توصيات.
3. المعرفة الأساسية بلغة C#: على الرغم من أنني سأشرح كل خطوة، إلا أن الفهم الأساسي للغة C# سيساعدك على المتابعة بسهولة أكبر.
4. دليل المستندات: جهّز مسارًا للدليل الذي ستحفظ فيه مستنداتك. سنشير إلى هذا باسم `YOUR DOCUMENT DIRECTORY`.

## استيراد مساحات الأسماء

للبدء، تأكد من استيراد المساحات الأساسية اللازمة في مشروعك:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

دعونا نقسم العملية إلى خطوات قابلة للإدارة.

## الخطوة 1: إنشاء مستند جديد

أولاً، سنقوم بإنشاء مستند Word جديد وبدء تشغيله `DocumentBuilder` كائن لمساعدتنا في إنشاء المحتوى الخاص بنا.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## الخطوة 2: بدء جدول وتعيين تنسيق الصف

سنبدأ بإنشاء جدول وتحديد الارتفاع وقاعدة الارتفاع للصفوف.

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## الخطوة 3: إدراج الخلايا وملئها بالمحتوى

بعد ذلك، نستخدم حلقة لإدراج خلايا في الجدول. لكل 7 خلايا، ننهي الصف لإنشاء صف جديد.

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

الآن، لنُضِف علامة مائية إلى مستندنا. سنُنشئ `Shape` الكائن وتعيين خصائصه.

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

سنقوم بتخصيص مظهر العلامة المائية بشكل أكبر عن طريق تعيين خصائص اللون والنص الخاصة بها.

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

لضمان التوافق، سنقوم بتحسين المستند ليتناسب مع Word 2010.

```csharp
doc.CompatibilityOptions.OptimizeFor(MsWordVersion.Word2010);
```

## الخطوة 8: حفظ المستند

وأخيرًا، سنقوم بحفظ مستندنا في الدليل المحدد.

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## خاتمة

وها أنت ذا! لقد نجحت في إنشاء مستند Word بتصميم جدول مُخصّص وإضافة علامة مائية باستخدام Aspose.Words لـ .NET. يهدف هذا البرنامج التعليمي إلى تقديم دليل واضح خطوة بخطوة لمساعدتك على فهم كل جزء من العملية. بفضل هذه المهارات، يمكنك الآن إنشاء مستندات Word أكثر تطورًا وتخصيصًا برمجيًا.

## الأسئلة الشائعة

### هل يمكنني استخدام خط مختلف لنص العلامة المائية؟
نعم، يمكنك تغيير الخط عن طريق ضبط `watermark.TextPath.FontFamily` الخاصية للخط المطلوب.

### كيف أقوم بتعديل موضع العلامة المائية؟
يمكنك تعديل `RelativeHorizontalPosition`، `RelativeVerticalPosition`، `HorizontalAlignment`، و `VerticalAlignment` خصائص لتعديل موضع العلامة المائية.

### هل من الممكن استخدام صورة بدلاً من النص للعلامة المائية؟
بالتأكيد! يمكنك إنشاء `Shape` مع النوع `ShapeType.Image` وضبط صورته باستخدام `ImageData.SetImage` طريقة.

### هل يمكنني إنشاء جداول ذات ارتفاعات صفوف مختلفة؟
نعم، يمكنك تعيين ارتفاعات مختلفة لكل صف عن طريق تغيير `RowFormat.Height` الخاصية قبل إدراج الخلايا في هذا الصف.

### كيف يمكنني إزالة العلامة المائية من المستند؟
يمكنك إزالة العلامة المائية من خلال تحديد موقعها في مجموعة أشكال المستند واستدعاء `Remove` طريقة.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}