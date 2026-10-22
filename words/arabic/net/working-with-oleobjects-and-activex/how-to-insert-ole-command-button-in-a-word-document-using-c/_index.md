---
category: general
date: 2026-10-07
description: تعلم كيفية إدراج زر أمر OLE في مستند Word باستخدام Aspose.Words C#. دليل
  خطوة بخطوة يغطي DocumentBuilder والخصائص وحفظ الملف.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert OLE command button
- Aspose.Words OLE control
- C# DocumentBuilder InsertForms2OleControl
- OleControlType CommandButton
- Word OLE command button
language: ar
lastmod: 2026-10-07
og_description: إدراج زر أمر OLE في مستند Word باستخدام C#. اتبع هذا الدرس المختصر
  لإضافة زر CommandButton وتكوينه وحفظه بوظيفة كاملة باستخدام Aspose.Words.
og_image_alt: Insert OLE command button example in Word document
og_title: إدراج زر أمر OLE في Word باستخدام C# – دليل Aspose.Words الكامل
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  headline: How to insert OLE command button in a Word document using C#
  type: TechArticle
- description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  name: How to insert OLE command button in a Word document using C#
  steps:
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for building Word documents programmatically.
      * `InsertForms2OleControl` tells Aspose.Words to embed a **Forms2 OLE control**,
      which is the legacy Word form technology that supports command buttons, check
      boxes, etc. * The `OleControlType.CommandButton` enum va'
  - name: 1. What if the button does not appear where I expect?
    text: '* Word uses points, not pixels. Convert screen pixels to points (`points
      = pixels * 72 / DPI`). * Ensure the rectangle does not intersect page margins;
      otherwise Word may shift the control.'
  - name: 2. Can I insert the button into an existing document?
    text: Yes. Load the document with `new Document("Existing.docx")` and use the
      same `DocumentBuilder` workflow. Just remember to move the builder’s cursor
      (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.)
      before calling `InsertForms2OleControl`.
  - name: 3. How do I attach a macro to the button?
    text: 'Aspose.Words does not create VBA code, but you can embed a macro after
      the document is generated:'
  - name: 4. Does this work with .NET Core on Linux?
    text: The OLE control is a Windows‑specific feature because it relies on COM.
      On Linux the button will be inserted, but it will appear as a static picture
      without interactive behavior. For cross‑platform interactive forms, consider
      using content controls (`StructuredDocumentTag`) instead.
  - name: 5. What if I need a different size or multiple buttons?
    text: Create additional `Rectangle` objects with unique coordinates and repeat
      the `InsertForms2OleControl` call. Each button can have its own `Caption` and
      `Name`.
  type: HowTo
tags:
- Aspose.Words
- C#
- OLE
- Word automation
title: كيفية إدراج زر أمر OLE في مستند Word باستخدام C#
url: /ar/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إدراج زر أمر OLE في مستند Word باستخدام C#

إذا كنت بحاجة إلى **إدراج زر أمر OLE** في ملف Word برمجياً، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك باستخدام Aspose.Words for .NET. سواءً كنت تبني تقريرًا يُملأ بنموذج أو تقوم بأتمتة قالب يتطلب تفاعل المستخدم، فإن الخطوات أدناه تقدم لك حلًا كاملاً وقابلًا للتنفيذ.

ستتعلم كيفية إنشاء مستند فارغ، واستخدام `DocumentBuilder` لوضع `Forms2OleControl`، وتعيين تسمية الزر واسمه، وأخيرًا حفظ الملف بامتداد `.docx`. لا تحتاج إلى أدوات خارجية بخلاف مكتبة Aspose.Words.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.7+)
* ترخيص صالح لـ Aspose.Words for .NET أو مفتاح تقييم مجاني
* Visual Studio 2022 (أو أي بيئة تطوير C# تفضلها)
* إلمام أساسي بصياغة C# ومفاهيم OLE في Word

> **نصيحة احترافية:** إذا كنت تستخدم نسخة التقييم المجانية، سيحتوي المستند المُولد على علامة مائية صغيرة. النسخة المرخصة تزيلها تلقائيًا.

## الخطوة 1: تثبيت Aspose.Words

أضف حزمة Aspose.Words إلى مشروعك عبر NuGet:

```bash
dotnet add package Aspose.Words
```

تتضمن الحزمة مساحات الأسماء `Aspose.Words.Drawing` و `Aspose.Words.Drawing.Ole` المطلوبة للتحكم في OLE.

## الخطوة 2: إدراج زر أمر OLE باستخدام DocumentBuilder

جوهر البرنامج التعليمي هو طريقة `InsertForms2OleControl`. تقوم بإنشاء **Forms2 OLE CommandButton** في موقع وحجم محددين.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System.Drawing;

// Create a new blank document and a DocumentBuilder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Define the rectangle where the button will appear (x, y, width, height)
// Values are in points (1 point = 1/72 inch)
Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

// Insert the Forms2 OLE CommandButton control
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // <-- OleControlType CommandButton (secondary keyword)
    buttonRect);

// Set the button's caption and name properties
commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";
```

