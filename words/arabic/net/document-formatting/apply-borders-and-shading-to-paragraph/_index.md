---
title: تطبيق الحدود والتظليل على الفقرة في مستند Word
linktitle: تطبيق الحدود والتظليل على الفقرة في مستند Word
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: قم بتطبيق الحدود والتظليل على الفقرات في مستندات Word باستخدام Aspose.Words for .NET. اتبع دليلنا خطوة بخطوة لتحسين تنسيق مستندك.
weight: 10
url: /ar/net/document-formatting/apply-borders-and-shading-to-paragraph/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تطبيق الحدود والتظليل على الفقرة في مستند Word

## مقدمة

مرحبًا، هل تساءلت يومًا عن كيفية جعل مستندات Word الخاصة بك تبرز من خلال بعض الحدود والتظليلات الرائعة؟ حسنًا، أنت في المكان الصحيح! اليوم، نتعمق في عالم Aspose.Words for .NET لإضفاء الحيوية على فقراتنا. تخيل أن مستندك يبدو أنيقًا مثل عمل مصمم محترف مع بضعة أسطر فقط من التعليمات البرمجية. هل أنت مستعد للبدء؟ هيا بنا!

## المتطلبات الأساسية

قبل أن نبدأ في تعلم البرمجة، دعونا نتأكد من أننا نمتلك كل ما نحتاج إليه. إليك قائمة مرجعية سريعة:

