---
category: general
date: 2026-09-08
description: تعلم كيفية إدراج عنصر تحكم المحتوى في مستند Word باستخدام C# و Aspose.Words.
  يتضمن خطوات إنشاء عنصر تحكم المحتوى، تعيين العنصر النائب، وحفظ الملف.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert content control
- create content control
language: ar
lastmod: 2026-09-08
og_description: إدراج عنصر تحكم المحتوى في ملف Word باستخدام C# و Aspose.Words. اتبع
  هذا الدليل لإنشاء عنصر تحكم المحتوى، وتعيين نص العنصر النائب، وحفظ المستند.
og_image_alt: Insert content control example in a Word document
og_title: إدراج عنصر تحكم المحتوى في Word باستخدام C# – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to insert content control in a Word document using C# and
    Aspose.Words. Includes steps to create content control, set placeholder, and save
    the file.
  headline: How to insert content control in a Word document with C#
  type: TechArticle
tags:
- content control
- Aspose.Words
- C#
- Word automation
title: كيفية إدراج عنصر تحكم المحتوى في مستند Word باستخدام C#
url: /ar/net/programming-with-sdt/how-to-insert-content-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إدراج عنصر تحكم المحتوى في مستند Word باستخدام C#

إذا كنت بحاجة إلى **إدراج عنصر تحكم المحتوى** في مستند Word، فإن هذا الدليل يوضح لك حلاً كاملاً قابلاً للتنفيذ. ستتعلم أيضًا كيفية **إنشاء عنصر تحكم المحتوى** برمجياً، وتعيين نص العنصر النائب، وكتابة الملف إلى القرص.

تتيح لك عناصر تحكم المحتوى تعريف مناطق يمكن للمستخدمين ملؤها أو تكرارها أو قفلها. تُستخدم على نطاق واسع في القوالب والنماذج والتقارير الديناميكية. الخطوات أدناه تستخدم مكتبة Aspose.Words لـ .NET، التي تعمل مع .NET 6+، .NET Framework 4.6+، و .NET Core.

## كيفية إدراج عنصر تحكم المحتوى في مستند Word

1. **إضافة Aspose.Words إلى مشروعك**  
   افتح طرفية في مجلد المشروع وشغّل:

   ```bash
   dotnet add package Aspose.Words
   ```

2. **إنشاء مستند فارغ جديد**  

   ```csharp
   // Step 1: Create a new empty document and a DocumentBuilder
   Document doc = new Document();
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```

## إنشاء عنصر تحكم المحتوى باستخدام Aspose.Words

تمثل عناصر تحكم المحتوى الفئة `StructuredDocumentTag` (SDT). يخلق الكود التالي عنصر تحكم محتوى **نص عادي** ويعطيه عنوانًا يمكنك الاستعلام عنه لاحقًا.

```csharp
// Step 2: Create a plain‑text StructuredDocumentTag (content control)
//         - Set a title that can be used to identify the control
//         - Provide placeholder text that appears when the control is empty
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,
    SdtType.PlainText,      // Plain‑text control
    MarkupLevel.Block);    // Block‑level control (behaves like a paragraph)

sdt.Title = "CustomerName";
sdt.PlaceholderName = "Enter name here";
```

*لماذا هذا مهم:*  
- `SdtType.PlainText` يضمن أن العنصر يتحكم يقبل أحرفًا عادية فقط.  
- `MarkupLevel.Block` يجعل العنصر يتحكم يتصرف كفقرة كاملة، وهو مثالي لحقول النماذج.  
- خاصية `Title` هي معرف ثابت يمكنك استخدامه عند البحث أو ربط البيانات.

## تعيين النص النائب والنص الافتراضي

النص النائب يوجه المستخدم قبل أن يكتب أي شيء. يمكنك أيضًا ملء العنصر مسبقًا بمحتوى افتراضي.

```csharp
// Step 4: Optionally set default content for the control
sdt.XmlMapping.SetXmlFragment("<text>John Doe</text>");
```

يجب أن يتطابق مقطع XML مع نوع بيانات العنصر. بالنسبة لعناصر تحكم النص العادي، العنصر `<text>` مطلوب. إذا تخطيت هذه الخطوة، سيظهر النص النائب المحدد مسبقًا بدلاً من ذلك.

## إدراج عنصر تحكم المحتوى في الموقع المطلوب

مؤشر `DocumentBuilder` يحدد أين يظهر العنصر. بشكل افتراضي، يكون المؤشر في بداية المستند.

```csharp
// Step 3: Insert the StructuredDocumentTag into the document at the builder's current position
builder.InsertNode(sdt);
```

إذا كنت بحاجة إلى العنصر داخل جدول أو رأس أو بعد فقرات موجودة، حرك الـ builder أولاً:

```csharp
builder.MoveToDocumentEnd();   // Example: place the control at the end of the file
builder.InsertNode(sdt);
```

