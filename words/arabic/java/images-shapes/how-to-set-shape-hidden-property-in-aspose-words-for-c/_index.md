---
category: general
date: 2026-08-20
description: تعلم كيفية تعيين خاصية الإخفاء للشكل في Aspose.Words للغة C#. يوضح هذا
  الدليل طريقة إدراج صورة وإخفاء الشكل بحيث لا يظهر أبداً في واجهة المستخدم أو في
  مخرجات الطباعة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set shape hidden property
- insert image into document
- hide shape in Aspose.Words
- C# shape hidden property
- Aspose.Words DocumentBuilder
- prevent shape from printing
language: ar
lastmod: 2026-08-20
og_description: تعيين خاصية الإخفاء للشكل في Aspose.Words باستخدام C#. إدراج صورة،
  إخفاء الشكل، وضمان عدم ظهوره أبداً في واجهة المستخدم أو مخرجات الطباعة.
og_image_alt: Diagram illustrating set shape hidden property on a Word document shape
og_title: تعيين خاصية الإخفاء للشكل في Aspose.Words – دليل C# الكامل
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to set shape hidden property in Aspose.Words for C#. This
    guide shows inserting an image and hiding the shape so it never appears in the
    UI or print output.
  headline: How to set shape hidden property in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Automation
- Shape Handling
title: كيفية تعيين خاصية الإخفاء للشكل في Aspose.Words للغة C#
url: /ar/java/images-shapes/how-to-set-shape-hidden-property-in-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تعيين خاصية إخفاء الشكل في Aspose.Words للـ C#

إذا كنت بحاجة إلى **تعيين خاصية إخفاء الشكل** في مستند Word، فإن هذا الدليل يوضح لك الخطوات الدقيقة باستخدام Aspose.Words للـ .NET. سواءً كنت تبني محرك قوالب، أو تُولّد تقارير، أو تُدرج شعارًا يجب أن يبقى غير مرئي، ستتعلم كيفية إدراج صورة وإخفاء الشكل بحيث لا يظهر أبدًا في واجهة المستخدم أو في مخرجات الطباعة.

في هذا الدليل نغطي أيضًا **إدراج صورة في المستند**، ونشرح لماذا يُهم إخفاء الشكل للطباعة، ونتناول الشيفرة الكاملة القابلة للتنفيذ. لا توجد مراجع خارجية مطلوبة—فقط انسخ، الصق، وشغّل.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* .NET 6.0 أو أحدث (أحدث نسخة من Aspose.Words تستهدف .NET 6+)
* ترخيص صالح لـ Aspose.Words للـ .NET (أو استخدم وضع التقييم المجاني)
* Visual Studio 2022 أو أي بيئة تطوير C# تفضلها
* ملف صورة (مثال: `logo.png`) موجود في مجلد يمكنك الإشارة إليه من الشيفرة

## الخطوة 1: إنشاء مستند جديد وDocumentBuilder

فئة `DocumentBuilder` هي نقطة الدخول لبناء محتوى Word برمجيًا. تتيح لك إدراج فقرات، جداول، وأشكال مثل الصور.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Initialize a new blank document
        Document doc = new Document();
        // DocumentBuilder provides methods to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*لماذا هذه الخطوة؟*  
إنشاء كائن `Document` يمنحك تمثيلًا في الذاكرة لملف .docx، بينما يوفر `DocumentBuilder` واجهة API سلسة لإدراج الكائنات. بدون هذين الكائنين لا يمكنك وضع شكل في المستند.

## الخطوة 2: إدراج الصورة كشكل

تتعامل Aspose.Words مع كل صورة كـ `Shape`. تُعيد طريقة `InsertImage` كائن الـ `Shape` هذا، والذي يمكنك التلاعب به لاحقًا.

```csharp
        // Step 2: Insert an image into the document
        // The returned Shape object lets us modify properties like size, rotation, and visibility.
        Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");
```

*لماذا هذه الخطوة؟*  
استخدام `InsertImage` لا يضيف الصورة إلى تدفق النص فحسب، بل يمنحك أيضًا مرجعًا (`picture`) يمكنك تكوينه. هذا أساسي لتطبيق **خاصية إخفاء الشكل في C#** التي سنقوم بتعيينها لاحقًا.

## الخطوة 3: تعيين خاصية إخفاء الشكل

تتحكم خاصية `Hidden` فيما إذا كان الشكل يشارك في واجهة المستخدم والطباعة. تعيينها إلى `true` يجعل الشكل غير مرئي في واجهة Word ويضمن عدم طباعته.

```csharp
        // Step 3: Hide the inserted shape so it won't appear in the UI or print output
        picture.Hidden = true;
```

*لماذا هذه الخطوة؟*  
عندما يُعلَّم الشكل بأنه مخفي، يتعامل Word معه كتعليق—موجود في بنية المستند لكنه لا يُعرض أبدًا. هذا هو جوهر **تعيين خاصية إخفاء الشكل**.

## الخطوة 4: حفظ المستند

أخيرًا، اكتب المستند إلى القرص. يمكنك اختيار أي تنسيق يدعمه Aspose.Words (`.docx`, `.pdf`, `.html`, إلخ).

