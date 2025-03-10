---
title: تعيين علامة التأكيد على الخط
linktitle: تعيين علامة التأكيد على الخط
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية تعيين علامات التأكيد على الخطوط في مستندات Word باستخدام Aspose.Words for .NET من خلال هذا الدليل المفصل خطوة بخطوة. مثالي لمطوري .NET.
weight: 10
url: /ar/net/working-with-fonts/set-font-emphasis-mark/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تعيين علامة التأكيد على الخط

## مقدمة

في درس اليوم، سنتعرف على كيفية تعيين علامات التأكيد على الخطوط في مستند Word باستخدام Aspose.Words for .NET. سواء كنت تبحث عن تسطير نص معين بعلامة فريدة أو ببساطة إبراز كلمات معينة، فهذا الدليل سيوفر لك ما تحتاجه. لذا، استعد ولنبدأ!

## المتطلبات الأساسية

قبل أن نتعمق في التفاصيل الدقيقة، تأكد من أنك قد استوفيت المتطلبات الأساسية التالية:

-  مكتبة Aspose.Words for .NET: تأكد من تثبيت مكتبة Aspose.Words for .NET. يمكنك تنزيلها من[هنا](https://releases.aspose.com/words/net/).
- بيئة التطوير: بيئة تطوير عاملة مثل Visual Studio.
- .NET Framework: تأكد من تثبيت .NET Framework.

## استيراد مساحات الأسماء

للعمل مع Aspose.Words لـ .NET، ستحتاج إلى استيراد المساحات الأساسية اللازمة. أضف هذه المساحات في أعلى ملف التعليمات البرمجية الخاص بك:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

الآن، دعنا نقسم العملية إلى خطوات بسيطة. اتبع كل خطوة بعناية لتعيين علامات التأكيد على الخط في مستند Word الخاص بك.

## الخطوة 1: تهيئة المستند وDocumentBuilder

أولاً وقبل كل شيء، تحتاج إلى تهيئة مستند جديد وDocumentBuilder. توفر فئة DocumentBuilder طرقًا لإدراج النص والعناصر الأخرى في المستند.

```csharp
// المسار إلى دليل المستند الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";

// تهيئة مستند جديد
Document document = new Document();

// قم بتهيئة DocumentBuilder باستخدام المستند
DocumentBuilder builder = new DocumentBuilder(document);
```

## الخطوة 2: تعيين علامة التأكيد على الخط

بعد أن أصبح DocumentBuilder جاهزًا، يمكنك الآن تعيين علامة التأكيد على الخط. في هذا المثال، سنستخدم علامة التأكيد "UnderSolidCircle".

```csharp
// تعيين علامة التأكيد على الخط
builder.Font.EmphasisMark = EmphasisMark.UnderSolidCircle;

// اكتب النص مع علامة التأكيد
builder.Write("Emphasis text");
builder.Writeln();
```

## الخطوة 3: مسح التنسيق وإضافة نص عادي

بعد ضبط علامة التأكيد، قد ترغب في إضافة نص عادي بدون أي تأكيد. للقيام بذلك، تحتاج إلى مسح التنسيق.

```csharp
// مسح تنسيق الخط
builder.Font.ClearFormatting();

// اكتب نصًا عاديًا
builder.Write("Simple text");
```

## الخطوة 4: حفظ المستند

بمجرد إضافة كل النص والتنسيق المطلوب، تكون الخطوة الأخيرة هي حفظ المستند. حدد المسار واسم الملف الذي تريد حفظ المستند فيه.

```csharp
// حفظ المستند
document.Save(dataDir + "WorkingWithFonts.SetFontEmphasisMark.docx");
```

## خاتمة

والآن، لقد انتهيت! إن ضبط علامات التأكيد على الخط في مستند Word باستخدام Aspose.Words for .NET أمر بسيط للغاية. فباستخدام بضعة أسطر فقط من التعليمات البرمجية، يمكنك إبراز النص وإضافة لمسة احترافية إلى مستنداتك. لا تتردد في تجربة علامات التأكيد والأنماط المختلفة لتناسب احتياجاتك.

## الأسئلة الشائعة

### ما هي علامات التأكيد للخط؟

علامات التأكيد على الخط عبارة عن رموز خاصة تُضاف إلى النص لتمييزه. ويمكن أن تتضمن نقاطًا ودوائر وعلامات زخرفية أخرى.

### هل يمكنني استخدام علامات التأكيد الأخرى مع Aspose.Words لـ .NET؟

 نعم، يدعم Aspose.Words for .NET علامات التأكيد المختلفة. يمكنك استكشاف خيارات مختلفة من خلال الرجوع إلى[التوثيق](https://reference.aspose.com/words/net/).

### هل استخدام Aspose.Words لـ .NET مجاني؟

 يتطلب Aspose.Words for .NET ترخيصًا للاستفادة من الوظائف الكاملة. يمكنك الحصول على نسخة تجريبية مجانية[هنا](https://releases.aspose.com/) أو شراء ترخيص[هنا](https://purchase.aspose.com/buy).

### كيف يمكنني الحصول على الدعم لـ Aspose.Words لـ .NET؟

 يمكنك الحصول على الدعم من مجتمع Aspose وفريق الدعم من خلال زيارة موقعهم[منتدى الدعم](https://forum.aspose.com/c/words/8).

### هل يمكنني استخدام Aspose.Words لـ .NET مع أطر عمل .NET الأخرى؟

نعم، Aspose.Words for .NET متوافق مع مختلف أطر عمل .NET، بما في ذلك .NET Core و.NET 5/6.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
