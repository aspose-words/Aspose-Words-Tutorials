---
category: general
date: 2026-08-20
description: تعلم كيفية إنشاء عنصر تحكم ActiveX، ضبط حجم الزر، وإضافة زر إلى Word
  مع مثال كامل بلغة C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- set button size
- add button to word
- how to insert button
- create clickable button
language: ar
lastmod: 2026-08-20
og_description: إنشاء عنصر تحكم ActiveX في ملف Word باستخدام C#. يوضح هذا الدليل كيفية
  ضبط حجم الزر، إضافة الزر إلى Word، وجعل الزر قابلًا للنقر.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX control
  button
og_title: إنشاء عنصر تحكم ActiveX في Word – دليل C# خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  headline: How to create ActiveX control in a Word document using C#
  type: TechArticle
- description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  name: How to create ActiveX control in a Word document using C#
  steps:
  - name: Why this works
    text: '* `InsertForms2OleControl` tells Word to embed an OLE object of type **CommandButton**,
      which is the classic ActiveX button class. * The width and height arguments
      directly **set button size**; Word translates the values from points (1 pt ≈
      1/72 in). * Naming the control (`Name = "btnSubmit"`) makes'
  - name: Pro tip
    text: 'If you want a square button, set both dimensions to the same value:'
  - name: 1. What if the button does not appear after saving?
    text: '* Verify that the Aspose.Words version supports `InsertForms2OleControl`.
      Versions prior to 22.5 lack this feature. * Ensure the target file format is
      `.docx` or `.doc`. Older formats like `.rtf` cannot store ActiveX objects.'
  - name: 2. Can I insert the button at a specific bookmark?
    text: 'Yes. Move the builder to the bookmark before calling `InsertForms2OleControl`:'
  - name: 3. How to **set button size** dynamically based on text length?
    text: Calculate the required width using the `Graphics.MeasureString` method (from
      `System.Drawing`) and convert pixels to points (`points = pixels * 72 / DPI`).
      Then pass the computed width to `InsertForms2OleControl`.
  - name: 4. Is there a way to add multiple buttons in a loop?
    text: 'Absolutely. Wrap the insertion logic in a `for` loop and adjust the `Left`
      and `Top` properties for each iteration:'
  type: HowTo
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
title: كيفية إنشاء عنصر تحكم ActiveX في مستند Word باستخدام C#
url: /ar/java/integration-interoperability/how-to-create-activex-control-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء عنصر تحكم ActiveX في مستند Word باستخدام C#

إذا كنت بحاجة إلى **إنشاء عنصر تحكم ActiveX** داخل ملف Microsoft Word، فإن هذا الدليل يوضح لك بالضبط كيفية القيام بذلك. سترى كيفية **إضافة زر إلى Word**، ضبط أبعاد الزر، وجعل العنصر قابلًا للنقر—كل ذلك باستخدام برنامج C# قصير ومستقل.

في هذا الدرس ستتمكن من:

* فهم لماذا يُعد عنصر تحكم ActiveX مفيدًا للمستندات التفاعلية في Word.  
* تعلم الشيفرة الدقيقة المطلوبة **لتعيين حجم الزر** وإعطائه تسمية.  
* رؤية كيفية **إنشاء زر قابل للنقر** يمكن ربطه لاحقًا بماكرو أو منطق خارجي.  

الخطوات تعمل مع Aspose.Words .NET 23.12 أو أحدث وتحتاج فقط إلى بيئة تطوير .NET.

> **المتطلبات المسبقة** – لديك ترخيص صالح لـ Aspose.Words (أو تستخدم نسخة التقييم) وVisual Studio 2022 أو أي بيئة تطوير C#.

---

## كيفية إنشاء عنصر تحكم ActiveX في مستند Word

