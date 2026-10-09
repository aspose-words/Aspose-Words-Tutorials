---
category: general
date: 2026-03-19
description: إنشاء مستند Word باستخدام C# و Aspose.Words، وتعلم كيفية إضافة شكل، إضافة
  شكل مستطيل، تطبيق الظل، وحفظ المستند بصيغة docx في دقائق.
draft: false
keywords:
- create word document
- how to add shape
- add rectangle shape
- save document as docx
- add shadow to shape
language: ar
og_description: إنشاء مستند Word باستخدام Aspose.Words، إضافة شكل مستطيل، تطبيق ظل
  خارجي، وحفظ المستند بصيغة docx. دليل خطوة بخطوة.
og_title: إنشاء مستند Word – إضافة شكل مستطيل وظل
tags:
- Aspose.Words
- C#
- Document Automation
title: إنشاء مستند Word – كيفية إضافة شكل مستطيل وظل
url: /ar/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word – كيفية إضافة شكل مستطيل وظل

هل احتجت يوماً إلى **إنشاء مستند word** برمجياً وتساءلت من أين تبدأ؟ لست وحدك. يواجه العديد من المطورين نفس المشكلة عندما يحاولون أول مرة إنشاء ملف .docx يحتوي على رسومات مخصصة. في هذا الدرس سنستعرض العملية بالكامل — كيفية إضافة شكل، وبشكل محدد **إضافة شكل مستطيل**، ومنحه **إضافة ظل إلى الشكل** بأناقة، وأخيراً **حفظ المستند كـ docx**.  

بنهاية الدليل ستحصل على مقتطف C# جاهز للاستخدام يمكنك إدراجه في أي مشروع .NET. لا مراجع غامضة، فقط مثال كامل قابل للتنفيذ.  

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضاً مع .NET Framework).  
- Aspose.Words for .NET مثبت (حزمة NuGet `Aspose.Words`).  
- فهم أساسي لصياغة C# — لا حاجة لأي شيء معقد.  

إذا كنت تفتقد المكتبة، نفّذ:

```bash
dotnet add package Aspose.Words
```

هذا كل شيء — لا حاجة لأي SDK إضافي، ولا COM interop، مجرد مرجع NuGet واحد.

---

## الخطوة 1: إنشاء مستند Word (الهدف الأساسي)

الشيء الأول الذي نحتاجه هو لوحة قماشية نظيفة. فكر في فئة `Document` كصفحة جديدة في Microsoft Word؛ فهي تحتوي على الأقسام والفقرات وكل ما ستضيفه لاحقاً.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Step 1: Initialize a new blank document
Document doc = new Document();               // This creates an empty .docx in memory
```

لماذا نبدأ بـ `Document` فارغ؟ لأنه يضمن عدم تسلل تنسيقات مخفية من قالب. في تجربتي، البدء من الصفر يجنبك تغييرات تخطيط غامضة عندما تقوم بإدراج الأشكال لاحقاً.

---

## الخطوة 2: إدراج شكل مستطيل – إضافة العنصر البصري

الآن بعد أن لدينا مستنداً، دعنا **نضيف شكل مستطيل** إلى الفقرة الأولى. كائن `Shape` متعدد الاستخدامات؛ يمكنك اختيار `ShapeType.Rectangle` أو `Ellipse` أو حتى رسومات مخصصة. إليك الحد الأدنى من الشيفرة:

```csharp
// Step 2: Create a rectangle and attach it to the first paragraph
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.78 inches)
    Height = 100,              // Height in points (≈1.39 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};

