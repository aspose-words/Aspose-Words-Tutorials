---
title: Word दस्तावेज़ में बुकमार्क दिखाएँ छुपाएँ
linktitle: Word दस्तावेज़ में बुकमार्क दिखाएँ छुपाएँ
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: हमारे चरण-दर-चरण गाइड के साथ .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ में बुकमार्क को गतिशील रूप से दिखाना या छिपाना सीखें। डेवलपर्स के लिए बिल्कुल सही।
weight: 10
url: /hi/net/programming-with-bookmarks/show-hide-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word दस्तावेज़ में बुकमार्क दिखाएँ छुपाएँ

## परिचय

क्या आपको कभी अपने Word दस्तावेज़ के कुछ हिस्सों को गतिशील रूप से छिपाने या दिखाने की ज़रूरत महसूस हुई है? खैर, आप भाग्यशाली हैं! Aspose.Words for .NET के साथ, आप अपने दस्तावेज़ों में बुकमार्क की गई सामग्री की दृश्यता को आसानी से प्रबंधित कर सकते हैं। यह ट्यूटोरियल आपको Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में बुकमार्क दिखाने और छिपाने की प्रक्रिया से परिचित कराएगा। हम कोड को चरण दर चरण तोड़ेंगे, इसलिए चाहे आप एक अनुभवी डेवलपर हों या एक नौसिखिया, आपको यह गाइड अनुसरण करने में आसान लगेगी।

## आवश्यक शर्तें

इससे पहले कि हम कोड में उतरें, आइए सुनिश्चित करें कि आपके पास वह सब कुछ है जो आपको चाहिए:

