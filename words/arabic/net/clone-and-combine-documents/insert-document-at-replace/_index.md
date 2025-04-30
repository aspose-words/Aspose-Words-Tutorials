---
"description": "تعلّم كيفية إدراج مستند Word بسلاسة في مستند آخر باستخدام Aspose.Words for .NET من خلال دليلنا المفصل خطوة بخطوة. مثالي للمطورين الذين يسعون إلى تبسيط معالجة المستندات."
"linktitle": "إدراج مستند عند الاستبدال"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "إدراج مستند عند الاستبدال"
"url": "/ar/net/clone-and-combine-documents/insert-document-at-replace/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إدراج مستند عند الاستبدال

## مقدمة

أهلاً بكم يا خبراء المستندات! هل وجدتم أنفسكم غارقين في البرمجة، تحاولون إيجاد طريقة لإدراج مستند وورد في آخر بسلاسة؟ لا تقلقوا، فنحن اليوم نتعمق في عالم Aspose.Words لـ .NET لنجعل هذه المهمة في غاية السهولة. سنشرح لكم خطوة بخطوة كيفية استخدام هذه المكتبة القوية لإدراج المستندات في نقاط محددة أثناء عملية البحث والاستبدال. هل أنتم مستعدون لتصبحوا خبراء في Aspose.Words؟ هيا بنا!

## المتطلبات الأساسية

قبل أن ننتقل إلى الكود، هناك بعض الأشياء التي تحتاج إلى وضعها في مكانها:

- فيجوال ستوديو: تأكد من تثبيت فيجوال ستوديو على جهازك. إذا لم يكن مثبتًا لديك بعد، يمكنك تنزيله من [هنا](https://visualstudio.microsoft.com/).
- Aspose.Words لـ .NET: ستحتاج إلى مكتبة Aspose.Words. يمكنك الحصول عليها من [موقع Aspose](https://releases.aspose.com/words/net/).
- المعرفة الأساسية بلغة C#: إن الفهم الأساسي للغة C# و.NET سيساعدك على متابعة هذا البرنامج التعليمي.

حسنًا، بعد أن انتهينا من هذه الأمور، فلنبدأ في تعلم بعض الأكواد البرمجية!

## استيراد مساحات الأسماء

أولاً، نحتاج إلى استيراد مساحات الأسماء اللازمة للعمل مع Aspose.Words. هذا يشبه تجميع جميع أدواتك قبل بدء أي مشروع. أضف هذه باستخدام التوجيهات في أعلى ملف C#:

```csharp
using System;
using System.Text.RegularExpressions;
using Aspose.Words;
using Aspose.Words.Replacing;
using Aspose.Words.Tables;
```

بعد أن حددنا متطلباتنا الأساسية، دعونا نقسم العملية إلى خطوات مُختصرة. كل خطوة حاسمة وستُقرّبنا من هدفنا.

## الخطوة 1: إعداد دليل المستندات

أولاً، علينا تحديد المجلد الذي تُخزَّن فيه مستنداتنا. هذا أشبه بتحضير المسرح قبل العرض الكبير.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

يستبدل `"YOUR DOCUMENT DIRECTORY"` مع المسار إلى دليلك. هنا ستعيش مستنداتك وتتنفس.

## الخطوة 2: تحميل المستند الرئيسي

بعد ذلك، نحمّل المستند الرئيسي الذي نريد إدراج مستند آخر فيه. اعتبره منصتنا الرئيسية حيث ستتم جميع الإجراءات.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

يقوم هذا الكود بتحميل المستند الرئيسي من الدليل المحدد.

## الخطوة 3: تعيين خيارات البحث والاستبدال

للعثور على الموقع المحدد الذي نريد إدراج مستندنا فيه، نستخدم خاصية البحث والاستبدال. يشبه هذا استخدام خريطة للعثور على الموقع الدقيق للإضافة الجديدة.

```csharp
FindReplaceOptions options = new FindReplaceOptions
{
    Direction = FindReplaceDirection.Backward,
    ReplacingCallback = new InsertDocumentAtReplaceHandler()
};
```

هنا، نقوم بتعيين الاتجاه إلى الخلف وتحديد معالج استدعاء مخصص سنقوم بتعريفه بعد ذلك.

## الخطوة 4: تنفيذ عملية الاستبدال

الآن، نخبر مستندنا الرئيسي بالبحث عن نص نائب محدد واستبداله بلا شيء، مع استخدام معاودة الاتصال المخصصة لإدراج مستند آخر.

```csharp
mainDoc.Range.Replace(new Regex("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

يقوم هذا الكود بإجراء عملية البحث والاستبدال، ثم يحفظ المستند المحدث.

## الخطوة 5: إنشاء معالج استدعاء الاستبدال المخصص

معالج استدعاء الاستدعاء المخصص لدينا هو نقطة التحول. سيحدد هذا المعالج كيفية إدخال المستند أثناء عملية البحث والاستبدال.

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

والجزء الأخير من لغزنا هو الطريقة التي يتم بها إدراج المستند في الموقع المحدد.

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

تعمل هذه الطريقة على استيراد العقد من المستند المراد إدراجها ووضعها في المكان الصحيح في المستند الرئيسي.

## خاتمة

هذا كل ما في الأمر! دليل شامل لإدراج مستند في آخر باستخدام Aspose.Words لـ .NET. باتباع هذه الخطوات، يمكنك أتمتة مهام تجميع المستندات ومعالجتها بسهولة. سواء كنت تُنشئ نظام إدارة مستندات أو تحتاج فقط إلى تبسيط سير عمل معالجة مستنداتك، فإن Aspose.Words هو رفيقك الموثوق.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟
Aspose.Words for .NET هي مكتبة فعّالة لمعالجة مستندات Word برمجيًا. تتيح لك إنشاء مستندات Word وتعديلها وتحويلها ومعالجتها بسهولة.

### هل يمكنني إدراج مستندات متعددة في وقت واحد؟
نعم، يمكنك تعديل معالج معاودة الاتصال للتعامل مع عمليات الإدخال المتعددة عن طريق التكرار عبر مجموعة من المستندات.

### هل هناك نسخة تجريبية مجانية متاحة؟
بالتأكيد! يمكنك تنزيل نسخة تجريبية مجانية من [هنا](https://releases.aspose.com/).

### كيف أحصل على الدعم لـ Aspose.Words؟
يمكنك الحصول على الدعم من خلال زيارة [منتدى Aspose.Words](https://forum.aspose.com/c/words/8).

### هل يمكنني الاحتفاظ بتنسيق المستند المدرج؟
نعم، `NodeImporter` تسمح لك الفئة بتحديد كيفية التعامل مع التنسيق عند استيراد العقد من مستند إلى آخر.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}