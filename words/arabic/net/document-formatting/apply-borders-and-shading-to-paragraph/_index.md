---
"description": "أضف حدودًا وتظليلًا إلى فقرات مستندات Word باستخدام Aspose.Words لـ .NET. اتبع دليلنا خطوة بخطوة لتحسين تنسيق مستندك."
"linktitle": "تطبيق الحدود والتظليل على الفقرة في مستند Word"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "تطبيق الحدود والتظليل على الفقرة في مستند Word"
"url": "/ar/net/document-formatting/apply-borders-and-shading-to-paragraph/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تطبيق الحدود والتظليل على الفقرة في مستند Word

## مقدمة

هل تساءلت يومًا كيف تجعل مستندات Word الخاصة بك مميزة بإطارات وتظليلات أنيقة؟ أنت في المكان الصحيح! اليوم، نغوص في عالم Aspose.Words لـ .NET لإضفاء لمسة جمالية على فقراتك. تخيل أن مستندك يبدو أنيقًا كعمل مصمم محترف ببضعة أسطر فقط من التعليمات البرمجية. هل أنت مستعد؟ هيا بنا!

## المتطلبات الأساسية

قبل أن نبدأ بالبرمجة، دعونا نتأكد من توفر كل ما نحتاجه. إليك قائمة مرجعية سريعة:

- Aspose.Words لـ .NET: يجب تثبيت هذه المكتبة. يمكنك تنزيلها من [موقع Aspose](https://releases.aspose.com/words/net/).
- بيئة التطوير: Visual Studio أو أي بيئة تطوير متكاملة أخرى تدعم .NET.
- المعرفة الأساسية بلغة C#: ما يكفي لفهم وتعديل أجزاء التعليمات البرمجية.
- رخصة صالحة: إما [رخصة مؤقتة](https://purchase.aspose.com/temporary-license/) أو تم شراؤها من [أسبوزي](https://purchase.aspose.com/buy).

## استيراد مساحات الأسماء

قبل البدء في الكود، علينا التأكد من استيراد مساحات الأسماء اللازمة إلى مشروعنا. هذا يُمكّننا من الوصول إلى جميع ميزات Aspose.Words الرائعة.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using Aspose.Words.Drawing;
using System.Drawing;
```

الآن، لنُقسّم العملية إلى خطوات مُختصرة. لكل خطوة عنوان وشرح مُفصّل. هل أنتَ مُستعد؟ هيا بنا!

## الخطوة 1: إعداد دليل المستندات الخاص بك

أولاً، نحتاج إلى مكان لحفظ مستندنا بتنسيق جميل. لنحدد مسار مجلد المستند.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

هذا الدليل هو المكان الذي سيتم فيه حفظ مستندك النهائي. استبدل `"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي على جهازك.

## الخطوة 2: إنشاء مستند جديد وDocumentBuilder

بعد ذلك، نحتاج إلى إنشاء مستند جديد و `DocumentBuilder` الكائن. `DocumentBuilder` إنها عصانا السحرية التي تمكننا من التحكم في المستند.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

ال `Document` يمثل الكائن مستند Word بأكمله، و `DocumentBuilder` يساعدنا على إضافة المحتوى وتنسيقه.

## الخطوة 3: تحديد حدود الفقرة

الآن، لنُضيف حدودًا أنيقة لفقرتنا. سنُحدد المسافة بين النص والفقرة ونُعيّن أنماطًا مُختلفة للحدود.

```csharp
BorderCollection borders = builder.ParagraphFormat.Borders;
borders.DistanceFromText = 20;
borders[BorderType.Left].LineStyle = LineStyle.Double;
borders[BorderType.Right].LineStyle = LineStyle.Double;
borders[BorderType.Top].LineStyle = LineStyle.Double;
borders[BorderType.Bottom].LineStyle = LineStyle.Double;
```

هنا، حددنا مسافة ٢٠ نقطة بين النص والحدود. الحدود على جميع الجوانب (يسار، يمين، أعلى، أسفل) مُصممة على شكل خطين. رائع، أليس كذلك؟

## الخطوة 4: تطبيق التظليل على الفقرة

الحدود رائعة، ولكن لنرفع مستوى التظليل. سنستخدم نمطًا قطريًا متقاطعًا مع مزيج من الألوان لإبراز فقرتنا.

```csharp
Shading shading = builder.ParagraphFormat.Shading;
shading.Texture = TextureIndex.TextureDiagonalCross;
shading.BackgroundPatternColor = System.Drawing.Color.LightCoral;
shading.ForegroundPatternColor = System.Drawing.Color.LightSalmon;
```

في هذه الخطوة، طبقنا نسيجًا متقاطعًا قطريًا، مع استخدام اللون المرجاني الفاتح كلون خلفية، واللون السلموني الفاتح كلون مقدمة. الأمر أشبه بتلبيس فقرتك بأزياء مصممة خصيصًا!

## الخطوة 5: إضافة نص إلى الفقرة

ما فائدة الفقرة بدون نص؟ لنُضِف جملةً نموذجيةً لنرى تنسيقنا عمليًا.

```csharp
builder.Write("I'm a formatted paragraph with double border and nice shading.");
```

يُدرج هذا السطر نصنا في المستند. بسيط، ولكنه الآن مُحاط بإطار أنيق وخلفية مُظللة.

## الخطوة 6: حفظ المستند

أخيرًا، حان وقت حفظ عملنا. لنحفظ المستند في المجلد المحدد باسم وصفي.

```csharp
doc.Save(dataDir + "DocumentFormatting.ApplyBordersAndShadingToParagraph.doc");
```

يؤدي هذا إلى حفظ مستندنا باسم `DocumentFormatting.ApplyBordersAndShadingToParagraph.doc` في الدليل الذي حددناه سابقًا.

## خاتمة

وها قد انتهينا! ببضعة أسطر من التعليمات البرمجية، حوّلنا فقرة عادية إلى محتوى جذاب بصريًا. يُسهّل Aspose.Words for .NET إضافة تنسيق احترافي إلى مستنداتك بشكل كبير. سواء كنت تُعدّ تقريرًا أو رسالة أو أي مستند، ستساعدك هذه الحيل على ترك انطباع رائع. جرّبها الآن، وشاهد مستنداتك تنبض بالحياة!

## الأسئلة الشائعة

### هل يمكنني استخدام أنماط خطوط مختلفة لكل حدود؟  
بالتأكيد! يتيح لك Aspose.Words لـ .NET تخصيص كل إطار على حدة. ما عليك سوى ضبط `LineStyle` لكل نوع حدود كما هو موضح في الدليل.

### ما هي القوام التظليلية الأخرى المتوفرة؟  
هناك العديد من القوام التي يمكنك استخدامها، مثل القوام المصمت، والخطوط الأفقية، والخطوط العمودية، وغيرها. تحقق من [وثائق Aspose](https://reference.aspose.com/words/net/) للحصول على القائمة الكاملة.

### كيف يمكنني تغيير لون الحدود؟  
يمكنك ضبط لون الحدود باستخدام `Color` خاصية لكل حد. على سبيل المثال، `borders[BorderType.Left].Color = Color.Red;`.

### هل من الممكن تطبيق الحدود والتظليل على جزء معين من النص؟  
نعم، يمكنك تطبيق الحدود والتظليل على نصوص محددة باستخدام `Run` كائن داخل `DocumentBuilder`.

### هل يمكنني أتمتة هذه العملية لعدة فقرات؟  
بالتأكيد! يمكنك التنقل بين فقراتك وتطبيق نفس إعدادات الحدود والتظليل برمجيًا.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}