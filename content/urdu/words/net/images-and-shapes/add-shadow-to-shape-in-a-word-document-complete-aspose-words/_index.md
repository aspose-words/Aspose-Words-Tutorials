---
category: general
date: 2025-12-08
description: Aspose.Words کے ساتھ شکل پر جلدی شیڈو لگائیں۔ Aspose استعمال کرتے ہوئے
  ورڈ دستاویز کیسے بنائیں، شکل پر شیڈو کیسے شامل کریں، اور C# میں شیڈو کی شفافیت کیسے
  لاگو کریں، سیکھیں۔
draft: false
keywords:
- add shadow to shape
- create word document using aspose
- how to add shape shadow
- apply shadow transparency
language: ur
og_description: Aspose.Words استعمال کرتے ہوئے Word فائل میں شکل پر سایہ شامل کریں۔
  یہ مرحلہ وار رہنمائی دکھاتی ہے کہ دستاویز کیسے بنائی جائے، شکل کیسے شامل کی جائے،
  اور سایہ کی شفافیت کیسے لاگو کی جائے۔
og_title: شیپ پر سایہ شامل کریں – Aspose.Words C# ٹیوٹوریل
tags:
- Aspose.Words
- C#
- Word Automation
title: ورڈ دستاویز میں شکل پر سایہ شامل کریں – مکمل Aspose.Words گائیڈ
url: /urdu/net/images-and-shapes/add-shadow-to-shape-in-a-word-document-complete-aspose-words/
---

{{< layout-start >}}

{{< layout-start >}}

# shape پر سایہ شامل کریں – مکمل Aspose.Words گائیڈ

کبھی Word فائل میں **shape پر سایہ شامل کرنا** ضروری ہوا لیکن آپ کو نہیں پتہ تھا کہ کون سی API کالز استعمال کریں؟ آپ اکیلے نہیں ہیں۔ بہت سے ڈویلپرز کو پہلی بار جب وہ کسی مستطیل یا کسی بھی ڈرائنگ ایلیمنٹ پر مناسب ڈراپ‑شیڈو دینے کی کوشش کرتے ہیں تو رکاوٹ ملتی ہے، خاص طور پر جب وہ Aspose.Words for .NET کے ساتھ کام کر رہے ہوں۔

اس ٹیوٹوریل میں ہم آپ کو ہر وہ چیز سکھائیں گے جو آپ کو جاننی ضروری ہے: **Aspose استعمال کرتے ہوئے Word دستاویز بنانے** سے لے کر سایہ کی ترتیب، اس کے بلر، فاصلہ، زاویہ، اور حتیٰ کہ **سایہ کی شفافیت لگانے** تک۔ آخر تک آپ کے پاس ایک تیار‑چلانے کے قابل C# پروگرام ہوگا جو ایک `.docx` فائل بنائے گا جس میں ایک خوبصورت سایہ دار مستطیل ہو—Word میں کسی دستی مداخلت کی ضرورت نہیں۔

---

## آپ کیا سیکھیں گے

- Visual Studio میں Aspose.Words پروجیکٹ کیسے سیٹ اپ کریں۔  
- بالکل درست قدم **Aspose استعمال کرتے ہوئے Word دستاویز بنانے** اور ایک shape داخل کرنے کے۔  
- **shape پر سایہ شامل کرنے** کے طریقے کے ساتھ بلر، فاصلہ، زاویہ، اور شفافیت پر مکمل کنٹرول۔  
- عام مسائل کی ٹroubleshooting کے لیے نکات (مثلاً، لائسنس غائب، غلط یونٹس)۔  
- ایک مکمل، کاپی‑اینڈ‑پیسٹ کوڈ نمونہ جو آپ آج ہی چلا سکتے ہیں۔  

> **Prerequisites:** .NET 6+ (or .NET Framework 4.7.2+), ایک معتبر Aspose.Words لائسنس (یا مفت ٹرائل), اور C# کی بنیادی واقفیت۔

---

## قدم 1 – اپنے پروجیکٹ کو سیٹ اپ کریں اور Aspose.Words شامل کریں

سب سے پہلے۔ Visual Studio کھولیں، ایک نیا **Console App (.NET Core)** بنائیں، اور Aspose.Words NuGet پیکج شامل کریں:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** اگر آپ کے پاس لائسنس فائل (`Aspose.Words.lic`) ہے تو اسے پروجیکٹ کی جڑ میں کاپی کریں اور اسٹارٹ اپ پر لوڈ کریں۔ یہ مفت ایویلیوئیشن موڈ میں ظاہر ہونے والے واٹرمارک سے بچاتا ہے۔

```csharp
// Load the license (optional but recommended)
var license = new Aspose.Words.License();
license.SetLicense("Aspose.Words.lic");
```

---

## قدم 2 – نیا خالی دستاویز بنائیں

