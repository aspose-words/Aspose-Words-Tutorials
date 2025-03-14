---
title: चार्ट में डेटा लेबल की संख्या को प्रारूपित करें
linktitle: चार्ट में डेटा लेबल की संख्या को प्रारूपित करें
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: इस चरण-दर-चरण मार्गदर्शिका के साथ .NET के लिए Aspose.Words का उपयोग करके चार्ट में डेटा लेबल को फ़ॉर्मेट करना सीखें। अपने Word दस्तावेज़ों को आसानी से बेहतर बनाएँ।
weight: 10
url: /hi/net/programming-with-charts/format-number-of-data-label/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# चार्ट में डेटा लेबल की संख्या को प्रारूपित करें

## परिचय

आकर्षक और जानकारीपूर्ण दस्तावेज़ बनाने में अक्सर अच्छी तरह से फ़ॉर्मेट किए गए डेटा लेबल वाले चार्ट शामिल होते हैं। यदि आप एक .NET डेवलपर हैं और अपने Word दस्तावेज़ों को परिष्कृत चार्ट के साथ बेहतर बनाना चाहते हैं, तो .NET के लिए Aspose.Words एक शानदार लाइब्रेरी है जो आपको ऐसा करने में मदद करेगी। यह ट्यूटोरियल आपको Aspose.Words for .NET का उपयोग करके चार्ट में नंबर लेबल को फ़ॉर्मेट करने की प्रक्रिया के बारे में चरण दर चरण बताएगा।

## आवश्यक शर्तें

कोड में आगे बढ़ने से पहले, कुछ पूर्व-आवश्यकताएं हैं जिनका आपको पालन करना होगा:

