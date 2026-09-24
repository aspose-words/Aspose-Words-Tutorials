---
category: general
date: 2026-02-21
description: تعلم كيفية تمكين التحذيرات، واكتشاف الخطوط المفقودة، وكيفية تحميل ملفات docx
  بأمان باستخدام Aspose.Words في C#. اتبع الدليل خطوةً بخطوة.
draft: false
keywords:
- how to enable warnings
- detect missing fonts
- how to load docx
- font substitution handling
- Aspose.Words warnings
language: ar
og_description: كيفية تمكين التحذيرات، واكتشاف الخطوط المفقودة، وتحميل ملفات docx بشكل
  صحيح باستخدام Aspose.Words. مثال كامل على الكود متضمن.
og_title: كيفية تمكين التحذيرات واكتشاف الخطوط المفقودة عند تحميل ملفات DOCX
tags:
- C#
- Aspose.Words
- Document processing
title: كيفية تمكين التحذيرات واكتشاف الخطوط المفقودة عند تحميل ملفات DOCX
url: /ar/net/working-with-fonts/how-to-enable-warnings-and-detect-missing-fonts-when-loading/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تمكين التحذيرات واكتشاف الخطوط المفقودة عند تحميل ملفات DOCX

هل تساءلت يومًا **كيف يتم تمكين التحذيرات** للخطوط المفقودة قبل أن تتسبب في تشويه عرض المستند بصمت؟ لست وحدك—فمعظم المطورين يفترضون أن المكتبة ستقوم بـ “العمل الصحيح” تلقائيًا، ثم يكتشفون لاحقًا أن خطًا ما تم استبداله دون أي إشارة.

في هذا الدرس سنوضح لك بالضبط **كيف يتم تمكين التحذيرات**، وكيف **تكتشف الخطوط المفقودة**، والطريقة الصحيحة **لتحميل ملف docx** باستخدام Aspose.Words for .NET. في النهاية ستحصل على عينة جاهزة للتنفيذ تطبع كل تحذير استبدال خط إلى وحدة التحكم، حتى لا تضطر أبدًا إلى التخمين ما الذي حدث داخل الملف.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضًا على .NET Framework 4.7+)  
- Visual Studio 2022 أو أي بيئة تطوير C# تفضلها  
- حزمة **Aspose.Words** من NuGet (`Install-Package Aspose.Words`)  
- ملف DOCX قد يحتوي على خطوط غير مثبتة على جهازك (سنسميه `input.docx`)

> **نصيحة محترف:** إذا لم يكن لديك ملف اختبار، افتح مستند Word يستخدم خطًا مخصصًا للشركة واحفظه باسم `input.docx`. سيتسبب ذلك في توليد التحذير الذي نريد التقاطه.

## نظرة عامة على الحل

1. **إنشاء** كائن `LoadOptions` مع تفعيل `FontSubstitutionWarnings`.  
2. **تحميل** ملف DOCX باستخدام هذه الخيارات.  
3. **فحص** مجموعة `WarningCallback` للبحث عن أي إدخالات `FontSubstitution`.  
4. **التفاعل** – يمكنك تسجيل التحذيرات، عرضها، أو حتى استبدال الخط المفقود برمجياً.

فيما يلي نشرح كل خطوة، نوضح *لماذا* هي مهمة، ونزودك بمقتطف كود كامل وقابل للتنفيذ.

---

## الخطوة 1: تثبيت Aspose.Words وإعداد المشروع

قبل أن نتمكن من **كيفية تمكين التحذيرات**، نحتاج إلى المكتبة التي تدعمها فعليًا.

```bash
# Using the .NET CLI
dotnet add package Aspose.Words
```

أو، في وحدة التحكم الخاصة بمدير الحزم في Visual Studio:

```powershell
Install-Package Aspose.Words
```

> **لماذا هذه الخطوة؟**  
> بدون الحزمة، لا وجود لـ `LoadOptions`، `Document`، وبنية التحذيرات. إضافة مرجع NuGet يضمن أنك تحصل على أحدث نسخة مستقرة (في وقت كتابة هذا، 24.5).

---

## الخطوة 2: إنشاء خيارات التحميل التي تمكّن تحذيرات استبدال الخطوط

