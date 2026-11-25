---
category: general
date: 2026-11-25
description: تعلم كيفية إنشاء مستند Word، إضافة شكل مستطيل، تلخيص المستند باستخدام
  الذكاء الاصطناعي، ترجمة النص باستخدام الذكاء الاصطناعي، وحفظ المستند بصيغة DOCX
  باستخدام Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- summarize document with ai
- save document as docx
- translate text using ai
language: ar
lastmod: 2026-11-25
og_description: إنشاء مستند Word، إضافة شكل مستطيل، تلخيص المستند باستخدام الذكاء
  الاصطناعي، ترجمة النص باستخدام الذكاء الاصطناعي، وحفظ المستند كملف DOCX—كل ذلك في
  دليل C# واحد.
og_image_alt: Screenshot showing a generated Word document with a rectangle shape
  and AI‑generated summary
og_title: إنشاء مستند Word يحتوي على أشكال، ملخص بالذكاء الاصطناعي، وترجمة باستخدام
  C#
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a Word document, add rectangle shape, summarize
    document with AI, translate text using AI, and save document as DOCX using Aspose.Words.
  headline: How to create a Word document with shapes, AI summarization, and translation
    in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- AI integration
title: كيفية إنشاء مستند Word يحتوي على أشكال وتلخيص بالذكاء الاصطناعي وترجمة باستخدام
  C#
url: /ar/net/ai-powered-document-processing/how-to-create-a-word-document-with-shapes-ai-summarization-a/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مستند Word مع الأشكال، وتلخيص AI، والترجمة في C#

إذا كنت بحاجة إلى **إنشاء مستند Word** برمجيًا، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك. باستخدام Aspose.Words for .NET ستتعلم **إضافة شكل مستطيل**، واستدعاء خدمة AI لـ **تلخيص المستند باستخدام AI**، وترجمة فقرة باستخدام **translate text using AI**، وأخيرًا **حفظ المستند كـ DOCX**.

يعاني العديد من المطورين من صعوبة دمج أتمتة المستندات مع ميزات AI الحديثة. في نهاية هذا البرنامج التعليمي ستحصل على مشروع C# واحد مكتمل الذات ينتج ملف *.docx* مُنسق بالكامل، يحتوي على شكل بصري، ملخص تم إنشاؤه بواسطة AI، ومحتوى متعدد اللغات.

## المتطلبات المسبقة

- .NET 6.0 SDK أو أحدث مثبت  
- Visual Studio 2022 (أو أي بيئة تطوير C#)  
- ترخيص Aspose.Words for .NET (أو مفتاح تقييم مجاني)  
- اتصال بالإنترنت لاستدعاءات تلخيص AI والترجمة  

لا توجد حزم NuGet إضافية مطلوبة بخلاف `Aspose.Words` و `Aspose.Words.AI`.

## الخطوة 1: إعداد المشروع وإضافة الحزم المطلوبة

أنشئ مشروع وحدة تحكم جديد وأدرج مكتبات Aspose.Words.

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

> **نصيحة احترافية:** إذا كنت تخطط لاستخدام وضع التقييم، استدعِ `Aspose.Words.License.SetLicense("Aspose.Words.lic");` مبكرًا في `Main` لتجنب العلامات المائية.

## الخطوة 2: تهيئة المستند – جوهر **create word document**

السطر البرمجي القابل للتنفيذ الأول ينشئ كائن **Word document** جديد. هذا الكائن هو القماش لجميع العمليات اللاحقة.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // Create a new, empty Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

يسهل `DocumentBuilder` إدراج النصوص، الأشكال، والعناصر التحكمية دون الحاجة إلى التعامل يدويًا مع شجرات العقد منخفضة المستوى.

## الخطوة 3: **إضافة شكل مستطيل** إلى المستند

يمكن استخدام شكل مستطيل كعنصر نائب بصري، خلفية تسمية، أو رسم بسيط. أولاً ننشئ `GroupShape`، ثم ندرج `Rectangle` داخله.

```csharp
        // Step 3: Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

العرض 100 نقطة والارتفاع 50 نقطة. وبما أنه موجود داخل `GroupShape`، يمكنك لاحقًا إضافة المزيد من العناصر (مثل صناديق النص) دون القلق بشأن تصادم التخطيط.

## الخطوة 4: إدراج StructuredDocumentTag (SDT) نص عادي

كائنات StructuredDocumentTag مفيدة لعناصر التحكم بالمحتوى التي يمكن ربطها بمصادر البيانات لاحقًا.

```csharp
        // Step 4: Add a plain‑text StructuredDocumentTag (SDT) to the document
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);
```

العلم `true` يحدد العلامة كعنصر تحكم **متكرر**، وهو مفيد للقوالب.

## الخطوة 5: إضافة عنصر تحكم ActiveX CommandButton (واجهة مستخدم اختيارية)

إذا كان المستند المُولد سيُستخدم في بيئة تدعم ActiveX، يمكنك تضمين زر.

```csharp
        // Step 5: Insert an ActiveX CommandButton control (Forms2 OLE control)
        builder.InsertForms2OleControl(OleControlType.CommandButton);
