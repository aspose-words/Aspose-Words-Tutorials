---
title: मेटाफ़ाइल्स को Svg में बदलें
linktitle: मेटाफ़ाइल्स को Svg में बदलें
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: इस विस्तृत, चरण-दर-चरण गाइड के साथ .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों में मेटाफ़ाइल्स को SVG में बदलें। सभी स्तरों के डेवलपर्स के लिए बिल्कुल सही।
weight: 10
url: /hi/net/programming-with-htmlsaveoptions/convert-metafiles-to-svg/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# मेटाफ़ाइल्स को Svg में बदलें

## परिचय

नमस्ते, कोडिंग के शौकीनों! क्या आपने कभी सोचा है कि .NET के लिए Aspose.Words का उपयोग करके अपने Word दस्तावेज़ों में मेटाफ़ाइल्स को SVG में कैसे बदला जाए? खैर, अब आपके लिए एक बेहतरीन अनुभव होने वाला है! आज, हम Aspose.Words की दुनिया में गहराई से उतरेंगे, जो एक शक्तिशाली लाइब्रेरी है जो दस्तावेज़ों में हेरफेर को आसान बनाती है। इस ट्यूटोरियल के अंत तक, आप मेटाफ़ाइल्स को SVG में बदलने में माहिर हो जाएँगे, जिससे आपके Word दस्तावेज़ अधिक बहुमुखी और दिखने में आकर्षक बन जाएँगे। तो, चलिए शुरू करते हैं, है न?

## आवश्यक शर्तें

इससे पहले कि हम विस्तृत विवरण में जाएं, आइए सुनिश्चित करें कि हमारे पास शुरुआत करने के लिए आवश्यक सभी चीजें मौजूद हैं:

