---
title: वर्ड दस्तावेज़ में बुकमार्क की गई सामग्री दिखाएँ छुपाएँ
linktitle: वर्ड दस्तावेज़ में बुकमार्क की गई सामग्री दिखाएँ छुपाएँ
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: इस विस्तृत, चरण-दर-चरण मार्गदर्शिका के साथ .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों में बुकमार्क की गई सामग्री को दिखाना और छिपाना सीखें।
weight: 10
url: /hi/net/programming-with-bookmarks/show-hide-bookmarked-content/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# वर्ड दस्तावेज़ में बुकमार्क की गई सामग्री दिखाएँ छुपाएँ

## परिचय

Aspose.Words for .NET के साथ दस्तावेज़ हेरफेर की दुनिया में गोता लगाने के लिए तैयार हैं? चाहे आप दस्तावेज़ कार्यों को स्वचालित करने के इच्छुक डेवलपर हों या Word फ़ाइलों को प्रोग्रामेटिक रूप से संभालने के बारे में उत्सुक हों, आप सही जगह पर हैं। आज, हम Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में बुकमार्क की गई सामग्री को दिखाने और छिपाने का तरीका जानेंगे। यह चरण-दर-चरण मार्गदर्शिका आपको बुकमार्क के आधार पर सामग्री दृश्यता को नियंत्रित करने में माहिर बना देगी। चलिए शुरू करते हैं!

## आवश्यक शर्तें

इससे पहले कि हम इसकी बारीकियों पर जाएं, आपको कुछ चीजों की आवश्यकता होगी:

