---
"description": "Aspose.Words for Java में हेडर और फ़ुटर का उपयोग कैसे करें, चरण-दर-चरण सीखें। बिना किसी परेशानी के पेशेवर दस्तावेज़ बनाएँ।"
"linktitle": "हेडर और फूटर का उपयोग करना"
"second_title": "Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई"
"title": "जावा के लिए Aspose.Words में हेडर और फूटर का उपयोग करना"
"url": "/hi/java/using-document-elements/using-headers-and-footers/"
"weight": 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# जावा के लिए Aspose.Words में हेडर और फूटर का उपयोग करना


इस व्यापक गाइड में, हम आपको Aspose.Words for Java में हेडर और फ़ुटर के साथ काम करने की प्रक्रिया से परिचित कराएँगे। हेडर और फ़ुटर दस्तावेज़ फ़ॉर्मेटिंग में आवश्यक तत्व हैं, और Aspose.Words आपकी ज़रूरतों के अनुसार उन्हें बनाने और अनुकूलित करने के लिए शक्तिशाली उपकरण प्रदान करता है।

अब, आइए इनमें से प्रत्येक चरण पर विस्तार से नजर डालें।

## 1. Aspose.Words का परिचय

Aspose.Words एक शक्तिशाली जावा एपीआई है जो आपको प्रोग्रामेटिक रूप से वर्ड दस्तावेज़ बनाने, हेरफेर करने और प्रस्तुत करने की अनुमति देता है। यह हेडर और फ़ुटर सहित दस्तावेज़ फ़ॉर्मेटिंग के लिए व्यापक सुविधाएँ प्रदान करता है।

## 2. अपना जावा वातावरण स्थापित करना

