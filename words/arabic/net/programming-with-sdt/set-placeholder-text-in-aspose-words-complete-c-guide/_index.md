---
category: general
date: 2026-07-19
description: تعيين نص العنصر النائب في StructuredDocumentTag باستخدام Aspose.Words.
  تعلم كيفية إضافة التحكم، الانتقال إلى التحكم وتعيين سمة العلامة في C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- move to control
- how to add control
- how to create sdt
- set tag attribute
language: ar
lastmod: 2026-07-19
og_description: قم بتعيين نص العنصر النائب في StructuredDocumentTag باستخدام Aspose.Words.
  اتبع هذا الدليل خطوة بخطوة لإضافة التحكم، الانتقال إلى التحكم، وتعيين سمة العلامة.
og_image_alt: Screenshot showing a Word document with placeholder text inside a content
  control created by Aspose.Words
og_title: تعيين نص العنصر النائب في Aspose.Words – دليل سريع بلغة C#
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Set placeholder text in a StructuredDocumentTag with Aspose.Words.
    Learn how to add control, move to control and set tag attribute in C#.
  headline: Set Placeholder Text in Aspose.Words – Complete C# Guide
  type: TechArticle
- description: Set placeholder text in a StructuredDocumentTag with Aspose.Words.
    Learn how to add control, move to control and set tag attribute in C#.
  name: Set Placeholder Text in Aspose.Words – Complete C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6+ (or .NET Framework 4.7.2) – the code works on any recent runtime.
      - Aspose.Words for .NET (NuGet package `Aspose.Words` version 23.12 or later).
      - A basic understanding of C# and Visual Studio (or your favorite IDE).'
  - name: Expected Result
    text: 'Open `SDTExample.docx` in Microsoft Word:'
  - name: What if I need a **dropdown** instead of plain text?
    text: Replace `SdtType.PlainText` with `SdtType.DropDownList` and populate the
      `ListItems` collection. The rest of the workflow—`InsertNode`, `MoveTo`, `SetTagAttribute`—remains
      the same.
  - name: Can I **set the tag attribute** after insertion?
    text: 'Absolutely. The `Tag` property can be modified at any time:'
  - name: How do I **find a control later** in a large document?
    text: Use the `Document.GetChildNodes(NodeType.StructuredDocumentTag, true)` method
      and filter by `Tag` or `Title`. This is handy when you need to replace placeholder
      text in bulk.
  - name: What if I want the placeholder to appear in **all languages**?
    text: Aspose.Words supports localized placeholder text via the `PlaceholderName`
      property. Set it to a resource string that varies per culture.
  type: HowTo
tags:
- Aspose.Words
- C#
- ContentControl
title: تعيين نص العنصر النائب في Aspose.Words – دليل C# الكامل
url: /ar/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تعيين نص العنصر النائب في Aspose.Words – دليل كامل بلغة C#

هل تساءلت يوماً كيف **تعيّن نصًا نائبًا** داخل عنصر تحكم محتوى في Word باستخدام Aspose.Words؟ لست وحدك. سواءً كنت تبني محرك توليد مستندات أو تحتاج فقط إلى قالب قابل لإعادة الاستخدام، فإن معرفة كيفية إضافة عنصر تحكم، الانتقال إليه وتعيين سمة العلامة (tag) أمر أساسي.

في هذا الدرس سنستعرض مثالًا واقعيًا يوضح بالضبط كيفية إنشاء SDT (StructuredDocumentTag)، إعطائه علامة، تعيين نص نائب، وكتابة محتوى افتراضي—كل ذلك باستخدام C# بسيط. في النهاية ستحصل على قطعة شفرة جاهزة للتنفيذ يمكنك إدراجها في أي مشروع .NET.

## ما ستتعلمه

- كيفية **إنشاء SDT** (StructuredDocumentTag) برمجيًا.
- الطريقة الصحيحة **لتعيين نص نائب** بحيث يرى المستخدمون تلميحات مفيدة.
- استخدام **الانتقال إلى عنصر التحكم** لتحديد موضع المؤشر داخل العنصر المضاف حديثًا.
- تعيين سمة **العلامة (tag)** للتعرف عليه لاحقًا.
- حفظ المستند والتحقق من النتيجة.

### المتطلبات المسبقة

