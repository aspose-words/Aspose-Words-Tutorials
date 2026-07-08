---
category: general
date: 2026-06-30
description: تعلم كيفية تحميل الخطوط في .NET باستخدام LoadOptions، وضبط إعدادات الخط،
  وتمكين الخطوط المخصصة واكتشاف الخطوط المفقودة عبر ردود التحذير.
draft: false
keywords:
- how to load fonts
- set font settings
- how to handle warnings
- enable custom fonts
- detect missing fonts
language: ar
og_description: كيف تقوم بتحميل الخطوط في .NET؟ يوضح لك هذا الدليل كيفية ضبط إعدادات
  الخط، وتمكين الخطوط المخصصة، واكتشاف الخطوط المفقودة باستخدام ردود التحذير.
og_title: كيفية تحميل الخطوط في .NET – ضبط إعدادات الخط والتحذيرات
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Learn how to load fonts in .NET using LoadOptions, set font settings,
    enable custom fonts and detect missing fonts with warning callbacks.
  headline: How to Load Fonts in .NET – Set Font Settings & Warnings
  type: TechArticle
- description: Learn how to load fonts in .NET using LoadOptions, set font settings,
    enable custom fonts and detect missing fonts with warning callbacks.
  name: How to Load Fonts in .NET – Set Font Settings & Warnings
  steps:
  - name: Creating `LoadOptions` and configuring **set font settings**.
    text: Creating `LoadOptions` and configuring **set font settings**.
  - name: '**Enable custom fonts** by pointing to a folder of extra typefaces.'
    text: '**Enable custom fonts** by pointing to a folder of extra typefaces.'
  - name: '**How to handle warnings** with a `WarningCallback` that prints font substitution
      messages.'
    text: '**How to handle warnings** with a `WarningCallback` that prints font substitution
      messages.'
  - name: '**Detect missing fonts** by filtering `WarningType.FontSubstitution`.'
    text: '**Detect missing fonts** by filtering `WarningType.FontSubstitution`.'
  - name: Saving the document, confirming that the fallback
    text: Saving the document, confirming that the fallback
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: كيفية تحميل الخطوط في .NET – ضبط إعدادات الخط والتحذيرات
url: /ar/net/working-with-fonts/how-to-load-fonts-in-net-set-font-settings-warnings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تحميل الخطوط في .NET – ضبط إعدادات الخطوط والتحذيرات

هل تساءلت يومًا **كيفية تحميل الخطوط** في مستند .NET دون أن تفقد أعصابك؟ لست الوحيد. فقدان الرموز، والبدائل الصامتة، والتحذيرات الغامضة يمكن أن تحول مولد التقارير البسيط إلى كابوس.  

في هذا الدرس سنستعرض مثالًا كاملًا جاهزًا للتنفيذ يوضح **كيفية تحميل الخطوط**، ضبط **إعدادات الخط**، **تمكين الخطوط المخصصة**، و**اكتشاف الخطوط المفقودة** عبر معالجة التحذيرات. في النهاية ستحصل على نمط ثابت يمكنك إدراجه في أي مشروع يستخدم Aspose.Words أو مكتبة مشابهة.

> **نظرة سريعة:** سننشئ كائن `LoadOptions`، نرفق رد نداء للتحذير، ونحمّل ملف DOCX يشير عمدًا إلى خط مفقود. سيطبع الطرفية رسالة واضحة كلما استبدلت المحرك خطًا.

## ما ستحتاجه

- .NET 6.0 أو أحدث (الكود يعمل أيضًا على .NET Framework 4.6+)
- Aspose.Words for .NET (حزمة NuGet التجريبية المجانية تكفي)
- ملف DOCX يشير إلى خط *ليس لديك* مثبت (مثال: `MissingFont.docx`)  

هذا كل شيء—لا خدمات إضافية، ولا ملفات إعدادات غامضة. إذا كان لديك هذه العناصر الثلاثة، فأنت جاهز للمتابعة.

