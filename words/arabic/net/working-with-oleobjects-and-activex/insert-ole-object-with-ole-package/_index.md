---
title: إدراج كائن Ole في Word باستخدام حزمة Ole
linktitle: إدراج كائن Ole في Word باستخدام حزمة Ole
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إدراج كائنات OLE في مستندات Word باستخدام Aspose.Words for .NET. اتبع دليلنا المفصل خطوة بخطوة لتضمين الملفات بسلاسة.
weight: 10
url: /ar/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إدراج كائن Ole في Word باستخدام حزمة Ole

## مقدمة

إذا كنت ترغب في تضمين ملف في مستند Word، فأنت في المكان المناسب. سواء كان ملف ZIP أو جدول بيانات Excel أو أي نوع آخر من الملفات، فإن تضمينه مباشرة في مستند Word الخاص بك يمكن أن يكون مفيدًا بشكل لا يصدق. فكر في الأمر كما لو كان لديك حجرة سرية في مستندك حيث يمكنك تخزين جميع أنواع الكنوز. واليوم، سنشرح كيفية القيام بذلك باستخدام Aspose.Words for .NET. هل أنت مستعد لتصبح معالج Word؟ دعنا نتعمق!

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

1. Aspose.Words for .NET: إذا لم تقم بتنزيله بالفعل، فقم بتنزيله من[هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: Visual Studio أو أي بيئة تطوير .NET أخرى.
3. الفهم الأساسي للغة C#: ليس عليك أن تكون خبيرًا، ولكن معرفة كيفية التعامل مع لغة C# سوف يساعدك.
4. دليل المستندات: مجلد يمكنك تخزين المستندات واسترجاعها فيه.

## استيراد مساحات الأسماء

أولاً وقبل كل شيء، دعنا نرتب مساحات الأسماء الخاصة بنا. تحتاج إلى تضمين مساحات الأسماء التالية في مشروعك:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
```

دعونا نقسم هذا إلى خطوات صغيرة الحجم، حتى يكون من السهل متابعتها.

## الخطوة 1: إعداد المستند الخاص بك

تخيل أنك فنان ولديك لوحة قماشية فارغة. أولاً، نحتاج إلى لوحة قماشية فارغة، وهي مستند Word الخاص بنا. وإليك كيفية إعدادها:

```csharp
// المسار إلى دليل المستند الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

يقوم هذا الكود بتهيئة مستند Word جديد وإعداد DocumentBuilder، والذي سنستخدمه لإدراج المحتوى في مستندنا.

## الخطوة 2: قراءة الكائن القديم الخاص بك

بعد ذلك، دعنا نقرأ الملف الذي تريد تضمينه. فكر في هذا الأمر كأنك تلتقط الكنز الذي تريد إخفاءه في حجرتك السرية:

```csharp
byte[] bs = File.ReadAllBytes(dataDir + "Zip file.zip");
```

يقوم هذا السطر بقراءة جميع البايتات من ملف ZIP الخاص بك ويخزنها في مجموعة بايتات.

## الخطوة 3: إدراج كائن Ole

الآن يأتي الجزء السحري. سنقوم بتضمين الملف في مستند Word الخاص بنا:

```csharp
using (Stream stream = new MemoryStream(bs))
{
    Shape shape = builder.InsertOleObject(stream, "Package", true, null);
    OlePackage olePackage = shape.OleFormat.OlePackage;
    olePackage.FileName = "filename.zip";
    olePackage.DisplayName = "displayname.zip";
}
```

 هنا، نقوم بإنشاء مجرى ذاكرة من مجموعة البايتات واستخدام`InsertOleObject` الطريقة لتضمينها في المستند. كما قمنا أيضًا بتعيين اسم الملف واسم العرض للكائن المضمن.

## الخطوة 4: احفظ مستندك

وأخيرا، دعونا نحفظ تحفتنا الفنية:

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
```

يؤدي هذا إلى حفظ المستند بالملف المضمن في الدليل المحدد.

## خاتمة

والآن، لقد نجحت في تضمين كائن OLE في مستند Word باستخدام Aspose.Words for .NET. الأمر أشبه بإضافة جوهرة مخفية داخل المستند يمكن الكشف عنها في أي وقت. يمكن أن تكون هذه التقنية مفيدة بشكل لا يصدق لمجموعة متنوعة من التطبيقات، من الوثائق الفنية إلى التقارير الديناميكية. 

## الأسئلة الشائعة

### هل يمكنني تضمين أنواع ملفات أخرى باستخدام هذه الطريقة؟
نعم، يمكنك تضمين أنواع مختلفة من الملفات مثل جداول Excel، وملفات PDF، والصور.

### هل أحتاج إلى ترخيص لـ Aspose.Words؟
 نعم، تحتاج إلى ترخيص صالح. يمكنك الحصول على[رخصة مؤقتة](https://purchase.aspose.com/temporary-license/) للتقييم.

### كيف يمكنني تخصيص اسم العرض الخاص بكائن OLE؟
 يمكنك ضبط`DisplayName` ممتلكات`OlePackage` لتخصيصه.

### هل Aspose.Words متوافق مع .NET Core؟
نعم، يدعم Aspose.Words كلاً من .NET Framework و.NET Core.

### هل يمكنني تحرير كائن OLE المضمن داخل مستند Word؟
لا، لا يمكنك تحرير كائن OLE مباشرةً داخل Word. يجب عليك فتحه في تطبيقه الأصلي.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
