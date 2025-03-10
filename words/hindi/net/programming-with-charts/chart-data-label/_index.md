---
title: चार्ट डेटा लेबल अनुकूलित करें
linktitle: चार्ट डेटा लेबल अनुकूलित करें
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: चरण-दर-चरण मार्गदर्शिका में .NET के लिए Aspose.Words का उपयोग करके चार्ट डेटा लेबल को कस्टमाइज़ करना सीखें। .NET डेवलपर्स के लिए बिल्कुल सही।
weight: 10
url: /hi/net/programming-with-charts/chart-data-label/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# चार्ट डेटा लेबल अनुकूलित करें

## परिचय

क्या आप अपने .NET एप्लीकेशन को गतिशील और अनुकूलित दस्तावेज़ प्रसंस्करण क्षमताओं के साथ बेहतर बनाना चाहते हैं? .NET के लिए Aspose.Words शायद आपका जवाब हो! इस गाइड में, हम .NET के लिए Aspose.Words का उपयोग करके चार्ट डेटा लेबल को अनुकूलित करने के बारे में विस्तार से जानेंगे, जो Word दस्तावेज़ बनाने, संशोधित करने और परिवर्तित करने के लिए एक शक्तिशाली लाइब्रेरी है। चाहे आप एक अनुभवी डेवलपर हों या अभी शुरुआत कर रहे हों, यह ट्यूटोरियल आपको प्रत्येक चरण से गुजारेगा, यह सुनिश्चित करते हुए कि आप इस टूल का प्रभावी ढंग से उपयोग करना समझते हैं।

## आवश्यक शर्तें

शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

