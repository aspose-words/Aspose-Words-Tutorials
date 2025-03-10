---
title: مقارنة الحبيبات في مستند Word
linktitle: مقارنة الحبيبات في مستند Word
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على ميزة مقارنة الحبيبات في مستندات Word في Aspose.Words لـ .NET التي تتيح مقارنة المستندات حرفًا بحرف، والإبلاغ عن التغييرات التي طرأت عليها.
weight: 10
url: /ar/net/compare-documents/comparison-granularity/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# مقارنة الحبيبات في مستند Word

فيما يلي دليل خطوة بخطوة لشرح كود المصدر C# أدناه، والذي يستخدم ميزة Compare Granularity في مستند Word الخاص بـ Aspose.Words لـ .NET.

## الخطوة 1: المقدمة

تتيح لك ميزة Compare Granularity في Aspose.Words for .NET مقارنة المستندات على مستوى الأحرف. وهذا يعني أنه سيتم مقارنة كل حرف والإبلاغ عن التغييرات وفقًا لذلك.

## الخطوة 2: إعداد البيئة

قبل البدء، يجب عليك إعداد بيئة التطوير الخاصة بك للعمل مع Aspose.Words for .NET. تأكد من تثبيت مكتبة Aspose.Words وامتلاك مشروع C# مناسب لتضمين الكود فيه.

## الخطوة 3: إضافة التجميعات المطلوبة

لاستخدام ميزة Compare Granularity في Aspose.Words لـ .NET، تحتاج إلى إضافة التجميعات اللازمة إلى مشروعك. تأكد من وجود المراجع المناسبة لـ Aspose.Words في مشروعك.

```csharp
using Aspose.Words;
using Aspose.Words.DocumentBuilder;
```

## الخطوة 4: إنشاء المستندات

في هذه الخطوة، سنقوم بإنشاء مستندين باستخدام فئة DocumentBuilder. سيتم استخدام هذه المستندات للمقارنة.

```csharp
// إنشاء مستند أ.
DocumentBuilder builderA = new DocumentBuilder(new Document());
builderA.Writeln("This is a simple A word.");

// إنشاء المستند B.
DocumentBuilder builderB = new DocumentBuilder(new Document());
builderB.Writeln("This is simple B words.");
```

## الخطوة 5: تكوين خيارات المقارنة

في هذه الخطوة، سنقوم بتكوين خيارات المقارنة لتحديد حبيبات المقارنة. هنا سوف نستخدم حبيبات على مستوى الأحرف.

```csharp
CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };
```

## الخطوة 6: مقارنة المستندات

الآن دعنا نقارن المستندات باستخدام طريقة Compare من فئة Document. سيتم حفظ التغييرات في المستند A.

```csharp
builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);
```

 ال`Compare`تقوم الطريقة بمقارنة المستند A بالمستند B وحفظ التغييرات في المستند A. يمكنك تحديد اسم المؤلف وتاريخ المقارنة للرجوع إليها.

## خاتمة

في هذه المقالة، استكشفنا ميزة Compare Granularity في Aspose.Words for .NET. تتيح لك هذه الميزة مقارنة المستندات على مستوى الأحرف والإبلاغ عن التغييرات. يمكنك استخدام هذه المعرفة لإجراء مقارنات تفصيلية للمستندات في مشاريعك.

### عينة من كود المصدر لحبيبات المقارنة باستخدام Aspose.Words لـ .NET

```csharp
            
DocumentBuilder builderA = new DocumentBuilder(new Document());
DocumentBuilder builderB = new DocumentBuilder(new Document());

builderA.Writeln("This is A simple word");
builderB.Writeln("This is B simple words");

CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };

builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);            
        
```

## خاتمة

في هذا البرنامج التعليمي، استكشفنا ميزة Comparison Granularity في Aspose.Words for .NET. تتيح لك هذه الميزة تحديد مستوى التفاصيل عند مقارنة المستندات. من خلال اختيار مستويات مختلفة من التفصيل، يمكنك إجراء مقارنات تفصيلية على مستوى الحرف أو الكلمة أو الكتلة، اعتمادًا على متطلباتك المحددة. يوفر Aspose.Words for .NET إمكانية مقارنة المستندات المرنة والقوية، مما يجعل من السهل تحديد الاختلافات في المستندات ذات مستويات التفصيل المتفاوتة.

### الأسئلة الشائعة

#### س: ما هو الغرض من استخدام مقارنة الحبيبات في Aspose.Words لـ .NET؟

تسمح لك ميزة مقارنة الحبيبات في Aspose.Words for .NET بتحديد مستوى التفاصيل عند مقارنة المستندات. باستخدام هذه الميزة، يمكنك مقارنة المستندات على مستويات مختلفة، مثل مستوى الأحرف أو مستوى الكلمات أو حتى مستوى الكتلة. يوفر كل مستوى من الحبيبات مستوى مختلفًا من التفاصيل في نتائج المقارنة.

#### س: كيف يمكنني استخدام حبيبات المقارنة في Aspose.Words لـ .NET؟

أ: لاستخدام حبيبات المقارنة في Aspose.Words لـ .NET، اتبع الخطوات التالية:
1. قم بإعداد بيئة التطوير الخاصة بك باستخدام مكتبة Aspose.Words.
2. قم بإضافة التجميعات اللازمة إلى مشروعك عن طريق الرجوع إلى Aspose.Words.
3.  قم بإنشاء المستندات التي تريد مقارنتها باستخدام`DocumentBuilder` فصل.
4.  قم بتكوين خيارات المقارنة عن طريق إنشاء`CompareOptions` الكائن والإعداد`Granularity` الملكية إلى المستوى المطلوب (على سبيل المثال،`Granularity.CharLevel` للمقارنة على مستوى الشخصية).
5.  استخدم`Compare`الطريقة على مستند واحد، وتمرير المستند الآخر و`CompareOptions` الكائن كمعلمات. ستقوم هذه الطريقة بمقارنة المستندات بناءً على التفاصيل المحددة وحفظ التغييرات في المستند الأول.

#### س: ما هي مستويات حبيبات المقارنة المتوفرة في Aspose.Words لـ .NET؟

أ: يوفر Aspose.Words لـ .NET ثلاثة مستويات من دقة المقارنة:
- `Granularity.CharLevel`:مقارنة المستندات على مستوى الأحرف.
- `Granularity.WordLevel`:مقارنة المستندات على مستوى الكلمة.
- `Granularity.BlockLevel`:مقارنة المستندات على مستوى الكتلة.

#### س: كيف يمكنني تفسير نتائج المقارنة باستخدام حبيبات مستوى الأحرف؟

ج: باستخدام تقنية التفصيل على مستوى الأحرف، يتم تحليل كل حرف في المستندات المقارنة بحثًا عن الاختلافات. وستُظهِر نتائج المقارنة التغييرات على مستوى الأحرف الفردية، بما في ذلك الإضافات والحذف والتعديلات.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
