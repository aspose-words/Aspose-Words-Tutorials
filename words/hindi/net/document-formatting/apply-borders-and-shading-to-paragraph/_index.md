---
title: वर्ड डॉक्यूमेंट में पैराग्राफ़ पर बॉर्डर और शेडिंग लागू करें
linktitle: वर्ड डॉक्यूमेंट में पैराग्राफ़ पर बॉर्डर और शेडिंग लागू करें
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों में पैराग्राफ़ पर बॉर्डर और शेडिंग लागू करें। अपने दस्तावेज़ फ़ॉर्मेटिंग को बेहतर बनाने के लिए हमारे चरण-दर-चरण मार्गदर्शिका का पालन करें।
weight: 10
url: /hi/net/document-formatting/apply-borders-and-shading-to-paragraph/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# वर्ड डॉक्यूमेंट में पैराग्राफ़ पर बॉर्डर और शेडिंग लागू करें

## परिचय

अरे, क्या आपने कभी सोचा है कि अपने वर्ड डॉक्यूमेंट को कुछ फैंसी बॉर्डर और शेडिंग के साथ कैसे पॉप बनाया जाए? खैर, आप सही जगह पर हैं! आज, हम अपने पैराग्राफ को और भी बेहतर बनाने के लिए .NET के लिए Aspose.Words की दुनिया में उतर रहे हैं। कल्पना करें कि आपका डॉक्यूमेंट सिर्फ़ कुछ कोड लाइनों के साथ एक पेशेवर डिज़ाइनर के काम की तरह आकर्षक दिखाई दे। शुरू करने के लिए तैयार हैं? चलिए शुरू करते हैं!

## आवश्यक शर्तें

इससे पहले कि हम अपनी आस्तीन ऊपर चढ़ाएं और कोडिंग में उतरें, आइए सुनिश्चित करें कि हमारे पास वह सब कुछ है जिसकी हमें ज़रूरत है। यहाँ आपकी त्वरित चेकलिस्ट है:

