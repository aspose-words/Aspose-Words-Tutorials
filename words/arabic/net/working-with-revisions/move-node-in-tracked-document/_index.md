---
"description": "تعرّف على كيفية نقل العقد في مستند Word مُتتبّع باستخدام Aspose.Words لـ .NET من خلال دليلنا المُفصّل خطوة بخطوة. مثالي للمطورين."
"linktitle": "نقل العقدة في المستند المتعقب"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "نقل العقدة في المستند المتعقب"
"url": "/ar/net/working-with-revisions/move-node-in-tracked-document/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# نقل العقدة في المستند المتعقب

## مقدمة

أهلاً بكم، يا مُحبي Aspose.Words! إذا احتجتم يومًا لنقل عقدة في مستند Word أثناء متابعة المراجعات، فأنتم في المكان المناسب. اليوم، سنتعمق في كيفية تحقيق ذلك باستخدام Aspose.Words لـ .NET. لن تتعلموا العملية خطوة بخطوة فحسب، بل ستكتسبون أيضًا بعض النصائح والحيل لجعل معالجة مستنداتكم سلسة وفعالة.

## المتطلبات الأساسية

قبل أن نبدأ في تعلم بعض الأكواد البرمجية، دعونا نتأكد من أنك حصلت على كل ما تحتاجه:

- Aspose.Words لـ .NET: تنزيله [هنا](https://releases.aspose.com/words/net/).
- بيئة .NET: تأكد من إعداد بيئة تطوير .NET متوافقة.
- المعرفة الأساسية بلغة C#: يفترض هذا البرنامج التعليمي أن لديك فهمًا أساسيًا للغة C#.

هل فهمت كل شيء؟ رائع! لننتقل إلى مساحات الأسماء التي نريد استيرادها.

## استيراد مساحات الأسماء

أولاً، علينا استيراد مساحات الأسماء اللازمة. هذه ضرورية للعمل مع Aspose.Words ومعالجة عُقد المستندات.

```csharp
using Aspose.Words;
using System;
```

حسنًا، لنُقسّم العملية إلى خطوات سهلة. سيتم شرح كل خطوة بالتفصيل لضمان فهمك لما يحدث في كل نقطة.

## الخطوة 1: تهيئة المستند

للبدء، نحتاج إلى تهيئة مستند جديد واستخدام `DocumentBuilder` لإضافة بعض الفقرات.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// إضافة بعض الفقرات
builder.Writeln("Paragraph 1");
builder.Writeln("Paragraph 2");
builder.Writeln("Paragraph 3");
builder.Writeln("Paragraph 4");
builder.Writeln("Paragraph 5");
builder.Writeln("Paragraph 6");

// التحقق من عدد الفقرات الأولية
Body body = doc.FirstSection.Body;
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## الخطوة 2: ابدأ بتتبع المراجعات

بعد ذلك، علينا البدء بتتبع المراجعات. هذا أمر بالغ الأهمية لأنه يسمح لنا برؤية التغييرات التي أُجريت على المستند.

```csharp
// ابدأ بتتبع المراجعات
doc.StartTrackRevisions("Author", new DateTime(2020, 12, 23, 14, 0, 0));
```

## الخطوة 3: نقل العقد

الآن يأتي الجزء الأساسي من مهمتنا: نقل عقدة من مكان إلى آخر. سننقل الفقرة الثالثة ونضعها قبل الفقرة الأولى.

```csharp
// قم بتحديد العقدة التي سيتم نقلها ونطاقها النهائي
Node node = body.Paragraphs[3];
Node endNode = body.Paragraphs[5].NextSibling;
Node referenceNode = body.Paragraphs[0];

// نقل العقد داخل النطاق المحدد
while (node != endNode)
{
    Node nextNode = node.NextSibling;
    body.InsertBefore(node, referenceNode);
    node = nextNode;
}
```

## الخطوة 4: إيقاف تتبع المراجعات

بمجرد نقل العقد، نحتاج إلى إيقاف تتبع المراجعات.

```csharp
// إيقاف تتبع المراجعات
doc.StopTrackRevisions();
```

## الخطوة 5: حفظ المستند

وأخيرًا، دعنا نحفظ مستندنا المعدّل في الدليل المحدد.

```csharp
// حفظ المستند المعدل
doc.Save(dataDir + "WorkingWithRevisions.MoveNodeInTrackedDocument.docx");

// إخراج عدد الفقرات النهائية
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## خاتمة

وها قد انتهيت! لقد نقلتَ عقدةً بنجاح في مستند مُتتبّع باستخدام Aspose.Words لـ .NET. تُسهّل هذه المكتبة القوية التعامل مع مستندات Word برمجيًا. سواءً كنت تُنشئ أو تُحرّر أو تتبّع التغييرات، فإن Aspose.Words تُلبّي احتياجاتك. لذا، جرّبها. برمجة ممتعة!

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟

Aspose.Words for .NET هي مكتبة فئات للعمل مع مستندات Word برمجيًا. تتيح للمطورين إنشاء مستندات Word وتحريرها وتحويلها وطباعتها داخل تطبيقات .NET.

### كيف يمكنني تتبع المراجعات في مستند Word باستخدام Aspose.Words؟

لتتبع المراجعات، استخدم `StartTrackRevisions` الطريقة على `Document` الكائن. سيؤدي هذا إلى تمكين تتبع المراجعة، وإظهار أي تغييرات تم إجراؤها على المستند.

### هل يمكنني نقل عقد متعددة في Aspose.Words؟

نعم، يمكنك نقل عقد متعددة عن طريق التكرار عليها واستخدام طرق مثل `InsertBefأوe` or `InsertAfter` لوضعهم في المكان المطلوب.

### كيف يمكنني إيقاف تتبع المراجعات في Aspose.Words؟

استخدم `StopTrackRevisions` الطريقة على `Document` اعترض على إيقاف تتبع المراجعات.

### أين يمكنني العثور على مزيد من الوثائق حول Aspose.Words لـ .NET؟

يمكنك العثور على وثائق مفصلة [هنا](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}