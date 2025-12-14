---
date: 2025-12-14
description: Aspose.Words for Java के साथ **इमेज शेप** कैसे डालें, सीखें। यह गाइड
  आपको दिखाता है कि कैसे शैप्स जोड़ें, टेक्स्ट बॉक्स शैप्स बनाएं, टेबल में शैप्स रखें,
  शैप का एस्पेक्ट रेशियो सेट करें, और कॉलआउट शैप्स जोड़ें।
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java में दस्तावेज़ आकारों का उपयोग
url: /hi/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java के साथ **insert image shape** कैसे डालें

## त्वरित उत्तर
- **शेप जोड़ने का मुख्य तरीका क्या है?** `DocumentBuilder.insertShape` का उपयोग करें या एक `Shape` इंस्टेंस बनाकर उसे डॉक्यूमेंट ट्री में जोड़ें।  
- **क्या मैं इमेज को शेप के रूप में डाल सकता हूँ?** हाँ – `builder.insertImage` कॉल करें और फिर प्राप्त `Shape` को किसी अन्य की तरह उपयोग करें।  
- **मैं शेप का aspect ratio कैसे रखूँ?** अपनी आवश्यकता के अनुसार `shape.setAspectRatioLocked(true)` या `false` सेट करें।  
- **क्या शेप्स को ग्रुप करना संभव है?** बिल्कुल – उन्हें `GroupShape` में रैप करें और ग्रुप को एक सिंगल नोड के रूप में डालें।  
- **क्या SmartArt डायग्राम Aspose.Words के साथ काम करते हैं?** हाँ, आप प्रोग्रामेटिकली SmartArt शेप्स को डिटेक्ट और अपडेट कर सकते हैं।

## **insert image shape** क्या है?
एक *image shape* एक दृश्य तत्व है जो Word डॉक्यूमेंट के भीतर रास्टर या वेक्टर ग्राफिक्स रखता है। Aspose.Words में, इमेज को एक `Shape` ऑब्जेक्ट द्वारा दर्शाया जाता है, जिससे आपको आकार, स्थिति, घुमाव, और रैपिंग पर पूर्ण नियंत्रण मिलता है।

## आपके डॉक्यूमेंट्स में शेप्स का उपयोग क्यों करें?
- **दृश्य प्रभाव:** शेप्स मुख्य जानकारी की ओर ध्यान आकर्षित करते हैं।  
- **इंटरैक्टिविटी:** बटन और कॉलआउट्स को URLs या बुकमार्क्स से लिंक किया जा सकता है।  
- **लेआउट लचीलापन:** ग्राफिक्स को एब्सोल्यूट या रिलेटिव कोऑर्डिनेट्स के साथ सटीक रूप से पोजिशन करें।  
- **ऑटोमेशन:** मैन्युअल एडिटिंग के बिना जटिल लेआउट्स जेनरेट करें।

## आवश्यकताएँ
- Java Development Kit (JDK 8 या उससे ऊपर)  
- Aspose.Words for Java लाइब्रेरी (आधिकारिक साइट से डाउनलोड करें)  
- Java और ऑब्जेक्ट‑ओरिएंटेड प्रोग्रामिंग का बेसिक ज्ञान  

आप लाइब्रेरी यहाँ डाउनलोड कर सकते हैं: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

## **add shape** कैसे करें – GroupShape डालना
`GroupShape` आपको कई शेप्स को एक सिंगल यूनिट के रूप में ट्रीट करने देता है। यह कई एलिमेंट्स को साथ में मूव या फॉर्मेट करने में उपयोगी है।

```java
Document doc = new Document();
doc.ensureMinimum();

GroupShape groupShape = new GroupShape(doc);
Shape accentBorderShape = new Shape(doc, ShapeType.ACCENT_BORDER_CALLOUT_1);
accentBorderShape.setWidth(100.0);
accentBorderShape.setHeight(100.0);

groupShape.appendChild(accentBorderShape);

Shape actionButtonShape = new Shape(doc, ShapeType.ACTION_BUTTON_BEGINNING);
actionButtonShape.setLeft(100.0);
actionButtonShape.setWidth(100.0);
actionButtonShape.setHeight(200.0);

groupShape.appendChild(actionButtonShape);

groupShape.setWidth(200.0);
groupShape.setHeight(200.0);
groupShape.setCoordSize(new Dimension(200, 200));

DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertNode(groupShape);

doc.save("Your Directory Path" + "WorkingWithShapes.AddGroupShape.docx");
```

## **text box shape** बनाएं
टेक्स्ट बॉक्स एक कंटेनर है जो फॉर्मेटेड टेक्स्ट रख सकता है। आप इसे डायनामिक लुक के लिए घुमा भी सकते हैं।

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertShape(ShapeType.TEXT_BOX, RelativeHorizontalPosition.PAGE, 100.0,
    RelativeVerticalPosition.PAGE, 100.0, 50.0, 50.0, WrapType.NONE);

shape.setRotation(30.0);
builder.writeln();

shape = builder.insertShape(ShapeType.TEXT_BOX, 50.0, 50.0);
shape.setRotation(30.0);

OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);

