---
title: استخدم الخط من الجهاز المستهدف
linktitle: استخدم الخط من الجهاز المستهدف
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية استخدام الخطوط من الجهاز المستهدف في مستندات Word باستخدام Aspose.Words for .NET. اتبع دليلنا خطوة بخطوة لدمج الخطوط بسلاسة.
weight: 10
url: /ar/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# استخدم الخط من الجهاز المستهدف

## مقدمة

هل أنت مستعد للغوص في عالم Aspose.Words الرائع لـ .NET؟ استعد، لأننا على وشك أن نأخذك في رحلة عبر عالم الخطوط السحري. اليوم، نركز على كيفية استخدام الخطوط من الجهاز المستهدف عند العمل مع مستندات Word. تضمن هذه الميزة الرائعة أن يبدو مستندك بالطريقة التي تريدها تمامًا، بغض النظر عن المكان الذي يتم عرضه فيه. لنبدأ!

## المتطلبات الأساسية

قبل أن ننتقل إلى التفاصيل الدقيقة، دعنا نتأكد من أن لديك كل ما تحتاجه:

1.  Aspose.Words for .NET: تأكد من تثبيت مكتبة Aspose.Words for .NET. إذا لم تكن قد قمت بذلك بالفعل، فيمكنك تنزيلها[هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: يجب أن يكون لديك بيئة تطوير .NET مهيأة، مثل Visual Studio.
3. المستند الذي سيتم العمل به: قم بإعداد مستند Word للاختبار. سنستخدم مستندًا باسم "Bullet points with alternative font.docx".

الآن بعد أن قمنا بتغطية الأساسيات، دعنا نتعمق في الكود!

## استيراد مساحات الأسماء

أولاً وقبل كل شيء، نحتاج إلى استيراد مساحات الأسماء الضرورية. هذا هو العمود الفقري لمشروعنا، والذي يربط كل النقاط.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## الخطوة 1: تحميل مستند Word

 الخطوة الأولى في برنامجنا التعليمي هي تحميل مستند Word. وهنا يبدأ كل شيء. سنستخدم`Document` لتحقيق ذلك، يمكنك استخدام فئة من مكتبة Aspose.Words.

### الخطوة 1.1: تحديد مسار المستند

لنبدأ بتحديد المسار إلى دليل المستندات الخاص بك. هذا هو المكان الذي يوجد فيه مستند Word الخاص بك.

```csharp
// المسار إلى دليل المستندات الخاص بك
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

### الخطوة 1.2: تحميل المستند

 الآن، نقوم بتحميل المستند باستخدام`Document` فصل.

```csharp
// تحميل مستند Word
Document doc = new Document(dataDir + "Bullet points with alternative font.docx");
```

## الخطوة 2: تكوين خيارات الحفظ

بعد ذلك، نحتاج إلى تكوين خيارات الحفظ. هذه الخطوة بالغة الأهمية لأنها تضمن أن الخطوط المستخدمة في المستند هي الخطوط المستخدمة على الجهاز المستهدف.

 سوف نقوم بإنشاء مثيل لـ`HtmlFixedSaveOptions` وضبط`UseTargetMachineFonts`الممتلكات ل`true`.

```csharp
// قم بتكوين خيارات النسخ الاحتياطي باستخدام ميزة "استخدام الخطوط من الجهاز المستهدف"
HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions
{
    UseTargetMachineFonts = true
};
```

## الخطوة 3: حفظ المستند

أخيرًا، نحفظ المستند كملف HTML ثابت. وهنا تحدث السحر!

 سوف نستخدم`Save` الطريقة لحفظ المستند باستخدام خيارات الحفظ المخصصة.

```csharp
// تحويل المستند إلى HTML ثابت
doc.Save(dataDir + "WorkingWithHtmlFixedSaveOptions.UseFontFromTargetMachine.html", saveOptions);
```

## الخطوة 4: التحقق من الناتج

أخيرًا وليس آخرًا، من الأفضل دائمًا التحقق من النتائج. افتح ملف HTML المحفوظ وتحقق من تطبيق الخطوط بشكل صحيح من الجهاز المستهدف.

انتقل إلى الدليل الذي قمت بحفظ ملف HTML فيه وافتحه في متصفح الويب.

```csharp
// التحقق من النتيجة عن طريق فتح ملف HTML
System.Diagnostics.Process.Start(dataDir + "WorkingWithHtmlFixedSaveOptions.UseFontFromTargetMachine.html");
```

والآن، لقد نجحت في استخدام الخطوط من الجهاز المستهدف في مستند Word الخاص بك باستخدام Aspose.Words for .NET.

## خاتمة

يضمن استخدام الخطوط من الجهاز المستهدف أن تبدو مستندات Word الخاصة بك متسقة واحترافية، بغض النظر عن المكان الذي يتم عرضها فيه. يجعل Aspose.Words for .NET هذه العملية مباشرة وفعالة. باتباع هذا البرنامج التعليمي، تعلمت كيفية تحميل مستند وتكوين خيارات الحفظ وحفظ المستند بإعدادات الخط المطلوبة. برمجة سعيدة!

## الأسئلة الشائعة

### هل يمكنني استخدام هذه الطريقة مع تنسيقات المستندات الأخرى؟
نعم، يدعم Aspose.Words for .NET تنسيقات المستندات المختلفة، ويمكنك تكوين خيارات حفظ مماثلة لتنسيقات مختلفة.

### ماذا لو كان الجهاز المستهدف لا يحتوي على الخطوط المطلوبة؟
إذا لم يكن الجهاز المستهدف يحتوي على الخطوط المطلوبة، فقد لا يتم عرض المستند بالشكل المطلوب. من الأفضل دائمًا تضمين الخطوط عند الضرورة.

### كيف أقوم بتضمين الخطوط في مستند؟
 يمكن تضمين الخطوط باستخدام`FontSettings` الفئة في Aspose.Words لـ .NET. راجع[التوثيق](https://reference.aspose.com/words/net/) لمزيد من التفاصيل.

### هل هناك طريقة لمعاينة المستند قبل الحفظ؟
 نعم يمكنك استخدام`DocumentRenderer` فئة لمعاينة المستند قبل الحفظ. تحقق من Aspose.Words لـ .NET[التوثيق](https://reference.aspose.com/words/net/) لمزيد من المعلومات.

### هل يمكنني تخصيص إخراج HTML بشكل أكبر؟
 بالتأكيد!`HtmlFixedSaveOptions` توفر الفئة خصائص متنوعة لتخصيص مخرجات HTML. استكشف[التوثيق](https://reference.aspose.com/words/net/) لكل الخيارات المتاحة.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
