---
title: إدراج فاصل صفحة في مستند Word باستخدام Aspose.Words for .NET
weight: 110
limit:
description: تعلم كيفية إضافة فواصل الصفحات إلى ملف Word باستخدام Aspose.Words for .NET عبر Document و DocumentBuilder.
keywords: [Aspose.Words for .NET, insert page break, documentbuilder page break, c# add page break, word document pagination]
url: /net/add-content-using-documentbuilder/insert-page-break/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إدراج فاصل صفحة في مستند Word باستخدام Aspose.Words
في هذا البرنامج التعليمي التفاعلي ستتعلم كيفية إضافة فواصل الصفحات برمجيًا إلى مستند Word باستخدام Aspose.Words for .NET. من خلال إنشاء كائن Document واستخدام DocumentBuilder، يمكنك التحكم في مكان بدء الصفحات الجديدة، وهو أمر أساسي لتنسيق التقارير أو الفواتير أو أي مستند متعدد الأقسام. اتبع المثال خطوة بخطوة لرؤية الشيفرة تعمل ومعاينة الملف الناتج.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-page-break" >}}


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

**Q: هل يمكنني استخدام InsertBreak لإضافة فاصل سطر أو فاصل قسم بدلاً من فاصل صفحة؟**
A: نعم، InsertBreak يقبل أي قيمة من تعداد BreakType، مثل BreakType.LineBreak أو BreakType.SectionBreakContinuous، لإدراج الفاصل المقابل.

**Q: هل يجب استدعاء InsertBreak قبل أم بعد كتابة النص للصفحة الجديدة؟**
A: يجب استدعاء InsertBreak بعد المحتوى الذي تريد وضعه في الصفحة الحالية؛ سيبدأ السطر التالي (Writeln) بعد ذلك في الصفحة الجديدة التي تم إنشاؤها بواسطة الفاصل.

**Q: ماذا يحدث إذا لم ينتهِ مسار dataDir بفاصل دليل؟**
A: إذا كان dataDir يفتقر إلى الشرطة المائلة النهائية، سيتم ربط اسم الملف مباشرةً (مثال: "C:\\DocsAddContentUsingDocumentBuilder.InsertBreak.docx"), مما قد يؤدي إلى مسار غير صالح؛ تأكد من أن المسار ينتهي بـ "\\" أو استخدم Path.Combine.

**Q: هل يمكنني إعادة استخدام نفس مثيل DocumentBuilder لإدراج فواصل متعددة في جميع أنحاء المستند؟**
A: نعم، يمكن استخدام نفس DocumentBuilder بشكل متكرر؛ كل استدعاء لـ InsertBreak يُدخل فاصلًا في موضع المؤشر الحالي للـ builder.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}