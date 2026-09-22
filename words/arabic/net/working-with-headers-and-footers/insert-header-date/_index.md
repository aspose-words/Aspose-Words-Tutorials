---
title: إدراج تاريخ ديناميكي في ترويسة مستند Word باستخدام Aspose.Words for .NET
weight: 110
limit:
description: تعلم كيفية إضافة حقل DATE ديناميكي إلى الترويسة الأساسية لمستند Word باستخدام Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert header date, dynamic DATE field, DocumentBuilder header, Word document header automation]
url: /net/working-with-headers-and-footers/insert-header-date/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: تعلم كيفية إضافة حقل DATE ديناميكي إلى الترويسة الأساسية لمستند Word
    باستخدام Aspose.Words for .NET.
  headline: إدراج تاريخ ديناميكي في ترويسة مستند Word باستخدام Aspose.Words for .NET
  type: TechArticle
- description: تعلم كيفية إضافة حقل DATE ديناميكي إلى الترويسة الأساسية لمستند Word
    باستخدام Aspose.Words for .NET.
  name: إدراج تاريخ ديناميكي في ترويسة مستند Word باستخدام Aspose.Words for .NET
  steps:
  - name: أنشئ مستندًا جديدًا وDocumentBuilder لتعديله.
    text: أنشئ مستندًا جديدًا وDocumentBuilder لتعديله.
  - name: انقل مؤشر الـ builder إلى الترويسة الأساسية بحيث تؤثر الإدخالات اللاحقة
      على الترويسة.
    text: انقل مؤشر الـ builder إلى الترويسة الأساسية بحيث تؤثر الإدخالات اللاحقة
      على الترويسة.
  - name: اكتب النص الثابت وأدرج حقل DATE بصيغة “MMMM d, yyyy” داخل الترويسة، مما
      يُنشئ تاريخًا ديناميكيًا.
    text: اكتب النص الثابت وأدرج حقل DATE بصيغة “MMMM d, yyyy” داخل الترويسة، مما
      يُنشئ تاريخًا ديناميكيًا.
  - name: ارجع إلى النص الرئيسي وأضف فقرة نموذجية، لتظهر محتوى المستند العادي إلى
      جانب الترويسة.
    text: ارجع إلى النص الرئيسي وأضف فقرة نموذجية، لتظهر محتوى المستند العادي إلى
      جانب الترويسة.
  - name: احفظ المستند كملف .docx.
    text: احفظ المستند كملف .docx.
  type: HowTo
- questions:
  - answer: استدعاء `MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` يضع الـ builder
      في الترويسة الأساسية الموجودة، و`Write`/`InsertField` يضيفان النص ببساطة إلى
      ما هو موجود بالفعل؛ لا يحذفان المحتوى الحالي.
    question: ماذا يحدث إذا كان المستند يحتوي بالفعل على ترويسة أساسية – هل سيستبدل
      الكود الخاص بي هذه الترويسة؟
  - answer: نعم – عدّل تنسيق المفتاح في كود الحقل الممرّر إلى `InsertField`، على سبيل
      المثال `builder.InsertField("DATE \\\\@ \\\"yyyy-MM-dd\\\"")` سيُنتج تاريخًا
      مثل 2026-09-22.
    question: هل يمكنني تغيير تنسيق التاريخ المستخدم في حقل DATE، وكيف؟
  - answer: استبدل `HeaderFooterType.HeaderPrimary` بـ `HeaderFooterType.HeaderFirst`
      عند استدعاء `MoveToHeaderFooter`؛ باقي الشيفرة يعمل بنفس الطريقة.
    question: إذا كنت أحتاج حقل التاريخ في ترويسة الصفحة الأولى بدلاً من الترويسة
      الأساسية، ماذا عليّ أن أفعل؟
  - answer: يُدرج الحقل باستخدام المفتاح `\\@` فقط، مما يُخبر Word بعرض التاريخ الحالي
      في كل مرة يتم فيها تحديث الحقل (مثلاً عند فتح الملف أو عند الضغط على Ctrl+Alt+F9).
    question: هل يتم تحديث حقل DATE تلقائيًا عندما يُفتح المستند لاحقًا؟
  type: FAQPage
images:
- /net/working-with-headers-and-footers/insert-header-date/og-image.png
og_title: إضافة تاريخ ديناميكي إلى ترويسة Word
og_description: دليل خطوة بخطوة لتضمين حقل تاريخ حي في ترويسة Word باستخدام Aspose.Words.
og_image_alt: لقطة شاشة توضح كيفية إدراج حقل DATE ديناميكي في ترويسة مستند Word باستخدام Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إدراج تاريخ ديناميكي في ترويسة مستند Word باستخدام Aspose.Words
يوضح هذا الدرس كيفية استخدام فئتي Document و DocumentBuilder في Aspose.Words for .NET لإدراج حقل DATE ديناميكي في الترويسة الأساسية لمستند Word. يتم تحديث الحقل المضاف تلقائيًا إلى التاريخ الحالي في كل مرة يُفتح فيها المستند، مما يضمن أن الترويسة دائمًا تعكس أحدث تاريخ. اتبع الشيفرة خطوة بخطوة لإضافة الحقل وحفظ الملف المحدث.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/insert-header-date" >}}


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
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: ماذا يحدث إذا كان المستند يحتوي بالفعل على ترويسة أساسية – هل سيستبدل الكود الخاص بي هذه الترويسة؟**  
A: استدعاء `MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` يضع الـ builder في الترويسة الأساسية الموجودة، و`Write`/`InsertField` يضيفان النص ببساطة إلى ما هو موجود بالفعل؛ لا يحذفان المحتوى الحالي.

**Q: هل يمكنني تغيير تنسيق التاريخ المستخدم في حقل DATE، وكيف؟**  
A: نعم – عدّل تنسيق المفتاح في كود الحقل الممرّر إلى `InsertField`، على سبيل المثال `builder.InsertField("DATE \\\\@ \\\"yyyy-MM-dd\\\"")` سيُنتج تاريخًا مثل 2026-09-22.

**Q: إذا كنت أحتاج حقل التاريخ في ترويسة الصفحة الأولى بدلاً من الترويسة الأساسية، ماذا عليّ أن أفعل؟**  
A: استبدل `HeaderFooterType.HeaderPrimary` بـ `HeaderFooterType.HeaderFirst` عند استدعاء `MoveToHeaderFooter`؛ باقي الشيفرة يعمل بنفس الطريقة.

**Q: هل يتم تحديث حقل DATE تلقائيًا عندما يُفتح المستند لاحقًا؟**  
A: يُدرج الحقل باستخدام المفتاح `\\@` فقط، مما يُخبر Word بعرض التاريخ الحالي في كل مرة يتم فيها تحديث الحقل (مثلاً عند فتح الملف أو عند الضغط على Ctrl+Alt+F9).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}