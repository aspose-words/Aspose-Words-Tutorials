---
category: general
date: 2026-06-20
description: أضف ظلًا إلى الشكل بسرعة وتعلم كيفية تغيير شفافية الظل، إضافة ظل الشكل،
  وتطبيق ظل ضبابي باستخدام Aspose.Words لـ .NET.
draft: false
keywords:
- add shadow to shape
- how to change shadow transparency
- how to add shape shadow
- how to apply blur shadow
language: ar
og_description: أضف ظلًا إلى الشكل في ملف Word، وتعرّف على كيفية تغيير شفافية الظل،
  وإضافة ظل للشكل، وتطبيق ظل ضبابي مع أمثلة شفرة واضحة.
og_title: إضافة ظل إلى الشكل – دليل C# خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Add shadow to shape quickly and learn how to change shadow transparency,
    add shape shadow, and apply blur shadow using Aspose.Words for .NET.
  headline: Add Shadow to Shape in Word Documents – Complete C# Guide
  type: TechArticle
- description: Add shadow to shape quickly and learn how to change shadow transparency,
    add shape shadow, and apply blur shadow using Aspose.Words for .NET.
  name: Add Shadow to Shape in Word Documents – Complete C# Guide
  steps:
  - name: What if the shape has no existing shadow object?
    text: Aspose.Words automatically creates a `Shadow` object when you first access
      `targetShape.Shadow`. No extra initialization is required.
  - name: Does this work with other shape types, like circles or pictures?
    text: Absolutely. The shadow API is shape‑agnostic. Just retrieve the appropriate
      `Shape` node, and the same properties apply.
  - name: How to make the shadow invisible again?
    text: Set `targetShape.Shadow.Visible = false;` or simply omit the shadow configuration.
  - name: Compatibility with older .NET versions?
    text: The code uses only features available in Aspose.Words 23.x and .NET Standard
      2.0+, so it runs on .NET Framework 4.6.1 and newer.
  type: HowTo
tags:
- Aspose.Words
- C#
- Document Automation
- Shapes
title: إضافة ظل إلى الشكل في مستندات Word – دليل C# الكامل
url: /ar/net/programming-with-shapes/add-shadow-to-shape-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة ظل إلى الشكل في مستندات Word – دليل C# كامل

هل تساءلت يوماً كيف **تضيف ظلًا إلى الشكل** في ملف Word دون الحاجة إلى التعامل مع الواجهة الرسومية؟ لست وحدك. يحتاج العديد من المطورين إلى تحسين مظهر المستند برمجياً، والخبر السار هو أن Aspose.Words يجعل ذلك سهلًا للغاية.

في هذا البرنامج التعليمي سنستعرض الخطوات الدقيقة **لإضافة ظل إلى الشكل**، ونوضح **كيفية تغيير شفافية الظل**، ونغطي **كيفية إضافة ظل للشكل** في سيناريوهات مختلفة، بل ونشرح **كيفية تطبيق ظل ضبابي** للحصول على تأثير عمق احترافي. في النهاية ستحصل على مقتطف يمكن إعادة استخدامه في أي مشروع .NET.

## ما ستتعلمه

- تحميل ملف DOCX، تحديد الشكل، وتكوين خصائص الظل الخاصة به.
- تعديل شفافية الظل باستخدام `Transparency`.
- تطبيق الضباب والإزاحة لإنشاء ظل واقعي.
- حفظ المستند المعدل والتحقق من النتيجة.
- نصائح للتعامل مع أشكال متعددة، أنواع أشكال مختلفة، وحالات الحافة.

> **المتطلبات المسبقة:** .NET 6 أو أحدث، Aspose.Words for .NET (حزمة NuGet `Aspose.Words`)، وفهم أساسي للغة C#. لا تحتاج إلى أدوات واجهة مستخدم.

![add shadow to shape example](image.png){ alt="مثال على إضافة ظل إلى الشكل" }

## الخطوة 1: إعداد المشروع وتحميل المستند

