---
category: general
date: 2026-10-23
description: إنشاء مستند Word فارغ باستخدام C# وتعلم كيفية إدراج عناصر تحكم ActiveX،
  بما في ذلك زر، باستخدام Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- create activex control
- word document activex button
language: ar
lastmod: 2026-10-23
og_description: إنشاء مستند Word فارغ باستخدام C# وتعلم كيفية إدراج عناصر تحكم ActiveX،
  بما في ذلك زر، باستخدام Aspose.Words.
og_image_alt: Result of creating a blank Word document with an ActiveX Submit button
og_title: إنشاء مستند Word فارغ وإضافة زر ActiveX باستخدام C#
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button in C#
  type: TechArticle
- description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  name: Create a blank Word document and add an ActiveX button in C#
  steps:
  - name: Instantiate a `Document`.
    text: Instantiate a `Document`.
  - name: Use `DocumentBuilder` to work with the file.
    text: Use `DocumentBuilder` to work with the file.
  - name: Call `InsertForms2OleControl` to **how to insert activex** controls.
    text: Call `InsertForms2OleControl` to **how to insert activex** controls.
  - name: Configure the control’s properties (**create activex control**).
    text: Configure the control’s properties (**create activex control**).
  - name: Save the file, yielding a **word document activex button** ready for VBA
      integration.
    text: Save the file, yielding a **word document activex button** ready for VBA
      integration.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: إنشاء مستند Word فارغ وإضافة زر ActiveX باستخدام C#
url: /ar/java/document-manipulation/create-a-blank-word-document-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word فارغ وإضافة زر ActiveX في C#

إذا كنت بحاجة إلى **إنشاء مستند Word فارغ** برمجياً، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك. سترى مثالًا كاملاً قابلاً للتنفيذ ينشئ مستندًا جديدًا، يدرج زر ActiveX من نوع CommandButton، ويحفظ الملف—كل ذلك باستخدام Aspose.Words for .NET.

