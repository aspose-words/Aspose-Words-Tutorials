---
title: إدراج Comment على فقرة محددة في مستند Word باستخدام Aspose.Words for .NET
weight: 210
limit:
description: دليل خطوة بخطوة لإضافة تعليق مؤلف إلى فقرة مختارة في مستند Word وحفظه كملف DOCX باستخدام Aspose.Words for .NET.
keywords: [add comment Aspose.Words for .NET, insert comment Word document, comment author Aspose.Words, c# add comment to Word, save DOCX with comment]
url: /net/working-with-comments/add-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: دليل خطوة بخطوة لإضافة تعليق مؤلف إلى فقرة مختارة في مستند Word وحفظه
    كملف DOCX باستخدام Aspose.Words for .NET.
  headline: إدراج Comment على فقرة محددة في مستند Word باستخدام Aspose.Words for .NET
  type: TechArticle
- description: دليل خطوة بخطوة لإضافة تعليق مؤلف إلى فقرة مختارة في مستند Word وحفظه
    كملف DOCX باستخدام Aspose.Words for .NET.
  name: إدراج Comment على فقرة محددة في مستند Word باستخدام Aspose.Words for .NET
  steps:
  - name: إنشاء كائن Document جديد وDocumentBuilder لبدء بناء ملف Word.
    text: إنشاء كائن Document جديد وDocumentBuilder لبدء بناء ملف Word.
  - name: استخدم DocumentBuilder.Writeln لإضافة ثلاثة فقرات نصية منفصلة إلى المستند.
    text: استخدم DocumentBuilder.Writeln لإضافة ثلاثة فقرات نصية منفصلة إلى المستند.
  - name: استرجع الفقرة الثانية بأمان، مع الرجوع إلى الأولى إذا كان المستند يحتوي
      على أقل من فقرتين.
    text: استرجع الفقرة الثانية بأمان، مع الرجوع إلى الأولى إذا كان المستند يحتوي
      على أقل من فقرتين.
  - name: أنشئ Comment مع تفاصيل المؤلف، حدّد نصه، وأرفقه بالفقرة المختارة.
    text: أنشئ Comment مع تفاصيل المؤلف، حدّد نصه، وأرفقه بالفقرة المختارة.
  - name: احفظ المستند المعدل كملف DOCX باسم 'sample.docx' في المجلد الحالي.
    text: احفظ المستند المعدل كملف DOCX باسم 'sample.docx' في المجلد الحالي.
  type: HowTo
- questions:
  - answer: يعود كتلة `if` إلى الفقرة الأولى (`paraList[0]`) عندما يكون `paraList.Count`
      أقل من 2، وبالتالي سيتم إرفاق التعليق بتلك الفقرة الوحيدة بدلاً من الفقرة الثانية
      غير الموجودة.
    question: ماذا يفعل الكود إذا كان المستند يحتوي على فقرة واحدة فقط؟
  - answer: يتم تمريرهما إلى مُنشئ `Comment` كوسيطين ثاني وثالث – `new Comment(wordDoc,
      \"Jordan\", \"JH\", DateTime.Now)` – حيث \"Jordan\" هو اسم المؤلف و\"JH\" هو
      الاختصارات.
    question: كيف يتم تعيين اسم المؤلف والاختصارات للتعليق في هذا المثال؟
  - answer: في هذا المقتطف يتم ربط التعليق بالـ `Paragraph` بالكامل عبر `AppendChild`،
      ولكن للتعليق على نطاق نصي تحتاج إلى إنشاء `CommentRangeStart` و`CommentRangeEnd`
      حول عقد الـ `Run` المطلوبة ثم إضافة عقدة `Comment` بينها.
    question: هل يمكنني إرفاق تعليق إلى جزء محدد من النص بدلاً من الفقرة بأكملها؟
  - answer: '`AppendChild` يضيف عقدة `Comment` إلى مجموعة الأطفال للفقرة، وتقوم Aspose.Words
      تلقائيًا بإنشاء علامات بدء/إنهاء التعليق المطلوبة عند حفظ المستند.'
    question: هل أحتاج إلى إدراج علامات التعليق يدويًا، أم أن `AppendChild` يتولى
      ذلك؟
  type: FAQPage
images:
- /net/working-with-comments/add-comment/og-image.png
og_title: إدراج تعليق في فقرة Word
og_description: إضافة تعليق مؤلف إلى فقرة محددة وتصدير الملف كملف DOCX باستخدام Aspose.Words.
og_image_alt: دليل يوضح كيفية إضافة تعليق إلى فقرة في مستند Word باستخدام Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إدراج Comment على فقرة محددة في مستند Word باستخدام Aspose.Words
مع Aspose.Words for .NET يمكنك إضافة تعليقات إلى ملفات Word برمجيًا. يشرح هذا البرنامج التعليمي إنشاء مستند جديد، وإدراج ثلاثة فقرات، وتحديد الفقرة الثانية، وإرفاق تعليق يتضمن معلومات المؤلف والتاريخ. أخيرًا، يتم حفظ المستند كملف DOCX مع الحفاظ على التعليق.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-comment" >}}


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
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: ماذا يفعل الكود إذا كان المستند يحتوي على فقرة واحدة فقط؟**  
A: يعود كتلة `if` إلى الفقرة الأولى (`paraList[0]`) عندما يكون `paraList.Count` أقل من 2، وبالتالي سيتم إرفاق التعليق بتلك الفقرة الوحيدة بدلاً من الفقرة الثانية غير الموجودة.

**Q: كيف يتم تعيين اسم المؤلف والاختصارات للتعليق في هذا المثال؟**  
A: يتم تمريرهما إلى مُنشئ `Comment` كوسيطين ثاني وثالث – `new Comment(wordDoc, \"Jordan\", \"JH\", DateTime.Now)` – حيث \"Jordan\" هو اسم المؤلف و\"JH\" هو الاختصارات.

**Q: هل يمكنني إرفاق تعليق إلى جزء محدد من النص بدلاً من الفقرة بأكملها؟**  
A: في هذا المقتطف يتم ربط التعليق بالـ `Paragraph` بالكامل عبر `AppendChild`، ولكن للتعليق على نطاق نصي تحتاج إلى إنشاء `CommentRangeStart` و`CommentRangeEnd` حول عقد الـ `Run` المطلوبة ثم إضافة عقدة `Comment` بينها.

**Q: هل أحتاج إلى إدراج علامات التعليق يدويًا، أم أن `AppendChild` يتولى ذلك؟**  
A: `AppendChild` يضيف عقدة `Comment` إلى مجموعة الأطفال للفقرة، وتقوم Aspose.Words تلقائيًا بإنشاء علامات بدء/إنهاء التعليق المطلوبة عند حفظ المستند.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}