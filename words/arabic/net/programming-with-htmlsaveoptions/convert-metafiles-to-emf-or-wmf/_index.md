---
"description": "دليل خطوة بخطوة لتحويل ملفات التعريف إلى تنسيقات EMF أو WMF عند تحويل مستند إلى HTML باستخدام Aspose.Words لـ .NET."
"linktitle": "تحويل ملفات التعريف إلى Emf أو WMF"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "تحويل ملفات التعريف إلى Emf أو WMF"
"url": "/ar/net/programming-with-htmlsaveoptions/convert-metafiles-to-emf-or-wmf/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تحويل ملفات التعريف إلى Emf أو WMF

## مقدمة

أهلاً بكم في رحلة أخرى متعمقة في عالم Aspose.Words لـ .NET. اليوم، سنتناول حيلة رائعة: تحويل صور SVG إلى صيغ EMF أو WMF في مستندات Word. قد يبدو هذا الأمر معقداً بعض الشيء، لكن لا تقلق. بنهاية هذا البرنامج التعليمي، ستصبح محترفاً فيه. سواء كنت مطوراً محترفاً أو بدأت للتو في استخدام Aspose.Words لـ .NET، سيرشدك هذا الدليل إلى كل ما تحتاج لمعرفته خطوة بخطوة.

## المتطلبات الأساسية

قبل أن نتعمق في الكود، لنتأكد من إعداد كل شيء. إليك ما تحتاجه:

1. مكتبة Aspose.Words لـ .NET: تأكد من تثبيت أحدث إصدار. إذا لم يكن لديك، يمكنك تنزيله من [هنا](https://releases.aspose.com/words/net/).
2. .NET Framework: تأكد من تثبيت .NET Framework على جهازك.
3. بيئة التطوير: بيئة التطوير المتكاملة مثل Visual Studio سوف تجعل حياتك أسهل.
4. المعرفة الأساسية بلغة C#: لا تحتاج إلى أن تكون خبيرًا، ولكن الفهم الأساسي سوف يساعدك.

هل فهمت كل شيء؟ رائع! لنبدأ.

## استيراد مساحات الأسماء

أولاً، علينا استيراد مساحات الأسماء اللازمة. هذا أمر بالغ الأهمية لأنه يُحدد لبرنامجنا مكان الفئات والأساليب التي سنستخدمها.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

تغطي هذه المساحات الاسمية كل شيء بدءًا من وظائف النظام الأساسية وحتى وظيفة Aspose.Words المحددة التي نحتاجها لهذا البرنامج التعليمي.

## الخطوة 1: إعداد دليل المستندات الخاص بك

لنبدأ بتحديد مسار مجلد المستندات. هذا هو المكان الذي سيتم فيه حفظ مستند Word بعد تحويل ملفات التعريف.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

يستبدل `"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي الذي تريد حفظ مستندك فيه.

## الخطوة 2: إنشاء سلسلة HTML باستخدام SVG

بعد ذلك، نحتاج إلى سلسلة HTML تحتوي على صورة SVG التي نريد تحويلها. إليك مثال بسيط:

```csharp
string html = 
    @"<html>
        <svg xmlns='http://www.w3.org/2000/svg' العرض='500' الارتفاع='40' viewBox='0 0 500 40'>
            <text x='0' y='35' font-family='Verdana' font-size='35'>Hello world!</text>
        </svg>
    </html>";
```

تتضمن مقتطفات HTML هذه صورة SVG أساسية تقول "مرحباً بالعالم!".

## الخطوة 3: تحميل HTML باستخدام خيار ConvertSvgToEmf

الآن، نستخدم `HtmlLoadOptions` لتحديد كيفية التعامل مع صور SVG في HTML. الإعداد `ConvertSvgToEmf` ل `true` يضمن تحويل صور SVG إلى تنسيق EMF.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions { ConvertSvgToEmf = true };
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

يؤدي مقتطف التعليمات البرمجية هذا إلى إنشاء رمز جديد `Document` الكائن عن طريق تحميل سلسلة HTML فيه باستخدام خيارات التحميل المحددة.

## الخطوة 4: تعيين خيارات حفظ Html لتنسيق الملف التعريفي

لحفظ المستند بتنسيق الملف التعريفي الصحيح، نستخدم `HtmlSaveOptions`. هنا، وضعنا `MetafileFormat` ل `HtmlMetafileFormat.Png`ولكن يمكنك تغيير هذا إلى `Emf` أو `Wmf` اعتمادًا على احتياجاتك.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions { MetafileFormat = HtmlMetafileFormat.Png };
```

## الخطوة 5: حفظ المستند

وأخيرا، نقوم بحفظ المستند باستخدام خيارات الحفظ المحددة.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToPng.html", saveOptions);
```

يؤدي هذا إلى حفظ المستند في الدليل المحدد بتنسيق الملف التعريفي المحول كما هو محدد.

## خاتمة

وهذا كل ما في الأمر! باتباع هذه الخطوات، تكون قد نجحت في تحويل صور SVG إلى صيغ EMF أو WMF في مستندات Word باستخدام Aspose.Words for .NET. هذه الطريقة مفيدة لضمان التوافق والحفاظ على سلامة مستنداتك البصرية عبر مختلف المنصات. برمجة ممتعة!

## الأسئلة الشائعة

### هل يمكنني تحويل صيغ الصور الأخرى باستخدام هذه الطريقة؟
نعم، يمكنك تحويل تنسيقات الصور المختلفة عن طريق ضبط خيارات التحميل والحفظ وفقًا لذلك.

### هل من الضروري استخدام إصدار محدد من .NET Framework؟
يدعم Aspose.Words for .NET إصدارات متعددة من .NET Framework، ولكن من الأفضل دائمًا استخدام الإصدار الأحدث للحصول على أفضل توافق وميزات.

### ما هي ميزة تحويل SVG إلى EMF أو WMF؟
يضمن تحويل SVG إلى EMF أو WMF الحفاظ على الرسومات المتجهة وتقديمها بشكل صحيح في البيئات التي قد لا تدعم SVG بشكل كامل.

### هل يمكنني أتمتة هذه العملية لمستندات متعددة؟
بالتأكيد! يمكنك تكرار عملية التحويل بين ملفات HTML متعددة، وتطبيق نفس العملية لأتمتة عملية التحويل للمعالجة الدفعية.

### أين يمكنني العثور على المزيد من الموارد والدعم لـ Aspose.Words لـ .NET؟
يمكنك العثور على وثائق شاملة [هنا](https://reference.aspose.com/words/net/) واحصل على الدعم من مجتمع Aspose [هنا](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}