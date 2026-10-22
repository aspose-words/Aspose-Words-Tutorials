---
category: general
date: 2026-10-13
description: تعلم كيفية إضافة زر أمر برمجيًا باستخدام Aspose.Words. يوضح هذا الدليل
  أيضًا كيفية إنشاء زر في مستند Word مع كود C# كامل.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button programmatically
- create word document button
language: ar
lastmod: 2026-10-13
og_description: أضف زر أمر برمجيًا إلى مستند Word باستخدام Aspose.Words. اتبع هذا
  الدليل الكامل لإنشاء زر مستند Word باستخدام C#.
og_image_alt: Screenshot of a Word document with a command button inserted programmatically
og_title: إضافة زر أمر برمجيًا إلى مستند Word – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  headline: How to add a command button programmatically in a Word document
  type: TechArticle
- description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  name: How to add a command button programmatically in a Word document
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the Aspose.Words NuGet package:'
    text: 'Add the Aspose.Words NuGet package:'
  - name: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
    text: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: كيفية إضافة زر أمر برمجيًا في مستند Word
url: /ar/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إضافة زر أمر برمجيًا في مستند Word  

إذا كنت بحاجة إلى **إضافة زر أمر برمجيًا**، فإن Aspose.Words توفر واجهة برمجة تطبيقات نظيفة تتيح لك تضمين عناصر تحكم نموذج OLE مباشرةً في ملف .docx. يشرح هذا البرنامج التعليمي كل خطوة مطلوبة لإنشاء **زر مستند Word** يتصرف كزر نموذج عادي عند فتح المستند في Microsoft Word.  

ستتعلم كيفية إعداد بيئة التطوير، وإدراج الزر، وتكوين خصائصه، والتحقق من النتيجة. لا توجد أدوات خارجية مطلوبة—فقط مشروع .NET ومكتبة Aspose.Words for .NET.  

## المتطلبات المسبقة  

قبل أن تبدأ، تأكد من وجود ما يلي:  

* .NET 6.0 SDK أو أحدث مثبت.  
* نسخة حديثة من Aspose.Words for .NET (الأمثلة تستخدم 23.12، لكن أي إصدار 22.x+ يعمل).  
* بيئة تطوير متكاملة مثل Visual Studio 2022 أو Visual Studio Code.  

الكود يعمل على Windows و macOS و Linux لأن Aspose.Words مستقل عن المنصة.  

## الخطوة 1: إعداد المشروع وإضافة مرجع Aspose.Words  

1. أنشئ مشروع وحدة تحكم جديد:  

   ```bash
   dotnet new console -n WordButtonDemo
   cd WordButtonDemo
   ```  

2. أضف حزمة NuGet الخاصة بـ Aspose.Words:  

   ```bash
   dotnet add package Aspose.Words
   ```  

3. افتح **Program.cs** واستبدل محتواه بالهيكل الموضح في الخطوات التالية.  

إعداد المشروع بهذه الطريقة يضمن أن المترجم يستطيع العثور على مساحات الأسماء `Aspose.Words` و `Aspose.Words.Drawing.Forms` المطلوبة لعناصر التحكم في النماذج.  

## الخطوة 2: تهيئة مستند فارغ وDocumentBuilder  

فئة `Document` تمثل ملف Word بالكامل، بينما يوفر `DocumentBuilder` واجهة برمجة تطبيقات انسيابية لإضافة المحتوى.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;
using System.Drawing;   // required for RectangleF

// Create an empty document.
Document doc = new Document();

// Create a builder linked to the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```  

*لماذا هذه الخطوة مهمة* – بدون `DocumentBuilder` لا يمكنك تحديد موضع الزر بدقة على الصفحة. كما أن الـ builder يحترم موقع المؤشر الحالي، مما يجعل من السهل إدراج عدة عناصر تحكم لاحقًا.  

## الخطوة 3: إدراج عنصر تحكم OLE زر الأمر  

تتعامل Aspose.Words مع زر الأمر كعنصر تحكم OLE من النوع `ControlType.CommandButton`. تقوم بتحديد موقعه وحجمه باستخدام `RectangleF` مقاسًا بالنقاط (1 نقطة = 1/72 بوصة).  

```csharp
// Define the button rectangle: X=100, Y=150, Width=120, Height=30 (points)
RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

// Insert the command button at the current cursor position.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    buttonRect);
```  

**نقاط رئيسية**  

* أصل المستطيل (X, Y) يكون نسبةً إلى الزاوية العلوية اليسرى للصفحة.  
* تعديل `Width` أو `Height` يغيّر الحجم البصري للزر.  
* `InsertForms2OleControl` تُعيد كائن `Forms2OleControl` يمكنك تكوينه أكثر.  

## الخطوة 4: تكوين اسم الزر وعنوانه  

**الاسم** يُستخدم بواسطة محرك ماكرو Word لتحديد العنصر، بينما **العنوان** هو النص الذي يراه المستخدم.  

```csharp
// Set a unique identifier for the button.
commandButton.Name = "cmdSubmit";

// Set the text displayed on the button.
commandButton.Caption = "Submit";
```  

