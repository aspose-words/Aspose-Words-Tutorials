---
category: general
date: 2026-08-04
description: إنشاء مستند Word فارغ وإدراج زر أمر باستخدام Aspose.Words. تعلم كيفية
  ضبط حجم الزر وإضافة زر قابل للنقر في C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert command button
- add clickable button
- set button size
- create command button
language: ar
lastmod: 2026-08-04
og_description: إنشاء مستند Word فارغ باستخدام Aspose.Words وإدراج زر أمر. يوضح هذا
  الدليل كيفية ضبط حجم الزر، إضافة زر قابل للنقر، وحفظ الملف.
og_image_alt: Screenshot of a Word document containing a clickable command button
  created with C#
og_title: إنشاء مستند Word فارغ وإضافة زر أمر – دليل C# كامل
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  headline: Create blank word document with a command button – step‑by‑step guide
  type: TechArticle
- description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  name: Create blank word document with a command button – step‑by‑step guide
  steps:
  - name: The ProgID of the OLE control – `"CommandButton"` for a standard button.
    text: The ProgID of the OLE control – `"CommandButton"` for a standard button.
  - name: A `Rectangle` that defines the **set button size** and position.
    text: A `Rectangle` that defines the **set button size** and position.
  - name: The caption that appears on the button.
    text: The caption that appears on the button.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: إنشاء مستند Word فارغ مع زر أمر – دليل خطوة بخطوة
url: /ar/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word فارغ مع زر أمر – دليل خطوة بخطوة

إذا كنت بحاجة إلى **إنشاء مستند Word فارغ** يحتوي على زر تفاعلي، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك باستخدام Aspose.Words for .NET. ستتعلم **إدراج زر أمر**، تعديل مظهره، وجعله قابلًا للنقر—كل ذلك في بضع أسطر من C#.

يغطي الدليل كل شيء من إعداد المشروع إلى حفظ الملف النهائي، بحيث يمكنك نسخ‑لصق الحل الكامل في تطبيقك الخاص. وعلى طول الطريق سنشرح أيضًا كيفية **إضافة زر قابل للنقر**، **تحديد حجم الزر**، و **إنشاء زر أمر** برمجيًا.

## المتطلبات المسبقة

* .NET 6.0 SDK أو أحدث مثبت.
* Visual Studio 2022 (أو أي بيئة تطوير تدعم .NET).
* حزمة NuGet لـ Aspose.Words for .NET (`Aspose.Words` الإصدار 23.12 أو أحدث).
* إلمام أساسي بـ C# والبرمجة الكائنية التوجه.

لا تحتاج إلى أي تجميعات Office interop إضافية لأن Aspose.Words يعمل بشكل مستقل تمامًا عن Microsoft Word.

## الخطوة 1: إعداد مشروع .NET

أنشئ تطبيقًا من نوع console سيستضيف كود أتمتة Word.

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

هذا الأمر ينشئ مجلدًا جديدًا باسم `WordButtonDemo` يحتوي على ملف `Program.cs` جاهز للتنفيذ ويضيف مكتبة Aspose.Words.

## الخطوة 2: إنشاء مستند Word فارغ

العملية الأولى هي **إنشاء مستند Word فارغ**. توفر Aspose.Words فئة `Document` التي تمثل ملف Word فارغ جاهز للاستخدام.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a new, empty Word document.
Document doc = new Document();
```

إنشاء مستند فارغ يمنحك لوحة رسم نظيفة يمكنك إضافة فقرات، جداول، أو في هذه الحالة زر أمر OLE.

## الخطوة 3: تهيئة DocumentBuilder

`DocumentBuilder` هو المساعد الذي يتيح لك إدراج محتوى في المستند. تحتاج إلى ربطه بالمستند الذي أنشأته للتو.

```csharp
// Attach a DocumentBuilder to the empty document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

يحافظ الـ builder على موضع المؤشر الحالي، لذا أي إدراج لاحق يحدث بالضبط حيث تريد.

## الخطوة 4: إدراج زر أمر

الآن نقوم **بإدراج زر أمر** (OLE `Forms2OleControl`) في المستند. تتطلب الطريقة `InsertForms2OleControl` ثلاثة معطيات:

1. معرف ProgID لعنصر OLE – `"CommandButton"` لزر قياسي.
2. `Rectangle` يحدد **حجم الزر** وموقعه.
3. التسمية التي تظهر على الزر.

```csharp
// Define the button's position (x, y) and size (width, height).
Rectangle buttonRect = new Rectangle(0, 0, 120, 30); // 120 px wide, 30 px high

// Insert the command button with the desired caption.
Forms2OleControl cmdButton = builder.InsertForms2OleControl(
    "CommandButton",   // ProgID for a CommandButton control
    buttonRect,        // Position and size
    "Click Me");       // Caption displayed on the button
```

عند فتح المستند في Word، يتصرف الزر كأي عنصر نموذج أصلي—يمكنك النقر عليه، وسيقوم Word بتنفيذ الماكرو المرتبط (إذا كان موجودًا). هذا يلبي متطلب **إضافة زر قابل للنقر**.

### لماذا نستخدم Forms2OleControl؟

