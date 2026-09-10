---
title: إدراج حقل TC في مستند Word باستخدام Aspose.Words for .NET
weight: 110
limit:
description: تعلم كيفية إدراج حقل TC بنص مخصص في مستند Word باستخدام Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert TC field, TC field Word, DocumentBuilder TC field, Word document index, table of contents field]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إدراج حقل TC في مستند Word باستخدام Aspose.Words
يوضح هذا البرنامج التعليمي كيفية استخدام Aspose.Words for .NET لإدراج حقل TC (جدول المحتويات) في مستند Word تم إنشاؤه حديثًا. باستخدام DocumentBuilder يمكنك إضافة حقل TC بنص إدخال مخصص، وهو مفيد لإنشاء فهرس قابل للبحث لجدول المحتويات. كما يُظهر المثال حفظ المستند على القرص.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-tc-field" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: ماذا يعني المفتاح "\f t" في شفرة حقل TC؟**
A: المفتاح "\f t" يُخبر Word بمعاملة الإدخال كإدخال جدول، مما يجعله يظهر في جدول المحتويات المُولد باستخدام المفتاح \f.

**Q: كيف يمكنني تغيير النص الذي يظهر في حقل TC؟**
A: استبدل "Entry Text" في استدعاء InsertField بأي سلسلة تريدها، على سبيل المثال، builder.InsertField("TC \"Chapter 1\" \f t");

**Q: هل يمكنني إدراج عدة حقول TC في نفس المستند؟**
A: نعم؛ ما عليك سوى استدعاء builder.InsertField بنصوص إدخال مختلفة في المواقع المطلوبة قبل حفظ المستند.

**Q: هل يعمل هذا الكود مع صيغ أخرى غير .docx، مثل .pdf؟**
A: يتم حفظ المستند كـ .docx في المثال، لكن Aspose.Words يمكنه الحفظ إلى صيغ أخرى (مثل .pdf) عن طريق تغيير امتداد الملف في doc.Save وضمان دعم صيغة الإخراج المناسبة.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}