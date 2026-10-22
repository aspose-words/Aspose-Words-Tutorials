---
category: general
date: 2026-09-21
description: تعلم كيفية إنشاء زر أمر ActiveX في مستند Word باستخدام Aspose.Words و
  C#. يغطي الدليل خطوة بخطوة الإدراج والتموضع والحفظ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- aspose.words activex
- c# documentbuilder
- insertforms2olecontrol
- activeX control in word
- programmatically add button
language: ar
lastmod: 2026-09-21
og_description: إنشاء زر أمر ActiveX في مستند Word باستخدام C# و Aspose.Words. اتبع
  هذا الدرس الكامل لإدراج الزر وتحديد موقعه وحفظه برمجيًا.
og_image_alt: Screenshot showing an ActiveX command button inserted in a Word document
  using C#
og_title: إنشاء زر أمر ActiveX في Word باستخدام C# – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create ActiveX command button in a Word document with
    Aspose.Words and C#. Step‑by‑step guide covers insertion, positioning, and saving.
  headline: How to create ActiveX command button in Word using C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
- DocumentBuilder
title: كيفية إنشاء زر أمر ActiveX في Word باستخدام C#
url: /ar/net/working-with-oleobjects-and-activex/how-to-create-activex-command-button-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء زر أمر ActiveX في Word باستخدام C#

إذا كنت بحاجة إلى **إنشاء زر أمر ActiveX** داخل ملف Word، يوضح لك هذا الدليل الخطوات الدقيقة. باستخدام Aspose.Words for .NET يمكنك إضافة الزر وتحديد موقعه وتكوينه بالكامل من خلال كود C#.

إدراج زر ActiveX برمجيًا يلغي الحاجة إلى العمل اليدوي في واجهة المستخدم ويسمح بإنشاء مستندات تلقائية للنماذج، التقارير، أو القوالب التفاعلية. في هذا الدرس ستتعلم كيفية استخدام **DocumentBuilder**، طريقة **InsertForms2OleControl**، والخصائص المرتبطة لتحقيق زر يعمل بالكامل.

## ما ستحتاجه

قبل أن تبدأ، تأكد من أن لديك:

* .NET 6.0 SDK أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.7+)
* Aspose.Words for .NET (حزمة NuGet `Aspose.Words`)
* بيئة تطوير متكاملة مثل Visual Studio 2022 أو VS Code
* معرفة أساسية بـ C# ومفاهيم مستندات Word

لا يلزم تثبيت Office إضافي لأن Aspose.Words يعمل بشكل مستقل عن Microsoft Word.

## الخطوة 1: إعداد مشروع C#

أنشئ مشروع console جديد وأضف حزمة Aspose.Words.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

مكتبة `Aspose.Words` توفر الفئة **DocumentBuilder** التي سنستخدمها لمعالجة المستند.

## الخطوة 2: تهيئة المستند والباني

كتلة الكود الأولى تنشئ مستندًا فارغًا وكائنًا من نوع `DocumentBuilder`. هذا الكائن هو نقطة الدخول لجميع عمليات معالجة Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// Create a new blank document.
Document doc = new Document();

// Create a builder to edit the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

**لماذا هذا مهم:** `DocumentBuilder` يحافظ على موضع المؤشر الحالي، لذا أي إدراج يليه سيظهر بالضبط حيث تضع المؤشر.

## الخطوة 3: إدراج زر أمر ActiveX

طريقة **InsertForms2OleControl** تنشئ عنصر تحكم ActiveX من النوع المطلوب. هنا نطلب `CommandButton` ونحدد حجمه بالنقاط (200 × 30 pt).

```csharp
// Insert an ActiveX CommandButton control (200 × 30 pt).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    OleControlType.CommandButton, 200, 30);
```

**التفسير:**  
* `OleControlType.CommandButton` يخبر Aspose.Words بإنشاء زر بدلاً من نوع تحكم آخر.  
* الطريقة تُعيد كائن `Forms2OleControl`، الذي يتيح حقول تحديد الموقع والخصائص.

## الخطوة 4: تحديد موقع الزر وتعيين خصائصه

بعد الإدراج يمكنك نقل الزر إلى أي مكان في الصفحة ومنحه اسمًا برمجيًا وعنوانًا مرئيًا.

