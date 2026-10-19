---
category: general
date: 2026-03-01
description: إنشاء مستند Word باستخدام Aspose.Words وتعلم كيفية إضافة شكل مستطيل،
  وكيفية إضافة الظل، وكيفية ضبط الشفافية، وكيفية إنشاء الشكل — كل ذلك بلغة C#.
draft: false
keywords:
- create word document
- add rectangle shape
- how to add shadow
- how to create shape
- how to set transparency
language: ar
og_description: إنشاء مستند Word باستخدام Aspose.Words في C#. تعلّم كيفية إضافة شكل
  مستطيل، وتطبيق ظل خارجي، وضبط الشفافية في بضع خطوات فقط.
og_title: إنشاء مستند Word مع شكل مستطيل وظل – دليل
tags:
- Aspose.Words
- C#
- Document Generation
title: إنشاء مستند Word مع شكل مستطيل وظل – دليل خطوة بخطوة
url: /ar/net/programming-with-shapes/create-word-document-with-a-rectangle-shape-and-shadow-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word مع شكل مستطيل وظل – دليل خطوة‑بخطوة

هل احتجت يومًا إلى **create word document** يحتوي على مستطيل مُصمم خصيصًا؟ ربما تقوم بإنشاء قالب تقرير وتريد ظلًا خفيفًا لإبراز التصميم. لست وحدك—المطورون يسألون باستمرار، “كيف يمكنني إضافة شكل مستطيل وظل برمجيًا؟” الخبر السار هو أنه باستخدام Aspose.Words يمكنك القيام بذلك ببضع أسطر.

في هذا البرنامج التعليمي سنستعرض العملية بالكامل: من إنشاء ملف Word فارغ، إلى إضافة شكل مستطيل، إلى تكوين ظل خارجي مع الشفافية. في النهاية ستحصل على ملف `Shadow.docx` جاهز للاستخدام يمكنك فتحه في Word ورؤية التأثير فورًا. لا أدوات خارجية، لا XML معقد—فقط كود C# نظيف وشروحات واضحة.

## ما ستتعلمه

- **How to create shape** كائنات في مستند Word باستخدام Aspose.Words.
- **How to add rectangle shape** إلى فقرة دون إفساد المحتوى الموجود.
- **How to add shadow** (outer shadow) والتحكم في لونه، وإزاحته، وتمويهّه، وشفافيته.
- **How to set transparency** على الظل لجعله يبدو احترافيًا.
- نصائح، ومخاطر، وتنوعات قد تحتاجها في مشاريع العالم الحقيقي.

### المتطلبات المسبقة

- .NET 6.0 أو أحدث (تعمل الواجهة البرمجية أيضًا مع .NET Framework 4.6+).
- Aspose.Words for .NET مثبت عبر NuGet (`Install-Package Aspose.Words`).
- فهم أساسي لبنية جمل C#—لا شيء معقد، فقط عبارات `using` المعتادة وإنشاء الكائنات.

> **نصيحة احترافية:** إذا كنت تستخدم Visual Studio، فعّل “nullable reference types” لالتقاط أخطاء الإشارة إلى null المحتملة مبكرًا.

## الخطوة 1 – إنشاء مستند Word فارغ

لـ **create word document** نبدأ بفئة `Document`. فكر فيها كقماش فارغ؛ يمكنك لاحقًا إضافة أقسام، فقرات، جداول، أو أشكال.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new blank document
Document document = new Document();
```

لماذا نحتاج إلى نسخة جديدة من `Document`؟ لأن كل شكل أو فقرة أو نمط يعيش داخل نموذج كائن المستند (DOM). البدء بمستند نظيف يضمن أن المستطيل الذي تضيفه لن يتداخل مع المحتوى الموجود.

## الخطوة 2 – تعريف شكل المستطيل

الآن نريد **how to create shape** مستطيل. يأخذ مُنشئ `Shape` المستند المالك ونوع الشكل. نحدد أيضًا عرضه وارتفاعه بالنقاط (1 pt ≈ 1/72 in).

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width = 200;   // 200 pt ≈ 2.78 in
rectangleShape.Height = 100; // 100 pt ≈ 1.39 in
```