```csharp
        // Step 4: Save the document to a .docx file
        doc.Save(@"OUTPUT\HiddenImageDocument.docx");
        // Optional: Save as PDF to verify the shape really stays hidden when printed
        doc.Save(@"OUTPUT\HiddenImageDocument.pdf");
    }
}
```

*لماذا هذه الخطوة؟*  
الحفظ يُكمل التغييرات في الذاكرة. فتح ملف `.docx` الناتج في Microsoft Word لا يظهر أي صورة مرئية، وتأكيد تصدير PDF يثبت أن الشكل لا يظهر في مخرجات الطباعة.

## مثال كامل قابل للتنفيذ

بدمج كل ما سبق، إليك البرنامج الكامل الذي يمكنك تجميعه وتشغيله:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeHiddenDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize a blank document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert an image as a shape
            // Replace YOUR_DIRECTORY with the actual folder that contains logo.png
            Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");

            // 3️⃣ Set the shape hidden property
            picture.Hidden = true; // This hides the shape in UI and when printing

            // 4️⃣ Save the document in both DOCX and PDF formats
            doc.Save(@"OUTPUT\HiddenImageDocument.docx");
            doc.Save(@"OUTPUT\HiddenImageDocument.pdf");

            Console.WriteLine("Document created successfully. The image is hidden.");
        }
    }
}
```

**الناتج المتوقع**

* فتح `HiddenImageDocument.docx` في Microsoft Word لا يُظهر أي صورة مرئية.
* تصدير أو طباعة المستند (أو فتح ملف PDF) لا يُظهر أي صورة.
* لا يزال الشكل المخفي موجودًا في XML الخاص بالمستند، ويمكنك التحقق من ذلك بفتح ملف `.docx` كملف zip وفحص `word/document.xml`—ستجد عنصر `<w:pict>` مع `w:hidden="true"`.

## الاختلافات الشائعة والحالات الخاصة

| الحالة | ما الذي يجب فعله | لماذا يهم |
|-----------|------------|----------------|
| **ملف الصورة مفقود** | غلف `InsertImage` داخل `try/catch` وتعامل مع `FileNotFoundException`. | يمنع تعطل التطبيق ويسمح لك بتسجيل خطأ واضح. |
| **وجود عدة أشكال مخفية** | استدعِ `picture.Hidden = true` لكل `Shape` تُدرجه، أو كرر عبر `doc.GetChildNodes(NodeType.Shape, true)`. | يضمن بقاء كل عنصر بصري غير مرغوب فيه مخفيًا. |
| **الحاجة إلى ظهور الشكل فقط في وضع التحرير** | عيّن `picture.Hidden = false` بعد التحرير، ثم عُد إلى `true` قبل الحفظ. | يسمح لك بالعمل مع الشكل في الواجهة بينما يبقى الناتج النهائي نظيفًا. |
| **الطباعة على إصدارات Word قديمة** | تحقق من المستند باستخدام Word 2010 أو أحدث؛ علم الإخفاء مدعوم في جميع الإصدارات الحديثة. | يضمن التوافق عبر قاعدة مستخدميك. |
| **استخدام تنسيق ملف مختلف (مثل PDF مباشرة)** | علم `Hidden` يعمل بنفس الطريقة؛ Aspose.Words يحترمه أثناء تحويل PDF. | يؤكد أن **منع الشكل من الطباعة** يعمل لجميع أهداف التصدير. |

## نصيحة احترافية: التحقق من علم الإخفاء برمجيًا

إذا كنت بحاجة إلى التأكد من أن الشكل مخفي قبل الحفظ، يمكنك فحص الخاصية:

```csharp
bool isHidden = picture.Hidden;
Console.WriteLine($"Shape hidden? {isHidden}");
```

هذا الفحص البسيط مفيد في خطوط الأنابيب الآلية حيث يجب ضمان الالتزام بسياسات توليد المستندات.

## الخلاصة

الآن تعرف كيف **تعيين خاصية إخفاء الشكل** في Aspose.Words للـ C#. عبر إدراج صورة، وتطبيق `picture.Hidden = true`، وحفظ المستند، يبقى الشكل خارج واجهة المستخدم ولا يظهر في مخرجات الطباعة. هذه التقنية أساسية عندما تحتاج إلى عناصر نائبة، علامات مائية، أو شعارات يجب أن تظل غير مرئية للمستخدم النهائي.

### ما التالي؟

* استكشف خصائص أخرى للأشكال مثل `picture.WrapType`، `picture.Rotation`، و`picture.RelativeHorizontalPosition`.
* تعلم كيفية **إخفاء الشكل في Aspose.Words** بناءً على مدخلات المستخدم أو الإعدادات.
* دمج الأشكال المخفية مع **إدراج صورة في المستند** داخل حلقات لتوليد علامات غير مرئية لمعالجة لاحقة (مثل حقول دمج البريد).

لا تتردد في تجربة صيغ صور مختلفة، تخطيطات مستندات، وأهداف تصدير متعددة. إخفاء الأشكال يمنحك تحكمًا دقيقًا فيما يراه القراء فعليًا—وما يبقى خلف الكواليس. برمجة سعيدة!

## ماذا يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}