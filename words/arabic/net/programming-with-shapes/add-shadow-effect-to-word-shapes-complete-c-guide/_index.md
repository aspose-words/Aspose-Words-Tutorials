---
category: general
date: 2026-02-10
description: أضف تأثير الظل إلى شكل في Word باستخدام C#. تعلّم كيفية تغيير لون الظل،
  وضبط الشفافية، وتطبيق ظل الشكل في بضع خطوات فقط.
draft: false
keywords:
- add shadow effect
- change shadow color
- how to set transparency
- add shape shadow
- apply shadow color
language: ar
og_description: أضف تأثير الظل إلى شكل في Word باستخدام C#. تعلّم كيفية تغيير لون
  الظل، ضبط الشفافية، وتطبيق ظل الشكل في بضع خطوات فقط.
og_title: إضافة تأثير الظل إلى أشكال Word – دليل C# الكامل
tags:
- Aspose.Words
- C#
- Document Automation
title: إضافة تأثير الظل إلى أشكال Word – دليل C# الكامل
url: /ar/net/programming-with-shapes/add-shadow-effect-to-word-shapes-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة تأثير الظل إلى أشكال Word – دليل C# كامل

هل احتجت يومًا إلى **إضافة تأثير الظل** إلى شكل في Word لكنك لم تكن متأكدًا من أين تبدأ؟ لست وحدك—غالبًا ما يسأل المطورون: “كيف أجعل الشكل يبدو أكثر ثلاثية الأبعاد؟” الخبر السار هو أنه ببضع أسطر من C# يمكنك تغيير لون الظل، ضبط الشفافية، وتعديل مظهر أي شكل بدقة. في هذا الدرس سنستعرض مثالًا كاملاً يمكن تشغيله يفعل ذلك بالضبط، بالإضافة إلى مجموعة من النصائح التي كنت تتمنى لو عرفتها مسبقًا.

سنغطي:

* تحميل ملف DOCX يحتوي بالفعل على شكل.  
* العثور على الشكل (حتى وإن كان داخل مجموعة).  
* تطبيق الظل—المسافة، الضبابية، اللون، والشفافية.  
* التحقق من النتيجة بحفظ المستند.  

لا حاجة لأي وثائق خارجية؛ كل ما تحتاجه موجود هنا. المتطلب الوحيد هو وجود مرجع إلى **Aspose.Words for .NET** (أو أي مكتبة متوافقة تُظهر `Shape.ShadowFormat`). إذا كنت تستخدم NuGet، فقط نفّذ `Install-Package Aspose.Words`. جاهز؟ لنبدأ.

---

## المتطلبات المسبقة

| المتطلب | لماذا هو مهم |
|-------------|----------------|
| .NET 6.0 أو أحدث | واجهات برمجة تطبيقات حديثة، أداء أفضل |
| Aspose.Words for .NET (أو ما يعادله) | يوفر الفئات `Document`، `Shape`، و`ShadowFormat` |
| ملف DOCX (`input.docx`) يحتوي على شكل واحد على الأقل | يتعامل الدرس مع شكل موجود؛ يمكنك إنشاء واحد في Word يدويًا إذا لزم الأمر |

> **نصيحة احترافية:** إذا لم يكن لديك شكل جاهز، افتح Word، أدرج مستطيلًا بسيطًا، احفظ الملف باسم `input.docx` وضعه في مجلد المشروع `Resources`.

---

## الخطوة 1 – تحميل مستند Word وتحديد الموقع الخاص بالشكل {#add-shadow-effect-step1}

أولًا وقبل كل شيء: نحتاج إلى كائن `Document` يشير إلى ملف المصدر. ثم سنستخرج أول شكل باستخدام بحث تكراري حتى يعمل حتى عندما يكون الشكل داخل مجموعة.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Step 1: Load the Word document that contains a shape
        Document doc = new Document("Resources/input.docx");

        // Step 2: Retrieve the first shape in the document (searches recursively)
        Shape targetShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (targetShape == null)
        {
            Console.WriteLine("No shape found in the document.");
            return;
        }

        // Continue with shadow settings...
