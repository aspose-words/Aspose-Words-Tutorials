---
category: general
date: 2026-07-29
description: Aspose.Words का उपयोग करके जावा में वर्ड दस्तावेज़ बनाएं। वर्ड में आयताकार
  आकार डालना, आकारों को समूहित करना सीखें, और दस्तावेज़ को जल्दी से DOCX के रूप में
  सहेजें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
- add shapes to word
language: hi
lastmod: 2026-07-29
og_description: Aspose.Words के साथ जावा में वर्ड दस्तावेज़ बनाएं। आयताकार आकार डालें,
  वर्ड में आकारों को समूहित करें, और कुछ ही मिनटों में दस्तावेज़ को docx के रूप में
  सहेजें।
og_image_alt: Screenshot showing how to create word document with grouped shapes using
  Java
og_title: आकारों के साथ वर्ड दस्तावेज़ बनाएं – जावा Aspose.Words ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  headline: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  name: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  steps:
  - name: '## Create Word Document with Shapes Using Aspose.Words'
    text: The first thing you need is an empty Word file to work with. Aspose.Words
      makes this a one‑liner.
  - name: '## Insert Rectangle Shape and Other Shapes'
    text: Now we’ll add a blue rectangle and a green ellipse. The rectangle demonstrates
      the **insert rectangle shape** keyword, while the ellipse shows that you can
      mix shape types freely.
  - name: '## Group Shapes in Word for Easy Manipulation'
    text: Having two separate objects is fine, but often you want to move them together.
      That’s where **group shapes in word** shines.
  - name: '## Save Document as DOCX and Verify Output'
    text: Finally, we persist the file. This step fulfills the **save document as
      docx** requirement.
  - name: '## Full Working Example and Common Pitfalls'
    text: Below is the complete, ready‑to‑run Java class. Copy‑paste it into your
      project, adjust the output folder, and hit *Run*.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: जावा में आकृतियों के साथ वर्ड दस्तावेज़ बनाएं – पूर्ण Aspose.Words गाइड
url: /hi/java/images-shapes/create-word-document-with-shapes-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# जावा में आकृतियों के साथ Word दस्तावेज़ बनाएं – पूर्ण Aspose.Words गाइड

क्या आप कभी सोचते थे कि प्रोग्रामेटिक रूप से **create word document** कैसे बनाएं और उसमें कस्टम ग्राफिक्स जोड़ें? आप अकेले नहीं हैं। चाहे आपको हाइलाइटेड सेक्शन के साथ रिपोर्ट जेनरेट करनी हो या तुरंत एक फ़्लायर डिजाइन करना हो, Word में shape handling में महारत हासिल करने से आप घंटों का मैन्युअल काम बचा सकते हैं।

इस ट्यूटोरियल में हम **create word document** को Aspose.Words for Java का उपयोग करके, **insert rectangle shape**, **group shapes in Word**, और अंत में **save document as docx** करने के सटीक चरणों से गुजरेंगे। अंत तक आपके पास एक पूरी तरह चलने वाला उदाहरण होगा जिसे आप किसी भी प्रोजेक्ट में डाल सकते हैं।

## आप क्या सीखेंगे

- पूरी तरह से Java कोड से जेनरेट किया गया नया Word फ़ाइल।  
- पृष्ठ पर दो अलग-अलग आकृतियाँ (एक rectangle और एक ellipse) जोड़ी गईं।  
- उन आकृतियों को **group shapes in word** API के साथ समूहित किया गया, जिससे वे एक ही ऑब्जेक्ट की तरह व्यवहार करती हैं।  
- फ़ाइल को डिस्क पर एक मानक `.docx` के रूप में सहेजा गया, जो Microsoft Word में बिना किसी समस्या के खुलता है।  

कोई बाहरी टूल नहीं, कोई जटिल XML हैक्स नहीं—सिर्फ साफ़, टाइप्ड Java और Aspose.Words।

---

## पूर्वापेक्षाएँ

पहले सुनिश्चित करें कि आपके पास है:

1. **Java Development Kit (JDK) 8 या नया** – कोड Java 8+ को टार्गेट करता है।  
2. **Aspose.Words for Java** JAR (आप Maven Central रिपॉजिटरी से नवीनतम संस्करण प्राप्त कर सकते हैं)।  
3. एक साधारण IDE (IntelliJ IDEA, Eclipse, या यहाँ तक कि एक साधारण टेक्स्ट एडिटर)।  

यदि आपके पास ये सब है, तो चलिए शुरू करते हैं।

---

## चरण‑दर‑चरण कार्यान्वयन

नीचे हम प्रक्रिया को छोटे‑छोटे चरणों में विभाजित करेंगे। प्रत्येक चरण में एक कोड स्निपेट, संक्षिप्त व्याख्या, और एक टिप होगी जो आधिकारिक दस्तावेज़ों में नहीं मिल सकती।

