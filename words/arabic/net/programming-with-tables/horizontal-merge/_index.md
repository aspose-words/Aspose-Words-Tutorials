---
"description": "تعرف على كيفية دمج الخلايا أفقيًا في مستند Word باستخدام Aspose.Words لـ .NET من خلال هذا البرنامج التعليمي المفصل خطوة بخطوة."
"linktitle": "دمج أفقي"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "دمج أفقي"
"url": "/ar/net/programming-with-tables/horizontal-merge/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# دمج أفقي

## مقدمة

أهلاً! هل أنت مستعد للتعمق في عالم Aspose.Words لـ .NET؟ سنتناول اليوم ميزة مفيدة للغاية: الدمج الأفقي للجداول. قد يبدو هذا الأمر تقنيًا بعض الشيء، لكن لا تقلق، فأنا هنا لمساعدتك. بنهاية هذا البرنامج التعليمي، ستصبح محترفًا في دمج الخلايا في مستندات Word برمجيًا. هيا بنا نبدأ!

## المتطلبات الأساسية

قبل أن ننتقل إلى التفاصيل الدقيقة، هناك بعض الأشياء التي ستحتاج إلى وضعها في مكانها:

1. مكتبة Aspose.Words لـ .NET: إذا لم تقم بتنزيل مكتبة Aspose.Words لـ .NET، يمكنك الحصول عليها. [هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: تأكد من إعداد بيئة تطوير مناسبة، مثل Visual Studio.
3. المعرفة الأساسية بلغة C#: سيكون من المفيد الحصول على فهم أساسي لبرمجة C#.

بمجرد الانتهاء من هذه الأمور، ستكون جاهزًا للانطلاق!

## استيراد مساحات الأسماء

قبل التعمق في الكود، لنتأكد من استيراد مساحات الأسماء اللازمة. في مشروع C# الخاص بك، تأكد من تضمين:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

حسنًا، دعنا نستعرض عملية دمج خلايا الجدول أفقيًا في مستند Word باستخدام Aspose.Words لـ .NET.

## الخطوة 1: إعداد مستندك

أولاً وقبل كل شيء، نحتاج إلى إنشاء مستند Word جديد وتهيئة `DocumentBuilder`:

```csharp
// المسار إلى دليل المستندات الخاص بك 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

يؤدي مقتطف التعليمات البرمجية هذا إلى إنشاء مستند جديد وإعداده `DocumentBuilder` من أجل العمل.

## الخطوة 2: إدخال الخلية الأولى

بعد ذلك، نبدأ بإدخال الخلية الأولى ووضع علامة عليها للدمج الأفقي:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.First;
builder.Write("Text in merged cells.");
```

هنا نقوم بإدخال خلية جديدة وتعيين `HorizontalMerge` الممتلكات إلى `CellMerge.First`، مما يشير إلى أن هذه الخلية هي بداية لتسلسل الخلايا المندمجة.

## الخطوة 3: إدراج الخلية المدمجة

الآن نقوم بإدخال الخلية التي سيتم دمجها مع الخلية السابقة:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.Previous;
builder.EndRow();
```

تم تعيين هذه الخلية للاندماج مع الخلية السابقة باستخدام `CellMerge.Previous`لاحظ كيف ننهي الصف بـ `builder.EndRow()`.

## الخطوة 4: إدراج الخلايا غير المدمجة

لتوضيح الفرق، دعنا نقوم بإدراج زوج من الخلايا غير المدمجة:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.None;
builder.Write("Text in one cell.");
builder.InsertCell();
builder.Write("Text in another cell.");
builder.EndRow();
```

هنا، نُدرج خليتين دون دمج أفقي. يُظهر هذا سلوك الخلايا عندما لا تكون جزءًا من تسلسل مُدمج.

## الخطوة 5: الانتهاء من الجدول

وأخيرًا ننهي الجدول ونحفظ المستند:

```csharp
builder.EndTable();
doc.Save(dataDir + "WorkingWithTables.HorizontalMerge.docx");
```

يكمل مقتطف التعليمات البرمجية هذا الجدول ويحفظ المستند في الدليل المحدد.

## خاتمة

وها قد انتهيت! لقد أتقنت للتو فن دمج الخلايا أفقيًا في مستند وورد باستخدام Aspose.Words لـ .NET. باتباع هذه الخطوات، يمكنك إنشاء هياكل جداول معقدة بسهولة. استمر في تجربة واستكشاف إمكانيات Aspose.Words لجعل مستنداتك ديناميكية ومرنة كما تريد. برمجة ممتعة!

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟
Aspose.Words for .NET هي مكتبة قوية تسمح للمطورين بإنشاء مستندات Word وتحريرها ومعالجتها برمجيًا في تطبيقات .NET.

### هل يمكنني دمج الخلايا عموديا باستخدام Aspose.Words لـ .NET؟
نعم، يمكنك أيضًا دمج الخلايا عموديًا باستخدام `CellFormat.VerticalMerge` ملكية.

### هل استخدام Aspose.Words for .NET مجاني؟
يُقدّم Aspose.Words for .NET نسخة تجريبية مجانية، ولكن للاستفادة الكاملة من الميزات، ستحتاج إلى شراء ترخيص. يمكنك الحصول على ترخيص مؤقت. [هنا](https://purchase.aspose.com/temporary-license/).

### كيف يمكنني معرفة المزيد عن Aspose.Words لـ .NET؟
يمكنك استكشاف الوثائق التفصيلية [هنا](https://reference.aspose.com/words/net/).

### أين يمكنني الحصول على الدعم لـ Aspose.Words لـ .NET؟
لأي استفسارات أو مشاكل، يمكنك زيارة منتدى دعم Aspose [هنا](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}