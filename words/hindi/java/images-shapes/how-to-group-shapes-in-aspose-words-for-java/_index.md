---
category: general
date: 2026-10-20
description: Aspose.Words for Java में आकृतियों को कैसे समूहित करें – सीखें कैसे आयताकार
  आकृति डालें, उन्हें समूहित करें, और एक ही गाइड में दस्तावेज़ को सहेजें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- how to insert rectangle
language: hi
lastmod: 2026-10-20
og_description: Aspose.Words for Java में आकृतियों को कैसे समूहित करें। यह ट्यूटोरियल
  दिखाता है कि आयताकार आकृति कैसे डालें, उन्हें समूहित करें, और परिणाम को निर्यात
  करें।
og_image_alt: Screenshot of a Word document showing two grouped rectangle shapes created
  with Aspose.Words for Java
og_title: Aspose.Words for Java में आकृतियों को समूहित करने का तरीका – चरण-दर-चरण
  मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: How to group shapes in Aspose.Words for Java – learn how to insert
    rectangle shape, group them, and save the document in a single guide.
  headline: How to group shapes in Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- shape manipulation
title: Aspose.Words for Java में आकृतियों को कैसे समूहित करें
url: /hi/java/images-shapes/how-to-group-shapes-in-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java में आकृतियों को समूहित कैसे करें

यदि आपको Aspose.Words for Java का उपयोग करके Word दस्तावेज़ में **how to group shapes** की आवश्यकता है, तो यह गाइड आपको पूरा कार्यप्रवाह दिखाता है। आप सीखेंगे कि **insert rectangle shape** कैसे डालें, दूसरा आयत जोड़ें, दोनों आकृतियों को समूहित करें, और अंत में फ़ाइल को सहेजें—सभी स्पष्ट, चलाने योग्य कोड के साथ।

आकृतियों को समूहित करना उपयोगी होता है जब आप कई ड्रॉइंग्स को एक इकाई के रूप में स्थानांतरित, घुमाना या शैलीबद्ध करना चाहते हैं। चाहे आप रिपोर्ट टेम्पलेट, आरेख, या कस्टम फ़्लायर बना रहे हों, आकृति समूहित करने में निपुणता आपके समय की बचत करती है और लेआउट को सुसंगत रखती है।

इस ट्यूटोरियल में आप करेंगे:

* नया `Document` और `DocumentBuilder` बनाएँ।
* **How to insert rectangle** आकृतियों को सटीक आयामों के साथ डालें।
* आयतों को `GroupShape` में समूहित करें।
* दस्तावेज़ को सहेजें और परिणाम सत्यापित करें।

> **Prerequisite** – आपके प्रोजेक्ट में Aspose.Words for Java (v23.12 या बाद का) जोड़ना आवश्यक है। Maven उपयोगकर्ता नीचे दिखाए गए निर्भरता को शामिल कर सकते हैं।

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## आप क्या चाहिए

| आइटम | कारण |
|------|--------|
| Java 17+ | आधुनिक भाषा सुविधाएँ और बेहतर प्रदर्शन |
| Aspose.Words for Java | `DocumentBuilder`, `Shape`, और `GroupShape` APIs प्रदान करता है |
| एक IDE (IntelliJ IDEA, Eclipse, VS Code, आदि) | उदाहरण को संकलित और चलाने के लिए |
| फ़ोल्डर में लिखने की अनुमति | दस्तावेज़ डिस्क पर सहेजा जाएगा |

## आयत आकृति कैसे डालें

पहला कदम `Document` और `DocumentBuilder` बनाना है। बिल्डर आपको `insertShape` जैसी विधियाँ देता है जिससे आप ड्रॉइंग ऑब्जेक्ट्स रख सकते हैं।

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle (100 × 50 points).
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Optional: give the rectangle a fill color for visibility.
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Step 3: Insert the second rectangle (80 × 40 points).
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // The two rectangles are currently independent objects.
        // Below we will group them together.
```

> **Why this matters** – `insertShape` का उपयोग करना Aspose.Words में **how to insert rectangle** ऑब्जेक्ट्स डालने का मानक तरीका है। यह स्वचालित रूप से आकृति को दस्तावेज़ के वर्तमान पैराग्राफ में जोड़ देता है, इसलिए आपको लो‑लेवल OpenXML को संभालने की जरूरत नहीं है।

## आयत स्थितियों को समायोजित करना (वैकल्पिक)

यदि दूसरे आयत को पहले आयत के सापेक्ष कस्टम स्थान चाहिए, तो आप उसकी `left` और `top` प्रॉपर्टीज़ को बदल सकते हैं। यह कदम वैकल्पिक है लेकिन अक्सर सटीक आरेख लेआउट के लिए आवश्यक होता है।

```java
        // Optional: reposition the second rectangle 20 points to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        // Optional: align the top edges.
        rectangle2.setTop(rectangle1.getTop());
