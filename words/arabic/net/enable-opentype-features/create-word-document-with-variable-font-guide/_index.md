---
category: general
date: 2026-03-19
description: إنشاء مستند Word باستخدام Aspose.Words وخط متغيّر. تعلّم كيفية تغيير
  وزن الخط، ضبط عرض الخط، وتعريف تباين الخط في C#.
draft: false
keywords:
- create word document
- change font weight
- set font width
- load variable font
- define font variation
language: ar
og_description: إنشاء مستند Word باستخدام خط متغير باستخدام Aspose.Words. يوضح لك
  هذا البرنامج التعليمي كيفية تحميل الخط، وتغيير وزن الخط، وتعيين عرض الخط، وتحديد
  تنوع الخط.
og_title: إنشاء مستند Word بخط متغيّر – دليل كامل
tags:
- Aspose.Words
- C#
- Variable Font
title: إنشاء مستند Word بخط متغير – دليل
url: /ar/net/enable-opentype-features/create-word-document-with-variable-font-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word بخط متغير – دليل

هل احتجت يومًا إلى **إنشاء مستند word** يستخدم خطًا متغيرًا حديثًا، لكنك لم تكن متأكدًا من أين تبدأ؟ لست وحدك. في العديد من المشاريع—مثل التقارير الديناميكية أو الكتيبات المتسقة مع العلامة التجارية—إمكانية **تغيير وزن الخط** في الوقت الفعلي تُعدّ تغييرًا جذريًا.

في هذا البرنامج التعليمي سنستعرض العملية بالكامل: من تحميل خط متغير إلى Aspose.Words، إلى ضبط وزنه وعرضه، وأخيرًا حفظ ملف DOCX يبدو تمامًا كما صممته. لا مراجع غامضة، فقط كود ملموس يمكنك وضعه في مشروع C# الآن.

## ما ستتعلمه

- كيفية **تحميل ملفات الخط المتغير** إلى Aspose.Words باستخدام `FontSettings`.
- الصياغة الخاصة **بتعريف محاور تباين الخط** مثل `wght` (الوزن) و `wdth` (العرض).
- طرق **ضبط عرض الخط** و **تغيير وزن الخط** على `Run` واحد.
- نصائح لتجاوز المشكلات الشائعة (غياب الحروف، مسارات المجلد غير الصحيحة، إلخ).
- مثال كامل قابل للتنفيذ يمكنك نسخه‑ولصقه واختباره فورًا.

> **المتطلبات المسبقة**: .NET 6+ (أو .NET Framework 4.6+)، Aspose.Words for .NET مثبت عبر NuGet، وملف خط متغير مثل *RobotoFlex.ttf* موجود في مجلد *Fonts* المحلي.

---

## الخطوة 1 – تحميل الخط المتغير إلى Aspose.Words

أولًا، يجب أن نخبر Aspose.Words أين يبحث عن الخطوط المخصصة. تقوم فئة `FontSettings` بهذه المهمة.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Configure Aspose.Words to use the folder that contains the variable font
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);

// Apply the settings globally (optional but convenient)
FontSettings.DefaultInstance = fontSettings;
```

**لماذا هذا مهم**: بدون تسجيل المجلد، يلجأ Aspose.Words إلى خطوط النظام ويتجاهل أي بيانات تباين OpenType تحاول تطبيقها لاحقًا. بتوجيهه إلى دليل محدد تضمن أن *RobotoFlex* (أو أي خط متغير آخر) يُعثر عليه في كل مرة يُشغل فيها الكود.

> **نصيحة احترافية**: اضبط المعامل الثاني لـ `SetFontsFolder` إلى `true` إذا أردت أن يبحث Aspose أيضًا في المجلدات الفرعية. هذا مفيد عندما تنظم الخطوط حسب النمط أو الوزن.

---

## الخطوة 2 – إنشاء مستند جديد وإضافة نص تجريبي

الآن بعد أن علم محرك الخطوط مكان البحث، نقوم بإنشاء `Document` فارغ ونضيف فقرة تحتوي على `Run`.

```csharp
// Create a fresh, empty document
Document document = new Document();

// Add a new paragraph to the first section
Paragraph paragraph = new Paragraph(document);
Run variableRun = new Run(document, "Variable‑weight text");

