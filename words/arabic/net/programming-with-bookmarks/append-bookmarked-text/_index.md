---
"description": "تعرّف على كيفية إضافة نص مُضاف إلى مستندات Word باستخدام Aspose.Words لـ .NET من خلال هذا الدليل المُفصّل. مثالي للمطورين."
"linktitle": "إضافة نص مُضاف إلى الإشارات المرجعية في مستند Word"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "إضافة نص مُضاف إلى الإشارات المرجعية في مستند Word"
"url": "/ar/net/programming-with-bookmarks/append-bookmarked-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إضافة نص مُضاف إلى الإشارات المرجعية في مستند Word

## مقدمة

أهلاً! هل سبق لك أن حاولت إضافة نص من قسم مُضاف إليه إشارة مرجعية في مستند وورد ووجدت الأمر صعباً؟ أنت محظوظ! سيشرح لك هذا البرنامج التعليمي العملية باستخدام Aspose.Words لـ .NET. سنُقسّمها إلى خطوات بسيطة لتتمكن من متابعتها بسهولة. هيا بنا نبدأ ونُضيف النص المُضاف إليه إشارة مرجعية باحترافية!

## المتطلبات الأساسية

قبل أن نبدأ، دعونا نتأكد من أن لديك كل ما تحتاجه:

- Aspose.Words لـ .NET: تأكد من تثبيته. إذا لم يكن كذلك، يمكنك [قم بتحميله هنا](https://releases.aspose.com/words/net/).
- بيئة التطوير: أي بيئة تطوير .NET مثل Visual Studio.
- المعرفة الأساسية بلغة C#: إن فهم مفاهيم البرمجة الأساسية بلغة C# سوف يساعدك.
- مستند Word مع إشارات مرجعية: مستند Word مع إشارات مرجعية تم إعدادها، والتي سنستخدمها لإضافة نص منها.

## استيراد مساحات الأسماء

أولاً، لنستورد مساحات الأسماء اللازمة. سيضمن هذا توفر جميع الأدوات اللازمة في متناول أيدينا.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

دعونا نقسم المثال إلى خطوات مفصلة.

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

الآن، لنحدد الفقرات التي تبدأ وتنتهي عندها الإشارة المرجعية. هذا أمر بالغ الأهمية لأننا نحتاج إلى التعامل مع النص ضمن هذه الحدود.

```csharp
// هذه هي الفقرة التي تحتوي على بداية الإشارة المرجعية.
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;

// هذه هي الفقرة التي تحتوي على نهاية الإشارة المرجعية.
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

if (startPara == null || endPara == null)
    throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");
```

## الخطوة 3: التحقق من صحة فقرات الوالدين

يجب التأكد من أن فقرات البداية والنهاية تحمل نفس الأصل. هذا سيناريو بسيط لتسهيل الأمور.

```csharp
// دعونا نقتصر على سيناريو بسيط إلى حد معقول.
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");
```

## الخطوة 4: تحديد العقدة التي يجب إيقافها

بعد ذلك، علينا تحديد العقدة التي سنتوقف عندها عن نسخ النص. ستكون هذه العقدة بعد الفقرة الأخيرة مباشرةً.

```csharp
// نريد نسخ جميع الفقرات من الفقرة الأولية وحتى الفقرة النهائية (بما في ذلك الفقرة النهائية)،
// لذلك فإن العقدة التي نتوقف عندها هي العقدة التي تقع بعد الفقرة النهائية.
Node endNode = endPara.NextSibling;
```

## الخطوة 5: إضافة النص المُضاف إلى المستند الوجهة

أخيرًا، دعنا ننتقل عبر العقد من الفقرة الأولية إلى العقدة بعد الفقرة النهائية، ونضيفها إلى المستند الوجهة.

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // يؤدي هذا إلى إنشاء نسخة من العقدة الحالية واستيرادها (يجعلها صالحة) في السياق
    // للمستند الوجهة. الاستيراد يعني ضبط الأنماط ومعرفات القائمة بشكل صحيح.
    Node newNode = importer.ImportNode(curNode, true);

    // أضف العقدة المستوردة إلى المستند الوجهة.
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// احفظ مستند الوجهة مع النص الملحق.
dstDoc.Save("appended_document.docx");
```

## خاتمة

وها قد انتهيت! لقد نجحت في إضافة نص من قسم مُضاف إلى المفضلة في مستند وورد باستخدام Aspose.Words لـ .NET. تُسهّل هذه الأداة القوية التعامل مع المستندات، والآن لديك حيلة أخرى في جعبتك. برمجة ممتعة!

## الأسئلة الشائعة

### هل يمكنني إضافة نص من إشارات مرجعية متعددة في وقت واحد؟
نعم، يمكنك تكرار العملية لكل إشارة مرجعية وإضافة النص وفقًا لذلك.

### ماذا لو كانت فقرات البداية والنهاية لها آباء مختلفون؟
يفترض المثال الحالي أن لديهما نفس الأصل. أما بالنسبة للأصلين المختلفين، فيتطلب الأمر معالجة أكثر تعقيدًا.

### هل يمكنني الاحتفاظ بالتنسيق الأصلي للنص الملحق؟
بالتأكيد! `ImportFormatMode.KeepSourceFormatting` يضمن الحفاظ على التنسيق الأصلي.

### هل من الممكن إضافة نص إلى موضع محدد في المستند الوجهة؟
نعم، يمكنك إضافة النص إلى أي موضع بالانتقال إلى العقدة المطلوبة في المستند الوجهة.

### ماذا لو كنت بحاجة إلى إضافة نص من إشارة مرجعية إلى قسم جديد؟
يمكنك إنشاء قسم جديد في المستند الوجهة وإضافة النص إليه.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}