---
category: general
date: 2026-09-30
description: أضف عنصر تحكم ActiveX إلى مستند Word باستخدام C#. تعلّم كيفية إدراج زر
  ActiveX، إضافة زر أمر، وجعله قابلًا للنقر.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- activex control word
- how to insert activex
- how to add command button
- insert activex button
- add clickable button word
language: ar
lastmod: 2026-09-30
og_description: أضف عنصر تحكم ActiveX إلى مستند Word باستخدام C#. اتبع هذا الدليل
  الكامل لإدراج زر ActiveX، وإضافة زر أمر، وجعله قابلًا للنقر.
og_image_alt: Word document displaying an inserted ActiveX command button
og_title: إضافة عنصر تحكم ActiveX إلى مستندات Word – دليل خطوة بخطوة بلغة C#
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Add an ActiveX control word to a Word document using C#. Learn how
    to insert an ActiveX button, add a command button, and make it clickable.
  headline: How to add an ActiveX control word in Word with C#
  type: TechArticle
tags:
- ActiveX
- Aspose.Words
- C#
- Word automation
title: كيفية إضافة عنصر تحكم ActiveX في Word باستخدام C#
url: /ar/net/working-with-oleobjects-and-activex/how-to-add-an-activex-control-word-in-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إضافة كلمة تحكم ActiveX في Word باستخدام C#

إذا كنت بحاجة إلى تضمين **ActiveX control word** داخل ملف Microsoft Word، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك. سترى مثالًا كاملاً قابلًا للتنفيذ يدرج زرًا قابلًا للنقر، يحفظ المستند، ويعمل مع أحدث Aspose.Words for .NET.

إضافة كلمة تحكم ActiveX تتيح لك إنشاء نماذج تفاعلية، حوارات مخصصة، أو عناصر واجهة مستخدم بسيطة تتصرف كعناصر تحكم Word الأصلية. سواء كنت تبني قالب عقد يتطلب تفاعل المستخدم أو تقريرًا يحتاج إلى زر “Run”، فإن الخطوات أدناه تغطي كل ما تحتاجه.

## المتطلبات المسبقة

