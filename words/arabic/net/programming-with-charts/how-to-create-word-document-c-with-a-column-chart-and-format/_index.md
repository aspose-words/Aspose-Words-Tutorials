---
category: general
date: 2026-09-21
description: تعلم كيفية إنشاء مستند Word باستخدام C# وإدراج مخطط عمودي، وتعيين موضع
  التسمية، وعرض القيم باستخدام Aspose.Words في دليل خطوة بخطوة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to insert chart
- how to set label
- how to display values
- insert column chart word
language: ar
lastmod: 2026-09-21
og_description: إنشاء مستند Word باستخدام C# و Aspose.Words. يوضح هذا الدليل كيفية
  إدراج مخطط عمودي، وتعيين موضع التسمية، وعرض القيم.
og_image_alt: Screenshot of a Word document created with C# that contains a column
  chart and data labels
og_title: إنشاء مستند Word باستخدام C# – إدراج مخطط عمودي، تعيين التسمية، إظهار القيم
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  headline: How to create Word document C# with a column chart and formatted labels
  type: TechArticle
- description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  name: How to create Word document C# with a column chart and formatted labels
  steps:
  - name: Expected result
    text: When you open `output.docx`, you should see a single column chart similar
      to the image below. Each column has a numeric label at its top, inside the column,
      displaying the series value.
  - name: Adding custom data to the chart
    text: 'If you need to replace the placeholder data, you can modify the chart’s
      `Series` collection:'
  - name: Changing label font and color
    text: 'You can further customize the label appearance:'
  - name: Inserting multiple charts
    text: The `DocumentBuilder` can insert as many charts as you need. Just call `InsertChart`
      again after moving the cursor with `builder.Writeln()` or `builder.InsertParagraph()`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Charts
title: كيفية إنشاء مستند Word باستخدام C# مع مخطط عمودي وعلامات منسقة
url: /ar/net/programming-with-charts/how-to-create-word-document-c-with-a-column-chart-and-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مستند Word باستخدام C# مع مخطط عمودي وعناوين منسقة

إذا كنت بحاجة إلى **create Word document C#** التي تتضمن مخططًا، فإن هذا الدليل يوضح لك بالضبط كيفية القيام بذلك. ستتعلم كيفية إدراج **column chart**، وضع تسمية البيانات الخاصة به، وعرض قيم التسمية—كل ذلك باستخدام Aspose.Words for .NET.

كان إنشاء ملف Word يحتوي على مخطط يتطلب سابقًا عملًا يدويًا في Microsoft Word. باستخدام خطوات **how to insert chart** الموضحة هنا، يمكنك أتمتة العملية بالكامل من خلال الكود، مما يجعل توليد التقارير سريعًا وقابلًا للتكرار. يغطي الدليل أيضًا خصائص **how to set label** و **how to display values** بحيث يكون المخطط جاهزًا للمستخدمين النهائيين.

بنهاية هذه المقالة ستحصل على برنامج C# كامل وقابل للتنفيذ يقوم بإنشاء ملف `.docx` يحتوي على مخطط عمودي تظهر تسميات البيانات الخاصة به داخل كل عمود وتعرض القيم الرقمية الخاصة بها.

## المتطلبات المسبقة

* .NET 6.0 SDK أو أحدث مثبت  
* نسخة مرخصة من **Aspose.Words for .NET** (الإصدار التجريبي المجاني يعمل للاختبار)  
* بيئة تطوير متكاملة مثل Visual Studio 2022 أو Visual Studio Code  

لا توجد حزم NuGet إضافية مطلوبة بخلاف `Aspose.Words`.

## الخطوة 1: إعداد المشروع وإضافة Aspose.Words

أنشئ مشروعًا جديدًا من نوع console وأضف حزمة Aspose.Words:

```bash
dotnet new console -n WordChartDemo
cd WordChartDemo
dotnet add package Aspose.Words
```

أمر `dotnet add package` يجلب أحدث نسخة مستقرة من **Aspose.Words**، والتي تتضمن API المخطط المستخدم في مثال **insert column chart word**.

## الخطوة 2: إنشاء مستند Word فارغ جديد

الجزء الأول من الكود ينشئ مستندًا فارغًا و`DocumentBuilder` يتيح لك إدراج المحتوى. هذا هو الأساس لـ **create word document C#**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 2: Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` يمثل ملف `.docx` بالكامل، بينما `DocumentBuilder` يوفر طرقًا مثل `InsertParagraph`، `InsertImage`، وبشكل حاسم لهذا الدليل، `InsertChart`.

## الخطوة 3: إدراج مخطط عمودي (how to insert chart)

الآن نقوم بإدراج **column chart**. طريقة `InsertChart` تأخذ نوع المخطط، العرض، والارتفاع بالنقاط.

