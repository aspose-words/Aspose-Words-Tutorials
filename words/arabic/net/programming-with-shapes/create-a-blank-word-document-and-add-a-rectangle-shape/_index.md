---
category: general
date: 2026-09-05
description: تعلم كيفية إنشاء مستند Word فارغ وإضافة شكل مستطيل يمكن إخفاؤه باستخدام
  Aspose.Words في C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- add rectangle shape
- how to hide shape
- hide shape word
- create hidden shape
language: ar
lastmod: 2026-09-05
og_description: إنشاء مستند Word فارغ وإدراج شكل مستطيل مخفي باستخدام Aspose.Words
  – دليل خطوة بخطوة لمطوري C#.
og_image_alt: Screenshot of a blank Word document with a hidden rectangle shape created
  by Aspose.Words in C#
og_title: إنشاء مستند Word فارغ مع شكل مستطيل مخفي
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  headline: Create a blank word document and add a rectangle shape
  type: TechArticle
- description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  name: Create a blank word document and add a rectangle shape
  steps:
  - name: Expected result
    text: 'Open `HiddenRectangle.docx` in Word:'
  - name: Can I hide multiple shapes at once?
    text: Yes. Create each shape, set `Hidden = true`, and insert them sequentially.
      The hidden flag works per node, so mixing hidden and visible shapes in the same
      document is supported.
  - name: What if I need the shape to be hidden only in the print view?
    text: 'Word distinguishes between **display** and **print** visibility through
      the `DisplayWhen` property. Aspose.Words does not expose a direct API for that
      flag, but you can modify the underlying XML:'
  - name: Does the hidden shape affect file size?
    text: A hidden shape adds the same XML payload as a visible one, so the file size
      increase is identical. However, because the shape
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: إنشاء مستند Word فارغ وإضافة شكل مستطيل
url: /ar/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word فارغ وإضافة شكل مستطيل

إذا كنت بحاجة إلى **إنشاء مستند Word فارغ** يحتوي أيضًا على شكل لا تريد أن يظهر في التخطيط، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك باستخدام Aspose.Words for .NET. سترى مثالًا كاملاً وقابلاً للتنفيذ ينشئ مستندًا جديدًا، يضيف شكلًا مستطيلًا، يخفي ذلك الشكل، ويحفظ الملف—دون الحاجة إلى أدوات إضافية.

يغطي البرنامج التعليمي كل شيء من إعداد المشروع إلى استكشاف الأخطاء الشائعة. في النهاية، ستتمكن من توليد ملف Word يبدو فارغًا للقارئ لكنه لا يزال يحمل بيانات مخفية، وهو مفيد لأشياء مثل العلامات المائية، تخزين XML مخصص، أو نقاط تثبيت التخطيط.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من أن لديك:

* .NET 6.0 SDK أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.7+)
* Visual Studio 2022 (أو أي بيئة تطوير تدعم C#)
* ترخيص NuGet فعال لـ **Aspose.Words** (الإصدار التجريبي المجاني يكفي للاختبار)
* إلمام أساسي بـ C# ومفهوم عقد المستند

يمكنك تثبيت المكتبة باستخدام أمر سطر الأوامر التالي:

```bash
dotnet add package Aspose.Words
```

> **نصيحة احترافية:** حافظ على تحديث نسخة Aspose.Words الخاصة بك؛ الـ API المستخدم في هذا الدرس ثابت اعتبارًا من الإصدار 23.10.

## كيفية إنشاء مستند Word فارغ باستخدام Aspose.Words

الخطوة الأولى هي إنشاء كائن `Document`. يمثل `Document` جديد مستندًا **فارغًا** — لا فقرات، لا أقسام، فقط حاوية الملف.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, empty Word document
Document document = new Document();
```

> **لماذا هذا مهم:** البدء بمستند نظيف يضمن أن الشكل المخفي الذي ستضيفه لاحقًا لا يتداخل مع المحتوى أو الأنماط الموجودة.

## إضافة شكل مستطيل إلى المستند

بعد ذلك ننشئ شكلًا مستطيلًا. في Aspose.Words يُعد الشكل عقدة يمكن وضعها في أي مكان في شجرة المستند، ويمكن تكوينها بالحجم، التعبئة، نمط الخط، والظهور.

```csharp
// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Define a rectangle shape (the "add rectangle shape" step)
Shape rectangle = new Shape(document, ShapeType.Rectangle)
{
    Width = 150,   // Width in points (1 point = 1/72 inch)
    Height = 80,   // Height in points
    FillColor = System.Drawing.Color.LightGray,
    StrokeColor = System.Drawing.Color.DarkGray,
    StrokeWeight = 0.5
};
```

الكود أعلاه ينشئ مستطيلًا مرئيًا. في هذه المرحلة يمكنك إدراجه في المستند باستخدام `builder.InsertNode(rectangle)`. ومع ذلك، لأننا نريد أن يبقى الشكل مخفيًا، سنقوم بتعديل خاصية `Hidden` قبل الإدراج.

## كيفية إخفاء الشكل في مستند Word

يوفر Word خاصية `Hidden` لعقد الشكل. عند ضبطها على `true`، لا يظهر الشكل في تخطيط الصفحة، لكنه يبقى جزءًا من XML المستند. هذا هو جوهر متطلب **كيفية إخفاء الشكل**.

```csharp
// Hide the shape so it won't be displayed
rectangle.Hidden = true;
```

> **توضيح:** ضبط `Hidden = true` يضيف السمة `<w:hide>` إلى XML الخاص بالشكل. تتجاهل معالجات Word الشكل أثناء العرض، ومع ذلك يمكن الوصول إلى الشكل برمجيًا أو عبر عرض XML الخاص بـ Word.

## إدراج الشكل المخفي في المستند الفارغ

الآن نضع المستطيل المخفي في شجرة المستند. لأن المستند لا يزال فارغًا، يصبح الشكل هو أول عقدة في القصة الرئيسية.

```csharp
// Insert the hidden rectangle at the current cursor position
builder.InsertNode(rectangle);
```

إذا فتحت الملف الناتج في Microsoft Word، سترى صفحة تبدو فارغة. الشكل موجود، لكنه غير مرئي.

## حفظ المستند

أخيرًا، اكتب المستند إلى القرص. يمكنك اختيار أي تنسيق مدعوم (`.docx`, `.pdf`, `.odt`, إلخ). في هذا الدرس سنستخدم تنسيق DOCX الحديث.

```csharp
// Save the file – adjust the path as needed
string outputPath = Path.Combine(Environment.CurrentDirectory, "HiddenRectangle.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### النتيجة المتوقعة

افتح `HiddenRectangle.docx` في Word:

* يظهر المستند فارغًا (لا أشكال أو نصوص مرئية).
* إذا فحصت الملف بأداة مثل **Open XML SDK** أو **Word XML Viewer**، ستلاحظ وجود عنصر `<w:pict>` يحتوي على المستطيل مع السمة `hidden`.

![blank word document with hidden rectangle shape](image.png){: .align-center alt="مستند Word فارغ مع شكل مستطيل مخفي"}

## مثال كامل وقابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه ولصقه في تطبيق Console. يتضمن جميع توجيهات `using` اللازمة، معالجة الأخطاء، وتعليقات توضيحية.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Prepare a DocumentBuilder to manipulate the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Define a rectangle shape (add rectangle shape)
        Shape rectangle = new Shape(document, ShapeType.Rectangle)
        {
            Width = 150,
            Height = 80,
            FillColor = System.Drawing.Color.LightGray,
            StrokeColor = System.Drawing.Color.DarkGray,
            StrokeWeight = 0.5,
            // 4️⃣ Hide the shape (how to hide shape)
            Hidden = true
        };

        // 5️⃣ Insert the hidden shape into the blank document
        builder.InsertNode(rectangle);

        // 6️⃣ Save the document (create hidden shape)
        string outputPath = Path.Combine(
            Environment.CurrentDirectory, "HiddenRectangle.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

شغّل البرنامج (`dotnet run`) وتحقق من ملف الإخراج. سيؤكد الطرفية موقع الحفظ.

## أسئلة شائعة وحالات خاصة

### هل يمكن إخفاء عدة أشكال في آنٍ واحد؟

نعم. أنشئ كل شكل، اضبط `Hidden = true`، ثم أدخلها بالتتابع. علم الإخفاء يعمل على مستوى كل عقدة، لذا يمكن خلط الأشكال المخفية والمرئية في نفس المستند.

### ماذا لو أردت إخفاء الشكل فقط في عرض الطباعة؟

يميز Word بين **العرض** و**الطباعة** عبر خاصية `DisplayWhen`. لا توفر Aspose.Words API مباشرًا لتلك السمة، لكن يمكنك تعديل XML الأساسي:

```csharp
rectangle.GetShapeRenderer().GetShapeXml()
    .SetAttribute("w:display", "print");
```

استخدم هذا فقط عندما تحتاج إلى إخفاء الشكل في العرض مع إبقائه مرئيًا عند الطباعة.

### هل يؤثر الشكل المخفي على حجم الملف؟

يضيف الشكل المخفي نفس حمولة XML كالشكل المرئي، لذا فإن الزيادة في حجم الملف متطابقة. ومع ذلك، لأن الشكل  

## ما الذي يجب أن تتعلمه لاحقًا؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}