1. Visual Studio: Visual Studio 2019 या बाद का संस्करण स्थापित करें.
2. .NET फ्रेमवर्क: सुनिश्चित करें कि आपके पास .NET फ्रेमवर्क 4.0 या बाद का संस्करण है।
3.  Aspose.Words for .NET: Aspose.Words for .NET को डाउनलोड करें और इंस्टॉल करें[लिंक को डाउनलोड करें](https://releases.aspose.com/words/net/).
4. C# का बुनियादी ज्ञान: C# प्रोग्रामिंग से परिचित होना आवश्यक है।
5.  वैध लाइसेंस: प्राप्त करें[अस्थायी लाइसेंस](https://purchase.aspose.com/temporary-license/) या यहाँ से खरीदें[खरीदें लिंक](https://purchase.aspose.com/buy).

## नामस्थान आयात करें

आरंभ करने के लिए, आपको अपने C# प्रोजेक्ट में आवश्यक नेमस्पेस आयात करने की आवश्यकता है। यह चरण महत्वपूर्ण है क्योंकि यह सुनिश्चित करता है कि आपके पास Aspose.Words द्वारा प्रदान की गई सभी कक्षाओं और विधियों तक पहुँच है।

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Charts;
```

## चरण 1: दस्तावेज़ और दस्तावेज़बिल्डर को आरंभ करें

वर्ड दस्तावेज़ बनाने और उसमें बदलाव करने के लिए, हमें सबसे पहले एक उदाहरण को आरंभीकृत करना होगा`Document` कक्षा और एक`DocumentBuilder` वस्तु।

```csharp
// आपके दस्तावेज़ निर्देशिका का पथ
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### स्पष्टीकरण

- दस्तावेज़ doc: दस्तावेज़ वर्ग का एक नया उदाहरण बनाता है.
- डॉक्यूमेंटबिल्डर बिल्डर: डॉक्यूमेंटबिल्डर डॉक्यूमेंट ऑब्जेक्ट में सामग्री सम्मिलित करने में मदद करता है।

## चरण 2: चार्ट डालें

 इसके बाद, हम दस्तावेज़ में एक बार चार्ट डालेंगे`DocumentBuilder` वस्तु।

```csharp
Shape shape = builder.InsertChart(ChartType.Bar, 432, 252);
Chart chart = shape.Chart;
```

### स्पष्टीकरण

- आकृति आकार: दस्तावेज़ में चार्ट को आकृति के रूप में दर्शाता है।
- builder.InsertChart(ChartType.Bar, 432, 252): निर्दिष्ट आयामों के साथ एक बार चार्ट सम्मिलित करता है।

## चरण 3: चार्ट श्रृंखला तक पहुंचें

डेटा लेबल को अनुकूलित करने के लिए, हमें सबसे पहले चार्ट में श्रृंखला तक पहुंचना होगा।

```csharp
ChartSeries series0 = shape.Chart.Series[0];
```

### स्पष्टीकरण

- चार्ट श्रृंखला श्रृंखला0: चार्ट की पहली श्रृंखला को पुनर्प्राप्त करता है, जिसे हम अनुकूलित करेंगे।

## चरण 4: डेटा लेबल अनुकूलित करें

डेटा लेबल को विभिन्न जानकारी प्रदर्शित करने के लिए अनुकूलित किया जा सकता है। हम लेबल को लीजेंड कुंजी, श्रृंखला नाम और मान दिखाने के लिए कॉन्फ़िगर करेंगे, जबकि श्रेणी का नाम और प्रतिशत छिपाएंगे।

```csharp
ChartDataLabelCollection labels = series0.DataLabels;
labels.ShowLegendKey = true;
labels.ShowLeaderLines = true;
labels.ShowCategoryName = false;
labels.ShowPercentage = false;
labels.ShowSeriesName = true;
labels.ShowValue = true;
labels.Separator = "/";
```

### स्पष्टीकरण

- चार्टडेटालेबलसंग्रह लेबल: श्रृंखला के डेटा लेबल तक पहुँचता है।
- labels.ShowLegendKey: लेजेंड कुंजी प्रदर्शित करता है.
- labels.ShowLeaderLines: डेटा बिंदुओं के बाहर स्थित डेटा लेबल के लिए लीडर लाइनें दिखाता है।
- labels.ShowCategoryName: श्रेणी का नाम छुपाता है.
- labels.ShowPercentage: प्रतिशत मान छुपाता है.
- labels.ShowSeriesName: श्रृंखला का नाम प्रदर्शित करता है.
- labels.ShowValue: डेटा बिंदुओं का मान प्रदर्शित करता है.
- labels.Separator: डेटा लेबल के लिए विभाजक सेट करता है।

## चरण 5: दस्तावेज़ सहेजें

अंत में, दस्तावेज़ को निर्दिष्ट निर्देशिका में सहेजें।

```csharp
doc.Save(dataDir + "WorkingWithCharts.ChartDataLabel.docx");
```

### स्पष्टीकरण

- doc.Save: निर्दिष्ट नाम से दस्तावेज़ को प्रदान की गई निर्देशिका में सहेजता है।

## निष्कर्ष

 बधाई हो! आपने .NET के लिए Aspose.Words का उपयोग करके चार्ट डेटा लेबल को सफलतापूर्वक अनुकूलित किया है। यह लाइब्रेरी Word दस्तावेज़ों को प्रोग्रामेटिक रूप से संभालने के लिए एक मजबूत समाधान प्रदान करती है, जिससे डेवलपर्स के लिए परिष्कृत और गतिशील दस्तावेज़ प्रसंस्करण अनुप्रयोग बनाना आसान हो जाता है।[प्रलेखन](https://reference.aspose.com/words/net/) अधिक सुविधाओं और क्षमताओं का पता लगाने के लिए.

## अक्सर पूछे जाने वाले प्रश्न

### .NET के लिए Aspose.Words क्या है?
Aspose.Words for .NET एक शक्तिशाली दस्तावेज़ प्रसंस्करण लाइब्रेरी है जो डेवलपर्स को प्रोग्रामेटिक रूप से Word दस्तावेज़ बनाने, संशोधित करने और परिवर्तित करने की अनुमति देता है।

### मैं .NET के लिए Aspose.Words कैसे स्थापित करूं?
 आप इसे यहाँ से डाउनलोड और इंस्टॉल कर सकते हैं[लिंक को डाउनलोड करें](https://releases.aspose.com/words/net/)दिए गए इंस्टॉलेशन निर्देशों का पालन करें।

### क्या मैं .NET के लिए Aspose.Words को निःशुल्क आज़मा सकता हूँ?
 हाँ, आप प्राप्त कर सकते हैं[मुफ्त परीक्षण](https://releases.aspose.com/) या एक[अस्थायी लाइसेंस](https://purchase.aspose.com/temporary-license/)उत्पाद का मूल्यांकन करने के लिए.

### क्या Aspose.Words for .NET .NET कोर के साथ संगत है?
हां, .NET के लिए Aspose.Words .NET कोर, .NET स्टैंडर्ड और .NET फ्रेमवर्क के साथ संगत है।

### मुझे .NET के लिए Aspose.Words का समर्थन कहां मिल सकता है?
 आप यहां जा सकते हैं[सहयता मंच](https://forum.aspose.com/c/words/8) Aspose समुदाय और विशेषज्ञों से सहायता और सहयोग के लिए।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
