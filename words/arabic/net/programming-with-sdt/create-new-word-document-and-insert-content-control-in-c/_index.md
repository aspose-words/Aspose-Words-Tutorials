---
category: general
date: 2026-10-13
description: إنشاء مستند Word جديد في C# وإدراج عنصر تحكم محتوى بنص نائب. تعلّم كيفية
  تعيين نص نائب وحفظ مستند Word بكفاءة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create new word document
- insert content control
- set placeholder text
- how to create sdt
- save word document c#
language: ar
lastmod: 2026-10-13
og_description: إنشاء مستند Word جديد في C# باستخدام Aspose.Words، وإدراج عنصر تحكم
  محتوى، وتعيين نص العنصر النائب، وحفظ مستند Word—كل ذلك في دليل واحد.
og_image_alt: Screenshot of a Word document showing a content control placeholder
og_title: إنشاء مستند Word جديد وإدراج عنصر تحكم المحتوى في C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  headline: Create new Word document and insert content control in C#
  type: TechArticle
- description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  name: Create new Word document and insert content control in C#
  steps:
  - name: Run the console app.
    text: Run the console app.
  - name: Open `output.docx` in Microsoft Word.
    text: Open `output.docx` in Microsoft Word.
  - name: Verify that the placeholder text appears inside a gray‑shaded box.
    text: Verify that the placeholder text appears inside a gray‑shaded box.
  - name: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
    text: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
  type: HowTo
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: إنشاء مستند Word جديد وإدراج عنصر تحكم المحتوى في C#
url: /ar/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word جديد وإدراج عنصر تحكم المحتوى في C#

إذا كنت بحاجة إلى **إنشاء مستند Word جديد** برمجيًا، يوضح لك هذا الدليل كيفية القيام بذلك باستخدام Aspose.Words for .NET. ستتعلم **إدراج عنصر تحكم المحتوى**، وتعيين **نص العنصر النائب**، وأخيرًا **حفظ مستند Word C#** كود يمكنك نسخه إلى مشروعك.

يمر الدليل عبر كل خطوة، يشرح لماذا كل استدعاء API مهم، ويغطي الاختلافات الشائعة مثل إضافة SDT بنص غني أو معالجة المستندات الموجودة. في النهاية ستحصل على مثال كامل قابل للتنفيذ يمكنك تكييفه للفواتير أو العقود أو أي مخرجات Word قالبية.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من أن لديك:

* .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.7+)
* حزمة NuGet لـ Aspose.Words for .NET (`Install-Package Aspose.Words`)
* بيئة تطوير متكاملة مثل Visual Studio 2022 أو Visual Studio Code

لا توجد مكتبات إضافية مطلوبة.

## إنشاء مستند Word جديد باستخدام Aspose.Words

الخطوة الأولى هي إنشاء كائن `Document`. هذا الكائن يمثل ملف Word فارغ في الذاكرة.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Step 1: Create a new, empty document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` يمنحك API سلس لإدراج العناصر في موضع المؤشر الحالي. لأن المستند فارغ، يبدأ المؤشر في بداية القسم الأول (والوحيد).

## إدراج عنصر تحكم المحتوى (StructuredDocumentTag)

**عنصر تحكم المحتوى** في Word يُسمى Structured Document Tag (SDT). الكود التالي ينشئ SDT نص عادي، يحدد عنوانه، ويعرّف نص العنصر النائب الذي يظهر عندما يفتح المستخدم الملف.

```csharp
// Step 2: Create a plain‑text StructuredDocumentTag (SDT)
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Title is used for identification in the document outline
    Title = "CustomerName",
    // Placeholder text is visible until the user types a value
    PlaceholderName = "Enter name here"
};

// Step 3: Insert the SDT at the builder's current insertion point
builder.InsertNode(sdt);
```

**لماذا هذا مهم:**  
* `SdtType.PlainText` يقيّد المحتوى بسطر واحد من النص العادي، وهو مثالي للحقول البسيطة مثل الاسم أو البريد الإلكتروني.  
* ضبط `PlaceholderName` يوفر إشارة بصرية (`Enter name here`) توجه المستخدم النهائي.  

إذا كنت بحاجة إلى حقل أغنى (مثلاً نص متعدد الأسطر أو منتقي تاريخ)، استبدل `SdtType.PlainText` بـ `SdtType.RichText` أو `SdtType.Date`.

## إضافة نص محيط اختياري

معظم القوالب تتضمن تسمية قبل عنصر التحكم. يمكنك إضافتها باستخدام نفس كائن `DocumentBuilder`:

```csharp
// Optional: add a label before the content control
builder.Writeln("Customer Name:");
builder.InsertNode(sdt);   // Re‑insert the SDT after the label
```

الملف الناتج يظهر:

```
Customer Name: [Enter name here]
```

## حفظ مستند Word بنمط C#

أخيرًا، اكتب المستند إلى القرص. Aspose.Words يحدد الصيغة تلقائيًا من امتداد الملف.

```csharp
// Step 4: Save the document to verify the result
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

