---
category: general
date: 2026-07-29
description: إضافة زر أمر إلى مستند Word باستخدام Aspose.Words. تعلّم كيفية تعيين
  خصائص عنصر التحكم ActiveX وتعيين تسمية زر الأمر في بضع خطوات سهلة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button to word document
- set activex control properties
- set command button caption
- Aspose.Words ActiveX example
- C# insert ActiveX control
language: ar
lastmod: 2026-07-29
og_description: إضافة زر أمر إلى مستند Word باستخدام Aspose.Words. يوضح هذا الدرس
  كيفية تعيين خصائص عنصر التحكم ActiveX وتعيين تسمية زر الأمر بسرعة.
og_image_alt: Screenshot of a Word document with a Submit command button inserted
  via C#
og_title: إضافة زر أمر إلى مستند Word – Aspose.Words خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  headline: Add Command Button to Word Document with Aspose.Words – Complete Guide
  type: TechArticle
- description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  name: Add Command Button to Word Document with Aspose.Words – Complete Guide
  steps:
  - name: Setting the Caption
    text: 'The caption is the text that appears on the button itself. To **set command
      button caption**, simply assign a string to the `Caption` property:'
  - name: Naming the Control
    text: 'Giving the control a meaningful name makes it easier to reference later
      (for example, when automating Word macros). We’ll set the `Name` property:'
  - name: Positioning on the Page
    text: 'Word uses points (1/72 of an inch) for layout. Adjust the `Left` and `Top`
      properties to place the button where you need it:'
  - name: Expected Result
    text: 1. The Word document opens with a single page. 2. A rectangular button labeled
      **Submit** appears at the coordinates you specified. 3. If you right‑click the
      button and choose **Properties**, you’ll see the name `btnSubmit` and other
      properties you set.
  - name: Inserting Other ActiveX Types
    text: 'The `InsertForms2OleControl` method isn’t limited to command buttons. You
      can embed check boxes, option buttons, or even custom ActiveX objects:'
  - name: Handling Word Versions
    text: Older Word versions (pre‑2007) use the binary `.doc` format, which stores
      ActiveX controls differently. Aspose.Words automatically converts the control
      when you save as `.doc`, but some properties (like precise positioning) may
      shift. If you target legacy formats, test the output in the specific Wor
  - name: Security Settings
    text: 'Word may disable ActiveX controls on machines with strict macro security.
      To avoid a “Security Warning” dialog, consider:'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: إضافة زر أمر إلى مستند Word باستخدام Aspose.Words – دليل شامل
url: /ar/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة زر أمر إلى مستند Word – دليل برمجة كامل

هل احتجت يومًا إلى **add command button to word document** لكن لم تكن متأكدًا من أي استدعاءات API تستخدم؟ لست وحدك؛ العديد من المطورين يواجهون هذه المشكلة عندما يحاولون أول مرة تضمين عناصر تحكم تفاعلية في ملف DOCX. الخبر السار هو أن Aspose.Words يجعل الأمر سهلًا بشكل مفاجئ. في هذا الدليل سنستعرض إنشاء عنصر تحكم CommandButton ActiveX، **set activex control properties**، و **set command button caption**—كل ذلك باستخدام كود C# نظيف يمكنك نسخه ولصقه الآن.

بنهاية هذا البرنامج التعليمي ستحصل على ملف Word يعمل بالكامل يحتوي على زر “Submit” قابل للنقر، جاهز للفتح في Microsoft Word. لا سكريبتات VBA خارجية، ولا تعديل يدوي للواجهة—فقط تحكم برمجي خالص.

## ما ستتعلمه

* كيفية إنشاء مستند Word فارغ و `DocumentBuilder`.
* استدعاء الطريقة الدقيقة لـ **add command button to word document** باستخدام Aspose.Words.
* طرق **set activex control properties** مثل الحجم، الموضع، والاسم.
* التقنية الصحيحة لـ **set command button caption** بحيث يظهر الزر النص المطلوب بالضبط.
* نصائح للتعامل مع الحالات الخاصة مثل أنواع الأزرار المختلفة، مقياس DPI، وتوافق إصدارات Word.

