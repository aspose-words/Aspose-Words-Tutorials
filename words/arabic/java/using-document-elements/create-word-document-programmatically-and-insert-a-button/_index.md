---
category: general
date: 2026-09-21
description: إنشاء مستند Word برمجيًا وتعلم كيفية حفظ زر مستند Word، وإدراج زر أمر
  Word، وتعيين تسمية زر الأمر باستخدام DocumentBuilder.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- save word document button
- insert command button word
- set command button caption
- how to use documentbuilder
language: ar
lastmod: 2026-09-21
og_description: إنشاء مستند Word برمجيًا باستخدام Aspose.Words. تعلّم كيفية حفظ زر
  مستند Word، وإدراج زر أمر Word، وتعيين تسمية زر الأمر، واستخدام DocumentBuilder
  للنماذج التفاعلية.
og_image_alt: Screenshot of a Word file that contains an inserted CommandButton created
  programmatically
og_title: إنشاء مستند Word برمجيًا وإضافة زر
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically and learn how to save word document
    button, insert command button word, and set command button caption using DocumentBuilder.
  headline: Create word document programmatically and insert a button
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: إنشاء مستند Word برمجيًا وإدراج زر
url: /ar/java/using-document-elements/create-word-document-programmatically-and-insert-a-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word برمجيًا وإدراج زر

إذا كنت بحاجة إلى **create word document programmatically**، توفر Aspose.Words واجهة برمجة تطبيقات سلسة تتيح لك إضافة عناصر تحكم تفاعلية مثل CommandButton. يشرح هذا البرنامج التعليمي أيضًا **how to use DocumentBuilder**، وكيفية **save word document button**، وكيفية **set command button caption** بحيث يظهر الزر تمامًا كما تتوقع داخل ملف .docx.

ستتعلم كيفية:

* تهيئة مستند فارغ باستخدام `Document`.
* العمل مع `DocumentBuilder` لتحرير المستند.
* إدراج **CommandButton** (`insert command button word`).
* تعيين اسم الزر والتسمية الظاهرة (`set command button caption`).
* حفظ النتيجة على القرص (`save word document button`).

تم كتابة الخطوات لمطوري .NET باستخدام C# وأحدث نسخة من Aspose.Words for .NET (v24.10). لا توجد حزم NuGet إضافية مطلوبة بخلاف Aspose.Words.

---

## ما تحتاجه قبل البدء