* .NET 6.0 SDK أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.8)
* Visual Studio 2022 (أو أي بيئة تطوير تدعم C#)
* Aspose.Words for .NET مثبت (`dotnet add package Aspose.Words`)
* فهم أساسي لـ C# وبنية مستند Word

> **نصيحة احترافية:** طريقة `InsertForms2OleControl` تعمل فقط مع عناصر تحكم “Forms 2.0” القديمة، وهي عناصر التحكم ActiveX التي يستخدمها Word لحقول النماذج. إذا استهدفت إصدارات Office أحدث، فإن العنصر لا يزال يُعرض بشكل صحيح في عميل سطح المكتب.

## الخطوة 1: إعداد المشروع واستيراد المساحات الاسمية

أنشئ مشروع console جديد وأضف عبارات `using` المطلوبة. يضمن ذلك أن المترجم يستطيع العثور على الفئات `Document` و `DocumentBuilder` و `OleControlType`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

مساحة الاسم `Aspose.Words` توفر واجهات برمجة تطبيقات عالية المستوى لمعالجة Word، بينما تحتوي `Aspose.Words.Drawing` على تعداد `OleControlType` اللازم لتحديد نوع عنصر تحكم ActiveX.

## الخطوة 2: تحميل مستند Word المصدر

يجب أن تبدأ بملف Word تريد تعديلّه. الكود التالي يحمل `input.docx` من المجلد الذي تحدده.

```csharp
// Step 2: Load the Word document you want to modify
string inputPath = @"C:\Docs\input.docx";
Document doc = new Document(inputPath);
```

إذا لم يكن الملف موجودًا، فإن Aspose.Words يرمي استثناء `FileNotFoundException`. غلف الاستدعاء داخل كتلة `try/catch` إذا كنت تحتاج إلى معالجة الأخطاء بلطف.

## الخطوة 3: إنشاء DocumentBuilder لتحرير المستند

`DocumentBuilder` هو الأداة الأساسية لإدراج النصوص، الصور، والعناصر التحكم. يحافظ على مؤشر يشير إلى الموقع الذي سيُوضع فيه العنصر التالي.

```csharp
// Step 3: Create a DocumentBuilder to work with the document's content
DocumentBuilder builder = new DocumentBuilder(doc);
```

بشكل افتراضي، يكون مؤشر الـ builder في بداية القسم الأول. يمكنك تحريكه باستخدام طرق مثل `MoveToDocumentEnd()` أو `MoveToParagraph(index)` إذا أردت وضع الزر في مكان آخر.

## الخطوة 4: إدراج عنصر تحكم ActiveX CommandButton

الآن يأتي جوهر الدرس: إدراج **ActiveX control word** يظهر كزر قابل للنقر. طريقة `InsertForms2OleControl` تأخذ وسيطين—نوع العنصر وعنوان (أو اسم) العنصر.

```csharp
// Step 4: Insert an ActiveX CommandButton control with the caption "ClickMe"
builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");
```

* **لماذا نستخدم `OleControlType.CommandButton`؟**  
  يخبر Word بإنشاء زر أمر Forms 2.0 كلاسيكي، يعرض عنوانًا ويمكن ربطه بماكرو أو سكريبت VBA لاحقًا.

* **ماذا يفعل العنوان؟**  
  السلسلة `"ClickMe"` تصبح النص الظاهر على الزر. يمكنك تغييره إلى أي شيء يناسب واجهة المستخدم الخاصة بك.

### إدراج الزر في موقع محدد

إذا كنت تحتاج الزر بعد فقرة معينة، حرك الـ builder أولاً:

```csharp
builder.MoveToParagraph(2); // moves to the third paragraph (zero‑based index)
builder.InsertParagraph(); // optional: add a blank line before the button
builder.InsertForms2OleControl(OleControlType.CommandButton, "Submit");
```

## الخطوة 5: حفظ المستند المعدل

بعد إدراج العنصر، احفظ التغييرات في ملف جديد (أو استبدل الأصلي).

```csharp
// Step 5: Save the modified document
string outputPath = @"C:\Docs\output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

عند فتح `output.docx` في نسخة Word لسطح المكتب، سترى الزر المسمى **ClickMe** (أو **Submit**، حسب العنوان الذي استخدمته). النقر على الزر في وضع التصميم لا يفعل شيئًا بشكل افتراضي؛ يمكنك تعيين ماكرو لاحقًا عبر تبويب “Developer” في Word.

## مثال كامل قابل للتنفيذ

فيما يلي برنامج مستقل يوضح سير العمل بالكامل. انسخه في `Program.cs` لتطبيق console جديد وشغّله.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXControlWordDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\Docs\input.docx";
            string outputPath = @"C:\Docs\output.docx";

            // 1️⃣ Load the source document
            Document doc = new Document(inputPath);

            // 2️⃣ Create a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Optional: move to the end of the document
            builder.MoveToDocumentEnd();
            builder.Writeln(); // add a blank line before the button

            // 3️⃣ Insert the ActiveX CommandButton (the core of the activex control word)
            builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");

            // 4️⃣ Save the result
            doc.Save(outputPath);
            Console.WriteLine($"Successfully saved the document with an ActiveX button to: {outputPath}");
        }
    }
}
```

### الناتج المتوقع

* يطبع الـ console رسالة نجاح مع مسار الإخراج.
* فتح `output.docx` يظهر زر **ClickMe** في الموقع الذي أدخله الـ builder.
* يمكن تحديد الزر، تغيير حجمه، أو تعيين ماكرو عبر **Developer → Design Mode** في Word.

## الأسئلة الشائعة ومعالجة الحالات الخاصة

| السؤال | الجواب |
|----------|--------|
| **كيف يمكن إدراج زر ActiveX في الترويسة/التذييل؟** | حرك الـ builder إلى الترويسة/التذييل باستخدام `builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` قبل استدعاء `InsertForms2OleControl`. |
| **ماذا لو أردت مربع اختيار بدلاً من الزر؟** | استخدم `OleControlType.CheckBox` وقدم عنوانًا مثل `"Agree"`. |
| **هل سيعمل الزر في Word Online؟** | لا. Word Online لا يدعم عناصر تحكم Forms 2.0 Legacy ActiveX. الزر يُعرض فقط في عميل سطح المكتب. |
| **هل يمكن ضبط حجم الزر برمجيًا؟** | بعد الإدراج، احصل على كائن `Shape` عبر `builder.CurrentParagraph.Runs[0].GetShape()` واضبط `Width`/`Height`. |
| **هل هناك طريقة لتعيين ماكرو من الكود؟** | Aspose.Words لا يتيح تعديل الماكرو. يجب فتح المستند في Word وإرفاق ماكرو يدويًا أو استخدام Office Interop API. |

## نصائح للاستخدام في الإنتاج

* **تجنب المسارات الصلبة** – استخدم `Path.Combine` وملفات الإعداد.
* **تحرير `Document`** – ضعها داخل عبارة `using` إذا كنت تتعامل مع ملفات كبيرة لتحرير الذاكرة بسرعة.
* **تحقق من صحة الإخراج** – افحص برمجيًا أن المستند يحتوي على شكل من نوع `OleControl` عبر تكرار `doc.GetChildNodes(NodeType.Shape, true)`.
* **ملاحظة أمان** – عناصر تحكم ActiveX يمكنها تشغيل كود على جهاز العميل. وزع المستندات فقط للمستخدمين الموثوق بهم وفكّر في التوقيعات الرقمية.

## الخلاصة

أنت الآن تعرف كيف تضيف **ActiveX control word** إلى مستند Word باستخدام C#. عبر تحميل المستند، إنشاء `DocumentBuilder`, إدراج زر أمر باستخدام `InsertForms2OleControl`، وحفظ الملف، يمكنك أتمتة إنشاء نماذج Word تفاعلية. جرّب قيم `OleControlType` أخرى، وضع العناصر في الترويسات أو الجداول، وادمجها مع ماكرو للحصول على تجارب مستخدم أغنى.

---

*الخطوات التالية*: استكشف **كيفية إدراج عناصر تحكم ActiveX** من أنواع أخرى، تعلم **كيفية إضافة معالجات أحداث زر الأمر** عبر VBA، واقرأ عن **أفضل ممارسات إدراج زر ActiveX** لتوافق متعدد المنصات.

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [Embedding OLE Objects and ActiveX Controls in Word Documents](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}