// Attach the run to the paragraph, then the paragraph to the document body
paragraph.AppendChild(variableRun);
document.FirstSection.Body.AppendChild(paragraph);
```

**ما يحدث**: يمثل `Run` قطعة متصلة من النص بتنسيق موحد. بإنشائه أولًا، نبقي منطق التنسيق معزولًا—مما يسهل تطبيق محاور تباين مختلفة على `Run`s منفصلة إذا لزم الأمر.

---

## الخطوة 3 – تعريف محاور التباين المطلوبة (الوزن والعرض)

تكشف الخطوط المتغيرة عن *محاور* يمكنك تعديلها في وقت التشغيل. الأكثر شيوعًا هما `wght` (وزن الخط) و `wdth` (عرض الخط). تمثل فئة `OpenTypeFontVariation` هذه المحاور في Aspose.Words.

```csharp
// Build a collection of variation axes
OpenTypeFontVariation variationAxes = new OpenTypeFontVariation
{
    // Change the weight to 700 (roughly Bold) and width to 100 (normal width)
    { "wght", 700 },
    { "wdth", 100 }
};
```

**لماذا هذه القيم**: في مواصفة OpenType، يتراوح `wght` من الحد الأدنى إلى الحد الأقصى للوزن في الخط (غالبًا 100–900). القيمة **700** تعطي مظهرًا غامقًا. يعمل `wdth` بالمثل؛ **100** يعني العرض الافتراضي (العادي)، بينما القيم الأقل من 100 تُضغط الحروف.

> **حالة حافة**: بعض الخطوط المتغيرة لا تدعم محورًا معينًا. إذا زودت علامة غير مدعومة، سيتجاهل Aspose ذلك بصمت. تحقق دائمًا من مواصفات الخط (عادةً في بيانات تعريف ملف `.ttf` أو `.otf`).

---

## الخطوة 4 – تطبيق التباين على الـ Run باستخدام اسم الخط

الآن نربط بيانات التباين بالنص الفعلي. تحتفظ فئة `FontInfo` باسم عائلة الخط ومجموعة المحاور.

```csharp
// Assign the variable font and its axes to the run's FontInfo
variableRun.Font.FontInfo = new FontInfo("RobotoFlex", variationAxes);
```

**شرح**: عبر تعيين `FontInfo`، نتجاوز الخاصية المعتادة `Font.Name` ونمرر للمحرك تكوينًا كاملًا للخط. هذه هي الطريقة الوحيدة لإخبار Aspose.Words باستخدام خط متغير مع محاور مخصصة.

> **خطأ شائع**: نسيان مطابقة اسم العائلة بالضبط داخل ملف الخط (`RobotoFlex` في هذا المثال). أي خطأ إملائي سيجعل Aspose يلجأ إلى خط افتراضي، وستفقد التباين.

---

## الخطوة 5 – حفظ المستند والتحقق من النتيجة

أخيرًا، نكتب المستند إلى القرص. سيحتوي ملف DOCX المُولَّد على تعليمات الخط المتغير، والتي يمكن لـ Microsoft Word (2016+) عرضها بشكل صحيح.

```csharp
// Save the document; Word will render the variable font with the specified weight and width
document.Save(@"C:\MyProject\Output\VariableFont.docx");
```

افتح الملف الناتج في Word، حدد النص، وانظر إلى مربع حوار **الخط**. يجب أن ترى *Roboto Flex* مدرجًا، وسيظهر النص أكثر سمكًا من المحتوى المحيط—تمامًا ما طلبه إعداد `wght = 700`.

> **نصيحة التحقق**: إذا بدا النص دون تغيير، تأكد من أن ملف الخط يدعم محور `wght`. بعض الخطوط “المتغيرة” لا تعرض سوى `ital` (مائل) أو `opsz` (حجم بصري).

---

## اختياري: إضافة المزيد من التباين – تغيير العرض ديناميكيًا

إذا أردت *ضبط عرض الخط* بشكل مختلف لفقرة أخرى، كرر الخطوات 3‑4 مع مجموعة `OpenTypeFontVariation` جديدة.

```csharp
// Example: widen the text to 115% (condensed vs expanded)
OpenTypeFontVariation wideAxes = new OpenTypeFontVariation
{
    { "wght", 500 },   // regular weight
    { "wdth", 115 }    // slightly expanded width
};

