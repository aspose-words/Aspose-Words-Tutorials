---
"description": "Java के लिए Aspose.Words का उपयोग करके गतिशील विषय-सूची बनाना सीखें। चरण-दर-चरण मार्गदर्शन और स्रोत कोड उदाहरणों के साथ TOC जनरेशन में महारत हासिल करें।"
"linktitle": "विषय सूची पीढ़ी"
"second_title": "Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई"
"title": "विषय सूची पीढ़ी"
"url": "/hi/java/table-processing/table-contents-generation/"
"weight": 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# विषय सूची पीढ़ी

## परिचय

क्या आपने कभी अपने Word दस्तावेज़ों में गतिशील और पेशेवर दिखने वाली विषय-सूची (TOC) बनाने में संघर्ष किया है? अब और न देखें! Aspose.Words for Java के साथ, आप पूरी प्रक्रिया को स्वचालित कर सकते हैं, समय की बचत कर सकते हैं और सटीकता सुनिश्चित कर सकते हैं। चाहे आप एक व्यापक रिपोर्ट या एक अकादमिक पेपर बना रहे हों, यह ट्यूटोरियल आपको Java के साथ प्रोग्रामेटिक रूप से TOC बनाने में मदद करेगा। शुरू करने के लिए तैयार हैं? चलिए शुरू करते हैं!

## आवश्यक शर्तें

कोडिंग शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

