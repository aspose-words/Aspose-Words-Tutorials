---
category: general
date: 2026-10-10
description: تعيين نص الزر وإضافة زر ActiveX في C# باستخدام Aspose.Words. تعلّم كيفية
  إدراج زر، إنشاء عنصر تحكم زر، وتخصيص التسمية في مستند Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button text
- how to insert button
- create button control
- add activex control
- add activex button
language: ar
lastmod: 2026-10-10
og_description: تعيين نص الزر وإضافة زر ActiveX في C# باستخدام Aspose.Words. اتبع
  هذا الدليل خطوة بخطوة لإدراج زر، وإنشاء عنصر تحكم الزر، وتخصيص تسميته.
og_image_alt: Screenshot of a Word document showing an ActiveX button with custom
  text
og_title: تعيين نص الزر وإضافة زر ActiveX في C# – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Set button text and add an ActiveX button in C# using Aspose.Words.
    Learn how to insert button, create button control, and customize the caption in
    a Word document.
  headline: Set button text and add an ActiveX button in C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- button control
- document automation
title: تعيين نص الزر وإضافة زر ActiveX في C#
url: /ar/java/document-manipulation/set-button-text-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تعيين نص الزر وإضافة زر ActiveX في C#

إذا كنت بحاجة إلى **تعيين نص الزر** على زر ActiveX داخل مستند Word، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك. في نهاية البرنامج التعليمي ستتمكن من **إدراج زر**، وإنشاء **عنصر تحكم زر**، وتخصيص التسمية الخاصة به ببضع أسطر فقط من كود C#.

