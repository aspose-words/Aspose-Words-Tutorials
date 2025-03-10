---
title: जावा के लिए Aspose.Words में सामग्री निकालने के लिए सहायक विधियाँ
linktitle: सामग्री निकालने के लिए सहायक विधियाँ
second_title: Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई
description: Java के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों से कुशलतापूर्वक सामग्री निकालने का तरीका जानें। इस व्यापक गाइड में सहायक विधियों, कस्टम फ़ॉर्मेटिंग और बहुत कुछ का पता लगाएं।
weight: 14
url: /hi/java/document-manipulation/helper-methods-for-extracting-content/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# जावा के लिए Aspose.Words में सामग्री निकालने के लिए सहायक विधियाँ


## जावा के लिए Aspose.Words में सामग्री निकालने के लिए सहायक विधियों का परिचय

Aspose.Words for Java एक शक्तिशाली लाइब्रेरी है जो डेवलपर्स को Word दस्तावेज़ों के साथ प्रोग्रामेटिक रूप से काम करने की अनुमति देती है। Word दस्तावेज़ों के साथ काम करते समय एक सामान्य कार्य उनसे सामग्री निकालना है। इस लेख में, हम Aspose.Words for Java का उपयोग करके कुशलतापूर्वक सामग्री निकालने के लिए कुछ सहायक विधियों का पता लगाएंगे।

## आवश्यक शर्तें

