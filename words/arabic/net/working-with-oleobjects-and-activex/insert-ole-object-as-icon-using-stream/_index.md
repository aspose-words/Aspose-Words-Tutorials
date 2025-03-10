---
title: إدراج كائن Ole كأيقونة باستخدام Stream
linktitle: إدراج كائن Ole كأيقونة باستخدام Stream
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إدراج كائن OLE كأيقونة باستخدام دفق مع Aspose.Words لـ .NET في هذا البرنامج التعليمي المفصل خطوة بخطوة.
weight: 10
url: /ar/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon-using-stream/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إدراج كائن Ole كأيقونة باستخدام Stream

## مقدمة

في هذا البرنامج التعليمي، سنتعرف على ميزة رائعة للغاية في Aspose.Words for .NET: إدراج كائن OLE (ربط الكائنات وتضمينها) كأيقونة باستخدام دفق. سواء كنت تقوم بتضمين عرض تقديمي في PowerPoint أو جدول بيانات Excel أو أي نوع آخر من الملفات، فسيوضح لك هذا الدليل كيفية القيام بذلك بالضبط. هل أنت مستعد للبدء؟ هيا بنا!

## المتطلبات الأساسية

قبل أن ننتقل إلى الكود، هناك بعض الأشياء التي ستحتاجها:

-  Aspose.Words لـ .NET: إذا لم تقم بذلك بالفعل،[تحميل](https://releases.aspose.com/words/net/) وتثبيت Aspose.Words لـ .NET.
- بيئة التطوير: Visual Studio أو أي بيئة تطوير C# أخرى.
- ملفات الإدخال: الملف الذي تريد تضمينه (على سبيل المثال، عرض تقديمي لـ PowerPoint) وصورة الرمز.

## استيراد مساحات الأسماء

للبدء، تأكد من استيراد المساحات الأساسية اللازمة في مشروعك:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
```

دعونا نقوم بتقسيم العملية خطوة بخطوة لتسهيل متابعتها.

## الخطوة 1: إنشاء مستند جديد

أولاً، سنقوم بإنشاء مستند جديد ومنشئ مستندات للعمل معه.

```csharp
// المسار إلى دليل المستند الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 فكر في`Document` كقماشتك الفارغة و`DocumentBuilder` كفرشاة الرسم الخاصة بك. نقوم بإعداد أدواتنا لبدء إنشاء تحفتنا الفنية.

## الخطوة 2: تحضير البث

بعد ذلك، نحتاج إلى إعداد مجرى ذاكرة يحتوي على الملف الذي نريد تضمينه. في هذا المثال، سنقوم بتضمين عرض تقديمي على PowerPoint.

```csharp
using (MemoryStream stream = new MemoryStream(File.ReadAllBytes("Path_to_your_directory/Presentation.pptx")))
{
```

هذه الخطوة تشبه تحميل الطلاء على الفرشاة. نقوم بتجهيز الملف للتضمين.

## الخطوة 3: إدراج كائن OLE كأيقونة

الآن، سنستخدم منشئ المستندات لإدراج كائن OLE في المستند. سنحدد مجرى الملف، ومعرف البرنامج لنوع الملف (في هذه الحالة، "الحزمة")، والمسار إلى صورة الرمز، وعلامة للملف المضمّن.

```csharp
builder.InsertOleObjectAsIcon(stream, "Package", "Path_to_your_directory/Logo icon.ico", "My embedded file");
}
```

وهنا يحدث السحر! نقوم بتضمين ملفنا وعرضه كأيقونة داخل المستند.

## الخطوة 4: حفظ المستند

وأخيرًا، نحفظ المستند في المسار المحدد.

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectAsIconUsingStream.docx");
```

هذه الخطوة تشبه وضع اللوحة النهائية في إطار وتعليقها على الحائط. الآن أصبحت مستنداتك جاهزة للاستخدام!

## خاتمة

والآن، لقد نجحت في تضمين كائن OLE كأيقونة في مستند Word باستخدام Aspose.Words for .NET. يمكن أن تساعدك هذه الميزة القوية في إنشاء مستندات ديناميكية وتفاعلية بسهولة. سواء كنت تقوم بتضمين عروض تقديمية أو جداول بيانات أو ملفات أخرى، فإن Aspose.Words يجعل الأمر سهلاً للغاية. لذا، جرّبه وشاهد الفرق الذي يمكن أن يحدثه في مستنداتك!

## الأسئلة الشائعة

### هل يمكنني تضمين أنواع مختلفة من الملفات باستخدام هذه الطريقة؟
نعم، يمكنك تضمين أي نوع ملف يدعمه OLE، بما في ذلك Word وExcel وPowerPoint والمزيد.

### هل أحتاج إلى ترخيص خاص لاستخدام Aspose.Words لـ .NET؟
 نعم، يتطلب Aspose.Words for .NET ترخيصًا. يمكنك الحصول على ترخيص[نسخة تجريبية مجانية](https://releases.aspose.com/) أو شراء[رخصة مؤقتة](https://purchase.aspose.com/temporary-license/) للاختبار.

### هل يمكنني تخصيص الأيقونة المستخدمة لكائن OLE؟
 بالتأكيد! يمكنك استخدام أي ملف صورة للأيقونة من خلال تحديد مساره في`InsertOleObjectAsIcon` طريقة.

### ماذا يحدث إذا كانت مسارات الملف أو الرمز غير صحيحة؟
ستؤدي هذه الطريقة إلى حدوث استثناء. تأكد من صحة مسارات الملفات لتجنب الأخطاء.

### هل من الممكن ربط الكائن المضمن بدلا من تضمينه؟
نعم، يسمح لك Aspose.Words بإدراج كائنات OLE مرتبطة، والتي تشير إلى الملف دون تضمين محتواه.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
