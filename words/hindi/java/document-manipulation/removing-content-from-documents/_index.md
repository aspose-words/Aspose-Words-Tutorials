---
date: 2026-01-06
description: Aspose.Words for Java का उपयोग करके Word दस्तावेज़ों से फुटर कैसे हटाएँ,
  साथ ही सेक्शन ब्रेक, पेज ब्रेक और अधिक कैसे हटाएँ, सीखें।
linktitle: Removing Content from Documents
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java का उपयोग करके Word दस्तावेज़ों से फुटर कैसे हटाएँ
url: /hi/java/document-manipulation/removing-content-from-documents/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java का इस्तेमाल करके Word डॉक्यूमेंट्स से फुटर कैसे हटाएँ

## Aspose.Words for Java का इंट्रोडक्शन

इस ट्यूटोरियल में आप **Word डॉक्यूमेंट्स से फुटर हटाने** के लिए Aspose.Words for Java का प्रोग्रामेटिक इस्तेमाल सिखाएँगे। चाहे आपको जेनरेटेड रिपोर्ट्स को क्लियर करना हो, दीर्घ जानकारी हटानी हो, या बाकी टेम्पलेट को व्यवस्थित करना हो, यह गाइड सबसे सामान्य सामग्री‑रिमूवल लैंडस्केप्स—पेज ब्रेक, सेक्शन ब्रेक, फुटर, और टेबल ऑफ़ मटीरियल्स—को कवर करता है। निर्भर शुरू करते हैं!

## क्विक आंसर्स
- **क्या मैं फुटर हटाते समय दूसरी सामग्री को प्रभावित किए बिना कर सकता हूँ?** हाँ, API आपको केवल फुटर नोड को टारगेट करने की अनुमति देता है।

- **क्या इन उदाहरणों को चलाने के लिए लाइसेंस चाहिए?** डेवलपमेंट के लिए फ्री ट्रायल चलती है; प्रोडक्शन के लिए लाइसेंस ज़रूरी है।
- **कौन से Word फ़ॉर्मेट सपोर्टेड हैं?** DOC, DOCX, DOCM, और OOXML‑आधारित फ़ॉर्मेट।
- **क्या कोड Java8 और उसके बाद के संस्करण के साथ संगत है?** बिल्कुल, लाइब्रेरी संस्करण 8 से आगे Java‑संगत है।
- **सेक्शन ब्रेक कैसे डिलीट करें?** नीचे “सेक्शन ब्रेक डिलीट करने का तरीका” सेक्शन देखें।

## “Word से फ़ुटर हटाएँ” क्या है?

Word डॉक्यूमेंट से फ़ुटर हटाना मतलब प्रत्येक पेज के नीचे मौजूद `HeaderFooter` नोड को डिलीट करना। यह ऑपरेशन तब उपयोगी होता है जब आप केवल Header‑केवल लेआउट बनाना चाहते हैं या फ़ुटर में मौजूद संवेदनशील डेटा को हटाना चाहते हैं।

## इस कार्य के लिए Java के लिए Aspose.Words का उपयोग क्यों करें?

Aspose.Words एक उच्च स्तरीय ऑब्जेक्ट मॉडल प्रदान करता है जो DOCX फ़ाइल फ़ॉर्मेट की एन्कोडिंग को एब्स्ट्रैक्ट करता है। आप कुछ ही जूतों के Java कोड से ग्राफिक्स, रन, सेक्शन, और फुटर को मैनीपुलेट कर सकते हैं, बिना सर्वर पर Microsoft Word इंस्टॉल किए।

## Prerequisites
- Java Development Kit (JDK)8या उससे नया वर्जन।
- Aspose.Words for Java Library (Aspose वेबसाइट से डाउनलोड करें)।
- एक सैंपल Word डॉक्यूमेंट (`Document.docx`) जिसे आप डायरेक्टरी में रखें।

## पेज ब्रेक हटाना