الخطوة الأولى هي إنشاء كائن `Document` فارغ و`DocumentBuilder`. يوفر الـ builder واجهة برمجة تطبيقات عالية المستوى لإدراج كائنات مثل عناصر تحكم ActiveX.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document and obtain a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // The rest of the steps are explained in the following sections.
            InsertActiveXButton(builder);

            // Save the result so you can open it in Word.
            doc.Save("ActiveXButton.docx");
            Console.WriteLine("Document saved as ActiveXButton.docx");
        }
```

طريقة `InsertActiveXButton` (المعرفة لاحقًا) تحتوي على المنطق **لإدراج زر** وتكوينه.

```csharp
        /// <summary>
        /// Inserts a CommandButton ActiveX control, sets its size, name, and caption.
        /// </summary>
        static void InsertActiveXButton(DocumentBuilder builder)
        {
            // Step 2: Insert a CommandButton ActiveX control with the desired size (width: 100, height: 30).
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                "CommandButton", 100, 30);

            // Step 3: Assign a name to the control for later reference.
            commandButton.Name = "btnSubmit";

            // Step 4: Set the caption that will be displayed on the button.
            commandButton.Caption = "Submit";

            // Optional: Position the button on the page (e.g., 100 points from the top left).
            commandButton.Left = 100;
            commandButton.Top = 150;
        }
    }
}
```

تشغيل البرنامج ينشئ **ActiveXButton.docx**. فتح الملف في Word يظهر زرًا معنونا بـ **Submit**. العنصر يعمل بالكامل—النقر عليه سيطلق حدث `CommandButton_Click` القياسي، والذي يمكنك ربطه لاحقًا بماكرو VBA.

### لماذا يعمل هذا

* `InsertForms2OleControl` يخبر Word بدمج كائن OLE من النوع **CommandButton**، وهو الفئة الكلاسيكية لزر ActiveX.  
* معاملات العرض والارتفاع تقوم مباشرةً **بتعيين حجم الزر**؛ Word يحول القيم من النقاط (1 pt ≈ 1/72 in).  
* تسمية العنصر (`Name = "btnSubmit"`) تسهل العثور عليه من VBA (`ActiveDocument.InlineShapes("btnSubmit")`).  

---

## ضبط حجم الزر والتسمية

إذا كنت بحاجة إلى مظهر مختلف، عدل القيم الرقمية في استدعاء `InsertForms2OleControl`. توقيع الطريقة هو:

```csharp
Forms2OleControl InsertForms2OleControl(string progId, double width, double height);
```

* **progId** – المعرف البرمجي لفئة ActiveX (`"CommandButton"` للزر القياسي).  
* **width / height** – الحجم بالنقاط. للحصول على زر بعرض 2 سم، استخدم `width = 56.7` (2 سم ≈ 56.7 pt).  

يمكنك أيضًا تعديل التسمية بعد الإدراج:

```csharp
commandButton.Caption = "Send Request";
```

تغيير التسمية لا يؤثر على الحجم، لكنه يؤثر على المظهر البصري للمستخدم.

### نصيحة احترافية

إذا أردت زرًا مربعًا، ضع نفس القيمة لكل من العرض والارتفاع:

```csharp
Forms2OleControl squareBtn = builder.InsertForms2OleControl("CommandButton", 50, 50);
squareBtn.Caption = "OK";
```

---

## إضافة زر إلى Word وجعله قابلًا للنقر

الكود أعلاه بالفعل **يضيف زرًا إلى Word**. لجعل الزر يؤدي فعلًا، عليك كتابة ماكرو VBA يتعامل مع حدث `Click`. إليك ماكرو بسيط يمكنك لصقه في محرر VBA في Word (`Alt+F11` → Insert → Module):

```vba
Sub btnSubmit_Click()
    MsgBox "You clicked the Submit button!", vbInformation
