---
category: general
date: 2026-08-14
description: كيفية إضافة زر ActiveX في مستند Word باستخدام Aspose.Words – تعلم إنشاء
  مستند Word فارغ وإدراج زر ActiveX برمجيًا.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert activex button
- create empty word document
- create word document aspose
language: ar
lastmod: 2026-08-14
og_description: كيفية إضافة زر ActiveX في مستند Word باستخدام Aspose.Words. يوضح لك
  هذا البرنامج التعليمي كيفية إنشاء مستند Word فارغ، وإدراج زر ActiveX، وحفظ النتيجة.
og_image_alt: Screenshot of an ActiveX button inserted into a Word document using
  Aspose.Words
og_title: كيفية إضافة زر ActiveX في Word – دليل Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  headline: How to add ActiveX button in a Word document with Aspose.Words
  type: TechArticle
- description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  name: How to add ActiveX button in a Word document with Aspose.Words
  steps:
  - name: Does the button work in all Word versions?
    text: ActiveX controls are supported in the desktop version of Word on Windows.
      They are not rendered in Word Online, Word for macOS, or mobile clients. If
      you need cross‑platform interactivity, consider using content controls or HTML‑based
      solutions instead.
  - name: What if I need a different size or position?
    text: '`InsertForms2OleControl` places the control at the current builder cursor.
      To move it, adjust the cursor with `builder.MoveTo` before insertion, or modify
      the control’s `Left` and `Top` properties after creation:'
  - name: Can I add other ActiveX types?
    text: Yes. The `Forms2OleControlType` enumeration includes `CheckBox`, `OptionButton`,
      `ListBox`, and more. Replace `CommandButton` with the desired enum value and
      adjust properties accordingly.
  - name: Is a macro required for the button to do something?
    text: The button itself does nothing until you attach VBA code. In Word, press
      **Alt+F11** to open the VBA editor, locate `btnSubmit_Click`, and write the
      desired logic. The generated document will retain the VBA project if you enable
      the **SaveFormat.Doc** (legacy `.doc`) format, but `.docx` files cannot
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Word automation
- C#
title: كيفية إضافة زر ActiveX في مستند Word باستخدام Aspose.Words
url: /ar/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إضافة زر ActiveX في مستند Word باستخدام Aspose.Words

إذا كنت بحاجة إلى **how to add ActiveX** للتحكم في ملف Word تم إنشاؤه، يوضح لك هذا الدليل الخطوات الدقيقة. ستتعلم **insert ActiveX button** برمجيًا، بدءًا من **create empty Word document** وانتهاءً بملف محفوظ يمكن فتحه في Microsoft Word.

إضافة زر يقوم بتشغيل كود VBA أو تشغيل ماكرو هو طلب شائع لمولدات التقارير الآلية، قوالب النماذج، أو العقود التفاعلية. يسمح لك استخدام Aspose.Words for .NET بإنشاء المستند دون تشغيل Office، مما يجعل العملية سريعة وصديقة للخادم.

## المتطلبات المسبقة

* .NET 6.0 (أو أحدث) SDK مثبت.
* Visual Studio 2022 أو أي بيئة تطوير متوافقة مع C#.
* حزمة NuGet الخاصة بـ Aspose.Words for .NET (`Aspose.Words` الإصدار 24.9 أو أحدث).  
  قم بتثبيتها باستخدام:
  ```bash
  dotnet add package Aspose.Words
  ```
* بيئة Windows إذا كنت تخطط لاختبار زر ActiveX، لأن عناصر التحكم ActiveX تتطلب نسخة Windows من Microsoft Word.

## الخطوة 1: إنشاء مستند Word فارغ

المهمة الأولى هي **create empty Word document** في الذاكرة. توفر Aspose.Words الفئة `Document` لهذا الغرض.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, blank Word document.
Document doc = new Document();
```

`Document` تمثل ملف .docx بالكامل. في هذه المرحلة لا يحتوي المستند على صفحات، ولكن يمكنك البدء في إضافة المحتوى فورًا.

## الخطوة 2: تهيئة DocumentBuilder

`DocumentBuilder` هي أداة مساعدة تتيح لك إدراج النصوص، الصور، وغيرها من الكائنات في المستند. تعمل على نسخة `Document` التي أنشأتها للتو.

```csharp
// Initialise the builder with the blank document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

يحافظ الـ builder على موضع المؤشر؛ أي شيء تقوم بإدراجه بعد هذا السطر سيظهر في بداية الصفحة الأولى.

## الخطوة 3: إدراج عنصر تحكم ActiveX CommandButton

تُظهر Aspose.Words طريقة `InsertForms2OleControl` لإضافة عناصر التحكم النماذج القديمة، بما في ذلك ActiveX. تتطلب الطريقة نوع العنصر وحجمه بالنقاط.

