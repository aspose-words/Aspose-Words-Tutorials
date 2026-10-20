---
category: general
date: 2026-05-01
description: كيفية تحريك الظل على شكل في Aspose.Words باستخدام C#. تعلم إضافة الظل
  إلى الشكل، تغيير الضبابية، ضبط الشفافية، وتدوير الظل في دقائق.
draft: false
keywords:
- how to move shadow
- add shadow to shape
- how to change blur
- how to set transparency
- how to rotate shadow
language: ar
og_description: كيفية تحريك الظل على شكل في Aspose.Words باستخدام C#. يوضح هذا البرنامج
  التعليمي كيفية إضافة ظل إلى الشكل، وتغيير الضبابية، وتعيين الشفافية، وتدوير الظل.
og_title: كيفية تحريك الظل في Aspose.Words – دليل C# الكامل
tags:
- Aspose.Words
- C#
- Document Automation
title: كيفية تحريك الظل في Aspose.Words – دليل C# الكامل
url: /ar/net/programming-with-shapes/how-to-move-shadow-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تحريك الظل في Aspose.Words – دليل C# كامل

هل تساءلت يومًا **كيفية تحريك الظل** على شكل داخل مستند Word دون فتح Word يدويًا؟ في عملي اليومي، كثيرًا ما احتجت إلى تعديل ظل الشكل برمجيًا—سواء كان لتقرير مصقول أو قالب ديناميكي. الخبر السار؟ باستخدام Aspose.Words يمكنك القيام بذلك ببضع أسطر، وستتعلم أيضًا **إضافة ظل إلى الشكل**، **كيفية تغيير الضبابية**، **كيفية ضبط الشفافية**، و**كيفية تدوير الظل** في نفس العملية.

في هذا الدرس سنستعرض سيناريو واقعي: تحميل ملف DOCX موجود يحتوي بالفعل على شكل، تعديل موضع الظل، نعومته، شفافيته، واتجاهه، ثم حفظ النتيجة. في النهاية ستحصل على مقتطف قابل لإعادة الاستخدام يمكنك إدراجه في أي مشروع .NET، وستفهم لماذا كل خاصية مهمة.

## المتطلبات المسبقة – ما تحتاجه قبل البدء

- **Aspose.Words for .NET** (الإصدار 23.12 أو أحدث). يمكنك الحصول عليه من NuGet باستخدام `Install-Package Aspose.Words`.
- بيئة تطوير .NET 6+ (Visual Studio، VS Code، Rider—أيا كان ما تفضله).
- ملف Word إدخال (`input.docx`) يحتوي بالفعل على شكل واحد على الأقل (مستطيل، دائرة، أو صورة يكفي).
- إلمام أساسي بصياغة C#—لا شيء معقد.

إذا كان أي من هذه غير متوفر لديك، توقف لحظةً وقم بتثبيت المكتبة؛ باقي الدليل يفترض أن الحزمة مضافة بالفعل.

## الخطوة 1: تحميل المستند والحصول على الشكل المستهدف – **كيفية تحريك الظل** تبدأ هنا

أول ما نقوم به هو تحميل المستند المصدر وتحديد الشكل الذي نريد تعديل خصائصه. Aspose.Words يتعامل مع كل كائن (فقرات، جداول، أشكال) كعقدة في شجرة، لذا يمكننا الاستعلام عنها مباشرة.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // 📂 Load the source DOCX that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // 🎯 Retrieve the first shape in the document.
        // The GetChild method walks the node tree; the third argument (true) means “search deep”.
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        // If no shape is found, bail out early.
        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // -------------------------------------------------
        // The next sections show **how to move shadow**,
        // **add shadow to shape**, **how to change blur**,
        // **how to set transparency**, and **how to rotate shadow**.
        // -------------------------------------------------
```

> **لماذا هذا مهم:** تحميل المستند مرة واحدة وإعادة استخدام نفس كائن `Document` يكون أكثر كفاءة. استدعاء `GetChild` آمن لأنه يُعيد `null` إذا كان الفهرس خارج النطاق، مما يتيح لنا التعامل مع الأشكال المفقودة بسلاسة.

## الخطوة 2: تعديل نصف قطر الضبابية – إتقان **كيفية تغيير الضبابية**

الظل الناعم يبدو احترافيًا، بينما الحافة الصلبة قد تبدو رخيصة. خاصية `BlurRadius` تتحكم في النعومة بالنقاط (1 pt ≈ 1/72 inch). لنرفعها إلى 8 pt.

```csharp
        // Increase the blur radius to soften the shadow edges.
        shape.ShadowFormat.BlurRadius = 8.0; // 8 points ≈ 0.11 inches
```

> **نصيحة محترف:** الضبابية الافتراضية هي 0.5 pt. أي قيمة فوق 5 pt تكون ملحوظة عادةً، لكن احذر من جعلها كبيرة جدًا—فقد يجعل الشكل يبدو منفصلًا عن الصفحة.

## الخطوة 3: ضبط الشفافية – الجواب على **كيفية ضبط الشفافية**

الشفافية تحدد مدى شفافية الظل. القيمة `0` تعني غير شفاف تمامًا؛ `1` تعني غير مرئي تمامًا. لتأثير خفيف سنستخدم `0.3` (30 % شفاف).

```csharp
        // Make the shadow semi‑transparent so the shape remains visible through it.
        shape.ShadowFormat.Transparency = 0.3; // 30% transparent
