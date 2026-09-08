---
category: general
date: 2026-09-08
description: تعيين اسم العلامة وإنشاء عنصر تحكم محتوى (SDT) في مستند Word باستخدام
  C#. تعلّم كيفية إضافة SDT، كتابة نص إلى العلامة، وتعديل المستند.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set tag name
- how to add sdt
- modify word document
- create content control
- write text to tag
language: ar
lastmod: 2026-09-08
og_description: حدد اسم العلامة وأنشئ عنصر تحكم محتوى (SDT) في مستند Word باستخدام
  C#. اتبع هذا الدليل خطوة بخطوة لإضافة SDT، كتابة نص إلى العلامة، وتعديل المستند.
og_image_alt: Screenshot showing a Word document with a StructuredDocumentTag whose
  tag name is set
og_title: تعيين اسم العلامة وإضافة SDT في مستند Word – دليل C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Set tag name and create a content control (SDT) in a Word document
    using C#. Learn how to add SDT, write text to tag, and modify the document.
  headline: How to set tag name and add SDT in a Word document with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: كيفية تعيين اسم العلامة وإضافة SDT في مستند Word باستخدام C#
url: /ar/java/document-manipulation/how-to-set-tag-name-and-add-sdt-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تعيين اسم العلامة وإضافة SDT في مستند Word باستخدام C#

إذا كنت بحاجة إلى **تعيين اسم العلامة** لـ StructuredDocumentTag (SDT) أثناء العمل مع ملفات Word، فإن هذا الدليل يوضح لك بالضبط كيفية القيام بذلك. سترى مثالًا كاملاً قابلاً للتنفيذ **ينشئ عنصر تحكم محتوى**، يكتب نصًا إلى العلامة، و**يعدل مستند Word** من البداية إلى النهاية.

غالبًا ما يسأل المطورون، *“كيفية إضافة sdt* إلى ملف .docx موجود ثم *كتابة نص إلى العلامة*؟* – الجواب يكمن في استخدام Aspose.Words for .NET API. بنهاية هذا الشرح ستتمكن من فتح ملف Word، إدراج SDT نص عادي، تعيين اسم العلامة، ملئه بالمحتوى، وحفظ التغييرات دون ترك أي موارد معلقة.

## المتطلبات المسبقة

