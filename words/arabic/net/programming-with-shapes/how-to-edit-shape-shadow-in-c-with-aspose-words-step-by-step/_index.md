---
category: general
date: 2026-02-20
description: كيفية تعديل ظل الشكل في C# باستخدام Aspose.Words. تعلم ضبط الضبابية،
  الإزاحة، الشفافية، ولون ظل الشكل بدقة من خلال أمثلة شفرة واضحة.
draft: false
keywords:
- how to edit shape shadow
- Aspose.Words shadow formatting
- C# shape shadow API
- document processing with Aspose
- shadow blur radius C#
language: ar
og_description: كيفية تعديل ظل الشكل في C# باستخدام Aspose.Words. يوضح لك هذا الدليل
  كيفية التحكم في الضبابية والمسافة والشفافية ولون ظل الشكل.
og_title: كيفية تعديل ظل الشكل في C# – دليل Aspose.Words الكامل
tags:
- Aspose.Words
- C#
- Document Automation
title: كيفية تعديل ظل الشكل في C# باستخدام Aspose.Words – دليل خطوة بخطوة
url: /ar/net/programming-with-shapes/how-to-edit-shape-shadow-in-c-with-aspose-words-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تعديل ظل الشكل في C# باستخدام Aspose.Words – دليل خطوة بخطوة

هل تساءلت يومًا **كيف تعدل ظل الشكل** في مستند Word دون فتح Word نفسه؟ لست وحدك—المطورون الذين يبنون تقارير آلية غالبًا ما يحتاجون إلى تعديل نمط الشكل بصريًا برمجيًا. الخبر السار؟ مع Aspose.Words for .NET يمكنك ضبط كل خاصية للظل في بضع أسطر من C# فقط.

في هذا الدرس سنستعرض تحميل مستند موجود، استخراج الشكل الأول، وضبط ظلّه بدقة (نصف قطر الضبابية، الإزاحة، الشفافية، اللون). في النهاية ستحصل على مقتطف قابل لإعادة الاستخدام يمكنك إدراجه في أي مشروع Aspose.Words. لا مراجع غامضة، فقط مثال كامل وجاهز للتنفيذ.

## ما ستتعلمه

- **المتطلبات المسبقة**: .NET 6+ (أو .NET Framework 4.7.2)، تثبيت Aspose.Words for .NET، ملف Word يحتوي على شكل واحد على الأقل.
- كيفية **استخراج شكل** من المستند باستخدام محدد `NodeType.Shape`.
- كيفية **تعديل خصائص الظل** باستخدام واجهة `ShadowFormat` السلسة.
- معالجة الحالات الاستثنائية عندما لا يُعثر على الشكل.
- التحقق من النتيجة بفتح الملف المحفوظ في Word.

> **نصيحة محترف:** إذا كنت بحاجة لتعديل عدة أشكال، ما عليك سوى تكرار `doc.GetChildNodes(NodeType.Shape, true)`—المنطق نفسه يُطبق.

---

## الخطوة 1: إعداد المشروع وإضافة Aspose.Words

قبل تشغيل أي كود، تأكد من الإشارة إلى حزمة NuGet الخاصة بـ Aspose.Words:

```bash
dotnet add package Aspose.Words
```

> **لماذا هذا مهم:** Aspose.Words يوفر الفئات `Document`، `Shape`، و`ShadowFormat` التي سنستخدمها. بدون الحزمة سيظهر خطأ “type or namespace not found” في المترجم.

### بنية المشروع

```
/MyShadowDemo
│   Program.cs
│   Shadow.docx   ← source file containing a shape with a default shadow
└─ /bin
```

---

## الخطوة 2: تحميل المستند الذي يحتوي على شكل