## حفظ المستند مع عنصر تحكم المحتوى المدخل

```csharp
// Step 5: Save the document with the content control
doc.Save(@"C:\Temp\SDT.docx");
```

الملف `SDT.docx` الآن يحتوي على عنصر تحكم محتوى نص عادي بعنوان **CustomerName** مع النص النائب “Enter name here” والنص الافتراضي “John Doe”.

![مثال على إدراج عنصر تحكم المحتوى في مستند Word](insert-content-control.png)

*نص بديل للصورة:* مثال على إدراج عنصر تحكم المحتوى في مستند Word

### النتيجة المتوقعة

عند فتح `SDT.docx` في Microsoft Word:
- يظهر نص نائب رمادي “Enter name here” إذا حذفت النص الافتراضي.  
- يتم تمييز العنصر عندما تنقر داخله، مما يدل على أنه يمكن تحريره.  
- علامة التبويب **Developer** (إذا مفعلة) تُظهر عنوان العنصر **CustomerName** في لوحة الخصائص.

## مثال كامل يعمل

فيما يلي برنامج واحد مستقل يمكنك نسخه، تجميعه، وتشغيله. يوضح كل خطوة من إعداد المشروع إلى حفظ الملف.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class InsertContentControlDemo
{
    static void Main()
    {
        // 1. Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a plain‑text content control (StructuredDocumentTag)
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            doc,
            SdtType.PlainText,
            MarkupLevel.Block);

        sdt.Title = "CustomerName";          // Identifier for later use
        sdt.PlaceholderName = "Enter name here";

        // 3. Insert the control at the current cursor position
        builder.InsertNode(sdt);

        // 4. Set default text (optional)
        sdt.XmlMapping.SetXmlFragment("<text>John Doe</text>");

        // 5. Save the document
        string outputPath = @"C:\Temp\SDT.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

شغّل البرنامج باستخدام `dotnet run`. بعد التنفيذ، افتح الملف المُولد للتحقق من ظهور عنصر تحكم المحتوى كما هو موضح.

## نصائح عملية ومشكلات شائعة

| الحالة | النهج الموصى به |
|-----------|----------------------|
| **عناصر تحكم متعددة من نفس النوع** | امنح كل عنصر تحكم `Title` فريدًا. يمكنك لاحقًا استرجاع عنصر تحكم باستخدام `doc.GetChildNodes(NodeType.StructuredDocumentTag, true).Cast<StructuredDocumentTag>().FirstOrDefault(s => s.Title == "YourTitle")`. |
| **العنصر غير مرئي في Word** | تأكد من حفظ المستند بامتداد `.docx` وأن نسخة `Aspose.Words` متوافقة مع نسخة Office لديك. |
| **الحاجة إلى عنصر تحكم نص غني** | استخدم `SdtType.RichText` بدلاً من `PlainText`. ثم يستخدم مقطع XML عناصر `<w:richText>`. |
| **وضع العنصر داخل خلية جدول** | انقل الـ builder إلى الخلية أولاً: `builder.MoveTo(cell.FirstParagraph); builder.InsertNode(sdt);`. |
| **الأداء مع المستندات الكبيرة** | أنشئ `StructuredDocumentTag` مرة واحدة وأعد استخدامها إذا كنت تحتاج إلى العديد من عناصر التحكم المتطابقة؛ استنسخه عبر `sdt.Clone(true)`. |

## الخطوات التالية

- **إنشاء عناصر تحكم متكررة** (`SdtType.RepeatingSection`) للجداول التي تنمو ديناميكيًا.  
- **ربط عناصر التحكم ببيانات XML** باستخدام `sdt.XmlMapping.LoadXml(xmlString)`.  
- **قفل العنصر** (`sdt.LockContentControl = true`) لمنع تحرير المستخدم مع الاستمرار في السماح بالتحديثات البرمجية.  

استكشاف هذه المواضيع سيعزز قدرتك على بناء قوالب Word قوية باستخدام Aspose.Words.

---

**الخلاصة**  
أنت الآن تعرف كيفية **إدراج عنصر تحكم المحتوى** في مستند Word باستخدام C#. يغطي الدليل إنشاء العنصر، تعيين النص النائب والنص الافتراضي، إدراجه في الموقع المطلوب، وحفظ الملف النهائي. مع هذه الأساسيات يمكنك بناء نماذج متقدمة، قوالب دمج بريد، وتقارير آلية تستفيد من ميزات عنصر تحكم المحتوى الأصلية في Word.

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [ضبط نمط عنصر التحكم بالمحتوى](/words/english/net/programming-with-sdt/set-content-control-style/)
- [ضبط لون عنصر التحكم بالمحتوى](/words/english/net/programming-with-sdt/set-content-control-color/)
- [كيفية إنشاء حقول نموذج وإضافة محتوى باستخدام DocumentBuilder في Aspose.Words للـ Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}