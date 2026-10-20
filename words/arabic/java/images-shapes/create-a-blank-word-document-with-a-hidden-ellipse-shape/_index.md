---
category: general
date: 2026-09-18
description: إنشاء مستند Word فارغ وإخفاء شكل بيضاوي باستخدام Aspose.Words. تعلّم
  كيفية إخفاء الشكل في Word، وكيفية إدراج بيضاوي، وإنشاء شكل مخفي بسرعة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to hide shape
- how to insert ellipse
- hide shape in word
- create hidden shape
language: ar
lastmod: 2026-09-18
og_description: إنشاء مستند Word فارغ وإخفاء شكل إهليلجي في Word. يوضح لك هذا الدليل
  خطوة بخطوة كيفية إدراج إهليلج، إخفاء الشكل في Word، وإنشاء شكل مخفي باستخدام Aspose.Words.
og_image_alt: Screenshot of a blank Word document containing a hidden ellipse shape
  created with Aspose.Words
og_title: إنشاء مستند Word فارغ مع شكل إهليلجي مخفي
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  headline: Create a blank Word document with a hidden ellipse shape
  type: TechArticle
- description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  name: Create a blank Word document with a hidden ellipse shape
  steps:
  - name: Pro tip
    text: If you later need to make the shape visible again, simply set `ellipse.Hidden
      = false;` and save the document.
  - name: What if the shape still appears?
    text: '* Ensure you are using Aspose.Words 23.9 or later – older versions had
      a bug where `Hidden` was ignored for some shape types. * Verify that you are
      not applying any additional formatting (e.g., `WrapType`) that forces the shape
      to occupy layout space.'
  - name: Can I hide other shape types?
    text: Yes. The same `Hidden` property works for `ShapeType.Rectangle`, `ShapeType.Picture`,
      etc. Just replace `ShapeType.Ellipse` with the desired type.
  - name: How to list hidden shapes later?
    text: '```csharp foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
      { if (shape.Hidden) Console.WriteLine($"Hidden shape: {shape.ShapeType}"); }
      ```'
  - name: Next steps
    text: '* Explore **how to hide shape** conditionally based on document content.
      * Learn **how to unhide shape** when generating a final version of the document.
      * Combine hidden shapes with **custom document properties** to embed machine‑readable
      data.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: إنشاء مستند Word فارغ مع شكل إهليلجي مخفي
url: /ar/java/images-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word فارغ مع شكل إهليلجي مخفي

إذا كنت بحاجة إلى **إنشاء مستند Word فارغ** يحتوي على شكل لا تريد أن يظهر في التخطيط، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك. باستخدام Aspose.Words for .NET يمكنك إدراج إهليلج برمجيًا ثم إخفاء الشكل بحيث يبقى المستند فارغًا بصريًا مع الاحتفاظ ببيانات الشكل.

في هذا البرنامج التعليمي ستتعلم:

* كيفية **إنشاء كائنات مستند Word فارغ**،
* كيفية **إدراج إهليلج** باستخدام `DocumentBuilder`،
* كيفية **إخفاء الشكل في Word** بحيث لا يؤثر على الصفحة،
* كيفية **إنشاء كائنات شكل مخفي** للمعالجة لاحقًا.

تعمل الخطوات مع .NET 6+ وأحدث نسخة من Aspose.Words (23.9 وقت كتابة هذا الدليل). لا يلزم تثبيت Office إضافي.

## المتطلبات المسبقة

* Visual Studio 2022 (أو أي بيئة تطوير C#)
* .NET 6 SDK أو أحدث
* حزمة Aspose.Words for .NET عبر NuGet  
  ```bash
  dotnet add package Aspose.Words
  ```
* معرفة أساسية بـ C# ومفاهيم مستندات Word

## الخطوة 1: إنشاء مستند Word فارغ

أول شيء يجب القيام به هو إنشاء كائن `Document`. يمثل هذا الكائن ملف `.docx` فارغ وهو الأساس لجميع العمليات اللاحقة.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document doc = new Document();   // <-- creates a blank Word document in memory
```

إن **إنشاء مستند Word فارغ** يمنحك لوحة رسم نظيفة – لا فقرات، لا أقسام، فقط بنية الحزمة الأساسية. هذا هو نقطة الانطلاق المثالية عندما تحتاج فقط إلى شكل مخفي ولا شيء آخر.

## الخطوة 2: تهيئة DocumentBuilder

`DocumentBuilder` يوفر واجهة برمجة تطبيقات مريحة لإضافة محتوى إلى `Document`. يعمل كالمؤشر الذي تتحرك به عبر المستند.