قبل أن تتمكن من **إضافة ظل إلى الشكل**، تحتاج إلى كائن مستند للعمل معه. هذه الخطوة بسيطة لكنها أساسية—بدون تحميل الملف لا شيء لتعديله.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load an existing DOCX that already contains a shape (e.g., a rectangle)
Document document = new Document(@"C:\Docs\input.docx");
```

*لماذا هذا مهم:*  
`Document` هو نقطة الدخول لجميع عمليات Aspose.Words. بتحميل الملف مبكرًا، تضمن أن أي تعديل لاحق على الشكل سيُجرى على شجرة العقد الصحيحة.

## الخطوة 2: استرجاع الشكل المستهدف

الآن بعد أن أصبح المستند في الذاكرة، نحتاج إلى تحديد الشكل الذي نريد تحسينه. إذا كان لديك عدة أشكال، يمكنك تعديل الفهرس أو استخدام محدد أكثر تعقيدًا.

```csharp
// Grab the first shape in the document – change the index if needed
Shape targetShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
```

> **نصيحة:** استخدم `document.GetChild(NodeType.Shape, index, true)` للبحث بشكل متكرر. إذا كنت تحتاج إلى شكل محدد بالاسم، تحقق من `targetShape.Name`.

## الخطوة 3: تفعيل الظل وتعيين لونه الأساسي

لن يظهر الظل إلا إذا كان مرئيًا وله لون. لنمنحه لونًا رماديًا داكنًا خفيفًا يعمل جيدًا على الخلفيات الفاتحة.

```csharp
// Make sure the shadow is turned on
targetShape.Shadow.Visible = true;

// Choose a neutral color for the shadow
targetShape.Shadow.Color = Color.DarkGray;
```

*شرح:*  
تعيين `Visible` إلى `true` يُفعِّل التأثير، بينما `Color.DarkGray` يوفر نغمة محايدة لا تتعارض مع معظم سمات المستند.

## الخطوة 4: كيفية تغيير شفافية الظل

الشفافية هي المفتاح لجعل الظل يبدو طبيعيًا. القيمة `0` تعني غير شفاف تمامًا؛ `1` يعني غير مرئي تمامًا. إليك كيفية **تغيير شفافية الظل** إلى 30 %:

```csharp
// 30 % transparent (0.3 means 30 % see‑through)
targetShape.Shadow.Transparency = 0.3;
```

*لماذا 0.3؟*  
ظل شفاف بنسبة 30 % يحاكي الإضاءة الواقعية دون أن يغمر حواف الشكل. يمكنك التجربة—`0.5` يعطي مظهرًا أكثر نعومة، بينما `0.1` يجعل الظل أكثر وضوحًا.

## الخطوة 5: كيفية تطبيق ظل ضبابي لإضفاء عمق

ظل حاد الحواف يبدو مسطحًا. إضافة الضباب تمنحه عمقًا. هنا نجيب على سؤال **كيفية تطبيق ظل ضبابي** في الكود.

```csharp
// Define the blur radius (in points). Larger values = softer shadow.
targetShape.Shadow.BlurRadius = 5;   // 5 pt blur

