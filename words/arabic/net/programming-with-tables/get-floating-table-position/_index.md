---
title: الحصول على موضع الجدول العائم
linktitle: الحصول على موضع الجدول العائم
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية الحصول على مواضع الجدول العائمة في مستندات Word باستخدام Aspose.Words for .NET. سيرشدك هذا الدليل التفصيلي خطوة بخطوة إلى كل ما تحتاج إلى معرفته.
weight: 10
url: /ar/net/programming-with-tables/get-floating-table-position/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# الحصول على موضع الجدول العائم

## مقدمة

هل أنت مستعد للغوص في عالم Aspose.Words لـ .NET؟ اليوم، سنأخذك في رحلة لكشف أسرار الجداول العائمة في مستندات Word. تخيل أن لديك جدولاً لا يظل ساكنًا فحسب، بل يطفو بشكل أنيق حول النص. رائع جدًا، أليس كذلك؟ سيرشدك هذا البرنامج التعليمي إلى كيفية الحصول على خصائص تحديد المواقع لهذه الجداول العائمة. لذا، فلنبدأ!

## المتطلبات الأساسية

قبل أن ننتقل إلى الجزء الممتع، هناك بعض الأشياء التي تحتاج إلى وضعها في مكانها:

1.  Aspose.Words for .NET: إذا لم تقم بذلك بالفعل، فقم بتنزيل Aspose.Words for .NET وتثبيته من[صفحة إصدارات Aspose](https://releases.aspose.com/words/net/).
2. بيئة التطوير: تأكد من إعداد بيئة تطوير .NET. يعد Visual Studio خيارًا رائعًا.
3. مستند نموذجي: ستحتاج إلى مستند Word يحتوي على جدول عائم. يمكنك إنشاء واحد أو استخدام مستند موجود. 

## استيراد مساحات الأسماء

للبدء، تحتاج إلى استيراد مساحات الأسماء الضرورية. وهذا يضمن لك إمكانية الوصول إلى فئات وطرق Aspose.Words المطلوبة للتعامل مع مستندات Word.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

حسنًا، دعنا نقسم العملية إلى خطوات سهلة المتابعة.

## الخطوة 1: قم بتحميل مستندك

أولاً وقبل كل شيء، عليك تحميل مستند Word الخاص بك. يجب أن يحتوي هذا المستند على الجدول العائم الذي تريد فحصه.

```csharp
// المسار إلى دليل المستند الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

 في هذه الخطوة، ستقوم بشكل أساسي بإخبار Aspose.Words بمكان العثور على مستندك. تأكد من استبدال`"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي للمستند الخاص بك.

## الخطوة 2: الوصول إلى الجداول الموجودة في المستند

بعد ذلك، تحتاج إلى الوصول إلى الجداول الموجودة ضمن القسم الأول من المستند. فكر في المستند باعتباره حاوية كبيرة، وستقوم بالبحث فيها للعثور على جميع الجداول.

```csharp
foreach (Table table in doc.FirstSection.Body.Tables)
{
    // يذهب الكود الخاص بك لمعالجة كل جدول هنا
}
```

هنا، يمكنك المرور عبر كل جدول موجود في نص القسم الأول من مستندك.

## الخطوة 3: التحقق من أن الجدول عائم

الآن، عليك تحديد ما إذا كان الجدول من النوع العائم. تحتوي الجداول العائمة على إعدادات خاصة لتغليف النص.

```csharp
if (table.TextWrapping == TextWrapping.Around)
{
    // يظهر هنا الكود الخاص بطباعة خصائص تحديد موضع الجدول
}
```

يتحقق هذا الشرط مما إذا كان نمط التفاف النص الخاص بالجدول مضبوطًا على "حول"، مما يشير إلى أن الجدول عبارة عن جدول عائم.

## الخطوة 4: طباعة خصائص الموضع

أخيرًا، دعنا نستخرج خصائص وضع الجدول العائم ونطبعها. تخبرك هذه الخصائص بمكان وضع الجدول بالنسبة للنص والصفحة.

```csharp
if (table.TextWrapping == TextWrapping.Around)
{
    Console.WriteLine("Horizontal Anchor: " + table.HorizontalAnchor);
    Console.WriteLine("Vertical Anchor: " + table.VerticalAnchor);
    Console.WriteLine("Absolute Horizontal Distance: " + table.AbsoluteHorizontalDistance);
    Console.WriteLine("Absolute Vertical Distance: " + table.AbsoluteVerticalDistance);
    Console.WriteLine("Allow Overlap: " + table.AllowOverlap);
    Console.WriteLine("Relative Vertical Alignment: " + table.RelativeVerticalAlignment);
    Console.WriteLine("..............................");
}
```

تتيح لك هذه الخصائص إلقاء نظرة تفصيلية حول كيفية تثبيت الجدول وتحديد موقعه داخل المستند.

## خاتمة

والآن، إليك ما تحتاج إليه! باتباع هذه الخطوات، يمكنك بسهولة استرداد خصائص وضع الجداول العائمة وطباعتها في مستندات Word باستخدام Aspose.Words for .NET. سواء كنت تقوم بأتمتة معالجة المستندات أو كنت مهتمًا فقط بتخطيطات الجداول، فستكون هذه المعرفة مفيدة بالتأكيد.

تذكر أن العمل باستخدام Aspose.Words for .NET يفتح لك عالمًا من الإمكانيات لمعالجة المستندات وأتمتتها. استمتع بالبرمجة!

## الأسئلة الشائعة

### ما هو الجدول العائم في مستندات Word؟
الجدول العائم هو جدول غير ثابت على النص ولكن يمكن تحريكه، وعادةً ما يكون النص يلتف حوله.

### كيف يمكنني معرفة ما إذا كان الجدول عائمًا باستخدام Aspose.Words لـ .NET؟
 يمكنك التحقق مما إذا كان الجدول عائمًا من خلال فحصه`TextWrapping` الملكية. إذا تم ضبطها على`TextWrapping.Around`، الجدول عائم.

### هل يمكنني تغيير خصائص وضع الجدول العائم؟
نعم، باستخدام Aspose.Words لـ .NET، يمكنك تعديل خصائص تحديد موقع جدول عائم لتخصيص تخطيطه.

### هل Aspose.Words for .NET مناسب لأتمتة المستندات على نطاق واسع؟
بالتأكيد! تم تصميم Aspose.Words for .NET لأتمتة المستندات عالية الأداء ويمكنه التعامل مع العمليات واسعة النطاق بكفاءة.

### أين يمكنني العثور على مزيد من المعلومات والموارد حول Aspose.Words لـ .NET؟
يمكنك العثور على وثائق وموارد مفصلة على[صفحة توثيق Aspose.Words لـ .NET](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
