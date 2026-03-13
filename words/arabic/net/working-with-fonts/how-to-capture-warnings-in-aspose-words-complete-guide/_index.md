---
category: general
date: 2026-03-13
description: كيفية التقاط التحذيرات عند تحميل المستندات باستخدام Aspose.Words، بالإضافة
  إلى نصائح للتعامل مع الخطوط المفقودة وتعيين إعدادات الخط المخصصة. تعلم حلًا كاملًا
  بلغة C#.
draft: false
keywords:
- how to capture warnings
- handle missing fonts
- set custom font settings
language: ar
og_description: كيفية التقاط التحذيرات عند تحميل ملفات Word باستخدام Aspose.Words،
  بالإضافة إلى طرق عملية للتعامل مع الخطوط المفقودة وتعيين إعدادات الخطوط المخصصة.
og_title: كيفية التقاط التحذيرات في Aspose.Words – دليل كامل
tags:
- Aspose.Words
- C#
- Document Processing
title: كيفية التقاط التحذيرات في Aspose.Words – الدليل الكامل
url: /ar/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-guide/
---

cell content but keep markdown table pipes.

Also bullet lists.

Let's produce final answer.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية التقاط التحذيرات في Aspose.Words – دليل كامل

هل تساءلت يومًا **كيف يمكنك التقاط التحذيرات** التي تظهر عندما يقوم Aspose.Words بتحميل مستند؟ في العديد من المشاريع الواقعية ستصادف تنبيهات استبدال الخطوط، ملاحظات حول ميزات مهجورة، أو حتى رسائل متعلقة بالأمان. تجاهلها يشبه القيادة بزجاج أمامي متشقق—قد تصل إلى وجهتك، لكنك لن تعرف متى سيحدث عطل ما.

الخبر السار هو أن Aspose.Words يوفّر لك طريقة نظيفة تعتمد على رد نداء (callback) لالتقاط تلك الرسائل. في هذا الدرس سنستعرض **مثال كامل بلغة C#** لا يقتصر فقط على التقاط التحذيرات بل يوضح أيضًا **كيفية التعامل مع الخطوط المفقودة** و**ضبط إعدادات الخطوط المخصصة** بحيث يتم عرض مستنداتك بالضبط كما تتوقع.

---

## ما ستتعلمه

- ضبط `LoadOptions` لتوصيل كائن `FontSettings` مخصص.  
- تسجيل رد نداء للتحذير يفلتر أحداث `FontSubstitution`.  
- إخراج تفاصيل التحذير إلى وحدة التحكم (أو أي مسجل تفضله).  
- توسيع الحل للتعامل بأناقة مع الخطوط المفقودة عبر منصات مختلفة.  

بنهاية هذا الدليل ستحصل على مقتطف جاهز للتنفيذ يمكنك إدراجه في أي مشروع .NET، بالإضافة إلى مجموعة من النصائح العملية لتجنب الأخطاء الشائعة.

---

## المتطلبات المسبقة

| المتطلب | لماذا يهم |
|-------------|----------------|
| **Aspose.Words for .NET** (v23.12 أو أحدث) | الـ API التي نستخدمها (`LoadOptions`, `IWarningCallback`) موجودة هنا. |
| **.NET 6+** (أو .NET Framework 4.7.2+) | ميزات اللغة الحديثة تجعل الكود أنظف. |
| **ملف DOCX تجريبي** (اسمه `input.docx`) موجود في مجلد معروف | نحتاج شيئًا لنحمله ونُطلق تحذيرًا. |
| **وحدة تحكم أو إطار تسجيل** (اختياري) | لرؤية التحذيرات الملتقطة قيد التنفيذ. |

لا توجد حزم NuGet إضافية مطلوبة بخلاف Aspose.Words نفسه.

---

## الخطوة 1: إعداد إعدادات خطوط مخصصة  