1. विजुअल स्टूडियो: .NET के साथ संगत कोई भी संस्करण।
2.  .NET के लिए Aspose.Words: इसे डाउनलोड करें[यहाँ](https://releases.aspose.com/words/net/).
3. C# की बुनियादी समझ: यदि आप एक सरल "हैलो वर्ल्ड" प्रोग्राम लिख सकते हैं, तो आप आगे बढ़ने के लिए तैयार हैं।
4. बुकमार्क के साथ एक वर्ड दस्तावेज़: हम इस ट्यूटोरियल के लिए बुकमार्क के साथ एक नमूना दस्तावेज़ का उपयोग करेंगे।

## नामस्थान आयात करें

सबसे पहले, आइए आवश्यक नेमस्पेस को आयात करें। इससे यह सुनिश्चित होता है कि हमारे पास हमारे कार्य के लिए आवश्यक सभी उपकरण हैं।

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

इन नामस्थानों के साथ, हम अपनी यात्रा शुरू करने के लिए पूरी तरह तैयार हैं।

## चरण 1: अपना प्रोजेक्ट सेट अप करना

ठीक है, चलिए विजुअल स्टूडियो में अपना प्रोजेक्ट सेट करके काम शुरू करते हैं।

### एक नया प्रोजेक्ट बनाएं

Visual Studio खोलें और एक नया कंसोल ऐप (.NET Core) प्रोजेक्ट बनाएँ। इसे कुछ आकर्षक नाम दें, जैसे "BookmarkVisibilityManager"।

### .NET के लिए Aspose.Words जोड़ें

आपको अपने प्रोजेक्ट में Aspose.Words for .NET जोड़ना होगा। आप यह NuGet पैकेज मैनेजर के ज़रिए कर सकते हैं।

1. टूल्स > NuGet पैकेज मैनेजर > समाधान के लिए NuGet पैकेज प्रबंधित करें पर जाएं।
2. "Aspose.Words" खोजें।
3. पैकेज स्थापित करें.

अब जबकि हमारा प्रोजेक्ट सेट हो गया है, चलिए अपने दस्तावेज़ को लोड करने के लिए आगे बढ़ते हैं।

## चरण 2: दस्तावेज़ लोड करना

हमें बुकमार्क वाले Word दस्तावेज़ को लोड करना होगा। इस ट्यूटोरियल के लिए, हम "Bookmarks.docx" नामक एक नमूना दस्तावेज़ का उपयोग करेंगे।

```csharp
// दस्तावेज़ निर्देशिका का पथ.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

 यह कोड स्निपेट आपके दस्तावेज़ निर्देशिका का पथ सेट करता है और दस्तावेज़ को लोड करता है`doc` वस्तु।

## चरण 3: बुकमार्क की गई सामग्री दिखाएँ/छिपाएँ

अब आता है मज़ेदार हिस्सा - बुकमार्क के आधार पर सामग्री दिखाना या छिपाना। हम एक विधि बनाएंगे जिसका नाम है`ShowHideBookmarkedContent` इसे संभालने के लिए.

बुकमार्क की गई सामग्री की दृश्यता को टॉगल करने की विधि यहां दी गई है:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    Node currentNode = bm.BookmarkStart;
    while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
    {
        if (currentNode.NodeType == NodeType.Run)
        {
            Run run = currentNode as Run;
            run.Font.Hidden = isHidden;
        }
        currentNode = currentNode.NextSibling;
    }
}
```

### विधि का विवरण

-  बुकमार्क पुनर्प्राप्ति:`Bookmark bm = doc.Range.Bookmarks[bookmarkName];` बुकमार्क लाता है.
- नोड ट्रैवर्सल: हम बुकमार्क के भीतर नोड्स को ट्रैवर्स करते हैं।
-  दृश्यता टॉगल: यदि नोड एक है`Run` (पाठ का एक निरंतर क्रम), हम इसे सेट करते हैं`Hidden` संपत्ति।

## चरण 4: विधि को लागू करना

हमारी विधि के अनुसार, आइए इसे बुकमार्क के आधार पर सामग्री दिखाने या छिपाने के लिए लागू करें।

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true);
```

कोड की यह पंक्ति "MyBookmark1" नामक बुकमार्क के भीतर की सामग्री को छिपा देगी।

## चरण 5: दस्तावेज़ को सहेजना

अंत में, आइए अपने संशोधित दस्तावेज़ को सुरक्षित करें।

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

इससे हमारे द्वारा किए गए परिवर्तनों के साथ दस्तावेज़ सुरक्षित हो जाता है।

## निष्कर्ष

और अब यह हो गया! आपने अभी सीखा है कि Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में बुकमार्क की गई सामग्री को कैसे दिखाया और छिपाया जाए। यह शक्तिशाली उपकरण दस्तावेज़ में हेरफेर को आसान बनाता है, चाहे आप रिपोर्ट को स्वचालित कर रहे हों, टेम्पलेट बना रहे हों, या बस Word फ़ाइलों के साथ छेड़छाड़ कर रहे हों। हैप्पी कोडिंग!

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं एक साथ कई बुकमार्क टॉगल कर सकता हूँ?
 हाँ, आप कॉल कर सकते हैं`ShowHideBookmarkedContent` प्रत्येक बुकमार्क के लिए विधि जिसे आप टॉगल करना चाहते हैं।

### क्या सामग्री छिपाने से दस्तावेज़ की संरचना प्रभावित होती है?
नहीं, सामग्री छिपाने से केवल उसकी दृश्यता प्रभावित होती है। सामग्री दस्तावेज़ में ही रहती है।

### क्या मैं इस पद्धति का उपयोग अन्य प्रकार की सामग्री के लिए कर सकता हूँ?
यह विधि विशेष रूप से टेक्स्ट रन को टॉगल करती है। अन्य सामग्री प्रकारों के लिए, आपको नोड ट्रैवर्सल लॉजिक को संशोधित करना होगा।

### क्या Aspose.Words for .NET निःशुल्क है?
 Aspose.Words निःशुल्क परीक्षण प्रदान करता है[यहाँ](https://releases.aspose.com/) , लेकिन उत्पादन उपयोग के लिए पूर्ण लाइसेंस की आवश्यकता है। आप इसे खरीद सकते हैं[यहाँ](https://purchase.aspose.com/buy).

### यदि मुझे कोई समस्या आती है तो मैं सहायता कैसे प्राप्त कर सकता हूँ?
 आप Aspose समुदाय से सहायता प्राप्त कर सकते हैं[यहाँ](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
