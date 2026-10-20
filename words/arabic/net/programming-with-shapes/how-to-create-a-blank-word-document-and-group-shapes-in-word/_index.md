---
category: general
date: 2026-10-20
description: تعلم كيفية إنشاء مستند Word فارغ، تجميع الأشكال في Word، تعيين لون تعبئة
  الشكل، واستخدام نوع الالتفاف داخل السطر مع مثال كامل بلغة C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- how to group shapes
- set shape fill color
- wrap type inline
language: ar
lastmod: 2026-10-20
og_description: إنشاء مستند Word فارغ، تجميع الأشكال في Word، وتعيين لون تعبئة الشكل
  مع نوع الالتفاف داخل السطر باستخدام Aspose.Words و C#. اتبع الدليل الكامل.
og_image_alt: Screenshot of a blank Word document containing a grouped rectangle and
  text box created with Aspose.Words
og_title: إنشاء مستند Word فارغ وتجميع الأشكال في Word – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  headline: How to create a blank Word document and group shapes in Word using Aspose.Words
  type: TechArticle
- description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  name: How to create a blank Word document and group shapes in Word using Aspose.Words
  steps:
  - name: Expected result
    text: '* A .docx file containing a single paragraph. * Inside the paragraph, an
      inline group that looks like a single composite object. * The rectangle is filled
      with light blue, and the text box displays “Grouped text”.'
  - name: What if I need the group to float rather than be inline?
    text: Replace `WrapType.Inline` with `WrapType.TopBottom` (or any other `WrapType`
      enum value). Floating groups can be positioned independently of paragraph flow,
      but they lose the automatic inline alignment.
  - name: Can I add more shapes, such as circles or images?
    text: Yes. Create additional `Shape` objects with `ShapeType.Ellipse` or `ShapeType.Image`,
      configure their properties, and call `group.AppendChild(newShape)`. The group
      will automatically expand to accommodate the new bounds if you update `group.Bounds`
      accordingly.
  - name: How do I change the group’s overall size after adding children?
    text: Adjust `group.Bounds` after all children are appended, or compute the union
      of child bounds programmatically. This ensures the group’s hit‑test area matches
      the visual content.
  - name: What if the output folder does not exist?
    text: 'Aspose.Words throws a `DirectoryNotFoundException`. Create the directory
      first:'
  - name: Does this work with .NET Framework instead of .NET Core?
    text: All APIs used (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) are
      available in the .NET Framework version of Aspose.Words, so the same code works
      unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: كيفية إنشاء مستند Word فارغ وتجميع الأشكال في Word باستخدام Aspose.Words
url: /ar/net/programming-with-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مستند Word فارغ وتجميع الأشكال في Word

إذا كنت بحاجة إلى **إنشاء مستند Word فارغ** يحتوي على عدة أشكال تعمل كوحدة واحدة، فإن هذا الدليل يوضح لك بالضبط كيفية القيام بذلك. ستتعرف على كيفية **تجميع الأشكال في Word**، وتعيين لون تعبئة الشكل، وتطبيق **wrap type inline** — كل ذلك باستخدام برنامج C# مختصر وقابل للتنفيذ.

يأخذك البرنامج التعليمي عبر كل سطر من الشيفرة، يشرح لماذا كل خطوة مهمة، ويسلط الضوء على الأخطاء الشائعة. في النهاية ستحصل على ملف .docx يعرض مستطيلًا ومربع نص مُجَمَّعين معًا، جاهزين لمزيد من الأتمتة.

## ما ستتعلمه

* كيفية تهيئة ملف Word فارغ باستخدام Aspose.Words.
* الطريقة الصحيحة لإنشاء **GroupShape** وإضافة الأشكال الفرعية.
* تقنيات **set shape fill color** والتحكم في الموضع.
* استخدام **wrap type inline** لجعل المجموعة تتصرف ككائن نصي واحد.
* كيفية حفظ الملف والتحقق من النتيجة.

لا يلزم أي خبرة سابقة في Aspose.Words، لكن يجب أن تكون مرتاحًا مع أساسيات لغة C# وأن يكون لديك Visual Studio (أو أي بيئة تطوير أخرى) مثبتة.

## المتطلبات المسبقة