Aspose.Words का उपयोग शुरू करने से पहले, सुनिश्चित करें कि आपने अपना Java डेवलपमेंट वातावरण सही तरीके से सेट किया है। आप Aspose.Words डॉक्यूमेंटेशन पेज पर आवश्यक सेटअप निर्देश पा सकते हैं: [Aspose.Words जावा दस्तावेज़ीकरण](https://reference.aspose.com/words/java/).

## 3. नया दस्तावेज़ बनाना

हेडर और फ़ुटर के साथ काम करने के लिए, आपको Aspose.Words का उपयोग करके एक नया दस्तावेज़ बनाना होगा। निम्न कोड यह दर्शाता है कि यह कैसे करना है:

```java
// नया दस्तावेज़ बनाने के लिए जावा कोड
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 4. पेज सेटअप को समझना

आपके दस्तावेज़ के लेआउट को नियंत्रित करने के लिए पेज सेटअप महत्वपूर्ण है। आप हेडर और फ़ुटर से संबंधित विभिन्न गुणों को निर्दिष्ट कर सकते हैं `PageSetup` वर्ग. उदाहरण के लिए:

```java
// पेज गुण सेट करना
Section currentSection = builder.getCurrentSection();
PageSetup pageSetup = currentSection.getPageSetup();
pageSetup.setDifferentFirstPageHeaderFooter(true);
pageSetup.setHeaderDistance(20.0);
```

## 5. अलग प्रथम पृष्ठ शीर्षलेख/पादलेख

Aspose.Words आपको अपने दस्तावेज़ के पहले पृष्ठ के लिए अलग-अलग हेडर और फ़ुटर रखने की अनुमति देता है। `pageSetup.setDifferentFirstPageHeaderFooter(true);` इस सुविधा को सक्षम करने के लिए.

## 6. हेडर्स के साथ काम करना

### 6.1. हेडर में टेक्स्ट जोड़ना

आप हेडर में टेक्स्ट जोड़ सकते हैं `DocumentBuilder`यहाँ एक उदाहरण है:

```java
// प्रथम पृष्ठ के शीर्षक में पाठ जोड़ना
builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.getFont().setName("Arial");
builder.getFont().setBold(true);
builder.getFont().setSize(14.0);
builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

### 6.2. हेडर में छवियाँ सम्मिलित करना

हेडर में छवियाँ सम्मिलित करने के लिए, आप इसका उपयोग कर सकते हैं `insertImage` विधि। यहाँ एक उदाहरण है:

```java
// हेडर में छवि सम्मिलित करना
builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
    RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
```

### 6.3. हेडर शैलियों को अनुकूलित करना

जैसा कि ऊपर दिए गए उदाहरणों में दिखाया गया है, आप फ़ॉन्ट, संरेखण आदि जैसे विभिन्न गुण सेट करके हेडर शैलियों को अनुकूलित कर सकते हैं।

## 7. फ़ुटर्स के साथ काम करना

### 7.1. फूटर्स में टेक्स्ट जोड़ना

हेडर के समान, आप फ़ुटर में भी टेक्स्ट जोड़ सकते हैं `DocumentBuilder`यहाँ एक उदाहरण है:

```java
// प्राथमिक फ़ुटर में पाठ जोड़ना
builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
// आवश्यकतानुसार पाठ और फ़ील्ड डालें
```

### 7.2. फ़ुटर्स में छवियाँ सम्मिलित करना

फ़ुटर में छवियाँ सम्मिलित करने के लिए, का उपयोग करें `insertImage` विधि, हेडर की तरह ही।

### 7.3. पाद लेख शैलियों को अनुकूलित करना

फ़ुटर शैलियों को अनुकूलित करने के लिए निम्न का उपयोग करें: `DocumentBuilder`, हेडर को अनुकूलित करने के समान।

## 8. पृष्ठ क्रमांकन

आप इस तरह के फ़ील्ड का उपयोग करके अपने हेडर और फ़ुटर में पेज नंबर शामिल कर सकते हैं `PAGE` और `NUMPAGES`जब आप पेज जोड़ते या हटाते हैं तो ये फ़ील्ड स्वचालित रूप से अपडेट हो जाते हैं।

## 9. फ़ुटर में कॉपीराइट जानकारी

अपने दस्तावेज़ के पाद लेख में कॉपीराइट जानकारी जोड़ने के लिए, आप दो कक्षों वाली एक तालिका का उपयोग कर सकते हैं, जिसमें एक कक्ष बाईं ओर तथा दूसरा कक्ष दाईं ओर संरेखित होगा, जैसा कि कोड स्निपेट में दिखाया गया है।

## 10. कई अनुभागों के साथ काम करना

Aspose.Words आपको एक दस्तावेज़ के भीतर कई अनुभागों के साथ काम करने की अनुमति देता है। आप प्रत्येक अनुभाग के लिए अलग-अलग पेज सेटअप और हेडर/फ़ुटर सेट कर सकते हैं।

## 11. लैंडस्केप ओरिएंटेशन

यदि आवश्यक हो तो आप विशिष्ट अनुभागों के ओरिएंटेशन को लैंडस्केप मोड में बदल सकते हैं।

## 12. पिछले अनुभागों से हेडर/फुटर की प्रतिलिपि बनाना

जटिल दस्तावेज़ बनाते समय पिछले अनुभागों से शीर्षलेख और पादलेख की प्रतिलिपि बनाने से समय की बचत हो सकती है।

## 13. अपने दस्तावेज़ को सहेजना

अपना दस्तावेज़ बनाने और उसे अनुकूलित करने के बाद, इसे सहेजना न भूलें `doc.save()` तरीका।

## संपूर्ण स्रोत कोड
```java
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        Section currentSection = builder.getCurrentSection();
        PageSetup pageSetup = currentSection.getPageSetup();
        // निर्दिष्ट करें कि क्या हम चाहते हैं कि प्रथम पृष्ठ के शीर्षलेख/पादलेख अन्य पृष्ठों से भिन्न हों।
        // आप निर्दिष्ट करने के लिए PageSetup.OddAndEvenPagesHeaderFooter प्रॉपर्टी का भी उपयोग कर सकते हैं
        // विषम और सम पृष्ठों के लिए अलग-अलग शीर्षलेख/पादलेख।
        pageSetup.setDifferentFirstPageHeaderFooter(true);
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
        builder.getFont().setName("Arial");
        builder.getFont().setBold(true);
        builder.getFont().setSize(14.0);
        builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_PRIMARY);
        // हेडर के ऊपरी/बाएं कोने में एक स्थित छवि डालें।
        // पृष्ठ के ऊपरी/बाएं किनारों से दूरी 10 पॉइंट निर्धारित की गई है।
        builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
            RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.write("Aspose.Words Header/Footer Creation Primer.");
        builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
        // हम पाठ के एक भाग को पंक्ति में (पृष्ठ क्रमांकन के साथ) बनाने के लिए दो कक्षों वाली तालिका का उपयोग करते हैं।
        // बाईं ओर संरेखित किया जाना चाहिए, तथा पाठ का अन्य भाग (कॉपीराइट सहित) दाईं ओर संरेखित किया जाना चाहिए।
        builder.startTable();
        builder.getCellFormat().clearFormatting();
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        // यह वर्तमान पृष्ठ संख्या और पृष्ठों की संख्या की स्वचालित गणना करने के लिए PAGE और NUMPAGES फ़ील्ड का उपयोग करता है।
        builder.write("Page ");
        builder.insertField("PAGE", "");
        builder.write(" of ");
        builder.insertField("NUMPAGES", "");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.LEFT);
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        builder.write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.endRow();
        builder.endTable();
        builder.moveToDocumentEnd();
        // एक दूसरा पेज बनाने के लिए पेज ब्रेक बनाएं जिस पर प्राथमिक शीर्षलेख/पादलेख दिखाई देंगे।
        builder.insertBreak(BreakType.PAGE_BREAK);
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        currentSection = builder.getCurrentSection();
        pageSetup = currentSection.getPageSetup();
        pageSetup.setOrientation(Orientation.LANDSCAPE);
        // इस अनुभाग को अलग प्रथम पृष्ठ शीर्षलेख/पादलेख की आवश्यकता नहीं है, हमें दस्तावेज़ में केवल एक शीर्षक पृष्ठ की आवश्यकता है,
        // और इस पृष्ठ के लिए शीर्षलेख/पादलेख पहले से ही पिछले अनुभाग में परिभाषित किया जा चुका है।
        pageSetup.setDifferentFirstPageHeaderFooter(false);
        // यह अनुभाग पिछले अनुभाग के शीर्षलेख/पादलेख प्रदर्शित करता है
        // इस पृष्ठ की चौड़ाई को रद्द करने के लिए डिफ़ॉल्ट रूप से currentSection.HeadersFooters.LinkToPrevious(false) को कॉल करें
        // नए अनुभाग के लिए अलग है, और इसलिए हमें पाद लेख तालिका के लिए अलग सेल चौड़ाई निर्धारित करने की आवश्यकता है।
        currentSection.getHeadersFooters().linkToPrevious(false);
        // यदि हम इस अनुभाग के लिए पहले से मौजूद हेडर/फुटर सेट का उपयोग करना चाहते हैं।
        // लेकिन कुछ मामूली संशोधनों के साथ, हेडर/फुटर की प्रतिलिपि बनाना समीचीन हो सकता है
        // पिछले अनुभाग से आवश्यक संशोधनों को वहां लागू करें जहां हम उन्हें चाहते हैं।
        copyHeadersFootersFromPreviousSection(currentSection);
        HeaderFooter primaryFooter = currentSection.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
        Row row = primaryFooter.getTables().get(0).getFirstRow();
        row.getFirstCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        row.getLastCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        doc.save("Your Directory Path" + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```	
copyHeadersFootersFromPreviousSection विधि का स्रोत कोड
```java
    /// <सारांश>
    //पिछले अनुभाग के शीर्षलेखों/पादलेखों को क्लोन करता है और निर्दिष्ट अनुभाग में उनकी प्रतिलिपि बनाता है।
    /// </सारांश>
    private void copyHeadersFootersFromPreviousSection(Section section)
    {
        Section previousSection = (Section)section.getPreviousSibling();
        if (previousSection == null)
            return;
        section.getHeadersFooters().clear();
        for (HeaderFooter headerFooter : (Iterable<HeaderFooter>) previousSection.getHeadersFooters())
            section.getHeadersFooters().add(headerFooter.deepClone(true));
	}
```

## निष्कर्ष

इस ट्यूटोरियल में, हमने Aspose.Words for Java में हेडर और फ़ुटर के साथ काम करने की मूल बातें कवर की हैं। आपने हेडर और फ़ुटर बनाने, उन्हें कस्टमाइज़ करने और स्टाइल करने के साथ-साथ अन्य आवश्यक दस्तावेज़ फ़ॉर्मेटिंग तकनीकों के बारे में सीखा है।

अधिक जानकारी और उन्नत सुविधाओं के लिए, देखें [Aspose.Words जावा दस्तावेज़ीकरण](https://reference.aspose.com/words/java/).

## पूछे जाने वाले प्रश्न

### 1. मैं अपने दस्तावेज़ के पाद लेख में पृष्ठ संख्या कैसे जोड़ सकता हूँ?
आप पृष्ठ संख्या जोड़कर पृष्ठ जोड़ सकते हैं `PAGE` Aspose.Words का उपयोग करके पाद लेख में फ़ील्ड जोड़ें।

### 2. क्या Aspose.Words जावा विकास वातावरण के साथ संगत है?
हां, Aspose.Words जावा डेवलपमेंट के लिए सहायता प्रदान करता है। सुनिश्चित करें कि आपके पास आवश्यक सेटअप मौजूद है।

### 3. क्या मैं हेडर और फूटर के फ़ॉन्ट और शैली को अनुकूलित कर सकता हूँ?
बिल्कुल, आप अपने हेडर और फूटर को देखने में आकर्षक बनाने के लिए फ़ॉन्ट, संरेखण और अन्य शैलियों को अनुकूलित कर सकते हैं।

### 4. क्या विषम और सम पृष्ठों के लिए अलग-अलग शीर्षक रखना संभव है?
हां, आप उपयोग कर सकते हैं `PageSetup.OddAndEvenPagesHeaderFooter` विषम और सम पृष्ठों के लिए अलग-अलग शीर्षलेख निर्दिष्ट करने के लिए।

### 5. मैं Aspose.Words for Java के साथ कैसे शुरुआत करूं?
आरंभ करने के लिए, यहां जाएं [Aspose.Words जावा दस्तावेज़ीकरण](https://reference.aspose.com/words/java/) एपीआई के उपयोग पर व्यापक मार्गदर्शन के लिए कृपया देखें.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}