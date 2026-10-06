---
category: general
date: 2026-03-08
description: إضافة ظل إلى الشكل في Word باستخدام Aspose.Words. تعلّم كيفية إضافة الظل
  وتطبيق تأثير الظل في Word باستخدام C# خلال دقائق.
draft: false
keywords:
- add shadow to shape
- how to add shadow
- apply shadow effect word
language: ar
og_description: أضف الظل إلى الشكل في Word فورًا. يوضح هذا الدليل كيفية إضافة الظل
  وتطبيق تأثير الظل في Word باستخدام Aspose.Words.
og_title: إضافة ظل إلى الشكل في Word – دليل C# الكامل
tags:
- Aspose.Words
- C#
- Word Automation
title: إضافة ظل إلى الشكل في Word باستخدام Aspose.Words – خطوة بخطوة
url: /ar/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة ظل إلى الشكل في Word باستخدام Aspose.Words – دليل كامل

هل احتجت يومًا إلى **إضافة ظل إلى الشكل** في مستند Word لكن لم تكن متأكدًا من أين تبدأ؟ لست وحدك—العديد من المطورين يواجهون هذه المشكلة عندما يبدأون أول مرة في أتمتة المستندات. الخبر السار؟ باستخدام Aspose.Words for .NET يمكنك تطبيق تأثير ظل بمظهر احترافي في بضع أسطر فقط من C#.

في هذا البرنامج التعليمي سنستعرض العملية بالكامل: من تحميل ملف DOCX يحتوي بالفعل على شكل، إلى تعديل لون الظل، والطمس، والإزاحة، والشفافية، وأخيرًا حفظ الملف المحدث. في النهاية ستعرف **كيفية إضافة ظل** إلى أي شكل وستفهم أيضًا **كيفية تطبيق تأثير الظل على مستوى المستند** إذا كنت بحاجة إلى مظهر متسق عبر المستند بأكمله.

## المتطلبات المسبقة

قبل أن نبدأ، تأكد من أن لديك:

* **Aspose.Words for .NET** (أحدث نسخة حتى 2026‑03‑08). يمكنك الحصول عليها من NuGet باستخدام `Install-Package Aspose.Words`.
* **بيئة تطوير .NET** – Visual Studio أو Rider أو حتى VS Code مع امتداد C#.
* ملف Word تجريبي (`Shadow.docx`) يحتوي بالفعل على شكل واحد على الأقل (مستطيل، دائرة، أو صورة). إذا لم يكن لديك، أنشئ مستندًا سريعًا عبر Insert → Shapes → أي شكل واحفظه.

لا توجد مكتبات خارجية أخرى مطلوبة.

## الخطوة 1 – تحميل المستند المصدر

أولًا وقبل كل شيء: نحتاج إلى جلب ملف Word إلى الذاكرة. Aspose.Words يتعامل مع المستند كشجرة من العقد، لذا فإن تحميله بسيط كاستدعاء مُنشئ `Document`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Load the Word file that already contains a shape.
Document sourceDoc = new Document("YOUR_DIRECTORY/Shadow.docx");
```

*لماذا هذا مهم*: تحميل المستند يمنحنا نموذج كائن قابل للتلاعب. بدون ذلك، لا يمكننا الوصول إلى الشكل أو خصائص الظل الخاصة به.

## الخطوة 2 – العثور على الشكل المستهدف

بعد ذلك، حدد الشكل الذي تريد تعديلّه. في أغلب الحالات البسيطة يكون الشكل الأول (`NodeType.Shape, 0`) هو المطلوب، لكن يمكنك أيضًا البحث بالاسم أو بموقعه في المستند.

```csharp
// Retrieve the first shape in the document.
// Cast is safe because GetChild returns a Node; we know it’s a Shape.
Shape targetShape = (Shape)sourceDoc.GetChild(NodeType.Shape, 0, true);

