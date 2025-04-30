---
"description": "Aspose.Words for Java में फ़ुटनोट्स और एंडनोट्स का प्रभावी ढंग से उपयोग करना सीखें। आज ही अपने दस्तावेज़ स्वरूपण कौशल को बेहतर बनाएँ!"
"linktitle": "फ़ुटनोट्स और एंडनोट्स का उपयोग करना"
"second_title": "Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई"
"title": "जावा के लिए Aspose.Words में फ़ुटनोट्स और एंडनोट्स का उपयोग करना"
"url": "/hi/java/using-document-elements/using-footnotes-and-endnotes/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# जावा के लिए Aspose.Words में फ़ुटनोट्स और एंडनोट्स का उपयोग करना


इस ट्यूटोरियल में, हम आपको Aspose.Words for Java में फ़ुटनोट्स और एंडनोट्स का उपयोग करने की प्रक्रिया से परिचित कराएँगे। फ़ुटनोट्स और एंडनोट्स दस्तावेज़ स्वरूपण में आवश्यक तत्व हैं, जिनका उपयोग अक्सर उद्धरण, संदर्भ और अतिरिक्त जानकारी के लिए किया जाता है। Aspose.Words for Java फ़ुटनोट्स और एंडनोट्स के साथ सहजता से काम करने के लिए मज़बूत कार्यक्षमता प्रदान करता है।

## 1. फुटनोट्स और एंडनोट्स का परिचय

फ़ुटनोट और एंडनोट ऐसे एनोटेशन हैं जो किसी दस्तावेज़ के भीतर पूरक जानकारी या उद्धरण प्रदान करते हैं। फ़ुटनोट पृष्ठ के निचले भाग में दिखाई देते हैं, जबकि एंडनोट किसी अनुभाग या दस्तावेज़ के अंत में एकत्र किए जाते हैं। इनका उपयोग आमतौर पर अकादमिक पत्रों, रिपोर्टों और कानूनी दस्तावेज़ों में स्रोतों को संदर्भित करने या सामग्री को स्पष्ट करने के लिए किया जाता है।

## 2. अपना वातावरण स्थापित करना

इससे पहले कि हम फ़ुटनोट्स और एंडनोट्स के साथ काम करना शुरू करें, आपको अपना डेवलपमेंट एनवायरनमेंट सेट अप करना होगा। सुनिश्चित करें कि आपके प्रोजेक्ट में Aspose.Words for Java API इंस्टॉल और कॉन्फ़िगर किया गया है।

## 3. अपने दस्तावेज़ में फ़ुटनोट जोड़ना

अपने दस्तावेज़ में फ़ुटनोट जोड़ने के लिए, इन चरणों का पालन करें:
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";

