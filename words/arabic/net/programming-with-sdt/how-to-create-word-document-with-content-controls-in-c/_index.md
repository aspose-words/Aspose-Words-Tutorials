---
category: general
date: 2026-09-05
description: إنشاء مستند Word باستخدام Aspose.Words، تعيين نص العنصر النائب، إضافة
  عنصر تحكم، وحفظ المستند كملف docx باستخدام C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- set placeholder text
- save document as docx
- how to add control
- how to create tag
language: ar
lastmod: 2026-09-05
og_description: إنشاء مستند Word باستخدام Aspose.Words لـ .NET، تعيين نص العنصر النائب،
  إضافة تحكم، وحفظ المستند بصيغة docx. اتبع هذا الدرس الكامل.
og_image_alt: Screenshot showing a word document created with a content control placeholder
og_title: إنشاء مستند Word مع عناصر تحكم المحتوى في C# – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create word document with Aspose.Words, set placeholder text, add control,
    and save document as docx in C#.
  headline: How to create word document with content controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Content Control
- Document Generation
title: كيفية إنشاء مستند Word مع عناصر التحكم في المحتوى في C#
url: /ar/net/programming-with-sdt/how-to-create-word-document-with-content-controls-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مستند Word مع عناصر تحكم المحتوى في C#

إذا كنت بحاجة إلى **إنشاء مستند Word** يتضمن عناصر تحكم محتوى منظمة، يوضح لك هذا الدليل كيفية إضافة علامة نصية عادية، **تعيين نص العنصر النائب**، و**حفظ المستند كملف docx** باستخدام Aspose.Words for .NET. المثال قابل للتنفيذ بالكامل ويظهر النهج الموصى به لإنشاء مستندات Word برمجيًا.

سوف تتعلم كيف:

* تهيئة ملف Word فارغ باستخدام `Document` و `DocumentBuilder`.
* **كيفية إضافة عنصر تحكم** (ـ `StructuredDocumentTag`) إلى جسم المستند.
* **كيفية إنشاء علامة** بعنوان وعنصر نائب يوجه المستخدم النهائي.
* حفظ النتيجة باستخدام `document.Save`، مع ضمان أن الملف صالح كـ `.docx`.

يفترض الدليل أن لديك بيئة تطوير C# أساسية ورخصة لـ Aspose.Words (التقييم المجاني يكفي لأغراض التعلم).

---

## المتطلبات المسبقة

| المتطلب | السبب |
|-------------|--------|
| .NET 6.0 أو أحدث | يوفر بيئة تشغيل Aspose.Words for .NET. |
| حزمة NuGet Aspose.Words for .NET | تزودك بفئات `Document` و `DocumentBuilder` و `StructuredDocumentTag`. |
| بيئة تطوير مثل Visual Studio 2022 | تجعل تشغيل وتصحيح العينة أمرًا سهلًا. |

ثبت الحزمة باستخدام .NET CLI:

```bash
dotnet add package Aspose.Words
```

---

## الخطوة 1: إعداد المشروع **لإنشاء مستند Word**

أنشئ مشروع وحدة تحكم جديد (أو أضف الشيفرة إلى مشروع موجود). السطران الأولان ينشئان ملف Word فارغًا و`DocumentBuilder` يتيح لك كتابة المحتوى.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Initialize a new empty document.
Document document = new Document();

// Obtain a builder positioned at the start of the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` يمثل بنية الملف، بينما `DocumentBuilder` يتتبع نقطة الإدراج. هذا النمط هو الأساس لأي سيناريو توليد Word.

---

## الخطوة 2: **كيفية إضافة عنصر تحكم** – إنشاء عنصر تحكم محتوى نصي عادي (علامة)

عنصر التحكم في Word يُسمى *structured document tag* (SDT). الشيفرة التالية تنشئ SDT نصيًا عاديًا، تعين عنوانًا، وتحدد العنصر النائب الذي يظهر عند فتح المستند.

```csharp
// Create a plain‑text StructuredDocumentTag (SDT) at block level.
StructuredDocumentTag contentControl = new StructuredDocumentTag(
    document, SdtType.PlainText, MarkupLevel.Block);

// Assign a meaningful title – useful for later retrieval.
contentControl.Title = "CustomerName";

// Define the placeholder text that prompts the user.
contentControl.PlaceholderName = "Enter name";

// Insert the tag at the builder's current cursor location.
builder.InsertNode(contentControl);
```

**لماذا هذا مهم:**  
* خاصية `Title` تعمل كمُعرّف ثابت، مما يتيح لك تحديد أو استبدال العنصر برمجيًا لاحقًا.  
* `PlaceholderName` يوفر إرشادًا بصريًا لمستهلك المستند دون الحاجة إلى شفرة واجهة مستخدم إضافية.

![Create word document with content control placeholder](image.png)

*نص بديل للصورة: إنشاء مستند Word مع عنصر تحكم محتوى يُظهر نص العنصر النائب.*

---

## الخطوة 3: نقل المؤشر داخل عنصر التحكم وكتابة النص الافتراضي

بعد إدراج العنصر، لا يزال مؤشر الـ builder يشير إلى خارجه. انقل المؤشر إلى داخل العلامة بحيث تصبح الكتابات اللاحقة جزءًا من محتوى العنصر.

```csharp
// Position the builder inside the newly added content control.
builder.MoveTo(contentControl);

// Write default text that appears when the placeholder is cleared.
builder.Write("John Doe");
```

