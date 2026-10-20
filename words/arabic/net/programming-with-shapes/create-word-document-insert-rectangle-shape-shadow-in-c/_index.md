---
category: general
date: 2026-05-26
description: إنشاء مستند Word في C# باستخدام Aspose.Words، إدراج شكل مستطيل، تعيين
  لون التعبئة، وإضافة تأثير الظل – دليل خطوة بخطوة.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- how to set fill
language: ar
og_description: إنشاء مستند Word في C# باستخدام Aspose.Words. تعلّم كيفية إدراج شكل
  مستطيل، ضبط لون التعبئة، وإضافة تأثير الظل.
og_title: إنشاء مستند Word – إدراج شكل مستطيل وظل في C#
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create Word document in C# with Aspose.Words, insert rectangle shape,
    set fill color, and add shadow effect – step‑by‑step guide.
  headline: Create Word Document – Insert Rectangle Shape & Shadow in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: إنشاء مستند Word – إدراج شكل مستطيل وظل في C#
url: /ar/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word – إدراج شكل مستطيل وظل في C#

هل تساءلت يومًا كيف **إنشاء مستند Word** برمجيًا دون فتح Microsoft Word أولاً؟ لست وحدك. في العديد من سيناريوهات الأتمتة—مثل الفواتير، العقود، أو توليد تقارير جماعية—تحتاج إلى طريقة موثوقة لإنشاء ملف .docx، وإدراج شكل داخله، وإعطائه لونًا، وربما حتى ظلًا للحصول على مظهر مصقول.

في هذا البرنامج التعليمي سنستعرض ذلك بالضبط: باستخدام Aspose.Words for .NET لـ **إنشاء مستند Word**، **إدراج شكل مستطيل**، تطبيق تعبئة، و**إضافة ظل**. في النهاية ستحصل على ملف جاهز للحفظ يمكنك تمريره إلى أي سير عمل لاحق.  

سنناقش أيضًا **كيفية إدراج الشكل** بطريقة مرنة، ولماذا **كيفية ضبط التعبئة** مهمة للاتساق البصري. لا إطالة، فقط الكود الذي يمكنك نسخه‑ولصقه وتشغيله.

## المتطلبات المسبقة

- .NET 6+ (or .NET Framework 4.7+) مثبت.
- ترخيص صالح لـ Aspose.Words for .NET (أو مفتاح تقييم مؤقت).
- Visual Studio، Rider، أو أي بيئة تطوير C# تفضلها.
- إلمام أساسي بتركيب C#—لا شيء معقد مطلوب.

هل لديك هذه المتطلبات؟ رائع، لنبدأ.

## الخطوة 1 – إنشاء مستند Word

أول شيء تحتاجه هو كائن مستند فارغ. هذا هو القماش الذي يعيش عليه كل شيء آخر.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder.
Document doc = new Document();                 // The document itself.
DocumentBuilder builder = new DocumentBuilder(doc); // Helper to add content.
```

`Document` يمثل ملف .docx في الذاكرة، بينما `DocumentBuilder` يزودنا بواجهة برمجة تطبيقات مريحة لإدراج النصوص والجداول والأشكال. **إنشاء مستند Word** بهذه الطريقة فوري—بدون واجهة مستخدم، بدون تفاعل COM، فقط .NET نقي.

## الخطوة 2 – إدراج شكل مستطيل

الآن بعد أن لدينا مستندًا، دعنا **نُدرج شكل مستطيل**. طريقة `InsertShape` تأخذ تعداد `ShapeType`، العرض، والارتفاع (بالنقاط). سنستخدم مستطيل بحجم 150 × 80 نقطة، وهو ما يساوي تقريبًا 2 × 1 بوصة.

```csharp
// Step 2: Insert a rectangle shape of the desired size.
Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

خلف الكواليس، تقوم Aspose بإنشاء كائن `Shape`، وتضيفه إلى الفقرة الحالية، وتعيد مرجعًا يمكنك تنسيقه. هذا هو جوهر **كيفية إدراج الشكل**—سطر واحد من الكود فقط، لكنه قوي للغاية.

## الخطوة 3 – كيفية ضبط التعبئة

الشكل بدون تعبئة يكون غير مرئي على صفحة بيضاء. دعنا نعطيه خلفية زرقاء فاتحة مريحة.

```csharp
// Step 3: Apply a fill color to make the shape visible.
shape.FillColor = System.Drawing.Color.LightBlue; // Any System.Drawing.Color works.
```

يمكنك أيضًا استخدام التدرجات، القوام، أو حتى تعبئة بصورة، لكن اللون الصلب يبقي المثال بسيطًا. هذا يوضح **كيفية ضبط التعبئة** على أي شكل تنشئه، مما يضمن الإشارة البصرية التي يتوقعها القراء.

## الخطوة 4 – كيفية إضافة الظل

الظلال تضيف عمقًا وتجعل الشكل يبرز. تُظهر Aspose.Words كائن `ShadowFormat` حيث يمكنك تبديل الرؤية، اختيار لون، وضبط الضبابية، المسافة، والزاوية بدقة.