اب ہم واقعی **Aspose استعمال کرتے ہوئے Word دستاویز بنائیں**۔ یہ آبجیکٹ ہماری shape کے لیے کینوس کے طور پر کام کرے گا۔

```csharp
// Step 2: Initialize a new blank document
Document doc = new Document();   // Represents an empty .docx file
```

`Document` کلاس باقی سب کے لیے انٹری پوائنٹ ہے—پیراگراف، سیکشن، اور یقیناً، ڈرائنگ آبجیکٹس۔

---

## قدم 3 – ایک مستطیل shape داخل کریں

دستاویز تیار ہونے کے بعد، ہم ایک shape شامل کر سکتے ہیں۔ یہاں ہم ایک سادہ مستطیل منتخب کرتے ہیں، لیکن یہی منطق دائرے، لائنیں، یا کسٹم پولیگون کے لیے بھی کام کرتی ہے۔

```csharp
// Step 3: Create a rectangular shape that will hold the shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 150,   // Width in points (1 point = 1/72 inch)
    Height = 100    // Height in points
};
```

> **shape کیوں؟** Aspose.Words میں `Shape` آبجیکٹ ٹیکسٹ، امیجز رکھ سکتا ہے، یا صرف ایک سجاوٹی عنصر کے طور پر کام کر سکتا ہے۔ shape پر سایہ شامل کرنا تصویر کے فریم کو تبدیل کرنے سے کہیں آسان ہے۔

---

## قدم 4 – سایہ کی ترتیب (shape پر سایہ شامل کریں)

یہ ٹیوٹوریل کا دل ہے—**shape پر سایہ کیسے شامل کریں** اور اس کی ظاہری شکل کو باریک‑باریک ایڈجسٹ کریں۔ `ShadowFormat` پراپرٹی آپ کو مکمل کنٹرول دیتی ہے۔

```csharp
// Step 4: Enable the shadow and configure its appearance
rectangle.ShadowFormat.Visible       = true;   // Turn the shadow on
rectangle.ShadowFormat.Blur          = 5.0;    // Blur radius – higher = softer edges
rectangle.ShadowFormat.Distance      = 3.0;    // Offset distance from the shape
rectangle.ShadowFormat.Angle         = 45;     // Direction in degrees (0 = right, 90 = down)
rectangle.ShadowFormat.Transparency  = 0.3;    // 30 % transparent – this is how we **apply shadow transparency**
```

### ہر پراپرٹی کا کیا کام ہے

| پراپرٹی | اثر | عام اقدار |
|----------|--------|----------------|
| **Visible** | سایہ کو آن/آف کرتا ہے۔ | `true` / `false` |
| **Blur** | سایہ کے کناروں کو نرم کرتا ہے۔ | `0` (hard) to `10` (very soft) |
| **Distance** | سایہ کو shape سے دور لے جاتا ہے۔ | `1`–`5` points is common |
| **Angle** | آفسیٹ کی سمت کو کنٹرول کرتا ہے۔ | `0`–`360` degrees |
| **Transparency** | سایہ کو جزوی طور پر شفاف بناتا ہے۔ | `0` (opaque) to `1` (invisible) |

> **Edge case:** اگر آپ `Transparency` کو `1` پر سیٹ کریں تو سایہ مکمل طور پر غائب ہو جاتا ہے—یہ پروگرام کے ذریعے ٹوگل کرنے کے لیے مفید ہے۔

---

## قدم 5 – shape کو دستاویز میں شامل کریں

اب ہم shape کو دستاویز کے باڈی کے پہلے پیراگراف سے منسلک کرتے ہیں۔ اگر کوئی پیراگراف موجود نہ ہو تو Aspose خود بخود ایک پیراگراف بناتا ہے۔

```csharp
// Step 5: Append the shape to the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);
```

اگر آپ کی دستاویز میں پہلے سے مواد موجود ہے تو آپ `InsertAfter` یا `InsertBefore` استعمال کر کے shape کو کسی بھی نوڈ پر داخل کر سکتے ہیں۔

---

## قدم 6 – دستاویز محفوظ کریں

آخر میں، فائل کو ڈسک پر لکھیں۔ آپ کوئی بھی سپورٹ شدہ فارمیٹ (`.docx`, `.pdf`, `.odt`, وغیرہ) منتخب کر سکتے ہیں، لیکن اس ٹیوٹوریل کے لیے ہم نیٹو Word فارمیٹ پر رہیں گے۔

