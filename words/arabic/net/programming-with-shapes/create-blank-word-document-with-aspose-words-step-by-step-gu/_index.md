---
category: general
date: 2026-02-23
description: إنشاء مستند Word فارغ باستخدام C# و Aspose.Words. تعلم كيفية إضافة شكل
  مستطيل، إضافة ظل للكلمة، وحفظ المستند مع الشكل في دقائق.
draft: false
keywords:
- create blank word document
- add rectangle shape
- how to add shape
- add shadow word
- save word with shape
language: ar
og_description: إنشاء مستند Word فارغ بسرعة. يوضح هذا الدليل كيفية إضافة شكل مستطيل،
  إضافة ظل للكلمة، وحفظ المستند مع الشكل باستخدام Aspose.Words.
og_title: إنشاء مستند Word فارغ – دليل C# الكامل
tags:
- Aspose.Words
- C#
- Document Automation
title: إنشاء مستند Word فارغ باستخدام Aspose.Words – دليل خطوة بخطوة
url: /ar/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word فارغ – دليل C# الكامل

هل تساءلت يومًا كيف **create blank word document** برمجيًا دون فتح Microsoft Word؟ أنت لست وحدك. في العديد من مشاريع الأتمتة نحتاج إلى ملف .docx جديد، نضع شكلًا عليه، نضيف لهذا الشكل ظلًا جميلًا، ثم **save word with shape** للاستخدام لاحقًا.  

في هذا الدليل سنستعرض ذلك بالضبط—بدءًا من مستند فارغ، **adding a rectangle shape**، تكوين تأثير **add shadow word**، وأخيرًا حفظ الملف. في النهاية ستحصل على مقتطف كامل قابل للتنفيذ يمكنك لصقه في أي تطبيق .NET console. لا غموض، لا قطع مفقودة.

## ما ستحتاجه

- **Aspose.Words for .NET** (أي نسخة حديثة، مثلاً 24.10).  
- .NET 6 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.7+).  
- بيئة تطوير C# أساسية—Visual Studio، Rider، أو حتى VS Code مع إضافة C#.

هذا كل شيء. لا حزم NuGet إضافية بخلاف Aspose.Words، ولا حاجة لتثبيت Word.

---

## الخطوة 1: إنشاء مستند Word فارغ

أول شيء تقوم به عندما تريد **create blank word document** هو إنشاء كائن من الفئة `Document`. فكر فيه كقماش نظيف تقدمه لك Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1 – initialize an empty document
Document document = new Document();   // this is a brand‑new, blank Word file
```

> **لماذا هذا مهم:** كائن `Document` يحتوي على جميع الأقسام والفقرات والأشكال. البدء بنسخة فارغة يضمن لك التحكم في كل عنصر يُضاف لاحقًا.

---

## الخطوة 2: إضافة شكل مستطيل إلى المستند

الآن بعد أن لدينا مستندًا نظيفًا، دعنا **add rectangle shape**. المستطيل هو `Shape` بسيط مع `ShapeType.Rectangle`. بالطبع يمكنك اختيار أنواع أخرى، لكن المستطيل يعمل بشكل ممتاز للعرض.

```csharp
// Step 2 – create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width = 200,   // width in points (≈2.78 inches)
    Height = 100   // height in points (≈1.39 inches)
};
```

> **نصيحة محترف:** إذا تساءلت يومًا **how to add shape** التي ليست مستطيلًا، فقط غيّر `ShapeType.Rectangle` إلى أي قيمة أخرى من الـ enum مثل `ShapeType.Ellipse` أو `ShapeType.Polygon`. باقي الكود يبقى كما هو.

---

## الخطوة 3: تكوين ظل مخصص للشكل

المستطيل العادي يبدو مملًا قليلًا، لذا سنقوم بـ **add shadow word** لجعله يبرز. Aspose.Words يوفر كائن `ShadowFormat` يحتوي على العديد من الخصائص.

```csharp
// Step 3 – enable and style the shadow
rectangleShape.ShadowFormat.Enabled = true;                // turn on the shadow
rectangleShape.ShadowFormat.Color = Color.Gray;           // shadow color
rectangleShape.ShadowFormat.OffsetX = 5;                  // horizontal offset (points)
rectangleShape.ShadowFormat.OffsetY = 5;                  // vertical offset (points)
rectangleShape.ShadowFormat.Transparency = 0.3;           // 30 % transparent
rectangleShape.ShadowFormat.BlurRadius = 4;               // soft edge blur
```

> **لماذا هذا مهم:** الظل يضيف إشارة عمق خفيفة، خاصةً عندما يُعرض المستند على الشاشة. اضبط `OffsetX` و `OffsetY` و `BlurRadius` لتتناسب مع لغة التصميم الخاصة بك.

---

## الخطوة 4: إدراج الشكل في المستند

مع جاهزية الشكل، نحتاج إلى وضعه في مكان ما. أبسط مكان هو الفقرة الأولى من القسم الأول. إذا لم يحتوي المستند على فقرات بعد, يقوم Aspose بإنشاء واحدة تلقائيًا.

```csharp
// Step 4 – put the rectangle into the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **حالة حافة:** إذا كنت تخطط لإدراج الشكل في موقع محدد (مثلاً بعد عنوان معين)، حدد `Paragraph` المستهدف عبر `document.GetChildNodes(NodeType.Paragraph, true)` واستخدم `InsertAfter` أو `InsertBefore` وفقًا لذلك.

