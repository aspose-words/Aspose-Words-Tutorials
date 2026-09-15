---
category: general
date: 2026-09-14
description: تعلم كيفية إخفاء الشكل في Word باستخدام C# — بما في ذلك كود إنشاء مستند
  Word، وإدراج شكل مستطيل في Word، وإخفاء الشكل في Word برمجياً.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- create word document code
- insert rectangle shape word
language: ar
lastmod: 2026-09-14
og_description: كيفية إخفاء الشكل في Word باستخدام C# — دليل خطوة بخطوة يوضح أيضًا
  كيفية إنشاء كود مستند Word وإدراج شكل مستطيل في Word.
og_image_alt: Word document preview with a visible rectangle shape and a hidden ellipse
  shape
og_title: كيفية إخفاء الشكل في مستند Word باستخدام كود C#
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to hide shape in Word using C#—including create word document
    code, insert rectangle shape word, and hide shape in word programmatically.
  headline: How to hide shape in a Word document with C# code
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: كيفية إخفاء الشكل في مستند Word باستخدام كود C#
url: /ar/net/programming-with-shapes/how-to-hide-shape-in-a-word-document-with-c-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إخفاء الشكل في مستند Word باستخدام كود C#

إذا كنت بحاجة إلى **how to hide shape** في ملف Word، يوضح هذا الدرس الحل الكامل. ستتعرف على كيفية إنشاء مستند Word، وإدراج شكل مستطيل، وإضافة شكل بيضاوي، وإخفاء ذلك البيضاوي بحيث يظهر المستطيل فقط عند فتح الملف.

الدليل يغطي كل ما تحتاجه—بدون مراجع خارجية، فقط الكود والشروحات. في النهاية ستتمكن من تضمين رسومات مخفية في أي مستند Word تُنشئه برمجياً.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (الكود يعمل أيضاً مع .NET Framework 4.7+)
- Aspose.Words for .NET (نسخة تجريبية مجانية أو نسخة مرخصة)  
  قم بتثبيتها عبر NuGet: `dotnet add package Aspose.Words`
- إلمام أساسي بـ C# وVisual Studio أو أي بيئة تطوير تفضلها

## الخطوة 1: إعداد المشروع واستيراد المساحات الاسمية

ابدأ بإنشاء تطبيق console جديد وأضف عبارات `using` المطلوبة. هذه الاستيرادات تمنحك الوصول إلى كائنات `Document` و`DocumentBuilder` وفئات الرسم اللازمة للتعامل مع الأشكال.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code follows in the next steps
        }
    }
}
```

**لماذا هذا مهم** – استيراد المساحات الاسمية الصحيحة يمنع أخطاء التجميع ويجعل واجهة API متاحة لإنشاء الأشكال والتحكم في رؤيتها.

## الخطوة 2: إنشاء مستند Word جديد ومُنشئ المحتوى

كائن `Document` يمثل الملف، بينما يوفر `DocumentBuilder` واجهة API سلسة لإضافة المحتوى. هذه هي النقطة الأولى التي تطبق فيها منطق **how to hide shape**: تحتاج إلى سياق المستند قبل أن يمكن وجود أي شكل.

```csharp
// Step 2: Create a new blank document and a builder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

**شرح** – كائن `Document` يبدأ فارغاً. يتم وضع `DocumentBuilder` في بداية الفقرة الأولى، جاهزاً لإدراج الأشكال أو النص.

## الخطوة 3: إدراج شكل مستطيل مرئي

المستطيل سيكون الشكل الذي يبقى مرئياً عند فتح المستند. يمكنك التحكم في حجمه وموقعه وتنسيقه مباشرة عبر كائن الشكل.

```csharp
// Step 3: Insert a visible rectangle shape and position it
Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
visibleRectangle.Left = 50;                 // 50 points from the left margin
visibleRectangle.Top = 100;                 // 100 points from the top of the page
visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;
```

**لماذا هذه الخطوة** – إضافة مستطيل تُظهر متطلب **insert rectangle shape word**. ضبط `FillColor` و`LineColor` يجعل الشكل واضحاً في المستند النهائي.

## الخطوة 4: إدراج شكل بيضاوي وإخفائه

الآن تضيف الشكل الذي تنوي إخفاؤه. الخاصية `Hidden` تخبر Word بعدم عرض الشكل في الواجهة، مع بقائه جزءاً من بنية المستند.

```csharp
// Step 4: Insert an ellipse shape, position it, and hide it from view
Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
hiddenEllipse.Left = 200;      // Position away from the rectangle
hiddenEllipse.Top = 100;
hiddenEllipse.Hidden = true;   // This flag implements how to hide shape
```

