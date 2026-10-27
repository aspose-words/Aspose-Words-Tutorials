---
category: general
date: 2026-10-26
description: تعلم كيفية إدراج عنصر تحكم محتوى نص عادي باستخدام Aspose.Words في C#.
  دليل خطوة بخطوة يغطي StructuredDocumentTag والعناوين ومعرفات العلامات.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert plain text content control
- structured document tag
- Aspose.Words DocumentBuilder
- C# content control
- SDT appearance
language: ar
lastmod: 2026-10-26
og_description: إدراج عنصر تحكم محتوى نص عادي باستخدام Aspose.Words في C#. اتبع هذا
  الدليل لإضافة العناوين ومعرفات العلامات وتخصيص المظهر.
og_image_alt: Screenshot of a Word document showing an inserted plain text content
  control
og_title: إدراج عنصر تحكم محتوى نص عادي في Word باستخدام C# – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  headline: How to insert plain text content control in a Word document with C#
  type: TechArticle
- description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  name: How to insert plain text content control in a Word document with C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Markup;'
  - name: Insert the plain‑text content control (SDT)
    text: '```csharp // Insert a plain‑text Structured Document Tag (SDT) with the
      default appearance. StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
      SdtType.PlainText, // The control type – plain text. SdtAppearance.Default);
      // Visual style; Default shows a light gray shading. ```'
  - name: Set a title and a tag identifier
    text: '```csharp // Give the SDT a friendly title that appears in the Content
      Controls pane. sdt.Title = "MyTag";'
  - name: Variations you might need
    text: '| Scenario | Code change | |----------|-------------| | **No visual shading**
      (border‑less) | Use `SdtAppearance.Hidden` instead of `Default`. | | **Read‑only
      field** | After insertion, set `sdt.LockContentControl = true`. | | **Pre‑populate
      with data** | Set `sdt.Text = "John Doe";` after creating '
  - name: What’s next?
    text: '- Explore other SDT types such as `RichText` or `ComboBox` for dropdowns.
      - Combine multiple content controls inside tables or repeat them using `RepeatingSection`.
      - Use `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` to read or modify
      control values programmatically.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: كيفية إدراج عنصر تحكم نص عادي في مستند Word باستخدام C#
url: /ar/java/document-manipulation/how-to-insert-plain-text-content-control-in-a-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إدراج عنصر تحكم محتوى نص عادي في مستند Word باستخدام C#

إذا كنت بحاجة إلى **إدراج عنصر تحكم محتوى نص عادي** في ملف Word، يوضح لك هذا الدرس بالضبط كيفية القيام بذلك باستخدام Aspose.Words for .NET. سواءً كنت تبني خدمة توليد مستندات أو تقوم بأتمتة إنشاء النماذج، فإن الخطوات أدناه تتيح لك إضافة منطقة قابلة لإعادة الاستخدام والتحرير يمكن للمستخدمين النهائيين ملؤها.

ستتعلم كيفية إنشاء `Document`، واستخدام `DocumentBuilder` لوضع Structured Document Tag (SDT) نص عادي، وتعيين عنوان صديق، وتحديد معرف علامة فريد. يشرح الدرس أيضًا الاختلافات الشائعة—مثل تغيير المظهر أو تضمين عناصر تحكم—حتى تتمكن من تكييف الحل مع أي مشروع.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.6+)
- ترخيص صالح لـ Aspose.Words for .NET (أو مفتاح تقييم مجاني)
- Visual Studio 2022 أو أي بيئة تطوير متوافقة مع C#
- إلمام أساسي بصياغة C#

> **نصيحة محترف:** إذا كنت تستخدم نسخة التقييم المجانية، تذكر أن المستند الناتج سيحتوي على علامة مائية. النسخة المرخصة تزيلها تلقائيًا.

## كيفية إدراج عنصر تحكم محتوى نص عادي باستخدام Aspose.Words

جوهر الحل هو عملية من ثلاث خطوات:

1. **إنشاء `Document` و `DocumentBuilder`.**  
2. **إدراج Structured Document Tag (SDT) نص عادي بالمظهر الافتراضي.**  
3. **تعيين عنوان ومعرف علامة للـ SDT.**  

يتم شرح كل خطوة أدناه، مع كود كامل قابل للتنفيذ.