---

## الخطوة 5: حفظ مستند Word مع الشكل

أخيرًا، نقوم بـ **save word with shape** إلى القرص. طريقة `Save` تحدد التنسيق تلقائيًا من امتداد الملف.

```csharp
// Step 5 – persist the document
string outputPath = @"C:\Temp\shadowedRectangle.docx";
document.Save(outputPath);
```

> **ما ستراه:** افتح `shadowedRectangle.docx` في Word (أو أي عارض متوافق) وسترى مستطيلًا رماديًا بظل ناعم يقع في أعلى الصفحة الأولى.

---

## مثال كامل يعمل

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑ولصقه في تطبيق console. يتضمن جميع توجيهات `using`، التعليقات، والخطوات الدقيقة التي ناقشناها.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeWordShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank word document
            Document document = new Document();

            // 2️⃣ Add a rectangle shape
            Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100
            };

            // 3️⃣ Configure a custom shadow (add shadow word)
            rectangleShape.ShadowFormat.Enabled = true;
            rectangleShape.ShadowFormat.Color = Color.Gray;
            rectangleShape.ShadowFormat.OffsetX = 5;
            rectangleShape.ShadowFormat.OffsetY = 5;
            rectangleShape.ShadowFormat.Transparency = 0.3;
            rectangleShape.ShadowFormat.BlurRadius = 4;

            // 4️⃣ Insert the shape into the first paragraph
            document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

            // 5️⃣ Save the document (save word with shape)
            string outputFile = @"YOUR_DIRECTORY\shadow.docx";
            document.Save(outputFile);

            // Confirmation
            System.Console.WriteLine($"Document saved to {outputFile}");
        }
    }
}
```

شغّل البرنامج، انتقل إلى `YOUR_DIRECTORY`، وافتح الملف `shadow.docx` المُنشأ. يجب أن ترى المستطيل بظل رمادي خفيف—تمامًا ما كنا نسعى لتحقيقه.

---

## الأسئلة المتكررة والنصائح

### كيف أغيّر لون الشكل؟
```csharp
rectangleShape.FillColor = Color.LightBlue;
```
فقط قم بتعيين `FillColor` قبل إلحاق الشكل.

### ماذا لو احتجت إلى أشكال متعددة على نفس الصفحة؟
أنشئ كائنات `Shape` إضافية وألحق كل واحدة بالفقرة نفسها أو بفقرات مختلفة. يمكنك أيضًا التحكم في التخطيط باستخدام `WrapType` و `RelativeHorizontalPosition`.

### هل يمكنني تصدير إلى PDF مع الحفاظ على الظل؟
بالتأكيد. استخدم `document.Save("output.pdf")`—Aspose.Words يحافظ على تأثير الظل في تحويل PDF.

### هل يعمل هذا على .NET Core؟
نعم. Aspose.Words متعدد المنصات؛ نفس الكود يعمل على .NET Core، .NET 5+، و .NET Framework.

### كيف أضيف شكلًا بدون فقرة؟
يمكنك إضافة الشكل مباشرة إلى `Run` أو إلى `Story`. للحصول على تموضع أكثر دقة، اضبط `rectangleShape.RelativeHorizontalPosition = RelativeHorizontalPosition.Page` وعدّل خصائص `Left`/`Top`.

---

## النتيجة البصرية

![شكل مستطيل بظل رمادي في مستند Word – مثال add shadow word](https://example.com/placeholder-image.png "مثال add shadow word")

*يتضمن نص بديل الصورة الكلمة الثانوية **add shadow word** لتلبية متطلبات SEO.*

---

## الخلاصة

لقد عرضنا للتو كيفية **create blank word document**، **add rectangle shape**، تطبيق تأثير **add shadow word**، وأخيرًا **save word with shape** باستخدام Aspose.Words for .NET. العملية بسيطة: إنشاء كائن `Document`، بناء `Shape`، تعديل `ShadowFormat`، إدراجه، ثم استدعاء `Save`.  

من هنا يمكنك التجربة—جرب أنواع أشكال مختلفة، العب بالألوان، أو ضع عدة أشكال فوق بعضها. إذا احتجت لدمج هذا المستند مع محتوى موجود، فقط حمّل الملف الموجود عبر `new Document("existing.docx")` واتبع نفس الخطوات.  

هل لديك المزيد من الأسئلة؟ اترك تعليقًا، وبرمجة سعيدة!

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}