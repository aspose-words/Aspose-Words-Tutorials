---
"description": ".NET के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों में हेडर और फ़ुटर जोड़ने और उन्हें कस्टमाइज़ करने का तरीका जानें। यह चरण-दर-चरण मार्गदर्शिका पेशेवर दस्तावेज़ स्वरूपण सुनिश्चित करती है।"
"linktitle": "हेडर फ़ुटर बनाएँ"
"second_title": "Aspose.Words दस्तावेज़ प्रसंस्करण API"
"title": "हेडर फ़ुटर बनाएँ"
"url": "/hi/net/working-with-headers-and-footers/create-header-footer/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# हेडर फ़ुटर बनाएँ

## परिचय

अपने दस्तावेज़ों में हेडर और फ़ुटर जोड़ने से उनकी व्यावसायिकता और पठनीयता बढ़ सकती है। .NET के लिए Aspose.Words के साथ, आप अपने Word दस्तावेज़ों के लिए हेडर और फ़ुटर आसानी से बना और कस्टमाइज़ कर सकते हैं। इस ट्यूटोरियल में, हम आपको चरण दर चरण प्रक्रिया से गुजारेंगे, यह सुनिश्चित करते हुए कि आप इन सुविधाओं को सहजता से लागू कर सकते हैं।

## आवश्यक शर्तें

आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

- Aspose.Words for .NET: डाउनलोड करें और इंस्टॉल करें [लिंक को डाउनलोड करें](https://releases.aspose.com/words/net/).
- विकास पर्यावरण: जैसे कि विजुअल स्टूडियो, अपना कोड लिखने और चलाने के लिए।
- C# का मूलभूत ज्ञान: C# और .NET फ्रेमवर्क की समझ।
- नमूना दस्तावेज़: शीर्षलेख और पादलेख लागू करने के लिए एक नमूना दस्तावेज़, या ट्यूटोरियल में दिखाए अनुसार एक नया दस्तावेज़ बनाएँ।

## नामस्थान आयात करें

सबसे पहले, आपको Aspose.Words क्लासेस और विधियों तक पहुंचने के लिए आवश्यक नामस्थानों को आयात करना होगा।

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System;
```

## चरण 1: दस्तावेज़ निर्देशिका निर्धारित करें

वह निर्देशिका निर्धारित करें जहाँ आपका दस्तावेज़ सहेजा जाएगा। इससे पथ को प्रभावी ढंग से प्रबंधित करने में मदद मिलती है।

```csharp
// दस्तावेज़ निर्देशिका का पथ
string dataDir = "YOUR_DIRECTORY_OF_DOCUMENTS";
```

## चरण 2: नया दस्तावेज़ बनाएँ

एक नया दस्तावेज़ बनाएँ और `DocumentBuilder` सामग्री को जोड़ने में सुविधा प्रदान करना।

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## चरण 3: पेज सेटअप कॉन्फ़िगर करें

पृष्ठ सेटिंग सेट करें, जिसमें यह भी शामिल है कि पहले पृष्ठ पर अलग हेडर/फुटर होगा या नहीं।

```csharp
Section currentSection = builder.CurrentSection;
PageSetup pageSetup = currentSection.PageSetup;

pageSetup.DifferentFirstPageHeaderFooter = true;
pageSetup.HeaderDistance = 20;
```

## चरण 4: पहले पेज पर हेडर जोड़ें

प्रथम पृष्ठ के हेडर अनुभाग पर जाएँ और हेडर पाठ को कॉन्फ़िगर करें।

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;

builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.Font.Size = 14;

builder.Write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

## चरण 5: प्राथमिक हेडर जोड़ें

प्राथमिक हेडर अनुभाग पर जाएं और एक छवि और पाठ डालें।

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);

// हेडर में एक छवि डालें
builder.InsertImage(dataDir + "Graphics Interchange Format.gif", 
    RelativeHorizontalPosition.Page, 10, RelativeVerticalPosition.Page, 10, 50, 50, WrapType.Through);

builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Aspose.Words Header/Footer Creation Primer.");
```

## चरण 6: प्राथमिक फ़ुटर जोड़ें

प्राथमिक फ़ुटर अनुभाग पर जाएँ और फ़ुटर सामग्री को प्रारूपित करने के लिए एक तालिका बनाएँ।

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.FooterPrimary);

