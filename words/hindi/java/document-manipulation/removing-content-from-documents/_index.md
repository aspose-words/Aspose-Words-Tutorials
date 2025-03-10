---
title: Java के लिए Aspose.Words में दस्तावेज़ों से सामग्री हटाना
linktitle: दस्तावेज़ों से सामग्री हटाना
second_title: Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई
description: Aspose.Words for Java का उपयोग करके Java में Word दस्तावेज़ों से सामग्री निकालना सीखें। पेज ब्रेक, सेक्शन ब्रेक और बहुत कुछ हटाएँ। अपने दस्तावेज़ प्रसंस्करण को अनुकूलित करें।
weight: 16
url: /hi/java/document-manipulation/removing-content-from-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java के लिए Aspose.Words में दस्तावेज़ों से सामग्री हटाना


## जावा के लिए Aspose.Words का परिचय

इससे पहले कि हम हटाने की तकनीकों में उतरें, आइए संक्षेप में Aspose.Words for Java का परिचय दें। यह एक Java API है जो Word दस्तावेज़ों के साथ काम करने के लिए व्यापक सुविधाएँ प्रदान करता है। आप इस लाइब्रेरी का उपयोग करके Word दस्तावेज़ों को सहजता से बना सकते हैं, संपादित कर सकते हैं, परिवर्तित कर सकते हैं और उनमें हेरफेर कर सकते हैं।

## पेज ब्रेक हटाना

पेज ब्रेक का इस्तेमाल अक्सर दस्तावेज़ के लेआउट को नियंत्रित करने के लिए किया जाता है। हालाँकि, ऐसे मामले हो सकते हैं जहाँ आपको उन्हें हटाने की ज़रूरत हो। यहाँ बताया गया है कि आप Aspose.Words for Java का उपयोग करके पेज ब्रेक कैसे हटा सकते हैं:

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

यह कोड स्निपेट दस्तावेज़ में पैराग्राफों की पुनरावृत्ति करेगा, पृष्ठ विरामों की जांच करेगा और उन्हें हटा देगा।

## अनुभाग विराम हटाना

सेक्शन ब्रेक दस्तावेज़ को अलग-अलग फ़ॉर्मेटिंग के साथ अलग-अलग सेक्शन में विभाजित करते हैं। सेक्शन ब्रेक हटाने के लिए, इन चरणों का पालन करें:

```java
for (int i = doc.getSections().getCount() - 2; i >= 0; i--) {
    doc.getLastSection().prependContent(doc.getSections().get(i));
    doc.getSections().get(i).remove();
}
```

यह कोड उलटे क्रम में अनुभागों को दोहराता है, वर्तमान अनुभाग की सामग्री को अंतिम अनुभाग के साथ जोड़ता है और फिर कॉपी किए गए अनुभाग को हटा देता है।

## फ़ुटर हटाना

Word दस्तावेज़ों में फ़ुटर में अक्सर पृष्ठ संख्याएँ, दिनांक या अन्य जानकारी होती है। यदि आपको उन्हें हटाने की आवश्यकता है, तो आप निम्न कोड का उपयोग कर सकते हैं:

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

यह कोड दस्तावेज़ के प्रत्येक अनुभाग से सभी प्रकार के फ़ुटर (प्रथम, प्राथमिक और सम) को हटा देता है।

## विषय-सूची हटाना

विषय-सूची (TOC) फ़ील्ड एक गतिशील तालिका उत्पन्न करते हैं जो शीर्षकों और उनके पृष्ठ क्रमांकों को सूचीबद्ध करती है। TOC को हटाने के लिए, आप निम्न कोड का उपयोग कर सकते हैं:

```java
Document doc = new Document("Your Directory Path" + "Table of contents.docx");
removeTableOfContents(doc, 0);
doc.save("Your Directory Path" + "RemoveContent.RemoveToc.doc");
```

 यह कोड एक विधि को परिभाषित करता है`removeTableOfContents` जो दस्तावेज़ से निर्दिष्ट TOC को हटा देता है.


## निष्कर्ष

इस लेख में, हमने जावा के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों से विभिन्न प्रकार की सामग्री को हटाने का तरीका खोजा है। चाहे वह पेज ब्रेक हो, सेक्शन ब्रेक हो, फ़ुटर हो या सामग्री की तालिका हो, Aspose.Words आपके दस्तावेज़ों को प्रभावी ढंग से हेरफेर करने के लिए उपकरण प्रदान करता है।

## अक्सर पूछे जाने वाले प्रश्न

### मैं विशिष्ट पृष्ठ विराम कैसे हटा सकता हूँ?

विशिष्ट पृष्ठ विरामों को हटाने के लिए, अपने दस्तावेज़ में पैराग्राफ़ों को पुनरावृत्त करें और इच्छित पैराग्राफ़ों के लिए पृष्ठ विराम विशेषता को साफ़ करें।

### क्या मैं फ़ुटर के साथ-साथ हेडर भी हटा सकता हूँ?

हां, आप पाद लेखों के लिए लेख में दिखाए गए समान दृष्टिकोण का पालन करके अपने दस्तावेज़ से शीर्षलेख और पादलेख दोनों को हटा सकते हैं।

### क्या Aspose.Words for Java नवीनतम Word दस्तावेज़ प्रारूपों के साथ संगत है?

हां, Java के लिए Aspose.Words नवीनतम Word दस्तावेज़ स्वरूपों का समर्थन करता है, जो आधुनिक दस्तावेज़ों के साथ संगतता सुनिश्चित करता है।

### Aspose.Words for Java क्या अन्य दस्तावेज़ हेरफेर सुविधाएँ प्रदान करता है?

Aspose.Words for Java में कई तरह की सुविधाएँ हैं, जिनमें दस्तावेज़ निर्माण, संपादन, रूपांतरण और बहुत कुछ शामिल है। विस्तृत जानकारी के लिए आप इसके दस्तावेज़ देख सकते हैं।
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
