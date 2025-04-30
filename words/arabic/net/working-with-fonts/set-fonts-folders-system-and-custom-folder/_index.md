---
"description": "تعرف على كيفية تعيين مجلدات الخطوط المخصصة والنظامية في مستندات Word باستخدام Aspose.Words لـ .NET، مما يضمن عرض مستنداتك بشكل صحيح عبر بيئات مختلفة."
"linktitle": "تعيين نظام مجلدات الخطوط والمجلد المخصص"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "تعيين نظام مجلدات الخطوط والمجلد المخصص"
"url": "/ar/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تعيين نظام مجلدات الخطوط والمجلد المخصص

## مقدمة

تخيل أنك تُنشئ مستندًا بنمط خط فريد، لتكتشف أن الخطوط لا تظهر بشكل صحيح على جهاز آخر. أمر مُحبط، أليس كذلك؟ هنا يأتي دور تهيئة مجلدات الخطوط. مع Aspose.Words لـ .NET، يمكنك تحديد مجلدات خطوط النظام والمخصصة لضمان ظهور مستنداتك دائمًا بالشكل المطلوب. لنبدأ بشرح كيفية تحقيق ذلك.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

- Aspose.Words لمكتبة .NET: إذا لم تقم بتنزيلها بالفعل، فقم بتنزيلها [هنا](https://releases.aspose.com/words/net/).
- بيئة التطوير: بيئة تطوير متكاملة مثل Visual Studio.
- المعرفة الأساسية بلغة C#: ستساعدك المعرفة بلغة C# على متابعة أمثلة التعليمات البرمجية.

## استيراد مساحات الأسماء

أولاً، قم باستيراد المساحات الأساسية اللازمة في مشروعك:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

الآن، دعونا نقسم العملية إلى خطوات بسيطة.

## الخطوة 1: تحميل المستند

للبدء، قم بتحميل مستند Word الخاص بك إلى Aspose.Words `Document` سيكون هذا المستند هو المستند الذي تريد تعيين مجلدات الخطوط فيه.

```csharp
// المسار إلى دليل المستندات الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## الخطوة 2: تهيئة إعدادات الخط

إنشاء مثيل جديد من `FontSettings`سيسمح لك هذا الكائن بإدارة مصادر الخطوط.

```csharp
FontSettings fontSettings = new FontSettings();
```

## الخطوة 3: استرداد مصادر خطوط النظام

استرجاع مصادر خطوط النظام الافتراضية. على أجهزة ويندوز، يتضمن هذا عادةً مجلد "Windows\Fonts".

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## الخطوة 4: إضافة مجلد الخطوط المخصصة

أضف مجلدًا مخصصًا يحتوي على خطوطك الإضافية. هذا مفيد إذا كانت لديك خطوط محددة غير مثبتة في مجلد خطوط النظام.

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## الخطوة 5: تحديث مصادر الخطوط

تحويل قائمة مصادر الخطوط مرة أخرى إلى مصفوفة وتعيينها إلى `FontSettings` هدف.

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## الخطوة 6: تطبيق إعدادات الخط على المستند

أخيرًا، قم بتطبيق الإعدادات المُكوّنة `FontSettings` إلى مستندك وحفظه بالتنسيق المطلوب، مثل PDF.

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## خاتمة

وهذا كل شيء! باتباع هذه الخطوات، يمكنك ضمان استخدام مستندات Word للخطوط الصحيحة، سواءً كانت خطوط نظام أو خطوطًا مخصصة مخزنة في مجلد محدد. يساعد هذا الإعداد في الحفاظ على سلامة مظهر مستندك في مختلف البيئات.

## الأسئلة الشائعة

### ماذا يحدث إذا كان الخط مفقودًا في كل من مجلد النظام والمجلد المخصص؟

سيستخدم Aspose.Words خطًا افتراضيًا لاستبدال الخط المفقود، مما يضمن بقاء المستند قابلاً للقراءة.

### هل يمكنني إضافة مجلدات خطوط مخصصة متعددة؟

نعم، يمكنك إضافة مجلدات خطوط مخصصة متعددة عن طريق تكرار عملية الإنشاء `FolderFontSource` الكائنات وإضافتها إلى قائمة مصادر الخط.

### هل من الممكن استخدام مسارات الشبكة لمجلدات الخطوط المخصصة؟

نعم، يمكنك تحديد مسار الشبكة في `FolderFontSource` منشئ.

### ما هي تنسيقات الملفات التي يدعمها Aspose.Words لحفظ المستندات؟

يدعم Aspose.Words تنسيقات مختلفة، بما في ذلك DOCX، وPDF، وHTML، والمزيد.

### كيف أتعامل مع إشعارات استبدال الخط؟

يمكنك التعامل مع إشعارات استبدال الخط باستخدام `FontSettings` الصف `FontSubstitutionWarning` حدث.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}