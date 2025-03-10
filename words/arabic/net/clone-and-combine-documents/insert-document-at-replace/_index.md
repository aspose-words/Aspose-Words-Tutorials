---
title: إدراج مستند عند الاستبدال
linktitle: إدراج مستند عند الاستبدال
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إدراج مستند Word في مستند آخر بسلاسة باستخدام Aspose.Words for .NET من خلال دليلنا المفصل خطوة بخطوة. مثالي للمطورين الذين يتطلعون إلى تبسيط معالجة المستندات.
weight: 10
url: /ar/net/clone-and-combine-documents/insert-document-at-replace/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إدراج مستند عند الاستبدال

## مقدمة

مرحبًا بكم، أيها الخبراء في التعامل مع المستندات! هل وجدت نفسك منغمسًا في كتابة التعليمات البرمجية، وتحاول معرفة كيفية إدراج مستند Word في مستند آخر بسلاسة؟ لا تقلق، لأننا اليوم نتعمق في عالم Aspose.Words for .NET لتسهيل هذه المهمة. سنستعرض دليلًا تفصيليًا خطوة بخطوة حول كيفية استخدام هذه المكتبة القوية لإدراج المستندات في نقاط معينة أثناء عملية البحث والاستبدال. هل أنت مستعد لتصبح معالجًا في Aspose.Words؟ لنبدأ!

## المتطلبات الأساسية

قبل أن ننتقل إلى الكود، هناك بعض الأشياء التي تحتاج إلى وضعها في مكانها:

