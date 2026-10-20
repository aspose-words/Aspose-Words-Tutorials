---
category: general
date: 2026-10-20
description: إخفاء/إظهار شكل باستخدام الخاصية الجديدة `Hidden` في Aspose.Words للغة
  C#. تعلم كيفية تبديل رؤية الشكل، ومعالجة الحالات الخاصة، وحفظ النتيجة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Hide/Show a Shape with the new `Hidden` prop
- Aspose.Words hide shape
- C# shape hidden property
- Word document shape visibility
- programmatically hide shape
language: ar
lastmod: 2026-10-20
og_description: إخفاء/إظهار شكل باستخدام الخاصية الجديدة `Hidden` في Aspose.Words
  للغة C#. إتقان تبديل رؤية الشكل وتجنب الأخطاء الشائعة.
og_image_alt: Screenshot of a Word document where a shape is hidden using the Hidden
  property
og_title: إخفاء/إظهار شكل باستخدام الخاصية الجديدة `Hidden` في Aspose.Words (C#)
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Hide/Show a Shape with the new `Hidden` prop using Aspose.Words for
    C#. Learn how to toggle shape visibility, handle edge cases, and save the result.
  headline: Hide/Show a Shape with the new `Hidden` prop in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: إخفاء/إظهار شكل باستخدام الخاصية الجديدة `Hidden` في Aspose.Words للغة C#
url: /ar/net/programming-with-shapes/hide-show-a-shape-with-the-new-hidden-prop-in-aspose-words-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إخفاء/إظهار شكل باستخدام الخاصية الجديدة `Hidden` في Aspose.Words للغة C#

إذا كنت بحاجة إلى **إخفاء/إظهار شكل باستخدام الخاصية الجديدة `Hidden`** في مستند Word، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك باستخدام Aspose.Words للـ .NET. سواءً كنت تُنشئ تقارير، تبني قوالب، أو تنظف مستندات مستوردة، فإن التحكم في رؤية الشكل برمجياً يوفر عليك التحرير اليدوي.

في هذا البرنامج التعليمي ستتعلم كيفية تحميل مستند، تحديد شكل، تبديل خاصية `Hidden`، وحفظ الملف المعدل. تغطي الخطوات أيضًا تنويعات شائعة مثل التعامل مع عدة أشكال ومعالجة الرسومات المضمنة (inline) مقابل العائمة (floating).

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* .NET 6.0 (أو أحدث) مثبت – تدعم Aspose.Words .NET Standard 2.0 و .NET Core.  
* نسخة مرخصة من **Aspose.Words للـ .NET** (الإصدار التجريبي المجاني يكفي للاستكشاف).  
* بيئة تطوير متكاملة مثل Visual Studio 2022 أو Visual Studio Code.  
* مستند Word (`input.docx`) يحتوي على شكل واحد على الأقل (مثل صورة، SmartArt، أو لوحة رسم).

## الخطوة 1: تحميل مستند Word

العملية الأولى هي إنشاء كائن `Document` يمثل ملف .docx الموجود على القرص.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*لماذا هذه الخطوة مهمة*: `Document` هو نقطة الدخول لجميع عمليات Aspose.Words. تحميل الملف إلى الذاكرة يمنحك وصولاً كاملاً إلى شجرة العقد، بما في ذلك الأشكال.

## الخطوة 2: استرجاع الشكل المستهدف

لتبديل الرؤية يجب الحصول على مرجع إلى عقدة الشكل. المثال أدناه يجلب الشكل الأول في المستند، لكن يمكنك تعديل المنطق لتحديد الأشكال حسب الاسم أو النوع أو الفهرس.

```csharp
// Get the first Shape node in the document tree
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

if (shape == null)
{
    throw new InvalidOperationException("No shape was found in the document.");
}
```

*لماذا هذه الخطوة مهمة*: `GetChild` مع القيمة `true` يقوم ببحث عميق، مما يضمن العثور على الأشكال حتى عندما تكون متداخلة داخل جداول أو رؤوس. التحقق من `null` يمنع حدوث `NullReferenceException` عندما لا يحتوي المستند على أي أشكال.

## الخطوة 3: إخفاء الشكل باستخدام خاصية `Hidden`

أدخلت Aspose.Words الخاصية `Hidden` للتحكم فيما إذا كان الشكل يُعرض أو يُطبع. تعيينها إلى `true` يخفي الشكل؛ وتعيينها إلى `false` يجعل الشكل مرئياً مرة أخرى.

```csharp
// Hide the shape so it will not appear in the rendered document
shape.Hidden = true;
```

إذا كنت بحاجة إلى **إظهار** شكل تم إخفاؤه مسبقًا، ما عليك سوى تعيين `false`:

```csharp
// Show the shape again
shape.Hidden = false;
```

*لماذا هذه الخطوة مهمة*: خاصية `Hidden` تعمل مع كل من الأشكال العائمة والمضمنة، وتندمج مع تنسيق “Hidden” الأصلي في Word. هذا النهج أكثر موثوقية من حذف الشكل لأن العقدة تبقى في شجرة المستند، مما يحافظ على التخطيط والمرجعيات.

## الخطوة 4: حفظ المستند المعدل

بعد تعديل الرؤية، اكتب التغييرات إلى ملف جديد (أو استبدل الأصلي إذا رغبت).

```csharp
// Save the document with the updated shape visibility
doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");
```

*لماذا هذه الخطوة مهمة*: `Save` تسلسل شجرة العقد في الذاكرة إلى حزمة .docx يمكن لـ Word فتحها. يتم حفظ علم الإخفاء، لذا عند فتح الملف في Microsoft Word سيظهر الشكل وفقًا لإعداد `Hidden`.

## مثال كامل قابل للتنفيذ

جمع جميع الخطوات معًا يمنحك برنامجًا مستقلاً يمكنك نسخه، تجميعه، وتشغيله.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShowShapeExample
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape in the document
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found. Exiting.");
            return;
        }

        // 3. Toggle the Hidden property
        // Hide the shape
        shape.Hidden = true;
        // To show the shape again, uncomment the following line:
        // shape.Hidden = false;

        // 4. Save the modified document
        doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");

        Console.WriteLine("Document saved. Shape hidden = " + shape.Hidden);
    }
}
```

**الناتج المتوقع** عند تشغيل البرنامج:

```
Document saved. Shape hidden = True
```

فتح `ShapeHidden.docx` في Microsoft Word يعرض المستند بدون الشكل المستهدف. إذا قمت بتعيين `shape.Hidden = false;` قبل الحفظ، سيظهر الشكل مرة أخرى.

## التعامل مع عدة أشكال

المثال أعلاه يعمل على شكل واحد. غالبًا ما تحتوي المستندات الواقعية على العديد من الرسومات. استخدم حلقة لإخفاء أو إظهار جميع الأشكال التي تفي بشرط معين (مثل اسم أو نوع محدد).

```csharp
// Hide every picture shape in the document
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Image)
    {
        s.Hidden = true; // hide picture
    }
}
doc.Save("YOUR_DIRECTORY/AllPicturesHidden.docx");
```

*نصيحة*: تصفية حسب `ShapeType` تجنب إخفاء العناصر الزخرفية مثل مربعات النص أو SmartArt عن غير قصد.

## الحالات الخاصة وأفضل الممارسات

| الحالة | المعالجة الموصى بها |
|-----------|----------------------|
| **الشكل داخل رأس/تذييل** | استرجع عقدة الرأس/التذييل أولاً، ثم استدعِ `GetChild(NodeType.Shape, …)` على ذلك المستند الفرعي. |
| **المستند لا يحتوي على أشكال** | تحقق دائمًا من `null` بعد `GetChild` أو افحص `doc.GetChildNodes(NodeType.Shape, true).Count`. |
| **ضرورة الحفاظ على علم الإخفاء عبر إصدارات Word مختلفة** | خاصية `Hidden` تُخزن في XML الخاص بالشكل كـ `<w:hidden/>`، وهو مدعوم من Word 2007 وما بعده. |
| **الأداء مع المستندات الكبيرة** | استخدم `doc.GetChildNodes(NodeType.Shape, true)` مرة واحدة وأعد استخدام المجموعة بدلًا من استدعاء `GetChild` بشكل متكرر. |

## نصيحة احترافية: دمج `Hidden` مع `WrapType`

عند إخفاء الشكل، لا يزال Word يحتفظ بالمساحة التي كان سيشغلها ما لم تقم أيضًا بتغيير سلوك الالتفاف. تعيين `WrapType = WrapType.None` يزيل مساحة العنصر النائب.

```csharp
shape.Hidden = true;
shape.WrapType = WrapType.None;
```

هذا يضمن أن التخطيط ينهار كما لو أن الشكل لم يكن موجودًا، وهو مفيد لتوليد تقارير نظيفة.

## الخلاصة

أنت الآن تعرف كيف **تخفي/تظهر شكل باستخدام الخاصية الجديدة `Hidden`** باستخدام Aspose.Words للغة C#. يغطي الحل تحميل المستند، تحديد الشكل، تبديل خاصية `Hidden`، وحفظ التغيير. باتباع نصائح أفضل الممارسات—التحقق من null، التعامل مع عدة أشكال، وضبط إعدادات الالتفاف—يمكنك التحكم في رؤية الأشكال بثقة في أي سيناريو أتمتة Word.

هل أنت مستعد لاستكشاف المزيد؟ فكر في الخطوات التالية:

* **إخفاء/إظهار عدة أشكال** بناءً على بيانات تعريف مخصصة (يستخدم تقنية “إخفاء الشكل برمجياً”).  
* **دمج `Hidden` مع محتوى شرطي** باستخدام حقول Aspose.Words لتوليد تقارير ديناميكية.  
* **استكشاف خصائص عقد أخرى**، مثل `Visible` لكائنات المخططات أو `IsDeleted` للتحكم على مستوى الفقرة.

برمجة سعيدة، واستمتع بالتحكم الدقيق الذي توفره Aspose.Words في رؤية أشكال مستندات Word!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [how to hide shape in Word using C# – step-by-step guide](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-using-c-step-by-step-guide/)
- [How to Hide Shape in Word with C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-with-c-step-by-step-guide/)
- [Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}