Page breaks पेजिनेशन को नियंत्रित करते हैं लेकिन कभी‑कभी इन्हें हटाना पड़ता है। नीचे दिया गया स्निपेट हर पैराग्राफ़ को स्कैन करता है, `PageBreakBefore` फ़्लैग को क्लियर करता है, और किसी भी स्पष्ट पेज‑ब्रेक कैरेक्टर को हटाता है।

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
NodeCollection paragraphs = doc.getChildNodes(NodeType.PARAGRAPH, true);
for (Paragraph para : (Iterable<Paragraph>) paragraphs) {
    if (para.getParagraphFormat().getPageBreakBefore()) {
        para.getParagraphFormat().setPageBreakBefore(false);
    }
    for (Run run : para.getRuns()) {
        if (run.getText().contains(ControlChar.PAGE_BREAK)) {
            run.setText(run.getText().replace(ControlChar.PAGE_BREAK, ""));
        }
    }
}
doc.save("Your Directory Path" + "RemoveContent.RemovePageBreaks.docx");
```

*प्रो टिप:* फुटर हटाने से पहले इसे चलाएँ यदि आप सिंगल-पेज लेआउट चाहते हैं।

## सेक्शन ब्रेक कैसे डिलीट करें

सेक्शन ब्रेक दस्तावेज़ को स्वतंत्र सेक्शन में विभाजित करते हैं, जिनके अपने हेडर, फुटर, और पेज सेटिंग्स होते हैं। सेक्शन को मर्ज करके प्रभावी रूप से **सेक्शन ब्रेक डिलीट** करने के लिए, रिवर्स ऑर्डर में इटररेट करें, प्रत्येक पहले वाले सेक्शन की सामग्री को अंतिम सेक्शन के आगे प्री‑पेंड करें, और फिर खाली सेक्शन को हटाएँ।

```java
for (int i = doc.getSections().getCount() - 2; i >= 0; i--) {
    doc.getLastSection().prependContent(doc.getSections().get(i));
    doc.getSections().get(i).remove();
}
```

यह तरीका सभी कंटेंट को बरकरार रखता है जबकि स्ट्रक्चरल ब्रेक को समाप्त करता है।

## फुटर्स हटाना (मुख्य लक्ष्य: वर्ड से फुटर्स हटाना)

फुटर अक्सर पेज नंबर, डेट, या संवेदनशील नोट्स रखते हैं। नीचे दिया गया कोड **सभी प्रकार के फुटर**—फ़र्स्ट पेज, प्राइमरी, और इवन पेज—को हर सेक्शन से हटाता है।

```java
Document doc = new Document("Your Directory Path" + "Header and footer types.docx");
for (Section section : doc.getSections()) {
    HeaderFooter footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_FIRST);
    footer.remove();
    footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
    footer.remove();
    footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_EVEN);
    footer.remove();
}
doc.save("Your Directory Path" + "RemoveContent.RemoveFooters.docx");
```

इस स्निपेट को चलाने के बाद, परिणामस्वरूप दस्तावेज़ में **कोई फुटर नहीं** रहेगा, जिससे “remove footers from Word” का मुख्य लक्ष्य प्राप्त होता है।

## विषय-सूची हटाना

टेबल ऑफ़ कंटेंट्स (TOC) एक फ़ील्ड के रूप में स्टोर किया जाता है। इसे डिलीट करने के लिए, उसके इंडेक्स द्वारा TOC फ़ील्ड को लोकेट करें और संबंधित नोड को हटाएँ।

```java
Document doc = new Document("Your Directory Path" + "Table of contents.docx");
removeTableOfContents(doc, 0);
doc.save("Your Directory Path" + "RemoveContent.RemoveToc.doc");
```

*(`removeTableOfContents` मेथड Aspose.Words उदाहरणों का हिस्सा है और सुसंगत TOC नोड को हटाता है।)*

## सामान्य समस्याएं और समस्या निवारण

| लक्षण | संभावित कारण | ठीक करें |
|---------|--------------|-----|
| कोड चलाने के बाद भी फुटर दिख रहे हैं | दस्तावेज़ में **header/footer** जोड़े हैं जो एक्सेस नहीं हो रहे (जैसे `FOOTER_FIRST` गायब) | सभी `HeaderFooterType` वैल्यूज़ पर लूप करें या `remove()` कॉल करने से पहले `null` चेक करें। |
| सेक्शन ब्रेक डिलीट करने के बाद पेज लेआउट अनपेक्षित रूप से बदल गया | सेक्शन‑स्पेसिफिक पेज सेटिंग्स (मार्जिन, ओरिएंटेशन) खो गई | हटाने से पहले सेक्शन सेटिंग्स को टार्गेट सेक्शन में कॉपी करें। |
| `ControlChar.PAGE_BREAK` हटाया नहीं गया | डॉक्यूमेंट पेज‑ब्रेक न्यूलर की जगह **सेक्शन ब्रेक** इस्तेमाल कर रहा है | पहले “सेक्शन ब्रेक डिलीट करने का तरीका” लागू करें। |

## अक्सर पूछे जाने वाले सवाल

**Q: क्या मैं केवल विशिष्ट फुटर (जैसे केवल फर्स्ट-पेज फुटर) हटाना चाहता हूँ?**
A: हाँ। उसके प्रकार (`FOOTER_FIRST`) से फुटर प्राप्त करें और केवल उस इंस्टेंस पर `remove()` कॉल करें।

**Q: सेक्शन ब्रेक को सामग्री मर्ज किए बिना कैसे डिलीट करें?**
A: यदि आपको उसकी सामग्री रखने की ज़रूरत नहीं है तो आप सीधे `Section` नोड को हटा सकते हैं, लेकिन ध्यान रखें कि उस सेक्शन से जुड़े सभी हेडर/फुटर भी खो देंगे।

**Q: क्या प्रोग्रामेटिक रूप से यह पता लगाया जा सकता है कि डॉक्यूमेंट में TOC मौजूद है या नहीं, डिलीट करने से पहले?**
A: `doc.getRange().getFields()` का इस्तेमाल करें और `FieldType.FIELD_TABLE_OF_CONTENTS` प्रकार के फील्ड की जांच करें।

**Q: क्या Aspose.Words विस्थापित वर्ड सबमिशन से फुटर हटाने का सपोर्ट करता है?**
A: हाँ, बस पासवर्ड के साथ डॉक्यूमेंट खोलें: `new Document(path, new LoadOptions(password))`।

**Q: क्या फुटर हटाने से डॉक्यूमेंट की पेजिनेशन प्रभावित होगी?**
A: फुटर हटाने से पेज नंबर नहीं बदलता जब तक कि फुटर में पेज-नंबर फील्ड न हो। अगर आपको पेज नंबर री-नंबर करने की ज़रूरत है, तो पेज-नंबर फील्ड को अपडेट करें।

## निष्कर्ष

हमने Aspose.Words for Java का उपयोग करके **Word दस्तावेज़ों से फुटर हटाने** के सभी आवश्यक चरणों को कवर किया, साथ ही पेज ब्रेक डिलीट करने, **सेक्शन ब्रेक डिलीट करने** और टेबल ऑफ़ कंटेंट्स को हटाने के संबंधित कार्य भी। इन स्निपेट्स को अपनाकर आप अपने एप्लिकेशन की आवश्यकताओं के अनुसार साफ़, प्रोफेशनल दस्तावेज़ बना सकते हैं।

---

**अंतिम अद्यतन:** 2026-01-06  
**परीक्षित संस्करण:** Aspose.Words for Java 24.12  
**लेखक:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
