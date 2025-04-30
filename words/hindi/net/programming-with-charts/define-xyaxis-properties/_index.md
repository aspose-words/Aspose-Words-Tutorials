---
"description": "इस चरण-दर-चरण मार्गदर्शिका के साथ .NET के लिए Aspose.Words का उपयोग करके चार्ट में XY अक्ष गुणधर्मों को परिभाषित करना सीखें। .NET डेवलपर्स के लिए बिल्कुल सही।"
"linktitle": "चार्ट में XY अक्ष गुण परिभाषित करें"
"second_title": "Aspose.Words दस्तावेज़ प्रसंस्करण API"
"title": "चार्ट में XY अक्ष गुण परिभाषित करें"
"url": "/hi/net/programming-with-charts/define-xyaxis-properties/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# चार्ट में XY अक्ष गुण परिभाषित करें

## परिचय

चार्ट डेटा को विज़ुअलाइज़ करने के लिए एक शक्तिशाली उपकरण हैं। जब आपको गतिशील चार्ट के साथ पेशेवर दस्तावेज़ बनाने की आवश्यकता होती है, तो Aspose.Words for .NET एक अमूल्य लाइब्रेरी है। यह लेख आपको Aspose.Words for .NET का उपयोग करके चार्ट में XY अक्ष गुणों को परिभाषित करने की प्रक्रिया के माध्यम से ले जाएगा, स्पष्टता और समझने में आसानी सुनिश्चित करने के लिए प्रत्येक चरण को तोड़ देगा।

## आवश्यक शर्तें

कोडिंग शुरू करने से पहले, आपके पास कुछ पूर्व-आवश्यकताएं होनी चाहिए:

1. Aspose.Words for .NET: सुनिश्चित करें कि आपके पास Aspose.Words for .NET लाइब्रेरी है। आप ऐसा कर सकते हैं [यहाँ पर डाउनलोड करो](https://releases.aspose.com/words/net/).
2. विकास वातावरण: आपको विजुअल स्टूडियो जैसे एकीकृत विकास वातावरण (IDE) की आवश्यकता है।
3. .NET फ्रेमवर्क: सुनिश्चित करें कि आपका विकास वातावरण .NET विकास के लिए सेट किया गया है।
4. C# का बुनियादी ज्ञान: यह मार्गदर्शिका मानती है कि आपको C# प्रोग्रामिंग की बुनियादी समझ है।

## नामस्थान आयात करें

आरंभ करने के लिए, आपको अपने प्रोजेक्ट में आवश्यक नेमस्पेस आयात करने की आवश्यकता है। यह सुनिश्चित करता है कि आपके पास दस्तावेज़ और चार्ट बनाने और उनमें हेरफेर करने के लिए आवश्यक सभी क्लास और विधियों तक पहुँच है।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

हम इस प्रक्रिया को सरल चरणों में विभाजित करेंगे, जिनमें से प्रत्येक चरण चार्ट में XY अक्ष गुणों को परिभाषित करने के विशिष्ट भाग पर ध्यान केंद्रित करेगा।

## चरण 1: दस्तावेज़ और दस्तावेज़बिल्डर को आरंभ करें

सबसे पहले, आपको एक नया दस्तावेज़ आरंभ करना होगा और `DocumentBuilder` वस्तु. `DocumentBuilder` दस्तावेज़ में सामग्री सम्मिलित करने में मदद करता है.

```csharp
// आपके दस्तावेज़ निर्देशिका का पथ 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## चरण 2: चार्ट डालें

इसके बाद, आप दस्तावेज़ में एक चार्ट डालेंगे। इस उदाहरण में, हम एक एरिया चार्ट का उपयोग करेंगे। आप चार्ट के आयामों को आवश्यकतानुसार अनुकूलित कर सकते हैं।

```csharp
// चार्ट डालें
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
Chart chart = shape.Chart;
```

## चरण 3: डिफ़ॉल्ट श्रृंखला साफ़ करें और कस्टम डेटा जोड़ें

डिफ़ॉल्ट रूप से, चार्ट में कुछ पूर्व-निर्धारित श्रृंखलाएँ होंगी। हम इन्हें हटा देंगे और अपनी कस्टम डेटा श्रृंखला जोड़ देंगे।

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
	new DateTime[]
	{
		new DateTime(2002, 01, 01), new DateTime(2002, 06, 01), new DateTime(2002, 07, 01),
		new DateTime(2002, 08, 01), new DateTime(2002, 09, 01)
	},
	new double[] { 640, 320, 280, 120, 150 });
```

## चरण 4: एक्स अक्ष गुण परिभाषित करें

अब, एक्स अक्ष के लिए गुण परिभाषित करने का समय आ गया है। इसमें श्रेणी प्रकार सेट करना, अक्ष क्रॉसिंग को अनुकूलित करना और टिक मार्क और लेबल समायोजित करना शामिल है।

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.CategoryType = AxisCategoryType.Category;
xAxis.Crosses = AxisCrosses.Custom;
xAxis.CrossesAt = 3; // वाई अक्ष (सैकड़ों) की प्रदर्शन इकाइयों में मापा जाता है।
xAxis.ReverseOrder = true;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
xAxis.TickLabelOffset = 200;
```

## चरण 5: Y अक्ष गुण परिभाषित करें

इसी तरह, आप Y अक्ष के लिए गुण सेट करेंगे। इसमें टिक लेबल की स्थिति, प्रमुख और लघु इकाइयाँ, डिस्प्ले यूनिट और स्केलिंग सेट करना शामिल है।

```csharp
ChartAxis yAxis = chart.AxisY;
yAxis.TickLabelPosition = AxisTickLabelPosition.High;
yAxis.MajorUnit = 100;
yAxis.MinorUnit = 50;
yAxis.DisplayUnit.Unit = AxisBuiltInUnit.Hundreds;
yAxis.Scaling.Minimum = new AxisBound(100);
yAxis.Scaling.Maximum = new AxisBound(700);
```

## चरण 6: दस्तावेज़ सहेजें

अंत में, दस्तावेज़ को अपनी निर्दिष्ट निर्देशिका में सहेजें। यह अनुकूलित चार्ट के साथ वर्ड दस्तावेज़ तैयार करेगा।

```csharp
doc.Save(dataDir + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

## निष्कर्ष

Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ों में चार्ट बनाना और उन्हें कस्टमाइज़ करना एक बार जब आप इसमें शामिल चरणों को समझ लेते हैं, तो यह बहुत आसान हो जाता है। इस गाइड ने आपको चार्ट में XY अक्ष गुणों को परिभाषित करने की प्रक्रिया से परिचित कराया है, दस्तावेज़ को आरंभ करने से लेकर अंतिम उत्पाद को सहेजने तक। इन कौशलों के साथ, आप विस्तृत, पेशेवर दिखने वाले चार्ट बना सकते हैं जो आपके दस्तावेज़ों को बेहतर बनाते हैं।

## अक्सर पूछे जाने वाले प्रश्न

### मैं .NET के लिए Aspose.Words के साथ किस प्रकार के चार्ट बना सकता हूँ?
आप विभिन्न प्रकार के चार्ट बना सकते हैं, जिनमें क्षेत्र, बार, रेखा, पाई आदि शामिल हैं।

### मैं .NET के लिए Aspose.Words कैसे स्थापित करूं?
आप .NET के लिए Aspose.Words को यहां से डाउनलोड कर सकते हैं [यहाँ](https://releases.aspose.com/words/net/) और दिए गए स्थापना निर्देशों का पालन करें।

### क्या मैं अपने चार्ट के स्वरूप को अनुकूलित कर सकता हूँ?
हां, .NET के लिए Aspose.Words रंग, फ़ॉन्ट और अक्ष गुणों सहित चार्ट के व्यापक अनुकूलन की अनुमति देता है।

### क्या .NET के लिए Aspose.Words का निःशुल्क परीक्षण उपलब्ध है?
हां, आप निःशुल्क परीक्षण प्राप्त कर सकते हैं [यहाँ](https://releases.aspose.com/).

### मैं और अधिक ट्यूटोरियल और दस्तावेज़ कहां पा सकता हूं?
आप अधिक ट्यूटोरियल और विस्तृत दस्तावेज़ यहाँ पा सकते हैं [.NET के लिए Aspose.Words दस्तावेज़न पृष्ठ](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}