### الخطوة 1: تهيئة المستند والباني

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document doc = new Document();

        // DocumentBuilder lets you insert content into the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` يمثل ملف Word بالكامل، بينما `DocumentBuilder` يوفر طرقًا مثل `InsertParagraph`، `InsertImage`، والأهم لهذا الدرس `InsertStructuredDocumentTag`. تهيئتهما أولًا يمنحك مساحة عمل يمكنك من خلالها وضع **عنصر تحكم محتوى نص عادي**.

### الخطوة 2: إدراج عنصر تحكم المحتوى النصي (SDT)

```csharp
        // Insert a plain‑text Structured Document Tag (SDT) with the default appearance.
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText,          // The control type – plain text.
            SdtAppearance.Default);    // Visual style; Default shows a light gray shading.
```

`SdtType.PlainText` يخبر Aspose.Words بإنشاء **عنصر تحكم محتوى نص عادي**، والذي يتصرف كصندوق نص بسيط يمكن للمستخدمين تحريره. `SdtAppearance.Default` يعرض العنصر بخلفية خفيفة، مما يجعل المنطقة القابلة للتحرير واضحة في المستند.

> **لماذا نستخدم `SdtAppearance.Default`؟**  
> المظهر الافتراضي هو الأكثر توافقًا عبر إصدارات Word المختلفة. إذا كنت تحتاج مظهرًا بدون حدود، يمكنك التحويل إلى `SdtAppearance.Hidden` لاحقًا.

### الخطوة 3: تعيين عنوان ومعرف علامة

```csharp
        // Give the SDT a friendly title that appears in the Content Controls pane.
        sdt.Title = "MyTag";

        // Assign a unique tag identifier; this is useful for programmatic access later.
        sdt.Tag = "TagId";

        // (Optional) Add placeholder text inside the control.
        sdt.PlaceholderName = "Enter your text here";

        // Save the document to verify the result.
        doc.Save("output.docx");
    }
}
```

