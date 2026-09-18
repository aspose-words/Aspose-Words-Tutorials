---
category: general
date: 2026-09-18
description: Aspose.Words के साथ एक खाली दस्तावेज़ बनाएं और Word में आकार सम्मिलित
  करें – सीखें कैसे एक त्रिकोण आकार जोड़ें और अधिक।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- add shapes to word
- how to insert triangle
- add triangle shape
- create word document
language: hi
lastmod: 2026-09-18
og_description: Aspose.Words का उपयोग करके Word में खाली दस्तावेज़ बनाएं और त्रिकोण
  आकार, समूहित आकार और अन्य ग्राफ़िक्स कैसे डालें सीखें। इस पूर्ण गाइड का पालन करें।
og_image_alt: Screenshot of a Word document showing a grouped shape with a triangle
  inside
og_title: खाली दस्तावेज़ बनाएं और वर्ड में आकृतियाँ जोड़ें – चरण-दर-चरण मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document and insert shapes to Word with Aspose.Words –
    learn how to add a triangle shape and more.
  headline: How to create blank document and add shapes to Word
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: खाली दस्तावेज़ कैसे बनाएं और वर्ड में आकार जोड़ें
url: /hi/java/images-shapes/how-to-create-blank-document-and-add-shapes-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word में खाली दस्तावेज़ कैसे बनाएं और आकार जोड़ें

यदि आपको **खाली दस्तावेज़ बनाना** है और फिर उसे ग्राफ़िक्स से समृद्ध करना है, तो यह गाइड आपको ठीक‑ठीक बताता है। हम शुरू से एक Word फ़ाइल बनाना और **Word में आकार जोड़ना**, जिसमें **त्रिकोण आकार कैसे डालें** शामिल है, Aspose.Words for Java का उपयोग करके दिखाएंगे।

आप इस ट्यूटोरियल को एक तैयार‑से‑उपयोग *.docx* फ़ाइल के साथ समाप्त करेंगे जिसमें एक समूहित आकार में त्रिकोण शामिल है। चरणों में प्रोजेक्ट सेटअप से लेकर अंतिम **create word document** को सहेजने तक सब कुछ शामिल है। Aspose.Words के अलावा कोई बाहरी टूल आवश्यक नहीं है।

## आवश्यकताएँ

* Java 17 या बाद का स्थापित हो  
* निर्भरता प्रबंधन के लिए Maven या Gradle  
* Aspose.Words for Java लाइसेंस (इस डेमो के लिए मुफ्त मूल्यांकन कार्य करता है)  

यदि आप कोई अलग बिल्ड सिस्टम पसंद करते हैं, तो निर्भरता सिंटैक्स को उसी अनुसार समायोजित करें। कोड किसी भी प्लेटफ़ॉर्म पर काम करता है जो Java का समर्थन करता है।

## Aspose.Words के साथ खाली दस्तावेज़ बनाएं

पहला ऑपरेशन मेमोरी में **खाली दस्तावेज़ बनाना** है। Aspose.Words एक `Document` क्लास प्रदान करता है जो किसी भी सामग्री के बिना Word फ़ाइल का प्रतिनिधित्व करता है।

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank document
```

`new Document()` कंस्ट्रक्टर एक खाली *.docx* संरचना बनाता है, जिसे आप बाद में पैराग्राफ, टेबल या ग्राफ़िक्स से भर सकते हैं। क्योंकि दस्तावेज़ खाली है, आप जो भी तत्व जोड़ते हैं उस पर पूरी नियंत्रण रख सकते हैं।

## Word में आकार जोड़ें – समूह आकार डालना

समूह आकार आपको कई ग्राफ़िक्स को एक इकाई के रूप में संभालने की अनुमति देता है। यह तब उपयोगी होता है जब आप कई आकारों को साथ में स्थानांतरित या आकार बदलना चाहते हैं।

```java
        // Step 2: Initialize a DocumentBuilder to construct content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a group shape of size 300 × 300 points
        GroupShape group = builder.insertGroupShape(300.0, 300.0);
