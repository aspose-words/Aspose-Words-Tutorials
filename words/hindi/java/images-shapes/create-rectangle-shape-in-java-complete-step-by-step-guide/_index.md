---
category: general
date: 2026-07-03
description: जावा में आयताकार आकार बनाएं और सीखें कि आकार में छाया कैसे जोड़ें, छाया
  प्रभाव लागू करें, आकार की पारदर्शिता सेट करें, और जल्दी से खाली दस्तावेज़ बनाएं।
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- set shape transparency
- create blank document
language: hi
og_description: जावा में छाया, पारदर्शिता और खाली दस्तावेज़ के साथ आयताकार आकार बनाएं।
  आकार प्रबंधन में निपुण होने के लिए इस मार्गदर्शिका का पालन करें।
og_title: जावा में आयत आकार बनाएं – पूर्ण प्रोग्रामिंग ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  headline: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  name: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  steps:
  - name: What if I want a different shadow color?
    text: 'Simply change the `setColor` call:'
  - name: Can I apply the same shadow to multiple shapes?
    text: 'Yes. Create one `ShadowEffect` instance, configure it, then reuse it:'
  - name: How do I change the shadow blur dynamically?
    text: Expose a UI slider that maps to `setBlurRadius`. Values between `2` and
      `12` are typical; larger numbers produce a “glow” rather than a crisp shadow.
  - name: What if I need the shape to float rather than be inline?
    text: 'Swap the wrap type:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Automation
title: जावा में आयताकार आकार बनाएं – पूर्ण चरण-दर-चरण मार्गदर्शिका
url: /hi/java/images-shapes/create-rectangle-shape-in-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create rectangle shape in Java – Complete Step‑by‑Step Guide

क्या आपने कभी सोचा है कि **Java** का उपयोग करके Word दस्तावेज़ में **rectangle shape** कैसे बनाएँ? आप अकेले नहीं हैं—डेवलपर्स अक्सर ज्यामितीय ग्राफ़िक्स को जल्दी से जोड़ने और उन्हें हल्का शैडो देने की आवश्यकता रखते हैं ताकि लेआउट अधिक प्रोफ़ेशनल दिखे। इस ट्यूटोरियल में हम पूरी प्रक्रिया को कवर करेंगे: **create blank document** से लेकर **add shadow to shape**, **apply shadow effect**, और यहाँ तक कि **set shape transparency** तक।

नीचे दिया गया कोड स्निपेट एक पूरी तरह कार्यात्मक उदाहरण है जिसे आप अपने प्रोजेक्ट में कॉपी‑पेस्ट कर सकते हैं। कोई बाहरी दस्तावेज़ीकरण आवश्यक नहीं—सिर्फ चरणों का पालन करें, “क्यों” समझें, और आप सेकंडों में शैडो वाले रेक्टैंगल बना पाएँगे।

## What You’ll Learn

- Aspose.Words for Java का उपयोग करके प्रोग्रामेटिकली **create rectangle shape** कैसे करें।
- **add shadow to shape** करने और उसके विज़ुअल प्रॉपर्टीज़ को कॉन्फ़िगर करने के लिए आवश्यक कॉल्स।
- **apply shadow effect** करने और ऑफ़सेट, ब्लर रेडियस, तथा रंग जैसे पैरामीटर को ट्यून करने के तरीके।
- अधिक सूक्ष्म लुक के लिए **set shape transparency** की तकनीकें।
- **create blank document**, शैप इन्सर्ट करना, और परिणाम को सेव करना।

> **Pro tip:** इन सभी कार्यों को एक ही `Document` इंस्टेंस पर किया जाता है, जिससे आप उन्हें बिना मध्यवर्ती फ़ाइल I/O की चिंता किए चेन कर सकते हैं।

## Prerequisites

शुरू करने से पहले सुनिश्चित करें कि आपके पास हैं:

- Java 17 (या कोई भी हालिया JDK) स्थापित।
- Aspose.Words for Java लाइब्रेरी आपके प्रोजेक्ट में जोड़ी हुई (Maven coordinates: `com.aspose:aspose-words:23.12`)।
- एक Java IDE या साधारण टेक्स्ट एडिटर—कुछ भी फैंसी नहीं, बस कोड कंपाइल और रन करने के लिए।

यदि इनमें से कोई भी कमी है, तो Oracle से JDK डाउनलोड करें और Maven या Gradle के माध्यम से Aspose डिपेंडेंसी जोड़ें। सेटअप हो जाने पर आप तैयार हैं।

## Step 1: **Create blank document** – the canvas for everything

सबसे पहला काम एक खाली `Document` ऑब्जेक्ट बनाना है। इसे एक नई कागज़ की शीट समझें; इसके बिना आपका रेक्टैंगल रखने की कोई जगह नहीं होगी।

```java
// Step 1: Create a new blank document
Document document = new Document();
```

क्यों शुरू में खाली दस्तावेज़ बनाते हैं? क्योंकि हर शैप एक `Section` के अंदर रहता है, और नया‑से‑बनाया गया `Document` पहले से ही एक डिफ़ॉल्ट सेक्शन के साथ बॉडी रखता है जहाँ नोड्स जोड़े जा सकते हैं। इस चरण को छोड़ने से बाद में मैन्युअली सेक्शन बनाना पड़ेगा, जो अनावश्यक जटिलता लाता है।

## Step 2: **Create rectangle shape** and define its size

अब हमारे पास कैनवास है, चलिए **create rectangle shape** करते हैं। `Shape` क्लास को डॉक्यूमेंट रेफ़रेंस और एक `ShapeType` चाहिए। यहाँ हम `RECTANGLE` चुनते हैं और चौड़ाई/ऊँचाई पॉइंट्स में सेट करते हैं (1 pt ≈ 1/72 इंच)।

```java
// Step 2: Insert a rectangle shape and define its size and layout
Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
rectangleShape.setWidth(200);   // 200 pt ≈ 2.78 inches
rectangleShape.setHeight(100);  // 100 pt ≈ 1.39 inches
rectangleShape.setWrapType(WrapType.INLINE);
```

`WrapType.INLINE` क्यों सेट किया? इनलाइन रैपिंग शैप को पैराग्राफ में एक कैरेक्टर की तरह व्यवहार कराती है, जिससे वह आसपास के टेक्स्ट के साथ चलता है। यदि आपको फ्लोटिंग व्यवहार चाहिए, तो `WrapType.SQUARE` या `WrapType.TOP_BOTTOM` में स्विच करें।

## Step 3: **Apply shadow effect** – give the rectangle depth

एक सपाट रेक्टैंगल… बस सपाट। शैडो जोड़ने से वह उभर कर दिखता है। हम **apply shadow effect** करने के लिए एक `ShadowEffect` इंस्टेंस बनाते हैं, फिर उसकी विज़ुअल प्रॉपर्टीज़ को ट्यून करते हैं।

```java
// Step 3: Create a shadow effect and configure its visual properties
ShadowEffect shadowEffect = new ShadowEffect();
shadowEffect.setColor(Color.getGray(0.5));   // medium gray
shadowEffect.setOffsetX(5);                  // horizontal offset (points)
shadowEffect.setOffsetY(5);                  // vertical offset (points)
shadowEffect.setBlurRadius(8);               // softness of the shadow
shadowEffect.setTransparency(0.3);           // 30 % transparent
```

आइए इसे थोड़ा विस्तार से देखें:

- **Color** – `Color.getGray(0.5)` 50 % ग्रे देता है, जो न्यूट्रल है और अधिकांश बैकग्राउंड पर काम करता है।
- **OffsetX/Y** – पॉज़िटिव वैल्यू शैडो को दाएँ और नीचे धकेलती है; नेगेटिव वैल्यू बाएँ/ऊपर ले जाएगी।
- **BlurRadius** – बड़ी वैल्यू सॉफ्ट, अधिक डिफ्यूज़्ड शैडो बनाती है।
- **Transparency** – `0` (ऑपेक) से `1` (पूरी तरह ट्रांसपरेंट) तक रेंज। यहाँ हमने `0.3` चुना है ताकि हल्का प्रभाव मिले।

