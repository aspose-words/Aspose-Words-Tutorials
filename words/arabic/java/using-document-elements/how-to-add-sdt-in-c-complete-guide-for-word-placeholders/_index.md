---
category: general
date: 2026-08-14
description: كيفية إضافة SDT بسرعة باستخدام Aspose.Words. تعلّم إنشاء عنصر نائب للكلمة
  وإدراج عنصر تحكم نص عادي في ملف .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add sdt
- create word placeholder
- insert plain text control
- Aspose.Words SDT
- C# Word automation
language: ar
lastmod: 2026-08-14
og_description: كيفية إضافة SDT في C# باستخدام Aspose.Words. اتبع هذا الدرس لإنشاء
  عنصر نائب للكلمة وإدراج عنصر تحكم نص عادي للمستندات الديناميكية.
og_image_alt: Screenshot of a Word document showing a plain‑text Structured Document
  Tag placeholder
og_title: كيفية إضافة SDT في C# – دليل خطوة بخطوة للعنصر النائب في Word
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add SDT quickly with Aspose.Words. Learn to create word placeholder
    and insert plain text control in a .docx file.
  headline: How to add SDT in C# – complete guide for Word placeholders
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- SDT
- Document Automation
title: كيفية إضافة SDT في C# – دليل كامل للمعلمات النائبة في Word
url: /ar/java/using-document-elements/how-to-add-sdt-in-c-complete-guide-for-word-placeholders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إضافة SDT في C# – دليل كامل لعلامات العنصر النائب في Word

إذا كنت بحاجة إلى **how to add sdt** في ملف Word، يوضح لك هذا الدليل الخطوات الدقيقة باستخدام Aspose.Words for .NET. في نهاية الدليل ستتمكن من **create word placeholder** العلامات التي تسمح للمستخدمين النهائيين بالكتابة مباشرةً في المستند، وستفهم كيفية **insert plain text control** بشكل موثوق.

العمل مع Structured Document Tags (SDTs) يزيل الحاجة إلى حقول النماذج اليدوية ويمنحك طريقة نظيفة برمجية لإنشاء عقود، تقارير، أو رسائل ديناميكية. المثال أدناه يغطي كل شيء من إعداد المشروع إلى حفظ ملف .docx النهائي، بحيث يمكنك نسخ‑لصق الشيفرة في حلّك الخاص دون فقدان أي تبعية.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.6+)
- Visual Studio 2022 أو أي بيئة تطوير C# تفضلها
- رخصة Aspose.Words for .NET (رخصة مؤقتة مجانية تعمل للاختبار)
- إلمام أساسي بصياغة C# ومفهوم SDTs

> **نصيحة احترافية:** إذا كنت تخطط لتوزيع المستندات المُنشأة، قم بتضمين ملف الترخيص لتجنب علامة التقييم.

## الخطوة 1: إعداد المشروع واستيراد Aspose.Words

Create a new console application and add the Aspose.Words NuGet package:

```bash
dotnet new console -n SdtDemo
cd SdtDemo
dotnet add package Aspose.Words
```

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
```

These `using` directives give you access to the `Document`, `DocumentBuilder`, and `StructuredDocumentTag` classes that are required for **insert plain text control** operations.

## الخطوة 2: تهيئة المستند والباني

The first code block creates an empty Word document and a `DocumentBuilder` that lets you write content into it.

```csharp
// Step 2: Create a new document and a builder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` works like a cursor; every subsequent call adds content at the current position. Initializing the document is the foundation for every **how to add sdt** scenario because the SDT must belong to a live `Document` instance.

## الخطوة 3: إدراج Structured Document Tag (SDT) نصي بسيط

Now we **insert plain text control** that acts as a placeholder where a user can type a name, a date, or any custom value.

```csharp
// Step 3: Insert a plain‑text Structured Document Tag (SDT)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
        StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);
```

- `StructuredDocumentTagType.PlainText` يخبر Aspose.Words بإنشاء حقل نصي بسيط.
- `SdtAppearanceTags.Default` يمنح العلامة النمط البصري القياسي في Word (مربع مظلل عند فتح المستند في Word).

## الخطوة 4: تكوين الـ SDT بعنوان ونص عنصر نائب

A well‑named SDT makes the document self‑explanatory for end users. Here we **create word placeholder** metadata and set the hint that appears inside the field.

```csharp
// Step 4: Give the SDT a meaningful title and placeholder text
plainTextTag.Title = "CustomerName";
plainTextTag.PlaceholderName = "Enter name here";
```

- `Title` هو المعرف الداخلي الذي يمكنك استخدامه لاحقًا عند استخراج أو تحديث القيمة برمجيًا.
- `PlaceholderName` هو التلميح الرمادي الظاهر في Word، يُخبر المستخدم بما يجب كتابته.

