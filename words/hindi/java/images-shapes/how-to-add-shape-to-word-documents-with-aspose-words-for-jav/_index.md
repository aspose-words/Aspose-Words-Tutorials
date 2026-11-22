---
category: general
date: 2026-11-22
description: Aspose.Words for Java का उपयोग करके Word में आकार कैसे जोड़ें सीखें –
  एक आयत डालें और इसे प्रोग्रामेटिकली छिपाएँ।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shape to word
- how to insert shape
- how to hide shape
- hide shape in word
language: hi
lastmod: 2026-11-22
og_description: Aspose.Words for Java का उपयोग करके Word में आकृति जोड़ें। यह ट्यूटोरियल
  दिखाता है कि कैसे एक आयत सम्मिलित करें, आकृति को छिपाएँ, और दस्तावेज़ को सहेजें।
og_image_alt: Screenshot of Java code that adds and hides a shape in a Word document
og_title: Aspose.Words के साथ Word में आकार जोड़ें – Java गाइड
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  headline: How to add shape to Word documents with Aspose.Words for Java
  type: TechArticle
- description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  name: How to add shape to Word documents with Aspose.Words for Java
  steps:
  - name: Expected output
    text: '* The file `output.docx` opens without any visible shapes. * If you inspect
      the document with Aspose.Words (e.g., `doc.getChildNodes(NodeType.SHAPE, true).size()`),
      the shape count will be **1**, confirming that the shape exists but is hidden.'
  - name: 1. Creating a shape in a fresh document
    text: 'If you start from scratch, replace the load line with:'
  - name: 2. Positioning the shape precisely
    text: 'By default, `insertShape` places the shape at the current cursor location.
      To position it absolutely:'
  - name: 3. Controlling visibility per output format
    text: 'If you need the shape visible in the Word UI but hidden when exporting
      to PDF, use `Shape.setWrapType(WrapType.NONE)` together with `Hidden`:'
  - name: 4. Adding text inside the shape
    text: 'A rectangle can contain a text frame:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: Aspose.Words for Java के साथ Word दस्तावेज़ों में आकृति कैसे जोड़ें
url: /hi/java/images-shapes/how-to-add-shape-to-word-documents-with-aspose-words-for-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java के साथ Word दस्तावेज़ में shape कैसे जोड़ें

यदि आपको प्रोग्रामेटिकली **Word** दस्तावेज़ों में **shape जोड़ना** है, तो Aspose.Words for Java इसे सरल बनाता है। इस गाइड में आप सीखेंगे **shape कैसे डालें**, उसकी दृश्यता को नियंत्रित करें, और **shape को कैसे छिपाएँ** ताकि अंतिम फ़ाइल बिल्कुल वही दिखे जिसकी आप अपेक्षा करते हैं।

आप एक पूर्ण, चलाने योग्य उदाहरण के माध्यम से जाएंगे जो मौजूदा `.docx` को लोड करता है, एक आयत (rectangle) डालता है, उसे छिपाता है, और परिणाम को सहेजता है। कोई बाहरी स्क्रिप्ट या मैन्युअल कदम आवश्यक नहीं हैं, और ट्यूटोरियल सामान्य विविधताओं को कवर करता है जैसे शून्य से नया दस्तावेज़ बनाना या केवल प्रिंटिंग के समय shape को छिपाना।

## आवश्यकताएँ

* Java 17 (या बाद का) स्थापित हो – पुराने संस्करण भी काम करेंगे लेकिन नवीनतम LTS बेहतर प्रदर्शन देता है।  
* निर्भरता प्रबंधन के लिए Maven 3.8+।  
* एक वैध Aspose.Words for Java लाइसेंस (सीखने के लिए मुफ्त मूल्यांकन काम करता है)।  
* आपकी पसंद का IDE या टेक्स्ट एडिटर (जैसे IntelliJ IDEA, VS Code)।

## चरण 1: अपने Maven प्रोजेक्ट में Aspose.Words जोड़ें

