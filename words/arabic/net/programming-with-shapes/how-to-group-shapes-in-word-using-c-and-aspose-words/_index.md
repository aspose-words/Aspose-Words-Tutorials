---
category: general
date: 2026-09-30
description: تجميع الأشكال في Word باستخدام C# – تعلم كيفية تجميع الأشكال، إضافة مستطيل
  وإهليلج، وإدراج شكل مستطيل في مستندات Word برمجياً.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- how to add rectangle
- how to add ellipse
- insert rectangle shape word
language: ar
lastmod: 2026-09-30
og_description: تجميع الأشكال في Word باستخدام C# و Aspose.Words. اتبع هذا الدليل
  الكامل لإضافة مستطيل، وإضافة إهليلج، وتعلم كيفية تجميع الأشكال بكفاءة.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape
og_title: تجميع الأشكال في Word باستخدام C# – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: group shapes in Word with C# – learn how to group shapes, add rectangle
    and ellipse, and insert rectangle shape Word documents programmatically.
  headline: How to group shapes in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: كيفية تجميع الأشكال في Word باستخدام C# و Aspose.Words
url: /ar/net/programming-with-shapes/how-to-group-shapes-in-word-using-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تجميع الأشكال في Word باستخدام C# و Aspose.Words

إذا كنت بحاجة إلى **group shapes in Word** برمجياً، فإن هذا الدليل يوضح لك بالضبط كيفية القيام بذلك. سترى كيفية إضافة مستطيل، إضافة إهليلج، ثم دمجهما في شكل مجموعة واحد باستخدام مكتبة Aspose.Words لـ .NET.

التعامل مع الأشكال هو مطلب شائع عند إنشاء التقارير أو العقود أو المواد التسويقية تلقائيًا. بنهاية هذا الدليل ستحصل على طريقة C# قابلة لإعادة الاستخدام تقوم بتحميل ملف DOCX، وإدراج مستطيل وإهليلج، وتجميعهما، وحفظ النتيجة—كل ذلك دون فتح Word يدويًا.

## المتطلبات المسبقة

* .NET 6.0 SDK أو أحدث مثبت  
* بيئة تطوير مثل Visual Studio 2022 (إصدار Community يعمل)  
* رخصة Aspose.Words لـ .NET أو نسخة تقييم مجانية (تعمل الواجهة البرمجية بدون رخصة ولكنها تضيف علامة مائية)  

تحتاج أيضًا إلى مستند Word مصدر (`input.docx`) في مجلد يمكنك الإشارة إليه من الشيفرة. يمكن أن يكون المستند فارغًا؛ يركز الدليل على معالجة الأشكال.

## الخطوة 1: إنشاء مشروع وحدة تحكم جديد وإضافة Aspose.Words

افتح الطرفية أو موجه أوامر Visual Studio وشغّل الأمر التالي:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

هذا ينشئ تطبيق وحدة تحكم جديد باسم **WordShapeDemo** ويضيف حزمة NuGet `Aspose.Words`، التي تحتوي على الفئات `Document` و `DocumentBuilder` المستخدمة للتعامل مع ملفات Word.

## الخطوة 2: تحميل أو إنشاء مستند

العملية الأولى عند العمل مع **group shapes in Word** هي الحصول على كائن `Document`. يمكنك إما تحميل ملف DOCX موجود أو البدء من مستند فارغ.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Load an existing document (replace the path with your own)
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");

        // If you prefer a brand‑new document, uncomment the next line:
        // Document document = new Document();
```

الفئة `Document` تمثل ملف Word بالكامل. تحميل ملف يمنحك لوحة جاهزة لإدراج الأشكال.

## الخطوة 3: بدء مجموعة شكل

*group shape* يتيح لك التعامل مع عدة أشكال مستقلة كوحدة واحدة—مثالي لتحريكها أو تغيير حجمها معًا. لبدء مجموعة، استدعِ `StartGroupShape()` على كائن `DocumentBuilder`.

```csharp
        // Create a builder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Begin a group shape that will contain multiple shapes
        builder.StartGroupShape();
```

استدعاء `StartGroupShape` يخبر Aspose.Words أن كل إدراج شكل لاحق ينتمي إلى نفس المجموعة المنطقية حتى تستدعي `EndGroupShape`.

## الخطوة 4: كيفية إضافة شكل مستطيل في Word

الآن بعد فتح المجموعة، أدخل مستطيلًا. طريقة `InsertShape` تأخذ تعداد `ShapeType`، يليه العرض والارتفاع (بالنقاط).

```csharp
        // Add a rectangle shape to the group (100 pt wide, 50 pt high)
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

يصبح المستطيل هو العضو الأول في المجموعة. يمكنك تخصيص تعبئته أو حدوده أو نصه لاحقًا إذا لزم الأمر.

## الخطوة 5: كيفية إضافة شكل إهليلج في Word

بعد ذلك، أضف إهليلجًا (دائرة عندما يكون العرض مساويًا للارتفاع). هذا يوضح **how to add ellipse** باستخدام نفس الـ builder.

```csharp
        // Add an ellipse shape to the same group (80 pt wide, 80 pt high)
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

كلا الشكلين الآن يشتركان في نفس مساحة الإحداثيات داخل المجموعة، مما يسهل محاذاتهما بصريًا.

## الخطوة 6: إغلاق تعريف مجموعة الشكل

عندما تكون قد أضفت جميع الأعضاء المطلوبين، أغلق المجموعة. هذا ينهى مجموعة الأشكال بحيث يتعامل Word معها ككائن واحد.

```csharp
        // End the group shape definition
        builder.EndGroupShape();
