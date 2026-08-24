---
category: general
date: 2026-08-23
description: Aspose.Words for Java का उपयोग करके एक खाली Word दस्तावेज़ बनाएं, आकृतियों
  को समूहित करना, आयताकार आकृति को रंगना, और कुछ ही मिनटों में दस्तावेज़ को docx के
  रूप में सहेजना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- save document as docx
- how to group shapes
- color rectangle shape
language: hi
lastmod: 2026-08-23
og_description: Aspose.Words for Java का उपयोग करके एक खाली Word दस्तावेज़ बनाएं,
  फिर देखें कि कैसे आकारों को समूहित करें, आयताकार आकार को रंगें, और दस्तावेज़ को
  प्रभावी ढंग से docx के रूप में सहेजें।
og_image_alt: Screenshot of a blank Word document containing grouped colored rectangle
  shapes
og_title: जावा में खाली वर्ड दस्तावेज़ बनाएं और आकृतियों को समूहित करें – चरण‑दर‑चरण
  मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create blank Word document with Aspose.Words for Java, learn how to
    group shapes, color rectangle shape, and save document as docx in minutes.
  headline: Create blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: जावा में एक खाली वर्ड दस्तावेज़ बनाएं और आकारों को समूहित करें
url: /hi/java/images-shapes/create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# खाली Word दस्तावेज़ बनाएं और Java में शैप्स को समूहित करें

यदि आपको प्रोग्रामेटिक रूप से **खाली Word दस्तावेज़ बनाना** है, तो Aspose.Words for Java इसे सरल बनाता है। यह ट्यूटोरियल आपको बिल्कुल दिखाता है कि कैसे **खाली Word दस्तावेज़ बनाएं**, **Word में शैप्स को समूहित करें**, **रंगीन आयताकार शैप लागू करें**, और अंत में **दस्तावेज़ को docx के रूप में सहेजें**। अंत तक आपके पास एक पुन: उपयोग योग्य कोड स्निपेट होगा जिसे आप किसी भी Java प्रोजेक्ट में डाल सकते हैं।

आप सीखेंगे:

* Aspose.Words के लिए आवश्यक Maven/Gradle डिपेंडेंसी।
* एक खाली दस्तावेज़ और `DocumentBuilder` को इंस्टैंशिएट करने का तरीका।
* `GroupShape` के अंदर **शैप्स को समूहित करने** के सटीक चरण।
* आयताकार शैप्स पर फ़िल रंग सेट करने का तरीका।
* **दस्तावेज़ को docx के रूप में सहेजने** की सर्वोत्तम प्रैक्टिस और आउटपुट फ़ाइल कहाँ मिलेगी।

Aspose.Words का कोई पूर्व अनुभव आवश्यक नहीं है, लेकिन आपको बुनियादी Java विकास में सहज होना चाहिए और आपके पास JDK 8 या नया स्थापित होना चाहिए।

---

## आवश्यकताएँ

| आवश्यकता | संस्करण / विवरण |
|-------------|-------------------|
| Java Development Kit | 8 या उससे ऊपर |
| Build tool | Maven 3+ या Gradle 6+ |
| Aspose.Words for Java | 23.12 या बाद का (लेखन के समय उपलब्ध नवीनतम संस्करण) |
| IDE (वैकल्पिक) | IntelliJ IDEA, Eclipse, VS Code, या कोई भी Java‑compatible एडिटर |

---

## चरण 1: अपने प्रोजेक्ट में Aspose.Words जोड़ें

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Gradle

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Pro tip:** यदि आप कॉरपोरेट प्रॉक्सी का उपयोग कर रहे हैं, तो Maven/Gradle को Aspose रिपॉजिटरी से पैकेज खींचने के लिए कॉन्फ़िगर करें जैसा कि आधिकारिक दस्तावेज़ों में बताया गया है।

---

## चरण 2: **खाली Word दस्तावेज़ बनाएं** बिल्डर के साथ

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document doc = new Document();               // <-- create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` कंस्ट्रक्टर मेमोरी में एक खाली `.docx` कंटेनर बनाता है। `DocumentBuilder` आपको कंटेंट जोड़ने के लिए एक फ्लुएंट API देता है, जिसमें शैप्स भी शामिल हैं।

---

## चरण 3: एक **Word में शैप्स को समूहित करने** कंटेनर डालें

```java
        // Step 3.1: Insert a GroupShape that will hold individual shapes
        // Width = 300 points, Height = 200 points
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

`GroupShape` एक मिनी‑कैनवास की तरह काम करता है। इसमें जोड़े गए सभी शैप्स एक साथ चलते हैं, जो लेआउट स्थिरता के लिए **शैप्स को समूहित करने** का बिल्कुल सही तरीका है।

---

## चरण 4: पहला **रंगीन आयताकार शैप** (लाल) जोड़ें

```java
        // Step 4.1: Create the first rectangle and set its fill color to red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        // Append the rectangle to the group
        groupShape.appendChild(redRectangle);
