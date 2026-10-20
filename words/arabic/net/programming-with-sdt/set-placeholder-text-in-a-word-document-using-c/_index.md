---
category: general
date: 2026-10-20
description: تعيين نص العنصر النائب في مستند Word باستخدام C#. تعلّم كيفية إضافة التحكم
  وتعيين العنصر النائب بسرعة باستخدام Aspose.Words لـ .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- how to add control
- how to set placeholder
- generate word c#
language: ar
lastmod: 2026-10-20
og_description: تعيين نص العنصر النائب في مستند Word باستخدام C#. يوضح هذا الدرس كيفية
  إضافة التحكم، وتعيين العنصر النائب، وإنشاء ملفات Word برمجيًا.
og_image_alt: Screenshot of a Word document showing placeholder text created with
  C# code
og_title: تعيين نص العنصر النائب في مستند Word باستخدام C# – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Set placeholder text in a Word document using C#. Learn how to add
    control and set placeholder quickly with Aspose.Words for .NET.
  headline: Set placeholder text in a Word document using C#
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, and .NET
      6+. The same code runs unchanged.
    question: Does this work with .NET Core?
  - answer: Use `sdt.SetText("Default value")` after creating the SDT. The placeholder
      disappears once a value is set.
    question: Can I set a default value in addition to the placeholder?
  - answer: 'Load the document, locate the SDT by its `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag,
      true)`) and read `sdt.GetText()`. ## Conclusion You now know how to **set placeholder
      text** in a Word document using C#. By creating a plain‑text `StructuredDocumentTag`,
      assigning a title and place'
    question: What if I need to retrieve the entered value later?
  type: FAQPage
tags:
- C#
- Aspose.Words
- Word automation
- Content control
title: تعيين نص العنصر النائب في مستند Word باستخدام C#
url: /ar/net/programming-with-sdt/set-placeholder-text-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تعيين نص العنصر النائب في مستند Word باستخدام C#

إذا كنت بحاجة إلى **تعيين نص العنصر النائب** في ملف Microsoft Word أثناء إنشائه باستخدام C#، فإن هذا الدليل يوضح لك بالضبط كيف تفعل ذلك. سترى حلاً مختصراً من البداية إلى النهاية يضيف عنصر تحكم محتوى، يحدد العنصر النائب الخاص به، ويحفظ المستند — كل ذلك باستخدام Aspose.Words for .NET.

يتساءل العديد من المطورين **كيفية إضافة عنصر تحكم** إلى مستند Word أو **كيفية تعيين العنصر النائب** دون فتح Word يدويًا. يجيب هذا البرنامج التعليمي على تلك الأسئلة ويظهر أيضًا طريقة نظيفة لـ **إنشاء ملفات Word C#** جاهزة لإدخال المستخدم.

## ما ستحققه

* إنشاء مستند Word فارغ برمجيًا.
* إدراج Structured Document Tag (SDT) نص عادي، وهو الاسم التقني لعنصر التحكم بالمحتوى.
* تعيين عنوان ذو معنى ونص عنصر نائب لـ SDT.
* حفظ ملف `.docx` الناتج إلى القرص.

لا تحتاج إلى أدوات إضافية بخلاف مكتبة Aspose.Words وبيئة تطوير .NET 6 (أو أحدث).

## المتطلبات المسبقة

* .NET 6 SDK أو أحدث مثبت.  
* Visual Studio 2022 (أو أي بيئة تطوير تدعم .NET).  
* حزمة NuGet الخاصة بـ Aspose.Words for .NET (`Install-Package Aspose.Words`).  

> **نصيحة احترافية:** استخدم النسخة التجريبية المجانية من Aspose.Words إذا كنت تقوم بالاختبار فقط؛ فهي تضيف علامة مائية ولكنها تعمل بنفس طريقة النسخة المرخصة.

## الخطوة 1: إعداد المشروع واستيراد المساحات الاسمية

أنشئ مشروعًا جديدًا من نوع console وأضف توجيهات `using` المطلوبة. هذه التوجيهات تجلب فئات Aspose.Words الأساسية ومساحة الاسم markup إلى نطاق الرؤية.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // The complete solution starts here.
        }
    }
}
```

*لماذا هذه الخطوة مهمة:* استيراد `Aspose.Words.Markup` يمنحك الوصول إلى `StructuredDocumentTag` و `SdtType` و `MarkupLevel` — الكائنات المطلوبة لـ **إضافة عنصر تحكم** و **تعيين العنصر النائب**.

## الخطوة 2: إنشاء مستند فارغ وDocumentBuilder

`Document` تمثل ملف Word بالكامل، بينما `DocumentBuilder` يوفر مؤشرًا مريحًا لإدراج العناصر.

```csharp
// Step 2: Initialize a new empty document.
Document doc = new Document();

// DocumentBuilder starts at the beginning of the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*لماذا هذه الخطوة مهمة:* البدء بمستند نظيف يضمن أن العنصر النائب الذي تحدده يظهر بالضبط حيث تريد، دون تداخل مع المحتوى الموجود.

## الخطوة 3: إنشاء عنصر التحكم بالمحتوى (Structured Document Tag)

هنا نقوم بإنشاء SDT نص عادي، نعطيه عنوانًا، ونحدد نص العنصر النائب الذي سيشاهده المستخدم عندما يكون العنصر فارغًا.

```csharp
// Step 3: Build a plain‑text Structured Document Tag (SDT).
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,                     // Parent document
    SdtType.PlainText,       // Control type – plain text box
    MarkupLevel.Inline);     // Inline placement (behaves like a word)

