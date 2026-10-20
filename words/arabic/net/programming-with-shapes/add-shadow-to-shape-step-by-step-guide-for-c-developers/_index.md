---
category: general
date: 2026-02-21
description: أضف ظلًا إلى الشكل في C# وتعلم كيفية تخصيص الظل، وتطبيق تأثير الظل، وتعيين
  شفافية الظل مع مثال كامل قابل للتنفيذ.
draft: false
keywords:
- add shadow to shape
- how to customize shadow
- apply shadow effect
- how to add shadow
- set shadow opacity
language: ar
og_description: أضف ظلًا إلى الشكل في C# باستخدام هذا الدليل. تعلم كيفية تخصيص الظل،
  تطبيق تأثير الظل، وضبط شفافية الظل ببضع أسطر من الشيفرة فقط.
og_title: إضافة ظل إلى الشكل – دورة شاملة في C#
tags:
- C#
- Aspose.Words
- Graphics
- Shadow Effect
title: إضافة ظل إلى الشكل – دليل خطوة بخطوة لمطوري C#
url: /ar/net/programming-with-shapes/add-shadow-to-shape-step-by-step-guide-for-c-developers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة ظل إلى الشكل – دليل C# كامل

هل احتجت يومًا إلى **إضافة ظل إلى الشكل** في مستند Word لكنك لم تكن متأكدًا من أين تبدأ؟ لست وحدك — كثير من المطورين يواجهون هذه المشكلة عند صقل التقارير أو النشرات التسويقية. الخبر السار؟ في بضع خطوات فقط يمكنك تحويل مستطيل مسطح إلى عنصر مصقول ثلاثي الأبعاد يبرز من الصفحة.

في هذا الدليل سنستعرض **مثالًا كاملاً وقابلاً للتنفيذ** يوضح لك كيفية تخصيص الظل، تطبيق تأثير الظل، وحتى ضبط شفافية الظل لأي شكل. في النهاية ستحصل على مقتطف يمكن إعادة استخدامه في أي مشروع Aspose.Words، دون الحاجة إلى مراجع غامضة.

## المتطلبات المسبقة

* **.NET 6.0** (أو أحدث) مثبت – الكود يعمل أيضًا مع .NET Framework 4.6+.
* حزمة **Aspose.Words for .NET** عبر NuGet – يُنصح بالإصدار 23.9 أو أحدث.
* فهم أساسي للغة C# ومبادئ البرمجة الكائنية.

إذا كنت تفتقد حزمة NuGet، نفّذ:

```bash
dotnet add package Aspose.Words
```

الآن بعد أن تم إعداد الأساس، لنبدأ العمل.

## الخطوة 1 – تحميل أو إنشاء مستند واسترجاع الشكل الأول

أول شيء نحتاجه هو كائن `Document` يحتوي فعليًا على شكل. لأغراض المثال سننشئ مستندًا جديدًا، ندرج مستطيلًا بسيطًا، ثم نسترجعه.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Create a blank document
        Document doc = new Document();

        // 2️⃣ Add a new shape (a rectangle) to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle);
        rect.Width = 150;
        rect.Height = 100;
        rect.WrapType = WrapType.Inline;
        rect.StrokeColor = Color.DarkBlue;
        rect.FillColor = Color.LightBlue;
        rect.StrokeWeight = 2.0;

        // Insert the shape into the document body
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Retrieve the shape we just added (demonstrates add shadow to shape)
        Shape firstShape = doc.GetChild(NodeType.Shape, 0, true) as Shape;
        if (firstShape == null)
        {
            Console.WriteLine("No shape found – aborting.");
            return;
        }

        // The remaining steps modify the shadow of firstShape