> **المتطلبات المسبقة:** Visual Studio (أو أي بيئة تطوير C#) مع تثبيت Aspose.Words for .NET (حزمة NuGet `Aspose.Words`). لا حاجة لخبرة سابقة في ActiveX.

---

## الخطوة 1: إعداد المشروع واستيراد المساحات الاسمية

قبل أن نتمكن من **add command button to word document**، نحتاج إلى مشروع C# ي引用 Aspose.Words. أنشئ تطبيق console جديد لـ .NET، ثم أضف حزمة NuGet:

```bash
dotnet add package Aspose.Words
```

الآن استورد المساحات الاسمية المطلوبة إلى ملف المصدر الخاص بك:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;
```

توفر لك هذه التوجيهات الثلاثة `using` الوصول إلى الفئات `Document` و `DocumentBuilder` و `Forms2OleControl` التي تدعم إدراج ActiveX.

*نصيحة:* إذا كنت تستخدم Visual Studio، سيقترح IDE إضافة هذه تلقائيًا عند كتابة أسماء الفئات.

---

## الخطوة 2: إنشاء مستند فارغ ومُنشئ

`Document` جديد يمثل ملف Word فارغ. `DocumentBuilder` هو “القلم” المريح الذي يتيح لنا الرسم، إدراج النص،—وبشكل حاسم—وضع عناصر تحكم ActiveX.

```csharp
// Initialize a new, empty Word document.
Document doc = new Document();

// Attach a builder to the document for editing.
DocumentBuilder builder = new DocumentBuilder(doc);
```

في هذه المرحلة يكون المستند مجرد لوحة فارغة—تخيله كصفحة نظيفة تنتظر زر الأمر الخاص بك.

---

## الخطوة 3: إدراج عنصر تحكم CommandButton ActiveX

الآن نضيف أخيرًا **add command button to word document**. توفر Aspose.Words طريقة `InsertForms2OleControl` التي تقبل نوع العنصر وأبعاده. سنستخدم `Forms2OleControlType.CommandButton` وسنحدد عرضًا مريحًا قدره 150 نقطة وارتفاعًا 30 نقطة.

```csharp
// Insert a CommandButton ActiveX control with a specific size.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton,
    width: 150,
    height: 30);
```

تُعيد الطريقة كائن `Forms2OleControl`، والذي سنستخدمه لـ **set activex control properties** في الخطوة التالية.

---

## الخطوة 4: تكوين العنصر – الاسم، التسمية، والموضع

### تعيين التسمية

التسمية هي النص الذي يظهر على الزر نفسه. لت **set command button caption**، قم ببساطة بتعيين سلسلة نصية إلى الخاصية `Caption`:

```csharp
commandButton.Caption = "Submit";
```

يمكنك تغيير `"Submit"` إلى أي شيء—“Save”، “Export”، “Launch”، إلخ—وسيقوم Word بعرض ذلك النص بالضبط.

### تسمية العنصر

إعطاء العنصر اسمًا ذا معنى يجعل من السهل الإشارة إليه لاحقًا (مثلاً عند أتمتة ماكروهات Word). سنقوم بتعيين الخاصية `Name`:

```csharp
commandButton.Name = "btnSubmit";
```

### تحديد الموضع على الصفحة

يستخدم Word النقاط (1/72 بوصة) للتخطيط. اضبط خصائص `Left` و `Top` لتحديد موضع الزر حيث تحتاجه:

```csharp
commandButton.Left = 100; // 100 points from the left margin
commandButton.Top  = 200; // 200 points from the top of the page
```

إذا كنت بحاجة إلى محاذاة الزر بالنسبة إلى فقرة، يمكنك أولاً تحريك مؤشر الـ builder، ثم إدراج العنصر؛ ستكون الإحداثيات نسبية لتلك الموضع.

*حالة خاصة:* على شاشات DPI عالية قد يظهر الحجم البصري مختلفًا قليلًا في Word. للحفاظ على حجم الزر الفعلي ثابتًا عبر الأجهزة، يمكنك حساب النقاط بناءً على DPI المستهدف (عادةً 96 DPI لـ Word).

---

## الخطوة 5: حفظ المستند

بعد تكوين الزر بالكامل، حفظ الملف يصبح سطرًا واحدًا:

```csharp
// Save the document; the ActiveX control is stored inside the DOCX.
doc.Save("CommandButton.docx");
```

الملف الناتج `CommandButton.docx` يحتوي على زر ActiveX يعمل بالكامل. افتحه في Microsoft Word، وسترى زر “Submit” في الموضع الذي وضعته بالضبط.

### النتيجة المتوقعة

1. يفتح مستند Word بصفحة واحدة.
2. يظهر زر مستطيل مُسمى **Submit** عند الإحداثيات التي حددتها.
3. إذا نقرت بزر الفأرة الأيمن على الزر واخترت **Properties**، سترى الاسم `btnSubmit` والخصائص الأخرى التي ضبطتها.

---

## الخطوة 6: تنويعات متقدمة ومشكلات شائعة

### إدراج أنواع أخرى من ActiveX

طريقة `InsertForms2OleControl` ليست محصورة على أزرار الأمر. يمكنك تضمين مربعات اختيار، أزرار اختيار، أو حتى كائنات ActiveX مخصصة:

```csharp
// Example: Insert a CheckBox instead of a CommandButton.
Forms2OleControl checkBox = builder.InsertForms2OleControl(
    Forms2OleControlType.CheckBox,
    width: 20,
    height: 20);
