---
"description": "Aspose.Words for .NET में प्रत्यय के बिना फ़ॉन्ट प्रतिस्थापन को प्रबंधित करना सीखें। अपने दस्तावेज़ों को हर बार सही दिखने के लिए हमारे चरण-दर-चरण मार्गदर्शिका का पालन करें।"
"linktitle": "प्रत्यय के बिना प्रतिस्थापन प्राप्त करें"
"second_title": "Aspose.Words दस्तावेज़ प्रसंस्करण API"
"title": "प्रत्यय के बिना प्रतिस्थापन प्राप्त करें"
"url": "/hi/net/working-with-fonts/get-substitution-without-suffixes/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# प्रत्यय के बिना प्रतिस्थापन प्राप्त करें

## परिचय

.NET के लिए Aspose.Words का उपयोग करके फ़ॉन्ट प्रतिस्थापन को प्रबंधित करने के बारे में इस व्यापक गाइड में आपका स्वागत है। यदि आपने कभी अपने दस्तावेज़ों में फ़ॉन्ट सही ढंग से प्रदर्शित नहीं होने से संघर्ष किया है, तो आप सही जगह पर आए हैं। यह ट्यूटोरियल आपको प्रत्ययों के बिना फ़ॉन्ट प्रतिस्थापन को कुशलतापूर्वक संभालने के लिए चरण-दर-चरण प्रक्रिया के माध्यम से ले जाएगा।

## आवश्यक शर्तें

ट्यूटोरियल में आगे बढ़ने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

- C# का मूलभूत ज्ञान: C# प्रोग्रामिंग को समझने से चरणों का पालन करना और उन्हें क्रियान्वित करना आसान हो जाएगा।
- .NET लाइब्रेरी के लिए Aspose.Words: लाइब्रेरी को डाउनलोड करें और इंस्टॉल करें [लिंक को डाउनलोड करें](https://releases.aspose.com/words/net/).
- विकास परिवेश: अपना कोड लिखने और चलाने के लिए Visual Studio जैसा विकास परिवेश सेट करें।
- नमूना दस्तावेज़: एक नमूना दस्तावेज़ (जैसे, `Rendering.docx`) इस ट्यूटोरियल के दौरान काम करने के लिए।

## नामस्थान आयात करें

सबसे पहले, हमें Aspose.Words द्वारा प्रदान की गई कक्षाओं और विधियों तक पहुँचने के लिए आवश्यक नामस्थानों को आयात करना होगा।

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System.Collections.Generic;
```

## चरण 1: दस्तावेज़ निर्देशिका निर्धारित करें

शुरू करने के लिए, वह निर्देशिका निर्दिष्ट करें जहाँ आपका दस्तावेज़ स्थित है। इससे आपको उस दस्तावेज़ को खोजने में मदद मिलती है जिस पर आप काम करना चाहते हैं।

```csharp
// आपके दस्तावेज़ निर्देशिका का पथ
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## चरण 2: प्रतिस्थापन चेतावनी हैंडलर सेट करें

इसके बाद, हमें एक चेतावनी हैंडलर सेट अप करना होगा जो हमें दस्तावेज़ प्रसंस्करण के दौरान फ़ॉन्ट प्रतिस्थापन होने पर सूचित करेगा। यह किसी भी फ़ॉन्ट समस्या को पकड़ने और संभालने के लिए महत्वपूर्ण है।

```csharp
DocumentSubstitutionWarnings substitutionWarningHandler = new DocumentSubstitutionWarnings();
Document doc = new Document(dataDir + "Rendering.docx");
doc.WarningCallback = substitutionWarningHandler;
```

## चरण 3: कस्टम फ़ॉन्ट स्रोत जोड़ें

इस चरण में, हम कस्टम फ़ॉन्ट स्रोत जोड़ेंगे ताकि यह सुनिश्चित हो सके कि Aspose.Words सही फ़ॉन्ट ढूँढ़ सके और उनका उपयोग कर सके। यह विशेष रूप से तब उपयोगी होता है जब आपके पास कस्टम निर्देशिकाओं में संग्रहीत विशिष्ट फ़ॉन्ट हों।

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(FontSettings.DefaultInstance.GetFontsSources());

FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);

