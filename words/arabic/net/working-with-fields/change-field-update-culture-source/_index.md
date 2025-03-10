---
title: تغيير مصدر تحديث الثقافة في الحقل
linktitle: تغيير مصدر تحديث الثقافة في الحقل
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية تغيير مصدر ثقافة تحديث الحقل في Aspose.Words لـ .NET باستخدام هذا الدليل. يمكنك التحكم في تنسيق التاريخ بناءً على ثقافات مختلفة بسهولة.
weight: 10
url: /ar/net/working-with-fields/change-field-update-culture-source/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تغيير مصدر تحديث الثقافة في الحقل

## مقدمة

في هذا البرنامج التعليمي، سنتعمق في عالم Aspose.Words لـ .NET ونستكشف كيفية تغيير مصدر ثقافة تحديث الحقل. إذا كنت تتعامل مع مستندات Word تتضمن حقول تاريخ وتحتاج إلى التحكم في كيفية تنسيق هذه التواريخ بناءً على ثقافات مختلفة، فهذا الدليل مناسب لك. دعنا نستعرض العملية خطوة بخطوة، ونضمن لك فهم كل مفهوم وإمكانية تطبيقه بفعالية في مشاريعك.

## المتطلبات الأساسية

قبل أن ننتقل إلى الكود، تأكد من أن لديك ما يلي:

-  Aspose.Words for .NET: يمكنك تنزيله من[هنا](https://releases.aspose.com/words/net/).
- بيئة التطوير: أي بيئة تطوير متكاملة متوافقة مع .NET (على سبيل المثال، Visual Studio).
- المعرفة الأساسية بلغة C#: يفترض هذا البرنامج التعليمي أن لديك فهمًا أساسيًا لبرمجة C#.

## استيراد مساحات الأسماء

أولاً، دعنا نستورد مساحات الأسماء اللازمة لمشروعنا. سيضمن هذا إمكانية الوصول إلى جميع الفئات والطرق المطلوبة التي يوفرها Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

الآن، دعنا نقسم المثال إلى خطوات متعددة لمساعدتك على فهم كيفية تغيير مصدر ثقافة تحديث الحقل في Aspose.Words لـ .NET.

## الخطوة 1: تهيئة المستند

 الخطوة الأولى هي إنشاء مثيل جديد لـ`Document` الصف و أ`DocumentBuilder`يشكل هذا الأساس لبناء مستند Word الخاص بنا ومعالجته.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## الخطوة 2: إدراج الحقول ذات الإعدادات المحلية المحددة

بعد ذلك، نحتاج إلى إدراج حقول في المستند. في هذا المثال، سنقوم بإدراج حقلين للتاريخ. وسنضبط إعدادات الخط على اللغة الألمانية (LocaleId = 1031) لإظهار كيفية تأثير الثقافة على تنسيق التاريخ.

```csharp
builder.Font.LocaleId = 1031; // الألمانية
builder.InsertField("MERGEFIELD Date1 \\@ \"dddd, d MMMM yyyy\"");
builder.Write(" - ");
builder.InsertField("MERGEFIELD Date2 \\@ \"dddd, d MMMM yyyy\"");
```

## الخطوة 3: تعيين مصدر ثقافة تحديث الحقل

 للتحكم في الثقافة المستخدمة عند تحديث الحقول، قمنا بتعيين`FieldUpdateCultureSource` ممتلكات`FieldOptions`تحدد هذه الخاصية ما إذا كانت الثقافة مأخوذة من رمز الحقل أو المستند.

```csharp
doc.FieldOptions.FieldUpdateCultureSource = FieldUpdateCultureSource.FieldCode;
```

## الخطوة 4: تنفيذ دمج البريد

نحتاج الآن إلى تنفيذ دمج بريدي لملء الحقول بالبيانات الفعلية. في هذا المثال، سنقوم بتعيين حقل التاريخ الثاني (`Date2`) إلى 1 يناير 2011.

```csharp
doc.MailMerge.Execute(new string[] { "Date2" }, new object[] { new DateTime(2011, 1, 1) });
```

## الخطوة 5: احفظ المستند

وأخيرًا، نقوم بحفظ المستند في الدليل المحدد. تكتمل عملية تغيير مصدر ثقافة تحديث الحقل بهذه الخطوة.

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeFieldUpdateCultureSource.docx");
```

## خاتمة

والآن، لقد نجحت في تغيير مصدر ثقافة تحديث الحقل في Aspose.Words لـ .NET. باتباع هذه الخطوات، يمكنك التأكد من أن مستندات Word الخاصة بك تعرض التواريخ وقيم الحقول الأخرى وفقًا لإعدادات الثقافة المحددة. يمكن أن يكون هذا مفيدًا بشكل خاص عند إنشاء مستندات لجمهور دولي.

## الأسئلة الشائعة

###  ما هو الغرض من وضع`LocaleId`?
 ال`LocaleId` يحدد إعدادات الثقافة للنص، والتي تؤثر على كيفية تنسيق التواريخ والبيانات الأخرى الحساسة للموقع.

### هل يمكنني استخدام لغة محلية أخرى غير اللغة الألمانية؟
 نعم يمكنك ضبط`LocaleId`إلى أي معرف محلي صالح. على سبيل المثال، 1033 للغة الإنجليزية (الولايات المتحدة).

###  ماذا يحدث إذا لم أقم بتعيين`FieldUpdateCultureSource` property?
إذا لم يتم تعيين هذه الخاصية، فسيتم استخدام إعدادات الثقافة الافتراضية للمستند عند تحديث الحقول.

### هل من الممكن تحديث الحقول بناءً على ثقافة المستند بدلاً من رمز الحقل؟
 نعم يمكنك ضبط`FieldUpdateCultureSource` ل`FieldUpdateCultureSource.Document` لاستخدام إعدادات ثقافة المستند.

### كيف أقوم بتنسيق التواريخ بنمط مختلف؟
 يمكنك تغيير نمط تنسيق التاريخ في`InsertField` الطريقة عن طريق تعديل`\\@` قيمة التبديل.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
