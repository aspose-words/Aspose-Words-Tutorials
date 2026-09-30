---
title: إضافة حقل نموذج صندوق مركب إلى مستند Word باستخدام Aspose.Words for .NET
weight: 310
limit:
description: تعلم كيفية إضافة حقل نموذج صندوق مركب مع عناصر محددة مسبقًا إلى مستند Word باستخدام Aspose.Words for .NET.
keywords: [combo box form field, Aspose.Words for .NET, documentbuilder combo box, add combo box word, word document form field]
url: /net/add-content-using-documentbuilder/insert-combo-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إضافة حقل نموذج صندوق مركب إلى مستند Word باستخدام Aspose.Words
يوضح هذا البرنامج التعليمي كيفية استخدام DocumentBuilder الخاص بـ Aspose.Words for .NET لإنشاء مستند Word جديد وإدراج حقل نموذج صندوق مركب مملوء بعناصر محددة مسبقًا. باتباع الشيفرة خطوة بخطوة، سترى كيفية تكوين خيارات صندوق المركب ثم حفظ المستند لاستخدامه في النماذج التفاعلية.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-combo-box" >}}


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

**Q: ماذا تمثل مصفوفة `items` التي يتم تمريرها إلى `InsertComboBox`؟**
A: إنها تحدد قائمة السلاسل التي تظهر كخيارات قابلة للتحديد في القائمة المنسدلة لصندوق المركب.

**Q: كيف يمكنني تغيير العنصر المحدد افتراضيًا عند فتح المستند؟**
A: عيّن الوسيط الثالث (`selectedIndex`) في `InsertComboBox` إلى الفهرس الصفري للعنصر الافتراضي المطلوب (مثلاً، `2` لـ "Three").

**Q: هل يمكن وضع صندوق المركب في موقع محدد داخل المستند؟**
A: نعم—قم بتحريك مؤشر `DocumentBuilder` إلى الموضع المطلوب باستخدام طرق مثل `MoveToParagraph` أو `InsertParagraph` أو `Write` قبل استدعاء `InsertComboBox`.

**Q: ما هو تنسيق الملف الذي يتم إنشاؤه بهذه الشيفرة وهل يمكن فتحه في إصدارات Word القديمة؟**
A: يقوم الكود بحفظ ملف `.docx`، والذي يمكن فتحه بواسطة Word 2007 وما بعده، وكذلك أي تطبيق يدعم تنسيق OpenXML.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}