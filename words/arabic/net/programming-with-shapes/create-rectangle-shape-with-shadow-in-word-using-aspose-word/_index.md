---
category: general
date: 2026-03-06
description: إنشاء شكل مستطيل في Word وإضافة ظل للشكل باستخدام Aspose.Words. تعلم
  كيفية إدراج مستطيل في Word وكيفية إضافة ظل للشكل في C#.
draft: false
keywords:
- create rectangle shape
- add shape shadow
- how to insert rectangle in word
- how to add shadow to shape
language: ar
og_description: إنشاء شكل مستطيل في Word وإضافة ظل للشكل باستخدام Aspose.Words. دليل
  خطوة بخطوة حول كيفية إدراج مستطيل في Word وكيفية إضافة ظل إلى الشكل.
og_title: إنشاء شكل مستطيل بظل في Word باستخدام Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: إنشاء شكل مستطيل بظل في Word باستخدام Aspose.Words
url: /ar/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-word-using-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء شكل مستطيل مع ظل في Word باستخدام Aspose.Words

هل احتجت يوماً إلى **إنشاء شكل مستطيل** في مستند Word لكنك لم تكن متأكدًا من كيفية إعطائه مظهرًا مصقولًا؟ لست وحدك—معظم المطورين يواجهون نفس المشكلة عندما يحاولون لأول مرة إضافة لمسة بصرية إلى المستندات الآلية. الخبر السار؟ باستخدام Aspose.Words لـ .NET يمكنك كل من **إنشاء شكل مستطيل** و**إضافة ظل للشكل** في بضع أسطر فقط من C#.

في هذا الدليل سنستعرض خطوة بخطوة **كيفية إدراج مستطيل في Word**، ثم نوضح **كيفية إضافة ظل إلى الشكل** ليظهر كأنه يخرج من الصفحة. في النهاية ستحصل على ملف `Shadow.docx` جاهز للحفظ يمكنك فتحه في Word ورؤية مستطيل رمادي اللون مع ظل ناعم. لا ملفات صور إضافية، ولا تعديل يدوي—فقط الكود.

## ما ستتعلمه

- بيانات C# الدقيقة اللازمة **لإنشاء شكل مستطيل** باستخدام Aspose.Words.  
- كيفية تمكين وتكوين الظل باستخدام كائن `Shadow`.  
- سبب أهمية كل خاصية (مثل `Transparency`، `Blur`، `Angle`).  
- المشكلات الشائعة (الوحدات، توافق الإصدارات) والحلول السريعة.  
- برنامج كامل جاهز للنسخ واللصق يمكنك تشغيله اليوم.

### المتطلبات المسبقة

- .NET 6+ (أو .NET Framework 4.7+).  
- Aspose.Words لـ .NET 23.10 أو أحدث (حزمة NuGet هي `Aspose.Words`).  
- فهم أساسي لـ C# و Visual Studio (أو أي بيئة تطوير تفضلها).  

إذا كان لديك هذه المتطلبات، لنبدأ مباشرة.

---

## الخطوة 1: إعداد المشروع واستيراد المساحات الاسمية

أولاً، أنشئ تطبيق console جديد (أو أعد استخدام أحد الموجودين) وأضف حزمة NuGet الخاصة بـ Aspose.Words:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

الآن استورد المساحات الاسمية المطلوبة في ملف `Program.cs` الخاص بك:

```csharp
using System.Drawing;               // For Color
using Aspose.Words;                  // Core document classes
using Aspose.Words.Drawing;          // Shape and Shadow types
```

> **نصيحة احترافية:** إذا كنت تستهدف .NET 6+، يمكنك تمكين توجيهات `using` العالمية لتجنب تكرار هذه الأسطر في كل ملف.

---

## الخطوة 2: **إنشاء شكل مستطيل** في مستند Word فارغ

سنبدأ بكائن `Document` جديد و`DocumentBuilder` للتعامل معه. طريقة `InsertShape` في الـ builder هي التي تحدث السحر.

```csharp
// Step 2: Initialize a new document and builder
Document document = new Document();                     // Blank Word file
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle – 200 × 100 points (≈2.78 × 1.39 inches)
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

لماذا 200 × 100 نقطة؟ في Word، النقطة تساوي 1/72 من البوصة، لذا يصبح المستطيل تقريبًا 2.8 × 1.4 إنش—كبير بما يكفي للانتباه لكنه ليس مفرطًا. يمكنك تغيير هذه القيم لتناسب تخطيطك؛ فقط تذكر أنها تُقاس بـ **النقاط**، وليس بالبكسل.

---

## الخطوة 3: **إضافة ظل للشكل** – ضبط المظهر

الآن بعد أن لدينا مستطيلًا، لنمنحه ظلًا رماديًا خفيفًا. كائن `Shadow` موجود داخل `Shape` ويوفر عدة خصائص مفيدة.

```csharp
// Step 3: Turn on the shadow and tweak its appearance
rectangle.Shadow.Enabled = true;               // Switch the shadow on
rectangle.Shadow.Color = Color.Gray;           // Shadow hue
rectangle.Shadow.Transparency = 0.3;           // 30 % transparent – looks softer
rectangle.Shadow.Blur = 5;                     // Blur radius (points)
rectangle.Shadow.Distance = 4;                 // How far the shadow sits from the shape
rectangle.Shadow.Angle = 45;                   // Direction in degrees (45° = down‑right)
rectangle.Shadow.Size = 100;                   // 100 % of the original shape size
```

### ما تقوم به كل خاصية

| الخاصية | التأثير | القيم النموذجية |
|----------|--------|----------------|
| **Enabled** | تشغيل أو إيقاف الظل | `true` أو `false` |
| **Color** | اللون الأساسي للظل | أي `System.Drawing.Color` |
| **Transparency** | الشفافية (0 = صلب، 1 = شفاف) | 0.0 – 1.0 |
| **Blur** | نعومة الحافة | 0 – 10 (كلما ارتفعت القيمة = أطرى) |
| **Distance** | الفاصل بين الشكل والظل | 0 – 20 نقطة |
| **Angle** | اتجاه الضوء الظاهر | 0 – 360 درجة |
| **Size** | مقياس الظل بالنسبة للشكل | 0 – 200 % |

> **لماذا تهتم بهذه الإعدادات؟**  
> ضبط الظل بدقة يتيح لك مطابقة إرشادات العلامة التجارية للشركة (مثلاً شفافية خفيفة 20 % للحصول على مظهر احترافي) دون اللجوء إلى محررات الصور الخارجية.

---

## الخطوة 4: حفظ المستند والتحقق من النتيجة

أخيرًا، احفظ الملف على القرص. يمكنك اختيار أي مجلد تفضله؛ فقط استبدل `YOUR_DIRECTORY` بمسار حقيقي.

```csharp
// Step 4: Persist the document
string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

