---
category: general
date: 2026-11-22
description: تعيين نص العنصر النائب في عنصر تحكم محتوى Word باستخدام C#. تعلّم كيفية
  إنشاء علامة مخصصة، وإدراج عنصر تحكم نص عادي، وإضافة العنصر النائب إلى العلامة باستخدام
  Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- create custom tag
- how to insert content control
- add placeholder to tag
- insert plain text control
language: ar
lastmod: 2026-11-22
og_description: تعيين نص العنصر النائب في عنصر تحكم المحتوى في Word باستخدام C#. يوضح
  لك هذا الدرس كيفية إنشاء علامة مخصصة، وإدراج عنصر تحكم نص عادي، وإضافة عنصر نائب
  إلى العلامة لتحسين تفاعل المستند.
og_image_alt: Screenshot showing a Word document with a content control placeholder
  text set using C#
og_title: تعيين نص العنصر النائب في عنصر تحكم محتوى Word – دليل C#
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Set placeholder text in a Word content control with C#. Learn how to
    create a custom tag, insert a plain text control, and add placeholder to tag using
    Aspose.Words.
  headline: Set placeholder text in a Word content control with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: تعيين نص العنصر النائب في عنصر تحكم محتوى Word باستخدام C#
url: /ar/java/using-document-elements/set-placeholder-text-in-a-word-content-control-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تعيين نص العنصر النائب في عنصر تحكم محتوى Word باستخدام C#

إذا كنت بحاجة إلى **تعيين نص العنصر النائب** في مستند Word برمجيًا، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك. باستخدام Aspose.Words for .NET يمكنك إنشاء علامة مخصصة، وإدراج عنصر تحكم نص عادي، وإضافة عنصر نائب إلى العلامة بحيث يكون المستند جاهزًا لإدخال المستخدم.

في هذا البرنامج التعليمي ستتعلم كيفية **إنشاء علامة مخصصة**، **كيفية إدراج عنصر تحكم محتوى**، و**إضافة عنصر نائب إلى العلامة** مع الحفاظ على شفرة مختصرة وجاهزة للإنتاج. لا توجد أدوات خارجية مطلوبة—فقط مشروع .NET ومكتبة Aspose.Words.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من أن لديك:

* .NET 6.0 SDK أو أحدث مثبتًا  
* رخصة صالحة لـ Aspose.Words for .NET (أو مفتاح تقييم مجاني)  
* إلمام أساسي بـ C# و Visual Studio (أو أي بيئة تطوير تفضلها)  

الأقسام التالية تفترض أنك أنشأت مشروع وحدة تحكم باسم `WordPlaceholderDemo`.

## الخطوة 1: تثبيت Aspose.Words

أضف حزمة NuGet إلى مشروعك:

```bash
dotnet add package Aspose.Words
```

> **نصيحة احترافية:** استخدم علم `--version` لتثبيت الحزمة على أحدث إصدار ثابت (مثال: `Aspose.Words.NET 24.9`).

## الخطوة 2: تحميل المستند المصدر وإنشاء `DocumentBuilder`

أول شيء تقوم به هو تحميل ملف `.docx` موجود (أو إنشاء مستند فارغ جديد) وإنشاء كائن `DocumentBuilder`. يمنحك الـ builder واجهة برمجة تطبيقات سلسة لإدراج العناصر والنص.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Load an existing Word file or create a new one
            Document doc = new Document("input.docx");   // <-- replace with your path
            DocumentBuilder builder = new DocumentBuilder(doc);
```

هذه الشفرة **تمهّد المشهد** لإدراج عنصر تحكم محتوى. يعمل `DocumentBuilder` مباشرة على كائن `doc`، لذا أي تغييرات تقوم بها تُعكس تلقائيًا.

## الخطوة 3: إنشاء علامة مخصصة (StructuredDocumentTag)

*العلامة المخصصة* في Word تُسمى **StructuredDocumentTag (SDT)**. يمكنك التفكير فيها كعنصر تحكم محتوى يحمل معرفًا فريدًا. إنشاء واحدة هو جوهر خطوة **إنشاء علامة مخصصة**.

```csharp
            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag identifier
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
```

طريقة `InsertStructuredDocumentTag` تأخذ وسيطين:

1. نوع العنصر (`PlainText` في هذه الحالة).  
2. سلسلة تُعرّف العلامة بشكل فريد (`"MyTag"`).  

باستخدام **علامة مخصصة**، يمكنك لاحقًا تحديد أو تعديل العنصر برمجيًا.

## الخطوة 4: تعيين عنوان لتحسين إمكانية الوصول

العنوان يحسن إمكانية الوصول ويجعل العنصر أسهل في العثور عليه في واجهة Word.

```csharp
            // Set a descriptive title (used by screen readers)
            sdt.Title = "CustomerName";
