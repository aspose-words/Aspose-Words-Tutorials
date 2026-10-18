---
title: إدراج مخطط عمودي نموذجي في مستند Word باستخدام Aspose.Words for .NET
weight: 410
limit:
description: دليل خطوة بخطوة لإنشاء ملف Word، وإدراج مخطط عمودي افتراضي باستخدام DocumentBuilder.InsertChart، والوصول إلى كائن المخطط، وحفظه كملف .docx.
keywords: [Aspose.Words for .NET, insert column chart, documentbuilder inserchart, create word document with chart, save chart to docx, chart object Aspose.Words]
url: /net/programming-with-charts/insert-sample-column-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: دليل خطوة بخطوة لإنشاء ملف Word، وإدراج مخطط عمودي افتراضي باستخدام
    DocumentBuilder.InsertChart، والوصول إلى كائن المخطط، وحفظه كملف .docx.
  headline: إدراج مخطط عمودي نموذجي في مستند Word باستخدام Aspose.Words for .NET
  type: TechArticle
- description: دليل خطوة بخطوة لإنشاء ملف Word، وإدراج مخطط عمودي افتراضي باستخدام
    DocumentBuilder.InsertChart، والوصول إلى كائن المخطط، وحفظه كملف .docx.
  name: إدراج مخطط عمودي نموذجي في مستند Word باستخدام Aspose.Words for .NET
  steps:
  - name: إنشاء مستند Word فارغ وDocumentBuilder لتحريره.
    text: إنشاء مستند Word فارغ وDocumentBuilder لتحريره.
  - name: إدراج مخطط عمودي بحجم 432 × 252 نقطة في المستند.
    text: إدراج مخطط عمودي بحجم 432 × 252 نقطة في المستند.
  - name: استرجاع كائن Chart من الشكل المُدرج لإجراء تخصيص إضافي إذا لزم الأمر.
    text: استرجاع كائن Chart من الشكل المُدرج لإجراء تخصيص إضافي إذا لزم الأمر.
  - name: حفظ المستند، الذي يحتوي الآن على المخطط العمودي المُدرج، كملف .docx.
    text: حفظ المستند، الذي يحتوي الآن على المخطط العمودي المُدرج، كملف .docx.
  type: HowTo
- questions:
  - answer: الأبعاد مُحددة بالنقاط (1 نقطة = 1/72 بوصة)، لذا 432 نقطة ≈ 6 بوصات و252
      نقطة ≈ 3.5 بوصة.
    question: ما الوحدات المستخدمة لمعلمات العرض والارتفاع (432، 252) في InsertChart؟
  - answer: نعم—بعد الإدراج لديك كائن Chart عبر `chartContainer.Chart`؛ يمكنك تعديل
      SeriesCollection وCategories وValues الخاصة به لاستبدال البيانات النموذجية.
    question: هل يمكنني تغيير بيانات المخطط بعد استدعاء InsertChart مع مجموعة البيانات
      الافتراضية؟
  - answer: ما عليك سوى استبدال `ChartType.Column` بقيمة تعداد أخرى مثل `ChartType.Line`
      في استدعاء `InsertChart`.
    question: هل يمكن إدراج نوع مخطط مختلف (مثل مخطط خطي) باستخدام نفس الشيفرة؟
  - answer: لا—`docBuilder.InsertChart` يضمّن المخطط تلقائيًا في `Shape`؛ استدعاء
      `wordDoc.Save` يكتب المخطط مع المستند.
    question: هل أحتاج إلى استدعاء أي طريقة إضافية لتضمين المخطط قبل حفظ المستند؟
  type: FAQPage
images:
- /net/programming-with-charts/insert-sample-column-chart/og-image.png
og_title: إدراج مخطط عمودي نموذجي في مستند Word
og_description: إضافة مخطط عمودي جاهز إلى مستند Word باستخدام Aspose.Words for .NET في دقائق.
og_image_alt: لقطة شاشة تُظهر مستند Word مع مخطط عمودي نموذجي مُدرج باستخدام Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إدراج مخطط عمودي نموذجي في مستند Word باستخدام Aspose.Words
يرشدك هذا البرنامج التعليمي إلى إنشاء مستند Word جديد وإدراج مخطط عمودي افتراضي باستخدام DocumentBuilder.InsertChart. ستتعرف أيضًا على كيفية استرجاع كائن Chart المضمن للتلاعب الإضافي. أخيرًا، يوضح الدليل كيفية حفظ المستند كملف .docx.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-sample-column-chart" >}}


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

**Q: ما الوحدات المستخدمة لمعلمات العرض والارتفاع (432، 252) في InsertChart؟**  
A: الأبعاد مُحددة بالنقاط (1 نقطة = 1/72 بوصة)، لذا 432 نقطة ≈ 6 بوصات و252 نقطة ≈ 3.5 بوصة.

**Q: هل يمكنني تغيير بيانات المخطط بعد استدعاء InsertChart مع مجموعة البيانات الافتراضية؟**  
A: نعم—بعد الإدراج لديك كائن Chart عبر `chartContainer.Chart`؛ يمكنك تعديل SeriesCollection وCategories وValues الخاصة به لاستبدال البيانات النموذجية.

**Q: هل يمكن إدراج نوع مخطط مختلف (مثل مخطط خطي) باستخدام نفس الشيفرة؟**  
A: ما عليك سوى استبدال `ChartType.Column` بقيمة تعداد أخرى مثل `ChartType.Line` في استدعاء `InsertChart`.

**Q: هل أحتاج إلى استدعاء أي طريقة إضافية لتضمين المخطط قبل حفظ المستند؟**  
A: لا—`docBuilder.InsertChart` يضمّن المخطط تلقائيًا في `Shape`؛ استدعاء `wordDoc.Save` يكتب المخطط مع المستند.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}