---
title: إدراج HTML محاذى في مستند Word باستخدام Aspose.Words for .NET
weight: 210
limit:
description: تعلم كيفية إدراج HTML بمحاذاة محددة في مستند Word باستخدام Aspose.Words for .NET.
keywords: [insert aligned html, Aspose.Words for .NET, documentbuilder html insertion, html alignment in word, c# insert html word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إدراج HTML محاذى في مستند Word باستخدام Aspose.Words
يوضح هذا البرنامج التعليمي كيفية استخدام DocumentBuilder الخاص بـ Aspose.Words for .NET لتضمين ترميز HTML في مستند Word والتحكم في محاذاته. ستتعرف على كيفية إدراج HTML، ضبط محاذاة الفقرة (يسار، وسط أو يمين)، ثم حفظ المستند الناتج. المثال مثالي للمطورين الذين يحتاجون إلى الحفاظ على تنسيق يشبه الويب أثناء إنشاء ملفات Word برمجيًا.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-aligned-html" >}}


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

**Q: هل يمكن استخدام InsertHtml لإضافة HTML إلى مستند Word موجود بدلاً من إنشاء مستند جديد؟**
A: نعم. أنشئ Document من الملف الموجود، وضع مؤشر DocumentBuilder في الموضع الذي تريد إدراج HTML فيه (مثلاً باستخدام builder.MoveToDocumentEnd())، ثم استدعِ builder.InsertHtml مع الترميز الخاص بك.

**Q: ما هي سمات HTML التي يحترمها InsertHtml لتحديد المحاذاة؟**
A: يُعطي InsertHtml اعتبارًا لخاصية \"align\" على العناصر ذات المستوى الكتلي مثل <p> و <div> وعلامات العناوين، ويطبق محاذاة الفقرة المقابلة في مستند Word الناتج.

**Q: ماذا يحدث إذا احتوت سلسلة HTML على وسوم أو CSS غير مدعومة؟**
A: يتم تجاهل الوسوم غير المدعومة ويتم إدراج النص الداخلي كنص عادي؛ كما يتم تجاهل أنماط CSS المضمنة التي لا يتعرف عليها Aspose.Words، لذا يتم عرض فقط الجزء المدعوم من HTML.

**Q: هل أحتاج إلى إغلاق DocumentBuilder قبل حفظ المستند؟**
A: ليس هناك حاجة لإغلاق صريح؛ بعد إدراج HTML يمكنك مباشرة استدعاء doc.Save بالاسم والصيغة المطلوبة للملف، وتُحرَّر موارد builder تلقائيًا.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}