-  Visual Studio: تأكد من تثبيت Visual Studio على جهازك. إذا لم يكن مثبتًا لديك بعد، فيمكنك تنزيله من[هنا](https://visualstudio.microsoft.com/).
-  Aspose.Words لـ .NET: ستحتاج إلى مكتبة Aspose.Words. يمكنك الحصول عليها من[موقع اسبوس](https://releases.aspose.com/words/net/).
- المعرفة الأساسية بلغة C#: إن الفهم الأساسي للغة C# و.NET سيساعدك على متابعة هذا البرنامج التعليمي.

حسنًا، بعد أن انتهينا من هذه الأمور، فلنبدأ في استخدام بعض الأكواد البرمجية!

## استيراد مساحات الأسماء

أولاً وقبل كل شيء، نحتاج إلى استيراد مساحات الأسماء اللازمة للعمل مع Aspose.Words. هذا يشبه تجميع كل أدواتك قبل بدء المشروع. أضف هذه باستخدام التوجيهات في أعلى ملف C# الخاص بك:

```csharp
using System;
using System.Text.RegularExpressions;
using Aspose.Words;
using Aspose.Words.Replacing;
using Aspose.Words.Tables;
```

الآن بعد أن حددنا المتطلبات الأساسية، فلنبدأ في تقسيم العملية إلى خطوات صغيرة. كل خطوة مهمة وستقربنا من هدفنا.

## الخطوة 1: إعداد دليل المستندات

أولاً، نحتاج إلى تحديد الدليل الذي سيتم تخزين مستنداتنا فيه. وهذا يشبه إعداد المسرح قبل العرض الكبير.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 يستبدل`"YOUR DOCUMENT DIRECTORY"` مع المسار إلى الدليل الخاص بك. هذا هو المكان الذي ستعيش فيه مستنداتك وتتنفس.

## الخطوة 2: تحميل المستند الرئيسي

بعد ذلك، نقوم بتحميل المستند الرئيسي الذي نريد إدراج مستند آخر فيه. فكر في هذا باعتباره المرحلة الرئيسية التي ستحدث فيها كل الإجراءات.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

يقوم هذا الكود بتحميل المستند الرئيسي من الدليل المحدد.

## الخطوة 3: تعيين خيارات البحث والاستبدال

للعثور على الموقع المحدد الذي نريد إدراج مستندنا فيه، نستخدم وظيفة البحث والاستبدال. وهذا يشبه استخدام خريطة للعثور على المكان الدقيق للإضافة الجديدة.

```csharp
FindReplaceOptions options = new FindReplaceOptions
{
    Direction = FindReplaceDirection.Backward,
    ReplacingCallback = new InsertDocumentAtReplaceHandler()
};
```

هنا، نقوم بتعيين الاتجاه إلى الخلف وتحديد معالج استدعاء مخصص سنقوم بتعريفه بعد ذلك.

## الخطوة 4: قم بإجراء عملية الاستبدال

الآن، نخبر مستندنا الرئيسي بالبحث عن نص نائب محدد واستبداله بلا شيء، مع استخدام معاودة الاتصال المخصصة لإدراج مستند آخر.

```csharp
mainDoc.Range.Replace(new Regex("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

يقوم هذا الكود بإجراء عملية البحث والاستبدال، ثم يحفظ المستند المحدث.

## الخطوة 5: إنشاء معالج استدعاء بديل مخصص

إن معالج الاستدعاء المخصص لدينا هو المكان الذي تحدث فيه السحر. سيحدد هذا المعالج كيفية تنفيذ عملية إدراج المستند أثناء عملية البحث والاستبدال.

```csharp
private class InsertDocumentAtReplaceHandler : IReplacingCallback
{
    ReplaceAction IReplacingCallback.Replacing(ReplacingArgs args)
    {
        Document subDoc = new Document(dataDir + "Document insertion 2.docx");

        // قم بإدراج مستند بعد الفقرة التي تحتوي على نص المطابقة.
        Paragraph para = (Paragraph)args.MatchNode.ParentNode;
        InsertDocument(para, subDoc);

        // قم بإزالة الفقرة التي تحتوي على النص المطابق.
        para.Remove();
        return ReplaceAction.Skip;
    }
}
```

هنا، نقوم بتحميل المستند المراد إدراجه ثم نستدعي طريقة مساعدة لإجراء عملية الإدراج.

## الخطوة 6: تحديد طريقة إدراج المستند

الجزء الأخير من لغزنا هو الطريقة التي تقوم فعليًا بإدراج المستند في الموقع المحدد.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    // التحقق مما إذا كانت وجهة الإدراج عبارة عن فقرة أو جدول
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;

        // إنشاء NodeImporter لاستيراد العقد من المستند المصدر
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        // قم بالتنقل عبر جميع العقد على مستوى الكتلة في أقسام المستند المصدر
        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        {
            foreach (Node srcNode in srcSection.Body)
            {
                // تخطي الفقرة الفارغة الأخيرة من القسم
                if (srcNode.NodeType == NodeType.Paragraph)
                {
                    Paragraph para = (Paragraph)srcNode;
                    if (para.IsEndOfSection && !para.HasChildNodes)
                        continue;
                }

                // استيراد العقدة وإدراجها في الوجهة
                Node newNode = importer.ImportNode(srcNode, true);
                destinationParent.InsertAfter(newNode, insertionDestination);
                insertionDestination = newNode;
            }
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}

```

تهتم هذه الطريقة باستيراد العقد من المستند المراد إدراجها ووضعها في المكان الصحيح في المستند الرئيسي.

## خاتمة

والآن لديك الدليل الشامل لإدراج مستند في مستند آخر باستخدام Aspose.Words for .NET. باتباع هذه الخطوات، يمكنك أتمتة مهام تجميع المستندات ومعالجتها بسهولة. سواء كنت تقوم ببناء نظام إدارة مستندات أو كنت بحاجة فقط إلى تبسيط سير عمل معالجة المستندات، فإن Aspose.Words هو رفيقك الموثوق.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟
Aspose.Words for .NET هي مكتبة قوية للتعامل مع مستندات Word برمجيًا. فهي تتيح لك إنشاء مستندات Word وتعديلها وتحويلها ومعالجتها بسهولة.

### هل يمكنني إدراج مستندات متعددة في وقت واحد؟
نعم، يمكنك تعديل معالج معاودة الاتصال للتعامل مع عمليات الإدخال المتعددة عن طريق التكرار عبر مجموعة من المستندات.

### هل هناك نسخة تجريبية مجانية متاحة؟
 بالتأكيد! يمكنك تنزيل نسخة تجريبية مجانية من[هنا](https://releases.aspose.com/).

### كيف أحصل على الدعم لـ Aspose.Words؟
 يمكنك الحصول على الدعم من خلال زيارة[منتدى Aspose.Words](https://forum.aspose.com/c/words/8).

### هل يمكنني الاحتفاظ بتنسيق المستند المدرج؟
 نعم،`NodeImporter` تسمح لك الفئة بتحديد كيفية التعامل مع التنسيق عند استيراد العقد من مستند إلى آخر.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