العمل مع عناصر تحكم ActiveX شائع عندما تريد نماذج تفاعلية في Word—سواء كنت تبني قالب عقد، أو استبيان، أو أداة داخلية. يستخدم المثال Aspose.Words for .NET، وهي مكتبة تتيح لك التعامل مع ملفات Word دون الحاجة إلى تثبيت Microsoft Office.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* .NET 6.0 SDK أو أحدث مثبت  
* Visual Studio 2022 (أو أي بيئة تطوير تدعم C#)  
* ترخيص Aspose.Words for .NET (التقييم المجاني يكفي للتعلم)  

كما تحتاج إلى إشارة إلى حزمة NuGet `Aspose.Words`:

```bash
dotnet add package Aspose.Words
```

## كيفية إدراج زر في مستند Word

الخطوة الأولى هي إنشاء كائن `Document` جديد و`DocumentBuilder`. الـ builder هو نقطة الدخول لإضافة المحتوى، بما في ذلك عناصر تحكم ActiveX.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**لماذا هذا مهم:** يمثل `Document` الملف .docx بالكامل، بينما يوفر `DocumentBuilder` طرقًا عالية المستوى مثل `InsertParagraph` و`InsertFormField`. بدءًا من مستند نظيف يضمن ظهور الزر في المكان الذي تريده بالضبط.

## إنشاء عنصر تحكم زر باستخدام Forms2OleControl

الآن نقوم بإنشاء عنصر التحكم الفعلي للزر. `Forms2OleControl` هو الصنف الذي يستخدمه Aspose.Words لجميع كائنات ActiveX، ونوع `COMMANDBUTTON` يُظهر زرًا قابلًا للنقر في Word.

```csharp
        // Step 2: Insert a Forms2OleControl of type COMMANDBUTTON
        Forms2OleControl button = builder.InsertForms2OleControl(
            Forms2OleControlType.COMMANDBUTTON, // control type
            100,  // left position (points)
            50,   // top position (points)
            200,  // width (points)
            150); // height (points)
```

**شرح:**  
* `InsertForms2OleControl` يضع العنصر في الإحداثيات الدقيقة التي تحددها.  
* الحجم يُعرّف بالنقاط (1 نقطة = 1/72 بوصة). عدّل هذه القيم لتناسب تخطيطك.

## إضافة عنصر تحكم ActiveX وإعطائه اسمًا فريدًا

كل كائن ActiveX يجب أن يمتلك اسمًا مميزًا حتى تتمكن من الإشارة إليه لاحقًا (مثلاً عند معالجة الأحداث في VBA).

```csharp
        // Step 3: Assign a unique name to the control
        button.SetName("MyActiveXButton");
```

**نصيحة:** تجنّب المسافات أو الأحرف الخاصة في الاسم؛ Word يتعامل مع الاسم كمعرف في نموذج النموذج الداخلي.

## تعيين نص الزر (التسمية) على زر ActiveX

هنا يأتي دور الكلمة المفتاحية الأساسية **تعيين نص الزر**. خاصية `Caption` تحدد التسمية التي يراها المستخدمون على الزر.

```csharp
        // Step 4: Set the text that appears on the button
        button.SetCaption("Click Me");
```

يمكنك تغيير التسمية في أي وقت قبل حفظ المستند. إذا احتجت لاحقًا إلى تعريب الواجهة، ما عليك سوى استدعاء `SetCaption` مرة أخرى بسلسلة نصية مختلفة.

## حفظ المستند والتحقق من النتيجة

أخيرًا، اكتب المستند إلى القرص. فتح الملف في Microsoft Word سيظهر الزر مع التسمية المخصصة.

```csharp
        // Step 5: Save the document
        doc.Save("ActiveXButton.docx");
        System.Console.WriteLine("Document created with an ActiveX button.");
    }
}
```

**الناتج المتوقع:** عند فتح *ActiveXButton.docx* في Word، سترى زرًا موضعًا عند الإحداثيات المحددة، مُسمّى **Click Me**. النقر على الزر سيُفعّل سلوك زر الأمر الافتراضي في Word (يمكنك تخصيصه لاحقًا باستخدام VBA).

![Set button text example](https://example.com/activex-button.png){alt="مثال على تعيين نص الزر"}

## إضافة زر ActiveX ومعالجة الأحداث (اختياري)

إذا كنت تريد أن يقوم الزر بتنفيذ إجراء مخصص، يمكنك إضافة ماكرو VBA يتفاعل مع حدث `Click`. يمكن حقن الماكرو برمجيًا، لكن ذلك خارج نطاق هذا الدرس. الجزء المهم هو أن الزر موجود بالفعل وتسميةه مُحددة—جاهزة لأي معالجة أحداث تختارها.

## المشكلات الشائعة وكيفية تجنّبها

| المشكلة | سبب حدوثها | الحل |
|-------|----------------|-----|
| الزر يظهر غير محاذٍ | الإحداثيات بوحدات النقاط، ليست بالبكسل | تحويل قيم البكسل إلى نقاط (`points = pixels * 72 / DPI`) |
| التسمية لا تتغيّر بعد الحفظ | تم استدعاء `SetCaption` بعد `Save` | دائمًا عيّن التسمية **قبل** استدعاء `doc.Save` |
| العنصر غير مرئي في إصدارات Word القديمة | بعض إصدارات Word القديمة لا تدعم ActiveX بالكامل | اختبر على نسخة Word المستهدفة؛ فكر في استخدام `CheckBox` أو `DropDownList` كبديل |
| تحذير الترخيص في الناتج | انتهاء صلاحية ترخيص التقييم | تطبيق ترخيص Aspose.Words صالح عبر `License license = new License(); license.SetLicense("Aspose.Words.lic");` |

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه، لصقه، وتشغيله. يتضمن جميع توجيهات `using` الضرورية ويظهر سير العمل بالكامل من إنشاء المستند إلى حفظه.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert an ActiveX command button at a specific location
            Forms2OleControl button = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON,
                100,   // left (points)
                50,    // top (points)
                200,   // width (points)
                150);  // height (points)

            // Give the button a unique identifier
            button.SetName("MyActiveXButton");

            // Set the visible text on the button (set button text)
            button.SetCaption("Click Me");

            // Save the document
            const string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}. Open it in Word to see the button.");
        }
    }
}
```

شغّل البرنامج باستخدام `dotnet run`. بعد التنفيذ، افتح *ActiveXButton.docx* لتتأكد من أن تسمية الزر هي **Click Me**.

## ملخص ما تعلمته

* تعلمت كيف **تعيّن نص الزر** على زر ActiveX باستخدام Aspose.Words.  
* رأيت الخطوات الدقيقة لـ **إدراج زر**، **إنشاء عنصر تحكم زر**، و**إضافة عنصر تحكم ActiveX** إلى مستند Word.  
* لديك الآن مقطع كود قابل لإعادة الاستخدام يمكنك تعديله لأي مشروع أتمتة Word يعتمد على النماذج.

## الخطوات التالية

* استكشف قيم `Forms2OleControlType` الأخرى مثل `CHECKBOX` أو `LISTBOX` لبناء نماذج أكثر غنى.  
* اجمع الزر مع ماكرو VBA لتنفيذ حسابات أو التحقق من البيانات.  
* استخدم API `FormField` في Aspose.Words لقراءة مدخلات المستخدم بعد ملء المستند.

لا تتردد في تجربة الحجم، الموضع، والتسمية لتتناسب مع متطلبات التصميم الخاصة بك. إذا واجهت أي مشاكل، توفر وثائق Aspose.Words مراجع مفصلة لكل صنف يُستخدم في هذا الدرس.

Happy coding!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مستند Word فارغ باستخدام Aspose.Words – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [إضافة ظل إلى الشكل في Word باستخدام Aspose.Words – خطوة بخطوة](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)
- [إضافة أرقام صفحات إلى تذييل مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}