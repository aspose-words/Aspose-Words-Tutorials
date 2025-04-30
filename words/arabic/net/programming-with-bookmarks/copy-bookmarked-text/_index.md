---
"description": "انسخ النصوص المرجعية بسهولة بين مستندات Word باستخدام Aspose.Words لـ .NET. تعلّم كيفية القيام بذلك من خلال هذا الدليل خطوة بخطوة."
"linktitle": "نسخ النص المُضاف إلى الإشارات المرجعية في مستند Word"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "نسخ النص المُضاف إلى الإشارات المرجعية في مستند Word"
"url": "/ar/net/programming-with-bookmarks/copy-bookmarked-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# نسخ النص المُضاف إلى الإشارات المرجعية في مستند Word

## مقدمة

هل سبق لك أن وجدت نفسك بحاجة إلى نسخ أقسام محددة من مستند وورد إلى آخر؟ حسنًا، أنت محظوظ! في هذا البرنامج التعليمي، سنشرح لك كيفية نسخ نص مُضاف إلى المفضلة من مستند وورد إلى آخر باستخدام Aspose.Words لـ .NET. سواء كنت تُنشئ تقريرًا ديناميكيًا أو تُؤتمت عملية إنشاء المستندات، سيُبسّط هذا الدليل العملية عليك.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

- مكتبة Aspose.Words لـ .NET: يمكنك تنزيلها من [هنا](https://releases.aspose.com/words/net/).
- بيئة التطوير: Visual Studio أو أي بيئة تطوير .NET أخرى.
- المعرفة الأساسية بلغة C#: الإلمام ببرمجة C# وإطار عمل .NET.

## استيراد مساحات الأسماء

للبدء، تأكد من استيراد مساحات الأسماء الضرورية في مشروعك:

```csharp
using Aspose.Words;
using Aspose.Words.Import;
using Aspose.Words.Bookmark;
```

## الخطوة 1: تحميل المستند المصدر

أولاً وقبل كل شيء، عليك تحميل المستند المصدر الذي يحتوي على النص الذي وضعته في الإشارات المرجعية والذي تريد نسخه.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Bookmarks.docx");
```

هنا، `dataDir` هو المسار إلى دليل المستندات الخاص بك، و `Bookmarks.docx` هي الوثيقة المصدرية.

## الخطوة 2: تحديد الإشارة المرجعية

بعد ذلك، قم بتحديد الإشارة المرجعية التي ترغب في نسخها من المستند المصدر.

```csharp
Bookmark srcBookmark = srcDoc.Range.Bookmarks["MyBookmark1"];
```

يستبدل `"MyBookmark1"` مع الاسم الفعلي للإشارة المرجعية الخاصة بك.

## الخطوة 3: إنشاء مستند الوجهة

الآن قم بإنشاء مستند جديد حيث سيتم نسخ النص الذي قمت بإضافته إلى الإشارات المرجعية.

```csharp
Document dstDoc = new Document();
CompositeNode dstNode = dstDoc.LastSection.Body;
```

## الخطوة 4: استيراد المحتوى المُضاف إلى الإشارات المرجعية

لضمان الحفاظ على الأنماط والتنسيق، استخدم `NodeImporter` لاستيراد المحتوى المضاف إلى إشاراتك المرجعية من المستند المصدر إلى المستند الوجهة.

```csharp
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);
AppendBookmarkedText(importer, srcBookmark, dstNode);
```

## الخطوة 5: تحديد طريقة AppendBookmarkedText

هنا يأتي دور السحر. حدّد طريقةً لمعالجة نسخ النص المُضاف إلى المفضلة:

```csharp
private void AppendBookmarkedText(NodeImporter importer, Bookmark srcBookmark, CompositeNode dstNode)
{
    Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
    Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

    if (startPara == null || endPara == null)
        throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");

    if (startPara.ParentNode != endPara.ParentNode)
        throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");

    Node endNode = endPara.NextSibling;

    for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
    {
        Node newNode = importer.ImportNode(curNode, true);
        dstNode.AppendChild(newNode);
    }
}
```

## الخطوة 6: حفظ مستند الوجهة

وأخيرًا، احفظ مستند الوجهة للتحقق من المحتوى المنسوخ.

```csharp
dstDoc.Save(dataDir + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

## خاتمة

وهذا كل شيء! لقد نجحت في نسخ نص مُضاف إلى المفضلة من مستند Word إلى آخر باستخدام Aspose.Words لـ .NET. هذه الطريقة فعّالة لأتمتة مهام معالجة المستندات، مما يجعل سير عملك أكثر كفاءةً وتبسيطًا.

## الأسئلة الشائعة

### هل يمكنني نسخ إشارات مرجعية متعددة مرة واحدة؟
نعم، يمكنك تكرار الإشارات المرجعية المتعددة واستخدام نفس الطريقة لنسخ كل واحدة منها.

### ماذا يحدث إذا لم يتم العثور على الإشارة المرجعية؟
ال `Range.Bookmarks` سوف تعود الممتلكات `null`لذا تأكد من التعامل مع هذه الحالة لتجنب الاستثناءات.

### هل يمكنني الحفاظ على تنسيق الإشارة المرجعية الأصلية؟
بالتأكيد! باستخدام `ImportFormatMode.KeepSourceFormatting` ويضمن الحفاظ على التنسيق الأصلي.

### هل هناك حد لحجم النص الذي تم وضع إشارة مرجعية عليه؟
لا يوجد حد محدد، ولكن الأداء قد يختلف مع المستندات الكبيرة للغاية.

### هل يمكنني نسخ النص بين تنسيقات مستند Word المختلفة؟
نعم، يدعم Aspose.Words تنسيقات Word المختلفة، وتعمل الطريقة عبر هذه التنسيقات.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}