- .NET 6+ (أو .NET Framework 4.7.2) – الشيفرة تعمل على أي بيئة تشغيل حديثة.
- Aspose.Words for .NET (حزمة NuGet `Aspose.Words` الإصدار 23.12 أو أحدث).
- فهم أساسي للغة C# وVisual Studio (أو أي بيئة تطوير مفضلة).

لا توجد مكتبات خارجية أخرى مطلوبة.

## الخطوة 1: تهيئة المستند وDocumentBuilder

أولاً—أنشئ كائن `Document` فارغ و`DocumentBuilder`. الـ builder هو فرشاة الرسم؛ المستند هو القماش.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Create a brand‑new blank document.
Document document = new Document();

// DocumentBuilder lets us insert text, tables, and controls.
DocumentBuilder docBuilder = new DocumentBuilder(document);
```

> **لماذا هذا مهم:** بدءًا بـ `Document` نظيف يضمن أن النص النائب الذي سنضيفه لاحقًا لن يتصادم مع محتوى موجود مسبقًا.

## الخطوة 2: إنشاء StructuredDocumentTag (SDT)

الآن سنوضح **كيفية إنشاء SDT** – عنصر تحكم محتوى يمكنه احتواء نص عادي، تواريخ، قوائم منسدلة، إلخ. في حالتنا نحتاج إلى عنصر نص عادي.

```csharp
// Create a plain‑text StructuredDocumentTag (content control).
StructuredDocumentTag plainTextSdt = new StructuredDocumentTag(
    document, SdtType.PlainText, true);

// Give the control a friendly name and a tag for later lookup.
plainTextSdt.Title = "CustomerName";
plainTextSdt.Tag   = "CustomerNameTag";

