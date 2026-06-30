---
category: general
date: 2026-06-30
description: كيفية إضافة الظل في C# باستخدام Aspose.Words. تعلم تغيير لون الظل، وضبط
  شفافية الظل، وإضافة الظل إلى الشكل، وحفظ المستند المعدل.
draft: false
keywords:
- how to add shadow
- change shadow color
- save modified document
- add shadow to shape
- adjust shadow transparency
language: ar
og_description: كيفية إضافة الظل في C# باستخدام Aspose.Words. يوضح هذا الدرس كيفية
  إضافة الظل إلى الشكل، وتغيير لون الظل، وضبط شفافية الظل، وحفظ المستند المعدل.
og_title: كيفية إضافة الظل إلى أشكال Word – دليل C# الكامل
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: How to add shadow in C# using Aspose.Words. Learn to change shadow
    color, adjust shadow transparency, add shadow to shape, and save modified document.
  headline: How to Add Shadow to Word Shapes – Complete C# Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: كيفية إضافة الظل إلى أشكال Word – دليل C# الكامل
url: /ar/net/programming-with-shapes/how-to-add-shadow-to-word-shapes-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إضافة الظل إلى أشكال Word – دليل C# الكامل

هل تساءلت يومًا **كيف تضيف ظلًا** إلى شكل Word باستخدام C#؟ لست وحدك. غالبًا ما يحتاج المطورون إلى هذا التأثير الخفيف لإضفاء عمق على التقارير أو الكتيبات أو أي مستند يرغب في أن يبدو أكثر صقلًا. الخبر السار؟ ببضع أسطر من الشيفرة يمكنك تمكين الظل، تعديل لونه، وحتى ضبط شفافيته — كل ذلك مع الحفاظ على سير العمل آليًا بالكامل.

في هذا البرنامج التعليمي سنستعرض **كيفية إضافة الظل** إلى شكل، **تغيير لون الظل**، **ضبط شفافية الظل**، وأخيرًا **حفظ المستند المعدل** بحيث تبقى التغييرات محفوظة. في النهاية ستحصل على مقتطف يمكن إعادة استخدامه في أي مشروع Aspose.Words.

## المتطلبات المسبقة

قبل أن نبدأ، تأكد من وجود ما يلي:

* **Aspose.Words for .NET** (الإصدار 23.11 أو أحدث). يمكنك الحصول عليه من NuGet باستخدام `Install-Package Aspose.Words`.
* بيئة تطوير **.NET 6+** (Visual Studio، Rider، أو VS Code).
* ملف Word إدخالي (`input.docx`) يحتوي بالفعل على شكل واحد على الأقل (مثل مستطيل، نجمة، أو صورة).

هذا كل ما تحتاجه — لا مكتبات إضافية، ولا خطوات يدوية في الواجهة. جاهز؟ لنبدأ.

## الخطوة 1 – تحميل مستند Word (كيفية إضافة الظل)

أول شيء تحتاج معرفته حول **كيفية إضافة الظل** هو أنه يجب تحميل المستند إلى كائن `Aspose.Words.Document`. هذا يمنحك وصولًا برمجيًا إلى كل عقدة، بما في ذلك الأشكال.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the source document that contains the shape.
        Document doc = new Document(@"C:\Docs\input.docx");
```

> **لماذا هذا مهم:** تحميل الملف هو البوابة لأي تعديل. بدون كائن `Document` لا يمكنك الوصول إلى شجرة الأشكال، وبالتالي لا يمكنك تطبيق الظل.

## الخطوة 2 – استرجاع الشكل المستهدف (إضافة ظل إلى الشكل)

الآن بعد أن أصبح المستند في الذاكرة، دعنا نحدد الشكل الذي نريد تنسيقه. تُظهر هذه الخطوة **إضافة ظل إلى الشكل** لأول شكل يتم العثور عليه، لكن يمكنك بسهولة توسيعها لتحديد الشكل بالاسم أو الفهرس.

```csharp
        // Retrieve the first shape in the document (searches recursively).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        if (shape == null)
        {
            Console.WriteLine("No shape found in the document.");
            return;
        }
