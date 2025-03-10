---
title: تعيين مجلد الخطوط
linktitle: تعيين مجلد الخطوط
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية تعيين مجلد خطوط مخصصة في Aspose.Words لـ .NET لضمان عرض مستندات Word الخاصة بك بشكل صحيح دون فقدان الخطوط.
weight: 10
url: /ar/net/working-with-fonts/set-fonts-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تعيين مجلد الخطوط

## مقدمة

هل سبق لك أن واجهت مشكلات تتعلق بخطوط مفقودة أثناء العمل مع مستندات Word في تطبيق .NET الخاص بك؟ حسنًا، لست وحدك. يمكن أن يؤدي تعيين مجلد الخطوط الصحيح إلى حل هذه المشكلة بسلاسة. في هذا الدليل، سنوضح لك كيفية تعيين مجلد الخطوط باستخدام Aspose.Words لـ .NET. دعنا نتعمق في الأمر!

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

- تم تثبيت Visual Studio على جهازك
- إعداد إطار عمل .NET
-  مكتبة Aspose.Words لـ .NET. إذا لم تقم بتنزيلها بالفعل، يمكنك تنزيلها من[هنا](https://releases.aspose.com/words/net/).

## استيراد مساحات الأسماء

أولاً، تحتاج إلى استيراد مساحات الأسماء اللازمة للعمل مع Aspose.Words. أضف الأسطر التالية في أعلى ملف التعليمات البرمجية الخاص بك:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

يعد إعداد مجلد الخطوط أمرًا سهلاً إذا اتبعت هذه الخطوات بعناية.

## الخطوة 1: تحديد دليل المستندات

قبل أي شيء آخر، قم بتحديد المسار إلى دليل المستندات الخاص بك. سيحتوي هذا الدليل على مستندات Word والخطوط التي تريد استخدامها.

```csharp
// المسار إلى دليل المستند الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 تأكد من الاستبدال`"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي إلى الدليل الخاص بك.

## الخطوة 2: تهيئة إعدادات الخط

 الآن، تحتاج إلى تهيئة`FontSettings` يسمح لك هذا الكائن بتحديد مجلدات الخطوط المخصصة.

```csharp
FontSettings fontSettings = new FontSettings();
```

## الخطوة 3: تعيين مجلد الخطوط

 استخدام`SetFontsFolder` طريقة`FontSettings` الكائن، حدد المجلد الذي سيتم تخزين الخطوط المخصصة فيه.

```csharp
fontSettings.SetFontsFolder(dataDir + "Fonts", false);
```

 هنا،`dataDir + "Fonts"` يشير إلى المجلد المسمى "الخطوط" ضمن دليل المستندات الخاص بك. المعلمة الثانية،`false`يشير إلى أن المجلد ليس متكررًا.

## الخطوة 4: إنشاء LoadOptions

 بعد ذلك، قم بإنشاء مثيل لـ`LoadOptions` ستساعدك هذه الفئة على تحميل المستند بإعدادات الخط المحددة.

```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.FontSettings = fontSettings;
```

## الخطوة 5: تحميل المستند

 أخيرًا، قم بتحميل مستند Word باستخدام`Document` الصف و`LoadOptions` هدف.

```csharp
Document doc = new Document(dataDir + "Rendering.docx", loadOptions);
```

 تأكد من ذلك`"Rendering.docx"` هو اسم مستند Word الخاص بك. يمكنك استبداله باسم الملف الخاص بك.

## خاتمة

والآن، إليك ما تحتاجه! باتباع هذه الخطوات، يمكنك بسهولة تعيين مجلد خطوط مخصص في Aspose.Words for .NET، مما يضمن عرض جميع الخطوط بشكل صحيح. يمكن أن يوفر لك هذا الإعداد البسيط الكثير من المتاعب ويجعل مستنداتك تبدو تمامًا كما تريدها.

## الأسئلة الشائعة

### لماذا أحتاج إلى تعيين مجلد الخطوط المخصصة؟
يؤدي تعيين مجلد الخطوط المخصصة إلى ضمان عرض جميع الخطوط المستخدمة في مستندات Word بشكل صحيح، مما يتجنب مشكلات الخطوط المفقودة.

### هل يمكنني تعيين مجلدات خطوط متعددة؟
 نعم يمكنك استخدام`SetFontsFolders` طريقة لتحديد مجلدات متعددة.

### ماذا يحدث إذا لم يتم العثور على الخط؟
سيحاول Aspose.Words استبدال الخط المفقود بخط مشابه من خطوط النظام.

### هل Aspose.Words متوافق مع .NET Core؟
نعم، يدعم Aspose.Words .NET Core بالإضافة إلى .NET Framework.

### أين يمكنني الحصول على الدعم إذا واجهت مشاكل؟
 يمكنك الحصول على الدعم من[منتدى دعم Aspose.Words](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
