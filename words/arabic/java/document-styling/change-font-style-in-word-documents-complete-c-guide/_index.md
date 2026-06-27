---
category: general
date: 2026-06-27
description: تغيير نمط الخط في مستندات Word باستخدام C#. تعلّم كيفية ضبط وزن الخط،
  وتعيين الوزن الغامق، وضبط عرض الخط للحصول على طباعية دقيقة.
draft: false
keywords:
- change font style
- set font weight
- set bold weight
- adjust font width
- modify font in word
language: ar
og_description: غيّر نمط الخط في مستندات Word باستخدام C#. اكتشف كيفية ضبط وزن الخط،
  وتعيين الوزن العريض، وتعديل عرض الخط في بضع خطوات سهلة.
og_title: تغيير نمط الخط في مستندات Word – دليل C# الكامل
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Change font style in Word documents with C#. Learn how to set font
    weight, set bold weight, and adjust font width for precise typography.
  headline: Change Font Style in Word Documents – Complete C# Guide
  type: TechArticle
- description: Change font style in Word documents with C#. Learn how to set font
    weight, set bold weight, and adjust font width for precise typography.
  name: Change Font Style in Word Documents – Complete C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code compiles on .NET Core as well) - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`) - A sample `input.docx`
      placed in a folder you can reference (we’ll call it `YOUR_DIRECTORY`)'
  - name: Expected Result
    text: '- All body text that previously used the default font now appears **bold**
      (weight 700). - If you experimented with `SetWidth(80)`, the characters will
      look a bit tighter; `SetWidth(120)` will spread them out. - No other content
      (images, tables, etc.) is altered—only the font characteristics of text'
  - name: Can I change the font family at the same time?
    text: 'Absolutely. After you’ve set the `FontVariation`, you can also assign a
      new `FontInfo` to the `FontSettings`:'
  - name: What if I need to **set bold weight** only for headings?
    text: 'Retrieve the heading style node and apply a separate `FontSettings` instance:'
  - name: Does this work with .NET Core on Linux?
    text: Yes—Aspose.Words is cross‑platform. Just ensure you have the appropriate
      runtime libraries installed (`libgdiplus` on some distributions) if you plan
      to render the document to PDF later.
  type: HowTo
tags:
- C#
- Aspose.Words
- typography
title: تغيير نمط الخط في مستندات Word – دليل C# الكامل
url: /ar/java/document-styling/change-font-style-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تغيير نمط الخط في مستندات Word – دليل C# كامل

هل احتجت إلى **تغيير نمط الخط** في ملف Word لكن لم تكن متأكدًا من أي استدعاء API يحقق ذلك؟ لست وحدك—معظم المطورين يواجهون هذه المشكلة عند محاولتهم تعديل الطباعة برمجيًا للمرة الأولى.  

الخبر السار هو أنه ببضع أسطر من C# يمكنك **تعيين وزن الخط**، بل وزيادة الوزن إلى غامق، وضبط عرض كل حرف. في هذا الدرس سنستعرض مثالًا كاملاً يمكن تشغيله ي modifies ملف `.docx` من البداية إلى النهاية.

## ما يغطيه هذا الدليل

سنبدأ بتحميل مستند موجود، ثم إنشاء كائن `FontSettings` يحتوي على `FontVariation`. من هناك سنقوم **بتعيين وزن الخط**، **تعيين وزن الغامق**، و**ضبط عرض الخط** قبل تطبيق التغييرات وحفظ النتيجة. لا ملفات تكوين خارجية، لا سلاسل سحرية—فقط C# صافية ومكتبة Aspose.Words. في النهاية ستتمكن من **تعديل الخط في مستندات Word** بثقة، سواء كنت تبني محرك تقارير أو أداة تنسيق جماعية.

### المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يُجمّع أيضًا على .NET Core)  
- حزمة NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- ملف `input.docx` تجريبي موجود في مجلد يمكنك الإشارة إليه (سنسميه `YOUR_DIRECTORY`)  

إذا كان لديك هذه الأساسيات، فلنبدأ.

---

## الخطوة 1: تغيير نمط الخط – تحميل مستند Word

أول شيء تحتاج إلى فعله هو جلب الملف الهدف إلى الذاكرة. فكر في ذلك كفتح لوحة فارغة ستمارس عليها الطباعة الجديدة.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Load the document you want to modify
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded successfully.");
```

