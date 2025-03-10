---
title: تقليل حجم ملف PDF باستخدام Scale WMF Fonts To Metafile Size
linktitle: تقليل حجم ملف PDF باستخدام Scale WMF Fonts To Metafile Size
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: دليل خطوة بخطوة لتقليل حجم ملف pdf باستخدام خطوط wmf المقياس إلى حجم الملف التعريفي عند التحويل إلى PDF باستخدام Aspose.Words لـ .NET.
weight: 10
url: /ar/net/programming-with-pdfsaveoptions/scale-wmf-fonts-to-metafile-size/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تقليل حجم ملف PDF باستخدام Scale WMF Fonts To Metafile Size

## مقدمة

عند العمل بملفات PDF، وخاصة تلك التي تم إنشاؤها من مستندات Word التي تحتوي على رسومات WMF (ملف تعريف Windows)، يمكن أن تصبح إدارة الحجم جانبًا بالغ الأهمية في التعامل مع المستندات. إحدى الطرق للتحكم في حجم PDF هي ضبط كيفية عرض خطوط WMF داخل المستند. في هذا البرنامج التعليمي، سنستكشف كيفية تقليل حجم PDF عن طريق تغيير حجم خطوط WMF إلى حجم الملف التعريفي باستخدام Aspose.Words for .NET.

## المتطلبات الأساسية

قبل البدء في الخطوات، تأكد من توفر ما يلي:

