---
title: पंक्ति प्रारूप पृष्ठों में विराम अक्षम करें
linktitle: पंक्ति प्रारूप पृष्ठों में विराम अक्षम करें
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: तालिका की पठनीयता और स्वरूपण को बनाए रखने के लिए .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों में पृष्ठों में पंक्ति विराम को अक्षम करना सीखें।
weight: 10
url: /hi/net/programming-with-tables/row-format-disable-break-across-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# पंक्ति प्रारूप पृष्ठों में विराम अक्षम करें

## परिचय

Word दस्तावेज़ों में तालिकाओं के साथ काम करते समय, आप यह सुनिश्चित करना चाहेंगे कि पंक्तियाँ पृष्ठों में विभाजित न हों, जो आपके दस्तावेज़ों की पठनीयता और स्वरूपण को बनाए रखने के लिए आवश्यक हो सकता है। Aspose.Words for .NET पृष्ठों में पंक्ति विराम को अक्षम करने का एक आसान तरीका प्रदान करता है।

इस ट्यूटोरियल में, हम आपको .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ में पृष्ठों में पंक्ति विराम को अक्षम करने की प्रक्रिया से अवगत कराएंगे।

## आवश्यक शर्तें

शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ हैं:
- Aspose.Words for .NET लाइब्रेरी स्थापित की गई।
- एक Word दस्तावेज़ जिसमें एक तालिका है जो एकाधिक पृष्ठों में फैली हुई है।

## नामस्थान आयात करें

सबसे पहले, अपने प्रोजेक्ट में आवश्यक नामस्थान आयात करें:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## चरण 1: दस्तावेज़ लोड करें

एकाधिक पृष्ठों वाली तालिका वाले दस्तावेज़ को लोड करें.

```csharp
// आपके दस्तावेज़ निर्देशिका का पथ
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## चरण 2: टेबल तक पहुंचें

दस्तावेज़ में पहली तालिका तक पहुँचें। यह मानता है कि जिस तालिका को आप संशोधित करना चाहते हैं वह दस्तावेज़ में पहली तालिका है।

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## चरण 3: सभी पंक्तियों के लिए पृष्ठों में विभाजन अक्षम करें

 तालिका में प्रत्येक पंक्ति के माध्यम से लूप करें और सेट करें`AllowBreakAcrossPages`संपत्ति को`false`इससे यह सुनिश्चित होता है कि पंक्तियाँ पृष्ठों पर नहीं टूटेंगी।

```csharp
// तालिका में सभी पंक्तियों के लिए पृष्ठों में विभाजन अक्षम करें.
foreach (Row row in table.Rows)
    row.RowFormat.AllowBreakAcrossPages = false;
```

## चरण 4: दस्तावेज़ सहेजें

संशोधित दस्तावेज़ को अपनी निर्दिष्ट निर्देशिका में सहेजें.

```csharp
doc.Save(dataDir + "WorkingWithTables.RowFormatDisableBreakAcrossPages.docx");
```

## निष्कर्ष

इस ट्यूटोरियल में, हमने Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में पृष्ठों में पंक्ति विराम को अक्षम करने का तरीका दिखाया है। ऊपर बताए गए चरणों का पालन करके, आप यह सुनिश्चित कर सकते हैं कि आपकी तालिका पंक्तियाँ बरकरार रहें और पृष्ठों में विभाजित न हों, जिससे दस्तावेज़ की पठनीयता और स्वरूपण बना रहे।

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं सभी पंक्तियों के बजाय किसी विशिष्ट पंक्ति के लिए पृष्ठों में पंक्ति विराम अक्षम कर सकता हूँ?  
 हां, आप इच्छित पंक्ति तक पहुंचकर और उसकी सेटिंग करके विशिष्ट पंक्तियों के लिए पंक्ति विराम अक्षम कर सकते हैं`AllowBreakAcrossPages`संपत्ति को`false`.

### क्या यह विधि मर्ज की गई कोशिकाओं वाली तालिकाओं के लिए काम करती है?  
 हां, यह विधि मर्ज किए गए कक्षों वाली तालिकाओं के लिए काम करती है।`AllowBreakAcrossPages` सेल विलय की परवाह किए बिना, पूरी पंक्ति पर लागू होता है।

### यदि तालिका किसी अन्य तालिका के अंदर स्थित है तो क्या यह विधि काम करेगी?  
हां, आप उसी तरह नेस्टेड टेबल तक पहुंच सकते हैं और उसे संशोधित कर सकते हैं। सुनिश्चित करें कि आप नेस्टेड टेबल को उसके इंडेक्स या अन्य गुणों के आधार पर सही तरीके से संदर्भित करते हैं।

### मैं कैसे जांच सकता हूं कि कोई पंक्ति पृष्ठों में विभाजन की अनुमति देती है या नहीं?  
 आप जाँच कर सकते हैं कि कोई पंक्ति पृष्ठों में विभाजन की अनुमति देती है या नहीं`AllowBreakAcrossPages` की संपत्ति`RowFormat` और इसके मूल्य की जाँच करें.

### क्या किसी दस्तावेज़ में सभी तालिकाओं पर यह सेटिंग लागू करने का कोई तरीका है?  
हां, आप दस्तावेज़ में सभी तालिकाओं को लूप कर सकते हैं और प्रत्येक पर यह सेटिंग लागू कर सकते हैं।
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