عند فتح `output.docx` في Microsoft Word، سترى نص العنصر النائب داخل عنصر تحكم مظلّل بالرمادي. يمكن للمستخدمين النقر على العنصر واستبدال النص النائب بقيمتهم الخاصة.

## مثال كامل قابل للتنفيذ

فيما يلي برنامج كونسول مستقل يجمع كل شيء معًا. انسخ الكود إلى مشروع كونسول جديد وشغّله.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Add a descriptive label
            builder.Writeln("Customer Name:");

            // Create and configure a plain‑text content control (SDT)
            StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
            {
                Title = "CustomerName",
                PlaceholderName = "Enter name here"
            };

            // Insert the SDT after the label
            builder.InsertNode(sdt);

            // Save the document
            string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**الناتج المتوقع** (الكونسول):

```
Document saved to C:\YourProject\bin\Debug\net6.0\output.docx
```

فتح `output.docx` يظهر سطرًا واحدًا مع التسمية *Customer Name:* متبوعًا بعنصر تحكم يعرض *Enter name here*.

## الاختلافات الشائعة وحالات الحافة

| السيناريو | تغيير الكود | السبب |
|----------|-------------|--------|
| **حقل نص غني** | `new StructuredDocumentTag(doc, SdtType.RichText, true)` | يسمح بإدخال متعدد الأسطر وتنسيق أساسي. |
| **عنصر تحكم للقراءة فقط** | `sdt.LockContentControl = true;` | يمنع المستخدمين من تعديل محتوى العنصر. |
| **ملء مسبق بالبيانات** | `sdt.AppendChild(new Run(doc, "John Doe"));` | يدرج قيمة افتراضية تستبدل العنصر النائب. |
| **إضافة إلى مستند موجود** | Load with `new Document("template.docx")` instead of an empty `Document` | يمكن من سيناريوهات القوالب حيث يتم وضع العنصر في تخطيط مسبق. |
| **عناصر تحكم متعددة** | Repeat the creation block with different titles and placeholders | مفيد للنماذج التي تجمع عدة معلومات. |

### نصيحة احترافية

عند إنشاء مستندات كبيرة، أعد استخدام كائن `DocumentBuilder` واحد بدلاً من إنشاء كائن جديد لكل عنصر تحكم. هذا يقلل من استهلاك الذاكرة ويحسن الأداء.

## اختبار النتيجة

1. شغّل تطبيق الكونسول.  
2. افتح `output.docx` في Microsoft Word.  
3. تحقق من ظهور نص العنصر النائب داخل صندوق مظلّل بالرمادي.  
4. انقر على الصندوق، اكتب اسمًا، واحفظ الملف. النص المدخل يستبدل العنصر النائب.

إذا لم يظهر العنصر النائب، تأكد من أنك تستخدم Aspose.Words الإصدار 23.9 أو أحدث، حيث أن الإصدارات القديمة كان فيها خلل في `PlaceholderName` على SDT نص عادي.

## الخلاصة

أنت الآن تعرف كيف **تنشئ مستند Word جديد**، **تدرج عنصر تحكم المحتوى**، **تحدد نص العنصر النائب**، و**تحفظ مستند Word C#** باستخدام Aspose.Words. المثال الكامل يوضح النمط القياسي، وجدول الاختلافات يبين كيفية تكييف الحل لسيناريوهات أغنى.

بعد ذلك، قد ترغب في استكشاف:

* **إدراج عنصر تحكم للمواعيد** – استخدم تعداد `SdtType.Date`.  
* **ملء قالب بالبيانات** – اجمع `StructuredDocumentTag` مع حقول دمج البريد.  
* **تصدير إلى PDF** – استدعِ `doc.Save("output.pdf")` بعد إضافة عناصر التحكم.

لا تتردد في تجربة أنواع SDT مختلفة، وإعدادات القفل، والتنسيق لتتناسب مع متطلبات مشروعك. happy coding!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مستند Word جديد](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [إدراج حقل نموذج إدخال نص في مستند Word](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [إنشاء مستند Word باستخدام Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}