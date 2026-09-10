---
category: general
date: 2026-01-05
description: كيفية التقاط الخطوط بسرعة ومعالجة الخطوط المفقودة باستخدام Aspose.Words.
  تعلّم حلاً خطوة‑بخطوة مع كود C# كامل.
draft: false
keywords:
- how to capture fonts
- handle missing fonts
- Aspose.Words warnings
- font substitution callback
- missing font detection
language: ar
og_description: كيفية التقاط الخطوط في Aspose.Words ومعالجة الخطوط المفقودة. اتبع
  هذا الدليل التفصيلي للحصول على تنفيذ موثوق بلغة C#.
og_title: كيفية التقاط الخطوط في Aspose.Words – دليل كامل
tags:
- Aspose.Words
- C#
- Document Processing
title: كيفية التقاط الخطوط في Aspose.Words – دليل كامل
url: /ar/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية التقاط الخطوط في Aspose.Words – دليل شامل

هل تساءلت يومًا **كيف يتم التقاط الخطوط** عند تحميل مستند Word باستخدام Aspose.Words؟ لست وحدك. فقدان الخطوط يمكن أن يسبب تشوهات طفيفة في التخطيط، وبدون تحذير مناسب قد لا تلاحظ ذلك حتى يبدو ملف PDF النهائي غير صحيح. في هذا الدرس سنوضح لك بالضبط كيفية التقاط الخطوط **و** التعامل مع الخطوط المفقودة بحيث يبقى الناتج مثاليًا على مستوى البكسل.

سنستعرض سيناريو واقعي، ونقوم بإعداد رد نداء تحذيري، ونزودك بمثال C# جاهز للتنفيذ. بنهاية الدرس ستعرف لماذا هذا مهم، وكيفية تنفيذه، وما الذي يجب الانتباه إليه عندما تختفي الخطوط من بيئتك.

## ما ستتعلمه

- كيفية تكوين **LoadOptions** للاستماع إلى التحذيرات المتعلقة بالخطوط.  
- دور **IWarningCallback** و **WarningInfo** في Aspose.Words.  
- نصائح عملية لاستكشاف الأخطاء وتسجيل الخطوط المفقودة.  
- عينة شفرة كاملة ومستقلة يمكنك لصقها في Visual Studio وتشغيلها فورًا.

**المتطلبات المسبقة:** .NET 6+ (أو .NET Framework 4.7.2+)، Aspose.Words for .NET مثبت عبر NuGet، ومعرفة أساسية بـ C#. لا توجد مكتبات أخرى مطلوبة.

---

## الخطوة 1: إعداد Load Options لالتقاط الخطوط

أول شيء نحتاجه هو كائن **LoadOptions**. هذا الكائن يخبر Aspose.Words كيف يتصرف أثناء قراءة المستند. من خلال تعيين **IWarningCallback** مخصص يمكننا اعتراض أي تحذيرات استبدال خطوط تحدث أثناء عملية التحميل.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Loading;

// Prepare load options and attach a warning callback
LoadOptions loadOptions = new LoadOptions
{
    // The callback will be invoked for every warning Aspose.Words raises
    WarningCallback = new FontWarningCollector()
};
```

**لماذا هذا مهم:**  
Aspose.Words يستبدل الخطوط المفقودة بصمت بخط افتراضي ما لم تطلب منه إبلاغك. من خلال توصيل رد نداء، نحن **نلتقط معلومات الخطوط** في وقت التحميل، مما يمنحنا فرصة لتسجيلها أو استبدالها أو حتى إيقاف العملية.

> **نصيحة احترافية:** احتفظ بـ `loadOptions` كمتغير قابل لإعادة الاستخدام إذا كنت تعالج العديد من المستندات في دفعة. هذا يجنبك إعادة إنشاء نفس رد النداء مرارًا وتكرارًا.

---

## الخطوة 2: تحميل المستند باستخدام الخيارات المكوَّنة

الآن بعد أن تم إعداد رد النداء، نقوم بتحميل المستند. مُنشئ **Document** يقبل المسار و **LoadOptions** التي قمنا بتكوينها للتو.

```csharp
// Replace with the actual path to your .docx file
string inputPath = @"C:\Docs\input.docx";

Document doc = new Document(inputPath, loadOptions);
```

إذا كان هناك أي خط مفقود، سيطلق Aspose.Words تحذيرًا سيتلقاه `FontWarningCollector` الخاص بنا. سيظل المستند يُحمَّل، لكن ستحصل على سجل واضح للخطوط التي تم استبدالها.

---

## الخطوة 3: تنفيذ FontWarningCollector – التعامل مع الخطوط المفقودة

جوهر **كيفية التقاط الخطوط** يكمن في فئة `FontWarningCollector`. هي تنفذ `IWarningCallback` وتصفِّي فقط أحداث `WarningType.FontSubstitution`.

```csharp
// Helper class that receives warning callbacks from Aspose.Words
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We care exclusively about font substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // Log the warning – you could also write to a file or database
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**شرح:**  
- `info.Type` يخبرنا بفئة التحذير. من خلال التحقق من `FontSubstitution` نحن **نتعامل مع الخطوط المفقودة** دون إغراق المخرجات برسائل غير ذات صلة (مثل الميزات المهجورة).  
- `info.Description` يحتوي على رسالة قابلة للقراءة للإنسان مثل “Font 'Comic Sans MS' was substituted with 'Arial'.” هذه هي البيانات التي تحتاجها لتدقيق مخزون الخطوط لديك.

