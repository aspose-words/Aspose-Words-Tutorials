---
category: general
date: 2026-09-21
description: إنشاء مستند Word فارغ يحتوي على إهليلج مخفي باستخدام C#. تعلم كيفية إخفاء
  الشكل في Word وإنشاء شكل مخفي برمجياً.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create ellipse
- hide shape in word
- create hidden shape
language: ar
lastmod: 2026-09-21
og_description: إنشاء مستند Word فارغ مع إهليلج مخفي باستخدام C#. يوضح هذا الدليل
  كيفية إخفاء الشكل في Word وبناء الأشكال المخفية برمجيًا.
og_image_alt: Screenshot of a blank Word document that contains a hidden ellipse shape
  created with C#
og_title: إنشاء مستند Word فارغ مع شكل إهليلجي مخفي في C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document with a hidden ellipse using C#. Learn how
    to hide shape in Word and generate a hidden shape programmatically.
  headline: How to create blank Word document and add a hidden ellipse shape in C#
  type: TechArticle
- questions:
  - answer: The shape’s XML adds a few hundred bytes, which is negligible for most
      use cases. The file remains essentially the same size as a truly empty document.
    question: Does hiding a shape affect document size?
  - answer: Yes. Load the document, locate the shape (`doc.GetChildNodes(NodeType.Shape,
      true)`), and set `shape.Hidden = false`.
    question: Can I unhide the shape later programmatically?
  - answer: No. Hidden objects are excluded from the print layout, so the printed
      page stays blank.
    question: Will the hidden shape appear when printing?
  - answer: 'The `Hidden` property is part of the OOXML spec, so any Word processor
      that fully implements OOXML (Word, LibreOffice, Google Docs) will respect the
      hidden flag. --- ## Conclusion You now know how to **create blank Word document**,
      **how to create ellipse**, **hide shape in Word**, and **create hidd'
    question: Is this approach compatible with Office Open XML (OOXML) only?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: كيفية إنشاء مستند Word فارغ وإضافة شكل إهليلجي مخفي في C#
url: /ar/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مستند Word فارغ وإضافة شكل بيضاوي مخفي في C#

إذا كنت بحاجة إلى **إنشاء مستند Word فارغ** يحتوي على رسم غير مرئي، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك. في نهاية البرنامج التعليمي ستحصل على ملف .docx يبدو فارغًا لكنه في الواقع يخزن شكلًا بيضاويًا مخفيًا عن التخطيط.

سنستخدم Aspose.Words for .NET لإنشاء المستند، وإدراج شكل بيضاوي، وإخفائه، وحفظ الملف. تغطي الخطوات أيضًا **كيفية إنشاء شكل بيضاوي**، والطريقة الصحيحة لـ **إخفاء الشكل في Word**، وكيفية **إنشاء شكل مخفي** يعمل مع أي مشروع .NET.

## المتطلبات المسبقة

