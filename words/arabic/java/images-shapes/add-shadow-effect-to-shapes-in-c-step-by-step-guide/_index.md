---
category: general
date: 2025-12-22
description: أضف تأثير الظل إلى أشكال C# الخاصة بك بسهولة. تعلم كيفية إضافة الظل،
  وكيفية ضبط الضبابية، وإنشاء ظل ناعم باستخدام تنسيق ظل الشكل.
draft: false
keywords:
- add shadow effect
- how to add shadow
- how to set blur
- create soft shadow
- add shape shadow
language: ar
og_description: أضف تأثير الظل إلى أشكال C# الخاصة بك. يوضح هذا الدرس كيفية إضافة
  الظل، وضبط الضبابية، وإنشاء ظل ناعم مع أمثلة واضحة على الشيفرة.
og_title: إضافة تأثير الظل إلى الأشكال في C# – دليل كامل
tags:
- C#
- graphics
- Aspose.Slides
- UI design
title: إضافة تأثير الظل للأشكال في C# – دليل خطوة بخطوة
url: /ar/java/images-shapes/add-shadow-effect-to-shapes-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة تأثير الظل إلى الأشكال في C# – دليل كامل

هل تساءلت يومًا كيف تضيف **تأثير الظل** إلى شكل دون قضاء ساعات في البحث عبر وثائق API؟ لست وحدك. يواجه العديد من المطورين صعوبة عندما يحتاجون إلى ذلك الظل الخفيف لإبراز عناصر واجهة المستخدم، والإجابة المعتادة “انظر إلى المرجع” تبدو كطريق مسدود.

في هذا الدرس سنستعرض كل ما تحتاجه **لإضافة تأثير الظل** إلى شكل باستخدام C#. سنغطي *كيفية إضافة الظل*، *كيفية ضبط الضبابية* للحصول على توهج ناعم، وحتى كيفية **إنشاء ظل ناعم** يبدو احترافيًا في أي تطبيق. في النهاية ستحصل على مثال جاهز للتنفيذ يمكنك إدراجه في مشروعك الآن.

## ما يغطيه هذا الدرس

- الاتصالات الدقيقة لواجهة API المطلوبة **لإضافة ظل الشكل** في Aspose.Slides (أو أي مكتبة مشابهة).
- كود خطوة بخطوة يمكنك نسخه ولصقه.
- لماذا كل إعداد مهم – ليس مجرد قائمة أوامر.
- حالات الحافة مثل الأشكال الشفافة، الظلال المتعددة، ونصائح الأداء.
- عينة كاملة قابلة للتنفيذ تنتج ظلًا ناعمًا مرئيًا على مستطيل.

لا يتطلب أي خبرة سابقة في واجهات برمجة الظل؛ فقط فهم أساسي لـ C# والبرمجة الكائنية.

---

## إضافة تأثير الظل – نظرة عامة

الظل هو في الأساس إزاحة بصرية مع ضبابية تحاكي العمق. في معظم مكتبات الرسوميات يبدو العملية هكذا:

1. **استرجاع** كائن تنسيق ظل الشكل.
2. **تكوين** الخصائص مثل الإزاحة، اللون، ونصف قطر الضبابية.
3. **تطبيق** الإعدادات مرة أخرى على الشكل.

عند اتباع هذه الخطوات الثلاث ستظهر **ظل ناعم** فورًا. المفتاح هو نصف قطر الضبابية – وهو المقبض الذي يحول الحافة الصلبة إلى ضبابية ناعمة.

### ورقة مصطلحات سريعة

| المصطلح | ما يفعله |
|------|--------------|
| **ShadowFormat** | يحمل جميع الخصائص المتعلقة بالظل (الإزاحة، اللون، الضبابية، إلخ). |
| **BlurRadius** | يتحكم في مدى وضوح حافة الظل. القيم الأعلى = ظل أكثر نعومة. |
| **OffsetX / OffsetY** | يحرك الظل أفقيًا/عموديًا. |
| **Transparency** | يجعل الظل أكثر أو أقل شفافية. |

فهم هذه سيساعدك على **إنشاء ظل ناعم** يبدو طبيعيًا.

## كيفية إضافة ظل إلى شكل

أولًا وقبل كل شيء – تحتاج إلى نسخة من الشكل. أدناه إعداد بسيط باستخدام Aspose.Slides، لكن النمط نفسه يعمل مع معظم مكتبات الرسوميات .NET.

