---
title: تحديث عنوان المخطط وتبديل إظهار وسيلة الإيضاح في Word باستخدام Aspose.Words for .NET
weight: 810
limit:
description: تعلّم كيفية تغيير عنوان المخطط والتحكم في إظهار وسيلة الإيضاح في مستند Word باستخدام Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, update chart title, toggle legend visibility, word chart manipulation, c# chart title, aspose words chart legend]
url: /net/programming-with-charts/update-chart-title/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: تعلّم كيفية تغيير عنوان المخطط والتحكم في إظهار وسيلة الإيضاح في مستند
    Word باستخدام Aspose.Words for .NET.
  headline: تحديث عنوان المخطط وتبديل إظهار وسيلة الإيضاح في Word باستخدام Aspose.Words
    for .NET
  type: TechArticle
- description: تعلّم كيفية تغيير عنوان المخطط والتحكم في إظهار وسيلة الإيضاح في مستند
    Word باستخدام Aspose.Words for .NET.
  name: تحديث عنوان المخطط وتبديل إظهار وسيلة الإيضاح في Word باستخدام Aspose.Words
    for .NET
  steps:
  - name: حدّد عنوان المخطط المزوّد من قبل المستخدم وما إذا كان يجب إظهار وسيلة الإيضاح.
    text: حدّد عنوان المخطط المزوّد من قبل المستخدم وما إذا كان يجب إظهار وسيلة الإيضاح.
  - name: أنشئ مستند Word جديدًا وDocumentBuilder لإضافة المحتوى.
    text: أنشئ مستند Word جديدًا وDocumentBuilder لإضافة المحتوى.
  - name: أدرج مخططًا عموديًا بحجم 432 × 252 pt في المستند وتأكد من أن الشكل يحتوي
      فعليًا على مخطط.
    text: أدرج مخططًا عموديًا بحجم 432 × 252 pt في المستند وتأكد من أن الشكل يحتوي
      فعليًا على مخطط.
  - name: استرجع كائن المخطط (chart)، عيّن نص عنوانه إلى القيمة التي قدمها المستخدم،
      وتأكد من عرض العنوان.
    text: استرجع كائن المخطط (chart)، عيّن نص عنوانه إلى القيمة التي قدمها المستخدم،
      وتأكد من عرض العنوان.
  - name: 'قم بتكوين وسيلة الإيضاح: اعرضها على اليمين إذا طُلب ذلك، وإلا أخفها، واسمح
      لها بالتراكب فوق منطقة الرسم.'
    text: 'قم بتكوين وسيلة الإيضاح: اعرضها على اليمين إذا طُلب ذلك، وإلا أخفها، واسمح
      لها بالتراكب فوق منطقة الرسم.'
  - name: احفظ المستند المعدل على القرص باسم CustomChart.docx.
    text: احفظ المستند المعدل على القرص باسم CustomChart.docx.
  type: HowTo
- questions:
  - answer: عند كون `displayLegend` مساويًا لـ `true`، يقوم الكود بتعيين `chartLegend.Position`
      إلى `LegendPosition.Right`، مما يجعل وسيلة الإيضاح مرئية على الجانب الأيمن من
      منطقة الرسم؛ وتظل خاصية `Overlay` مساوية لـ `true`، لذا يمكن لوسيلة الإيضاح
      أن تتراكب على المخطط لتوفير المساحة.
    question: ماذا يغيّر ضبط `displayLegend` إلى `true` في المخطط المُنشأ؟
  - answer: عيّن `chartTitle.Show = false` (أو ببساطة لا تقم بتعيين `Show` إلى `true`)
      بعد تعيين `chartTitle.Text`؛ لن يتم عرض العنوان في مستند Word.
    question: كيف يمكن إخفاء عنوان المخطط إذا لم يقدِّم المستخدم عنوانًا؟
  - answer: نعم—`InsertChart` تُعيد كائن `Shape` يجب أن يحتوي على مخطط، لكن التحقق
      من `HasChart` يضمن أن الشكل فعليًا يحمل كائن `Chart`؛ وإلا سيُطلق الكود استثناء
      `InvalidOperationException`.
    question: هل من الضروري فحص `chartContainer.HasChart` بعد استدعاء `InsertChart`؟
  - answer: بالطبع؛ عيّن أي قيمة من تعداد `LegendPosition` (مثل `LegendPosition.Top`
      أو `LegendPosition.Bottom` أو `LegendPosition.Left`) إلى `chartLegend.Position`
      لإعادة تموضع وسيلة الإيضاح حسب الحاجة.
    question: هل يمكنني وضع وسيلة الإيضاح في مكان غير الجانب الأيمن؟
  type: FAQPage
images:
- /net/programming-with-charts/update-chart-title/og-image.png
og_title: تغيير عنوان المخطط ووسيلة الإيضاح في Word
og_description: تعلّم كيفية تعيين عنوان مخطط مخصص والتحكم في عرض وسيلة الإيضاح في مستند Word باستخدام Aspose.Words for .NET.
og_image_alt: دليل يُظهر الشيفرة التي تُحدّث عنوان المخطط وتبدّل وسيلة الإيضاح في مستند Word باستخدام Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تحديث عنوان المخطط وتبديل إظهار وسيلة الإيضاح في Word باستخدام Aspose.Words
يوضح هذا البرنامج التعليمي كيفية تعديل مخطط داخل مستند Word برمجيًا باستخدام Aspose.Words for .NET. ستتعلم كيفية إدراج مخطط عمودي، استبدال عنوانه بالنص المزوّد من قبل المستخدم، والتحكم في إظهار وسيلة الإيضاح وتراكبها بناءً على تفضيلات المستخدم. تسمح لك هذه الخطوات بتخصيص عرض المخطط ديناميكيًا دون تحرير يدوي.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/update-chart-title" >}}


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

**Q: ماذا يغيّر ضبط `displayLegend` إلى `true` في المخطط المُنشأ؟**  
A: عند كون `displayLegend` مساويًا لـ `true`، يقوم الكود بتعيين `chartLegend.Position` إلى `LegendPosition.Right`، مما يجعل وسيلة الإيضاح مرئية على الجانب الأيمن من منطقة الرسم؛ وتظل خاصية `Overlay` مساوية لـ `true`، لذا يمكن لوسيلة الإيضاح أن تتراكب على المخطط لتوفير المساحة.

**Q: كيف يمكن إخفاء عنوان المخطط إذا لم يقدِّم المستخدم عنوانًا؟**  
A: عيّن `chartTitle.Show = false` (أو ببساطة لا تقم بتعيين `Show` إلى `true`) بعد تعيين `chartTitle.Text`؛ لن يتم عرض العنوان في مستند Word.

**Q: هل من الضروري فحص `chartContainer.HasChart` بعد استدعاء `InsertChart`؟**  
A: نعم—`InsertChart` تُعيد كائن `Shape` يجب أن يحتوي على مخطط، لكن التحقق من `HasChart` يضمن أن الشكل فعليًا يحمل كائن `Chart`؛ وإلا سيُطلق الكود استثناء `InvalidOperationException`.

**Q: هل يمكنني وضع وسيلة الإيضاح في مكان غير الجانب الأيمن؟**  
A: بالطبع؛ عيّن أي قيمة من تعداد `LegendPosition` (مثل `LegendPosition.Top` أو `LegendPosition.Bottom` أو `LegendPosition.Left`) إلى `chartLegend.Position` لإعادة تموضع وسيلة الإيضاح حسب الحاجة.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}