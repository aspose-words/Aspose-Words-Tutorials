---
category: general
date: 2026-07-26
description: Aspose.Words का उपयोग करके जावा में आयताकार आकार डालें। आकार का आकार
  सेट करना, आकार की स्थिति निर्धारित करना, और DOCX फ़ाइल में आकारों को समूहित करना
  कैसे सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- set shape size
- position shape
- how to group shapes
- how to add rectangle
language: hi
lastmod: 2026-07-26
og_description: जावा में आयताकार आकार डालें ताकि समृद्ध DOCX ग्राफिक्स बन सकें। आकार
  का आकार निर्धारित करने, आकार को स्थित करने और आकारों को आसानी से समूहित करने के
  लिए इस चरण‑दर‑चरण गाइड का पालन करें।
og_image_alt: Screenshot showing a rectangle shape inserted and grouped in a Java‑generated
  Word document
og_title: जावा में आयताकार आकार सम्मिलित करें – समूह बनाना और स्थिति निर्धारण में
  निपुण बनें
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert rectangle shape in Java using Aspose.Words. Learn how to set
    shape size, position shape, and how to group shapes in a DOCX file.
  headline: Insert Rectangle Shape in Java – Group and Position Shapes
  type: TechArticle
tags:
- Aspose.Words
- Java
- Shapes
- DOCX
title: जावा में आयताकार आकार सम्मिलित करें – आकारों को समूहित और स्थित करें
url: /hi/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java में आयताकार आकार सम्मिलित करें – समूह बनाएं और आकारों को स्थित करें

क्या आपको कभी Java कोड लिखते समय Word दस्तावेज़ में **आयताकार आकार सम्मिलित** करने की आवश्यकता पड़ी है? आप अकेले नहीं हैं—रिपोर्ट, इनवॉइस, या कस्टम टेम्प्लेट बनाते डेवलपर्स अक्सर इस समस्या का सामना करते हैं। अच्छी खबर यह है कि Aspose.Words for Java की कुछ लाइनों से आप **आयताकार आकार सम्मिलित** कर सकते हैं, **आकार का आकार सेट** कर सकते हैं, **आकार को स्थित** कर सकते हैं, और यहाँ तक कि **आकारों को समूहित करने का तरीका** भी जान सकते हैं ताकि वे एक इकाई के रूप में चलें।

इस गाइड में हम एक खाली दस्तावेज़ बनाने से लेकर दो आयतों को सुगमता से समूहित करते हुए `.docx` फ़ाइल सहेजने तक की पूरी प्रक्रिया को चरण-दर-चरण देखेंगे। अंत तक आप **आयत जोड़ने का तरीका** वस्तुओं को जान जाएंगे, उनके आयामों को नियंत्रित करेंगे, उन्हें ठीक जहाँ चाहिए वहाँ रखेंगे, और उन्हें पुन: उपयोग योग्य समूह में बंडल करेंगे। Aspose.Words के अलावा कोई बाहरी लाइब्रेरी आवश्यक नहीं है, और कोड Java 8‑plus के साथ काम करता है।

## पूर्वापेक्षाएँ

- Java 8 या उससे नया स्थापित हो (मैं JDK 17 उपयोग कर रहा हूँ, लेकिन Maven को सपोर्ट करने वाला कोई भी संस्करण काम करेगा)
- Aspose.Words for Java 23.9 या बाद का – अपनी `pom.xml` में निर्भरता जोड़ें या JAR डाउनलोड करें
- Java सिंटैक्स की बुनियादी समझ (यदि आप `main` मेथड लिख सकते हैं, तो आप तैयार हैं)
- अपनी पसंद का IDE या टेक्स्ट एडिटर (IntelliJ IDEA, Eclipse, VS Code…)

> **प्रो टिप:** यदि आप Maven उपयोग कर रहे हैं, तो निर्भरता इस प्रकार दिखती है:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

अब जब हमने बुनियादी सेटअप कर लिया है, चलिए कोड में डुबकी लगाते हैं।

## आयताकार आकार सम्मिलित करें और उसका आकार सेट करें

सबसे पहले आप एक नया `Document` और एक `DocumentBuilder` बनाएँगे। बिल्डर आपका “पेन” है जो पृष्ठ पर आकार बनाता है। नीचे हम **आयताकार आकार सम्मिलित** करते हैं और तुरंत **आकार का आकार सेट** 100 × 80 पॉइंट्स पर करते हैं।

