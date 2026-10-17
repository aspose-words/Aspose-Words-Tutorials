---
category: general
date: 2026-02-13
description: تحويل PNG إلى Base64 في C# بسرعة – تعلم كيفية ترميز الصورة إلى Base64،
  وتضمين الصورة في HTML باستخدام Base64، ونسخ الدفق إلى الذاكرة للمشاريع الويب.
draft: false
keywords:
- convert png to base64
- base64 encode image
- embed image html base64
- image stream to base64
- copy stream to memory
language: ar
og_description: تحويل PNG إلى Base64 في C# بسرعة. يوضح هذا الدرس كيفية ترميز الصورة
  إلى Base64، وتضمين الصورة في HTML باستخدام Base64، ونسخ الدفق إلى الذاكرة.
og_title: تحويل PNG إلى Base64 في C# – دليل كامل
tags:
- C#
- image-processing
- data-uri
title: تحويل PNG إلى Base64 في C# – دليل كامل
url: /ar/net/basic-conversions/convert-png-to-base64-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تحويل PNG إلى Base64 في C# – دليل شامل

هل احتجت يوماً إلى **تحويل PNG إلى Base64** لكن لم تعرف من أين تبدأ؟ لست وحدك؛ كثير من المطورين يواجهون هذه المشكلة عندما يحاولون تضمين الصور مباشرةً في HTML أو CSS. الخبر السار هو أن الحل بسيط جداً بمجرد معرفة الخطوات الصحيحة.

في هذا الدرس سنستعرض مثالاً كاملاً قابلاً للتنفيذ يقوم **بترميز الصورة إلى base64**، يوضح لك كيفية **تضمين صورة html base64** عبر data‑URI، ويشرح أفضل طريقة لـ **نسخ الدفق إلى الذاكرة** دون تسريب الموارد. في النهاية ستحصل على مقتطف يمكن إعادة استخدامه في أي مشروع .NET.

## ما ستتعلمه

- كيفية التحقق من امتداد الملف بطريقة غير حساسة لحالة الأحرف.  
- الأنماط الأكثر أماناً لتحويل **دفق الصورة إلى base64** باستخدام `MemoryStream`.  
- بناء data‑URI صحيح يفهمه المتصفحات.  
- تنظيف الدفق الأصلي لضمان بقاء تطبيقك خفيفاً.  

لا تحتاج إلى مكتبات خارجية—فقط فئات BCL المدمجة مع .NET. إذا كنت مرتاحاً مع أساسيات C# ولديك مشروع يتعامل مع رفع الملفات، فأنت جاهز للبدء.

---