if (targetShape == null)
{
    throw new InvalidOperationException("No shape found in the document.");
}
```

*لماذا هذا مهم*: الإشارة مباشرة إلى الشكل تضمن أننا نؤثر فقط على الكائن المقصود. إذا كان لديك عدة أشكال، يمكنك التكرار عبر `sourceDoc.GetChildNodes(NodeType.Shape, true)` واختيار الشكل المناسب.

## الخطوة 3 – ضبط إعدادات الظل

الآن الجزء الممتع—تعديل الظل. Aspose.Words يتيح خمس خصائص رئيسية:

| الخاصية | ما الذي تتحكم فيه |
|----------|-------------------|
| `ShadowColor` | اللون الأساسي للظل (مثال: الأسود). |
| `ShadowBlur` | مدى نعومة الحواف (القيمة الأكبر = أكثر نعومة). |
| `ShadowOffsetX` | الإزاحة الأفقية (القيمة الموجبة تتحرك إلى اليمين). |
| `ShadowOffsetY` | الإزاحة العمودية (القيمة الموجبة تتحرك إلى الأسفل). |
| `ShadowTransparency` | الشفافية (0 = غير شفاف، 1 = شفاف بالكامل). |

إليك مقتطف كامل يضيف ظلًا أسودًا خفيفًا شبه شفاف:

```csharp
// Set the shadow color to pure black.
targetShape.ShadowColor = Color.FromArgb(0, 0, 0);

// Apply a moderate blur to soften the edges.
targetShape.ShadowBlur = 4.0;          // Measured in points.

// Shift the shadow a few points right and down.
targetShape.ShadowOffsetX = 3.0;       // Horizontal offset.
targetShape.ShadowOffsetY = 3.0;       // Vertical offset.

// Make the shadow 30 % transparent (i.e., 70 % visible).
targetShape.ShadowTransparency = 0.3;
```

### لماذا اختيار هذه القيم؟

* **اللون الأسود** يناسب معظم المستندات لأنه يتباين جيدًا مع الخلفيات الفاتحة.
* **الطمس = 4.0** يعطي حافة ناعمة دون أن يبدو مشوشًا.
* **الإزاحة X/Y = 3.0** تحاكي مصدر ضوء موضعه قليلاً فوق اليسار، وهو دليل بصري طبيعي.
* **الشفافية = 0.3** تضمن أن الظل ليس مهيمنًا—يكفي فقط لإضافة عمق.

لا تتردد في التجربة: ظل أحمر (`Color.FromArgb(255,0,0)`) يمكن أن يكون جذابًا للتحذيرات، بينما طمس أكبر (مثال: `8.0`) يخلق تأثيرًا حالميًا.

## الخطوة 4 – حفظ المستند المحدث

بعد أن يصبح الظل بالمظهر الذي تريده، احفظ التغييرات. يمكنك استبدال الملف الأصلي أو الكتابة إلى موقع جديد.

```csharp
// Save the modified document.
sourceDoc.Save("YOUR_DIRECTORY/ShadowAdjusted.docx");
```

إذا كنت بحاجة إلى إخراج PDF بدلاً من ذلك، ما عليك سوى تغيير الامتداد أو استخدام `SaveOptions`:

```csharp
sourceDoc.Save("YOUR_DIRECTORY/ShadowAdjusted.pdf", SaveFormat.Pdf);
```

*لماذا هذا مهم*: الحفظ ينهى التغييرات ويجعل المستند جاهزًا للتوزيع أو الطباعة أو المعالجة الإضافية.

## مثال كامل يعمل

فيما يلي البرنامج الكامل، جاهز للنسخ واللصق في تطبيق Console. جميع التعليقات مدمجة للوضوح.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source DOCX that already contains a shape.
        Document sourceDoc = new Document("YOUR_DIRECTORY/Shadow.docx");

        // 2️⃣ Grab the first shape (or replace with your own search logic).
        Shape targetShape = (Shape)sourceDoc.GetChild(NodeType.Shape, 0, true);
        if (targetShape == null)
        {
            System.Console.WriteLine("No shape found – aborting.");
            return;
        }

        // 3️⃣ Apply a custom shadow.
        targetShape.ShadowColor = Color.FromArgb(0, 0, 0);   // black
        targetShape.ShadowBlur = 4.0;                      // soft edges
        targetShape.ShadowOffsetX = 3.0;                   // right shift
        targetShape.ShadowOffsetY = 3.0;                   // down shift
        targetShape.ShadowTransparency = 0.3;             // 30 % transparent

        // 4️⃣ Save the document with the new visual effect.
        sourceDoc.Save("YOUR_DIRECTORY/ShadowAdjusted.docx");

        System.Console.WriteLine("Shadow applied successfully!");
    }
}
```