| المتطلب | السبب |
|-------------|--------|
| .NET 6.0 أو أحدث | يوفر بيئة تشغيل لمشروع C#. |
| Aspose.Words for .NET (أحدث نسخة) | يوفّر الفئات `Document`، `DocumentBuilder`، وفئات الشكل المستخدمة في المثال. |
| مسار مجلد قابل للكتابة | تحتاج دالة `doc.Save` إلى دليل صالح لكتابة ملف الإخراج. |
| معرفة أساسية بلغة C# | تمكّنك من متابعة الشيفرة وتعديلها وفقًا لسيناريوهاتك. |

تثبيت Aspose.Words عبر NuGet:

```bash
dotnet add package Aspose.Words
```

---

## الخطوة 1: إنشاء مستند Word فارغ

العملية الأولى هي **إنشاء مستند Word فارغ**. تمثل فئة `Document` في Aspose.Words ملف Word في الذاكرة، وتوفر فئة `DocumentBuilder` واجهة برمجة تطبيقات مريحة لتحريره.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new empty document.
Document doc = new Document();

// Attach a builder to the document for easy content insertion.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*لماذا هذا مهم*: البدء بمستند نظيف يضمن أن الشكل الجماعي الذي ستضيفه سيكون المحتوى الوحيد، مما يجعل عملية التحقق بسيطة.

## الخطوة 2: تعريف مجموعة أشكال مع wrap type inline

تعمل **GroupShape** كحاوية للأشكال الأخرى. ضبط خاصية `WrapType` إلى `Inline` يضمن أن المجموعة تتصرف ككائن نصي واحد داخل تدفق الفقرة.

```csharp
// Create a group shape that will hold the rectangle and text box.
GroupShape group = new GroupShape(doc, WrapType.Inline);

// Define the bounding rectangle of the group (x, y, width, height).
group.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
```

*لماذا هذا مهم*: استخدام **wrap type inline** يمنع المجموعة من الانفصال عن النص المحيط، وهو أمر أساسي عندما تريد أن تتحرك المجموعة كوحدة واحدة.

## الخطوة 3: إضافة مستطيل وتعيين لون تعبئة الشكل

المستطيل عنصر بصري شائع. يأخذ مُنشئ `Shape` معاملًا من نوع `ShapeType`؛ ثم نحدد الأبعاد ولون التعبئة.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 150,
    Height = 100,
    FillColor = System.Drawing.Color.LightBlue
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

*لماذا هذا مهم*: تُظهر خاصية `FillColor` **set shape fill color** عمليًا، مما يمنح المستطيل خلفية زرقاء فاتحة تبرز في المستند النهائي.

## الخطوة 4: إضافة مربع نص – كيفية تجميع الأشكال بفعالية

مربع النص يوفر نصًا قابلًا للتحرير داخل المجموعة. ضع موقعه بالنسبة لنظام إحداثيات المجموعة عن طريق تعديل خاصية `Top`.

```csharp
// Create a text box shape.
Shape textBox = new Shape(doc, ShapeType.TextBox)
{
    Width = 120,
    Height = 60,
    TextBoxText = "Grouped text",
    Top = 110 // Position below the rectangle inside the group.
};

// Append the text box to the group.
group.AppendChild(textBox);
```

*لماذا هذا مهم*: تُجيب هذه الخطوة على سؤال **how to group shapes** — عبر إلحاق كل شكل فرعي بنفس كائن `GroupShape`. يضمن إزاحة `Top` ظهور مربع النص أسفل المستطيل، مما يُظهر التحكم الدقيق في التخطيط.

## الخطوة 5: إدراج مجموعة الأشكال المكتملة في المستند

الآن بعد أن احتوت المجموعة كلا الشكلين الفرعيين، قم بإدراجها في موضع الـ builder الحالي.

```csharp
// Insert the group shape at the builder’s cursor location.
builder.InsertNode(group);
```

*لماذا هذا مهم*: إدراج المجموعة كعقدة واحدة يضمن أن Word يتعامل مع المستطيل ومربع النص ككائن منطقي واحد، ويحافظ على مواضعهما النسبية أثناء التحرير.

## الخطوة 6: حفظ المستند والتحقق من النتيجة

أخيرًا، اكتب المستند إلى القرص. استبدل `YOUR_DIRECTORY` بمسار حقيقي على جهازك.

```csharp
// Save the document to the specified folder.
doc.Save("YOUR_DIRECTORY/GroupShape.docx");
```

