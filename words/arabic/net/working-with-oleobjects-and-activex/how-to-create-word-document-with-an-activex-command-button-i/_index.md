---
category: general
date: 2026-09-05
description: إنشاء مستند Word باستخدام Aspose.Words C# وتعلم كيفية إدراج زر أمر ActiveX،
  وتحديد حجم الزر، وإضافة وظيفة تفاعلية للزر.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to insert activex
- add command button
- add interactive button
- set button size
language: ar
lastmod: 2026-09-05
og_description: إنشاء مستند Word باستخدام C# وإدراج زر أمر ActiveX. يوضح هذا الدرس
  كيفية ضبط حجم الزر وإضافة ميزات تفاعلية للزر.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
  created with C#
og_title: إنشاء مستند Word مع زر أمر ActiveX في C# – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  headline: How to create Word document with an ActiveX command button in C#
  type: TechArticle
- description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  name: How to create Word document with an ActiveX command button in C#
  steps:
  - name: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
    text: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
  - name: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
    text: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
  - name: '**Configure the button** – caption, size, and position.'
    text: '**Configure the button** – caption, size, and position.'
  - name: '**Save** the document to disk.'
    text: '**Save** the document to disk.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
- UI controls
title: كيفية إنشاء مستند Word مع زر أمر ActiveX باستخدام C#
url: /ar/net/working-with-oleobjects-and-activex/how-to-create-word-document-with-an-activex-command-button-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مستند Word مع زر أمر ActiveX في C#

إذا كنت بحاجة إلى **إنشاء مستند Word** برمجيًا وإدراج عنصر واجهة مستخدم قابل للنقر، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك. باستخدام Aspose.Words for .NET يمكنك **إنشاء مستند Word**، **إضافة زر أمر**، والتحكم في مظهره—كل ذلك دون فتح Microsoft Word.

ستتعلم **كيفية إدراج عناصر تحكم ActiveX**، **ضبط حجم الزر**، وجعل الزر يتصرف كمكون واجهة مستخدم تفاعلي. لا تحتاج إلى خبرة سابقة في COM أو VBA؛ فقط بيئة تطوير .NET ومكتبة Aspose.Words.

## ما ستحقه

* **إنشاء مستند Word** من الصفر باستخدام C#.
* **إدراج زر أمر ActiveX** (عنصر التحكم الكلاسيكي “Click Me”).
* **ضبط حجم الزر** وتحديد موقعه بدقة.
* إضافة منطق **زر تفاعلي** بسيط اختياريًا (مثل عنصر نائب للماكرو).
* حفظ الملف كـ `.docx` يمكن فتحه في Microsoft Word أو أي عارض متوافق.

### المتطلبات المسبقة

| المتطلب | السبب |
|-------------|--------|
| .NET 6.0 أو أحدث | يوفر بيئة تشغيل كود C#. |
| Aspose.Words for .NET (أحدث إصدار) | يوفر واجهات `Document`، `DocumentBuilder`، و`Forms2OleControl` المستخدمة في المثال. |
| Visual Studio 2022 (أو أي بيئة تطوير C#) | يجعل من السهل تجميع وتشغيل العينة. |
| معرفة أساسية بـ C# | ضرورية لفهم تدفق الكود. |

> **نصيحة احترافية:** إذا كنت تستخدم نسخة تجريبية من Aspose.Words، تأكد من ضبط الترخيص قبل تشغيل الكود لتجنب علامات مائية للتقييم.

## كيفية إنشاء مستند Word – سير العمل العام

تتكون العملية من أربع خطوات منطقية:

1. **تهيئة مستند جديد** و`DocumentBuilder` لتعديله.  
2. **إدراج زر أمر ActiveX** باستخدام `InsertForms2OleControl`.  
3. **تهيئة الزر** – التسمية، الحجم، والموقع.  
4. **حفظ** المستند إلى القرص.

يتم شرح كل خطوة في قسمها الخاص أدناه.

![مستند Word مع زر ActiveX](/images/activex-button.png "لقطة شاشة لمستند Word يحتوي على زر أمر ActiveX تم إنشاؤه باستخدام C#")

## كيفية إدراج زر أمر ActiveX

يبدأ جزء **كيفية إدراج ActiveX** بطريقة `InsertForms2OleControl`. هذه الطريقة تنشئ عنصر تحكم قائم على COM يتعامل معه Word ككائن ActiveX.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// 1️⃣ Create a blank document and a builder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 2️⃣ Insert an ActiveX CommandButton control.
//    Parameters: control type, width, height, left, top (all in points).
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // ActiveX type
    150,                           // Width (points)
    100,                           // Height (points)
    50,                            // Left offset from page margin
    50);                           // Top offset from page margin
```

**لماذا هذا يعمل:** `OleControlType.CommandButton` يخبر Aspose.Words بإنشاء زر بنمط VB الكلاسيكي. يتم التعبير عن الحجم والموقع بالنقاط (نقطة واحدة = 1/72 بوصة)، مما يوفر تحكمًا دقيقًا في التخطيط.

## كيفية إضافة زر أمر وضبط حجم الزر

بعد إدراج العنصر يمكنك تعديل خصائصه البصرية. خطوة **إضافة زر أمر** تغطي أيضًا **ضبط حجم الزر**.

```csharp
// 3️⃣ Set the button's caption – the text the user sees.
commandButton.Caption = "Click Me";

// 4️⃣ Optionally change size after insertion (if you need dynamic sizing).
//    Width and height are mutable properties.
commandButton.Width = 200;   // New width in points
commandButton.Height = 80;   // New height in points

