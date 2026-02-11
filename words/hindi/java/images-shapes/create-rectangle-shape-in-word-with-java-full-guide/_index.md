---
category: general
date: 2026-02-10
description: Aspose.Words for Java का उपयोग करके Word दस्तावेज़ में आयताकार आकार बनाएं।
  सीखें कि शैडो का रंग कैसे सेट करें, शैडो कैसे जोड़ें, और प्रोग्रामेटिक रूप से Word
  दस्तावेज़ बनाएं।
draft: false
keywords:
- create rectangle shape
- set shadow color
- create word document
- how to add shadow
- how to create shape
language: hi
og_description: Aspose.Words for Java का उपयोग करके Word दस्तावेज़ में आयताकार आकार
  बनाएं। छाया का रंग सेट करने, छाया जोड़ने और Word दस्तावेज़ बनाने के लिए इस चरण‑दर‑चरण
  ट्यूटोरियल का पालन करें।
og_title: जावा के साथ वर्ड में आयताकार आकार बनाएं – पूर्ण गाइड
tags:
- Aspose.Words
- Java
- Document Automation
title: जावा के साथ वर्ड में आयताकार आकार बनाएं – पूर्ण गाइड
url: /hi/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

text**; keep them but translate inside.

Also keep code snippets placeholders.

Let's produce.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word में Java के साथ आयताकार आकार बनाएं – पूर्ण गाइड

क्या आपको कभी **Word दस्तावेज़ में आयताकार आकार** बनाना था लेकिन नहीं पता था कहाँ से शुरू करें? आप अकेले नहीं हैं—कई डेवलपर्स को पहली बार प्रोग्रामेटिक रूप से Word में ग्राफ़िक्स ड्रॉ करने पर यही समस्या आती है। अच्छी खबर? Aspose.Words for Java के साथ आप पेज पर एक आयत डाल सकते हैं, उसे सुंदर शैडो दे सकते हैं, और फ़ाइल को सेकंडों में सेव कर सकते हैं। इस ट्यूटोरियल में हम बिल्कुल **शैडो कैसे जोड़ें**, **शैडो का रंग कैसे सेट करें**, और **शुरू से Word दस्तावेज़ कैसे बनाएं** यह सब दिखाएंगे।

हम वह सब कवर करेंगे जिसकी आपको ज़रूरत है: आवश्यक लाइब्रेरीज़, प्रत्येक कोड लाइन, कुछ सेटिंग्स क्यों महत्वपूर्ण हैं, और कुछ ट्रिक्स जो आधिकारिक डॉक्यूमेंटेशन में नहीं मिलेंगी। अंत तक आपके पास एक तैयार‑से‑चलाने वाला उदाहरण होगा जो एक आयताकार आकार को नरम ग्रे शैडो के साथ बनाता है, और *Shadow.docx* के रूप में सेव हो जाता है।

## Prerequisites – What You Need Before You Start

कोड में डुबकी लगाने से पहले सुनिश्चित करें कि आपके पास ये चीज़ें हैं:

| Requirement | Reason |
|-------------|--------|
| Java Development Kit (JDK) 8 या नया | Aspose.Words किसी भी आधुनिक JDK पर चलता है। |
| Maven या Gradle (वैकल्पिक) | Aspose.Words डिपेंडेंसी जोड़ना आसान बनाता है। |
| Aspose.Words for Java लाइसेंस (या फ्री ट्रायल) | लाइब्रेरी कमर्शियल है; परीक्षण के लिए ट्रायल चलाएगा। |
| एक IDE (IntelliJ IDEA, Eclipse, VS Code, आदि) | उदाहरण को जल्दी चलाने और डिबग करने में मदद करता है। |

यदि आपके पास पहले से एक Java प्रोजेक्ट है, तो बस Maven कॉर्डिनेट जोड़ें:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

इससे आगे कोई जटिल सेटअप नहीं—सिर्फ एक साधारण `public static void main` मेथड चलाएगा।

