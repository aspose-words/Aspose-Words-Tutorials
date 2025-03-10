---
title: إدراج مستند في دمج البريد
linktitle: إدراج مستند في دمج البريد
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إدراج المستندات في حقول دمج البريد باستخدام Aspose.Words لـ .NET في هذا البرنامج التعليمي الشامل خطوة بخطوة.
weight: 10
url: /ar/net/clone-and-combine-documents/insert-document-at-mail-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إدراج مستند في دمج البريد

## مقدمة

مرحبًا بك في عالم أتمتة المستندات باستخدام Aspose.Words for .NET! هل تساءلت يومًا عن كيفية إدراج المستندات ديناميكيًا في حقول معينة داخل مستند رئيسي أثناء عملية دمج المراسلات؟ حسنًا، أنت في المكان الصحيح. سيرشدك هذا البرنامج التعليمي خطوة بخطوة خلال عملية إدراج المستندات في حقول دمج المراسلات باستخدام Aspose.Words for .NET. الأمر أشبه بتجميع قطع أحجية، حيث تقع كل قطعة في مكانها تمامًا. لذا، فلنبدأ!

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

1.  Aspose.Words لـ .NET: يمكنك[قم بتنزيل الإصدار الأحدث هنا](https://releases.aspose.com/words/net/) إذا كنت بحاجة إلى شراء ترخيص، فيمكنك القيام بذلك[هنا](https://purchase.aspose.com/buy) . وبدلا من ذلك، يمكنك الحصول على[رخصة مؤقتة](https://purchase.aspose.com/temporary-license/) أو جربها مع[نسخة تجريبية مجانية](https://releases.aspose.com/).
2. بيئة التطوير: Visual Studio أو أي C# IDE آخر.
3. المعرفة الأساسية بلغة C#: إن الإلمام ببرمجة C# سيجعل هذا البرنامج التعليمي سهلاً.

## استيراد مساحات الأسماء

أولاً وقبل كل شيء، ستحتاج إلى استيراد مساحات الأسماء الضرورية. فهي بمثابة اللبنات الأساسية لمشروعك.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.MailMerging;
using System.Linq;
```

دعنا نقسم العملية إلى خطوات يمكن إدارتها. كل خطوة ستعتمد على الخطوة السابقة، مما يقودك إلى الحل الكامل.

## الخطوة 1: إعداد الدليل الخاص بك

قبل أن تتمكن من البدء في إدراج المستندات، يتعين عليك تحديد المسار إلى دليل المستندات. هذا هو المكان الذي يتم فيه تخزين مستنداتك.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## الخطوة 2: تحميل المستند الرئيسي

بعد ذلك، ستقوم بتحميل المستند الرئيسي. يحتوي هذا المستند على حقول الدمج التي سيتم إدراج المستندات الأخرى فيها.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

## الخطوة 3: إعداد معاودة الاتصال لدمج الحقول

للتعامل مع عملية الدمج، ستحتاج إلى تعيين وظيفة استدعاء. ستكون هذه الوظيفة مسؤولة عن إدراج المستندات في حقول الدمج المحددة.

```csharp
mainDoc.MailMerge.FieldMergingCallback = new InsertDocumentAtMailMergeHandler();
```

## الخطوة 4: تنفيذ دمج المراسلات

الآن حان الوقت لتنفيذ عملية دمج البريد. وهنا يحدث السحر. ستحدد حقل الدمج والمستند الذي يجب إدراجه في هذا الحقل.

```csharp
mainDoc.MailMerge.Execute(new[] { "Document_1" }, new object[] { dataDir + "Document insertion 2.docx" });
```

## الخطوة 5: حفظ المستند

بعد اكتمال عملية دمج البريد، ستحفظ المستند المعدّل. سيحتوي هذا المستند الجديد على المحتوى المدرج في المكان الذي تريده.

```csharp
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

## الخطوة 6: إنشاء معالج الاتصال الراجع

معالج الاستدعاء هو فئة تقوم بمعالجة خاصة لحقل الدمج. فهو يقوم بتحميل المستند المحدد في قيمة الحقل وإدراجه في حقل الدمج الحالي.

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

وها أنت ذا! لقد نجحت في إدراج مستندات في حقول معينة أثناء عملية دمج المراسلات باستخدام Aspose.Words for .NET. يمكن لهذه الميزة القوية أن توفر لك قدرًا كبيرًا من الوقت والجهد، وخاصة عند التعامل مع كميات كبيرة من المستندات. فكر في الأمر وكأنك تمتلك مساعدًا شخصيًا يتولى كل المهام الشاقة نيابة عنك. لذا، انطلق وجربها. استمتع بالبرمجة!

## الأسئلة الشائعة

### هل يمكنني إدراج مستندات متعددة في حقول الدمج المختلفة؟
نعم، يمكنك ذلك. ما عليك سوى تحديد حقول الدمج المناسبة ومسارات المستندات المقابلة في`MailMerge.Execute` طريقة.

### هل من الممكن تنسيق المستند المدرج بشكل مختلف عن المستند الرئيسي؟
 بالتأكيد! يمكنك استخدام`ImportFormatMode` المعلمة في`NodeImporter` للتحكم في التنسيق.

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