نبدأ بتحميل ملف Word. يقبل مُنشئ `Document` مسارًا أو تدفقًا، مما يجعله مرنًا للتخزين السحابي أو المحلي.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 👉 Replace with the actual path to your .docx file
        string inputPath  = @"YOUR_DIRECTORY\Shadow.docx";
        string outputPath = @"YOUR_DIRECTORY\ShadowFineTuned.docx";

        // Load the document – this reads the whole file into memory
        Document doc = new Document(inputPath);
```

**ما الذي يحدث؟** كائن `Document` الآن يمثل ملف Word بالكامل، مما يتيح لنا الوصول إلى كل عقدة (فقرات، جداول، أشكال، إلخ). التحميل سريع ولا يتطلب تثبيت Word على الخادم.

---

## الخطوة 3: استخراج أول شكل (مع فحص الأمان)

إذا لم يحتوي المستند على أي أشكال، يجب الخروج بأمان بدلاً من إلقاء استثناء `NullReferenceException`.

```csharp
        // Try to fetch the first shape in the document tree
        Shape shape = doc.GetChild(NodeType.Shape, 0, true) as Shape;

        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document. Exiting.");
            return; // Early exit – nothing to edit
        }
```

**لماذا نستخدم `GetChild(..., true)`** – العلم `true` يخبر Aspose.Words بالبحث بشكل متكرر، لذا تُؤخذ الأشكال المتداخلة داخل الجداول أو المجموعات في الاعتبار أيضًا.

---

## الخطوة 4: ضبط مظهر الظل بدقة

Aspose.Words يقدم واجهة API سلسة لإعدادات الظل. كل طريقة تُعيد كائن `ShadowFormat`، مما يسمح بسلسلة الاستدعاءات لقراءة أسهل.

```csharp
        // Adjust shadow parameters – all values are in points unless otherwise noted
        shape.ShadowFormat
            .SetBlurRadius(5)          // Blur radius (points) – 5 gives a soft edge
            .SetDistanceX(3)           // Horizontal offset (points) – shifts right
            .SetDistanceY(3)           // Vertical offset (points) – shifts down
            .SetTransparency(0.2)      // 20 % transparent (0.0 = opaque, 1.0 = fully transparent)
            .SetColor(Color.Black);    // Shadow colour – black works for most themes
```

### ما الذي تفعله كل خاصية

| الخاصية | التأثير | النطاق المعتاد |
|----------|--------|---------------|
| **BlurRadius** | يتحكم في مدى وضوح حواف الظل. القيم الأكبر = ظل أكثر نعومة. | 0 – 10 pts (شائع) |
| **DistanceX / DistanceY** | يحرك الظل أفقياً/عمودياً. القيم الموجبة تُنقل إلى اليمين/الأسفل. | -10 – 10 pts |
| **Transparency** | يحدد الشفافية. `0` = صلب، `1` = غير مرئي. | 0.0 – 1.0 |
| **Color** | اللون الفعلي للظل. استخدم `Color.FromArgb` لتحديد RGBA مخصص. | أي `System.Drawing.Color` |

> **حالة استثنائية:** إذا قمت بتعيين `BlurRadius` سالب، سيقوم Aspose.Words بتقليصه إلى `0`. احرص دائمًا على التحقق من القيم التي يقدمها المستخدم إذا كنت تعرض هذه الوظيفة عبر API.

---

## الخطوة 5: حفظ المستند المحدث

أخيرًا، اكتب المستند المعدل إلى القرص. يمكنك أيضًا إرساله مباشرةً كاستجابة في تطبيق ويب.

```csharp
        // Persist the changes
        doc.Save(outputPath);
        System.Console.WriteLine($"Shadow fine‑tuned! Saved as {outputPath}");
    }
}
```

افتح `ShadowFineTuned.docx` في Microsoft Word – ستلاحظ أن الشكل الآن يمتلك ظلًا أسودًا أكثر نعومة، مع إزاحة طفيفة وشفافية 20 ٪. الفرق بصريًا بسيط لكنه ملحوظ، خاصةً في العروض التقديمية أو ملفات PDF التسويقية.

---

## مثال كامل جاهز للتنفيذ (انسخه‑ألصقه)

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 👉 Update these paths before running
        string inputPath  = @"YOUR_DIRECTORY\Shadow.docx";
        string outputPath = @"YOUR_DIRECTORY\ShadowFineTuned.docx";

        // Load the document
        Document doc = new Document(inputPath);

        // Retrieve the first shape (null‑safe)
        Shape shape = doc.GetChild(NodeType.Shape, 0, true) as Shape;
        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // Fine‑tune the shadow
        shape.ShadowFormat
            .SetBlurRadius(5)          // Soft blur
            .SetDistanceX(3)           // Shift right
            .SetDistanceY(3)           // Shift down
            .SetTransparency(0.2)      // 20 % transparent
            .SetColor(Color.Black);    // Classic black

        // Save the result
        doc.Save(outputPath);
        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### النتيجة المتوقعة

- يصبح ظل الشكل أكثر نعومة (مُضبب) وإزاحة طفيفة.
- الشفافية تجعل الظل يندمج مع الخلفية، مما يمنع ظهور حد قاسي.
- عند فتح الملف في Word ستظهر تأثيرات احترافية دون تعديل يدوي.

---

## أسئلة شائعة وتنوعات

### 1. *هل يمكن تعديل ظلال لأشكال متعددة؟*  
نعم. استبدل استخراج الشكل الفردي بحلقة:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape s in shapes)
{
    s.ShadowFormat
        .SetBlurRadius(4)
        .SetDistanceX(2)
        .SetDistanceY(2)
        .SetTransparency(0.15)
        .SetColor(Color.Gray);
}
```