1.  Aspose.Words for .NET: सुनिश्चित करें कि आपके पास Aspose.Words for .NET लाइब्रेरी स्थापित है। यदि नहीं, तो आप इसे डाउनलोड कर सकते हैं[यहाँ](https://releases.aspose.com/words/net/).
2. विकास पर्यावरण: विजुअल स्टूडियो जैसा एक IDE.
3. C# का बुनियादी ज्ञान: C# प्रोग्रामिंग से परिचित होना लाभदायक होगा।
4. एक वर्ड दस्तावेज़: बुकमार्क के साथ एक नमूना वर्ड दस्तावेज़.

## नामस्थान आयात करें

कोड शुरू करने से पहले, आपको आवश्यक नेमस्पेस आयात करने की आवश्यकता है। अपनी C# फ़ाइल की शुरुआत में निम्नलिखित जोड़ें:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

## चरण 1: अपना दस्तावेज़ लोड करें

सबसे पहले, आपको बुकमार्क वाले वर्ड डॉक्यूमेंट को लोड करना होगा। आप इसे इस तरह से कर सकते हैं:

```csharp
// दस्तावेज़ निर्देशिका का पथ.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

### स्पष्टीकरण

- dataDir: यह वह निर्देशिका पथ है जहां आपका Word दस्तावेज़ स्थित है।
-  दस्तावेज़ doc: यह एक नया उदाहरण आरंभ करता है`Document` class को अपनी निर्दिष्ट फ़ाइल के साथ जोड़ें।

## चरण 2: बुकमार्क की गई सामग्री दिखाएँ या छिपाएँ

इसके बाद, हम बुकमार्क की गई सामग्री को दिखाने या छिपाने के लिए एक विधि परिभाषित करेंगे। यहाँ पूरी विधि दी गई है:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool showHide)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.MoveToDocumentEnd();

    // {IF "{MERGEFIELD बुकमार्क}" = "सत्य" "" ""}
    Field field = builder.InsertField("IF \"", null);
    builder.MoveTo(field.Start.NextSibling);
    builder.InsertField("MERGEFIELD " + bookmarkName + "", null);
    builder.Write("\" = \"true\" ");
    builder.Write("\"");
    builder.Write("\"");
    builder.Write(" \"\"");

    Node currentNode = field.Start;
    bool flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.Run)
            if (currentNode.ToString(SaveFormat.Text).Trim() == "\"")
                flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkStart.ParentNode.InsertBefore(currentNode, bm.BookmarkStart);
        currentNode = nextNode;
    }

    Node endNode = bm.BookmarkEnd;
    flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.FieldEnd)
            flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkEnd.ParentNode.InsertAfter(currentNode, endNode);
        endNode = currentNode;
        currentNode = nextNode;
    }

    doc.MailMerge.Execute(new[] { bookmarkName }, new object[] { showHide });
}
```

### स्पष्टीकरण

- बुकमार्क bm: दस्तावेज़ से बुकमार्क लाता है.
- डॉक्यूमेंटबिल्डर बिल्डर: दस्तावेज़ को नेविगेट करने और संशोधित करने में मदद करता है।
- फ़ील्ड फ़ील्ड: बुकमार्क की स्थिति की जांच करने के लिए एक IF फ़ील्ड सम्मिलित करता है।
- नोड currentNode: फ़ील्ड के प्रारंभ और अंत को खोजने के लिए नोड्स के माध्यम से यात्रा करता है।

## चरण 3: दिखाएँ/छिपाएँ फ़ंक्शन निष्पादित करें

 अब, आपको कॉल करने की आवश्यकता है`ShowHideBookmarkedContent` विधि, दस्तावेज़, बुकमार्क नाम और दृश्यता ध्वज पास करना:

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", false);
```

### स्पष्टीकरण

- doc: आपका दस्तावेज़ ऑब्जेक्ट.
- "MyBookmark1": उस बुकमार्क का नाम जिसे आप दिखाना/छिपाना चाहते हैं।
- असत्य: दृश्यता ध्वज (दिखाने के लिए सत्य, छिपाने के लिए असत्य)।

## चरण 4: अपना दस्तावेज़ सहेजें

अंत में, संशोधित दस्तावेज़ को सहेजें:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### स्पष्टीकरण

- dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx": नए दस्तावेज़ का पथ और नाम जहाँ परिवर्तन सहेजे जायेंगे।

## निष्कर्ष

और अब आप समझ गए होंगे! आपने सफलतापूर्वक सीख लिया है कि Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में बुकमार्क कैसे दिखाएँ और छिपाएँ। यह तकनीक सशर्त सामग्री वाले दस्तावेज़ों को गतिशील रूप से बनाने के लिए अविश्वसनीय रूप से उपयोगी हो सकती है।

## अक्सर पूछे जाने वाले प्रश्न

### .NET के लिए Aspose.Words क्या है?
.NET के लिए Aspose.Words एक शक्तिशाली दस्तावेज़ प्रसंस्करण लाइब्रेरी है जो डेवलपर्स को प्रोग्रामेटिक रूप से Word दस्तावेज़ बनाने, संशोधित करने और परिवर्तित करने की अनुमति देता है।

### मैं .NET के लिए Aspose.Words कैसे प्राप्त करूं?
 आप .NET के लिए Aspose.Words को यहां से डाउनलोड कर सकते हैं[यहाँ](https://releases.aspose.com/words/net/). एक निःशुल्क परीक्षण भी उपलब्ध है।

### क्या मैं इस विधि का उपयोग अन्य प्रकार के बुकमार्क के लिए कर सकता हूँ?
हां, इस विधि को आपके वर्ड दस्तावेज़ में किसी भी बुकमार्क की दृश्यता प्रबंधित करने के लिए अनुकूलित किया जा सकता है।

### यदि मेरे दस्तावेज़ में निर्दिष्ट बुकमार्क नहीं है तो क्या होगा?
यदि बुकमार्क मौजूद नहीं है, तो विधि त्रुटि उत्पन्न करेगी। बुकमार्क दिखाने/छिपाने का प्रयास करने से पहले सुनिश्चित करें कि बुकमार्क मौजूद है।

### यदि मुझे कोई समस्या आती है तो मैं सहायता कैसे प्राप्त कर सकता हूँ?
 आप Aspose समुदाय से सहायता प्राप्त कर सकते हैं[यहाँ](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
