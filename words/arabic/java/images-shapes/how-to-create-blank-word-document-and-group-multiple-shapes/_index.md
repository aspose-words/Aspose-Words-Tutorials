---
category: general
date: 2026-10-26
description: إنشاء مستند Word فارغ في C# وتعلم كيفية إدراج مجموعة أشكال، ثم إضافة
  شكل مستطيل إلى المجموعة. يغطي هذا الدليل تجميع أشكال متعددة خطوة بخطوة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group multiple shapes
- insert rectangle shape
- how to insert group
- how to add rectangle
language: ar
lastmod: 2026-10-26
og_description: إنشاء مستند Word فارغ باستخدام C# ومعرفة كيفية إدراج مجموعة، ثم إضافة
  شكل مستطيل. إتقان تجميع أشكال متعددة مع مثال كامل للكود.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle shape
og_title: إنشاء مستند Word فارغ وتجميع أشكال متعددة – دليل C#
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create a blank Word document in C# and learn how to insert a group
    shape, then add a rectangle shape to the group. This guide covers group multiple
    shapes step‑by‑step.
  headline: How to create blank Word document and group multiple shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: كيفية إنشاء مستند Word فارغ وتجميع أشكال متعددة
url: /ar/java/images-shapes/how-to-create-blank-word-document-and-group-multiple-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مستند Word فارغ وتجميع أشكال متعددة

إذا كنت بحاجة إلى **إنشاء مستند Word فارغ** برمجيًا، فإن هذا الدليل يوضح لك بالضبط كيفية القيام بذلك. سترى كيفية إدراج شكل مجموعة، ثم **إضافة مستطيل** إلى تلك المجموعة، مع تغطية سير العمل الكامل من مستند فارغ إلى رسم مجمع.

العمل مع ملفات Word غالبًا ما يعني ترتيب عدة رسومات معًا—تخيل مخططًا مكوّنًا من أشكال متعددة. بنهاية هذا الدليل ستتمكن من **تجميع أشكال متعددة**، وإدراج **شكل مستطيل**، وفهم **كيفية إدراج مجموعة** و**كيفية إضافة مستطيل** بطريقة نظيفة وقابلة لإعادة الاستخدام.

## ما ستحتاجه

* .NET 6.0 أو أحدث (الكود يعمل أيضًا مع .NET Framework 4.6+)
* **Aspose.Words for .NET** حزمة NuGet (`Install-Package Aspose.Words`)
* فهم أساسي للغة C# وبيئة Visual Studio IDE (أي بيئة تطوير تعمل)

> **نصيحة احترافية:** Aspose.Words يعمل بالكامل دون اتصال؛ لا تحتاج إلى اتصال بالإنترنت بعد تثبيت الحزمة.

## الخطوة 1: إنشاء مستند Word فارغ

العملية الأولى هي إنشاء كائن `Document` فارغ. هذا الكائن يمثل **مستند Word الفارغ** الذي ستضيف إليه الأشكال لاحقًا.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – create a new blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*لماذا هذا مهم:* `Document` بدون أي أقسام أو فقرات لا يزال ملف .docx صالحًا. البدء من صفحة نظيفة يضمن عدم تدخل أي تنسيق مخفي مع الأشكال التي ستضيفها لاحقًا.

## الخطوة 2: إدراج شكل مجموعة (how to insert group)

يعمل **group shape** كحاوية يمكنها احتواء كائنات رسم أخرى. في Aspose.Words يمكنك إنشاؤه باستخدام `InsertGroupShape`.

```csharp
        // Step 2 – insert a group shape that will hold other shapes
        GroupShape group = builder.InsertGroupShape();   // <-- container for shapes
```

*لماذا تستخدم مجموعة؟* التجميع يتيح لك تحريك أو تدوير أو تغيير حجم عدة أشكال كوحدة واحدة. هذا أساسي للمخططات التي تحتاج فيها العناصر إلى البقاء محاذية.

## الخطوة 3: إدراج شكل مستطيل (insert rectangle shape)

الآن أضف مستطيلًا إلى المستند. تُعيد طريقة `InsertShape` كائن `Shape` يمكنك لاحقًا ربطه بالمجموعة.