```

**لماذا نفعل ذلك:**  
استرجاع الشكل عبر `GetChild` يحاكي السيناريوهات الواقعية حيث يكون الشكل موجودًا مسبقًا (مثلًا، تم تحميله من قالب). كما يضمن أن كود الظل التالي يعمل على كائن صالح، متجنبًا استثناءات الإشارة إلى null.

> **نصيحة محترف:** إذا كنت تتعامل مع عدة أشكال، استخدم `GetChild(NodeType.Shape, index, true)` أو تكرّر عبر `doc.GetChildNodes(NodeType.Shape, true)`.

## الخطوة 2 – تشغيل تأثير الظل

ظل الشكل يكون معطَّلًا بشكل افتراضي. تمكينه هو الشرط الأول لأي تخصيص لاحق.

```csharp
        // 4️⃣ Enable the shadow
        firstShape.Shadow.Enabled = true;
```

**لماذا هذا مهم:**  
بدون ضبط `Enabled = true`، أي تغييرات لاحقة في الخصائص (اللون، الضبابية، الإزاحة) ستُهمل. فكر فيها كتشغيل مفتاح الضوء قبل أن تتمكن من تعديل سطوع المصباح.

## الخطوة 3 – اختيار لون الظل (ولماذا الأسود هو نقطة بداية جيدة)

اختيار اللون يؤثر بشكل كبير على الإحساس بالعمق. الأسود (أو الرمادي الداكن جدًا) هو الأكثر شيوعًا لأنه يناسب أي خلفية.

```csharp
        // 5️⃣ Set the shadow color – black gives a classic look
        firstShape.Shadow.Color = Color.Black;
```

**بديل:**  
إذا كان مستندك يحتوي على خلفية داكنة، جرّب درجة أفتح:

```csharp
        // firstShape.Shadow.Color = Color.FromArgb(150, 150, 150); // light gray
```

## الخطوة 4 – تعيين شفافية الظل

تُعبّر الشفافية عن قيمة بين `0.0` (شفاف تمامًا) و`1.0` (معتم تمامًا). ظل شفاف بنسبة 40 % يبدو طبيعيًا لمعظم تصاميم واجهات المستخدم.

```csharp
        // 6️⃣ Make the shadow 40 % transparent
        firstShape.Shadow.Transparency = 0.4; // 0 = opaque, 1 = invisible
```

**كيفية التخصيص:**  
- **أكثر هدوءًا:** `0.2` (شفافية 20 %)  
- **خفيف جدًا:** `0.7` (شفافية 70 %)

## الخطوة 5 – تعريف الضبابية ونعومة الحواف

الضبابية تتحكم في مدى نعومة حواف الظل. قيمة `4.0` تعمل جيدًا للأشكال المتوسطة الحجم.

```csharp
        // 7️⃣ Soften the edges with a blur radius
        firstShape.Shadow.Blur = 4.0;
```

**حالات حافة:**  
إذا ضبطت `Blur` على `0`، يصبح الظل صورة ظلية ذات حواف صلبة، ما قد يبدو قاسيًا. وعلى العكس، القيم فوق `10` قد تجعل الظل يبدو كتوّهج.

## الخطوة 6 – تحديد موضع الظل بالنسبة إلى الشكل

قِيَم الإزاحة تحرك الظل أفقيًا (`OffsetX`) وعموديًا (`OffsetY`). الأرقام الموجبة تحرك الظل إلى الأسفل وإلى اليمين.

```csharp
        // 8️⃣ Position the shadow 5 points right and 5 points down
        firstShape.Shadow.OffsetX = 5;
        firstShape.Shadow.OffsetY = 5;
