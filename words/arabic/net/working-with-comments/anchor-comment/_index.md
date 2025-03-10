---
title: تعليق المرساة
linktitle: تعليق المرساة
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إضافة تعليقات المرساة في مستندات Word باستخدام Aspose.Words for .NET. اتبع دليلنا خطوة بخطوة للتعاون الفعال في المستندات.
weight: 10
url: /ar/net/working-with-comments/anchor-comment/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تعليق المرساة

## مقدمة

هل سبق لك أن وجدت نفسك في موقف حيث كنت بحاجة إلى إضافة تعليقات إلى أقسام نصية معينة في مستند Word برمجيًا؟ تخيل أنك تتعاون مع فريقك في مستند، وتحتاج إلى إبراز أجزاء معينة بتعليقات ليراجعها الآخرون. في هذا البرنامج التعليمي، سنتعمق في كيفية إدراج تعليقات المرساة في مستندات Word باستخدام Aspose.Words for .NET. سنقسم العملية إلى خطوات بسيطة، مما يسهل عليك متابعتها وتنفيذها في مشاريعك.

## المتطلبات الأساسية

قبل أن نبدأ، دعونا نتأكد من أن لديك كل ما تحتاجه:

-  Aspose.Words لـ .NET: تأكد من تثبيت مكتبة Aspose.Words. يمكنك تنزيلها من[هنا](https://releases.aspose.com/words/net/).
- بيئة التطوير: أي بيئة تطوير .NET مثل Visual Studio.
- الفهم الأساسي لـ C#: إن الإلمام ببرمجة C# سيساعدك على اتباع الخطوات بسهولة.

الآن، دعنا ننتقل إلى مساحات الأسماء التي ستحتاج إلى استيرادها لهذه المهمة.

## استيراد مساحات الأسماء

للبدء، تأكد من استيراد مساحات الأسماء اللازمة في مشروعك. فيما يلي مساحات الأسماء المطلوبة:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.CommentRangeStart;
using Aspose.Words.CommentRangeEnd;
```

بعد توضيح المتطلبات الأساسية ومساحات الأسماء، دعنا ننتقل إلى الجزء الممتع: تقسيم العملية خطوة بخطوة.

## الخطوة 1: إنشاء مستند جديد

أولاً، لنقم بإنشاء مستند Word جديد. سيعمل هذا المستند كلوحة لتعليقاتنا.

```csharp
// قم بتحديد الدليل الذي سيتم حفظ المستند فيه
string dataDir = "YOUR DOCUMENT DIRECTORY";        

// إنشاء مثيل لفئة المستند
Document doc = new Document();
```

 في هذه الخطوة، نقوم بتهيئة ملف جديد`Document` الكائن الذي سيتم استخدامه لإضافة تعليقاتنا.

## الخطوة 2: إضافة نص إلى المستند

بعد ذلك، سنضيف بعض النصوص إلى المستند. وسيكون هذا النص هو الهدف لتعليقاتنا.

```csharp
// إنشاء الفقرة الأولى وتشغيلها
Paragraph para1 = new Paragraph(doc);
Run run1 = new Run(doc, "Some ");
Run run2 = new Run(doc, "text ");
para1.AppendChild(run1);
para1.AppendChild(run2);
doc.FirstSection.Body.AppendChild(para1);

// إنشاء الفقرة الثانية وتشغيلها
Paragraph para2 = new Paragraph(doc);
Run run3 = new Run(doc, "is ");
Run run4 = new Run(doc, "added ");
para2.AppendChild(run3);
para2.AppendChild(run4);
doc.FirstSection.Body.AppendChild(para2);
```

 هنا، نقوم بإنشاء فقرتين ببعض النصوص. يتم تغليف كل جزء من النص في`Run` الكائن، والذي يضاف بعد ذلك إلى الفقرات.

## الخطوة 3: إنشاء تعليق

الآن، دعونا ننشئ تعليقًا وسنضيفه إلى نصنا.

```csharp
// إنشاء تعليق جديد
Comment comment = new Comment(doc, "Awais Hafeez", "AH", DateTime.Today);
comment.SetText("Comment text.");
```

 في هذه الخطوة، نقوم بإنشاء`Comment` الكائن وإضافة فقرة وتشغيل بنص التعليق.

## الخطوة 4: تحديد نطاق التعليق

لترسيخ التعليق على نص محدد، نحتاج إلى تحديد بداية ونهاية نطاق التعليق.

```csharp
// تعريف CommentRangeStart و CommentRangeEnd
CommentRangeStart commentRangeStart = new CommentRangeStart(doc, comment.Id);
CommentRangeEnd commentRangeEnd = new CommentRangeEnd(doc, comment.Id);

// أدخل CommentRangeStart و CommentRangeEnd في المستند
run1.ParentNode.InsertAfter(commentRangeStart, run1);
run3.ParentNode.InsertAfter(commentRangeEnd, run3);

// أضف التعليق إلى المستند
commentRangeEnd.ParentNode.InsertAfter(comment, commentRangeEnd);
```

 هنا، نقوم بإنشاء`CommentRangeStart` و`CommentRangeEnd` الكائنات، وربطها بالتعليق من خلال معرفها. ثم نقوم بإدراج هذه النطاقات في المستند، مما يؤدي فعليًا إلى ربط تعليقنا بالنص المحدد.

## الخطوة 5: احفظ المستند

وأخيرًا، دعونا نحفظ مستندنا في الدليل المحدد.

```csharp
// حفظ المستند
doc.Save(dataDir + "WorkingWithComments.AnchorComment.doc");
```

تؤدي هذه الخطوة إلى حفظ المستند الذي يحتوي على التعليق الثابت في الدليل المحدد.

## خاتمة

والآن، لقد تعلمت بنجاح كيفية إضافة تعليقات مرساة إلى أقسام نصية محددة في مستند Word باستخدام Aspose.Words for .NET. هذه التقنية مفيدة بشكل لا يصدق للتعاون في المستندات، حيث تتيح لك تسليط الضوء على أجزاء معينة من النص والتعليق عليها بسهولة. سواء كنت تعمل على مشروع مع فريقك أو تقوم بمراجعة المستندات، فإن هذه الطريقة ستعزز إنتاجيتك وتبسط سير عملك.

## الأسئلة الشائعة

### ما هو الغرض من استخدام تعليقات المرساة في مستندات Word؟
تُستخدم تعليقات المرساة لتسليط الضوء على أقسام محددة من النص والتعليق عليها، مما يجعل تقديم الملاحظات والتعاون في المستندات أسهل.

### هل يمكنني إضافة تعليقات متعددة إلى نفس قسم النص؟
نعم، يمكنك إضافة تعليقات متعددة إلى نفس قسم النص عن طريق تحديد نطاقات تعليقات متعددة.

### هل استخدام Aspose.Words لـ .NET مجاني؟
 يقدم Aspose.Words for .NET نسخة تجريبية مجانية يمكنك تنزيلها[هنا](https://releases.aspose.com/) للحصول على الميزات الكاملة، يمكنك شراء ترخيص[هنا](https://purchase.aspose.com/buy).

### هل يمكنني تخصيص مظهر التعليقات؟
في حين يركز Aspose.Words على الوظيفة، فإن ظهور التعليقات في مستندات Word يتم التحكم فيه بشكل عام بواسطة Word نفسه.

### أين يمكنني العثور على مزيد من الوثائق حول Aspose.Words لـ .NET؟
 يمكنك العثور على وثائق مفصلة[هنا](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