```csharp
        // Step 3 – create a rectangle shape with specific dimensions
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

*لماذا مستطيل؟* المستطيلات هي أكثر العناصر الأساسية شيوعًا للمخططات الانسيابية، ونماذج واجهات المستخدم، والرسومات النائبة. الأبعاد تُعبّر بالنقاط (1 pt ≈ 1/72 inch).

## الخطوة 4: إضافة المستطيل إلى المجموعة (how to add rectangle)

الشكل الذي تم إنشاؤه باستخدام `InsertShape` يعيش مباشرةً في جسم المستند. لجعله جزءًا من المجموعة، استدعِ `AppendChild` على `GroupShape`.

```csharp
        // Step 4 – add the rectangle to the previously created group
        group.AppendChild(rectangle);   // <-- rectangle now belongs to the group
```

*ماذا يحدث خلف الكواليس؟* `AppendChild` ينقل عقدة المستطيل من القصة الرئيسية للمستند إلى مجموعة داخلية للمجموعة، مع الحفاظ على حجمه وموقعه بالنسبة لأصل المجموعة.

## الخطوة 5: حفظ المستند

أخيرًا، احفظ الملف على القرص. يمكنك فتح ملف `.docx` الناتج في Microsoft Word لرؤية المستطيل المجمع.

```csharp
        // Step 5 – save the document to a file
        doc.Save("GroupedShapeExample.docx");
    }
}
```

> **حالة خاصة:** إذا كنت تنوي إضافة أشكال أخرى (مثل دوائر، خطوط) إلى نفس المجموعة، كرّر **الخطوة 3** و**الخطوة 4** لكل شكل جديد قبل الحفظ. ستقوم المجموعة تلقائيًا بتعديل صندوق الحدود الخاص بها لتشمل جميع العناصر الفرعية.

## كيفية تجميع أشكال متعددة – توسيع المثال

فيما يلي مقتطف سريع يضيف شكلًا ثانيًا (بيضاوي) إلى نفس المجموعة، موضحًا **تجميع أشكال متعددة** في مستند واحد.

```csharp
        // Additional shape: an ellipse
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
        group.AppendChild(ellipse);   // now the group contains rectangle + ellipse
```

عند فتح `GroupedShapeExample.docx`، سترى المستطيل والبيضاوي يتحركان معًا عند اختيار المجموعة في Word.

## أسئلة شائعة وحلول المشكلات

| السؤال | الجواب |
|----------|--------|
| **هل أحتاج إلى ترخيص لـ Aspose.Words؟** | التقييم المجاني يعمل بدون ترخيص، لكنه يضيف علامة مائية. للإنتاج، قم بتطبيق ترخيص لإزالة العلامة المائية وإتاحة الأداء الكامل. |
| **هل يمكنني وضع الأشكال بدقة؟** | نعم. بعد إدراج الشكل يمكنك تعيين خصائص `Shape.Left`، `Shape.Top`، `Shape.Width`، و`Shape.Height`. |
| **ماذا لو اختفى المستطيل بعد الحفظ؟** | تأكد من استدعاء `group.AppendChild(rectangle)` *بعد* إدراج المستطيل. يجب إضافة الشكل إلى جسم المستند أولاً ثم نقله إلى المجموعة. |
| **هل يمكن تجميع الأشكال عبر أقسام مختلفة؟** | لا. يجب أن تنتمي جميع الأشكال في مجموعة إلى نفس القصة (القسم). أنشئ مجموعات منفصلة لكل قسم إذا لزم الأمر. |

## ملخص

أنت الآن تعرف كيفية **إنشاء مستند Word فارغ**، **إدراج مجموعة**، **إضافة مستطيل**، و**تجميع أشكال متعددة** باستخدام Aspose.Words for .NET. يمكن نسخ المثال الكامل القابل للتنفيذ أعلاه إلى تطبيق كونسول وتشغيله فورًا.

## الخطوات التالية

* جرّب أحجام وألوان **insert rectangle shape** المختلفة (`rectangle.FillColor = Color.LightBlue;`).  
* استكشف أنواع أشكال أخرى (`ShapeType.Polygon`، `ShapeType.Line`) لإثراء مخططاتك.  
* تعلم كيفية تحويل ملف `.docx` النهائي إلى PDF (`doc.Save("output.pdf");`) للتوزيع.  
* تعمق في **how to add rectangle** إلى المستندات الموجودة التي تحتوي بالفعل على نص—استخدم `DocumentBuilder.MoveTo` لتحديد موقع المجموعة حيث تحتاجها.

لا تتردد في تعديل الكود لاحتياجاتك الخاصة في التقارير أو إنشاء المخططات. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء مستند Word فارغ وتجميع الأشكال في C#](/words/english/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/)
- [كيفية تجميع الأشكال في Word وإضافة أشكال إلى مستند Word](/words/english/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/)
- [كيفية إنشاء شكل مستطيل وتجمع الأشكال في Word باستخدام Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}