## الخطوة 5: إضافة محتوى محيط

A document rarely consists of a single SDT. You typically need regular paragraphs before and after the placeholder. Use the builder’s `WriteLine` method to add static text.

```csharp
// Step 5: Add regular content before and after the SDT
builder.Writeln("Dear ");
builder.InsertNode(plainTextTag);   // Re‑insert the tag at the current cursor position
builder.Writeln(",");
builder.Writeln("After the SDT");
```

The call to `InsertNode` places the previously created SDT exactly where you need it, preserving the surrounding flow of text.

## الخطوة 6: حفظ المستند كملف .docx

Finally, persist the document to disk. The path can be absolute or relative to the project folder.

```csharp
// Step 6: Save the document to a file
string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Opening `SDT.docx` in Microsoft Word shows a grey placeholder that reads **Enter name here**. Users can click the field, type a value, and the document will retain that value when saved again.

## مثال كامل قابل للتنفيذ

Putting all the pieces together gives you a self‑contained program you can run instantly:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a plain‑text SDT
        StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
            StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);

        // Configure the SDT
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // Add surrounding content
        builder.Writeln("Dear ");
        builder.InsertNode(plainTextTag);
        builder.Writeln(",");
        builder.Writeln("After the SDT");

        // Save the file
        string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**الناتج المتوقع** عند تشغيل البرنامج:

```
Document saved to C:\YourProject\bin\Debug\net6.0\SDT.docx
```

Opening the generated `SDT.docx` shows:

```
Dear [Enter name here],
After the SDT
```

The bracketed text is the **insert plain text control** placeholder that users can replace.

## الاختلافات الشائعة وحالات الحافة

| الحالة | كيفية تعديل الشيفرة |
|-----------|-----------------------|
| **عناصر نائبة متعددة** | استدعِ `InsertStructuredDocumentTag` بشكل متكرر ومنح كل علامة `Title` فريدة. |
| **SDT نص غني** | استخدم `StructuredDocumentTagType.RichText` بدلاً من `PlainText`. |
| **قفل العنصر النائب** | اضبط `plainTextTag.LockContentControl = true;` لمنع المستخدمين من حذف الحقل. |
| **ملء مسبق بقيمة** | عيّن `plainTextTag.Text = "John Doe";` قبل الحفظ. |
| **مظهر شرطي** | استخدم `plainTextTag.SdtType = StructuredDocumentTagType.CheckBox;` لإنشاء عنصر تحكم صندوق اختيار. |

## نصائح استكشاف الأخطاء وإصلاحها

- **Placeholder not visible** – تأكد من فتح الملف في Microsoft Word (أو عارض متوافق). بعض المحررات الخفيفة تخفي الـ SDTs.
- **License warning** – إذا رأيت علامة مائية للتقييم، تحقق من أن ملف الترخيص تم تحميله بشكل صحيح (`License license = new License(); license.SetLicense("Aspose.Words.lic");`).
- **Incorrect cursor position** – بعد إدراج SDT، يبقى مؤشر الباني *بعد* العلامة. إذا كنت بحاجة لإضافة نص *داخل* العلامة، استخدم `builder.MoveTo(plainTextTag);` قبل الكتابة.

## الخلاصة

أنت الآن تعرف **how to add sdt** إلى مستند Word باستخدام Aspose.Words for .NET، وكيفية **create word placeholder** العلامات، وكيفية **insert plain text control** التي يمكن للمستخدمين تعديلها مباشرةً في Word. يوضح المثال الكامل التهيئة، وإدراج العلامة، والتكوين، والمحتوى المحيط، والحفظ—كل ذلك في برنامج واحد قابل للتنفيذ.

بعد ذلك، استكشف المواضيع ذات الصلة مثل **insert rich text control**، **populate SDTs from a database**، أو **convert the final document to PDF**. جميع هذه تبني على الأساسيات نفسها التي تم تغطيتها هنا، بحيث يمكنك توسيع خط أنابيب الأتمتة بثقة.

برمجة سعيدة، ولا تتردد في تجربة أنواع SDT المختلفة لتناسب احتياجات أتمتة المستندات الخاصة بك!

## ماذا يجب أن تتعلم بعد ذلك؟

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [كيفية إنشاء حقول نموذج وإضافة محتوى باستخدام DocumentBuilder في Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [كيفية إنشاء نطاقات قابلة للتحرير في مستندات للقراءة فقط باستخدام Aspose.Words for Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)
- [إضافة إشارات مرجعية في Word باستخدام Aspose.Words for Java – إدراج، تحديث، حذف](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}