```csharp
using Aspose.Slides;
using Aspose.Slides.Export;
using System.Drawing;

// Create a new presentation and add a blank slide
Presentation pres = new Presentation();
ISlide slide = pres.Slides[0];

// Add a rectangle shape (our canvas for the shadow)
IShape rect = slide.Shapes.AddAutoShape(ShapeType.Rectangle, 100, 100, 300, 150);
rect.FillFormat.FillType = FillType.Solid;
rect.FillFormat.SolidFillColor = Color.LightBlue;
rect.LineFormat.Width = 2;
rect.LineFormat.FillFormat.SolidFillColor = Color.DarkBlue;
```

> **نصيحة احترافية:** اختر شكلاً له تعبئة مرئية؛ وإلا قد يختفي الظل خلف خلفية شفافة.

الآن بعد أن لدينا `rect`، يمكننا **إضافة ظل الشكل** عبر الوصول إلى `ShadowFormat` الخاص به:

```csharp
// Step 1: Obtain the shape you want to modify (already done above)
// Step 2: Access the shape's shadow formatting object
ShadowFormat shadow = rect.ShadowFormat;

// Step 3: Enable the shadow and set basic properties
shadow.Visible = true;                 // Turn the shadow on
shadow.Type = ShadowType.Inner;        // You can also use Outer, Perspective, etc.
shadow.Color = Color.Black;           // Classic black shadow
shadow.OffsetX = 5;                    // 5 points to the right
shadow.OffsetY = 5;                    // 5 points down
```

في هذه المرحلة سيحصل المستطيل على ظل حاد ومحدد. إذا شغلت العرض، سترى **إضافة تأثير الظل** التي تكون أكثر عملية من مجرد زخرفة.

## كيفية ضبط الضبابية لظل ناعم

الحافة الصلبة قد تبدو رخيصة، خاصة على شاشات عالية الدقة DPI. هنا يأتي دور **كيفية ضبط الضبابية**. خاصية `BlurRadius` تقبل قيمة `float` تمثل نصف القطر بالنقاط.

```csharp
// Step 4: Set the blur radius to create a soft shadow
shadow.BlurRadius = 5.0f;   // 5 points gives a subtle, soft look
```

لماذا `5.0f`؟ عمليًا، القيم بين `3.0f` و `8.0f` تنتج ظلًا ناعمًا طبيعيًا لمعظم عناصر الواجهة. أي قيمة أعلى تبدأ تبدو كتوّهّج بدلاً من الظل.

يمكنك أيضًا تعديل الشفافية لجعل الظل أقل حدة:

```csharp
shadow.Transparency = 0.4f; // 40% transparent – looks lighter
```

الآن لقد **أضفت تأثير الظل** الذي يكون مرئيًا ولطيفًا. احفظ الملف لرؤية النتيجة:

```csharp
pres.Save("AddShadowEffect.pptx", SaveFormat.Pptx);
```

افتح `AddShadowEffect.pptx` في PowerPoint أو أي عارض، وسترى مستطيلًا بإزاحة ضبابية جميلة – مثال تقليدي على **إنشاء ظل ناعم**.

## إنشاء ظل ناعم بإعدادات مخصصة

أحيانًا تحتاج إلى تحكم فني أكبر. فيما يلي طريقة مساعدة تجمع الإعدادات الشائعة في استدعاء واحد. لا تتردد في نسخها إلى فئة الأدوات.

```csharp
/// <summary>
/// Applies a customizable soft shadow to any IShape.
/// </summary>
public static void ApplySoftShadow(IShape shape, float offsetX = 5f, float offsetY = 5f,
                                   float blur = 6f, Color? color = null, float transparency = 0.35f)
{
    if (shape == null) throw new ArgumentNullException(nameof(shape));

    ShadowFormat sf = shape.ShadowFormat;
    sf.Visible = true;
    sf.Type = ShadowType.Outer;
    sf.OffsetX = offsetX;
    sf.OffsetY = offsetY;
    sf.BlurRadius = blur;
    sf.Color = color ?? Color.Black;
    sf.Transparency = transparency;
}
```

استخدمها هكذا:

```csharp
ApplySoftShadow(rect, offsetX: 8, offsetY: 8, blur: 7, color: Color.DarkSlateGray);
```