builder.StartTable();
builder.CellFormat.ClearFormatting();
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);

// पृष्ठ क्रमांकन जोड़ें
builder.Write("Page ");
builder.InsertField("PAGE", "");
builder.Write(" of ");
builder.InsertField("NUMPAGES", "");

builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Left;
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

builder.Write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Right;

builder.EndRow();
builder.EndTable();
```

## चरण 7: सामग्री और पेज ब्रेक जोड़ें

दस्तावेज़ के अंत में जाएँ, पृष्ठ विराम जोड़ें, और भिन्न पृष्ठ सेटिंग्स के साथ एक नया अनुभाग बनाएँ।

```csharp
builder.MoveToDocumentEnd();
builder.InsertBreak(BreakType.PageBreak);
builder.InsertBreak(BreakType.SectionBreakNewPage);

currentSection = builder.CurrentSection;
pageSetup = currentSection.PageSetup;
pageSetup.Orientation = Orientation.Landscape;
pageSetup.DifferentFirstPageHeaderFooter = false;

currentSection.HeadersFooters.LinkToPrevious(false);
CopyHeadersFootersFromPreviousSection(currentSection);

HeaderFooter primaryFooter = currentSection.HeadersFooters[HeaderFooterType.FooterPrimary];
Row row = primaryFooter.Tables[0].FirstRow;
row.FirstCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);
row.LastCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

doc.Save(dataDir + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```

## चरण 8: पिछले अनुभाग से हेडर और फ़ुटर कॉपी करें

यदि आप पिछले अनुभाग से शीर्षलेखों और पादलेखों का पुनः उपयोग करना चाहते हैं, तो उन्हें कॉपी करें और आवश्यक संशोधन लागू करें।

```csharp
private static void CopyHeadersFootersFromPreviousSection(Section section)
{
    Section previousSection = (Section)section.PreviousSibling;
    if (previousSection == null) return;

    section.HeadersFooters.Clear();

    foreach (HeaderFooter headerFooter in previousSection.HeadersFooters)
    {
        section.HeadersFooters.Add(headerFooter.Clone(true));
    }
}
```

## निष्कर्ष

इन चरणों का पालन करके, आप Aspose.Words for .NET का उपयोग करके अपने Word दस्तावेज़ों में हेडर और फ़ुटर को प्रभावी ढंग से जोड़ और कस्टमाइज़ कर सकते हैं। यह आपके दस्तावेज़ की उपस्थिति और व्यावसायिकता को बढ़ाता है, जिससे यह अधिक पठनीय और आकर्षक बन जाता है।

## अक्सर पूछे जाने वाले प्रश्न

### .NET के लिए Aspose.Words क्या है?

Aspose.Words for .NET एक लाइब्रेरी है जो डेवलपर्स को .NET अनुप्रयोगों के भीतर प्रोग्रामेटिक रूप से Word दस्तावेज़ बनाने, संपादित करने और परिवर्तित करने में सक्षम बनाती है।

### क्या मैं हेडर या फ़ुटर में छवियाँ जोड़ सकता हूँ?

हां, आप आसानी से हेडर या फ़ुटर में चित्र जोड़ सकते हैं `DocumentBuilder.InsertImage` तरीका।

### मैं पहले पृष्ठ के लिए अलग-अलग शीर्षलेख और पादलेख कैसे सेट करूं?

आप पहले पृष्ठ के लिए अलग-अलग शीर्षलेख और पादलेख सेट कर सकते हैं `DifferentFirstPageHeaderFooter` की संपत्ति `PageSetup` कक्षा।

### मैं Aspose.Words पर अधिक दस्तावेज़ कहां पा सकता हूं?

आप यहाँ पर विस्तृत दस्तावेज पा सकते हैं [Aspose.Words API दस्तावेज़न पृष्ठ](https://reference.aspose.com/words/net/).

### क्या Aspose.Words के लिए समर्थन उपलब्ध है?

हाँ, Aspose उनके माध्यम से समर्थन प्रदान करता है [सहयता मंच](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}