`Forms2OleControl` يدمج كائن OLE مباشرةً في ملف DOCX، محافظًا على خصائص العنصر دون الحاجة إلى تجميع Word Interop. إنها الطريقة الأكثر موثوقية لـ **إنشاء زر أمر** يعمل عبر إصدارات Word.

## الخطوة 5: تخصيص الزر (اختياري)

قد ترغب في **تحديد حجم الزر** بدقة أكبر أو تغيير خصائص إضافية مثل الخط أو لون الخلفية. تعرض Aspose.Words كائن OLE الأساسي، مما يسمح بمزيد من التعديلات.

```csharp
// Example: change the button's background color (requires OLE automation).
// Note: This step is optional and demonstrates additional customization.
cmdButton.OleFormat.Icon = true; // Show an icon instead of the default appearance.
```

إذا كنت بحاجة إلى حجم مختلف، ما عليك سوى تعديل قيم `Rectangle` في الخطوة 4. تُقاس الإحداثيات بالنقاط (1 pt = 1/72 inch)، لذا فإن `120` تعادل تقريبًا عرض 1.67 إنش.

## الخطوة 6: حفظ المستند

أخيرًا، احفظ المستند على القرص. يحتوي الملف الناتج على **مستند Word فارغ** مع زر أمر يعمل بالكامل.

```csharp
// Save the document as a .docx file.
doc.Save("CommandButtonDemo.docx");
```

عند فتح `CommandButtonDemo.docx` في Microsoft Word، سترى زرًا بعنوان “Click Me”. النقر على الزر سيظهر حوار الماكرو الافتراضي ما لم تقم بإرفاق ماكرو مخصص.

## الكود المصدر الكامل

فيما يلي البرنامج الكامل الذي يمكنك نسخه إلى `Program.cs`. يتضمن جميع الخطوات المذكورة أعلاه ويُترجم دون تعديل.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordButtonDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Create a blank word document.
            Document doc = new Document();

            // Step 3: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 4: Define button size and insert command button.
            Rectangle buttonRect = new Rectangle(0, 0, 120, 30);
            Forms2OleControl cmdButton = builder.InsertForms2OleControl(
                "CommandButton",
                buttonRect,
                "Click Me");

            // Optional: further customization (e.g., set icon).
            // cmdButton.OleFormat.Icon = true;

            // Step 6: Save the document.
            doc.Save("CommandButtonDemo.docx");

            System.Console.WriteLine("Document created successfully.");
        }
    }
}
```

### النتيجة المتوقعة

تشغيل البرنامج ينتج `CommandButtonDemo.docx`. فتح الملف في Word يظهر:

* صفحة واحدة تحتوي على زر بعنوان **Click Me**.
* الزر يحترم **حجم الزر** (120 × 30 نقطة).
* النقر على الزر يُفعل سلوك زر الأمر الافتراضي في Word، مؤكدًا أن عملية **إضافة زر قابل للنقر** نجحت.

## الأسئلة الشائعة والحالات الخاصة

| السؤال | الجواب |
|----------|--------|
| **هل يعمل هذا مع ملفات .doc؟** | نعم. غيّر امتداد الملف في `doc.Save("file.doc")`. يتم تخزين عنصر OLE أيضًا في الصيغة الثنائية القديمة. |
| **ماذا لو احتجت إلى أزرار متعددة؟** | استدعِ `InsertForms2OleControl` بشكل متكرر، مع تعديل `Rectangle` لكل زر جديد لتجنب التداخل. |
| **هل يمكن إرفاق ماكرو بالزر؟** | الزر نفسه لا يحتوي على كود ماكرو. يجب إضافة ماكرو VBA إلى المستند يدويًا أو عبر مجموعة `Modules` لكائن `Document`. |
| **هل الزر مرئي عند تصدير PDF؟** | عند تصدير DOCX إلى PDF باستخدام Aspose.Words، يُعرض الزر كصورة ثابتة، وليس كعنصر تفاعلي. |
| **ما إصدارات Word المدعومة؟** | زر الأمر OLE يعمل في Word 2007 وما بعده، لأنه يتبع مواصفة Forms2.0 القياسية. |

## الخلاصة

أنت الآن تعرف كيف **إنشاء مستند Word فارغ**، **إدراج زر أمر**، **إضافة زر قابل للنقر**، و **تحديد حجم الزر** باستخدام Aspose.Words for .NET. يوضح المثال الكامل سير عمل **إنشاء زر أمر** من البداية إلى النهاية، مما يمنحك أساسًا قويًا لمهام أتمتة Word المتقدمة.

## الخطوات التالية

* استكشف عناصر OLE أخرى (مثل `CheckBox`، `ListBox`) عن طريق تغيير ProgID في `InsertForms2OleControl`.
* اجمع الزر مع ماكرو VBA لتنفيذ إجراءات مخصصة عندما ينقر المستخدم عليه.
* استخدم `DocumentBuilder` من Aspose.Words لإضافة محتوى إضافي مثل الجداول، الصور، أو الهوامش قبل إدراج الزر.
* جرّب قيم **تحديد حجم الزر** لتتناسب مع متطلبات تخطيط مستندك.

برمجة سعيدة، واستمتع بإنشاء مستندات Word أكثر غنىً مع عناصر تحكم تفاعلية!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مجموعة أشكال في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [إنشاء مستند Word فارغ مع شكل مستطيل مظلّل – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [إنشاء مستند Word باستخدام Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}