---
category: general
date: 2026-10-13
description: تعلم استبدال الخطوط في المستند باستخدام C#. يوضح هذا الدليل كيفية تعيين
  ترميز big5، تحميل ملف DOCX، واستبدال الخطوط القديمة بالخطوط الحديثة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- font substitution in document
- big5 encoding
- C# LoadOptions
- legacy font replacement
- document encoding for Chinese
- Docx loading C#
language: ar
lastmod: 2026-10-13
og_description: استبدال الخطوط في المستند أمر أساسي عند التعامل مع ملفات صينية قديمة.
  اتبع هذا الدليل خطوة بخطوة لتحميل ملف DOCX بترميز big5 واستبدال الخطوط القديمة.
og_image_alt: Screenshot of C# code that performs font substitution in document
og_title: استبدال الخط في المستند باستخدام C# – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn font substitution in document using C#. This guide shows how
    to set big5 encoding, load a DOCX, and replace legacy fonts with modern ones.
  headline: How to perform font substitution in document with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Unicode
- Chinese text
title: كيفية تنفيذ استبدال الخط في المستند باستخدام C#
url: /ar/net/working-with-fonts/how-to-perform-font-substitution-in-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# استبدال الخط في المستند – دليل C# كامل

إذا كنت بحاجة إلى **font substitution in document** لعرض ملفات الصينية القديمة بشكل صحيح، يوضح لك هذا الدليل بالضبط كيفية القيام بذلك. من خلال تكوين ترميز النص المناسب واستبدال خط قديم بآخر حديث، تضمن أن ملف DOCX النهائي يُعرض كما هو مقصود.

غالبًا ما يتعطل معالجة المستند عندما يستخدم المصدر ترميزًا قديمًا مثل **big5** أو يشير إلى خط لم يعد موجودًا على النظام. يشرح هذا الدليل كيفية تحميل ملف DOCX بالترميز الصحيح **big5 encoding**، وتطبيق **legacy font replacement**، وإنتاج مخرج نظيف يعمل على أي جهاز Windows.

ستتعلم:

* كيفية إنشاء كائن `LoadOptions` باستخدام **big5 encoding**.  
* كيفية فتح ملف DOCX باستخدام **C# LoadOptions**.  
* كيفية تنفيذ **font substitution in document** عن طريق ربط خط قديم ببديل حديث.  
* التعامل مع الحالات الخاصة للخطوط المفقودة وعائلات الخطوط المتعددة.

لا توجد أدوات خارجية مطلوبة بخلاف مكتبة Aspose.Words for .NET، ويمكن نسخ الكود الكامل إلى مشروع وحدة تحكم وتشغيله فورًا.

## المتطلبات المسبقة

* .NET 6.0 أو أحدث (العينة تستخدم صياغة وحدة تحكم .NET 6).  
* Aspose.Words for .NET – التثبيت عبر `dotnet add package Aspose.Words`.  
* ملف DOCX محفوظ بترميز **big5 encoding** ويشير إلى الخط القديم `MingLiU-ExtB`.  
* إلمام أساسي بـ C# وVisual Studio أو أي بيئة تطوير تفضلها.

## الخطوة 1: إعداد المشروع واستيراد المساحات الاسمية

أنشئ تطبيق وحدة تحكم جديد وأضف توجيهات `using` المطلوبة. هذا يضمن أن الكود يُترجم دون تعديلات إضافية.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The tutorial steps are called from here.
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // Steps 2‑4 are implemented inside this method.
        }
    }
}
```

> **نصيحة احترافية:** احتفظ بطريقة `Main` بسيطة؛ فهذا يحسن القابلية للقراءة ويجعل المتابعة أسهل.

## الخطوة 2: تعريف خيارات التحميل مع ترميز النص الصحيح (big5 للغة الصينية التقليدية)

تُخبر فئة `LoadOptions` مكتبة Aspose.Words كيف تفسر البايتات الخام في الملف المصدر. استخدام **big5 encoding** أمر حاسم لحروف الصينية التقليدية التي تم حفظها بهذه الصفحة الترميزية القديمة.

```csharp
// Step 2: Define load options with big5 encoding.
LoadOptions loadOptions = new LoadOptions
{
    // Explicitly set the encoding to the traditional Chinese code page.
    Encoding = Encoding.GetEncoding("big5")
};
```

**لماذا هذا مهم:** إذا حذفت الترميز أو استخدمت UTF‑8 الافتراضي، قد تظهر الأحرف كرموز مشوشة (mojibake). تحديد `big5` يحافظ على الرموز الأصلية قبل أي استبدال للخط.

## الخطوة 3: تحميل ملف DOCX باستخدام الترميز المحدد

مرّر كائن `loadOptions` إلى مُنشئ `Document`. هذا يحمل الملف مع احترام **document encoding for Chinese** الذي حددته مسبقًا.

```csharp
// Step 3: Load the DOCX file with the big5 encoding.
string inputPath = @"C:\Docs\big5_doc.docx"; // Update this path to your file location.
Document doc = new Document(inputPath, loadOptions);
```

إذا تعذر العثور على الملف، سيطرح البرنامج استثناء `FileNotFoundException`. تأكد من صحة المسار وأن التطبيق يمتلك أذونات القراءة.

## الخطوة 4: استبدال خط قديم ببديل حديث

العديد من المستندات الصينية القديمة تشير إلى الخط `MingLiU-ExtB`، والذي قد لا يكون موجودًا في إصدارات Windows الحديثة. ربطه بـ `Microsoft JhengHei` (خط Unicode متوفر على نطاق واسع) يضمن عرضًا صحيحًا.

```csharp
// Step 4: Perform font substitution in document.
doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