### لماذا يعمل هذا

* `DocumentBuilder` هو الـ API الأساسي لبناء مستندات Word برمجياً.  
* `InsertForms2OleControl` يخبر Aspose.Words بدمج **Forms2 OLE control**، وهي تقنية النماذج القديمة في Word التي تدعم أزرار الأوامر، ومربعات الاختيار، وما إلى ذلك.  
* قيمة التعداد `OleControlType.CommandButton` تحدد أن التحكم المُدرج هو **زر أمر** — النوع الدقيق الذي طلبت **إدراج زر أمر OLE**.  
* `Rectangle` يحدد الموضع البصري. عدّل إحداثيات X/Y أو العرض/الارتفاع لتتناسب مع تخطيطك.

## الخطوة 3: حفظ المستند

بعد ضبط الزر، اكتب المستند إلى القرص. يمكنك اختيار أي تنسيق تدعمه Aspose.Words (`.docx`, `.pdf`, `.odt`, …). في هذا الدليل سنحفظه كمستند Word.

```csharp
// Choose a folder you have write access to
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");

// Save the document containing the button
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

عند فتح `CommandButton.docx` في Microsoft Word، سترى زرًا قابلًا للنقر يحمل التسمية **Click Me**. الضغط عليه في Word يفتح مربع الحوار الافتراضي “Run Macro” لأن الزر هو عنصر تحكم نموذج OLE؛ يمكنك لاحقًا إرفاق ماكرو أو كود VBA إذا لزم الأمر.

## الخطوة 4: التحقق من النتيجة (المخرجات المتوقعة)

افتح الملف المُولد:

1. يظهر الزر عند الإحداثيات التي حددتها (تقريبًا 1.4 in من اليسار وأعلى الصفحة).  
2. التسمية تظهر **Click Me**.  
3. خاصية الاسم (`cmdSubmit`) مرئية في لوحة **Developer → Properties** في Word، وهو مفيد عندما تحتاج إلى الإشارة إلى التحكم من VBA.

![مثال على إدراج زر أمر OLE في مستند Word](insert-ole-button.png)

*نص بديل للصورة*: **مثال على إدراج زر أمر OLE في مستند Word** (يتضمن الكلمة المفتاحية الأساسية للولوجية وتحسين محركات البحث).

## الحالات الخاصة والأسئلة الشائعة

### 1. ماذا لو لم يظهر الزر في الموضع المتوقع؟

* يستخدم Word النقاط وليس البكسل. حوّل بكسلات الشاشة إلى نقاط (`points = pixels * 72 / DPI`).  
* تأكد من أن المستطيل لا يتقاطع مع هوامش الصفحة؛ وإلا قد يقوم Word بتحريك التحكم.

### 2. هل يمكنني إدراج الزر في مستند موجود؟

نعم. حمّل المستند باستخدام `new Document("Existing.docx")` واستخدم نفس سير عمل `DocumentBuilder`. فقط تذكّر تحريك مؤشر الـ builder (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, إلخ) قبل استدعاء `InsertForms2OleControl`.

### 3. كيف أرفق ماكرو بالزر؟

Aspose.Words لا ينشئ كود VBA، لكن يمكنك تضمين ماكرو بعد توليد المستند:

```csharp
// Load the generated document
Document doc = new Document(outputPath);

