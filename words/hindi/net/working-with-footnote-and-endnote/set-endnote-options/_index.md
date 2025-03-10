---
title: एंडनोट विकल्प सेट करें
linktitle: एंडनोट विकल्प सेट करें
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: इस व्यापक चरण-दर-चरण मार्गदर्शिका के साथ .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों में एंडनोट विकल्प सेट करना सीखें।
weight: 10
url: /hi/net/working-with-footnote-and-endnote/set-endnote-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# एंडनोट विकल्प सेट करें

## परिचय

क्या आप एंडनोट्स को कुशलतापूर्वक प्रबंधित करके अपने वर्ड दस्तावेज़ों को बेहतर बनाना चाहते हैं? आगे न देखें! इस ट्यूटोरियल में, हम आपको .NET के लिए Aspose.Words का उपयोग करके वर्ड दस्तावेज़ों में एंडनोट विकल्प सेट करने की प्रक्रिया से परिचित कराएँगे। इस गाइड के अंत तक, आप अपने दस्तावेज़ की ज़रूरतों के हिसाब से एंडनोट्स को कस्टमाइज़ करने में माहिर हो जाएँगे।

## आवश्यक शर्तें

ट्यूटोरियल में शामिल होने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ मौजूद हैं:

-  Aspose.Words for .NET: सुनिश्चित करें कि आपके पास Aspose.Words for .NET लाइब्रेरी स्थापित है। आप इसे यहाँ से डाउनलोड कर सकते हैं[यहाँ](https://releases.aspose.com/words/net/).
- विकास परिवेश: एक विकास परिवेश स्थापित करें, जैसे कि विजुअल स्टूडियो।
- C# का बुनियादी ज्ञान: C# प्रोग्रामिंग की बुनियादी समझ लाभदायक होगी।

## नामस्थान आयात करें

आरंभ करने के लिए, आपको आवश्यक नामस्थान आयात करने होंगे। ये नामस्थान Word दस्तावेज़ों में हेरफेर करने के लिए आवश्यक कक्षाओं और विधियों तक पहुँच प्रदान करते हैं।

```csharp
using Aspose.Words;
using Aspose.Words.Notes;
```

## चरण 1: दस्तावेज़ लोड करें

 सबसे पहले, उस डॉक्यूमेंट को लोड करें जहाँ हम एंडनोट विकल्प सेट करना चाहते हैं।`Document` इसे पूरा करने के लिए Aspose.Words लाइब्रेरी से .

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## चरण 2: डॉक्यूमेंटबिल्डर को आरंभ करें

 इसके बाद, हम आरंभ करेंगे`DocumentBuilder`क्लास. यह क्लास दस्तावेज़ में सामग्री जोड़ने का एक सरल तरीका प्रदान करता है.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## चरण 3: टेक्स्ट जोड़ें और एंडनोट डालें

 अब, आइए दस्तावेज़ में कुछ पाठ जोड़ें और एक एंडनोट डालें।`InsertFootnote` की विधि`DocumentBuilder` क्लास हमें दस्तावेज़ में एंडनोट्स जोड़ने की अनुमति देता है।

```csharp
builder.Write("Some text");
builder.InsertFootnote(FootnoteType.Endnote, "Footnote text.");
```

## चरण 4: एंडनोट विकल्पों तक पहुंचें और उन्हें सेट करें

 एंडनोट विकल्पों को अनुकूलित करने के लिए, हमें एक्सेस करने की आवश्यकता है`EndnoteOptions` की संपत्ति`Document` फिर हम पुनः आरंभ नियम और स्थिति जैसे विभिन्न विकल्प सेट कर सकते हैं।

```csharp
EndnoteOptions option = doc.EndnoteOptions;
option.RestartRule = FootnoteNumberingRule.RestartPage;
option.Position = EndnotePosition.EndOfSection;
```

## चरण 5: दस्तावेज़ सहेजें

 अंत में, आइए दस्तावेज़ को अपडेट किए गए एंडनोट विकल्पों के साथ सेव करें।`Save` की विधि`Document` क्लास हमें दस्तावेज़ को निर्दिष्ट निर्देशिका में सहेजने की अनुमति देता है।

```csharp
doc.Save(dataDir + "WorkingWithFootnotes.SetEndnoteOptions.docx");
```

## निष्कर्ष

.NET के लिए Aspose.Words का उपयोग करके अपने Word दस्तावेज़ों में एंडनोट विकल्प सेट करना इन सरल चरणों के साथ बहुत आसान है। एंडनोट्स के पुनरारंभ नियम और स्थिति को अनुकूलित करके, आप अपने दस्तावेज़ों को विशिष्ट आवश्यकताओं को पूरा करने के लिए तैयार कर सकते हैं। Aspose.Words के साथ, Word दस्तावेज़ों में हेरफेर करने की शक्ति आपकी उंगलियों पर है।

## अक्सर पूछे जाने वाले प्रश्न

### .NET के लिए Aspose.Words क्या है?
Aspose.Words for .NET, Word दस्तावेज़ों को प्रोग्रामेटिक रूप से मैनिपुलेट करने के लिए एक शक्तिशाली लाइब्रेरी है। यह डेवलपर्स को विभिन्न प्रारूपों में Word दस्तावेज़ बनाने, संशोधित करने और परिवर्तित करने की अनुमति देता है।

### क्या मैं Aspose.Words का निःशुल्क उपयोग कर सकता हूँ?
 आप Aspose.Words का निःशुल्क परीक्षण कर सकते हैं। विस्तारित उपयोग के लिए, आप यहाँ से लाइसेंस खरीद सकते हैं[यहाँ](https://purchase.aspose.com/buy).

### एंडनोट्स क्या हैं?
एंडनोट्स किसी अनुभाग या दस्तावेज़ के अंत में रखे गए संदर्भ या नोट्स होते हैं। वे अतिरिक्त जानकारी या उद्धरण प्रदान करते हैं।

### मैं एंडनोट्स के स्वरूप को कैसे अनुकूलित करूँ?
 आप एंडनोट विकल्पों जैसे कि क्रमांकन, स्थिति और पुनः आरंभ नियमों को अनुकूलित कर सकते हैं`EndnoteOptions` .NET के लिए Aspose.Words में क्लास।

### मैं .NET के लिए Aspose.Words पर अधिक दस्तावेज़ कहां पा सकता हूं?
 विस्तृत दस्तावेज यहां उपलब्ध है[.NET दस्तावेज़ीकरण के लिए Aspose.Words](https://reference.aspose.com/words/net/) पृष्ठ.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