```

**لماذا نفعل ذلك:**  
* `Document` هو نقطة الدخول لأي ملف Word.  
* `GetChild(NodeType.Shape, 0, true)` يتجول في شجرة العقد بالكامل، مما يضمن عدم تفويت الأشكال المتداخلة.  
* فحص الـ null يمنع حدوث `NullReferenceException` إذا كان الملف خاليًا من الأشكال—حالة حافة يتغافل عنها كثير من المبتدئين.

---

## الخطوة 2 – ضبط مسافة الظل والضبابية {#add-shadow-effect-step2}

الظل ليس مجرد لون؛ إزاحته ونعومته مهمان بنفس القدر. لنُبعد الظل بضع نقاط ونضيف له ضبابية خفيفة.

```csharp
        // Step 3: Set how far the shadow is offset from the shape
        targetShape.ShadowFormat.Distance = 4.0;   // 4 points offset

        // Step 4: Define the softness of the shadow edges
        targetShape.ShadowFormat.BlurRadius = 2.0; // 2 points blur
```

**التوضيح:**  
* **Distance** يتحكم في إزاحة X/Y. القيمة `4.0` تحرك الظل إلى الأسفل وإلى اليمين، محاكاةً لمصدر ضوء من أعلى اليسار.  
* **BlurRadius** يحدد مدى نعومة الحافة. الرقم المنخفض يبقي الظل حادًا؛ الرقم الأعلى يجعله يبدو كوهج ناعم.

إذا أردت اتجاه إضاءة مختلف، يمكنك أيضًا تعديل `ShadowFormat.Angle` (الافتراضي 45°).  

---

## الخطوة 3 – تغيير لون الظل وضبط الشفافية {#add-shadow-effect-step3}

الآن للجزء الممتع—تغيير اللون وجعل الظل شبه شفاف. هنا يأتي دور الكلمات المفتاحية الثانوية **change shadow color** و**how to set transparency**.

```csharp
        // Step 5: Choose a colour for the shadow
        targetShape.ShadowFormat.Color = Color.DarkGray; // Change shadow color here

        // Step 6: Make the shadow partially transparent (30 % transparent)
        targetShape.ShadowFormat.Transparency = 0.3; // Value between 0 (opaque) and 1 (fully transparent)
```

**لماذا هذا مهم:**  
* `Color.DarkGray` هو اختيار آمن يعمل على الخلفيات الفاتحة والداكنة على حد سواء. يمكنك استبداله بـ `Color.FromArgb(255, 0, 0, 0)` للحصول على أسود نقي أو أي قيمة ARGB مخصصة.  
* ضبط `Transparency` إلى `0.3` يمنحك تأثير شفافية بنسبة 30 %—يكفي لإظهار العمق دون إخفاء الشكل الأساسي.  

**حالة حافة:** بعض إصدارات Word القديمة تتجاهل الشفافية على أنواع معينة من الأشكال (مثل WordArt). إذا لاحظت أن الظل يبقى غير شفاف، جرّب تحويل الشكل إلى صورة أولًا.

---

## الخطوة 4 – حفظ النتيجة والتحقق منها {#add-shadow-effect-step4}

بعد تعديل الظل، نكتب المستند مرة أخرى إلى القرص. فتح الملف في Word يجب أن يُظهر ظلًا ملونًا شبه شفاف حول الشكل.

```csharp
        // Step 7: Save the modified document
        doc.Save("Resources/output_with_shadow.docx");
        Console.WriteLine("Shadow effect applied successfully. Check output_with_shadow.docx.");
    }
}
```

**قائمة التحقق من التحقق:**  

1. افتح `output_with_shadow.docx` في Microsoft Word.  
2. انقر على الشكل → Format → Shape Effects → Shadow.  
3. يجب أن ترى ظلًا رماديًا داكنًا، إزاحته ~4 pt، مع ضبابية، وشفافية 30 %.  

إذا ظهر أي شيء غير صحيح، أعد فحص خصائص `ShadowFormat`—خاصة `Distance` و`Transparency`.  

---

## الاختلافات الشائعة وسيناريوهات "ماذا لو" {#add-shadow-effect-variations}

### إضافة ظل إلى عدة أشكال

إذا كنت بحاجة إلى **add shape shadow** لكل شكل في المستند، استبدل جلب الشكل الفردي بحلقة تكرار:

```csharp
        NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
        foreach (Shape shp in shapes)
        {
            shp.ShadowFormat.Distance = 5.0;
            shp.ShadowFormat.BlurRadius = 3.0;
            shp.ShadowFormat.Color = Color.Black;
            shp.ShadowFormat.Transparency = 0.4;
        }
```

### استخدام لون مخصص مع ألفا

أحيانًا تريد أن يكون لون الظل نفسه شبه شفاف. اجمع بين `Color.FromArgb` و`Transparency` للحصول على تأثير طبقي:

```csharp
        // Semi‑transparent blue shadow
        targetShape.ShadowFormat.Color = Color.FromArgb(180, 0, 0, 255); // 180/255 ≈ 70% opacity
        targetShape.ShadowFormat.Transparency = 0.2; // Additional 20% transparency
