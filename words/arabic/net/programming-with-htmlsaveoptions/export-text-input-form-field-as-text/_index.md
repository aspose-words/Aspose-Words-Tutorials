---
title: تصدير حقل إدخال النص في النموذج كنص
linktitle: تصدير حقل إدخال النص في النموذج كنص
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية تصدير حقول نموذج إدخال النص كنص عادي باستخدام Aspose.Words لـ .NET باستخدام هذا الدليل الشامل خطوة بخطوة.
weight: 10
url: /ar/net/programming-with-htmlsaveoptions/export-text-input-form-field-as-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تصدير حقل إدخال النص في النموذج كنص

## مقدمة

إذن، هل تغوص في عالم Aspose.Words لـ .NET؟ اختيار رائع! إذا كنت تتطلع إلى تعلم كيفية تصدير حقل نموذج إدخال نص كنص، فأنت في المكان المناسب. سواء كنت مبتدئًا أو تصقل مهاراتك، فسيرشدك هذا الدليل إلى كل ما تحتاج إلى معرفته. لنبدأ، أليس كذلك؟

## المتطلبات الأساسية

قبل أن نتعمق في التفاصيل، دعنا نتأكد من أن لديك كل ما تحتاجه لمتابعة الأمر بسلاسة:

-  Aspose.Words for .NET: قم بتنزيل أحدث إصدار وتثبيته من[هنا](https://releases.aspose.com/words/net/).
- IDE: Visual Studio أو أي بيئة تطوير C#.
- المعرفة الأساسية بلغة C#: فهم قواعد لغة C# الأساسية ومفاهيم البرمجة الموجهة للكائنات.
- المستند: نموذج مستند Word (`Rendering.docx`) مع حقول نموذج إدخال النص.

## استيراد مساحات الأسماء

أولاً وقبل كل شيء، عليك استيراد مساحات الأسماء الضرورية. فهي بمثابة اللبنات الأساسية التي تجعل كل شيء يعمل بسلاسة.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

حسنًا، الآن بعد أن أصبحت مساحات الأسماء الخاصة بنا جاهزة، فلننتقل إلى العمل!

## الخطوة 1: إعداد المشروع

قبل أن ندخل في الكود، دعونا نتأكد من إعداد مشروعنا بشكل صحيح.

## إنشاء المشروع

1. افتح Visual Studio: ابدأ بفتح Visual Studio أو بيئة تطوير C# المفضلة لديك.
2.  إنشاء مشروع جديد: انتقل إلى`File > New > Project` . يختار`Console App (.NET Core)` أو أي نوع آخر من المشاريع ذات الصلة.
3.  اسم مشروعك: أعط مشروعك اسمًا ذا معنى، مثل`AsposeWordsExportExample`.

## إضافة Aspose.Words

1.  إدارة حزم NuGet: انقر بزر الماوس الأيمن على مشروعك في مستكشف الحلول وحدد`Manage NuGet Packages`.
2.  البحث عن Aspose.Words: في مدير الحزم NuGet، ابحث عن`Aspose.Words`.
3.  تثبيت Aspose.Words: انقر فوق`Install` لإضافة مكتبة Aspose.Words إلى مشروعك.

## الخطوة 2: تحميل مستند Word

الآن بعد أن تم إعداد مشروعنا، فلنقم بتحميل مستند Word الذي يحتوي على حقول نموذج إدخال النص.

1. تحديد دليل المستند: قم بتحديد المسار إلى الدليل الذي يتم تخزين مستندك فيه.
2.  تحميل المستند: استخدم`Document` الفئة لتحميل مستند Word الخاص بك.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

## الخطوة 3: إعداد دليل التصدير

قبل التصدير، دعنا نتأكد من أن دليل التصدير جاهز. هذا هو المكان الذي سيتم فيه حفظ ملف HTML والصور.

1. تحديد دليل التصدير: حدد المسار الذي سيتم حفظ الملفات المصدرة فيه.
2. التحقق من الدليل وتنظيفه: تأكد من وجود الدليل وأنه فارغ.

```csharp
string imagesDir = Path.Combine(dataDir, "Images");

if (Directory.Exists(imagesDir))
    Directory.Delete(imagesDir, true);

Directory.CreateDirectory(imagesDir);
```

## الخطوة 4: تكوين خيارات الحفظ

وهنا يحدث السحر. نحتاج إلى إعداد خيارات الحفظ لتصدير حقل نموذج إدخال النص كنص عادي.

1.  إنشاء خيارات الحفظ: تهيئة خيار جديد`HtmlSaveOptions` هدف.
2.  تعيين خيار تصدير النص: قم بتكوين`ExportTextInputFormFieldAsText`الممتلكات ل`true`.
3. تعيين مجلد الصور: قم بتحديد المجلد الذي سيتم حفظ الصور فيه.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    ExportTextInputFormFieldAsText = true,
    ImagesFolder = imagesDir
};
```

## الخطوة 5: حفظ المستند بصيغة HTML

أخيرًا، دعنا نحفظ مستند Word كملف HTML باستخدام خيارات الحفظ التي قمنا بتكوينها.

1. تحديد مسار الإخراج: حدد المسار الذي سيتم حفظ ملف HTML فيه.
2.  حفظ المستند: استخدم`Save` طريقة`Document`الفئة لتصدير المستند.

```csharp
doc.Save(dataDir + "ExportedDocument.html", saveOptions);
```

## خاتمة

والآن، لقد نجحت في تصدير حقل نموذج إدخال نص كنص عادي باستخدام Aspose.Words for .NET. من المفترض أن يمنحك هذا الدليل نهجًا واضحًا خطوة بخطوة لتحقيق هذه المهمة. تذكر أن الممارسة تؤدي إلى الإتقان، لذا استمر في تجربة خيارات وإعدادات مختلفة لمعرفة ما يمكنك فعله باستخدام Aspose.Words.

## الأسئلة الشائعة

### هل يمكنني تصدير أنواع أخرى من حقول النموذج باستخدام نفس الطريقة؟

 نعم، يمكنك تصدير أنواع أخرى من حقول النموذج عن طريق تكوين خصائص مختلفة لـ`HtmlSaveOptions` فصل.

### ماذا لو كانت مستندي تحتوي على صور؟

 سيتم حفظ الصور في مجلد الصور المحدد. تأكد من ضبط`ImagesFolder` الممتلكات في`HtmlSaveOptions`.

### هل أحتاج إلى ترخيص لـ Aspose.Words؟

 نعم، يمكنك الحصول على نسخة تجريبية مجانية[هنا](https://releases.aspose.com/) أو شراء ترخيص[هنا](https://purchase.aspose.com/buy).

### هل يمكنني تخصيص HTML المُصدر؟

 بالتأكيد! يوفر Aspose.Words خيارات متنوعة لتخصيص مخرجات HTML. راجع[التوثيق](https://reference.aspose.com/words/net/) لمزيد من التفاصيل.

### هل Aspose.Words متوافق مع .NET Core؟

نعم، Aspose.Words متوافق مع .NET Core، و.NET Framework، ومنصات .NET الأخرى.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