-  Aspose.Words for .NET: يجب أن يكون لديك هذه المكتبة مثبتة. يمكنك تنزيلها من[موقع اسبوس](https://releases.aspose.com/words/net/).
- بيئة التطوير: Visual Studio أو أي بيئة تطوير متكاملة أخرى تدعم .NET.
- المعرفة الأساسية بلغة C#: ما يكفي لفهم أجزاء التعليمات البرمجية وتعديلها.
- رخصة صالحة: إما[رخصة مؤقتة](https://purchase.aspose.com/temporary-license/) أو تم شراؤها من[أسبو](https://purchase.aspose.com/buy).

## استيراد مساحات الأسماء

قبل البدء في الكود، نحتاج إلى التأكد من استيراد المساحات الأساسية اللازمة إلى مشروعنا. وهذا يجعل جميع الميزات الرائعة لـ Aspose.Words في متناول أيدينا.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using Aspose.Words.Drawing;
using System.Drawing;
```

الآن، دعنا نقسم العملية إلى خطوات صغيرة. سيكون لكل خطوة عنوان وشرح مفصل. هل أنت مستعد؟ هيا بنا!

## الخطوة 1: إعداد دليل المستندات الخاص بك

أولاً وقبل كل شيء، نحتاج إلى مكان لحفظ مستندنا المنسق بشكل جميل. دعنا نحدد المسار إلى دليل المستند الخاص بك.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 هذا الدليل هو المكان الذي سيتم فيه حفظ مستندك النهائي. استبدل`"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي على جهازك.

## الخطوة 2: إنشاء مستند جديد وDocumentBuilder

 بعد ذلك، نحتاج إلى إنشاء مستند جديد و`DocumentBuilder` الكائن.`DocumentBuilder` إنها عصانا السحرية التي تمكننا من التحكم في المستند.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 ال`Document` يمثل الكائن مستند Word بأكمله، و`DocumentBuilder` يساعدنا على إضافة المحتوى وتنسيقه.

## الخطوة 3: تحديد حدود الفقرة

الآن، دعنا نضيف بعض الحدود الأنيقة إلى فقرتنا. سنحدد المسافة من النص ونضع أنماط حدود مختلفة.

```csharp
BorderCollection borders = builder.ParagraphFormat.Borders;
borders.DistanceFromText = 20;
borders[BorderType.Left].LineStyle = LineStyle.Double;
borders[BorderType.Right].LineStyle = LineStyle.Double;
borders[BorderType.Top].LineStyle = LineStyle.Double;
borders[BorderType.Bottom].LineStyle = LineStyle.Double;
```

هنا، قمنا بتعيين مسافة 20 نقطة بين النص والحدود. تم تعيين الحدود على جميع الجوانب (اليسار واليمين والأعلى والأسفل) لتكون خطوطًا مزدوجة. أليس هذا رائعًا؟

## الخطوة 4: تطبيق التظليل على الفقرة

الحدود رائعة، ولكن دعنا نرفعها إلى مستوى أعلى من خلال بعض التظليل. سنستخدم نمطًا متقاطعًا قطريًا مع مزيج من الألوان لجعل فقرتنا بارزة.

```csharp
Shading shading = builder.ParagraphFormat.Shading;
shading.Texture = TextureIndex.TextureDiagonalCross;
shading.BackgroundPatternColor = System.Drawing.Color.LightCoral;
shading.ForegroundPatternColor = System.Drawing.Color.LightSalmon;
```

في هذه الخطوة، طبقنا نسيجًا متقاطعًا قطريًا باللون المرجاني الفاتح كلون خلفية واللون السلموني الفاتح كلون أمامي. الأمر أشبه بتزيين فقرتك بملابس مصممة خصيصًا!

## الخطوة 5: إضافة نص إلى الفقرة

ما معنى الفقرة بدون نص؟ دعنا نضيف جملة نموذجية لنرى التنسيق الذي استخدمناه أثناء العمل.

```csharp
builder.Write("I'm a formatted paragraph with double border and nice shading.");
```

يقوم هذا السطر بإدراج النص الخاص بنا في المستند. بسيط، ولكنه الآن محاط بإطار أنيق وخلفية مظللة.

## الخطوة 6: حفظ المستند

أخيرًا، حان الوقت لحفظ عملنا. فلنحفظ المستند في الدليل المحدد باسم وصفي.

```csharp
doc.Save(dataDir + "DocumentFormatting.ApplyBordersAndShadingToParagraph.doc");
```

 يؤدي هذا إلى حفظ مستندنا باسم`DocumentFormatting.ApplyBordersAndShadingToParagraph.doc` في الدليل الذي حددناه سابقًا.

## خاتمة

والآن، لقد انتهينا! فباستخدام بضعة أسطر من التعليمات البرمجية، قمنا بتحويل فقرة عادية إلى محتوى جذاب بصريًا. يجعل Aspose.Words for .NET من السهل للغاية إضافة تنسيق احترافي إلى مستنداتك. سواء كنت تقوم بإعداد تقرير أو خطاب أو أي مستند، فإن هذه الحيل ستساعدك على ترك انطباع رائع. لذا، انطلق وجربها وشاهد مستنداتك تنبض بالحياة!

## الأسئلة الشائعة

### هل يمكنني استخدام أنماط خطوط مختلفة لكل حدود؟  
 بالتأكيد! يتيح لك Aspose.Words for .NET تخصيص كل حد على حدة. ما عليك سوى تعيين`LineStyle` لكل نوع حدود كما هو موضح في الدليل.

### ما هي القوام التظليلية الأخرى المتوفرة؟  
 هناك العديد من القوام التي يمكنك استخدامها، مثل القوام الصلب والخطوط الأفقية والخطوط الرأسية والمزيد. تحقق من[توثيق Aspose](https://reference.aspose.com/words/net/) للحصول على القائمة الكاملة.

### كيف يمكنني تغيير لون الحدود؟  
 يمكنك ضبط لون الحدود باستخدام`Color` خاصية لكل حدود. على سبيل المثال،`borders[BorderType.Left].Color = Color.Red;`.

### هل من الممكن تطبيق الحدود والتظليل على جزء معين من النص؟  
 نعم، يمكنك تطبيق الحدود والتظليل على نصوص محددة باستخدام`Run` كائن داخل`DocumentBuilder`.

### هل يمكنني أتمتة هذه العملية لعدة فقرات؟  
بالتأكيد! يمكنك التنقل بين فقراتك وتطبيق نفس الحدود وإعدادات التظليل برمجيًا.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
