---
category: general
date: 2026-01-08
description: إنشاء مستند Word فارغ وتعلم كيفية إضافة ظل إلى شكل مستطيل. إدراج ملفات
  Word الخاصة بالأشكال وإضافة ظل الشكل باستخدام C# و Aspose.Words.
draft: false
keywords:
- create blank word
- how to add shadow
- rectangle shape word
- insert shape word
- add shape shadow
language: ar
og_description: أنشئ مستند Word فارغ وتعرّف على كيفية إضافة ظل إلى شكل مستطيل باستخدام
  C#. كود كامل، شروحات، ونصائح.
og_title: إنشاء مستند Word فارغ – إضافة شكل مستطيل بظل
tags:
- Aspose.Words
- C#
- Document Automation
title: إنشاء مستند Word فارغ مع شكل مستطيل مظلَّل – دليل خطوة بخطوة
url: /ar/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word فارغ مع شكل مستطيل بظل – دليل كامل

هل احتجت يوماً إلى **إنشاء مستند Word فارغ** برمجياً ثم تزيينه بمستطيل ذو ظل جميل؟ لست وحدك. يواجه العديد من المطورين صعوبة عندما يكتشفون أن إدراج الأشكال وتطبيق التأثيرات ليس بالأمر السهل مثل كتابة النص.  

في هذا الدليل سنستعرض العملية بالكامل — من إنشاء ملف `.docx` فارغ إلى **كيفية إضافة ظل** إلى كائن **rectangle shape word**، وأخيراً **إدراج محتوى shape word** مع تأثير **add shape shadow** مصقول. في النهاية ستحصل على مقطع جاهز للاستخدام يعمل مع أحدث Aspose.Words لـ .NET.

---

## ما ستحتاجه

- **Aspose.Words for .NET** (v24.10 أو أحدث) – المكتبة التي تشغل كل ما يلي.  
- بيئة تطوير .NET (Visual Studio، Rider، أو `dotnet` CLI).  
- معرفة أساسية بـ C# – إذا كنت تستطيع كتابة “Hello World”، فأنت جاهز.

لا توجد حزم NuGet إضافية مطلوبة؛ كل شيء موجود داخل `Aspose.Words` و `System.Drawing`.

---

## الخطوة 1: إنشاء مستند Word فارغ

أول شيء يجب القيام به هو إنشاء كائن `Document` فارغ. فكر فيه كقماش جديد — تماماً كما لو أنك تفتح ملف Word جديد يدوياً.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a brand‑new blank Word document
Document document = new Document();   // This creates an empty .docx in memory
```

*لماذا هذا مهم:*  
كائن `Document` يمثل ملف Word بالكامل. البدء بملف فارغ يمنحك السيطرة الكاملة على كل عنصر ستضيفه لاحقاً، من الفقرات إلى الأشكال.

---

## الخطوة 2: تعريف شكل مستطيل (Rectangle Shape Word)

الآن نحتاج إلى شكل للعمل معه. المستطيل هو أبسط شكل هندسي ويعمل جيداً للبانرات، العناصر النائبة، أو نماذج واجهة المستخدم البسيطة.

```csharp
// Step 2: Create a rectangle shape with specific dimensions
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};
```

*لماذا هذا مهم:*  
تحديد `Width` و `Height` يتيح لك التحكم في البصمة البصرية للشكل. `ShapeType.Rectangle` يخبر Aspose برسم صندوق كلاسيكي — مثالي لتوضيح **add shape shadow** لاحقاً.

---

## الخطوة 3: تطبيق ظل على الشكل (How to Add Shadow)

الظلال تضيف عمقاً، تجعل المستطيل المسطح يبدو ككائن مادي. Aspose.Words يتيح خاصية `Shadow` حيث يمكنك تعديل اللون، المسافة، الضبابية، والشفافية.

```csharp
// Step 3: Enable and configure the shadow effect
rectangleShape.Shadow.Enabled      = true;               // Turn the shadow on
rectangleShape.Shadow.Color        = Color.Gray;         // Shadow color
rectangleShape.Shadow.Distance    = 5.0;                // How far the shadow is offset
rectangleShape.Shadow.BlurRadius  = 3.0;                // Softness of the edge
rectangleShape.Shadow.Transparency = 0.2;               // 0 = opaque, 1 = fully transparent
```

*لماذا هذا مهم:*  
كل خاصية تؤثر على الإشارة البصرية:

- **Enabled** – بدون هذا يتم تجاهل الإعدادات الأخرى.  
- **Color** – اختر لوناً يتناسب مع سمة المستند.  
- **Distance** – القيم الأكبر تدفع الظل بعيداً أكثر.  
- **BlurRadius** – الأرقام الأعلى تجعل الظل أكثر نعومة.  
- **Transparency** – ضبط الشفافية للحصول على لمسة خفيفة.

لا تتردد في التجربة؛ للحصول على تأثير دراماتيكي، ارتقِ بـ `Distance` إلى `10` واضبط `Transparency` إلى `0.5`.

---

## الخطوة 4: إدراج الشكل في المستند (Insert Shape Word)

مع جاهزية المستطيل، نحتاج إلى مكان لوضعه. أبسط موقع هو الفقرة الأولى في جسم المستند.

```csharp
// Step 4: Append the shape to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

*لماذا هذا مهم:*  
`FirstSection.Body.FirstParagraph` موجود دائماً في `Document` جديد. بإضافة الشكل هنا، تضمن ظهور الشكل في أعلى الملف — مفيد للرؤوس أو بانرات العنوان.

