---
title: إظهار أو إخفاء المحتوى المُضاف إلى الإشارات المرجعية في مستند Word
linktitle: إظهار أو إخفاء المحتوى المُضاف إلى الإشارات المرجعية في مستند Word
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إظهار المحتوى الذي تم وضع إشارة مرجعية عليه وإخفائه في مستندات Word باستخدام Aspose.Words for .NET من خلال هذا الدليل المفصل خطوة بخطوة.
weight: 10
url: /ar/net/programming-with-bookmarks/show-hide-bookmarked-content/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إظهار أو إخفاء المحتوى المُضاف إلى الإشارات المرجعية في مستند Word

## مقدمة

هل أنت مستعد للغوص في عالم معالجة المستندات باستخدام Aspose.Words for .NET؟ سواء كنت مطورًا يبحث عن أتمتة مهام المستندات أو مجرد شخص فضولي بشأن التعامل مع ملفات Word برمجيًا، فأنت في المكان المناسب. اليوم، سنستكشف كيفية إظهار وإخفاء المحتوى المُشار إليه في مستند Word باستخدام Aspose.Words for .NET. سيجعلك هذا الدليل خطوة بخطوة محترفًا في التحكم في رؤية المحتوى استنادًا إلى الإشارات المرجعية. لنبدأ!

## المتطلبات الأساسية

قبل أن ننتقل إلى التفاصيل الدقيقة، هناك بعض الأشياء التي ستحتاجها:

1. Visual Studio: أي إصدار متوافق مع .NET.
2.  Aspose.Words for .NET: قم بتنزيله[هنا](https://releases.aspose.com/words/net/).
3. الفهم الأساسي للغة C#: إذا كان بإمكانك كتابة برنامج "Hello World" البسيط، فأنت على ما يرام.
4. مستند Word يحتوي على إشارات مرجعية: سنستخدم مستندًا نموذجيًا يحتوي على إشارات مرجعية لهذا البرنامج التعليمي.

## استيراد مساحات الأسماء

أولاً وقبل كل شيء، دعنا نستورد مساحات الأسماء الضرورية. وهذا يضمن حصولنا على كل الأدوات التي نحتاجها لمهمتنا.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

مع وضع هذه المساحات الأسماء في مكانها الصحيح، أصبحنا جاهزين لبدء رحلتنا.

## الخطوة 1: إعداد مشروعك

حسنًا، فلنبدأ بإعداد مشروعنا في Visual Studio.

### إنشاء مشروع جديد

افتح Visual Studio وأنشئ مشروع تطبيق وحدة تحكم جديد (.NET Core). أطلق عليه اسمًا جذابًا، مثل "BookmarkVisibilityManager".

### إضافة Aspose.Words إلى .NET

سوف تحتاج إلى إضافة Aspose.Words for .NET إلى مشروعك. يمكنك القيام بذلك عبر NuGet Package Manager.

1. انتقل إلى الأدوات > مدير حزم NuGet > إدارة حزم NuGet للحل.
2. ابحث عن "Aspose.Words".
3. تثبيت الحزمة.

رائع! الآن بعد أن تم إعداد مشروعنا، فلننتقل إلى تحميل مستندنا.

## الخطوة 2: تحميل المستند

نحتاج إلى تحميل مستند Word الذي يحتوي على الإشارات المرجعية. في هذا البرنامج التعليمي، سنستخدم مستندًا نموذجيًا باسم "Bookmarks.docx".

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

 يحدد مقتطف التعليمات البرمجية هذا المسار إلى دليل المستند الخاص بك ويقوم بتحميل المستند في`doc` هدف.

## الخطوة 3: إظهار/إخفاء المحتوى المُضاف إلى الإشارات المرجعية

الآن يأتي الجزء الممتع - إظهار أو إخفاء المحتوى بناءً على الإشارات المرجعية. سننشئ طريقة تسمى`ShowHideBookmarkedContent` للتعامل مع هذا.

إليك الطريقة التي ستعمل على تبديل رؤية المحتوى الذي تم وضع إشارة مرجعية عليه:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    Node currentNode = bm.BookmarkStart;
    while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
    {
        if (currentNode.NodeType == NodeType.Run)
        {
            Run run = currentNode as Run;
            run.Font.Hidden = isHidden;
        }
        currentNode = currentNode.NextSibling;
    }
}
```

### تفصيل الطريقة

-  استرجاع الإشارة المرجعية:`Bookmark bm = doc.Range.Bookmarks[bookmarkName];` يقوم بجلب الإشارة المرجعية.
- عبور العقدة: نقوم بعبور العقد الموجودة داخل الإشارة المرجعية.
-  تبديل الرؤية: إذا كانت العقدة عبارة عن`Run` (سلسلة متجاورة من النص)، قمنا بتعيينها`Hidden` ملكية.

## الخطوة 4: تطبيق الطريقة

بعد أن وضعنا طريقتنا موضع التنفيذ، فلنطبقها لإظهار أو إخفاء المحتوى استنادًا إلى الإشارة المرجعية.

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true);
```

سيقوم هذا السطر من التعليمات البرمجية بإخفاء المحتوى داخل الإشارة المرجعية المسماة "MyBookmark1".

## الخطوة 5: حفظ المستند

وأخيرًا، دعونا نحفظ مستندنا المعدّل.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

يؤدي هذا إلى حفظ المستند بالتغييرات التي أجريناها.

## خاتمة

والآن، لقد تعلمت للتو كيفية إظهار وإخفاء المحتوى الذي تمت الإشارة إليه في مستند Word باستخدام Aspose.Words for .NET. تجعل هذه الأداة القوية معالجة المستندات سهلة للغاية، سواء كنت تقوم بأتمتة التقارير أو إنشاء قوالب أو مجرد العبث بملفات Word. استمتع بالبرمجة!

## الأسئلة الشائعة

### هل يمكنني تبديل إشارات مرجعية متعددة مرة واحدة؟
 نعم يمكنك الاتصال`ShowHideBookmarkedContent` الطريقة لكل إشارة مرجعية تريد تبديلها.

### هل يؤثر إخفاء المحتوى على بنية المستند؟
لا، إن إخفاء المحتوى يؤثر فقط على ظهوره، ويظل المحتوى موجودًا في المستند.

### هل يمكنني استخدام هذه الطريقة لأنواع أخرى من المحتوى؟
تعمل هذه الطريقة على تبديل تشغيلات النصوص على وجه التحديد. بالنسبة لأنواع المحتوى الأخرى، ستحتاج إلى تعديل منطق عبور العقد.

### هل Aspose.Words لـ .NET مجاني؟
 يقدم Aspose.Words نسخة تجريبية مجانية[هنا](https://releases.aspose.com/) ولكن يلزم الحصول على ترخيص كامل للاستخدام الإنتاجي. يمكنك شراؤه[هنا](https://purchase.aspose.com/buy).

### كيف يمكنني الحصول على الدعم إذا واجهت مشاكل؟
 يمكنك الحصول على الدعم من مجتمع Aspose[هنا](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
