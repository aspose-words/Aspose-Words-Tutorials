---
title: प्रतिस्थापित पर दस्तावेज़ डालें
linktitle: प्रतिस्थापित पर दस्तावेज़ डालें
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: हमारे विस्तृत, चरण-दर-चरण गाइड के साथ .NET के लिए Aspose.Words का उपयोग करके एक Word दस्तावेज़ को दूसरे में सहजता से सम्मिलित करना सीखें। दस्तावेज़ प्रसंस्करण को सुव्यवस्थित करने की चाह रखने वाले डेवलपर्स के लिए बिल्कुल सही।
weight: 10
url: /hi/net/clone-and-combine-documents/insert-document-at-replace/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# प्रतिस्थापित पर दस्तावेज़ डालें

## परिचय

हेलो, डॉक्यूमेंट मास्टर्स! क्या आपने कभी खुद को कोड में इतना डूबा हुआ पाया है कि यह पता लगाने की कोशिश कर रहे हैं कि एक वर्ड डॉक्यूमेंट को दूसरे में कैसे आसानी से डाला जाए? घबराएँ नहीं, क्योंकि आज हम .NET के लिए Aspose.Words की दुनिया में गोता लगाने जा रहे हैं ताकि यह काम आसान हो जाए। हम एक विस्तृत, चरण-दर-चरण गाइड के माध्यम से चलेंगे कि कैसे इस शक्तिशाली लाइब्रेरी का उपयोग किसी खोज और प्रतिस्थापन ऑपरेशन के दौरान विशिष्ट बिंदुओं पर दस्तावेज़ डालने के लिए किया जाए। Aspose.Words जादूगर बनने के लिए तैयार हैं? चलिए शुरू करते हैं!

## आवश्यक शर्तें

इससे पहले कि हम कोड में प्रवेश करें, कुछ चीजें हैं जिन्हें आपको ध्यान में रखना होगा:

-  विज़ुअल स्टूडियो: सुनिश्चित करें कि आपके मशीन पर विज़ुअल स्टूडियो इंस्टॉल है। यदि आपके पास अभी तक यह नहीं है, तो आप इसे यहाँ से डाउनलोड कर सकते हैं[यहाँ](https://visualstudio.microsoft.com/).
-  .NET के लिए Aspose.Words: आपको Aspose.Words लाइब्रेरी की आवश्यकता होगी। आप इसे यहाँ से प्राप्त कर सकते हैं[Aspose वेबसाइट](https://releases.aspose.com/words/net/).
- बुनियादी C# ज्ञान: C# और .NET की बुनियादी समझ आपको इस ट्यूटोरियल को आगे बढ़ाने में मदद करेगी।

ठीक है, अब इन बातों से निपटकर, आइए कुछ कोड के साथ अपने हाथ गंदे करें!

## नामस्थान आयात करें

सबसे पहले, हमें Aspose.Words के साथ काम करने के लिए आवश्यक नेमस्पेस आयात करने की आवश्यकता है। यह किसी प्रोजेक्ट को शुरू करने से पहले अपने सभी उपकरण इकट्ठा करने जैसा है। अपनी C# फ़ाइल के शीर्ष पर इन using निर्देशों को जोड़ें:

```csharp
using System;
using System.Text.RegularExpressions;
using Aspose.Words;
using Aspose.Words.Replacing;
using Aspose.Words.Tables;
```

अब जब हमने अपनी पूर्व-आवश्यकताएँ तय कर ली हैं, तो चलिए इस प्रक्रिया को छोटे-छोटे चरणों में विभाजित करते हैं। प्रत्येक चरण महत्वपूर्ण है और हमें हमारे लक्ष्य के करीब ले जाएगा।

## चरण 1: दस्तावेज़ निर्देशिका सेट अप करना

सबसे पहले, हमें वह डायरेक्टरी निर्दिष्ट करनी होगी जहाँ हमारे दस्तावेज़ संग्रहीत हैं। यह बड़े प्रदर्शन से पहले मंच तैयार करने जैसा है।

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 प्रतिस्थापित करें`"YOUR DOCUMENT DIRECTORY"` अपनी निर्देशिका के पथ के साथ। यह वह जगह है जहाँ आपके दस्तावेज़ रहेंगे और साँस लेंगे।

## चरण 2: मुख्य दस्तावेज़ लोड करें

इसके बाद, हम मुख्य दस्तावेज़ को लोड करते हैं जिसमें हम दूसरा दस्तावेज़ सम्मिलित करना चाहते हैं। इसे हमारे मुख्य मंच के रूप में सोचें जहाँ सारी क्रियाएँ होंगी।

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

यह कोड निर्दिष्ट निर्देशिका से मुख्य दस्तावेज़ लोड करता है।

## चरण 3: खोजें और बदलें विकल्प सेट करें

हम अपने दस्तावेज़ को जिस विशिष्ट स्थान पर सम्मिलित करना चाहते हैं, उसे खोजने के लिए हम ढूँढ़ें और बदलें कार्यक्षमता का उपयोग करते हैं। यह हमारे नए जोड़े गए दस्तावेज़ के लिए सटीक स्थान खोजने के लिए मानचित्र का उपयोग करने जैसा है।

```csharp
FindReplaceOptions options = new FindReplaceOptions
{
    Direction = FindReplaceDirection.Backward,
    ReplacingCallback = new InsertDocumentAtReplaceHandler()
};
```

यहां, हम दिशा को पीछे की ओर सेट कर रहे हैं और एक कस्टम कॉलबैक हैंडलर निर्दिष्ट कर रहे हैं जिसे हम आगे परिभाषित करेंगे।

## चरण 4: प्रतिस्थापन ऑपरेशन निष्पादित करें

अब, हम अपने मुख्य दस्तावेज़ को एक विशिष्ट प्लेसहोल्डर टेक्स्ट की तलाश करने और उसे कुछ भी न रखने के लिए कहते हैं, जबकि दूसरे दस्तावेज़ को सम्मिलित करने के लिए हमारे कस्टम कॉलबैक का उपयोग करते हैं।

```csharp
mainDoc.Range.Replace(new Regex("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

यह कोड खोज और प्रतिस्थापन ऑपरेशन निष्पादित करता है, और फिर अद्यतन दस्तावेज़ को सहेजता है।

## चरण 5: कस्टम रिप्लेसिंग कॉलबैक हैंडलर बनाएं

हमारा कस्टम कॉलबैक हैंडलर वह जगह है जहाँ जादू होता है। यह हैंडलर परिभाषित करेगा कि खोज और प्रतिस्थापन ऑपरेशन के दौरान दस्तावेज़ प्रविष्टि कैसे की जाती है।

```csharp
private class InsertDocumentAtReplaceHandler : IReplacingCallback
{
    ReplaceAction IReplacingCallback.Replacing(ReplacingArgs args)
    {
        Document subDoc = new Document(dataDir + "Document insertion 2.docx");

        // मिलान पाठ वाले पैराग्राफ के बाद एक दस्तावेज़ डालें।
        Paragraph para = (Paragraph)args.MatchNode.ParentNode;
        InsertDocument(para, subDoc);

        // मिलान पाठ वाले पैराग्राफ को हटाएँ.
        para.Remove();
        return ReplaceAction.Skip;
    }
}
```

यहां, हम सम्मिलित किए जाने वाले दस्तावेज़ को लोड करते हैं और फिर सम्मिलन करने के लिए एक सहायक विधि को कॉल करते हैं।

## चरण 6: दस्तावेज़ सम्मिलित करने की विधि निर्धारित करें

हमारी पहेली का अंतिम टुकड़ा वह विधि है जो वास्तव में दस्तावेज़ को निर्दिष्ट स्थान पर सम्मिलित करती है।

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    // जाँच करें कि प्रविष्टि गंतव्य पैराग्राफ़ है या तालिका
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;

        // स्रोत दस्तावेज़ से नोड्स आयात करने के लिए NodeImporter बनाएँ
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        // स्रोत दस्तावेज़ के अनुभागों में सभी ब्लॉक-स्तरीय नोड्स के माध्यम से लूप करें
        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        {
            foreach (Node srcNode in srcSection.Body)
            {
                // किसी अनुभाग के अंतिम खाली पैराग्राफ को छोड़ दें
                if (srcNode.NodeType == NodeType.Paragraph)
                {
                    Paragraph para = (Paragraph)srcNode;
                    if (para.IsEndOfSection && !para.HasChildNodes)
                        continue;
                }

                // नोड को गंतव्य में आयात करें और डालें
                Node newNode = importer.ImportNode(srcNode, true);
                destinationParent.InsertAfter(newNode, insertionDestination);
                insertionDestination = newNode;
            }
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}

```

यह विधि सम्मिलित किए जाने वाले दस्तावेज़ से नोड्स को आयात करने तथा उन्हें मुख्य दस्तावेज़ में सही स्थान पर रखने का कार्य करती है।

## निष्कर्ष

और अब यह आपके लिए है! .NET के लिए Aspose.Words का उपयोग करके एक दस्तावेज़ को दूसरे में सम्मिलित करने के लिए एक व्यापक मार्गदर्शिका। इन चरणों का पालन करके, आप दस्तावेज़ असेंबली और हेरफेर कार्यों को आसानी से स्वचालित कर सकते हैं। चाहे आप एक दस्तावेज़ प्रबंधन प्रणाली बना रहे हों या बस अपने दस्तावेज़ प्रसंस्करण वर्कफ़्लो को सुव्यवस्थित करने की आवश्यकता हो, Aspose.Words आपका भरोसेमंद सहायक है।

## अक्सर पूछे जाने वाले प्रश्न

### .NET के लिए Aspose.Words क्या है?
Aspose.Words for .NET, Word दस्तावेज़ों को प्रोग्रामेटिक रूप से मैनिपुलेट करने के लिए एक शक्तिशाली लाइब्रेरी है। यह आपको Word दस्तावेज़ों को आसानी से बनाने, संशोधित करने, परिवर्तित करने और संसाधित करने की अनुमति देता है।

### क्या मैं एक साथ कई दस्तावेज़ सम्मिलित कर सकता हूँ?
हां, आप दस्तावेज़ों के संग्रह पर पुनरावृत्ति करके एकाधिक प्रविष्टियों को संभालने के लिए कॉलबैक हैंडलर को संशोधित कर सकते हैं।

### क्या कोई निःशुल्क परीक्षण उपलब्ध है?
 बिलकुल! आप यहाँ से निःशुल्क परीक्षण डाउनलोड कर सकते हैं[यहाँ](https://releases.aspose.com/).

### मैं Aspose.Words के लिए समर्थन कैसे प्राप्त करूं?
 आप यहां जाकर सहायता प्राप्त कर सकते हैं[Aspose.Words फ़ोरम](https://forum.aspose.com/c/words/8).

### क्या मैं सम्मिलित दस्तावेज़ का स्वरूपण रख सकता हूँ?
 हां`NodeImporter` क्लास आपको यह निर्दिष्ट करने की अनुमति देता है कि एक दस्तावेज़ से दूसरे दस्तावेज़ में नोड्स आयात करते समय स्वरूपण कैसे प्रबंधित किया जाए।
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