End Sub
```

نظرًا لأن العنصر مسمى `btnSubmit`، يقوم Word تلقائيًا بربط حدث `Click` بـ `btnSubmit_Click`. هذه هي الطريقة القياسية **لإنشاء زر قابل للنقر** دون الحاجة إلى مكتبات خارجية.

> **ملاحظة:** قد تمنع إعدادات أمان الماكرو في Word عناصر تحكم ActiveX. تأكد من اختيار “Enable all macros” أو “Enable VBA macros” للمستند، أو وقع الماكرو رقمياً للاستخدام الإنتاجي.

---

## أسئلة شائعة: كيفية إدراج زر واستكشاف الأخطاء وإصلاحها

### 1. ماذا لو لم يظهر الزر بعد الحفظ؟

* تحقق من أن نسخة Aspose.Words تدعم `InsertForms2OleControl`. الإصدارات السابقة لـ 22.5 لا تحتوي على هذه الميزة.  
* تأكد من أن تنسيق الملف المستهدف هو `.docx` أو `.doc`. الصيغ القديمة مثل `.rtf` لا يمكنها تخزين كائنات ActiveX.

### 2. هل يمكنني إدراج الزر في إشارة مرجعية محددة؟

نعم. انقل الـ builder إلى الإشارة المرجعية قبل استدعاء `InsertForms2OleControl`:

```csharp
builder.MoveToBookmark("InsertHere");
builder.InsertForms2OleControl("CommandButton", 100, 30);
```

### 3. كيف **ضبط حجم الزر** ديناميكيًا بناءً على طول النص؟

احسب العرض المطلوب باستخدام طريقة `Graphics.MeasureString` (من `System.Drawing`) وحول البكسلات إلى نقاط (`points = pixels * 72 / DPI`). ثم مرّر العرض المحسوب إلى `InsertForms2OleControl`.

### 4. هل هناك طريقة لإضافة عدة أزرار داخل حلقة؟

بالطبع. غلف منطق الإدراج داخل حلقة `for` واضبط خصائص `Left` و `Top` لكل تكرار:

```csharp
for (int i = 0; i < 3; i++)
{
    Forms2OleControl btn = builder.InsertForms2OleControl("CommandButton", 80, 25);
    btn.Name = $"btnOption{i + 1}";
    btn.Caption = $"Option {i + 1}";
    btn.Left = 50;
    btn.Top = 100 + i * 40; // stagger vertically
}
```

---

## النتيجة المتوقعة

عند تشغيل البرنامج وفتح **ActiveXButton.docx**:

* يظهر زر **Submit** واحد بالقرب من أعلى‑يسار الصفحة الأولى.  
* حجم الزر يطابق الأبعاد التي حددتها (`100 pt × 30 pt`).  
* إذا أضفت ماكرو VBA، فإن النقر على الزر يعرض صندوق رسالة: “You clicked the Submit button!”.

لقد نجحت الآن في **إنشاء عنصر تحكم ActiveX**، **تعيين حجم الزر**، و**إضافة زر إلى Word** مع تعلمك أيضًا **كيفية إدراج زر** و**إنشاء زر قابل للنقر** لمهام الأتمتة المستقبلية.

---

## الخلاصة

في هذا الدرس تعلمت كيفية **إنشاء عنصر تحكم ActiveX** داخل مستند Word باستخدام C#. باتباع الخطوات يمكنك **تعيين حجم الزر**، إعطاء العنصر اسمًا ذا معنى، و**إضافة زر إلى Word** ليصبح **زرًا قابلًا للنقر** مرتبطًا بماكرو VBA.  

من هنا يمكنك استكشاف:

* ربط الزر بإضافة COM .NET بدلاً من VBA.  
* استخدام فئات ActiveX أخرى مثل `CheckBox` أو `ComboBox`.  
* أتمتة إنشاء نماذج كاملة تحتوي على عدة عناصر تحكم.

لا تتردد في تجربة أحجام مختلفة

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [إنشاء مستند Word مع صورة عائمة في .NET](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [إنشاء مستند Word مع رأس وتذييل باستخدام Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [إنشاء PDF قابل للوصول من Word – دليل كامل](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}