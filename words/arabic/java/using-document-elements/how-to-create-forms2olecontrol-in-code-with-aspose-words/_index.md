---
category: general
date: 2026-09-11
description: تعلم كيفية إنشاء forms2olecontrol في الكود باستخدام Aspose.Words DocumentBuilder.
  يغطي هذا الدليل خطوة بخطوة إدراج زر أمر ActiveX، واستخدام setOleClassName، وتحديد
  الحجم.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create forms2olecontrol in code
- ActiveX command button
- Aspose.Words DocumentBuilder
- setOleClassName method
- Forms2OleControl size
language: ar
lastmod: 2026-09-11
og_description: إنشاء forms2olecontrol في الكود باستخدام Aspose.Words. اتبع هذا الدليل
  لإدراج زر أمر ActiveX، وتعيين اسم الفئة الخاص به، وضبط حجمه.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX command
  button inserted via code
og_title: إنشاء forms2olecontrol في الكود – دليل Aspose.Words الكامل
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  headline: How to create forms2olecontrol in code with Aspose.Words
  type: TechArticle
- description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  name: How to create forms2olecontrol in code with Aspose.Words
  steps:
  - name: Initialise the DocumentBuilder
    text: The `DocumentBuilder` class is the entry point for most document‑generation
      tasks in Aspose.Words. It gives you methods to add text, images, tables, and,
      importantly for this tutorial, OLE controls.
  - name: Insert the Forms2OleControl
    text: The `insertForms2OleControl` method returns a `Forms2OleControl` object.
      This object represents the OLE control placeholder that Word will render as
      an ActiveX button.
  - name: Specify the ActiveX class with setOleClassName
    text: Word needs to know which type of ActiveX control to render. The class name
      for a standard command button is `"Forms.CommandButton.1"`.
  - name: Adjust the Forms2OleControl size
    text: A button that is too small or too large looks unprofessional. You can control
      its dimensions with `setWidth` and `setHeight`.
  - name: Save the document and test
    text: After configuring the control, save the document to a location of your choice.
  - name: When to use Forms2OleControl vs. Content Controls
    text: If you only need simple data entry (e.g., a plain text field), Word’s built‑in
      content controls are lighter weight. Use `Forms2OleControl` when you require
      full ActiveX functionality such as event handling or custom VBA interaction.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: كيفية إنشاء forms2olecontrol في الكود باستخدام Aspose.Words
url: /ar/java/using-document-elements/how-to-create-forms2olecontrol-in-code-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء forms2olecontrol برمجيًا باستخدام Aspose.Words

إذا كنت بحاجة إلى **إنشاء forms2olecontrol برمجيًا**، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك باستخدام Aspose.Words .NET API. سواءً كنت تقوم بأتمتة قالب يتطلب زر أمر ActiveX أو ترغب ببساطة في إثراء مستند Word برمجيًا، تغطي الخطوات أدناه كل شيء بدءًا من إدراج التحكم وحتى تكوين مظهره.

في هذا البرنامج التعليمي ستتعلم كيفية استخدام **Aspose.Words DocumentBuilder** لإدراج **زر أمر ActiveX**، وتعيين فئته باستخدام طريقة **setOleClassName**، وضبط **حجم Forms2OleControl**. لا تحتاج إلى أدوات خارجية—فقط بيئة تطوير .NET ومكتبة Aspose.Words.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من توفر ما يلي:

* .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.7+)
* نسخة حديثة من حزمة Aspose.Words for .NET عبر NuGet
* إلمام أساسي بـ C# ومفهوم عناصر التحكم ActiveX في مستندات Word

إذا كان أيٌ من هذه مفقودًا، قم بتثبيت حزمة NuGet باستخدام:

```bash
dotnet add package Aspose.Words
```

## ما يغطيه هذا البرنامج التعليمي

* إنشاء كائن `DocumentBuilder`
* إدراج `Forms2OleControl` (الكائن الأساسي لزر أمر ActiveX)
* تعيين اسم الفئة الصحيح باستخدام `setOleClassName`
* ضبط العرض والارتفاع البصري باستخدام خصائص **حجم Forms2OleControl**
* حفظ المستند والتحقق من النتيجة

بنهاية الدليل ستحصل على ملف Word يعمل بالكامل يحتوي على زر قابل للنقر يمكنك تخصيصه أكثر أو ربطه بماكرو VBA.

---

## كيفية إنشاء forms2olecontrol برمجيًا – خطوة بخطوة

### الخطوة 1: تهيئة DocumentBuilder

