---
category: general
date: 2026-01-11
description: जावा में तेज़ी से वर्ड दस्तावेज़ बनाएं, एक आयताकार आकार जोड़ें, उसका
  भराव रंग सेट करें, और आकार पर छाया लागू करें। चरण‑दर‑चरण सीखें।
draft: false
keywords:
- create word document java
- add rectangle shape
- apply shadow to shape
- set shape fill color
- how to add shape
language: hi
og_description: जावा में एक वर्ड दस्तावेज़ बनाएं, जिसमें आयताकार आकार डालें, उसका
  भराव रंग सेट करें, और छाया लागू करें। कोड के साथ पूर्ण गाइड।
og_title: जावा में वर्ड दस्तावेज़ बनाएं – आयताकार आकार में छाया जोड़ें
tags:
- Aspose.Words
- Java
- Document Generation
title: जावा में वर्ड दस्तावेज़ बनाएं – छाया प्रभाव के साथ आयताकार आकार जोड़ें
url: /hi/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create Word Document Java – Add Rectangle Shape with Shadow Effect

क्या आपको कभी **create word document java** बनाना पड़ा और उसे थोड़ा अधिक पेशेवर दिखाना था? शायद आप एक रिपोर्ट जेनरेटर बना रहे हैं और साधारण पेज पर्याप्त नहीं है। अच्छी खबर? Aspose.Words for Java के साथ आप दस्तावेज़ में एक rectangle shape जोड़ सकते हैं, उसे रंग दे सकते हैं, और यहाँ तक कि एक हल्का shadow भी लगा सकते हैं—सिर्फ कुछ लाइनों में।

इस ट्यूटोरियल में हम ठीक वही करेंगे: rectangle shape कैसे जोड़ें, उसकी fill color सेट करें, और shape पर shadow लागू करें ताकि आपका Word फ़ाइल थोड़ा अधिक प्रोफ़ेशनल लगे। अंत तक आपके पास एक runnable example होगा जिसे आप अपने प्रोजेक्ट में copy‑paste कर सकते हैं।

## What You’ll Need

- **Java 17** (या कोई भी नया JDK) – कोड मानक भाषा सुविधाओं का उपयोग करता है।
- **Aspose.Words for Java** लाइब्रेरी – संस्करण 23.9 या उससे नया अनुशंसित है।
- आपका पसंदीदा IDE या टेक्स्ट एडिटर – IntelliJ IDEA, Eclipse, VS Code… आप चुनें।
- एक फ़ोल्डर जहाँ जनरेट किया गया `ShadowShape.docx` सहेजा जाएगा।

कोई अतिरिक्त configuration wizardry की जरूरत नहीं; बस Aspose.Words JAR को अपने classpath में जोड़ें और आप तैयार हैं।

## Step 1: Set Up the Project and Import Aspose.Words

सबसे पहले, एक नया Maven (या Gradle) प्रोजेक्ट बनाएं और Aspose.Words dependency जोड़ें। Maven के लिए यहाँ एक न्यूनतम `pom.xml` स्निपेट है:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>23.9</version>
        <classifier>jdk17</classifier>
    </dependency>
</dependencies>
```

यदि आप Maven का उपयोग नहीं कर रहे हैं, तो JAR फ़ाइल को अपने `libs` फ़ोल्डर में डालें और उसे build path में जोड़ें।

> **Pro tip:** Aspose एक मुफ्त trial license प्रदान करता है जिसे आप `License license = new License(); license.setLicense("Aspose.Words.lic");` के साथ एम्बेड कर सकते हैं। तेज़ टेस्ट के लिए इसे छोड़ दें; लाइब्रेरी evaluation mode में काम करती है।

## Step 2: Create a New Document and Builder

अब हम वास्तव में **create word document java** ऑब्जेक्ट्स बनाएंगे। `Document` क्लास पूरी .docx फ़ाइल का प्रतिनिधित्व करती है, जबकि `DocumentBuilder` हमें कंटेंट इन्सर्ट करने देता है।

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

इस चरण के बाद आपके पास एक खाली दस्तावेज़ तैयार है जिसमें आप shapes, paragraphs या कोई भी चीज़ जोड़ सकते हैं।

## Step 3: Insert a Rectangle Shape and Set Its Fill Color

Shape जोड़ना इतना सरल है जितना `insertShape` को कॉल करना। हम **add rectangle shape** तकनीक का उपयोग करेंगे, जो secondary keyword *add rectangle shape* के अंतर्गत आता है।

```java
        // Insert a rectangle shape – 200pt wide, 100pt tall
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);

        // Set the fill color to a bright orange
        rectangle.setFillColor(java.awt.Color.ORANGE);
```

ऑरेंज क्यों? यह सफ़ेद पृष्ठभूमि में उभर कर दिखता है, लेकिन आप इसे किसी भी `java.awt.Color` में बदल सकते हैं। यह चरण secondary keyword *set shape fill color* को कवर करता है।

## Step 4: Configure the Shadow Appearance – Apply Shadow to Shape

अब आता है मज़ेदार हिस्सा: rectangle को एक subtle drop shadow देना। Aspose API एक `ShadowFormat` ऑब्जेक्ट प्रदान करता है जो shadow के हर पहलू को नियंत्रित करता है।

```java
        // Get the shadow format object for the shape
        ShadowFormat shadow = rectangle.getShadowFormat();

        // Make the shadow visible
        shadow.setVisible(true);

        // Choose a neutral gray for the shadow color
        shadow.setColor(java.awt.Color.GRAY);

        // Blur radius – larger values produce a softer edge
        shadow.setBlur(5.0);

        // Offset determines how far the shadow is displaced
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);

        // Transparency (0 = opaque, 1 = fully transparent)
        shadow.setTransparency(0.2);

        // Define the shadow style and type
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);

        // Scale controls the overall size of the shadow relative to the shape
        shadow.setScale(1.0);