Add the following dependency to your `pom.xml`. This pulls the latest stable version (as of November 2026).

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **Pro tip:** यदि आप अपना लाइसेंसिंग लॉजिक के साथ JAR वितरित करने की योजना बना रहे हैं तो `<scope>provided</scope>` क्लॉज़ का उपयोग करें।

## Word में shape जोड़ें – दस्तावेज़ को प्रारंभ करना

The first functional step is to obtain a `Document` object. You can either load an existing file or create a fresh one.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document (or create a new one)
        Document doc = new Document("input.docx");   // <-- replace with your path
        // If you prefer a blank document, use:
        // Document doc = new Document();
```

*Why this matters*: `Document` क्लास सभी Word संचालन के लिए प्रवेश बिंदु है। मौजूदा फ़ाइल लोड करने से शैलियाँ, हेडर और फुटर संरक्षित रहते हैं, जबकि नया दस्तावेज़ आपको एक साफ़ शुरुआत देता है।

## Word दस्तावेज़ में shape कैसे डालें

Next, create a `DocumentBuilder` to modify the document’s content. The builder gives you methods for inserting text, tables, and **shapes**.

```java
        // Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape with a width of 100 points and height of 50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
```

The `insertShape` call returns a `Shape` object that you can further configure (color, border, text, etc.). The dimensions are expressed in points (1 pt = 1/72 in).

*Why you might use a rectangle*: Rectangles are the most common container for annotations, watermarks, or placeholders. You can replace `ShapeType.RECTANGLE` with `ShapeType.ELLIPSE`, `ShapeType.LINE`, etc., to meet different visual needs.

## Word में shape को कैसे छिपाएँ

Sometimes you need a shape to exist for layout calculations but not appear in the final rendering. Aspose.Words provides the `setHidden(true)` method to achieve this.

```java
        // Hide the shape so it does not appear when the document is opened
        rectangle.setHidden(true);
```

The hidden flag works like the **Hidden** formatting option in Microsoft Word: the shape is omitted from the visual layout but still participates in the document’s object model. This is useful for:

* ऐसे मेटाडेटा या मार्कर संग्रहीत करना जिन्हें आपका एप्लिकेशन बाद में पढ़ता है।  
* ऐसे प्लेसहोल्डर बनाना जो प्रकाशन से ठीक पहले हटा दिए जाते हैं।  
* विभिन्न आउटपुट फ़ॉर्मेट के लिए दृश्यता नियंत्रित करना (जैसे, HTML में छिपाएँ लेकिन PDF में रखें)।

> **Note:** Hidden shapes are still exported to PDF by default. If you need them omitted from PDF as well, set `rectangle.getWrapType( ) = WrapType.NONE` and adjust the `Hidden` property accordingly.

## चरण 4: संशोधित दस्तावेज़ को सहेजें

Finally, persist the changes to a new file.

```java
        // Save the document with the hidden rectangle
        doc.save("output.docx");   // <-- replace with your desired output path
    }
}
```

When you open `output.docx` in Microsoft Word, the rectangle will not be visible, but it remains part of the document tree. You can verify its presence programmatically by re‑loading the file and checking `Shape.isHidden()`.

### अपेक्षित आउटपुट

* फ़ाइल `output.docx` बिना किसी दृश्यमान shape के खुलती है।  
* यदि आप Aspose.Words से दस्तावेज़ की जाँच करते हैं (जैसे, `doc.getChildNodes(NodeType.SHAPE, true).size()`), तो shape की संख्या **1** होगी, जो पुष्टि करती है कि shape मौजूद है लेकिन छिपा हुआ है।

## उन्नत विविधताएँ और किनारे के मामले

### 1. नई दस्तावेज़ में shape बनाना

If you start from scratch, replace the load line with:

```java
Document doc = new Document();          // creates an empty Word file
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Report Title");        // add a title before the shape
```

### 2. shape को सटीक रूप से स्थित करना

By default, `insertShape` places the shape at the current cursor location. To position it absolutely:

```java
rectangle.setLeft(72);   // 1 inch from the left margin
rectangle.setTop(144);   // 2 inches from the top of the page
rectangle.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangle.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
```

### 3. आउटपुट फ़ॉर्मेट के अनुसार दृश्यता नियंत्रित करना

If you need the shape visible in the Word UI but hidden when exporting to PDF, use `Shape.setWrapType(WrapType.NONE)` together with `Hidden`:

```java
rectangle.setHidden(false);                 // visible in Word
rectangle.getParagraph().getParagraphFormat()
        .setPageBreakBefore(true);          // ensure it stays on its own line
