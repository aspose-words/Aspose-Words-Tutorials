---
category: general
date: 2026-03-16
description: تعلم كيفية استخدام FontSettings في Aspose.Words للتعامل مع الخطوط المفقودة
  بسلاسة—الكود الكامل، معالجة الأحداث، ونصائح أفضل الممارسات.
draft: false
keywords:
- how to use fontsettings
- handle missing fonts
- Aspose.Words font substitution
- missing font detection C#
- document loading options
language: ar
og_description: كيفية استخدام FontSettings في Aspose.Words للتعامل مع الخطوط المفقودة—دليل
  خطوة بخطوة مع مثال كامل بلغة C# ونصائح عملية.
og_title: كيفية استخدام FontSettings لمعالجة الخطوط المفقودة في Aspose.Words
tags:
- Aspose.Words
- C#
- Font Management
title: كيفية استخدام FontSettings لمعالجة الخطوط المفقودة في Aspose.Words
url: /ar/net/working-with-fonts/how-to-use-fontsettings-to-handle-missing-fonts-in-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية استخدام FontSettings لمعالجة الخطوط المفقودة في Aspose.Words

هل تساءلت يومًا **كيف تستخدم FontSettings** عندما تشير مستندات Word الخاصة بك إلى خطوط غير مثبتة على الخادم؟ لست وحدك. يمكن أن تتسبب الخطوط المفقودة في بدائل غير جذابة أو حتى إلقاء استثناءات، وغالبًا ما يتجاهل معظم المطورين المشكلة حتى تظهر في بيئة الإنتاج.  

في هذا الدرس سنوضح لك بالضبط **كيف تستخدم FontSettings** لـ **معالجة الخطوط المفقودة** في Aspose.Words، مع التقاط التحذيرات التفصيلية، والحفاظ على سلوك عرض المستند بشكل متوقع. في النهاية ستحصل على عينة C# جاهزة للتنفيذ، وتفهم سبب أهمية كل سطر، وتعرف كيف تُكيّف الحل للمشاريع الأكبر.

## ما يغطيه هذا الدليل

- إعداد **FontSettings** والاشتراك في حدث `SubstitutionWarning`.  
- ربط الإعدادات بـ `LoadOptions` حتى تُحترم أثناء تحميل المستند.  
- تشغيل مستند اختبار يفتقد الخطوط عمدًا وقراءة مخرجات وحدة التحكم.  
- نصائح لتسجيل التحذيرات، وتعطيل الاستبدال التلقائي، ومعالجة الحالات الخاصة مثل وجود عدة خطوط مفقودة.  

لا تحتاج إلى أي وثائق خارجية — كل ما تحتاجه موجود هنا.

## المتطلبات المسبقة

- .NET 6+ (أو .NET Framework 4.6.2+).  
- Aspose.Words for .NET 23.9 أو أحدث (واجهة البرمجة التي نستخدمها مستقرة عبر الإصدارات الأخيرة).  
- ملف `.docx` بسيط يحتوي على خط تعرف أنه غير مثبت (مثال: *Comic Sans MS* على حاوية Linux).  

هذا كل شيء — لا توجد حزم NuGet إضافية بخلاف Aspose.Words.

## لماذا معالجة الخطوط المفقودة مهمة

عندما يشير المستند إلى خط لا يستطيع وقت التشغيل العثور عليه، تقوم Aspose.Words تلقائيًا باستبداله بأقرب خط متاح. هذا الاستبدال قد يكون مقبولًا في كثير من الأحيان، لكن أحيانًا تحتاج إلى **تسجيل** الخطوط المفقودة (لأغراض الامتثال) أو **منع** الاستبدال تمامًا (مثلاً للملفات PDF الخاصة بالعلامة التجارية). من خلال ربط `FontSettings.SubstitutionWarning`، تحصل على رؤية كاملة وتحكم كامل.

## الخطوة 1: إنشاء FontSettings والاشتراك في حدث التحذير Substitution‑Warning

الخطوة الأولى هي إنشاء كائن `FontSettings`. هذا الكائن يحمل جميع إعدادات الخطوط للمكتبة. الجزء الحاسم هو ربط حدث `SubstitutionWarning`، الذي يُطلق **في كل مرة** لا تستطيع Aspose.Words العثور على الخط المطلوب.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – Initialise FontSettings and listen for missing‑font warnings
FontSettings fontSettings = new FontSettings();