```csharp
// Position the button (coordinates are in points).
cmdBtn.Left = 100;          // X‑coordinate
cmdBtn.Top = 150;           // Y‑coordinate

// Set the button's programmatic name and displayed text.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

**نصيحة محترف:** نظام الإحداثيات يبدأ من الزاوية العليا اليسرى للصفحة. عدّل `Left` و `Top` لمطابقة الزر مع حقول النموذج الأخرى.

## الخطوة 5: حفظ المستند

أخيرًا، اكتب المستند إلى القرص. سيحتوي الملف على زر ActiveX، جاهز للفتح في Microsoft Word حيث يصبح الزر تفاعليًا.

```csharp
// Save the document that now contains the ActiveX button.
doc.Save("ActiveXCommandButton.docx");
```

عند فتح `ActiveXCommandButton.docx` في Word، سترى زرًا بعنوان **Submit** في الموقع المحدد. النقر عليه في Word سيُطلق سلوك زر الأمر الافتراضي (يمكنك تخصيصه لاحقًا باستخدام VBA أو إضافات Word).

## مثال كامل قابل للتنفيذ

جمع كل الأجزاء معًا ينتج برنامجًا مستقلًا يمكنك نسخه، لصقه، وتشغيله.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX CommandButton (200 × 30 pt).
        Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
            OleControlType.CommandButton, 200, 30);

        // 3. Position and configure the button.
        cmdBtn.Left = 100;          // X‑coordinate (points)
        cmdBtn.Top = 150;           // Y‑coordinate (points)
        cmdBtn.Name = "btnSubmit";
        cmdBtn.Caption = "Submit";

        // 4. Save the document.
        doc.Save("ActiveXCommandButton.docx");

        Console.WriteLine("Document created successfully.");
    }
}
```

**الناتج المتوقع:** يطبع الطرفية *“Document created successfully.”* وتحتوي المجلد الآن على `ActiveXCommandButton.docx`. فتح الملف في Microsoft Word يظهر زر **Submit** قابل للنقر موضعه 100 pt من الهامش الأيسر و150 pt من أعلى الصفحة.

## المشكلات الشائعة وكيفية تجنبها

| المشكلة | لماذا يحدث | الحل |
|---------|------------|------|
| الزر يظهر خارج الصفحة | قيمة `Left`/`Top` تتجاوز أبعاد الصفحة | استخدم `doc.FirstSection.PageSetup.PageWidth` و `PageHeight` لحساب إحداثيات آمنة |
| الزر غير مرئي في Word | تم حفظ المستند بصيغة تُزيل عناصر التحكم ActiveX (مثل `.txt`) | احفظ دائمًا بصيغة `.docx` أو `.doc` |
| خطأ تشغيل `ArgumentOutOfRangeException` | تم تعيين العرض أو الارتفاع إلى صفر أو قيمة سلبية | تأكد من أن قيم الحجم الممررة إلى `InsertForms2OleControl` أعداد موجبة |

## توسيع الحل

يمكنك تخصيص الزر أكثر عن طريق تعيين خصائص إضافية مثل `Enabled`، `Visible`، أو إرفاق ماكرو عبر VBA. تسمح لك فئة **Forms2OleControl** أيضًا بإدراج عناصر تحكم ActiveX أخرى مثل مربعات الاختيار (`OleControlType.CheckBox`) أو قوائم الاختيار (`OleControlType.ComboBox`).

إذا كنت بحاجة إلى إنشاء عدة أزرار داخل حلقة، غلف منطق الإدراج في طريقة مساعدة:

```csharp
static Forms2OleControl AddCommandButton(DocumentBuilder builder,
    string name, string caption, double left, double top)
{
    var btn = builder.InsertForms2OleControl(OleControlType.CommandButton, 200, 30);
    btn.Name = name;
    btn.Caption = caption;
    btn.Left = left;
    btn.Top = top;
    return btn;
}
```

## الخلاصة

أنت الآن تعرف كيف **تنشئ زر أمر ActiveX** في مستند Word باستخدام C# و Aspose.Words. غطى الدرس إعداد المشروع، إدراج الزر باستخدام `InsertForms2OleControl`، تحديد موقعه، وحفظ الملف النهائي. مع هذه الأساسيات يمكنك أتمتة النماذج المعقدة، تضمين عناصر تحكم تفاعلية، ودمج مستندات Word في حلول .NET أكبر.

بعد ذلك، استكشف مواضيع ذات صلة مثل حقول نموذج **Aspose.Words ActiveX**، تنسيق متقدم باستخدام **C# DocumentBuilder**، أو إضافة **تحكم ActiveX في Word** برمجيًا لمربعات الاختيار والقوائم المنسدلة. جرّب إحداثيات وأحجام مختلفة لتناسب متطلبات التخطيط الخاصة بك. Happy coding!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [إنشاء مستند Word باستخدام Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [إنشاء شكل مستطيل في Word باستخدام Aspose.Words – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [إنشاء مستند Word مع جدول باستخدام Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}