- **العنوان** (`sdt.Title`) يظهر في لوحة *Content Controls* في Word، مما يساعد المستخدمين على فهم هدف الحقل.  
- **العلامة** (`sdt.Tag`) هي معرف موجه للمطور يمكنك الاستعلام عنه لاحقًا عبر `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.  
- **PlaceholderName** يوفر نصًا إرشاديًا رماديًا، محسنًا تجربة المستخدم.

الكود الكامل أعلاه يشكل برنامجًا مستقلًا يمكنك تجميعه وتشغيله. بعد التنفيذ، سيحتوي `output.docx` على عنصر تحكم محتوى نص عادي واحد بعنوان *MyTag* وعلامة *TagId*.

![Diagram showing insert plain text content control in a Word document](image.png){alt="إدراج عنصر تحكم محتوى نص عادي"}

## فهم StructuredDocumentTag (SDT) وخصائصه

**Structured Document Tag** (SDT) هو نموذج الكائن الأساسي لعناصر تحكم محتوى Word. أهم الخصائص لإدراج عنصر تحكم نص عادي هي:

| الخاصية | الغرض | القيم النموذجية |
|----------|---------|----------------|
| `SdtType` | يحدد نوع العنصر (نص عادي، نص غني، صورة، إلخ) | `PlainText`, `RichText`, `ComboBox`, `DatePicker` |
| `SdtAppearance` | النمط البصري للعنصر | `Default`, `Hidden`, `BoundingBox`, `Tags` |
| `Title` | اسم قابل للقراءة يظهر في لوحة *Content Controls* | أي سلسلة قصيرة |
| `Tag` | معرف قابل للقراءة آليًا يستخدم في الكود | سلسلة أبجدية رقمية |
| `PlaceholderName` | النص المعروض عندما يكون العنصر فارغًا | نص إرشادي مخصص |

عند تعيين `SdtType.PlainText`، يقوم Word بتقييد المحتوى إلى أحرف عادية، مما يمنع التنسيق الغني. هذا يجعل العنصر مثاليًا لحقول نماذج بسيطة مثل *الاسم*، *البريد الإلكتروني*، أو *رقم الهاتف*.

### الاختلافات التي قد تحتاجها

| السيناريو | تعديل الكود |
|----------|-------------|
| **بدون تظليل بصري** (بدون حدود) | استخدم `SdtAppearance.Hidden` بدلاً من `Default`. |
| **حقل للقراءة فقط** | بعد الإدراج، عيّن `sdt.LockContentControl = true`. |
| **ملء مسبق بالبيانات** | عيّن `sdt.Text = "John Doe";` بعد إنشاء العلامة. |
| **عناصر تحكم متعددة داخل جدول** | أدخل الـ SDT داخل خلية جدول باستخدام `builder.InsertCell();` قبل استدعاء `InsertStructuredDocumentTag`. |

## المشكلات الشائعة وكيفية تجنبها

1. **نسيان تعيين العنوان** – سيظل Word ينشئ العنصر، لكن المستخدمين لن يروا وصفًا معنويًا في لوحة *Content Controls*. احرص دائمًا على تعيين `sdt.Title`.  
2. **استخدام `SdtType` غير الصحيح** – إذا كنت تحتاج نصًا عاديًا واخترت عن طريق الخطأ `RichText`، سيسمح العنصر بالتنسيق، مما قد يعيق المعالجة اللاحقة. تحقق من قيمة الـ enum.  
3. **الحفظ في مجلد للقراءة فقط** – استدعاء `doc.Save` سيطرح استثناء `UnauthorizedAccessException`. تأكد من أن الدليل الهدف قابل للكتابة أو استخدم `Path.GetTempPath()` للاختبار.  
4. **عدم تطبيق الترخيص** – بدون ترخيص صالح، يحتوي المستند الناتج على علامة مائية للتقييم. طبّق الترخيص مبكرًا في برنامجك:  

```csharp
License lic = new License();
lic.SetLicense("Aspose.Words.lic");
```

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج بالكامل، جاهز للنسخ واللصق في مشروع وحدة تحكم جديد.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace InsertPlainTextContentControl
{
    class Program
    {
        static void Main()
        {
            // Apply license (optional for evaluation)
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1️⃣ Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a plain‑text Structured Document Tag (SDT) with default appearance
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,          // Plain text control
                SdtAppearance.Default);    // Light gray shading

            // 3️⃣ Assign a title and a tag identifier to the SDT
            sdt.Title = "MyTag";          // Human‑readable title
            sdt.Tag = "TagId";            // Unique machine identifier
            sdt.PlaceholderName = "Enter your text here";

            // (Optional) Add some introductory text before the control
            builder.MoveToDocumentStart();
            builder.Writeln("Please fill in the following field:");

            // 4️⃣ Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**الناتج المتوقع:** عند فتح `output.docx` في Microsoft Word ستظهر سطر نص *“Please fill in the following field:”* متبوعًا بمنطقة ذات حدود رمادية فاتحة معنونة *MyTag*. يظهر النص النائب *Enter your text here* باللون الرمادي الفاتح حتى يبدأ المستخدم بالكتابة.

## الخلاصة

أنت الآن تعرف كيف **تدرج عنصر تحكم محتوى نص عادي** في مستند Word باستخدام Aspose.Words for .NET. غطى الدرس تهيئة `Document`، وإدراج `StructuredDocumentTag` من النوع `PlainText`، وتخصيص العنوان والعلامة والنص النائب. من خلال فهم خيارات `SdtAppearance` والمشكلات الشائعة، يمكنك بناء نماذج، قوالب، وتقارير آلية تعتمد على عناصر تحكم قابلة للتحرير بثقة.

### ما التالي؟

- استكشف أنواع SDT أخرى مثل `RichText` أو `ComboBox` للقوائم المنسدلة.  
- اجمع عدة عناصر تحكم داخل جداول أو كرّرها باستخدام `RepeatingSection`.  
- استخدم `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` لقراءة أو تعديل قيم العناصر برمجيًا.

لا تتردد في تجربة الاختلافات المذكورة أعلاه، ودمج النمط في خطوط إنتاج توليد المستندات الأكبر لديك. Happy coding!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء عنصر تحكم محتوى في C# باستخدام Aspose.Words](/words/english/net/programming-with-sdt/how-to-create-content-control-in-c-with-aspose-words/)
- [إنشاء مستند Word جديد وإدراج عنصر تحكم محتوى في C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)
- [إضافة محتوى باستخدام Document Builder في Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}