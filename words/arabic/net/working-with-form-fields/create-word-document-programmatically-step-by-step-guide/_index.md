---
category: general
date: 2026-08-04
description: إنشاء مستند Word برمجيًا باستخدام C#. تعلم كيفية إضافة زر أمر برمجيًا
  باستخدام Aspose.Words في بضع خطوات فقط.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- programmatically add command button
- Aspose.Words InsertForms2OleControl
- C# Word automation
- OLE command button in Word
language: ar
lastmod: 2026-08-04
og_description: إنشاء مستند Word برمجيًا باستخدام Aspose.Words. يوضح هذا الدليل كيفية
  إضافة زر أمر برمجيًا، تكوينه، وحفظ الملف.
og_image_alt: Screenshot of a Word document that contains a Command Button added programmatically
og_title: إنشاء مستند Word برمجيًا – دليل كامل بلغة C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  headline: Create word document programmatically – step‑by‑step guide
  type: TechArticle
- description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  name: Create word document programmatically – step‑by‑step guide
  steps:
  - name: The `ControlType` enum value (here `CommandButton`).
    text: The `ControlType` enum value (here `CommandButton`).
  - name: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
    text: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
  - name: Optionally, additional OLE properties (not needed for the basic button).
    text: Optionally, additional OLE properties (not needed for the basic button).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: إنشاء مستند Word برمجيًا – دليل خطوة بخطوة
url: /ar/net/working-with-form-fields/create-word-document-programmatically-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word برمجيًا – دليل C# كامل

إذا كنت بحاجة إلى **إنشاء مستند Word برمجيًا**، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك باستخدام Aspose.Words for .NET. في بضع أسطر فقط من C# يمكنك إنشاء ملف `.docx` فارغ، **إضافة زر أمر برمجيًا**، ضبط خصائصه، وحفظ النتيجة.  

الخطوات أدناه تغطي كل شيء من إعداد المشروع إلى التعامل مع الحالات الخاصة، بحيث يمكنك نسخ الشيفرة إلى تطبيقك الخاص وتشغيلها دون تعديل.

## ما ستحققه

* تهيئة مستند Word جديد بالكامل في الذاكرة.  
* **إضافة زر أمر برمجيًا** كعناصر تحكم OLE في أي موقع وحجم.  
* تكوين تسمية الزر، الاسم الداخلي، وغيرها من خصائص OLE.  
* حفظ المستند المُنشأ إلى القرص أو إلى تدفق للمعالجة الإضافية.

### المتطلبات المسبقة

* .NET 6.0 أو أحدث (الشيفرة تعمل أيضًا مع .NET Framework 4.6+).  
* رخصة صالحة لـ Aspose.Words for .NET (أو نسخة تجريبية مجانية).  
* إلمام أساسي بـ C# و Visual Studio (أو أي بيئة تطوير تختارها).  

> **نصيحة احترافية:** إذا شغلت العينة بدون رخصة، سيضيف Aspose.Words علامة مائية تقييم صغيرة إلى الصفحة الأولى.

## الخطوة 1: إعداد المشروع واستيراد المساحات الاسمية المطلوبة

أنشئ تطبيق Console جديد (أو دمجه في خدمة موجودة) وأضف حزمة NuGet الخاصة بـ Aspose.Words:

```bash
dotnet add package Aspose.Words
```

ثم قم بتضمين المساحات الاسمية الأساسية في أعلى ملف `.cs` الخاص بك:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
```

هذه الاستيرادات تمنحك الوصول إلى `Document` و `DocumentBuilder` و `Forms2OleControl` و بنية `RectangleF` المستخدمة لتحديد المواقع.

## الخطوة 2: تهيئة مستند Word جديد

أول عملية في أي سير عمل **إنشاء مستند Word برمجيًا** هي إنشاء كائن `Document`. هذا الكائن يعيش فقط في الذاكرة حتى تقوم بحفظه صراحةً.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Attach a DocumentBuilder to simplify content insertion
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` يعمل كالمؤشر الذي يتتبع مكان وضع العنصر التالي. استخدامه يجعل الشيفرة مختصرة ويعكس الطريقة التي تكتب بها مباشرةً في Word.

## الخطوة 3: إدراج عنصر تحكم OLE زر أمر

توفر Aspose.Words طريقة `InsertForms2OleControl` لتضمين كائنات OLE مثل أزرار الأوامر، مربعات الاختيار، أو صناديق القوائم. الطريقة تتطلب ثلاثة معاملات:

1. قيمة تعداد `ControlType` (هنا `CommandButton`).  
2. كائن `RectangleF` يحدد موضع X‑Y وعرض‑ارتفاع العنصر (تقاس بالنقاط، حيث 72 pt = 1 inch).  
3. اختياريًا، خصائص OLE إضافية (غير مطلوبة للزر الأساسي).  

