---
title: إظهار إخفاء الإشارات المرجعية في مستند Word
linktitle: إظهار إخفاء الإشارات المرجعية في مستند Word
second_title: Aspose.Words واجهة برمجة تطبيقات معالجة المستندات
description: تعرف على كيفية إظهار الإشارات المرجعية أو إخفائها ديناميكيًا في مستند Word باستخدام Aspose.Words لـ .NET من خلال دليلنا خطوة بخطوة. مثالية للمطورين.
weight: 10
url: /ar/net/programming-with-bookmarks/show-hide-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إظهار إخفاء الإشارات المرجعية في مستند Word

## مقدمة

هل وجدت نفسك بحاجة إلى إخفاء أو إظهار أجزاء معينة من مستند Word الخاص بك ديناميكيًا؟ حسنًا، أنت محظوظ! باستخدام Aspose.Words for .NET، يمكنك بسهولة إدارة رؤية المحتوى الذي تم وضع إشارة مرجعية عليه في مستنداتك. سيرشدك هذا البرنامج التعليمي خلال عملية إظهار الإشارات المرجعية وإخفائها في مستند Word باستخدام Aspose.Words for .NET. سنقوم بتحليل الكود خطوة بخطوة، لذا سواء كنت مطورًا متمرسًا أو مبتدئًا، ستجد هذا الدليل سهل المتابعة.

## المتطلبات الأساسية

قبل أن نتعمق في الكود، دعنا نتأكد من أن لديك كل ما تحتاجه:

1.  Aspose.Words for .NET: تأكد من تثبيت مكتبة Aspose.Words for .NET. إذا لم يكن الأمر كذلك، يمكنك تنزيله[هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: بيئة تطوير متكاملة (IDE) مثل Visual Studio.
3. المعرفة الأساسية بـ C#: الإلمام ببرمجة C# سيكون مفيدًا.
4. مستند Word: نموذج مستند Word يحتوي على إشارات مرجعية.

## استيراد مساحات الأسماء

قبل البدء بالكود، تحتاج إلى استيراد مساحات الأسماء الضرورية. أضف ما يلي في بداية ملف C# الخاص بك:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

## الخطوة 1: قم بتحميل المستند الخاص بك

أول الأشياء أولاً، تحتاج إلى تحميل مستند Word الذي يحتوي على الإشارات المرجعية. وإليك كيف يمكنك القيام بذلك:

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

### توضيح

- dataDir: هذا هو مسار الدليل الذي يوجد به مستند Word الخاص بك.
-  مستند المستند: يؤدي هذا إلى تهيئة مثيل جديد لـ`Document` فئة مع الملف المحدد الخاص بك.

## الخطوة 2: إظهار أو إخفاء المحتوى الذي تم وضع إشارة مرجعية عليه

بعد ذلك، سنحدد طريقة لإظهار أو إخفاء المحتوى الذي تم وضع إشارة مرجعية عليه. وإليكم الطريقة كاملة:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool showHide)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.MoveToDocumentEnd();

    // {إذا "{إشارة مرجعية MERGEFIELD}" = "صحيح" "" ""}
    Field field = builder.InsertField("IF \"", null);
    builder.MoveTo(field.Start.NextSibling);
    builder.InsertField("MERGEFIELD " + bookmarkName + "", null);
    builder.Write("\" = \"true\" ");
    builder.Write("\"");
    builder.Write("\"");
    builder.Write(" \"\"");

    Node currentNode = field.Start;
    bool flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.Run)
            if (currentNode.ToString(SaveFormat.Text).Trim() == "\"")
                flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkStart.ParentNode.InsertBefore(currentNode, bm.BookmarkStart);
        currentNode = nextNode;
    }

    Node endNode = bm.BookmarkEnd;
    flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.FieldEnd)
            flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkEnd.ParentNode.InsertAfter(currentNode, endNode);
        endNode = currentNode;
        currentNode = nextNode;
    }

    doc.MailMerge.Execute(new[] { bookmarkName }, new object[] { showHide });
}
```

### توضيح

- الإشارة المرجعية bm: لجلب الإشارة المرجعية من المستند.
- منشئ DocumentBuilder: يساعد في التنقل وتعديل المستند.
- حقل الحقل: يقوم بإدراج حقل IF للتحقق من حالة الإشارة المرجعية.
- العقدة الحالية: تتنقل عبر العقد للعثور على بداية الحقل ونهايته.

## الخطوة 3: تنفيذ وظيفة العرض/الإخفاء

 الآن عليك الاتصال بالرقم`ShowHideBookmarkedContent` الطريقة، تمرير المستند، اسم الإشارة المرجعية، وعلامة الرؤية:

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", false);
```

### توضيح

- مستند: كائن المستند الخاص بك.
- "MyBookmark1": اسم الإشارة المرجعية التي تريد إظهارها/إخفاءها.
- خطأ: علامة الرؤية (صواب للإظهار، خطأ للإخفاء).

## الخطوة 4: احفظ المستند الخاص بك

وأخيرا، احفظ الوثيقة المعدلة:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### توضيح

- dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx": مسار واسم المستند الجديد حيث سيتم حفظ التغييرات.

## خاتمة

وهناك لديك! لقد تعلمت بنجاح كيفية إظهار الإشارات المرجعية وإخفائها في مستند Word باستخدام Aspose.Words لـ .NET. يمكن أن تكون هذه التقنية مفيدة بشكل لا يصدق لإنشاء المستندات ذات المحتوى الشرطي ديناميكيًا.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟
Aspose.Words for .NET هي مكتبة قوية لمعالجة المستندات تتيح للمطورين إنشاء مستندات Word وتعديلها وتحويلها برمجيًا.

### كيف يمكنني الحصول على Aspose.Words لـ .NET؟
 يمكنك تنزيل Aspose.Words لـ .NET من[هنا](https://releases.aspose.com/words/net/). نسخة تجريبية مجانية متاحة أيضا.

### هل يمكنني استخدام هذه الطريقة لأنواع أخرى من الإشارات المرجعية؟
نعم، يمكن تكييف هذه الطريقة لإدارة رؤية أي إشارات مرجعية في مستند Word الخاص بك.

### ماذا لو لم يحتوي المستند الخاص بي على الإشارة المرجعية المحددة؟
إذا كانت الإشارة المرجعية غير موجودة، فستقوم الطريقة بإلقاء خطأ. تأكد من وجود الإشارة المرجعية قبل محاولة إظهارها/إخفائها.

### كيف يمكنني الحصول على الدعم إذا واجهت مشاكل؟
 يمكنك الحصول على الدعم من مجتمع Aspose[هنا](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