-  Aspose.Words for .NET: सुनिश्चित करें कि आपके पास Aspose.Words for .NET लाइब्रेरी स्थापित है। यदि आपने इसे अभी तक स्थापित नहीं किया है, तो आप[यहाँ पर डाउनलोड करो](https://releases.aspose.com/words/net/).
- विकास पर्यावरण: आपके पास .NET विकास पर्यावरण होना चाहिए। Visual Studio अत्यधिक अनुशंसित है।
- C# का बुनियादी ज्ञान: C# प्रोग्रामिंग से परिचित होना आवश्यक है क्योंकि इस ट्यूटोरियल में C# कोड लिखना और समझना शामिल है।
-  अस्थायी लाइसेंस: Aspose.Words को बिना किसी सीमा के उपयोग करने के लिए, आप एक प्राप्त कर सकते हैं[अस्थायी लाइसेंस](https://purchase.aspose.com/temporary-license/).

अब, आइए चार्ट में संख्या लेबल को प्रारूपित करने की चरण-दर-चरण प्रक्रिया को समझें।

## नामस्थान आयात करें

सबसे पहले, हमें .NET के लिए Aspose.Words के साथ काम करने के लिए आवश्यक नेमस्पेस आयात करने की आवश्यकता है। अपनी C# फ़ाइल के शीर्ष पर निम्न पंक्तियाँ जोड़ें:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## चरण 1: अपनी दस्तावेज़ निर्देशिका सेट करें

इससे पहले कि आप अपने वर्ड डॉक्यूमेंट में बदलाव करना शुरू करें, आपको वह डायरेक्टरी निर्दिष्ट करनी होगी जहाँ आपका डॉक्यूमेंट सेव किया जाएगा। यह बाद में सेव ऑपरेशन के लिए ज़रूरी है।

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 प्रतिस्थापित करें`"YOUR DOCUMENT DIRECTORY"` आपके दस्तावेज़ निर्देशिका के वास्तविक पथ के साथ.

## चरण 2: दस्तावेज़ और दस्तावेज़बिल्डर को आरंभ करें

 अगला कदम एक नया आरंभ करना है`Document` और एक`DocumentBuilder` . द`DocumentBuilder` एक सहायक वर्ग है जो हमें दस्तावेज़ सामग्री का निर्माण करने की अनुमति देता है।

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## चरण 3: दस्तावेज़ में चार्ट डालें

 अब, आइए दस्तावेज़ में एक चार्ट डालें`DocumentBuilder`इस ट्यूटोरियल में, हम एक उदाहरण के रूप में लाइन चार्ट का उपयोग करेंगे।

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
chart.Title.Text = "Data Labels With Different Number Format";
```

यहां, हम एक विशिष्ट चौड़ाई और ऊंचाई के साथ एक लाइन चार्ट सम्मिलित करते हैं, और चार्ट शीर्षक सेट करते हैं।

## चरण 4: डिफ़ॉल्ट श्रृंखला साफ़ करें और नई श्रृंखला जोड़ें

डिफ़ॉल्ट रूप से, चार्ट में कुछ पूर्व-निर्मित श्रृंखलाएँ होंगी। हमें इन्हें साफ़ करना होगा और विशिष्ट डेटा बिंदुओं के साथ अपनी खुद की श्रृंखला जोड़नी होगी।

```csharp
// डिफ़ॉल्ट रूप से उत्पन्न श्रृंखला को हटाएँ.
chart.Series.Clear();

// कस्टम डेटा बिंदुओं के साथ नई श्रृंखला जोड़ें.
ChartSeries series1 = chart.Series.Add("Aspose Series 1", 
	new string[] { "Category 1", "Category 2", "Category 3" }, 
	new double[] { 2.5, 1.5, 3.5 });
```

## चरण 5: डेटा लेबल सक्षम करें

चार्ट पर डेटा लेबल प्रदर्शित करने के लिए, हमें उन्हें अपनी श्रृंखला के लिए सक्षम करना होगा।

```csharp
series1.HasDataLabels = true;
series1.DataLabels.ShowValue = true;
```

## चरण 6: डेटा लेबल को प्रारूपित करें

इस ट्यूटोरियल का मुख्य उद्देश्य डेटा लेबल को फ़ॉर्मेट करना है। हम प्रत्येक डेटा लेबल पर अलग-अलग संख्या फ़ॉर्मेट लागू कर सकते हैं।

```csharp
series1.DataLabels[0].NumberFormat.FormatCode = "\"$\"#,##0.00"; // मुद्रा प्रारूप
series1.DataLabels[1].NumberFormat.FormatCode = "dd/mm/yyyy"; // तारिख का प्रारूप
series1.DataLabels[2].NumberFormat.FormatCode = "0.00%"; // प्रतिशत प्रारूप
```

 इसके अतिरिक्त, आप डेटा लेबल के प्रारूप को स्रोत सेल से लिंक कर सकते हैं। लिंक किए जाने पर,`NumberFormat` सामान्य पर रीसेट कर दिया जाएगा और स्रोत सेल से विरासत में प्राप्त किया जाएगा।

```csharp
series1.DataLabels[2].NumberFormat.IsLinkedToSource = true;
```

## चरण 7: दस्तावेज़ सहेजें

अंत में, दस्तावेज़ को निर्दिष्ट निर्देशिका में सहेजें।

```csharp
doc.Save(dataDir + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

यह आपके दस्तावेज़ को निर्दिष्ट नाम से सहेजता है और यह सुनिश्चित करता है कि स्वरूपित डेटा लेबल वाला आपका चार्ट संरक्षित रहे।

## निष्कर्ष

Aspose.Words for .NET का उपयोग करके चार्ट में डेटा लेबल को फ़ॉर्मेट करना आपके Word दस्तावेज़ों की पठनीयता और व्यावसायिकता को बहुत बढ़ा सकता है। इस चरण-दर-चरण मार्गदर्शिका का पालन करके, अब आप चार्ट बनाने, डेटा श्रृंखला जोड़ने और अपनी ज़रूरतों को पूरा करने के लिए डेटा लेबल को फ़ॉर्मेट करने में सक्षम होंगे। Aspose.Words for .NET एक शक्तिशाली उपकरण है जो Word दस्तावेज़ों के व्यापक अनुकूलन और स्वचालन की अनुमति देता है, जिससे यह .NET डेवलपर्स के लिए एक अमूल्य संपत्ति बन जाता है।

## अक्सर पूछे जाने वाले प्रश्न

### .NET के लिए Aspose.Words क्या है?
.NET के लिए Aspose.Words C# का उपयोग करके प्रोग्रामेटिक रूप से Word दस्तावेज़ों को बनाने, हेरफेर करने और परिवर्तित करने के लिए एक शक्तिशाली लाइब्रेरी है।

### क्या मैं .NET के लिए Aspose.Words के साथ अन्य प्रकार के चार्ट को प्रारूपित कर सकता हूं?
हां, .NET के लिए Aspose.Words विभिन्न प्रकार के चार्ट का समर्थन करता है, जिसमें बार, कॉलम, पाई और बहुत कुछ शामिल है।

### मैं .NET के लिए Aspose.Words हेतु अस्थायी लाइसेंस कैसे प्राप्त करूं?
आप अस्थायी लाइसेंस प्राप्त कर सकते हैं[यहाँ](https://purchase.aspose.com/temporary-license/).

### क्या एक्सेल में डेटा लेबल को स्रोत कक्षों से लिंक करना संभव है?
हां, आप डेटा लेबल को स्रोत कक्षों से लिंक कर सकते हैं, जिससे स्रोत कक्ष से संख्या प्रारूप प्राप्त किया जा सकता है।

### मैं .NET के लिए Aspose.Words के अधिक विस्तृत दस्तावेज़ कहां पा सकता हूं?
 आप विस्तृत दस्तावेज पा सकते हैं[यहाँ](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
