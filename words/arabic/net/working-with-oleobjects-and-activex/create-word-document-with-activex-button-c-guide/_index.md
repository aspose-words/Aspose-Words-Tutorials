---
category: general
date: 2026-07-19
description: إنشاء مستند Word باستخدام Aspose.Words C# وتعلم كيفية إضافة زر أمر ActiveX،
  وضبط حجم الزر، وإدراج الزر برمجيًا.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to add activex
- insert command button
- set button size
- how to insert button
language: ar
lastmod: 2026-07-19
og_description: إنشاء مستند Word باستخدام Aspose.Words C# وتضمين زر أمر ActiveX في
  ثوانٍ. اتبع الدليل خطوة بخطوة لتحديد حجم الزر وإدراجه بسهولة.
og_image_alt: Screenshot of a Word document showing an ActiveX command button inserted
  via C#
og_title: إنشاء مستند Word مع زر ActiveX – دليل C#
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  headline: Create Word Document with ActiveX Button – C# Guide
  type: TechArticle
- description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  name: Create Word Document with ActiveX Button – C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works on .NET Framework 4.7+). - A valid
      Aspose.Words for .NET license (or a free evaluation key). - Visual Studio 2022
      (or any IDE you like). - Basic familiarity with C# and object‑oriented programming.'
  - name: Platform Limitations
    text: '- ActiveX controls only run on the Windows version of Word. If your audience
      includes macOS or Word Online users, the button will appear as a static image.
      - Some corporate environments disable ActiveX for security; you may need to
      sign the document or inform users to enable content.'
  - name: VBA Interaction (Optional)
    text: If you want the button to execute a macro, you’ll have to add a VBA project
      to the document after saving. Aspose.Words does not generate VBA code automatically,
      but you can use the `Document.VbaProject` API to inject it.
  - name: Naming Collisions
    text: Always give each control a unique `Name`. Re‑using the same name can cause
      runtime errors when Word tries to resolve the control.
  - name: Performance Tip
    text: When inserting many controls, reuse a single `DocumentBuilder` instance
      and avoid calling `doc.Save` inside a loop. Batch the inserts and save once
      at the end.
  - name: What’s Next?
    text: '- **Style the button** – change fonts, colors, or add an image background.
      - **Attach VBA macros** – make the button perform calculations or launch external
      programs. - **Combine with other controls** – checkboxes, list boxes, or even
      embedded Excel sheets.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: إنشاء مستند Word مع زر ActiveX – دليل C#
url: /ar/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word مع زر ActiveX – دليل C# كامل

هل تساءلت يومًا كيف **إنشاء مستند Word** يحتوي على زر ActiveX فعال؟ ربما تقوم بأتمتة تقرير وتحتاج إلى عنصر تحكم “Approve” قابل للنقر داخل الملف. في هذا الدرس سنستعرض ذلك بالضبط—باستخدام Aspose.Words for .NET لإضافة زر أمر ActiveX، ضبط حجمه، وإدراجه حيث تحتاجه.  

إذا سألت نفسك يومًا *how to add activex* دون فتح Word يدويًا، فأنت في المكان الصحيح. في النهاية ستحصل على مثال قابل للتنفيذ، شرح واضح لكل خطوة، ونصائح للتعامل مع المشكلات الشائعة.

## ما ستتعلمه

- كيفية إعداد Aspose.Words في مشروع C#  
- الكود الدقيق **إنشاء مستند Word** وإدراج زر أمر ActiveX  
- طرق **ضبط حجم الزر** وتخصيص التسمية والاسم  
- الطريقة الصحيحة لـ **إدراج زر أمر** و**كيفية إدراج زر** في أي موقع داخل المستند  
- اعتبارات الحالات الخاصة (إصدار Word، حدود المنصة، تحذيرات الأمان)

### المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضًا على .NET Framework 4.7+).  
- رخصة صالحة لـ Aspose.Words for .NET (أو مفتاح تقييم مجاني).  
- Visual Studio 2022 (أو أي بيئة تطوير تفضلها).  
- إلمام أساسي بـ C# والبرمجة الكائنية.