```

> **Pro tip:** सभी माप बिंदुओं (points) में होते हैं (1 pt ≈ 1/72 in)। यदि आपको UI‑आधारित गणनाओं के लिए पिक्सेल मान चाहिए तो `convertPointsToPixels` का उपयोग करें।

## आकृतियों को कैसे समूहित करें

अब जब आयतें मौजूद हैं, आप उन्हें `GroupShape` के अंदर रख सकते हैं। समूहित करने से दो आयतें एक ही वस्तु की तरह व्यवहार करती हैं—समूह को स्थानांतरित, घुमाने या स्वरूपित करने से दोनों आकृतियों पर प्रभाव पड़ेगा।

```java
        // Step 4: Insert an empty GroupShape.
        GroupShape group = builder.insertGroupShape();

        // Step 5: Add the rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Optional: set a border for the whole group.
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);
```

> **Why grouping works** – `GroupShape` `Shape` से विरासत में प्राप्त करता है, इसलिए आप समूह को किसी अन्य ड्रॉइंग ऑब्जेक्ट की तरह ही संभाल सकते हैं। जब आप `appendChild` कॉल करते हैं, तो आकृतियाँ अपनी मूल स्थिति से हटकर समूह की चाइल्ड बन जाती हैं।

## समूहित आकृतियों वाले दस्तावेज़ को सहेजना

अंत में, दस्तावेज़ को डिस्क पर लिखें। फ़ाइल में दो आयतों के साथ एक ही `GroupShape` होगा।

```java
        // Step 6: Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### अपेक्षित परिणाम

Microsoft Word में `GroupShape.docx` खोलें:

* आपको दो आयतें (नीली और हरी) साइड‑बाय‑साइड स्थित दिखेंगी।
* किसी भी आयत का चयन करने से पूरा समूह चयनित हो जाएगा—खींचने से दोनों साथ में चलेंगे।
* समूह में एक पतली लाल सीमा है, जो दर्शाती है कि `GroupShape` गुण लागू हुए हैं।

यदि आप समूह पर राइट‑क्लिक करके **Group → Ungroup** चुनते हैं, तो आयतें स्वतंत्र आकृतियों में वापस आ जाती हैं, जिससे यह सिद्ध होता है कि समूहित करने की प्रक्रिया उलटनीय है।

## सामान्य विविधताएँ और किनारे के मामले

| स्थिति | कैसे निपटें |
|-----------|------------------|
| **More than two shapes** | प्रत्येक आकृति डालें, फिर सभी को एक ही `GroupShape` में जोड़ें। |
| **Different shape types** (e.g., ellipse, picture) | `builder.insertShape(ShapeType.ELLIPSE, …)` या `builder.insertImage(...)` का उपयोग करके जोड़ने से पहले। |
| **Scaling the group** | `group.setWidth(newWidth)` या `group.setHeight(newHeight)` कॉल करें; चाइल्ड्स अनुपातिक रूप से स्केल होते हैं। |
| **Rotating the group** | `group.setRotationAngle(45);` पूरे संग्रह को उसके केंद्र के चारों ओर घुमाता है। |
| **Preserving original positions** | समूहित करने से पहले प्रत्येक आकृति के `left`/`top` को सहेजें और आवश्यकता पड़ने पर अनग्रुप करने के बाद पुनर्स्थापित करें। |

## पूरा, चलाने योग्य उदाहरण

नीचे पूर्ण Java क्लास दिया गया है जिसे आप अपने IDE में कॉपी‑पेस्ट कर सकते हैं। इसमें सभी इम्पोर्ट्स, त्रुटि संभालना, और स्पष्टता के लिए टिप्पणियाँ शामिल हैं।

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert the first rectangle (100 × 50 points) and give it a blue fill.
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Insert the second rectangle (80 × 40 points) with a green fill.
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // Optional positioning – move the second rectangle 20 pt to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        rectangle2.setTop(rectangle1.getTop());

        // Insert an empty group shape.
        GroupShape group = builder.insertGroupShape();

        // Add both rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Style the group (red border, 1.5 pt weight).
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);

        // Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

प्रोग्राम चलाएँ, परिणामी `GroupShape.docx` खोलें, और आप वर्णित अनुसार समूहित आयतें देखेंगे।

## निष्कर्ष

अब आप Aspose.Words for Java में **how to group shapes** जानते हैं, दस्तावेज़ बनाने से लेकर आयत आकृतियों को डालने, उनकी स्थितियों को समायोजित करने, और अंत में `GroupShape` के साथ समूहित करने तक। यह तकनीक आपको कई ड्रॉइंग्स को एक इकाई के रूप में संभालने देती है, जिससे लेआउट समायोजन और दृश्य सुसंगतता सरल हो जाती है।

**अगले कदम**

- विभिन्न भराव पैटर्न या बॉर्डर वाले **how to insert rectangle** आकृतियों का अन्वेषण करें।
- **insert rectangle shape** को टेक्स्ट बॉक्स के साथ मिलाकर लेबल वाले आरेख बनाएं।
- समूह को घुमाने या स्केल करने के साथ प्रयोग करें ताकि अधिक जटिल ग्राफिक्स बन सकें।

कोड को अन्य आकृति प्रकारों, बड़े समूहों, या डायनेमिक दस्तावेज़ जनरेशन परिदृश्यों के लिए अनुकूलित करने में संकोच न करें। कोडिंग का आनंद लें!

## आपको आगे क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स निकट-संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API सुविधाओं में निपुण होने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Java में आयत आकृति डालें – समूह बनाएं और स्थितियों को सेट करें](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [Java में समूह आकृति कैसे डालें – पूर्ण गाइड](/words/english/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/)
- [Aspose.Words में आकृति पर शैडो कैसे सेट करें – पूर्ण गाइड](/words/english/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}