public void getFootnoteOptions(){
    Document doc = new Document(dataDir + "Document.docx");
    
    // फ़ुटनोट क्षेत्र को फ़ॉर्मेट करने के लिए स्तंभों की संख्या निर्दिष्ट करें.
    doc.getFootnoteOptions().setColumns(3);
    doc.save("Your Directory Path" + "WorkingWithFootnotes.SetFootNoteColumns.docx");
}
```

## 4. फ़ुटनोट विकल्प संशोधित करना

आप फ़ुटनोट विकल्पों को उनके स्वरूप और व्यवहार को अनुकूलित करने के लिए संशोधित कर सकते हैं। यहाँ बताया गया है कि कैसे:
```java
@Test
public void setFootnoteAndEndNotePosition() throws Exception {
    Document doc = new Document(dataDir + "Document.docx");
    
    doc.getFootnoteOptions().setPosition(FootnotePosition.BENEATH_TEXT);
    doc.getEndnoteOptions().setPosition(EndnotePosition.END_OF_SECTION);
    
    doc.save(outPath + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
}
```

## 5. अपने दस्तावेज़ में एंडनोट्स जोड़ना

अपने दस्तावेज़ में एंडनोट जोड़ना बहुत आसान है। यहाँ एक उदाहरण दिया गया है:
```java
@Test
public void setEndnoteOptions() throws Exception {
    Document doc = new Document(dataDir + "Document.docx");
    DocumentBuilder builder = new DocumentBuilder(doc);
    
    builder.write("Some text");
    builder.insertFootnote(FootnoteType.ENDNOTE, "Footnote text.");
    
    EndnoteOptions option = doc.getEndnoteOptions();
    option.setRestartRule(FootnoteNumberingRule.RESTART_PAGE);
    option.setPosition(EndnotePosition.END_OF_SECTION);
    
    doc.save(outPath + "WorkingWithFootnotes.SetEndnoteOptions.docx");
}
```

## 6. एंडनोट सेटिंग्स को अनुकूलित करना

आप अपने दस्तावेज़ की आवश्यकताओं को पूरा करने के लिए एंडनोट सेटिंग्स को और अधिक अनुकूलित कर सकते हैं।

## संपूर्ण स्रोत कोड
```java
	string dataDir = "Your Document Directory";
	string outPath = "Your Output Directory";
	public void getFootnoteOptions(){
        Document doc = new Document(dataDir + "Document.docx");
        // फ़ुटनोट क्षेत्र को फ़ॉर्मेट करने के लिए स्तंभों की संख्या निर्दिष्ट करें.
        doc.getFootnoteOptions().setColumns(3);
        doc.save("Your Directory Path" + "WorkingWithFootnotes.SetFootNoteColumns.docx");
    }
    @Test
    public void setFootnoteAndEndNotePosition() throws Exception
    {
        Document doc = new Document(dataDir + "Document.docx");
        doc.getFootnoteOptions().setPosition(FootnotePosition.BENEATH_TEXT);
        doc.getEndnoteOptions().setPosition(EndnotePosition.END_OF_SECTION);
        doc.save(outPath + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
    }
    @Test
    public void setEndnoteOptions() throws Exception
    {
        Document doc = new Document(dataDir + "Document.docx");
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.write("Some text");
        builder.insertFootnote(FootnoteType.ENDNOTE, "Footnote text.");
        EndnoteOptions option = doc.getEndnoteOptions();
        option.setRestartRule(FootnoteNumberingRule.RESTART_PAGE);
        option.setPosition(EndnotePosition.END_OF_SECTION);
        doc.save(outPath + "WorkingWithFootnotes.SetEndnoteOptions.docx");
	}
```

## 7. निष्कर्ष

इस ट्यूटोरियल में, हमने Aspose.Words for Java में फ़ुटनोट्स और एंडनोट्स के साथ काम करने का तरीका खोजा है। ये सुविधाएँ उचित उद्धरणों और संदर्भों के साथ अच्छी तरह से संरचित दस्तावेज़ बनाने के लिए अमूल्य हैं।

अब जब आपने फ़ुटनोट्स और एंडनोट्स का उपयोग करना सीख लिया है, तो आप अपने दस्तावेज़ के स्वरूपण को बेहतर बना सकते हैं और अपनी सामग्री को अधिक पेशेवर बना सकते हैं।

### अक्सर पूछे जाने वाले प्रश्नों

### 1. फुटनोट और एंडनोट में क्या अंतर है?
फ़ुटनोट पृष्ठ के निचले भाग में दिखाई देते हैं, जबकि एंडनोट किसी अनुभाग या दस्तावेज़ के अंत में एकत्रित किए जाते हैं।

### 2. मैं फ़ुटनोट्स या एंडनोट्स की स्थिति कैसे बदल सकता हूँ?
आप इसका उपयोग कर सकते हैं `setPosition` फ़ुटनोट या एंडनोट की स्थिति बदलने की विधि।

### 3. क्या मैं फ़ुटनोट्स और एंडनोट्स के स्वरूपण को अनुकूलित कर सकता हूँ?
हां, आप Java के लिए Aspose.Words का उपयोग करके फ़ुटनोट्स और एंडनोट्स के स्वरूपण को अनुकूलित कर सकते हैं।

### 4. क्या दस्तावेज़ स्वरूपण में फ़ुटनोट और एंडनोट महत्वपूर्ण हैं?
हां, दस्तावेजों में संदर्भ और अतिरिक्त जानकारी प्रदान करने के लिए फुटनोट और एंडनोट आवश्यक हैं।

Aspose.Words for Java की अधिक सुविधाओं का पता लगाने और अपने दस्तावेज़ निर्माण क्षमताओं को बढ़ाने के लिए स्वतंत्र महसूस करें। हैप्पी कोडिंग!


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}