// Append the shape to the first paragraph (creates one if missing)
Paragraph firstPara = doc.FirstSection.Body.FirstParagraph;
firstPara.AppendChild(rect);
```

**ما الذي يحدث خلف الكواليس؟**  
- `ShapeType.Rectangle` يُخبر Aspose أننا نريد صندوقاً بسيطاً.  
- `WrapType.Inline` يضمن أن يتحرك المستطيل مع تدفق النص، وهو ما تتوقعه عادةً في سيناريو معالجة النصوص.  
- بإلحاقه بـ `FirstParagraph`، نتجنب الحاجة إلى إدراج فقرة جديدة يدوياً؛ Aspose ينشئ واحدة لنا إذا كان المستند فارغاً تماماً.

> **نصيحة احترافية:** إذا كنت تحتاج أن يكون الشكل *خلف* النص، غيّر `WrapType` إلى `WrapType.Transparent`. هذا التغيير الصغير يمكن أن يحدث فرقاً بصرياً كبيراً.

---

## الخطوة 3: تطبيق ظل خارجي – تحسين المظهر

المستطيل المسطح هو… حسناً، مسطح. إضافة **إضافة ظل إلى الشكل** يمنحه عمقاً دون الحاجة إلى صور إضافية. `ShadowFormat` في Aspose يجعل ذلك سطرًا واحدًا.

```csharp
// Step 3: Configure an outer shadow for the rectangle
rect.ShadowFormat.Type = ShadowType.OuterShadow;
rect.ShadowFormat.Blur = 5.0;           // Softness of the shadow edge
rect.ShadowFormat.Distance = 3.0;      // How far the shadow is offset
rect.ShadowFormat.Angle = 45;          // Direction in degrees (45° = bottom‑right)
rect.ShadowFormat.Color = Color.Gray; // Classic gray shadow
```

لماذا نهتم بهذه القيم المحددة؟  
- **Blur** بقيمة `5.0` يعطي حافة رقيقة ناعمة تبدو احترافية على معظم الشاشات.  
- **Distance** بقيمة `3.0` و **Angle** بقيمة `45` يخلق مصدر إضاءة طبيعي من أعلى اليسار، وهو معيار شائع في التصميم.  
- `Color.Gray` يعمل على كل من السمات الفاتحة والداكنة؛ يمكنك استبداله بـ `Color.Black` إذا كنت تحتاج إلى تباين أقوى.

إذا احتجت يوماً إلى ظل *داخلي* (فكر في زر مغمور)، فقط غيّر `ShadowType.OuterShadow` إلى `ShadowType.InnerShadow`. لا تزال الخصائص نفسها سارية.

---

## الخطوة 4: حفظ المستند كـ DOCX – حفظ عملك

كل هذا ممتع، لكنك في النهاية ستحتاج إلى ملف على القرص. خطوة **حفظ المستند كـ docx** بسيطة:

```csharp
// Step 4: Persist the document to a .docx file
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
doc.Save(outputPath, SaveFormat.Docx);
```

بعض الملاحظات:  
- `SaveFormat.Docx` يضمن تنسيق Office Open XML الحديث، المتوافق مع Word 2007+.  
- إذا كنت تحتاج إلى بث الملف مباشرةً إلى استجابة ويب، استبدل مسار الملف بـ `MemoryStream` واكتبها إلى استجابة HTTP.

بعد تشغيل الشيفرة، افتح `ShadowedRectangle.docx` في Microsoft Word. يجب أن ترى مستطيلًا رماديًا مع ظل ناعم، مدمجًا مع الفقرة الأولى — بالضبط ما كنا نسعى لتحقيقه.

---

## كيفية إضافة شكل – طرق بديلة

المثال أعلاه يستخدم نهج *inline*، لكن أحيانًا تريد شكلاً يطفو فوق النص. هنا يأتي دور **كيفية إضافة شكل** مع تغليف مختلف.

```csharp
Shape floatingRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 250,
    Height = 120,
    WrapType = WrapType.Square, // Allows text to wrap around the shape
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    HorizontalAlignment = HorizontalAlignment.Center
};

