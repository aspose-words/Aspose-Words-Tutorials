---
"description": "تعرّف على كيفية ضبط علامات توكيد الخطوط في مستندات Word باستخدام Aspose.Words لـ .NET من خلال هذا الدليل المفصل خطوة بخطوة. مثالي لمطوري .NET."
"linktitle": "تعيين علامة التأكيد على الخط"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "تعيين علامة التأكيد على الخط"
"url": "/ar/net/working-with-fonts/set-font-emphasis-mark/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تعيين علامة التأكيد على الخط

## مقدمة

في درس اليوم، سنتعمق في كيفية ضبط علامات توكيد الخط في مستند Word باستخدام Aspose.Words لـ .NET. سواء كنت ترغب في تسطير نص معين بعلامة مميزة أو ببساطة إبراز كلمات معينة، فهذا الدليل سيلبي احتياجاتك. لذا، استعد ولنبدأ!

## المتطلبات الأساسية

قبل أن نتعمق في التفاصيل الدقيقة، تأكد من أنك قد استوفيت المتطلبات الأساسية التالية:

- مكتبة Aspose.Words لـ .NET: تأكد من تثبيت مكتبة Aspose.Words لـ .NET. يمكنك تنزيلها من [هنا](https://releases.aspose.com/words/net/).
- بيئة التطوير: بيئة تطوير عاملة مثل Visual Studio.
- .NET Framework: تأكد من تثبيت .NET Framework.

## استيراد مساحات الأسماء

للعمل مع Aspose.Words لـ .NET، ستحتاج إلى استيراد مساحات الأسماء اللازمة. أضف هذه في أعلى ملف الكود الخاص بك:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

الآن، لنُقسّم العملية إلى خطوات بسيطة. اتبع كل خطوة بعناية لضبط علامات توكيد الخط في مستند Word.

## الخطوة 1: تهيئة المستند وDocumentBuilder

أولاً، عليك تهيئة مستند جديد و"منشئ المستندات". يوفر هذا النوع من المنشئ طرقاً لإدراج نص وعناصر أخرى في المستند.

```csharp
// المسار إلى دليل المستندات الخاص بك 
string dataDir = "YOUR DOCUMENT DIRECTORY";

// تهيئة مستند جديد
Document document = new Document();

// تهيئة DocumentBuilder باستخدام المستند
DocumentBuilder builder = new DocumentBuilder(document);
```

## الخطوة 2: تعيين علامة التأكيد على الخط

بعد تجهيز DocumentBuilder، يمكنك الآن ضبط علامة التشديد على الخط. في هذا المثال، سنستخدم علامة التشديد "UnderSolidCircle".

```csharp
// تعيين علامة التأكيد على الخط
builder.Font.EmphasisMark = EmphasisMark.UnderSolidCircle;

// اكتب النص مع علامة التأكيد
builder.Write("Emphasis text");
builder.Writeln();
```

## الخطوة 3: مسح التنسيق وإضافة نص عادي

بعد ضبط علامة التشديد، قد ترغب بإضافة نص عادي بدون أي تشديد. لذلك، عليك مسح التنسيق.

```csharp
// مسح تنسيق الخط
builder.Font.ClearFormatting();

// كتابة نص عادي
builder.Write("Simple text");
```

## الخطوة 4: حفظ المستند

بعد إضافة النص والتنسيق المطلوب، تأتي الخطوة الأخيرة وهي حفظ المستند. حدد المسار واسم الملف الذي تريد حفظ المستند فيه.

```csharp
// حفظ المستند
document.Save(dataDir + "WorkingWithFonts.SetFontEmphasisMark.docx");
```

## خاتمة

وهذا كل ما في الأمر! ضبط علامات توكيد الخط في مستند وورد باستخدام Aspose.Words لـ .NET سهل للغاية. ببضعة أسطر فقط من التعليمات البرمجية، يمكنك إبراز نصك وإضافة لمسة احترافية إلى مستنداتك. لا تتردد في تجربة علامات وأنماط توكيد مختلفة تناسب احتياجاتك.

## الأسئلة الشائعة

### ما هي علامات التأكيد للخط؟

علامات تمييز الخط هي رموز خاصة تُضاف إلى النص لإبرازه. يمكن أن تشمل نقاطًا ودوائر وعلامات زخرفية أخرى.

### هل يمكنني استخدام علامات التأكيد الأخرى مع Aspose.Words لـ .NET؟

نعم، يدعم Aspose.Words لـ .NET علامات توكيد متنوعة. يمكنك استكشاف خيارات مختلفة بالرجوع إلى [التوثيق](https://reference.aspose.com/words/net/).

### هل استخدام Aspose.Words for .NET مجاني؟

يتطلب Aspose.Words for .NET ترخيصًا للاستفادة الكاملة من جميع وظائفه. يمكنك الحصول على نسخة تجريبية مجانية. [هنا](https://releases.aspose.com/) أو شراء ترخيص [هنا](https://purchase.aspose.com/buy).

### كيف يمكنني الحصول على الدعم لـ Aspose.Words لـ .NET؟

يمكنك الحصول على الدعم من مجتمع Aspose وفريق الدعم من خلال زيارة موقعهم [منتدى الدعم](https://forum.aspose.com/c/words/8).

### هل يمكنني استخدام Aspose.Words لـ .NET مع أطر عمل .NET الأخرى؟

نعم، Aspose.Words for .NET متوافق مع مختلف أطر عمل .NET، بما في ذلك .NET Core و.NET 5/6.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}