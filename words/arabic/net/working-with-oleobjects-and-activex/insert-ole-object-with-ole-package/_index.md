---
"description": "تعرّف على كيفية إدراج كائنات OLE في مستندات Word باستخدام Aspose.Words لـ .NET. اتبع دليلنا المفصل خطوة بخطوة لتضمين الملفات بسلاسة."
"linktitle": "إدراج كائن Ole في Word باستخدام حزمة Ole"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "إدراج كائن Ole في Word باستخدام حزمة Ole"
"url": "/ar/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إدراج كائن Ole في Word باستخدام حزمة Ole

## مقدمة

إذا كنت ترغب يومًا بتضمين ملف في مستند وورد، فأنت في المكان المناسب. سواءً كان ملف ZIP أو جدول بيانات Excel أو أي نوع ملف آخر، فإن تضمينه مباشرةً في مستند وورد مفيدٌ للغاية. تخيل الأمر وكأنه خزنة سرية في مستندك تخزن فيها كنوزًا لا تُحصى. واليوم، سنشرح كيفية القيام بذلك باستخدام Aspose.Words لـ .NET. هل أنت مستعد لتصبح خبيرًا في وورد؟ هيا بنا!

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

1. Aspose.Words لـ .NET: إذا لم تقم بتنزيله بالفعل، فقم بتنزيله من [هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: Visual Studio أو أي بيئة تطوير .NET أخرى.
3. الفهم الأساسي للغة C#: لا تحتاج إلى أن تكون خبيرًا، ولكن معرفة طريقتك في التعامل مع لغة C# سوف تساعدك.
4. دليل المستندات: مجلد يمكنك تخزين المستندات واسترجاعها فيه.

## استيراد مساحات الأسماء

أولاً، لنرتب مساحات الأسماء. عليك تضمين المساحات التالية في مشروعك:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
```

دعونا نقسم هذا إلى خطوات صغيرة الحجم، حتى يكون من السهل متابعتها.

## الخطوة 1: إعداد مستندك

تخيّل أنك فنانٌ أمام لوحةٍ بيضاء. أولًا، نحتاج إلى لوحةٍ بيضاء، وهي مستند وورد. إليك كيفية إعدادها:

```csharp
// المسار إلى دليل المستندات الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

يقوم هذا الكود بتهيئة مستند Word جديد وإعداد DocumentBuilder، والذي سنستخدمه لإدراج المحتوى في مستندنا.

## الخطوة 2: قراءة كائنك القديم

الآن، لنقرأ الملف الذي تريد تضمينه. تخيل هذا كأنك تلتقط الكنز الذي تريد إخفاؤه في حجرتك السرية:

```csharp
byte[] bs = File.ReadAllBytes(dataDir + "Zip file.zip");
```

يقوم هذا السطر بقراءة كافة البايتات من ملف ZIP الخاص بك ويخزنها في مجموعة بايتات.

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

هنا، نقوم بإنشاء مجرى ذاكرة من مجموعة البايتات واستخدام `InsertOleObject` طريقة تضمينه في المستند. كما حددنا اسم الملف واسم العرض للكائن المُضمّن.

## الخطوة 4: احفظ مستندك

وأخيرًا، دعونا نحفظ تحفتنا الفنية:

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
```

يؤدي هذا إلى حفظ المستند مع الملف المضمن في الدليل المحدد.

## خاتمة

وها قد انتهيت! لقد نجحت في تضمين كائن OLE في مستند Word باستخدام Aspose.Words لـ .NET. الأمر أشبه بإضافة جوهرة مخفية داخل مستندك، يمكنك الوصول إليها في أي وقت. هذه التقنية مفيدة للغاية في تطبيقات متنوعة، من التوثيق الفني إلى التقارير الديناميكية. 

## الأسئلة الشائعة

### هل يمكنني تضمين أنواع ملفات أخرى باستخدام هذه الطريقة؟
نعم، يمكنك تضمين أنواع مختلفة من الملفات مثل جداول بيانات Excel وملفات PDF والصور.

### هل أحتاج إلى ترخيص لـ Aspose.Words؟
نعم، تحتاج إلى رخصة سارية المفعول. يمكنك الحصول على [رخصة مؤقتة](https://purchase.aspose.com/temporary-license/) للتقييم.

### كيف يمكنني تخصيص اسم العرض لكائن OLE؟
يمكنك ضبط `DisplayName` ممتلكات `OlePackage` لتخصيصه.

### هل Aspose.Words متوافق مع .NET Core؟
نعم، يدعم Aspose.Words كل من .NET Framework و.NET Core.

### هل يمكنني تحرير كائن OLE المضمن داخل مستند Word؟
لا، لا يمكنك تعديل كائن OLE مباشرةً داخل Word. يجب فتحه في تطبيقه الأصلي.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}