### ## Aspose.Words का उपयोग करके आकृतियों के साथ Word दस्तावेज़ बनाएं

सबसे पहले आपको एक खाली Word फ़ाइल चाहिए जिस पर आप काम कर सकें। Aspose.Words इसे एक‑लाइनर बना देता है।

```java
// Step 1: Initialise a blank document and a DocumentBuilder
Document doc = new Document();                 // Represents the Word file
DocumentBuilder builder = new DocumentBuilder(doc);
```

**यह क्यों महत्वपूर्ण है:**  
`Document` सब कुछ—टेक्स्ट, टेबल, इमेज, और shapes—के लिए कंटेनर है। `DocumentBuilder` वह दोस्ताना हेल्पर है जो आपको लो‑लेवल ऑब्जेक्ट्स से झुंझलाते बिना कंटेंट जोड़ने देता है। इसे एक पेन की तरह समझें जो सीधे पेज पर लिखता है।

> **प्रो टिप:** यदि आप टेम्पलेट (जैसे कंपनी लेटरहेड) से शुरू करना चाहते हैं, तो `new Document()` को `new Document("template.docx")` से बदलें।

### ## Rectangle Shape और अन्य Shapes डालें

अब हम एक नीला rectangle और एक हरा ellipse जोड़ेंगे। rectangle **insert rectangle shape** कीवर्ड को दर्शाता है, जबकि ellipse दिखाता है कि आप shape प्रकारों को स्वतंत्र रूप से मिला सकते हैं।

```java
// Step 2: Insert a rectangle shape (100x50 points) and set its appearance
Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
rect.setLeft(50);                               // X‑coordinate in points
rect.setTop(50);                                // Y‑coordinate in points
rect.getFill().setColor(java.awt.Color.BLUE);  // Fill color

// Step 3: Insert an ellipse shape (80x80 points) and configure it
Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
ellipse.setLeft(180);
ellipse.setTop(30);
ellipse.getFill().setColor(java.awt.Color.GREEN);
```

**आंतरिक रूप से क्या हो रहा है?**  
हर `insertShape` कॉल एक `Shape` ऑब्जेक्ट बनाता है और स्वचालित रूप से उसे वर्तमान पैराग्राफ में जोड़ देता है। `setLeft`/`setTop` मेथड्स shape को पेज मार्जिन के सापेक्ष पोजिशन करते हैं, पॉइंट्स में मापे जाते हैं (1 pt = 1/72 in)। इन संख्याओं को बदलकर आप shapes को कहीं भी रख सकते हैं।

> **सामान्य प्रश्न:** *क्या मैं ठोस रंग की बजाय कोई चित्र जोड़ सकता हूँ?*  
> बिल्कुल—बस fill color को `shape.getFill().setImage("path/to/image.png")` के साथ इमेज से बदल दें।

### ## आसान हेरफेर के लिए Word में Shapes को Group करें

दो अलग‑अलग ऑब्जेक्ट्स होना ठीक है, लेकिन अक्सर आप उन्हें साथ‑साथ मूव करना चाहते हैं। यही वह जगह है जहाँ **group shapes in word** काम आता है।

```java
// Step 4: Create a GroupShape container and add the two shapes
GroupShape group = builder.insertGroupShape(); // Starts an empty group
group.appendChild(rect);
group.appendChild(ellipse);

// Step 5: Reposition the whole group as a single entity
group.setLeft(100);
group.setTop(150);
```

**Group क्यों?**  
जब shapes को समूहित किया जाता है, तो कोई भी ट्रांसफ़ॉर्मेशन—मूव, रोटेट, रिसाइज़—पूरे कलेक्शन पर लागू होता है। यह वही व्यवहार है जो आप Word UI में कई shapes को मैन्युअली सिलेक्ट करके *Group* बटन दबाने पर देखते हैं। यह बाद के कोड को भी सरल बनाता है क्योंकि आपको कई ऑब्जेक्ट्स की बजाय केवल एक को एडजस्ट करना पड़ता है।

> **एज केस:** यदि बाद में आपको अन‑ग्रुप करना पड़े, तो `group.getParentNode().removeChild(group)` कॉल करें और बच्चों को व्यक्तिगत रूप से फिर से इन्सर्ट करें।

### ## DOCX के रूप में Document सहेजें और आउटपुट सत्यापित करें

अंत में, हम फ़ाइल को स्थायी रूप से सहेजते हैं। यह चरण **save document as docx** की आवश्यकता को पूरा करता है।

```java
// Step 6: Write the document to disk as a .docx file
String outputPath = "output/GroupShapeExample.docx";
doc.save(outputPath, SaveFormat.DOCX);
System.out.println("Document saved successfully to " + outputPath);
```