تتيح لك الطريقة **إضافة ظل الشكل** بسطر واحد، مما يحافظ على نظافة الكود الرئيسي. كما أنها توضح *كيفية إضافة الظل* بطريقة قابلة لإعادة الاستخدام – ممارسة تتوسع جيدًا عندما يكون لديك العشرات من الأشكال.

## إضافة ظل الشكل – مثال كامل يعمل

فيما يلي برنامج مستقل يمكنك تجميعه وتشغيله. ينشئ عرضًا تقديميًا، يضيف ثلاثة مستطيلات، كل منها بإعداد ظل مختلف، ويحفظ الملف.

```csharp
using Aspose.Slides;
using Aspose.Slides.Export;
using System;
using System.Drawing;

namespace ShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Initialize presentation
            Presentation pres = new Presentation();
            ISlide slide = pres.Slides[0];

            // Rectangle 1 – basic shadow
            IShape rect1 = slide.Shapes.AddAutoShape(ShapeType.Rectangle, 50, 50, 200, 100);
            rect1.FillFormat.SolidFillColor = Color.LightCoral;
            ApplyShadow(rect1, blur: 3f, offsetX: 4, offsetY: 4, transparency: 0.2f);

            // Rectangle 2 – soft shadow (our main focus)
            IShape rect2 = slide.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 50, 200, 100);
            rect2.FillFormat.SolidFillColor = Color.LightGreen;
            ApplyShadow(rect2, blur: 6f, offsetX: 6, offsetY: 6, transparency: 0.4f);

            // Rectangle 3 – heavy blur for a glow effect
            IShape rect3 = slide.Shapes.AddAutoShape(ShapeType.Rectangle, 550, 50, 200, 100);
            rect3.FillFormat.SolidFillColor = Color.LightSkyBlue;
            ApplyShadow(rect3, blur: 12f, offsetX: 0, offsetY: 0, transparency: 0.6f, color: Color.DarkBlue);

            // Save the result
            pres.Save("ShadowDemo.pptx", SaveFormat.Pptx);
            Console.WriteLine("Presentation created – open ShadowDemo.pptx to see the add shadow effect.");
        }

        // Reusable helper (same as earlier)
        public static void ApplyShadow(IShape shape, float offsetX = 5f, float offsetY = 5f,
                                       float blur = 5f, Color? color = null, float transparency = 0.35f)
        {
            ShadowFormat sf = shape.ShadowFormat;
            sf.Visible = true;
            sf.Type = ShadowType.Outer;
            sf.OffsetX = offsetX;
            sf.OffsetY = offsetY;
            sf.BlurRadius = blur;
            sf.Color = color ?? Color.Black;
            sf.Transparency = transparency;
        }
    }
}
```

**الناتج المتوقع:** عند فتح *ShadowDemo.pptx*، سترى ثلاثة مستطيلات. يوضح الأوسط التقنية الكلاسيكية **إنشاء ظل ناعم** مع ضبابية وإزاحة معتدلة، بينما تُظهر الأخرى تنوعًا أخف وأثقل.

![مثال على إضافة تأثير الظل](shadow-example.png "مثال على إضافة تأثير الظل")

*نص بديل للصورة:* مثال على إضافة تأثير الظل

## المشكلات الشائعة والنصائح

- **الظل غير ظاهر؟** تأكد من أن `ShadowFormat.Visible` مضبوط على `true`. بعض المكتبات تكون الظلال غير مرئية افتراضيًا.
- **الضبابية تبدو شديدة.** قلل `BlurRadius` أو زد `Transparency`. قيمة `0.4f` للشفافية عادةً ما تخفف المظهر.
- **مخاوف الأداء.** رسم العديد من الظلال قد يبطئ إعادة رسم واجهة المستخدم. خزن النتيجة مؤقتًا إذا كنت ترسم داخل حلقة.
- **ظلال متعددة.** معظم واجهات API تدعم ظلًا واحدًا فقط لكل شكل. لمحاكاة ظلال متعددة، قم بنسخ الشكل، أزح كل نسخة، وارسمها بالترتيب الصحيح.
- **مشكلات عبر المنصات.** إذا كنت تستهدف Xamarin أو MAUI، تحقق من توفر API الظل على المنصة المستهدفة؛ وإلا قد تحتاج إلى مُصمم مخصص.

## الخلاصة

أنت الآن تعرف بالضبط كيف **تضيف تأثير الظل** إلى الأشكال في C#. من الخطوات الأساسية لاسترجاع كائن `ShadowFormat` إلى ضبط الضبابية بدقة

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}