> **نصيحة احترافية:** إذا كنت تشغل هذا على خادم بدون واجهة مستخدم، تأكد من أن رخصة Aspose.Words إما في وضع التجربة أو أنك قد طبقت ملف رخصة صحيح لتجنب رسائل العلامة المائية.

---

## الخطوة 2: تعيين وزن الخط وتعيين وزن الغامق

الآن بعد أن أصبح المستند في الذاكرة، ننشئ حاوية `FontSettings`. هذا الكائن هو البوابة لكل تعديل على مستوى الخط يمكنك القيام به.  

فئة `FontVariation` تسمح لك بتحديد ثلاث سمات أساسية:

| الخاصية | ما تقوم به | النطاق المعتاد |
|----------|--------------|---------------|
| `Weight` | يتحكم في مدى ثقل الحرف الظاهر. القيمة **700** هي الغامق القياسي. | 100‑900 |
| `Width`  | يمدد أو يضغط الحرف أفقياً. **100** يعني العرض الطبيعي. | 50‑200 |
| `Slant`  | يضيف ميلًا يشبه المائل. الأرقام الموجبة تميل إلى اليمين. | -90‑90 |

فيما يلي **نُعيّن وزن الخط** إلى 700 (غامق) ونظهر أيضًا كيف يمكنك رفعه أعلى إذا كان الخط يدعم نمط “extra‑bold”.

```csharp
        // Create a FontSettings object to hold customizations
        FontSettings fontSettings = new FontSettings();

        // Define a FontVariation with the desired style attributes
        FontVariation variation = new FontVariation();
        variation.SetWeight(700);   // Set bold weight (standard)
        // variation.SetWeight(800); // Uncomment for extra‑bold if supported
        variation.SetSlant(0);      // No slant – keep upright

        // Attach the variation to the FontSettings
        fontSettings.SetFontVariation(variation);
```

> **لماذا هذا مهم:** تعيين **set bold weight** مباشرة عبر `SetWeight` يتجاوز الحاجة إلى كائن نمط “Bold” منفصل، مما يمنحك تحكمًا دقيقًا في سمك الخطوط.

---

## الخطوة 3: ضبط عرض الخط

إذا احتجت يومًا لجعل الخط يبدو أكثر ضيقًا للعنوان أو أكثر مساحة للفقرة، ستسعد بوصولك إلى هذه الخطوة. خاصية `Width` تفعل ذلك بالضبط.

```csharp
        // Adjust the width of the font – 100 is normal, 80 is condensed, 120 is expanded
        variation.SetWidth(100); // Normal width
        // variation.SetWidth(80);  // Uncomment for a condensed look
        // variation.SetWidth(120); // Uncomment for an expanded look
```

> **خطأ شائع:** ليس كل الخطوط تحترم تغييرات العرض. إذا لم تلاحظ تغييرًا بصريًا، تحقق مما إذا كانت عائلة الخط التي تستخدمها تدعم الأحرف المكثفة/الممتدة.

---

## الخطوة 4: تطبيق إعدادات الخط – تعديل الخط في Word

مع تكوين `FontSettings` بالكامل، الخطوة الأخيرة هي إخبار المستند باستخدامها. هنا نـ **نُعدّل الخط في Word** على مستوى المستند، مؤثرًا على كل تشغيل نصي يرث النمط الافتراضي.

```csharp
        // Apply the FontSettings to the document
        document.FontSettings = fontSettings;
        Console.WriteLine("Font settings applied.");
```

