---
title: إضافة حقل نموذج مربع اختيار إلى مستند Word باستخدام Aspose.Words for .NET
weight: 210
limit:
description: تعلم كيفية إضافة حقل نموذج مربع اختيار إلى مستند Word جديد برمجيًا باستخدام Aspose.Words for .NET وحفظ الملف.
keywords: [Aspose.Words for .NET, insert check box, check box form field, .NET DocumentBuilder, Word document automation, add form field programmatically]
url: /net/add-content-using-documentbuilder/insert-check-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إضافة حقل نموذج مربع اختيار إلى مستند Word باستخدام Aspose.Words
يوضح هذا البرنامج التعليمي كيفية إنشاء مستند Word جديد واستخدام DocumentBuilder الخاص بـ Aspose.Words for .NET لإدراج حقل نموذج مربع اختيار. باتباع الخطوات، ستظهر لك الشيفرة الدقيقة اللازمة لإضافة العنصر التفاعلي ثم حفظ المستند إلى ملف. إنها طريقة سريعة لإنشاء ملفات Word بسيطة تدعم النماذج برمجيًا.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-check-box" >}}


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

**Q: ماذا يمثل الوسيط الرابع (0) في InsertCheckBox؟**
A: يحدد الحجم البصري لمربع الاختيار بالنقاط؛ قيمة 0 تخبر Aspose.Words باستخدام الحجم الافتراضي.

**Q: هل يمكنني إدراج أكثر من مربع اختيار بنفس الاسم؟**
A: لا – يجب أن يكون اسم كل حقل نموذج فريدًا؛ محاولة إدراج مربع اختيار آخر يُدعى \"CheckBox\" سيؤدي إلى رمي ArgumentException.

**Q: كيف يمكنني إضافة مربع اختيار إلى مستند موجود بدلاً من مستند جديد؟**
A: حمّل المستند أولاً (مثال: `Document doc = new Document(\"Existing.docx\");`) ثم أنشئ DocumentBuilder لهذا المستند واستدعِ `InsertCheckBox` في موضع المؤشر المطلوب.

**Q: كيف يمكنني قراءة حالة مربع الاختيار المُدرج بعد حفظ المستند؟**
A: استرجع حقل النموذج عبر `doc.Range.FormFields[\"CheckBox\"]` وتفقد الخاصية `Checked` لمعرفة ما إذا كان محددًا.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}