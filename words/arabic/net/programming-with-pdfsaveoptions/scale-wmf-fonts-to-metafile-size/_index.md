---
"description": "دليل خطوة بخطوة لتقليل حجم ملف pdf باستخدام مقياس خطوط wmf لحجم الملف التعريفي عند التحويل إلى PDF باستخدام Aspose.Words لـ .NET."
"linktitle": "تقليل حجم ملف PDF باستخدام مقياس خطوط WMF إلى حجم الملف التعريفي"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "تقليل حجم ملف PDF باستخدام مقياس خطوط WMF إلى حجم الملف التعريفي"
"url": "/ar/net/programming-with-pdfsaveoptions/scale-wmf-fonts-to-metafile-size/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تقليل حجم ملف PDF باستخدام مقياس خطوط WMF إلى حجم الملف التعريفي

## مقدمة

عند العمل مع ملفات PDF، وخاصةً تلك المُولَّدة من مستندات Word التي تحتوي على رسومات WMF (ملف تعريف Windows)، تُصبح إدارة الحجم جانبًا أساسيًا في معالجة المستندات. إحدى طرق التحكم في حجم ملف PDF هي ضبط طريقة عرض خطوط WMF داخل المستند. في هذا البرنامج التعليمي، سنستكشف كيفية تقليل حجم ملف PDF عن طريق ضبط حجم خطوط WMF بما يتناسب مع حجم ملف التعريف باستخدام Aspose.Words لـ .NET.

## المتطلبات الأساسية

قبل البدء في الخطوات، تأكد من أن لديك ما يلي:

1. Aspose.Words لـ .NET: تأكد من تثبيت مكتبة Aspose.Words. إذا لم تكن مثبتة، يمكنك [قم بتحميله هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: يفترض هذا البرنامج التعليمي أن لديك بيئة تطوير .NET مهيأة (مثل Visual Studio) حيث يمكنك كتابة وتنفيذ كود C#.
3. الفهم الأساسي لبرمجة .NET: ستكون المعرفة بمفاهيم برمجة .NET الأساسية وقواعد لغة C# مفيدة.
4. مستند وورد يحتوي على رسومات WMF: ستحتاج إلى مستند وورد يحتوي على رسومات WMF. يمكنك استخدام مستندك الخاص أو إنشاء مستند للاختبار.

## استيراد مساحات الأسماء

أولاً، عليك استيراد مساحات الأسماء اللازمة في مشروع C# الخاص بك. سيُتيح لك هذا الوصول إلى الفئات والأساليب اللازمة للعمل مع Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## الخطوة 1: تحميل مستند Word

للبدء، حمّل مستند Word الذي يحتوي على رسومات WMF. يتم ذلك باستخدام `Document` فئة من Aspose.Words.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// تحميل المستند
Document doc = new Document(dataDir + "WMF with text.docx");
```

هنا، `dataDir` هو عنصر نائب لمسار دليل المستند. نقوم بإنشاء مثيل لـ `Document` بتمرير المسار إلى ملف Word. يؤدي هذا إلى تحميل المستند إلى الذاكرة، جاهزًا للمعالجة الإضافية.

## الخطوة 2: تكوين خيارات عرض الملف التعريفي

بعد ذلك، عليك تكوين خيارات عرض ملف التعريف. على وجه التحديد، اضبط `ScaleWmfFontsToMetafileSize` الممتلكات إلى `false`يتحكم هذا فيما إذا كانت خطوط WMF يتم قياسها لتتناسب مع حجم الملف التعريفي.

```csharp
// إنشاء مثيل جديد لـ MetafileRenderingOptions
MetafileRenderingOptions metafileRenderingOptions = new MetafileRenderingOptions
{
    ScaleWmfFontsToMetafileSize = false
};
```

ال `MetafileRenderingOptions` توفر الفئة خيارات لعرض ملفات التعريف (مثل WMF). من خلال ضبط `ScaleWmfFontsToMetafileSize` ل `false`، فأنت تطلب من Aspose.Words عدم تغيير حجم الخطوط وفقًا لحجم الملف التعريفي، مما قد يساعد في تقليل الحجم الإجمالي لملف PDF.

## الخطوة 3: تعيين خيارات حفظ PDF

الآن، قم بتكوين خيارات حفظ PDF لاستخدام خيارات عرض الملفات التعريفية التي حددتها. هذا يُعلم Aspose.Words كيفية التعامل مع الملفات التعريفية عند حفظ المستند بتنسيق PDF.

```csharp
// إنشاء مثيل جديد لـ PdfSaveOptions
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    MetafileRenderingOptions = metafileRenderingOptions
};
```

ال `PdfSaveOptions` تتيح لك الفئة تحديد إعدادات مختلفة لحفظ المستند بتنسيق PDF. بتعيين الإعدادات المُهيأة مسبقًا `MetafileRenderingOptions` الى `MetafileRenderingOptions` ممتلكات `PdfSaveOptions`، تأكد من حفظ المستند وفقًا لإعدادات عرض الملف التعريفي المطلوبة.

## الخطوة 4: حفظ المستند بتنسيق PDF

أخيرًا، احفظ مستند Word كملف PDF باستخدام خيارات الحفظ المُعدّة. سيؤدي هذا إلى تطبيق جميع الإعدادات، بما في ذلك خيارات عرض الملف التعريفي، على ملف PDF الناتج.


```csharp
// حفظ المستند بصيغة PDF
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ScaleWmfFontsToMetafileSize.pdf", saveOptions);
```

في هذه الخطوة، `Save` طريقة `Document` تُستخدم الفئة لتصدير المستند إلى ملف PDF. يُحدَّد مسار حفظ ملف PDF، بالإضافة إلى `PdfSaveOptions` التي تتضمن إعدادات عرض الملف التعريفي.

## خاتمة

من خلال تغيير حجم خطوط WMF إلى حجم ملف التعريف، يمكنك تقليل حجم ملفات PDF المُولّدة من مستندات Word بشكل ملحوظ. تُساعد هذه التقنية على تحسين تخزين وتوزيع المستندات دون المساس بجودة المحتوى المرئي. يضمن اتباع الخطوات الموضحة أعلاه أن تكون ملفات PDF الخاصة بك أكثر سهولة في الإدارة وكفاءة في الحجم.

## الأسئلة الشائعة

### ما هو WMF ولماذا هو مهم لحجم PDF؟

WMF (ملف تعريف ويندوز) هو تنسيق رسومي يُستخدم في مايكروسوفت ويندوز. يحتوي على بيانات متجهة وبيانات نقطية. ولأن بيانات المتجهات قابلة للتغيير والتعديل، فمن المهم التعامل معها بشكل صحيح لتجنب ملفات PDF كبيرة الحجم.

### كيف يؤثر تغيير حجم خطوط WMF إلى حجم الملف التعريفي على ملف PDF؟

قد يساعد تغيير حجم خطوط WMF إلى حجم الملف التعريفي في تقليل الحجم الإجمالي لملف PDF من خلال تجنب عرض الخطوط عالية الدقة التي قد تؤدي إلى زيادة حجم الملف.

### هل يمكنني استخدام تنسيقات ملفات تعريف أخرى مع Aspose.Words؟

نعم، يدعم Aspose.Words تنسيقات الملفات التعريفية المختلفة، بما في ذلك EMF (ملف التعريف التعريفي المحسن) بالإضافة إلى WMF.

### هل هذه التقنية قابلة للتطبيق على جميع أنواع مستندات Word؟

نعم، يمكن تطبيق هذه التقنية على أي مستند Word يحتوي على رسومات WMF، مما يساعد في تحسين حجم ملف PDF الناتج.

### أين يمكنني العثور على مزيد من المعلومات حول Aspose.Words؟

يمكنك استكشاف المزيد حول Aspose.Words في [توثيق Aspose.Words](https://reference.aspose.com/words/net/)للتنزيلات والتجارب والدعم، تفضل بزيارة [صفحة تحميل Aspose.Words](https://releases.aspose.com/words/net/)، [شراء Aspose.Words](https://purchase.aspose.com/buy)، [نسخة تجريبية مجانية](https://releases.aspose.com/)، [رخصة مؤقتة](https://purchase.aspose.com/temporary-license/)، و [يدعم](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}