---
title: सीधे तालिका डालें
linktitle: सीधे तालिका डालें
second_title: Aspose.Words दस्तावेज़ प्रसंस्करण API
description: Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ों में सीधे टेबल सम्मिलित करना सीखें। अपने दस्तावेज़ निर्माण को सरल बनाने के लिए हमारी विस्तृत, चरण-दर-चरण मार्गदर्शिका का पालन करें।
weight: 10
url: /hi/net/programming-with-tables/insert-table-directly/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# सीधे तालिका डालें

## परिचय
प्रोग्रामेटिक रूप से टेबल बनाना काफी चुनौतीपूर्ण हो सकता है, खासकर जब जटिल दस्तावेज़ संरचनाओं से निपटना हो। लेकिन चिंता न करें, हम इसे आपके लिए समझाने के लिए यहाँ हैं! इस गाइड में, हम Aspose.Words for .NET का उपयोग करके सीधे Word दस्तावेज़ में टेबल डालने के चरणों के माध्यम से चलेंगे। चाहे आप एक अनुभवी डेवलपर हों या अभी शुरुआत कर रहे हों, यह ट्यूटोरियल आपको आसानी से प्रक्रिया में महारत हासिल करने में मदद करेगा।

## आवश्यक शर्तें

कोड में गोता लगाने से पहले, आइए सुनिश्चित करें कि आपके पास शुरू करने के लिए आवश्यक सभी चीजें हैं। यहाँ एक त्वरित चेकलिस्ट दी गई है:

