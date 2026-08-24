---
category: general
date: 2026-08-23
description: إنشاء زر إرسال في أتمتة Word باستخدام C#. تعلم كيفية إضافة زر ActiveX،
  وتعيين اسم الزر، والعنوان، والنص برمجيًا.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create submit button
- set button text
- set button name
- add activex button
- set button caption
language: ar
lastmod: 2026-08-23
og_description: إنشاء زر إرسال في أتمتة Word باستخدام C#. يوضح هذا الدليل كيفية إضافة
  زر ActiveX، وتعيين اسمه، وعنوانه، والنص الخاص به باستخدام Aspose.Words.
og_image_alt: Screenshot of a Word document showing a created submit button
og_title: إنشاء زر إرسال في أتمتة Word باستخدام C#
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  headline: How to create submit button in C# Word automation
  type: TechArticle
- description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  name: How to create submit button in C# Word automation
  steps:
  - name: Expected output
    text: 'Running the program creates `SubmitButton.docx`. When you open the file
      in Microsoft Word:'
  - name: Handling naming collisions
    text: 'If you run the routine multiple times on the same document, Word may auto‑rename
      duplicate controls. To guarantee uniqueness, you can prepend a GUID:'
  - name: Localizing the button caption
    text: 'For multilingual documents, store captions in a resource file and assign
      them at runtime:'
  - name: Responding to the button click
    text: 'The button itself does not contain click logic in C#. You typically attach
      a VBA macro:'
  type: HowTo
tags:
- C#
- Word automation
- ActiveX
- Aspose.Words
title: كيفية إنشاء زر إرسال في أتمتة Word باستخدام C#
url: /ar/net/working-with-oleobjects-and-activex/how-to-create-submit-button-in-c-word-automation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء زر إرسال في أتمتة Word باستخدام C#

إذا كنت بحاجة إلى **إنشاء زر إرسال** داخل مستند Word باستخدام C#، فإن هذا الدليل يشرح لك العملية بالكامل. سترى كيفية إضافة زر ActiveX، وتعيين اسم برمجي، وتحديد تسمية الزر بحيث يبدو كعنصر تحكم *Submit* عادي.

يمكن لأتمتة عناصر التحكم في النماذج داخل Word أن تحل محل العمل اليدوي في التصميم وتضمن الاتساق عبر مئات المستندات. في الخطوات أدناه ستتعلم أيضًا كيفية **تعيين نص الزر**، **تعيين اسم الزر**، و**تعيين تسمية الزر**—وكل ذلك أساسي عندما يشارك الزر في سير عمل يعتمد على الماكرو.

## المتطلبات المسبقة

* .NET 6.0 (أو أحدث) مثبت.
* إشارة إلى **Aspose.Words for .NET** (المكتبة التي توفر `DocumentBuilder.InsertForms2OleControl`).
* إلمام أساسي بـ C# وعناصر التحكم النماذجية ActiveX في Word.

يمكنك تثبيت Aspose.Words عبر NuGet:

```bash
dotnet add package Aspose.Words
```

> **نصيحة احترافية:** استخدم أحدث نسخة مستقرة من Aspose.Words للاستفادة من إصلاحات الأخطاء والميزات الجديدة المتعلقة بعناصر التحكم ActiveX.

## نظرة عامة على الحل

تم تنظيم هذا الدليل إلى ثلاث خطوات واضحة:

1. **إضافة زر ActiveX** – استخدم طريقة `InsertForms2OleControl` لوضع زر أمر في المستند.  
2. **تعيين اسم الزر** – قم بتعيين معرف برمجي فريد باستخدام الخاصية `Name`.  
3. **تعيين تسمية الزر** – حدد النص الظاهر على الزر عبر الخاصية `Caption` (والتي تتحكم أيضًا في **تعيين نص الزر** الذي تراه في واجهة المستخدم).

بنهاية هذا الدليل ستحصل على روتين **إنشاء زر إرسال** كامل الوظائف يمكنك إعادة استخدامه في أي مشروع أتمتة Word.

## الخطوة 1: إضافة زر ActiveX إلى المستند

