---
category: general
date: 2026-11-18
description: إنشاء مستند Word فارغ وإدراج زر ActiveX باستخدام C#. تعلم كيفية إضافة
  التحكم، تعيين تسمية الزر، وحفظ الملف.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- how to add control
- insert activex button
- set button caption
language: ar
lastmod: 2026-11-18
og_description: أنشئ مستند Word فارغًا وأدرج زر ActiveX باستخدام C#. اتبع هذا الدرس
  الكامل لإضافة التحكم، وتعيين تسمية الزر، وحفظ النتيجة.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX button with
  the caption “Press”
og_title: إنشاء مستند Word فارغ وإدراج زر ActiveX – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  headline: Create a blank Word document and insert an ActiveX button
  type: TechArticle
- description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  name: Create a blank Word document and insert an ActiveX button
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET installed (`Install-Package Aspose.Words`). * Basic familiarity with
      C# and Visual Studio or any .NET‑compatible IDE.'
  - name: Tip
    text: 'If you need the button to appear on a specific page, move the builder’s
      cursor first:'
  - name: Expected result
    text: Opening `with_button.docx` in Word shows a blank page with a rectangular
      button labeled **Press**. Clicking the button does nothing by default because
      no VBA macro is attached, but the control is fully functional and can be wired
      to code later.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: إنشاء مستند Word فارغ وإدراج زر ActiveX
url: /ar/net/working-with-oleobjects-and-activex/create-a-blank-word-document-and-insert-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word فارغ وإدراج زر ActiveX

إذا كنت بحاجة إلى **إنشاء مستند Word فارغ** ووضع زر ActiveX تفاعلي بداخله، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك باستخدام Aspose.Words for .NET. سترى الكود الكامل، وتفهم لماذا كل سطر مهم، وتتعلم كيفية **تعيين تسمية الزر** بحيث يبدو التحكم جاهزًا لتفاعل المستخدم.

بالإضافة إلى الهدف الأساسي، سنغطي **كيفية إدراج ActiveX**، الخطوات **كيفية إضافة عنصر تحكم** إلى ملف Word، وتفاصيل **إدراج زر ActiveX** مع تسمية مخصصة. في النهاية ستحصل على نمط قابل لإعادة الاستخدام لأي سيناريو أتمتة مستند يتطلب عناصر واجهة مستخدم مدمجة.

## ما ستتعلمه

* كيفية **إنشاء مستند Word فارغ** برمجيًا.  
* استدعاءات API الدقيقة المطلوبة **لإدراج زر ActiveX** وتكوين خصائصه.  
* كيفية **تعيين تسمية الزر** بحيث يعرض التحكم النص المطلوب.  
* نصائح لحفظ الملف في الموقع الذي تختاره ومعالجة المشكلات الشائعة.

### المتطلبات المسبقة

* .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.6+).  
* Aspose.Words for .NET مثبت (`Install-Package Aspose.Words`).  
* إلمام أساسي بـ C# و Visual Studio أو أي بيئة تطوير متوافقة مع .NET.

---

## إنشاء مستند Word فارغ باستخدام Aspose.Words

الخطوة الأولى هي إنشاء كائن `Document` فارغ. هذا الكائن يمثل ملف Word لا يحتوي على أي محتوى حتى نضيف شيئًا.

```csharp
// Step 1: Create a new blank document
Document document = new Document();
```

*لماذا هذا مهم*: `Document` الفارغ يمنحك لوحة رسم نظيفة. يمكنك لاحقًا إضافة فقرات أو جداول أو عناصر تحكم دون القلق بشأن التنسيق الموجود.

---

## تهيئة DocumentBuilder للعمل مع المستند

`DocumentBuilder` هو فئة مساعدة تتيح لك إدراج محتوى في موضع المؤشر الحالي. تتعقب تلقائيًا موقعك في المستند.

```csharp
// Step 2: Initialise a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

*لماذا هذا مهم*: بدون `DocumentBuilder` ستحتاج إلى تعديل شجرة العقد منخفضة المستوى يدويًا. يبسط الـ builder إدراج النصوص والصور وعناصر تحكم ActiveX.

---

## كيفية إدراج زر ActiveX (insert activex button)

الآن نستخدم `InsertForms2OleControl` لتضمين عنصر تحكم ActiveX. تتطلب الطريقة ثلاثة معلمات:

1. نوع عنصر التحكم (`OleControlType.CommandButton`).  
2. اسم داخلي لعنصر التحكم (يستخدمه VBA أو كود الماكرو).  
3. `RectangleF` يحدد الموقع والحجم على الصفحة.

```csharp
// Step 3: Insert a CommandButton ActiveX control at the current cursor position
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,          // type of control
    "ClickMe",                             // internal name (identifier)
    new System.Drawing.RectangleF(0, 0, 100, 30)); // x, y, width, height
