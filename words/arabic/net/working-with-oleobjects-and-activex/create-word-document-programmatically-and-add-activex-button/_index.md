---
category: general
date: 2026-08-10
description: إنشاء مستند Word برمجيًا باستخدام Aspose.Words، ثم إضافة زر تحكم ActiveX.
  إدراج زر أمر ActiveX في دقائق.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add activex control word
- insert activex command button
language: ar
lastmod: 2026-08-10
og_description: إنشاء مستند Word برمجيًا باستخدام Aspose.Words، ثم إضافة زر كلمة تحكم
  ActiveX. تعلّم كيفية إدراج زر أمر ActiveX بسرعة.
og_image_alt: Screenshot of a Word document created programmatically with an ActiveX
  command button
og_title: إنشاء مستند Word برمجيًا – إضافة زر ActiveX في C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  headline: Create word document programmatically and add ActiveX button
  type: TechArticle
- description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  name: Create word document programmatically and add ActiveX button
  steps:
  - name: Open `ActiveX_CommandButton.docx` in Microsoft Word.
    text: Open `ActiveX_CommandButton.docx` in Microsoft Word.
  - name: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
    text: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
  - name: Click **Design Mode**. The button should appear with the label “Submit”.
    text: Click **Design Mode**. The button should appear with the label “Submit”.
  - name: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
    text: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- C#
title: إنشاء مستند Word برمجيًا وإضافة زر ActiveX
url: /ar/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word برمجيًا وإضافة زر ActiveX

إذا كنت بحاجة إلى **إنشاء مستند Word برمجيًا**، فإن هذا الدليل يشرح لك العملية بالكامل باستخدام Aspose.Words for .NET. ستتعلم أيضًا كيفية **إضافة عناصر تحكم activex في Word** و**إدراج كائنات زر أمر activex** في مثال واحد متكامل.

إنشاء ملفات Word من خلال الكود يلغي الحاجة إلى فتح Microsoft Word يدويًا، مما يتيح لك إنشاء تقارير، فواتير، أو عقود مدفوعة بالبيانات تلقائيًا. بنهاية هذا الدليل ستحصل على تطبيق C# Console جاهز للتنفيذ ينتج ملف `.docx` يحتوي على زر ActiveX CommandButton تفاعلي.

## المتطلبات المسبقة

* .NET 6.0 SDK أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.6+)
* Visual Studio 2022 أو أي بيئة تطوير تدعم .NET
* ترخيص صالح لـ Aspose.Words for .NET (يمكنك استخدام مفتاح التقييم المجاني للاختبار)
* إلمام أساسي بصياغة C# ومفهوم تحكمات COM/ActiveX

> **نصيحة احترافية:** إذا كنت تخطط لتوزيع المستند المُنشأ على مستخدمين لا يمتلكون Word مثبتًا، قم بدمج ملفات تشغيل تحكم ActiveX جنبًا إلى جنب مع ملف `.docx` أو قدّم قالبًا يدعم الماكرو.

## إنشاء مستند Word برمجيًا – الإعداد الأولي

أولاً، أضف حزمة Aspose.Words NuGet إلى مشروعك:

```bash
dotnet add package Aspose.Words
```

ثم أنشئ مشروع Console جديد (إذا لم يكن لديك مشروع بالفعل):

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
```

افتح ملف `Program.cs` الذي تم إنشاؤه – سنستبدل محتوياته بالحل الكامل أدناه.

## الخطوة 1: استيراد المساحات الاسمية وتكوين الترخيص

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // OPTIONAL: Apply your Aspose.Words license to remove evaluation watermarks.
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");
```

*لماذا هذا مهم*: استيراد `Aspose.Words.Drawing` يمنحك الوصول إلى `Forms2OleControl`، الفئة التي تمثل تحكم ActiveX داخل مستند Word. ضبط الترخيص مبكرًا يمنع تحذيرات وقت التشغيل في بيئة الإنتاج.

## الخطوة 2: إنشاء مستند فارغ وDocumentBuilder