إذا كنت بحاجة لإدراج الشكل في مكان آخر، يمكنك تحديد `Paragraph` أو `Run` معين واستخدام `InsertAfter` أو `InsertBefore`.

---

## الخطوة 5: حفظ ملف Word

الخطوة الأخيرة هي حفظ المستند الموجود في الذاكرة إلى القرص. اختر مجلدًا لديك صلاحية كتابة فيه، ومنح الملف اسمًا معبرًا.

```csharp
// Step 5: Save the document with the shadowed rectangle
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
document.Save(outputPath);
```

*لماذا هذا مهم:*  
استدعاء `Save` يكتب ملف `.docx` متوافق بالكامل. افتحه في Microsoft Word أو LibreOffice أو أي عارض، وسترى مستطيلًا بظل رمادي ناعم — تماماً ما قمنا بإعداده.

---

## مثال كامل يعمل

فيما يلي البرنامج الكامل الذي يمكنك نسخه ولصقه في تطبيق Console. يتضمن جميع توجيهات `using`، إنشاء الشكل، إعداد الظل، الإدراج، والحفظ.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Define a rectangle shape (rectangle shape word)
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
        {
            Width  = 200,
            Height = 100
        };

        // 3️⃣ How to add shadow – configure the shadow effect
        rectangleShape.Shadow.Enabled      = true;
        rectangleShape.Shadow.Color        = Color.Gray;
        rectangleShape.Shadow.Distance    = 5.0;
        rectangleShape.Shadow.BlurRadius  = 3.0;
        rectangleShape.Shadow.Transparency = 0.2;

        // 4️⃣ Insert shape word into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 5️⃣ Save the file (add shape shadow persisted)
        string outputPath = @"C:\Temp\ShadowedRectangle.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**الناتج المتوقع:**  
افتح `ShadowedRectangle.docx` وسترى مستطيلًا رماديًا فاتحًا في أعلى الصفحة مركّزًا مع ظل خفيف مُزاح بمقدار 5 نقطة. لا نص إضافي، فقط الشكل — تماماً ما ينتجه الكود.

---

## أسئلة شائعة وحالات خاصة

### ماذا لو احتجت إلى شكل مختلف؟

استبدل `ShapeType.Rectangle` بأي قيمة أخرى من تعداد `ShapeType` (`Ellipse`، `Triangle`، `Star`، إلخ). خصائص الظل تعمل بنفس الطريقة.

### هل يمكن إضافة ظلال متعددة؟

Aspose.Words يدعم ظلًا واحدًا فقط لكل شكل. إذا كنت بحاجة إلى تأثيرات متعددة الطبقات، أنشئ شكلين متداخلين بإعدادات ظل مختلفة.

### كيف يعمل هذا على .NET Core؟

نفس الـ API يعمل على .NET 6/7/8. فقط تأكد من الإشارة إلى حزمة **Aspose.Words.NETCore** (أو الحزمة القياسية، التي أصبحت الآن متعددة المنصات).

### هل ما زالت `System.Drawing` مدعومة على Linux؟

`System.Drawing.Common` أصبحت مخصصة لنظام Windows فقط بدءًا من .NET 6. للمشاريع متعددة المنصات، استخدم `Aspose.Drawing` (حزمة NuGet منفصلة) أو التزم بالألوان المعرفة بواسطة `Aspose.Words` نفسها.

### ماذا عن مقياس DPI؟

أبعاد الشكل بوحدات النقاط (1 pt = 1/72 inch). إذا كنت تحتاج إلى حجم بدقة البكسل لدقة DPI معينة، احسب النقاط كـ `pixels * 72 / dpi`.

---

## نصائح احترافية وملاحظات

- **نصيحة احترافية:** اضبط `rectangleShape.WrapType = WrapType.Inline;` إذا أردت أن يتدفق الشكل مع النص بدلاً من أن يطفو فوقه.  
- **احذر من:** نسيان تمكين الظل (`Enabled = true`). الإعدادات الأخرى ستُهمل صامتًا.  
- **ملاحظة أداء:** إضافة العديد من الأشكال داخل حلقة ضيقة قد تكون بطيئة. اجمعها في `Section` واحدة واستدعِ `document.UpdatePageLayout()` مرة واحدة في النهاية.  
- **تحقق من الإصدار:** تم تقديم واجهة برمجة الظل في Aspose.Words 20.2. إذا كنت تستخدم إصدارًا أقدم، قم بالترقية لتجنب فقدان الخصائص.

---

## الخلاصة

لقد **أنشأنا مستند Word فارغ**، بنينا **rectangle shape word**، تعلمنا **كيفية إضافة الظل**، وأخيرًا **أدخلنا محتوى shape word** مع تأثير **add shape shadow** مصقول — كل ذلك باستخدام Aspose.Words لـ .NET.  

المقطع قابل للتنفيذ بالكامل، يعمل على Windows و .NET متعدد المنصات، ويمكن توسيعه لأشكال أخرى، ألوان، أو حتى صور GIF متحركة. لاحقًا، قد تستكشف إضافة نص داخل المستطيل، تطبيق تعبئات متدرجة، أو إنشاء تقرير كامل مع عدة أشكال منسقة.  

هل لديك أفكار أخرى؟ جرّب استبدال الظل الرمادي بظل أزرق، زد الضبابية للحصول على مظهر حالمي، أو اجمع عدة أشكال في شعار مخصص. السماء هي الحد، والآن لديك اللبنات الأساسية للقيام بذلك.  

برمجة سعيدة، ولتكون مستنداتك دائمًا حادة (مع الكمية المناسبة من الظل)!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}