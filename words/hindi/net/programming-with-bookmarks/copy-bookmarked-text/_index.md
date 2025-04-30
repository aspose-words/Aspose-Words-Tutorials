---
"description": ".NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों के बीच बुकमार्क किए गए टेक्स्ट को आसानी से कॉपी करें। इस चरण-दर-चरण मार्गदर्शिका से जानें कि कैसे।"
"linktitle": "बुकमार्क किए गए टेक्स्ट को वर्ड डॉक्यूमेंट में कॉपी करें"
"second_title": "Aspose.Words दस्तावेज़ प्रसंस्करण API"
"title": "बुकमार्क किए गए टेक्स्ट को वर्ड डॉक्यूमेंट में कॉपी करें"
"url": "/hi/net/programming-with-bookmarks/copy-bookmarked-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# बुकमार्क किए गए टेक्स्ट को वर्ड डॉक्यूमेंट में कॉपी करें

## परिचय

क्या आपको कभी एक Word दस्तावेज़ से दूसरे में विशिष्ट अनुभागों को कॉपी करने की आवश्यकता महसूस हुई है? खैर, आप भाग्यशाली हैं! इस ट्यूटोरियल में, हम आपको Aspose.Words for .NET का उपयोग करके एक Word दस्तावेज़ से दूसरे में बुकमार्क किए गए टेक्स्ट को कॉपी करने का तरीका बताएंगे। चाहे आप एक गतिशील रिपोर्ट बना रहे हों या दस्तावेज़ निर्माण को स्वचालित कर रहे हों, यह मार्गदर्शिका आपके लिए प्रक्रिया को सरल बनाएगी।

## आवश्यक शर्तें

इससे पहले कि हम आगे बढ़ें, सुनिश्चित करें कि आपके पास निम्नलिखित चीजें हैं:

- .NET लाइब्रेरी के लिए Aspose.Words: आप इसे यहाँ से डाउनलोड कर सकते हैं [यहाँ](https://releases.aspose.com/words/net/).
- विकास वातावरण: विजुअल स्टूडियो या कोई अन्य .NET विकास वातावरण।
- C# का मूलभूत ज्ञान: C# प्रोग्रामिंग और .NET फ्रेमवर्क से परिचित होना।

## नामस्थान आयात करें

आरंभ करने के लिए, सुनिश्चित करें कि आपके प्रोजेक्ट में आवश्यक नामस्थान आयातित हैं:

```csharp
using Aspose.Words;
using Aspose.Words.Import;
using Aspose.Words.Bookmark;
```

## चरण 1: स्रोत दस्तावेज़ लोड करें

सबसे पहले, आपको उस स्रोत दस्तावेज़ को लोड करना होगा जिसमें वह बुकमार्क किया गया पाठ है जिसे आप कॉपी करना चाहते हैं।

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Bookmarks.docx");
```

यहाँ, `dataDir` आपके दस्तावेज़ निर्देशिका का पथ है, और `Bookmarks.docx` स्रोत दस्तावेज़ है.

## चरण 2: बुकमार्क की पहचान करें

इसके बाद, उस बुकमार्क की पहचान करें जिसे आप स्रोत दस्तावेज़ से कॉपी करना चाहते हैं।

```csharp
Bookmark srcBookmark = srcDoc.Range.Bookmarks["MyBookmark1"];
```

प्रतिस्थापित करें `"MyBookmark1"` अपने बुकमार्क के वास्तविक नाम के साथ.

## चरण 3: गंतव्य दस्तावेज़ बनाएँ

अब, एक नया दस्तावेज़ बनाएं जहां बुकमार्क किया गया पाठ कॉपी किया जाएगा।

```csharp
Document dstDoc = new Document();
CompositeNode dstNode = dstDoc.LastSection.Body;
```

## चरण 4: बुकमार्क की गई सामग्री आयात करें

यह सुनिश्चित करने के लिए कि शैलियाँ और स्वरूपण संरक्षित हैं, उपयोग करें `NodeImporter` बुकमार्क की गई सामग्री को स्रोत दस्तावेज़ से गंतव्य दस्तावेज़ में आयात करने के लिए।

```csharp
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);
AppendBookmarkedText(importer, srcBookmark, dstNode);
```

## चरण 5: AppendBookmarkedText विधि को परिभाषित करें

यहाँ पर जादू होता है। बुकमार्क किए गए टेक्स्ट की प्रतिलिपि बनाने के लिए एक विधि परिभाषित करें:

```csharp
private void AppendBookmarkedText(NodeImporter importer, Bookmark srcBookmark, CompositeNode dstNode)
{
    Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
    Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

    if (startPara == null || endPara == null)
        throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");

    if (startPara.ParentNode != endPara.ParentNode)
        throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");

    Node endNode = endPara.NextSibling;

    for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
    {
        Node newNode = importer.ImportNode(curNode, true);
        dstNode.AppendChild(newNode);
    }
}
```

## चरण 6: गंतव्य दस्तावेज़ सहेजें

अंत में, कॉपी की गई सामग्री को सत्यापित करने के लिए गंतव्य दस्तावेज़ को सहेजें।

```csharp
dstDoc.Save(dataDir + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

## निष्कर्ष

और बस! आपने .NET के लिए Aspose.Words का उपयोग करके बुकमार्क किए गए टेक्स्ट को एक Word दस्तावेज़ से दूसरे में सफलतापूर्वक कॉपी कर लिया है। यह विधि दस्तावेज़ हेरफेर कार्यों को स्वचालित करने के लिए शक्तिशाली है, जिससे आपका वर्कफ़्लो अधिक कुशल और सुव्यवस्थित हो जाता है।

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं एक साथ कई बुकमार्क कॉपी कर सकता हूँ?
हां, आप एकाधिक बुकमार्क्स को पुनरावृत्त कर सकते हैं और प्रत्येक को कॉपी करने के लिए समान विधि का उपयोग कर सकते हैं।

### यदि बुकमार्क न मिले तो क्या होगा?
The `Range.Bookmarks` संपत्ति वापस मिलेगी `null`, इसलिए अपवादों से बचने के लिए सुनिश्चित करें कि आप इस मामले को संभालें।

### क्या मैं मूल बुकमार्क का स्वरूपण संरक्षित रख सकता हूँ?
बिलकुल! `ImportFormatMode.KeepSourceFormatting` यह सुनिश्चित करता है कि मूल स्वरूपण संरक्षित रहे.

### क्या बुकमार्क किये गये पाठ के आकार की कोई सीमा है?
इसकी कोई विशिष्ट सीमा नहीं है, लेकिन अत्यंत बड़े दस्तावेज़ों के साथ प्रदर्शन भिन्न हो सकता है।

### क्या मैं विभिन्न वर्ड दस्तावेज़ प्रारूपों के बीच पाठ की प्रतिलिपि बना सकता हूँ?
हां, Aspose.Words विभिन्न Word प्रारूपों का समर्थन करता है, और यह विधि इन प्रारूपों में काम करती है।


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}