```

### معالجة الأشكال داخل مجموعة

الأشكال المجمعة تُخزن كعقدة `GroupShape`. البحث التكراري الذي استخدمناه (العلم `true`) يغوص بالفعل داخل المجموعات، ولكن إذا أردت التعامل مع المجموعة ككيان واحد، حوّل إلى `GroupShape` وتكرّر على `ChildNodes` الخاصة بها.

```csharp
        GroupShape group = targetShape.ParentNode as GroupShape;
        if (group != null)
        {
            foreach (Shape inner in group.GetChildNodes(NodeType.Shape, true))
            {
                // Apply same shadow settings to each inner shape
                inner.ShadowFormat = targetShape.ShadowFormat.Clone();
            }
        }
```

---

## نصائح احترافية ومخاطر محتملة {#add-shadow-effect-tips}

* **نصيحة احترافية:** أثناء التجربة، اضبط `ShadowFormat.Visible = true` صراحة. بعض الـ APIs تخفي الظل حتى يتغير أحد الخصائص.  
* **احذر من:** إعداد Word “No Outline” قد يجعل الظل يبدو منفصلًا. تأكد من أن نمط خط الشكل مرئي إذا أردت أن يكمل الظل الشكل.  
* **ملاحظة الأداء:** تحديث آلاف الأشكال في مستند كبير قد يكون بطيئًا. اجمع التغييرات ونفّذ `doc.UpdatePageLayout()` مرة واحدة في النهاية.  
* **التوافق:** Aspose.Words 23.10+ يدعم بالكامل خصائص الظل لملفات DOCX، لكن الإصدارات الأقدم قد تتجاهل `BlurRadius`. اختبر دائمًا مع نسخة المكتبة التي تستخدمها.

---

## مثال كامل يعمل {#add-shadow-effect-complete}

فيما يلي البرنامج الكامل جاهز للنسخ واللصق. يتضمن جميع توجيهات `using`، معالجة الأخطاء، وتعليقات توضيحية.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the document that already contains a shape.
        Document doc = new Document("Resources/input.docx");

        // Retrieve the first shape (recursively searches groups).
        Shape targetShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (targetShape == null)
        {
            Console.WriteLine("No shape found in the document.");
            return;
        }

        // Apply shadow distance and blur.
        targetShape.ShadowFormat.Distance = 4.0;      // Offset from shape
        targetShape.ShadowFormat.BlurRadius = 2.0;   // Soft edges

        // Change shadow color and set transparency.
        targetShape.ShadowFormat.Color = Color.DarkGray; // Change shadow color
        targetShape.ShadowFormat.Transparency = 0.3;     // How to set transparency (30%)

        // Save the modified document.
        doc.Save("Resources/output_with_shadow.docx");
        Console.WriteLine("Shadow effect applied successfully. Check output_with_shadow.docx.");
    }
}
```

تشغيل هذا البرنامج سينتج `output_with_shadow.docx` مع **add shadow effect** الذي طلبته. افتح الملف، وسترى ظلًا رماديًا داكنًا، ضبابيًا، وشفافيته 30 %—تمامًا كما تتوقع في عرض تقديمي احترافي.

---

## الخلاصة

لقد أظهرنا لك كيفية **add shadow effect** إلى شكل في Word باستخدام C#. من خلال تحميل المستند، تحديد الشكل، تعديل خصائص `ShadowFormat`، وحفظ الملف، تحصل على تحكم كامل في **change shadow color**، **how to set transparency**، و**add shape shadow** خلال دقائق قليلة.  

في الخطوة التالية، قد ترغب في **apply shadow color** بشكل شرطي—ربما ظلال أغمق للأشكال الكبيرة أو ألوان مختلفة بناءً على إدخال المستخدم. أو استكشاف تحسينات بصرية أخرى مثل التوهج، الانعكاس، أو الحواف ثلاثية الأبعاد. نمط `ShadowFormat` نفسه يعمل مع تلك الميزات، لذا أنت الآن مجهز لتوسيع هذا الدرس أكثر.

هل لديك أسئلة أو صادفت حالة حافة غريبة؟ اترك تعليقًا أدناه، ودعنا نحل المشكلة معًا. برمجة سعيدة، ولتكن مستنداتك دائمًا ذات عمق إضافي!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}