## Step 4: **Add shadow to shape** – bind the effect

इफ़ेक्ट बनाना पर्याप्त नहीं; हमें **add shadow to shape** करके `ShadowEffect` ऑब्जेक्ट को रेक्टैंगल से जोड़ना होगा।

```java
// Step 4: Apply the shadow effect to the rectangle shape
rectangleShape.setShadowEffect(shadowEffect);
```

बैकएंड में, यह कॉल OpenXML मार्कअप (`<w:shdw>`) को अपडेट करता है जिसे Word शैडो रेंडर करने के लिए उपयोग करता है। यदि आप सेव्ड `.docx` फ़ाइल को देखें तो `<w:effect>` एलिमेंट में हमारे सेट किए गए पैरामीटर दिखेंगे।

## Step 5: **Set shape transparency** – optional but often useful

कभी‑कभी आप चाहते हैं कि रेक्टैंगल खुद ही अर्ध‑ट्रांसपरेंट हो, ताकि बैकग्राउंड टेक्स्ट दिख सके। `Shape` क्लास `setFillColor` और `setFillTransparency` प्रदान करता है। नीचे एक छोटा उदाहरण है जो रेक्टैंगल को 40 % ट्रांसपरेंट बनाता है:

```java
// Optional: make the rectangle partially transparent
rectangleShape.setFillColor(Color.getWhite());
rectangleShape.setFillTransparency(0.4); // 40 % transparent
```

ऐसा क्यों करें? कल्पना करें एक वॉटरमार्क या हाइलाइटेड कॉल‑आउट जहाँ मूल कंटेंट पढ़ा जा सके। अपनी डिज़ाइन भाषा के अनुसार ट्रांसपरेंसी वैल्यू को एडजस्ट करें।

## Step 6: Insert the shape into the document

हमने रेक्टैंगल बनाया, शैडो जोड़ी, और (वैकल्पिक) ट्रांसपरेंसी सेट की। अब अंतिम कदम है **add the shape to the first section of the document**।

```java
// Step 5: Add the shape to the first section of the document
document.getFirstSection().getBody().appendChild(rectangleShape);
```

शैप को बॉडी में जोड़ने से वह पहले पैराग्राफ के अंत में रखी जाएगी। यदि आपको विशिष्ट इन्सर्शन पॉइंट चाहिए, तो टार्गेट `Paragraph` प्राप्त करें और `insertBefore` या `insertAfter` का उपयोग करें।

## Step 7: Save the document – see the result

सारा काम एक ही `save` कॉल में समेटा जाता है। अपने वातावरण के अनुसार उपयुक्त पाथ चुनें।

```java
// Step 6: Save the document with the shadowed shape
document.save("YOUR_DIRECTORY/ShadowShape.docx");
```

परिणामस्वरूप `ShadowShape.docx` को Microsoft Word या LibreOffice में खोलें, और आपको एक साफ़ रेक्टैंगल दिखेगा जिसमें हल्का ग्रे शैडो होगा, और यदि आपने वैकल्पिक चरण किया है तो थोड़ा ट्रांसपरेंट भी होगा। विज़ुअल हमारे प्रोग्रामेटिकली परिभाषित पैरामीटर से मेल खाता है।

---

