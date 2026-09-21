---
category: general
date: 2026-09-21
description: जावा का उपयोग करके प्रोग्रामेटिक रूप से वर्ड दस्तावेज़ बनाएं। वर्ड में
  आकृतियों को समूहित करना, आयताकार आकृति सम्मिलित करना, आकृति का आकार सेट करना, और
  वर्ड दस्तावेज़ में आकृतियों को जोड़ना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to group shapes in word
- how to insert rectangle shape
- add shapes to word document
- set shape size word
language: hi
lastmod: 2026-09-21
og_description: 'जावा के साथ प्रोग्रामेटिक रूप से वर्ड दस्तावेज़ बनाएं: यह गाइड दिखाता
  है कि वर्ड में आकारों को कैसे समूहित करें, आयताकार आकार सम्मिलित करें, आकार का आकार
  सेट करें, और वर्ड दस्तावेज़ में आकार जोड़ें।'
og_image_alt: Screenshot of a Java program creating a Word document with grouped shapes
og_title: प्रोग्रामेटिक रूप से वर्ड दस्तावेज़ बनाएं, जावा में शैप्स को समूहित करें
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically using Java. Learn how to group
    shapes in Word, insert a rectangle shape, set shape size, and add shapes to a
    Word document.
  headline: Create word document programmatically, group shapes in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word automation
- Shapes
title: प्रोग्रामेटिक रूप से वर्ड दस्तावेज़ बनाएं, जावा में शैप्स को समूहित करें
url: /hi/java/images-shapes/create-word-document-programmatically-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# प्रोग्रामेटिकली वर्ड डॉक्यूमेंट बनाएं, जावा में शैप्स को ग्रुप करें

यदि आपको **प्रोग्रामेटिकली वर्ड डॉक्यूमेंट बनाना** है, तो यह गाइड आपको एक पूर्ण समाधान के माध्यम से ले जाएगी। आप देखेंगे कि **वर्ड में शैप्स को ग्रुप कैसे करें**, एक रेक्टैंगल कैसे डालें, उसका आकार सेट करें, और अन्य शैप्स जोड़ें—सभी जावा और Aspose.Words for Java लाइब्रेरी का उपयोग करके।

यह ट्यूटोरियल प्रोजेक्ट सेटअप से लेकर अंतिम .docx फ़ाइल को सेव करने तक के हर चरण को कवर करता है। अंत तक आप एक ऐसा वर्ड डॉक्यूमेंट जेनरेट करने में सक्षम होंगे जिसमें एक रेक्टैंगल और एक इमेज एक ही ग्रुप में रैप्ड हों, जिससे उन्हें साथ में मूव या रिसाइज़ करना आसान हो जाता है। Aspose.Words API का कोई पूर्व अनुभव आवश्यक नहीं है, लेकिन आपके पास बेसिक जावा डेवलपमेंट एनवायरनमेंट होना चाहिए।

## प्रीरेक्विज़िट्स

* Java Development Kit (JDK) 8 या नया  
* Maven या Gradle डिपेंडेंसी मैनेजमेंट के लिए  
* Aspose.Words for Java 23.9 (या नवीनतम संस्करण) – लाइब्रेरी एवाल्यूएशन के लिए फ्री है  
* एक इमेज फ़ाइल (जैसे `sample.jpg`) जिसे आप किसी ज्ञात डायरेक्टरी में रखें  

इन आइटम्स को तैयार रखने से कोड अतिरिक्त कॉन्फ़िगरेशन के बिना चल पाएगा।

## स्टेप 1: प्रोजेक्ट सेट अप करें और Aspose.Words इम्पोर्ट करें

एक Maven प्रोजेक्ट बनाएं (या अपने मौजूदा `pom.xml` में डिपेंडेंसी जोड़ें):

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

यदि आप Gradle पसंद करते हैं, तो `build.gradle` में निम्नलिखित जोड़ें:

```gradle
implementation 'com.aspose:aspose-words:23.9'
```

डिपेंडेंसी रिजॉल्व हो जाने के बाद, अपने जावा सोर्स फ़ाइल में आवश्यक क्लासेज इम्पोर्ट करें:

```java
import com.aspose.words.*;
import java.io.File;
```

## स्टेप 2: प्रोग्रामेटिकली वर्ड डॉक्यूमेंट बनाएं

किसी भी ऑटोमेशन परिदृश्य में पहला ऑपरेशन `Document` ऑब्जेक्ट और `DocumentBuilder` को इंस्टैंशिएट करना होता है। बिल्डर टेक्स्ट, इमेज और शैप्स को इन्सर्ट करना आसान बनाता है।

```java
public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

इस बिंदु पर डॉक्यूमेंट केवल मेमोरी में मौजूद है। अब आप शैप्स जोड़ना शुरू कर सकते हैं।

## स्टेप 3: रेक्टैंगल शैप इन्सर्ट करें – रेक्टैंगल शैप कैसे इन्सर्ट करें

एक रेक्टैंगल बेसिक `Shape` है जिसका `ShapeType.RECTANGLE` होता है। आप इसके डाइमेंशन `setWidth`, `setHeight` से नियंत्रित करते हैं और `setTop` तथा `setLeft` से पोजिशन सेट करते हैं।

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);
        rectangle.setTop(10.0);
        rectangle.setLeft(10.0);

        // Optional: give the rectangle a visible fill and line color
        rectangle.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
        rectangle.getStrokeColor().setColor(java.awt.Color.DARK_GRAY);
```

