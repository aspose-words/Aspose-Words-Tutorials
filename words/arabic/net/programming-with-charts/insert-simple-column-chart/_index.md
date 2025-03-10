---
title: إدراج مخطط عمودي بسيط في مستند Word
linktitle: إدراج مخطط عمودي بسيط في مستند Word
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إدراج مخطط عمودي بسيط في Word باستخدام Aspose.Words for .NET. قم بتعزيز مستنداتك باستخدام عروض البيانات المرئية الديناميكية.
weight: 10
url: /ar/net/programming-with-charts/insert-simple-column-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إدراج مخطط عمودي بسيط في مستند Word

## مقدمة

في العصر الرقمي الحالي، يعد إنشاء مستندات ديناميكية وغنية بالمعلومات أمرًا ضروريًا. يمكن للعناصر المرئية مثل المخططات البيانية تحسين عرض البيانات بشكل كبير، مما يجعل من الأسهل استيعاب المعلومات المعقدة في لمحة. في هذا البرنامج التعليمي، سنتعمق في كيفية إدراج مخطط عمودي بسيط في مستند Word باستخدام Aspose.Words for .NET. سواء كنت مطورًا أو محلل بيانات أو شخصًا يريد إضافة بعض الإثارة إلى تقاريره، فإن إتقان هذه المهارة يمكن أن يأخذ إنشاء المستندات إلى المستوى التالي.

## المتطلبات الأساسية

قبل أن نتعمق في التفاصيل، تأكد من توفر المتطلبات الأساسية التالية:

- المعرفة الأساسية ببرمجة C# وإطار عمل .NET.
- تم تثبيت Aspose.Words لـ .NET في بيئة التطوير الخاصة بك.
- بيئة تطوير مثل Visual Studio تم إعدادها وجاهزة للاستخدام.
- القدرة على إنشاء مستندات Word ومعالجتها برمجيًا.

## استيراد المساحات الاسمية

أولاً، لنبدأ باستيراد المساحات الأساسية اللازمة في الكود C# الخاص بك:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
```

الآن، دعنا نستعرض عملية إدراج مخطط عمودي بسيط في مستند Word باستخدام Aspose.Words for .NET. اتبع الخطوات التالية بعناية لتحقيق النتيجة المرجوة:

## الخطوة 1: تهيئة المستند وDocumentBuilder

```csharp
// المسار إلى دليل المستند الخاص بك
string dataDir = "YOUR_DOCUMENT_DIRECTORY";

// تهيئة مستند جديد
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## الخطوة 2: إدراج شكل الرسم البياني

```csharp
// إدراج شكل مخطط من نوع العمود
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
ChartSeriesCollection seriesColl = chart.Series;
```

## الخطوة 3: مسح السلسلة الافتراضية وإضافة سلسلة بيانات مخصصة

```csharp
// مسح أي سلسلة تم إنشاؤها افتراضيًا
seriesColl.Clear();

// تحديد أسماء الفئات وقيم البيانات
string[] categories = new string[] { "Category 1", "Category 2" };
double[] dataValues1 = new double[] { 1, 2 };
double[] dataValues2 = new double[] { 3, 4 };

// إضافة سلسلة بيانات إلى الرسم البياني
seriesColl.Add("Aspose Series 1", categories, dataValues1);
seriesColl.Add("Aspose Series 2", categories, dataValues2);
```

## الخطوة 4: حفظ المستند

```csharp
// احفظ المستند بالرسم البياني المُدرج
doc.Save(dataDir + "InsertSimpleColumnChart.docx");
```

## خاتمة

تهانينا! لقد نجحت في تعلم كيفية إدراج مخطط عمودي بسيط في مستند Word باستخدام Aspose.Words for .NET. باتباع هذه الخطوات، يمكنك الآن دمج عناصر مرئية ديناميكية في مستنداتك، مما يجعلها أكثر جاذبية وإفادة.

## الأسئلة الشائعة

### هل يمكنني تخصيص مظهر الرسم البياني باستخدام Aspose.Words لـ .NET؟
نعم، يمكنك تخصيص جوانب مختلفة من الرسم البياني مثل الألوان والخطوط والأنماط برمجيًا.

### هل Aspose.Words for .NET مناسب لإنشاء مخططات معقدة؟
بالتأكيد! يدعم Aspose.Words for .NET مجموعة واسعة من أنواع المخططات وخيارات التخصيص لإنشاء مخططات معقدة.

### هل يدعم Aspose.Words for .NET تصدير المخططات إلى تنسيقات أخرى مثل PDF؟
نعم، يمكنك تصدير المستندات التي تحتوي على مخططات بيانية إلى تنسيقات مختلفة بما في ذلك تنسيق PDF بسلاسة.

### هل يمكنني دمج البيانات من مصادر خارجية في هذه المخططات البيانية؟
نعم، يسمح لك Aspose.Words for .NET بملء المخططات بشكل ديناميكي بالبيانات من مصادر خارجية مثل قواعد البيانات أو واجهات برمجة التطبيقات.

### أين يمكنني العثور على المزيد من الموارد والدعم لـ Aspose.Words لـ .NET؟
 قم بزيارة[توثيق Aspose.Words لـ .NET](https://reference.aspose.com/words/net/) للحصول على مراجع مفصلة لواجهة برمجة التطبيقات وأمثلة عليها. للحصول على الدعم، يمكنك أيضًا زيارة[منتدى Aspose.Words](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