// Optional: Verify that the substitution succeeded.
foreach (FontInfo fontInfo in doc.FontInfos)
{
    Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
}
```

**شرح:**  
* `FontInfos.Substitution.Add(oldFont, newFont)` يسجل قاعدة استبدال عامة. في كل مرة يصادف فيها Aspose.Words الخط `MingLiU-ExtB`، يتم استبداله بـ `Microsoft JhengHei`.  
* الحلقة الاختيارية تطبع خريطة الاستبدال، وهو مفيد للتصحيح في المستندات الكبيرة التي تحتوي على عائلات خطوط متعددة.

## الخطوة 5: حفظ المستند المعالج

بعد الاستبدال، اكتب المستند إلى ملف جديد. سيعرض الناتج النص الصيني باستخدام الخط الحديث، مما يلغي تحذيرات فقدان الحروف.

```csharp
// Step 5: Save the updated document.
string outputPath = @"C:\Docs\big5_doc_fixed.docx";
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to {outputPath}");
```

افتح الملف الناتج في Microsoft Word أو أي عارض DOCX؛ يجب أن ترى حروف الصينية التقليدية معروضة بشكل نظيف باستخدام `Microsoft JhengHei`.

## معالجة الحالات الخاصة والمشكلات الشائعة

| الحالة | النهج الموصى به |
|-----------|----------------------|
| **الخط المصدر غير مدرج في المستند** | استخدم `doc.FontInfos.Substitution.Add` بنمط البدل العام، مثال: `doc.FontInfos.Substitution.Add("*MingLiU*", "Microsoft JhengHei")`. |
| **ضرورة استبدال عدة خطوط قديمة** | استدعِ `Add` لكل زوج، أو حمّل قاموس استبدال من ملف إعدادات. |
| **الخط الهدف غير متوفر على الجهاز الهدف** | اختر خطًا يأتي مع Windows (مثل `Arial Unicode MS`) أو دمج الخط باستخدام `doc.FontInfos.EmbeddingMode = FontEmbeddingMode.EmbedAll`. |
| **ما زالت أخطاء الترميز تظهر** | تحقق من أن الملف المصدر يستخدم فعلاً **big5**؛ يمكنك فحص الملف بمحرر سداسي أو استخدام `File.ReadAllBytes` ومقارنة أنماط البايت. |

## مثال كامل يعمل

فيما يلي البرنامج الكامل المستقل. انسخه إلى `Program.cs`، عدّل مسارات الملفات، ثم شغّله.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // 1️⃣ Define big5 encoding for Traditional Chinese.
            LoadOptions loadOptions = new LoadOptions
            {
                Encoding = Encoding.GetEncoding("big5")
            };

            // 2️⃣ Load the DOCX that uses the legacy font.
            string inputPath = @"C:\Docs\big5_doc.docx";
            Document doc = new Document(inputPath, loadOptions);

            // 3️⃣ Substitute MingLiU-ExtB with Microsoft JhengHei.
            doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

            // 4️⃣ (Optional) Log substitution details for verification.
            foreach (FontInfo fontInfo in doc.FontInfos)
            {
                Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
            }

            // 5️⃣ Save the corrected document.
            string outputPath = @"C:\Docs\big5_doc_fixed.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"✅ Font substitution in document completed. Output saved to {outputPath}");
        }
    }
}
```

**النتيجة المتوقعة:** عند فتح `big5_doc_fixed.docx` ستظهر جميع حروف الصينية التقليدية معروضة بشكل صحيح، دون تحذيرات فقدان الحروف، لأن `MingLiU-ExtB` تم استبداله بـ `Microsoft JhengHei`.

## الخلاصة

أصبحت الآن تمتلك طريقة موثوقة لمهام **font substitution in document** باستخدام C#. من خلال تكوين **big5 encoding**، تحميل ملف DOCX عبر `LoadOptions`، وربط الخطوط القديمة ببدائل حديثة، تتخلص من مشاكل العرض التي تعيق ملفات الصينية القديمة.  

من هنا يمكنك:

* توسيع خريطة الاستبدال لتشمل خطوطًا قديمة إضافية.  
* أتمتة العملية لمجموعة من المستندات (التكرار عبر مجلد).  
* دمج استبدال الخط مع تحولات مستند أخرى مثل إضافة علامة مائية أو تحويل إلى PDF.

لا تتردد في تجربة خطوط هدف مختلفة أو دمج خطوط مخصصة للحصول على قابلية نقل كاملة. إذا واجهت أي مشاكل، راجع جدول الحالات الخاصة أعلاه أو استشر وثائق Aspose.Words لمعالجة الخطوط المتقدمة.

برمجة سعيدة!

## ما الذي ينبغي أن تتعلمه لاحقًا؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك الخاصة.

- [تمكين تحذيرات استبدال الخط في Aspose.Words – دليل كامل](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [تسجيل تحذيرات استبدال الخط – دليل Aspose.Words كامل](/words/english/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/)
- [التحميل مع الترميز في مستند Word](/words/english/net/programming-with-loadoptions/load-with-encoding/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}