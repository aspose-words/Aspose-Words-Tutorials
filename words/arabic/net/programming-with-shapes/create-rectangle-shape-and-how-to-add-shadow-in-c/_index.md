---
category: general
date: 2026-04-04
description: إنشاء شكل مستطيل في C# باستخدام Aspose.Words وتعلم كيفية إضافة ظل، وتطبيق
  تمويه على الظل، وجعل الظل شفافًا – دليل خطوة بخطوة.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- how to create document
- apply blur to shadow
- make shadow transparent
language: ar
og_description: إنشاء شكل مستطيل في C# باستخدام Aspose.Words. تعلم كيفية إضافة الظل،
  تطبيق الضبابية على الظل، وجعل الظل شفافًا في دليل مختصر.
og_title: إنشاء شكل مستطيل وكيفية إضافة الظل في C#
tags:
- Aspose.Words
- C#
- Document Automation
title: إنشاء شكل مستطيل وكيفية إضافة الظل في C#
url: /ar/net/programming-with-shapes/create-rectangle-shape-and-how-to-add-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء شكل مستطيل وكيفية إضافة الظل في C#

هل احتجت يوماً إلى **إنشاء شكل مستطيل** في مستند Word لكنك لم تكن متأكدًا من كيفية إضافة ظل خفيف؟ لست وحدك. في العديد من سيناريوهات التقارير أو العلامة التجارية، يمكن للمستطيل البسيط مع ظل شفاف نصف شفاف أن يجعل التخطيط يبدو مصقولًا دون جهد كبير.

في هذا الدرس سنستعرض **كيفية إنشاء مستند** باستخدام Aspose.Words، ثم نوضح **كيفية إضافة الظل**، **تطبيق تمويه على الظل**، وحتى **جعل الظل شفافًا**. في النهاية ستحصل على مقتطف C# جاهز للتنفيذ ينتج ملف *.docx* يحتوي على مستطيل مظلل بشكل جميل—كل ذلك في بضع دقائق.

## ما ستحتاجه

- .NET 6 أو أحدث (تعمل الواجهة البرمجية أيضًا مع .NET Framework 4.6+)
- Aspose.Words for .NET (الإصدار التجريبي المجاني يكفي لهذا المثال)
- محرر كود – Visual Studio، VS Code، Rider، أو أي بيئة تفضّلها
- معرفة أساسية بـ C# – لا شيء معقد، فقط القدرة على تشغيل تطبيق Console

إذا كان لديك هذه المتطلبات، يمكننا القفز مباشرة إلى الحل.

## الخطوة 1 – كيفية إنشاء المستند وتهيئة القماش

أولاً وقبل كل شيء: تحتاج إلى كائن `Document` فارغ. فكر فيه كصفحة بيضاء سيحولها Aspose.Words لاحقًا إلى ملف Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Create a new blank document
Document doc = new Document();
```

لماذا نقوم بإنشاء كائن `Document` بدلاً من تحميل قالب؟ البدء من الصفر يضمن عدم وجود أنماط أو أقسام مخفية قد تتداخل مع المستطيل. كما أنه يحافظ على حجم الملف صغيرًا—عادة جيدة عند توليد مستندات متعددة في حلقة.

## الخطوة 2 – إنشاء شكل مستطيل (جوهر الكلمة المفتاحية الأساسية)

الآن نقوم فعليًا **بإنشاء شكل مستطيل**. فئة `Shape` مرنة؛ فأنت تحدد النوع (Rectangle)، الحجم، وكيفية التفافه مع النص المحيط.

```csharp
// Define a rectangular shape
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.8 inches)
    Height = 100,              // Height in points (≈1.4 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};
