---
"description": "تعرّف على كيفية تنسيق تسميات البيانات في المخططات البيانية باستخدام Aspose.Words لـ .NET من خلال هذا الدليل المفصل. حسّن مستندات Word الخاصة بك بسهولة."
"linktitle": "تنسيق رقم تسمية البيانات في الرسم البياني"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "تنسيق رقم تسمية البيانات في الرسم البياني"
"url": "/ar/net/programming-with-charts/format-number-of-data-label/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تنسيق رقم تسمية البيانات في الرسم البياني

## مقدمة

غالبًا ما يتطلب إنشاء مستندات شيقة وغنية بالمعلومات تضمين مخططات بيانية مع تسميات بيانات منسقة جيدًا. إذا كنت مطور .NET وترغب في تحسين مستندات Word الخاصة بك بمخططات بيانية متطورة، فإن Aspose.Words for .NET مكتبة رائعة تساعدك على تحقيق ذلك. سيرشدك هذا البرنامج التعليمي خطوة بخطوة خلال عملية تنسيق تسميات الأرقام في مخطط بياني باستخدام Aspose.Words for .NET.

## المتطلبات الأساسية

قبل الغوص في الكود، هناك بعض المتطلبات الأساسية التي يجب أن تكون موجودة:

- Aspose.Words لـ .NET: تأكد من تثبيت مكتبة Aspose.Words لـ .NET. إذا لم تقم بتثبيتها بعد، يمكنك [قم بتحميله هنا](https://releases.aspose.com/words/net/).
- بيئة التطوير: يجب أن تكون لديك بيئة تطوير .NET. يُنصح بشدة باستخدام Visual Studio.
- المعرفة الأساسية بلغة C#: تعتبر المعرفة ببرمجة C# ضرورية لأن هذا البرنامج التعليمي يتضمن كتابة وفهم كود C#.
- ترخيص مؤقت: لاستخدام Aspose.Words دون أي قيود، يمكنك الحصول على [رخصة مؤقتة](https://purchase.aspose.com/temporary-license/).

الآن، دعنا ننتقل إلى عملية تنسيق تسميات الأرقام في الرسم البياني خطوة بخطوة.

## استيراد مساحات الأسماء

أولاً، نحتاج إلى استيراد مساحات الأسماء اللازمة للعمل مع Aspose.Words لـ .NET. أضف الأسطر التالية في أعلى ملف C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## الخطوة 1: إعداد دليل المستندات الخاص بك

قبل البدء بمعالجة مستند Word، عليك تحديد المجلد الذي ستحفظ فيه المستند. هذا ضروري لعملية الحفظ لاحقًا.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

يستبدل `"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي إلى دليل المستند الخاص بك.

## الخطوة 2: تهيئة المستند وDocumentBuilder

الخطوة التالية هي تهيئة ملف جديد `Document` و أ `DocumentBuilder`. ال `DocumentBuilder` هي فئة مساعدة تسمح لنا بإنشاء محتوى المستند.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## الخطوة 3: إدراج مخطط في المستند

الآن، دعنا ندرج مخططًا في المستند باستخدام `DocumentBuilder`في هذا البرنامج التعليمي، سنستخدم مخططًا خطيًا كمثال.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
chart.Title.Text = "Data Labels With Different Number Format";
```

هنا نقوم بإدراج مخطط خطي بعرض وارتفاع محددين، ونقوم بتعيين عنوان المخطط.

## الخطوة 4: مسح السلسلة الافتراضية وإضافة سلسلة جديدة

افتراضيًا، سيحتوي الرسم البياني على سلاسل مُولّدة مسبقًا. علينا مسحها وإضافة سلاسلنا الخاصة بنقاط بيانات محددة.

```csharp
// حذف السلسلة المولدة افتراضيًا.
chart.Series.Clear();

// أضف سلسلة جديدة بنقاط بيانات مخصصة.
ChartSeries series1 = chart.Series.Add("Aspose Series 1", 
	new string[] { "Category 1", "Category 2", "Category 3" }, 
	new double[] { 2.5, 1.5, 3.5 });
```

## الخطوة 5: تمكين تسميات البيانات

لعرض تسميات البيانات على الرسم البياني، نحتاج إلى تمكينها لسلسلتنا.

```csharp
series1.HasDataLabels = true;
series1.DataLabels.ShowValue = true;
```

## الخطوة 6: تنسيق تسميات البيانات

جوهر هذا البرنامج التعليمي هو تنسيق تسميات البيانات. يمكننا تطبيق تنسيقات أرقام مختلفة على كل تسمية بيانات على حدة.

```csharp
series1.DataLabels[0].NumberFormat.FormatCode = "\"$\"#,##0.00"; // تنسيق العملة
series1.DataLabels[1].NumberFormat.FormatCode = "dd/mm/yyyy"; // تنسيق التاريخ
series1.DataLabels[2].NumberFormat.FormatCode = "0.00%"; // تنسيق النسبة المئوية
```

بالإضافة إلى ذلك، يمكنك ربط تنسيق تسمية البيانات بخلية مصدر. عند الربط، `NumberFormat` سيتم إعادة تعيينها إلى عامة وتوارثها من الخلية المصدر.

```csharp
series1.DataLabels[2].NumberFormat.IsLinkedToSource = true;
```

## الخطوة 7: حفظ المستند

وأخيرًا، قم بحفظ المستند في الدليل المحدد.

```csharp
doc.Save(dataDir + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

يؤدي هذا إلى حفظ مستندك بالاسم المحدد ويضمن الحفاظ على الرسم البياني الخاص بك مع تسميات البيانات المنسقة.

## خاتمة

تنسيق تسميات البيانات في مخطط بياني باستخدام Aspose.Words لـ .NET يُحسّن بشكل كبير من سهولة قراءة مستندات Word واحترافيتها. باتباع هذا الدليل التفصيلي، ستتمكن الآن من إنشاء مخطط بياني، وإضافة سلاسل بيانات، وتنسيق تسميات البيانات بما يلبي احتياجاتك. يُعد Aspose.Words لـ .NET أداة فعّالة تتيح تخصيص مستندات Word وأتمتتها على نطاق واسع، مما يجعلها أداة قيّمة لمطوري .NET.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟
Aspose.Words for .NET هي مكتبة قوية لإنشاء مستندات Word ومعالجتها وتحويلها برمجيًا باستخدام C#.

### هل يمكنني تنسيق أنواع أخرى من الرسوم البيانية باستخدام Aspose.Words لـ .NET؟
نعم، يدعم Aspose.Words for .NET مجموعة متنوعة من أنواع المخططات، بما في ذلك المخطط الشريطي، والمخطط العمودي، والمخطط الدائري، والمزيد.

### كيف يمكنني الحصول على ترخيص مؤقت لـ Aspose.Words لـ .NET؟
يمكنك الحصول على ترخيص مؤقت [هنا](https://purchase.aspose.com/temporary-license/).

### هل من الممكن ربط تسميات البيانات بالخلايا المصدرية في Excel؟
نعم، يمكنك ربط تسميات البيانات بالخلايا المصدر، مما يسمح بتوارث تنسيق الأرقام من الخلية المصدر.

### أين يمكنني العثور على المزيد من الوثائق التفصيلية لـ Aspose.Words لـ .NET؟
يمكنك العثور على وثائق شاملة [هنا](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}