FontSourceBase[] updatedFontSources = fontSources.ToArray();
FontSettings.DefaultInstance.SetFontsSources(updatedFontSources);
```

इस कोड में:
- हम वर्तमान फ़ॉन्ट स्रोतों को पुनः प्राप्त करते हैं और एक नया जोड़ते हैं `FolderFontSource` हमारे कस्टम फ़ॉन्ट निर्देशिका की ओर इशारा करते हुए (`C:\\MyFonts\\`).
- फिर हम इस नई सूची के साथ फ़ॉन्ट स्रोतों को अद्यतन करते हैं।

## चरण 4: दस्तावेज़ सहेजें

अंत में, फ़ॉन्ट प्रतिस्थापन सेटिंग लागू करने के बाद दस्तावेज़ को सहेजें। इस ट्यूटोरियल के लिए, हम इसे PDF के रूप में सहेजेंगे।

```csharp
doc.Save(dataDir + "WorkingWithFonts.GetSubstitutionWithoutSuffixes.pdf");
```

## चरण 5: चेतावनी हैंडलर क्लास बनाएँ

चेतावनियों को प्रभावी ढंग से संभालने के लिए, एक कस्टम क्लास बनाएं जो इसे लागू करता है `IWarningCallback` इंटरफ़ेस. यह क्लास किसी भी फ़ॉन्ट प्रतिस्थापन चेतावनी को कैप्चर और लॉग करेगा.

```csharp
public class DocumentSubstitutionWarnings : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            FontWarnings.Warning(info);
    }

    public WarningInfoCollection FontWarnings = new WarningInfoCollection();
}
```

इस वर्ग में:
- The `Warning` विधि फ़ॉन्ट प्रतिस्थापन से संबंधित चेतावनियाँ कैप्चर करती है।
- The `FontWarnings` संग्रह इन चेतावनियों को आगे के निरीक्षण या लॉगिंग के लिए संग्रहीत करता है।

## निष्कर्ष

अब आप .NET के लिए Aspose.Words का उपयोग करके प्रत्यय के बिना फ़ॉन्ट प्रतिस्थापन को संभालने की प्रक्रिया में महारत हासिल कर चुके हैं। यह ज्ञान सुनिश्चित करेगा कि आपके दस्तावेज़ सिस्टम पर उपलब्ध फ़ॉन्ट की परवाह किए बिना अपनी इच्छित उपस्थिति बनाए रखें। Aspose.Words की शक्ति का पूरी तरह से उपयोग करने के लिए विभिन्न सेटिंग्स और स्रोतों के साथ प्रयोग करते रहें।

## अक्सर पूछे जाने वाले प्रश्न

### मैं एकाधिक कस्टम निर्देशिकाओं से फ़ॉन्ट का उपयोग कैसे कर सकता हूं?

आप कई जोड़ सकते हैं `FolderFontSource` उदाहरणों के लिए `fontSources` फ़ॉन्ट स्रोतों को सूचीबद्ध करें और तदनुसार अद्यतन करें।

### मैं .NET के लिए Aspose.Words का निःशुल्क परीक्षण संस्करण कहां से डाउनलोड कर सकता हूं?

आप यहां से निःशुल्क परीक्षण डाउनलोड कर सकते हैं [Aspose निःशुल्क परीक्षण पृष्ठ](https://releases.aspose.com/).

### क्या मैं अनेक प्रकार की चेतावनियों को संभाल सकता हूँ? `IWarningCallback`?

हां `IWarningCallback` इंटरफ़ेस आपको न केवल फ़ॉन्ट प्रतिस्थापन बल्कि विभिन्न प्रकार की चेतावनियों को संभालने की अनुमति देता है।

### मुझे Aspose.Words के लिए समर्थन कहां मिल सकता है?

सहायता के लिए, यहां जाएं [Aspose.Words समर्थन मंच](https://forum.aspose.com/c/words/8).

### क्या अस्थायी लाइसेंस खरीदना संभव है?

हां, आप अस्थायी लाइसेंस प्राप्त कर सकते हैं [अस्थायी लाइसेंस पृष्ठ](https://purchase.aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}