```csharp
// Insert an ActiveX CommandButton (150x30 points).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

الكائن `Forms2OleControl` المرتجع يتيح لك ضبط الخصائص مثل اسم العنصر وعنوانه.

## الخطوة 4: ضبط خصائص الزر

تعيين `Name` ذو معنى يتيح لك الإشارة إلى العنصر من كود VBA لاحقًا. الـ `Caption` هو النص الذي يراه المستخدم على الزر.

```csharp
// Set the button’s programmatic name (used in VBA) and displayed caption.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

> **نصيحة احترافية:** احتفظ بالاسم قصيرًا وألفبائيًا رقميًا؛ سيقوم Word برفض الأسماء التي تحتوي على مسافات أو أحرف خاصة.

## الخطوة 5: حفظ المستند

أخيرًا، احفظ المستند على القرص. استخدم امتداد `.docx` لملفات Word الحديثة؛ يعمل زر ActiveX بنفس الطريقة في ملفات `.doc`، لكن `.docx` هو التنسيق المفضل للمشروعات الجديدة.

```csharp
// Save the document containing the ActiveX button.
doc.Save(@"C:\Temp\ActiveXButton.docx");
```

عند فتح `ActiveXButton.docx` في Microsoft Word، سترى زر **Submit** قابل للنقر. إذا قمت بتمكين الماكرو، يمكنك إرفاق كود VBA إلى `btnSubmit_Click` وجعله ينفذ عندما ينقر المستخدم على الزر.

## مثال كامل قابل للتنفيذ

جمع كل الأجزاء معًا يمنحك برنامجًا مستقلًا يمكنك نسخه، لصقه، وتشغيله.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create an empty Word document.
            Document doc = new Document();

            // Step 2: Initialise DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX CommandButton control.
            Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Step 4: Set button properties.
            cmdBtn.Name = "btnSubmit";
            cmdBtn.Caption = "Submit";

            // Step 5: Save the document.
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**الناتج المتوقع** – بعد تشغيل البرنامج، يطبع الطرفية موقع الحفظ، وعند فتح الملف المُولد في Word يظهر زر بعنوان **Submit** موضعه في أعلى الصفحة الأولى.

## معالجة الأسئلة الشائعة والحالات الخاصة

### هل يعمل الزر في جميع إصدارات Word؟

تُدعم عناصر التحكم ActiveX في نسخة سطح المكتب من Word على Windows. لا يتم عرضها في Word Online، Word لنظام macOS، أو العملاء المحمولين. إذا كنت بحاجة إلى تفاعل عبر المنصات، فكر في استخدام عناصر التحكم بالمحتوى أو حلول تعتمد على HTML بدلاً من ذلك.

### ماذا لو احتجت إلى حجم أو موضع مختلف؟

`InsertForms2OleControl` يضع العنصر عند موضع المؤشر الحالي للـ builder. لتحريكه، عدل المؤشر باستخدام `builder.MoveTo` قبل الإدراج، أو غيّر خصائص `Left` و `Top` للعنصر بعد الإنشاء:

```csharp
cmdBtn.Left = 100;   // points from the left margin
cmdBtn.Top = 200;    // points from the top margin
```

### هل يمكنني إضافة أنواع أخرى من ActiveX؟

نعم. تشمل تعداد `Forms2OleControlType` القيم `CheckBox`، `OptionButton`، `ListBox`، وأكثر. استبدل `CommandButton` بالقيمة المطلوبة من التعداد واضبط الخصائص وفقًا لذلك.

### هل الماكرو مطلوب لجعل الزر يقوم بشيء؟

الزر نفسه لا يفعل شيئًا حتى تقوم بإرفاق كود VBA. في Word، اضغط **Alt+F11** لفتح محرر VBA، ابحث عن `btnSubmit_Click`، واكتب المنطق المطلوب. سيحتفظ المستند المُولد بمشروع VBA إذا قمت بتمكين تنسيق **SaveFormat.Doc** (الـ `.doc` القديم)، لكن ملفات `.docx` لا يمكنها تخزين ماكرو VBA. استخدم تنسيق `.doc` إذا كنت بحاجة إلى VBA مدمج.

## الخلاصة

أنت الآن تعرف **how to add ActiveX** إلى ملفات Word باستخدام Aspose.Words. باتباع الخطوات لإنشاء **create empty Word document**، تهيئة `DocumentBuilder`، **insert ActiveX button**، ضبط خصائصه، وحفظ الملف، يمكنك إنشاء قوالب Word تفاعلية مباشرة من كود .NET الخاص بك.

بعد ذلك، استكشف المواضيع ذات الصلة مثل معالجة أحداث **insert ActiveX button**، إضافة **create word document aspose** للجداول أو الصور، وتأمين المستندات المُمكّنة للماكرو للنشر المؤسسي. جرب أنواعًا مختلفة من عناصر التحكم وخيارات التخطيط لتخصيص تجربة المستخدم وفقًا لاحتياجات تطبيقك.

برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مستند Word مع رأس وتذييل باستخدام Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [إنشاء شكل مجموعة في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [إنشاء مستند Word مع جدول باستخدام Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}