قد تتساءل، “هل يمكنني استخدام السنتيمترات بدلًا من النقاط؟” الواجهة البرمجية تقبل النقاط فقط، لكن يمكنك التحويل: `points = centimeters * 28.35`. هذا التحويل الصغير مفيد عندما تقوم بمحاذاة الأشكال مع هوامش الصفحة.

## الخطوة 3 – إضافة ظل خارجي وتعيين الشفافية

هنا يحدث السحر: **how to add shadow** و **how to set transparency** على ذلك الظل. خاصية `ShadowFormat` تمنحك التحكم الكامل.

```csharp
// Enable shadow visibility
rectangleShape.ShadowFormat.Visible = true;

// Choose a shadow color
rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;

// Set transparency (0 = opaque, 1 = fully transparent)
rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent

// Position the shadow relative to the shape
rectangleShape.ShadowFormat.OffsetX = 5; // horizontal offset in points
rectangleShape.ShadowFormat.OffsetY = 5; // vertical offset in points

// Blur makes the shadow look softer
rectangleShape.ShadowFormat.BlurRadius = 4;

// Specify that this is an outer shadow (instead of inner)
rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;
```

**لماذا هذه الإعدادات؟**  
- **Transparency** تسمح للنقش الأساسي للصفحة بالظهور، مما يمنع الظل من أن يبدو ثقيلًا جدًا.  
- **OffsetX/Y** يخلقان الانطباع أن الشكل مرفوع عن الصفحة.  
- **BlurRadius** ينعّم الحواف—بدونه سيكون الظل مستطيلًا صلبًا، وهو غير طبيعي.

إذا كنت تحتاج إلى تأثير أكثر دراماتيكية، زد `OffsetX/Y` إلى 10 وزد `BlurRadius` إلى 8. وعلى العكس، للحصول على إشارة خفيفة، حافظ على القيم عند 2 و2 على التوالي.

## الخطوة 4 – إدراج الشكل في المستند

نقوم الآن **add rectangle shape** إلى الفقرة الأولى في المستند. إذا لم يحتوي المستند على محتوى، يتم إنشاء `FirstParagraph` تلقائيًا لك.

```csharp
// Append the rectangle to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

ماذا لو أردت الشكل داخل خلية جدول معينة أو فقرة لاحقة؟ فقط حدد ذلك العقدة (`doc.GetChild(NodeType.Paragraph, index, true)`) واستدعِ `AppendChild` عليها. يمكن استنساخ نفس كائن الشكل إذا كنت بحاجة إلى نسخ متعددة.

## الخطوة 5 – حفظ المستند

أخيرًا، نُـ **create word document** ملف على القرص. استخدم مسارًا يناسب بيئتك؛ المثال يستخدم عنصر نائب.

```csharp
// Save the document as a .docx file
document.Save(@"YOUR_DIRECTORY/Shadow.docx");
```

عند فتح `Shadow.docx` في Microsoft Word، سترى مستطيل رمادي فاتح مع ظل خارجي ناعم مائل إلى أسفل اليمين. شفافية الظل بنسبة 30 % تضمن أنه لا يطغى على الصفحة.

![إنشاء مستند word مع شكل مستطيل بظل](image.png "إنشاء مستند word مع شكل مستطيل بظل")

*نص بديل للصورة: إنشاء مستند word مع شكل مستطيل بظل*

## الكود الكامل الجاهز للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه ولصقه في تطبيق Console. لا أجزاء مفقودة، ولا “انظر الوثائق للمزيد”.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Add a rectangular shape and define its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width = 200;   // width in points
        rectangleShape.Height = 100;  // height in points

        // Step 3: Configure an outer shadow for the shape
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;
        rectangleShape.ShadowFormat.Transparency = 0.3;   // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;          // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;          // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;
        rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;

        // Step 4: Insert the shape into the first paragraph of the document
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // Step 5: Save the document with the shadowed shape
        document.Save(@"YOUR_DIRECTORY/Shadow.docx");

        Console.WriteLine("Word document created successfully at YOUR_DIRECTORY/Shadow.docx");
    }
}
```

