---
title: कस्टम XML भाग पर मैप किए गए तालिका दोहराए जाने वाले अनुभाग का निर्माण करना
linktitle: कस्टम XML भाग पर मैप किए गए तालिका दोहराए जाने वाले अनुभाग का निर्माण करना
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ में CustomXmlPart पर मैप किए गए दोहराए जाने वाले अनुभाग के साथ एक तालिका बनाने का तरीका जानें।
weight: 10
url: /hi/net/programming-with-sdt/creating-table-repeating-section-mapped-to-custom-xml-part/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# कस्टम XML भाग पर मैप किए गए तालिका दोहराए जाने वाले अनुभाग का निर्माण करना

## परिचय

इस ट्यूटोरियल में, हम एक दोहराए जाने वाले अनुभाग के साथ एक तालिका बनाने की प्रक्रिया से गुजरेंगे जो .NET के लिए Aspose.Words का उपयोग करके एक कस्टम XML भाग में मैप किया गया है। यह संरचित डेटा के आधार पर गतिशील रूप से दस्तावेज़ बनाने के लिए विशेष रूप से उपयोगी है।

## आवश्यक शर्तें

शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
1.  Aspose.Words for .NET लाइब्रेरी स्थापित है। आप इसे यहाँ से डाउनलोड कर सकते हैं[Aspose वेबसाइट](https://releases.aspose.com/words/net/).
2. C# और XML की बुनियादी समझ।

## नामस्थान आयात करें

अपने प्रोजेक्ट में आवश्यक नामस्थान शामिल करना सुनिश्चित करें:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Tables;
```

## चरण 1: दस्तावेज़ और दस्तावेज़बिल्डर को आरंभ करें

 सबसे पहले, एक नया दस्तावेज़ बनाएं और एक आरंभ करें`DocumentBuilder`:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## चरण 2: कस्टम XML भाग जोड़ें

दस्तावेज़ में एक कस्टम XML भाग जोड़ें। इस XML में वह डेटा है जिसे हम अपनी तालिका में मैप करना चाहते हैं:

```csharp
CustomXmlPart xmlPart = doc.CustomXmlParts.Add("Books",
    "<books><book><title>Everyday Italian</title><author>Giada De Laurentiis</author></book>" +
    "<book><title>Harry Potter</title><author>J K. Rowling</author></book>" +
    "<book><title>Learning XML</title><author>Erik T. Ray</author></book></books>");
```

## चरण 3: तालिका संरचना बनाएँ

 इसके बाद, का उपयोग करें`DocumentBuilder` तालिका शीर्षलेख बनाने के लिए:

```csharp
Table table = builder.StartTable();
builder.InsertCell();
builder.Write("Title");
builder.InsertCell();
builder.Write("Author");
builder.EndRow();
builder.EndTable();
```

## चरण 4: दोहराए जाने वाला अनुभाग बनाएँ

 एक बनाने के`StructuredDocumentTag` (SDT) दोहराए जाने वाले अनुभाग के लिए और इसे XML डेटा पर मैप करें:

```csharp
StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSection, MarkupLevel.Row);
repeatingSectionSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book", "");
table.AppendChild(repeatingSectionSdt);
```

## चरण 5: दोहराए जाने वाले अनुभाग आइटम बनाएँ

दोहराए जाने वाले अनुभाग आइटम के लिए SDT बनाएं और उसे दोहराए जाने वाले अनुभाग में जोड़ें:

```csharp
StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSectionItem, MarkupLevel.Row);
repeatingSectionSdt.AppendChild(repeatingSectionItemSdt);
Row row = new Row(doc);
repeatingSectionItemSdt.AppendChild(row);
```

## चरण 6: XML डेटा को तालिका कक्षों में मैप करें

शीर्षक और लेखक के लिए SDT बनाएं, उन्हें XML डेटा से मैप करें, और उन्हें पंक्ति में जोड़ें:

```csharp
StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
titleSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.AppendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
authorSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.AppendChild(authorSdt);
```

## चरण 7: दस्तावेज़ सहेजें

अंत में, दस्तावेज़ को निर्दिष्ट निर्देशिका में सहेजें:

```csharp
doc.Save(dataDir + "WorkingWithSdt.CreatingTableRepeatingSectionMappedToCustomXmlPart.docx");
```

## निष्कर्ष

इन चरणों का पालन करके, आपने .NET के लिए Aspose.Words का उपयोग करके कस्टम XML भाग में मैप किए गए दोहराए जाने वाले अनुभाग के साथ सफलतापूर्वक एक तालिका बनाई है। यह संरचित डेटा के आधार पर गतिशील सामग्री निर्माण की अनुमति देता है, जिससे दस्तावेज़ निर्माण अधिक लचीला और शक्तिशाली हो जाता है।

## अक्सर पूछे जाने वाले प्रश्न

### संरचित दस्तावेज़ टैग (SDT) क्या है?
एसडीटी, जिसे सामग्री नियंत्रण के रूप में भी जाना जाता है, दस्तावेज़ में एक परिबद्ध क्षेत्र है जिसका उपयोग संरचित डेटा को रखने के लिए किया जाता है।

### क्या मैं कस्टम XML भाग में अन्य डेटा प्रकारों का उपयोग कर सकता हूँ?
हां, आप अपने कस्टम XML भाग को किसी भी डेटा प्रकार के साथ संरचित कर सकते हैं और उन्हें तदनुसार मैप कर सकते हैं।

### मैं दोहराए जाने वाले अनुभाग में और अधिक पंक्तियाँ कैसे जोड़ूँ?
दोहराए जाने वाला अनुभाग स्वचालित रूप से मैप किए गए XML पथ में प्रत्येक आइटम के लिए पंक्ति संरचना की प्रतिकृति बनाता है।
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
