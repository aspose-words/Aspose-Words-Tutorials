---
category: general
date: 2026-10-23
description: إنشاء مستند Word فارغ، إضافة شكل مستطيل، وإخفاء الشكل في Word باستخدام
  Aspose.Words. كود خطوة بخطوة لمطوري .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- how to insert shape
- hide shape word
language: ar
lastmod: 2026-10-23
og_description: أنشئ مستند Word فارغ، أضف شكلاً مستطيلاً، وأخفِ الشكل في Word باستخدام
  Aspose.Words. اتبع المثال الكامل بلغة C#.
og_image_alt: Screenshot of a Word document containing a hidden rectangle shape
og_title: إنشاء مستند Word فارغ وإضافة شكل مستطيل مخفي
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create a blank Word document, add a rectangle shape, and hide the shape
    in Word using Aspose.Words. Step‑by‑step code for .NET developers.
  headline: Create a blank Word document and add a rectangle shape
  type: TechArticle
tags:
- Aspose.Words
- .NET
- Word automation
title: إنشاء مستند Word فارغ وإضافة شكل مستطيل
url: /ar/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word فارغ وإضافة شكل مستطيل

إذا كنت بحاجة إلى **إنشاء مستند Word فارغ**، يوضح لك هذا الدليل كيفية القيام بذلك باستخدام Aspose.Words for .NET. ستتعلم أيضًا **كيفية إدراج شكل**—وبشكل محدد مستطيل—و**إخفاء شكل Word** بحيث لا يؤثر على التخطيط.

يتناول الدليل كل سطر من الشيفرة، يشرح لماذا كل خطوة مهمة، ويغطي المشكلات الشائعة مثل رؤية الشكل المخفي في أوضاع عرض Word المختلفة. في النهاية ستحصل على ملف `.docx` كامل الوظيفة يحتوي على شكل مستطيل مخفي يمكنك لاحقًا إظهاره أو التلاعب به برمجيًا.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.6+)
- حزمة NuGet الخاصة بـ Aspose.Words for .NET (`Install-Package Aspose.Words`)
- بيئة تطوير مثل Visual Studio 2022 أو VS Code مع امتدادات C#
- إلمام أساسي بصياغة C# ومفاهيم مستندات Word

لا يلزم تثبيت Office إضافي لأن Aspose.Words يعمل بالكامل في الذاكرة.

## إنشاء مستند Word فارغ

الخطوة الأولى هي إنشاء كائن `Document` فارغ. هذا الكائن يمثل ملف Word لا يحتوي على أقسام أو فقرات أو محتوى بعد.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

**لماذا هذا مهم:**  
`Document` الفارغ يمنحك لوحة نظيفة. إذا بدأت من قالب موجود، قد ترث الأشكال المخفية أنماطًا غير مرغوب فيها. البدء من الصفر يضمن أن شكل المستطيل الذي تضيفه لاحقًا هو المحتوى الوحيد الذي تتحكم فيه.

## إضافة شكل مستطيل إلى المستند

بعد ذلك، نحتاج إلى `DocumentBuilder` لوضع المحتوى في المستند. طريقة `InsertShape` الخاصة بالباني هي الطريقة القياسية **لإدراج شكل**، مثل المستطيلات أو الدوائر أو الرسومات المخصصة.

```csharp
// Step 2: Initialize a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(document);

// Step 3: Insert a rectangle shape of size 200x100 points
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**لماذا هذا مهم:**  
`InsertShape` تُعيد كائن `Shape` يمكنك تعديل إعداداته لاحقًا (اللون، نمط الخط، إلخ). الأبعاد تُعطى بالنقاط (1 نقطة = 1/72 بوصة)، وهو ما يتطابق مع نظام القياس الداخلي في Word.

### اختياري: تنسيق المستطيل (اختياري)

إذا كنت تريد أن يكون للمستطيل حد مرئي عندما تقوم بإظهاره لاحقًا، يمكنك ضبط وزن الخط ولونه:

```csharp
rectangleShape.LineWeight = 0.5;               // Thin border
rectangleShape.LineColor = System.Drawing.Color.Blue;
```

هذه الأسطر اختيارية لأن الشكل سيُخفى في الخطوة التالية.

## إخفاء الشكل في Word

Word يسمح بإخفاء الأشكال عن التخطيط مع بقائها جزءًا من نموذج كائنات المستند. ضبط الخاصية `Hidden` إلى `true` يجعل الشكل غير مرئي في العرض العادي لكنه لا يزال قابلًا للتحديد عبر الـ API.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
rectangleShape.Hidden = true;
```

**لماذا هذا مهم:**  
الشكل المخفي مفيد لتخزين البيانات الوصفية، أو كعناصر نائبة للمعالجة لاحقًا، أو محتوى شرطي يمكنك إظهاره فقط في ظروف معينة (مثلًا عند إنشاء تقرير نهائي). يبقى الشكل في الملف، لذا يمكنك إظهاره برمجيًا لاحقًا باستخدام `rectangleShape.Hidden = false;`.

## حفظ المستند