```

لاحظ استخدام صيغة تهيئة الكائن—إنها مختصرة وتقلل من احتمال نسيان ضبط خاصية ما لاحقًا. سيقع المستطيل داخل الفقرة الأولى، التي سنضيفها في الخطوة التالية.

## الخطوة 3 – كيفية إضافة الظل وتخصيص مظهره

إضافة الظل ليست سطرًا واحدًا فقط؛ لديك عدة خصائص لتعديلها. هنا يأتي دور الكلمات المفتاحية الثانوية **apply blur to shadow** و **make shadow transparent**.

```csharp
// Configure the shadow
rect.Shadow.Format.Color = Color.DarkGray;   // Shadow colour
rect.Shadow.Format.BlurRadius = 5.0;         // Apply blur to shadow (points)
rect.Shadow.Format.OffsetX = 3;              // Horizontal offset
rect.Shadow.Format.OffsetY = 3;              // Vertical offset
rect.Shadow.Format.Transparency = 0.3;       // 30 % transparent (make shadow transparent)
```

ملاحظة سريعة حول القيم: `BlurRadius` بقيمة 5 يعطي تمويهًا ناعمًا؛ زدها إلى 10 للحصول على مظهر أكثر نعومة، أو قلّها إلى 2 لحافة أكثر حدة. قيمة `Transparency` تتراوح بين 0 (معتم) إلى 1 (شفاف). اضبطها وفقًا لمتطلبات التباين في علامتك التجارية.

### نصيحة احترافية

إذا احتجت ظلًا ملونًا (مثلاً أزرق الشركة)، استبدل `Color.DarkGray` بـ `Color.FromArgb(80, 0, 120, 215)`. الوسيط الأول هو قناة ألفا—اجعلها منخفضة للحصول على تأثير خفيف.

## الخطوة 4 – إدراج الشكل في المستند

بعد أن أصبح المستطيل وظله جاهزين، نضعهما الآن في الفقرة الأولى من المستند. هذه الخطوة تضمن ظهور الشكل في أعلى الملف.

```csharp
// Append the shape to the first paragraph of the first section
doc.FirstSection.Body.FirstParagraph.AppendChild(rect);
```

لماذا الفقرة الأولى؟ إنها قيمة افتراضية آمنة تعمل حتى عندما يكون المستند فارغًا تمامًا. إذا كان لديك موقع محدد (مثل بعد عنوان)، يمكنك تحديد ذلك العقدة وإدراج الشكل هناك بدلاً من ذلك.

## الخطوة 5 – حفظ الملف والتحقق من النتيجة

أخيرًا، نقوم بحفظ المستند على القرص. يمكنك اختيار أي مسار تفضله؛ فقط تأكد من وجود المجلد.

```csharp
// Save the document
doc.Save(@"C:\Temp\ShadowRectangle.docx");
```

عند فتح *ShadowRectangle.docx* في Microsoft Word، يجب أن ترى مستطيلًا بأبعاد 200 × 100 نقطة مع ظل رمادي داكن، تمويه خفيف، شفاف بنسبة 30 % ومُزاح ثلاث نقاط إلى اليمين والأسفل. التأثير خفيف لكنه يضيف عمقًا لتصاميم كانت مسطحة.

![إنشاء شكل مستطيل مع ظل في Aspose.Words](https://example.com/placeholder-image.png "إنشاء شكل مستطيل مع ظل في Aspose.Words")

*نص بديل للصورة:* **create rectangle shape with shadow in Aspose.Words** – الصورة تُظهر المستند النهائي مع المستطيل المظلَل.

## الاختلافات الشائعة والحالات الحدية

### تغيير لون الظل ديناميكيًا

إذا كان تطبيقك يدعم السمات، قد تستخرج لون الظل من ملف إعدادات:

```csharp
Color themeShadow = ColorTranslator.FromHtml(ConfigurationManager.AppSettings["ShadowColor"]);
rect.Shadow.Format.Color = themeShadow;
```

### جعل الشكل غير مدمج داخل النص

أحيانًا تريد أن يطفو المستطيل فوق النص. غيّر `WrapType` إلى `WrapType.Square` واضبط `RelativeHorizontalPosition` إلى `RelativeHorizontalPosition.Margin` لمزيد من التحكم.

```csharp
rect.WrapType = WrapType.Square;
rect.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
rect.Left = 72; // 1 inch from the left margin
```

### التعامل مع صفحات متعددة

إذا كنت تحتاج مستطيلًا في كل صفحة، قم بالتكرار عبر `doc.Sections` وأضف نسخة مستنسخة من الشكل إلى الفقرة الأولى في كل قسم. تذكر استدعاء `rect.Clone(true)` لتكرار إعدادات الظل أيضًا.

## ملخص – ما أنجزناه

- **إنشاء شكل مستطيل** باستخدام Aspose.Words
- **كيفية إضافة الظل** مع اللون، الإزاحة، التمويه، والشفافية
- توضيح **apply blur to shadow** و **make shadow transparent**
- حفظ ملف Word يمكنك فتحه فورًا

كل هذا تحقق ببضع أسطر فقط، مما يثبت أن التعديلات البصرية المتقدمة لا تتطلب دائمًا مكتبات رسومية ثقيلة.

## ما التالي؟

- جرّب `ShapeType`s أخرى (Ellipse, Cloud, إلخ) واختبر سلوك الظلال.
- اجمع المستطيل مع صناديق النص لإنشاء ملاحظات معنونة.
- تعمق في **كيفية إنشاء مستند** يحتوي على قوالب مسبقة للأشكال، ثم املأها برمجيًا.

لا تتردد في تعديل نصف القطر للتمويه، اللون، أو الشفافية حتى يصبح الظل مناسبًا للغة تصميمك. الواجهة البرمجية مرنة، والتغييرات تظهر فورًا عند إعادة تشغيل تطبيق Console.

برمجة سعيدة، ولتكن مستنداتك دائمًا ذات عمق إضافي!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}