```

*لماذا هذا مهم*: هذا هو جوهر **كيفية إدراج activex** في مستند Word. إحداثيات المستطيل تُعبّر عنها بالنقاط (نقطة واحدة = 1/72 بوصة). اضبطها لتحديد موضع الزر حيث تحتاجه.

### نصيحة

إذا كنت بحاجة إلى ظهور الزر في صفحة محددة، حرك مؤشر الـ builder أولاً:

```csharp
builder.MoveToSection(0);  // moves to the first (and only) section
builder.InsertParagraph(); // ensures there is a paragraph to host the control
```

---

## كيفية تعيين تسمية الزر (set button caption)

بعد وضع عنصر التحكم، يمكنك تعديل خصائصه. الخاصية الأكثر وضوحًا هي `Caption`، التي تحدد النص المعروض على الزر.

```csharp
// Step 4: Set the visible caption of the button
commandButton.Caption = "Press";
```

*لماذا هذا مهم*: المستخدمون يرون التسمية، وليس الاسم الداخلي. تغييرها يجعل الزر ذو معنى في المستند النهائي.

---

## حفظ المستند الذي يحتوي على الزر

أخيرًا، احفظ المستند على القرص. يمكنك اختيار أي تنسيق مدعوم (`.docx`, `.pdf`, إلخ). هنا نحفظه كمستند Word.

```csharp
// Step 5: Save the document with the ActiveX button
string outputPath = @"C:\Temp\with_button.docx";
document.Save(outputPath);
```

*لماذا هذا مهم*: حفظ الملف يسمح لك بفتحه في Microsoft Word واختبار الزر. عندما يُفتح المستند، سيظهر الزر مع التسمية “Press”.

### النتيجة المتوقعة

فتح `with_button.docx` في Word يظهر صفحة فارغة مع زر مستطيل يحمل التسمية **Press**. النقر على الزر لا يفعل شيئًا بشكل افتراضي لأن لا ماكرو VBA مرفق، لكن عنصر التحكم يعمل بالكامل ويمكن ربطه بالكود لاحقًا.

---

## كيفية إضافة عنصر تحكم إلى فقرة محددة (how to add control)

أحيانًا تريد الزر داخل فقرة معينة، على سبيل المثال بعد نص إرشادي. استخدم `MoveTo` لتحديد موضع الـ builder قبل إدراج عنصر التحكم.

```csharp
// Example: add a paragraph, then insert the button after it
builder.Writeln("Click the button below to continue:");
builder.InsertParagraph(); // creates a new empty paragraph
builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    "ContinueBtn",
    new System.Drawing.RectangleF(0, 0, 120, 35));
```

*لماذا هذا مهم*: هذا النمط يوضح **كيفية إضافة عنصر تحكم** في السياق، مما يضمن بقاء تخطيط المستند منطقيًا.

---

## المشكلات الشائعة وكيفية تجنبها

| المشكلة | سبب حدوثه | الحل |
|-------|----------------|-----|
| ظهر الزر خارج الصفحة | إحداثيات المستطيل خارج هوامش الصفحة | استخدم `builder.PageSetup` للحصول على أبعاد الصفحة وحساب `RectangleF` آمن. |
| التسمية لا تظهر | `Caption` تم تعيينه قبل أن يتم تهيئة عنصر التحكم بالكامل | قم بتعيين `Caption` **بعد** استدعاء `InsertForms2OleControl`، كما هو موضح في الخطوة 4. |
| المستند يُحفظ بدون الزر | تم تحريك مؤشر الـ builder بعد الإدراج دون حفظ التغييرات | احتفظ بالـ builder على نفس الصفحة أو استدعِ `builder.Document.UpdatePageLayout()` قبل الحفظ. |

---

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه ولصقه وتشغيله. ينشئ ملف Word فارغ، يُدرج زر ActiveX، يحدد تسميته، ويحفظ النتيجة.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Initialise DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // Optional: add some explanatory text
        builder.Writeln("Below is an ActiveX button created programmatically:");
        builder.InsertParagraph();

        // 3️⃣ Insert the ActiveX CommandButton
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "MyButton",
            new RectangleF(0, 0, 100, 30));

        // 4️⃣ Set the button caption
        commandButton.Caption = "Press";

        // 5️⃣ Save the document
        string outputPath = @"C:\Temp\with_button.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**الناتج**: بعد تشغيل البرنامج، افتح `C:\Temp\with_button.docx` في Microsoft Word. سترى صفحة واحدة تحتوي على النص “Below is an ActiveX button created programmatically:” متبوعًا بزر يحمل التسمية **Press**.

---

## الخلاصة

أنت الآن تعرف كيفية **إنشاء مستند Word فارغ**، **إدراج زر ActiveX**، **تعيين تسمية الزر**، و**حفظ** النتيجة باستخدام Aspose.Words for .NET. يمكن توسيع النمط نفسه إلى عناصر تحكم ActiveX أخرى (مربعات اختيار، قوائم، إلخ) عن طريق تغيير `OleControlType`.

بعد ذلك، قد تستكشف **كيفية إدراج أحداث زر ActiveX** باستخدام VBA، أو **كيفية إضافة عنصر تحكم** إلى مستندات موجودة تحتوي بالفعل على محتوى. كلا الموضوعين يبنيان مباشرةً على المفاهيم التي تم تغطيتها هنا.

برمجة سعيدة، ولا تتردد في تجربة أحجام ومواقع وتسمية مختلفة لتتناسب مع متطلبات واجهة المستخدم لتطبيقك!

---

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء مستند Word باستخدام C# مع زر أمر ActiveX](/words/english/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/)
- [كيفية إضافة زر ActiveX في مستند Word باستخدام Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}