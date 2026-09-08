---
category: general
date: 2026-09-08
description: كيفية حفظ ملف docx أثناء إدراج عنصر تحكم ActiveX في C#. اتبع هذا الدليل
  خطوة بخطوة لإضافة زر أمر برمجيًا.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save docx
- insert activex control
- add activex button
- create word document programmatically
- how to add command button
language: ar
lastmod: 2026-09-08
og_description: كيفية حفظ ملف docx أثناء إدراج عنصر تحكم ActiveX في C#. يشرح هذا الدرس
  خطوة بخطوة إنشاء مستند Word برمجيًا، إضافة زر أمر، وحفظ الملف.
og_image_alt: How to save docx with an ActiveX command button displayed in the document
og_title: كيفية حفظ ملف docx وإدراج زر ActiveX في C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: How to save docx while inserting an ActiveX control in C#. Follow this
    step‑by‑step guide to add a command button programmatically.
  headline: How to save docx and insert an ActiveX button with C#
  type: TechArticle
tags:
- C#
- Word automation
- ActiveX
- Docx
title: كيفية حفظ ملف docx وإدراج زر ActiveX باستخدام C#
url: /ar/net/working-with-oleobjects-and-activex/how-to-save-docx-and-insert-an-activex-button-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية حفظ ملف docx وإدراج زر ActiveX باستخدام C#

إذا كنت بحاجة إلى إنشاء مستند Word برمجيًا ثم حفظه بصيغة docx مع زر تفاعلي، يوضح لك هذا الدليل كيفية القيام بذلك. ستتعلم كيفية إدراج عنصر تحكم ActiveX، إضافة زر ActiveX، وحفظ ملف .docx الناتج باستخدام C# ومكتبة Aspose.Words.