قبل تحميل المستند يمكنك إخبار Aspose.Words أين يبحث عن الخطوط. هذه هي خطوة **ضبط إعدادات الخطوط المخصصة** في اللغز.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

// 1️⃣ Create a FontSettings instance and point it at your font folder.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// 2️⃣ Plug the FontSettings into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**لماذا هذا مهم:**  
إذا كان ملف DOCX يشير إلى خط غير مثبت على الجهاز، سيستبدل Aspose.Words الخط تلقائيًا *ما لم* تكون قد ضبطت مجلد يحتوي على الخطوط المطلوبة. ضبط مجلد مخصص يقلل من احتمالية ظهور تحذيرات “استبدال الخط” من البداية.

> **نصيحة احترافية:** على نظام Linux قد تحتاج إلى إضافة حزمة `fonts-dejavu-core` أو أي مجموعة خطوط TrueType تعتمد عليها مستنداتك.

---

## الخطوة 2: تسجيل رد نداء للتحذير  

Aspose.Words يطبق `IWarningCallback`. سننشئ معالجًا صغيرًا يطبع فقط التحذيرات التي تهمنا: الخطوط المفقودة أو المستبدلة.

```csharp
// 3️⃣ Register the callback.
loadOptions.WarningCallback = new FontWarningHandler();
```

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warn(IWarningInfo info)
    {
        // Filter for font‑substitution warnings only.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // You could log to a file, send to telemetry, etc.
            Console.WriteLine($"[Font Substitution] {info.Description}");
        }
        // Optionally handle other warning types here.
    }
}
```

**لماذا هذا مهم:**  
سيناريو **التعامل مع الخطوط المفقودة** يصبح مرئيًا الآن. بدلاً من التخمين أي خط تم استبداله، ستحصل على وصف واضح مثل “تم استبدال الخط 'Calibri' بـ 'Arial'”. هذا لا يقدر بثمن عند تصحيح مشاكل التخطيط في ملفات PDF أو التقارير المطبوعة.

---

## الخطوة 3: تحميل المستند باستخدام الخيارات المكوَّنة  

الآن نأتي أخيرًا لتحميل المستند إلى الذاكرة، باستخدام `LoadOptions` التي أعددناها مسبقًا.

```csharp
// 4️⃣ Load the DOCX. Any warnings will flow through FontWarningHandler.
Document doc = new Document(@"C:\Docs\input.docx", loadOptions);

// Quick sanity check – render the first page to PDF (optional).
doc.Save(@"C:\Docs\output.pdf");
Console.WriteLine("Document loaded and saved successfully.");
```

إذا كان الملف المصدر يستخدم خطًا غير موجود في `C:\MyFonts`، ستظهر لك مخرجات مشابهة لـ:

```
[Font Substitution] Font 'OpenSans-Regular' was substituted with 'Arial'.
Document loaded and saved successfully.
```

هذا السطر هو **نتيجة كيفية التقاط التحذيرات** التي كنت تبحث عنها.

---

## الخطوة 4: مثال كامل جاهز (انسخ‑الصق)

فيما يلي البرنامج بالكامل، جاهز للترجمة. الصقه في مشروع وحدة تحكم جديد وشغّله—فقط تأكد من أن المسارات تشير إلى مواقع فعلية على جهازك.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

namespace AsposeWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Prepare LoadOptions with custom FontSettings.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                // Step 2: Attach the warning callback.
                WarningCallback = new FontWarningHandler()
            };

            // -------------------------------------------------
            // Step 3: Load the document – warnings flow to handler.
            // -------------------------------------------------
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath, loadOptions);

            // Optional: Save as PDF to verify rendering.
            string outputPath = @"C:\Docs\output.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any warning messages.");
        }
    }

    // -------------------------------------------------
    // Warning handler that focuses on missing‑font events.
    // -------------------------------------------------
    public class FontWarningHandler : IWarningCallback
    {
        public void Warn(IWarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"[Font Substitution] {info.Description}");
            }
            // You could add more branches for other warning types.
        }
    }
}
```