لا توجد مكتبات طرف ثالث أخرى مطلوبة.

---

## الخطوة 1: إنشاء مستند Word – إعداد المشروع

قبل أن نتمكن من **إدراج زر أمر**، نحتاج إلى ملف Word فارغ للعمل معه. تُظهر هذه الخطوة أيضًا نمط “إنشاء مستند Word” الكلاسيكي باستخدام Aspose.Words.

```csharp
// Add the Aspose.Words NuGet package first:
//   dotnet add package Aspose.Words
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

// 1️⃣  Initialize a new blank document.
Document doc = new Document();

// 1️⃣  Create a DocumentBuilder – it lets us place content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **لماذا هذا مهم:** `Document` تمثل ملف .docx بالكامل، بينما `DocumentBuilder` يتتبع موضع المؤشر الحالي. جميع الإدراجات اللاحقة (بما في ذلك عنصر التحكم ActiveX الخاص بنا) تتم نسبةً إلى هذا الـ builder.

---

## الخطوة 2: كيفية إضافة ActiveX – بناء عنصر التحكم CommandButton

الآن بعد أن أصبح المستند موجودًا، دعنا نتعامل مع جزء **how to add activex**. تُوفر Aspose.Words الفئة `Forms2OleControl` لكائنات ActiveX. هنا سننشئ زر أمر ونُكوّن خصائصه، بما في ذلك متطلب **ضبط حجم الزر**.

```csharp
// 2️⃣  Create the ActiveX command button.
Forms2OleControl commandButton = new Forms2OleControl(
    doc,                     // Parent document
    Forms2OleControlType.CommandButton); // Control type

// Configure appearance – this is where we **set button size**.
commandButton.Width = 120;          // Width in points (≈1.67 inches)
commandButton.Height = 30;          // Height in points (≈0.42 inches)

// Set the text the user sees.
commandButton.Caption = "Click Me";

