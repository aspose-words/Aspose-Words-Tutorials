---
category: general
date: 2026-09-11
description: إضافة عنصر تحكم محتوى في مستند Word باستخدام Aspose.Words. اتبع هذا الدليل
  خطوة بخطوة لإدراج علامة مستند منسقة (SDT) نصية بسيطة برمجيًا.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add content control in word document
- StructuredDocumentTag
- DocumentBuilder
- Aspose.Words
- plain‑text SDT
- word automation
language: ar
lastmod: 2026-09-11
og_description: إضافة عنصر تحكم بالمحتوى في مستند Word باستخدام Aspose.Words. يوضح
  هذا الدليل كيفية إدراج علامة مستند منسقة (SDT) نصية بسيطة برمجيًا وتخصيصها.
og_image_alt: Screenshot of a Word document showing a content control placeholder
og_title: إضافة عنصر تحكم المحتوى في مستند Word – دليل Aspose.Words الكامل
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Add content control in Word document using Aspose.Words. Follow this
    step‑by‑step guide to insert a plain‑text Structured Document Tag (SDT) programmatically.
  headline: Add content control in Word document with Aspose.Words
  type: TechArticle
tags:
- word
- content‑control
- csharp
- aspose
title: إضافة عنصر تحكم محتوى في مستند Word باستخدام Aspose.Words
url: /ar/java/document-manipulation/add-content-control-in-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة عنصر تحكم المحتوى في مستند Word باستخدام Aspose.Words

إذا كنت بحاجة إلى **إضافة عنصر تحكم المحتوى في مستند Word** برمجياً، فإن هذا الدرس يوضح لك بالضبط كيفية القيام بذلك باستخدام Aspose.Words لـ .NET. سواءً كنت تبني خدمة توليد مستندات أو تقوم بأتمتة إنشاء النماذج، ستتعلم كيفية إدراج Structured Document Tag (SDT) نصي عادي ومنحه عنوانًا ذا معنى.

في هذا الدليل سترى مثالًا كاملاً قابلاً للتنفيذ يغطي جميع الاستيرادات المطلوبة، ويشرح لماذا كل استدعاء API مهم، ويظهر كيفية التحقق من النتيجة. لا تحتاج إلى أي مراجع خارجية—فقط انسخ الشيفرة، شغّلها، وافتح الملف *.docx* المُولد.

## Prerequisites

قبل أن تبدأ، تأكد من أن لديك:

* .NET 6.0 SDK أو أحدث مثبت  
* Visual Studio 2022 (أو أي بيئة تطوير C#)  
* Aspose.Words لـ .NET 23.5 أو أحدث – يمكنك الحصول على حزمة NuGet تجريبية مجانية  

هذه العناصر تشكل الحد الأدنى لإعداد **أتمتة Word** باستخدام Aspose.Words.

## Step 1: Set up the project and import namespaces

أنشئ مشروعًا جديدًا من نوع console وأضف حزمة Aspose.Words:

```bash
dotnet new console -n ContentControlDemo
cd ContentControlDemo
dotnet add package Aspose.Words
```

الآن افتح `Program.cs` وأضف توجيهات `using` المطلوبة:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Builders;
using Aspose.Words.Markup;
```

هذه المساحات الاسمية تمنحك الوصول إلى `DocumentBuilder` و `StructuredDocumentTag` وأنواع أساسية أخرى needed to **add content control in Word document**.

## Step 2: Create a new document and a DocumentBuilder

`DocumentBuilder` هو نقطة الدخول الأساسية لإنشاء ملفات Word. يحتفظ بمؤشر يتتبع مكان إدراج العنصر التالي.

```csharp
// Step 2: Initialize a new blank document and a builder
Document doc = new Document();                 // creates an empty .docx
DocumentBuilder builder = new DocumentBuilder(doc);
```

*لماذا هذا مهم*: كائن `Document` يمثل ملف Word بالكامل، بينما `DocumentBuilder` يبسط إدراج الفقرات والجداول و**عناصر تحكم المحتوى** مثل Structured Document Tags.

## Step 3: Insert a plain‑text Structured Document Tag (SDT)

جوهر حلنا هو طريقة `insertStructuredDocumentTag`. إنها تنشئ **عنصر تحكم محتوى** يمكنه احتواء نص عادي، تواريخ، قوائم منسدلة، إلخ. هنا نستخدم قيمة التعداد `SdtType.PLAIN_TEXT`.

```csharp
// Step 3: Insert a plain‑text SDT at the current cursor position
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText,   // the type of control – plain‑text here
    true);               // true = the tag is shown as a placeholder in the UI