![create rectangle shape with shadow in a Word document](https://example.com/images/rectangle-shadow.png "create rectangle shape with shadow")

*Image alt text:* **create rectangle shape with shadow** – अंतिम आउटपुट का विज़ुअल प्रतिनिधित्व।

## Common Questions & Edge Cases

### What if I want a different shadow color?

सिर्फ `setColor` कॉल को बदलें:

```java
shadowEffect.setColor(Color.getRed()); // bright red shadow
```

ध्यान रखें कि बहुत ज़्यादा चमकीले शैडो अनप्रोफ़ेशनल लग सकते हैं; सूक्ष्म टोन आमतौर पर बेहतर होते हैं।

### Can I apply the same shadow to multiple shapes?

हाँ। एक `ShadowEffect` इंस्टेंस बनाएँ, उसे कॉन्फ़िगर करें, और फिर कई शैप्स में री‑यूज़ करें:

```java
Shape circle = new Shape(document, ShapeType.OVAL);
circle.setShadowEffect(shadowEffect); // same effect as rectangle
```

सिर्फ `ShadowEffect` को अन्य शैप्स से अटैच करने के बाद उसे बदलने से बचें, जब तक आप सभी शैप्स को एक साथ अपडेट न करना चाहते हों।

### How do I change the shadow blur dynamically?

एक UI स्लाइडर बनाएँ जो `setBlurRadius` से मैप हो। सामान्य रेंज `2` से `12` तक होती है; बड़ी वैल्यू “ग्लो” जैसा प्रभाव देती है न कि तीखा शैडो।

### What if I need the shape to float rather than be inline?

रैप टाइप बदलें:

```java
rectangleShape.setWrapType(WrapType.SQUARE);
rectangleShape.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangleShape.setHorizontalAlignment(HorizontalAlignment.CENTER);
```

फ़्लोटिंग शैप्स अधिक लेआउट फ़्रीडम देती हैं लेकिन अतिरिक्त पोज़िशनिंग लॉजिक की आवश्यकता होती है।

## Full Working Example

नीचे पूरा, कॉपी‑पेस्ट‑रेडी प्रोग्राम है जिसमें हमने चर्चा किए सभी चरण शामिल हैं। इसे एक सामान्य Java एप्लिकेशन के रूप में चलाएँ।

```java
import com.aspose.words.*;

public class ShadowRectangleDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank document
        Document document = new Document();

        // 2. Build the rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);

        // 3. Configure shadow effect
        ShadowEffect shadowEffect = new ShadowEffect();
        shadowEffect.setColor(Color.getGray(0.5));
        shadowEffect.setOffsetX(5);
        shadowEffect.setOffsetY(5);
        shadowEffect.setBlurRadius(8);
        shadowEffect.setTransparency(0.3);

        // 4. Apply shadow to the rectangle
        rectangleShape.setShadowEffect(shadowEffect);

        // 5. (Optional) Make rectangle semi‑transparent
        rectangleShape.setFillColor(Color.getWhite());
        rectangleShape.setFillTransparency(0.4);

        // 6. Insert shape into the document
        document.getFirstSection().getBody().appendChild(rectangleShape);

        // 7. Save the file
        document.save("ShadowShape.docx");
    }
}
```

**Expected output:** जब आप `ShadowShape.docx` खोलेंगे, तो आपको एक सफ़ेद रेक्टैंगल दिखेगा, 200 × 100 pt, पहले पैराग्राफ के केंद्र में, 5 pt ऑफ़सेट वाला मध्यम‑ग्रे शैडो, ब्लर रेडियस 8, और 30 % ट्रांसपरेंट। रेक्टैंगल स्वयं 40 % ट्रांसपरेंट होगा, जिससे नीचे का टेक्स्ट झलक सकेगा।

## Wrapping Up

हमने अभी **create rectangle shape** को शून्य से बनाया, **add shadow to shape**, **apply shadow effect**, और यहाँ तक कि **set shape transparency** भी किया—सभी **create blank document** को बेसिस बनाकर। यह तरीका सीधा है, Aspose.Words की फ्लुएंट API पर आधारित है, और इसे सर्कल, स्टार या कस्टम पॉलीगॉन में भी विस्तारित किया जा सकता है।

अब आपका अगला कदम क्या है? `ShapeType.RECTANGLE` को `ShapeType.OVAL` से बदलें और शैडो वाले सर्कल बनाएँ, या ग्रेडिएंट फ़िल्स के साथ प्रयोग करें।

## What Should You Learn Next?

नीचे दिए गए ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच को एक्सप्लोर कर सकें।

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}