```

> **نصيحة:** إذا كان مستندك يحتوي على عدة أشكال، استبدل `0` بالفهرس المناسب أو استخدم حلقة عبر `doc.GetChildNodes(NodeType.Shape, true)`.

## الخطوة 3 – تمكين الظل وتكوين مظهره (تغيير لون الظل وضبط شفافية الظل)

هنا يكمن جوهر **كيفية إضافة الظل**: نقوم بتفعيل الظل، وتحديد الإزاحة، والطمس، واللون، والشفافية. لا تتردد في تجربة القيم الرقمية للحصول على المظهر الدقيق الذي تريده.

```csharp
        // Turn the shadow on.
        shape.ShadowFormat.Visible = true;

        // Position the shadow 4 points to the right and 4 points down.
        shape.ShadowFormat.OffsetX = 4; // Horizontal offset in points.
        shape.ShadowFormat.OffsetY = 4; // Vertical offset in points.

        // Adjust shadow transparency – this demonstrates **adjust shadow transparency**.
        shape.ShadowFormat.Transparency = 0.3; // 30 % transparent.

        // Change the shadow color – this is the **change shadow color** part.
        shape.ShadowFormat.Color = Color.Gray; // You can use any System.Drawing.Color.

        // Add a subtle blur to soften the edges.
        shape.ShadowFormat.BlurRadius = 5; // Blur radius in points.
```

> **لماذا هذه الإعدادات؟**  
> *`Visible`* يُفعِّل التأثير.  
> *`OffsetX`/`OffsetY`* تحاكي مصدر الضوء، مما يضيف عمقًا.  
> *`Transparency`* يتيح لك جعل الظل أفتح أو أغمق دون تغيير اللون — طريقة كلاسيكية **لضبط شفافية الظل**.  
> *`Color`* يتيح لك **تغيير لون الظل**؛ اللون الرمادي يناسب معظم المستندات التجارية، لكن يمكنك استخدام `Color.Black` أو أي لون مخصص عبر `Color.FromArgb(...)`.  
> *`BlurRadius`* يضيف واقعية — الظلال الحادة تبدو صناعية.

## الخطوة 4 – حفظ المستند المعدل (حفظ المستند المعدل)

أخيرًا، نقوم بحفظ التغييرات. هذه الخطوة تجيب على **حفظ المستند المعدل** دون أي تدخل يدوي.

```csharp
        // Save the updated document to a new file.
        doc.Save(@"C:\Docs\output.docx");

        Console.WriteLine("Shadow applied and document saved successfully.");
    }
}
```

> **ماذا يحدث خلف الكواليس؟** تقوم Aspose.Words بكتابة أجزاء XML المحدثة، بما في ذلك عنصر `<w:shadow>` مع جميع السمات التي قمت بتعيينها. سيفتح المستند `output.docx` في Word مع الظل مفعَّلًا بالفعل.

## مثال كامل يعمل

بدمج كل ما سبق، إليك البرنامج الكامل جاهزًا للنسخ واللصق:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the shape.
        Document doc = new Document(@"C:\Docs\input.docx");

        // 2️⃣ Retrieve the first shape (add shadow to shape).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found in the document.");
            return;
        }

        // 3️⃣ Enable the shadow and configure its appearance.
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.OffsetX = 4;
        shape.ShadowFormat.OffsetY = 4;
        shape.ShadowFormat.Transparency = 0.3;      // Adjust shadow transparency.
        shape.ShadowFormat.Color = Color.Gray;      // Change shadow color.
        shape.ShadowFormat.BlurRadius = 5;

        // 4️⃣ Save the modified document (save modified document).
        doc.Save(@"C:\Docs\output.docx");

        Console.WriteLine("Shadow applied and document saved successfully.");
    }
}
```

### النتيجة المتوقعة

