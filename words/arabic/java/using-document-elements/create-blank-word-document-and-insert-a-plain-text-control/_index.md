---
category: general
date: 2026-09-18
description: إنشاء مستند Word فارغ باستخدام C# وتعيين نص العنصر النائب، ثم حفظ المستند
  بصيغة docx. تعلم إدراج عنصر تحكم نص عادي وإضافة اسم العنصر النائب.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set placeholder text
- save document as docx
- insert plain text control
- add placeholder name
language: ar
lastmod: 2026-09-18
og_description: إنشاء مستند Word فارغ باستخدام C#. تعيين نص العنصر النائب، إدراج عنصر
  تحكم نص عادي، إضافة اسم العنصر النائب، وحفظ المستند بصيغة docx.
og_image_alt: Screenshot of a Word document showing a plain‑text content control with
  placeholder text
og_title: إنشاء مستند Word فارغ بنص نائب – دليل C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  headline: Create blank Word document and insert a plain‑text control
  type: TechArticle
- description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  name: Create blank Word document and insert a plain‑text control
  steps:
  - name: An empty Word file (the **blank Word document** you created)
    text: An empty Word file (the **blank Word document** you created)
  - name: A plain‑text content control (the **insert plain text control** step)
    text: A plain‑text content control (the **insert plain text control** step)
  - name: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
    text: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
  - name: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
    text: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
  - name: A line of regular text after the control, demonstrating that normal content
      can follow
    text: A line of regular text after the control, demonstrating that normal content
      can follow
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: إنشاء مستند Word فارغ وإدراج عنصر تحكم نص عادي
url: /ar/java/using-document-elements/create-blank-word-document-and-insert-a-plain-text-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word فارغ وإدراج عنصر تحكم نص عادي

إذا كنت بحاجة إلى **إنشاء مستند Word فارغ** برمجياً، يوضح لك هذا الدليل كيفية القيام بذلك باستخدام C#. ستتعلم **إدراج عنصر تحكم نص عادي**، **تعيين نص العنصر النائب**، **إضافة اسم العنصر النائب**، وأخيراً **حفظ المستند كملف docx**. الخطوات مكتملة ذاتياً، لذا يمكنك نسخ الكود إلى أي مشروع .NET وتشغيله فوراً.

العمل مع ملفات Word غالباً ما يتطلب نقطة بداية نظيفة—مستند فارغ يحتوي مسبقاً على العناصر التي سيملأها المستخدمون. في نهاية هذا الدرس ستحصل على ملف `.docx` يحتوي على عنصر تحكم محتوى نص عادي مع عنصر نائب مفيد، يليه محتوى عادي.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضاً مع .NET Framework 4.6+)
- إشارة إلى مكتبة **Aspose.Words for .NET** (متاحة عبر NuGet `Install-Package Aspose.Words`)
- إلمام أساسي بتطبيقات C# console
- إذن كتابة للمجلد الناتج الذي تحدده في `doc.save(...)`

## ما ستبنيه

المستند النهائي (`SDT.docx`) يحتوي على:

1. ملف Word فارغ (الـ **blank Word document** الذي أنشأته)
2. عنصر تحكم محتوى نص عادي (خطوة **insert plain text control**)
3. نص العنصر النائب الذي يظهر داخل العنصر حتى يكتب المستخدم شيئاً (خطوة **set placeholder text**)
4. اسم عنصر نائب يمكن استخدامه للوصول البرمجي لاحقاً (خطوة **add placeholder name**)
5. سطر من النص العادي بعد العنصر، يوضح أن المحتوى العادي يمكن أن يتبع

## الخطوة 1: إنشاء مستند Word فارغ

العملية الأولى هي إنشاء كائن `Document` فارغ. هذا الكائن يمثل **مستند Word فارغ** جديد تماماً في الذاكرة.

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

// Step 1: Create a new blank document
Document doc = new Document();
```

*لماذا هذا مهم:* كائن `Document` الفارغ يمنحك التحكم الكامل في كل عنصر تضيفه، مما يضمن عدم وجود أنماط أو أقسام مخفية تتداخل مع عنصر التحكم الذي ستدرجه لاحقاً.

## الخطوة 2: تهيئة DocumentBuilder

`DocumentBuilder` هو الفئة المساعدة التي تسمح لك بالكتابة داخل الـ `Document`. تتعقب موضع المؤشر الحالي وتوفر طرقاً لإدراج جميع أنواع كائنات Word.

```csharp
// Step 2: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

*لماذا هذا مهم:* استخدام `DocumentBuilder` يبسط عملية إضافة **عنصر تحكم نص عادي** لأن الـ builder يعرف نقطة الإدراج الدقيقة.

## الخطوة 3: إدراج عنصر تحكم نص عادي

الآن نضيف **عنصر تحكم محتوى نص عادي** (المعروف أيضاً باسم Structured Document Tag أو SDT). النوع `StructuredDocumentTagType.PLAIN_TEXT` يخبر Word بمعالجة المحتوى كنص عادي، وليس تنسيقاً غنياً.

```csharp
// Step 3: Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");
```

*لماذا هذا مهم:* طريقة `InsertStructuredDocumentTag` تنشئ العنصر وتعيد مرجعاً (`sdt`) يمكنك تعديل إعداداته لاحقاً، مثل إضافة نص العنصر النائب أو اسم مخصص.

## الخطوة 4: تعيين نص العنصر النائب وإضافة اسم العنصر النائب

