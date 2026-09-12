---
category: general
date: 2026-09-11
description: تعلم كيفية إنشاء مستند Word باستخدام C# وإضافة زر أمر برمجياً باستخدام
  Aspose.Words في بضع خطوات بسيطة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- programmatically add command button
language: ar
lastmod: 2026-09-11
og_description: إنشاء مستند Word باستخدام C# وإضافة زر أمر برمجيًا باستخدام Aspose.Words.
  اتبع هذا الدليل الكامل للحصول على حل عملي.
og_image_alt: Screenshot of a Word document containing a Submit command button created
  with C#
og_title: إنشاء مستند Word بـ C# – إضافة زر أمر برمجيًا
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  headline: How to create word document c# and programmatically add a command button
  type: TechArticle
- description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  name: How to create word document c# and programmatically add a command button
  steps:
  - name: Launch Word and open `CommandButton.docx`.
    text: Launch Word and open `CommandButton.docx`.
  - name: You should see a button labeled **Submit** in the document body.
    text: You should see a button labeled **Submit** in the document body.
  - name: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
    text: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
title: كيفية إنشاء مستند Word باستخدام C# وإضافة زر أمر برمجياً
url: /ar/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-and-programmatically-add-a-com/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مستند Word باستخدام C# وإضافة زر أمر برمجياً

إذا كنت بحاجة إلى **create word document c#** وتضمين زر تفاعلي، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك. باستخدام Aspose.Words يمكنك إضافة زر أمر برمجياً في بضع أسطر من الشيفرة فقط، مما يلغي الحاجة إلى العمل اليدوي على واجهة المستخدم في Word.

في هذا الشرح ستتعلم كيفية:

* تهيئة ملف Word فارغ باستخدام C#.
* إدراج عنصر تحكم ActiveX **CommandButton**.
* ضبط خصائص الزر مثل الاسم والتسمية.
* حفظ المستند بحيث يظهر الزر عند فتح الملف في Microsoft Word.

لا توجد أدوات خارجية مطلوبة بخلاف مكتبة Aspose.Words لـ .NET، وتعمل الخطوات مع .NET 6+ أو .NET Framework 4.6.2 وما بعده.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من أن لديك:

| المتطلب | السبب |
|------------|--------|
| .NET 6 SDK (or .NET Framework 4.6.2+) | يوفر بيئة التشغيل لمشروع C#. |
| Visual Studio 2022 (or any C# IDE) | يجعل كتابة وبناء وتشغيل الشيفرة أمراً سهلاً. |
| Aspose.Words for .NET NuGet package | يوفّر الفئات `Document` و `DocumentBuilder` و `Forms2OleControl` المستخدمة في المثال. |
| Basic knowledge of C# syntax | يتيح لك متابعة الشيفرة دون الحاجة إلى منحنيات تعلم إضافية. |

يمكنك إضافة حزمة Aspose.Words عبر وحدة تحكم NuGet:

```powershell
Install-Package Aspose.Words
```

## الخطوة 1: إعداد مشروع C# Console جديد

أنشئ تطبيقًا سطر أوامر سيولد ملف Word. افتح الطرفية وشغّل:

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

ملف `Program.cs` المُولَّد سيحتوي على الشيفرة الموضحة في الخطوات التالية.

## الخطوة 2: إنشاء مستند فارغ وDocumentBuilder

العملية الأولى هي إنشاء كائن `Document`، الذي يمثل ملف `.docx` فارغ، و`DocumentBuilder` الذي يتيح لك تعديل محتويات المستند.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Step 2: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**لماذا هذا مهم:**  
`Document` هو الحاوية لجميع عناصر Word (فقرات، جداول، عناصر تحكم). `DocumentBuilder` يوفر واجهة برمجة تطبيقات سلسة لإدراج الكائنات في موقع المؤشر الحالي دون التعامل مع مجموعات العقد منخفضة المستوى.

## الخطوة 3: إدراج عنصر تحكم ActiveX CommandButton

يدعم Aspose.Words إدراج عناصر تحكم ActiveX القديمة عبر طريقة `InsertForms2OleControl`. تتطلب الطريقة نوع العنصر وحجم النقاط المطلوب.

```csharp
        // Step 3: Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);
```

**ما يحدث في الخلفية:**  
يتعامل Word مع عنصر تحكم ActiveX ككائن OLE (Object Linking and Embedding). فئة `Forms2OleControl` تغلف بيانات OLE وتكشف عن خصائص مثل `Name` و `Caption`.

## الخطوة 4: ضبط اسم الزر وتسمية النص

بعد وضع العنصر، يمكنك تخصيص خصائصه في وقت التشغيل. ضبط `Name` ذو معنى يساعدك على التعرف على الزر لاحقًا، بينما `Caption` يحدد النص المعروض على الزر.

```csharp
        // Step 4: Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";
```

**نصيحة احترافية:**  
إذا كنت تخطط لمعالجة حدث النقر للزر باستخدام VBA، يصبح `Name` هو اسم الماكرو الذي تشير إليه، مثال: `Sub btnSubmit_Click()`.

## الخطوة 5: حفظ المستند على القرص

أخيرًا، اكتب المستند إلى ملف `.docx`. اختر مجلدًا لديك صلاحية كتابة فيه؛ يستخدم المثال مسارًا نسبيًا يُحل إلى دليل إخراج المشروع.

```csharp
        // Step 5: Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

تشغيل البرنامج ينتج `CommandButton.docx`. فتح الملف في Microsoft Word يعرض زر **Submit** قابل للنقر:

![مستند Word يحتوي على زر أمر Submit](/images/command-button.png "لقطة شاشة لمستند Word يحتوي على زر أمر Submit تم إنشاؤه باستخدام C#")

*نص بديل للصورة (og_image_alt):* `Screenshot of a Word document containing a Submit command button created with C#`

## التحقق من النتيجة

1. افتح Word وافتح `CommandButton.docx`.  
2. يجب أن ترى زرًا معنونا **Submit** في جسم المستند.  
3. عند تمرير المؤشر فوق الزر سيظهر الاسم `btnSubmit` في لوحة **Properties** (علامة تبويب Developer → Properties).  

إذا لم يظهر الزر، تأكد من تمكين علامة تبويب **Developer** في Word (File → Options → Customize Ribbon → ضع علامة على *Developer*). تُخفى عناصر تحكم ActiveX عندما تكون العلامة غير مفعلة.

## التعامل مع الاختلافات الشائعة والحالات الطرفية

| الحالة | التعديل الموصى به |
|-----------|------------------------|
| **Different button size** | غيّر قيم العرض والارتفاع في `InsertForms2OleControl`. على سبيل المثال، `150, 40` ينشئ زرًا أكبر. |
| **Multiple buttons** | استدعِ `InsertForms2OleControl` عدة مرات، مع تحريك مؤشر الـ builder بين الاستدعاءات (`builder.Writeln();`). |
| **Button without ActiveX** | استخدم `InsertFormField` لإضافة حقل نموذج قديم (مثل مربع اختيار) إذا كنت بحاجة إلى توافق مع إصدارات Word القديمة التي تحظر ActiveX. |
| **Cross‑platform usage** | عناصر تحكم ActiveX تعمل فقط على إصدارات Word لنظام Windows. بالنسبة لـ Mac أو عارضات الويب، فكر في إدراج ارتباط تشعبي مُصمم كزر بدلاً من ذلك. |
| **Security warnings** | قد يعرض Word تحذيرًا أمنيًا عند فتح مستند يحتوي على عناصر تحكم ActiveX. توقيع المستند بشهادة موثوقة يقلل من هذه الإزعاجات. |

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑ولصقه في `Program.cs`. يتم تجميعه وتشغيله دون تعديل بعد إضافة حزمة Aspose.Words من NuGet.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);

        // Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**المخرجات المتوقعة في وحدة التحكم:**

```
Document saved to C:\Path\To\WordButtonDemo\bin\Debug\net6.0\CommandButton.docx
```

فتح الملف المُولَّد يُظهر زر **Submit** جاهزًا للتفاعل.

## الخلاصة

أنت الآن تعرف كيف **create word document c#** و**programmatically add command button** باستخدام Aspose.Words. العملية تختصر في تهيئة `Document`، إدراج `Forms2OleControl`، ضبط خصائصه، وحفظ الملف. من هنا يمكنك:

* إضافة المزيد من عناصر التحكم (مثل مربعات الاختيار، حقول النص) عن طريق تغيير `ControlType`.  
* إرفاق ماكرو VBA بالزر للمنطق المخصص.  
* دمج هذه التقنية مع ميزات أخرى في Aspose.Words مثل دمج البريد أو ملء القوالب.

جرّب أحجامًا وتسمية نصوص مختلفة، وأزرار متعددة لتناسب سيناريو الأتمتة الخاص بك. Happy coding!

## ما الذي ينبغي أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مستند Word مع رأس وتذييل باستخدام Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [إنشاء مستند Word باستخدام Aspose.Words لـ .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [إنشاء شكل مجموعة في مستند Word باستخدام Aspose.Words لـ .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}