![مخطط مثال تحميل الخطوط](https://example.com/how-to-load-fonts-diagram.png)

*نص بديل للصورة: مخطط مثال تحميل الخطوط*

## الخطوة 1: إنشاء خيارات التحميل وتمكين إعدادات الخط المخصص  

أول شيء تقوم به عندما تريد **ضبط إعدادات الخط** هو إنشاء كائن `LoadOptions`. داخل هذا الكائن تضع مثيلًا من `FontSettings` يشير إلى مجلد يحتوي على أي ملفات .ttf أو .otf مخصصة قد تحتاجها.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Step 1: Create load options and enable custom font settings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // Point to a folder that holds extra fonts (optional but useful)
        loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

**لماذا هذا مهم:** بشكل افتراضي Aspose.Words يبحث فقط عن الخطوط المثبتة على النظام. إذا كان مستندك يستخدم خط علامة تجارية للشركة موجود على مشاركة شبكة، تحتاج إلى إخبار المكتبة بمكان العثور عليه. هذا هو جوهر **تمكين الخطوط المخصصة**.

## الخطوة 2: إرفاق معالج تحذير لاكتشاف الخطوط المفقودة  

إذا تخطيت معالجة التحذيرات، يتم استبدال الرموز المفقودة بهدوء بخط احتياطي—غالبًا Times New Roman. هذا قد يفسد العلامة التجارية أو حتى يسبب تغيرات في التخطيط. لـ **كيفية معالجة التحذيرات**، أرفق رد نداء يفحص `WarningType.FontSubstitution`.

```csharp
        // Step 2: Attach a warning handler to capture font substitution warnings
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution detected: {args.Description}");
        };
```

**نصيحة احترافية:** `WarningCallback` يُطلق لأي تحذير، ليس فقط للخطوط المفقودة. التصفية حسب `WarningType.FontSubstitution` تحافظ على نظافة المخرجات وتجيب مباشرة على سؤال **اكتشاف الخطوط المفقودة**.

## الخطوة 3: تحميل المستند باستخدام الخيارات المكوَّنة  

الآن بعد أن أعددنا الخيارات، يمكننا أخيرًا **تحميل الخطوط** في المستند. مُنشئ `Document` يقبل مسار الملف بالإضافة إلى `LoadOptions` التي أنشأناها للتو.

```csharp
        // Step 3: Load the document using the configured options
        Document doc = new Document(@"C:\Docs\DocWithMissingFont.docx", loadOptions);
```

إذا كان الملف المصدر يشير إلى خط غير موجود في مجلد النظام *أو* المجلد المخصص الذي حددناه مسبقًا, سيطبع رد نداء التحذير من الخطوة 2 سطرًا مفيدًا في الطرفية.

## الخطوة 4: التحقق من مجموعة الخطوط المحملة (اختياري لكن مفيد)  

أحيانًا تريد التحقق مرتين من الخطوط التي تم حلها فعليًا. Aspose.Words يتيح لك الوصول إلى `FontSettings` التي مررت بها، بحيث يمكنك تعداد مصادر الخطوط التي تم حلها.

```csharp
        // Step 4: (Optional) List all font sources that were used
        FontSourcesCollection sources = loadOptions.FontSettings.GetFontSources();
        Console.WriteLine("\nLoaded font sources:");
        foreach (var source in sources)
            Console.WriteLine($"- {source.GetType().Name}");
```

تشغيل هذا المقتطف بعد التحميل سيطبع شيئًا مثل:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was substituted with 'Arial'.
Loaded font sources:
- FolderFontSource
- SystemFontSource
```

سطر التحذير يؤكد أننا نجحنا في **اكتشاف الخطوط المفقودة**، بينما القائمة تُظهر أن مجلدات النظام والمخصصة تم استشارتها.

## الخطوة 5: حفظ أو عرض المستند  

بمجرد تحميل المستند والتحقق من الخطوط، يمكنك المتابعة بأي معالجة—حفظ كملف PDF، عرض كصور، أو تعديل الـ DOM. لإكمال المثال، إليك سطرًا واحدًا يحفظ النتيجة كملف PDF:

```csharp
        // Step 5: Save the document as PDF (fonts now embedded where possible)
        doc.Save(@"C:\Docs\Result.pdf");
        Console.WriteLine("\n✅ Document saved as PDF.");
    }
}
```

عند فتح ملف PDF، سيتم استبدال أي رموز مفقودة بالبديل الذي رأيته في مخرجات الطرفية. إذا أضفت الخط المفقود إلى `C:\MyCustomFonts`، أعد تشغيل البرنامج وستختفي التحذيرات—دليل على أن **تمكين الخطوط المخصصة** يعمل فعلاً.

---

## مثال عملي كامل

انسخ الكتلة الكاملة أدناه إلى مشروع وحدة تحكم جديد، أضف حزمة Aspose.Words عبر NuGet، واضغط **Run**. عدّل مسارات الملفات لتتناسب مع بيئتك.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Create load options and enable custom font settings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };
        // Point to a folder with extra fonts (if you have any)
        loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);

        // 2️⃣ Attach a warning handler to capture font substitution warnings
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {args.Description}");
        };

        // 3️⃣ Load the document using the configured options
        Document doc = new Document(@"C:\Docs\DocWithMissingFont.docx", loadOptions);

        // 4️⃣ (Optional) List loaded font sources for debugging
        FontSourcesCollection sources = loadOptions.FontSettings.GetFontSources();
        Console.WriteLine("\nLoaded font sources:");
        foreach (var source in sources)
            Console.WriteLine($"- {source.GetType().Name}");

        // 5️⃣ Save as PDF – you’ll see the same warnings if fonts were missing
        doc.Save(@"C:\Docs\Result.pdf");
        Console.WriteLine("\n✅ PDF saved successfully.");
    }
}
```

