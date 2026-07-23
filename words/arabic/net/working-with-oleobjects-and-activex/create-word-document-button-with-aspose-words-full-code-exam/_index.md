---
category: general
date: 2026-07-23
description: إنشاء زر مستند Word باستخدام Aspose.Words – دليل خطوة بخطوة لإدراج زر
  CommandButton من نوع ActiveX في ملف .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document button
- ActiveX CommandButton
- DocumentBuilder
- InsertForms2OleControl
- Aspose.Words
language: ar
lastmod: 2026-07-23
og_description: 'إنشاء زر مستند Word باستخدام Aspose.Words: تعلم كيفية تضمين زر CommandButton
  من نوع ActiveX في ملف Word خلال دقائق.'
og_image_alt: Screenshot of a Word document showing an inserted CommandButton control
og_title: زر إنشاء مستند Word – دليل Aspose.Words الكامل
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  headline: create word document button with Aspose.Words – Full Code Example
  type: TechArticle
- description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  name: create word document button with Aspose.Words – Full Code Example
  steps:
  - name: '**Creates** an OLE object inside the Word file.'
    text: '**Creates** an OLE object inside the Word file.'
  - name: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
    text: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
  - name: '**Positions** it according to the rectangle we supplied.'
    text: '**Positions** it according to the rectangle we supplied.'
  - name: Launch Microsoft Word.
    text: Launch Microsoft Word.
  - name: Navigate to **File → Open** and select `CommandButton.docx`.
    text: Navigate to **File → Open** and select `CommandButton.docx`.
  - name: You should see a rectangular button labeled “CommandButton1”.
    text: You should see a rectangular button labeled “CommandButton1”.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
- CommandButton
title: زر إنشاء مستند Word باستخدام Aspose.Words – مثال كامل للكود
url: /ar/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء زر مستند Word باستخدام Aspose.Words – دليل البرمجة الكامل

هل احتجت يوماً إلى **create word document button** لكن لم تكن متأكدًا من أي API تستخدم؟ لست وحدك—معظم المطورين يواجهون صعوبة عندما يحاولون دمج عناصر تحكم تفاعلية داخل ملف .docx. الخبر السار؟ مع Aspose.Words for .NET يمكنك إضافة زر ActiveX CommandButton كامل الوظيفة إلى مستند Word ببضع أسطر من الشيفرة فقط.

في هذا الدرس سنستعرض العملية بالكامل: من إعداد المشروع، تهيئة `DocumentBuilder`، إدراج الزر باستخدام `InsertForms2OleControl`، وأخيرًا حفظ الملف بحيث يتعرف Word على التحكم. في النهاية ستحصل على ملف Word جاهز يحتوي على زر قابل للنقر—بدون الحاجة إلى تعقيدات COM interop.

## ما ستحتاجه

قبل أن نبدأ، تأكد من توفر المتطلبات التالية:

- **.NET 6.0** أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.6+).  
- حزمة **Aspose.Words for .NET** من NuGet (الإصدار 23.9 أو أحدث).  
- فهم أساسي للغة C# (سنحافظ على البنية مناسبة للمبتدئين).  
- Visual Studio 2022 أو أي بيئة تطوير تفضلها.

هذا كل ما تحتاجه—بدون مراجع COM إضافية، بدون Office interop، مجرد كود مُدار بالكامل.

---

## الخطوة 1: إعداد Aspose.Words لإنشاء **create word document button**

أولاً، أضف حزمة Aspose.Words إلى مشروعك:

```bash
dotnet add package Aspose.Words
```

أو، إذا كنت تستخدم واجهة NuGet في Visual Studio، ابحث عن “Aspose.Words” واضغط **Install**. هذه السطر الواحد يمنحك الوصول إلى `Document`، `DocumentBuilder`، وطريقة `InsertForms2OleControl` التي سنحتاجها لاحقًا.

> **نصيحة احترافية:** حافظ على تحديث حزم NuGet الخاصة بك؛ الإصدارات الأحدث غالبًا ما تتضمن إصلاحات للأخطاء المتعلقة بمعالجة ActiveX.

---

## الخطوة 2: تهيئة **DocumentBuilder** لـ **ActiveX CommandButton**

الآن ننشئ مستند Word جديد ونُنشئ كائن `DocumentBuilder`. فكر في `DocumentBuilder` كفرشاة الرسم التي تسمح لك برسم المحتوى على القماش.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 2.1: Create a new empty document
        Document document = new Document();

        // Step 2.2: Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

لاحظ أننا نستورد `System.Drawing`—هيكل `Rectangle` يحدد موقع الزر وحجمه. هنا سيعيش **ActiveX CommandButton**.

---

## الخطوة 3: استخدام **InsertForms2OleControl** لإضافة **CommandButton**

هذا هو جوهر الدرس: إدراج الزر نفسه. طريقة `InsertForms2OleControl` تستقبل ثلاث معطيات—نوع التحكم، `Rectangle`، واختياريًا اسمًا. سنستخدم `OleControlType.CommandButton` لتحديد التحكم المطلوب.

```csharp
        // Step 3: Insert an ActiveX CommandButton at (0,0) with width=100, height=30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));
```

هذا الاستدعاء الواحد يقوم بالكثير:

1. **ينشئ** كائن OLE داخل ملف Word.  
2. **يسجله** كـ ActiveX CommandButton، والذي سيعرضه Word كعنصر UI قابل للنقر.  
3. **يضعه** وفقًا للمستطيل الذي قدمناه.

إذا رغبت في تغيير تسمية الزر أو خصائص أخرى، يمكنك فعل ذلك بعد الإدراج عبر الوصول إلى `OleFormat` الأساسي. في معظم الحالات، التسمية الافتراضية (“CommandButton1”) كافية.

---

## الخطوة 4: حفظ مستند Word الذي يحتوي على **CommandButton**

الحفظ بسيط—فقط حدد مجلدًا لديك صلاحية كتابة فيه. يجب أن يكون امتداد الملف `.docx` لكي يبقى الزر موجودًا بعد الحفظ.

```csharp
        // Step 4: Save the document with the embedded button
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

عند فتح `CommandButton.docx` في Microsoft Word، ستظهر زرًا صغيرًا في الزاوية العليا اليسرى من الصفحة الأولى. النقر عليه لا يفعل شيئًا مباشرة (ذلك يتطلب VBA)، لكن التحكم يعمل بالكامل ويمكن ربطه لاحقًا.

> **لماذا يعمل هذا:** تقوم Aspose.Words بكتابة تدفق OLE مباشرة داخل حزمة DOCX، متجاوزة الحاجة إلى أن يولد Word التحكم أثناء التشغيل. هذا يضمن ظهور الزر تمامًا حيث وضعتَه.

---

## الخطوة 5: التحقق من الزر في Word

افتح الملف المُولد:

1. شغّل Microsoft Word.  
2. انتقل إلى **File → Open** واختر `CommandButton.docx`.  
3. يجب أن ترى زرًا مستطيلاً يحمل التسمية “CommandButton1”.  

إذا لم يظهر الزر، تأكد من تفعيل **Design Mode** (Developer → Design Mode). هذا يُظهر التمثيل البصري للتحكمات ActiveX.

---

## الخطوة 6: خيارات متقدمة – تخصيص **ActiveX CommandButton**

فيما يلي بعض التعديلات السريعة التي قد تجدها مفيدة:

| الهدف | مقتطف الشيفرة |
|------|--------------|
| تغيير التسمية | ```csharp<br/>OleFormat ole = builder.CurrentParagraph.Runs[0].OleFormat;<br/>ole.OleControlCaption = "Submit";``` |
| تعيين اسم ماكرو (يتطلب دعم ماكرو في Word) | ```csharp<br/>ole.OleControlMacroName = "MyMacro";``` |
| تغيير الحجم بعد الإدراج | ```csharp<br/>builder.MoveToDocumentEnd();<br/>builder.InsertForms2OleControl(OleControlType.CommandButton, new Rectangle(0,0,150,40));``` |

تُظهر هذه المقتطفات مرونة `InsertForms2OleControl`. يمكنك حتى دمج تحكمات ActiveX أخرى مثل `CheckBox` أو `ListBox` بتغيير قيمة تعداد `OleControlType`.

---

## مثال كامل يعمل

فيما يلي البرنامج الكامل جاهز للنسخ واللصق الذي **creates a word document button** من الصفر:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class CreateWordDocumentButton
{
    static void Main()
    {
        // 1️⃣ Create a new empty document
        Document document = new Document();

        // 2️⃣ Initialize DocumentBuilder – the tool that lets us edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert an ActiveX CommandButton at position (0,0) with size 100x30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));

        // 4️⃣ Save the .docx file – this is where the button lives
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);

        Console.WriteLine($"✅ Document with button saved to: {outputPath}");
    }
}
```

**الناتج المتوقع عند تشغيل البرنامج:**

```
✅ Document with button saved to: C:\Temp\CommandButton.docx
```

افتح الملف الناتج وسترى الزر في الموضع الذي حدده الكود.

---

## الأخطاء الشائعة وكيفية تجنّبها

- **غياب مرجع `System.Drawing`** – هيكل `Rectangle` موجود هناك؛ بدونها سيشتكي المترجم.  
- **استخدام نسخة قديمة من Aspose.Words** – الإصدارات الأولية لم تدعم `InsertForms2OleControl` بالكامل. قم بالترقية إلى أحدث حزمة مستقرة.  
- **الحفظ كـ `.doc` بدلاً من `.docx`** – يتم حذف تدفق OLE في الصيغة الثنائية القديمة، مما يؤدي إلى اختفاء الزر.  
- **التنفيذ على خادم بدون Word مثبت** – سيظل الزر موجودًا في الملف، لكن لا يمكنك معاينته بدون Word. هذا لا يعيق خطوط الأنابيب الآلية للتوليد.

---

## الخطوات التالية – توسيع سير عمل **create word document button**

الآن بعد أن أتقنت الأساسيات، فكر في الأفكار المتقدمة التالية:

- **إرفاق ماكرو VBA** بالزر لتنفيذ منطق أعمال مخصص.  
- **إنشاء أزرار متعددة** داخل حلقة لتصميم نماذج ديناميكية.  
- **دمج مع Aspose.PDF** لتصدير نفس المستند إلى PDF مع الحفاظ على التخطيط البصري (يصبح الزر صورة ثابتة في PDF).  
- **


## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مستند Word باستخدام Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [إنشاء شكل مستطيل في Word باستخدام Aspose.Words – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [إدراج صورة مدمجة في مستند Word باستخدام Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}