```csharp
            // Create a new empty Word document.
            Document doc = new Document();

            // DocumentBuilder provides a convenient API for inserting text, tables, and controls.
            DocumentBuilder builder = new DocumentBuilder(doc);
```

كائن `Document` هو تمثيل الذاكرة الداخلية لملف `.docx`. يعمل `DocumentBuilder` كالمؤشر الذي تتحرك به داخل المستند لإدراج العناصر.

## الخطوة 3: إدراج تحكم ActiveX CommandButton

```csharp
            // Insert an ActiveX CommandButton.
            // Parameters: control type, width, height, left position, top position (all in points).
            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, // ActiveX type
                100,   // Width in points
                50,    // Height in points
                150,   // Left offset from the page margin
                200);  // Top offset from the page margin
```

`InsertForms2OleControl` ينشئ كائن OLE يتعامل معه Word كتحكم ActiveX. يستخدم نظام الإحداثيات النقاط (نقطة واحدة = 1/72 بوصة)، وهو ما يتطابق مع محرك تخطيط Word.

## الخطوة 4: تعيين تسمية الزر والخصائص الاختيارية

```csharp
            // Set the text that appears on the button.
            commandBtn.Caption = "Submit";

            // Optional: assign a macro name that Word will call when the button is clicked.
            // commandBtn.OnAction = "MyMacroName";
```

تعيين خاصية `Caption` هو الطريقة الأكثر شيوعًا لتسمية الزر. إذا كنت بحاجة إلى أن ينفذ الزر ماكرو VBA، عيّن اسم الماكرو إلى `OnAction`. يركز هذا الدليل على الجزء البصري؛ تغطية دمج الماكرو موجودة في قسم “الخطوات التالية”.

## الخطوة 5: حفظ المستند

```csharp
            // Define the output path – change this to a folder that exists on your machine.
            string outputPath = @"ActiveX_CommandButton.docx";

            // Save the document with the embedded ActiveX control.
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

عند تشغيل البرنامج، سترى رسالة في وحدة التحكم تؤكد أن ملف `ActiveX_CommandButton.docx` قد تم كتابته على القرص.

### الكود الكامل (جاهز للنسخ واللصق)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton,
                100, 50, 150, 200);

            commandBtn.Caption = "Submit";
            // commandBtn.OnAction = "MyMacroName";

            string outputPath = @"ActiveX_CommandButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

تشغيل المقتطف ينتج ملف Word يحتوي على **زر أمر ActiveX** قابل للنقر. افتح الملف في Microsoft Word، وانتقل إلى **وضع التصميم** (علامة Developer → Design Mode)، وسترى الزر معروضًا بالضبط في الموضع الذي وضعته فيه.

## الخطوة 6: التحقق من النتيجة

1. افتح `ActiveX_CommandButton.docx` في Microsoft Word.  
2. فعّل علامة **Developer** إذا لم تكن مرئية (`File → Options → Customize Ribbon → check Developer`).  
3. انقر على **Design Mode**. يجب أن يظهر الزر مع التسمية “Submit”.  
4. إذا أضفت ماكرو `OnAction`، انقر على الزر بينما وضع التصميم مغلق لتشغيل الماكرو.

إذا لم يظهر الزر، تأكد من أن إعدادات أمان Word تسمح بتحكمات ActiveX (`File → Options → Trust Center → Trust Center Settings → ActiveX Settings`).

## الأسئلة الشائعة والحالات الخاصة

| Question | Answer |
|----------|--------|
| **Can I insert other ActiveX types?** | Yes. `Forms2OleControlType` enum includes `CheckBox`, `OptionButton`, `ComboBox`, etc. Replace `CommandButton` with the desired enum value |

| السؤال | الجواب |
|----------|--------|
| **هل يمكنني إدراج أنواع أخرى من ActiveX؟** | نعم. يتضمن تعداد `Forms2OleControlType` القيم `CheckBox`، `OptionButton`، `ComboBox`، إلخ. استبدل `CommandButton` بالقيمة المطلوبة من التعداد. |

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء شكل مجموعة في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [إنشاء مستند Word مع رأس وتذييل باستخدام Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [إدراج صورة مضمنة في مستند Word باستخدام Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}