**المخرجات المتوقعة:**  

- إذا كانت جميع الخطوط متوفرة:  
  `Document processed. Check console for any warning messages.`  

- إذا كان هناك خط مفقود:  
  ```
  [Font Substitution] Font 'Times New Roman' was substituted with 'Arial'.
  Document processed. Check console for any warning messages.
  ```

---

## الخطوة 5: التعديلات الشائعة وحالات الحافة  

| الحالة | ما الذي يجب تعديله |
|-----------|----------------|
| **مجلدات خطوط متعددة** | استدعِ `fontSettings.AddFontFolder(@"C:\MoreFonts", true);` لكل موقع إضافي. |
| **قمع جميع التحذيرات** | نفّذ `Warn` لكن اترك الجسم فارغًا، أو اضبط `loadOptions.WarningCallback = null;`. |
| **التقاط أنواع تحذير أخرى** | قارن `info.WarningType` مع `WarningType.DeprecatedFeature`, `WarningType.UnexpectedContent`, إلخ. |
| **التشغيل على Linux/macOS** | تأكد من أن مجلد الخطوط يحتوي على ملفات `.ttf`/`.otf` متوافقة مع Linux؛ قد تحتاج لتثبيت `libfontconfig`. |
| **المستندات الكبيرة** | فكر في تحميل المستند بشكل متدفق (`LoadOptions.LoadFormat = LoadFormat.Docx;`) لتقليل الضغط على الذاكرة. |

بتوقع هذه السيناريوهات ستتجنب المفاجآت عند الانتقال من بيئة التطوير إلى خط أنابيب CI أو خادم سحابي.

---

## الخطوة 6: تأكيد بصري (اختياري)

إذا كنت تفضّل إشارة بصرية سريعة، يمكنك تفريغ التحذيرات الملتقطة إلى تقرير HTML صغير. إليك مقتطفًا بسيطًا يكتب الرسائل إلى `warnings.html`:

```csharp
using System.IO;
using System.Text;

public class HtmlWarningHandler : IWarningCallback
{
    private readonly StringBuilder _sb = new StringBuilder();

    public void Warn(IWarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            _sb.AppendLine($"<li>{info.Description}</li>");
        }
    }

    public void WriteReport(string path)
    {
        string html = $"<html><body><h2>Font Substitution Warnings</h2><ul>{_sb}</ul></body></html>";
        File.WriteAllText(path, html);
    }
}
```

بعد تحميل المستند، استدعِ `handler.WriteReport(@"C:\Docs\warnings.html");` وافتحه في المتصفح. الصورة أدناه توضح الشكل المحتمل للتقرير:

![How to capture warnings screenshot](/images/capture-warnings.png)

*النص البديل:* **كيفية التقاط التحذيرات** – لقطة شاشة لمخرجات وحدة التحكم وتقرير HTML.

---

## الخاتمة  

لقد غطينا **كيفية التقاط التحذيرات** في Aspose.Words، وأظهرنا طريقة موثوقة **للتعامل مع الخطوط المفقودة**، ووضحنا **كيفية ضبط إعدادات الخطوط المخصصة** لضمان عرض ثابت. المثال الكامل جاهز للإدراج في أي حل .NET، ويمكن توسيع `FontWarningHandler` ليتناسب مع استراتيجيتك في التسجيل أو القياس.

ما الخطوة التالية؟ جرّب استبدال استدعاءات `Console.WriteLine` بمسجل منظم مثل Serilog، أو ادفع التحذيرات إلى Application Insights للمراقبة في الوقت الحقيقي. يمكنك أيضًا استكشاف نمط `DocumentVisitor` إذا احتجت إلى فحص محتوى المستند بعد التحميل.

هل لديك أسئلة حول أنواع تحذير أخرى أو استراتيجيات تضمين الخطوط؟ اترك تعليقًا أدناه—برمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}