| المتطلبات المسبقة | السبب |
|-------------------|--------|
| Visual Studio 2022 (or any C# IDE) | لتجميع وتشغيل كود العينة. |
| .NET 6.0 SDK أو أحدث | يوفر بيئة التشغيل للمثال. |
| Aspose.Words for .NET (v24.10 أو أحدث) | المكتبة التي تتيح لك **create word document programmatically** والتعامل مع عناصر التحكم في النماذج. |
| إلمام أساسي بـ C# ومفاهيم OOP | مطلوب لفهم تدفق الكود. |

يمكنك تثبيت Aspose.Words عبر NuGet:

```bash
dotnet add package Aspose.Words
```

---

## إنشاء مستند Word برمجيًا

الخطوة الأولى هي إنشاء كائن `Document` فارغ. هذا الكائن يمثل ملف Word بالكامل في الذاكرة.

```csharp
// Step 1: Create a new blank document
Document doc = new Document();
```

إنشاء المستند برمجيًا يمنحك مساحة عمل نظيفة يمكنك إضافة فقرات أو جداول أو عناصر تحكم تفاعلية عليها.

---

## كيفية استخدام DocumentBuilder

`DocumentBuilder` هو الفئة الأساسية لتحرير `Document`. يوفر طرقًا لإدراج النصوص والصور وحقول النماذج. في هذا البرنامج التعليمي نستخدمه لوضع CommandButton.

```csharp
// Step 2: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

يحافظ الـ builder على مؤشر داخلي يشير إلى موقع الإدراج الحالي. بشكل افتراضي يبدأ في بداية القسم الأول، وهو مثالي لمثالنا.

---

## إدراج زر CommandButton في Word

تتعامل Aspose.Words مع CommandButton كعنصر تحكم ActiveX. طريقة `InsertForms2OleControl` تنشئ عنصر OLE عام ثم نقوم بتكوينه كزر.

```csharp
// Step 3: Insert an ActiveX Forms2OleControl (a CommandButton)
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

في هذه المرحلة يكون العنصر موجودًا في المستند لكنه لا يمتلك تمثيلًا بصريًا حتى نحدد نوعه.

---

## تعيين تسمية زر CommandButton

الآن نخبر عنصر OLE بأنه يجب أن يتصرف كـ CommandButton ونمنحه تسمية ودية.

```csharp
// Step 4: Define the control as a CommandButton
commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

// Step 5: Set a unique name for the button (used for identification)
commandButton.SetName("btnSubmit");

// Step 6: Set the visible caption that appears on the button
commandButton.SetCaption("Submit");
```

تعيين **command button caption** أمر أساسي لأن Word يعرض هذا النص على سطح الزر. إذا تجاهلت `SetCaption`، سيظهر الزر بتسمية عامة.

---

## حفظ مستند Word مع زر

أخيرًا، احفظ المستند على القرص. طريقة `Save` تكتب حزمة Word بالكامل، بما في ذلك الزر الذي تم إدراجه حديثًا، إلى ملف .docx.

```csharp
// Step 7: Save the document containing the CommandButton
doc.Save("YOUR_DIRECTORY/CommandButton.docx");
```

الملف `CommandButton.docx` الآن يحتوي على زر فعال بالكامل مسمى **Submit**. عندما يفتح المستخدم الملف في Microsoft Word وينقر على الزر، سيتم تشغيل الإجراء الافتراضي (الذي يمكنك ربطه لاحقًا عبر VBA).

---

## مثال كامل يعمل

فيما يلي البرنامج الكامل الذي يمكنك نسخه ولصقه وتشغيله. يوضح سير العمل الكامل من إنشاء المستند إلى حفظ الزر.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder (how to use DocumentBuilder)
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a CommandButton (insert command button word)
        Forms2OleControl commandButton = builder.InsertForms2OleControl();

        // 4. Define the control type as CommandButton
        commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

        // 5. Give the button a unique name (optional but useful)
        commandButton.SetName("btnSubmit");

        // 6. Set the visible caption (set command button caption)
        commandButton.SetCaption("Submit");

        // 7. Save the document (save word document button)
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**النتيجة المتوقعة**

* ملف باسم `CommandButton.docx` موجود في المسار الذي حددته.
* فتح الملف في Microsoft Word يظهر زر **Submit** واحد في الصفحة الأولى.
* يمكن تحديد الزر، تغيير حجمه، أو ربطه بماكرو من علامة تبويب **Developer** في Word.

---

## أسئلة شائعة ومعالجة الحالات الخاصة

| السؤال | الجواب |
|--------|--------|
| *ماذا لو احتجت إلى أكثر من زر؟* | كرر الخطوات 3–6 بأسماء وتسمية مختلفة. يجب أن يكون لكل زر قيمة `SetName` فريدة. |
| *هل يمكنني ضبط حجم الزر؟* | نعم. بعد إدراج العنصر، يمكنك تعديل خصائص `Width` و `Height` عبر كائن `OleFormat`. |
| *هل سيعمل الزر على جميع إصدارات Word؟* | عناصر التحكم ActiveX مدعومة في نسخة Word المكتبية (Windows). لا يتم عرضها في Word Online أو على macOS. |
| *كيف أضيف معالج نقر؟* | تحتاج إلى كتابة كود VBA يشير إلى اسم الزر (`btnSubmit`). يمكن تضمين ماكرو VBA باستخدام `doc.VbaProject`. |
| *ماذا لو احتجت إلى إدراج الزر داخل خلية جدول؟* | انقل مؤشر الـ builder إلى الخلية المطلوبة (`builder.MoveTo(cell.FirstParagraph)`) قبل استدعاء `InsertForms2OleControl`. |

---

## نصائح احترافية

* **نصيحة احترافية:** دائمًا عيّن اسمًا ذا معنى باستخدام `SetName`. يبسط ذلك أتمتة VBA ويسهل تصحيح الأخطاء.
* **احذر من:** نسيان استدعاء `SetControlType`. بدون هذا الاستدعاء يظهر كائن OLE كعنصر نائب عام بدلاً من زر قابل للنقر.
* **نصيحة أداء:** إذا كنت تنشئ العديد من المستندات في حلقة، أعد استخدام نسخة واحدة من `DocumentBuilder` واستدعِ `builder.MoveToDocumentEnd()` قبل كل إدراج لتجنب إعادة تعيين المؤشر غير الضرورية.

---

## الخطوات التالية

الآن بعد أن عرفت كيفية **create word document programmatically**، **insert command button word**، **set command button caption**، و **save word document button**، يمكنك استكشاف سيناريوهات أكثر تقدمًا:

* أضف عناصر تحكم **TextFormField** لإدخال المستخدم.
* دمج الأزرار مع حقول **MacroButton** لتنفيذ VBA مباشرة.
* استخدم **DocumentBuilder.InsertImage** لوضع أيقونات على أزرارك.
* دمج مع ASP.NET لإنشاء نماذج Word على

---

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مستند Word جديد](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [إنشاء مستند Word باستخدام Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [إدراج صورة مدمجة في مستند Word باستخدام Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}