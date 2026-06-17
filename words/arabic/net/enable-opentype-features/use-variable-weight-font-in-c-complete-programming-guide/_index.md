---
category: general
date: 2026-06-02
description: تعلم كيفية استخدام الخط بوزن متغير في C# وتعيين وزن الخط برمجياً مع تغيير
  كود تمدد الخط للخطوط الديناميكية.
draft: false
keywords:
- use variable weight font
- set font weight programmatically
- change font stretch code
- variable font Aspose.Words
- dynamic typography C#
language: ar
og_description: استخدم خطًا بوزن متغير في C# لتعيين وزن الخط برمجيًا وتغيير شفرة تمدد
  الخط، مما يتيح طباعة ديناميكية في مستنداتك.
og_title: استخدام خط الوزن المتغيّر في C# – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  headline: Use Variable Weight Font in C# – Complete Programming Guide
  type: TechArticle
- description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  name: Use Variable Weight Font in C# – Complete Programming Guide
  steps:
  - name: What if the font doesn’t appear at all?
    text: '- **Missing FontSettings**: Double‑check that `doc.FontSettings = fontSettings;`
      is executed **before** any text is added. - **Incorrect family name**: Use `fontSettings.GetFonts()`
      to list all discovered families; copy the exact string. - **Unsupported weight/stretch**:
      Some variable fonts only sup'
  - name: Can I change the weight after the document is saved?
    text: Yes. The `Run` object is mutable, so you can adjust `FontWeight` or `FontStretch`
      at any point before the final `Save`. If you need to toggle weights dynamically
      (e.g., based on user interaction), consider generating separate runs for each
      state.
  - name: Does this work with DOCX output?
    text: Absolutely. The variable‑weight metadata is stored in the underlying OpenXML,
      and modern versions of Word can interpret it. However, older Word versions may
      ignore the stretch setting.
  type: HowTo
tags:
- C#
- Aspose.Words
- Variable Fonts
title: استخدام خط الوزن المتغيّر في C# – دليل برمجي شامل
url: /ar/net/enable-opentype-features/use-variable-weight-font-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# استخدم خطًا بوزن متغيّر في C# – دليل برمجة شامل

هل احتجت يومًا إلى **استخدام خط بوزن متغيّر** في مشروع .NET لكن لم تكن متأكدًا من كيفية جعل الوزن والتمدد يستجيبان لإدخال المستخدم؟ لست وحدك. في العديد من سيناريوهات واجهة المستخدم أو التقارير تريد أن يتكيف النص — ربما عنوان خفيف يصبح غامقًا عند التحويم، أو فقرة تتوسع عرضها للتأكيد. الخبر السار هو أنه مع Aspose.Words يمكنك **تعيين وزن الخط برمجيًا** وحتى **تغيير رمز تمدد الخط** في الوقت الفعلي.

في هذا الدرس سنستعرض مثالًا عمليًا يوضح بالضبط كيفية تحميل خط بوزن متغيّر، تطبيق وزن مخصص، وتعديل إعداد التمدد — كل ذلك مع كود C# واضح يمكنك نسخه ولصقه. في النهاية ستحصل على تطبيق console قابل للتنفيذ ينتج ملف PDF يعرض التأثير.

---

## ما الذي ستحتاجه

- **Aspose.Words for .NET** (الإصدار 23.12 أو أحدث). المكتبة تدعم بالكامل الخطوط ذات الوزن المتغيّر.
- مجلد يحتوي على ملف خط بوزن متغيّر واحد على الأقل، مثل *RobotoFlex‑Variable.ttf*. يمكنك تنزيله من Google Fonts.
- .NET 6 SDK (أو أي نسخة حديثة من .NET) وبيئة تطوير IDE التي تفضلها.
- معرفة أساسية بـ C# — لا شيء معقد، مجرد بضع أسطر من الكود.

هذا كل ما تحتاجه. لا توجد حزم NuGet إضافية بخلاف Aspose.Words، ولا ملفات إعدادات غامضة.

---