نص العنصر النائب يمنح المستخدم إشارة بصرية حول ما يجب كتابته. خطوة **إضافة اسم العنصر النائب** تعين معرفاً برمجياً يمكنك الاستعلام عنه لاحقاً باستخدام `doc.GetChildNodes` أو واجهات برمجة تطبيقات مماثلة.

```csharp
// Step 4a: Set a placeholder text that appears when the SDT is empty
sdt.SetPlaceholderName("Enter text…");

// Step 4b: Add a placeholder name (tag ID) for later retrieval
sdt.Tag = "MyTag";
```

*لماذا هذا مهم:* `SetPlaceholderName` يتحكم في نص التلميح الرمادي المعروض داخل عنصر التحكم. ضبط `Tag` (الإجراء **add placeholder name**) يتيح لك العثور على العنصر في شجرة المستند دون الحاجة إلى مسح الملف بالكامل.

## الخطوة 5: إضافة محتوى عادي بعد العنصر

لإثبات أن المستند يستمر بشكل طبيعي بعد العنصر، نكتب سطرًا بسيطًا من النص.

```csharp
// Step 5: Add regular content after the SDT
builder.Writeln("After the tag.");
```

## الخطوة 6: حفظ المستند كملف docx

أخيراً، نقوم بحفظ المستند الموجود في الذاكرة إلى القرص. هذه هي عملية **حفظ المستند كملف docx** التي تنتج الملف الذي يمكنك فتحه في Microsoft Word.

```csharp
// Step 6: Save the document as a .docx file
string outputPath = @"YOUR_DIRECTORY/SDT.docx";
doc.Save(outputPath);
```

*لماذا هذا مهم:* استخدام تنسيق `.docx` يضمن أقصى توافق مع إصدارات Word الحديثة، Google Docs، وأدوات أخرى متوافقة مع Office.

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه إلى مشروع console‑app. استبدل `YOUR_DIRECTORY` بمسار مجلد فعلي على جهازك.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

namespace WordSdtExample
{
    class Program
    {
        static void Main()
        {
            // Create a new blank Word document
            Document doc = new Document();

            // Initialize a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");

            // Set a placeholder text that appears when the SDT is empty
            sdt.SetPlaceholderName("Enter text…");

            // Add a placeholder name (tag) for later retrieval
            sdt.Tag = "MyTag";

            // Add regular content after the SDT
            builder.Writeln("After the tag.");

            // Save the document as a .docx file
            string outputPath = @"C:\Temp\SDT.docx"; // change to your folder
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### النتيجة المتوقعة

- فتح `SDT.docx` في Word يظهر صندوق رمادي فارغ مع النص **Enter text…** بداخله.
- الصندوق هو عنصر تحكم محتوى نص عادي؛ يمكنك الكتابة مباشرةً فيه.
- أسفل الصندوق، يظهر السطر **After the tag.** كنص فقرة عادي.

إذا لم يظهر العنصر النائب، تحقق من أنك تستخدم نسخة حديثة من Aspose.Words (v23.1 أو أحدث) وأن المستند يُفتح في نسخة Word تدعم عناصر التحكم (Word 2007+).

## الاختلافات الشائعة وحالات الحافة

| السيناريو | كيفية تعديل الكود |
|----------|-------------------|
| **Multiple placeholders** | استدعِ `InsertStructuredDocumentTag` مرة أخرى بمعرف علامة مختلف واسم عنصر نائب. |
| **Rich‑text control** | استخدم `StructuredDocumentTagType.RichText` بدلاً من `PlainText`. |
| **Setting default text** | بعد الإدراج، عيّن `sdt.Text = "Default value";` – هذا النص يستبدل العنصر النائب عند تحميل المستند. |
| **Saving to a stream** | استبدل `doc.Save(outputPath);` بـ `doc.Save(stream, SaveFormat.Docx);` لإرسال الملف عبر HTTP. |
| **Changing placeholder color** | استخدم `sdt.PlaceholderTextColor = System.Drawing.Color.Gray;` (يتطلب `using System.Drawing`). |

## نصائح احترافية

- **إعادة استخدام معرف العلامة**: الحفاظ على نفس العلامة (`MyTag`) عبر المستندات يتيح لك أتمتة تعبئة البيانات لاحقاً باستخدام `doc.Range.Replace` أو `StructuredDocumentTagCollection`.
- **تجنب المسارات الصلبة**: استخدم `Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), "SDT.docx")` لموقع إخراج قابل للنقل.
- **الأداء**: إذا كنت بحاجة لتوليد آلاف المستندات، أنشئ قالب `Document` واحد يحتوي على الـ SDT مسبقاً، ثم استنسخه باستخدام `doc.Clone()` لكل تكرار.

## الخلاصة

أنت الآن تعرف كيف **تنشئ مستند Word فارغ**، **تدرج عنصر تحكم نص عادي**، **تعيّن نص العنصر النائب**، **تضيف اسم العنصر النائب**، وت **حفظ المستند كملف docx** باستخدام Aspose.Words for .NET. هذا النمط يشكل الأساس لبناء قوالب Word مملوءة بنماذج، تقارير آلية، أو أي حل يتطلب عناصر نائب قابلة للتحرير من قبل المستخدم.

لا تتردد في تجربة أنواع تحكم أخرى، دمج عدة عناصر نائب، أو دمج هذا الكود في واجهة برمجة تطبيقات ويب تُعيد ملف `.docx` المُولد مباشرةً إلى المستدعين. للخطوة التالية، استكشف **ملء عنصر التحكم بالبيانات برمجياً** أو **تحويل ملف Word المُولد إلى PDF** باستخدام ميزات التحويل المدمجة في Aspose.Words. Happy coding!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك الخاصة.

- [Insert Text Input Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}