قلب **كيفية تمكين التحذيرات** يكمن في فئة `LoadOptions`. ضبط `FontSubstitutionWarnings` على `true` يخبر المحرك بتسجيل كل مرة يضطر فيها لاستبدال خط مفقود.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Step 2: Build the options object
LoadOptions loadOptions = new LoadOptions
{
    // This flag makes the library emit warnings for any font it cannot find.
    FontSubstitutionWarnings = true
};
```

> **لماذا نفعّل هذه العلامة؟**  
> بشكل افتراضي، يقوم Aspose.Words باستبدال الخطوط المفقودة بصمت بخط احتياطي (عادةً Arial). قد يؤدي ذلك إلى تغيرات في التخطيط، أو أحرف غير مرئية، أو انتهاك للهوية البصرية. تفعيل العلامة يمنحك رؤية كاملة.

---

## الخطوة 3: تحميل ملف DOCX باستخدام الخيارات المكوّنة

الآن بعد أن عرفنا **كيفية تحميل docx** مع تمكين التحذيرات، نقوم فعليًا بعملية التحميل.

```csharp
// Step 3: Load the document – replace the path with your own file location.
string docPath = @"YOUR_DIRECTORY\input.docx";
Document document = new Document(docPath, loadOptions);
```

> **ماذا يحدث خلف الكواليس؟**  
> أثناء تحليل ملف DOCX، يتحقق Aspose.Words من كل عنصر `<w:rFonts>`. إذا لم يكن الخط المحدد مثبتًا، يسجل تحذير `FontSubstitution` ويستبدله بخط افتراضي. وبما أننا فعلنا التحذيرات، تظهر هذه الإدخالات في `document.WarningCallback.Warnings`.

---

## الخطوة 4: استرجاع وعرض تحذيرات استبدال الخطوط

خاصية `WarningCallback` تحتفظ بـ `WarningInfoCollection`. قم بالتكرار عبرها، صَفِّها لتشمل `WarningType.FontSubstitution`، واطبع الرسائل.

```csharp
// Step 4: Iterate over warnings and print font‑substitution details.
foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substituted: {warning.Message}");
    }
}
```

**الناتج المتوقع** (مثال):

```
⚠️ Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
⚠️ Font substituted: Font 'CorporateLogo' was not found. Substituted with 'Times New Roman'.
```

> **ماذا تفعل بهذه الرسائل؟**  
> يمكنك تسجيلها في ملف، عرضها في واجهة مستخدم، أو حتى تشغيل روتين استبدال خط مخصص. الفكرة هي أنك الآن *تكتشف الخطوط المفقودة* بدلاً من التخمين لاحقًا.

---

## الخطوة 5: (اختياري) استبدال الخطوط المفقودة بخط احتياطي محدد

إذا كان لديك خط شركة تريد فرضه، يمكنك معالجة التحذيرات واستبداله مباشرةً.

```csharp
// Optional: Custom fallback font
string fallbackFont = "Calibri";

foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        // Extract the missing font name from the warning message
        string missingFont = warning.Message.Split('\'')[1];
        Console.WriteLine($"Replacing missing font '{missingFont}' with '{fallbackFont}'");
        document.FontInfos[missingFont].SubstitutedFont = fallbackFont;
    }
}
```

> **لماذا قد ترغب في ذلك؟**  
> يضمن التناسق البصري عبر جميع المستندات المُولدة، وهو أمر حاسم للامتثال للعلامة التجارية.

---

## مثال كامل قابل للتنفيذ

فيما يلي ملف C# واحد يمكنك نسخه‑ولصقه في تطبيق Console. يغطي كل شيء—من تثبيت الحزمة إلى طباعة التحذيرات.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with warnings enabled
            LoadOptions loadOptions = new LoadOptions
            {
                FontSubstitutionWarnings = true
            };

            // 2️⃣ Load the DOCX (adjust the path as needed)
            string docPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Show all font‑substitution warnings
            Console.WriteLine("=== Font Substitution Warnings ===");
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Message}");
                }
            }

            // 4️⃣ (Optional) Replace missing fonts with Calibri
            string fallback = "Calibri";
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    string missingFont = warning.Message.Split('\'')[1];
                    Console.WriteLine($"Replacing '{missingFont}' with '{fallback}'");
                    doc.FontInfos[missingFont].SubstitutedFont = fallback;
                }
            }

            // 5️⃣ Save the corrected document (optional)
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**لتشغيله:** `dotnet run` من مجلد المشروع. إذا كان هناك أي خطوط مفقودة، ستظهر التحذيرات، وسيُطبق الاستبدال الاختياري قبل حفظ الملف.

---

## الأسئلة المتكررة

### هل يعمل هذا مع تحويل PDF أيضًا؟

نعم. بعد معالجة التحذيرات، يمكنك استدعاء `doc.Save("output.pdf")` وستظهر الخطوط المستبدلة في ملف PDF كما هي في DOCX.

### ماذا لو أردت كتم التحذيرات لخط معين؟

يمكنك تصفيتها في الحلقة—تجاهل `WarningInfo` التي يحتوي `Message` الخاص بها على اسم الخط الذي تريد تجاهله.

### هل `FontSubstitutionWarnings` متاح في إصدارات Aspose.Words القديمة؟

تم تقديمه في الإصدار 20.5. إذا كنت تستخدم نسخة أقدم، قم بالترقية عبر NuGet؛ التغيير في الـ API متوافق مع الإصدارات السابقة.

---

## الخلاصة

استعرضنا **كيفية تمكين التحذيرات**، وأظهرنا لك **كيفية اكتشاف الخطوط المفقودة**، وبيّنّا الطريقة الصحيحة **لتحميل docx** باستخدام Aspose.Words مع رؤية كاملة لاستبدالات الخطوط. من خلال فحص `document.WarningCallback.Warnings` تحصل على سجل تدقيق موثوق—لا مزيد من الاستبدالات الصامتة.

الخطوة التالية؟ جرّب ربط منطق التحذير بإطار تسجيل مثل Serilog، أو أنشئ واجهة تُظهر الخطوط المفقودة قبل تسليم المستند للمستخدمين. يمكنك أيضًا استكشاف فئة `FontSettings` لمزيد من التحكم الدقيق في سياسات استبدال الخطوط.

برمجة سعيدة، ولتظهر مستنداتك دائمًا كما تصورت! 

![مخطط يوضح التدفق من تحميل ملف DOCX إلى التقاط تحذيرات استبدال الخطوط – كيفية تمكين التحذيرات في Aspose.Words](/images/font-warning-flow.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}