-  Aspose.Words for .NET: आपको यह लाइब्रेरी इंस्टॉल करनी होगी। आप इसे यहाँ से डाउनलोड कर सकते हैं[Aspose वेबसाइट](https://releases.aspose.com/words/net/).
- विकास वातावरण: विजुअल स्टूडियो या कोई अन्य IDE जो .NET का समर्थन करता है।
- C# का बुनियादी ज्ञान: कोड स्निपेट को समझने और उसमें सुधार करने के लिए पर्याप्त।
- वैध लाइसेंस: या तो[अस्थायी लाइसेंस](https://purchase.aspose.com/temporary-license/) या किसी से खरीदा हुआ[असपोज](https://purchase.aspose.com/buy).

## नामस्थान आयात करें

कोड में कूदने से पहले, हमें यह सुनिश्चित करना होगा कि हमारे पास हमारे प्रोजेक्ट में आवश्यक नेमस्पेस आयातित हैं। इससे Aspose.Words की सभी शानदार सुविधाएँ हमारे लिए सुलभ हो जाती हैं।

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using Aspose.Words.Drawing;
using System.Drawing;
```

अब, चलिए इस प्रक्रिया को छोटे-छोटे चरणों में विभाजित करते हैं। प्रत्येक चरण में एक शीर्षक और विस्तृत विवरण होगा। तैयार हैं? चलिए शुरू करते हैं!

## चरण 1: अपनी दस्तावेज़ निर्देशिका सेट करें

सबसे पहले, हमें अपने सुंदर स्वरूपित दस्तावेज़ को सहेजने के लिए एक स्थान की आवश्यकता है। आइए अपने दस्तावेज़ निर्देशिका का पथ सेट करें।

```csharp
// दस्तावेज़ निर्देशिका का पथ.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 यह निर्देशिका वह जगह है जहाँ आपका अंतिम दस्तावेज़ सहेजा जाएगा।`"YOUR DOCUMENT DIRECTORY"` आपके मशीन पर वास्तविक पथ के साथ.

## चरण 2: नया दस्तावेज़ और दस्तावेज़बिल्डर बनाएँ

 इसके बाद, हमें एक नया दस्तावेज़ और एक बनाना होगा`DocumentBuilder` वस्तु.`DocumentBuilder` यह हमारी जादुई छड़ी है जो हमें दस्तावेज़ में हेरफेर करने देती है।

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` ऑब्जेक्ट हमारे संपूर्ण वर्ड दस्तावेज़ का प्रतिनिधित्व करता है, और`DocumentBuilder` हमें सामग्री जोड़ने और प्रारूपित करने में मदद करता है.

## चरण 3: पैराग्राफ़ की सीमाएँ निर्धारित करें

अब, आइए अपने पैराग्राफ़ में कुछ स्टाइलिश बॉर्डर जोड़ें। हम टेक्स्ट से दूरी तय करेंगे और अलग-अलग बॉर्डर स्टाइल सेट करेंगे।

```csharp
BorderCollection borders = builder.ParagraphFormat.Borders;
borders.DistanceFromText = 20;
borders[BorderType.Left].LineStyle = LineStyle.Double;
borders[BorderType.Right].LineStyle = LineStyle.Double;
borders[BorderType.Top].LineStyle = LineStyle.Double;
borders[BorderType.Bottom].LineStyle = LineStyle.Double;
```

यहाँ, हमने टेक्स्ट और बॉर्डर के बीच 20 पॉइंट की दूरी तय की है। सभी तरफ (बाएं, दाएं, ऊपर, नीचे) बॉर्डर डबल लाइन में सेट किए गए हैं। फैंसी है, है न?

## चरण 4: पैराग्राफ़ पर छायांकन लागू करें

बॉर्डर बहुत बढ़िया हैं, लेकिन चलिए इसे कुछ शेडिंग के साथ एक पायदान ऊपर ले चलते हैं। हम अपने पैराग्राफ को अलग दिखाने के लिए रंगों के मिश्रण के साथ विकर्ण क्रॉस पैटर्न का उपयोग करेंगे।

```csharp
Shading shading = builder.ParagraphFormat.Shading;
shading.Texture = TextureIndex.TextureDiagonalCross;
shading.BackgroundPatternColor = System.Drawing.Color.LightCoral;
shading.ForegroundPatternColor = System.Drawing.Color.LightSalmon;
```

इस चरण में, हमने पृष्ठभूमि रंग के रूप में हल्के कोरल और अग्रभूमि रंग के रूप में हल्के सैल्मन के साथ एक विकर्ण क्रॉस बनावट लागू की। यह आपके पैराग्राफ को डिजाइनर कपड़ों में सजाने जैसा है!

## चरण 5: पैराग्राफ़ में टेक्स्ट जोड़ें

बिना पाठ के पैराग्राफ़ क्या होता है? आइए एक नमूना वाक्य जोड़ें और देखें कि हमारा फ़ॉर्मेटिंग कैसे काम करता है।

```csharp
builder.Write("I'm a formatted paragraph with double border and nice shading.");
```

यह लाइन हमारे टेक्स्ट को डॉक्यूमेंट में डाल देती है। सरल, लेकिन अब यह एक स्टाइलिश फ्रेम और छायांकित पृष्ठभूमि में लिपटा हुआ है।

## चरण 6: दस्तावेज़ सहेजें

अंत में, अब हमारे काम को सहेजने का समय आ गया है। आइए दस्तावेज़ को वर्णनात्मक नाम के साथ निर्दिष्ट निर्देशिका में सहेज लें।

```csharp
doc.Save(dataDir + "DocumentFormatting.ApplyBordersAndShadingToParagraph.doc");
```

 यह हमारे दस्तावेज़ को इस नाम से सहेजता है`DocumentFormatting.ApplyBordersAndShadingToParagraph.doc` उस निर्देशिका में जिसे हमने पहले निर्दिष्ट किया था।

## निष्कर्ष

और अब यह हो गया! कोड की कुछ ही पंक्तियों के साथ, हमने एक सादे पैराग्राफ को एक आकर्षक सामग्री में बदल दिया है। Aspose.Words for .NET आपके दस्तावेज़ों में पेशेवर दिखने वाली फ़ॉर्मेटिंग जोड़ना अविश्वसनीय रूप से आसान बनाता है। चाहे आप कोई रिपोर्ट, पत्र या कोई भी दस्तावेज़ तैयार कर रहे हों, ये तरकीबें आपको एक बेहतरीन छाप छोड़ने में मदद करेंगी। तो आगे बढ़ें, इसे आज़माएँ और अपने दस्तावेज़ों को जीवंत होते देखें!

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं प्रत्येक बॉर्डर के लिए अलग-अलग लाइन शैलियों का उपयोग कर सकता हूँ?  
 बिलकुल! Aspose.Words for .NET आपको प्रत्येक बॉर्डर को व्यक्तिगत रूप से कस्टमाइज़ करने की अनुमति देता है। बस सेट करें`LineStyle` प्रत्येक बॉर्डर प्रकार के लिए, जैसा कि गाइड में दिखाया गया है।

### अन्य कौन सी छायांकन बनावटें उपलब्ध हैं?  
 आप कई तरह की बनावट का इस्तेमाल कर सकते हैं, जैसे कि ठोस, क्षैतिज पट्टी, ऊर्ध्वाधर पट्टी, और भी बहुत कुछ।[Aspose दस्तावेज़ीकरण](https://reference.aspose.com/words/net/) पूरी सूची के लिए यहां क्लिक करें.

### मैं बॉर्डर का रंग कैसे बदल सकता हूँ?  
 आप बॉर्डर का रंग सेट कर सकते हैं`Color` प्रत्येक सीमा के लिए संपत्ति। उदाहरण के लिए,`borders[BorderType.Left].Color = Color.Red;`.

### क्या पाठ के किसी विशिष्ट भाग पर बॉर्डर और छायांकन लागू करना संभव है?  
 हां, आप इसका उपयोग करके पाठ के विशिष्ट भागों पर बॉर्डर और छायांकन लागू कर सकते हैं`Run` वस्तु के भीतर`DocumentBuilder`.

### क्या मैं एकाधिक पैराग्राफों के लिए इस प्रक्रिया को स्वचालित कर सकता हूँ?  
निश्चित रूप से! आप अपने पैराग्राफ़ में लूप कर सकते हैं और समान बॉर्डर और शेडिंग सेटिंग को प्रोग्रामेटिक रूप से लागू कर सकते हैं।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