### النتيجة المتوقعة

افتح `ShadowAdjusted.docx` في Microsoft Word. يجب أن يعرض الشكل المستهدف الآن ظلًا أسودًا خفيفًا مائلًا إلى أسفل‑اليمين، مع حواف ناعمة ولمسة من الشفافية. يعمل التأثير على **كيفية إضافة ظل** لكل من الأشكال المضمنة والعائمة.

## الحالات الخاصة والنصائح

| الحالة | ما الذي يجب مراقبته | الإصلاح المقترح |
|-----------|-------------------|---------------|
| **الشكل لديه ظل بالفعل** | الإعدادات الجديدة تستبدل القديمة، مما قد يكون غير متوقع. | استرجع القيم الحالية أولاً (`var oldColor = targetShape.ShadowColor;`) وقرّر ما إذا كنت ستدمج أو تستبدل. |
| **خلفية شفافة** | ظل شفاف بالكامل (`ShadowTransparency = 1`) يصبح غير مرئي. | احتفظ بالقيمة بين `0` و `0.9` للحصول على تأثير مرئي. |
| **أشكال كبيرة جدًا** | الإزاحات بقيمة `3.0` نقطة قد تبدو ضئيلة. | قم بتعديل الإزاحات نسبياً (`targetShape.Width * 0.02`). |
| **عدة أشكال تحتاج نفس الظل** | تكرار نفس الكود لكل شكل أمر ممل. | التكرار عبر جميع الأشكال: `foreach (Shape s in sourceDoc.GetChildNodes(NodeType.Shape, true)) { /* apply settings */ }`. |
| **الحفظ إلى صيغ Word القديمة (.doc)** | بعض الصيغ القديمة لا تدعم خصائص الظل المتقدمة. | احفظ كـ `.docx` أو استخدم `SaveFormat.Docx`. |

**نصيحة احترافية:** عندما تطبق نفس الظل على العديد من الأشكال، احفظ الإعدادات في طريقة مساعدة:

```csharp
static void ApplyStandardShadow(Shape shape)
{
    shape.ShadowColor = Color.Black;
    shape.ShadowBlur = 4.0;
    shape.ShadowOffsetX = 3.0;
    shape.ShadowOffsetY = 3.0;
    shape.ShadowTransparency = 0.3;
}
```

ثم استدعِ `ApplyStandardShadow(s)` داخل الحلقة. هذا يحافظ على الكود DRY (Don’t Repeat Yourself) ويجعل التعديلات المستقبلية سهلة.

## الأسئلة المتكررة

**س: هل يعمل هذا مع Word 2010 وما بعده؟**  
نعم. Aspose.Words يج abstracts تنسيق الملف الأساسي، لذا فإن نفس API يعمل عبر Word 2007، 2010، 2013، 2016، وحتى Office 365.

**س: هل يمكنني تطبيق الظل على صورة بدلاً من شكل رسم؟**  
بالطبع. الصور أيضًا هي عقد `Shape`. نفس الخصائص (`ShadowColor`, `ShadowBlur`, إلخ) تنطبق.

**س: ماذا لو احتجت إلى توهج ملون بدلاً من الظل التقليدي؟**  
قم بتعيين `ShadowColor` إلى لون التوهج وزد `ShadowBlur` بشكل كبير (مثال: `12.0`). سيظهر التأثير كالهالة.

**س: هل هناك طريقة لمعاينة الظل قبل الحفظ؟**  
يمكنك تصيير المستند إلى PDF أو صورة (`sourceDoc.Save("preview.png", SaveFormat.Png)`) وتفحص النتيجة دون فتح Word.

## الخلاصة

لقد غطينا كل ما تحتاجه **لإضافة ظل إلى الشكل** في مستند Word باستخدام Aspose.Words for .NET. بدءًا من تحميل الملف، وتحديد الشكل، وضبط الخصائص البصرية للظل، وأخيرًا حفظ التغييرات، لديك الآن نمط قابل لإعادة الاستخدام لـ **كيفية إضافة

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}