```

في هذه المرحلة يحتوي المستند على شكل مجموعة واحد يتكون من مستطيل وإهليلج.

## الخطوة 7: حفظ المستند المعدل

أخيرًا، احفظ التغييرات إلى القرص. يمكنك استبدال الملف الأصلي أو إنشاء ملف جديد.

```csharp
        // Save the document with the grouped shapes
        document.Save(@"YOUR_DIRECTORY\output.docx");

        Console.WriteLine("Document saved with grouped shapes.");
    }
}
```

تشغيل البرنامج ينتج `output.docx`. افتح الملف في Microsoft Word، حدد الشكل، وسترى أن المستطيل والإهليلج يتحركان معًا—دليل على نجاح عملية **group shapes in Word**.

### النتيجة المتوقعة

* ملف Word يحتوي على كائن مجموعة واحد.  
* تحديد المجموعة يتيح لك سحبها، تغيير حجمها، أو تدوير كل من المستطيل والإهليلج في آن واحد.  
* لا حاجة لتفاعل يدوي مع Word؛ كل شيء يتم عبر كود C#.

![الأشكال المجمعة في مستند Word](grouped-shapes.png "لقطة شاشة لمستند Word تُظهر مستطيلًا وإهليلجًا مجمّعين")

*نص بديل للصورة: “لقطة شاشة لمستند Word تُظهر مستطيلًا وإهليلجًا مجمّعين”* (يفي بمتطلبات نص بديل الصورة).

## لماذا تجميع الأشكال مهم

تجميع الأشكال أكثر من مجرد راحة بصرية. فهو يتيح لك:

* **Maintain layout consistency** – تحريك مجموعة يحافظ على المواقع النسبية دون تغيير.  
* **Apply transformations once** – تدوير أو تحجيم المجموعة بأكملها بدلاً من كل شكل على حدة.  
* **Simplify downstream processing** – عندما تقرأ أدوات أخرى ملف DOCX، فإنها ترى شكلًا مركبًا واحدًا، مما يقلل التعقيد.

إذا احتجت يومًا لإضافة المزيد من الأشكال (مثل خط أو مربع نص) إلى نفس الوحدة المنطقية، كل ما عليك هو استدعاء `InsertShape` مرة أخرى قبل `EndGroupShape`.

## الاختلافات الشائعة وحالات الحافة

| Situation | How to handle it |
|-----------|-----------------|
| **Different units** – لديك قياسات بالسنتيمتر | حوّل السنتيمترات إلى نقاط (`1 cm ≈ 28.35 pt`) قبل استدعاء `InsertShape`. |
| **Adding a text label** – تريد تسمية داخل المجموعة | أدخل `ShapeType.TextBox` بعد المستطيل والإهليلج، ثم عيّن خاصية `Text`. |
| **Applying a fill color** – تحتاج إلى مستطيل أزرق | بعد `InsertShape`، استرجع الشكل الأخير عبر `builder.CurrentParagraph.Runs[0].Font` ثم عيّن `shape.FillColor = System.Drawing.Color.Blue;`. |
| **Using a different document format** – تستهدف `.doc` بدلاً من `.docx` | الكود نفسه يعمل؛ فقط غيّر امتداد الملف عند استدعاء `Save`. Aspose.Words يتعامل تلقائيًا مع الصيغة. |

## نصائح احترافية

* **Reuse the builder** – يمكنك بدء وإنهاء مجموعات متعددة في نفس المستند؛ فقط استدعِ `StartGroupShape` مرة أخرى بعد `EndGroupShape`.  
* **Performance** – إدراج الأشكال على دفعات داخل كتلة `StartGroupShape/EndGroupShape` واحدة أسرع من إدراج الأشكال بشكل منفرد خارج مجموعة.  
* **Licensing** – رخصة التقييم تضيف علامة مائية على الصفحة الأولى. قم بتثبيت رخصة صحيحة لإزالتها في بيئات الإنتاج.

## الخلاصة

أنت الآن تعرف كيف **group shapes in Word** باستخدام C#، وكيف **add rectangle**، وكيف **add ellipse**، وكيف **insert rectangle shape Word** المستندات باستخدام Aspose.Words. المثال الكامل القابل للتنفيذ يوضح كل خطوة من إعداد المشروع إلى حفظ الملف النهائي.

من هنا يمكنك استكشاف أنواع أشكال إضافية، تطبيق الأنماط، أو دمج الأشكال المجمعة مع الجداول والصور لإنشاء مستندات متقدمة يتم إنشاؤها برمجيًا.

---

**الخطوات التالية**

* تعلم كيفية **rotate grouped shapes**: استخدم `Shape.RotationAngle` بعد إغلاق المجموعة.  
* استكشف **fill and outline customization** للمستطيلات والإهليلجات.  
* دمج هذه المنطق في واجهة برمجة تطبيقات ASP.NET Core لتوليد التقارير عند الطلب.  

برمجة سعيدة!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مجموعة شكل في مستند Word باستخدام Aspose.Words لـ .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [إدراج أشكال في مستندات Word باستخدام Aspose.Words لـ .NET](/words/english/net/working-with-shapes/insert-shape/)
- [إنشاء شكل مستطيل في Word – دليل Aspose.Words الكامل](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}