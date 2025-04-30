---
"description": "تعرف على ميزة مقارنة الحبيبات في مستندات Word في Aspose.Words لـ .NET التي تتيح مقارنة المستندات حرفًا بحرف، والإبلاغ عن التغييرات التي طرأت."
"linktitle": "مقارنة الحبيبات في مستند Word"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "مقارنة الحبيبات في مستند Word"
"url": "/ar/net/compare-documents/comparison-granularity/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# مقارنة الحبيبات في مستند Word

فيما يلي دليل خطوة بخطوة لشرح كود المصدر C# أدناه، والذي يستخدم ميزة Compare Granularity في مستند Word الخاص بـ Aspose.Words لـ .NET.

## الخطوة 1: المقدمة

تتيح لك ميزة "مقارنة الحبيبات" في Aspose.Words لـ .NET مقارنة المستندات على مستوى الأحرف. هذا يعني أنه سيتم مقارنة كل حرف والإبلاغ عن التغييرات وفقًا لذلك.

## الخطوة 2: إعداد البيئة

قبل البدء، عليك إعداد بيئة التطوير الخاصة بك للعمل مع Aspose.Words لـ .NET. تأكد من تثبيت مكتبة Aspose.Words وامتلاك مشروع C# مناسب لتضمين الكود فيه.

## الخطوة 3: إضافة التجميعات المطلوبة

لاستخدام ميزة مقارنة التفاصيل في Aspose.Words لـ .NET، عليك إضافة التجميعات اللازمة إلى مشروعك. تأكد من وجود المراجع الصحيحة لـ Aspose.Words في مشروعك.

```csharp
using Aspose.Words;
using Aspose.Words.DocumentBuilder;
```

## الخطوة 4: إنشاء المستندات

في هذه الخطوة، سننشئ مستندين باستخدام فئة DocumentBuilder. سيتم استخدام هذين المستندين للمقارنة.

```csharp
// إنشاء المستند أ.
DocumentBuilder builderA = new DocumentBuilder(new Document());
builderA.Writeln("This is a simple A word.");

// إنشاء المستند ب.
DocumentBuilder builderB = new DocumentBuilder(new Document());
builderB.Writeln("This is simple B words.");
```

## الخطوة 5: تكوين خيارات المقارنة

في هذه الخطوة، سنُهيئ خيارات المقارنة لتحديد دقة المقارنة. هنا، سنستخدم دقة على مستوى الأحرف.

```csharp
CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };
```

## الخطوة 6: مقارنة المستندات

الآن، لنقارن المستندات باستخدام طريقة المقارنة في فئة المستندات. سيتم حفظ التغييرات في المستند أ.

```csharp
builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);
```

ال `Compare` تقوم الطريقة بمقارنة المستند A بالمستند B وتحفظ التغييرات في المستند A. يمكنك تحديد اسم المؤلف وتاريخ المقارنة للرجوع إليها.

## خاتمة

في هذه المقالة، استكشفنا ميزة "مقارنة التفاصيل" في Aspose.Words لـ .NET. تتيح لك هذه الميزة مقارنة المستندات على مستوى الأحرف والإبلاغ عن التغييرات. يمكنك استخدام هذه المعرفة لإجراء مقارنات تفصيلية للمستندات في مشاريعك.

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

في هذا البرنامج التعليمي، استكشفنا ميزة دقة المقارنة في Aspose.Words لـ .NET. تتيح لك هذه الميزة تحديد مستوى الدقة عند مقارنة المستندات. باختيار مستويات دقة مختلفة، يمكنك إجراء مقارنات مفصلة على مستوى الأحرف أو الكلمات أو الكتل، وفقًا لاحتياجاتك الخاصة. يوفر Aspose.Words لـ .NET إمكانية مرنة وفعّالة لمقارنة المستندات، مما يُسهّل تحديد الاختلافات بين المستندات ذات مستويات الدقة المختلفة.

### الأسئلة الشائعة

#### س: ما هو الغرض من استخدام حبيبات المقارنة في Aspose.Words لـ .NET؟

ج: تتيح لك ميزة دقة المقارنة في Aspose.Words لـ .NET تحديد مستوى التفاصيل عند مقارنة المستندات. باستخدام هذه الميزة، يمكنك مقارنة المستندات على مستويات مختلفة، مثل مستوى الأحرف، أو مستوى الكلمات، أو حتى مستوى الكتل. يوفر كل مستوى دقة مستوى مختلفًا من التفاصيل في نتائج المقارنة.

#### س: كيف يمكنني استخدام حبيبات المقارنة في Aspose.Words لـ .NET؟

أ: لاستخدام حبيبات المقارنة في Aspose.Words لـ .NET، اتبع الخطوات التالية:
1. قم بإعداد بيئة التطوير الخاصة بك باستخدام مكتبة Aspose.Words.
2. قم بإضافة التجميعات اللازمة إلى مشروعك عن طريق الرجوع إلى Aspose.Words.
3. قم بإنشاء المستندات التي تريد مقارنتها باستخدام `DocumentBuilder` فصل.
4. قم بتكوين خيارات المقارنة عن طريق إنشاء `CompareOptions` الكائن والإعداد `Granularity` الممتلكات إلى المستوى المطلوب (على سبيل المثال، `Granularity.CharLevel` للمقارنة على مستوى الشخصية).
5. استخدم `Compare` الطريقة على مستند واحد، وتمرير المستند الآخر و `CompareOptions` كائنات كمعلمات. ستُقارن هذه الطريقة المستندات بناءً على التفاصيل المحددة، وتحفظ التغييرات في المستند الأول.

#### س: ما هي مستويات حبيبات المقارنة المتوفرة في Aspose.Words لـ .NET؟

أ: يوفر Aspose.Words for .NET ثلاثة مستويات من دقة المقارنة:
- `Granularity.CharLevel`:مقارنة المستندات على مستوى الأحرف.
- `Granularity.WordLevel`:مقارنة المستندات على مستوى الكلمة.
- `Granularity.BlockLevel`:مقارنة المستندات على مستوى الكتلة.

#### س: كيف يمكنني تفسير نتائج المقارنة مع التفاصيل على مستوى الأحرف؟

ج: باستخدام تقنية التفصيل على مستوى الأحرف، يُحلَّل كل حرف في المستندات المُقارَنة بحثًا عن الاختلافات. تُظهر نتائج المقارنة التغييرات على مستوى كل حرف، بما في ذلك الإضافات والحذف والتعديلات.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}