### 2. *ماذا لو أردت ظلًا ملونًا (مثلاً أزرق للعلامة التجارية)؟*  
فقط غيّر استدعاء `SetColor`:

```csharp
.SetColor(Color.FromArgb(128, 0, 120, 215)); // Semi‑transparent brand blue
```

### 3. *هل هناك طريقة لإزالة الظل تمامًا؟*  
عيّن الخاصية `Visible` إلى `false`:

```csharp
shape.ShadowFormat.Visible = false;
```

### 4. *هل يعمل هذا مع .NET Core؟*  
بالتأكيد. Aspose.Words for .NET متعدد المنصات؛ نفس الكود يعمل على Windows وLinux وmacOS.

---

## الخلاصة

أنت الآن تعرف **كيفية تعديل ظل الشكل** في C# باستخدام Aspose.Words. عبر تحميل المستند، تحديد الشكل، وتطبيق إعدادات `ShadowFormat`، يمكنك تحقيق نفس اللمسة البصرية التي تحصل عليها يدويًا في Word برمجيًا. هذا النهج قابل للتوسع—سواء كنت تعالج قالبًا واحدًا أو مئات الآلاف من التقارير.

هل أنت مستعد للخطوة التالية؟ جرّب دمج هذا مع خيارات تنسيق أخرى للأشكال (لون التعبئة، نمط الخط) أو أتمتة عملية إنشاء المستند بالكامل. API الخاص بـ Aspose.Words غني، وإتقان تعديل الظل هو مجرد بداية.

---

### مواضيع ذات صلة قد ترغب في استكشافها

- **Manipulation of shapes in Aspose.Words** – تغيير الحجم، الدوران، وعكس الأشكال.
- **Applying text effects** – كيفية ضبط `TextEffect` لـ WordArt.
- **Batch processing documents** – استخدام `Directory.GetFiles` لتعديل الظلال في العديد من الملفات دفعة واحدة.
- **Exporting to PDF** – الحفاظ على تنسيق الظل عند التحويل إلى PDF.

لا تتردد في ترك تعليق إذا واجهت أي صعوبات، أو مشاركة كيفية تخصيصك للظلال في مشاريعك. برمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}