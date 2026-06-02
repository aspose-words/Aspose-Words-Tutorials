---
category: general
date: 2026-06-02
description: كيفية إضافة الظل في C# باستخدام Aspose.Words – تعلم كيفية تغيير الشفافية،
  وتطبيق الضبابية على الظل، وتكوين ظل الشكل بسرعة.
draft: false
keywords:
- how to add shadow
- how to change transparency
- add shadow to shape
- apply blur to shadow
- configure shape shadow
language: ar
og_description: كيفية إضافة الظل في C# باستخدام Aspose.Words. يوضح لك هذا الدليل كيفية
  تغيير الشفافية، وتطبيق الضبابية على الظل، وتكوين ظل الشكل بسهولة.
og_title: كيفية إضافة ظل إلى أشكال Word في C# – خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: How to add shadow in C# with Aspose.Words – learn how to change transparency,
    apply blur to shadow and configure shape shadow quickly.
  headline: How to Add Shadow to Word Shapes in C# – Complete Guide
  type: TechArticle
- description: How to add shadow in C# with Aspose.Words – learn how to change transparency,
    apply blur to shadow and configure shape shadow quickly.
  name: How to Add Shadow to Word Shapes in C# – Complete Guide
  steps:
  - name: What Each Property Does
    text: '| Property | Purpose | Typical Values | |----------|---------|----------------|
      | `Visible` | Turns the shadow on or off. | `true` / `false` | | `Transparency`
      | Controls opacity. | `0.0` (opaque) – `1.0` (transparent) | | `BlurRadius`
      | Softens the edges of the shadow. | `0` (sharp) – `10+` (very s'
  - name: Expected Result
    text: '- The shape appears lifted off the page. - The shadow is 25 % transparent,
      allowing underlying text to show through faintly. - A soft blur makes the shadow
      look realistic rather than a harsh silhouette. - The offset is noticeable but
      not overwhelming, giving a professional finish.'
  - name: Adding Shadow to Multiple Shapes
    text: 'If your document contains several shapes, loop through them:'
  - name: Changing Shadow Colour Dynamically
    text: 'You can tie the shadow colour to the shape’s fill colour for a cohesive
      look:'
  - name: Handling Shapes Without Existing ShadowFormat
    text: All shapes expose a `ShadowFormat`, even if the shadow is initially invisible.
      No special handling is required—just set `Visible = true`.
  - name: Performance Considerations
    text: When processing large documents (hundreds of pages), avoid loading the entire
      file into memory repeatedly. Load once, apply all shadow changes in a single
      pass, then save. Aspose.Words is optimized for such batch operations.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
- Shadow Effects
title: كيفية إضافة الظل إلى أشكال Word في C# – دليل شامل
url: /ar/net/programming-with-shapes/how-to-add-shadow-to-word-shapes-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إضافة ظل إلى أشكال Word باستخدام C# – دليل شامل

هل تساءلت يومًا **كيف تضيف ظلًا** إلى شكل Word باستخدام C#؟ لست وحدك—المطورون الذين يبنون تقارير، فواتير، أو منشورات تسويقية غالبًا ما يحتاجون إلى ذلك العمق الخفيف لجعل رسوماتهم تبرز. في هذا البرنامج التعليمي سنستعرض مثالًا عمليًا لا يوضح فقط **كيفية إضافة الظل** بل يوضح أيضًا **كيفية تغيير الشفافية**، **تطبيق تمويه على الظل**، و**تهيئة خصائص ظل الشكل** باستخدام Aspose.Words.

بنهاية هذا الدليل ستحصل على مستند Word يعمل بالكامل حيث يحتوي الشكل على ظل شبه شفاف واقعي. لا أدوات خارجية غامضة، فقط كود C# نظيف يمكنك إدراجه في أي مشروع .NET.

## المتطلبات المسبقة

قبل أن نبدأ، تأكد من أن لديك ما يلي جاهزًا:

- .NET 6.0 أو أحدث (الكود يعمل أيضًا على .NET Framework 4.7+).
- Aspose.Words for .NET (حزمة NuGet `Aspose.Words` الإصدار 23.9 أو أحدث).
- ملف `.docx` بسيط يحتوي بالفعل على شكل واحد على الأقل (مثل مستطيل أو شكل تلقائي).
- Visual Studio 2022 أو أي بيئة تطوير تفضلها.

هذا كل ما تحتاجه—لا شيء معقد، فقط الأساسيات التي لديك على الأرجح بالفعل.

## الخطوة 1: تحميل مستند Word الذي يحتوي على شكل

أول شيء نحتاجه هو فتح المستند الموجود. فكر في ذلك كتحميل لوحة قبل أن تبدأ برسم الظل.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load a Word document that already contains a shape.
Document doc = new Document(@"C:\Docs\input.docx");
```

> **لماذا هذا مهم:** `Document` هو نقطة الدخول لجميع عمليات Aspose.Words. تحميل الملف يمنحنا الوصول إلى كل عقدة، بما في ذلك الأشكال، الفقرات، الجداول، وأكثر.

## الخطوة 2: استرجاع الشكل المستهدف

إذا كان المستند يحتوي على عدة أشكال، يمكنك تحديد الشكل الذي تحتاجه عن طريق الفهرس، الاسم، أو حتى النوع. للتبسيط، سنأخذ الشكل الأول.

```csharp
// Retrieve the first shape in the document.
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
```

> **نصيحة:** استخدم `doc.GetChild(NodeType.Shape, index, true)` عندما تعرف الترتيب، أو قم بالتكرار عبر `doc.GetChildNodes(NodeType.Shape, true)` لسيناريوهات أكثر تعقيدًا.

## الخطوة 3: الوصول إلى ShadowFormat الخاص بالشكل

كل شكل يمتلك كائن `ShadowFormat` يتحكم في مظهر الظل. هنا سنطبق كل السحر.

```csharp
// Access the shape's shadow format.
ShadowFormat shadow = shape.ShadowFormat;
```

> **نصيحة احترافية:** كائن `ShadowFormat` خفيف الوزن؛ يمكنك تعديلّه عدة مرات قبل الحفظ، وستنعكس التغييرات فورًا.

## الخطوة 4: تهيئة مظهر الظل

الآن يأتي قلب الدرس—ضبط كل خاصية لتحقيق التأثير المطلوب. أدناه سن **نضيف ظلًا إلى الشكل**، نجعله **شفافًا بنسبة 25 %**، **نطبق تمويهًا على الظل**، ونضبط زاوية الإزاحة.

```csharp
// Show the shadow.
shadow.Visible = true;

// Set transparency – this is how to change transparency.
shadow.Transparency = 0.25; // 0 = opaque, 1 = fully transparent

// Apply a soft blur – this demonstrates how to apply blur to shadow.
shadow.BlurRadius = 5.0; // Measured in points

// Distance from the shape – controls how far the shadow is offset.
shadow.Distance = 3.0; // Points

// Angle determines the direction of the offset (0° = right, 90° = up).
shadow.Angle = 45.0; // Degrees

// Choose a colour for the shadow. Black works well for most cases.
shadow.Color = Color.Black;
```

### ما تقوم به كل خاصية

| الخاصية | الغرض | القيم النموذجية |
|----------|---------|----------------|
| `Visible` | تشغيل أو إيقاف الظل. | `true` / `false` |
| `Transparency` | التحكم في الشفافية. | `0.0` (معتم) – `1.0` (شفاف) |
| `BlurRadius` | تنعيم حواف الظل. | `0` (حاد) – `10+` (ناعم جدًا) |
| `Distance` | المسافة التي يُزاح الظل فيها عن الشكل. | `0` – `20` نقطة |
| `Angle` | اتجاه الإزاحة بالدرجات. | `0`–`360` |
| `Color` | لون الظل. | أي `System.Drawing.Color` |

> **لماذا هذه الإعدادات الافتراضية؟** زاوية 45° مع مسافة وتمويه معتدلين تعطي ظلًا طبيعيًا يناسب معظم المستندات التجارية.

## الخطوة 5: حفظ المستند المعدل

بعد تهيئة الظل، نقوم ببساطة بحفظ التغييرات.

```csharp
// Save the modified document.
doc.Save(@"C:\Docs\output.docx");
```

إذا فتحت `output.docx` في Microsoft Word، ستلاحظ أن الشكل الآن يمتلك ظلًا شبه شفاف ومُطمّع مائل بزاوية 45°—تمامًا ما قمنا بإعداده.

### النتيجة المتوقعة

- يبدو الشكل كأنه مرتفع عن الصفحة.
- الظل شفاف بنسبة 25 %، مما يسمح للنص الموجود تحته أن يظهر بخفوت.
- تمويه ناعم يجعل الظل يبدو واقعيًا بدلاً من silhouette حاد.
- الإزاحة ملحوظة ولكنها ليست مفرطة، مما يمنح مظهرًا احترافيًا.

![لقطة شاشة توضح كيفية إضافة ظل إلى شكل في مستند Word](https://example.com/images/add-shadow-to-shape.png "كيفية إضافة ظل إلى شكل في Word")

*نص بديل للصورة:* **لقطة شاشة توضح كيفية إضافة ظل إلى شكل في مستند Word** – هذا يلبي مباشرةً متطلبات SEO لنص بديل يحتوي على الكلمة المفتاحية الأساسية.

## الاختلافات الشائعة وحالات الحافة

### إضافة ظل إلى عدة أشكال

إذا كان المستند يحتوي على عدة أشكال، يمكنك تكرار العملية عبرها:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape s in shapes)
{
    ShadowFormat sf = s.ShadowFormat;
    sf.Visible = true;
    sf.Transparency = 0.3;
    sf.BlurRadius = 4.0;
    sf.Distance = 2.5;
    sf.Angle = 30.0;
    sf.Color = Color.Gray;
}
```

### تغيير لون الظل ديناميكيًا

يمكنك ربط لون الظل بلون تعبئة الشكل للحصول على مظهر متناسق:

```csharp
shadow.Color = Color.FromArgb(
    shape.FillFormat.ForeColor.R,
    shape.FillFormat.ForeColor.G,
    shape.FillFormat.ForeColor.B);
```

### التعامل مع أشكال لا تمتلك ShadowFormat موجودًا مسبقًا

جميع الأشكال تعرض كائن `ShadowFormat`، حتى وإن كان الظل غير مرئي في البداية. لا تحتاج إلى معالجة خاصة—فقط عيّن `Visible = true`.

### اعتبارات الأداء

عند معالجة مستندات كبيرة (مئات الصفحات)، تجنب تحميل الملف بالكامل إلى الذاكرة مرارًا وتكرارًا. حمّل مرة واحدة، طبّق جميع تغييرات الظل في مرور واحد، ثم احفظ. Aspose.Words مُحسّن لمثل هذه العمليات الدفعاتية.

## نصائح احترافية ومخاطر محتملة

- **نصيحة احترافية:** حافظ على `BlurRadius` أقل من 8 نقاط للمستندات المطبوعة؛ القيم الأعلى قد تتسبب في ظهور تشوهات rasterization في إصدارات Word القديمة.
- **احذر من:** ضبط `Transparency` إلى `1.0` يجعل الظل غير مرئي—تحقق من أنك تستخدم قيمة بين `0` و `1`.
- **تذكر:** يتم قياس `Angle` باتجاه عقارب الساعة من المحور الأفقي. إذا أردت ظلًا يظهر “أسفل” الشكل، استخدم زاوية تقريبًا `90` درجة.

## الخطوات التالية

الآن بعد أن عرفت **كيفية إضافة الظل** و**كيفية تغيير الشفافية**، قد ترغب في استكشاف المواضيع ذات الصلة:

- **إضافة تأثيرات انعكاس** إلى الأشكال (`shape.ReflectionFormat`).
- **تطبيق تعبئات تدرجية** للحصول على تنسيق بصري أغنى.
- **دمج عدة أشكال** في مجموعة واحدة وتطبيق ظل موحد.
- **تصدير المستند إلى PDF** مع الحفاظ على تأثيرات الظل (`doc.Save("output.pdf", SaveFormat.Pdf)`).

جميع هذه يبني على نفس المبادئ التي غطيناها لتكوين ظل الشكل.

## الخلاصة

استعرضنا مثالًا كاملاً وقابلًا للتنفيذ يوضح **كيفية إضافة ظل** إلى شكل Word باستخدام C#. من خلال الوصول إلى كائن `ShadowFormat` يمكنك **تغيير الشفافية**، **تطبيق تمويه على الظل**، وتكوين **ظل الشكل** بالكامل لتلبية أي متطلبات تصميم. الكود قصير، واضح، وجاهز للإدراج في مشاريعك—بدون مكتبات إضافية، بدون سحر.

جرّبه، عدّل القيم، وشاهد كيف يمكن لظل بسيط أن يمنح مستندات Word مظهرًا مصقولًا واحترافيًا. إذا واجهت أي مشاكل أو كان لديك أفكار لتوسعات، لا تتردد في مشاركتها في التعليقات. ترميز سعيد!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [How to Add Shadow in C# – Complete Programming Guide](/words/english/python-net/images-shapes/how-to-add-shadow-in-c-complete-programming-guide/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}