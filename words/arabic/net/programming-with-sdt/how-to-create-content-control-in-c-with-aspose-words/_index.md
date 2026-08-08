---
category: general
date: 2026-08-07
description: كيفية إنشاء عنصر تحكم المحتوى في C# باستخدام Aspose.Words – تعلم كيفية
  إضافة SDT، تعيين العنصر النائب، كتابة النص الافتراضي، وإدراج عنصر تحكم نص عادي.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create content control
- how to add sdt
- how to set placeholder
- how to write default text
- insert plain text control
language: ar
lastmod: 2026-08-07
og_description: كيفية إنشاء التحكم بالمحتوى في C# باستخدام Aspose.Words. يوضح هذا
  الدرس كيفية إضافة SDT، تعيين العنصر النائب، كتابة النص الافتراضي، وإدراج التحكم
  بالنص العادي.
og_image_alt: Screenshot of a Word document showing a plain‑text content control with
  placeholder text
og_title: كيفية إنشاء عنصر تحكم المحتوى في C# – دليل Aspose.Words الكامل
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to create content control in C# using Aspose.Words – learn how
    to add SDT, set placeholder, write default text, and insert plain text control.
  headline: How to create content control in C# with Aspose.Words
  type: TechArticle
- description: How to create content control in C# using Aspose.Words – learn how
    to add SDT, set placeholder, write default text, and insert plain text control.
  name: How to create content control in C# with Aspose.Words
  steps:
  - name: Expected output
    text: '- A `.docx` file on the desktop named `CustomerNameControl.docx`. - Inside
      the file, a single content control containing the text **John Doe**. - The placeholder
      text appears in light gray until the user types a new value.'
  - name: Adding multiple content controls
    text: You can repeat the **how to add sdt** steps to insert several controls in
      the same document. Just create a new `StructuredDocumentTag` for each field
      and move the builder accordingly.
  - name: Reading a placeholder programmatically
    text: 'If you need to verify that a placeholder was set correctly, inspect the
      `PlaceholderName` property:'
  - name: Using other SDT types
    text: Aspose.Words supports dropdown lists, date pickers, and rich‑text controls.
      Replace `SdtType.PlainText` with `SdtType.DropDownList` or `SdtType.RichText`
      to change the control type.
  type: HowTo
tags:
- Aspose.Words
- C#
- Content Control
- SDT
title: كيفية إنشاء عنصر تحكم المحتوى في C# باستخدام Aspose.Words
url: /ar/net/programming-with-sdt/how-to-create-content-control-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء عنصر تحكم محتوى في C# باستخدام Aspose.Words

إذا كنت بحاجة إلى **كيفية إنشاء عنصر تحكم محتوى** في مستند Word برمجيًا، فإن هذا الدليل يوضح لك ذلك بالضبط. سترى كيفية إضافة SDT، تعيين عنصر نائب، كتابة نص افتراضي، وإدراج عنصر تحكم نص عادي — كل ذلك باستخدام Aspose.Words for .NET.

يغطي البرنامج التعليمي كل خطوة من إعداد المشروع إلى حفظ ملف `.docx` النهائي. في النهاية ستتمكن من إنشاء مستندات تحتوي على عناصر تحكم محتوى مكوّنة بالكامل، جاهزة للمعالجة اللاحقة أو تفاعل المستخدم.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