checkBox.Name = "chkAgree";
checkBox.Caption = "I Agree";
```

نفس نمط **set activex control properties** ينطبق—فقط استبدل نوع الـ enum.

### التعامل مع إصدارات Word

الإصدارات القديمة من Word (قبل 2007) تستخدم تنسيق `.doc` الثنائي، الذي يخزن عناصر تحكم ActiveX بشكل مختلف. تقوم Aspose.Words تلقائيًا بتحويل العنصر عند حفظه كـ `.doc`، لكن بعض الخصائص (مثل الموضع الدقيق) قد تتغير. إذا كنت تستهدف تنسيقات قديمة، اختبر النتيجة في إصدار Word المحدد الذي تحتاجه.

### إعدادات الأمان

قد يقوم Word بتعطيل عناصر تحكم ActiveX على الأجهزة التي لديها أمان ماكرو صارم. لتجنب نافذة “تحذير أمان”، ضع في الاعتبار:

* توقيع المستند بشهادة موثوقة.
* إرشاد المستخدمين لتمكين محتوى ActiveX لهذا الموقع.
* استخدام بديل خالٍ من الماكرو (مثل عناصر تحكم محتوى عادية) إذا كان الأمان مصدر قلق.

---

## الخطوة 7: مثال كامل يعمل

فيما يلي البرنامج الكامل الجاهز للتنفيذ والذي يدمج كل خطوة ناقشناها. انسخه إلى ملف `Program.cs` الخاص بك، عدل مسار الإخراج إذا لزم الأمر، واضغط **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            width: 150,   // Width in points
            height: 30);  // Height in points

        // Step 3: Set the control's name and caption.
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Step 4: Position the control on the page.
        commandButton.Left = 100; // 100 points from left edge
        commandButton.Top  = 200; // 200 points from top edge

        // Optional: Add a paragraph above the button for context.
        builder.MoveToDocumentEnd();
        builder.Writeln("Click the button below to submit the form:");

        // Step 5: Save the document.
        string outputPath = "CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved successfully to {outputPath}");
    }
}
```

**ما يفعله هذا الكود:**

* يبدأ بمستند جديد.
* يدرج زر أمر، **sets activex control properties**، و **sets command button caption**.
* يضيف فقرة توضيحية قصيرة.
* يحفظ الملف باسم `CommandButton.docx`.

شغّل البرنامج، افتح الملف المُنشأ، وسترى الزر تحت النص التوضيحي.

---

## الخلاصة

لقد أوضحنا للتو كيفية **add command button to word document** باستخدام Aspose.Words، وكيفية **set activex control properties**، وكيفية **set command button caption**—كل ذلك في مقتطف C# مختصر وجاهز للإنتاج. الطريقة قابلة للتوسيع: استبدل نوع العنصر، عدّل الأبعاد، أو كرّر عبر مصدر بيانات لإدراج عشرات الأزرار تلقائيًا.

هل تريد التعمق أكثر؟ جرّب:

* ربط الزر بماكرو يُطلق تصدير البيانات.
* إضافة صور أو أيقونات مخصصة داخل الزر باستخدام الخاصية `Picture`.
* إنشاء نموذج كامل يحتوي على عدة عناصر تحكم ActiveX (صناديق نصية، قوائم منسدلة، إلخ).

التجربة هي أفضل طريقة لإتقان أتمتة Word. إذا واجهت مشكلة، تذكر مراجعة حسابات DPI وإعدادات أمان Word. برمجة سعيدة، ولتكن مستنداتك أكثر تفاعلية دائمًا!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إضافة محتوى باستخدام Document Builder في Aspose.Words لـ .NET](/words/english/net/add-content-using-document-builder/)
- [إنشاء شكل مجموعة في مستند Word باستخدام Aspose.Words لـ .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [إنشاء مستند Word مع رأس وتذييل باستخدام Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}