فئة `DocumentBuilder` هي نقطة الدخول لمعظم مهام إنشاء المستندات في Aspose.Words. توفر لك طرقًا لإضافة نصوص، صور، جداول، والأهم لهذا الدرس، عناصر تحكم OLE.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Initialise the builder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

**لماذا هذا مهم:**  
`DocumentBuilder` يحافظ على موضع المؤشر الحالي داخل المستند. بإنشائه مبكرًا، تضمن أن أي إدراج لاحق—مثل **زر أمر ActiveX**—سيظهر تمامًا في المكان الذي تريد.

### الخطوة 2: إدراج Forms2OleControl

طريقة `insertForms2OleControl` تُعيد كائنًا من نوع `Forms2OleControl`. يمثل هذا الكائن العنصر النائب للتحكم OLE الذي سيعرضه Word كزر ActiveX.

```csharp
// Insert the Forms2OleControl at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

**لماذا هذا مهم:**  
بدون هذا الاستدعاء لا يمكنك تعديل خصائص التحكم. الكائن `Forms2OleControl` المُرجع يمنحك وصولًا كاملًا إلى طريقة **setOleClassName**، وخصائص الحجم، وإعدادات OLE الأخرى.

### الخطوة 3: تحديد فئة ActiveX باستخدام setOleClassName

يحتاج Word إلى معرفة نوع عنصر التحكم ActiveX الذي يجب عرضه. اسم الفئة للزر القياسي هو `"Forms.CommandButton.1"`.

```csharp
// Tell Word that this OLE control is a CommandButton
commandButton.SetOleClassName("Forms.CommandButton.1");
```

**لماذا هذا مهم:**  
طريقة `setOleClassName` هي الجسر بين العنصر النائب OLE العام وزر **ActiveX command button** المحدد. استخدام اسم فئة غير صحيح يؤدي إلى ظهور كائن فارغ أو حدوث خطأ وقت التشغيل عند فتح المستند.

### الخطوة 4: ضبط حجم Forms2OleControl

زر صغير جدًا أو كبير جدًا يبدو غير احترافي. يمكنك التحكم بأبعاده باستخدام `setWidth` و `setHeight`.

```csharp
// Set the visual dimensions (points) of the button
commandButton.SetWidth(80);   // width in points
commandButton.SetHeight(30);  // height in points
```

**لماذا هذا مهم:**  
هذه الخصائص تشكل **حجم Forms2OleControl**. تؤثر على مظهر الزر في واجهة Word وتضمن أن أي ماكرو مرفق يمتلك مساحة نقر كافية.

### الخطوة 5: حفظ المستند واختباره

بعد تكوين التحكم، احفظ المستند في الموقع الذي تختاره.

```csharp
// Save the document as a .docx file
doc.Save("ActiveXButton.docx");
```

افتح `ActiveXButton.docx` في Microsoft Word. يجب أن ترى زرًا بعنوان “CommandButton1” (العنوان الافتراضي). النقر عليه لن يفعل شيئًا ما لم تُضف ماكرو VBA، لكن التحكم نفسه يعمل بالكامل.

**الناتج المتوقع:**  

![مستند Word مع زر أمر ActiveX مُدرج](/images/activeX-button.png "لقطة شاشة لمستند Word تُظهر زر ActiveX تم إنشاؤه حديثًا عبر الكود")

*نص alt للصورة يحتوي على الكلمة المفتاحية الأساسية من أجل الوصولية وتحسين محركات البحث.*

---

## فهم فئة ActiveX Forms2OleControl

فئة `Forms2OleControl` تغلف البنية التحتية منخفضة المستوى لـ OLE التي يستخدمها Word لعناصر ActiveX. هي ترث من `Shape`، مما يعني أنه يمكنك أيضًا تطبيق تنسيقات الشكل التقليدية (مثل الحدود، الدوران) إذا لزم الأمر.

* **زر أمر ActiveX** – الاستخدام الأكثر شيوعًا؛ يمكنك ربطه بماكرو عبر أدوات المطور في Word.
* **طريقة setOleClassName** – تحدد أي فئة COM يقوم Word بتحميلها؛ تشمل القيم الصالحة الأخرى `"Forms.TextBox.1"` و `"Forms.ComboBox.1"`.
* **حجم Forms2OleControl** – يُتحكم فيه عبر `SetWidth`/`SetHeight`. تقبل هذه الطرق نقاطًا (1 pt = 1/72 in).

### متى تستخدم Forms2OleControl مقابل عناصر التحكم المحتوى

إذا كنت تحتاج فقط إلى إدخال بيانات بسيط (مثل حقل نص عادي)، فإن عناصر التحكم المدمجة في Word أخف وزنًا. استخدم `Forms2OleControl` عندما تحتاج إلى وظائف ActiveX كاملة مثل معالجة الأحداث أو التفاعل مع VBA مخصص.

---

## ضبط خصائص إضافية (اختياري)

بينما الخطوات الأساسية كافية **لإنشاء forms2olecontrol برمجيًا**، غالبًا ما ترغب في تحسين مظهر الزر أو سلوكه.

```csharp
// Change the button caption (requires a VBA macro to read it)
commandButton.SetOleData("Caption", "Submit");