```csharp
// Step 4: Configure the shadow effect – enable it, set color, blur, distance and angle.
shape.ShadowFormat.Visible = true;                     // Turn the shadow on.
shape.ShadowFormat.Color = System.Drawing.Color.Gray; // Shadow color.
shape.ShadowFormat.BlurRadius = 4.0;                  // Softness in pixels.
shape.ShadowFormat.Distance = 3.0;                    // How far the shadow is offset.
shape.ShadowFormat.Angle = 45;                        // Direction of the offset (degrees).
```

لماذا هذه القيم بالتحديد؟ زاوية 45° تعطي مصدر إضاءة طبيعي من أعلى‑يمين، وضبابية معتدلة تحافظ على الظل خفيفًا، والمسافة القصيرة تمنع الشكل من الظهور منفصلًا. لا تتردد في التجربة—تغيير الزاوية إلى 135° سيجعل الظل يسقط إلى أسفل‑اليسار، على سبيل المثال.

## الخطوة 5 – حفظ المستند

تم إنجاز كل العمل؛ الآن نكتب الملف إلى القرص. اختر أي مسار تفضله؛ فقط تأكد من وجود المجلد.

```csharp
// Step 5: Save the document with the shaped shadow.
doc.Save("YOUR_DIRECTORY/ShadowShape.docx");
```

عند فتح `ShadowShape.docx` في Microsoft Word، سترى مستطيلًا أزرق فاتح مع ظل رمادي ناعم—تمامًا ما برمجناه.

## مثال كامل يعمل

بجمع كل ذلك معًا، إليك البرنامج الكامل الجاهز للنسخ‑واللصق:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a rectangle shape (150 × 80 points).
        Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

        // 3️⃣ Set a solid fill color so the shape is visible.
        shape.FillColor = System.Drawing.Color.LightBlue;

        // 4️⃣ Add a subtle shadow for depth.
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.Color = System.Drawing.Color.Gray;
        shape.ShadowFormat.BlurRadius = 4.0;   // pixels
        shape.ShadowFormat.Distance = 3.0;     // pixels
        shape.ShadowFormat.Angle = 45;        // degrees

        // 5️⃣ Persist the document.
        doc.Save("ShadowShape.docx");
    }
}
```

### النتيجة المتوقعة

- ملف باسم **ShadowShape.docx** يظهر في المجلد المستهدف.
- فتحه في Word يظهر مستطيلًا أزرق فاتحًا في وسط الصفحة الأولى.
- المستطيل يلقي ظلًا رماديًا بزاوية 45°، مما يعطي تأثيرًا ثلاثي الأبعاد خفيفًا.

## أسئلة شائعة وحالات خاصة

**ماذا لو احتجت إلى شكل مختلف؟**  
استبدل `ShapeType.Rectangle` بأي قيمة تعداد أخرى (`Ellipse`، `Star`، `Arrow`، إلخ). يبقى باقي الكود كما هو.

**هل يمكنني إضافة نص داخل الشكل؟**  
نعم—بعد إنشاء الشكل، استدعِ `shape.AppendChild(new Paragraph(doc))` ثم أدخل `Run` بنصك. تذكر ضبط خصائص `shape.TextBox` إذا كنت تريد التفاف النص.

**ماذا عن DPI أو وحدات القياس؟**  
تعمل Aspose بالنقاط (1 pt = 1/72 inch). إذا كنت تفضل السنتيمترات، اضرب في 28.35 (لأن 1 cm ≈ 28.35 pt).

**هل أحتاج إلى ترخيص لتعمل هذه العملية؟**  
الإصدار التجريبي يضيف علامة مائية على الصفحة الأولى. الترخيص الصحيح يزيلها ويفتح كامل واجهة البرمجة.

## نصائح وملاحظات

- **نصيحة احترافية:** استدعِ `builder.MoveToDocumentEnd()` قبل إدراج الشكل إذا أردت وضعه في نهاية المستند تمامًا.
- **احذر من:** حفظ الملف في مجلد للقراءة فقط سيسبب استثناء `UnauthorizedAccessException`. تأكد من أن تطبيقك يملك صلاحيات الكتابة.
- **ملاحظة أداء:** لتوليد جماعي (مئات المستندات)، أعد استخدام نسخة واحدة من كائن `Document` كقالب واستنسخه باستخدام `doc.Clone(true)` لتجنب عبء التهيئة المتكرر.

## الخلاصة

أنت الآن تعرف كيف **إنشاء مستند Word**، **إدراج شكل مستطيل**، **ضبط التعبئة**، و**إضافة الظل** باستخدام Aspose.Words for .NET. المقتطف أعلاه هو حل مستقل يمكنك إدراجه في أي مشروع C#، سواء كان تطبيقًا سطريًا، واجهة برمجة تطبيقات ويب، أو خدمة خلفية.

من هنا قد تستكشف:

- إضافة أشكال متعددة بألوان مختلفة.
- استخدام التدرجات أو تعبئة بالصور (`shape.FillColor = ...` → `shape.FillPattern`).
- دمج الأشكال مع الجداول لتصاميم تقارير معقدة.

جرّبه، عدّل المعلمات، وشاهد ملفات Word الآلية تبدو أكثر احترافية ببضع أسطر من الكود فقط. برمجة سعيدة!

## دروس ذات صلة

- [إنشاء شكل مستطيل في Word باستخدام C# – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [دورة ظل شكل Aspose.Words – إضافة ظل إلى شكل Word في C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [إنشاء شكل مجموعة في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}