```

`DocumentBuilder` सामग्री जोड़ने के लिए मुख्य API है। `insertGroupShape` कॉल 300 × 300 पॉइंट्स (लगभग 4 × 4 इंच) का कंटेनर बनाता है। इस कॉल के बाद कर्सर *समूह के अंदर* स्थित हो जाता है, अतिरिक्त आकारों के लिए तैयार।

### समूह आकार का उपयोग क्यों करें?

समूह बनाना संबंधित ग्राफ़िक्स को संरेखित रखता है और समान फ़ॉर्मेटिंग लागू करना आसान बनाता है। यदि आप बाद में त्रिकोण को स्थानांतरित करने का निर्णय लेते हैं, तो पूरा समूह साथ में चलता है, लेआउट को संरक्षित रखता है।

## समूह के अंदर त्रिकोण आकार कैसे डालें

अब हम **त्रिकोण आकार कैसे डालें** पर चर्चा करेंगे। त्रिकोण `ShapeType` के अंतर्निहित मानों में से एक है।

```java
        // Step 4: Move the cursor into the group's first paragraph
        builder.moveTo(group.getFirstParagraph());

        // Step 5: Insert a triangle shape of size 60 × 60 points inside the group
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);
```

`moveTo` कॉल सुनिश्चित करता है कि बिल्डर का इन्सर्शन पॉइंट समूह के पहले पैराग्राफ में हो। `insertShape` फिर 60 × 60 पॉइंट्स का त्रिकोण जोड़ता है। क्योंकि कर्सर समूह के अंदर है, त्रिकोण समूह आकार का एक चाइल्ड बन जाता है।

**त्रिकोण आकार जोड़ें** टिप्स:

* आकार पॉइंट्स में मापा जाता है; 72 पॉइंट्स एक इंच के बराबर होते हैं। अपने लेआउट के अनुसार आयाम समायोजित करें।  
* यदि आपको अलग दिशा चाहिए, तो `builder.getCurrentParagraph().getParagraphFormat().setAlignment()` का उपयोग करके समूह के भीतर आकार को संरेखित करें।  
* त्रिकोण समूह की भराव और रेखा शैलियों को विरासत में लेता है, जब तक आप उन्हें `shape.getFillColor()` या `shape.getStrokeColor()` से ओवरराइड न करें।  

## दस्तावेज़ सहेजें – create word document

ग्राफ़िक्स बन जाने के बाद, आप फ़ाइल को सहेजते हैं। यह चरण **create word document** ऑपरेशन को अंतिम रूप देता है।

```java
        // Step 6: Save the document with the extended group shape
        doc.save("ExtendedGroup.docx");               // create word document
    }
}
```

`doc.save` इन‑मेमोरी प्रतिनिधित्व को डिस्क पर एक मानक Word दस्तावेज़ के रूप में लिखता है। आप `ExtendedGroup.docx` को Microsoft Word, LibreOffice, या किसी भी व्यूअर में खोल सकते हैं जो OOXML फ़ॉर्मेट का समर्थन करता है। फ़ाइल में एक समूहित आकार दिखेगा जिसमें त्रिकोण होगा, बिल्कुल कोड द्वारा निर्मित जैसा।

## पूरा चलाने योग्य उदाहरण

सभी भागों को मिलाकर, यहाँ पूरा प्रोग्राम है जिसे आप कॉपी, कंपाइल और चलाकर उपयोग कर सकते हैं:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Prepare a builder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a group shape (300 × 300 points)
        GroupShape group = builder.insertGroupShape(300.0, 300.0);

        // 4. Position the cursor inside the group
        builder.moveTo(group.getFirstParagraph());

        // 5. Insert a triangle shape (60 × 60 points)
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);

        // 6. Save the file – this creates the final Word document
        doc.save("ExtendedGroup.docx");
    }
}
```

### अपेक्षित परिणाम