इससे पहले कि हम कोड उदाहरणों में उतरें, सुनिश्चित करें कि आपके पास Aspose.Words for Java आपके Java प्रोजेक्ट में इंस्टॉल और सेट अप है। आप इसे यहाँ से डाउनलोड कर सकते हैं[यहाँ](https://releases.aspose.com/words/java/).

## सहायक विधि 1: शैली के आधार पर पैराग्राफ़ निकालना

```java
public static ArrayList<Paragraph> paragraphsByStyleName(Document doc, String styleName) {
    // निर्दिष्ट शैली के पैराग्राफ़ एकत्रित करने के लिए एक सरणी बनाएँ।
    ArrayList<Paragraph> paragraphsWithStyle = new ArrayList<Paragraph>();
    NodeCollection paragraphs = doc.getChildNodes(NodeType.PARAGRAPH, true);

    // निर्दिष्ट शैली वाले पैराग्राफ ढूंढने के लिए सभी पैराग्राफ देखें।
    for (Paragraph paragraph : (Iterable<Paragraph>) paragraphs) {
        if (paragraph.getParagraphFormat().getStyle().getName().equals(styleName))
            paragraphsWithStyle.add(paragraph);
    }
    return paragraphsWithStyle;
}
```

आप अपने Word दस्तावेज़ में किसी खास शैली वाले पैराग्राफ़ को निकालने के लिए इस विधि का उपयोग कर सकते हैं। यह तब उपयोगी होता है जब आप किसी खास फ़ॉर्मेटिंग वाली सामग्री को निकालना चाहते हैं, जैसे कि शीर्षक या ब्लॉक उद्धरण।

## हेल्पर विधि 2: नोड्स द्वारा सामग्री निकालना

```java
public static ArrayList<Node> extractContentBetweenNodes(Node startNode, Node endNode, boolean isInclusive) {
    // सबसे पहले, जाँच लें कि इस विधि को भेजे गए नोड्स उपयोग के लिए वैध हैं या नहीं।
    verifyParameterNodes(startNode, endNode);
    
    // निकाले गए नोड्स को संग्रहीत करने के लिए एक सूची बनाएं.
    ArrayList<Node> nodes = new ArrayList<Node>();

    // यदि कोई भी मार्कर टिप्पणी का भाग है, जिसमें टिप्पणी भी शामिल है, तो हमें पॉइंटर को स्थानांतरित करने की आवश्यकता है
    // CommentRangeEnd नोड के बाद पाए गए कमेंट नोड पर अग्रेषित करें।
    if (endNode.getNodeType() == NodeType.COMMENT_RANGE_END && isInclusive) {
        Node node = findNextNode(NodeType.COMMENT, endNode.getNextSibling());
        if (node != null)
            endNode = node;
    }
    
    // यदि आवश्यक हो तो मार्कर नोड्स को विभाजित करने के लिए इस विधि में पास किए गए मूल नोड्स का रिकॉर्ड रखें।
    Node originalStartNode = startNode;
    Node originalEndNode = endNode;

    //ब्लॉक-स्तरीय नोड्स (पैराग्राफ और तालिकाएँ) के आधार पर सामग्री निकालें। उन्हें खोजने के लिए पैरेंट नोड्स के माध्यम से जाएँ।
    // हम पहले और अंतिम नोड की सामग्री को विभाजित करेंगे, यह इस बात पर निर्भर करेगा कि मार्कर नोड इनलाइन हैं या नहीं।
    startNode = getAncestorInBody(startNode);
    endNode = getAncestorInBody(endNode);
    boolean isExtracting = true;
    boolean isStartingNode = true;
    // वर्तमान नोड जिसे हम दस्तावेज़ से निकाल रहे हैं।
    Node currNode = startNode;

    // सामग्री निकालना शुरू करें। सभी ब्लॉक-स्तरीय नोड्स को प्रोसेस करें और पहले को विशेष रूप से विभाजित करें
    // और अंतिम नोड्स को आवश्यकतानुसार बदलें ताकि पैराग्राफ़ फ़ॉर्मेटिंग बरकरार रहे।
    // यह विधि नियमित एक्सट्रैक्टर की तुलना में थोड़ी अधिक जटिल है क्योंकि हमें कारक की आवश्यकता होती है
    // इसे उपयोगी बनाने के लिए इनलाइन नोड्स, फील्ड्स, बुकमार्क्स आदि का उपयोग करके निष्कर्षण करना।
    while (isExtracting) {
        // प्रतिलिपि प्राप्त करने के लिए वर्तमान नोड और उसके संतानों का क्लोन बनाएं।
        Node cloneNode = currNode.deepClone(true);
        boolean isEndingNode = currNode.equals(endNode);
        if (isStartingNode || isEndingNode) {
            // हमें प्रत्येक मार्कर को अलग से संसाधित करने की आवश्यकता है, इसलिए इसे एक अलग विधि में पास करें।
            // नोड इंडेक्स को बनाए रखने के लिए सबसे पहले End को संसाधित किया जाना चाहिए।
            if (isEndingNode) {
                // !isStartingNode: यदि मार्कर एक ही नोड हैं तो नोड को दो बार न जोड़ें।
                processMarker(cloneNode, nodes, originalEndNode, currNode, isInclusive,
                        false, !isStartingNode, false);
                isExtracting = false;
            }
            //सशर्त को अलग करने की आवश्यकता है क्योंकि ब्लॉक स्तर के प्रारंभ और अंत मार्कर एक ही नोड हो सकते हैं।
            if (isStartingNode) {
                processMarker(cloneNode, nodes, originalStartNode, currNode, isInclusive,
                        true, true, false);
                isStartingNode = false;
            }
        } else
            // नोड कोई आरंभ या अंत मार्कर नहीं है, बस कॉपी को सूची में जोड़ें।
            nodes.add(cloneNode);

        // अगले नोड पर जाएँ और उसे निकालें। यदि अगला नोड शून्य है,
        // शेष सामग्री एक अलग अनुभाग में पाई जाती है।
        if (currNode.getNextSibling() == null && isExtracting) {
            // अगले अनुभाग पर जाएँ.
            Section nextSection = (Section) currNode.getAncestor(NodeType.SECTION).getNextSibling();
            currNode = nextSection.getBody().getFirstChild();
        } else {
            // बॉडी में अगले नोड पर जाएँ.
            currNode = currNode.getNextSibling();
        }
    }

    // इनलाइन बुकमार्क्स वाले मोड की अनुकूलता के लिए, अगला पैराग्राफ (खाली) जोड़ें।
    if (isInclusive && originalEndNode == endNode && !originalEndNode.isComposite())
        includeNextParagraph(endNode, nodes);

    // नोड मार्करों के बीच नोड्स लौटाएँ.
    return nodes;
}
```

यह विधि आपको दो निर्दिष्ट नोड्स के बीच सामग्री निकालने की अनुमति देती है, चाहे वे पैराग्राफ, टेबल या कोई अन्य ब्लॉक-स्तरीय तत्व हों। यह इनलाइन मार्कर, फ़ील्ड और बुकमार्क सहित विभिन्न परिदृश्यों को संभालता है।

## हेल्पर विधि 3: नया दस्तावेज़ तैयार करना

```java
public static Document generateDocument(Document srcDoc, ArrayList<Node> nodes) throws Exception {
    Document dstDoc = new Document();
    
    // रिक्त दस्तावेज़ से पहला पैराग्राफ़ हटाएँ।
    dstDoc.getFirstSection().getBody().removeAllChildren();
    
    // सूची से प्रत्येक नोड को नए दस्तावेज़ में आयात करें। नोड का मूल स्वरूपण बनाए रखें।
    NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
    for (Node node : nodes) {
        Node importNode = importer.importNode(node, true);
        dstDoc.getFirstSection().getBody().appendChild(importNode);
    }
    
    return dstDoc;
}
```

यह विधि आपको स्रोत दस्तावेज़ से नोड्स की सूची आयात करके एक नया दस्तावेज़ बनाने की अनुमति देती है। यह नोड्स के मूल स्वरूपण को बनाए रखता है, जिससे यह विशिष्ट सामग्री वाले नए दस्तावेज़ बनाने के लिए उपयोगी हो जाता है।

## निष्कर्ष

Word दस्तावेज़ों से सामग्री निकालना कई दस्तावेज़ प्रसंस्करण कार्यों का एक महत्वपूर्ण हिस्सा हो सकता है। Aspose.Words for Java शक्तिशाली सहायक विधियाँ प्रदान करता है जो इस प्रक्रिया को सरल बनाती हैं। चाहे आपको शैली के अनुसार पैराग्राफ़ निकालने हों, नोड्स के बीच सामग्री निकालनी हो या नए दस्तावेज़ बनाने हों, ये विधियाँ आपको अपने Java अनुप्रयोगों में Word दस्तावेज़ों के साथ कुशलतापूर्वक काम करने में मदद करेंगी।

## अक्सर पूछे जाने वाले प्रश्न

### मैं Java के लिए Aspose.Words कैसे स्थापित कर सकता हूँ?

 जावा के लिए Aspose.Words स्थापित करने के लिए, आप इसे Aspose वेबसाइट से डाउनलोड कर सकते हैं।[यहाँ](https://releases.aspose.com/words/java/) नवीनतम संस्करण प्राप्त करने के लिए.

### क्या मैं किसी Word दस्तावेज़ के विशिष्ट अनुभागों से सामग्री निकाल सकता हूँ?

हां, आप इस लेख में बताए गए तरीकों का उपयोग करके वर्ड डॉक्यूमेंट के विशिष्ट अनुभागों से सामग्री निकाल सकते हैं। बस उस अनुभाग को परिभाषित करने वाले आरंभ और अंत नोड्स को निर्दिष्ट करें जिसे आप निकालना चाहते हैं।

### क्या Aspose.Words for Java, Java 11 के साथ संगत है?

हां, Aspose.Words for Java, Java 11 और उच्चतर संस्करणों के साथ संगत है। आप इसे अपने Java अनुप्रयोगों में बिना किसी समस्या के उपयोग कर सकते हैं।

### क्या मैं निकाली गई सामग्री के स्वरूपण को अनुकूलित कर सकता हूँ?

हां, आप जेनरेट किए गए दस्तावेज़ में आयातित नोड्स को संशोधित करके निकाली गई सामग्री के स्वरूपण को अनुकूलित कर सकते हैं। Aspose.Words for Java आपकी ज़रूरतों को पूरा करने के लिए व्यापक स्वरूपण विकल्प प्रदान करता है।

### मैं Java के लिए Aspose.Words के लिए अधिक दस्तावेज़ और उदाहरण कहां पा सकता हूं?

 आप Aspose.Words for Java के लिए Aspose वेबसाइट पर विस्तृत दस्तावेज़ और उदाहरण पा सकते हैं।[https://reference.aspose.com/words/java/](https://reference.aspose.com/words/java/) विस्तृत दस्तावेज़ीकरण और संसाधनों के लिए.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