```csharp
// Step 6: Save the document with the shadowed shape
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

نتیجہ میں بنے `ShadowedShape.docx` کو Microsoft Word میں کھولیں، اور آپ کو ایک مستطیل دکھائی دے گی جس پر نرم، 45‑ڈگری کا سایہ ہے جو 30 % شفاف ہے—بالکل وہی جو ہم نے ترتیب دیا تھا۔

---

## مکمل کام کرنے والی مثال

نیچے **مکمل، کاپی‑اینڈ‑پیسٹ کے لیے تیار** پروگرام ہے جو اوپر دیے گئے تمام قدموں کو شامل کرتا ہے۔ اسے `Program.cs` کے طور پر محفوظ کریں اور `dotnet run` کے ساتھ چلائیں۔

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // OPTIONAL: Load Aspose.Words license (remove if using trial)
        // -------------------------------------------------
        try
        {
            var license = new License();
            license.SetLicense("Aspose.Words.lic");
        }
        catch (Exception ex)
        {
            Console.WriteLine("License not found – running in evaluation mode: " + ex.Message);
        }

        // -------------------------------------------------
        // 1. Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // 2. Insert a rectangle shape
        // -------------------------------------------------
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 150,
            Height = 100
        };

        // -------------------------------------------------
        // 3. Configure the shadow – this is where we **add shadow to shape**
        // -------------------------------------------------
        rectangle.ShadowFormat.Visible      = true;   // Show the shadow
        rectangle.ShadowFormat.Blur         = 5.0;    // Soft edges
        rectangle.ShadowFormat.Distance     = 3.0;    // Offset distance
        rectangle.ShadowFormat.Angle        = 45;     // Direction in degrees
        rectangle.ShadowFormat.Transparency = 0.3;    // 30 % transparent (apply shadow transparency)

        // -------------------------------------------------
        // 4. Add the shape to the document
        // -------------------------------------------------
        doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);

        // -------------------------------------------------
        // 5. Save the file
        // -------------------------------------------------
        string outFile = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
        doc.Save(outFile);
        Console.WriteLine($"Document created successfully: {outFile}");
    }
}
```

**متوقع نتیجہ:** ایک فائل جس کا نام `ShadowedShape.docx` ہے، جس میں ایک واحد مستطیل ہے جس پر ہلکا، نیم‑شفاف ڈراپ شیڈو 45° کے زاویے پر ہے۔

---

## مختلف صورتیں اور ایڈوانس ٹپس

### سایہ کا رنگ تبدیل کرنا

ڈیفالٹ طور پر سایہ shape کے فل رنگ سے وراثت میں ملتا ہے، لیکن آپ ایک کسٹم رنگ سیٹ کر سکتے ہیں:

```csharp
rectangle.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### مختلف سایوں کے ساتھ متعدد shapes

اگر آپ کو کئی shapes کی ضرورت ہے تو صرف تخلیق اور ترتیب کے قدموں کو دہراتے رہیں۔ اگر آپ بعد میں ان کا حوالہ دینا چاہتے ہیں تو ہر shape کو ایک منفرد نام دیں۔

### PDF میں ایکسپورٹ کرنا اور سایے محفوظ رکھنا

Aspose.Words PDF میں محفوظ کرتے وقت سایہ کے اثرات کو برقرار رکھتا ہے:

```csharp
doc.Save("ShadowedShape.pdf");
```

### عام مشکلات

| علامت | ممکنہ وجہ | حل |
|---------|--------------|-----|
| سایہ نظر نہیں آ رہا | `ShadowFormat.Visible` کو `false` پر چھوڑ دیا گیا | اسے `true` پر سیٹ کریں۔ |
| سایہ بہت سخت لگ رہا ہے | `Blur` کو `0` پر سیٹ کیا گیا | `Blur` کو 3–6 تک بڑھائیں۔ |
| PDF میں سایہ غائب ہو جاتا ہے | پرانا Aspose.Words ورژن (< 22.9) استعمال کرنا | لائبریری کو جدید ترین ورژن پر اپگریڈ کریں۔ |

---

## نتیجہ

ہم نے Aspose.Words کے ذریعے **shape پر سایہ کیسے شامل کریں** کا احاطہ کیا ہے، دستاویز کی ابتدا سے لے کر بلر، فاصلہ، زاویہ، اور **سایہ کی شفافیت لگانے** تک۔ مکمل مثال ایک صاف، پروڈکشن‑ریڈی طریقہ دکھاتی ہے جسے آپ کسی بھی shape یا دستاویز کے لے آؤٹ کے لیے اپناؤ سکتے ہیں۔

اگر آپ کے پاس **Aspose استعمال کرتے ہوئے Word دستاویز بنانے** کے بارے میں مزید پیچیدہ مناظر—جیسے سایہ والے جدول یا ڈائنامک ڈیٹا‑ڈرائیوڈ shapes—کے بارے میں سوالات ہیں تو نیچے تبصرہ کریں یا Aspose.Words کی امیج ہینڈلنگ اور پیراگراف فارمیٹنگ کے متعلقہ ٹیوٹوریلز دیکھیں۔

کوڈنگ کا لطف اٹھائیں، اور اپنے Word دستاویزات کو ایک اضافی بصری چمک دینے کا مزہ لیں!

--- 

![shape پر سایہ کی مثال](shadowed_shape.png "shape پر سایہ کی مثال")

{{< layout-end >}}

{{< layout-end >}}