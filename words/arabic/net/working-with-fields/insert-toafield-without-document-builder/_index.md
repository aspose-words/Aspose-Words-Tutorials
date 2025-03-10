---
title: إدراج حقل TOA بدون منشئ المستندات
linktitle: إدراج حقل TOA بدون منشئ المستندات
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إدراج حقل TOA دون استخدام منشئ المستندات في Aspose.Words for .NET. اتبع دليلنا خطوة بخطوة لإدارة الاستشهادات القانونية بكفاءة.
weight: 10
url: /ar/net/working-with-fields/insert-toafield-without-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إدراج حقل TOA بدون منشئ المستندات

## مقدمة

قد يبدو إنشاء حقل جدول المصادر (TOA) في مستند Word أشبه بتجميع أجزاء لغز معقد. ومع ذلك، بمساعدة Aspose.Words for .NET، تصبح العملية سلسة ومباشرة. في هذه المقالة، سنرشدك خلال الخطوات اللازمة لإدراج حقل جدول المصادر (TOA) دون استخدام منشئ المستندات، مما يسهل عليك إدارة الاستشهادات والمراجع القانونية داخل مستندات Word الخاصة بك.

## المتطلبات الأساسية

قبل الخوض في البرنامج التعليمي، دعنا نغطي الأساسيات التي ستحتاجها:

-  Aspose.Words for .NET: تأكد من تثبيت أحدث إصدار. يمكنك تنزيله من[موقع اسبوس](https://releases.aspose.com/words/net/).
- بيئة التطوير: بيئة تطوير متكاملة متوافقة مع .NET مثل Visual Studio.
- المعرفة الأساسية بلغة C#: سيكون من المفيد فهم قواعد ومفاهيم لغة C# الأساسية.
- نموذج مستند Word: قم بإنشاء مستند نموذجي أو احتفظ به جاهزًا حيث تريد إدراج حقل TOA.

## استيراد مساحات الأسماء

للبدء، ستحتاج إلى استيراد مساحات الأسماء الضرورية من مكتبة Aspose.Words. يضمن هذا الإعداد إمكانية وصولك إلى جميع الفئات والطرق المطلوبة لمعالجة المستندات.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

دعنا نقسم العملية إلى خطوات بسيطة وسهلة المتابعة. سنرشدك خلال كل مرحلة، ونشرح ما يفعله كل جزء من التعليمات البرمجية وكيف يساهم في إنشاء حقل TOA.

## الخطوة 1: تهيئة المستند

 أولاً، تحتاج إلى إنشاء مثيل لـ`Document` يمثل هذا الكائن مستند Word الذي تعمل عليه.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

يقوم هذا الكود بإنشاء مستند Word جديد. يمكنك اعتباره بمثابة إنشاء لوحة قماشية فارغة يمكنك إضافة المحتوى إليها.

## الخطوة 2: إنشاء حقل TA وتكوينه

بعد ذلك، سنضيف حقل TA (جدول السلطات). يحدد هذا الحقل الإدخالات التي ستظهر في جدول السلطات.

```csharp
Paragraph para = new Paragraph(doc);

// نريد إدراج حقول TA وTOA مثل هذا:
// { TA \c 1 \l "القيمة 0" }
FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);
fieldTA.EntryCategory = "1";
fieldTA.LongCitation = "Value 0";

doc.FirstSection.Body.AppendChild(para);
```

فيما يلي تفصيل:
- فقرة الفقرة = فقرة جديدة(doc);: إنشاء فقرة جديدة داخل المستند.
-  FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);: إضافة حقل TA إلى الفقرة. ال`FieldType.FieldTOAEntry` يحدد أن هذا هو حقل إدخال TOA.
- fieldTA.EntryCategory = "1";: يحدد فئة الإدخال. وهذا مفيد لتصنيف أنواع مختلفة من الإدخالات.
- fieldTA.LongCitation = "Value 0";: يحدد نص الاقتباس الطويل. هذا هو النص الذي سيظهر في TOA.
- doc.FirstSection.Body.AppendChild(para);: يضيف الفقرة التي تحتوي على الحقل TA إلى نص المستند.

## الخطوة 3: إضافة حقل TOA

الآن، سنقوم بإدراج حقل TOA الفعلي الذي يجمع كل إدخالات TA في جدول.

```csharp
para = new Paragraph(doc);

FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);
fieldToa.EntryCategory = "1";
doc.FirstSection.Body.AppendChild(para);
```

في هذه الخطوة:
- FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);: إضافة حقل TOA إلى الفقرة.
- fieldToa.EntryCategory = "1";: يقوم بتصفية الإدخالات لتشمل فقط تلك التي تم وضع علامة عليها بالفئة "1".

## الخطوة 4: تحديث حقل TOA

بعد إدخال حقل TOA، ستحتاج إلى تحديثه للتأكد من أنه يعكس أحدث الإدخالات.

```csharp
fieldToa.Update();
```

يقوم هذا الأمر بتحديث حقل TOA، مما يضمن عرض جميع الإدخالات المحددة بشكل صحيح في الجدول.

## الخطوة 5: احفظ المستند

وأخيرًا، احفظ مستندك باستخدام حقل TOA المُضاف حديثًا.

```csharp
doc.Save(dataDir + "WorkingWithFields.InsertTOAFieldWithoutDocumentBuilder.docx");
```

 يحفظ هذا السطر من التعليمات البرمجية المستند في الدليل المحدد. تأكد من استبدال`"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي الذي تريد حفظ ملفك فيه.

## خاتمة

والآن، لقد نجحت في إضافة حقل TOA إلى مستند Word دون استخدام منشئ المستندات. باتباع الخطوات التالية، يمكنك إدارة الاستشهادات بكفاءة وإنشاء جداول شاملة للمراجع في مستنداتك القانونية. يجعل Aspose.Words for .NET هذه العملية سلسة وفعالة، مما يمنحك الأدوات اللازمة للتعامل مع مهام المستندات المعقدة بسهولة.

## الأسئلة الشائعة

### هل يمكنني إضافة حقول TA متعددة بفئات مختلفة؟
 نعم، يمكنك إضافة حقول TA متعددة بفئات مختلفة عن طريق ضبط`EntryCategory`الممتلكات وفقا لذلك.

### كيف يمكنني تخصيص مظهر TOA؟
يمكنك تخصيص مظهر TOA عن طريق تعديل خصائص حقل TOA، مثل تنسيق الإدخال وعناوين الفئات.

### هل من الممكن تحديث حقل TOA تلقائيًا؟
 بينما يمكنك تحديث حقل TOA يدويًا باستخدام`Update` الطريقة، Aspose.Words لا تدعم حاليًا التحديثات التلقائية لتغييرات المستند.

### هل يمكنني إضافة حقول TA برمجيًا في أجزاء محددة من المستند؟
نعم، يمكنك إضافة حقول TA في مواقع محددة عن طريق إدراجها في الفقرات أو الأقسام المطلوبة.

### كيف يمكنني التعامل مع حقول TOA المتعددة في مستند واحد؟
 يمكنك إدارة حقول TOA المتعددة عن طريق تعيين حقول مختلفة`EntryCategory` القيم والتأكد من أن كل حقل TOA يقوم بتصفية الإدخالات بناءً على فئته.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