```

هذه الخطوة اختيارية؛ يمكنك إزالتها إذا لم يتفاعل جمهورك المستهدف مع المستند في بيئة Windows.

## الخطوة 6: **تلخيص المستند باستخدام AI**

توفر Aspose.Words.AI غلافًا مريحًا حول خدمات نماذج اللغة الكبيرة. هنا نستدعي `DocumentSummarizer.Summarize` باستخدام خلفية OpenAI.

```csharp
        // Step 6: Summarize the document content using an AI service
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);
```

تحلل الطريقة شجرة العقد الحالية، تستخرج أكثر الجمل صلة، وتعيد فقرة مختصرة. هذه هي جوهر وظيفة **summarize document with AI**.

## الخطوة 7: **ترجمة النص باستخدام AI**

بعد ذلك نوضح كيفية ترجمة سلسلة نموذجية من الإنجليزية إلى الفرنسية. تستدعي طريقة `Translator.Translate` داخليًا نموذج Google AI.

```csharp
        // Step 7: Translate a sample paragraph to French using Google AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);
```

يمكنك استبدال `Language.French` بأي قيمة تعداد لغة مدعومة، مما يتيح إنشاء مستندات متعددة اللغات في الوقت الفعلي.

## الخطوة 8: **حفظ المستند كـ DOCX**

أخيرًا، احفظ المستند المعدل على القرص. طريقة `Save` تكتب تلقائيًا ملف *.docx* عندما تحدد امتداد `.docx`.

```csharp
        // Step 8: Save the modified document
        document.Save("Result.docx"); // **save document as docx**
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

الملف `Result.docx` الآن يحتوي على:

- شكل مستطيل داخل مجموعة أشكال  
- عنصر تحكم محتوى نص عادي (SDT)  
- زر ActiveX CommandButton (إذا احتفظت بالخطوة 5)  
- فقرة ملخص تم إنشاؤها بواسطة AI  
- ترجمة فرنسية لعبارة “Hello world”

يمكنك فتح الملف في Microsoft Word للتحقق من كل عنصر.

## الكود المصدر الكامل

فيما يلي البرنامج الكامل الجاهز للتنفيذ. انسخه إلى `Program.cs` وشغّل `dotnet run`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // 1. Create a new Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3. Add a plain‑text StructuredDocumentTag (SDT)
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);

        // 4. Insert an ActiveX CommandButton (optional)
        builder.InsertForms2OleControl(OleControlType.CommandButton);

        // 5. Summarize the document using AI
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);

        // 6. Translate a paragraph to French using AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);

        // 7. Save the document as DOCX
        document.Save("Result.docx");
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

### النتيجة المتوقعة

```
Document summary:
[AI‑generated concise summary of the document’s current content]

Translated paragraph (English → French):
Bonjour le monde

Document saved as Result.docx
```

عند فتح `Result.docx`، ستلاحظ شكل المستطيل بالقرب من الأعلى، عنصر الـ SDT النائب، الزر، فقرة الملخص، والترجمة الفرنسية المدخلة كنص عادي.

## الخلاصة

أنت الآن تعرف كيف **إنشاء مستند Word** من الصفر، **إضافة شكل مستطيل**، **تلخيص المستند باستخدام AI**، **ترجمة النص باستخدام AI**، و**حفظ المستند كـ DOCX**—كل ذلك ببضع أسطر مختصرة من C#. هذا النمط قابل للتوسع: يمكنك استبدال السلاسل الثابتة ببيانات ديناميكية، إضافة المزيد من الأشكال أو المخططات، وتغيير مزود AI عن طريق تعديل معلمات `SummarizerOptions` أو `Translator`.

### ما التالي؟

- استكشف تنويعات **add rectangle shape**: غيّر لون التعبئة، نمط الخط، أو أضف نصًا داخل الشكل.  
- استخدم **summarize document with AI** على مستندات أكبر لتوليد ملخصات تنفيذية تلقائيًا.  
- وسّع **translate text using AI** لمعالجة دفعات من الفقرات أو الجداول لتقارير متعددة اللغات.  
- دمج واجهات برمجة Aspose.Words للرسم البياني لإدراج تصورات بيانية جنبًا إلى جنب مع رؤى تم إنشاؤها بواسطة AI.  

لا تتردد في التجربة، ومشاركة نتائجك في التعليقات أو على GitHub. Happy coding!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك الخاصة.

- [Create a blank word document and add a rectangle shape](/words/english/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Add Text Watermark in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-watermark/add-text-watermark/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}