### النتيجة المتوقعة

- يظهر ملف باسم **Shadow.docx** في المجلد المستهدف.  
- عند فتحه في Word يظهر مستطيل (200 × 100 pt) مع ظل خارجي رمادي داكن.  
- الظل مائل بمقدار 5 pt أفقياً وعمودياً، مُطمّع، وشفافيته 30 %.

## الأسئلة الشائعة والحالات الخاصة

| السؤال | الجواب |
|----------|--------|
| **Can I change the shadow color to match my brand?** | بالطبع—ما عليك سوى استبدال `System.Drawing.Color.DarkGray` بأي `Color` تفضله، مثل `Color.FromArgb(255, 0, 120, 215)` للحصول على لمسة زرقاء. |
| **What if I need an inner shadow instead of outer?** | عيّن `ShadowFormat.Style = ShadowStyle.InnerShadow`. باقي الخصائص تعمل بنفس الطريقة. |
| **Is transparency supported in older Word versions?** | نعم. Aspose.Words يكتب XML المناسب الذي تفهمه Word 2007+. قد تتجاهل الإصدارات الأقدم قيمة الشفافية لكنها ستظهر الظل. |
| **Can I add multiple shapes with different shadows?** | بالتأكيد—أنشئ كائنات `Shape` جديدة، اضبط كل ظل على حدة، وألحقها بالعقد المطلوبة. |
| **What about performance for hundreds of shapes?** | إنشاء عدد كبير من الأشكال قد يزيد من استهلاك الذاكرة. أعد استخدام نسخة واحدة من `Document` وأضف الأشكال داخل حلقة؛ حرّر الكائنات المؤقتة إذا واجهت ضغطًا. |

## نصائح لمشاريع العالم الحقيقي

- **Batch generation:** عند توليد تقارير لعدد كبير من المستخدمين، أنشئ قالب `Document` واحدًا واستنسخه لكل تكرار. استبدل العناصر النائبة قبل إلحاق الأشكال.  
- **Dynamic sizing:** استخدم أبعاد الصفحة (`document.FirstSection.PageSetup.PageWidth`) لحساب حجم الشكل نسبةً إلى الصفحة، مما يضمن تخطيطًا ثابتًا عبر أحجام الورق المختلفة.  
- **Testing:** افتح دائمًا ملف `.docx` المُولد في Word بعد تعديل قيم الظل. المراجعة البصرية أسرع من التخمين بالأرقام.  

## الخطوات التالية

الآن بعد أن عرفت **how to add rectangle shape**, **how to add shadow**, و **how to set transparency**, فكر في استكشاف:

- إضافة **gradient fills** إلى الأشكال (`Shape.FillFormat`).  
- تضمين **pictures** داخل الأشكال لتأثيرات العلامة المائية.  
- استخدام **tables** لمحاذاة عدة أشكال ذات ظلال في شبكة.  
- تصدير المستند نفسه إلى PDF (`document.Save("output.pdf")`) مع الحفاظ على الظلال.

كل من هذه الأمور يبني على المفاهيم الأساسية نفسها، لذا ستشعر بالراحة عند توسيع الكود.

### ملخص

بدأنا بـ **create word document** باستخدام Aspose.Words، ثم **how to create shape** مستطيل، ثم طبقنا **how to add shadow**, وضبطنا **how to set transparency**, ثم حفظنا النتيجة. العملية بأكملها تتناسب مع نمط مضغوط وقابل لإعادة الاستخدام يمكنك تكييفه مع أي سيناريو أتمتة.

لا تتردد في التجربة—غيّر الألوان، العب بالإزاحات، أو رص عدة أشكال معًا. عندما تواجه عائقًا، عد إلى الأقسام السابقة؛ فهي مصممة لتكون مرجعًا سريعًا. برمجة سعيدة، ولتظل مستنداتك دائمًا مصقولة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}