1. Aspose.Words لـ .NET: تأكد من تثبيت مكتبة Aspose.Words. إذا لم يكن الأمر كذلك، فيمكنك[تحميله هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: يفترض هذا البرنامج التعليمي أن لديك بيئة تطوير .NET مهيأة (مثل Visual Studio) حيث يمكنك كتابة وتنفيذ كود C#.
3. الفهم الأساسي لبرمجة .NET: سيكون من المفيد التعرف على مفاهيم برمجة .NET الأساسية وقواعد لغة C#.
4. مستند Word يحتوي على رسومات WMF: ستحتاج إلى مستند Word يحتوي على رسومات WMF. يمكنك استخدام مستندك الخاص أو إنشاء مستند للاختبار.

## استيراد مساحات الأسماء

أولاً، تحتاج إلى استيراد مساحات الأسماء الضرورية في مشروع C# الخاص بك. سيمنحك هذا إمكانية الوصول إلى الفئات والطرق المطلوبة للعمل مع Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## الخطوة 1: تحميل مستند Word

 للبدء، قم بتحميل مستند Word الذي يحتوي على رسومات WMF. يتم ذلك باستخدام`Document` فئة من Aspose.Words.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// تحميل المستند
Document doc = new Document(dataDir + "WMF with text.docx");
```

 هنا،`dataDir` هو عنصر نائب لمسار دليل المستند الخاص بك. نقوم بإنشاء مثيل لـ`Document` يتم تحميل المستند إلى الذاكرة، جاهزًا للمعالجة الإضافية.

## الخطوة 2: تكوين خيارات عرض الملف التعريفي

 بعد ذلك، تحتاج إلى تكوين خيارات عرض الملف التعريفي. على وجه التحديد، قم بتعيين`ScaleWmfFontsToMetafileSize`الممتلكات ل`false`يتحكم هذا فيما إذا كانت خطوط WMF يتم قياسها لتتناسب مع حجم الملف التعريفي.

```csharp
// إنشاء مثيل جديد لـ MetafileRenderingOptions
MetafileRenderingOptions metafileRenderingOptions = new MetafileRenderingOptions
{
    ScaleWmfFontsToMetafileSize = false
};
```

 ال`MetafileRenderingOptions` توفر الفئة خيارات لكيفية عرض الملفات التعريفية (مثل WMF). من خلال ضبط`ScaleWmfFontsToMetafileSize` ل`false`، فأنت تطلب من Aspose.Words عدم تغيير حجم الخطوط وفقًا لحجم الملف التعريفي، وهو ما قد يساعد في تقليل الحجم الإجمالي لملف PDF.

## الخطوة 3: تعيين خيارات حفظ PDF

الآن، قم بتكوين خيارات حفظ PDF لاستخدام خيارات عرض الملفات التعريفية التي قمت بتعيينها للتو. هذا يخبر Aspose.Words بكيفية التعامل مع الملفات التعريفية عند حفظ المستند بتنسيق PDF.

```csharp
// إنشاء مثيل جديد لـ PdfSaveOptions
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    MetafileRenderingOptions = metafileRenderingOptions
};
```

 ال`PdfSaveOptions` تتيح لك الفئة تحديد إعدادات مختلفة لحفظ المستند بتنسيق PDF. من خلال تعيين الإعدادات التي تم تكوينها مسبقًا`MetafileRenderingOptions` الى`MetafileRenderingOptions` ممتلكات`PdfSaveOptions`، تأكد من حفظ المستند وفقًا لإعدادات عرض الملف التعريفي المطلوبة.

## الخطوة 4: حفظ المستند بصيغة PDF

أخيرًا، احفظ مستند Word بتنسيق PDF باستخدام خيارات الحفظ المهيئة. سيؤدي هذا إلى تطبيق جميع الإعدادات، بما في ذلك خيارات عرض الملف التعريفي، على ملف PDF الناتج.


```csharp
// حفظ المستند بصيغة PDF
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ScaleWmfFontsToMetafileSize.pdf", saveOptions);
```

 في هذه الخطوة،`Save` طريقة`Document` يتم استخدام الفئة لتصدير المستند إلى ملف PDF. يتم تحديد المسار الذي سيتم حفظ ملف PDF فيه، بالإضافة إلى`PdfSaveOptions` التي تتضمن إعدادات عرض الملف التعريفي.

## خاتمة

من خلال تغيير حجم خطوط WMF إلى حجم ملف التعريف، يمكنك تقليل حجم ملفات PDF التي تم إنشاؤها من مستندات Word بشكل كبير. تساعد هذه التقنية في تحسين تخزين المستندات وتوزيعها دون المساس بجودة المحتوى المرئي. يضمن اتباع الخطوات الموضحة أعلاه أن ملفات PDF الخاصة بك أكثر قابلية للإدارة وكفاءة من حيث الحجم.

## الأسئلة الشائعة

### ما هو WMF ولماذا هو مهم لحجم PDF؟

WMF (ملف تعريف Windows Metafile) هو تنسيق رسومي يستخدم في Microsoft Windows. ويمكنه أن يحتوي على بيانات متجهية وبيانات نقطية. ونظرًا لأن بيانات المتجهات يمكن قياسها ومعالجتها، فمن المهم التعامل معها بشكل صحيح لتجنب ملفات PDF كبيرة الحجم بشكل غير ضروري.

### كيف يؤثر تغيير حجم خطوط WMF إلى حجم الملف التعريفي على ملف PDF؟

قد يساعد تغيير حجم خطوط WMF إلى حجم الملف التعريفي في تقليل الحجم الإجمالي لملف PDF من خلال تجنب عرض الخطوط عالية الدقة التي قد تؤدي إلى زيادة حجم الملف.

### هل يمكنني استخدام تنسيقات ملفات تعريف أخرى مع Aspose.Words؟

نعم، يدعم Aspose.Words تنسيقات الملفات التعريفية المختلفة، بما في ذلك EMF (الملف التعريفي المحسن) بالإضافة إلى WMF.

### هل هذه التقنية قابلة للتطبيق على جميع أنواع مستندات Word؟

نعم، يمكن تطبيق هذه التقنية على أي مستند Word يحتوي على رسومات WMF، مما يساعد في تحسين حجم ملف PDF الناتج.

### أين يمكنني العثور على مزيد من المعلومات حول Aspose.Words؟

 يمكنك استكشاف المزيد حول Aspose.Words في[توثيق Aspose.Words](https://reference.aspose.com/words/net/) . للتنزيلات والإصدارات التجريبية والدعم، قم بزيارة[صفحة تحميل برنامج Aspose.Words](https://releases.aspose.com/words/net/), [شراء Aspose.Words](https://purchase.aspose.com/buy), [نسخة تجريبية مجانية](https://releases.aspose.com/), [رخصة مؤقتة](https://purchase.aspose.com/temporary-license/) ، و[يدعم](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
