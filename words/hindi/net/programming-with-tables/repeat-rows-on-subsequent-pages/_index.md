---
title: अगले पृष्ठों पर पंक्तियाँ दोहराएँ
linktitle: अगले पृष्ठों पर पंक्तियाँ दोहराएँ
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: .NET के लिए Aspose.Words का उपयोग करके दोहराए जाने वाले टेबल हेडर पंक्तियों के साथ Word दस्तावेज़ बनाने का तरीका जानें। पेशेवर और परिष्कृत दस्तावेज़ सुनिश्चित करने के लिए इस गाइड का पालन करें।
weight: 10
url: /hi/net/programming-with-tables/repeat-rows-on-subsequent-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# अगले पृष्ठों पर पंक्तियाँ दोहराएँ

## परिचय

प्रोग्रामेटिक रूप से वर्ड डॉक्यूमेंट बनाना एक कठिन काम हो सकता है, खासकर तब जब आपको कई पेजों पर फ़ॉर्मेटिंग को बनाए रखने की ज़रूरत हो। क्या आपने कभी वर्ड में टेबल बनाने की कोशिश की है, और पाया है कि आपकी हेडर पंक्तियाँ अगले पेजों पर दोहराई नहीं जा रही हैं? चिंता न करें! .NET के लिए Aspose.Words के साथ, आप आसानी से सुनिश्चित कर सकते हैं कि आपके टेबल हेडर प्रत्येक पेज पर दोहराए जाएँ, जिससे आपके दस्तावेज़ों को एक पेशेवर और पॉलिश लुक मिले। इस ट्यूटोरियल में, हम आपको सरल कोड उदाहरणों और विस्तृत स्पष्टीकरणों का उपयोग करके इसे प्राप्त करने के चरणों के माध्यम से चलेंगे। चलिए शुरू करते हैं!

## आवश्यक शर्तें

आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

