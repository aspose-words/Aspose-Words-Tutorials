---
category: general
date: 2026-10-23
description: تعلم كيفية إدراج إهليلج وكيفية إضافة شكل مستطيل في Word باستخدام Aspose.Words.
  يتضمن نقل المؤشر إلى الشكل وكيفية إنشاء مجموعة أشكال.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert ellipse
- how to add rectangle
- move cursor to shape
- insert rectangle shape word
- how to create group shape
language: ar
lastmod: 2026-10-23
og_description: كيفية إدراج الشكل البيضاوي وكيفية إضافة شكل مستطيل في Word باستخدام
  Aspose.Words. اتبع الدليل خطوة بخطوة لنقل المؤشر إلى الشكل وإنشاء مجموعة أشكال.
og_image_alt: Screenshot of a Word document showing a group shape containing a rectangle
  and an ellipse
og_title: كيفية إدراج أشكال إهليلجية ومستطيلة في مجموعة أشكال في Word
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to insert ellipse and how to add rectangle shape in Word
    using Aspose.Words. Includes move cursor to shape and how to create group shape.
  headline: How to insert ellipse and rectangle shapes inside a group shape with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: كيفية إدراج أشكال إهليلجية ومستطيلة داخل مجموعة أشكال باستخدام Aspose.Words
url: /ar/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إدراج أشكال القطع الناقص والمستطيل داخل شكل مجموعة باستخدام Aspose.Words

إذا كنت بحاجة إلى معرفة **كيفية إدراج القطع الناقص** في مستند Word برمجياً، فإن هذا الدليل يوضح العملية بالكامل. ستتعرف أيضًا على **كيفية إضافة شكل مستطيل**، وتتعلم **نقل المؤشر إلى الشكل**، وتكتشف **كيفية إنشاء شكل مجموعة** يحتوي على عدة كائنات رسومية.

غالبًا ما تتطلب أتمتة Word تموضعًا دقيقًا للكائنات الرسومية. في نهاية هذا البرنامج التعليمي يمكنك إنشاء ملف `.docx` يحتوي على مستطيل وقطعة ناقص مجمّعين، جاهزين لمزيد من التنسيق أو التصدير. لا تحتاج إلى أدوات خارجية بخلاف مكتبة Aspose.Words for .NET وبيئة تطوير .NET.

## المتطلبات المسبقة

* تثبيت .NET 6.0 أو أحدث.
* إضافة Aspose.Words for .NET (حزمة NuGet `Aspose.Words`) إلى مشروعك.
* معرفة أساسية بصياغة C# وVisual Studio (أو أي بيئة تطوير متكاملة).

تضمن هذه المتطلبات تجميع الشيفرة دون الحاجة إلى إعدادات إضافية.

## كيفية إنشاء شكل مجموعة في Word

يعمل شكل المجموعة كحاوية تسمح لك بنقل أو تدوير أو تنسيق عدة أشكال كوحدة واحدة. الشيفرة التالية تنشئ مجموعة بحجم محدد (300 × 200 نقطة) وتجهّز المستند لمزيد من عمليات الرسم.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapeDemo
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a group shape that will act as a container for other shapes.
        GroupShape group = builder.InsertGroupShape(300, 200);
        
        // The group shape is now part of the document.
        // Subsequent shape insertions will be placed inside this group.
```

*لماذا هذه الخطوة مهمة*: يحدد شكل المجموعة نظام إحداثيات محلي. جميع الأشكال التي تُضاف بعد نقل المؤشر إلى داخل المجموعة سيتم تموضعها بالنسبة لأصل المجموعة، مما يجعل حسابات التخطيط بسيطة.

## كيفية إضافة شكل مستطيل في Word

الآن بعد وجود المجموعة، يمكنك **إدراج شكل مستطيل** داخلها. سيعمل المستطيل كخلفية أو كعنصر نائب بصري لمحتوى آخر.

```csharp
        // Move the cursor into the group so that the next shape is added to it.
        builder.MoveTo(group);
        
        // Insert a rectangle of width 100 points and height 50 points.
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

*شرح*: `MoveTo(group)` يخبر الـ builder أن نقطة الإدراج النشطة هي شكل المجموعة. بدون نقل المؤشر، سيضيف `InsertShape` المستطيل إلى جسم المستند الرئيسي بدلاً من المجموعة.

## كيفية إدراج القطع الناقص

مع وجود المستطيل، يمكنك الآن توضيح **كيفية إدراج القطع الناقص**. سيُوسّط القطع الناقص داخل نفس المجموعة، متراكبًا مع المستطيل إذا رغبت.