// The lambda receives detailed info about the missing font and the chosen substitute.
fontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.MissingFontName  → the name Aspose.Words tried to load.
    // e.SubstitutedFontName → the font that was actually used instead.
    // e.WarningType → the enum describing why the warning was raised.
    Console.WriteLine($"Missing font: {e.MissingFontName}");
    Console.WriteLine($"Substituted with: {e.SubstitutedFontName}");
    Console.WriteLine($"Reason: {e.WarningType}");
};
```

**لماذا هذا مهم:**  
- **الرؤية:** تعرف فورًا أي خطوط غائبة.  
- **القابلية للتدقيق:** يمكن توجيه وحدة التحكم (أو مسجل الأحداث) إلى ملف لتقارير الامتثال.  
- **التحكم:** لاحقًا يمكنك استبدال الاستبدال بخط مخصص خاص بك.

> **نصيحة احترافية:** إذا كنت تفضل إطار تسجيل (Serilog، NLog، إلخ)، استبدل استدعاءات `Console.WriteLine` بـ `logger.Information(...)`.

## الخطوة 2: ربط FontSettings بـ LoadOptions

`LoadOptions` هو الوسيلة التي تخبر Aspose.Words كيف تتعامل مع الملف أثناء مرحلة التحميل. من خلال تعيين كائن `FontSettings`، تضمن أن معالج التحذير نشط *قبل* تحليل أي محتوى.

```csharp
// Step 2 – Bind FontSettings to LoadOptions so the loader knows about our event handler
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**لماذا هذا مهم:**  
- إذا قمت بتحميل مستند دون تمرير `LoadOptions`، سيُطبق التعامل الافتراضي مع الخطوط وستفوتك التحذيرات.  
- يتيح لك هذا النهج أيضًا تعديل سلوكيات التحميل الأخرى (مثل حماية كلمة المرور) في نفس الكائن.

## الخطوة 3: تحميل المستند باستخدام الخيارات المكوَّنة

الآن نقرأ ملف Word. يمكن أن يكون المسار مطلقًا أو نسبيًا؛ ستلتزم Aspose.Words بـ `LoadOptions` التي أعددناها للتو.

```csharp
// Step 3 – Load the document while applying our FontSettings
string docPath = @"YOUR_DIRECTORY/MissingFonts.docx";   // <-- adjust to your environment
Document document = new Document(docPath, loadOptions);
```

إذا كان المستند يحتوي على خط غير مثبت، سيُطلق حدث `SubstitutionWarning`، وستظهر لك مخرجات مشابهة للمثال أدناه.

### مخرجات وحدة التحكم المتوقعة

```
Missing font: Comic Sans MS
Substituted with: Arial
Reason: FontSubstitution
```

قد يختلف الاستبدال الفعلي بناءً على سلسلة استبدال الخطوط في نظام التشغيل، لكن **اسم الخط المفقود** سيُذكر دائمًا.

## الخطوة 4: التحقق من النتيجة (عرض اختياري)

غالبًا ما ترغب في التأكد من أن المستند لا يزال يبدو جيدًا بعد الاستبدال. طريقة سريعة هي حفظه كملف PDF وفتح النتيجة.

```csharp
// Optional: Save as PDF to visually confirm the substitution
document.Save(@"OUTPUT/Result.pdf", SaveFormat.Pdf);
Console.WriteLine("Document saved as PDF – check the rendering.");
```

إذا كنت بحاجة إلى **منع** الاستبدال تمامًا، اضبط `FontSettings.SubstitutionSettings.TableSubstitution = false` قبل التحميل. عندها ستُطلق Aspose.Words استثناءً للخطوط المفقودة، ويمكنك التقاطه ومعالجته.

```csharp
// Disable automatic substitution – will raise an exception on missing fonts
fontSettings.SubstitutionSettings.TableSubstitution = false;
```

## مثال كامل يعمل