// Add a VBA macro module (requires Aspose.Words licensing)
doc.VbaProject.Modules.Add("Module1", "Sub cmdSubmit_Click()\n MsgBox \"Button clicked!\"\nEnd Sub");

// Save again
doc.Save(outputPath);
```

### 4. هل يعمل هذا مع .NET Core على Linux؟

عنصر التحكم OLE هو ميزة خاصة بـ Windows لأنها تعتمد على COM. على Linux سيُدرج الزر، لكنه سيظهر كصورة ثابتة دون سلوك تفاعلي. للنماذج التفاعلية متعددة المنصات، فكر في استخدام عناصر التحكم بالمحتوى (`StructuredDocumentTag`) بدلاً من ذلك.

### 5. ماذا لو أحتاج إلى حجم مختلف أو عدة أزرار؟

أنشئ كائنات `Rectangle` إضافية بإحداثيات فريدة وكرر استدعاء `InsertForms2OleControl`. يمكن لكل زر أن يمتلك `Caption` و `Name` خاصين به.

## مثال كامل يعمل

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑ولصقه في تطبيق Console. يتضمن جميع توجيهات `using` الضرورية، ومعالجة الأخطاء، وتعليقات توضيحية.

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

namespace OleCommandButtonDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document
                Document document = new Document();
                DocumentBuilder builder = new DocumentBuilder(document);

                // 2️⃣ Define button rectangle (x, y, width, height) in points
                Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

                // 3️⃣ Insert the Forms2 OLE CommandButton control
                Forms2OleControl commandButton = builder.InsertForms2OleControl(
                    OleControlType.CommandButton,
                    buttonRect);

                // 4️⃣ Set visual properties
                commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
                commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";

                // 5️⃣ Save the document
                string outputPath = Path.Combine(
                    Environment.CurrentDirectory,
                    "CommandButton.docx");

                document.Save(outputPath);
                Console.WriteLine($"Document saved successfully: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Error: {ex.Message}");
            }
        }
    }
}
```

شغّل البرنامج، افتح `CommandButton.docx` المُولد، وسترى زر **Click Me** جاهزًا لمزيد من التخصيص.

## الخلاصة

أنت الآن تعرف كيف **تدرج زر أمر OLE** في مستند Word باستخدام C# و Aspose.Words. غطى الدليل:

* تثبيت حزمة Aspose.Words  
* استخدام `DocumentBuilder.InsertForms2OleControl` مع `OleControlType.CommandButton`  
* ضبط خصائص الزر (`Caption`, `Name`)  
* حفظ المستند والتحقق من النتيجة  

من هنا يمكنك استكشاف مواضيع ذات صلة مثل **Aspose.Words OLE control** لمربعات الاختيار، قوائم السحب، أو دمج أوراق Excel كاملة. يمكنك أيضًا تجربة أتمتة **Word OLE command button** في قوالب أكبر، أو استبدال عناصر التحكم OLE بـ **content controls** الحديثة لدعم أفضل عبر المنصات.

لا تتردد في تعديل قيم المستطيل، إضافة أزرار متعددة، أو إرفاق ماكرو VBA لتلبية احتياجات تطبيقك. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف طرق تنفيذ بديلة في مشاريعك.

- [Insert Ole Object In Word Document](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object/)
- [Insert Ole Object In Word Document As Icon](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/)
- [Insert Ole Object In Word With Ole Package](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}