// Here’s the crucial part: set the placeholder text that the user sees.
plainTextSdt.PlaceholderText = "Enter name here";
```

> **نصيحة محترف:** خاصية `PlaceholderText` هي ما يراه المستخدم قبل كتابة أي شيء. وهي مختلفة عن النص الافتراضي الذي قد تكتبه لاحقًا.

## الخطوة 3: إدراج العنصر في المستند

بعد تجهيز الـ SDT، نحتاج إلى **إضافة العنصر** إلى المستند. طريقة `InsertNode` تقوم بذلك بالضبط.

```csharp
// Insert the content control at the current cursor position.
docBuilder.InsertNode(plainTextSdt);
```

> **ماذا يحدث خلف الكواليس؟** تقوم `InsertNode` بوضع الـ SDT كطفل للفقرة الحالية، مع الحفاظ على أي تنسيق محيط.

## الخطوة 4: الانتقال إلى العنصر وكتابة محتوى افتراضي (اختياري)

إذا أردت ملء العنصر مسبقًا بقيمة (مثلاً اسم عميل افتراضي)، أولاً **انتقل إلى العنصر** ثم اكتب.

```csharp
// Optionally clear the placeholder and write a default name.
plainTextSdt.RemoveAllChildren();          // Remove the placeholder node.
docBuilder.MoveTo(plainTextSdt);           // Move cursor inside the SDT.
docBuilder.Write("John Doe");              // Write default text.
```

> **لماذا نزيل النص النائب:** النص النائب هو إشارة بصرية، وليس محتوى فعليًا في المستند. إزالته قبل الكتابة تضمن أن المستند النهائي يحتوي فقط على النص الحقيقي.

## الخطوة 5: حفظ المستند

أخيرًا، احفظ الملف على القرص. يمكنك أيضًا إرساله كستريم في استجابة تطبيق ويب—فقط استبدل استدعاء `Save`.

```csharp
// Save the Word document to the desired location.
document.Save("C:/Temp/SDTExample.docx");
```

### النتيجة المتوقعة

افتح `SDTExample.docx` في Microsoft Word:

- سترى عنصر تحكم نص عادي بعنوان **CustomerName**.
- يعرض العنصر النص النائب “Enter name here” كنص باهت (إذا لم تقم بكتابة محتوى افتراضي).
- إذا تركت سطر `Write("John Doe")`، سيظهر “John Doe” داخل العنصر، وسيختفي النص النائب.

## مثال كامل يعمل

فيما يلي البرنامج الكامل جاهز للنسخ واللصق. يتضمن جميع الخطوات السابقة، بالإضافة إلى بعض الفحوصات الوقائية.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise document and builder.
        Document document = new Document();
        DocumentBuilder docBuilder = new DocumentBuilder(document);

        // 2️⃣ Create a plain‑text SDT (content control).
        StructuredDocumentTag plainTextSdt = new StructuredDocumentTag(
            document, SdtType.PlainText, true);
        plainTextSdt.Title = "CustomerName";
        plainTextSdt.Tag   = "CustomerNameTag";
        plainTextSdt.PlaceholderText = "Enter name here";

        // 3️⃣ Insert the control into the document.
        docBuilder.InsertNode(plainTextSdt);

        // 4️⃣ (Optional) Move to the control and set default text.
        plainTextSdt.RemoveAllChildren();   // Clear placeholder.
        docBuilder.MoveTo(plainTextSdt);    // Move cursor inside.
        docBuilder.Write("John Doe");       // Write default value.

        // 5️⃣ Save the file.
        string outputPath = @"C:\Temp\SDTExample.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

شغّل البرنامج، افتح الملف المُولد، وسترى كل شيء يعمل كما هو موضح.

## أسئلة شائعة وحالات خاصة

### ماذا لو أردت **قائمة منسدلة** بدلاً من نص عادي؟

استبدل `SdtType.PlainText` بـ `SdtType.DropDownList` واملأ مجموعة `ListItems`. باقي سير العمل—`InsertNode`، `MoveTo`، `SetTagAttribute`—يبقى كما هو.

### هل يمكنني **تعيين سمة العلامة** بعد الإدراج؟

بالطبع. يمكن تعديل خاصية `Tag` في أي وقت:

```csharp
plainTextSdt.Tag = "NewTagValue";
```

تذكّر فقط حفظ المستند مرة أخرى لتصبح التغييرات سارية.

### كيف أجد **عنصر تحكم** لاحقًا في مستند كبير؟

استخدم الطريقة `Document.GetChildNodes(NodeType.StructuredDocumentTag, true)` وقم بالترشيح حسب `Tag` أو `Title`. هذا مفيد عندما تحتاج إلى استبدال النص النائب على نطاق واسع.

```csharp
foreach (StructuredDocumentTag sdt in document.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    if (sdt.Tag == "CustomerNameTag")
    {
        // Do something with this control.
    }
}
```

### ماذا لو أردت أن يظهر النص النائب **بجميع اللغات**؟

يدعم Aspose.Words النص النائب المحلي عبر خاصية `PlaceholderName`. عيّنها إلى سلسلة موارد تختلف حسب الثقافة.

## نصائح وحيل (نصائح محترف)

- **أعد استخدام نفس الـ SDT** عبر مستندات متعددة عن طريق استنساخه (`plainTextSdt.Clone(true)`)، ثم إدراج النسخة حيثما تحتاج.
- **تجنّب العلامات المكررة**؛ فهي تجعل البحث لاحقًا غير واضح. احرص على أن تكون العلامات فريدة لكل مستند.
- **نصيحة أداء:** إذا كنت تولد آلاف المستندات، أعد استخدام كائن `Document` واحد كقالب واستبدل النص النائب فقط. هذا يقلل من تكلفة إنشاء الكائنات.

## الخلاصة

غطّينا كل ما تحتاجه لت **تعيين نص نائب** في StructuredDocumentTag الخاص بـ Aspose.Words، من إنشاء العنصر إلى الانتقال إليه، كتابة محتوى افتراضي، وتعيين سمة العلامة. بهذه المعرفة يمكنك بناء قوالب Word ديناميكية توجه المستخدمين، تفرض قواعد إدخال البيانات، وتبقى سهلة الصيانة.

هل أنت مستعد للتحدي التالي؟ جرّب استبدال SDT النصي بـ **منتقي تاريخ** أو **صندوق مركب**، أو استكشف كيفية ربط SDT بمصادر بيانات XML لمزيد من أتمتة المستندات.

برمجة سعيدة، ولتكن مستنداتك دائمًا مُقَدمة بشكل مثالي!

## ماذا يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف طرق تنفيذ بديلة في مشاريعك.

- [تعيين نمط عنصر التحكم](/words/hindi/net/programming-with-sdt/set-content-control-style/)
- [تعيين لون عنصر التحكم](/words/hindi/net/programming-with-sdt/set-content-control-color/)
- [كيفية إنشاء حقول نموذج وإضافة محتوى باستخدام DocumentBuilder في Aspose.Words للـ Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}