sdt.Title = "CustomerName";                 // Logical name for the control
sdt.PlaceholderName = "Enter name here";    // Text shown when empty
```

*لماذا هذه الخطوة مهمة:* خاصية `Title` تتيح لك الإشارة إلى العنصر لاحقًا (مثلاً للربط بالبيانات). `PlaceholderName` هو بالضبط **نص العنصر النائب** الذي تريد ظهوره، لتوجيه المستخدم النهائي.

## الخطوة 4: إدراج العنصر في موضع المؤشر الحالي

باستخدام `DocumentBuilder`، أدخل الـ SDT في المستند حيث يكون المؤشر الحالي للـ builder.

```csharp
// Step 4: Insert the SDT into the document.
builder.InsertNode(sdt);
```

*لماذا هذه الخطوة مهمة:* إدراج العقدة يربط العنصر بالـ DOM الخاص بالمستند. إذا احتجت إلى إضافة عدة عناصر نائب، يمكنك تحريك مؤشر الـ builder وتكرار هذه الخطوة.

## الخطوة 5: حفظ المستند

أخيرًا، احفظ المستند إلى القرص. استبدل `YOUR_DIRECTORY` بمسار فعلي على جهازك.

```csharp
// Step 5: Save the .docx file.
string outputPath = @"C:\Temp\SDT.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

عند فتح `SDT.docx` في Microsoft Word، سترى مربع نص مدمج مظلل بالرمادي يحتوي على **Enter name here**. النقر داخل المربع يزيل العنصر النائب، مما يسمح للمستخدم بكتابة اسم العميل.

### النتيجة المتوقعة

| موقع الملف | معاينة المحتوى |
|---------------|-----------------|
| `C:\Temp\SDT.docx` | عنصر نائب مدمج **Enter name here** داخل عنصر تحكم محتوى نص عادي بعنوان *CustomerName*. |

## الحالات الخاصة والاختلافات

| الحالة | التعديل الموصى به |
|-----------|------------------------|
| **عناصر نائب متعددة** | إنشاء كائنات `StructuredDocumentTag` إضافية ذات قيم `Title` و `PlaceholderName` مختلفة، ثم إدراج كل منها حيثما يلزم. |
| **عنصر نائب نص غني** | استخدم `SdtType.RichText` بدلاً من `PlainText` للسماح بالتنسيق داخل العنصر النائب. |
| **عنصر تحكم على مستوى الفقرة** | غيّر `MarkupLevel.Inline` إلى `MarkupLevel.Block` لجعل العنصر يتصرف كفقرة كاملة. |
| **العنصر النائب غير مرئي** | تأكد من أن إعدادات عرض المستند في Word ليست مضبوطة لإخفاء عناصر التحكم بالمحتوى (`File → Options → Advanced → Show content controls`). |
| **الحفظ إلى تدفق** | استدعِ `doc.Save(stream, SaveFormat.Docx)` إذا كنت بحاجة لإرسال الملف عبر HTTP بدلاً من حفظه على القرص. |

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه، لصقه، وتشغيله. يتضمن جميع الخطوات السابقة في طريقة `Main` واحدة.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Position a builder at the start of the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Define a plain‑text content control (SDT) with placeholder text.
            StructuredDocumentTag sdt = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Inline);

            sdt.Title = "CustomerName";                 // Logical identifier
            sdt.PlaceholderName = "Enter name here";    // The placeholder you see in Word

            // 4️⃣ Insert the SDT into the document.
            builder.InsertNode(sdt);

            // 5️⃣ Save the document to disk.
            string outputPath = @"C:\Temp\SDT.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document successfully saved to {outputPath}");
        }
    }
}
```

شغّل البرنامج، افتح الملف المُنشأ، وسترى نص العنصر النائب جاهزًا لإدخال المستخدم.

## الأسئلة الشائعة

**س: هل يعمل هذا مع .NET Core؟**  
ج: نعم. Aspose.Words for .NET متوافق مع .NET Core و .NET 5 و .NET 6+. الكود نفسه يعمل دون تعديل.

**س: هل يمكنني تعيين قيمة افتراضية بالإضافة إلى العنصر النائب؟**  
ج: استخدم `sdt.SetText("Default value")` بعد إنشاء الـ SDT. يختفي العنصر النائب بمجرد تعيين قيمة.

**س: ماذا لو احتجت لاسترجاع القيمة المدخلة لاحقًا؟**  
ج: حمّل المستند، ابحث عن الـ SDT باستخدام `Title` الخاص به (`doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`) واقرأ `sdt.GetText()`.

## الخلاصة

أنت الآن تعرف كيف **تعيين نص العنصر النائب** في مستند Word باستخدام C#. من خلال إنشاء `StructuredDocumentTag` نص عادي، تعيين عنوان وعنصر نائب، إدراجه باستخدام `DocumentBuilder`، وحفظ الملف، يمكنك **إضافة عنصر تحكم** و **إنشاء ملفات Word C#** برمجيًا.  

من هنا يمكنك استكشاف:

* إضافة عناصر تحكم نص غني أو قائمة منسدلة (`SdtType.RichText`, `SdtType.DropDownList`).  
* تعبئة عدة عناصر نائب من قاعدة بيانات.  
* تحويل الـ `.docx` المُنشأ إلى PDF باستخدام Aspose.Words.

جرّب أنواع عناصر التحكم المختلفة وأنماط العناصر النائبة لتتناسب مع احتياجات تطبيقك. ترميز سعيد!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [تعيين نص العنصر النائب في Aspose.Words – دليل C# كامل](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [إنشاء مستند Word برمجيًا – إضافة عنصر تحكم ومحتوى نائب](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [كيفية إضافة عنصر تحكم وإنشاء مستند Word باستخدام Aspose – كامل](/words/english/net/programming-with-sdt/how-to-add-content-control-and-create-word-document-with-asp/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}