![create rectangle shape example](https://example.com/rectangle-shadow.png "Word में शैडो के साथ आयताकार आकार बनाएं")

*Image alt text: शैडो के साथ आयताकार आकार का उदाहरण, जिसमें सियान आयत और ग्रे शैडो दिखाया गया है।*

## Step 1 – Create a New Word Document

सबसे पहले हमें एक खाली दस्तावेज़ बनाना है। इसे ऐसे समझें जैसे आप एक नया Word फ़ाइल खोल रहे हैं जिस पर बाद में चित्र बनायेंगे।

```java
// Step 1: Initialize a blank Document object
Document document = new Document();
```

खाली `Document` से क्यों शुरू करें? क्योंकि Aspose.Words `Document` क्लास को सभी बाद की ऑपरेशन्स (पैराग्राफ, टेबल, या शैप) के लिए कैनवास मानता है। यदि आप इस स्टेप को छोड़ देंगे तो किसी भी चीज़ को इन्सर्ट करने की कोशिश में `NullPointerException` मिलेगा।

## Step 2 – Set Up a DocumentBuilder

`DocumentBuilder` आपका दोस्ताना पेन है जो `Document` में लिखता है। यह कंटेंट जोड़ने का अनुशंसित तरीका है क्योंकि यह स्वचालित रूप से कर्सर पोज़िशन को मैनेज करता है।

```java
// Step 2: Create a DocumentBuilder tied to our document
DocumentBuilder builder = new DocumentBuilder(document);
```

आप सोच सकते हैं, “डॉक्यूमेंट को सीधे मैनीपुलेट क्यों नहीं करते?” जवाब: बिल्डर लो‑लेवल डिटेल्स जैसे सेक्शन हैंडलिंग को एब्स्ट्रैक्ट कर देता है, जिससे कोड साफ़ और कम एरर‑प्रोन बनता है।

## Step 3 – Insert the Rectangle Shape

अब आता है मज़ेदार हिस्सा—**आकार कैसे बनाएं**। हम एक आयत इन्सर्ट करेंगे जिसका आकार 100 × 50 पॉइंट्स होगा और उसे सियान फ़िल देंगे ताकि आप इसे देख सकें।

```java
// Step 3: Insert a rectangle shape of size 100x50 points
Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

// Apply a solid fill color to make the shape visible
rectangle.setFillColor(java.awt.Color.CYAN);
```

कुछ नोट्स:

* `ShapeType.RECTANGLE` Aspose को बताता है कि हमें आयत चाहिए; आप इसे `OVAL`, `LINE` आदि से बदल सकते हैं।
* डाइमेंशन पॉइंट्स में होते हैं (1 pt ≈ 1/72 in)। अपने लेआउट के अनुसार इन्हें समायोजित करें।
* बिना फ़िल कलर के शैप सफ़ेद पेज पर अदृश्य रहेगा—इसलिए सियान रंग दिया गया है।

## Step 4 – Add a Shadow and **Set Shadow Color**

यहीं हम **शैडो कैसे जोड़ें** वाले हिस्से का उत्तर देंगे। `ShadowFormat` ऑब्जेक्ट शैडो के हर विज़ुअल पहलू को कंट्रोल करता है, रंग से लेकर ब्लर रेडियस तक।

```java
// Step 4: Enable the shape's shadow and configure its appearance
rectangle.getShadowFormat().setVisible(true);                     // Turn the shadow on
rectangle.getShadowFormat().setColor(java.awt.Color.GRAY);      // **set shadow color** to gray
rectangle.getShadowFormat().setBlurRadius(5.0);                  // Soft blur for realism
rectangle.getShadowFormat().setOffsetX(4.0);                     // Horizontal offset
rectangle.getShadowFormat().setOffsetY(4.0);                     // Vertical offset
rectangle.getShadowFormat().setTransparency(0.3);               // 30 % transparent
```

इन विशेष मानों का कारण क्या है?

* **Visibility** – `setVisible(true)` के बिना बाकी सेटिंग्स अनदेखी रह जाती हैं।
* **Color** – ग्रे एक न्यूट्रल विकल्प है जो लाइट और डार्क दोनों बैकग्राउंड पर काम करता है। आप `java.awt.Color.GRAY` को किसी भी `java.awt.Color` से बदल सकते हैं।
* **Blur radius** – `5.0` का मान हल्का फेदर देता है; बड़े नंबर शैडो को अधिक डिफ्यूज़ बनाते हैं।
* **OffsetX/Y** – ऑफ़सेट शैडो को दाएँ और नीचे शिफ्ट करता है, जिससे टॉप‑लेफ़्ट लाइट सोर्स की नकल होती है।
* **Transparency** – अर्द्ध‑पारदर्शी शैडो पेज के साथ बेहतर ब्लेंड होता है, खासकर प्रिंटिंग में।

यदि आप तेज़ लुक चाहते हैं, तो ब्लर रेडियस को `0` कर दें और ऑफ़सेट बढ़ा दें। प्रयोग करने में हिचकिचाएँ नहीं—शैडो बहुत विज़ुअल होते हैं, और सही सेटिंग्स आपके दस्तावेज़ के डिज़ाइन पर निर्भर करती हैं।

## Step 5 – Save the Document

आख़िर में, सब कुछ `.docx` फ़ाइल में सेव कर देते हैं। आप कोई भी पाथ चुन सकते हैं; बस यह सुनिश्चित करें कि डायरेक्टरी मौजूद हो।

```java
// Step 5: Save the document with the shaped shadow to a file
document.save("YOUR_DIRECTORY/Shadow.docx");
```

जब आप *Shadow.docx* को Microsoft Word में खोलेंगे, तो आपको एक सियान आयत साथ में हल्का ग्रे शैडो दिखेगा जो दाएँ और नीचे 4 pts की दूरी पर है। यही पूरा **Word दस्तावेज़ बनाना** वर्कफ़्लो है।

### Expected Result

| Element | Appearance |
|---------|------------|
| Rectangle | सियान फ़िल, 100 × 50 pt आकार |
| Shadow | ग्रे, 30 % ट्रांसपेरेंट, 5 pt ब्लर, ऑफ़सेट (4, 4) |
| File | `Shadow.docx` आपके द्वारा दिए गए पाथ पर स्टोर किया गया |

यदि शैप नहीं दिख रहा है, तो फ़िल कलर पेज बैकग्राउंड के समान तो नहीं है, और शैडो को `visible` सेट किया गया है, यह दोबारा चेक करें।

## Pro Tips & Common Pitfalls

* **Pro tip:** यदि आप शैप के चारों ओर बॉर्डर चाहते हैं तो `rectangle.setStrokeColor(java.awt.Color.BLACK);` इस्तेमाल करें। यह प्रिंटेड पेज पर आयत को अधिक उभारा दिखाता है।
* **Watch out for:** रीड‑ओनली फ़ोल्डर में सेव करने से `IOException` फेंका जाएगा। लिखने योग्य लोकेशन चुनें या फ़ाइल परमिशन समायोजित करें।
* **Edge case:** यदि आपको ट्रांसपेरेंट फ़िल (कोई रंग नहीं) चाहिए, तो `rectangle.setFillColor(java.awt.Color.WHITE); rectangle.setFillOpacity(0.0);` कॉल करें। शैप अभी भी शैडो डालेगा, जो वॉटरमार्क‑स्टाइल ग्राफ़िक्स में उपयोगी हो सकता है।
* **Performance note:** लूप में सैकड़ों शैप जोड़ने से मेमोरी उपयोग बढ़ सकता है। सभी शैप जोड़ने के बाद केवल एक बार `document.save` कॉल करें।

## Full Working Example

नीचे पूरा प्रोग्राम दिया गया है जिसे आप `ShadowDemo` नामक Java क्लास में कॉपी‑पेस्ट कर सकते हैं। यह (यदि आपके क्लासपाथ में Aspose.Words JAR है) बिना किसी बदलाव के कम्पाइल और रन होगा।

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to construct the document content
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Apply a solid fill color to make the shape visible
        rectangle.setFillColor(java.awt.Color.CYAN);

        // Step 4: Enable the shape's shadow and configure its appearance
        rectangle.getShadowFormat().setVisible(true);
        rectangle.getShadowFormat().setColor(java.awt.Color.GRAY); // set shadow color
        rectangle.getShadowFormat().setBlurRadius(5.0);
        rectangle.getShadowFormat().setOffsetX(4.0);
        rectangle.getShadowFormat().setOffsetY(4.0);
        rectangle.getShadowFormat().setTransparency(0.3);

        // Step 5: Save the document with the shaped shadow to a file
        document.save("YOUR_DIRECTORY/Shadow.docx");
    }
}
```

प्रोग्राम चलाएँ, उत्पन्न *Shadow.docx* खोलें, और आपको वही आयत और शैडो दिखेगा जैसा ऊपर बताया गया है।

## What If You Need More Shapes?

आप सोच सकते हैं, “क्या मैं **आयताकार आकार** कई बार बना सकता हूँ या अन्य शैप्स इस्तेमाल कर सकता हूँ?” बिल्कुल। बस इन्सर्शन कोड को लूप में रखें और `builder.moveTo` या `builder.insertParagraph` से कोऑर्डिनेट्स बदलें। वही शैडो सेटिंग्स को एक हेल्पर मेथड में निकालकर पुनः उपयोग किया जा सकता है:

```java
private static void applyStandardShadow(Shape shape) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(java.awt.Color.GRAY);
    shape.getShadowFormat().setBlurRadius(5.0);
    shape.getShadowFormat().setOffsetX(4.0);
    shape.getShadowFormat().setOffsetY(4.0);
    shape.getShadowFormat().setTransparency(0.3);
}
```

हर शैप इन्सर्शन के बाद `applyStandardShadow(rectangle);` कॉल करें ताकि आपका कोड DRY (Don’t Repeat Yourself) रहे।

## Next Steps – Going Beyond the Basics

अब जब आप **शैडो कैसे जोड़ें** जानते हैं, तो इन संबंधित टॉपिक्स को एक्सप्लोर करें:

* **टेक्स्ट रन के लिए शैडो रंग कैसे सेट करें** – शीर्षकों को हल्का लिफ्ट देता है।
* **टेबल और इमेज के साथ Word दस्तावेज़ बनाएं** – शैप को अन्य कंटेंट के साथ मिलाएँ।
* **Word के बिल्ट‑इन** का उपयोग करके **आकार एनीमेशन** बनाना

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}