```java
import com.aspose.words.*;

public class GroupedRectanglesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder to add content
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape(400, 200);
        // The group itself is 400×200 points – adjust as needed

        // ---------- First rectangle ----------
        // Insert rectangle shape
        Shape rectangle1 = new Shape(document, ShapeType.RECTANGLE);
        // Set shape size
        rectangle1.setWidth(100);
        rectangle1.setHeight(80);
        // Position shape inside the group
        rectangle1.setLeft(20);   // 20 points from the left edge of the group
        rectangle1.setTop(30);    // 30 points from the top edge of the group
        // Add the rectangle to the group
        group.appendChild(rectangle1);
```

ध्यान दें कि `setWidth`/`setHeight` कॉल्स **आकार का आकार सेट** करती हैं पॉइंट्स में (1 pt ≈ 1/72 इंच)। यदि आप एक ही मेथड पसंद करते हैं तो `setSize` भी उपयोग कर सकते हैं, लेकिन स्पष्ट कॉल्स इरादा स्पष्ट रूप से दर्शाते हैं।

## पृष्ठ पर आकार को स्थित करें

पहला आयत प्राप्त करने के बाद, हमें दूसरे आयत को **आकार को स्थित** करना होगा ताकि वह पहले के साथ ओवरलैप न हो। स्थिति निर्धारण उसी तरह काम करता है: आप `Left` और `Top` प्रॉपर्टीज़ को समूह की मूल बिंदु के सापेक्ष सेट करते हैं।

```java
        // ---------- Second rectangle ----------
        Shape rectangle2 = new Shape(document, ShapeType.RECTANGLE);
        rectangle2.setWidth(120);
        rectangle2.setHeight(60);
        // Position this rectangle a bit farther to the right and lower down
        rectangle2.setLeft(150);
        rectangle2.setTop(50);
        group.appendChild(rectangle2);
```

यदि आप सोच रहे हैं कि हम `setX` के बजाय `setLeft` क्यों उपयोग करते हैं, तो इसका कारण है कि Aspose.Words क्लासिक Windows GDI कोऑर्डिनेट सिस्टम अपनाता है—`Left` क्षैतिज ऑफसेट है, `Top` लंबवत ऑफसेट है। इन मानों को बदलने से आप लेआउट को टेबल या पैराग्राफ़ के साथ झंझट किए बिना सूक्ष्म रूप से समायोजित कर सकते हैं।

## आकारों को समूहित करने का तरीका

आप पूछ सकते हैं, “समूह बनाने की ज़रूरत क्यों?” समूह बनाना तब समझ में आता है जब आप चाहते हैं कि आकार एक साथ चलें, इकाई के रूप में घुमें, या एक समान शैली साझा करें। ऊपर के स्निपेट में हमने पहले ही `builder.insertGroupShape` के माध्यम से एक `GroupShape` बनाया है। वह ऑब्जेक्ट मूलतः एक कंटेनर है—इसे एक फ़ोल्डर की तरह सोचें जो अन्य आकार फ़ाइलों को रखता है।

> **क्यों यह महत्वपूर्ण है:** यदि आप बाद में कैप्शन जोड़ने या पूरे डायग्राम को घुमाने का निर्णय लेते हैं, तो आपको केवल समूह को संशोधित करना होगा, न कि प्रत्येक आयत को अलग‑अलग।

## समूह में आयत जोड़ने का तरीका

समूह में **आयत जोड़ने का तरीका** बस `group.appendChild(rectangle)` को कॉल करना है। अंतर्गत Aspose.Words समूह के आंतरिक संग्रह को अपडेट करता है और स्वचालित रूप से बाउंडिंग बॉक्स को पुनः गणना करता है ताकि समूह अभी भी अपनी निर्धारित चौड़ाई और ऊँचाई में फिट हो।

```java
        // At this point the group already contains both rectangles.
        // You can also set the group’s border or fill if you like.
        group.getShapeStyle().setLineColor(Color.BLACK);
        group.getShapeStyle().setFillColor(Color.LIGHTGRAY);
```

आप अन्य `ShapeType`s—`ShapeType.ELLIPSE`, `ShapeType.TRIANGLE`, आदि—के साथ प्रयोग कर सकते हैं, और वही `appendChild` पैटर्न काम करता है।

## दस्तावेज़ सहेजें

अंत में, हम दस्तावेज़ को डिस्क पर सहेजते हैं। पथ पूर्ण या सापेक्ष हो सकता है; बस यह सुनिश्चित करें कि फ़ोल्डर मौजूद है।

