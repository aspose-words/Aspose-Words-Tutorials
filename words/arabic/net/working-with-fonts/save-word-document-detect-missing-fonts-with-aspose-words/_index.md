---
category: general
date: 2026-03-22
description: احفظ مستند Word واكتشف الخطوط المفقودة باستخدام Aspose.Words. تعلم كيفية
  تتبع الخطوط المفقودة والتقاط أخطاء الخطوط في C#.
draft: false
keywords:
- save word document
- detect missing fonts
- track missing fonts
- capture font errors
language: ar
og_description: احفظ مستند Word واكتشف الخطوط المفقودة في C#. يوضح هذا الدليل كيفية
  تتبع الخطوط المفقودة والتقاط أخطاء الخطوط باستخدام رد نداء تحذيري.
og_title: حفظ مستند Word – اكتشاف الخطوط المفقودة باستخدام Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: حفظ مستند Word – اكتشاف الخطوط المفقودة باستخدام Aspose.Words
url: /ar/net/working-with-fonts/save-word-document-detect-missing-fonts-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ مستند Word – اكتشاف الخطوط المفقودة باستخدام Aspose.Words

هل احتجت يومًا إلى **save word document** لكنك لم تكن متأكدًا مما إذا كانت بعض الخطوط داخل المستند ستبقى بعد عملية الحفظ والتحميل؟ يحدث ذلك أكثر مما تعتقد، خاصةً عندما تنتقل المستندات بين أجهزة ذات مكتبات خطوط مختلفة. الخبر السار؟ توفر لك Aspose.Words طريقة مدمجة لـ **detect missing fonts** أثناء **save word document**، بحيث يمكنك تسجيل التحذيرات أو حتى استبدالها قبل أن يظهر الملف على شاشة المستخدم.

في هذا البرنامج التعليمي سنستعرض مثالًا كاملاً وجاهزًا للتنفيذ لا يقتصر فقط على حفظ مستند Word بل أيضًا **tracks missing fonts** و **captures font errors** باستخدام معالج تحذير مخصص. في النهاية ستعرف بالضبط لماذا يعتبر استدعاء التحذير مهمًا، وكيفية ربطه، وكيف يبدو إخراج وحدة التحكم عندما يحدث استبدال.  
بدون أي إضافات غير ضرورية—فقط الكود الذي يمكنك إدراجه في مشروع .NET الآن.

> **المتطلبات المسبقة**  
> • .NET 6 (or any recent .NET Framework) مثبت  
> • Visual Studio 2022 أو بيئة التطوير المتكاملة المفضلة لديك  
> • نسخة مرخصة من **Aspose.Words for .NET** (الإصدار التجريبي المجاني يعمل للاختبار)  

إذا كان لديك هذه المتطلبات، فلنبدأ.

---

## حفظ مستند Word واكتشاف الخطوط المفقودة

الفكرة الأساسية بسيطة: قبل استدعاء `Document.Save`، قم بتعيين كائن ينفذ `IWarningCallback` إلى `Document.WarningCallback`. ستستدعي Aspose.Words هذا الكائن لكل تحذير تواجهه، بما في ذلك تحذيرات **font substitution** التي تحدث عندما يشير المستند المصدر إلى خط لا يستطيع نظامك العثور عليه.

```csharp
using Aspose.Words;
using Aspose.Words.Warning;

// Step 1: Create a warning handler that prints font substitution messages
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only react to font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// Step 2: Load a document that may contain missing fonts
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Step 3: Register the warning handler with the document
document.WarningCallback = new FontWarningHandler();

// Step 4: Save the document; any font substitution warnings will be output to the console
document.Save("YOUR_DIRECTORY/output.docx");
```

**ما ستراه:**  
إذا كان `input.docx` يشير إلى خط غير مثبت، ستطبع وحدة التحكم شيئًا مثل:

```
Font substitution: Font "Comic Sans MS" was substituted with "Arial".
```

هذا السطر يخبرك بالضبط أي خط كان مفقودًا وما استخدمته Aspose.Words بدلاً منه—مثالي لـ **capturing font errors** قبل أن تقوم بإصدار الملف.

---

## تتبع الخطوط المفقودة باستخدام استدعاء التحذير (خطوة بخطوة)

### 1️⃣ تثبيت Aspose.Words

افتح وحدة تحكم NuGet في مشروعك وشغّل الأمر:

```bash
dotnet add package Aspose.Words
```

هذا يجلب أحدث نسخة مستقرة (حاليًا 24.10). الحفاظ على تحديث المكتبة يضمن حصولك على أحدث قدرات **detect missing fonts** وإصلاحات الأخطاء.

### 2️⃣ تعريف معالج التحذير