* .NET 6.0 أو أحدث مثبت.
* رخصة صالحة لـ Aspose.Words for .NET (أو يمكنك العمل بالإصدار التجريبي).
* Visual Studio 2022 (أو أي بيئة تطوير تدعم C#).
* مستند Word إدخال (`input.docx`) موجود في مجلد يمكنك الإشارة إليه من الكود.

## الخطوة 1: إعداد المشروع واستيراد المساحات الاسمية

أنشئ مشروع تطبيق Console جديد وأضف حزمة Aspose.Words من NuGet:

```bash
dotnet new console -n WordSdtDemo
cd WordSdtDemo
dotnet add package Aspose.Words
```

ثم، أضف توجيهات `using` اللازمة في أعلى ملف `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;
```

هذه المساحات الاسمية تمنحك الوصول إلى الفئات `Document` و `DocumentBuilder` و `StructuredDocumentTag`، وهي أساسية **لتعديل مستند Word**.

## الخطوة 2: تحميل مستند Word الموجود

العملية الأولى هي تحميل الملف الذي تريد تحريره. هذه الخطوة مطلوبة في كل سيناريو تحتاج فيه إلى **تعديل محتويات مستند Word**.

```csharp
// Load an existing Word document from disk
string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
Console.WriteLine($"Loaded document: {inputPath}");
```

> **لماذا نقوم بتحميل المستند أولاً** – كائن `Document` يمثل حزمة .docx كاملة في الذاكرة. فقط بعد التحميل يمكنك إدراج عقد جديدة بأمان مثل SDT.

## الخطوة 3: إدراج StructuredDocumentTag (SDT) وتعيين اسم العلامة

الآن نجيب على السؤال الأساسي: **كيفية إضافة sdt** و **تعيين اسم العلامة**. نستخدم `DocumentBuilder.InsertStructuredDocumentTag` مع `SdtType.PlainText`. الوسيط الثاني هو اسم العلامة، والذي يمكنك الإشارة إليه لاحقًا برمجيًا أو عبر واجهة Word.

```csharp
// Create a DocumentBuilder attached to the loaded document
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a plain‑text StructuredDocumentTag (content control) at the cursor position
// The second parameter ("MyTag") is the tag name we are setting.
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Confirm that the tag name has been set
Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");
```

> **شرح** – `InsertStructuredDocumentTag` تُعيد كائن `StructuredDocumentTag`. بتمرير `"MyTag"` نحن **نعيّن اسم العلامة** مباشرةً عند الإنشاء. إذا احتجت لتغييره لاحقًا، يمكنك تعيين قيمة جديدة إلى `sdt.Tag`.

## الخطوة 4: كتابة نص إلى العلامة التي تم إنشاؤها حديثًا

بعد وجود الـ SDT، عادةً ما تريد **كتابة نص إلى العلامة** حتى يرى المستخدمون النهائيون محتوى placeholder أو افتراضي. طريقة `SetText` تقوم بذلك بالضبط.

```csharp
// Populate the SDT with sample content
sdt.SetText("Sample content");

// Optionally, you can also set the placeholder text that appears when the tag is empty
sdt.PlaceholderName = "Enter your text here";
Console.WriteLine("Text written to the SDT.");
```

> **لماذا نستخدم SetText** – تعيين القيمة مباشرةً إلى الخاصية `Text` سيستبدل كل شجرة العقد. `SetText` تُحدّث النص الداخلي لعنصر التحكم بالمحتوى بأمان مع الحفاظ على هيكله.

## الخطوة 5: حفظ المستند المعدل

أخيرًا، احفظ التغييرات إلى ملف جديد. هذا يُكمل سير عمل **تعديل مستند Word**.

```csharp
// Define the output path
string outputPath = @"YOUR_DIRECTORY\output.docx";

// Save the document with the inserted content control
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

عند فتح `output.docx` في Microsoft Word، سترى عنصر تحكم نص عادي مُسمّى **MyTag** يحتوي على النص “Sample content”. يمكن تعديل العنصر يدويًا، ولا يزال اسم العلامة متاحًا عبر أدوات المطور في Word.

## الكود المصدر الكامل

فيما يلي البرنامج الكامل المستقل. انسخه إلى `Program.cs` وشغّله؛ لا تحتاج إلى أي مقتطفات إضافية.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the existing Word document
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(inputPath);
            Console.WriteLine($"Loaded document: {inputPath}");

            // 2️⃣ Create a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and set its tag name
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText, "MyTag");
            Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");

            // 4️⃣ Write text to the tag (and optionally set a placeholder)
            sdt.SetText("Sample content");
            sdt.PlaceholderName = "Enter your text here";
            Console.WriteLine("Text written to the SDT.");

            // 5️⃣ Save the modified document
            string outputPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### النتيجة المتوقعة في وحدة التحكم

```
Loaded document: YOUR_DIRECTORY\input.docx
Inserted SDT with tag name: MyTag
Text written to the SDT.
Document saved to: YOUR_DIRECTORY\output.docx
```

### ما يبدو عليه ملف Word الناتج

![مستند Word يُظهر عنصر تحكم محتوى مُسمّى MyTag مع النص “Sample content”](/images/word-sdt-example.png){: .img-fluid alt="مثال على تعيين اسم العلامة في مستند Word"}

*تُظهر لقطة الشاشة الـ SDT مع **اسم العلامة** المُعيّن إلى *MyTag* والنص المضمّن مرئيًا.*

## الاختلافات الشائعة وحالات الحافة

| الحالة | كيفية التعامل |
|-----------|------------------|
| **إنشاء SDT نص غني** | استخدم `SdtType.RichText` بدلاً من `PlainText`. |
| **تعيين اسم علامة مختلف بعد الإدراج** | `sdt.Tag = "NewTag";` – يمكنك إعادة تعيين اسم العلامة في أي وقت. |
| **إضافة الـ SDT داخل فقرة محددة** | حرك مؤشر الـ builder (`builder.MoveToParagraph(index)`) قبل استدعاء `InsertStructuredDocumentTag`. |
| **عدة SDTs في نفس المستند** | كرر الخطوتين 3‑4 لكل عنصر تحكم؛ يمكن لكل منها أن يكون له اسم علامة فريد. |
| **العمل مع مستندات محمية** | تأكد من أن المستند غير محمي (`doc.Unprotect()`) قبل إدراج SDT. |

## نصائح احترافية لأتمتة Word قوية

* **الترخيص مبكرًا** – استدعِ `Aspose.Words.License license = new Aspose.Words.License(); license.SetLicense("Aspose.Words.lic");` في بداية `Main` لتجنب علامات مائية للتقييم.
* **تحرير الكائنات** – غلف `Document` داخل كتلة `using` إذا كنت تستهدف .NET Framework لضمان تحرير مقابض الملفات.
* **التحقق من وجود العلامة** – عند قراءة مستند لاحقًا، استخدم `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` لتحديد العلامات عبر خاصية `Tag`.
* **الأداء** – للمستندات الكبيرة، حمّل الأقسام المطلوبة فقط باستخدام `LoadOptions` مع `LoadFormat.Docx` و `LoadFormat.Auto`.  

## الخلاصة

أنت الآن تعرف كيف **تعيّن اسم العلامة**، **تنشئ عنصر تحكم محتوى**، **تكتب نصًا إلى العلامة**، و **تعدل مستند Word** باستخدام C#. المثال الكامل يوضح النمط القياسي لـ **كيفية إضافة sdt** وحفظ التغييرات بأمان.  

من هنا

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إضافة محتوى باستخدام Document Builder في Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [مستند Word - كيفية إزالة المحتوى](/words/english/net/remove-content/)
- [إنشاء مستند Word باستخدام Aspose.Words – دليل خطوة بخطوة](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}