// Give the control a unique name for later reference.
commandButton.Name = "cmdButton1";
```

> **نصيحة احترافية:** يُقاس الحجم بالنقاط (نقطة واحدة = 1/72 بوصة). اضبط القيم لتناسب تخطيطك؛ لزر شريط أدوات نموذجي، 120 × 30 يعمل بشكل جيد.

---

## الخطوة 3: إدراج زر أمر – جوهر **Insert Command Button**

مع جاهزية عنصر التحكم، الآن نقوم **بإدراج زر أمر** في المستند عند الموقع الحالي للـ builder. يمكنك نقل الـ builder إلى أي مكان (مثلاً بعد فقرة) قبل استدعاء هذه الطريقة.

```csharp
// 3️⃣  Insert the prepared ActiveX control into the document.
builder.InsertForms2OleControl(commandButton);
```

إذا كنت بحاجة إلى **how to insert button** في إشارة مرجعية محددة، فقط حرك الـ builder أولاً:

```csharp
builder.MoveToBookmark("MyPlace"); // Ensure a bookmark named 'MyPlace' exists
builder.InsertForms2OleControl(commandButton);
```

> **ماذا يحدث خلف الكواليس؟** تقوم Aspose.Words بكتابة تدفقات كائنات OLE اللازمة داخل حزمة .docx، بحيث يمكن لـ Word عرض الزر دون أي ماكرو إضافي.

---

## الخطوة 4: حفظ المستند – إكمال دورة **Create Word Document**

الخطوة الأخيرة بسيطة: حفظ الملف على القرص. هذا يُكمل دورة **إنشاء مستند Word**، إدراج ActiveX، والحفظ.

```csharp
// 4️⃣  Save the document where you want it.
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
```

افتح الملف الناتج في Microsoft Word (لـ Windows فقط). يجب أن ترى زرًا قابلًا للنقر يحمل التسمية “Click Me”. النقر عليه سيُطلق الإجراء الافتراضي لزر CommandButton—لن يحدث شيء ما لم تقم بإرفاق كود VBA، لكن عنصر التحكم يعمل بالكامل.

> **الناتج المتوقع:** ملف .docx بصفحة واحدة، زر مركزي عند نقطة الإدراج، حجمه 120 × 30 pt، مع تسمية “Click Me”.  
> ![زر ActiveX تم إدراجه في مستند Word](placeholder-image.png)  
> *نص بديل للصورة:* **زر ActiveX تم إدراجه في مستند Word باستخدام C#** (يتطابق مع `og_image_alt`).

---

## الخطوة 5: الحالات الخاصة، الأمان، وأفضل الممارسات

### قيود المنصة
- عناصر تحكم ActiveX تعمل فقط على نسخة Word لنظام Windows. إذا كان جمهورك يشمل مستخدمي macOS أو Word Online، سيظهر الزر كصورة ثابتة.
- بعض بيئات الشركات تعطل ActiveX لأسباب أمنية؛ قد تحتاج إلى توقيع المستند أو إبلاغ المستخدمين بتمكين المحتوى.

### التفاعل مع VBA (اختياري)
إذا أردت أن ينفذ الزر ماكرو، سيتعين عليك إضافة مشروع VBA إلى المستند بعد الحفظ. لا تُنشئ Aspose.Words كود VBA تلقائيًا، لكن يمكنك استخدام API `Document.VbaProject` لإدخاله.

### تصادمات الأسماء
احرص دائمًا على إعطاء كل عنصر تحكم `Name` فريد. إعادة استخدام نفس الاسم قد يسبب أخطاءً وقت التشغيل عندما يحاول Word حل العنصر.

### نصيحة الأداء
عند إدراج العديد من العناصر، أعد استخدام نسخة واحدة من `DocumentBuilder` وتجنب استدعاء `doc.Save` داخل حلقة. اجمع الإدراجات واحفظ مرة واحدة في النهاية.

---

## مثال كامل يعمل

بجمع كل شيء معًا، إليك برنامج كامل جاهز للنسخ واللصق:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Create and configure the ActiveX command button.
        Forms2OleControl commandButton = new Forms2OleControl(
            doc, Forms2OleControlType.CommandButton);
        commandButton.Width = 120;          // Set button size – width
        commandButton.Height = 30;          // Set button size – height
        commandButton.Caption = "Click Me";
        commandButton.Name = "cmdButton1";

        // Insert the button at the current cursor position.
        builder.InsertForms2OleControl(commandButton);

        // Save the document.
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

شغّل البرنامج، افتح الملف المحفوظ، وسترى الزر بالضبط حيث كان الـ builder موضعه.

---

## الخلاصة

لقد قمنا للتو **بإنشاء مستند Word** من الصفر، وتعلمنا **how to add activex** عبر تكوين `Forms2OleControl`، وأتقنّا خصائص **ضبط حجم الزر**، وأظهرنا الطريقة الصحيحة لـ **إدراج زر أمر** و**how to insert button** في أي موقع داخل الملف.  

من خلال عينة كود واحدة الآن لديك أساس قوي لأتمتة Word أكثر غنىً—سواء كنت تبني قوالب بنماذج تفاعلية، أو تُنشئ عقودًا تتطلب إقرار المستخدم، أو ببساطة تضيف بعض عناصر التحكم المفيدة في تقرير.

### ما التالي؟

- **تنسيق الزر** – تغيير الخطوط، الألوان، أو إضافة خلفية صورة.  
- **إرفاق ماكرو VBA** – جعل الزر يقوم بالحسابات أو تشغيل برامج خارجية.  
- **دمج مع عناصر تحكم أخرى** – مربعات اختيار، قوائم منسدلة، أو حتى أوراق Excel مدمجة.  

لا تتردد في التجربة، وإذا واجهت مشكلة، اترك تعليقًا أدناه. برمجة سعيدة، واستمتع بأتمتة Word باستخدام Aspose.Words!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مستند Word باستخدام Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [إنشاء شكل مجموعة في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [إدراج صورة مدمجة في مستند Word باستخدام Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}