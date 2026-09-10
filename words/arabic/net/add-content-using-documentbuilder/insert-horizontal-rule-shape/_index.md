---
title: إدراج شكل خط أفقي في مستند Word باستخدام Aspose.Words for .NET
weight: 110
limit:
description: تعلم كيفية إضافة شكل خط أفقي إلى مستند Word باستخدام Aspose.Words for .NET عبر DocumentBuilder.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, documentbuilder horizontal line, create Word document .NET, horizontal rule shape tutorial]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إدراج شكل خط أفقي في مستند Word باستخدام Aspose.Words
في هذا البرنامج التعليمي ستتعلم كيفية إدراج شكل خط أفقي برمجيًا في مستند Word باستخدام Aspose.Words for .NET. باستخدام الفئتين Document و DocumentBuilder نقوم بإنشاء مستند جديد، وإضافة فقرة نصية، ثم وضع شكل خط أفقي في الموقع المطلوب. يوفر الخط الأفقي فاصلًا بصريًا يمكن أن يكون مفيدًا لفواصل الأقسام أو للتأكيد البصري.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-horizontal-rule-shape" >}}


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

**Q: أين بالضبط يضع `builder.InsertHorizontalRule()` الخط في المستند؟**
A: `InsertHorizontalRule` يُدرج شكل خط أفقي في موضع المؤشر الحالي لـ `DocumentBuilder`؛ إذا كنت تريد أن يكون على سطر منفصل، استدعِ `builder.Writeln()` قبل الإدراج.

**Q: هل يمكنني تغيير السماكة أو اللون أو العرض للخط الأفقي المُدرج؟**
A: `InsertHorizontalRule` يضيف خطًا بنمط افتراضي ولا يتيح خيارات تنسيق؛ لتخصيص تلك الخصائص تحتاج إلى إدراج `Shape` يدويًا (مثلاً `builder.InsertShape(ShapeType.HorizontalLine)`) ثم ضبط خصائص `LineFormat` الخاصة به.

**Q: هل من الممكن إضافة أكثر من خط أفقي في نفس المستند؟**
A: نعم—ما عليك سوى استدعاء `builder.InsertHorizontalRule()` في كل مرة تحتاج فيها إلى خط جديد؛ كل استدعاء ينشئ شكلًا منفصلًا في موقع `DocumentBuilder` الحالي.

**Q: هل سيكون الخط الأفقي مرئيًا عند فتح ملف .docx المحفوظ في Microsoft Word؟**
A: بالطبع؛ يتم حفظ الخط كشكل داخل ملف .docx، لذا يعرضه Word تمامًا كما يظهر في المستند المُنشأ.

**Q: ماذا يحدث إذا لم يكن مجلد `dataDir` موجودًا قبل استدعاء `doc.Save(...)`؟**
A: `doc.Save` سيُطلق استثناء `DirectoryNotFoundException`؛ تأكد من وجود دليل الهدف أو أنشئه برمجيًا قبل الحفظ.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}