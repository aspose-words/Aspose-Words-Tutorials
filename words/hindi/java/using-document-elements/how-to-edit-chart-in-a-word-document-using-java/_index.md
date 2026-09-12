---
category: general
date: 2026-09-11
description: Java के साथ Word दस्तावेज़ में चार्ट को कैसे संपादित करें – चार्ट सेटिंग्स
  को अपडेट करना, चार्ट ग्रिडलाइन सक्षम करना, चार्ट विकल्प बदलना, और अपडेटेड दस्तावेज़
  को सहेजना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- update chart settings
- save updated document
- change chart options
- enable chart gridlines
language: hi
lastmod: 2026-09-11
og_description: जावा के साथ वर्ड दस्तावेज़ में चार्ट को कैसे संपादित करें। चार्ट सेटिंग्स
  अपडेट करने, चार्ट ग्रिडलाइन सक्षम करने, चार्ट विकल्प बदलने और अपडेटेड दस्तावेज़
  को सहेजने के लिए इस गाइड का पालन करें।
og_image_alt: Screenshot of a Word document showing a chart with gridlines enabled
og_title: जावा का उपयोग करके वर्ड दस्तावेज़ में चार्ट कैसे संपादित करें – पूर्ण मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  headline: How to edit chart in a Word document using Java
  type: TechArticle
- description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  name: How to edit chart in a Word document using Java
  steps:
  - name: Expected result
    text: 'When you open `output.docx`:'
  - name: What if the document has no chart?
    text: 'Attempting to cast a non‑chart shape will throw a `ClassCastException`.
      Guard against this by checking the shape type:'
  - name: How to edit a specific chart instead of the first one?
    text: 'Iterate through `shapes` and match a known title or an alternative identifier:'
  - name: Can I disable gridlines again later?
    text: 'Yes, simply set the property to `false`:'
  - name: Does this work with `.doc` (binary) files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. However, some newer chart features (like graduations) are only
      stored in the OOXML format, so you’ll see the effect only when saving as `.docx`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Java का उपयोग करके Word दस्तावेज़ में चार्ट को कैसे संपादित करें
url: /hi/java/using-document-elements/how-to-edit-chart-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java का उपयोग करके Word दस्तावेज़ में चार्ट को कैसे संपादित करें

यदि आपको Word फ़ाइल में **चार्ट को कैसे संपादित करें** की आवश्यकता है, तो यह गाइड आपको सटीक चरण दिखाता है। आप सीखेंगे कि चार्ट सेटिंग्स को कैसे अपडेट करें, चार्ट ग्रिडलाइन सक्षम करें, चार्ट विकल्प बदलें, और अंत में **अपडेटेड दस्तावेज़ को सहेजें** बिना किसी फ़ॉर्मेटिंग को खोए।

प्रोग्रामेटिक रूप से चार्ट के साथ काम करना अक्सर एक ब्लैक‑बॉक्स ऑपरेशन जैसा लगता है, विशेष रूप से जब आप ग्रेजुएशन या ग्रिडलाइन जैसी दृश्य विवरणों को समायोजित करना चाहते हैं। यह ट्यूटोरियल वह सब कवर करता है जो आपको जानना आवश्यक है, दस्तावेज़ लोड करने से लेकर बदलावों को सहेजने तक। कोई बाहरी टूल आवश्यक नहीं है—केवल Aspose.Words for Java लाइब्रेरी (संस्करण 24.9 या बाद का) चाहिए।

इस लेख के अंत तक आप सक्षम होंगे:

* `.docx` फ़ाइल लोड करें जिसमें चार्ट हो।
* चार्ट शेप को खोजें और उसकी प्रॉपर्टीज़ बदलें।
* चार्ट ग्रिडलाइन (ग्रेजुएशन) सक्षम करें और अन्य विकल्प समायोजित करें।
* **अपडेटेड दस्तावेज़ को** नई फ़ाइल में सहेजें।

## आवश्यकताएँ

* आपके मशीन पर Java 17 या बाद का स्थापित हो।  
* निर्भरताओं को प्रबंधित करने के लिए Maven या Gradle।  
* Aspose.Words for Java 24.9+ (वह संस्करण जिसने `setShowGraduations` पेश किया)।  
* एक Word दस्तावेज़ (`input.docx`) जिसमें पहले से कम से कम एक चार्ट हो।

यदि आप Aspose.Words से परिचित नहीं हैं, तो इसे एक पूर्ण‑विशेषताओं वाला API मानें जो आपको प्रोग्रामेटिक रूप से Word दस्तावेज़ पढ़ने, संशोधित करने और लिखने देता है—जैसे आप वेब ब्राउज़र में DOM को नियंत्रित करते हैं।

## चरण 1: प्रोजेक्ट सेट अप करें और लाइब्रेरी इम्पोर्ट करें

Create a new Maven project or add the dependency to an existing one:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