لماذا نحتاج إلى فئة منفصلة؟ يسمح لك تنفيذ `IWarningCallback` بتركيز جميع منطق التحذير في مكان واحد. يمكنك أيضًا تسجيل التحذيرات إلى ملف، أو إرسال بيانات قياس، أو إلقاء استثناء إذا كان الخط المفقود يمثل خطأً جسيمًا في سير عملك.

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only the warnings we care about
        if (info.Type == WarningType.FontSubstitution)
        {
            // Here we simply write to the console,
            // but you could replace this with any logging framework.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

> **نصيحة احترافية:** إذا كنت بحاجة إلى **track missing fonts** عبر مستندات متعددة، احفظ الرسائل في `List<string>` داخل المعالج واظهرها لاحقًا للتقارير.

### 3️⃣ تحميل المستند المصدر

يمكن لمنشئ `Document` قبول مسار ملف، أو تدفق، أو حتى بايتات خام. في معظم الحالات ستشير إليه إلى ملف `.docx` استلمته من مستخدم أو نظام آخر.

```csharp
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

إذا كان الملف كبيرًا، فكر في استخدام `LoadOptions` لتمكين التحميل الكسول، مما يقلل من استهلاك الذاكرة.

### 4️⃣ ربط الاستدعاء

قم بتعيين المثيل إلى `doc.WarningCallback`. من هذه النقطة فصاعدًا، ستمر كل تحذير (بما في ذلك استبدالات الخطوط) عبر المعالج الخاص بك.

```csharp
doc.WarningCallback = new FontWarningHandler();
```

### 5️⃣ حفظ المستند

الآن يمكنك استدعاء `Save` بأمان. يعمل معالج التحذير **متزامنًا** أثناء عملية الحفظ، لذا سترى الإخراج فورًا.

```csharp
doc.Save("YOUR_DIRECTORY/output.docx");
```

إذا كنت تفضل الحفظ إلى تنسيق مختلف (PDF، HTML، إلخ)، فإن آلية التحذير نفسها تعمل—ستستمر Aspose.Words في الإبلاغ عن الخطوط المفقودة قبل التحويل.

---

## التقاط أخطاء الخطوط – حالات الحافة الشائعة

بينما يغطي التدفق الأساسي معظم السيناريوهات، غالبًا ما تواجه المشاريع الواقعية بعض المشكلات. فيما يلي بعض الاختلافات التي قد تصادفها وكيفية التعامل معها.

### خط مفقود في الترويسة/التذييل

الترويسات والتذييلات هي عقد منفصلة، لكن نظام التحذير يتعامل معها كالنص الأساسي. لا يلزم أي كود إضافي؛ سيُستدعى الاستدعاء لتلك الخطوط أيضًا. فقط تأكد من تحميل المستند بالكامل (السلوك الافتراضي يفعل ذلك).

### استبدالات متعددة في مستند واحد

إذا كان المستند يستخدم عدة خطوط غير معروفة، سيُستدعى المعالج مرة لكل استبدال. لتجنب إغراق وحدة التحكم، يمكنك إزالة التكرارات من الرسائل:

```csharp
class FontWarningHandler : IWarningCallback
{
    private readonly HashSet<string> _seen = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution && _seen.Add(info.Description))
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

### تحويل التحذيرات إلى استثناءات

أحيانًا يكون الخط المفقود سببًا لإيقاف العملية. قم بإلقاء استثناء داخل المعالج لإلغاء الحفظ:

```csharp
if (info.Type == WarningType.FontSubstitution)
{
    throw new InvalidOperationException($"Missing font detected: {info.Description}");
}
```

تذكر أن تغلف `doc.Save` بكتلة `try/catch` للتعامل مع الاستثناء بشكل سلس.

---

## التحقق من النتيجة – ما المتوقع

بعد إكمال الحفظ، افتح `output.docx` في Microsoft Word (أو أي عارض متوافق). يجب أن ترى نفس التخطيط البصري كما في الأصل، لكن الخطوط المستبدلة ستظهر كبديل رأيته في وحدة التحكم. للتحقق مرة أخرى، يمكنك:

1. افتح **File → Options → Advanced → Show document content → Use draft quality** – هذا يجبر Word على إظهار أي استبدالات خطوط مخفية.  
2. استخدم حوار **Replace Fonts** في Word (`Ctrl+Shift+F`) لمعرفة الخطوط التي تم تضمينها فعليًا.

إذا كان كل شيء متطابقًا، فقد نجحت في **saved word document** مع **detecting missing fonts** و **capturing font errors**. 🎉

---

## مثال كامل يعمل (جاهز للنسخ واللصق)

فيما يلي البرنامج الكامل الذي يمكنك إدراجه في مشروع تطبيق Console جديد. فقط استبدل `YOUR_DIRECTORY` بمسار مجلد فعلي على جهازك.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warning;

namespace FontWarningDemo
{
    // Step 1: Create a warning handler that prints font substitution messages
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            // Only handle font‑substitution warnings
            if (info.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substitution: {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Load a document that may contain missing fonts
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // Step 3: Register the warning handler with the document
            document.WarningCallback = new FontWarningHandler();

            // Step 4: Save the document; any font substitution warnings will be output to the console
            document.Save("YOUR_DIRECTORY/output.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**الإخراج المتوقع في وحدة التحكم** (مثال):

```
Font substitution: Font "Times New Roman" was substituted with "Arial".
Document saved successfully.
```

هذه هي القصة بالكامل—بدون خطوات مخفية، ولا مستندات خارجية تحتاج إلى متابعتها.

---

## الخاتمة

لقد أظهرنا لك الآن كيفية **save word document** مع **detect missing fonts** النشط، **track missing fonts**، و **capture font errors** باستخدام استدعاء التحذير في Aspose.Words. من خلال ربط تنفيذ صغير لـ `IWarningCallback`، تحصل على رؤية كاملة لاستبدالات الخطوط أثناء الحفظ، مما يمنحك الفرصة لتسجيلها أو استبدالها أو إلغاء العملية حسب الحاجة.

هل أنت مستعد للتحدي التالي؟ جرّب توسيع المعالج لكتابة التحذيرات في سجل JSON منظم، أو دمجه مع Aspose.PDF لتحويل نفس المستند مع الحفاظ على معلومات الخطوط. يمكنك أيضًا استكشاف تضمين الخطوط المفقودة مباشرةً في ملف الإخراج—تدعم Aspose.Words تضمين الخطوط عبر `LoadOptions.FontSettings`.

جرّبه، عدّل الكود ليناسب سير عملك، وأخبرنا كيف يعمل بالنسبة لك. برمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}