```

> **لماذا قد يهمك ذلك:** إذا كان الشكل داكنًا، ظل غير شفاف بالكامل قد يغطي النص الموجود تحته. ضبط الشفافية يحافظ على قابلية القراءة مع إضفاء العمق.

## الخطوة 4: تحريك الظل – جوهر **كيفية تحريك الظل**

خاصية `Distance` تحدد المسافة التي يُزاح الظل فيها عن الشكل، مقاسة بالنقاط. كلما زادت المسافة، يبتعد الظل أكثر، مما يخلق تأثيرًا أكثر دراماتيكية.

```csharp
        // Move the shadow farther from the shape for a more pronounced effect.
        shape.ShadowFormat.Distance = 4.0; // 4 points ≈ 0.055 inches
```

> **ماذا لو احتجت إزاحة طفيفة؟** ضبط `Distance` إلى `0` يجعل الظل يجلس مباشرة خلف الشكل، وهو مفيد لتأثيرات النقش.

## الخطوة 5: تدوير مصدر الضوء – حل **كيفية تدوير الظل**

الظلال ليست دائمًا مباشرة إلى الأسفل؛ فهي تتبع زاوية مصدر الضوء. خاصية `Angle` (بالدرجات) تدور الظل حول الشكل. لنميله 45°.

```csharp
        // Rotate the light source to change the shadow direction.
        shape.ShadowFormat.Angle = 45; // 45 degrees clockwise from the vertical axis
```

> **تجربة سريعة:** جرّب `90` للحصول على ظل يمين أو `-30` لظل يميل إلى اليسار. التغيير البصري يكون فوريًا.

## الخطوة 6: حفظ المستند – رؤية نتيجة **إضافة ظل إلى الشكل**

الآن بعد أن عدلنا الظل، سنكتب المستند مرة أخرى إلى القرص. يمكنك استبدال الملف الأصلي أو إنشاء ملف جديد؛ المثال يستخدم ملف إخراج جديد.

```csharp
        // Save the modified document with the adjusted shadow.
        doc.Save(@"YOUR_DIRECTORY\output.docx");

        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

> **الناتج المتوقع:** افتح `output.docx`. سيظهر ظل الشكل أكثر نعومة، مع إزاحة طفيفة، شبه شفاف، ومائل بزاوية 45°. إذا قارنت بينه وبين `input.docx`، الفرق واضح ولا يمكن إنكاره.

### مثال كامل يعمل (جاهز للنسخ واللصق)

فيما يلي البرنامج بالكامل في كتلة واحدة. الصقه في مشروع Console جديد، استبدل `YOUR_DIRECTORY` بمسار مجلد فعلي، ثم شغّله.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the source document that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // Retrieve the first shape in the document (the one we will modify).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 1️⃣ Change blur – soften the edges.
        shape.ShadowFormat.BlurRadius = 8.0;

        // 2️⃣ Set transparency – make it 30% see‑through.
        shape.ShadowFormat.Transparency = 0.3;

        // 3️⃣ Move the shadow – increase distance from the shape.
        shape.ShadowFormat.Distance = 4.0;

        // 4️⃣ Rotate the shadow – change light direction.
        shape.ShadowFormat.Angle = 45;

        // Save the result.
        doc.Save(@"YOUR_DIRECTORY\output.docx");
        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

## أسئلة شائعة وحالات حافة

### ماذا لو كان المستند يحتوي على أشكال متعددة؟

يمكنك التكرار عبر جميع الأشكال:

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    // Apply the same shadow settings or customize per shape.
}
```

### هل يمكنني إضافة ظل إلى شكل لا يحتوي على ظل حاليًا؟

بالطبع. كائن `ShadowFormat` موجود دائمًا؛ كل ما عليك هو تفعيله:

```csharp
shape.ShadowFormat.Enabled = true;
```

### هل يعمل هذا مع الصور وSmartArt؟

نعم. أي عقدة تُشتق من `Shape`—بما في ذلك الصور، المخططات، وSmartArt—تُظهر `ShadowFormat`. نفس الخصائص تنطبق.

### كيف أتحكم في لون الظل؟

استخدم خاصية `Color`:

```csharp
shape.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### مخاوف التوافق؟

Aspose.Words 23.12+ يدعم .NET 6، .NET Core 3.1، و .NET Framework 4.6.2+. الـ API المعروض ثابت عبر هذه الإصدارات.

## الخلاصة

لقد غطينا للتو **كيفية تحريك الظل** على شكل باستخدام Aspose.Words، وخلال ذلك أظهرنا أيضًا **إضافة ظل إلى الشكل**، **كيفية تغيير الضبابية**، **كيفية ضبط الشفافية**، و**كيفية تدوير الظل**. المثال الكامل القابل للتنفيذ يتيح لك تعديل ظل أي شكل في ثوانٍ معدودة، مما يمنح مستنداتك مظهرًا مصقولًا واحترافيًا دون الحاجة لفتح Word.

هل أنت مستعد للخطوة التالية؟ جرّب دمج هذه التعديلات مع **التنسيق الشرطي**—على سبيل المثال، تطبيق ظل أعمق فقط على العناوين أو على المخططات التي تتجاوز حجمًا معينًا. أو استكشف **تعبئات التدرج** للشكل نفسه لإنشاء تصميم جذاب حقًا.

إذا واجهت أي صعوبات، اترك تعليقًا أدناه. برمجة سعيدة، ولتسقط ظلالك دائمًا حيث تريدها!

![مخطط يوضح تأثير تحريك الظل على شكل – مثال على كيفية تحريك الظل](https://example.com/images/shadow-demo.png "مثال على كيفية تحريك الظل")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}