![مثال على استخدام خط بوزن متغيّر](https://example.com/variable-weight-sample.png "عرض توضيحي لاستخدام خط بوزن متغيّر")

*نص بديل: لقطة شاشة تُظهر استخدام خط بوزن متغيّر في مستند PDF مُولَّد.*

---

## الخطوة 1: إعداد FontSettings وتوجيهه إلى مجلد الخطوط الخاص بك  

أولًا وقبل كل شيء — تحتاج Aspose.Words إلى معرفة مكان وجود خطوط الوزن المتغيّر. يتم ذلك بإنشاء كائن `FontSettings` وإرفاق `FolderFontSource`. العلامة `true` تُخبر المحرك بالبحث في المجلدات الفرعية أيضًا، وهو مفيد إذا كنت تحتفظ بعدة عائلات خطوط معًا.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create FontSettings and point to the folder containing variable‑weight fonts
var fontSettings = new FontSettings();
fontSettings.SetFontSources(new FontSourceBase[]
{
    new FolderFontSource(@"C:\MyProject\Fonts\", true) // Adjust path to your own directory
});
```

**لماذا هذا مهم:** بدون تسجيل المجلد، ستعود Aspose.Words إلى خطوط النظام وستتجاهل بيانات الوزن المتغيّر المدمجة في ملف الخط المخصص الخاص بك. هذه الخطوة هي الأساس لكل ما يلي.

---

## الخطوة 2: ربط FontSettings بالمستند  

الآن ننشئ `Document` جديد (أو نحمل مستندًا موجودًا) ونخبره باستخدام `FontSettings` التي أعددناها للتو. هذا الربط هو ما يجعل بيانات الوزن المتغيّر متاحة لكل `Run` نضيفه لاحقًا.

```csharp
// Step 2: Attach the FontSettings to the document
var doc = new Document();          // Starts with a blank document
doc.FontSettings = fontSettings;   // Connects our custom fonts
```

إذا كان لديك قالب مسبق — مثل ملف Word يحتوي على عناصر نائبة — يمكنك استبدال `new Document()` بـ `new Document("Template.docx")`. سيُطبق نفس `FontSettings`.

---

## الخطوة 3: إضافة Run من النص سيستخدم خط الوزن المتغيّر  

الـ **Run** هو أصغر وحدة لتنسيق النص في Aspose.Words. سننشئ واحدة، ندرجها في فقرة جديدة، ثم نغيّر خصائص الخط لاحقًا.

```csharp
// Step 3: Add a run of text that will use the variable‑weight font
var paragraph = new Paragraph(doc);
doc.FirstSection.Body.AppendChild(paragraph);

var run = new Run(doc, "Variable‑weight text demo");
paragraph.AppendChild(run);
```

في هذه المرحلة سيُعرض النص باستخدام الخط الافتراضي (عادةً Times New Roman). السحر يحدث عندما نعيّن عائلة الخط المتغيّر.

---

## الخطوة 4: اختيار عائلة الخط المتغيّر  

هنا نبدأ فعليًا **باستخدام خط بوزن متغيّر**. عيّن `Font.Name` إلى اسم العائلة بالضبط كما هو معرف داخل ملف الخط المتغيّر. بالنسبة لـ Roboto Flex، الاسم هو `"Roboto Flex"`.

```csharp
// Step 4: Choose the variable‑weight font family
run.Font.Name = "Roboto Flex";
```

إذا لم تكن متأكدًا من اسم العائلة، افتح ملف `.ttf` في عارض خطوط أو استخدم طريقة `fontSettings.GetFonts()` لاستعراض العائلات المتاحة.

---

## الخطوة 5: تعيين وزن الخط والتمدد برمجيًا  

الآن نصل إلى جوهر الدرس: **نعيّن وزن الخط برمجيًا** و**نغيّر رمز تمدد الخط**. كلا الخاصيتين تقبلان قيمًا عددية تتطابق مع مواصفات OpenType.

```csharp
// Step 5: Specify the desired weight and stretch for the run
run.Font.FontWeight = 300;   // Light weight (300)
run.Font.FontStretch = 125; // Expanded stretch (125% of normal width)
```

- **FontWeight**: 100 (نحيف) → 900 (أسود). اختر أي قيمة يدعمها الخط المتغيّر.
- **FontStretch**: 50 (مكثف جدًا) → 200 (ممتد جدًا). القيمة الافتراضية هي 100 (عادي).

> **نصيحة احترافية:** ليس كل خط متغيّر يُظهر النطاق الكامل. إذا عيّنت قيمة غير مدعومة، سيقوم المحرك بتقريبها إلى أقرب وزن أو تمدد متاح.

---

## الخطوة 6: حفظ المستند والتحقق من النتيجة  

أخيرًا، احفظ المستند كملف PDF (أو DOCX) وافتحه لترى التأثير. الـ PDF صيغة ممتازة للتحقق البصري لأن العرض يكون ثابتًا عبر المنصات.

```csharp
// Step 6: Save the document as PDF
doc.Save(@"C:\MyProject\Output\VariableWeightDemo.pdf", SaveFormat.Pdf);
```

عند فتح *VariableWeightDemo.pdf*، يجب أن ترى العبارة “Variable‑weight text demo” مُعرضة بنسخة خفيفة وممتدة قليلًا من Roboto Flex. غيّر `FontWeight` إلى `700` و`FontStretch` إلى `80` وأعد التشغيل — راقب النص يتحول إلى غامق وأكثر تكثفًا.

---

## أسئلة شائعة وحالات خاصة  

### ماذا لو لم يظهر الخط مطلقًا؟  

- **غياب FontSettings**: تأكد من تنفيذ `doc.FontSettings = fontSettings;` **قبل** إضافة أي نص.
- **اسم عائلة غير صحيح**: استخدم `fontSettings.GetFonts()` لسرد جميع العائلات المكتشفة؛ انسخ السلسلة بالضبط.
- **وزن/تمدد غير مدعوم**: بعض الخطوط المتغيّرة تدعم فقط جزءًا من نطاق 100‑900 للوزن. استخدم `run.Font.FontWeight = 400;` كخيار آمن.

### هل يمكن تغيير الوزن بعد حفظ المستند؟  

نعم. كائن `Run` قابل للتعديل، لذا يمكنك تعديل `FontWeight` أو `FontStretch` في أي وقت قبل استدعاء `Save` النهائي. إذا احتجت لتبديل الأوزان ديناميكيًا (مثلاً بناءً على تفاعل المستخدم)، فكر في إنشاء Runs منفصلة لكل حالة.

### هل يعمل هذا مع مخرجات DOCX؟  

بالتأكيد. تُحفظ بيانات الوزن المتغيّر في بنية OpenXML الأساسية، ويمكن لإصدارات Word الحديثة تفسيرها. ومع ذلك، قد تتجاهل إصدارات Word القديمة إعداد التمدد.

---

## مثال كامل يعمل  

فيما يلي برنامج console كامل يمكنك تجميعه وتشغيله فورًا. يتضمن جميع توجيهات `using` اللازمة، معالجة الأخطاء، وتعليقات توضيحية.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace VariableWeightDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure FontSettings
            var fontSettings = new FontSettings();
            fontSettings.SetFontSources(new FontSourceBase[]
            {
                // 👉 Point to your local folder containing the variable‑weight font files
                new FolderFontSource(@"C:\MyProject\Fonts\", true)
            });

            // 2️⃣ Create the document and attach FontSettings
            var doc = new Document();
            doc.FontSettings = fontSettings;

            // 3️⃣ Build a paragraph with a run of text
            var paragraph = new Paragraph(doc);
            doc.FirstSection.Body.AppendChild(paragraph);
            var run = new Run(doc, "Variable‑weight text demo");
            paragraph.AppendChild(run);

            // 4️⃣ Apply the variable‑weight font family
            run.Font.Name = "Roboto Flex";

            // 5️⃣ Set weight (300 = Light) and stretch (125 = Expanded)
            run.Font.FontWeight = 300;   // set font weight programmatically
            run.Font.FontStretch = 125; // change font stretch code

            // 6️⃣ Save as PDF to verify the rendering
            string outputPath = @"C:\MyProject\Output\VariableWeightDemo.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}");
            Console.WriteLine("Open the PDF to see the light, expanded Roboto Flex text.");
        }
    }
}
```

**الناتج المتوقع:** يطبع الـ console مسار الحفظ، ويظهر الـ PDF المُولَّد النص بنمط خفيف وممتد — تمامًا ما قمنا بإعداده.

---

## ملخص  

غطّينا كيفية **استخدام خط بوزن متغيّر** في C# مع Aspose.Words، وأظهرنا كيفية **تعيين وزن الخط برمجيًا**، ووضحنا **رمز تغيير تمدد الخط** اللازم لتوسيع أو تضييق الحروف. الخطوات بسيطة: ضبط `FontSettings`، ربطها بـ `Document`، إنشاء `Run`، اختيار عائلة الخط المتغيّر، وأخيرًا تعديل `FontWeight` و`FontStretch`.

---

## ما التالي؟  

- **دمج ديناميكي في الواجهة**: اربط المنطق نفسه بتطبيق WinForms أو WPF لتسمح للمستخدمين باختيار الوزن/التمدد عبر أشرطة تمرير.
- **عدة Runs**: اجمع عدة Runs بأوزان مختلفة داخل الفقرة نفسها لإنشاء تسلسلات طباعية غنية.
- **محاور متقدمة**: بعض الخطوط المتغيّرة توفر محاور إضافية (مثل الميل، الحجم البصري). استخدم `run.Font.FontStyle` أو استكشف `FontVariationSettings` لمزيد من التحكم الدقيق.
- **نصائح الأداء**: خزن كائن `FontSettings` في الذاكرة عند معالجة مستندات متعددة لتجنب فحص المجلدات المتكرر.

لا تتردد في التجربة — استبدل *Roboto Flex* بـ *Inter Variable* أو أي خط OpenType متغيّر آخر، وستلاحظ كيف تضيف مستنداتك مستوى جديدًا من المرونة البصرية. برمجة سعيدة!

## ما الذي ينبغي أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تُكمل التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Use Font From Target Machine](/words/english/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Use Font From Target Machine](/words/german/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Use Font From Target Machine](/words/french/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}