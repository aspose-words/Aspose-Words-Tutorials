---
"description": "تعرف على كيفية إدراج حقول الدمج وتكوينها في مستندات Word باستخدام Aspose.Words لـ .NET من خلال هذا البرنامج التعليمي الشامل خطوة بخطوة."
"linktitle": "إدراج حقل الدمج باستخدام DOM"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "إدراج حقل الدمج باستخدام DOM"
"url": "/ar/net/working-with-fields/insert-merge-field-using-dom/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إدراج حقل الدمج باستخدام DOM

## مقدمة

إذا كنت تعمل على معالجة المستندات في .NET، فربما صادفت Aspose.Words. توفر هذه المكتبة القوية مجموعة واسعة من الميزات لمعالجة مستندات Word برمجيًا. في هذا البرنامج التعليمي، سنركز على ميزة محددة: إدراج حقل دمج باستخدام نموذج كائن المستند (DOM) في Aspose.Words لـ .NET. سيرشدك هذا الدليل خلال كل خطوة، من إعداد بيئتك إلى إدراج حقل دمج وتحديثه في مستند Word.

## المتطلبات الأساسية

قبل الغوص في الكود، دعنا نتأكد من أن لديك كل ما تحتاجه لمتابعة هذا البرنامج التعليمي.

1. المعرفة الأساسية بلغة C#: يجب أن تكون مرتاحًا في برمجة C#.
2. تم تثبيت Visual Studio: تأكد من تثبيت Visual Studio أو أي C# IDE آخر على جهازك.
3. Aspose.Words لـ .NET: قم بتنزيل أحدث إصدار من Aspose.Words لـ .NET وتثبيته من [الإصدارات](https://releases.aspose.com/words/net/).
4. رخصة صالحة: إذا لم يكن لديك ترخيص، يمكنك الحصول على [رخصة مؤقتة](https://purchase.aspose.com/temporary-license/) للتقييم.

## الخطوة 1: إعداد مشروعك

أولاً وقبل كل شيء، دعنا نقوم بإعداد مشروع جديد في Visual Studio.

1. افتح Visual Studio.
2. أنشئ مشروعًا جديدًا: انتقل إلى ملف > جديد > مشروع. اختر تطبيق وحدة تحكم C#.
3. قم بتسمية مشروعك: قم بإعطاء مشروعك اسمًا ذا معنى وانقر فوق "إنشاء".

## الخطوة 2: تثبيت Aspose.Words

لاستخدام Aspose.Words، عليك إضافته إلى مشروعك. يمكنك القيام بذلك عبر مدير الحزم NuGet.

1. افتح مدير حزم NuGet: انقر بزر الماوس الأيمن فوق مشروعك في مستكشف الحلول، ثم حدد إدارة حزم NuGet.
2. ابحث عن Aspose.Words: في مدير الحزم NuGet، ابحث عن "Aspose.Words".
3. تثبيت الحزمة: انقر فوق "تثبيت" لإضافة Aspose.Words إلى مشروعك.

## الخطوة 3: استيراد مساحات الأسماء

لبدء استخدام Aspose.Words، عليك استيراد مساحات الأسماء اللازمة إلى مشروعك. إليك كيفية القيام بذلك:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

## الخطوة 4: تهيئة مستندك

الآن بعد إعداد كل شيء، دعنا نقوم بإنشاء مستند Word جديد ونقوم بتشغيل DocumentBuilder.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// إنشاء المستند و DocumentBuilder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## الخطوة 5: نقل المؤشر إلى فقرة محددة

بعد ذلك، نحتاج إلى نقل المؤشر إلى فقرة محددة في المستند حيث نريد إدراج حقل الدمج.

```csharp
Paragraph para = (Paragraph) doc.GetChild(NodeType.Paragraph, 0, true);
builder.MoveTo(para);
```

## الخطوة 6: إدراج حقل الدمج

إدراج حقل دمج أمر سهل. سنستخدم `InsertField` طريقة `DocumentBuilder` فصل.

```csharp
// إدراج حقل دمج الحقل.
FieldMergeField field = (FieldMergeField)builder.InsertField(FieldType.FieldMergeField, false);
```

## الخطوة 7: تكوين حقل الدمج

بعد إدراج حقل الدمج، يمكنك تعيين خصائص مختلفة لتكوينه وفقًا لاحتياجاتك.

```csharp
field.FieldName = "Test1";
field.TextBefore = "Test2";
field.TextAfter = "Test3";
field.IsMapped = true;
field.IsVerticalFormatting = true;
```

## الخطوة 8: تحديث المستند وحفظه

وأخيرًا، قم بتحديث الحقل للتأكد من تطبيق كافة الإعدادات وحفظ المستند.

```csharp
// تحديث المجال.
field.Update();

// احفظ المستند.
doc.Save(dataDir + "InsertionChampMergeChamp.docx");
```

## خاتمة

باتباع هذه الخطوات، يمكنك بسهولة إدراج وتكوين حقول الدمج في مستند Word باستخدام Aspose.Words لـ .NET. غطّى هذا البرنامج التعليمي الخطوات الأساسية، بدءًا من إعداد بيئتك وحتى حفظ المستند النهائي. باستخدام Aspose.Words، يمكنك أتمتة مهام معالجة المستندات المعقدة، مما يزيد من قوة وكفاءة تطبيقات .NET.

## الأسئلة الشائعة

###  ما هو حقل الدمج؟
حقل الدمج هو عنصر نائب في مستند يمكن استبداله ديناميكيًا ببيانات من مصدر بيانات، مثل قاعدة بيانات أو ملف CSV.

###  هل يمكنني استخدام Aspose.Words مجانًا؟
يقدم Aspose.Words نسخة تجريبية مجانية يمكنك تنزيلها [هنا](https://releases.aspose.com/)للاستخدام طويل الأمد، ستحتاج إلى شراء ترخيص.

###  كيف أحصل على ترخيص مؤقت لـ Aspose.Words؟
يمكنك الحصول على ترخيص مؤقت من موقع Aspose [هنا](https://purchase.aspose.com/temporary-license/).

### ما هي إصدارات .NET التي يدعمها Aspose.Words؟
يدعم Aspose.Words إصدارات متعددة من .NET، بما في ذلك .NET Framework، و.NET Core، و.NET Standard.

###  أين يمكنني العثور على وثائق API الخاصة بـ Aspose.Words؟
وثائق API متاحة [هنا](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}