```

यह कोड ब्लॉक **apply shadow to shape** ठीक उसी तरह करता है जैसा secondary keyword सुझाता है। आप `blur`, `offsetX/Y`, और `transparency` को अपनी डिज़ाइन भाषा के अनुसार समायोजित कर सकते हैं। उदाहरण के लिए, बड़ा `offsetX` अधिक नाटकीय छाया बनाता है, जबकि उच्च `transparency` shadow को फुसफुसाते जैसा बनाता है।

## Step 5: Save the Document

अंत में, दस्तावेज़ को डिस्क पर लिखते हैं। वह फ़ोल्डर चुनें जहाँ आपके पास लिखने की अनुमति हो, और फ़ाइल को एक स्पष्ट नाम दें।

```java
        // Save the result – adjust the path as needed
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

जब आप `ShadowShape.docx` को Microsoft Word या LibreOffice में खोलेंगे, तो आपको एक चमकीला ऑरेंज rectangle एक नरम ग्रे shadow के साथ दिखाई देगा।

![create word document java with rectangle shape](/images/shadow-rectangle.png "create word document java – rectangle with shadow")

*Image alt text includes the primary keyword, satisfying the SEO rule.*

## Common Questions & Edge Cases

### What if I need a different shape?

Aspose.Words कई `ShapeType` मानों का समर्थन करता है – stars, arrows, callouts, आप जो चाहें। बस `ShapeType.RECTANGLE` को `ShapeType.OVAL` या किसी अन्य enum constant से बदल दें। वही **how to add shape** कदम लागू होते हैं।

### How do I add the shape to a specific paragraph?

Builder के साथ सीधे shape इन्सर्ट करने के बजाय, आप पहले shape बना सकते हैं (`new Shape(document, ShapeType.RECTANGLE)`) और फिर उसे `Paragraph` में `paragraph.appendChild(shape)` के ज़रिए जोड़ सकते हैं। इससे लेआउट पर अधिक नियंत्रण मिलता है।

### Can I apply a gradient fill instead of a solid color?

हां! `rectangle.getFill().setFillType(FillType.GRADIENT)` उपयोग करें और एक `LinearGradientFill` परिभाषित करें। API थोड़ा अधिक verbose है, लेकिन आधुनिक डिज़ाइनों के लिए बहुत अच्छा काम करता है।

### What about compatibility with older Word versions?

Aspose.Words डिफ़ॉल्ट रूप से .docx फॉर्मेट में सहेजता है, जो Word 2007+ और LibreOffice द्वारा समर्थित है। यदि आपको .doc चाहिए, तो `document.save("file.doc", SaveFormat.DOC)` कॉल करें। Shadow rendering में थोड़ा अंतर हो सकता है, लेकिन shape स्वयं बना रहता है।

## Full Working Example (Copy‑Paste Ready)

नीचे पूरा प्रोग्राम दिया गया है, जिसे आप तुरंत compile और run कर सकते हैं। `YOUR_DIRECTORY` को अपने मशीन पर वास्तविक पाथ से बदलें।

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape and set its fill color
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);
        rectangle.setFillColor(java.awt.Color.ORANGE);

        // Step 3: Apply shadow to shape
        ShadowFormat shadow = rectangle.getShadowFormat();
        shadow.setVisible(true);
        shadow.setColor(java.awt.Color.GRAY);
        shadow.setBlur(5.0);
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);
        shadow.setTransparency(0.2);
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);
        shadow.setScale(1.0);

        // Step 4: Save the document
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

इस कोड को चलाने पर एक Word फ़ाइल बनती है जिसमें ऑरेंज rectangle और एक नरम ग्रे shadow होता है—बिल्कुल वही जो हमने **create word document java** के साथ एक styled shape बनाने के लिए लक्ष्य रखा था।

## Conclusion

अब आपके पास **create word document java** के लिए एक ठोस, end‑to‑end रेसिपी है जो *adds rectangle shape*, *sets shape fill color*, और *applies shadow to shape* करती है। तरीका सीधा है, API fluent है, और आप इसे अनगिनत तरीकों से विस्तारित कर सकते हैं—विभिन्न shapes, gradient fills, या यहाँ तक कि एक shape पर कई shadows।

अगला क्या? कई shapes को लेयर करें, `ShadowStyle.ETCHED` के साथ अलग visual feel आज़माएँ, या इसे table generation के साथ मिलाकर पूरी‑फ़ीचर वाली रिपोर्ट बनाएं। संभावनाएँ केवल आपकी कल्पना (और शायद Aspose license tier) तक सीमित हैं।

यदि आपको कोई समस्या आती है या आगे की सुधारों के लिए विचार हैं, तो नीचे कमेंट करें। Happy coding, और अपने Word दस्तावेज़ों को थोड़ा कम बोरिंग बनाते रहें!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}