1.  Aspose.Words for .NET लाइब्रेरी: सुनिश्चित करें कि आपने Aspose.Words for .NET लाइब्रेरी डाउनलोड और इंस्टॉल कर ली है। आप इसे यहाँ से प्राप्त कर सकते हैं[डाउनलोड पृष्ठ](https://releases.aspose.com/words/net/).
2. विकास वातावरण: विजुअल स्टूडियो जैसा विकास वातावरण.
3. C# का बुनियादी ज्ञान: C# प्रोग्रामिंग की मूल बातें समझना।
4. दस्तावेज़ निर्देशिका: एक निर्देशिका पथ जहाँ आप अपने दस्तावेज़ सहेजेंगे.

इन पूर्व-आवश्यकताओं के साथ, आप कोडिंग शुरू करने के लिए तैयार हैं!

## नामस्थान आयात करें

सबसे पहले, आइए आवश्यक नेमस्पेस को आयात करें। ये नेमस्पेस हमें वर्ड दस्तावेज़ों के साथ काम करने के लिए आवश्यक क्लास और विधियाँ प्रदान करेंगे।

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

अब जब हमने अपना नामस्थान तैयार कर लिया है, तो चलिए रोमांचक भाग की ओर बढ़ते हैं - सीधे वर्ड दस्तावेज़ में तालिकाओं को बनाना और सम्मिलित करना।

## चरण 1: दस्तावेज़ सेट करना

चलिए एक नया वर्ड डॉक्यूमेंट सेट अप करके शुरू करते हैं। यहीं पर हमारी टेबल डाली जाएगी।

```csharp
// आपके दस्तावेज़ निर्देशिका का पथ
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

 यह कोड एक नया Word दस्तावेज़ आरंभ करता है। आपको प्रतिस्थापित करने की आवश्यकता होगी`"YOUR DOCUMENT DIRECTORY"` आपके दस्तावेज़ निर्देशिका के वास्तविक पथ के साथ.

## चरण 2: टेबल ऑब्जेक्ट बनाना

इसके बाद, हम टेबल ऑब्जेक्ट बनाते हैं। यहीं पर हम अपनी टेबल की संरचना को परिभाषित करेंगे।

```csharp
// हम टेबल ऑब्जेक्ट बनाकर शुरू करते हैं। ध्यान दें कि हमें डॉक्यूमेंट ऑब्जेक्ट पास करना होगा
// प्रत्येक नोड के कन्स्ट्रक्टर के लिए। ऐसा इसलिए है क्योंकि हमारे द्वारा बनाया गया प्रत्येक नोड संबंधित होना चाहिए
// किसी दस्तावेज़ के लिए.
Table table = new Table(doc);
doc.FirstSection.Body.AppendChild(table);
```

यहां, हम एक नई तालिका बनाते हैं और इसे अपने दस्तावेज़ के पहले खंड के मुख्य भाग में जोड़ते हैं।

## चरण 3: पंक्तियाँ और कक्ष जोड़ना

एक टेबल पंक्तियों और कक्षों से बनी होती है। आइए इन तत्वों को चरण दर चरण जोड़ते हैं।

### पंक्ति जोड़ना

```csharp
// यहाँ हम EnsureMinimum को कॉल कर सकते हैं ताकि हमारे लिए पंक्तियाँ और सेल बनाए जा सकें। इस विधि का उपयोग किया जाता है
// यह सुनिश्चित करने के लिए कि निर्दिष्ट नोड वैध है। इस मामले में, एक वैध तालिका में कम से कम एक पंक्ति और एक सेल होना चाहिए।
// इसके बजाय, हम पंक्ति और तालिका का निर्माण स्वयं करेंगे।
// यदि हम किसी एल्गोरिथम के अंदर कोई तालिका बना रहे हों तो यह सबसे अच्छा तरीका होगा।
Row row = new Row(doc);
row.RowFormat.AllowBreakAcrossPages = true;
table.AppendChild(row);
```

यह कोड एक नई पंक्ति बनाता है और उसे हमारी तालिका में जोड़ता है।

### पंक्ति में कक्ष जोड़ना

अब, आइए अपनी पंक्ति में कुछ कक्ष जोड़ें। 

```csharp
Cell cell = new Cell(doc);
cell.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
cell.CellFormat.Width = 80;
cell.AppendChild(new Paragraph(doc));
cell.FirstParagraph.AppendChild(new Run(doc, "Row 1, Cell 1 Text"));
row.AppendChild(cell);
```

इस स्निपेट में, हम एक सेल बनाते हैं, उसका बैकग्राउंड रंग हल्का नीला सेट करते हैं, और उसकी चौड़ाई निर्धारित करते हैं। फिर, हम अपने टेक्स्ट को रखने के लिए सेल में एक पैराग्राफ़ और एक रन जोड़ते हैं।

## चरण 4: कोशिकाओं की क्लोनिंग

कोशिकाओं को जोड़ने की प्रक्रिया को तेज करने के लिए, हम मौजूदा कोशिकाओं का क्लोन बना सकते हैं।

```csharp
// फिर हम तालिका में अन्य कक्षों और पंक्तियों के लिए यही प्रक्रिया दोहराएंगे।
//हम मौजूदा कोशिकाओं और पंक्तियों की क्लोनिंग करके भी काम को गति दे सकते हैं।
row.AppendChild(cell.Clone(false));
row.LastCell.AppendChild(new Paragraph(doc));
row.LastCell.FirstParagraph.AppendChild(new Run(doc, "Row 1, Cell 2 Text"));
```

यह कोड मौजूदा सेल को क्लोन करता है और उसे पंक्ति में जोड़ता है। फिर हम नए सेल में एक पैराग्राफ और एक रन जोड़ते हैं।

## चरण 5: ऑटो फ़िट सेटिंग लागू करना

अंत में, आइए अपनी तालिका में ऑटो फिट सेटिंग लागू करें ताकि यह सुनिश्चित हो सके कि स्तंभों की चौड़ाई निश्चित है।

```csharp
// अब हम कोई भी ऑटो फिट सेटिंग लागू कर सकते हैं।
table.AutoFit(AutoFitBehavior.FixedColumnWidths);
```

## चरण 6: दस्तावेज़ को सहेजना

हमारी तालिका पूरी तरह से तैयार हो जाने के बाद, अब दस्तावेज़ को सहेजने का समय है।

```csharp
doc.Save(dataDir + "WorkingWithTables.InsertTableDirectly.docx");
```

यह कोड सम्मिलित तालिका के साथ दस्तावेज़ को सहेजता है।

## निष्कर्ष

बधाई हो! आपने Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में सीधे टेबल सफलतापूर्वक सम्मिलित कर ली है। इस प्रक्रिया का उपयोग प्रोग्रामेटिक रूप से जटिल टेबल बनाने के लिए किया जा सकता है, जिससे आपके दस्तावेज़ स्वचालन कार्य बहुत आसान हो जाते हैं। चाहे आप रिपोर्ट, चालान या कोई अन्य दस्तावेज़ प्रकार बना रहे हों, टेबल में हेरफेर करना समझना एक महत्वपूर्ण कौशल है।

## अक्सर पूछे जाने वाले प्रश्न

### मैं .NET के लिए Aspose.Words कैसे डाउनलोड कर सकता हूँ?
 आप .NET के लिए Aspose.Words को यहां से डाउनलोड कर सकते हैं[डाउनलोड पृष्ठ](https://releases.aspose.com/words/net/).

### क्या मैं खरीदने से पहले .NET के लिए Aspose.Words आज़मा सकता हूँ?
 हां, आप अनुरोध कर सकते हैं[मुफ्त परीक्षण](https://releases.aspose.com/) खरीदने से पहले पुस्तकालय का मूल्यांकन करें।

### मैं .NET के लिए Aspose.Words कैसे खरीदूं?
आप .NET के लिए Aspose.Words खरीद सकते हैं[खरीद पृष्ठ](https://purchase.aspose.com/buy).

### मैं .NET के लिए Aspose.Words का दस्तावेज़ कहां पा सकता हूं?
 दस्तावेज़ उपलब्ध है[यहाँ](https://reference.aspose.com/words/net/).

### यदि मुझे .NET के लिए Aspose.Words का उपयोग करते समय सहायता की आवश्यकता हो तो क्या होगा?
 सहायता के लिए आप यहां जा सकते हैं[Aspose.Words फ़ोरम](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