![مخطط يوضح تدفق ملف PNG إلى بيانات Base64 – تحويل png إلى base64](https://example.com/convert-png-to-base64-diagram.png "مثال تحويل png إلى base64")

## تحويل PNG إلى Base64 – خطوة بخطوة

فيما يلي نقسم العملية إلى خمس خطوات منطقية. كل عنوان يعكس جزءاً من اللغز، مما يسهل عليك (وعلى المساعدين الذكائيين) العثور على الجزء الذي تحتاجه.

### الخطوة 1: التحقق من أن المورد هو PNG (غير حساس لحالة الأحرف)

قبل إهدار الذاكرة، نتأكد أن الملف الوارد هو فعلاً PNG. علم `StringComparison.OrdinalIgnoreCase` يتعامل مع أي مزيج من الأحرف الكبيرة أو الصغيرة في الامتداد.

```csharp
// Step 1: Verify that the resource is a PNG image (case‑insensitive)
if (args.ResourceFileExtension.Equals(".png", StringComparison.OrdinalIgnoreCase))
{
    // Continue with conversion...
}
else
{
    // Not a PNG – you might log or throw here
    throw new InvalidOperationException("Only PNG files are supported.");
}
```

*لماذا هذا مهم:* محاولة ترميز ملف غير صورة (أو JPEG) كـ PNG قد يفسد النتيجة ويكسر data‑URI الذي ستضمّنه لاحقاً.

### الخطوة 2: نسخ الدفق إلى الذاكرة

يجب قراءة الدفق `Stream` الوارد (ربما من معالج رفع) بالكامل. استخدام جملة `using var` يضمن التخلص من الذاكرة تلقائياً، مما يحافظ على **نسخ الدفق إلى الذاكرة** نظيفاً.

```csharp
using var memory = new MemoryStream();
args.Stream.CopyTo(memory);
```

*نصيحة احترافية:* إذا كنت تتعامل مع ملفات كبيرة جداً، فكر في استخدام `CopyToAsync` مع حجم مخزن مؤقت معقول لتجنب حجز الخيوط.

### الخطوة 3: ترميز الصورة إلى Base64

الآن بعد أن أصبحت بايتات الصورة موجودة في `memory`، يمكننا تحويلها إلى سلسلة Base64. هذا هو جوهر **base64 encode image**.

```csharp
// Step 3: Encode the buffered bytes as a Base64 string
string base64Data = Convert.ToBase64String(memory.ToArray());
```

*ما الذي يحدث؟* `Convert.ToBase64String` يأخذ مصفوفة بايتات ويعيد تمثيلها النصي الذي يمكن للمتصفحات فك ترميزه مرة أخرى إلى بيانات ثنائية.

### الخطوة 4: بناء Data‑URI للـ HTML/CSS

يتيح لك Data‑URI تضمين الصورة مباشرةً في العلامات، مما يلغي طلبات HTTP الإضافية. الصيغة هي `data:[<mediatype>][;base64],<data>`.

```csharp
// Step 4: Build a data‑URI that embeds the PNG directly in HTML/CSS
args.ResourceFilePath = $"data:image/png;base64,{base64Data}";
```

عند عرض `args.ResourceFilePath` داخل وسم `<img src="...">` لاحقاً، سيظهر PNG فوراً في المتصفح.

### الخطوة 5: تحرير الدفق الأصلي

بما أن الصورة الآن ممثلة بـ Data‑URI، لم يعد الدفق `Stream` الأصلي ضرورياً. تعيينه إلى `null` يساعد جامع القمامة على استعادة مقبض السوكيت أو الملف الأساسي.

```csharp
// Step 5: Release the original stream because the resource is now embedded
args.Stream = null;
```

*حالة خاصة:* إذا كنت تحتاج إلى الملف الأصلي لاحقاً (مثلاً لتخزينه على القرص)، فتجاوز هذه الخطوة واحتفظ بإشارة إليه في مكان آخر.

---

## مثال كامل يعمل

جمع جميع الأجزاء معاً ينتج طريقة مختصرة يمكنك لصقها في أي فئة تعالج الموارد المرفوعة.

```csharp
using System;
using System.IO;

public class ResourceProcessor
{
    public void ProcessPng(ResourceArgs args)
    {
        // Verify extension (primary check)
        if (!args.ResourceFileExtension.Equals(".png", StringComparison.OrdinalIgnoreCase))
        {
            throw new InvalidOperationException("Only PNG files can be converted to Base64.");
        }

        // Copy the incoming stream into a memory buffer (copy stream to memory)
        using var memory = new MemoryStream();
        args.Stream.CopyTo(memory);

        // Encode the buffered bytes as a Base64 string (base64 encode image)
        string base64Data = Convert.ToBase64String(memory.ToArray());

        // Build a data‑URI that embeds the PNG directly in HTML/CSS (embed image html base64)
        args.ResourceFilePath = $"data:image/png;base64,{base64Data}";

        // Release the original stream because the resource is now embedded (image stream to base64)
        args.Stream = null;
    }
}

// Helper class to mimic incoming arguments
public class ResourceArgs
{
    public string ResourceFileExtension { get; set; }   // e.g., ".png"
    public Stream Stream { get; set; }                 // original file stream
    public string ResourceFilePath { get; set; }       // will hold the data‑URI
}
```

**الناتج المتوقع:** بعد تشغيل `ProcessPng`، يحتوي `args.ResourceFilePath` على سلسلة تشبه:

```
data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...
```

يمكنك الآن وضع هذه السلسلة مباشرةً داخل وسم `<img>`:

```html
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA..." alt="Converted PNG">
```

ستظهر الصورة فوراً، دون أي حركة مرور إضافية.

---

## أسئلة شائعة وحالات خاصة

### ماذا لو كان PNG كبيراً؟

الصور الكبيرة قد تستهلك الذاكرة لأن الملف بالكامل يُحفظ في `MemoryStream`. للملفات التي تتجاوز عدة ميغابايت، فكر في تحويل Base64 على دفعات أو تصغير حجم الصورة قبل الترميز.

### هل يمكن جعل العملية غير متزامنة؟

بالطبع. استبدل `CopyTo` بـ `CopyToAsync` وعلم الطريقة بـ `async Task`. هذا يبقي خيط طلب ASP.NET حرًا أثناء إكمال عمليات الإدخال/الإخراج.

```csharp
await args.Stream.CopyToAsync(memory);
```

### هل يعمل هذا مع صيغ صور أخرى؟

الكود نفسه لا يعتمد على الصيغة؛ عليك فقط تعديل نوع MIME في Data‑URI (`image/jpeg`, `image/gif`، إلخ) وتغيير فحص الامتداد وفقاً لذلك.

### كيف أتعامل مع الأخطاء بشكل أنيق؟

غلف الكتلة بالكامل بـ `try/catch` وسجّل الاستثناء. إذا كنت في Web API، أرجع حالة 400 Bad Request مع رسالة توضيحية.

---

## الخلاصة

أنت الآن تعرف كيف **تحول PNG إلى Base64** في C# من البداية حتى النهاية. غطى الدرس التحقق من نوع الملف، النسخ الآمن للدفق إلى الذاكرة، تنفيذ **base64 encode image**، بناء Data‑URI صحيح لـ **embed image html base64**، وتنظيف الموارد.  

من هنا يمكنك استكشاف تعديل حجم الصورة أثناء التشغيل، تخزين Data‑URIs المولدة في ذاكرة التخزين المؤقت، أو حتى إنشاء عناصر نائب SVG. أياً كان ما تختاره، فإن النمط الموضح أعلاه سيشكل أساساً صلباً لأي سيناريو تحتاج فيه إلى تحويل **دفق الصورة إلى base64** وتضمينه مباشرةً في العلامات.

هل لديك تعديل على هذه العملية؟ ربما تعمل مع WebAssembly أو Blazor—شارك تجاربك في التعليقات. happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}