- .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.7+)
- ترخيص Aspose.Words for .NET أو مفتاح تقييم مؤقت
- Visual Studio 2022 (أو أي بيئة تطوير تدعم C#)
- إلمام أساسي بصياغة C#

لا توجد حزم NuGet إضافية مطلوبة بخلاف `Aspose.Words`.

## كيفية إنشاء عنصر تحكم محتوى – الخطوة 1: إعداد المشروع

أنشئ تطبيقًا جديدًا من نوع console وأضف حزمة Aspose.Words:

```bash
dotnet new console -n ContentControlDemo
cd ContentControlDemo
dotnet add package Aspose.Words
```

تبدأ عملية **كيفية إنشاء عنصر تحكم محتوى** بإنشاء كائن `Document` جديد. يمثل هذا الكائن ملف Word الذي ستقوم بتعديله.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

> **نصيحة محترف:** احتفظ بمثيل `DocumentBuilder` فعال طوال دورة حياة المستند؛ إعادة إنشائه دون ضرورة يضيف عبئًا إضافيًا.

## كيفية إضافة SDT – الخطوة 2: إدراج Structured Document Tag نص عادي

SDT (Structured Document Tag) هو الاسم التقني لعنصر تحكم المحتوى. لـ **كيفية إضافة sdt**، أنشئ كائن `StructuredDocumentTag` بالنوع المطلوب.

```csharp
        // Create a plain‑text SDT (content control)
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            document,
            SdtType.PlainText,   // Plain‑text control
            true);               // Is it a repeating section? false for single use

        // Give the control a title – this is how you reference it later
        sdt.Title = "CustomerName";

        // Insert the SDT at the current cursor position
        builder.InsertNode(sdt);
```

الخيار `SdtType.PlainText` ينشئ مربع نص بسيط يمكن للمستخدمين تحريره. تعيين الخاصية `Title` يساعدك في تحديد موقع العنصر لاحقًا عندما تحتاج إلى استرجاع محتواه أو تعديلّه.

## كيفية تعيين عنصر نائب – الخطوة 3: تكوين نص العنصر النائب

العنصر النائب يوجه المستخدم النهائي من خلال إظهار نص مثال قبل أن يبدأ بالكتابة. لـ **كيفية تعيين عنصر نائب**، عيّن الخاصية `PlaceholderName`.

```csharp
        // Define the placeholder that appears when the control is empty
        sdt.PlaceholderName = "Enter name here";
```

عند فتح المستند في Microsoft Word، يظهر نص العنصر النائب الرمادي داخل العنصر حتى يضيف المستخدم قيمة.

## كيفية كتابة نص افتراضي – الخطوة 4: إضافة محتوى مبدئي داخل الـ SDT

إذا أردت أن يحتوي العنصر على محتوى مسبق التعريف، يجب نقل الـ builder داخل الـ SDT ثم كتابة النص. هذا يوضح **كيفية كتابة نص افتراضي**.

```csharp
        // Position the builder inside the SDT so we can add content
        builder.MoveTo(sdt);

        // Write the default text that will be visible initially
        builder.Write("John Doe");
```

الاتصال بـ `MoveTo` يغيّر موقع المؤشر إلى داخل الـ SDT. بعد `Write`، يظهر العنصر النص “John Doe” كقيمة مبدئية.

## إدراج عنصر تحكم نص عادي – الخطوة 5: حفظ المستند

أخيرًا، احفظ المستند على القرص. هذا يكمل عملية **إدراج عنصر تحكم نص عادي**.

```csharp
        // Save the document with the content control embedded
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CustomerNameControl.docx");

        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

عند فتح `CustomerNameControl.docx` في Word، سترى عنصر تحكم نص عادي بعنوان **CustomerName**، يظهر العنصر النائب “Enter name here” والنص الافتراضي “John Doe”.

### النتيجة المتوقعة

- ملف `.docx` على سطح المكتب اسمه `CustomerNameControl.docx`.
- داخل الملف، عنصر تحكم محتوى واحد يحتوي على النص **John Doe**.
- يظهر نص العنصر النائب باللون الرمادي الفاتح حتى يكتب المستخدم قيمة جديدة.

## تنويعات إضافية وحالات حافة

### إضافة عدة عناصر تحكم محتوى

يمكنك تكرار خطوات **كيفية إضافة sdt** لإدراج عدة عناصر في نفس المستند. فقط أنشئ `StructuredDocumentTag` جديد لكل حقل وانقل الـ builder وفقًا لذلك.

```csharp
// Example: add a second control for "OrderNumber"
StructuredDocumentTag orderTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
orderTag.Title = "OrderNumber";
orderTag.PlaceholderName = "Enter order #";
builder.InsertNode(orderTag);
builder.MoveTo(orderTag);
builder.Write("12345");
```

### قراءة العنصر النائب برمجيًا

إذا احتجت إلى التحقق من أن العنصر النائب تم تعيينه بشكل صحيح، افحص الخاصية `PlaceholderName`:

```csharp
string placeholder = sdt.PlaceholderName; // returns "Enter name here"
```

### استخدام أنواع SDT أخرى

يدعم Aspose.Words قوائم منسدلة، مختارات تاريخ، وعناصر تحكم نص غني. استبدل `SdtType.PlainText` بـ `SdtType.DropDownList` أو `SdtType.RichText` لتغيير نوع العنصر.

## الأخطاء الشائعة وكيفية تجنّبها

| العرض | السبب | الحل |
|---------|-------|-----|
| العنصر النائب لا يظهر أبداً | تم حفظ المستند قبل تعيين العنصر النائب | تأكد من تعيين `PlaceholderName` **قبل** استدعاء `Save`. |
| النص الافتراضي مفقود | لم يتم نقل الـ builder داخل الـ SDT | استدعِ `builder.MoveTo(sdt)` قبل `builder.Write`. |
| عنوان العنصر فارغ | الخاصية `Title` غير مُعينة | عيّن دائمًا `Title` ذو معنى لتسهيل الاسترجاع لاحقًا. |

## الخلاصة

أنت الآن تعرف **كيفية إنشاء عنصر تحكم محتوى** في C# باستخدام Aspose.Words، بما في ذلك **كيفية إضافة sdt**، **كيفية تعيين عنصر نائب**، **كيفية كتابة نص افتراضي**، و**إدراج عنصر تحكم نص عادي**. المثال الكامل يُترجم إلى ملف Word جاهز للاستخدام يُظهر كل مفهوم.

من هنا يمكنك استكشاف سيناريوهات أكثر تقدماً مثل ربط عناصر التحكم بالمحتوى ببيانات XML، معالجة الأقسام المتكررة، أو تحويل المستند إلى PDF مع الحفاظ على عناصر التحكم. كل هذه المواضيع تبنى مباشرةً على الأساسيات التي غطيناها في هذا الدرس.

برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تُبنى على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Rich Text Box Content Control](/words/hindi/net/programming-with-sdt/rich-text-box-content-control/)
- [Rich Text Box Content Control](/words/hongkong/net/programming-with-sdt/rich-text-box-content-control/)
- [Rich Text Box Content Control](/words/spanish/net/programming-with-sdt/rich-text-box-content-control/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}