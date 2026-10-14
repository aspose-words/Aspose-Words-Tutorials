---
category: general
date: 2026-10-13
description: जावा के साथ वर्ड में समूहित आकृतियाँ बनाना सीखें। यह गाइड आपको दिखाता
  है कि समूह आकृति कैसे डालें, समूह में रेखा कैसे जोड़ें, और वर्ड‑व्यापी कई आकृतियों
  को कैसे समूहित करें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create grouped shapes
- add line to group
- group multiple shapes word
- insert group shape
language: hi
lastmod: 2026-10-13
og_description: जावा के साथ वर्ड में समूहित आकार बनाएं। समूह आकार डालने, समूह में
  रेखा जोड़ने और वर्ड दस्तावेज़ों में कई आकारों को समूहित करने के लिए इस पूर्ण ट्यूटोरियल
  का पालन करें।
og_image_alt: Screenshot of a Word document showing created grouped shapes
og_title: जावा के साथ वर्ड में समूहित आकार बनाएं – चरण‑दर‑चरण मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to create grouped shapes in Word with Java. This guide shows
    you how to insert group shape, add line to group, and group multiple shapes word‑wide.
  headline: How to create grouped shapes in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: जावा का उपयोग करके वर्ड दस्तावेज़ में समूहित आकार कैसे बनाएं
url: /hi/java/images-shapes/how-to-create-grouped-shapes-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java का उपयोग करके Word दस्तावेज़ में समूहित आकार कैसे बनाएं

यदि आपको Java से Microsoft Word फ़ाइल में **grouped shapes** बनाना है, तो यह ट्यूटोरियल पूरी प्रक्रिया को चरण‑बद्ध दिखाता है। आप देखेंगे कि **insert group shape** कैसे डालें, उसी कंटेनर में एक आयत और एक रेखा रखें, और अंत में समूहित ग्राफ़िक्स के साथ दस्तावेज़ को सहेजें।

Shapes को समूहित करने से कई ड्राइंग ऑब्जेक्ट्स को एक इकाई के रूप में आसानी से ले जाया, आकार बदला या स्टाइल किया जा सकता है—डायग्राम, फ्लोचार्ट या कस्टम पेज डेकोरेशन के लिए आदर्श। इस गाइड के अंत तक आप **add line to group**, **group multiple shapes word** दस्तावेज़ बना पाएँगे, और इस तकनीक को किसी भी संख्या में shapes के लिए दोहरा सकेंगे।

## Prerequisites

- आपके विकास मशीन पर Java 17 या उससे नया स्थापित हो।  
- Aspose.Words for Java लाइसेंस (या एक मुफ्त इवैल्यूएशन)।  
- एक Maven या Gradle प्रोजेक्ट जहाँ आप Aspose.Words डिपेंडेंसी जोड़ सकें:

```xml
<!-- Maven example -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

कोई अतिरिक्त लाइब्रेरी आवश्यक नहीं है।

## Step 1: Insert the group shape container

पहला कदम दस्तावेज़ में **insert group shape** डालना है। यह कंटेनर सभी बाद के shapes को रखेगा।

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // The rest of the code will add shapes to this group
```

`builder.insertGroupShape()` एक खाली `Shape` ऑब्जेक्ट बनाता है जिसका प्रकार `GROUPSHAPE` है। इसे आप एक पारदर्शी कैनवास समझ सकते हैं जो अन्य ड्राइंग ऑब्जेक्ट्स को समाहित कर सकता है।

## Step 2: Add a rectangle to the group

आयत अक्सर समूह के लिए दृश्य पृष्ठभूमि के रूप में काम करती है।

```java
        // Create a rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        rectangleShape.setLeft(0);      // X‑coordinate inside the group
        rectangleShape.setTop(0);       // Y‑coordinate inside the group

        // Append the rectangle to the group container
        groupShape.appendChild(rectangleShape);
```

`Left` और `Top` को `0` सेट करने से आयत समूह के ऊपर‑बाएँ कोने में स्थित हो जाती है। आप इन मानों को बदलकर shape को समूह के भीतर ऑफ़सेट कर सकते हैं।

## Step 3: **Add line to group** – create a line shape

अब हम **add line to group** करेंगे। रेखा आयत के नीचे दिखाई देगी।

```java
        // Create a line shape
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);   // length of the line
        lineShape.setTop(60);      // vertical position (60 points down)

        // Append the line to the same group
        groupShape.appendChild(lineShape);
```

`Top` प्रॉपर्टी रेखा को आयत से 60 पॉइंट नीचे ले जाती है, जिससे एक साधा स्टैक्ड लेआउट बनता है। यदि आपको क्षैतिज ऑफ़सेट चाहिए तो `Left` भी सेट कर सकते हैं।

## Step 4: Save the document with the grouped shapes

