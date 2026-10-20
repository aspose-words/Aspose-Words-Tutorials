---
category: general
date: 2026-02-18
description: أنشئ شكل مستطيل باستخدام Aspose.Words وتعلم كيفية إضافة الظل، وتحديد
  حجم الشكل، وحفظ مستند Word في بضع دقائق.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- save word document
- set shape size
- how to create document
language: ar
og_description: إنشاء شكل مستطيل في ملف Word، وتعلم كيفية إضافة الظل، وتحديد حجم الشكل،
  وحفظ المستند باستخدام Aspose.Words في C#.
og_title: إنشاء شكل مستطيل في Word – دليل Aspose.Words الكامل
tags:
- Aspose.Words
- C#
- Word automation
title: إنشاء شكل مستطيل في Word باستخدام Aspose.Words – دليل خطوة بخطوة
url: /ar/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء شكل مستطيل في Word باستخدام Aspose.Words – دليل خطوة بخطوة

هل احتجت يومًا إلى **إنشاء شكل مستطيل** في ملف Word لكن لم تكن متأكدًا من أين تبدأ؟ لست وحدك—غالبًا ما يسأل المطورون: “كيف أضيف ظلًا إلى الشكل وأظل أحتفظ بإمكانية تحرير المستند؟” في هذا الدرس سنجيب على ذلك وسنوضح لك أيضًا **كيفية إضافة الظل**، **تحديد حجم الشكل**، و**حفظ مستند Word** في تدفق واحد سلس.

سنستعرض كل ما تحتاجه، بدءًا من تهيئة مستند جديد (نعم، هذه هي الخطوة الأولى لـ **كيفية إنشاء مستند**) وحتى حفظ ملف *.docx* النهائي على القرص. لا مراجع خارجية، مجرد مثال مستقل يمكنك نسخه‑ولصقه في Visual Studio وتشغيله اليوم.

---

## المتطلبات المسبقة

- .NET 6+ (أو .NET Framework 4.7+). Aspose.Words يعمل مع أي بيئة تشغيل .NET حديثة.
- رخصة Aspose.Words صالحة (أو مفتاح التقييم المجاني) – وإلا ستظهر علامة مائية.
- Visual Studio، Rider، أو أي محرر C# تفضله.
- معرفة أساسية بـ C#—ليس شيئًا معقدًا، فقط القدرة على تشغيل تطبيق console.

> **نصيحة احترافية:** إذا كنت تستخدم macOS، يمكن تشغيل نفس الكود تحت .NET 6 مع VS Code—فقط تأكد من الإشارة إلى حزمة NuGet `Aspose.Words`.

---

## الخطوة 1: تهيئة المستند – الأساس لـ **كيفية إنشاء مستند**

قبل أن نرسم أي شيء، نحتاج إلى لوحة فارغة. تسمي Aspose.Words هذه اللوحة بـ `Document`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

> **لماذا هذا مهم:** كائن `Document` يمثل ملف *.docx* بالكامل. جميع الأشكال والفقرات والأقسام التي تضيفها تصبح أبناء لهذا الكائن. بدءًا بمستند نظيف يضمن عدم وجود أنماط مخفية تتداخل مع المستطيل الخاص بك.

---

## الخطوة 2: تعريف المستطيل و**تحديد حجم الشكل**

المستطيل هو مجرد `Shape` مع `ShapeType.Rectangle`. سنعطيه أبعادًا صريحة حتى يظهر بالضبط كما هو مقصود.

```csharp
// Step 2: Create a rectangular shape and define its size
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points (≈2.78 inches)
rectangleShape.Height = 100; // height in points (≈1.39 inches)
```

> **ماذا تعني الأرقام:** Aspose.Words يستخدم النقاط (1 pt = 1/72 in). عدّل القيم لتناسب تخطيطك؛ بالنسبة لصفحة A4 النموذجية، 200 pt عرض مريح.

---

## الخطوة 3: **كيفية إضافة الظل** – لجعل الشكل يبرز

الظلال تعطي إشارة بصرية بأن الشكل “مرفوع” عن الصفحة. خاصية `Shadow` تتيح لك تعديل اللون، والمسافة، والشفافية، والتمويه.

```csharp
// Step 3: Apply a shadow to the shape
rectangleShape.Shadow.Color        = Color.Black; // Shadow color
rectangleShape.Shadow.Distance    = 5;           // Offset distance in points
rectangleShape.Shadow.Transparency = 0.4;        // 40 % transparent
rectangleShape.Shadow.BlurRadius  = 8;           // Soft edge radius
```

> **لماذا نستخدم الشفافية؟** الظل الكامل غير الشفاف قد يبدو قاسيًا. ضبطه على 0.4 يجعل التأثير خفيفًا واحترافيًا.

---

## الخطوة 4: وضع المستطيل – تدفق inline مع النص المحيط

إذا أردت أن يتصرف الشكل كحرف داخل فقرة، اضبط `WrapType` إلى `Inline`. هذا يحافظ على تخطيط predictable، خاصةً عندما يتم تحرير المستند لاحقًا.