Run wideRun = new Run(document, "Expanded width text");
wideRun.Font.FontInfo = new FontInfo("RobotoFlex", wideAxes);
Paragraph wideParagraph = new Paragraph(document);
wideParagraph.AppendChild(wideRun);
document.FirstSection.Body.AppendChild(wideParagraph);
```

الآن لديك `Run`ين—أحدهما غامق، والآخر أوسع قليلًا—مما يوضح كلًا من **تغيير وزن الخط** و **ضبط عرض الخط** في نفس المستند.

---

## مثال كامل يعمل

انسخ المقتطف أدناه إلى تطبيق console جديد (`Program.cs`) وشغّله. تأكد من أن مجلد `Fonts` يحتوي على `RobotoFlex.ttf` (أو أي خط متغير تفضله).

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the variable font
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);
        FontSettings.DefaultInstance = fontSettings;

        // 2️⃣ Create a document and a run
        Document doc = new Document();
        Paragraph para = new Paragraph(doc);
        Run run = new Run(doc, "Variable‑weight text");
        para.AppendChild(run);
        doc.FirstSection.Body.AppendChild(para);

        // 3️⃣ Define variation axes (weight = 700, width = 100)
        OpenTypeFontVariation axes = new OpenTypeFontVariation
        {
            { "wght", 700 },
            { "wdth", 100 }
        };

        // 4️⃣ Apply the variation using the font name
        run.Font.FontInfo = new FontInfo("RobotoFlex", axes);

        // 5️⃣ Save the result
        doc.Save(@"C:\MyProject\Output\VariableFont.docx");
    }
}
```

**الناتج المتوقع**: ملف `VariableFont.docx` حيث تظهر العبارة “Variable‑weight text” بالخط الغامق، بفضل محور `wght = 700`، مع الحفاظ على العرض الافتراضي.

---

## الأسئلة المتكررة وحالات الحافة

| السؤال | الجواب |
|----------|--------|
| *ماذا لو لم يتم العثور على الخط؟* | تحقق من مسار المجلد، تأكد من مطابقة اسم الملف، وتأكد من أن العملية لديها صلاحيات القراءة. يمكنك أيضًا استدعاء `fontSettings.GetFonts()` لسرد الخطوط المكتشفة. |
| *هل يمكن دمج عدة Runs مع تباينات مختلفة؟* | بالتأكيد. كل `Run` يمكنه حمل `FontInfo` خاص به. كرر الخطوات 3‑4 لكل Run. |
| *هل تدعم إصدارات Word القديمة الخطوط المتغيرة؟* | قدم Word 2016 (Build 16.0.8001) دعمًا أساسيًا. إذا استهدفت إصدارات أقدم، سيتراجع المستند إلى أقرب نسخة ثابتة من الخط. |
| *هل هناك حد لعدد المحاور التي يمكن ضبطها؟* | يمكنك ضبط أي عدد يحدده الخط. العلامات الشائعة هي `wght`, `wdth`, `ital`, `opsz`, `GRAD`. توفير علامة غير مدعومة لا يؤثر سوى بعدم حدوث أي تغيير. |
| *كيف أُصحح نقص الحروف؟* | استخدم `FontSettings.GetFontSources()` لفحص الخطوط المحملة، و`FontInfo.HasGlyph(char)` لاختبار الأحرف الفردية. |

---

## الخلاصة

في بضع خطوات أظهرنا **كيفية إنشاء مستند word** يستفيد من قوة الخطوط المتغيرة، مما يتيح لك **تغيير وزن الخط**، **ضبط عرض الخط**، **تحميل ملفات الخط المتغيرة**، و**تعريف محاور تباين الخط**—كل ذلك باستخدام Aspose.Words for .NET.

الفكرة الأساسية بسيطة: سجِّل مجلد الخطوط، صِف المحاور المطلوبة، اربطها بـ `Run`، ثم احفظ. من هنا يمكنك توسيع التقنية لتشمل أقسامًا كاملة، جداول، أو حتى توليد تقارير مخصصة للعلامة التجارية برمجيًا.

**الخطوات التالية**: جرّب استبدال `RobotoFlex` بخط متغير آخر، جرب محور `ital` (مائل)، أو أنشئ نسخة PDF من نفس المستند باستخدام Aspose.PDF. النمط نفسه يُطبق—تحميل، تعريف، تطبيق، حفظ.

برمجة سعيدة، واستمتع بالمرونة التي توفرها الخطوط المتغيرة في مشاريع أتمتة Word الخاصة بك!

<img src="variable-font-demo.png" alt="Create word document with variable font example">

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}