```

`ShapeType.RECTANGLE` कॉन्स्टेंट एक साधारण आयत बनाता है। `getFill().setForeColor(...)` को कॉल करके आप **रंगीन आयताकार शैप** को नियंत्रित करते हैं। आप `java.awt.Color.RED` को किसी भी `java.awt.Color` कॉन्स्टेंट या कस्टम RGB वैल्यू से बदल सकते हैं।

---

## चरण 5: दूसरा **रंगीन आयताकार शैप** (हरा) जोड़ें और उसकी स्थिति निर्धारित करें

```java
        // Step 5.1: Create a second rectangle, color it green, and offset it inside the group
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // Horizontal offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);
```

`setLeft` (या `setTop`) सेट करने से शैप **Word में शैप्स को समूहित करने** कंटेनर के टॉप‑लेफ़्ट कोने के सापेक्ष स्थान बदलता है। यह **शैप्स को समूहित करने** के साथ सटीक पोजिशनिंग का प्रदर्शन करता है।

---

## चरण 6: **दस्तावेज़ को docx के रूप में सहेजें** और परिणाम सत्यापित करें

```java
        // Step 6.1: Persist the document to the file system
        String outputPath = "output/GroupShapeDemo.docx";
        doc.save(outputPath);          // <-- save document as docx
        System.out.println("Document saved to: " + outputPath);
    }
}
```

`save` मेथड स्वचालित रूप से एक `.docx` फ़ाइल लिखता है क्योंकि फ़ाइल एक्सटेंशन `.docx` है। यदि आपको कोई अलग फ़ॉर्मेट चाहिए (जैसे PDF), तो उपयुक्त `SaveFormat` एन्नुम पास करें।

> **Tip:** सुनिश्चित करें कि लक्ष्य डायरेक्टरी (`output/` इस उदाहरण में) मौजूद है या `new File("output").mkdirs();` के साथ प्रोग्रामेटिक रूप से बनाएं।

---

## त्वरित कॉपी‑पेस्ट के लिए पूर्ण स्रोत कोड

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document
        Document doc = new Document();               // create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape (the container for grouped shapes)
        GroupShape groupShape = builder.insertGroupShape(300, 200);

        // 3️⃣ First rectangle – red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        groupShape.appendChild(redRectangle);

        // 4️⃣ Second rectangle – green, positioned next to the red one
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);

        // 5️⃣ Save the file as DOCX
        String outPath = "output/GroupShapeDemo.docx";
        doc.save(outPath);          // save document as docx
        System.out.println("Document saved to: " + outPath);
    }
}
```

**अपेक्षित आउटपुट:** `GroupShapeDemo.docx` को Microsoft Word में खोलने पर एक ही पृष्ठ पर दो रंगीन आयतें (बाएँ लाल, दाएँ हरा) दिखेंगी जो समूह का चयन करने पर एक साथ मूव करती हैं।

---

## सामान्य प्रश्न और एज‑केस हैंडलिंग

| प्रश्न | उत्तर |
|----------|--------|
| *क्या मैं उसी समूह में दो से अधिक शैप्स जोड़ सकता हूँ?* | हाँ। प्रत्येक अतिरिक्त शैप के लिए `groupShape.appendChild(yourShape)` कॉल करें। समूह स्वचालित रूप से सबसे दूर तक फैले आकारों के अनुसार रिसाइज़ हो जाएगा, या आप मैन्युअली उसकी चौड़ाई/ऊँचाई समायोजित कर सकते हैं। |
| *यदि मुझे कोई अलग शैप टाइप चाहिए (जैसे ellipse)?* | `ShapeType.RECTANGLE` को `ShapeType.ELLIPSE` से बदलें। वही fill‑color लॉजिक लागू रहेगा। |
| *क्या मुझे `Document` ऑब्जेक्ट को डिस्पोज़ करना चाहिए?* | Aspose.Words आंतरिक रूप से नेटिव रिसोर्सेज़ को मैनेज करता है। JVM के समाप्त होने पर रिसोर्सेज़ रिलीज़ हो जाते हैं। लंबे समय तक चलने वाले एप्लिकेशन के लिए, यदि आप **Aspose.Words for Java (Native)** संस्करण उपयोग कर रहे हैं, तो `doc.dispose();` कॉल करें। |
| *मैं Z‑order कैसे बदलूँ ताकि एक आयत ऊपर दिखे?* | समूह के भीतर बच्चों को पुनः क्रमित करने के लिए `groupShape.insertAfter(shape, referenceShape);` या `groupShape.insertBefore(shape, referenceShape);` उपयोग करें। |
| *क्या मैं विभिन्न सेक्शनों में शैप्स को समूहित कर सकता हूँ?* | नहीं। `GroupShape` को एक ही पैराग्राफ या शैप कंटेनर के भीतर होना चाहिए। विभिन्न सेक्शनों में समूहित करने के लिए प्रत्येक सेक्शन में अलग-अलग समूह बनाएं। |

---

## निष्कर्ष

अब आप जानते हैं कि Aspose.Words for Java के साथ **खाली Word दस्तावेज़ कैसे बनाएं**, **Word में शैप्स को समूहित करें**, **रंगीन आयताकार शैप** की स्टाइलिंग लागू करें, और **दस्तावेज़ को docx के रूप में सहेजें**। यह पैटर्न अधिक जटिल लेआउट्स तक स्केल करता है—सिर्फ अतिरिक्त शैप्स जोड़ें, ऑफ़सेट समायोजित करें, और वैकल्पिक रूप से समूह के अंदर टेक्स्ट, इमेज या हाइपरलिंक सेट करें।

**अगले कदम** जिन्हें आप एक्सप्लोर कर सकते हैं:

* **Word में शैप्स को समूहित करें** का उपयोग करके फ्लोचार्ट या UI मॉक‑अप बनाएं।
* **दस्तावेज़ को docx के रूप में सहेजें** को PDF रूपांतरण (`doc.save("out.pdf")`) के साथ प्रयोग करें।
* अधिक समृद्ध विज़ुअल डिज़ाइन के लिए **रंगीन आयताकार शैप** पर ग्रेडिएंट या पैटर्न लागू करें।
* उन्नत रिपोर्टिंग दस्तावेज़ों के लिए समूहित शैप्स को टेबल या चार्ट के साथ संयोजित करें।

परियोजना की ब्रांडिंग के अनुसार आयाम, रंग या शैप टाइप को बदलने में संकोच न करें। Happy coding!

## आप अगला क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच को एक्सप्लोर कर सकें।

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}