```java
        // Save the document to a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

जब आप `GroupShapeDemo.docx` को Microsoft Word में खोलेंगे, तो आपको एक ही समूह दिखाई देगा जिसमें आयत और रेखा दोनों शामिल हैं। समूह का चयन करने से दोनों shapes एक साथ मूव होते हैं, जिससे यह साबित होता है कि आपने सफलतापूर्वक **group multiple shapes word** किया है।

## Full, runnable example

नीचे पूरा प्रोग्राम सभी इम्पोर्ट्स और एरर हैंडलिंग के साथ दिया गया है। इसे अपने IDE में कॉपी करें, `YOUR_DIRECTORY` को वास्तविक फ़ोल्डर पाथ से बदलें, और चलाएँ।

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // Step 3: Add a rectangle to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);
        rectangleShape.setHeight(50);
        rectangleShape.setLeft(0);
        rectangleShape.setTop(0);
        groupShape.appendChild(rectangleShape);

        // Step 4: Add a line to the group
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);
        lineShape.setTop(60);
        groupShape.appendChild(lineShape);

        // Step 5: Save the document
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

### Expected output

- लक्ष्य फ़ोल्डर में `GroupShapeDemo.docx` नाम की फ़ाइल बनती है।  
- Word में फ़ाइल खोलने पर एक ही समूहित ऑब्जेक्ट दिखता है जिसमें ऊपर आयत और नीचे रेखा होती है।  
- समूह को ड्रैग करने से दोनों shapes साथ‑साथ मूव होते हैं, जिससे पुष्टि होती है कि आपने **created grouped shapes** सफलतापूर्वक बना लिए हैं।

## Tips and common pitfalls

- **Pro tip:** यदि आपको समूह के भीतर व्यक्तिगत shapes को घुमाना या स्टाइल करना है, तो उन्हें समूह में जोड़ने से पहले संबंधित सेटर्स (`setRotation`, `getFill().setForeColor` आदि) कॉल करें। समूह इन विज़ुअल प्रॉपर्टीज़ को संरक्षित रखेगा।  
- **Watch out for:** रेखा के लिए `Top` प्रॉपर्टी सेट करना न भूलें, अन्यथा वह आयत के ऊपर ओवरलैप हो सकती है और समूह अव्यवस्थित दिखेगा।  
- **Edge case:** जब आप दो से अधिक shapes जोड़ते हैं, तो याद रखें कि प्रत्येक चाइल्ड के कोऑर्डिनेट्स समूह के मूल (0,0) के सापेक्ष होते हैं। लेआउट उसी अनुसार प्लान करें।  
- **Performance note:** बड़ी संख्या में shapes (सैकड़ों) को समूहित करने से फ़ाइल साइज थोड़ा बढ़ सकता है, लेकिन बाद में Word में एडिटिंग आसान हो जाती है।

## How to **group multiple shapes word** documents programmatically

ऊपर दिखाया गया पैटर्न—एक समूह कंटेनर बनाएं, प्रत्येक चाइल्ड shape को कॉन्फ़िगर करें, और जोड़ें—किसी भी संख्या में shapes के लिए काम करता है: सर्कल, चित्र, टेक्स्ट बॉक्स आदि। बस “create shape → set properties → append” चरणों को दोहराएँ और फिर `doc.save()` कॉल करें।

यदि आपको **add line to group** को पहले से मौजूद समूह में जोड़ना है, तो आप मौजूदा समूह को इस तरह प्राप्त कर सकते हैं:

```java
Shape existingGroup = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                                 .stream()
                                 .filter(s -> ((Shape) s).getShapeType() == ShapeType.GROUPSHAPE)
                                 .findFirst()
                                 .orElseThrow(() -> new IllegalStateException("No group found"));
existingGroup.appendChild(lineShape);
```

यह दर्शाता है कि आप दस्तावेज़ के जीवन‑चक्र में किसी भी बिंदु पर समूह को संशोधित कर सकते हैं।

## Conclusion

अब आप Java और Aspose.Words का उपयोग करके Word दस्तावेज़ में **create grouped shapes** करना जानते हैं। **inserting group shape**, **adding line to group**, और **group multiple shapes word** करके आप जटिल ड्रॉइंग बना सकते हैं जो एक ही ऑब्जेक्ट की तरह व्यवहार करती हैं—डायग्राम, टेम्प्लेट और स्वचालित रिपोर्ट जेनरेशन के लिए आदर्श।

अगले चरण में, इन संबंधित विषयों को देखें:

- **Applying styles to grouped shapes** – सभी चाइल्ड पर एक साथ फ़िल रंग, बॉर्डर और इफ़ेक्ट सेट करना सीखें।  
- **Exporting grouped shapes to PDF** – देखें कि दस्तावेज़ को PDF में बदलने पर वही समूह कैसे बना रहता है।  
- **Animating shapes with VBA** – Java‑जनित समूहों को Word मैक्रो के साथ मिलाकर इंटरैक्टिव दस्तावेज़ बनाएं।

विभिन्न shape प्रकार, आकार और पोज़िशन के साथ प्रयोग करने में संकोच न करें। समूह बनाना आपको कई ऑब्जेक्ट्स को एक के रूप में ट्रीट करने की लचीलापन देता है, जिससे कोड और उपयोगकर्ता इंटरैक्शन दोनों सरल हो जाते हैं। Happy coding!

## What Should You Learn Next?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑बद्ध व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स को मास्टर कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ का अन्वेषण कर सकें।

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}