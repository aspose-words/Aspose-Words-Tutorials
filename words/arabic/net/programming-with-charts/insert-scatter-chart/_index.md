---
title: إدراج مخطط التشتت في مستند Word
linktitle: إدراج مخطط التشتت في مستند Word
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إدراج مخطط تشتت في Word باستخدام Aspose.Words for .NET. خطوات سهلة لدمج التمثيلات المرئية للبيانات في مستنداتك.
weight: 10
url: /ar/net/programming-with-charts/insert-scatter-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إدراج مخطط التشتت في مستند Word

## مقدمة

في هذا البرنامج التعليمي، ستتعلم كيفية الاستفادة من Aspose.Words for .NET لإدراج مخطط تشتت في مستند Word الخاص بك. المخططات التشتتية هي أدوات بصرية قوية يمكنها عرض نقاط البيانات بشكل فعال استنادًا إلى متغيرين، مما يجعل مستنداتك أكثر جاذبية وإفادة.

## المتطلبات الأساسية

قبل أن نتعمق في إنشاء مخططات التشتت باستخدام Aspose.Words لـ .NET، تأكد من توفر المتطلبات الأساسية التالية:

1.  تثبيت Aspose.Words لـ .NET: قم بتنزيل Aspose.Words لـ .NET وتثبيته من[هنا](https://releases.aspose.com/words/net/).
   
2. المعرفة الأساسية بلغة C#: ستكون المعرفة بلغة البرمجة C# وإطار عمل .NET مفيدة.

## استيراد مساحات الأسماء

للبدء، تحتاج إلى استيراد المساحات الأساسية اللازمة في مشروع C# الخاص بك:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
```

الآن، دعنا نوضح عملية إدراج مخطط التشتت في مستند Word الخاص بك باستخدام Aspose.Words لـ .NET:

## الخطوة 1: تهيئة المستند وDocumentBuilder

 أولاً، قم بتهيئة مثيل جديد من`Document` الصف و`DocumentBuilder` الفئة لبدء بناء مستندك.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## الخطوة 2: إدراج مخطط التشتت

 استخدم`InsertChart` طريقة`DocumentBuilder` فئة لإدراج مخطط تشتت في المستند.

```csharp
Shape shape = builder.InsertChart(ChartType.Scatter, 432, 252);
Chart chart = shape.Chart;
```

## الخطوة 3: إضافة سلسلة البيانات إلى الرسم البياني

الآن، أضف سلسلة بيانات إلى مخطط التشتت الخاص بك. يوضح هذا المثال إضافة سلسلة تحتوي على نقاط بيانات محددة.

```csharp
chart.Series.Add("Aspose Series 1", new double[] { 0.7, 1.8, 2.6 }, new double[] { 2.7, 3.2, 0.8 });
```

## الخطوة 4: حفظ المستند

 أخيرًا، احفظ المستند المعدّل في الموقع المطلوب باستخدام`Save` طريقة`Document` فصل.

```csharp
doc.Save(dataDir + "WorkingWithCharts.InsertScatterChart.docx");
```

## خاتمة

تهانينا! لقد نجحت في تعلم كيفية إدراج مخطط تشتت في مستند Word الخاص بك باستخدام Aspose.Words for .NET. تعد المخططات التشتتية أدوات ممتازة لتصور علاقات البيانات، وباستخدام Aspose.Words، يمكنك دمجها بسهولة في مستنداتك لتعزيز الوضوح والفهم.

## الأسئلة الشائعة

### هل يمكنني تخصيص مظهر الرسم البياني المبعثر باستخدام Aspose.Words؟
نعم، يسمح Aspose.Words بتخصيص واسع النطاق لخصائص الرسم البياني مثل الألوان والمحاور والعلامات.

### هل Aspose.Words متوافق مع الإصدارات المختلفة من Microsoft Word؟
يدعم Aspose.Words إصدارات مختلفة من Microsoft Word، مما يضمن التوافق عبر الأنظمة الأساسية.

### هل يوفر Aspose.Words الدعم لأنواع أخرى من المخططات البيانية؟
نعم، يدعم Aspose.Words مجموعة واسعة من أنواع المخططات بما في ذلك المخططات الشريطية، والمخططات الخطية، والمخططات الدائرية.

### هل يمكنني تحديث البيانات في مخطط التشتت ديناميكيًا برمجيًا؟
بالتأكيد، يمكنك تحديث بيانات الرسم البياني بشكل ديناميكي باستخدام مكالمات API الخاصة بـ Aspose.Words.

### أين يمكنني الحصول على مزيد من المساعدة أو الدعم لـ Aspose.Words؟
 لمزيد من المساعدة، قم بزيارة[منتدى دعم Aspose.Words](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