```csharp
        // Keep the cursor inside the same group.
        builder.MoveTo(group);
        
        // Insert an ellipse of width 80 points and height 80 points.
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

*لماذا يجب نقل المؤشر*: كل استدعاء لـ `InsertShape` يراعي موقع المؤشر الحالي. إعادة استدعاء `MoveTo(group)` يضمن أن القطع الناقص يكون أيضًا طفلًا للمجموعة، محافظًا على الهيكلية المطلوبة.

## نقل المؤشر إلى الشكل قبل إدراج كائنات إضافية

إذا كنت بحاجة إلى إضافة المزيد من الأشكال لاحقًا، دائمًا **انقل المؤشر إلى الشكل** قبل كل إدراج. هذا النمط يمنع وضعًا غير مقصود خارج المجموعة.

```csharp
        // Example: add a third shape, such as a line.
        builder.MoveTo(group);
        builder.InsertShape(ShapeType.Line, 150, 0);
```

*نصيحة*: إعادة استخدام `MoveTo(group)` منخفضة التكلفة وتحسّن قابلية قراءة الشيفرة. كما أنها تجعل الصيانة المستقبلية أسهل لأن سياق الإدراج واضح.

## حفظ المستند

أخيرًا، احفظ المستند على القرص. المثال يحفظ الملف باسم `GroupShape.docx` في المجلد الذي تحدده.

```csharp
        // Save the document to the desired location.
        document.Save(@"C:\Temp\GroupShape.docx");
    }
}
```

عند فتح الملف المحفوظ في Microsoft Word، سترى مجموعة واحدة تحتوي على مستطيل وقطعة ناقص، كلاهما موضعهما صحيح.

### النتيجة المتوقعة

* ملف `.docx` باسم `GroupShape.docx`.
* داخل المستند، كائن رسم مجمّع بحجم 300 × 200 نقطة.
* داخل المجموعة:
  * مستطيل (100 × 50 نقطة) يقع عند أصل المجموعة.
  * قطعة ناقص (80 × 80 نقطة) متراكبة مع المستطيل.
  * أي أشكال إضافية قمت بإضافتها بعد نقل المؤشر.

## الاختلافات الشائعة وحالات الحافة

| الحالة | النهج الموصى به |
|-----------|----------------------|
| **أحجام وحدات مختلفة** | Aspose.Words يستخدم النقاط (1 pt = 1/72 in). حوّل السنتيمترات أو البوصات إلى نقاط قبل استدعاء `InsertShape`. |
| **تدوير الأشكال داخل المجموعة** | بعد إدراج شكل، استرجع كائن `ShapeBase` الخاص به واضبط `ShapeBase.RotationAngle`. |
| **إضافة نص داخل الشكل** | استخدم `ShapeBase.AppendChild(new Paragraph(document))` ثم أضف `Run` بالنص المطلوب. |
| **الحفظ كملف PDF بدلاً من DOCX** | استدعِ `document.Save("GroupShape.pdf", SaveFormat.Pdf);` – يتم الحفاظ على هيكلية المجموعة في مخرجات PDF. |

تظهر هذه الاختلافات أن منطق **كيفية إدراج القطع الناقص** نفسه يمكن تكييفه للعديد من السيناريوهات الواقعية.

## نصائح احترافية

* **إعادة استخدام نفس كائن `DocumentBuilder`** – يقلل ذلك من استهلاك الذاكرة ويحافظ على حالة المستند متسقة.
* **التحقق من أبعاد الشكل** – قد تتسبب العرض أو الارتفاعات الكبيرة جدًا في مشكلات عرض في إصدارات Word القديمة.
* **تجميع قبل التنسيق** – تطبيق ألوان التعبئة أو أنماط الخط على المجموعة بعد إضافة جميع الأطفال يضمن مظهرًا موحدًا.

## الخلاصة

أنت الآن تفهم **كيفية إدراج القطع الناقص** و**كيفية إضافة المستطيل** داخل حاوية مجمّعة في مستند Word باستخدام Aspose.Words. من خلال **نقل المؤشر إلى الشكل** باستمرار قبل كل إدراج، تحافظ على هيكلية نظيفة وتجنب الوضع غير المقصود. المثال الكامل يُجمع، يُنفّذ، وينتج شكلًا مجمّعًا يمكن تخصيصه أكثر أو تصديره.

هل أنت مستعد لاستكشاف المزيد؟ جرّب دمج هذه التقنية مع **كيفية إنشاء شكل مجموعة** لإنشاء مخططات معقدة، أو جرب **إدراج شكل مستطيل في Word** جنبًا إلى جنب مع صناديق النص لإنشاء تقارير غنية. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء شكل مستطيل وأشكال مجموعة في Word باستخدام Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [كيفية إنشاء مستند Word فارغ وإضافة شكل قطع ناقص مخفي في C#](/words/english/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/)
- [كيفية إنشاء شكل مجموعة docx وإضافة عناصر تحكم تفاعلية في C#](/words/english/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}