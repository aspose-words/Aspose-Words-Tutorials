---
title: إخفاء محور الرسم البياني في مستند Word
linktitle: إخفاء محور الرسم البياني في مستند Word
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إخفاء محور الرسم البياني في مستند Word باستخدام Aspose.Words لـ .NET من خلال البرنامج التعليمي المفصل خطوة بخطوة.
weight: 10
url: /ar/net/programming-with-charts/hide-chart-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إخفاء محور الرسم البياني في مستند Word

## مقدمة

غالبًا ما يتضمن إنشاء مستندات Word ديناميكية وجذابة بصريًا دمج المخططات والرسوم البيانية. قد يتطلب أحد هذه السيناريوهات إخفاء محور المخطط للحصول على عرض أنظف. يوفر Aspose.Words for .NET واجهة برمجة تطبيقات شاملة وسهلة الاستخدام لمثل هذه المهام. سيرشدك هذا البرنامج التعليمي خلال الخطوات اللازمة لإخفاء محور مخطط في مستند Word باستخدام Aspose.Words for .NET.

## المتطلبات الأساسية

قبل أن نتعمق في البرنامج التعليمي، تأكد من أن لديك المتطلبات الأساسية التالية:

-  Aspose.Words for .NET: يمكنك تنزيله من[هنا](https://releases.aspose.com/words/net/).
- بيئة التطوير: أي بيئة تطوير متكاملة تدعم تطوير .NET، مثل Visual Studio.
- .NET Framework: تأكد من تثبيت .NET Framework على جهازك.
- المعرفة الأساسية بلغة C#: ستكون المعرفة بلغة البرمجة C# مفيدة.

## استيراد مساحات الأسماء

للبدء في العمل باستخدام Aspose.Words لـ .NET، تحتاج إلى استيراد المساحات المطلوبة في مشروعك. إليك كيفية القيام بذلك:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

دعونا نقوم بتقسيم العملية إلى خطوات بسيطة وسهلة المتابعة.

## الخطوة 1: تهيئة المستند وDocumentBuilder

تتضمن الخطوة الأولى إنشاء مستند Word جديد وتهيئة كائن DocumentBuilder.

```csharp
// المسار إلى دليل المستند الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 في هذه الخطوة، نقوم بتحديد المسار الذي سيتم حفظ المستند فيه. ثم نقوم بإنشاء ملف جديد`Document` كائن و`DocumentBuilder` كائن لبدء بناء مستندنا.

## الخطوة 2: إدراج مخطط

 بعد ذلك، سنقوم بإدراج مخطط في المستند باستخدام`DocumentBuilder` هدف.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

 هنا، نقوم بإدراج مخطط عمودي بأبعاد محددة.`InsertChart` الطريقة تعيد`Shape` الكائن الذي يحتوي على الرسم البياني.

## الخطوة 3: مسح السلسلة الموجودة

قبل إضافة بيانات جديدة إلى الرسم البياني، نحتاج إلى مسح أي سلسلة موجودة.

```csharp
chart.Series.Clear();
```

تضمن هذه الخطوة إزالة أي بيانات افتراضية في الرسم البياني، مما يفسح المجال للبيانات الجديدة التي سنضيفها بعد ذلك.

## الخطوة 4: إضافة بيانات السلسلة

الآن، دعونا نضيف سلسلة البيانات الخاصة بنا إلى الرسم البياني.

```csharp
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2 });
```

في هذه الخطوة، نضيف سلسلة بعنوان "سلسلة Aspose 1" مع الفئات والقيم المقابلة لها.

## الخطوة 5: إخفاء المحور Y

 لإخفاء المحور Y للرسم البياني، قمنا ببساطة بتعيين`Hidden` خاصية المحور Y لـ`true`.

```csharp
chart.AxisY.Hidden = true;
```

يقوم هذا السطر من التعليمات البرمجية بإخفاء المحور Y، مما يجعله غير مرئي في الرسم البياني.

## الخطوة 6: حفظ المستند

وأخيرًا، قم بحفظ المستند في الدليل المحدد.

```csharp
doc.Save(dataDir + "WorkingWithCharts.HideChartAxis.docx");
```

يقوم هذا الأمر بحفظ مستند Word الذي يحتوي على الرسم البياني في المسار المحدد.

## خاتمة

مبروك! لقد نجحت في تعلم كيفية إخفاء محور الرسم البياني في مستند Word باستخدام Aspose.Words for .NET. تسهل هذه المكتبة القوية التعامل مع مستندات Word برمجيًا. باتباع الخطوات التالية، يمكنك إنشاء مستندات مخصصة وذات مظهر احترافي بأقل جهد.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟
Aspose.Words for .NET عبارة عن واجهة برمجة تطبيقات قوية لإنشاء مستندات Word وتحريرها وتحويلها ومعالجتها داخل تطبيقات .NET.

### هل يمكنني إخفاء المحورين X وY في الرسم البياني؟
 نعم، يمكنك إخفاء كلا المحورين عن طريق ضبط`Hidden` ممتلكات كل منهما`AxisX` و`AxisY` ل`true`.

### هل هناك نسخة تجريبية مجانية متاحة لـ Aspose.Words لـ .NET؟
 نعم، يمكنك الحصول على نسخة تجريبية مجانية[هنا](https://releases.aspose.com/).

### أين يمكنني العثور على مزيد من الوثائق؟
 يمكنك العثور على وثائق مفصلة على Aspose.Words لـ .NET[هنا](https://reference.aspose.com/words/net/).

### كيف يمكنني الحصول على الدعم لـ Aspose.Words لـ .NET؟
 يمكنك الحصول على الدعم من مجتمع Aspose[هنا](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
