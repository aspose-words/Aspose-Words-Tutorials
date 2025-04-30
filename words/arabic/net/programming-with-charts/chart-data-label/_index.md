---
"description": "تعرّف على كيفية تخصيص تسميات بيانات المخططات باستخدام Aspose.Words لـ .NET في دليل خطوة بخطوة. مثالي لمطوري .NET."
"linktitle": "تخصيص تسمية بيانات الرسم البياني"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "تخصيص تسمية بيانات الرسم البياني"
"url": "/ar/net/programming-with-charts/chart-data-label/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تخصيص تسمية بيانات الرسم البياني

## مقدمة

هل ترغب في تحسين تطبيقات .NET لديك بإمكانيات معالجة مستندات ديناميكية ومخصصة؟ قد يكون Aspose.Words for .NET هو الحل الأمثل! في هذا الدليل، سنتعمق في تخصيص تسميات بيانات المخططات باستخدام Aspose.Words for .NET، وهي مكتبة فعّالة لإنشاء مستندات Word وتعديلها وتحويلها. سواء كنت مطورًا محترفًا أو مبتدئًا، سيرشدك هذا البرنامج التعليمي خلال كل خطوة، مما يضمن فهمك لكيفية استخدام هذه الأداة بفعالية.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

1. Visual Studio: قم بتثبيت Visual Studio 2019 أو الإصدار الأحدث.
2. .NET Framework: تأكد من أن لديك .NET Framework 4.0 أو إصدار أحدث.
3. Aspose.Words لـ .NET: قم بتنزيل Aspose.Words لـ .NET وتثبيته من [رابط التحميل](https://releases.aspose.com/words/net/).
4. المعرفة الأساسية بلغة C#: المعرفة ببرمجة C# أمر ضروري.
5. رخصة صالحة: الحصول على [رخصة مؤقتة](https://purchase.aspose.com/temporary-license/) أو شراء واحدة من [رابط الشراء](https://purchase.aspose.com/buy).

## استيراد مساحات الأسماء

للبدء، عليك استيراد مساحات الأسماء اللازمة إلى مشروع C# الخاص بك. هذه الخطوة بالغة الأهمية لأنها تضمن لك الوصول إلى جميع الفئات والأساليب التي يوفرها Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Charts;
```

## الخطوة 1: تهيئة المستند وDocumentBuilder

لإنشاء مستندات Word ومعالجتها، نحتاج أولاً إلى تهيئة مثيل لـ `Document` الصف و `DocumentBuilder` هدف.

```csharp
// المسار إلى دليل المستندات الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### توضيح

- مستند doc: إنشاء مثيل جديد لفئة المستند.
- منشئ DocumentBuilder: يساعد DocumentBuilder في إدراج المحتوى في كائن المستند.

## الخطوة 2: إدراج مخطط

بعد ذلك، سنقوم بإدراج مخطط شريطي في المستند باستخدام `DocumentBuilder` هدف.

```csharp
Shape shape = builder.InsertChart(ChartType.Bar, 432, 252);
Chart chart = shape.Chart;
```

### توضيح

- الشكل الشكل: يمثل الرسم البياني كشكل في المستند.
- builder.InsertChart(ChartType.Bar، 432، 252): يقوم بإدراج مخطط شريطي بأبعاد محددة.

## الخطوة 3: الوصول إلى سلسلة المخططات

لتخصيص تسميات البيانات، نحتاج أولاً إلى الوصول إلى السلسلة في الرسم البياني.

```csharp
ChartSeries series0 = shape.Chart.Series[0];
```

### توضيح

- ChartSeries series0: استرداد السلسلة الأولى من الرسم البياني، والتي سنقوم بتخصيصها.

## الخطوة 4: تخصيص تسميات البيانات

يمكن تخصيص تسميات البيانات لعرض معلومات متنوعة. سنقوم بضبط التسميات لعرض مفتاح الأسطورة، واسم السلسلة، والقيمة، مع إخفاء اسم الفئة والنسبة المئوية.

```csharp
ChartDataLabelCollection labels = series0.DataLabels;
labels.ShowLegendKey = true;
labels.ShowLeaderLines = true;
labels.ShowCategoryName = false;
labels.ShowPercentage = false;
labels.ShowSeriesName = true;
labels.ShowValue = true;
labels.Separator = "/";
```

### توضيح

- تسميات ChartDataLabelCollection: الوصول إلى تسميات البيانات الخاصة بالسلسلة.
- labels.ShowLegendKey: يعرض مفتاح الأسطورة.
- labels.ShowLeaderLines: يعرض خطوط القيادة لعلامات البيانات الموضوعة بعيدًا عن نقاط البيانات.
- labels.ShowCategoryName: إخفاء اسم الفئة.
- labels.ShowPercentage: إخفاء قيمة النسبة المئوية.
- labels.ShowSeriesName: يعرض اسم السلسلة.
- labels.ShowValue: يعرض قيمة نقاط البيانات.
- labels.Separator: تعيين الفاصل لعلامات البيانات.

## الخطوة 5: حفظ المستند

وأخيرًا، قم بحفظ المستند في الدليل المحدد.

```csharp
doc.Save(dataDir + "WorkingWithCharts.ChartDataLabel.docx");
```

### توضيح

- doc.Save: يحفظ المستند بالاسم المحدد في الدليل المقدم.

## خاتمة

تهانينا! لقد نجحت في تخصيص تسميات بيانات المخططات باستخدام Aspose.Words لـ .NET. توفر هذه المكتبة حلاً فعالاً للتعامل مع مستندات Word برمجيًا، مما يُسهّل على المطورين إنشاء تطبيقات معالجة مستندات متطورة وديناميكية. تعمق في [التوثيق](https://reference.aspose.com/words/net/) لاستكشاف المزيد من الميزات والقدرات.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟
Aspose.Words for .NET هي مكتبة معالجة مستندات قوية تسمح للمطورين بإنشاء مستندات Word وتعديلها وتحويلها برمجيًا.

### كيف أقوم بتثبيت Aspose.Words لـ .NET؟
يمكنك تنزيله وتثبيته من [رابط التحميل](https://releases.aspose.com/words/net/). اتبع تعليمات التثبيت المقدمة.

### هل يمكنني تجربة Aspose.Words for .NET مجانًا؟
نعم يمكنك الحصول على [نسخة تجريبية مجانية](https://releases.aspose.com/) أو أ [رخصة مؤقتة](https://purchase.aspose.com/temporary-license/) لتقييم المنتج.

### هل Aspose.Words for .NET متوافق مع .NET Core؟
نعم، Aspose.Words for .NET متوافق مع .NET Core، و.NET Standard، و.NET Framework.

### أين يمكنني الحصول على الدعم لـ Aspose.Words لـ .NET؟
يمكنك زيارة [منتدى الدعم](https://forum.aspose.com/c/words/8) للحصول على المساعدة والمساعدة من مجتمع Aspose والخبراء.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}