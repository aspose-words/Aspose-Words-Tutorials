---
category: general
date: 2026-08-10
description: إدراج شكل مستطيل في Word باستخدام C#. تعلم كيفية إخفاء الشكل، إخفاء الشكل
  في Word، وإنشاء شكل مخفي باستخدام Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- hide shape in word
- create hidden shape
language: ar
lastmod: 2026-08-10
og_description: إدراج شكل مستطيل في Word باستخدام C#. يشرح هذا البرنامج التعليمي كيفية
  إخفاء الشكل، إخفاء الشكل في Word، وإنشاء شكل مخفي مع أمثلة كاملة للكود.
og_image_alt: Screenshot showing a hidden rectangle shape inserted into a Word document
  using C#
og_title: إدراج شكل مستطيل في Word باستخدام C# – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  headline: Insert rectangle shape in Word with C# – complete guide
  type: TechArticle
- description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  name: Insert rectangle shape in Word with C# – complete guide
  steps:
  - name: Can I hide only the outline but keep the fill visible?
    text: Yes. Instead of setting `Hidden = true`, you can set `rectangle.LineFormat.Visible
      = false` to hide the border while keeping the fill color. This is a variation
      of **how to hide shape** that preserves part of the visual appearance.
  - name: Does the hidden flag work in older Word versions (2003, 2007)?
    text: The hidden attribute is part of the Open XML specification introduced with
      Word 2007. Documents saved in the older binary `.doc` format will not preserve
      the flag. To support legacy formats, save the document as `.docx` and, if needed,
      convert it later using Aspose.Words’ `SaveFormat.Doc`.
  - name: What if I need to hide multiple shapes at once?
    text: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` on each shape that meets your criteria (e.g., a specific
      `ShapeType` or a custom `AlternativeText` value).
  - name: Is there a performance impact when hiding shapes?
    text: The hidden flag adds a tiny XML attribute; it does not affect rendering
      speed. However, a very large number of hidden objects can increase file size
      marginally. Remove shapes you never need to keep the document lean.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: إدراج شكل مستطيل في Word باستخدام C# – دليل كامل
url: /ar/net/programming-with-shapes/insert-rectangle-shape-in-word-with-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إدراج شكل مستطيل في Word باستخدام C# – دليل كامل

إذا كنت بحاجة إلى **إدراج شكل مستطيل** في مستند Word باستخدام C#، يوضح لك هذا الدليل الخطوات الدقيقة. ستتعلم أيضًا **كيفية إخفاء الشكل** بحيث لا يظهر في الملف النهائي، وهو ما يجيب على الاستفسار الشائع **إخفاء الشكل في Word** ويظهر كيفية **إنشاء شكل مخفي** برمجيًا.

يغطي البرنامج التعليمي كل شيء بدءًا من إعداد Aspose.Words SDK وحتى التحقق من أن الشكل مخفي. بنهاية المقال ستحصل على مقتطف شفرة قابل لإعادة الاستخدام يمكنك إدراجه في أي مشروع .NET.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

- .NET 6.0 أو أحدث مثبت (تعمل الشفرة أيضًا مع .NET Framework 4.6+)
- ترخيص صالح لـ Aspose.Words for .NET أو مفتاح تقييم مؤقت
- Visual Studio 2022 (أو أي بيئة تطوير تدعم C#)
- إلمام أساسي بصياغة C# وDocument Object Model (DOM) لملفات Word

لا توجد حزم NuGet إضافية مطلوبة بخلاف `Aspose.Words`.

## الخطوة 1: إنشاء مستند فارغ جديد وDocumentBuilder

العملية الأولى هي إنشاء كائن `Document`. يوفر `DocumentBuilder` واجهة برمجة تطبيقات مريحة لإدراج محتوى مثل الأشكال والفقرات والجداول.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document document = new Document();

// DocumentBuilder lets you add elements to the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

**لماذا هذا مهم:** يمثل `Document` الملف .docx بالكامل، بينما يحافظ `DocumentBuilder` على مؤشر يتتبع مكان وضع العنصر التالي. تهيئة كلا الكائنين هو الأساس لأي مهمة أتمتة Word.

## الخطوة 2: إدراج شكل مستطيل

الآن تقوم بإدراج المستطيل. تتطلب طريقة `InsertShape` نوع الشكل وأبعاده بالنقاط (1 نقطة ≈ 1/72 بوصة). حجم **200 × 100 نقطة** ينتج مستطيلًا تقريبًا 2.78 × 1.39 بوصة.

```csharp
// Insert a rectangle of 200x100 points.
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**لماذا هذا مهم:** كائن `Shape` الذي تحصل عليه قابل للتكوين بالكامل—يمكن تعديل اللون، والحدود، والنص، والظهور قبل حفظ المستند.

## الخطوة 3: إخفاء الشكل

لمنع عرض المستطيل أو طباعته، عيّن خاصية `Hidden` إلى `true`. هذه الخاصية تتطابق مباشرة مع سمة Word “Hidden”، التي يحترمها Word في كل من وضع العرض والطباعة.

```csharp
// Hide the shape so it never appears.
rectangle.Hidden = true;
```

**لماذا هذا مهم:** ضبط `Hidden` هو الطريقة القياسية لـ **إخفاء الشكل في Word** دون إزالته من بنية المستند. يبقى الشكل قابلًا للوصول عبر الشفرة، مما يتيح عمليات تعديل لاحقة مثل التنسيق الشرطي أو تبديل الظهور بناءً على البيانات.

## الخطوة 4: حفظ المستند

أخيرًا، احفظ المستند على القرص. اختر أي مجلد تفضله؛ المثال يستخدم مسارًا مؤقتًا يجب استبداله بمسار حقيقي.