### النتيجة المتوقعة

```
⚠️ Font substitution: Font 'Papyrus' was substituted with 'Arial'.

Loaded font sources:
- FolderFontSource
- SystemFontSource

✅ PDF saved successfully.
```

إذا وضعت ملف `Papyrus.ttf` المفقود في `C:\MyCustomFonts` وشغلت البرنامج مرة أخرى، سيختفي سطر التحذير، مما يؤكد أن المجلد المخصص تم استشارته بشكل صحيح.

---

## أسئلة شائعة ومشكلات محتملة

| السؤال | الجواب |
|----------|--------|
| **ماذا لو لم يكن لدي رد نداء للتحذير؟** | المستند لا يزال يُحمَّل، لكنك لن تعرف متى حدث الاستبدال. إضافة رد النداء هي أبسط طريقة لـ **كيفية معالجة التحذيرات**. |
| **هل يمكنني تحميل الخطوط من ملف zip؟** | نعم—استخدم `new FolderFontSource(zipPath, true)` أو نفّذ `IFontSource` مخصص. هذا لا يزال يندرج تحت **تمكين الخطوط المخصصة**. |
| **هل أحتاج إلى تضمين الخطوط في ملف PDF؟** | عيّن `doc.SaveOptions.PdfSaveOptions.EmbedFullFonts = true;` قبل الحفظ. التضمين يضمن أن يظهر PDF بنفس الشكل على أي جهاز. |
| **ماذا لو كان المستند يستخدم خطًا مرخصًا ولا يمكن إعادة توزيعه؟** | لا يزال بإمكانك *اكتشاف* الخط المفقود عبر التحذيرات، لكن لا يجب تضمينه إلا إذا كان لديك الحقوق. فكر في استبداله بخط مفتوح المصدر مشابه. |

## ملخص

لقد غطينا **كيفية تحميل الخطوط** في .NET عن طريق:

1. إنشاء `LoadOptions` وتكوين **ضبط إعدادات الخط**.  
2. **تمكين الخطوط المخصصة** عبر الإشارة إلى مجلد يحتوي على خطوط إضافية.  
3. **كيفية معالجة التحذيرات** باستخدام `WarningCallback` الذي يطبع رسائل استبدال الخط.  
4. **اكتشاف الخطوط المفقودة** عن طريق تصفية `WarningType.FontSubstitution`.  
5. حفظ المستند، مؤكدًا أن البديل...

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [ضبط مجلدات الخطوط النظامية والمخصصة](/words/english/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/)
- [كيفية اكتشاف الخطوط في Aspose.Words – معالجة التحذيرات والإعدادات](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [كيفية التقاط الخطوط في Aspose.Words – دليل كامل](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}