---
"description": "تعرّف على كيفية ضبط اتجاه النص في مستند Word باستخدام Aspose.Words لـ .NET من خلال هذا الدليل المفصل. مثالي للتعامل مع اللغات التي تُكتب من اليمين إلى اليسار."
"linktitle": "اتجاه نص المستند"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "اتجاه نص المستند"
"url": "/ar/net/programming-with-txtloadoptions/document-text-direction/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# اتجاه نص المستند

## مقدمة

عند العمل مع مستندات Word، وخاصةً تلك التي تحتوي على لغات متعددة أو تتطلب تنسيقًا خاصًا، يُعدّ ضبط اتجاه النص أمرًا بالغ الأهمية. على سبيل المثال، عند التعامل مع لغات من اليمين إلى اليسار، مثل العبرية أو العربية، قد تحتاج إلى ضبط اتجاه النص وفقًا لذلك. في هذا الدليل، سنشرح كيفية ضبط اتجاه النص في المستند باستخدام Aspose.Words لـ .NET. 

## المتطلبات الأساسية

قبل أن نتعمق في الكود، تأكد من أن لديك ما يلي:

- مكتبة Aspose.Words لـ .NET: تأكد من تثبيت Aspose.Words لـ .NET. يمكنك تنزيلها من [موقع Aspose](https://releases.aspose.com/words/net/).
- Visual Studio: بيئة تطوير لكتابة وتنفيذ كود C#.
- المعرفة الأساسية بلغة C#: ستكون المعرفة ببرمجة C# مفيدة لأننا سنكتب بعض التعليمات البرمجية.

## استيراد مساحات الأسماء

للبدء، ستحتاج إلى استيراد مساحات الأسماء اللازمة للعمل مع Aspose.Words في مشروعك. إليك كيفية القيام بذلك:

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
```

توفر هذه المساحات الأسماء إمكانية الوصول إلى الفئات والطرق اللازمة للتعامل مع مستندات Word.

## الخطوة 1: تحديد المسار إلى دليل المستندات الخاص بك

أولاً، حدّد مسار مستندك. هذا ضروري لتحميل الملفات وحفظها بشكل صحيح.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

يستبدل `"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي الذي يتم تخزين مستندك فيه.

## الخطوة 2: إنشاء TxtLoadOptions مع إعداد اتجاه المستند

بعد ذلك، ستحتاج إلى إنشاء مثيل لـ `TxtLoadOptions` ووضعها `DocumentDirection` هذه الخاصية تُعلِّم Aspose.Words كيفية التعامل مع اتجاه النص في المستند.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DocumentDirection = DocumentDirection.Auto };
```

في هذا المثال، نستخدم `DocumentDirection.Auto` السماح لـ Aspose.Words بتحديد الاتجاه تلقائيًا استنادًا إلى المحتوى.

## الخطوة 3: تحميل المستند

الآن، قم بتحميل المستند باستخدام `Document` الفئة والتعريفات المحددة مسبقًا `loadOptions`.

```csharp
Document doc = new Document(dataDir + "Hebrew text.txt", loadOptions);
```

هنا، `"Hebrew text.txt"` هو اسم ملف النص. تأكد من وجود هذا الملف في الدليل المحدد.

## الخطوة 4: الوصول إلى التنسيق ثنائي الاتجاه للفقرة والتحقق منه

للتأكد من ضبط اتجاه النص بشكل صحيح، انتقل إلى الفقرة الأولى من المستند وتحقق من تنسيقها ثنائي الاتجاه.

```csharp
Paragraph paragraph = doc.FirstSection.Body.FirstParagraph;
Console.WriteLine(paragraph.ParagraphFormat.Bidi);
```

تعتبر هذه الخطوة مفيدة لاستكشاف الأخطاء وإصلاحها والتأكد من تطبيق اتجاه نص المستند كما هو متوقع.

## الخطوة 5: حفظ المستند بالإعدادات الجديدة

وأخيرًا، احفظ المستند لتطبيق التغييرات والاحتفاظ بها.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
```

هنا، `"WorkingWithTxtLoadOptions.DocumentTextDirection.docx"` هو اسم ملف الإخراج. تأكد من اختيار اسم يعكس التغييرات التي أجريتها.

## خاتمة

يُعدّ ضبط اتجاه النص في مستندات Word عمليةً سهلةً مع Aspose.Words لـ .NET. باتباع هذه الخطوات، يمكنك بسهولة ضبط كيفية تعامل مستندك مع النص من اليمين إلى اليسار أو من اليسار إلى اليمين. سواءً كنت تعمل على مستندات متعددة اللغات أو تحتاج إلى تنسيق اتجاه النص للغات محددة، يوفر Aspose.Words حلاًّ فعّالاً يلبي احتياجاتك.

## الأسئلة الشائعة

### ما هو `DocumentDirection` الممتلكات المستخدمة ل؟

ال `DocumentDirection` الممتلكات في `TxtLoadOptions` يحدد اتجاه النص للمستند. يمكن ضبطه على `DocumentDirection.Auto`، `DocumentDirection.LeftToRight`، أو `DocumentDirection.RightToLeft`.

### هل يمكنني تحديد اتجاه النص لفقرات محددة بدلاً من المستند بأكمله؟

نعم، يمكنك تعيين اتجاه النص لفقرات محددة باستخدام `ParagraphFormat.Bidi` الممتلكات، ولكن `TxtLoadOptions.DocumentDirection` تحدد الخاصية الاتجاه الافتراضي للمستند بأكمله.

### ما هي تنسيقات الملفات المدعومة للتحميل باستخدام `TxtLoadOptions`؟

`TxtLoadOptions` يُستخدم بشكل أساسي لتحميل ملفات النصوص (.txt). بالنسبة لتنسيقات الملفات الأخرى، استخدم فئات مختلفة مثل `DocLoadOptions` أو `DocxLoadOptions`.

### كيف يمكنني التعامل مع المستندات ذات الاتجاهات النصية المختلطة؟

بالنسبة للمستندات ذات التوجيهات النصية المختلطة، قد تحتاج إلى معالجة التنسيق لكل فقرة على حدة. استخدم `ParagraphFormat.Bidi` خاصية لضبط اتجاه كل فقرة حسب الحاجة.

### أين يمكنني العثور على مزيد من المعلومات حول Aspose.Words لـ .NET؟

لمزيد من التفاصيل، راجع [توثيق Aspose.Words لـ .NET](https://reference.aspose.com/words/net/)يمكنك أيضًا استكشاف موارد إضافية مثل [رابط التحميل](https://releases.aspose.com/words/net/)، [يشتري](https://purchase.aspose.com/buy)، [نسخة تجريبية مجانية](https://releases.aspose.com/)، [رخصة مؤقتة](https://purchase.aspose.com/temporary-license/)، و [يدعم](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}