عند فتح `GroupShape.docx` في Microsoft Word، يجب أن ترى مستطيلًا أزرق فاتحًا مع مربع نص يحمل النص “Grouped text” موضعًا مباشرةً تحته. اختيار أي من الشكلين سيختار المجموعة بالكامل، مما يؤكد أن **group shapes in Word** يعمل كما هو متوقع.

### النتيجة المتوقعة

* ملف .docx يحتوي على فقرة واحدة.
* داخل الفقرة، مجموعة inline تبدو ككائن مركب واحد.
* المستطيل مملوء باللون الأزرق الفاتح، ومربع النص يعرض “Grouped text”.

![Screenshot of the generated Word document](grouped_shapes.png){.center width=600 alt="لقطة شاشة لمستند Word فارغ مع مستطيل ومربع نص مُجَمَّعين باستخدام Aspose.Words"}

## الأسئلة الشائعة ومعالجة الحالات الخاصة

### ماذا لو أردت أن تكون المجموعة عائمة بدلاً من أن تكون inline؟

استبدل `WrapType.Inline` بـ `WrapType.TopBottom` (أو أي قيمة أخرى من تعداد `WrapType`). المجموعات العائمة يمكن وضعها بشكل مستقل عن تدفق الفقرة، لكنها تفقد محاذاة الـ inline التلقائية.

### هل يمكنني إضافة أشكال أخرى، مثل دوائر أو صور؟

نعم. أنشئ كائنات `Shape` إضافية باستخدام `ShapeType.Ellipse` أو `ShapeType.Image`، اضبط خصائصها، ثم استدعِ `group.AppendChild(newShape)`. ستتوسع المجموعة تلقائيًا لتستوعب الحدود الجديدة إذا قمت بتحديث `group.Bounds` وفقًا لذلك.

### كيف أغيّر حجم المجموعة الكلي بعد إضافة الأطفال؟

عدّل `group.Bounds` بعد إلحاق جميع الأطفال، أو احسب اتحاد حدود الأطفال برمجيًا. يضمن ذلك أن مساحة الضرب (hit‑test) للمجموعة تتطابق مع المحتوى المرئي.

### ماذا لو لم يكن مجلد الإخراج موجودًا؟

ترمي Aspose.Words استثناء `DirectoryNotFoundException`. أنشئ المجلد أولًا:

```csharp
string outputPath = "YOUR_DIRECTORY";
Directory.CreateDirectory(outputPath);
doc.Save(Path.Combine(outputPath, "GroupShape.docx"));
```

### هل يعمل هذا مع .NET Framework بدلًا من .NET Core؟

جميع واجهات برمجة التطبيقات المستخدمة (`Document`، `DocumentBuilder`، `GroupShape`، `Shape`) متوفرة في نسخة .NET Framework من Aspose.Words، لذا يعمل نفس الكود دون تعديل.

## نصائح احترافية

* **نصيحة الأداء** – أعد استخدام كائن `DocumentBuilder` واحد عند إدراج العديد من المجموعات؛ إنشاء builder جديد لكل مجموعة يضيف عبئًا غير ضروري.
* **التناسق البصري** – اضبط `rectangle.StrokeColor` ليتطابق مع `FillColor` للحصول على مظهر سلس، أو عيّن `rectangle.LineWidth = 0` لإخفاء الحدود.
* **التصحيح** – استدعِ `doc.UpdatePageLayout()` قبل الحفظ إذا عدلت العديد من الأشكال؛ هذا يجبر Word على إعادة حساب التخطيط وقد يمنع القص غير المتوقع.

## الخلاصة

أنت الآن تعرف كيف **تنشئ مستند Word فارغ**، **تجميع الأشكال في Word**، **تعيين لون تعبئة الشكل**، وتطبيق **wrap type inline** باستخدام Aspose.Words for .NET. يوضح المثال الكامل النهج القياسي لبناء رسومات مركبة تتصرف ككائن واحد في Word.

من هنا يمكنك استكشاف:

* إضافة أشكال إضافية مثل الصور أو المخططات.
* تجربة قيم `WrapType` مختلفة للمجموعات العائمة.
* أتمتة إنشاء دفعات من المخططات المجمعة عبر مستندات متعددة.

لا تتردد في تعديل الشيفرة لتناسب سيناريوهات الأتمتة الخاصة بك، وشارك نتائجك في التعليقات!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [How to Save PDF from Word with Inline Shapes – Complete Guide](/words/english/java/document-conversion-and-export/how-to-save-pdf-from-word-with-inline-shapes-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}