1. जावा डेवलपमेंट किट (JDK): आपके सिस्टम पर इंस्टॉल है। आप इसे यहाँ से डाउनलोड कर सकते हैं [ओरेकल की वेबसाइट](https://www.oracle.com/java/technologies/javase-downloads.html).
2. Aspose.Words for Java लाइब्रेरी: से नवीनतम संस्करण डाउनलोड करें [रिलीज़ पेज](https://releases.aspose.com/words/java/).
3. एकीकृत विकास वातावरण (IDE): जैसे कि IntelliJ IDEA, Eclipse, या NetBeans.
4. Aspose अस्थायी लाइसेंस: मूल्यांकन सीमाओं से बचने के लिए, एक प्राप्त करें [अस्थायी लाइसेंस](https://purchase.aspose.com/temporary-license/).

## पैकेज आयात करें

Aspose.Words for Java का प्रभावी ढंग से उपयोग करने के लिए, सुनिश्चित करें कि आप आवश्यक क्लासेस को आयात करें। आयात यहाँ दिए गए हैं:

```java
import com.aspose.words.*;
```

अपने वर्ड दस्तावेज़ में गतिशील TOC उत्पन्न करने के लिए इन चरणों का पालन करें।

## चरण 1: दस्तावेज़ और दस्तावेज़बिल्डर को आरंभ करें

पहला कदम एक नया दस्तावेज़ बनाना और उसका उपयोग करना है `DocumentBuilder` वर्ग को इसमें हेरफेर करने के लिए।


```java
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document`: वर्ड दस्तावेज़ का प्रतिनिधित्व करता है.
- `DocumentBuilder`: एक सहायक वर्ग जो दस्तावेज़ में आसान हेरफेर की अनुमति देता है।

## चरण 2: विषय-सूची डालें

अब, दस्तावेज़ के आरंभ में TOC डालें।


```java
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");
builder.insertBreak(BreakType.PAGE_BREAK);
```

- `insertTableOfContents`: TOC फ़ील्ड सम्मिलित करता है। पैरामीटर निर्दिष्ट करते हैं:
  - `\o "1-3"`: स्तर 1 से 3 तक के शीर्षक शामिल करें।
  - `\h`: प्रविष्टियों को हाइपरलिंक बनाएं.
  - `\z`: वेब दस्तावेज़ों के लिए पृष्ठ संख्या को दबाएँ।
  - `\u`: हाइपरलिंक के लिए शैलियाँ संरक्षित रखें.
- `insertBreak`: TOC के बाद एक पृष्ठ विराम जोड़ता है।

## चरण 3: TOC भरने के लिए शीर्षक जोड़ें

TOC को भरने के लिए, आपको शीर्षक शैलियों के साथ पैराग्राफ जोड़ने की आवश्यकता है।


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 1");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_2);
builder.writeln("Heading 1.1");
builder.writeln("Heading 1.2");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 2");
```

- `setStyleIdentifier`: पैराग्राफ़ शैली को एक विशिष्ट शीर्षक स्तर पर सेट करता है (उदाहरण के लिए, `HEADING_1`, `HEADING_2`).
- `writeln`निर्दिष्ट शैली के साथ दस्तावेज़ में पाठ जोड़ता है।

## चरण 4: नेस्टेड हेडिंग जोड़ें

TOC स्तरों को प्रदर्शित करने के लिए, नेस्टेड शीर्षकों को शामिल करें।


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_3);
builder.writeln("Heading 3.1.1");
builder.writeln("Heading 3.1.2");
builder.writeln("Heading 3.1.3");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_4);
builder.writeln("Heading 3.1.3.1");
builder.writeln("Heading 3.1.3.2");
```

- TOC में पदानुक्रम दिखाने के लिए गहरे स्तर के शीर्षक जोड़ें।

## चरण 5: TOC फ़ील्ड अपडेट करें

नवीनतम शीर्षकों को प्रदर्शित करने के लिए TOC फ़ील्ड को अद्यतन किया जाना चाहिए।


```java
doc.updateFields();
```

- `updateFields`: दस्तावेज़ में सभी फ़ील्ड को ताज़ा करता है, यह सुनिश्चित करता है कि TOC जोड़े गए शीर्षकों को प्रतिबिंबित करता है।

## चरण 6: दस्तावेज़ सहेजें

अंत में, दस्तावेज़ को अपने इच्छित प्रारूप में सहेजें।


```java
doc.save(dataDir + "DocumentBuilder.InsertToc.docx");
```

- `save`: दस्तावेज़ को निर्यात करता है `.docx` फ़ाइल. आप अन्य प्रारूप निर्दिष्ट कर सकते हैं जैसे `.pdf` या `.txt` यदि ज़रूरत हो तो।

## निष्कर्ष

बधाई हो! आपने Aspose.Words for Java का उपयोग करके Word दस्तावेज़ में सफलतापूर्वक एक गतिशील विषय-सूची तैयार कर ली है। कोड की कुछ ही पंक्तियों के साथ, आपने एक ऐसा कार्य स्वचालित कर दिया है जिसमें अन्यथा घंटों लग सकते थे। तो, आगे क्या है? अपनी TOC को विशिष्ट आवश्यकताओं के अनुरूप बनाने के लिए विभिन्न शीर्षक शैलियों और प्रारूपों के साथ प्रयोग करने का प्रयास करें।

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं TOC प्रारूप को और अधिक अनुकूलित कर सकता हूँ?
बिल्कुल! आप TOC पैरामीटर समायोजित कर सकते हैं जैसे पेज नंबर शामिल करना, टेक्स्ट संरेखित करना, या कस्टम हेडिंग शैलियों का उपयोग करना।

### क्या Java के लिए Aspose.Words हेतु लाइसेंस अनिवार्य है?
हां, पूर्ण कार्यक्षमता के लिए लाइसेंस की आवश्यकता है। आप एक से शुरू कर सकते हैं [अस्थायी लाइसेंस](https://purchase.aspose.com/temporary-license/).

### क्या मैं किसी मौजूदा दस्तावेज़ के लिए TOC तैयार कर सकता हूँ?
हाँ! दस्तावेज़ को लोड करें `Document` ऑब्जेक्ट पर जाएं और TOC को सम्मिलित करने और अद्यतन करने के लिए समान चरणों का पालन करें।

### क्या यह पीडीएफ निर्यात के लिए काम करता है?
हां, यदि आप दस्तावेज़ को पीडीएफ में सहेजते हैं तो TOC पीडीएफ में दिखाई देगा `.pdf` प्रारूप।

### मैं अधिक दस्तावेज कहां पा सकता हूं?
इसकी जाँच पड़ताल करो [जावा दस्तावेज़ीकरण के लिए Aspose.Words](https://reference.aspose.com/words/java/) अधिक उदाहरण और विवरण के लिए.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}