doc.FirstSection.Body.FirstParagraph.AppendChild(floatingRect);
```

هنا قمنا بتغيير `WrapType` إلى `Square` ومركزنا الشكل في الصفحة. هذا النمط مفيد لصفحات الغلاف أو اللافتات الزخرفية. تذكر: الأشكال العائمة تزيد حجم الملف قليلاً لأن Word يخزن بيانات تموضع إضافية.

---

## النتيجة المتوقعة والتحقق

عند فتح الملف المُنشأ، يجب أن ترى:

- فقرة واحدة تحتوي على مستطيل رمادي.  
- المستطيل بأبعاد تقريبية 2.8 × 1.4 بوصة.  
- ظل خارجي خفيف مائل إلى أسفل اليمين.  

إذا ظهر الشكل *خارج* الفقرة، تحقق مرة أخرى من `WrapType`. إذا كان الظل يبدو قاسياً جداً، قلل قيمة `Blur` أو غيّر `Color` إلى درجة أفتح.

---

## الأخطاء الشائعة وكيفية تجنبها

| المشكلة | سبب حدوثها | الحل |
|-------|----------------|-----|
| اختفاء الشكل بعد الحفظ | `WrapType` مضبوط على `Inline` لكن الفقرة تم إزالتها | تأكد من وجود الفقرة؛ استخدم `doc.FirstSection.Body.FirstParagraph` لضمان وجودها. |
| الظل يبدو بكسليًا | استخدام قيمة `Blur` منخفضة جداً | زيادة `Blur` إلى ما لا يقل عن `3.0` للحصول على حواف ناعمة. |
| حجم الملف يزداد بشكل كبير | إضافة العديد من الصور عالية الدقة إلى جانب الأشكال | استخدم `doc.RemoveUnusedResources()` قبل الحفظ إذا أضفت صورًا. |
| اللون لا يظهر في الوضع الداكن | استخدام لون `Color` داكن للشكل نفسه | اختر لونًا متباينًا (مثل `Color.White`) لتحسين الرؤية. |

---

## مثال كامل يعمل

فيما يلي الشيفرة الكاملة الجاهزة للنسخ واللصق التي تجمع كل ما ناقشناه. لا تتردد في تشغيلها كتطبيق كونسول.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank Word document
        Document doc = new Document();

        // 2️⃣ Add a rectangle shape to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 200,
            Height = 100,
            WrapType = WrapType.Inline
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Apply an outer shadow to the rectangle
        rect.ShadowFormat.Type = ShadowType.OuterShadow;
        rect.ShadowFormat.Blur = 5.0;
        rect.ShadowFormat.Distance = 3.0;
        rect.ShadowFormat.Angle = 45;
        rect.ShadowFormat.Color = Color.Gray;

        // 4️⃣ Save the document as a .docx file
        string outPath = @"C:\Temp\ShadowShape.docx";
        doc.Save(outPath, SaveFormat.Docx);

        // Optional: Let the user know we’re done
        System.Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**شرح كل جزء** موجود كتعليقات داخل الشيفرة، لتلبية قرّاء SEO والمساعدين الذكائيين الذين يفضّلون الإجابات المتكاملة.

---

## الخلاصة

لقد **أنشأنا مستند word** من الصفر، وتعلمنا **كيفية إضافة شكل**، وبشكل محدد **إضافة شكل مستطيل**، ومنحناه **إضافة ظل إلى الشكل**، وأخيراً **حفظ المستند كـ docx**. الخطوات بسيطة، الشيفرة مختصرة، والنتيجة تبدو مصقولة.  

إذا كنت مستعدًا للانتقال إلى المستوى التالي، جرّب استبدال المستطيل بصورة مخصصة، أو تجربة ألوان ظل مختلفة، أو إنشاء تقرير كامل يحتوي على أقسام متعددة بأشكال. واجهة برمجة التطبيقات Aspose.Words مرنة بما يكفي للتعامل مع كل شيء من الفواتير إلى الكتيبات التسويقية.

هل لديك أسئلة حول أنواع أشكال أخرى أو تحتاج مساعدة في دمج هذا في خدمة ASP.NET Core؟ اترك تعليقًا أدناه، وتمنياتنا لك ببرمجة سعيدة! 

![إنشاء مستند word مع شكل مستطيل وظل](placeholder-image.png "إنشاء مستند word مع شكل مستطيل وظل

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}