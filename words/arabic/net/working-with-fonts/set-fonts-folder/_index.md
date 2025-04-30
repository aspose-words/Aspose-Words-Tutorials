---
"description": "تعرف على كيفية تعيين مجلد خطوط مخصصة في Aspose.Words لـ .NET لضمان عرض مستندات Word الخاصة بك بشكل صحيح دون فقدان أي خطوط."
"linktitle": "تعيين مجلد الخطوط"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "تعيين مجلد الخطوط"
"url": "/ar/net/working-with-fonts/set-fonts-folder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تعيين مجلد الخطوط

## مقدمة

هل سبق لك أن واجهت مشاكل في الخطوط المفقودة أثناء العمل على مستندات Word في تطبيق .NET؟ حسنًا، لست وحدك. يُمكنك حل هذه المشكلة بسهولة عن طريق ضبط مجلد الخطوط الصحيح. في هذا الدليل، سنشرح لك كيفية ضبط مجلد الخطوط باستخدام Aspose.Words لـ .NET. هيا بنا!

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

- تم تثبيت Visual Studio على جهازك
- إعداد .NET Framework
- مكتبة Aspose.Words لـ .NET. إذا لم تقم بتنزيلها بعد، يمكنك تنزيلها من [هنا](https://releases.aspose.com/words/net/).

## استيراد مساحات الأسماء

أولاً، عليك استيراد مساحات الأسماء اللازمة للعمل مع Aspose.Words. أضف الأسطر التالية في أعلى ملف الكود الخاص بك:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

يعد إعداد مجلد الخطوط أمرًا بسيطًا إذا اتبعت الخطوات التالية بعناية.

## الخطوة 1: تحديد دليل المستندات

قبل أي شيء، حدد مسار مجلد المستندات. سيحتوي هذا المجلد على مستندات Word والخطوط التي تريد استخدامها.

```csharp
// المسار إلى دليل المستندات الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

تأكد من الاستبدال `"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي إلى الدليل الخاص بك.

## الخطوة 2: تهيئة إعدادات الخط

الآن، تحتاج إلى تهيئة `FontSettings` هذا الكائن يسمح لك بتحديد مجلدات الخطوط المخصصة.

```csharp
FontSettings fontSettings = new FontSettings();
```

## الخطوة 3: تعيين مجلد الخطوط

باستخدام `SetFontsFolder` طريقة `FontSettings` الكائن، حدد المجلد الذي سيتم تخزين الخطوط المخصصة فيه.

```csharp
fontSettings.SetFontsFolder(dataDir + "Fonts", false);
```

هنا، `dataDir + "Fonts"` يشير إلى المجلد المسمى "الخطوط" ضمن دليل المستندات. المعلمة الثانية، `false`يشير إلى أن المجلد ليس متكررًا.

## الخطوة 4: إنشاء LoadOptions

بعد ذلك، قم بإنشاء مثيل لـ `LoadOptions` ستساعدك هذه الفئة على تحميل المستند بإعدادات الخط المحددة.

```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.FontSettings = fontSettings;
```

## الخطوة 5: تحميل المستند

أخيرًا، قم بتحميل مستند Word باستخدام `Document` الصف و `LoadOptions` هدف.

```csharp
Document doc = new Document(dataDir + "Rendering.docx", loadOptions);
```

تأكد من ذلك `"Rendering.docx"` هو اسم مستند Word الخاص بك. يمكنك استبداله باسم ملفك.

## خاتمة

وهذا كل شيء! باتباع هذه الخطوات، يمكنك بسهولة إنشاء مجلد خطوط مخصص في Aspose.Words لـ .NET، مما يضمن عرض جميع خطوطك بشكل صحيح. هذا الإعداد البسيط سيوفر عليك الكثير من العناء ويجعل مستنداتك تظهر بالشكل الذي تريده تمامًا.

## الأسئلة الشائعة

### لماذا أحتاج إلى تعيين مجلد الخطوط المخصصة؟
يؤدي تعيين مجلد الخطوط المخصصة إلى ضمان عرض جميع الخطوط المستخدمة في مستندات Word بشكل صحيح، مما يتجنب مشكلات الخطوط المفقودة.

### هل يمكنني تعيين مجلدات خطوط متعددة؟
نعم يمكنك استخدام `SetFontsFolders` طريقة لتحديد مجلدات متعددة.

### ماذا يحدث إذا لم يتم العثور على الخط؟
سيحاول Aspose.Words استبدال الخط المفقود بخط مشابه من خطوط النظام.

### هل Aspose.Words متوافق مع .NET Core؟
نعم، يدعم Aspose.Words .NET Core بالإضافة إلى .NET Framework.

### أين يمكنني الحصول على الدعم إذا واجهت مشاكل؟
يمكنك الحصول على الدعم من [منتدى دعم Aspose.Words](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}