إذا أردت استهداف فقرة أو تشغيل معين فقط، يمكنك استرجاع ذلك العقدة وتعيين `FontSettings` له بشكل فردي. المثال أعلاه يوضح النهج الشامل، وهو مثالي لسيناريوهات التنسيق الجماعي.

---

## الخطوة 5: حفظ والتحقق من التغييرات

الحفظ هو الجزء الأخير، لكنه ليس الأقل أهمية في سير العمل. بعد حفظ الملف يمكنك فتحه في Microsoft Word لرؤية النمط الجديد قيد التنفيذ.

```csharp
        // Save the modified document
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### النتيجة المتوقعة

- كل النص الأساسي الذي كان يستخدم الخط الافتراضي الآن يظهر **غامقًا** (الوزن 700).  
- إذا جربت `SetWidth(80)`، ستظهر الأحرف أكثر ضيقًا؛ `SetWidth(120)` ستوسعها.  
- لا يتم تعديل أي محتوى آخر (صور، جداول، إلخ)—فقط خصائص الخط للنصوص.

افتح `output.docx` في Word، حدد فقرة، وتفقد مربع حوار **Font**. ستلاحظ أن خانة **Bold** مُحددة وأن **Scale** (العرض) يعكس القيمة التي اخترتها.

---

## الأسئلة المتكررة والحالات الخاصة

### هل يمكنني تغيير عائلة الخط في الوقت نفسه؟

بالطبع. بعد تعيين `FontVariation`، يمكنك أيضًا إسناد `FontInfo` جديد إلى `FontSettings`:

```csharp
fontSettings.SetFontsFolder(@"C:\MyFonts\", true); // Point to a folder with custom fonts
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes("Times New Roman", new[] { "MyCustomFont" });
```

### ماذا لو أردت **تعيين وزن الغامق** فقط للعناوين؟

استرجع عقدة نمط العنوان وطبق نسخة منفصلة من `FontSettings`:

```csharp
Style headingStyle = document.Styles["Heading 1"];
headingStyle.Font.Name = "Arial";
headingStyle.Font.Size = 16;
headingStyle.Font.Bold = true; // Quick way for headings only
```

### هل يعمل هذا مع .NET Core على Linux؟

نعم—Aspose.Words متعدد المنصات. فقط تأكد من تثبيت مكتبات التشغيل المناسبة (`libgdiplus` على بعض التوزيعات) إذا كنت تخطط لتحويل المستند إلى PDF لاحقًا.

---

## الخاتمة

لقد قمنا الآن **بتغيير نمط الخط** في مستند Word من البداية إلى النهاية، مغطين كيفية **تعيين وزن الخط**، **تعيين وزن الغامق**، و**ضبط عرض الخط** باستخدام C#. المثال الكامل القابل للتنفيذ يوضح كل استيراد، إنشاء كائن، واستدعاء طريقة، بحيث يمكنك نسخه ولصقه في مشروعك ومشاهدة التحول الط typographic فورًا.

الآن بعد أن عرفت كيف **تعديل الخط في Word**، يمكنك استكشاف مواضيع ذات صلة مثل **إدراج خطوط مخصصة**، **تطبيق تدرجات لونية**، أو **إنشاء جداول ديناميكية**. كل منها يبني على أساس `FontSettings` الذي استخدمناه هنا، لذا أنت بالفعل خطوة أمام الآخرين.

هل لديك سيناريو غير مغطى؟ اترك تعليقًا، وسنستكشفه معًا. برمجة سعيدة—ولتظهر مستنداتك دائمًا كما تريد!  

![change font style example](placeholder.png){alt="مثال على تغيير نمط الخط"}

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [Set Font Emphasis Mark](/words/hindi/net/working-with-fonts/set-font-emphasis-mark/)
- [Set Font Fallback Settings](/words/hindi/net/working-with-fonts/set-font-fallback-settings/)
- [Set Font Formatting](/words/hindi/net/working-with-fonts/set-font-formatting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}