```csharp
// Step 2: Initialise a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

يقوم الـ builder تلقائيًا بإنشاء القسم والفقرة الأوليين الافتراضيين، لذا يمكنك البدء في إدراج الأشكال دون الحاجة لإضافة أقسام يدويًا.

## الخطوة 3: إدراج شكل إهليلجي

الآن نقوم **بإدراج إهليلج** باستخدام طريقة `InsertShape`. تأخذ الطريقة تعداد `ShapeType`، العرض، والارتفاع (بالنقاط).

```csharp
// Step 3: Insert an ellipse shape with a width of 100 points and a height of 50 points
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
```

لماذا إهليلج؟ الإهليلج هو شكل متجه يمكن إخفاؤه دون التأثير على تدفق النص المحيط. العرض 100 pt والارتفاع 50 pt قيم عشوائية؛ يمكنك تعديلها لتناسب احتياجات المعالجة اللاحقة.

## الخطوة 4: إخفاء الشكل بحيث لا يظهر في التخطيط

لـ **إخفاء الشكل في Word**، اضبط الخاصية `Hidden` لكائن `Shape` على `true`. عند فتح المستند في Microsoft Word، سيكون الشكل غير مرئي ولن يشغل مساحة في التخطيط.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
ellipse.Hidden = true;   // <-- this hides the shape in Word
```

علامة `Hidden` تُخزن في XML الخاص بالشكل (`<w:hidden/>`). يحترم Word هذه السمة أثناء العرض، وهذا هو السبب في أن المستند يبدو فارغًا تمامًا رغم وجود الشكل.

### نصيحة احترافية

إذا احتجت لاحقًا إلى جعل الشكل مرئيًا مرة أخرى، ما عليك سوى تعيين `ellipse.Hidden = false;` وحفظ المستند.

## الخطوة 5: حفظ المستند مع الشكل المخفي

أخيرًا، احفظ المستند على القرص. سيكون الملف `.docx` عاديًا يمكن لأي معالج Word فتحه.

```csharp
// Step 5: Save the document with the hidden shape
doc.Save(@"C:\Temp\HiddenEllipse.docx");
```

الملف المحفوظ، `HiddenEllipse.docx`، هو **مستند Word فارغ** يحتوي على إهليلج مخفي. عند فتحه في Microsoft Word سيظهر صفحة فارغة، لكن الشكل لا يزال موجودًا في بنية Open XML.

## مثال كامل يعمل

فيما يلي البرنامج الكامل المستقل الذي يمكنك نسخه ولصقه وتشغيله.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();

            // 2️⃣ Initialise DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse shape (width: 100pt, height: 50pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the shape so it does not affect layout
            ellipse.Hidden = true;

            // 5️⃣ Save the result
            string outputPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**الناتج المتوقع**

* ملف باسم `HiddenEllipse.docx` يظهر في `C:\Temp`.
* فتح الملف في Microsoft Word يعرض صفحة فارغة تمامًا.
* إذا فحصت المستند باستخدام Open XML SDK أو عارض ZIP، ستجد عنصر `<w:shape>` مع `<w:hidden/>` داخل جزء المستند.

## أسئلة شائعة وحالات خاصة

### ماذا لو استمر الشكل في الظهور؟

* تأكد من أنك تستخدم Aspose.Words 23.9 أو أحدث – الإصدارات القديمة كان فيها خلل يتجاهل `Hidden` لبعض أنواع الأشكال.
* تحقق من أنك لا تطبق أي تنسيق إضافي (مثل `WrapType`) يجبر الشكل على شغل مساحة في التخطيط.

### هل يمكن إخفاء أنواع أشكال أخرى؟

نعم. خاصية `Hidden` نفسها تعمل مع `ShapeType.Rectangle`، `ShapeType.Picture`، إلخ. فقط استبدل `ShapeType.Ellipse` بالنوع المطلوب.

### كيف أسرد الأشكال المخفية لاحقًا؟

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.Hidden)
        Console.WriteLine($"Hidden shape: {shape.ShapeType}");
}
```

تقوم هذه الشريحة بالت iterating على جميع الأشكال وتطبع تلك المخفية، وهو مفيد لتدفقات عمل **إنشاء شكل مخفي** حيث تحتاج لاحقًا إلى معالجة أو إظهار هذه الأشكال.

## الخلاصة

أنت الآن تعرف كيف **تنشئ مستند Word فارغ**، **تدرج إهليلج**، وتـ **تخفي الشكل في Word** لإنتاج **شكل مخفي** يبقى غير مرئي للقارئ. هذه التقنية مفيدة لتخزين البيانات الوصفية، العلامات المرجعية، أو XML مخصص داخل المستند دون تغيير مظهره البصري.

### الخطوات التالية

* استكشاف **كيفية إخفاء الشكل** بشكل شرطي بناءً على محتوى المستند.
* تعلم **كيفية إظهار الشكل** عند إنشاء النسخة النهائية من المستند.
* دمج الأشكال المخفية مع **خصائص المستند المخصصة** لتضمين بيانات قابلة للقراءة آليًا.

لا تتردد في تجربة أنواع أشكال مختلفة، أحجام، ومنطق حالة الإخفاء لتناسب سيناريو الأتمتة الخاص بك. Happy coding!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [إنشاء مستند Word فارغ مع شكل مستطيل مظلل – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [إنشاء شكل مستطيل في Word باستخدام Aspose.Words – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [إنشاء مجموعة أشكال في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}