// Offset determines where the shadow falls relative to the shape.
targetShape.Shadow.OffsetX = 3;      // 3 pt to the right
targetShape.Shadow.OffsetY = 3;      // 3 pt downwards
```

*ما الذي يحدث؟*  
`BlurRadius` ينعّم الحواف، بينما `OffsetX/Y` يحدد موضع الظل كما لو أن مصدر الضوء يقع أعلى اليسار. عدّل هذه القيم لتتناسب مع لغة التصميم الخاصة بك.

## الخطوة 6: كيفية إضافة ظل الشكل إلى عدة أشكال (اختياري)

إذا كان المستند يحتوي على عدة أشكال، ربما تريد **إضافة ظل الشكل** لكل منها. حلقة بسيطة تقوم بالمهمة:

```csharp
// Iterate over every shape in the document
foreach (Shape shape in document.GetChildNodes(NodeType.Shape, true))
{
    shape.Shadow.Visible = true;
    shape.Shadow.Color = Color.DarkGray;
    shape.Shadow.Transparency = 0.3;
    shape.Shadow.BlurRadius = 5;
    shape.Shadow.OffsetX = 3;
    shape.Shadow.OffsetY = 3;
}
```

*نصيحة احترافية:*  
إذا كنت تريد التأثير فقط على المستطيلات، تحقق من `shape.ShapeType == ShapeType.Rectangle` داخل الحلقة.

## الخطوة 7: حفظ المستند المعدل

اكتملت جميع العمليات الثقيلة—الآن احفظ التغييرات. يمكنك استبدال الملف الأصلي أو الكتابة إلى موقع جديد.

```csharp
// Save to a new file to keep the original untouched
document.Save(@"C:\Docs\output.docx");
```

عند فتح `output.docx` في Word، سترى المستطيل (أو أي شكل استهدفته) يحمل ظلًا خفيفًا، شبه شفاف، ومضببًا.

## أسئلة شائعة وحالات حافة

### ماذا لو لم يكن لدى الشكل كائن ظل موجود مسبقًا؟
Aspose.Words ينشئ كائن `Shadow` تلقائيًا عند أول وصول لك إلى `targetShape.Shadow`. لا تحتاج إلى تهيئة إضافية.

### هل يعمل هذا مع أنواع أشكال أخرى، مثل الدوائر أو الصور؟
بالطبع. واجهة برمجة الظل لا تهم نوع الشكل. فقط استرجع عقدة `Shape` المناسبة، وستطبق نفس الخصائص.

### كيف أجعل الظل غير مرئي مرة أخرى؟
عيّن `targetShape.Shadow.Visible = false;` أو ببساطة لا تقم بتكوين الظل.

### التوافق مع إصدارات .NET القديمة؟
الكود يستخدم فقط الميزات المتوفرة في Aspose.Words 23.x و .NET Standard 2.0+، لذا يعمل على .NET Framework 4.6.1 وما بعده.

## مثال كامل يعمل

إليك البرنامج الكامل الجاهز للتنفيذ الذي يجمع كل شيء معًا:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load the document that contains the shape
        Document doc = new Document(@"C:\Docs\input.docx");

        // Retrieve the first shape (e.g., a rectangle) from the document
        Shape rect = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        // Enable shadow and set its basic properties
        rect.Shadow.Visible = true;
        rect.Shadow.Color = Color.DarkGray;

        // How to change shadow transparency – 30 % transparent
        rect.Shadow.Transparency = 0.3;

        // How to apply blur shadow – add depth with blur and offset
        rect.Shadow.BlurRadius = 5;   // 5 pt blur radius
        rect.Shadow.OffsetX = 3;      // horizontal offset
        rect.Shadow.OffsetY = 3;      // vertical offset

        // Save the modified document
        doc.Save(@"C:\Docs\output.docx");
    }
}
```

**الناتج المتوقع:** افتح `output.docx` وسترى المستطيل الأصلي الآن مُظهرًا بظل رمادي داكن، شفاف بنسبة 30 %، ومضببًا مع إزاحة طفيفة إلى أسفل‑يمين.

## الخلاصة

غطينا كل ما تحتاجه **لإضافة ظل إلى الشكل** برمجيًا، من تحميل الملف إلى تعديل الشفافية والضباب. الآن تعرف **كيفية تغيير شفافية الظل**، **كيفية إضافة ظل الشكل** عبر عناصر متعددة، و**كيفية تطبيق ظل ضبابي** للحصول على مظهر مصقول.

هل أنت مستعد للخطوة التالية؟ جرّب التجربة مع:

- ألوان ظل مختلفة (`Color.Black`, `Color.FromArgb(128, 0, 0, 0)`) لتأثيرات أغمق.
- إزاحات ديناميكية بناءً على حجم الشكل للحفاظ على النسبة.
- دمج الظلال مع التدرجات أو الانعكاسات لتصميمات متقدمة.

لا تتردد في ترك تعليق إذا واجهت أي صعوبات، وبرمجة سعيدة!

## ماذا يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Add Group Shape](/words/english/net/programming-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}