```csharp
// Step 4: Set the shape to flow inline with the surrounding text
rectangleShape.WrapType = WrapType.Inline;
```

> **حالة خاصة:** إذا كنت بحاجة إلى أن يطفو المستطيل فوق النص (مثل العلامة المائية)، غيّر `WrapType` إلى `Square` أو `BehindText`.

---

## الخطوة 5: إدراج الشكل في جسم المستند

الآن نضع المستطيل فعليًا في الفقرة الأولى. إذا لم يكن للمستند محتوى بعد، يتم إنشاء `FirstParagraph` تلقائيًا.

```csharp
// Step 5: Insert the shape into the first paragraph of the document
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **نصيحة:** يمكنك أيضًا إنشاء فقرة جديدة أولًا ثم إلحاق الشكل—مفيد عندما تحتاج إلى نص محيط.

---

## الخطوة 6: **حفظ مستند Word** – الخطوة النهائية

مع كل شيء في مكانه، حفظ الملف يصبح سطرًا واحدًا. اختر أي مسار تفضله؛ المثال يستخدم عنصر نائب يجب استبداله بمسارك الخاص.

```csharp
// Step 6: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowShape.docx");
```

> **النتيجة:** افتح *.docx* المُولد في Microsoft Word. سترى مستطيلًا بظل أسود، عرضه 200 pt وارتفاعه 100 pt، موضعًا inline مع الفقرة الأولى.

---

## النتيجة المتوقعة

عند فتح **ShadowShape.docx**، سيظهر المستند كما يلي:

- فقرة واحدة تحتوي على شكل مستطيل.
- المستطيل له ظل أسود خفيف إزاحته 5 pt.
- حجم الشكل يطابق الأبعاد المحددة في الخطوة 2.
- لا يظهر نص إضافي ما لم تقم بإضافته يدويًا.

إذا لم يظهر الشكل، تحقق مرة أخرى من أنك أدرجت الإصدار الصحيح من Aspose.Words وأن رخصتك (أو نسخة التجربة) مفعلة.

---

## أسئلة شائعة وتنوعات

| السؤال | الجواب |
|----------|--------|
| *هل يمكنني تغيير لون الظل إلى غير الأسود؟* | بالتأكيد—اضبط `rectangleShape.Shadow.Color = Color.Blue;` أو أي `System.Drawing.Color` آخر. |
| *ماذا لو احتجت مستطيلًا أكبر؟* | عدّل قيم `Width` و `Height`. تذكر أن القيم بوحدات النقاط؛ 72 pt = 1 in. |
| *هل يمكن وضع الشكل في موقع مطلق؟* | نعم—استخدم `WrapType = WrapType.Absolute` واضبط خصائص `Top`/`Left`. |
| *هل يعمل هذا مع .NET Core؟* | نعم. Aspose.Words متعدد المنصات؛ فقط ثبّت حزمة NuGet لـ .NET Standard. |
| *هل يمكن إضافة نص داخل المستطيل؟* | ليس مباشرة؛ ستحتاج إلى إدراج شكل `TextBox` بدلًا من المستطيل العادي. |

---

## مثال كامل جاهز للتنفيذ (نسخ‑لصق)

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize a new document
        Document document = new Document();

        // 2️⃣ Create rectangle and set its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 200;
        rectangleShape.Height = 100;

        // 3️⃣ Add a subtle black shadow
        rectangleShape.Shadow.Color         = Color.Black;
        rectangleShape.Shadow.Distance     = 5;
        rectangleShape.Shadow.Transparency = 0.4;
        rectangleShape.Shadow.BlurRadius   = 8;

        // 4️⃣ Make the shape flow inline with text
        rectangleShape.WrapType = WrapType.Inline;

        // 5️⃣ Insert the shape into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 6️⃣ Persist the file
        document.Save(@"C:\Temp\ShadowShape.docx");

        System.Console.WriteLine("Document saved successfully!");
    }
}
```

شغّل البرنامج، انتقل إلى `C:\Temp\ShadowShape.docx`، وسترى المستطيل مع الظل تمامًا كما هو موصوف.

---

## الخلاصة

أنت الآن تعرف **كيفية إنشاء شكل مستطيل** في ملف Word باستخدام Aspose.Words، وكيفية **تحديد حجم الشكل**، **إضافة الظل**، وأخيرًا **حفظ مستند Word** بالتغييرات. العملية بأكملها—من **كيفية إنشاء مستند** إلى حفظ النتيجة—تُنفّذ ببضع أسطر من C# ويمكن توسيعها لتصاميم أكثر تعقيدًا.

هل أنت مستعد للتحدي التالي؟ جرّب استبدال المستطيل بشكل ذو زوايا مستديرة، جرب ألوان ظلال مختلفة، أو أدخل الشكل داخل خلية جدول. كل تعديل يعزز المفاهيم الأساسية التي غطيناها هنا.

إذا وجدت هذا الدليل مفيدًا، شاركه، اترك تعليقًا بتنوعاتك الخاصة، أو استكشف دروسنا الأخرى حول أتمتة Word، مثل إدراج الصور أو إنشاء الجداول باستخدام Aspose.Words. برمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}