> **Pro tip:** नवीनतम स्थिर रिलीज़ का उपयोग करें ताकि आपके पास `setShowGraduations` मेथड हो। पुराने संस्करण कंपाइल नहीं होंगे।

## चरण 2: Word दस्तावेज़ लोड करें जिसमें चार्ट हो

किसी भी **चार्ट को कैसे संपादित करें** कार्यप्रवाह में पहला कदम स्रोत फ़ाइल को लोड करना है। Aspose.Words पूरे दस्तावेज़ को `Document` क्लास से दर्शाता है।

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // Replace with the actual path to your input file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document into memory
        Document doc = new Document(inputPath);
```

`Document` ऑब्जेक्ट आपको फ़ाइल के भीतर हर नोड तक पहुँच देता है, जिसमें शेप्स, टेबल्स और पैराग्राफ़ शामिल हैं।

## चरण 3: दस्तावेज़ में पहला चार्ट शेप खोजें

चार्ट `Shape` नोड्स के रूप में संग्रहीत होते हैं जिनका रेंडरर `Chart` होता है। चार्ट को संपादित करने के लिए आपको पहले उस नोड को प्राप्त करना होगा।

```java
        // Find all shape nodes (including charts)
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);

        // Assume the first shape is a chart; adjust the index if needed
        Shape chartShape = (Shape) shapes.get(0);

        // Cast the shape renderer to Chart
        Chart chart = (Chart) chartShape.getChart();
```

यदि दस्तावेज़ में कई चार्ट हैं, तो `shapes` पर इटररेट करें और कास्ट करने से पहले `chartShape.getChart() != null` जांचें। यह `ClassCastException` को रोकता है और सुनिश्चित करता है कि आप केवल वैध चार्ट ऑब्जेक्ट्स पर **चार्ट विकल्प बदलें**।

## चरण 4: चार्ट ग्रिडलाइन (ग्रेजुएशन) सक्षम करें – संस्करण 24.9 में नया प्रॉपर्टी

`setShowGraduations` प्रॉपर्टी वैल्यू एक्सिस पर माइनर ग्रिडलाइन की दृश्यता को टॉगल करती है। इन्हें सक्षम करने से अक्सर घने डेटा सेट की पठनीयता बढ़ती है।

```java
        // Turn on gridlines (graduations) for the value axis
        chart.setShowGraduations(true);
```

> **Why this matters:** ग्रिडलाइन दर्शकों को प्रत्येक डेटा पॉइंट के लिए एक दृश्य संदर्भ देती हैं, जिससे ट्रेंड्स को पहचानना आसान हो जाता है। डिफ़ॉल्ट `false` है, इसलिए आवश्यकता पड़ने पर आपको इन्हें स्पष्ट रूप से सक्षम करना होगा।

आप अन्य पहलुओं को भी कस्टमाइज़ कर सकते हैं, जैसे मेजर ग्रिडलाइन, एक्सिस टाइटल, या लेजेंड की स्थिति। नीचे चार्ट टाइटल और लेजेंड पोजीशन बदलने का एक उदाहरण है—दोनों **चार्ट विकल्प बदलें** का हिस्सा हैं।

```java
        // Change the chart title
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);

        // Move the legend to the bottom
        chart.getLegend().setPosition(LegendPosition.BOTTOM);
```

## चरण 5: अपडेटेड चार्ट सेटिंग्स के साथ दस्तावेज़ सहेजें

चार्ट को संशोधित करने के बाद, बदलावों को सहेजें। यह चरण **अपडेटेड दस्तावेज़ को सहेजें** चरण को पूरा करता है।

```java
        // Replace with the desired output path
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // Save the modified document
        doc.save(outputPath);
        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

प्रोग्राम चलाने पर `output.docx` उत्पन्न होगा जहाँ चार्ट अब ग्रिडलाइन, नया टाइटल और पुनः स्थित लेजेंड दिखाएगा। विज़ुअल बदलावों की पुष्टि के लिए फ़ाइल को Microsoft Word में खोलें।

## पूर्ण स्रोत कोड (रनएबल)

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the Word document that contains a chart
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Locate the first chart shape in the document
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
        Shape chartShape = (Shape) shapes.get(0);
        Chart chart = (Chart) chartShape.getChart();

        // 3️⃣ Enable chart gridlines (graduations)
        chart.setShowGraduations(true);

        // 4️⃣ Change chart options (title and legend)
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);
        chart.getLegend().setPosition(LegendPosition.BOTTOM);

        // 5️⃣ Save the document with the updated chart settings
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

### अपेक्षित परिणाम

जब आप `output.docx` खोलते हैं:

* चार्ट वैल्यू एक्सिस पर माइनर ग्रिडलाइन दिखाता है।  
* टाइटल पढ़ता है **“Sales Overview 2026”**।  
* लेजेंड चार्ट के नीचे दिखाई देता है।

