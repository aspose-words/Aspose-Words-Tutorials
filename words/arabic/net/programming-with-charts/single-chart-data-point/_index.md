---
"description": "تعرّف على كيفية تخصيص نقاط بيانات مخطط فردي باستخدام Aspose.Words لـ .NET في دليل مفصل خطوة بخطوة. حسّن مخططاتك باستخدام علامات وأحجام فريدة."
"linktitle": "تخصيص نقطة بيانات مخطط واحدة في مخطط"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "تخصيص نقطة بيانات مخطط واحدة في مخطط"
"url": "/ar/net/programming-with-charts/single-chart-data-point/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تخصيص نقطة بيانات مخطط واحدة في مخطط

## مقدمة

هل تساءلت يومًا كيف يمكنك إبراز مخططاتك البيانية بنقاط بيانات فريدة؟ حسنًا، اليوم هو يومك المحظوظ! سنتعمق في تخصيص نقطة بيانات واحدة في المخطط البياني باستخدام Aspose.Words لـ .NET. استعدوا لرحلة تعليمية خطوة بخطوة، غنية بالمعلومات، وممتعة وسهلة المتابعة.

## المتطلبات الأساسية

قبل أن نبدأ، دعونا نتأكد من أنك قد حصلت على كل الأساسيات في مكانها:

- Aspose.Words لمكتبة .NET: تأكد من أن لديك الإصدار الأحدث. [تحميله هنا](https://releases.aspose.com/words/net/).
- .NET Framework: تأكد من تثبيت .NET Framework على جهازك.
- الفهم الأساسي لـ C#: سيكون الفهم الأساسي لبرمجة C# مفيدًا.
- بيئة التطوير المتكاملة (IDE): يوصى باستخدام Visual Studio.

## استيراد مساحات الأسماء

أولاً وقبل كل شيء، دعنا نستورد مساحات الأسماء الضرورية لبدء العمل:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## الخطوة 1: تهيئة المستند وDocumentBuilder

حسنًا، لنبدأ بإنشاء مستند جديد وبرنامج DocumentBuilder. سيكون هذا هو لوحة الرسم البياني.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

هنا، `dataDir` هو مسار الدليل الذي ستحفظ فيه مستندك. `DocumentBuilder` تساعد الفئة في إنشاء المستند.

## الخطوة 2: إدراج مخطط

الآن، لنُدرج مخططًا خطيًا في المستند. سيكون هذا ساحةً لتخصيص نقاط البيانات.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
```

ال `InsertChart` تأخذ الطريقة نوع المخطط، والعرض، والارتفاع كمعلمات. في هذه الحالة، نُدرج مخططًا خطيًا بعرض 432 وارتفاع 252.

## الخطوة 3: الوصول إلى سلسلة المخططات

الآن، حان وقت الوصول إلى السلسلة في مخططنا البياني. يمكن أن يحتوي المخطط البياني على عدة سلاسل، وكل سلسلة تحتوي على نقاط بيانات.

```csharp
ChartSeries series0 = chart.Series[0];
ChartSeries series1 = chart.Series[1];
```

هنا، نقوم بالوصول إلى السلسلتين الأوليين في مخططنا. 

## الخطوة 4: تخصيص نقاط البيانات

هنا يأتي السحر! لنُخصّص نقاط بيانات مُحدّدة ضمن سلسلتنا.

```csharp
ChartDataPointCollection dataPointCollection = series0.DataPoints;
ChartDataPoint dataPoint00 = dataPointCollection[0];
ChartDataPoint dataPoint01 = dataPointCollection[1];
```

نقوم بجلب نقاط البيانات من السلسلة الأولى. الآن، لنُخصّص هذه النقاط.

### تخصيص نقطة البيانات 00

```csharp
dataPoint00.Explosion = 50;
dataPoint00.Marker.Symbol = MarkerSymbol.Circle;
dataPoint00.Marker.Size = 15;
```

ل `dataPoint00`، نقوم بإعداد انفجار (مفيد للمخططات الدائرية)، وتغيير رمز العلامة إلى دائرة، وتعيين حجم العلامة إلى 15.

### تخصيص نقطة البيانات 01

```csharp
dataPoint01.Marker.Symbol = MarkerSymbol.Diamond;
dataPoint01.Marker.Size = 20;
```

ل `dataPoint01`، نقوم بتغيير رمز العلامة إلى ماسة وضبط حجم العلامة إلى 20.

### تخصيص نقطة البيانات في السلسلة 1

```csharp
ChartDataPoint dataPoint12 = series1.DataPoints[2];
dataPoint12.InvertIfNegative = true;
dataPoint12.Marker.Symbol = MarkerSymbol.Star;
dataPoint12.Marker.Size = 20;
```

بالنسبة لنقطة البيانات الثالثة في `series1`، نقوم بتعيينه لعكس القيمة إذا كانت سلبية، وتغيير رمز العلامة إلى نجمة، وتعيين حجم العلامة إلى 20.

## الخطوة 5: حفظ المستند

وأخيرًا، دعنا نحفظ مستندنا مع كل التخصيصات.

```csharp
doc.Save(dataDir + "WorkingWithCharts.SingleChartDataPoint.docx");
```

يحفظ هذا السطر المستند في الدليل المحدد بالاسم `WorkingWithCharts.SingleChartDataPoint.docx`.

## خاتمة

ها قد انتهيت! لقد نجحت في تخصيص نقاط بيانات فردية في مخطط باستخدام Aspose.Words لـ .NET. بتعديل بعض الخصائص، يمكنك جعل مخططاتك أكثر إفادة وجاذبية بصريًا. لذا، جرّب علامات وأحجامًا مختلفة لمعرفة الأنسب لبياناتك.

## الأسئلة الشائعة

### هل يمكنني تخصيص نقاط البيانات في أنواع أخرى من الرسوم البيانية؟

بالتأكيد! يمكنك تخصيص نقاط البيانات في أنواع مختلفة من المخططات، بما في ذلك المخططات الشريطية والمخططات الدائرية وغيرها. العملية متشابهة في مختلف أنواع المخططات.

### هل من الممكن إضافة تسميات مخصصة لنقاط البيانات؟

نعم، يمكنك إضافة تسميات مخصصة إلى نقاط البيانات باستخدام `ChartDataPoint.Label` يتيح لك هذا توفير سياق أكبر لكل نقطة بيانات.

### كيف يمكنني إزالة نقطة بيانات من سلسلة؟

يمكنك إزالة نقطة بيانات عن طريق تعيين رؤيتها على "خطأ" باستخدام `dataPoint.IsVisible = false`.

### هل يمكنني استخدام الصور كعلامات لنقاط البيانات؟

على الرغم من أن Aspose.Words لا يدعم استخدام الصور مباشرة كعلامات، إلا أنه يمكنك إنشاء أشكال مخصصة واستخدامها كعلامات.

### هل من الممكن تحريك نقاط البيانات في الرسم البياني؟

لا يدعم Aspose.Words for .NET تحريك نقاط بيانات المخططات. مع ذلك، يمكنك إنشاء مخططات متحركة باستخدام أدوات أخرى وتضمينها في مستندات Word.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}