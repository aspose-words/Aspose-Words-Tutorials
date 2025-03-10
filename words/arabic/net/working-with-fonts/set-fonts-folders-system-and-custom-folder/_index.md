---
title: تعيين مجلدات الخطوط للنظام والمجلد المخصص
linktitle: تعيين مجلدات الخطوط للنظام والمجلد المخصص
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية تعيين مجلدات الخطوط المخصصة والنظام في مستندات Word باستخدام Aspose.Words لـ .NET، مما يضمن عرض مستنداتك بشكل صحيح عبر بيئات مختلفة.
weight: 10
url: /ar/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تعيين مجلدات الخطوط للنظام والمجلد المخصص

## مقدمة

تخيل أنك تقوم بإنشاء مستند بنمط خط فريد، فقط لتكتشف أن الخطوط لا يتم عرضها بشكل صحيح على جهاز آخر. إنه أمر محبط، أليس كذلك؟ هنا يأتي دور تكوين مجلدات الخطوط. باستخدام Aspose.Words for .NET، يمكنك تحديد مجلدات خطوط النظام والمخصصة لضمان ظهور مستنداتك دائمًا بالشكل المقصود. دعنا نتعمق في كيفية تحقيق ذلك.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

-  Aspose.Words for .NET Library: إذا لم تقم بتنزيلها بالفعل، فقم بتنزيلها[هنا](https://releases.aspose.com/words/net/).
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

الآن، دعونا نقوم بتقسيم العملية إلى خطوات بسيطة.

## الخطوة 1: تحميل المستند

 للبدء، قم بتحميل مستند Word الخاص بك إلى Aspose.Words`Document` سيكون هذا المستند هو المستند الذي تريد تعيين مجلدات الخطوط فيه.

```csharp
// المسار إلى دليل المستند الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## الخطوة 2: تهيئة إعدادات الخط

 إنشاء مثيل جديد من`FontSettings`سيسمح لك هذا الكائن بإدارة مصادر الخطوط.

```csharp
FontSettings fontSettings = new FontSettings();
```

## الخطوة 3: استرداد مصادر الخطوط للنظام

استرداد مصادر الخطوط الافتراضية للنظام. على جهاز كمبيوتر يعمل بنظام Windows، يتضمن هذا عادةً "Windows\Fonts\"الدليل."

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## الخطوة 4: إضافة مجلد خطوط مخصص

أضف مجلدًا مخصصًا يحتوي على الخطوط الإضافية. يعد هذا مفيدًا إذا كان لديك خطوط معينة غير مثبتة في دليل خطوط النظام.

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## الخطوة 5: تحديث مصادر الخطوط

 تحويل قائمة مصادر الخطوط مرة أخرى إلى مصفوفة وتعيينها إلى`FontSettings` هدف.

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## الخطوة 6: تطبيق إعدادات الخط على المستند

 أخيرًا، قم بتطبيق التكوين الذي تم تكوينه`FontSettings` إلى مستندك وحفظه بالتنسيق المطلوب، مثل PDF.

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## خاتمة

والآن، إليك الأمر! باتباع هذه الخطوات، يمكنك التأكد من أن مستندات Word الخاصة بك تستخدم الخطوط الصحيحة، سواء كانت خطوط نظام أو خطوط مخصصة مخزنة في دليل معين. يساعد هذا الإعداد في الحفاظ على سلامة مظهر مستندك عبر بيئات مختلفة.

## الأسئلة الشائعة

### ماذا يحدث إذا كان الخط مفقودًا في كل من مجلد النظام والمجلد المخصص؟

سيستخدم Aspose.Words خطًا افتراضيًا ليحل محل الخط المفقود، مما يضمن بقاء المستند قابلاً للقراءة.

### هل يمكنني إضافة مجلدات خطوط مخصصة متعددة؟

 نعم، يمكنك إضافة مجلدات خطوط مخصصة متعددة عن طريق تكرار عملية الإنشاء`FolderFontSource` الكائنات وإضافتها إلى قائمة مصادر الخط.

### هل من الممكن استخدام مسارات الشبكة لمجلدات الخطوط المخصصة؟

 نعم، يمكنك تحديد مسار الشبكة في`FolderFontSource` منشئ.

### ما هي تنسيقات الملفات التي يدعمها Aspose.Words لحفظ المستندات؟

يدعم Aspose.Words تنسيقات مختلفة، بما في ذلك DOCX، وPDF، وHTML، والمزيد.

### كيف أتعامل مع إشعارات استبدال الخط؟

 يمكنك التعامل مع إشعارات استبدال الخط باستخدام`FontSettings` الصف`FontSubstitutionWarning`حدث.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