> **احذر:** إذا كنت بحاجة إلى إيقاف المعالجة عندما يكون خط حاسم مفقودًا، ارمي استثناءً داخل كتلة `if` بدلاً من مجرد الطباعة.

---

## الخطوة 4: التحقق من النتيجة – ما المتوقع

شغّل البرنامج من وحدة التحكم أو بيئة التطوير المتكاملة. لكل خط مفقود، ستظهر لك سطر مثل:

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
```

إذا كانت جميع الخطوط موجودة، سيبقى رد النداء صامتًا وسيتم تحميل المستند دون أي مشكلة. يمكنك الآن المتابعة بأمان لحفظ أو تحويل أو طباعة المستند، مع الثقة أنك **قمت بالتقاط معلومات الخطوط**.

---

## الخطوة 5: مثال كامل يعمل (جميع الأجزاء معًا)

فيما يلي البرنامج الكامل الجاهز للنسخ واللصق. يتضمن توجيهات using، وتنفيذ رد النداء، وعرضًا صغيرًا لحفظ المستند المحمَّل كملف PDF.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Loading;

namespace FontCaptureDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Configure load options with our warning collector
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // 2️⃣ Path to the source DOCX (adjust as needed)
            string inputPath = @"C:\Docs\input.docx";

            // 3️⃣ Load the document – any missing fonts trigger our callback
            Document doc = new Document(inputPath, loadOptions);

            // 4️⃣ Optional: Save as PDF to see the final result
            string outputPdf = @"C:\Docs\output.pdf";
            doc.Save(outputPdf);

            Console.WriteLine("Document processed successfully.");
        }
    }

    // 5️⃣ Our custom warning collector – handles missing fonts
    class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // You could log to a file, raise an event, or collect into a list
                Console.WriteLine($"Font substitution detected: {info.Description}");
            }
        }
    }
}
```

**تشغيل الكود:**  
1. أنشئ مشروع وحدة تحكم جديد (`dotnet new console -n FontCaptureDemo`).  
2. أضف حزمة Aspose.Words (`dotnet add package Aspose.Words`).  
3. استبدل ملف `Program.cs` الذي تم إنشاؤه بالمقتطف أعلاه.  
4. ضع ملف DOCX يشير عمدًا إلى خط غير موجود لديك (مثال: “Papyrus”).  
5. نفّذ (`dotnet run`). راقب وحدة التحكم لرسائل الاستبدال، ثم افتح `output.pdf` للتحقق من التخطيط.

---

## أسئلة شائعة وحالات خاصة

### ماذا لو احتجت قائمة الخطوط المفقودة لاحقًا؟

احفظ الرسائل في `List<string>` داخل `FontWarningCollector` وعرّفها عبر خاصية. بهذه الطريقة يمكنك كتابة القائمة إلى ملف سجل بعد معالجة العديد من المستندات.

### هل يعمل هذا مع الملفات المشفرة أو المحمية بكلمة مرور؟

نعم، لكن يجب أيضًا توفير كلمة المرور عبر `LoadOptions.Password`. يعمل رد النداء بنفس الطريقة بمجرد فك تشفير المستند.

### هل يمكنني استبدال خط مفقود بخط احتياطي مخصص؟

بالطبع. داخل طريقة `Warning` يمكنك استدعاء `doc.FontSettings.SubstitutionSettings.FontSubstitutes.AddMissing("MissingFont", "MyFallback")`. هذا يضمن أن يكون الاستبدال حتميًا.

### هل سيؤثر هذا على الأداء؟

العبء إضافي قليل — في الأساس استدعاء طريقة لكل تحذير. في دفعة من آلاف المستندات، يكون التأثير ضئيلًا مقارنةً بتكلفة الإدخال/الإخراج لتحميل كل ملف.

---

## الخلاصة

لقد غطينا **كيفية التقاط الخطوط** في Aspose.Words، وأظهرنا لك كيف **تتعامل مع الخطوط المفقودة** باستخدام رد نداء تحذيري نظيف، وقد قدمنا مثالًا كاملًا وقابلًا للتنفيذ. من خلال ربط هذا النمط في خط أنابيب معالجة المستندات الخاص بك، لن تُفاجأ مرة أخرى بالاستبدالات الصامتة للخطوط.

هل أنت مستعد للخطوة التالية؟ جرّب توسيع المجمع لكتابة سجلات JSON، أو دمجه مع لوحة مراقبة، أو تضمين الخطوط المفقودة تلقائيًا في ملف PDF الناتج. الاحتمالات لا حصر لها، والآن لديك أساس قوي.

برمجة سعيدة! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}