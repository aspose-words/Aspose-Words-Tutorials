---
category: general
date: 2026-01-06
description: كيفية إضافة ظل إلى شكل في Word باستخدام Aspose.Words C#. تعلم تطبيق الظل
  على الشكل، ضبط زاوية الظل، وتعديل مسافة الظل بسرعة.
draft: false
keywords:
- how to add shadow
- apply shadow to shape
- add shape shadow
- set shadow angle
- adjust shadow distance
language: ar
og_description: كيفية إضافة ظل إلى شكل Word في C#. يوضح هذا البرنامج التعليمي كيفية
  تطبيق الظل على الشكل، وتعيين زاوية الظل، وضبط مسافة الظل باستخدام Aspose.Words.
og_title: كيفية إضافة ظل إلى شكل في Word – دليل Aspose.Words الكامل
tags:
- Aspose.Words
- C#
- Document Processing
- Graphics
title: كيفية إضافة ظل إلى شكل Word باستخدام Aspose.Words – دليل خطوة بخطوة
url: /ar/net/programming-with-shapes/how-to-add-shadow-to-a-word-shape-using-aspose-words-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إضافة ظل إلى شكل Word باستخدام Aspose.Words

هل تساءلت يومًا **كيف تضيف ظلًا** إلى شكل في مستند Word دون فتح Word نفسه؟ لست وحدك—غالبًا ما يحتاج المطورون إلى هذا اللمسة البصرية للتقارير أو الفواتير أو النشرات التسويقية، لكنهم لا يرغبون في تشغيل الواجهة الرسومية في كل مرة.

في هذا الدرس سنستعرض **كيفية إضافة ظل** إلى شكل برمجيًا، نشرح لماذا كل خاصية مهمة، ونظهر لك كيفية *تطبيق الظل على الشكل*، *تعيين زاوية الظل*، و*ضبط مسافة الظل* ببضع أسطر من كود C#.

> **ما ستحصل عليه:** مثال كامل قابل للتنفيذ يحمل ملف DOCX، يضيف ظلًا واقعيًا إلى أول شكل، ويحفظ النتيجة كملف جديد. لا تحتاج إلى أدوات خارجية، فقط Aspose.Words for .NET.

## المتطلبات المسبقة

- .NET 6.0 (أو أي نسخة حديثة من .NET Framework)  
- Aspose.Words for .NET ≥ 23.10 (أحدث نسخة مستقرة وقت كتابة هذا الدرس)  
- مستند Word (`shapes.docx`) يحتوي على شكل رسومي واحد على الأقل  
- Visual Studio، Rider، أو أي بيئة تطوير C# تفضّلها  

إذا كنت تفتقد المكتبة، احصل عليها من NuGet:

```bash
dotnet add package Aspose.Words
```

الآن بعد أن غطينا الأساسيات، لننتقل إلى الخطوات الفعلية.

## كيفية إضافة ظل إلى شكل – نظرة عامة

جوهر **كيفية إضافة ظل** يكمن في كائن `ShadowFormat` الذي يقدمه كل `Shape`. فكر في `ShadowFormat` كـ "ورقة الأنماط" للظل—خصائصه تحدد الرؤية، اللون، الضبابية، الإزاحة، والاتجاه.

فيما يلي خارطة طريق عالية المستوى:

1. تحميل المستند المصدر.  
2. استرجاع الـ `Shape` المستهدف.  
3. الحصول على `ShadowFormat` الخاص به.  
4. ضبط الخصائص البصرية للظل (بما في ذلك *تعيين زاوية الظل* و*ضبط مسافة الظل*).  
5. حفظ المستند المعدل.

كل خطوة موضحة في قسمها الخاص، بحيث يمكنك اختيار ما تحتاجه فقط.

<img src="shadow-example.png" alt="how to add shadow example in Word document">

## الخطوة 1 – تحميل مستند Word

أولًا، نحتاج إلى كائن `Document` يشير إلى ملف المصدر. هذه العملية خفيفة؛ Aspose.Words يقرأ الملف ويبني شجرة DOM في الذاكرة.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Load the DOCX that already contains a shape.
Document doc = new Document("YOUR_DIRECTORY/shapes.docx");
```

**لماذا هذا مهم:** تحميل المستند يمنحنا الوصول إلى شجرة العقد، حيث توجد الأشكال كـ `NodeType.Shape`. إذا تخطيت هذه الخطوة، لن يكون هناك شيء لتطبيق الظل عليه.

## الخطوة 2 – استرجاع أول شكل (أو أي شكل تريده)

يمكنك جلب شكل حسب الفهرس، أو الاسم، أو شرط مخصص. للتبسيط، سنأخذ أول شكل في المستند. طريقة `GetChild` تتجول في الشجرة بعمق أول، وتعيد العقدة المطلوبة.

```csharp
// Grab the first shape – change the index if you need a different one.
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (shape == null)
{
    throw new InvalidOperationException("No shape found in the document.");
}
```

**نصيحة احترافية:** إذا كان مستندك يحتوي على عدة أشكال، يمكنك التكرار على `doc.GetChildNodes(NodeType.Shape, true)` وتطبيق الظل على كلٍ منها. هذا شائع عندما تحتاج إلى *إضافة ظل للشكل* على شريحة أو صفحة كاملة.

## الخطوة 3 – الوصول إلى كائن تنسيق الظل وتكوينه

الآن وصلنا إلى جوهر **كيفية إضافة ظل**: كائن `ShadowFormat`. هذا الكائن يحمل كل تعديل يمكنك إجراؤه على مظهر الظل.

```csharp
// Step 3: Get the shadow format for the shape.
ShadowFormat shadow = shape.ShadowFormat;