1.  .NET के लिए Aspose.Words: आप इसे यहाँ से डाउनलोड कर सकते हैं[Aspose रिलीज़ पेज](https://releases.aspose.com/words/net/).
2. .NET फ्रेमवर्क: सुनिश्चित करें कि आपके मशीन पर .NET फ्रेमवर्क स्थापित है।
3. विकास पर्यावरण: विजुअल स्टूडियो जैसा कोई भी IDE काम करेगा।
4. C# का बुनियादी ज्ञान: C# से थोड़ी परिचितता उपयोगी होगी, लेकिन यदि आप नौसिखिए हैं तो चिंता न करें - हम आपको सब कुछ विस्तार से समझाएंगे।

## नामस्थान आयात करें

सबसे पहले, आइए आयात करें। अपने C# प्रोजेक्ट में, आपको आवश्यक नामस्थान आयात करने की आवश्यकता होगी। Aspose.Words कार्यक्षमताओं तक पहुँचने के लिए यह महत्वपूर्ण है।

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

अब जबकि हमने अपनी पूर्वावश्यकताएं और नामस्थान व्यवस्थित कर लिए हैं, तो आइए मेटाफाइल्स को SVG में परिवर्तित करने के लिए चरण-दर-चरण मार्गदर्शिका पर गौर करें।

## चरण 1: दस्तावेज़ और दस्तावेज़बिल्डर को आरंभ करें

 ठीक है, चलिए एक नया वर्ड डॉक्यूमेंट बनाकर और उसे आरंभ करके काम शुरू करते हैं`DocumentBuilder` यह बिल्डर हमें अपने दस्तावेज़ में सामग्री जोड़ने में मदद करेगा।

```csharp
// दस्तावेज़ निर्देशिका का पथ.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 यहाँ, हम एक नया दस्तावेज़ और एक दस्तावेज़ बिल्डर आरंभ करते हैं।`dataDir` वेरिएबल आपके डॉक्यूमेंट डायरेक्टरी का पथ रखता है जहां आप अपनी फ़ाइलें सहेजेंगे।

## चरण 2: दस्तावेज़ में पाठ जोड़ें

 अब, चलिए अपने दस्तावेज़ में कुछ टेक्स्ट जोड़ते हैं। हम इसका उपयोग करेंगे`Write` की विधि`DocumentBuilder` पाठ सम्मिलित करने के लिए.

```csharp
builder.Write("Here is an SVG image: ");
```

यह पंक्ति आपके दस्तावेज़ में "यहाँ एक SVG छवि है: " पाठ जोड़ती है। आप जिस SVG छवि को सम्मिलित करने जा रहे हैं, उसके लिए कुछ संदर्भ या विवरण प्रदान करना हमेशा एक अच्छा विचार है।

## चरण 3: SVG छवि डालें

 अब, मज़ेदार भाग के लिए! हम अपने दस्तावेज़ में एक SVG छवि डालेंगे`InsertHtml` तरीका।

```csharp
builder.InsertHtml(
    @"<svg height='210' width='500'>
    <polygon points='100,10 40,198 190,78 10,78 160,198' 
    style='fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;' />
</svg> ");
```

यह स्निपेट दस्तावेज़ में एक SVG छवि सम्मिलित करता है। SVG कोड निर्दिष्ट बिंदुओं, रंगों और शैलियों के साथ एक सरल बहुभुज को परिभाषित करता है। अपनी आवश्यकताओं के अनुसार SVG कोड को अनुकूलित करने के लिए स्वतंत्र महसूस करें।

## चरण 4: HtmlSaveOptions परिभाषित करें

 यह सुनिश्चित करने के लिए कि हमारी मेटाफ़ाइलें SVG के रूप में सहेजी गई हैं, हम परिभाषित करेंगे`HtmlSaveOptions` और सेट करें`MetafileFormat`संपत्ति को`HtmlMetafileFormat.Svg`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    MetafileFormat = HtmlMetafileFormat.Svg
};
```

यह Aspose.Words को बताता है कि दस्तावेज़ में किसी भी मेटाफ़ाइल को HTML में निर्यात करते समय SVG के रूप में सहेजना है।

## चरण 5: दस्तावेज़ सहेजें

 अंत में, चलिए अपना दस्तावेज़ सेव करते हैं। हम इसका उपयोग करेंगे`Save` की विधि`Document` क्लास में जाकर डायरेक्टरी पथ और सेव विकल्प पास करें।

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToSvg.html", saveOptions);
```

 यह पंक्ति दस्तावेज़ को फ़ाइल नाम के साथ निर्दिष्ट निर्देशिका में सहेजती है`WorkingWithHtmlSaveOptions.ConvertMetafilesToSvg.html` . द`saveOptions` सुनिश्चित करें कि मेटाफ़ाइलें SVG में परिवर्तित हो गई हैं।

## निष्कर्ष

और अब यह हो गया! आपने Aspose.Words for .NET का उपयोग करके अपने Word दस्तावेज़ में मेटाफ़ाइल्स को SVG में सफलतापूर्वक परिवर्तित कर लिया है। बहुत बढ़िया, है न? कोड की सिर्फ़ कुछ पंक्तियों के साथ, आप स्केलेबल वेक्टर ग्राफ़िक्स जोड़कर अपने Word दस्तावेज़ों को बेहतर बना सकते हैं, जिससे वे ज़्यादा गतिशील और दिखने में आकर्षक बन सकते हैं। तो, आगे बढ़ें और अपने प्रोजेक्ट में इसे आज़माएँ। हैप्पी कोडिंग!

## अक्सर पूछे जाने वाले प्रश्न

### .NET के लिए Aspose.Words क्या है?
Aspose.Words for .NET एक शक्तिशाली लाइब्रेरी है जो आपको C# का उपयोग करके प्रोग्रामेटिक रूप से Word दस्तावेज़ बनाने, संशोधित करने और परिवर्तित करने की अनुमति देती है।

### क्या मैं .NET कोर के साथ .NET के लिए Aspose.Words का उपयोग कर सकता हूं?
हां, Aspose.Words for .NET .NET कोर का समर्थन करता है, जो इसे विभिन्न .NET अनुप्रयोगों के लिए बहुमुखी बनाता है।

### मैं .NET के लिए Aspose.Words का निःशुल्क परीक्षण कैसे प्राप्त कर सकता हूँ?
 आप यहां से निःशुल्क परीक्षण डाउनलोड कर सकते हैं[Aspose रिलीज़ पेज](https://releases.aspose.com/).

### क्या Aspose.Words का उपयोग करके अन्य छवि प्रारूपों को SVG में परिवर्तित करना संभव है?
हां, Aspose.Words मेटाफाइल सहित विभिन्न छवि प्रारूपों को SVG में परिवर्तित करने का समर्थन करता है।

### मैं .NET के लिए Aspose.Words का दस्तावेज़ कहां पा सकता हूं?
 आप विस्तृत दस्तावेज यहाँ पा सकते हैं[Aspose दस्तावेज़ीकरण पृष्ठ](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