إذا رغبت بترك العنصر فارغًا، احذف استدعاء `Write`. سيظل العنصر النائب مرئيًا حتى يكتب المستخدم قيمة.

---

## الخطوة 4: **تعيين نص العنصر النائب** (نهج بديل)

أحيانًا تحتاج إلى تغيير العنصر النائب بعد إنشاء العلامة. يمكنك تعديل خاصية `PlaceholderName` مباشرة:

```csharp
contentControl.PlaceholderName = "Type the customer's full name here";
```

تغيير العنصر النائب **لا** يؤثر على المحتوى الموجود، مما يجعله آمنًا لتحديث تلميحات الواجهة دون تعديل البيانات التي أدخلها المستخدم.

---

## الخطوة 5: **حفظ المستند كملف docx**

احفظ المستند الموجود في الذاكرة إلى ملف فعلي. طريقة `Save` تحدد الصيغة تلقائيًا بناءً على امتداد الملف.

```csharp
// Save the document in DOCX format.
document.Save("YOUR_DIRECTORY/SdtExample.docx");
```

إذا كنت بحاجة إلى صيغة مختلفة (مثل PDF أو HTML)، قدم قيمة من تعداد `SaveFormat`:

```csharp
document.Save("SdtExample.pdf", SaveFormat.Pdf);
```

---

## الخطوة 6: مثال كامل قابل للتنفيذ

تجميع الأجزاء معًا ينتج برنامجًا مختصرًا يوضح **كيفية إنشاء علامة**، تعيين العنصر النائب، و**حفظ المستند كملف docx**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Create a plain‑text content control (tag).
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            document, SdtType.PlainText, MarkupLevel.Block);
        sdt.Title = "CustomerName";
        sdt.PlaceholderName = "Enter name";

        // 3. Insert the control and move inside it.
        builder.InsertNode(sdt);
        builder.MoveTo(sdt);

        // 4. Write default text (optional).
        builder.Write("John Doe");

        // 5. Save the file as DOCX.
        document.Save("SdtExample.docx");
        Console.WriteLine("Word document created successfully.");
    }
}
```

**الناتج المتوقع:**  
تشغيل البرنامج ينشئ `SdtExample.docx` يحتوي على فقرة واحدة مع عنصر تحكم محتوى نصي عادي بعنوان *CustomerName*. يظهر العنصر النصي “John Doe” كمحتوى مبدئي؛ إذا أزيل النص الافتراضي، يظهر العنصر النائب “Enter name” باللون الرمادي الفاتح عند فتح الملف في Microsoft Word.

---

## الاختلافات الشائعة وحالات الحافة

| السيناريو | التعديل الموصى به |
|----------|------------------------|
| **عناصر تحكم متعددة** | كرّر الخطوات 2‑4 لكل حقل، مع إعطاء كلٍ منها `Title` فريد. |
| **عنصر تحكم نص غني** | استخدم `SdtType.RichText` بدلاً من `PlainText`. |
| **قسم متكرر** | اختر `SdtType.RepeatingSection` وأضف عناصر تحكم فرعية داخل القسم. |
| **مستند موجود** | حمّل ملفًا موجودًا بـ `new Document("template.docx")` وأدرج عناصر التحكم في الموقع المطلوب. |
| **عنصر نائب يونيكود** | عيّن `PlaceholderName` إلى أي سلسلة يونيكود؛ Word سيعرضها بشكل صحيح. |
| **مستندات كبيرة** | حرّر `DocumentBuilder` بعد الاستخدام لتحرير الذاكرة (`builder.Dispose();`). |

**نصيحة محترف:** عندما تحتاج لاسترجاع القيمة التي أدخلها المستخدم لاحقًا، استدعِ `StructuredDocumentTag.GetText()` بعد حفظ المستند وإعادة فتحه. تُعيد هذه الطريقة النص الداخلي دون العنصر النائب.

**احذر من:** استخدام عنصر نائب يطابق النص الافتراضي قد يسبب ارتباكًا، لأن Word يخفي العنصر النائب عند وجود أي نص. احرص على تمييزهما.

---

## الخلاصة

أنت الآن تعرف **كيفية إنشاء مستند Word** برمجيًا، **كيفية إضافة عنصر تحكم**، **كيفية إنشاء علامة**، **تعيين نص العنصر النائب**، و**حفظ المستند كملف docx** باستخدام Aspose.Words for .NET. يمكن نسخ المثال الكامل إلى أي مشروع C# وتوسيعه لدعم أنواع عناصر تحكم إضافية، أقسام متكررة، أو دمجه مع مصادر بيانات.

الخطوات التالية التي قد تستكشفها تشمل:

* إضافة **عناصر تحكم محتوى صورة** (`SdtType.Picture`) لتضمين رسومات يقدمها المستخدم.  
* استخدام **الربط** لربط SDTs ببيانات XML لسيناريوهات الدمج البريدي.  
* تحويل الـ DOCX المُولد إلى PDF (`SaveFormat.Pdf`) للتوزيع.

جرّب أنواع علامات مختلفة ورسائل عناصر نائب لتتناسب مع سير عمل تطبيقك. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مستند Word باستخدام Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [إنشاء مستند Word مع جدول باستخدام Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [إنشاء مستند Word مع الترويسة والتذييل باستخدام Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}