// Make the shadow visible.
shadow.Visible = true;

// Choose a dark gray color for a subtle effect.
shadow.Color = Color.DarkGray;

// Set transparency to 30 % (0.0 = opaque, 1.0 = fully transparent).
shadow.Transparency = 0.3;

// Blur radius – larger values give a softer edge.
shadow.Size = 5;
```

### تعيين زاوية الظل وضبط مسافة الظل

تظهر هنا كلمات المفتاح *تعيين زاوية الظل* و*ضبط مسافة الظل*. الزاوية تحدد اتجاه الضوء الظاهري، بينما المسافة تحدد بعد الظل عن الشكل.

```csharp
// Angle in degrees – 45° points down‑right.
shadow.Angle = 45;

// Distance in points – how far the shadow is shifted.
shadow.Distance = 3;
```

**لماذا هذه القيم؟** زاوية 45° مع مسافة 3 نقطة تحاكي مصدر ضوء من أعلى اليسار، وهو ما يبدو طبيعيًا لمعظم تنسيقات المستندات. يمكنك التجربة: 0° يضع الظل مباشرةً أسفل الشكل، و180° يوجهه إلى الأعلى.

## الخطوة 4 – حفظ المستند والتحقق من النتيجة

بعد ضبط خصائص الظل، كل ما عليك هو كتابة المستند مرة أخرى إلى القرص. Aspose.Words يتولى كل تفاصيل OOXML منخفضة المستوى.

```csharp
// Save the modified document with the new shadow effect.
doc.Save("YOUR_DIRECTORY/shadowed.docx");
```

افتح `shadowed.docx` في Microsoft Word أو أي عارض متوافق—يجب أن ترى الشكل الأول الآن يحمل ظلًا رماديًا داكنًا ناعمًا بزاوية 45°.

### قائمة التحقق السريعة

- **الرؤية:** هل الظل فعليًا مرسوم؟ (`shadow.Visible` يجب أن يكون `true`).  
- **اللون والشفافية:** هل الظل يبدو رماديًا خفيفًا بدلًا من أسود قاسي؟  
- **الزاوية والمسافة:** هل الظل يظهر بالإزاحة التي حددتها؟  
- **الضبابية (الحجم):** هل الحافة ناعمة بما يكفي لتصميمك؟  

إذا لاحظت أي شيء غير صحيح، عدل الخاصية المقابلة وأعد الحفظ. التغييرات تظهر فورًا.

## تنويعات شائعة ومعالجة الحالات الطرفية

### إضافة ظلال إلى عدة أشكال

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape s in shapes)
{
    ShadowFormat sf = s.ShadowFormat;
    sf.Visible = true;
    sf.Color = Color.Black;
    sf.Transparency = 0.2;
    sf.Size = 4;
    sf.Angle = 30;
    sf.Distance = 2;
}
doc.Save("YOUR_DIRECTORY/all_shapes_shadowed.docx");
```

### إعادة تعيين الظل (إزالته)

إذا احتجت إلى *إضافة ظل للشكل* بشكل شرطي، يمكنك إيقافه لاحقًا:

```csharp
shape.ShadowFormat.Visible = false;
```

### ملاحظات التوافق

- Aspose.Words 23.10+ يدعم بالكامل خصائص الظل لـ DOCX، DOC، وحتى تصدير PDF.  
- يبقى تأثير الظل محفوظًا عند التحويل إلى PDF عبر `doc.Save("out.pdf")`.  
- الإصدارات القديمة من Word (< 2007) لا تخزن ظلال OOXML، لذا سيفقد التأثير إذا حفظت كـ `.doc`. استخدم `.docx` للحصول على أفضل النتائج.

## نصيحة احترافية – استخدم طريقة مساعدة لإعادة الاستخدام

إذا وجدت نفسك تطبق نفس إعدادات الظل في مشاريع متعددة، غلف المنطق في طريقة مساعدة:

```csharp
public static void ApplyStandardShadow(Shape target, Color? color = null,
                                        double transparency = 0.3,
                                        double size = 5,
                                        double angle = 45,
                                        double distance = 3)
{
    ShadowFormat sf = target.ShadowFormat;
    sf.Visible = true;
    sf.Color = color ?? Color.DarkGray;
    sf.Transparency = transparency;
    sf.Size = size;
    sf.Angle = angle;
    sf.Distance = distance;
}
```

الآن سطر واحد `ApplyStandardShadow(shape);` يقوم بكل مهمة *تطبيق الظل على الشكل*.

## الخلاصة

غطّينا **كيفية إضافة ظل** إلى شكل Word باستخدام Aspose.Words من البداية حتى النهاية. بتحميل المستند، جلب الشكل، تكوين `ShadowFormat` (بما في ذلك *تعيين زاوية الظل* و*ضبط مسافة الظل*), وحفظ الملف، يمكنك إعطاء أي مخطط ظلًا احترافيًا دون الحاجة لفتح Word.

لا تتردد في تجربة المفاهيم الثانوية—*تطبيق الظل على الشكل* بألوان مختلفة، *إضافة ظل للشكل* لمجموعة كاملة، أو تعديل *تعيين زاوية الظل* لتأثير إضاءة دراماتيكي. الخطوة المنطقية التالية هي دمج هذه الظلال مع ميزات تنسيق أخرى مثل الحدود، الانعكاسات، أو حتى الدوران ثلاثي الأبعاد.

هل لديك أسئلة حول الحالات الطرفية، الأداء، أو تحويل النتيجة إلى PDF؟ اترك تعليقًا أدناه، ونتمنى لك برمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}