المهمة الأولى هي **إضافة زر activex** إلى ملف Word. تُظهر Aspose.Words التعداد `Forms2OleControlType.CommandButton` لهذا الغرض.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load or create a new document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a CommandButton ActiveX control at the cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton);
```

**لماذا هذه الخطوة مهمة:**  
عناصر التحكم ActiveX هي العناصر النماذجية الوحيدة في Word التي يمكنها تنفيذ ماكرو VBA أو التفاعل مع شفرة خارجية. إضافة العنصر تخلق موضعًا يمكن للخطوات اللاحقة تكوينه.

> **حالة خاصة:** إذا كان المستند يحتوي بالفعل على عنصر تحكم بنفس الاسم، سيقوم Word بإعادة تسمية العنصر الجديد تلقائيًا (مثال: `CommandButton1`). تعيين الاسم صراحةً في الخطوة التالية يتجنب هذه التصادمات.

## الخطوة 2: تعيين اسم الزر

إن **تعيين اسم الزر** الموثوق به أمر حاسم عندما تحتاج إلى الإشارة إلى عنصر التحكم من VBA أو من أجزاء أخرى من شفرة C#. الخاصية `Name` تمنح الزر معرفًا برمجيًا.

```csharp
// Assign a unique programmatic name
commandBtn.Name = "btnSubmit";
```

**لماذا يجب عليك تعيين اسم:**  
عند فتح المستند، يمكن لـ VBA استرجاع الزر عبر `ActiveDocument.InlineShapes("btnSubmit")`. اسم ذو معنى مثل `btnSubmit` يوضح النية أيضًا عند فحص XML الخاص بالمستند.

> **نصيحة احترافية:** احرص على أن تكون الأسماء قصيرة، أبجدية رقمية، وتبدأ بحرف لتظل متوافقة مع قواعد تسمية VBA.

## الخطوة 3: تعيين تسمية الزر (النص الظاهر)

النص الذي يراه المستخدمون على الزر يتحكم فيه خاصية **تعيين تسمية الزر**. في واجهة Word يظهر هذا كعلامة الزر، وهو أيضًا **تعيين نص الزر** الذي تريد عرضه.

```csharp
// Define the text shown on the button
commandBtn.Caption = "Submit";
```

**لماذا التسمية مهمة:**  
التسمية هي العلامة التي يراها المستخدم. تعديلها لاحقًا لا يؤثر على اسم الزر، لذا يمكنك توطين الواجهة دون كسر أي شفرة تعتمد على `btnSubmit`.

> **سؤال شائع:** *هل يمكنني تعيين كل من Caption و Value؟*  
> بالنسبة لـ `CommandButton`، تتحكم `Caption` في التسمية، بينما لا يُستخدم `Value`. إذا كنت بحاجة إلى قيمة مخفية، احفظها في خاصية مستند مخصصة بدلاً من ذلك.

## مثال عملي كامل

جمع الخطوات الثلاث معًا يمنحك روتينًا كاملاً يمكنك إدراجه في أي تطبيق كونسول أو Windows:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert the ActiveX command button
        Forms2OleControl commandBtn = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton);

        // 3. Set a meaningful name for later reference
        commandBtn.Name = "btnSubmit";

        // 4. Set the visible caption (this is the button text)
        commandBtn.Caption = "Submit";

        // Optional: position the button (in points)
        commandBtn.Left = 100;   // distance from left margin
        commandBtn.Top = 200;    // distance from top margin
        commandBtn.Width = 80;
        commandBtn.Height = 30;

        // Save the document
        doc.Save("SubmitButton.docx");
        Console.WriteLine("Document with submit button created successfully.");
    }
}
```

### النتيجة المتوقعة

تشغيل البرنامج ينشئ `SubmitButton.docx`. عند فتح الملف في Microsoft Word:

* يظهر زر **Submit** في الموقع المحدد.
* اسم الزر هو `btnSubmit` (تحقق عبر *Developer → Design Mode → Properties*).
* النقر على الزر في وضع التصميم يظهر التسمية *Submit*.

الآن لديك وحدة بناء قابلة لإعادة الاستخدام لأي حل Word يعتمد على النماذج.

## اعتبارات إضافية

### معالجة تصادم الأسماء

إذا نفذت الروتين عدة مرات على نفس المستند، قد يقوم Word بإعادة تسمية عناصر التحكم المكررة تلقائيًا. لضمان التفرد، يمكنك إضافة GUID مسبقًا:

```csharp
commandBtn.Name = $"btnSubmit_{Guid.NewGuid():N}";
```

### توطين تسمية الزر

للمستندات متعددة اللغات، احفظ التسميات في ملف موارد وعيّنها أثناء التشغيل:

```csharp
commandBtn.Caption = Resources.SubmitButtonLabel;
```

### الاستجابة لنقر الزر

الزر نفسه لا يحتوي على منطق النقر في C#. عادةً ما تُرفق ماكرو VBA:

```vba
Sub btnSubmit_Click()
    MsgBox "Form submitted!"
End Sub
```

نظرًا لأنك **قمت بتعيين اسم الزر** إلى `btnSubmit`، فإن اسم الماكرو يتبع تلقائيًا قاعدة `<Name>_Click`.

## أسئلة شائعة في حل المشكلات

| السؤال | الجواب |
|----------|--------|
| **لماذا يظهر الزر فارغًا؟** | تأكد من تعيين الخاصية `Caption`؛ بدونها لا يظهر أي نص على الزر. |
| **هل يمكنني استخدام عنصر تحكم ActiveX مختلف؟** | نعم. استبدل `Forms2OleControlType.CommandButton` بـ `CheckBox` أو `OptionButton` وغيرها، لكن الخصائص تختلف. |
| **هل هذا متوافق مع .NET Core؟** | Aspose.Words for .NET يدعم .NET 6+، لذا يعمل نفس الكود على .NET Core و .NET Framework. |
| **ماذا لو كان المستند يحتوي بالفعل على زر؟** | استخدم `Name` فريد (مثلاً أضف GUID) لتجنب التعارضات. |

## الخلاصة

أنت الآن تعرف كيف **إنشاء زر إرسال** برمجيًا في مستند Word باستخدام C#. باتباع الخطوات الثلاث—**إضافة زر activex**، **تعيين اسم الزر**، و**تعيين تسمية الزر**—يمكنك بشكل موثوق **تعيين نص الزر**، **تعيين اسم الزر**، و**تعيين تسمية الزر** لأي حل نماذج مؤتمت.

من هنا قد تستكشف:

* إضافة ماكرو VBA يتفاعل مع نقرة **زر الإرسال**.
* تنسيق الزر بخطوط أو ألوان مخصصة عبر XML الأساسي.
* إنشاء عدة أزرار في حلقة للنماذج الديناميكية.

لا تتردد في تجربة تسميات، أسماء، ومواقع مختلفة لتناسب سير عملك الخاص. أتمنى لك أتمتة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء شكل مجموعة في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [إنشاء مخطط خطي في Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [إنشاء مستند Word مع رأس وتذييل باستخدام Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}