العمل مع ملفات Word غالبًا ما يتطلب أكثر من النص العادي. إضافة **زر ActiveX** تتيح لك تضمين وظائف تفاعلية يمكن استخدامها في القوالب المدعومة بالماكرو أو الحلول الخاصة بنظام Windows فقط. بنهاية هذا الدرس ستتمكن من إدراج أي عنصر تحكم ActiveX، لكننا سنركز على السيناريو الأكثر شيوعًا: **زر ActiveX في مستند Word** يرسل نموذجًا.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.7+)
* Visual Studio 2022 (أو أي بيئة تطوير C#)
* حزمة **Aspose.Words for .NET** عبر NuGet  
  ```bash
  dotnet add package Aspose.Words
  ```
* إلمام أساسي بصياغة C#

> **نصيحة احترافية:** Aspose.Words مكتبة تجارية، لكنها توفر ترخيصًا مؤقتًا مجانيًا للاختبار. قم بتثبيت الترخيص مبكرًا لتجنب علامة التقييم المائية.

## الخطوة 1: إنشاء مستند Word فارغ باستخدام Aspose.Words

الخطوة الأولى هي إنشاء كائن `Document`. هذا يمثل ملف `.docx` فارغ في الذاكرة.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
```

`Document` يبدأ بدون أقسام أو صفحات أو محتوى. إنه القالب النظيف الذي تحتاجه لسيناريوهات **إنشاء مستند Word فارغ** مثل توليد تقارير من الصفر.

## الخطوة 2: الحصول على DocumentBuilder لتعديل المستند

`DocumentBuilder` يوفر واجهة برمجة تطبيقات مريحة لإضافة النصوص، الصور، والعناصر التحكمية. سنستخدمه لتحديد موضع عنصر التحكم ActiveX.

```csharp
// Obtain a DocumentBuilder tied to the blank document
DocumentBuilder builder = new DocumentBuilder(document);
```

يقوم الـ builder تلقائيًا بإضافة قسم افتراضي وصفحة أولى، بحيث يمكنك البدء في إدراج الكائنات فورًا.

## الخطوة 3: كيفية إدراج عناصر تحكم ActiveX في المستند

Aspose.Words يوفّر الدالة `InsertForms2OleControl` لتضمين كائنات OLE/ActiveX. تتطلب الدالة نوع العنصر، العرض، والارتفاع (بـ points). أدناه ندرج **CommandButton**—زر النموذج الكلاسيكي الذي تراه في قوالب Word القديمة.

```csharp
// Insert an ActiveX CommandButton control (100 × 30 points)
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

> **لماذا يعمل هذا:** `Forms2OleControlType.COMMANDBUTTON` يخبر Word بإنشاء زر يمكنه الاستجابة لأحداث النقر عندما يُفتح المستند في بيئة Windows تدعم ActiveX.

## الخطوة 4: إنشاء عنصر تحكم ActiveX – ضبط خصائصه

الآن نعطي الزر اسمًا برمجيًا وعنوانًا مرئيًا. هذا هو الجزء من **إنشاء عنصر تحكم ActiveX** الذي غالبًا ما يغفل عنه المطورون.

```csharp
// Set the button's name (used in VBA) and the text shown to users
commandButton.Name = "btnSubmit";
commandButton.Caption = "Submit";
```

* `Name` هو المعرف الذي ستشير إليه من ماكرو VBA (`ActiveDocument.InlineShapes("btnSubmit")`).
* `Caption` هو النص الظاهر على الزر نفسه.

## الخطوة 5: حفظ مستند Word مع زر ActiveX

أخيرًا، نكتب المستند إلى القرص. يجب أن يكون امتداد الملف `.docx` (أو `.docm` إذا كنت تخطط لإضافة ماكرو لاحقًا). المثال يحفظ في مجلد مؤقت—استبدله بالمسار الخاص بك.

```csharp
// Save the document containing the ActiveX button
string outputPath = @"C:\Temp\ActiveXButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

عند فتح الملف الناتج في Microsoft Word (Windows فقط)، سترى **زر ActiveX في مستند Word** يعمل ويمكن ربطه بكود VBA.

## مثال كامل يعمل

فيما يلي البرنامج الكامل الذي يمكنك نسخه ولصقه في مشروع Console جديد.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a blank Word document
            Document document = new Document();

            // 2. Get a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3. Insert an ActiveX CommandButton (100 × 30 points)
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

            // 4. Configure the button
            commandButton.Name = "btnSubmit";
            commandButton.Caption = "Submit";

            // 5. Save the file
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**الناتج المتوقع عند تشغيل البرنامج**

```
Document saved to C:\Temp\ActiveXButton.docx
```

افتح الملف `ActiveXButton.docx` المُولد في Word، وسترى زرًا بعنوان **Submit** موضعًا في أعلى الصفحة الأولى.

## الحالات الخاصة والمشكلات الشائعة

| الحالة | ما يجب مراقبته | التوصية |
|-----------|-------------------|----------------|
| التشغيل على macOS أو Linux | ActiveX تقنية خاصة بـ Windows، لذا سيظهر الزر كعنصر نائب. | استخدم الدرس فقط للقوالب المستهدفة لنظام Windows. |
| فتح المستند في Word Online | لا تدعم Word Online عناصر تحكم ActiveX. | قدّم واجهة بديلة أو ارشد المستخدمين لفتح الملف في تطبيق سطح المكتب. |
| الحاجة إلى ملف يدعم الماكرو | ملفات `.docx` لا يمكنها تخزين كود VBA. | احفظ كـ `.docm` (`document.Save("MyFile.docm", SaveFormat.Docm)`) وأضف الماكرو بشكل منفصل. |
| عدم تطابق حجم العنصر | قيم العرض/الارتفاع بوحدات points (1 pt ≈ 1/72 in). | عدّل القيم الرقمية للحصول على الحجم البصري المطلوب. |

## الأسئلة المتكررة

**كيف يمكن إدراج عناصر تحكم ActiveX غير الزر؟**  
استخدم نفس الدالة `InsertForms2OleControl` لكن مرّر قيمة مختلفة من تعداد `Forms2OleControlType`، مثل `COMBOBOX` أو `LISTBOX`.

**هل يمكن تغيير خط الزر أو لونه؟**  
مظهر زر ActiveX يتحكم فيه التطبيق المستضيف (Word) وثيم Windows الأساسي. يمكنك تعديل خصائص مثل `ForeColor` و `BackColor` عبر VBA بعد فتح المستند.

**هل هناك طريقة لإضافة معالج نقر مباشرة من C#؟**  
لا. يجب أن يتم التعامل مع حدث النقر عبر VBA أو إضافة Word لأن الزر يعمل داخل عملية Word، وليس داخل تطبيق .NET الخاص بك.

## الخلاصة

أنت الآن تعرف كيف **تنشئ مستند Word فارغ** برمجياً وتدمج **زر ActiveX** باستخدام Aspose.Words for .NET. الخطوات التي تم تغطيتها:

1. إنشاء كائن `Document`.
2. استخدام `DocumentBuilder` للعمل مع الملف.
3. استدعاء `InsertForms2OleControl` لـ **كيفية إدراج عناصر تحكم ActiveX**.
4. ضبط خصائص العنصر (**إنشاء عنصر تحكم ActiveX**).
5. حفظ الملف، مما ينتج **زر ActiveX في مستند Word** جاهز للتكامل مع VBA.

من هنا يمكنك استكشاف إضافة أنواع تحكم أخرى، ربط ماكرو VBA، أو تحويل المستند إلى PDF مع الحفاظ على الزر (كصورة ثابتة). جرّب أحجامًا وعناوين وأسماء مختلفة.

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [كيفية إضافة زر ActiveX في مستند Word باستخدام Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [إنشاء مستند Word مع زر ActiveX – دليل C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}