افتح `output.docx` في Microsoft Word. سيظهر الشكل الأول الموجود في `input.docx` الآن بظل رمادي ناعم، إزاحة 4 نقطة، شفافية 30 %، وطمس خفيف. يبقى باقي المستند دون تغيير.

## الاختلافات الشائعة وحالات الحافة

| الحالة | ما الذي يجب تعديله | السبب |
|-----------|----------------|-----|
| **أشكال متعددة** | استخدم حلقة عبر `doc.GetChildNodes(NodeType.Shape, true)` وطبق الإعدادات نفسها على كل منها. | يضمن أن كل رسم يحصل على نفس العمق البصري. |
| **ألوان ظل مختلفة** | استخدم `shape.ShadowFormat.Color = Color.FromArgb(255, 100, 100);` للحصول على ظل أحمر مائل. | يسمح بالتماشي مع العلامة التجارية أو الثيم. |
| **عدم الحاجة لظل على شكل معين** | تخطى الشكل بناءً على `shape.Name` أو `shape.ShapeType`. | يمنع ظهور تأثير غير مرغوب فيه على الشعارات أو الأيقونات. |
| **شفافية أعلى** | عيّن `Transparency = 0.7` للحصول على ظل شفاف شبه شبح. | مفيد للخلفيات الخفيفة. |
| **الأداء مع المستندات الكبيرة** | حمّل المستند باستخدام `LoadOptions` التي تتخطى الخطوط غير الضرورية. | يقلل من استهلاك الذاكرة عند معالجة ملفات متعددة. |

## نصائح وحيل (نصائح احترافية)

* **نصيحة احترافية:** إذا كنت تريد *ظلًا إسقاطيًا* يشبه Photoshop، زد `BlurRadius` إلى 10‑12 واضبط `Transparency` إلى 0.2 للحصول على مظهر أكثر حدة.
* **احذر من:** الأشكال *المضمنة* مقابل *العائمة*. الأشكال المضمنة ترث تنسيق الفقرة، وقد لا يظهر الظل بنفس الطريقة. استخدم `shape.IsInline` لتحديد ما إذا كنت بحاجة لتحويلها إلى شكل عائم أولًا.
* **طريقة قابلة لإعادة الاستخدام:** غلف منطق الظل في طريقة مساعدة:

```csharp
static void ApplyShadow(Shape s, int offset = 4, double transparency = 0.3,
                        Color? color = null, int blur = 5)
{
    s.ShadowFormat.Visible = true;
    s.ShadowFormat.OffsetX = offset;
    s.ShadowFormat.OffsetY = offset;
    s.ShadowFormat.Transparency = transparency;
    s.ShadowFormat.Color = color ?? Color.Gray;
    s.ShadowFormat.BlurRadius = blur;
}
```

الآن يمكنك استدعاء `ApplyShadow(shape);` في أي مكان تحتاجه.

## الخلاصة

لقد استعرضنا **كيفية إضافة الظل** إلى شكل Word باستخدام C#. أظهرت الخطوات لك كيفية **إضافة ظل إلى الشكل**، **تغيير لون الظل**، **ضبط شفافية الظل**، وأخيرًا **حفظ المستند المعدل**. مع هذه المعرفة يمكنك إضفاء لمسة بصرية احترافية على أي تقرير آلي، كتيب تسويقي، أو مذكرة داخلية.

ما الخطوة التالية؟ جرّب دمج هذا مع ميزات تنسيق أخرى — مثل التعبئات المتدرجة أو التأثيرات ثلاثية الأبعاد — لإنشاء مستندات جذابة حقًا. أو استكشف API الخاص بـ Aspose.Words للجداول، المخططات، والدمج البريدي لإنشاء خطوط معالجة مستندات شاملة من البداية إلى النهاية.

هل لديك سؤال حول نوع شكل معين أو تحتاج لتطبيق الظلال بشكل شرطي؟ اترك تعليقًا أدناه، ولنستمر في النقاش. برمجة سعيدة!

## ماذا يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Add Text Watermark in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-watermark/add-text-watermark/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}