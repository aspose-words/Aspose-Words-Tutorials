---
title: نقل العقدة في المستند المتعقب
linktitle: نقل العقدة في المستند المتعقب
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية نقل العقد في مستند Word متتبع باستخدام Aspose.Words for .NET من خلال دليلنا المفصل خطوة بخطوة. مثالي للمطورين.
weight: 10
url: /ar/net/working-with-revisions/move-node-in-tracked-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# نقل العقدة في المستند المتعقب

## مقدمة

مرحبًا بكم، أيها المتحمسون لبرنامج Aspose.Words! إذا كنتم في حاجة إلى نقل عقدة في مستند Word أثناء تتبع المراجعات، فأنتم في المكان المناسب. اليوم، سنتناول كيفية تحقيق ذلك باستخدام برنامج Aspose.Words for .NET. لن تتعلموا العملية خطوة بخطوة فحسب، بل ستتعلمون أيضًا بعض النصائح والحيل لجعل معالجة المستندات الخاصة بكم سلسة وفعالة.

## المتطلبات الأساسية

قبل أن نبدأ في تعلم بعض الأكواد البرمجية، دعونا نتأكد من أنك حصلت على كل ما تحتاجه:

-  Aspose.Words for .NET: قم بتنزيله[هنا](https://releases.aspose.com/words/net/).
- بيئة .NET: تأكد من إعداد بيئة تطوير .NET متوافقة.
- المعرفة الأساسية بلغة C#: يفترض هذا البرنامج التعليمي أن لديك فهمًا أساسيًا للغة C#.

هل حصلت على كل شيء؟ رائع! دعنا ننتقل إلى مساحات الأسماء التي نحتاج إلى استيرادها.

## استيراد مساحات الأسماء

أولاً وقبل كل شيء، نحتاج إلى استيراد مساحات الأسماء الضرورية. فهي ضرورية للعمل مع Aspose.Words والتعامل مع عقد المستندات.

```csharp
using Aspose.Words;
using System;
```

حسنًا، دعنا نقسم العملية إلى خطوات يمكن إدارتها. سيتم شرح كل خطوة بالتفصيل لضمان فهمك لما يحدث في كل نقطة.

## الخطوة 1: تهيئة المستند

 للبدء، نحتاج إلى تهيئة مستند جديد واستخدام`DocumentBuilder` لإضافة بعض الفقرات.

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

## الخطوة 2: ابدأ في تتبع المراجعات

بعد ذلك، نحتاج إلى البدء في تتبع المراجعات. وهذا أمر بالغ الأهمية لأنه يسمح لنا برؤية التغييرات التي تم إجراؤها على المستند.

```csharp
// ابدأ بتتبع المراجعات
doc.StartTrackRevisions("Author", new DateTime(2020, 12, 23, 14, 0, 0));
```

## الخطوة 3: نقل العقد

الآن يأتي الجزء الأساسي من مهمتنا: نقل عقدة من مكان إلى آخر. سنقوم بنقل الفقرة الثالثة ووضعها قبل الفقرة الأولى.

```csharp
// قم بتحديد العقدة المراد نقلها ونطاقها النهائي
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

## الخطوة 4: التوقف عن تتبع المراجعات

بمجرد نقل العقد، نحتاج إلى إيقاف تتبع المراجعات.

```csharp
// إيقاف تتبع المراجعات
doc.StopTrackRevisions();
```

## الخطوة 5: احفظ المستند

وأخيرًا، دعونا نحفظ مستندنا المعدّل في الدليل المحدد.

```csharp
// حفظ المستند المعدل
doc.Save(dataDir + "WorkingWithRevisions.MoveNodeInTrackedDocument.docx");

// إخراج عدد الفقرات النهائية
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## خاتمة

وها أنت ذا! لقد نجحت في نقل عقدة في مستند متتبع باستخدام Aspose.Words for .NET. تسهل هذه المكتبة القوية التعامل مع مستندات Word برمجيًا. سواء كنت تقوم بالإنشاء أو التحرير أو تتبع التغييرات، فإن Aspose.Words ستلبي احتياجاتك. لذا، انطلق وجربها. استمتع بالبرمجة!

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟

Aspose.Words for .NET هي مكتبة فئة للعمل مع مستندات Word برمجيًا. وهي تسمح للمطورين بإنشاء مستندات Word وتحريرها وتحويلها وطباعتها داخل تطبيقات .NET.

### كيف يمكنني تتبع المراجعات في مستند Word باستخدام Aspose.Words؟

 لتتبع المراجعات، استخدم`StartTrackRevisions` الطريقة على`Document` الكائن. سيؤدي هذا إلى تمكين تتبع المراجعة، وإظهار أي تغييرات تم إجراؤها على المستند.

### هل يمكنني نقل عدة عقد في Aspose.Words؟

نعم، يمكنك نقل عقد متعددة عن طريق التكرار عليها واستخدام طرق مثل`InsertBefore` أو`InsertAfter` لوضعهم في المكان المطلوب.

### كيف يمكنني إيقاف تتبع المراجعات في Aspose.Words؟

 استخدم`StopTrackRevisions` الطريقة على`Document` اعترض على إيقاف تتبع المراجعات.

### أين يمكنني العثور على مزيد من الوثائق حول Aspose.Words لـ .NET؟

 يمكنك العثور على وثائق مفصلة[هنا](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
