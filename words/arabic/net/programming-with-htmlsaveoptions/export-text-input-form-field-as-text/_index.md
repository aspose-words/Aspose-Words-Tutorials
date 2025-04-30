---
"description": "تعرف على كيفية تصدير حقول نموذج إدخال النص كنص عادي باستخدام Aspose.Words لـ .NET باستخدام هذا الدليل الشامل خطوة بخطوة."
"linktitle": "تصدير حقل نموذج إدخال النص كنص"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "تصدير حقل نموذج إدخال النص كنص"
"url": "/ar/net/programming-with-htmlsaveoptions/export-text-input-form-field-as-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تصدير حقل نموذج إدخال النص كنص

## مقدمة

هل تغوص الآن في عالم Aspose.Words لـ .NET؟ خيار رائع! إذا كنت ترغب في تعلم كيفية تصدير حقل إدخال نص كنص، فأنت في المكان المناسب. سواء كنت مبتدئًا أو تُحسّن مهاراتك، سيرشدك هذا الدليل إلى كل ما تحتاج لمعرفته. هيا بنا نبدأ، أليس كذلك؟

## المتطلبات الأساسية

قبل أن نتعمق في التفاصيل، دعنا نتأكد من أن لديك كل ما تحتاجه لمتابعة الأمر بسلاسة:

- Aspose.Words for .NET: قم بتنزيل أحدث إصدار وتثبيته من [هنا](https://releases.aspose.com/words/net/).
- IDE: Visual Studio أو أي بيئة تطوير C#.
- المعرفة الأساسية بلغة C#: فهم قواعد اللغة الأساسية في لغة C# ومفاهيم البرمجة الموجهة للكائنات.
- المستند: نموذج مستند Word (`Rendering.docx`) مع حقول نموذج إدخال النص.

## استيراد مساحات الأسماء

أولاً، عليك استيراد مساحات الأسماء اللازمة. فهي بمثابة اللبنات الأساسية التي تضمن سلاسة العمل.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

حسنًا، الآن بعد أن أصبحت مساحات الأسماء جاهزة، فلننتقل إلى العمل!

## الخطوة 1: إعداد المشروع

قبل أن ندخل في الكود، دعونا نتأكد من إعداد مشروعنا بشكل صحيح.

## إنشاء المشروع

1. افتح Visual Studio: ابدأ بفتح Visual Studio أو بيئة تطوير C# المفضلة لديك.
2. إنشاء مشروع جديد: انتقل إلى `File > New > Project`يختار `Console App (.NET Core)` أو أي نوع آخر من المشاريع ذات الصلة.
3. تسمية مشروعك: امنح مشروعك اسمًا ذا معنى، مثل `AsposeWordsExportExample`.

## إضافة Aspose.Words

1. إدارة حزم NuGet: انقر بزر الماوس الأيمن على مشروعك في مستكشف الحلول وحدد `Manage NuGet Packages`.
2. ابحث عن Aspose.Words: في مدير الحزم NuGet، ابحث عن `Aspose.Words`.
3. تثبيت Aspose.Words: انقر فوق `Install` لإضافة مكتبة Aspose.Words إلى مشروعك.

## الخطوة 2: تحميل مستند Word

الآن بعد أن تم إعداد مشروعنا، فلنقم بتحميل مستند Word الذي يحتوي على حقول نموذج إدخال النص.

1. تحديد دليل المستند: قم بتحديد المسار إلى الدليل الذي يتم تخزين مستندك فيه.
2. تحميل المستند: استخدم `Document` الفئة لتحميل مستند Word الخاص بك.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

## الخطوة 3: إعداد دليل التصدير

قبل التصدير، تأكد من جاهزية مجلد التصدير. سيُحفظ ملف HTML والصور فيه.

1. تحديد دليل التصدير: حدد المسار الذي سيتم حفظ الملفات المصدرة فيه.
2. التحقق من الدليل وتنظيفه: تأكد من وجود الدليل وأنه فارغ.

```csharp
string imagesDir = Path.Combine(dataDir, "Images");

if (Directory.Exists(imagesDir))
    Directory.Delete(imagesDir, true);

Directory.CreateDirectory(imagesDir);
```

## الخطوة 4: تكوين خيارات الحفظ

هنا يكمن السر. علينا ضبط خيارات الحفظ لتصدير حقل نموذج إدخال النص كنص عادي.

1. إنشاء خيارات الحفظ: تهيئة خيار جديد `HtmlSaveOptions` هدف.
2. تعيين خيار تصدير النص: تكوين `ExportTextInputFormFieldAsText` الممتلكات إلى `true`.
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
2. حفظ المستند: استخدم `Save` طريقة `Document` الفئة لتصدير المستند.

```csharp
doc.Save(dataDir + "ExportedDocument.html", saveOptions);
```

## خاتمة

وها قد انتهيت! لقد نجحت في تصدير حقل إدخال نص كنص عادي باستخدام Aspose.Words لـ .NET. يُفترض أن يكون هذا الدليل قد قدّم لك نهجًا واضحًا وخطوة بخطوة لتحقيق هذه المهمة. تذكر، الممارسة تصنع الإتقان، لذا استمر في تجربة خيارات وإعدادات مختلفة لاكتشاف ما يمكنك فعله أيضًا باستخدام Aspose.Words.

## الأسئلة الشائعة

### هل يمكنني تصدير أنواع أخرى من حقول النماذج باستخدام نفس الطريقة؟

نعم، يمكنك تصدير أنواع أخرى من حقول النماذج عن طريق تكوين خصائص مختلفة لـ `HtmlSaveOptions` فصل.

### ماذا لو كانت مستندي تحتوي على صور؟

سيتم حفظ الصور في مجلد الصور المحدد. تأكد من ضبط `ImagesFolder` الممتلكات في `HtmlSaveOptions`.

### هل أحتاج إلى ترخيص لـ Aspose.Words؟

نعم، يمكنك الحصول على نسخة تجريبية مجانية [هنا](https://releases.aspose.com/) أو شراء ترخيص [هنا](https://purchase.aspose.com/buy).

### هل يمكنني تخصيص HTML المُصدَّر؟

بالتأكيد! يوفر Aspose.Words خيارات متنوعة لتخصيص مخرجات HTML. راجع [التوثيق](https://reference.aspose.com/words/net/) لمزيد من التفاصيل.

### هل Aspose.Words متوافق مع .NET Core؟

نعم، Aspose.Words متوافق مع .NET Core، و.NET Framework، ومنصات .NET الأخرى.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}