```java
        // Step 5: Save the document containing the grouped shapes
        String outPath = "output/GroupShape.docx";
        document.save(outPath);
        System.out.println("Document saved to: " + outPath);
    }
}
```

जब आप Microsoft Word में `GroupShape.docx` खोलते हैं, तो आपको दो आयतें बगल‑बगल दिखेंगी, दोनों एक हल्के‑ग्रे बॉक्स के भीतर लॉक होंगी। ग्रे बॉक्स को चुनने से दोनों आयतें एक साथ हाइलाइट होंगी—यह प्रमाण है कि **आकारों को समूहित करने का तरीका** वास्तव में काम करता है।

![Grouped rectangles in a Word document](placeholder-image.png){: .center-image alt="Java‑जनित DOCX फ़ाइल में दो आयतों को समूहित दिखाते हुए आयताकार आकार सम्मिलित करने का उदाहरण"}

*छवि वैकल्पिक पाठ (SEO):* **Java‑जनित DOCX फ़ाइल में दो आयतों को समूहित दिखाते हुए आयताकार आकार का उदाहरण**।

## अपेक्षित आउटपुट

- `output` फ़ोल्डर में स्थित `GroupShape.docx` फ़ाइल।
- दस्तावेज़ के भीतर: 400 × 200 pt का समूह जिसमें दो आयतें (100 × 80 pt और 120 × 60 pt) क्रमशः (20, 30) और (150, 50) पर स्थित हैं।
- समूह में पतली काली बॉर्डर और हल्का‑ग्रे फ़िल है, जिससे समूह बनाना दृश्य रूप से स्पष्ट हो जाता है।

फ़ाइल खोलें और ग्रे बॉक्स को ड्रैग करने की कोशिश करें—दोनों आयतें एक साथ चलनी चाहिए। यदि नहीं चलतीं, तो दोबारा जांचें कि आपने प्रत्येक आकार के लिए `group.appendChild` कॉल किया है।

## सामान्य कठिनाइयाँ और किनारी मामलों

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| **आयतें पृष्ठ के बाहर दिखाई देती हैं** | `Left`/`Top` मान समूह के आयामों से अधिक हो जाते हैं | समूह का आकार बढ़ाएँ (`insertGroupShape(width, height)`) या ऑफसेट कम करें |
| **समूह सहेजने के बाद गायब हो जाता है** | समूह का `Width`/`Height` 0 पर सेट है | `insertGroupShape` कॉल करते समय शून्य‑से‑भिन्न आयाम प्रदान करें |
| **आकार के रंग गलत दिखते हैं** | डिफ़ॉल्ट फ़िल ट्रांसपेरेंट है; Word इसे सफ़ेद के रूप में रेंडर कर सकता है | `setFillColor` स्पष्ट रूप से सेट करें या `ShapeStyle` उपयोग करें |
| **अपवाद `ArgumentOutOfRangeException`** | नकारात्मक निर्देशांक का उपयोग करना | `Left` और `Top` को नकारात्मक न रखें |

इन समस्याओं को शुरुआती चरण में हल करने से आप “मेरे आकार क्यों गायब हो रहे हैं?” जैसी सिरदर्द से बचते हैं, जिसका सामना कई नए उपयोगकर्ता करते हैं।

## पुनरावलोकन और अगले कदम

हमने Java में **आयताकार आकार सम्मिलित** करने की पूरी प्रक्रिया को कवर किया है: दस्तावेज़ बनाना, **आकार का आकार सेट**, **आकार को स्थित**, **आकारों को समूहित करने का तरीका**, और **समूह में आयत जोड़ने का तरीका**। पूर्ण, चलाने योग्य उदाहरण ऊपर कोड ब्लॉक में है, और आप इसे सीधे Maven प्रोजेक्ट में पेस्ट करके परिणाम देख सकते हैं।

अगला क्या? विचार करें:

- प्रत्येक आयत के भीतर टेक्स्ट जोड़ना द्वारा

## अगला आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API सुविधाओं में महारत हासिल करने और अपने प्रोजेक्ट में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Word दस्तावेज़ Java बनाएं – शैडो इफ़ेक्ट के साथ आयताकार आकार जोड़ें](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for .NET का उपयोग करके Word दस्तावेज़ में समूह आकार बनाएं](/words/english/net/working-with-shapes/add-group-shape/)
- [शैडो वाले आयताकार आकार के साथ खाली Word दस्तावेज़ बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}