doc.save("Your Directory Path" + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## **shape aspect ratio** सेट करें
कभी-कभी आपको शेप को फ्रीली स्ट्रेच करना पड़ता है, कभी आप उसकी मूल अनुपात को बनाए रखना चाहते हैं। aspect ratio को कंट्रोल करना सरल है।

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## **shape in table** रखें
टेबल सेल के अंदर शेप एम्बेड करना रिपोर्ट लेआउट्स के लिए उपयोगी हो सकता है। नीचे दिया गया उदाहरण एक टेबल बनाता है और फिर एक वाटरमार्क‑स्टाइल शेप डालता है जो पूरे पेज को कवर करता है।

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

builder.startTable();
builder.getRowFormat().setHeight(100.0);
builder.getRowFormat().setHeightRule(HeightRule.EXACTLY);

for (int i = 0; i < 31; i++) {
    if (i != 0 && i % 7 == 0)
        builder.endRow();

    builder.insertCell();
    builder.write("Cell contents");
}

builder.endTable();

Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.isLayoutInCell(true); // Display the shape outside of the table cell if it will be placed into a cell.
watermark.setWidth(300.0);
watermark.setHeight(70.0);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setRotation(-40);
watermark.setFillColor(Color.GRAY);
watermark.setStrokeColor(Color.GRAY);
watermark.getTextPath().setText("watermarkText");
watermark.getTextPath().setFontFamily("Arial");
watermark.setName("WaterMark_{Guid.NewGuid()}");
watermark.setWrapType(WrapType.NONE);

Run run = (Run) doc.getChildNodes(NodeType.RUN, true).get(doc.getChildNodes(NodeType.RUN, true).getCount() - 1);
builder.moveTo(run);
builder.insertNode(watermark);

doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010);
doc.save("Your Directory Path" + "WorkingWithShapes.LayoutInCell.docx");
```

## **callout shape** जोड़ें
एक callout शेप नोट्स या वार्निंग्स को हाइलाइट करने के लिए परफेक्ट है। ऊपर का कोड पहले से ही `ACCENT_BORDER_CALLOUT_1` दिखाता है, आप `ShapeType` को किसी भी callout वैरिएंट में बदल सकते हैं ताकि आपके डिजाइन के अनुसार हो।

## SmartArt शेप्स के साथ काम करना

### SmartArt शेप्स का पता लगाना
SmartArt डायग्राम्स को प्रोग्रामेटिकली पहचान सकते हैं, जिससे आप उन्हें आवश्यकतानुसार प्रोसेस या रिप्लेस कर सकते हैं।

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### SmartArt ड्रॉइंग्स को अपडेट करना
एक बार पहचान लेने के बाद, आप डेटा में बदलाव को दर्शाने के लिए SmartArt ग्राफिक्स को रिफ्रेश कर सकते हैं।

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## सामान्य समस्याएँ और टिप्स
- **शेप नहीं दिख रहा:** सुनिश्चित करें कि शेप टार्गेट नोड के बाद `builder.insertNode` का उपयोग करके डाला गया है।  
- **अनपेक्षित घुमाव:** याद रखें कि घुमाव शेप के सेंटर के आसपास लागू होता है; आवश्यक होने पर `setLeft`/`setTop` को समायोजित करें।  
- **Aspect ratio लॉक्ड:** डिफ़ॉल्ट रूप से, कई शेप्स अपना aspect ratio लॉक कर देते हैं; फ्रीली स्ट्रेच करने के लिए `setAspectRatioLocked(false)` कॉल करें।  
- **SmartArt डिटेक्शन फेल:** सुनिश्चित करें कि आप Aspose.Words का वह वर्ज़न उपयोग कर रहे हैं जो SmartArt को सपोर्ट करता है (v24+).

## अक्सर पूछे जाने वाले प्रश्न

**प्रश्न: Aspose.Words for Java क्या है?**  
**उत्तर:** Aspose.Words for Java एक जावा लाइब्रेरी है जो डेवलपर्स को प्रोग्रामेटिकली Word डॉक्यूमेंट्स को बनाना, मॉडिफाई करना और कनवर्ट करना संभव बनाती है। यह विभिन्न फॉर्मैट्स में डॉक्यूमेंट्स के साथ काम करने के लिए फीचर्स और टूल्स की विस्तृत रेंज प्रदान करती है।

**प्रश्न: मैं Aspose.Words for Java कैसे डाउनलोड कर सकता हूँ?**  
**उत्तर:** आप इस लिंक का पालन करके Aspose वेबसाइट से Aspose.Words for Java डाउनलोड कर सकते हैं: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

**प्रश्न: डॉक्यूमेंट शेप्स का उपयोग करने के क्या लाभ हैं?**  
**उत्तर:** डॉक्यूमेंट शेप्स आपके डॉक्यूमेंट्स में विज़ुअल एलिमेंट्स और इंटरैक्टिविटी जोड़ते हैं, जिससे वे अधिक आकर्षक और जानकारीपूर्ण बनते हैं। शेप्स के साथ आप कॉलआउट्स, बटन, इमेजेज, वाटरमार्क्स आदि बना सकते हैं, जिससे कुल मिलाकर यूज़र एक्सपीरियंस बेहतर होता है।

**प्रश्न: क्या मैं शेप्स की उपस्थिति को कस्टमाइज़ कर सकता हूँ?**  
**उत्तर:** हाँ, आप शेप्स की प्रॉपर्टीज़ जैसे आकार, स्थिति, घुमाव, और फ़िल कलर को एडजस्ट करके उनकी उपस्थिति को कस्टमाइज़ कर सकते हैं। Aspose.Words for Java शेप कस्टमाइज़ेशन के लिए विस्तृत विकल्प प्रदान करता है।

**प्रश्न: क्या Aspose.Words for Java SmartArt के साथ संगत है?**  
**उत्तर:** हाँ, Aspose.Words for Java SmartArt शेप्स को सपोर्ट करता है, जिससे आप अपने डॉक्यूमेंट्स में कॉम्प्लेक्स डायग्राम्स और ग्राफिक्स के साथ काम कर सकते हैं।

---

**अंतिम अपडेट:** 2025-12-14  
**परीक्षित संस्करण:** Aspose.Words for Java 24.12 (latest)  
**लेखक:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}