```

*لماذا هذا مهم*: ضبط القيمة `true` يجعل عنصر التحكم يظهر كعنصر نائب رمادي فاتح، مما يشير للمستخدمين النهائيين بضرورة ملء الحقل.

## Step 4: Give the SDT a title for later identification

العنوان (أو الوسم) يتيح لك العثور على عنصر التحكم لاحقًا، على سبيل المثال عندما تحتاج إلى استبدال محتوياته برمجياً.

```csharp
// Step 4: Assign a title so you can find the control later
sdt.Title = "CustomerName";
```

العنوان لا يظهر في واجهة المستند، لكنه يُخزن في XML الأساسي ويمكن استرجاعه عبر Aspose.Words API.

## Step 5: Add placeholder text inside the SDT

لجعل عنصر التحكم أكثر سهولة للمستخدم، أدخل تشغيلًا افتراضيًا يخبر المستخدم ماذا يكتب.

```csharp
// Step 5: Add placeholder text inside the SDT
Run placeholder = new Run(builder.Document, "Enter name here");
sdt.AppendChild(placeholder);
```

*لماذا هذا مهم*: كائن `Run` يمثل قطعة من النص. بإلحاقه بالـ SDT تنشئ تلميحًا مرئيًا يختفي بمجرد بدء المستخدم الكتابة.

## Step 6: Save the document

أخيرًا، احفظ المستند على القرص حتى تتمكن من فتحه في Microsoft Word.

```csharp
// Step 6: Save the finished document
string outPath = "ContentControlExample.docx";
doc.Save(outPath);
Console.WriteLine($"Document saved to {outPath}");
```

عند فتح `ContentControlExample.docx`، سترى عنصر تحكم محتوى مظلل بالرمادي بعنوان **CustomerName** مع نص العنصر النائب *Enter name here*.

## Full working example

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑ولصقه في `Program.cs`. يتضمن جميع الخطوات، التعليقات، ومعالجة الأخطاء اللازمة.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Builders;
using Aspose.Words.Markup;

namespace ContentControlDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new empty document
            Document doc = new Document();

            // Initialize the DocumentBuilder – this controls where we insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a plain‑text Structured Document Tag (SDT)
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,   // type of content control
                true);               // show as placeholder

            // Assign a title for later lookup (not visible in the UI)
            sdt.Title = "CustomerName";

            // Add placeholder text that instructs the user
            Run placeholder = new Run(builder.Document, "Enter name here");
            sdt.AppendChild(placeholder);

            // Save the document to the file system
            string outPath = "ContentControlExample.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Expected output

تشغيل البرنامج يطبع:

```
Document saved to ContentControlExample.docx
```

فتح الملف المُولد في Word يظهر عنصر تحكم محتوى واحد مع العنصر النائب الرمادي **Enter name here**. يمكن تعديل العنصر أو حذفه أو الوصول إليه برمجياً لاحقًا باستخدام عنوانه *CustomerName*.

## Common variations and edge cases

| السيناريو | كيفية تعديل الشيفرة |
|----------|----------------------|
| **عناصر تحكم محتوى متعددة** | استدعِ `InsertStructuredDocumentTag` بشكل متكرر، مع تعيين `Title` فريد في كل مرة. |
| **عنصر تحكم محتوى نص غني** | استخدم `SdtType.RichText` بدلاً من `PlainText`. |
| **عنصر تحكم اختيار تاريخ** | استخدم `SdtType.Date` واختياريًا عيّن `sdt.DateDisplayFormat`. |
| **قفل عنصر التحكم** | عيّن `sdt.LockContentControl = true` لمنع المستخدمين من إزالته. |
| **العثور على عنصر التحكم لاحقًا** | استخدم `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` وقم بالترشيح حسب `Title`. |

هذه التغييرات توضح مرونة **Aspose.Words** عندما تحتاج إلى **إضافة عنصر تحكم المحتوى في مستند Word** لسيناريوهات تعبئة نماذج مختلفة.

## Pro tips

* **الأداء** – إذا كنت تُنشئ العديد من المستندات في حلقة، أعد استخدام نسخة واحدة من `DocumentBuilder` واستدعِ `doc.Clone()` لكل تكرار لتجنب إنشاء كائنات متكرر.  
* **التنسيق** – يمكنك تطبيق `ParagraphFormat` أو `Font` على الـ `Run` العنصر النائب لتتناسب مع النمط البصري لمستندك.  
* **التحقق** – بعد إدراج عنصر التحكم، يمكنك فحص `sdt.IsShowingPlaceholderText` للتأكد من أن العنصر النائب معروض بشكل صحيح.  

## Conclusion

أنت الآن تعرف كيفية **إضافة عنصر تحكم المحتوى في مستند Word** باستخدام Aspose.Words، بدءًا من إنشاء `DocumentBuilder` إلى إدراج `StructuredDocumentTag` نصي عادي، وتعيين عنوان، وإضافة نص عنصر نائب. يمكن توسيع المثال الكامل إلى أنواع SDT أخرى، وعناصر تحكم متعددة، وخيارات قفل أو تنسيق متقدمة.

هل أنت مستعد للمزيد؟ استكشف هذه المواضيع ذات الصلة:

* **العمل مع الجداول داخل عناصر التحكم** – استخدم `DocumentBuilder.InsertTable` بعد الـ SDT.  
* **استخراج البيانات من العناصر المملوءة** – استرجع عقدة `Sdt` حسب العنوان واقرأ خاصية `Text` الخاصة بها.  
* **استخدام OpenXML SDK** – نهج بديل إذا كنت تفضل مكتبة مجانية مدعومة من مايكروسوفت.  

## What Should You Learn Next?

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إضافة محتوى باستخدام Document Builder في Aspose.Words لـ .NET](/words/english/net/add-content-using-document-builder/)
- [إدراج صورة مدمجة في مستند Word باستخدام Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [إنشاء مستند Word مع جدول باستخدام Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}