```

خاصية `Title` اختيارية، لكن إضافتها تُعد ممارسة جيدة عندما **تضيف عنصر نائب إلى العلامة** لتجربة مستخدم أفضل.

## الخطوة 5: إضافة نص العنصر النائب إلى العلامة

الآن يأتي الهدف الرئيسي: **تعيين نص العنصر النائب**. يظهر هذا النص عندما يكون العنصر فارغًا، موجهًا المستخدم إلى ما يجب كتابته.

```csharp
            // Provide placeholder text that shows when the tag is empty
            sdt.PlaceholderText = "Enter name…";
```

خاصية `PlaceholderText` هي بالضبط ما تحتاجه **لإضافة عنصر نائب إلى العلامة**. إنها تعمل كالتلميح الرمادي الذي تراه في حقول النماذج الحديثة.

## الخطوة 6: حفظ المستند المعدل

بعد تكوين العنصر، احفظ المستند مرة أخرى على القرص.

```csharp
            // Save the document with the new content control
            doc.Save("output.docx");   // <-- replace with your desired path
        }
    }
}
```

عند فتح `output.docx` في Microsoft Word، سترى عنصر تحكم نص عادي مُسمّى “CustomerName” مع العنصر النائب “Enter name…”. النقر داخل العنصر يزيل العنصر النائب، مما يسمح للمستخدم بالكتابة.

### النتيجة المتوقعة

* ملف Word (`output.docx`) يحتوي على عنصر تحكم نص عادي واحد.  
* العنصر يعرض العنصر النائب “Enter name…” حتى يكتب المستخدم شيئًا.  
* معرف العلامة للعنصر هو `MyTag`، ويمكنك الاستعلام عنه لاحقًا باستخدام `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.

## الخطوة 7: كيفية إدراج عنصر تحكم محتوى في مكان آخر (متقدم)

إذا كنت بحاجة إلى **كيفية إدراج عنصر تحكم محتوى** في موقع محدد—مثلاً بعد فقرة معينة—استخدم طريقة `MoveTo` قبل إدراج العلامة:

```csharp
            // Move the cursor to the end of the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            // Insert another plain‑text control with a different tag
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";
```

هذا المقتطف يوضح **إدراج عنصر تحكم نص عادي** عدة مرات داخل نفس المستند.

## الأخطاء الشائعة وكيفية تجنّبها

| المشكلة | سبب حدوثها | الحل |
|-------|----------------|-----|
| العنصر النائب غير مرئي | العنصر يحتوي بالفعل على نص (حتى مساحة) | تأكد من أن `sdt.Text` فارغ قبل تعيين `PlaceholderText`. |
| تصادم معرف العلامة | إعادة استخدام نفس اسم العلامة (`MyTag`) في نفس المستند | استخدم معرفات فريدة لكل `StructuredDocumentTag`. |
| استثناء الترخيص | تشغيل بدون رخصة صالحة لـ Aspose.Words | تطبيق ملف الترخيص (`license.SetLicense("Aspose.Words.lic")`) في بداية `Main`. |
| المستند غير محفوظ | نسيان استدعاء `doc.Save` أو استخدام مسار للقراءة فقط | تحقق من أن مسار الإخراج قابل للكتابة واستدعِ `doc.Save`. |

## مثال كامل يعمل

فيما يلي البرنامج الكامل الذي يمكنك نسخه ولصقه في `Program.cs`. يتضمن جميع الخطوات—**إنشاء علامة مخصصة**، **كيفية إدراج عنصر تحكم محتوى**، **إضافة عنصر نائب إلى العلامة**، و**إدراج عنصر تحكم نص عادي**—في تدفق موحد.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Optional: apply your Aspose.Words license here
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // Load the source document (or create a new one)
            Document doc = new Document("input.docx");
            DocumentBuilder builder = new DocumentBuilder(doc);

            // --------- Create custom tag ----------
            StructuredDocumentTag nameTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
            nameTag.Title = "CustomerName";
            nameTag.PlaceholderText = "Enter name…";

            // Insert a second control after the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";

            // Save the result
            doc.Save("output.docx");
            Console.WriteLine("Document saved with placeholder text set.");
        }
    }
}
```

شغّل البرنامج باستخدام `dotnet run`. بعد التنفيذ، افتح `output.docx` للتحقق من أن كلا العنصرين يعرضان العناصر النائبة الخاصة بهما.

## الخطوات التالية

* **تخصيص المظهر** – استخدم `sdt.Font` لتغيير حجم الخط أو لونه أو نمطه داخل العنصر.  
* **ربط ببيانات XML** – استكشف `sdt.XmlMapping` إذا كنت بحاجة إلى ربط العنصر ببيانات XML.

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [إنشاء مستند Word برمجيًا – إضافة عنصر تحكم محتوى وعنصر نائب](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [تعيين نص العنصر النائب في Aspose.Words – دليل C# كامل](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [إنشاء مستند Word جديد وإدراج عنصر تحكم محتوى في C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}