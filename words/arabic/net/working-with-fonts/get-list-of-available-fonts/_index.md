---
"description": "اكتشف كيفية الحصول على قائمة بالخطوط المتاحة باستخدام Aspose.Words لـ .NET في هذا الدليل التعليمي المفصل خطوة بخطوة. طوّر مهاراتك في إدارة الخطوط."
"linktitle": "احصل على قائمة الخطوط المتوفرة"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "احصل على قائمة الخطوط المتوفرة"
"url": "/ar/net/working-with-fonts/get-list-of-available-fonts/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# احصل على قائمة الخطوط المتوفرة

## مقدمة

هل واجهتَ يومًا صعوبة في إدارة الخطوط في مستندات Word؟ إذا كنتَ مطورًا لـ .NET، فـ Aspose.Words for .NET هنا لمساعدتك! هذه المكتبة الفعّالة لا تساعدك فقط على إنشاء مستندات Word وتعديلها برمجيًا، بل توفر أيضًا إمكانيات شاملة لإدارة الخطوط. في هذا الدليل، سنشرح لك خطوة بخطوة كيفية الحصول على قائمة بالخطوط المتاحة باستخدام Aspose.Words for .NET. سنُقسّمها إلى خطوات سهلة الفهم لضمان سهولة متابعتها. هيا بنا نبدأ ونجعل إدارة الخطوط في غاية السهولة!

## المتطلبات الأساسية

قبل أن نبدأ، هناك بعض الأشياء التي ستحتاجها:

- Aspose.Words لـ .NET: تأكد من تثبيت مكتبة Aspose.Words لـ .NET. يمكنك تنزيلها من [هنا](https://releases.aspose.com/words/net/).
- Visual Studio: يستخدم هذا المثال Visual Studio كبيئة تطوير.
- .NET Framework: تأكد من تثبيت .NET Framework على جهازك.
- دليل المستندات: مسار الدليل الذي يتم تخزين مستنداتك فيه.

## استيراد مساحات الأسماء

أولاً، قم باستيراد المساحات الأساسية اللازمة إلى مشروعك:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

## الخطوة 1: تهيئة إعدادات الخط

الخطوة الأولى هي تهيئة إعدادات الخط. هذا سيسمح لك بإدارة مصادر الخطوط لمستنداتك.

```csharp
FontSettings fontSettings = new FontSettings();
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

- FontSettings: يتم استخدام هذه الفئة لتحديد إعدادات استبدال الخط ومصادر الخط.
- fontSources: نقوم بإنشاء قائمة بمصادر الخطوط الموجودة من إعدادات الخط الحالية.

## الخطوة 2: تحديد دليل المستندات

بعد ذلك، حدد مسار مجلد المستندات. هنا سيبحث Aspose.Words عن الخطوط.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

- dataDir: هذا المتغير النصي يحمل مسار الدليل الذي توجد فيه خطوطك. استبدل `"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي.

## الخطوة 3: إضافة مجلد الخطوط المخصصة

الآن، أضف مصدر مجلد جديد لتوجيه Aspose.Words للبحث في هذا المجلد عن الخطوط.

```csharp
FolderFontSource folderFontSource = new FolderFontSource(dataDir, true);
```

- مصدر خط المجلد: تُمثل هذه الفئة مصدر خط المجلد. المعلمة الثانية (`true`يشير إلى ما إذا كان سيتم البحث عن الخطوط بشكل متكرر في المجلدات الفرعية.

## الخطوة 4: تحديث مصادر الخطوط

أضف مجلد الخط المخصص إلى قائمة مصادر الخطوط الموجودة وقم بتحديث إعدادات الخط.

```csharp
fontSources.Add(folderFontSource);
FontSourceBase[] updatedFontSources = fontSources.ToArray();
```

- fontSources.Add(folderFontSource): يضيف مجلد الخط المخصص إلى مصادر الخطوط الموجودة.
- updatedFontSources: تحويل قائمة مصادر الخط إلى مصفوفة.

## الخطوة 5: استرداد الخطوط وعرضها

أخيرًا، قم باسترداد الخطوط المتوفرة وعرض تفاصيلها.

```csharp
foreach (PhysicalFontInfo fontInfo in updatedFontSources[0].GetAvailableFonts())
{
    Console.WriteLine("FontFamilyName : " + fontInfo.FontFamilyName);
    Console.WriteLine("FullFontName  : " + fontInfo.FullFontName);
    Console.WriteLine("Version  : " + fontInfo.Version);
    Console.WriteLine("FilePath : " + fontInfo.FilePath);
}
```

- GetAvailableFonts(): استرداد قائمة الخطوط المتوفرة من مصدر الخط الأول في القائمة المحدثة.
- fontInfo: مثال على `PhysicalFontInfo` يحتوي على تفاصيل حول كل خط.

## خاتمة

تهانينا! لقد نجحت في استرجاع قائمة الخطوط المتاحة باستخدام Aspose.Words لـ .NET. شرح لك هذا البرنامج التعليمي كل خطوة، من تهيئة إعدادات الخط إلى عرض تفاصيله. بفضل هذه المعرفة، يمكنك الآن إدارة الخطوط في مستندات Word بسهولة. تذكر أن Aspose.Words لـ .NET أداة فعّالة تُحسّن بشكل كبير من قدرات معالجة مستنداتك. لذا، استكشف المزيد من الميزات لجعل عملية التطوير أكثر كفاءة.

## الأسئلة الشائعة

### هل يمكنني استخدام Aspose.Words لـ .NET مع أطر عمل .NET الأخرى؟
نعم، Aspose.Words for .NET متوافق مع مختلف أطر عمل .NET بما في ذلك .NET Core و.NET 5+.

### كيف أقوم بتثبيت Aspose.Words لـ .NET؟
يمكنك تثبيته عبر NuGet Package Manager في Visual Studio عن طريق البحث عن "Aspose.Words".

### هل من الممكن إضافة مجلدات خطوط مخصصة متعددة؟
نعم، يمكنك إضافة مجلدات خطوط مخصصة متعددة عن طريق إنشاء عدة `FolderFontSource` الحالات وإضافتها إلى قائمة مصادر الخط.

### هل يمكنني استرجاع تفاصيل الخط من مصدر خط محدد؟
نعم، يمكنك استرداد تفاصيل الخط من أي مصدر خط عن طريق تحديد فهرس مصدر الخط في `updatedFontSources` مصفوفة.

### هل يدعم Aspose.Words لـ .NET استبدال الخطوط؟
نعم، فهو يدعم استبدال الخط للتأكد من عرض النص بشكل صحيح حتى لو لم يكن الخط الأصلي متاحًا.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}