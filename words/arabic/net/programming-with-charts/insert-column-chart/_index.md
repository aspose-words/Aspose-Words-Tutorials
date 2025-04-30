---
"description": "تعرّف على كيفية إدراج مخططات عمودية في مستندات Word باستخدام Aspose.Words لـ .NET. حسّن عرض البيانات في تقاريرك وعروضك التقديمية."
"linktitle": "إدراج مخطط عمودي في مستند Word"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "إدراج مخطط عمودي في مستند Word"
"url": "/ar/net/programming-with-charts/insert-column-chart/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إدراج مخطط عمودي في مستند Word

## مقدمة

في هذا البرنامج التعليمي، ستتعلم كيفية تحسين مستندات Word الخاصة بك عن طريق إدراج مخططات عمودية جذابة بصريًا باستخدام Aspose.Words لـ .NET. تُعد المخططات العمودية فعّالة في عرض اتجاهات البيانات ومقارناتها، مما يجعل مستنداتك أكثر إفادة وتفاعلًا.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

- المعرفة الأساسية ببرمجة C# وبيئة .NET.
- Aspose.Words for .NET مُثبّت في بيئة التطوير لديك. يمكنك تنزيله. [هنا](https://releases.aspose.com/words/net/).
- محرر نصوص أو بيئة تطوير متكاملة (IDE) مثل Visual Studio.

## استيراد مساحات الأسماء

قبل البدء في الترميز، قم باستيراد مساحات الأسماء الضرورية:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
```

اتبع الخطوات التالية لإدراج مخطط عمودي في مستند Word الخاص بك باستخدام Aspose.Words لـ .NET:

## الخطوة 1: إنشاء مستند جديد

أولاً، قم بإنشاء مستند Word جديد وقم بتشغيله `DocumentBuilder` هدف.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## الخطوة 2: إدراج الرسم البياني العمودي

استخدم `InsertChart` طريقة `DocumentBuilder` فئة لإدراج مخطط عمودي.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## الخطوة 3: إضافة البيانات إلى الرسم البياني

أضف سلسلة بيانات إلى الرسم البياني باستخدام `Series` ممتلكات `Chart` هدف.

```csharp
chart.Series.Add("Aspose Series 1", new string[] { "Category 1", "Category 2" }, new double[] { 1, 2 });
```

## الخطوة 4: حفظ المستند

احفظ المستند الذي يحتوي على مخطط العمود المدرج في الموقع المطلوب.

```csharp
doc.Save(dataDir + "InsertColumnChart.docx");
```

## خاتمة

تهانينا! لقد تعلمت بنجاح كيفية إدراج مخطط عمودي في مستند وورد باستخدام Aspose.Words لـ .NET. تُحسّن هذه المهارة المظهر المرئي والقيمة المعلوماتية لمستنداتك بشكل كبير، مما يجعل عرض البيانات أكثر وضوحًا وتأثيرًا.

## الأسئلة الشائعة

### هل يمكنني تخصيص مظهر الرسم البياني العمودي؟
نعم، يوفر Aspose.Words لـ .NET خيارات واسعة لتخصيص عناصر الرسم البياني مثل الألوان والعلامات والمحاور.

### هل Aspose.Words for .NET متوافق مع الإصدارات المختلفة من Microsoft Word؟
نعم، يدعم Aspose.Words for .NET إصدارات مختلفة من Microsoft Word، مما يضمن التوافق عبر بيئات مختلفة.

### كيف يمكنني دمج البيانات الديناميكية في الرسم البياني العمودي؟
بإمكانك ملء البيانات بشكل ديناميكي في مخططك العمودي عن طريق استرداد البيانات من قواعد البيانات أو المصادر الخارجية الأخرى في تطبيق .NET الخاص بك.

### هل يمكنني تصدير مستند Word الذي يحتوي على الرسم البياني المدرج إلى PDF أو تنسيقات أخرى؟
نعم، يسمح لك Aspose.Words for .NET بحفظ المستندات التي تحتوي على مخططات بتنسيقات مختلفة بما في ذلك PDF وHTML والصور.

### أين يمكنني الحصول على مزيد من الدعم أو المساعدة لـ Aspose.Words لـ .NET؟
لمزيد من المساعدة، قم بزيارة [منتدى Aspose.Words لـ .NET](https://forum.aspose.com/c/words/8) أو اتصل بدعم Aspose.




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}