* .NET 6.0 SDK أو أحدث مثبت  
* Visual Studio 2022 (أو أي محرر C#)  
* ترخيص Aspose.Words for .NET أو نسخة تقييم مجانية  
* إلمام أساسي بصياغة C#  

لا توجد حزم NuGet إضافية مطلوبة بخلاف `Aspose.Words`.

## إنشاء مستند Word فارغ باستخدام Aspose.Words

الخطوة الأولى هي إنشاء ملف Word فارغ. هذا يمنحنا مساحة عمل نظيفة حيث يمكننا لاحقًا إدراج رسومات مخفية.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();

        // The document is currently empty – it contains no paragraphs or shapes.
        // This is the foundation for all further operations.
```

**لماذا نبدأ بمستند فارغ** – البدء من ملف فارغ يضمن عدم تدخل أي محتوى غير مرغوب فيه مع الشكل المخفي. كما أنه يحافظ على حجم الملف بأقل قدر ممكن، وهو مفيد عندما يُستخدم المستند لاحقًا كقالب.

## كيفية إنشاء شكل بيضاوي داخل المستند الفارغ

بعد ذلك نحتاج إلى `DocumentBuilder` لإضافة المحتوى. يتيح لنا الـ builder وضع الأشكال بدقة في المكان الذي نريده.

```csharp
        // Step 2: Initialize a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert an ellipse shape (width: 100 points, height: 50 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

        // The ellipse now exists on the page, but it is visible by default.
```

**شرح** – `ShapeType.Ellipse` يخبر Aspose.Words برسم شكل شبه دائري. يتم قياس العرض والارتفاع بالنقاط (1 pt ≈ 1/72 inch). يمكنك تعديل هذه القيم لتناسب احتياجات التصميم الخاصة بك.

## إخفاء الشكل في Word بحيث لا يظهر في التخطيط

الشكل المخفي لا يزال موجودًا في XML الخاص بالمستند، مما يمكن أن يكون مفيدًا للبيانات الوصفية أو التنسيق الشرطي أو التعديلات البرمجية لاحقًا. لإخفائه، نضبط الخاصية `Hidden` إلى `true`.

```csharp
        // Step 4: Hide the shape so it does not appear in the layout
        ellipse.Hidden = true;

        // When Hidden = true, Word treats the shape as if it were not there.
        // The shape remains in the document’s DOM, allowing you to retrieve or modify it later.
```

**لماذا نُخفي الشكل** – يتم تجاهل الأشكال المخفية من قبل محرك التخطيط، لذا تبدو الصفحة فارغة تمامًا. ومع ذلك، تظل بيانات الشكل موجودة، مما يمكن أن يكون مفيدًا لتخزين العلامات أو الإشارات المرجعية أو XML مخصص يمكن للعمليات اللاحقة قراءته.

## حفظ المستند مع الشكل المخفي

أخيرًا نكتب الملف إلى القرص. سيفتح ملف `.docx` المحفوظ في Microsoft Word دون أي محتوى مرئي، ومع ذلك يظل الشكل البيضاوي المخفي موجودًا.

```csharp
        // Step 5: Save the document with the hidden shape
        doc.Save(@"C:\Temp\HiddenEllipse.docx");

        // The file now contains a hidden ellipse and appears empty when opened.
    }
}
```

**التحقق** – افتح الملف المُنشأ في Word، ثم اضغط `Alt+F9` لتبديل رموز الحقول و `Ctrl+A` → `Ctrl+Shift+F9` لعرض الكائنات المخفية. سترى الشكل البيضاوي في XML الخاص بالمستند (`word/document.xml`) ولكن لا شيء على الصفحة.

---

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑ولصقه في مشروع وحدة تحكم جديد. يتضمن جميع توجيهات `using` وطريقة `Main` حتى تتمكن من تشغيله دون أي إعدادات إضافية.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank Word document
            Document doc = new Document();

            // 2️⃣ Prepare a builder to insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse (100 pt × 50 pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the ellipse so the page stays empty
            ellipse.Hidden = true;

            // 5️⃣ Save the file
            string outPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outPath);

            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**الناتج المتوقع** – عند تشغيل البرنامج، يطبع الطرفية مسار الملف، ويحتوي ملف Word الناتج على لا كائنات مرئية. إذا فحصت المستند بأداة ضغط (`.docx` هو أرشيف zip)، ستجد عنصر `<w:pict>` الذي يصف الشكل البيضاوي داخل `word/document.xml`.

---

## الاختلافات الشائعة والحالات الخاصة

| السيناريو | ما الذي يجب تغييره | لماذا يهم |
|----------|----------------|----------------|
| **شكل مختلف** | استبدل `ShapeType.Ellipse` بـ `ShapeType.Rectangle` أو `ShapeType.Line`، إلخ. | يسمح لك بإخفاء رسومات أخرى مع الحفاظ على نفس سير العمل. |
| **أشكال مخفية متعددة** | استدعِ `InsertShape` عدة مرات واضبط `Hidden = true` لكل منها. | مفيد لتضمين مجموعة من العلامات أو العناصر النائبة. |
| **رؤية شرطية** | استخدم `shape.Visible = false` مع `shape.Hidden = true` لمزيد من الأمان. | بعض إصدارات Word القديمة تتعامل مع `Visible` بشكل مختلف؛ ضبط كلاهما يغطي جميع الحالات. |
| **الحفظ إلى تدفق** | استبدل `doc.Save(path)` بـ `doc.Save(stream, SaveFormat.Docx)`. | يمكنك من إرسال المستند مباشرة عبر HTTP أو تخزينه في قاعدة بيانات. |
| **تطبيق نمط** | بعد الإدراج، عدل `ellipse.FillColor` و `ellipse.LineWeight` وغيرها قبل الإخفاء. | يتم الاحتفاظ بتنسيق الشكل في XML، مما قد يكون مفيدًا لإظهاره لاحقًا. |

**نصيحة احترافية:** اختبر دائمًا الشكل المخفي على نسخة Word المستهدفة (مثل Word 2019، Word 365) لأن بعض المشكلات في العرض قد تظهر عندما تتفاعل الكائنات المخفية مع تخطيطات صفحات معقدة.

---

## الأسئلة المتكررة

**س: هل يؤثر إخفاء الشكل على حجم المستند؟**  
ج: يضيف XML الخاص بالشكل بضع مئات من البايتات، وهو أمر ضئيل بالنسبة لمعظم الاستخدامات. يظل الملف بحجم مماثل تقريبًا لمستند فارغ فعليًا.

**س: هل يمكنني إظهار الشكل لاحقًا برمجيًا؟**  
ج: نعم. قم بتحميل المستند، وابحث عن الشكل (`doc.GetChildNodes(NodeType.Shape, true)`)، واضبط `shape.Hidden = false`.

**س: هل سيظهر الشكل المخفي عند الطباعة؟**  
ج: لا. يتم استبعاد الكائنات المخفية من تخطيط الطباعة، لذا تظل الصفحة المطبوعة فارغة.

**س: هل هذا النهج متوافق مع Office Open XML (OOXML) فقط؟**  
ج: الخاصية `Hidden` هي جزء من مواصفات OOXML، لذا أي معالج Word يطبق OOXML بالكامل (Word، LibreOffice، Google Docs) سيحترم علامة الإخفاء.

---

## الخلاصة

أنت الآن تعرف كيف **تنشئ مستند Word فارغ**، **تنشئ شكل بيضاوي**، **تخفي الشكل في Word**، و**تنشئ شكلًا مخفيًا** باستخدام Aspose.Words for .NET. غطى البرنامج التعليمي دورة الحياة الكاملة — من تهيئة ملف فارغ إلى إدراج الشكل، إخفائه، وحفظه — بالإضافة إلى خطوات التحقق والاختلافات الشائعة.

* إضافة صناديق نصية مخفية للبيانات الوصفية (تقنية `hide shape in word` المطبقة على النص)  
* استخدام أجزاء XML مخصصة لتخزين بيانات منظمة إلى جانب الأشكال المخفية  
* تحويل مستند الشكل المخفي إلى PDF مع الحفاظ على العناصر المخفية  

جرّب أشكالًا وإعدادات رؤية مختلفة لترى كيف يمكن للمحتوى المخفي أن يعمل كمخزن بيانات خفيف داخل ملفات Word.

برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء شكل مستطيل في Word باستخدام C# – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [إنشاء مجموعة أشكال في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [إنشاء مستند Word مع مستطيل مظلل – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}