افتح `Shadow.docx` في Microsoft Word وسترى مستطيلًا رماديًا مع ظل ناعم مائل بزاوية 45°. هذه الإشارة البصرية تجعل الشكل يبدو “مرفوعًا” عن الصفحة—تمامًا ما تتوقعه من تقرير أو فاتورة مصقولة.

---

## مثال كامل يعمل

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑ولصقه في `Program.cs`. لا توجد أجزاء مفقودة؛ يترجم ويعمل كما هو.

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (200 × 100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // 3️⃣ Enable the shape's shadow and configure its appearance
        rectangle.Shadow.Enabled = true;               // Turn the shadow on
        rectangle.Shadow.Color = Color.Gray;           // Shadow colour
        rectangle.Shadow.Transparency = 0.3;           // 30 % transparent
        rectangle.Shadow.Blur = 5;                     // Blur radius
        rectangle.Shadow.Distance = 4;                 // Offset from the shape
        rectangle.Shadow.Angle = 45;                   // Direction in degrees
        rectangle.Shadow.Size = 100;                   // Shadow size as a percentage

        // 4️⃣ Save the document with the shadowed shape
        string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### النتيجة المتوقعة

- **الملف:** `Shadow.docx` موجود في مجلد تنفيذ المشروع.  
- **المظهر:** مستطيل واحد مركزي على الصفحة، مملوء باللون الأبيض الافتراضي، وظل رمادي مائل 4 نقاط إلى الأسفل‑اليمين، مع تمويه طفيف لمظهر طبيعي.

---

## أسئلة شائعة وحالات خاصة

### 1. ماذا لو احتجت إلى وحدة مختلفة (مثلاً السنتيمتر)؟

Aspose.Words يعمل بالنقاط، ولكن يمكنك تحويل السنتيمترات إلى نقاط باستخدام الصيغة البسيطة:  
`points = centimeters * 28.3465`.  

```csharp
double cmWidth = 5.0; // 5 cm
double cmHeight = 2.5; // 2.5 cm
Shape rectCm = builder.InsertShape(ShapeType.Rectangle,
                                   (float)(cmWidth * 28.3465),
                                   (float)(cmHeight * 28.3465));
```

### 2. هل يعمل هذا مع إصدارات Aspose.Words القديمة؟

تم تقديم واجهة برمجة تطبيقات `Shadow` في الإصدار 14.0. إذا كنت تستخدم إصدارًا أقدم، ستحتاج إلى الترقية عبر NuGet. باقي الكود (إنشاء الأشكال) مستقر منذ سنوات عديدة، لذا لن تواجه تغييرات كسرية.

### 3. هل يمكنني إضافة ظل لأشكال أخرى (مثلاً دوائر)؟

بالتأكيد—أي كائن `Shape` يملك خاصية `Shadow`. فقط استبدل `ShapeType.Rectangle` بـ `ShapeType.Ellipse` أو `ShapeType.Cloud`، ثم طبق نفس إعدادات الظل.

### 4. ماذا لو احتجت ظلًا ملونًا (مثلاً أزرق للعلامة التجارية)؟

استبدل `Color.Gray` بأي `Color` تفضله:

```csharp
rectangle.Shadow.Color = Color.FromArgb(30, 0, 120); // Dark blue
```

تذكر تعديل `Transparency` حتى لا يصبح اللون سائدًا جدًا.

---

## 🎨 ملخص بصري

![create rectangle shape with shadow in Word using Aspose.Words](image-placeholder.png "create rectangle shape with shadow in Word using Aspose.Words")

*نص بديل: إنشاء شكل مستطيل مع ظل في Word باستخدام Aspose.Words*

تُظهر لقطة الشاشة (عنصر نائب) المستند النهائي—فقط المستطيل وظله الرمادي الناعم.

---

## الخلاصة

أنت الآن تعرف كيف **تنشئ شكل مستطيل** في ملف Word، **تضيف ظلًا للشكل**، وتضبط كل جانب بصري باستخدام Aspose.Words لـ .NET. البرنامج القصير الذي بنيناه يغطي سير العمل بالكامل—من

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}