जब आप `ExtendedGroup.docx` खोलेंगे, तो आपको पृष्ठ के केंद्र में एक एकल समूह आकार दिखाई देगा। उस समूह के अंदर, एक छोटा त्रिकोण डिफ़ॉल्ट स्थिति में दिखाई देगा। त्रिकोण को समूह का हिस्सा बनाकर चयनित और स्थानांतरित किया जा सकता है, जिससे पुष्टि होती है कि **add shapes to word** इच्छित रूप से काम किया।

## आम प्रश्न और किनारे के मामले

| प्रश्न | उत्तर |
|----------|--------|
| *क्या मैं समूह के अंदर एक से अधिक आकार जोड़ सकता हूँ?* | हाँ। त्रिकोण डालने के बाद, कर्सर को समूह के अंदर रखें और `builder.insertShape` को फिर से अलग `ShapeType` के साथ कॉल करें। |
| *यदि मुझे त्रिकोण को लाल चाहिए तो क्या करें?* | `insertShape` द्वारा लौटाए गए `Shape` को प्राप्त करें और `shape.getFillColor().setColor(Color.RED)` को कॉल करें। |
| *क्या यह पुराने .doc फ़ाइलों के साथ काम करता है?* | Aspose.Words उस फ़ॉर्मेट में सहेजता है जिसे आप निर्दिष्ट करते हैं। लेगेसी Word दस्तावेज़ बनाने के लिए `doc.save("file.doc", SaveFormat.DOC)` का उपयोग करें। |
| *मैं समूह की बॉर्डर कैसे बदलूँ?* | आउटलाइन को कस्टमाइज़ करने के लिए `group.getStrokeColor().setColor(Color.BLUE)` और `group.setLineWeight(2.0)` का उपयोग करें। |
| *क्या त्रिकोण को घुमाने का कोई तरीका है?* | डिग्री में कोण सेट करने के लिए `shape.getRotation()` को कॉल करें। |

## प्रो टिप्स

* **Reuse the builder** – प्रत्येक आकार के लिए नया `DocumentBuilder` बनाना ओवरहेड जोड़ता है। प्रति दस्तावेज़ एक ही बिल्डर रखें।  
* **Unit conversion** – यदि आप मिलीमीटर के साथ काम करते हैं, तो उन्हें पॉइंट्स में बदलें (`points = mm * 2.83465`)।  
* **Performance** – बड़े दस्तावेज़ों के लिए, सभी आकार जोड़ने के बाद केवल एक बार `doc.updatePageLayout()` कॉल करें।  

## निष्कर्ष

अब आप जानते हैं कि **खाली दस्तावेज़ कैसे बनाएं**, **Word में आकार कैसे जोड़ें**, और विशेष रूप से Aspose.Words for Java का उपयोग करके **त्रिकोण आकार कैसे डालें**। पूरा उदाहरण एक खाली फ़ाइल से लेकर सहेजे गए **create word document** तक का पूर्ण वर्कफ़्लो दर्शाता है जिसमें एक समूहित त्रिकोण शामिल है।

यहाँ से आप अतिरिक्त `ShapeType` मानों का अन्वेषण कर सकते हैं, कस्टम स्टाइलिंग लागू कर सकते हैं, या कई समूहों को मिलाकर जटिल डायग्राम बना सकते हैं। विभिन्न आकारों, रंगों और स्थितियों के साथ प्रयोग करके Java में Word ऑटोमेशन में महारत हासिल करें।

--- 

*क्या आप अपनी अगली रिपोर्ट को ऑटोमेट करने के लिए तैयार हैं? उदाहरण को क्लोन करें, आयामों को समायोजित करें, और कोड को आज ही अपने एप्लिकेशन में एकीकृत करें।*

## आपको आगे क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन निकट-संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API सुविधाओं में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में समूह आकार बनाएं](/words/english/net/working-with-shapes/add-group-shape/)
- [छाया वाले आयत आकार के साथ खाली Word दस्तावेज़ बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words के साथ Word में आयत आकार बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}