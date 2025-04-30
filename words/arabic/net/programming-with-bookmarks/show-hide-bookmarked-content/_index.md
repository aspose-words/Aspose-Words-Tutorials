---
"description": "تعرف على كيفية إظهار المحتوى الذي تم وضع إشارة مرجعية عليه وإخفائه في مستندات Word باستخدام Aspose.Words for .NET باستخدام هذا الدليل المفصل خطوة بخطوة."
"linktitle": "إظهار أو إخفاء المحتوى المُضاف إلى الإشارات المرجعية في مستند Word"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "إظهار أو إخفاء المحتوى المُضاف إلى الإشارات المرجعية في مستند Word"
"url": "/ar/net/programming-with-bookmarks/show-hide-bookmarked-content/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إظهار أو إخفاء المحتوى المُضاف إلى الإشارات المرجعية في مستند Word

## مقدمة

هل أنت مستعد للتعمق في عالم معالجة المستندات باستخدام Aspose.Words لـ .NET؟ سواء كنت مطورًا يبحث عن أتمتة مهام المستندات أو مجرد شخص مهتم بمعالجة ملفات Word برمجيًا، فأنت في المكان المناسب. سنستكشف اليوم كيفية إظهار وإخفاء المحتوى المُضاف إلى الإشارات المرجعية في مستند Word باستخدام Aspose.Words لـ .NET. سيجعلك هذا الدليل التفصيلي محترفًا في التحكم في ظهور المحتوى بناءً على الإشارات المرجعية. هيا بنا نبدأ!

## المتطلبات الأساسية

قبل أن ننتقل إلى التفاصيل الدقيقة، هناك بعض الأشياء التي ستحتاجها:

1. Visual Studio: أي إصدار متوافق مع .NET.
2. Aspose.Words لـ .NET: تنزيله [هنا](https://releases.aspose.com/words/net/).
3. الفهم الأساسي للغة C#: إذا كنت تستطيع كتابة برنامج "Hello World" البسيط، فأنت على ما يرام.
4. مستند Word يحتوي على إشارات مرجعية: سنستخدم مستندًا نموذجيًا يحتوي على إشارات مرجعية لهذا البرنامج التعليمي.

## استيراد مساحات الأسماء

أولاً، لنستورد مساحات الأسماء اللازمة. هذا يضمن توفر جميع الأدوات اللازمة لمهمتنا.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

مع وضع هذه المساحات الأسماء في مكانها الصحيح، أصبحنا جاهزين لبدء رحلتنا.

## الخطوة 1: إعداد مشروعك

حسنًا، لنبدأ الأمور بإعداد مشروعنا في Visual Studio.

### إنشاء مشروع جديد

افتح Visual Studio وأنشئ مشروع تطبيق وحدة تحكم (.NET Core). سمِّه اسمًا جذابًا، مثل "BookmarkVisibilityManager".

### إضافة Aspose.Words لـ .NET

ستحتاج إلى إضافة Aspose.Words for .NET إلى مشروعك. يمكنك القيام بذلك عبر مدير حزم NuGet.

1. انتقل إلى الأدوات > مدير حزم NuGet > إدارة حزم NuGet للحل.
2. ابحث عن "Aspose.Words".
3. تثبيت الحزمة.

رائع! الآن وقد انتهينا من إعداد مشروعنا، لننتقل إلى تحميل مستندنا.

## الخطوة 2: تحميل المستند

نحتاج إلى تحميل مستند وورد الذي يحتوي على الإشارات المرجعية. في هذا الدرس، سنستخدم مستندًا نموذجيًا باسم "Bookmarks.docx".

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

يحدد مقتطف التعليمات البرمجية هذا المسار إلى دليل المستند الخاص بك ويحمل المستند في `doc` هدف.

## الخطوة 3: إظهار/إخفاء المحتوى المُضاف إلى الإشارات المرجعية

الآن يأتي الجزء الممتع - إظهار أو إخفاء المحتوى بناءً على الإشارات المرجعية. سننشئ طريقة تُسمى `ShowHideBookmarkedContent` للتعامل مع هذا.

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

- استرجاع الإشارة المرجعية: `Bookmark bm = doc.Range.Bookmarks[bookmarkName];` يقوم بجلب الإشارة المرجعية.
- عبور العقدة: نقوم بعبور العقد الموجودة داخل الإشارة المرجعية.
- تبديل الرؤية: إذا كانت العقدة عبارة عن `Run` (سلسلة متجاورة من النص)، قمنا بتعيينها `Hidden` ملكية.

## الخطوة 4: تطبيق الطريقة

بعد أن طبقنا طريقتنا، فلنطبقها لإظهار أو إخفاء المحتوى استنادًا إلى الإشارة المرجعية.

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true);
```

سوف يقوم هذا السطر من التعليمات البرمجية بإخفاء المحتوى داخل الإشارة المرجعية المسماة "MyBookmark1".

## الخطوة 5: حفظ المستند

وأخيرًا، دعونا نحفظ مستندنا المعدّل.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

يؤدي هذا إلى حفظ المستند بالتغييرات التي أجريناها.

## خاتمة

ها قد انتهيت! لقد تعلمت للتو كيفية إظهار وإخفاء المحتوى المُضاف إلى المفضلة في مستند وورد باستخدام Aspose.Words لـ .NET. تُسهّل هذه الأداة القوية التعامل مع المستندات، سواءً كنت تُؤتمت التقارير، أو تُنشئ قوالب، أو تُجري تعديلات بسيطة على ملفات وورد. برمجة ممتعة!

## الأسئلة الشائعة

### هل يمكنني تبديل إشارات مرجعية متعددة في وقت واحد؟
نعم يمكنك الاتصال `ShowHideBookmarkedContent` الطريقة لكل إشارة مرجعية تريد تبديلها.

### هل يؤثر إخفاء المحتوى على بنية المستند؟
لا، إخفاء المحتوى يؤثر فقط على ظهوره، ويبقى المحتوى في المستند.

### هل يمكنني استخدام هذه الطريقة لأنواع أخرى من المحتوى؟
هذه الطريقة تُبدّل تشغيل النصوص تحديدًا. بالنسبة لأنواع المحتوى الأخرى، ستحتاج إلى تعديل منطق عبور العقد.

### هل Aspose.Words لـ .NET مجاني؟
يقدم Aspose.Words نسخة تجريبية مجانية [هنا](https://releases.aspose.com/)، ولكن يلزم الحصول على ترخيص كامل للاستخدام الإنتاجي. يمكنك شراؤه [هنا](https://purchase.aspose.com/buy).

### كيف يمكنني الحصول على الدعم إذا واجهت مشاكل؟
يمكنك الحصول على الدعم من مجتمع Aspose [هنا](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}