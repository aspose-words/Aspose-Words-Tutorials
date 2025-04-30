---
"description": "تعرّف على كيفية الحصول على مواضع الجداول العائمة في مستندات Word باستخدام Aspose.Words لـ .NET. سيرشدك هذا الدليل المفصل خطوة بخطوة إلى كل ما تحتاج لمعرفته."
"linktitle": "الحصول على موضع الجدول العائم"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "الحصول على موضع الجدول العائم"
"url": "/ar/net/programming-with-tables/get-floating-table-position/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# الحصول على موضع الجدول العائم

## مقدمة

هل أنت مستعد للتعمق في عالم Aspose.Words لـ .NET؟ سنأخذك اليوم في رحلة لاكتشاف أسرار الجداول العائمة في مستندات Word. تخيل أن لديك جدولًا لا يستقر فحسب، بل يطفو بأناقة حول النص. رائع، أليس كذلك؟ سيشرح لك هذا البرنامج التعليمي كيفية الحصول على خصائص تحديد المواقع لهذه الجداول العائمة. هيا بنا نبدأ!

## المتطلبات الأساسية

قبل أن ننتقل إلى الجزء الممتع، هناك بعض الأشياء التي تحتاج إلى وضعها في مكانها:

1. Aspose.Words لـ .NET: إذا لم تقم بذلك بالفعل، فقم بتنزيل Aspose.Words لـ .NET وتثبيته من [صفحة إصدارات Aspose](https://releases.aspose.com/words/net/).
2. بيئة التطوير: تأكد من إعداد بيئة تطوير .NET لديك. يُعد Visual Studio خيارًا ممتازًا.
3. مستند نموذجي: ستحتاج إلى مستند Word بجدول عائم. يمكنك إنشاء واحد أو استخدام مستند موجود. 

## استيراد مساحات الأسماء

للبدء، عليك استيراد مساحات الأسماء اللازمة. هذا يضمن لك الوصول إلى فئات وطرق Aspose.Words اللازمة لمعالجة مستندات Word.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

حسنًا، دعنا نقسم العملية إلى خطوات سهلة المتابعة.

## الخطوة 1: تحميل المستند الخاص بك

أولاً، عليك تحميل مستند Word. يجب أن يحتوي هذا المستند على الجدول العائم الذي تريد فحصه.

```csharp
// المسار إلى دليل المستندات الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

في هذه الخطوة، ستُخبر Aspose.Words بمكان مستندك. تأكد من استبدال `"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي للمستند الخاص بك.

## الخطوة 2: الوصول إلى الجداول في المستند

بعد ذلك، عليك الوصول إلى الجداول في القسم الأول من المستند. تخيّل المستند كحاوية كبيرة، وستبحث فيه للعثور على جميع الجداول.

```csharp
foreach (Table table in doc.FirstSection.Body.Tables)
{
    // يذهب الكود الخاص بك لمعالجة كل جدول هنا
}
```

هنا، يمكنك المرور عبر كل جدول موجود في نص القسم الأول من مستندك.

## الخطوة 3: التحقق مما إذا كان الجدول عائمًا

الآن، عليك تحديد ما إذا كان الجدول من نوع الجدول العائم. الجداول العائمة لها إعدادات خاصة لتغليف النص.

```csharp
if (table.TextWrapping == TextWrapping.Around)
{
    // يظهر هنا الكود الخاص بطباعة خصائص وضع الجدول
}
```

يتحقق هذا الشرط مما إذا كان نمط التفاف النص الخاص بالجدول مضبوطًا على "حول"، مما يشير إلى أن الجدول عبارة عن جدول عائم.

## الخطوة 4: طباعة خصائص الموضع

أخيرًا، لنستخرج ونطبع خصائص موقع الجدول العائم. توضح هذه الخصائص موقع الجدول بالنسبة للنص والصفحة.

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

وهذا كل ما في الأمر! باتباع هذه الخطوات، يمكنك بسهولة استرداد خصائص وضع الجداول العائمة وطباعتها في مستندات Word باستخدام Aspose.Words لـ .NET. سواء كنت تُؤتمت معالجة المستندات أو مهتمًا فقط بتخطيطات الجداول، ستكون هذه المعرفة مفيدة لك بالتأكيد.

تذكر أن العمل مع Aspose.Words لـ .NET يفتح آفاقًا واسعةً لمعالجة المستندات وأتمتتها. برمجة ممتعة!

## الأسئلة الشائعة

### ما هو الجدول العائم في مستندات Word؟
الجدول العائم هو جدول غير ثابت على النص ولكن يمكن تحريكه، وعادةً ما يكون النص يلتف حوله.

### كيف يمكنني معرفة ما إذا كان الجدول عائمًا باستخدام Aspose.Words لـ .NET؟
يمكنك التحقق مما إذا كان الجدول عائمًا عن طريق فحصه `TextWrapping` الملكية. إذا تم ضبطها على `TextWrapping.Around`، الجدول عائم.

### هل يمكنني تغيير خصائص وضع الجدول العائم؟
نعم، باستخدام Aspose.Words لـ .NET، يمكنك تعديل خصائص تحديد موقع جدول عائم لتخصيص تخطيطه.

### هل Aspose.Words for .NET مناسب لأتمتة المستندات على نطاق واسع؟
بالتأكيد! صُمم Aspose.Words for .NET لأتمتة المستندات بكفاءة عالية، ويمكنه التعامل مع العمليات واسعة النطاق بكفاءة.

### أين يمكنني العثور على مزيد من المعلومات والموارد حول Aspose.Words لـ .NET؟
يمكنك العثور على وثائق وموارد مفصلة على [صفحة توثيق Aspose.Words لـ .NET](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}