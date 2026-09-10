---
title: إدراج شكل خط أفقي في مستند Word باستخدام Aspose.Words for .NET
weight: 110
limit:
description: دليل خطوة بخطوة لإدراج شكل خط أفقي في مستند Word باستخدام Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, horizontal rule shape .NET, DocumentBuilder horizontal rule, add horizontal line Word, create Word document Aspose]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إدراج شكل خط أفقي في مستند Word باستخدام Aspose.Words
تعرف على كيفية استخدام Aspose.Words for .NET لإدراج شكل خط أفقي في مستند Word. يشرح هذا البرنامج التعليمي خطوة بخطوة إنشاء مستند جديد، إضافة سطر نص، وضع شكل خط أفقي باستخدام DocumentBuilder، وحفظ الملف. يوفر الخط الأفقي فاصلًا بصريًا بسيطًا لمحتواك.

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

**Q: هل يمكنني تغيير مظهر (اللون، السماكة) الخط الأفقي الذي تم إدراجه باستخدام DocumentBuilder.InsertHorizontalRule()؟**
A: يقوم InsertHorizontalRule بإنشاء شكل خط أفقي مدمج بتنسيق افتراضي؛ لتعديل مظهره يجب عليك استرجاع كائن Shape المُدرج (builder.CurrentParagraph.LastChild) وتعديل خصائص LineFormat الخاصة به.

**Q: ماذا يحدث إذا استدعيت InsertHorizontalRule() بعد فقرة تنتهي بالفعل بفاصل سطر؟**
A: تقوم الطريقة بإدراج الخط كفقرة منفصلة، لذا أي فاصل سطر مسبق يخلق ببساطة فقرة فارغة قبل الخط؛ سيظل الخط يظهر على سطره الخاص.

**Q: هل يمكن إدراج أكثر من خط أفقي واحد في نفس المستند باستخدام DocumentBuilder؟**
A: نعم، كل استدعاء لـ builder.InsertHorizontalRule() يضيف شكل خط أفقي جديد في موضع المؤشر الحالي، مما يسمح بوجود عدة خطوط في جميع أنحاء المستند.

**Q: هل يعمل InsertHorizontalRule() عند حفظ المستند إلى صيغ غير DOCX، مثل PDF؟**
A: يتم تخزين الخط الأفقي كشكل في نموذج المستند، لذا عند حفظه إلى PDF أو XPS أو أي صيغ مدعومة أخرى يتم عرض الخط بشكل صحيح في الناتج.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}