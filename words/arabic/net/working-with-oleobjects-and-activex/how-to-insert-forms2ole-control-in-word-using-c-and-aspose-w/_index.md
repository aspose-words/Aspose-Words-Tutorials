---
category: general
date: 2026-11-22
description: تعلم كيفية إدراج عنصر Forms2Ole في Word باستخدام C#. يغطي هذا الدليل
  خطوة بخطوة DocumentBuilder، وضع زر الأمر، وحفظ ملف .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert forms2ole control word
- Aspose.Words
- DocumentBuilder
- command button
- C# Word automation
language: ar
lastmod: 2026-11-22
og_description: إدراج عنصر Forms2Ole في Word باستخدام C#. اتبع هذا الدليل لإضافة زر
  أمر باستخدام Aspose.Words و DocumentBuilder.
og_image_alt: Screenshot of a Word document showing an inserted Forms2Ole command
  button created with C#
og_title: إدراج عنصر Forms2Ole في Word باستخدام C# – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn to insert a Forms2Ole control in Word with C#. This step‑by‑step
    guide covers DocumentBuilder, command button placement, and saving the .docx.
  headline: How to insert Forms2Ole control in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: كيفية إدراج عنصر التحكم Forms2Ole في Word باستخدام C# و Aspose.Words
url: /ar/net/working-with-oleobjects-and-activex/how-to-insert-forms2ole-control-in-word-using-c-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إدراج عنصر Forms2Ole في Word باستخدام C# و Aspose.Words

إذا كنت بحاجة إلى **إدراج عنصر Forms2Ole في Word**، فإن هذا الدليل يوضح لك بالضبط كيفية القيام بذلك باستخدام C#. سواء كنت تبني قالبًا قابلًا للملء أو تقوم بأتمتة إنشاء النماذج، فإن الحل أدناه يتيح لك إضافة زر أمر برمجيًا.

سوف تتعلم كيفية إنشاء مستند فارغ، واستخدام `DocumentBuilder` لوضع العنصر، وحفظ النتيجة كملف `.docx`. يغطي الدليل أيضًا المشكلات الشائعة، مثل أنظمة الإحداثيات والتوافق مع إصدارات Word القديمة.

## المتطلبات المسبقة

* .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.6+)
* Aspose.Words for .NET (حزمة NuGet `Aspose.Words`)
* فهم أساسي لـ C# ونموذج كائنات Word
* بيئة تطوير متكاملة مثل Visual Studio أو VS Code

## الخطوة 1: إعداد المشروع واستيراد المساحات الاسمية

أنشئ تطبيقًا جديدًا من نوع console وأضف حزمة Aspose.Words:

```bash
dotnet new console -n InsertForms2OleDemo
cd InsertForms2OleDemo
dotnet add package Aspose.Words
```

في `Program.cs` استورد المساحات الاسمية المطلوبة:

```csharp
using System;
using System.Drawing;               // for Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;        // for Forms2OleControl
```

> **نصيحة احترافية:** استخدم أحدث نسخة من Aspose.Words للحصول على الدعم الكامل لواجهة برمجة التطبيقات `Forms2OleControl`.

## الخطوة 2: إنشاء مستند فارغ وتهيئة DocumentBuilder

تمثل الفئة `Document` ملف Word، بينما توفر `DocumentBuilder` طرقًا لإدراج المحتوى.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Initialize DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` يعمل كالمؤشر؛ بعد هذا السطر يمكنك بدء وضع العناصر في أي مكان داخل المستند.

## الخطوة 3: تحديد موضع الزر وحجمه

يقيس Word الإحداثيات بالنقاط (1 pt ≈ 1/72 in). يصف الهيكل `Rectangle` من `System.Drawing` حدود العنصر.

```csharp
// Step 3: Define the button's position and size (x, y, width, height)
Rectangle buttonBounds = new Rectangle(0, 0, 100, 30); // 100 pt wide, 30 pt tall
```

* `0,0` يضع العنصر في الزاوية العلوية اليسرى من الصفحة الحالية.
* عدل `x` و `y` لتحريك الزر إلى مكان آخر (مثال: `new Rectangle(150, 200, 100, 30)`).

## الخطوة 4: إدراج زر أمر Forms2Ole

الآن استخدم `InsertForms2OleControl` لإضافة العنصر. تتطلب الطريقة نوع العنصر، اسمًا، والحدود المحددة أعلاه.

```csharp
// Step 4: Insert a Forms2Ole command button named "ClickMe"
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,   // type of control
    "ClickMe",                  // internal name (used for VBA or macros)
    buttonBounds);              // position and size