فيما يلي البرنامج الكامل الجاهز للتنفيذ. الصقه في تطبيق Console، عدّل مسار الملف، واضغط **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create FontSettings and hook the warning event
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionWarning += (sender, e) =>
            {
                Console.WriteLine($"Missing font: {e.MissingFontName}");
                Console.WriteLine($"Substituted with: {e.SubstitutedFontName}");
                Console.WriteLine($"Reason: {e.WarningType}");
            };

            // 2️⃣ Attach FontSettings to LoadOptions
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings
                // Uncomment the next line to *disable* substitution and force an exception
                // , FontSettings = { SubstitutionSettings = { TableSubstitution = false } }
            };

            // 3️⃣ Load the document
            string docPath = @"YOUR_DIRECTORY/MissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save as PDF to see the visual result
            doc.Save(@"OUTPUT/Result.pdf", SaveFormat.Pdf);
            Console.WriteLine("Processing complete. Check the console for missing‑font warnings.");
        }
    }
}
```

### ما يمكن توقعه

- ستطبع وحدة التحكم كل خط مفقود مع الخط المستبدل المختار.  
- إذا احتفظت بالحفظ الاختياري إلى PDF، سيظهر المستند باستخدام الخط البديل، مما يضمن سلامة التخطيط.

## أسئلة شائعة وحالات خاصة

| السؤال | الجواب |
|----------|--------|
| **ماذا لو كان هناك عدة خطوط مفقودة؟** | يُطلق الحدث مرة واحدة لكل خط مفقود، لذا ستحصل على سطر سجل منفصل لكل منها. |
| **هل يمكنني استبدال الخط الافتراضي بخط مخصص؟** | نعم. داخل معالج الحدث يمكنك استدعاء `e.SubstitutedFont = new FontInfo("MyCustomFont")`. |
| **هل يُرفع التحذير للخطوط المدمجة التي فشل تحميلها؟** | بالتأكيد — سواء كان الخط خارجيًا أو مدمجًا، فإن آلية التحذير هي نفسها. |
| **هل يجب إغلاق كائن `Document`؟** | `Document` يطبق `IDisposable`. استخدم كتلة `using` إذا كنت تقوم بتحميل العديد من الملفات داخل حلقة. |
| **هل سيعمل هذا على حاويات Linux؟** | طالما أن Aspose.Words يمكنه العثور على خطوط النظام (مثلاً عبر `fontconfig`)، فإن آلية الحدث نفسها تعمل. |

## أفضل الممارسات ونصائح احترافية

- **مركزة التسجيل:** أنشئ طريقة مساعدة تكتب لكل من وحدة التحكم وملف سجل دائم.  
- **معالجة دفعات:** عند تحويل عشرات المستندات، أعد استخدام نفس كائن `FontSettings` لتجنب الاشتراكات المتكررة للحدث.  
- **الأداء:** تحذيرات الاستبدال تضيف عبئًا ضئيلًا، لكن إذا كنت تعالج آلاف الملفات، ففكر في تعطيلها بعد التحقق من مجموعة الخطوط.  
- **أمان الإصدارات:** واجهة `SubstitutionWarning` مستقرة منذ Aspose.Words 16.0، لذا يمكنك الاعتماد عليها في الترقيات المستقبلية.

## الخلاصة

لقد استعرضنا **كيفية استخدام FontSettings** في Aspose.Words لـ **معالجة الخطوط المفقودة** بطريقة أنيقة. من خلال إنشاء كائن `FontSettings`، الاشتراك في `SubstitutionWarning`، وتحميل المستندات عبر `LoadOptions`، تحصل على رؤية كاملة لمشكلات الخطوط وتقرر ما إذا كنت ستسجلها أو تستبدلها أو توقف العملية عند حدوث نقص.  

من مخرجات وحدة التحكم البسيطة إلى منطق الاستبدال المخصص، يمكن توسيع النمط ليشمل خطوط أنابيب معالجة المستندات الضخمة، مما يضمن بقاء المخرجات متسقة وقابلة للتدقيق.

**الخطوات التالية:**  

- استكشف **استبدال الخطوط المخصص** عبر تعيين `e.SubstitutedFont` داخل الحدث.  
- اجمع هذا النهج مع **تحويل المستند إلى صور** لإنشاء صور مصغرة.  
- انظر إلى **Aspose.PDF** إذا كنت بحاجة إلى تضمين الخطوط المستبدلة مباشرة في ملف PDF النهائي لضمان قابلية النقل الكاملة.

Happy coding, and may your documents never suffer from a rogue missing font again!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}