إذا كنت تخطط لإضافة ماكرو VBA لاحقًا، استخدم اسمًا وصفيًا لأن مسجل ماكرو Word يشير إلى هذه الخاصية.  

## الخطوة 5: (اختياري) حفظ المستند والتحقق من النتيجة  

حفظ الملف يتيح لك فتحه في Microsoft Word لتأكيد ظهور الزر وعمله.  

```csharp
// Save the document to the output folder.
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButtonDemo.docx");
doc.Save(outputPath);

Console.WriteLine($"Document saved to: {outputPath}");
```  

عند فتح *CommandButtonDemo.docx* في Word، يجب أن ترى زرًا بعنوان **Submit** موضعه تقريبًا 1.4 بوصة من الهامش الأيسر و2.1 بوصة من أعلى الصفحة. النقر على الزر لا يفعل شيئًا بشكل افتراضي لأن لا ماكرو مرتبط به، لكن عنصر التحكم البصري يعمل بالكامل.  

## الخطوة 6: الحالات الخاصة والمشكلات الشائعة  

| الحالة | ما يجب مراقبته | الإصلاح الموصى به |
|-----------|-------------------|-----------------|
| **تداخل الزر مع نص موجود** | قد يتقاطع المستطيل مع فقرة، مما يسبب مشاكل في التخطيط. | أدرج الزر بعد استدعاء `builder.Writeln()` لنقل المؤشر إلى سطر جديد، أو اضبط إحداثية `Y`. |
| **يفتح المستند مع تحذير** | بعض إصدارات Word تُظهر تحذيرًا لعناصر تحكم OLE التي لا تحتوي على برنامج مرتبط. | تأكد من أن نوع العنصر هو `CommandButton`؛ Word يتعامل معه كعنصر نموذج قياسي ولا يتطلب برنامجًا خارجيًا. |
| **التشغيل على Linux ببيئة بدون واجهة** | لا يمكن تشغيل Word لاختبار الواجهة، لكن الملف يظل صالحًا. | استخدم اختبار وحدة يقرأ خصائص العنصر (`commandButton.Name`, `commandButton.Caption`) للتحقق من ضبطها بشكل صحيح. |
| **الحاجة إلى عدة أزرار** | إعادة استخدام نفس `DocumentBuilder` دون نقل المؤشر يضيف الزر فوق السابق. | استدعِ `builder.MoveToDocumentEnd()` أو عدل قيمة `Y` في المستطيل قبل كل إدراج. |

معالجة هذه الحالات الخاصة مبكرًا توفر الوقت عند توسيع الحل إلى نماذج كاملة تحتوي على عشرات العناصر.  

## الخطوة 7: مثال كامل قابل للتنفيذ  

فيما يلي برنامج مستقل يمكنك نسخه ولصقه وتشغيله دون تعديل (باستثناء استعادة حزمة NuGet).  

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

namespace WordButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a new empty document.
            Document doc = new Document();

            // 2. Create a DocumentBuilder to work with the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Define the button rectangle (position + size).
            RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

            // 4. Insert the command button OLE control.
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                buttonRect);

            // 5. Set identifying properties.
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // 6. Save the document.
            string outputPath = Path.Combine(
                Environment.CurrentDirectory,
                "CommandButtonDemo.docx");
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

**الناتج المتوقع**  

تشغيل البرنامج يطبع مسارًا مشابهًا لـ:  

```
Document saved to: C:\Path\To\WordButtonDemo\CommandButtonDemo.docx
```  

فتح *CommandButtonDemo.docx* المُنشأ يُظهر زر **Submit** واحدًا موضعه عند الإحداثيات المحددة في الكود. لا تظهر عناصر واجهة إضافية، مما يؤكد نجاح سير عمل **إضافة زر أمر برمجيًا**.  

## الخلاصة  

أنت الآن تعرف كيفية **إضافة زر أمر برمجيًا** إلى مستند Word باستخدام Aspose.Words، وتفهم أيضًا كيفية **إنشاء زر مستند Word** يمكن ربطه لاحقًا بماكرو VBA أو أدوات أتمتة خارجية. تتكون العملية من تهيئة مستند، وإدراج عنصر تحكم OLE `CommandButton`، وتكوين خصائصه، وحفظ الملف.  

من هنا يمكنك:  

* إضافة المزيد من العناصر (مربعات اختيار، حقول نص) بتكرار الخطوة 3 مع قيم `ControlType` مختلفة.  
* ربط ماكرو VBA بالزر لتنفيذ إجراءات مثل حفظ نموذج أو إرسال بريد إلكتروني.  
* توليد نماذج كاملة ديناميكيًا عبر حلقة على مجموعة تعريفات الحقول المستندة إلى البيانات.  

جرّب تعديل إحداثيات المستطيل وعنوان الزر لتتناسب مع تصميم واجهة المستخدم الخاص بك. Happy coding!  


## ما الذي ينبغي أن تتعلمه بعد ذلك؟


الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إضافة حقل نموذج صندوق اختيار (Combo Box) إلى مستند Word باستخدام Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [إضافة حقل نموذج مربع تحقق (Check Box) إلى مستند Word باستخدام Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)
- [إنشاء مستند Word فارغ باستخدام Aspose.Words – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}