**شرح** – ضبط `Hidden = true` هو جوهر **hide shape in word**. Word يحترم هذه العلامة أثناء العرض والطباعة العادية، لكن لا يزال بإمكانك الوصول إلى الشكل برمجياً إذا لزم الأمر.

## الخطوة 5: حفظ المستند

أخيراً، اكتب المستند إلى القرص. اختر مجلداً لديك صلاحية كتابة فيه، وأعطِ الملف اسماً واضحاً يعكس هدف الدرس.

```csharp
// Step 5: Save the document with both shapes
string outputPath = @"C:\Temp\ShapeVisibility.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**النتيجة** – فتح `ShapeVisibility.docx` في Microsoft Word يظهر فقط المستطيل الأزرق الفاتح. البيضاوي المخفي لا يظهر، مما يؤكد أنك نجحت في **how to hide shape** في ملف Word.

## مثال كامل يعمل

دمج جميع المقاطع يعطيك برنامجاً واحداً قابلاً للتنفيذ:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert a visible rectangle
            Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            visibleRectangle.Left = 50;
            visibleRectangle.Top = 100;
            visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
            visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;

            // Insert a hidden ellipse
            Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
            hiddenEllipse.Left = 200;
            hiddenEllipse.Top = 100;
            hiddenEllipse.Hidden = true; // hides the shape

            // Save the document
            string outputPath = @"C:\Temp\ShapeVisibility.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### النتيجة المتوقعة

- **مرئية**: عند فتح `ShapeVisibility.docx`، ترى مستطيلاً أزرق فاتحاً موضعاً قرب الهامش الأيسر. لا يظهر أي بيضاوي.
- **برمجية**: يبقى البيضاوي المخفي في XML الخاص بالمستند (`<w:drawing>`) مع الخاصية `w:hidden` مفعلة، ويمكنك التحقق من ذلك بفتح الملف كملف zip وفحص `document.xml`.

## أسئلة شائعة وحالات خاصة

| السؤال | الجواب |
|----------|--------|
| *هل يمكنني إخفاء عدة أشكال؟* | نعم. اضبط `Hidden = true` على كل شكل تريد إخفاؤه. |
| *هل تُطبع الأشكال المخفية؟* | بشكل افتراضي لا تقوم Word بطباعة الكائنات المخفية. إذا احتجت طباعتها، أزل علامة `Hidden` قبل الطباعة. |
| *هل الخاصية المخفية مدعومة في إصدارات Word القديمة؟* | الخاصية `Hidden` جزء من معيار Office Open XML وتعمل في Word 2007 وما بعده. |
| *ماذا لو أردت تبديل الرؤية أثناء التشغيل؟* | استرجع الشكل عبر `document.GetChildNodes(NodeType.Shape, true)` وغيّر قيمة `Hidden` بناءً على منطقك. |

## نصائح احترافية

- **الأداء**: إذا كنت تولد مستندات كثيرة، أعد استخدام نفس كائن `DocumentBuilder` بدلاً من إنشاء واحد جديد لكل ملف.
- **التحكم في الإصدارات**: احفظ ملفات `.docx` المُولدة في مجلد تحت التحكم بالإصدارات؛ يمكن للأشكال المخفية أن تعمل كعلامات بيانات وصفية للمعالجة اللاحقة.
- **الاختبار**: أتمت اختباراً بصرياً سريعاً بتحويل DOCX إلى PDF باستخدام Aspose.Words (`document.Save("out.pdf")`). سيُخفي الـ PDF أيضاً البيضاوي، مما يؤكد أن علامة الإخفاء تنتقل عبر تحويل الصيغ.

## الخلاصة

أنت الآن تعرف **how to hide shape** في مستند Word باستخدام C#. استعرض الدرس إنشاء مستند، **insert rectangle shape word**، إضافة بيضاوي، وتطبيق علامة `Hidden` لتحقيق سلوك **hide shape in word**. مع الكود الكامل القابل للتنفيذ يمكنك دمج رسومات مخفية في أي تدفق عمل تقارير أو قوالب آلية.

### الخطوات التالية

- استكشف خصائص أشكال أخرى مثل الدوران، الظل، وتغليف النص.  
- اجمع بين الأشكال المخفية وخصائص المستند المخصصة لتضمين بيانات قابلة للقراءة آلياً.  
- اطلع على أنماط **create word document code** لإنشاء جداول، مخططات، وعناصر تحكم محتوى لتوسيع مجموعة أدوات الأتمتة الخاصة بك.

لا تتردد في تجربة أنواع أشكال وإعدادات رؤية مختلفة—مشروع أتمتة Word التالي لك على بعد بضع أسطر من الكود فقط!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء شكل مستطيل في Word باستخدام C# – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [إنشاء مستند Word فارغ مع شكل مستطيل بظل – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [دروس ظل شكل Aspose.Words – إضافة ظل إلى شكل Word في C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}