يغطي الدرس كل خطوة مطلوبة **لإنشاء مستند Word برمجيًا**، تضمين **زر أمر**، وحفظ الملف على القرص. لا تحتاج إلى خبرة سابقة في كائنات COM، لكن يجب أن تكون لديك معرفة أساسية بـ C# وVisual Studio مثبتة.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* .NET 6.0 SDK أو أحدث  
* Visual Studio 2022 (أو أي بيئة تطوير C#)  
* حزمة NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
* فهم بنية مشروع C#  

هذه العناصر تضمن أن الكود يُترجم ويعمل دون إعدادات إضافية.

## الخطوة 1: إعداد مشروع C# console جديد

أنشئ تطبيقًا سطر أوامر يستضيف منطق أتمتة Word.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

الأمر أعلاه ينشئ مجلدًا باسم **WordActiveXDemo**، يضيف مرجع Aspose.Words، ويجهز المشروع للترجمة.

## الخطوة 2: إنشاء مستند Word برمجيًا

افتح ملف `Program.cs` الذي تم إنشاؤه وأضف توجيهات `using` المطلوبة.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;   // not used directly but required for some overloads
```

الآن أنشئ كائن `Document` فارغ. يمثل هذا الكائن ملف Word بالكامل في الذاكرة.

```csharp
// Step 2: Create a new blank document
Document document = new Document();
```

فئة `Document` هي نقطة الدخول لجميع عمليات معالجة Word. في هذه المرحلة لا يحتوي المستند على صفحات، لكن Aspose.Words سيُنشئ قسمًا افتراضيًا تلقائيًا عند إضافة محتوى.

## الخطوة 3: إدراج عنصر تحكم ActiveX – إضافة زر activex

كائن **Forms2OleControl** يتيح لك تضمين عنصر تحكم ActiveX داخل فقرة Word. يُدرج الكود التالي زر **CommandButton** بعرض 150 pt وارتفاع 30 pt.

```csharp
// Step 3: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX CommandButton control with the desired size
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

`InsertForms2OleControl` ينشئ العنصر ويعيد نسخة من نوع `Forms2OleControl` يمكن تكوينها لاحقًا. تُضيف الطريقة تلقائيًا فقرة جديدة لاستضافة العنصر، لذا لا تحتاج إلى إدارة كائنات الفقرات يدويًا.

## الخطوة 4: تكوين زر الأمر – كيفية إضافة خصائص زر الأمر

عيّن خصائص **Name** و**Caption** للزر لجعله قابلًا للتعريف أثناء التشغيل وسهل الاستخدام في الواجهة.

```csharp
// Step 4: Set the control's name and caption
commandButton.Name = "cmdSubmit";
commandButton.Caption = "Submit";
```

خاصية `Name` مفيدة عندما تتعامل لاحقًا مع حدث النقر للزر عبر VBA أو ماكرو Word. خاصية `Caption` هي النص الذي يراه المستخدم على سطح الزر.

### نصيحة احترافية
إذا كنت تخطط لأتمتة معالجة النقر من C#، أدرج ماكرو VBA يشير إلى `cmdSubmit`. سيطلب Word من المستخدم تمكين الماكرو عند فتح المستند، وهذا سلوك أمان قياسي لعناصر ActiveX.

## الخطوة 5: كيفية حفظ docx

بعد وضع العنصر، احفظ المستند كملف .docx. تختار طريقة `Save` الصيغة المناسبة تلقائيًا بناءً على امتداد الملف.

```csharp
// Step 5: Save the document containing the CommandButton
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

حفظ الملف يُكمل سير عمل **كيفية حفظ docx**. يمكن فتح الملف الناتج في Microsoft Word، حيث سيظهر زر ActiveX في الصفحة الأولى. عند النقر على الزر، سيعرض Word رسالة placeholder ما لم يُرفق ماكرو.

## الخطوة 6: تشغيل البرنامج والتحقق من النتيجة

قم بترجمة وتشغيل تطبيق سطر الأوامر:

```bash
dotnet run
```

بعد انتهاء البرنامج، افتح `C:\Temp\CommandButton.docx` في Microsoft Word:

* يحتوي المستند على صفحة واحدة بها زر **Submit** بالقرب من الأعلى.  
* عند تمرير المؤشر فوق الزر يظهر تلميح بالأسم `cmdSubmit`.  
* لا يُفقد أي محتوى، وحجم الملف مشابه لحجم ملف .docx فارغ قياسي.

إذا لم يظهر الزر، تأكد من التالي:

1. إعدادات **Trust Center** في Word تسمح بعناصر ActiveX.  
2. تم حفظ الملف بامتداد `.docx` (ليس `.doc`).  

## الحالات الخاصة والاختلافات الشائعة

| الحالة | التعديل الموصى به |
|-----------|------------------------|
| تحتاج إلى حجم زر مختلف | غيّر قيم العرض والارتفاع في `InsertForms2OleControl`. |
| تريد الزر في صفحة محددة | استخدم `builder.MoveToDocumentEnd();` بعد إضافة الصفحات، أو أدخل فاصل صفحة قبل العنصر. |
| يجب دعم بيئات بدون Aspose.Words | استخدم Open XML SDK لإدراج عنصر `w:object`، لكن يصبح الكود أكثر تعقيدًا. |
| مطلوب مستند يدعم الماكرو | احفظ بامتداد `.docm` (`document.Save("MyDoc.docm");`) وأدرج وحدة VBA تتعامل مع `cmdSubmit_Click`. |

## الكود المصدر الكامل

فيما يلي البرنامج الكامل المستقل الذي يمكنك نسخه إلى `Program.cs` وتشغيله دون تعديل (باستثناء مسار الإخراج).

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
            // Create a new blank document
            Document document = new Document();

            // Initialize a DocumentBuilder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control with the desired size
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Set the control's name and caption
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // Save the document containing the CommandButton
            string outputPath = @"C:\Temp\CommandButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### النتيجة المتوقعة في سطر الأوامر

```
Document saved to C:\Temp\CommandButton.docx
```

فتح الملف في Word يعرض زرًا بعنوان **Submit**. النقر على الزر يُفعّل سلوك ActiveX الافتراضي (مربع رسالة يُظهر أنه لا يوجد ماكرو مرفق).

## الخلاصة

يوضح هذا الدرس **كيفية حفظ docx** مع تضمين **عنصر تحكم ActiveX**، وبشكل خاص **إضافة زر activex** يعمل كزر أمر. الآن تعرف كيف **تنشئ مستند Word برمجيًا**، تُكوّن خصائص الزر، وتُحفظ الملف لتفاعل المستخدم النهائي.

من هنا يمكنك استكشاف:

* إضافة ماكرو VBA للتعامل مع `cmdSubmit_Click`.  
* إدراج عناصر تحكم ActiveX أخرى مثل مربعات الاختيار أو القوائم المنسدلة.  
* توليد مستندات متعددة الصفحات مع عناصر تفاعلية متعددة.  

جرّب أنواعًا مختلفة من العناصر وخيارات التخطيط لبناء قوالب Word غنية وتفاعلية تُسهّل عمليات عملك.

## ماذا يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تُكمل التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Aspose.Words – حفظ docx كملف txt وتصدير معادلات Word كـ LaTeX – دليل شامل](/words/english/net/basic-conversions/save-docx-as-txt-complete-guide-to-export-word-equations-as/)
- [كيفية استعادة docx – دليل C# للملفات Word التالفة](/words/english/net/programming-with-loadoptions/how-to-recover-docx-c-guide-for-corrupted-word-files/)
- [كيفية حفظ Word كملف Markdown – دليل C# كامل](/words/english/net/programming-with-markdownsaveoptions/how-to-save-word-as-markdown-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}