// Disable the button initially
commandButton.SetOleData("Enabled", false);

// Add a tooltip
commandButton.SetOleData("ToolTipText", "Click to submit the form");
```

**لماذا هذا مهم:**  
`SetOleData` يسمح لك بكتابة قيم خصائص عشوائية مباشرة إلى تدفق OLE. هذه هي الطريقة الأكثر مرونة لتخصيص **زر أمر ActiveX** دون اللجوء إلى VBA.

---

## المشكلات الشائعة واستكشاف الأخطاء

| العَرَض | السبب المحتمل | الحل |
|--------|--------------|-----|
| الزر يظهر كمربع رمادي | اسم فئة غير صحيح تم تمريره إلى `setOleClassName` | تأكد من أن السلسلة هي بالضبط `"Forms.CommandButton.1"` (حساسة لحالة الأحرف) |
| الحجم لا يتغير | تم ضبط العرض/الارتفاع قبل إدراج التحكم | استدعِ `SetWidth`/`SetHeight` **بعد** `InsertForms2OleControl` دائمًا |
| المستند يُظهر خطأ “OLE object not found” عند الفتح | نقص رخصة Aspose.Words (الإصدار التجريبي قد يحد من OLE) | طبّق رخصة صالحة أو استخدم النسخة التجريبية المجانية مع دعم OLE كامل |
| عنوان الزر يبقى “CommandButton1” | لم يتم استخدام `SetOleData` أو الماكرو لا يقرأ الخاصية | استخدم ماكرو VBA لقراءة خاصية `"Caption"` أو اضبط العنوان عبر واجهة Word |

---

## مثال كامل قابل للتنفيذ

فيما يلي تطبيق console كامل يمكنك نسخه، لصقه، وتشغيله. يوضح كل ما تم تغطيته في هذا الدرس.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace Forms2OleControlDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1. Create a new document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2. Insert the Forms2OleControl (ActiveX placeholder)
            Forms2OleControl commandButton = builder.InsertForms2OleControl();

            // 3. Set the ActiveX class to CommandButton
            commandButton.SetOleClassName("Forms.CommandButton.1");

            // 4. Define the visual size of the button
            commandButton.SetWidth(80);   // 80 points = ~1.11 inches
            commandButton.SetHeight(30);  // 30 points = ~0.42 inches

            // Optional: set a custom caption via OLE data (requires VBA to read)
            commandButton.SetOleData("Caption", "Submit");

            // 5. Save the document
            string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**شرح كل قسم**

* **توجيهات using** – تستدعي مساحة الأسماء Aspose.Words المطلوبة لـ `Document`، `DocumentBuilder`، و `Forms2OleControl`.
* **إنشاء المستند** – يخلق ملف Word فارغ.
* **InsertForms2OleControl** – يضع عنصر التحكم OLE عند موضع المؤشر الحالي للـ builder.
* **SetOleClassName** – يخبر Word أن التحكم هو **زر أمر ActiveX**.
* **SetWidth / SetHeight** – يضبط **حجم Forms2OleControl** لمظهر احترافي.
* **SetOleData (اختياري)** – يوضح كيفية كتابة خصائص إضافية مثل العنوان.
* **Save** – يكتب ملف `.docx` النهائي إلى القرص.

شغّل البرنامج (`dotnet run`) وافتح `ActiveXButton.docx`. يجب أن ترى زرًا يمكنك ربطه لاحقًا بماكرو.

---

## الخلاصة

أنت الآن تعرف كيف **تنشئ forms2olecontrol برمجيًا** باستخدام Aspose.Words، من تهيئة `DocumentBuilder` إلى تكوين **زر أمر ActiveX** عبر `setOleClassName` والتحكم في **حجم Forms2OleControl**. يتيح لك هذا النهج أتمتة مستندات Word معقدة، وإدراج عناصر واجهة تفاعلية، وإبقاء كل المنطق داخل التطبيق.

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}