```csharp
        // Step 3: Insert a column chart with a width of 400 pt and height of 300 pt.
        Chart chart = builder.InsertChart(ChartType.Column, 400, 300);
```

في هذه المرحلة يحتوي المخطط على سلسلة بيانات افتراضية بقيم placeholder. يمكنك استبدال بيانات السلسلة إذا كنت تحتاج أرقامًا مخصصة، ولكن لعرض **how to set label** و **how to display values**، البيانات الافتراضية كافية.

## الخطوة 4: وضع تسمية البيانات داخل كل عمود (how to set label)

تسميات البيانات هي النص الذي يظهر على كل عمود. لجعل المخطط أسهل للقراءة، نقوم بنقل التسمية داخل العمود وتفعيل قيمتها الرقمية.

```csharp
        // Step 4: Access the first data label of the first series.
        ChartDataLabel label = chart.DataLabels[0];

        // Position the label at the inside end of the column.
        label.Position = ChartDataLabelPosition.InsideEnd;

        // Show the numeric value of each data point.
        label.ShowValue = true;
```

`ChartDataLabelPosition.InsideEnd` يضع التسمية في أعلى العمود ولكن لا يزال داخل شكل العمود، وهو نمط بصري شائع للتقارير. ضبط `ShowValue` على `true` يحقق متطلبات **how to display values**.

## الخطوة 5: حفظ المستند

أخيرًا، احفظ المستند على القرص. يمكن فتح الملف باستخدام Microsoft Word أو LibreOffice أو أي عارض يدعم تنسيق Open XML.

```csharp
        // Step 5: Save the document to the output folder.
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

تشغيل البرنامج ينتج ملف `output.docx` يحتوي على مخطط عمودي مع تسميات البيانات موضوعة داخل كل عمود وتظهر قيمها.

### النتيجة المتوقعة

عند فتح `output.docx`، يجب أن ترى مخطط عمودي واحد مشابه للصورة أدناه. كل عمود يحتوي على تسمية رقمية في أعلىه، داخل العمود، تعرض قيمة السلسلة.

![Chart in a Word document created with C#](/images/word-chart-example.png "Chart in a Word document created with C# – create word document C#")

*Alt text:* *مخطط في مستند Word تم إنشاؤه باستخدام C# يوضح كيفية إدراج column chart word وعرض القيم.*

## الاختلافات الشائعة وحالات الحافة

### إضافة بيانات مخصصة إلى المخطط

إذا كنت بحاجة لاستبدال بيانات placeholder، يمكنك تعديل مجموعة `Series` للمخطط:

```csharp
// Replace the default series with custom values.
chart.Series.Clear();
ChartSeries series = chart.Series.Add(ChartType.Column);
series.Name = "Sales Q1";
series.AddCategory("Jan", 120);
series.AddCategory("Feb", 150);
series.AddCategory("Mar", 180);
```

### تغيير خط التسمية واللون

يمكنك تخصيص مظهر التسمية أكثر:

```csharp
label.Font.Name = "Arial";
label.Font.Size = 10;
label.Font.Color = System.Drawing.Color.DarkBlue;
```

### إدراج مخططات متعددة

`DocumentBuilder` يمكنه إدراج عدد غير محدود من المخططات حسب الحاجة. فقط استدعِ `InsertChart` مرة أخرى بعد تحريك المؤشر باستخدام `builder.Writeln()` أو `builder.InsertParagraph()`.

## نصائح احترافية

* **نصيحة احترافية:** اضبط `chart.HasTitle = true` وعيّن `chart.Title.Text` لإعطاء المخطط عنوانًا وصفيًا. هذا يحسن إمكانية الوصول لقراء الشاشة.
* **احذر من:** عند الحفظ إلى مشاركة شبكة، تأكد من أن التطبيق لديه أذونات كتابة؛ وإلا سيطرح `doc.Save` استثناء `UnauthorizedAccessException`.
* **نصيحة أداء:** أعد استخدام نسخة واحدة من `DocumentBuilder` لعمليات الإدراج المتعددة؛ إنشاء بنّاء جديد لكل عملية يضيف عبئًا غير ضروري.

## الخلاصة

أنت الآن تعرف كيف **create Word document C#** الذي يحتوي على مخطط عمودي، وكيفية **insert chart** العناصر، **set label** المواضع، و **display values** داخل كل عمود. مثال الكود الكامل أعلاه جاهز للتنفيذ، ويمكنك توسيعه ببيانات مخصصة أو تنسيقات أو مخططات إضافية.

بعد ذلك، استكشف المواضيع ذات الصلة مثل **how to insert picture**، **how to generate tables**، أو **how to apply document themes** لجعل تقاريرك الآلية أكثر غنى. Happy coding!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إدراج مخطط عمودي في Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [إدراج مخطط عمودي بسيط في Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [إدراج مخطط مساحة في مستند Word | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}