यदि मूल चार्ट में पहले से ग्रिडलाइन थीं, तो दृश्य रूप unchanged रहता है, जिससे पुष्टि होती है कि कोड **idempotent** है।

## सामान्य प्रश्न और एज‑केस हैंडलिंग

### यदि दस्तावेज़ में कोई चार्ट नहीं है तो क्या होगा?

नॉन‑चार्ट शेप को कास्ट करने का प्रयास `ClassCastException` फेंकेगा। शेप टाइप जांचकर इस स्थिति से बचें:

```java
if (chartShape.getShapeType() == ShapeType.CHART) {
    Chart chart = (Chart) chartShape.getChart();
    // proceed with modifications
}
```

### पहले वाले के बजाय किसी विशिष्ट चार्ट को कैसे संपादित करें?

`shapes` पर इटररेट करें और ज्ञात टाइटल या वैकल्पिक पहचानकर्ता से मिलाएँ:

```java
for (Node node : shapes) {
    Shape shape = (Shape) node;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart c = (Chart) shape.getChart();
        if ("Revenue Q1".equals(c.getTitle().getText())) {
            // modify this chart
        }
    }
}
```

### क्या मैं बाद में ग्रिडलाइन फिर से डिसेबल कर सकता हूँ?

हाँ, बस प्रॉपर्टी को `false` सेट करें:

```java
chart.setShowGraduations(false);
```

### क्या यह `.doc` (बाइनरी) फ़ाइलों के साथ काम करता है?

Aspose.Words फ़ाइल फ़ॉर्मेट को एब्स्ट्रैक्ट करता है, इसलिए वही कोड `.doc` और `.docx` दोनों के लिए काम करता है। हालांकि, कुछ नई चार्ट सुविधाएँ (जैसे ग्रेजुएशन) केवल OOXML फ़ॉर्मेट में संग्रहीत होती हैं, इसलिए प्रभाव केवल `.docx` के रूप में सहेजने पर ही दिखेगा।

## प्रोडक्शन‑रेडी कोड के लिए टिप्स

* **इनपुट पाथ्स को वैलिडेट करें** – लोड करने से पहले `Files.exists(Paths.get(inputPath))` का उपयोग करें।  
* **API कॉल्स को** try‑catch ब्लॉक्स में रैप करें ताकि `Exception` विवरण दिखें, विशेषकर जब भ्रष्ट दस्तावेज़ों से निपट रहे हों।  
* **रिसोर्सेज़ को डिस्पोज़ करें** – यद्यपि Aspose.Words मेमोरी मैनेज करता है, `doc.close()` (या यदि उपलब्ध हो तो try‑with‑resources) कॉल करने से नेटिव हैंडल जल्दी मुक्त हो सकते हैं।  
* **वर्ज़न चेक** – `setShowGraduations` कॉल करने से पहले सुनिश्चित करें कि रनटाइम लाइब्रेरी वर्ज़न ≥ 24.9 है। यदि प्रोग्रामेटिक गार्ड चाहिए तो आप `License.getVersion()` क्वेरी कर सकते हैं।

## निष्कर्ष

अब आप जानते हैं **चार्ट को कैसे संपादित करें** ऑब्जेक्ट्स को Java का उपयोग करके Word दस्तावेज़ में। प्रक्रिया—दस्तावेज़ लोड करना, चार्ट खोजना, चार्ट ग्रिडलाइन सक्षम करना, चार्ट विकल्प बदलना, और **अपडेटेड दस्तावेज़ को सहेजना**—प्रोग्रामेटिक चार्ट मैनिपुलेशन के सबसे सामान्य परिदृश्यों को कवर करती है।  

यहाँ से आप अतिरिक्त कस्टमाइज़ेशन जैसे डेटा सीरीज़ के रंग बदलना, चार्ट स्टाइल लागू करना, या चार्ट को इमेज के रूप में एक्सपोर्ट करना एक्सप्लोर कर सकते हैं। इन सभी कार्यों में वही पैटर्न अपनाया जाता है: `Chart` इंस्टेंस प्राप्त करें, उसकी प्रॉपर्टीज़ समायोजित करें, और **अपडेटेड दस्तावेज़ को सहेजें**।  

हैप्पी कोडिंग, और अपने रिपोर्टिंग आवश्यकताओं के अनुसार अन्य चार्ट सेटिंग्स के साथ प्रयोग करने में संकोच न करें!

## आप आगे क्या सीख सकते हैं?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच को एक्सप्लोर करने में मदद करती हैं।

- [Aspose.Words for Java का उपयोग करके कॉलम चार्ट कैसे बनाएं](/words/english/java/document-conversion-and-export/using-charts/)
- [Aspose.Words for Java के साथ दस्तावेज़ को PDF के रूप में कैसे सहेजें](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [चार्ट में डेटा लेबल्स के लिए डिफ़ॉल्ट विकल्प सेट करें](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}