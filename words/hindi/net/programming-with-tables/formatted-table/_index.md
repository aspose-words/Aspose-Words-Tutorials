---
"description": "इस विस्तृत चरण-दर-चरण मार्गदर्शिका के साथ .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों में तालिकाओं को बनाने और प्रारूपित करने का तरीका जानें।"
"linktitle": "स्वरूपित तालिका"
"second_title": "Aspose.Words दस्तावेज़ प्रसंस्करण API"
"title": "स्वरूपित तालिका"
"url": "/hi/net/programming-with-tables/formatted-table/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# स्वरूपित तालिका

## परिचय

Word दस्तावेज़ों में प्रोग्रामेटिक रूप से टेबल बनाना और फ़ॉर्मेट करना एक कठिन काम लग सकता है, लेकिन Aspose.Words for .NET के साथ, यह सरल और प्रबंधनीय हो जाता है। इस ट्यूटोरियल में, हम आपको Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में फ़ॉर्मेट की गई टेबल बनाने का तरीका बताएँगे। हम आपके परिवेश को सेट करने से लेकर आपके दस्तावेज़ को एक सुंदर फ़ॉर्मेट की गई टेबल के साथ सहेजने तक सब कुछ कवर करेंगे।

## आवश्यक शर्तें

कोड में गोता लगाने से पहले, आइए सुनिश्चित करें कि आपके पास वह सब कुछ है जो आपको चाहिए:

1. .NET लाइब्रेरी के लिए Aspose.Words: इसे यहाँ से डाउनलोड करें [यहाँ](https://releases.aspose.com/words/net/).
2. विकास पर्यावरण: विजुअल स्टूडियो जैसा एक IDE.
3. .NET फ्रेमवर्क: सुनिश्चित करें कि आपके मशीन पर .NET फ्रेमवर्क स्थापित है।

## नामस्थान आयात करें

वास्तविक कोड लिखने से पहले, आपको आवश्यक नामस्थान आयात करने होंगे:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

## चरण 1: अपनी दस्तावेज़ निर्देशिका सेट करें

सबसे पहले, आपको वह पथ निर्धारित करना होगा जहां आपका दस्तावेज़ सहेजा जाएगा।

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

प्रतिस्थापित करें `"YOUR DOCUMENT DIRECTORY"` उस वास्तविक पथ के साथ जहाँ आप दस्तावेज़ को सहेजना चाहते हैं.

## चरण 2: दस्तावेज़ और दस्तावेज़बिल्डर को आरंभ करें

अब, एक नया दस्तावेज़ और एक DocumentBuilder ऑब्जेक्ट आरंभ करें।

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

The `DocumentBuilder` एक सहायक वर्ग है जो दस्तावेज़ निर्माण की प्रक्रिया को सरल बनाता है।

## चरण 3: टेबल शुरू करें

इसके बाद, का उपयोग करके तालिका बनाना शुरू करें `StartTable` तरीका।

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

तालिका शुरू करने के लिए एक सेल सम्मिलित करना आवश्यक है।

## चरण 4: टेबल-वाइड फ़ॉर्मेटिंग लागू करें

आप संपूर्ण तालिका को प्रभावित करने वाला स्वरूपण लागू कर सकते हैं। उदाहरण के लिए, बायाँ इंडेंट सेट करना:

```csharp
table.LeftIndent = 20.0;
```

## चरण 5: हेडर पंक्ति को प्रारूपित करें

शीर्ष लेख पंक्ति के लिए ऊँचाई, संरेखण और अन्य गुण सेट करें.

```csharp
builder.RowFormat.Height = 40.0;
builder.RowFormat.HeightRule = HeightRule.AtLeast;
builder.CellFormat.Shading.BackgroundPatternColor = Color.FromArgb(198, 217, 241);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Font.Size = 16;
builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.CellFormat.Width = 100.0;
builder.Write("Header Row,\n Cell 1");
```

इस चरण में, हम पृष्ठभूमि का रंग, फ़ॉन्ट का आकार और संरेखण निर्धारित करके हेडर पंक्ति को प्रमुख बनाते हैं।

## चरण 6: अतिरिक्त हेडर सेल डालें

शीर्ष लेख पंक्ति के लिए अधिक कक्ष सम्मिलित करें:

```csharp
builder.InsertCell();
builder.Write("Header Row,\n Cell 2");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Header Row,\n Cell 3");
builder.EndRow();
```

## चरण 7: मुख्य पंक्तियों को प्रारूपित करें

शीर्षलेख सेट करने के बाद, तालिका के मुख्य भाग को प्रारूपित करें:

```csharp
builder.CellFormat.Shading.BackgroundPatternColor = Color.White;
builder.CellFormat.Width = 100.0;
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.RowFormat.Height = 30.0;
builder.RowFormat.HeightRule = HeightRule.Auto;
```

## चरण 8: बॉडी पंक्तियाँ डालें

मुख्य पंक्तियां सामग्री के साथ डालें:

```csharp
builder.InsertCell();
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Write("Row 1, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 1, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 1, Cell 3 Content");
builder.EndRow();
```

अतिरिक्त पंक्तियों के लिए दोहराएँ:

```csharp
builder.InsertCell();
builder.CellFormat.Width = 100.0;
builder.Write("Row 2, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 2, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 2, Cell 3 Content.");
builder.EndRow();
builder.EndTable();
```

## चरण 9: दस्तावेज़ सहेजें

अंत में, दस्तावेज़ को निर्दिष्ट निर्देशिका में सहेजें:

```csharp
doc.Save(dataDir + "WorkingWithTables.FormattedTable.docx");
```

इससे स्वरूपित तालिका के साथ एक वर्ड दस्तावेज़ निर्मित और सहेजा जाएगा।

## निष्कर्ष

और अब यह हो गया! इन चरणों का पालन करके, आप .NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ में एक अच्छी तरह से स्वरूपित तालिका बना सकते हैं। यह शक्तिशाली लाइब्रेरी Word दस्तावेज़ों को प्रोग्रामेटिक रूप से हेरफेर करना आसान बनाती है, जिससे आपका समय और प्रयास बचता है।

## अक्सर पूछे जाने वाले प्रश्न

### .NET के लिए Aspose.Words क्या है?
.NET के लिए Aspose.Words, Word दस्तावेज़ों को प्रोग्रामेटिक रूप से बनाने, संपादित करने और परिवर्तित करने के लिए एक शक्तिशाली लाइब्रेरी है।

### क्या मैं अलग-अलग पंक्तियों के लिए अलग-अलग रंगों का उपयोग कर सकता हूँ?
हां, आप अलग-अलग पंक्तियों या कक्षों पर रंगों सहित अलग-अलग स्वरूपण लागू कर सकते हैं।

### क्या Aspose.Words for .NET निःशुल्क है?
Aspose.Words for .NET एक सशुल्क लाइब्रेरी है, लेकिन आप एक प्राप्त कर सकते हैं [मुफ्त परीक्षण](https://releases.aspose.com/).

### मैं .NET के लिए Aspose.Words का समर्थन कैसे प्राप्त करूं?
आप यहाँ से सहायता प्राप्त कर सकते हैं [Aspose सामुदायिक मंच](https://forum.aspose.com/c/words/8).

### क्या मैं .NET के लिए Aspose.Words के साथ अन्य प्रकार के दस्तावेज़ बना सकता हूँ?
हां, .NET के लिए Aspose.Words पीडीएफ, HTML और TXT सहित विभिन्न दस्तावेज़ स्वरूपों का समर्थन करता है।


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}