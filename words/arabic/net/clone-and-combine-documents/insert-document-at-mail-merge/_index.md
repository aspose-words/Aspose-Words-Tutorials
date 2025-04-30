---
"description": "تعرف على كيفية إدراج المستندات في حقول دمج البريد باستخدام Aspose.Words لـ .NET في هذا البرنامج التعليمي الشامل خطوة بخطوة."
"linktitle": "إدراج مستند في دمج البريد"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "إدراج مستند في دمج البريد"
"url": "/ar/net/clone-and-combine-documents/insert-document-at-mail-merge/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إدراج مستند في دمج البريد

## مقدمة

أهلاً بك في عالم أتمتة المستندات مع Aspose.Words لـ .NET! هل تساءلت يومًا عن كيفية إدراج مستندات ديناميكيًا في حقول محددة ضمن مستند رئيسي أثناء عملية دمج المراسلات؟ أنت في المكان الصحيح. سيرشدك هذا البرنامج التعليمي خطوة بخطوة خلال عملية إدراج المستندات في حقول دمج المراسلات باستخدام Aspose.Words لـ .NET. الأمر أشبه بتجميع أجزاء أحجية، حيث تتكامل كل قطعة في مكانها الصحيح. هيا بنا!

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

1. Aspose.Words لـ .NET: يمكنك [قم بتنزيل الإصدار الأحدث هنا](https://releases.aspose.com/words/net/)إذا كنت بحاجة إلى شراء ترخيص، يمكنك القيام بذلك [هنا](https://purchase.aspose.com/buy). وبدلا من ذلك، يمكنك الحصول على [رخصة مؤقتة](https://purchase.aspose.com/temporary-license/) أو جربها مع [نسخة تجريبية مجانية](https://releases.aspose.com/).
2. بيئة التطوير: Visual Studio أو أي بيئة تطوير متكاملة أخرى لـC#.
3. المعرفة الأساسية بلغة C#: إن الإلمام ببرمجة C# سيجعل هذا البرنامج التعليمي سهلاً.

## استيراد مساحات الأسماء

أولاً، ستحتاج إلى استيراد مساحات الأسماء اللازمة. هذه المساحات هي بمثابة اللبنات الأساسية لمشروعك.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.MailMerging;
using System.Linq;
```

دعونا نقسم العملية إلى خطوات سهلة. كل خطوة ستبني على سابقتها، مما يقودك إلى حل شامل.

## الخطوة 1: إعداد الدليل الخاص بك

قبل البدء بإدراج المستندات، عليك تحديد مسار مجلد المستندات. هذا هو المكان الذي تُخزَّن فيه مستنداتك.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## الخطوة 2: تحميل المستند الرئيسي

بعد ذلك، ستُحمّل المستند الرئيسي. يحتوي هذا المستند على حقول الدمج التي سيتم إدراج المستندات الأخرى فيها.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

## الخطوة 3: إعداد استدعاء دمج الحقول

لإدارة عملية الدمج، ستحتاج إلى إعداد دالة استدعاء. ستكون هذه الدالة مسؤولة عن إدراج المستندات في حقول الدمج المحددة.

```csharp
mainDoc.MailMerge.FieldMergingCallback = new InsertDocumentAtMailMergeHandler();
```

## الخطوة 4: تنفيذ دمج البريد

الآن حان وقت تنفيذ عملية دمج البريد. هنا تبدأ العملية. ستحدد حقل الدمج والمستند الذي يجب إدراجه فيه.

```csharp
mainDoc.MailMerge.Execute(new[] { "Document_1" }, new object[] { dataDir + "Document insertion 2.docx" });
```

## الخطوة 5: حفظ المستند

بعد اكتمال دمج البريد، ستحفظ المستند المعدّل. سيحتوي هذا المستند الجديد على المحتوى المُدرج في المكان الذي تريده.

```csharp
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

## الخطوة 6: إنشاء معالج الاتصال العكسي

معالج الاستدعاء هو فئة تُجري معالجة خاصة لحقل الدمج. يُحمّل المستند المحدد في قيمة الحقل ويُدرجه في حقل الدمج الحالي.

```csharp
private class InsertDocumentAtMailMergeHandler : IFieldMergingCallback
{
    void IFieldMergingCallback.FieldMerging(FieldMergingArgs args)
    {
        if (args.DocumentFieldName == "Document_1")
        {
            DocumentBuilder builder = new DocumentBuilder(args.Document);
            builder.MoveToMergeField(args.DocumentFieldName);

            Document subDoc = new Document((string)args.FieldValue);
            InsertDocument(builder.CurrentParagraph, subDoc);

            if (!builder.CurrentParagraph.HasChildNodes)
                builder.CurrentParagraph.Remove();

            args.Text = null;
        }
    }
}
```

## الخطوة 7: إدراج المستند

تقوم هذه الطريقة بإدراج المستند المحدد في الفقرة الحالية أو خلية الجدول.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        foreach (Node srcNode in srcSection.Body)
        {
            if (srcNode.NodeType == NodeType.Paragraph)
            {
                Paragraph para = (Paragraph)srcNode;
                if (para.IsEndOfSection && !para.HasChildNodes)
                    continue;
            }

            Node newNode = importer.ImportNode(srcNode, true);
            destinationParent.InsertAfter(newNode, insertionDestination);
            insertionDestination = newNode;
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}
```

## خاتمة

وها قد انتهيت! لقد نجحت في إدراج مستندات في حقول محددة أثناء عملية دمج بريد باستخدام Aspose.Words لـ .NET. هذه الميزة الفعّالة توفر عليك الكثير من الوقت والجهد، خاصةً عند التعامل مع كميات كبيرة من المستندات. تخيل الأمر وكأن لديك مساعدًا شخصيًا يتولى جميع المهام الشاقة نيابةً عنك. لذا، جرّبها. برمجة ممتعة!

## الأسئلة الشائعة

### هل يمكنني إدراج مستندات متعددة في حقول الدمج المختلفة؟
نعم، يمكنك ذلك. ما عليك سوى تحديد حقول الدمج المناسبة ومسارات المستندات المقابلة في `MailMerge.Execute` طريقة.

### هل من الممكن تنسيق المستند المدرج بشكل مختلف عن المستند الرئيسي؟
بالتأكيد! يمكنك استخدام `ImportFormatMode` المعلمة في `NodeImporter` للتحكم في التنسيق.

### ماذا لو كان اسم حقل الدمج ديناميكيًا؟
يمكنك التعامل مع أسماء حقول الدمج الديناميكية عن طريق تمريرها كمعلمات إلى معالج الاستدعاء.

### هل يمكنني استخدام هذه الطريقة مع تنسيقات ملفات مختلفة؟
نعم، يدعم Aspose.Words تنسيقات الملفات المختلفة بما في ذلك DOCX وPDF والمزيد.

### كيف أتعامل مع الأخطاء أثناء عملية إدراج المستند؟
قم بتنفيذ معالجة الأخطاء في معالج معاودة الاتصال الخاص بك لإدارة أي استثناءات قد تحدث.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}