// 5️⃣ Move the button if you need a different position.
commandButton.Left = 100;    // New left offset
commandButton.Top = 120;     // New top offset
```

**شرح:**  

* `Caption` هو التسمية المعروضة على الزر.  
* `Width` و `Height` يتيحان لك **ضبط حجم الزر** بعد الإدراج الأولي—مفيد عندما يعتمد الحجم على بيانات وقت التشغيل.  
* `Left` و `Top` يعيدان تموضع العنصر دون إعادة إنشاء المستند.

> **مشكلة شائعة:** نسيان استخدام النقاط بدلاً من البكسل سيتسبب في ظهور الزر صغيرًا جدًا أو كبيرًا جدًا. دائمًا قم بتحويل قيم البكسل (`px * 72 / DPI`) إذا بدأت من قياسات الشاشة.

## كيفية إضافة زر تفاعلي (اختياري)

يمكن لزر ActiveX تنفيذ ماكرو عند النقر، لكن تضمين كود VBA من C# خارج نطاق سير عمل Aspose.Words النقي. بدلاً من ذلك، يمكنك إضافة خاصية عنصر نائب سيعترف بها Word كاسم ماكرو.

```csharp
// 6️⃣ Assign a macro name (the macro must exist in the Word template).
commandButton.OleFormat.Object = "MyMacroName";
```

عند فتح المستخدم للملف `.docx` المُولد في Word، سيحاول النقر على الزر تشغيل `MyMacroName`. إذا لم يكن الماكرو موجودًا، سيطلب Word من المستخدم إنشائه.

**لماذا قد تستخدم هذا:** بالنسبة للنماذج المؤسسية التي يملأ فيها ماكرو الحقول، يحتاج كود C# فقط إلى وضع الزر؛ منطق الماكرو يعيش في مشروع VBA الخاص بالمستند.

## حفظ المستند والتحقق من النتيجة

```csharp
// 7️⃣ Save the document to the desired folder.
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "CommandButton.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

**الناتج المتوقع:** عند فتح `CommandButton.docx` في Microsoft Word يظهر زر يحمل التسمية **Click Me** موضعه 100 نقطة من الهامش الأيسر و120 نقطة من الأعلى. أبعاد الزر هي **200 نقطة × 80 نقطة**. النقر على الزر يُشغّل عنصر الماكرو (إن كان موجودًا).

## مثال كامل يعمل

فيما يلي البرنامج الكامل القابل للتنفيذ الذي يجمع كل شيء معًا. انسخه في مشروع تطبيق Console جديد، أضف حزمة NuGet الخاصة بـ Aspose.Words، وشغّله.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton, // ActiveX type
            150,                         // Initial width
            100,                         // Initial height
            50,                          // Left offset
            50);                         // Top offset

        // Set button caption and resize.
        commandButton.Caption = "Click Me";
        commandButton.Width = 200;   // Set button size (width)
        commandButton.Height = 80;   // Set button size (height)
        commandButton.Left = 100;    // Re‑position horizontally
        commandButton.Top = 120;     // Re‑position vertically

        // Optional: link to a macro named MyMacroName.
        commandButton.OleFormat.Object = "MyMacroName";

        // Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

شغّل البرنامج، ثم افتح الملف المُولد. سترى **زرًا تفاعليًا** جاهزًا للمزيد من التخصيص.

## الأسئلة المتكررة

| السؤال | الإجابة |
|----------|--------|
| **هل يعمل هذا مع .NET Core؟** | نعم. يدعم Aspose.Words .NET Standard، لذا يعمل نفس الكود على .NET 5/6/7. |
| **هل يمكنني استخدام عناصر تحكم ActiveX أخرى (مثل CheckBox)؟** | بالطبع. استبدل `OleControlType.CommandButton` بـ `OleControlType.CheckBox`، `OleControlType.OptionButton`، إلخ. |
| **ماذا لو احتجت زرًا أكبر على صفحة أفقية؟** | قم بضبط خصائص `Width`، `Height`، `Left`، و`Top` بنسبية. تذكر أن النقاط تبقى كما هي بغض النظر عن اتجاه الصفحة. |
| **هل يلزم وجود ماكرو لجعل الزر قابلًا للنقر؟** | لا. الزر يعمل كعنصر واجهة مستخدم كامل الوظيفة؛ الماكرو يضيف سلوكًا مخصصًا فقط عند النقر. |

## الخلاصة

أنت الآن تعرف كيفية **إنشاء مستند Word** باستخدام Aspose.Words، **إضافة زر أمر**، **ضبط حجم الزر**، وربط الزر اختياريًا بماكرو لسلوك **إضافة زر تفاعلي**. يتيح لك هذا النهج أتمتة إنشاء النماذج، توليد تقارير ديناميكية، أو بناء نماذج أولية لواجهة مستخدم تعتمد على Word مباشرةً من C#.

بعد ذلك، قد تستكشف:

* **كيفية إدراج مربعات اختيار ActiveX** للنماذج الاستطلاعية.  
* **كيفية إضافة محتوى نص غني** حول الزر باستخدام `DocumentBuilder`.  
* **كيفية حماية المستند** مع الحفاظ على وظيفة الزر.  

لا تتردد في تجربة أنواع تحكم مختلفة، أحجام، وأسماء ماكرو لتناسب سيناريوك الخاص. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مستند Word باستخدام Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [إدراج صورة مدمجة في مستند Word باستخدام Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [إنشاء مستند Word مع جدول باستخدام Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}