```

**تجربة:**  
- **ظل سفلي:** `OffsetX = 0`، `OffsetY = 10`  
- **تأثير مرتفع:** `OffsetX = -5`، `OffsetY = -5`

## الخطوة 7 – حفظ والتحقق من النتيجة

أخيرًا، احفظ المستند على القرص وافتحه في Microsoft Word (أو أي عارض متوافق) لتشاهد الظل يعمل.

```csharp
        // 9️⃣ Save the document
        string outPath = "ShadowedShape.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}. Open it to see the shadow.");
    }
}
```

عند فتح **ShadowedShape.docx**، يجب أن ترى مستطيلًا أزرق فاتح مع ظل أسود ناعم شبه شفاف مُزاح بخمس نقاط. إذا لم يظهر الظل، تأكد من أن `firstShape.Shadow.Enabled` يساوي `true` وأنك تستخدم نسخة حديثة من Aspose.Words.

### الكود الكامل (جاهز للنسخ واللصق)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class ShadowDemo
{
    static void Main()
    {
        Document doc = new Document();
        Shape rect = new Shape(doc, ShapeType.Rectangle);
        rect.Width = 150;
        rect.Height = 100;
        rect.WrapType = WrapType.Inline;
        rect.StrokeColor = Color.DarkBlue;
        rect.FillColor = Color.LightBlue;
        rect.StrokeWeight = 2.0;
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        Shape firstShape = doc.GetChild(NodeType.Shape, 0, true) as Shape;
        if (firstShape == null)
        {
            Console.WriteLine("No shape found – aborting.");
            return;
        }

        // Enable shadow
        firstShape.Shadow.Enabled = true;

        // Choose shadow color
        firstShape.Shadow.Color = Color.Black;

        // Set opacity (40 % transparent)
        firstShape.Shadow.Transparency = 0.4;

        // Soften edges
        firstShape.Shadow.Blur = 4.0;

        // Position shadow
        firstShape.Shadow.OffsetX = 5;
        firstShape.Shadow.OffsetY = 5;

        // Save document
        string outPath = "ShadowedShape.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}. Open it to see the shadow.");
    }
}
```

## أسئلة شائعة وحالات حافة

| السؤال | الجواب |
|----------|--------|
| **ماذا لو كان الشكل صورة بدلاً من مستطيل؟** | تنطبق نفس خصائص الظل؛ فقط تأكد من أن `ShapeType` للشكل هو `Picture`. |
| **هل يمكنني تحريك الظل؟** | لا تدعم Aspose.Words التحريك، لكن يمكنك إنشاء صفحات متعددة بإزاحات تدريجية واستخدام PowerPoint للتحريك. |
| **هل يعمل الظل في تصدير PDF؟** | نعم. عند حفظ المستند كملف PDF (`doc.Save("out.pdf")`)، تحتفظ Aspose.Words بتأثير الظل. |
| **كيف أزيل الظل لاحقًا؟** | اضبط `firstShape.Shadow.Enabled = false;` أو ببساطة عيّن `firstShape.Shadow = null`. |
| **هل هناك حد لقيم الضبابية؟** | عمليًا، القيم فوق `15` تجعل الظل يبدو كهالة وقد تزيد من حجم الملف. |

## الخطوات التالية – استمر في التقدم

الآن بعد أن عرفت **كيفية إضافة الظل** و**ضبط شفافية الظل**، فكر في استكشاف ما يلي:

* **كيفية تخصيص الظل** أكثر باستخدام `Shadow.Distance` للحصول على إزاحة أكثر وضوحًا.
* **تطبيق تأثير الظل** على إطارات النص أو WordArt لتصاميم مستندات أغنى.
* **دمج ظلال متعددة** (مثلًا، داخلية + خارجية) للحصول على مظهر طبقي.
* **تصدير إلى HTML** وملاحظة كيف يعكس CSS `box‑shadow` نفس الإعدادات.

إذا كنت تبني مولد تقارير، أضف ظلالًا إلى العناوين، المخططات، أو صناديق التوضيح لتوجيه نظر القارئ. جرّب ألوانًا وشفافات مختلفة — ربما ظل أزرق خفيف لثيم مؤسسي.

---

### ملخص سريع

استعرضنا **مثالًا كاملاً ومستقلاً** يوضح كيفية **إضافة ظل إلى الشكل**، **تخصيص الظل**، **تطبيق تأثير الظل**، و**ضبط شفافية الظل** باستخدام Aspose.Words في C#. الكود جاهز للتنفيذ، والشروحات تغطي كلًا من *ما* و*لماذا*، وأصبح لديك الآن أساس قوي لتنسيق الأشكال في أي مشروع أتمتة Word.

برمجة سعيدة، ولتكن مستنداتك دائمًا ذات لمسة ثلاثية الأبعاد إضافية!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}