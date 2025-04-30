---
"description": "تعرّف على كيفية تعريف خصائص المحور X وY في مخطط باستخدام Aspose.Words لـ .NET من خلال هذا الدليل المفصل. مثالي لمطوري .NET."
"linktitle": "تحديد خصائص المحور XY في الرسم البياني"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "تحديد خصائص المحور XY في الرسم البياني"
"url": "/ar/net/programming-with-charts/define-xyaxis-properties/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تحديد خصائص المحور XY في الرسم البياني

## مقدمة

المخططات البيانية أداة فعّالة لعرض البيانات. عند الحاجة إلى إنشاء مستندات احترافية بمخططات بيانية ديناميكية، تُعدّ مكتبة Aspose.Words for .NET فعّالة للغاية. ستشرح هذه المقالة عملية تعريف خصائص المحور X-Y في مخطط بياني باستخدام Aspose.Words for .NET، مع شرح مُفصّل لكل خطوة لضمان الوضوح وسهولة الفهم.

## المتطلبات الأساسية

قبل الغوص في الترميز، هناك بعض المتطلبات الأساسية التي يجب أن تكون موجودة:

1. Aspose.Words لـ .NET: تأكد من توفر مكتبة Aspose.Words لـ .NET. يمكنك [قم بتحميله هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: تحتاج إلى بيئة تطوير متكاملة (IDE) مثل Visual Studio.
3. .NET Framework: تأكد من إعداد بيئة التطوير الخاصة بك لتطوير .NET.
4. المعرفة الأساسية بلغة C#: يفترض هذا الدليل أن لديك فهمًا أساسيًا لبرمجة C#.

## استيراد مساحات الأسماء

للبدء، عليك استيراد مساحات الأسماء اللازمة في مشروعك. هذا يضمن لك الوصول إلى جميع الفئات والأساليب اللازمة لإنشاء المستندات والمخططات ومعالجتها.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

سنقوم بتقسيم العملية إلى خطوات بسيطة، تركز كل منها على جزء محدد من تحديد خصائص المحور XY في الرسم البياني.

## الخطوة 1: تهيئة المستند وDocumentBuilder

أولاً، تحتاج إلى تهيئة مستند جديد و `DocumentBuilder` الكائن. `DocumentBuilder` يساعد في إدراج المحتوى في المستند.

```csharp
// المسار إلى دليل المستندات الخاص بك 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## الخطوة 2: إدراج مخطط

بعد ذلك، ستُدرج مخططًا في المستند. في هذا المثال، سنستخدم مخططًا مساحيًا. يمكنك تخصيص أبعاد المخطط حسب الحاجة.

```csharp
// إدراج الرسم البياني
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
Chart chart = shape.Chart;
```

## الخطوة 3: مسح السلسلة الافتراضية وإضافة بيانات مخصصة

افتراضيًا، سيحتوي الرسم البياني على سلاسل بيانات محددة مسبقًا. سنمسحها ونضيف سلسلة البيانات المخصصة.

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
	new DateTime[]
	{
		new DateTime(2002, 01, 01), new DateTime(2002, 06, 01), new DateTime(2002, 07, 01),
		new DateTime(2002, 08, 01), new DateTime(2002, 09, 01)
	},
	new double[] { 640, 320, 280, 120, 150 });
```

## الخطوة 4: تحديد خصائص المحور X

الآن، حان وقت تحديد خصائص المحور X. يتضمن ذلك تحديد نوع الفئة، وتخصيص تقاطع المحور، وتعديل علامات التجزئة والعلامات.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.CategoryType = AxisCategoryType.Category;
xAxis.Crosses = AxisCrosses.Custom;
xAxis.CrossesAt = 3; // يتم قياسها بوحدات العرض على المحور Y (المئات).
xAxis.ReverseOrder = true;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
xAxis.TickLabelOffset = 200;
```

## الخطوة 5: تحديد خصائص المحور Y

وبالمثل، ستُعيّن خصائص المحور Y. يشمل ذلك تحديد موضع علامة التجزئة، والوحدات الرئيسية والثانوية، ووحدة العرض، والقياس.

```csharp
ChartAxis yAxis = chart.AxisY;
yAxis.TickLabelPosition = AxisTickLabelPosition.High;
yAxis.MajorUnit = 100;
yAxis.MinorUnit = 50;
yAxis.DisplayUnit.Unit = AxisBuiltInUnit.Hundreds;
yAxis.Scaling.Minimum = new AxisBound(100);
yAxis.Scaling.Maximum = new AxisBound(700);
```

## الخطوة 6: حفظ المستند

أخيرًا، احفظ المستند في المجلد المُحدد. سيؤدي هذا إلى إنشاء مستند Word بالمخطط المُخصّص.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

## خاتمة

إنشاء وتخصيص المخططات البيانية في مستندات Word باستخدام Aspose.Words لـ .NET سهلٌ للغاية بمجرد فهم الخطوات اللازمة. يشرح هذا الدليل عملية تعريف خصائص المحور X-Y في المخطط، بدءًا من تهيئة المستند وحتى حفظه. بفضل هذه المهارات، يمكنك إنشاء مخططات بيانية مفصلة واحترافية تُحسّن من جودة مستنداتك.

## الأسئلة الشائعة

### ما هي أنواع المخططات البيانية التي يمكنني إنشاؤها باستخدام Aspose.Words لـ .NET؟
يمكنك إنشاء أنواع مختلفة من المخططات البيانية، بما في ذلك المخططات المساحية والشريطية والخطية والدائرية والمزيد.

### كيف أقوم بتثبيت Aspose.Words لـ .NET؟
يمكنك تنزيل Aspose.Words لـ .NET من [هنا](https://releases.aspose.com/words/net/) واتبع تعليمات التثبيت المقدمة.

### هل يمكنني تخصيص مظهر الرسوم البيانية الخاصة بي؟
نعم، يسمح Aspose.Words لـ .NET بالتخصيص الشامل للمخططات، بما في ذلك الألوان والخطوط وخصائص المحور.

### هل هناك نسخة تجريبية مجانية متاحة لـ Aspose.Words لـ .NET؟
نعم، يمكنك الحصول على نسخة تجريبية مجانية [هنا](https://releases.aspose.com/).

### أين يمكنني العثور على المزيد من الدروس والوثائق؟
يمكنك العثور على المزيد من الدروس التعليمية والوثائق التفصيلية على [صفحة توثيق Aspose.Words لـ .NET](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}