1.  .NET के लिए Aspose.Words: आप इसे डाउनलोड कर सकते हैं[यहाँ](https://releases.aspose.com/words/net/).
2. आपके मशीन पर .NET फ्रेमवर्क स्थापित है।
3. विज़ुअल स्टूडियो या कोई अन्य IDE जो .NET विकास का समर्थन करता है।
4. C# प्रोग्रामिंग की बुनियादी समझ.

सुनिश्चित करें कि आपने .NET के लिए Aspose.Words स्थापित किया है और आगे बढ़ने से पहले अपना विकास वातावरण सेट अप किया है।

## नामस्थान आयात करें

आरंभ करने के लिए, आपको अपने प्रोजेक्ट में आवश्यक नामस्थान आयात करने होंगे। अपनी C# फ़ाइल के शीर्ष पर निम्नलिखित using निर्देश जोड़ें:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

इन नामस्थानों में Word दस्तावेज़ों और तालिकाओं में परिवर्तन करने के लिए आवश्यक वर्ग और विधियाँ शामिल हैं।

## चरण 1: दस्तावेज़ को आरंभ करें

 सबसे पहले, आइए एक नया वर्ड डॉक्यूमेंट बनाएं और`DocumentBuilder` हमारी तालिका बनाने के लिए.

```csharp
// आपके दस्तावेज़ निर्देशिका का पथ
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 यह कोड एक नया दस्तावेज़ आरंभ करता है और`DocumentBuilder` ऑब्जेक्ट, जो दस्तावेज़ संरचना के निर्माण में मदद करता है।

## चरण 2: तालिका प्रारंभ करें और शीर्षलेख पंक्तियाँ परिभाषित करें

इसके बाद, हम तालिका शुरू करेंगे और शीर्षक पंक्तियों को परिभाषित करेंगे जिन्हें हम आगामी पृष्ठों पर दोहराना चाहते हैं।

```csharp
builder.StartTable();
builder.RowFormat.HeadingFormat = true;
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.CellFormat.Width = 100;

builder.InsertCell();
builder.Writeln("Heading row 1");
builder.EndRow();

builder.InsertCell();
builder.Writeln("Heading row 2");
builder.EndRow();
```

 यहाँ, हम एक नई तालिका शुरू करते हैं, सेट करते हैं`HeadingFormat`संपत्ति को`true` यह इंगित करने के लिए कि पंक्तियाँ शीर्षलेख हैं, और कोशिकाओं के संरेखण और चौड़ाई को परिभाषित करें।

## चरण 3: तालिका में डेटा पंक्तियाँ जोड़ें

अब, हम अपनी तालिका में कई डेटा पंक्तियाँ जोड़ेंगे। ये पंक्तियाँ अगले पृष्ठों पर दोहराई नहीं जाएँगी।

```csharp
builder.CellFormat.Width = 50;
builder.ParagraphFormat.ClearFormatting();
for (int i = 0; i < 50; i++)
{
    builder.InsertCell();
    builder.RowFormat.HeadingFormat = false;
    builder.Write("Column 1 Text");
    
    builder.InsertCell();
    builder.Write("Column 2 Text");
    builder.EndRow();
}
```

 यह लूप तालिका में डेटा की 50 पंक्तियाँ सम्मिलित करता है, प्रत्येक पंक्ति में दो कॉलम होते हैं।`HeadingFormat` इसके लिए सेट है`false` इन पंक्तियों के लिए, क्योंकि वे शीर्ष पंक्तियाँ नहीं हैं।

## चरण 4: दस्तावेज़ सहेजें

अंत में, हम दस्तावेज़ को निर्दिष्ट निर्देशिका में सहेजते हैं।

```csharp
doc.Save(dataDir + "WorkingWithTables.RepeatRowsOnSubsequentPages.docx");
```

यह दस्तावेज़ को आपके दस्तावेज़ निर्देशिका में निर्दिष्ट नाम से सहेजता है।

## निष्कर्ष

और अब यह हो गया! कोड की कुछ ही पंक्तियों के साथ, आप .NET के लिए Aspose.Words का उपयोग करके अगले पृष्ठों पर दोहराए जाने वाले हेडर पंक्तियों वाले टेबल के साथ एक वर्ड दस्तावेज़ बना सकते हैं। यह न केवल आपके दस्तावेज़ों की पठनीयता को बढ़ाता है बल्कि एक सुसंगत और पेशेवर उपस्थिति भी सुनिश्चित करता है। अब, आगे बढ़ें और इसे अपने प्रोजेक्ट में आज़माएँ!

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं हेडर पंक्तियों को और अधिक अनुकूलित कर सकता हूँ?
 हां, आप शीर्षक पंक्तियों के गुणों को संशोधित करके अतिरिक्त स्वरूपण लागू कर सकते हैं`ParagraphFormat`, `RowFormat` , और`CellFormat`.

### क्या तालिका में और अधिक कॉलम जोड़ना संभव है?
 बिल्कुल! आप आवश्यकतानुसार अधिक सेल्स डालकर जितने चाहें उतने कॉलम जोड़ सकते हैं`InsertCell` तरीका।

### मैं आगामी पृष्ठों पर अन्य पंक्तियों को कैसे दोहरा सकता हूँ?
 किसी भी पंक्ति को दोहराने के लिए, सेट करें`RowFormat.HeadingFormat`संपत्ति को`true` उस विशिष्ट पंक्ति के लिए.

### क्या मैं किसी दस्तावेज़ में मौजूदा तालिकाओं के लिए इस विधि का उपयोग कर सकता हूँ?
 हां, आप मौजूदा तालिकाओं को उनके माध्यम से एक्सेस करके संशोधित कर सकते हैं`Document` ऑब्जेक्ट और समान स्वरूपण लागू करना।

### .NET के लिए Aspose.Words में अन्य कौन से तालिका स्वरूपण विकल्प उपलब्ध हैं?
 Aspose.Words for .NET टेबल फ़ॉर्मेटिंग विकल्पों की एक विस्तृत श्रृंखला प्रदान करता है, जिसमें सेल मर्जिंग, बॉर्डर सेटिंग और टेबल संरेखण शामिल हैं।[प्रलेखन](https://reference.aspose.com/words/net/) अधिक जानकारी के लिए.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