أخيرًا، احفظ المستند على القرص. امتداد الملف يحدد تنسيق Word؛ `.docx` هو تنسيق Open XML الحديث.

```csharp
// Step 5: Save the document with the hidden shape
string outputPath = @"C:\Temp\HiddenShape.docx";
document.Save(outputPath);
```

**النتيجة:**  
فتح `HiddenShape.docx` في Microsoft Word يظهر صفحة **فارغة**. المستطيل غير مرئي، ولكن إذا ذهبت إلى **Home → Select → Selection Pane**، ستظهر القائمة التي تحتوي على الشكل ويمكنك تبديل رؤيته.

## مثال كامل يعمل

فيما يلي البرنامج الكامل الذي يمكنك نسخه ولصقه وتشغيله. يتضمن جميع عبارات `using` الضرورية والتعليقات.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for content insertion
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape (200x100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Optional styling (comment out if not needed)
        rectangleShape.LineWeight = 0.5;
        rectangleShape.LineColor = System.Drawing.Color.Blue;

        // Hide the shape so it does not appear in the layout
        rectangleShape.Hidden = true;

        // Save the document
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**المخرجات المتوقعة:**  

- يطبع الـ Console مسار الحفظ.  
- يفتح `HiddenShape.docx` كصفحة فارغة في Word.  
- شكل المستطيل موجود لكنه مخفي؛ يمكنك التحقق منه عبر *Selection Pane* أو برمجيًا بتعيين `Hidden = false` وإعادة فتح الملف.

## أسئلة شائعة وحالات خاصة

| السؤال | الجواب |
|----------|--------|
| **هل يمكنني إخفاء أنواع أشكال أخرى؟** | نعم. أي `Shape` (مثل `ShapeType.Ellipse`، `ShapeType.Picture`) يدعم الخاصية `Hidden`. |
| **هل سيزيد الشكل المخفي من حجم الملف؟** | الزيادة ضئيلة (بضع كيلوبايت) لأن بيانات الشكل تُخزن كـ XML في حزمة `.docx`. |
| **ماذا لو أردت أن يظهر الشكل فقط في عرض الطباعة؟** | استخدم الخاصية `Shape.IsPrint` بدلاً من `Hidden`. ضبط `IsPrint = false` يخفي الشكل من المخرجات المطبوعة لكنه يبقى مرئيًا على الشاشة. |
| **كيف يمكن إظهار الشكل لاحقًا؟** | حمّل المستند، حدد الشكل (مثلاً عبر `Shape.Name`)، ثم اضبط `shape.Hidden = false;` واحفظ. |
| **هل يعمل هذا مع تنسيق .doc (ثنائي)؟** | نعم، يمكن لـ Aspose.Words حفظ إلى `.doc` باستخدام `document.Save("file.doc");`. يتم الحفاظ على علامة الإخفاء. |

## نصائح احترافية

- **قم بتسمية الأشكال الخاصة بك**: `rectangleShape.Name = "PlaceholderRectangle";` يجعل من السهل العثور عليها لاحقًا عبر `document.GetChildNodes(NodeType.Shape, true).Cast<Shape>().FirstOrDefault(s => s.Name == "PlaceholderRectangle")`.
- **معالجة دفعية**: إذا كنت بحاجة لإضافة أشكال مخفية إلى العديد من المستندات، غلف الشيفرة داخل طريقة وأعد استخدام كائن `DocumentBuilder`.
- **الأداء**: إنشاء شكل أمر بسيط، لكن حفظ المستندات الكبيرة بشكل متكرر قد يكون مقيدًا بعمليات الإدخال/الإخراج. فكر في استخدام `MemoryStream` للمعالجة الوسيطة.

## الخلاصة

أنت الآن تعرف كيف **تنشئ مستند Word فارغ**، **تضيف شكل مستطيل**، و**تخفي شكل Word** باستخدام Aspose.Words for .NET. تتيح لك هذه التقنية تضمين عناصر نائبة غير مرئية يمكنك إظهارها أو تعديلها لاحقًا، وهو نمط مفيد لإنشاء تقارير ديناميكية، محتوى شرطي، وتنسيق المستندات.

الخطوات التالية التي قد تستكشفها:

- استبدل المستطيل بصورة أو مخطط باستخدام `ShapeType.Picture`.
- استخدم **how to insert shape** في أقسام الرأس/التذييل لعناصر نائبة على نمط العلامة المائية.
- دمج الأشكال المخفية مع **add rectangle shape**‑based data validation (مثلاً تخزين JSON في خاصية `AlternativeText` للشكل).

برمجة سعيدة، ولا تتردد في تجربة أنواع أشكال أخرى وخيارات الرؤية لتناسب احتياجات أتمتة المستندات الخاصة بك!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مصدر يتضمن أمثلة شيفرة كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مستند Word – كيفية إضافة شكل مستطيل وظل](/words/english/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/)
- [إنشاء مجموعة أشكال في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [إنشاء مستند Word فارغ مع شكل إهليلجي مخفي – دليل C# كامل](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}