**यह क्यों महत्वपूर्ण है:** आकार और पोजिशन को स्पष्ट रूप से सेट करना (`set shape size word`) यह सुनिश्चित करता है कि रेक्टैंगल ठीक उसी जगह पर दिखे जहाँ आप चाहते हैं, चाहे डॉक्यूमेंट का डिफ़ॉल्ट लेआउट कुछ भी हो।

## स्टेप 4: इमेज इन्सर्ट करें – वर्ड डॉक्यूमेंट में शैप्स जोड़ें

`DocumentBuilder` फ़ाइल पाथ से सीधे इमेज इन्सर्ट कर सकता है। इन्सर्ट करने के बाद, आप पिक्चर को किसी भी अन्य शैप की तरह रीपोजिशन कर सकते हैं।

```java
        // Insert an image; replace the path with your own image location
        String imagePath = "YOUR_DIRECTORY/sample.jpg";
        if (!new File(imagePath).exists()) {
            throw new IllegalArgumentException("Image file not found: " + imagePath);
        }
        Shape picture = builder.insertImage(imagePath);
        picture.setTop(70.0);
        picture.setLeft(10.0);
```

अब रेक्टैंगल और पिक्चर दोनों डॉक्यूमेंट के अंदर स्वतंत्र शैप्स हैं।

## स्टेप 5: शैप्स को ग्रुप करें – वर्ड में शैप्स को ग्रुप कैसे करें

शैप्स को ग्रुप करना उपयोगी होता है जब आप उन्हें एक ही यूनिट के रूप में मूव या रिसाइज़ करना चाहते हैं। Aspose.Words इस उद्देश्य के लिए `GroupShape` कंटेनर प्रदान करता है।

```java
        // Create a GroupShape that will contain the rectangle and the picture
        GroupShape group = builder.insertGroupShape();

        // Append the rectangle and picture to the group
        group.appendChild(rectangle);
        group.appendChild(picture);
```

जब ग्रुप सेव किया जाता है, तो Word दो बच्चों को एक लॉजिकल ऑब्जेक्ट के रूप में ट्रीट करता है। बाद में आप ग्रुप को सिलेक्ट करके ड्रैग कर सकते हैं, और रेक्टैंगल व इमेज दोनों साथ में मूव होंगे।

## स्टेप 6: डॉक्यूमेंट को सेव करें

अंत में, डॉक्यूमेंट को डिस्क पर लिखें। पाथ जावा प्रोसेस द्वारा राइटेबल होना चाहिए।

```java
        // Save the document with the grouped shapes
        String outputPath = "YOUR_DIRECTORY/GroupShapeExample.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

`main` मेथड चलाने पर **GroupShapeExample.docx** नाम की फ़ाइल बनती है। इसे Microsoft Word में खोलें; आपको एक रेक्टैंगल और एक इमेज ग्रुप के अंदर लॉक हुए दिखेंगे। ग्रुप को सिलेक्ट करने से दोनों ऑब्जेक्ट एक साथ मूव होते हैं, जिससे ग्रुपिंग सफल होने की पुष्टि होती है।

## अपेक्षित आउटपुट

* एक वर्ड फ़ाइल (`GroupShapeExample.docx`) जो आपने निर्दिष्ट डायरेक्टरी में स्थित होगी।  
* फ़ाइल के अंदर, एक रेक्टैंगल (हल्के‑ग्रे फ़िल) टॉप‑लेफ़्ट कॉर्नर पर दिखाई देगा, और इमेज सीधे उसके नीचे स्थित होगी।  
* दोनों ऑब्जेक्ट एक ही ग्रुप का हिस्सा हैं, इसलिए एक को ड्रैग करने से दूसरा भी मूव हो जाएगा।

## सामान्य वैरिएशन्स और एज केस

| स्थिति | सिफ़ारिश |
|-----------|----------------|
| **विभिन्न इमेज फ़ॉर्मेट** | Aspose.Words PNG, BMP, GIF, और TIFF को सपोर्ट करता है। `insertImage` में उपयुक्त फ़ाइल एक्सटेंशन उपयोग करें। |
| **निगेटिव डाइमेंशन** | API `ArgumentException` थ्रो करता है। `setWidth` / `setHeight` कॉल करने से पहले हमेशा चौड़ाई और ऊँचाई को वैलिडेट करें। |
| **बड़ी डॉक्यूमेंट्स** | कई शैप्स को ग्रुप करने से फ़ाइल साइज बढ़ सकती है। जब परफ़ॉर्मेंस महत्वपूर्ण हो, तो शैप्स को एक ही पिक्चर में मर्ज करने पर विचार करें। |
| **वर्ड वर्ज़न कम्पैटिबिलिटी** | GroupShape Word 2007 (`.docx`) और उसके बाद के वर्ज़न में काम करता है। पुराने `.doc` फ़ाइलों के लिए, ग्रुप फ्लैटेन हो जाएगा। |
| **डायनामिक पोजिशनिंग** | यदि आपको एडैप्टिव प्लेसमेंट चाहिए, तो पेज साइज (`doc.getFirstSection().getPageSetup().getPageWidth()`) के आधार पर कैलकुलेशन उपयोग करें। |

**Pro tip:** ग्रुप बनाने के बाद, आप इसे बदल सकते हैं

## आगे क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक रिसोर्स में पूर्ण कार्यशील कोड उदाहरण और स्टेप‑बाय‑स्टेप एक्सप्लानेशन शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ का अन्वेषण कर सकें।

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}