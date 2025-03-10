---
title: إضافة نص مُشار إليه في مستند Word
linktitle: إضافة نص مُشار إليه في مستند Word
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إضافة نص مُشار إليه في مستند Word باستخدام Aspose.Words for .NET من خلال هذا الدليل التفصيلي. مثالي للمطورين.
weight: 10
url: /ar/net/programming-with-bookmarks/append-bookmarked-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة نص مُشار إليه في مستند Word

## مقدمة

مرحبًا! هل سبق لك أن حاولت إضافة نص من قسم مُضاف إليه إشارة مرجعية في مستند Word ووجدت الأمر صعبًا؟ أنت محظوظ! سيرشدك هذا البرنامج التعليمي خلال العملية باستخدام Aspose.Words for .NET. سنقسمها إلى خطوات بسيطة حتى تتمكن من متابعتها بسهولة. دعنا نتعمق في الأمر ونقوم بإضافة النص المُضاف إليه إشارة مرجعية مثل المحترفين!

## المتطلبات الأساسية

قبل أن نبدأ، دعونا نتأكد من أن لديك كل ما تحتاجه:

-  Aspose.Words for .NET: تأكد من تثبيته. إذا لم يكن مثبتًا، يمكنك[تحميله هنا](https://releases.aspose.com/words/net/).
- بيئة التطوير: أي بيئة تطوير .NET مثل Visual Studio.
- المعرفة الأساسية بلغة C#: إن فهم مفاهيم برمجة C# الأساسية سوف يساعدك.
- مستند Word مع إشارات مرجعية: مستند Word مع إشارات مرجعية تم إعدادها، والتي سنستخدمها لإضافة نص منها.

## استيراد مساحات الأسماء

أولاً وقبل كل شيء، دعنا نستورد مساحات الأسماء الضرورية. سيضمن هذا أن تكون كل الأدوات التي نحتاجها في متناول أيدينا.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

دعونا نقوم بتقسيم المثال إلى خطوات مفصلة.

## الخطوة 1: تحميل المستند وتهيئة المتغيرات

حسنًا، لنبدأ بتحميل مستند Word الخاص بنا وتهيئة المتغيرات التي سنحتاجها.

```csharp
// قم بتحميل المستندات المصدر والوجهة.
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

// تهيئة مستورد المستندات.
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

// ابحث عن الإشارة المرجعية في المستند المصدر.
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## الخطوة 2: تحديد فقرات البداية والنهاية

الآن، دعنا نحدد الفقرات التي تبدأ وتنتهي عندها الإشارة المرجعية. هذا أمر بالغ الأهمية لأننا نحتاج إلى التعامل مع النص ضمن هذه الحدود.

```csharp
// هذه هي الفقرة التي تحتوي على بداية الإشارة المرجعية.
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;

// هذه هي الفقرة التي تحتوي على نهاية الإشارة المرجعية.
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

if (startPara == null || endPara == null)
    throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");
```

## الخطوة 3: التحقق من صحة فقرات الوالدين

نحن بحاجة إلى التأكد من أن فقرات البداية والنهاية لها نفس الأصل. هذا سيناريو بسيط لإبقاء الأمور واضحة.

```csharp
// نقتصر على سيناريو بسيط إلى حد معقول.
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");
```

## الخطوة 4: تحديد العقدة التي يجب إيقافها

بعد ذلك، نحتاج إلى تحديد العقدة التي سنتوقف عندها عن نسخ النص. ستكون هذه العقدة هي العقدة التي تقع مباشرة بعد الفقرة الأخيرة.

```csharp
// نريد نسخ جميع الفقرات من الفقرة الأولية وحتى الفقرة النهائية (بما في ذلك الفقرة النهائية)،
// لذلك فإن العقدة التي نتوقف عندها هي العقدة التي تقع بعد الفقرة النهائية.
Node endNode = endPara.NextSibling;
```

## الخطوة 5: إضافة النص المُشار إليه إلى المستند الوجهة

أخيرًا، دعنا ننتقل عبر العقد من فقرة البداية إلى العقدة بعد فقرة النهاية، ونضيفها إلى المستند الوجهة.

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // يؤدي هذا إلى إنشاء نسخة من العقدة الحالية واستيرادها (جعلها صالحة) في السياق
    // المستند الوجهة. يعني الاستيراد ضبط الأنماط ومعرفات القائمة بشكل صحيح.
    Node newNode = importer.ImportNode(curNode, true);

    // إضافة العقدة المستوردة إلى المستند الوجهة.
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// احفظ مستند الوجهة مع النص الملحق.
dstDoc.Save("appended_document.docx");
```

## خاتمة

والآن، لقد نجحت في إضافة نص من قسم تم وضع إشارة مرجعية عليه في مستند Word باستخدام Aspose.Words for .NET. تجعل هذه الأداة القوية معالجة المستندات سهلة للغاية، والآن لديك حيلة أخرى في جعبتك. استمتع بالبرمجة!

## الأسئلة الشائعة

### هل يمكنني إضافة نص من إشارات مرجعية متعددة دفعة واحدة؟
نعم، يمكنك تكرار العملية لكل إشارة مرجعية وإضافة النص وفقًا لذلك.

### ماذا لو كانت فقرة البداية والفقرة النهائية لهما آباء مختلفون؟
يفترض المثال الحالي أن لديهم نفس الأصل. بالنسبة للأصلين المختلفين، يلزم معالجة أكثر تعقيدًا.

### هل يمكنني الاحتفاظ بالتنسيق الأصلي للنص الملحق؟
 بالتأكيد!`ImportFormatMode.KeepSourceFormatting` يضمن الحفاظ على التنسيق الأصلي.

### هل من الممكن إضافة نص إلى موضع محدد في المستند الوجهة؟
نعم، يمكنك إضافة النص إلى أي موضع بالانتقال إلى العقدة المطلوبة في المستند الوجهة.

### ماذا لو كنت بحاجة إلى إضافة نص من إشارة مرجعية إلى قسم جديد؟
يمكنك إنشاء قسم جديد في المستند الوجهة وإضافة النص هناك.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