```csharp
// Save the document with the hidden rectangle.
document.Save(@"C:\Temp\HiddenShape.docx");
```

**لماذا هذا مهم:** حفظ المستند ينهى الملف ويكتب علامة الإخفاء في Open XML الأساسي. عند فتح المستند في Microsoft Word، سيكون المستطيل غير مرئي، مما يؤكد أنك نجحت في **إنشاء شكل مخفي**.

## الخطوة 5: التحقق من الشكل المخفي

افتح ملف `HiddenShape.docx` الذي تم إنشاؤه في Microsoft Word:

1. انتقل إلى **ملف → خيارات → العرض** وتأكد من أن *“إظهار النص المخفي”* غير محدد.  
2. يجب ألا يكون المستطيل مرئيًا على أي صفحة.  
3. للتحقق مرة أخرى، فعّل *“إظهار النص المخفي”*؛ سيظهر المستطيل بخط منقط خفيف، مما يثبت وجود الشكل لكنه مخفي.

إذا ظل المستطيل مرئيًا، تحقق من أنك حفظت الملف بعد ضبط `Hidden = true` وأنك تفتح الملف الصحيح.

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه ولصقه وتشغيله مباشرة.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape of 200x100 points.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Step 3: Hide the shape so it does not appear when viewed or printed.
        rectangle.Hidden = true;

        // Step 4: Save the document with the hidden shape.
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
        Console.WriteLine("Open the file in Word to verify that the rectangle is hidden.");
    }
}
```

**الناتج المتوقع:** يطبع الطرفية مسار الملف وتذكيرًا قصيرًا. عند فتح الملف في Word، يكون المستطيل غير مرئي ما لم يتم تمكين النص المخفي.

## أسئلة شائعة وحالات خاصة

### هل يمكن إخفاء الحد فقط مع إبقاء التعبئة مرئية؟

نعم. بدلاً من ضبط `Hidden = true`، يمكنك تعيين `rectangle.LineFormat.Visible = false` لإخفاء الحدود مع الحفاظ على لون التعبئة. هذا يُعدّ تنويعًا لـ **كيفية إخفاء الشكل** مع الحفاظ على جزء من المظهر البصري.

### هل تعمل علامة الإخفاء في إصدارات Word القديمة (2003، 2007)؟

سمة الإخفاء هي جزء من مواصفة Open XML التي تم تقديمها مع Word 2007. المستندات المحفوظة بصيغة `.doc` الثنائية القديمة لن تحتفظ بهذه العلامة. لدعم الصيغ القديمة، احفظ المستند كـ `.docx`، وإذا لزم الأمر، حوّله لاحقًا باستخدام `SaveFormat.Doc` في Aspose.Words.

### ماذا لو أردت إخفاء عدة أشكال في آن واحد؟

قم بالتكرار عبر مجموعة `Document.GetChildNodes(NodeType.Shape, true)` واضبط `Hidden = true` على كل شكل يطابق معاييرك (مثل نوع `ShapeType` معين أو قيمة `AlternativeText` مخصصة).

```csharp
foreach (Shape shp in document.GetChildNodes(NodeType.Shape, true))
{
    if (shp.AlternativeText == "HideMe")
        shp.Hidden = true;
}
```

### هل هناك تأثير على الأداء عند إخفاء الأشكال؟

علامة الإخفاء تضيف سمة XML صغيرة؛ لا تؤثر على سرعة العرض. ومع ذلك، قد يزيد عدد كبير جدًا من الكائنات المخفية من حجم الملف بشكل طفيف. احذف الأشكال التي لا تحتاجها للحفاظ على خفة المستند.

## نصائح وممارسات أفضل

- **امنح الشكل اسمًا ذا معنى** باستخدام `rectangle.Name = "MyHiddenRectangle"`؛ يساعد ذلك عند البحث عن الشكل لاحقًا في الـ DOM.  
- **عيّن `AlternativeText`** إلى علامة مخصصة (مثل `"HiddenShape"`). يتيح لك ذلك تحديد الشكل دون الاعتماد على فهرسته.  
- **غلف الشفرة بكتلة try‑catch** للتعامل مع أخطاء الترخيص أو استثناءات الإدخال/الإخراج بشكل سلس.  
- **حرّر الـ Document** بعد الحفظ إذا كنت تعالج ملفات متعددة في حلقة لتفريغ الموارد غير المدارة: `document.Dispose();`.

## الخلاصة

أنت الآن تعرف كيف **تدخل شكل مستطيل** في مستند Word باستخدام C#، وكيف **تخفي الشكل في Word**، وكيف **تنشئ شكلًا مخفيًا** يبقى جزءًا من بنية المستند لكنه غير مرئي للمستخدمين النهائيين. المثال الكامل القابل للتنفيذ يوضح سير العمل بالكامل، من إنشاء المستند إلى التحقق.

بعد ذلك، يمكنك استكشاف **كيفية إخفاء الشكل** بناءً على مدخلات المستخدم، أو دمج الأشكال المخفية مع عناصر التحكم بالمحتوى لإنشاء مستندات ديناميكية. يمكنك أيضًا تطبيق التقنية نفسها على أنواع أخرى من الأشكال مثل الإهليلجات، والأسهم، أو الرسومات المخصصة.

لا تتردد في تجربة أبعاد، ألوان، وإعدادات رؤية مختلفة. إذا واجهت أي مشاكل، راجع الخطوات أعلاه أو استشر وثائق Aspose.Words للحصول على تفاصيل أعمق حول الـ API. برمجة سعيدة!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}