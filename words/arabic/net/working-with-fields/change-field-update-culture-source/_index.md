---
"description": "تعرّف على كيفية تغيير مصدر ثقافة تحديث الحقل في Aspose.Words لـ .NET باستخدام هذا الدليل. تحكّم بسهولة في تنسيق التاريخ بناءً على ثقافات مختلفة."
"linktitle": "تغيير مصدر تحديث ثقافة الحقل"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "تغيير مصدر تحديث ثقافة الحقل"
"url": "/ar/net/working-with-fields/change-field-update-culture-source/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تغيير مصدر تحديث ثقافة الحقل

## مقدمة

في هذا البرنامج التعليمي، سنتعمق في عالم Aspose.Words لـ .NET ونستكشف كيفية تغيير مصدر ثقافة تحديث الحقول. إذا كنت تتعامل مع مستندات Word تتضمن حقول تواريخ وتحتاج إلى التحكم في تنسيق هذه التواريخ بناءً على ثقافات مختلفة، فهذا الدليل مناسب لك. سنشرح العملية خطوة بخطوة، لضمان فهمك لكل مفهوم وتطبيقه بفعالية في مشاريعك.

## المتطلبات الأساسية

قبل أن ننتقل إلى الكود، تأكد من أن لديك ما يلي:

- Aspose.Words for .NET: يمكنك تنزيله من [هنا](https://releases.aspose.com/words/net/).
- بيئة التطوير: أي بيئة تطوير متكاملة متوافقة مع .NET (على سبيل المثال، Visual Studio).
- المعرفة الأساسية بلغة C#: يفترض هذا البرنامج التعليمي أن لديك فهمًا أساسيًا لبرمجة C#.

## استيراد مساحات الأسماء

أولاً، لنستورد مساحات الأسماء اللازمة لمشروعنا. سيضمن هذا وصولنا إلى جميع الفئات والأساليب المطلوبة التي يوفرها Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

الآن، دعنا نقسم المثال إلى خطوات متعددة لمساعدتك على فهم كيفية تغيير مصدر ثقافة تحديث الحقل في Aspose.Words لـ .NET.

## الخطوة 1: تهيئة المستند

الخطوة الأولى هي إنشاء مثيل جديد لـ `Document` الصف و `DocumentBuilder`. وهذا يضع الأساس لبناء ومعالجة مستند Word الخاص بنا.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## الخطوة 2: إدراج الحقول ذات الإعدادات المحلية المحددة

بعد ذلك، علينا إدراج حقول في المستند. في هذا المثال، سندرج حقلي تاريخ. سنضبط لغة الخط على الألمانية (LocaleId = 1031) لتوضيح تأثير الثقافة على تنسيق التاريخ.

```csharp
builder.Font.LocaleId = 1031; // الألمانية
builder.InsertField("MERGEFIELD Date1 \\@ \"dddd, d MMMM yyyy\"");
builder.Write(" - ");
builder.InsertField("MERGEFIELD Date2 \\@ \"dddd, d MMMM yyyy\"");
```

## الخطوة 3: تعيين مصدر ثقافة تحديث الحقل

للتحكم في الثقافة المستخدمة عند تحديث الحقول، قمنا بتعيين `FieldUpdateCultureSource` ممتلكات `FieldOptions` تحدد هذه الخاصية ما إذا كانت الثقافة مأخوذة من رمز الحقل أو المستند.

```csharp
doc.FieldOptions.FieldUpdateCultureSource = FieldUpdateCultureSource.FieldCode;
```

## الخطوة 4: تنفيذ دمج البريد

نحتاج الآن إلى تنفيذ دمج بريدي لملء الحقول بالبيانات الفعلية. في هذا المثال، سنضبط حقل التاريخ الثاني (`Date2`) إلى 1 يناير 2011.

```csharp
doc.MailMerge.Execute(new string[] { "Date2" }, new object[] { new DateTime(2011, 1, 1) });
```

## الخطوة 5: حفظ المستند

أخيرًا، نحفظ المستند في المجلد المحدد. تُكمل هذه الخطوة عملية تغيير مصدر ثقافة تحديث الحقل.

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeFieldUpdateCultureSource.docx");
```

## خاتمة

ها قد انتهيت! لقد نجحت في تغيير مصدر ثقافة تحديث الحقول في Aspose.Words لـ .NET. باتباع هذه الخطوات، يمكنك ضمان عرض مستندات Word للتواريخ وقيم الحقول الأخرى وفقًا لإعدادات الثقافة المحددة. يُعد هذا مفيدًا بشكل خاص عند إنشاء مستندات لجمهور دولي.

## الأسئلة الشائعة

### ما هو الغرض من وضع `LocaleId`؟
ال `LocaleId` يحدد إعدادات الثقافة للنص، والتي تؤثر على كيفية تنسيق التواريخ والبيانات الحساسة للموقع.

### هل يمكنني استخدام لغة محلية أخرى غير اللغة الألمانية؟
نعم يمكنك ضبط `LocaleId` لأي مُعرِّف محلي صالح. على سبيل المثال، 1033 للغة الإنجليزية (الولايات المتحدة).

### ماذا يحدث إذا لم أقم بتعيين `FieldUpdateCultureSource` ملكية؟
إذا لم يتم تعيين هذه الخاصية، فسيتم استخدام إعدادات الثقافة الافتراضية للمستند عند تحديث الحقول.

### هل من الممكن تحديث الحقول بناءً على ثقافة المستند بدلاً من رمز الحقل؟
نعم يمكنك ضبط `FieldUpdateCultureSource` ل `FieldUpdateCultureSource.Document` لاستخدام إعدادات ثقافة المستند.

### كيف أقوم بتنسيق التواريخ بنمط مختلف؟
يمكنك تغيير نمط تنسيق التاريخ في `InsertField` الطريقة عن طريق تعديل `\\@` قيمة التبديل.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}