**क्या अपेक्षित है:**  
जनरेट किए गए `GroupShapeExample.docx` को Microsoft Word में खोलें। आपको एक नीला rectangle और एक हरा ellipse दिखाई देगा, जो साफ़‑सुथरे तरीके से समूहित हैं। समूह को ड्रैग करें—दोनों shapes एक साथ मूव करेंगे, ठीक उसी तरह जैसा UI में अपेक्षित है।

> **टिप:** यदि आपको PDF संस्करण चाहिए, तो `SaveFormat.PDF` का उपयोग करें; वही कोड बिना बदलाव के काम करेगा।

### ## पूर्ण कार्यशील उदाहरण और सामान्य समस्याएँ

नीचे पूरी, तैयार‑चलाने‑योग्य Java क्लास दी गई है। इसे अपने प्रोजेक्ट में कॉपी‑पेस्ट करें, आउटपुट फ़ोल्डर समायोजित करें, और *Run* दबाएँ।

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle shape and set its position and fill color
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rect.setLeft(50);
        rect.setTop(50);
        rect.getFill().setColor(java.awt.Color.BLUE);

        // Step 3: Insert a second ellipse shape and configure its position and fill color
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
        ellipse.setLeft(180);
        ellipse.setTop(30);
        ellipse.getFill().setColor(java.awt.Color.GREEN);

        // Step 4: Group the two shapes together using the new GroupShape API
        GroupShape group = builder.insertGroupShape();
        group.appendChild(rect);
        group.appendChild(ellipse);

        // Step 5: Optionally reposition the entire group as a single object
        group.setLeft(100);
        group.setTop(150);

        // Step 6: Save the document containing the grouped shapes
        String outPath = "output/GroupShapeExample.docx";
        doc.save(outPath, SaveFormat.DOCX);
        System.out.println("Document saved successfully to " + outPath);
    }
}
```

#### सामान्य समस्याएँ और उन्हें कैसे टालें

| समस्या | क्यों होता है | समाधान |
|-------|----------------|-----|
| **`NullPointerException` on `builder`** | Document बनाते बाद `DocumentBuilder` को instantiate करना भूल जाना। | `new DocumentBuilder(doc)` को किसी भी shape insertion से पहले चलाएँ। |
| **Shapes appear off‑page** | पिक्सेल मानों का उपयोग करना बजाय points के, या margins को ध्यान में न रखना। | ध्यान रखें कि Aspose.Words points की अपेक्षा करता है; 72 pt = 1 in. `setLeft`/`setTop` को उसी अनुसार समायोजित करें। |
| **Group disappears after save** | Shapes को group बनाने के बाद ही फ़ाइल सहेजी गई। | फ़ाइल सहेजने से पहले हमेशा group बनाएं। |
| **File not found on save** | आउटपुट डायरेक्टरी मौजूद नहीं है। | `new File("output").mkdirs();` जैसे प्रोग्रामेटिक रूप से डायरेक्टरी बनाएं या मौजूदा पथ उपयोग करें। |

---

## निष्कर्ष

हमने अभी **create word document** को शून्य से बनाया, **add shapes to word**, **insert rectangle shape**, **group shapes in word**, और अंत में **save document as docx** किया—सिर्फ कुछ ही Java लाइनों में। Aspose.Words की शक्ति उसके स्पष्ट ऑब्जेक्ट मॉडल में है; आप Word फ़ाइल को एक कैनवास की तरह मान सकते हैं, उस पर shapes के साथ पेंट कर सकते हैं, और फिर इसे जहाँ भी चाहिए, एक्सपोर्ट कर सकते हैं।

क्या आप थोड़ा साहसी महसूस कर रहे हैं? rectangle को स्टार से बदलें, `Shape.getTextBox()` से shapes के अंदर टेक्स्ट जोड़ें, या रोटेशन (`shape.setRotationAngle(45)`) के साथ प्रयोग करें। API समृद्ध है, और संभावनाएँ लगभग अनंत हैं।

अधिक उन्नत परिदृश्यों—जैसे shapes को बुकमार्क्स से लिंक करना या एम्बेडेड फ़ॉन्ट्स के साथ PDF एक्सपोर्ट करना—के बारे में प्रश्न हैं? नीचे टिप्पणी छोड़ें, और हम साथ‑साथ गहराई में उतरेंगे। Happy coding!

## अब आप क्या सीखें

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोचेज़ को एक्सप्लोर करने में मदद करेंगे।

- [Word दस्तावेज़ Java बनाएं – शैडो इफ़ेक्ट के साथ Rectangle Shape जोड़ें](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में Group Shape बनाएं](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words के साथ Word में rectangle shape बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}