```csharp
// Step 3: Programmatically add command button at (100,100) with size 120×30 points
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **لماذا يعمل هذا:** `InsertForms2OleControl` ينشئ حاوية OLE في المستند ويعيد غلاف `Forms2OleControl`. يتيح لك الغلاف التلاعب بكائن OLE الأساسي (الزر الفعلي) دون الحاجة للتعامل مع التفاعل منخفض المستوى مع COM.

## الخطوة 4: تكوين تسمية الزر والاسم الداخلي

بعد الإدراج، عادةً ما تريد إعطاء الزر تسمية مرئية للمستخدم ومعرفًا داخليًا يمكن للماكرو أو الإضافة الرجوع إليه لاحقًا.

```csharp
// Step 4: Set caption and name of the button
commandButton.OleFormat.OleObject.Caption = "Click Me";
commandButton.OleFormat.OleObject.Name = "cmdClickMe";
```

* `Caption` هو النص المعروض على الزر في واجهة Word.  
* `Name` هو المعرف البرمجي المستخدم من قبل VBA أو سكريبتات الأتمتة الخارجية.  

### اختياري: إرفاق ماكرو بالزر

إذا كنت تخطط لتشغيل ماكرو VBA عند النقر على الزر، يمكنك إرفاق اسم الماكرو:

```csharp
commandButton.OleFormat.OleObject.MacroName = "MyMacro";
```

> **حالة خاصة:** عندما يُفتح المستند المستهدف على جهاز لا يحتوي على الماكرو، سيظهر Word تحذير أمان. احرص دائمًا على توقيع ماكروهاتك أو إبلاغ المستخدمين بالإعدادات المطلوبة.

## الخطوة 5: حفظ المستند

يمكنك كتابة الملف إلى القرص، أو `MemoryStream`، أو مباشرةً إلى كائن استجابة في واجهة ويب API. أبسط طريقة لعرض توضيحي في Console هي الحفظ إلى مجلد محلي:

```csharp
// Step 5: Persist the document containing the button
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

يفتح ملف `.docx` الناتج في Microsoft Word مع زر أمر فعال يظهر النص “Click Me”. النقر على الزر سيُشغل الماكرو المرفق (إن وجد) أو يعرض رسالة افتراضية.

## مثال كامل يعمل

انسخ البرنامج التالي إلى `Program.cs` وشغّله. يوضح كامل سير عمل **إنشاء مستند Word برمجيًا**، بما في ذلك معالجة الأخطاء.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        try
        {
            // 1️⃣ Initialise a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a CommandButton OLE control
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                new RectangleF(100, 100, 120, 30));

            // 3️⃣ Set button properties
            commandButton.OleFormat.OleObject.Caption = "Click Me";
            commandButton.OleFormat.OleObject.Name = "cmdClickMe";
            // Optional macro assignment (uncomment if needed)
            // commandButton.OleFormat.OleObject.MacroName = "MyMacro";

            // 4️⃣ Save the document
            string outputPath = @"C:\Temp\CommandButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document created successfully at {outputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ Error: {ex.Message}");
        }
    }
}
```

**النتيجة المتوقعة:** فتح `CommandButton.docx` في Word يظهر زرًا مسمى “Click Me”. تمرير المؤشر فوق الزر يكشف عن الاسم `cmdClickMe` في لوحة الخصائص.

## الأسئلة الشائعة واستكشاف الأخطاء

| السؤال | الجواب |
|----------|--------|
| *هل يمكنني إضافة الزر إلى مستند موجود؟* | نعم. حمّل الملف باستخدام `new Document("Existing.docx")`، ثم استخدم نفس استدعاء `InsertForms2OleControl`. |
| *ما الوحدات التي يستخدمها `RectangleF`؟* | نقاط (1 inch = 72 pt). عدّل القيم لتحديد موقع الزر بدقة. |
| *هل سيعمل الزر على Word لنظام Mac؟* | عناصر تحكم OLE مدعومة فقط في Word على Windows. على Mac يظهر الزر كصورة ثابتة. |
| *هل أحتاج إلى رخصة للاستخدام في الإنتاج؟* | الرخصة التجارية تزيل علامات مائية التقييم وتفتح جميع الوظائف. |
| *كيف أغيّر حجم الزر بعد الإدراج؟* | عدّل `commandButton.Width` و `commandButton.Height` أو أعد الإدراج باستخدام `RectangleF` جديد. |

## توسيع الحل

الآن بعد أن عرفت كيفية **إضافة زر أمر برمجيًا**، يمكنك استكشاف المواضيع ذات الصلة التالية:

* **إدراج عناصر تحكم نماذج أخرى** – استخدم `ControlType.CheckBox`، `ControlType.OptionButton`، إلخ. (يغطي الكلمة الثانوية *Aspose.Words InsertForms2OleControl*).  
* **ملء المستند ببيانات ديناميكية** – دمج البيانات من قاعدة بيانات إلى جداول أو حقول دمج البريد.  
* **التصدير إلى PDF** – بعد إضافة الزر، استدعِ `doc.Save("output.pdf", SaveFormat.Pdf)` لإنشاء نسخة PDF (متعلق بـ *C# Word automation*).  

## الخلاصة

أنت الآن تمتلك نمطًا كاملاً وجاهزًا للإنتاج لـ **إنشاء مستند Word برمجيًا** و **إضافة زر أمر برمجيًا** باستخدام Aspose.Words for .NET. غطى الدليل إعداد المشروع، تهيئة المستند، إدراج زر OLE، تكوين الخصائص، وحفظ الملف. لا تتردد في تعديل الشيفرة لإدراج عناصر تحكم نماذج أخرى، إرفاق ماكروهات، أو دمج المنطق في خدمات ويب أو وظائف خلفية.

برمجة سعيدة، واستمتع بأتمتة مستندات Word!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شيفرة كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مستند Word باستخدام Aspose.Words – دليل خطوة بخطوة](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)
- [إنشاء مستند Word مع جدول باستخدام Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [إنشاء شكل مجموعة في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}