```

الكائن `Forms2OleControl` المرجع يتيح لك تعديل خصائص مثل `Enabled`، `Visible`، أو حتى إرفاق اسم ماكرو لاحقًا.

### لماذا نستخدم Forms2Ole؟

* **التوافق مع الإصدارات القديمة** – تعمل عناصر Forms2Ole في Word 97‑2003 (`.doc`) والملفات `.docx` الأحدث.
* **دعم الماكرو** – يمكنها تشغيل ماكروهات VBA، مما يجعلها مثالية للقوالب التفاعلية.
* **تحديد موقع دقيق** – على عكس عناصر التحكم بالمحتوى، يمكنك التحكم في الإحداثيات الدقيقة.

## الخطوة 5: حفظ المستند

أخيرًا، احفظ الملف على القرص. اختر مجلدًا لديك صلاحية كتابة فيه.

```csharp
// Step 5: Save the document to see the inserted button
string outputPath = @"./output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

افتح `output.docx` في Microsoft Word. سترى زرًا معنونا بـ **ClickMe** في الزاوية العلوية اليسرى من الصفحة الأولى. النقر عليه في Word لن يفعل شيئًا حتى تقوم بتعيين ماكرو، لكن العنصر يعمل بشكل كامل.

## معالجة الحالات الحدية الشائعة

| الحالة | طريقة المعالجة |
|-----------|-------------------|
| **الزر يظهر خارج الصفحة** | تحقق من أن إحداثيات `Rectangle` ضمن هوامش الصفحة. استخدم `builder.PageSetup.PageWidth` و `PageHeight` لحساب حدود آمنة. |
| **العنصر غير مرئي في إصدارات Word القديمة** | احفظ المستند كملف `.doc` (`doc.Save("output.doc", SaveFormat.Doc)`) لضمان توافق Forms2Ole مع Word 97‑2003. |
| **الحاجة لتغيير التسمية** | بعد الإدراج، عيّن `commandButton.Caption = "Submit";`. |
| **تعيين ماكرو** | عيّن `commandButton.MacroName = "MyMacro"`؛ يجب أن يكون الماكرو موجودًا في مشروع VBA الخاص بالمستند. |
| **أزرار متعددة** | كرّر الخطوة 4 مع قيم `Rectangle` مختلفة وأسماء فريدة. |

## مثال كامل قابل للتنفيذ

بجمع كل شيء معًا، إليك برنامجًا مستقلًا يمكنك نسخه، لصقه، وتشغيله:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace InsertForms2OleDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document doc = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Define button bounds (x, y, width, height) in points
            Rectangle buttonBounds = new Rectangle(0, 0, 100, 30);

            // Insert a Forms2Ole command button named "ClickMe"
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                "ClickMe",
                buttonBounds);

            // Optional: set button caption
            commandButton.Caption = "Click Me!";

            // Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**الناتج المتوقع:** بعد تشغيل البرنامج، يفتح `output.docx` في Word مع زر قابل للنقر معنون *Click Me!* موضعه في الزاوية العلوية اليسرى من الصفحة الأولى.

## الخلاصة

أنت الآن تعرف كيفية **إدراج عنصر Forms2Ole في Word** باستخدام C# و Aspose.Words. العملية تشمل إنشاء `Document`، تحديد موقع `Rectangle`، واستدعاء `InsertForms2OleControl` عبر `DocumentBuilder`. مع عينة الكود الكاملة وإرشادات الحالات الحدية، يمكنك دمج أزرار الأوامر في أي سير عمل Word مؤتمت.

### الخطوات التالية

* استكشف قيم `ControlType` أخرى مثل `CheckBox` أو `OptionButton`.
* دمج عناصر Forms2Ole مع ماكروهات VBA للنماذج التفاعلية.
* استخدم `DocumentBuilder.MoveTo` لوضع الأزرار في فقرات أو جداول محددة.
* راجع وثائق Aspose.Words **Forms2Ole** للحصول على إعدادات خصائص متقدمة.

برمجة سعيدة، واستمتع بإنشاء مستندات Word أغنى باستخدام C# و Aspose.Words!

## ما الذي ينبغي أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [كيفية إدراج زر أمر OLE في مستند Word باستخدام C#](/words/english/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/)
- [كيفية إضافة عنصر ActiveX في Word باستخدام Aspose.Words – دليل خطوة بخطوة](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/)
- [إضافة زر أمر إلى مستند Word باستخدام Aspose.Words – دليل كامل](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}