// When converting to PDF, hide it programmatically:
if (exportingToPdf) {
    rectangle.setHidden(true);
}
```

### 4. shape के अंदर टेक्स्ट जोड़ना

A rectangle can contain a text frame:

```java
Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 200, 50);
textBox.getTextBox().setInternalMarginLeft(5);
textBox.getTextBox().setInternalMarginTop(5);
builder.moveTo(textBox.getFirstParagraph());
builder.write("Confidential");
```

आप फिर उसी `setHidden(true)` कॉल से टेक्स्ट बॉक्स को छिपा सकते हैं।

## सामान्य समस्याएँ और उन्हें कैसे टालें

| लक्षण | कारण | समाधान |
|---------|-------|-----|
| `setHidden(true)` के बाद भी shape दिखाई देता है | दस्तावेज़ को hidden फ़्लैग सेट करने से पहले सहेजा गया था। | `setHidden(true)` को **`doc.save()` से पहले** कॉल करना सुनिश्चित करें। |
| shape का आकार विकृत दिखता है | उच्च DPI स्क्रीन पर points और pixels के बीच भ्रम। | सभी प्लेटफ़ॉर्म पर सुसंगत आकार के लिए points (72 pt = 1 in) का उपयोग करें। |
| छिपा हुआ shape अभी भी प्रिंट होता है | कुछ प्रिंटर hidden फ़्लैग को नजरअंदाज करते हैं। | `Shape.setWrapType(WrapType.NONE)` सेट करें और साथ ही `Shape.getParagraph().getParagraphFormat().setPageBreakBefore(false)` को साफ़ करें। |

## निष्कर्ष

आप अब जानते हैं कि Aspose.Words for Java का उपयोग करके **Word** दस्तावेज़ों में **shape कैसे जोड़ें**, **shape कैसे डालें**, और **shape को कैसे छिपाएँ** ताकि यह अंतिम उपयोगकर्ताओं के लिए अदृश्य रहे जबकि दस्तावेज़ संरचना का हिस्सा बना रहे। ऊपर दिया गया पूर्ण उदाहरण फ़ाइल को लोड करता है, एक आयत डालता है, उसे छिपाता है, और परिणाम को सहेजता है, सामान्य उपयोग‑केस और कई किनारे के मामलों को कवर करता है।

अब आप संबंधित विषयों का अन्वेषण कर सकते हैं जैसे कस्टम फ़िल रंगों के साथ **shape कैसे डालें**, शर्तीय प्रिंटिंग के लिए **Word में shape को कैसे छिपाएँ**, या Aspose.Words के साथ बड़े पैमाने पर दस्तावेज़ प्रोसेसिंग को स्वचालित करना। विभिन्न `ShapeType` मानों, स्थितिकरण विकल्पों, और दृश्यता फ़्लैगों के साथ प्रयोग करें ताकि आपका कार्य‑प्रवाह पूरी तरह फिट हो सके।

Happy coding, and enjoy the flexibility that programmatic Word manipulation brings to your Java applications!

## अगला आप क्या सीखें?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Aspose.Words का उपयोग करके Java में प्रोग्रामेटिकली Word दस्तावेज़ बनाएं, shape जोड़ें और छिपाएँ](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [Java का उपयोग करके Word दस्तावेज़ में shape को कैसे छिपाएँ](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Aspose.Words के साथ एक खाली .docx Word दस्तावेज़ बनाएं और छिपा हुआ आयताकार shape जोड़ें](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}