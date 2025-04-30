---
"description": "Java के लिए Aspose.Words का उपयोग करके विषय-सूची (TOC) बनाना और उसे अनुकूलित करना सीखें। आसानी से व्यवस्थित और पेशेवर दस्तावेज़ बनाएँ।"
"linktitle": "विषय-सूची तैयार करना"
"second_title": "Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई"
"title": "Java के लिए Aspose.Words में विषय-सूची तैयार करना"
"url": "/hi/java/document-manipulation/generating-table-of-contents/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java के लिए Aspose.Words में विषय-सूची तैयार करना


## जावा के लिए Aspose.Words में विषय-सूची तैयार करने का परिचय

इस ट्यूटोरियल में, हम आपको Aspose.Words for Java का उपयोग करके सामग्री की तालिका (TOC) बनाने की प्रक्रिया से परिचित कराएँगे। TOC संगठित दस्तावेज़ बनाने के लिए एक महत्वपूर्ण विशेषता है। हम TOC की उपस्थिति और लेआउट को अनुकूलित करने का तरीका बताएंगे।

## आवश्यक शर्तें

आरंभ करने से पहले, सुनिश्चित करें कि आपके जावा प्रोजेक्ट में Aspose.Words for Java इंस्टॉल और सेट अप है।

## चरण 1: नया दस्तावेज़ बनाएँ

सबसे पहले, आइए काम करने के लिए एक नया दस्तावेज़ बनाएं।

```java
Document doc = new Document();
```

## चरण 2: TOC शैलियाँ अनुकूलित करें

अपने TOC के स्वरूप को अनुकूलित करने के लिए, आप इससे जुड़ी शैलियों को संशोधित कर सकते हैं। इस उदाहरण में, हम प्रथम-स्तरीय TOC प्रविष्टियों को बोल्ड करेंगे।

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

## चरण 3: अपने दस्तावेज़ में सामग्री जोड़ें

आप दस्तावेज़ में अपनी सामग्री जोड़ सकते हैं। इस सामग्री का उपयोग TOC बनाने के लिए किया जाएगा।

## चरण 4: TOC तैयार करें

TOC जेनरेट करने के लिए, अपने दस्तावेज़ में वांछित स्थान पर TOC फ़ील्ड डालें। यह फ़ील्ड आपके दस्तावेज़ में शीर्षकों और शैलियों के आधार पर स्वचालित रूप से पॉप्युलेट हो जाएगी।

```java
// अपने दस्तावेज़ में इच्छित स्थान पर TOC फ़ील्ड डालें।
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

## चरण 5: दस्तावेज़ सहेजें

अंत में, दस्तावेज़ को TOC के साथ सेव करें।

```java
doc.save("your_output_path_here");
```

## TOC में टैब स्टॉप को अनुकूलित करना

आप पृष्ठ संख्याओं के लेआउट को नियंत्रित करने के लिए अपने TOC में टैब स्टॉप को भी कस्टमाइज़ कर सकते हैं। यहाँ बताया गया है कि आप टैब स्टॉप को कैसे बदल सकते हैं:

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // इस पैराग्राफ में प्रयुक्त पहला टैब प्राप्त करें, जो पृष्ठ संख्याओं को संरेखित करता है।
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // पुराना टैब हटाएँ.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // संशोधित स्थिति पर एक नया टैब डालें (उदाहरण के लिए, बाईं ओर 50 इकाई)।
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

अब आपके दस्तावेज़ में पृष्ठ संख्या संरेखण के लिए समायोजित टैब स्टॉप के साथ एक अनुकूलित सामग्री तालिका है।


## निष्कर्ष

इस ट्यूटोरियल में, हमने जावा के लिए Aspose.Words का उपयोग करके सामग्री की तालिका (TOC) बनाने का तरीका खोजा है, जो Word दस्तावेज़ों के साथ काम करने के लिए एक शक्तिशाली लाइब्रेरी है। एक अच्छी तरह से संरचित TOC लंबे दस्तावेज़ों को व्यवस्थित करने और नेविगेट करने के लिए आवश्यक है, और Aspose.Words TOC को आसानी से बनाने और अनुकूलित करने के लिए उपकरण प्रदान करता है।

## अक्सर पूछे जाने वाले प्रश्न

### मैं TOC प्रविष्टियों का स्वरूपण कैसे बदल सकता हूँ?

आप TOC स्तरों से जुड़ी शैलियों को संशोधित कर सकते हैं `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`, जहाँ X TOC स्तर है.

### मैं अपने TOC में और अधिक स्तर कैसे जोड़ सकता हूँ?

अपने TOC में अधिक स्तर शामिल करने के लिए, आप TOC फ़ील्ड को संशोधित कर सकते हैं और स्तरों की वांछित संख्या निर्दिष्ट कर सकते हैं।

### क्या मैं विशिष्ट TOC प्रविष्टियों के लिए टैब स्टॉप की स्थिति बदल सकता हूँ?

हां, जैसा कि ऊपर दिए गए कोड उदाहरण में दिखाया गया है, आप पैराग्राफों के माध्यम से पुनरावृत्ति करके और टैब स्टॉप को तदनुसार संशोधित करके विशिष्ट TOC प्रविष्टियों के लिए टैब स्टॉप की स्थिति बदल सकते हैं।


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}