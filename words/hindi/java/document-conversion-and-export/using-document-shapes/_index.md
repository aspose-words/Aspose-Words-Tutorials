---
date: 2026-02-16
description: Aspose.Words for Java का उपयोग करके टेक्स्ट बॉक्स बनाना, वॉटरमार्क शब्द
  जोड़ना, कई आकारों को समूहित करना, आकार का अनुपात सेट करना और टेबल सेल में आकार रखना
  सीखें।
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java में टेक्स्ट बॉक्स कैसे बनाएं और डॉक्यूमेंट शेप्स का उपयोग
  करें
url: /hi/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java में दस्तावेज़ आकारों का उपयोग

## Aspose.Words for Java में दस्तावेज़ आकारों के उपयोग का परिचय

इस व्यापक गाइड में, **आप सीखेंगे कि टेक्स्ट बॉक्स कैसे बनाएं** ऑब्जेक्ट्स और अन्य शक्तिशाली आकारों को Aspose.Words for Java के साथ कैसे बनाएं। आकार आपको Word दस्तावेज़ों को कॉलआउट, बटन, वॉटरमार्क, SmartArt और अधिक से समृद्ध करने की सुविधा देते हैं—जिससे वे दृश्य रूप से आकर्षक और इंटरैक्टिव बनते हैं। हम वास्तविक उदाहरणों के माध्यम से चलेंगे, सरल टेक्स्ट बॉक्स डालने से लेकर कई आकारों को समूहित करने, अनुपात सेट करने, और तालिका कोशिकाओं के भीतर आकार रखने तक।

## त्वरित उत्तर
- **टेक्स्ट बॉक्स जोड़ने का मुख्य तरीका क्या है?** Use `DocumentBuilder.insertShape(ShapeType.TEXT_BOX, …)`.
- **क्या मैं आकारों को समूहित कर सकता हूँ?** Yes – create a `GroupShape` and append child shapes.
- **मैं किसी आकार के अनुपात को लॉक या अनलॉक कैसे करूँ?** Call `shape.setAspectRatioLocked(true/false)`.
- **क्या आकार के साथ वॉटरमार्क जोड़ना संभव है?** Absolutely – insert a `Shape` with `TEXT_PLAIN_TEXT` and set its fill/stroke.
- **क्या SmartArt डायग्राम Aspose.Words के साथ काम करते हैं?** Yes – detect with `shape.hasSmartArt()` and update via `shape.updateSmartArtDrawing()`.

## टेक्स्ट बॉक्स क्या है और टेक्स्ट बॉक्स आकार क्यों बनाएं?

टेक्स्ट बॉक्स एक कंटेनर है जो स्वरूपित टेक्स्ट, छवियों या अन्य आकारों को रख सकता है। अपने ऑटोमेशन में **create text box** का उपयोग करने से आप पृष्ठ पर कहीं भी फ्लोटिंग कंटेंट रख सकते हैं, जो एनोटेशन, कॉलआउट या सजावटी तत्वों के लिए आदर्श है बिना मुख्य दस्तावेज़ प्रवाह को बदले।

## आकार कैसे जोड़ें

कोड में जाने से पहले, सुनिश्चित करें कि आपके प्रोजेक्ट में Aspose.Words for Java रेफ़रेंस किया गया है। यदि आपने अभी तक इसे नहीं जोड़ा है, तो आधिकारिक साइट से लाइब्रेरी डाउनलोड करें:

[Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### दस्तावेज़ में आकार जोड़ना

## एकाधिक आकारों को समूहित कैसे करें

`GroupShape` आपको कई व्यक्तिगत आकारों को एक इकाई के रूप में व्यवहार करने देता है—जो उन्हें साथ में स्थानांतरित या घुमाने के लिए उपयोगी है।

### GroupShape डालना

नीचे एक पूर्ण उदाहरण है जो एक समूह बनाता है, दो विभिन्न आकार जोड़ता है, और समूह को दस्तावेज़ में डालता है।

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

## टेक्स्ट बॉक्स कैसे बनाएं (create text box)

### टेक्स्ट बॉक्स आकार डालना

`insertShape` मेथड टेक्स्ट बॉक्स जोड़ना सरल बनाता है। नीचे का उदाहरण टेक्स्ट बॉक्स को स्थित करने और घुमाने के दो तरीके दिखाता है।

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

## आकार के अनुपात को कैसे सेट करें

### अनुपात प्रबंधन

कभी-कभी आपको आकार को उसकी मूल अनुपात को बनाए रखे बिना फैलाना पड़ता है। नीचे का स्निपेट इमेज आकार के अनुपात को अनलॉक करने का प्रदर्शन करता है।

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## आकार को तालिका सेल में कैसे रखें

### तालिका सेल के भीतर आकार रखना

नीचे एक चरण‑दर‑चरण उदाहरण है जो एक तालिका बनाता है, फिर एक वॉटरमार्क आकार डालता है जो पृष्ठ के सापेक्ष स्थित है लेकिन एक सेल के भीतर भी रखा जा सकता है।

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

## SmartArt आकारों के साथ काम करना

### SmartArt आकारों का पता लगाना

आप `hasSmartArt()` मेथड का उपयोग करके प्रोग्रामेटिकली दस्तावेज़ में SmartArt ऑब्जेक्ट्स खोज सकते हैं।

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### SmartArt ड्रॉइंग्स को अपडेट करना

एक बार जब आप SmartArt आकारों को ढूंढ लेते हैं, तो आप `updateSmartArtDrawing()` के साथ उनके आंतरिक ड्रॉइंग डेटा को रिफ्रेश कर सकते हैं।

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## निष्कर्ष

इस गाइड में, हमने **create text box** ऑब्जेक्ट्स बनाना, कई आकारों को समूहित करना, अनुपात समायोजित करना, तालिका कोशिकाओं के भीतर आकार एम्बेड करना, वॉटरमार्क जोड़ना, और Aspose.Words for Java का उपयोग करके SmartArt डायग्राम्स के साथ काम करना कवर किया है। ये तकनीकें आपको प्रोग्रामेटिकली समृद्ध रूप से स्वरूपित, इंटरैक्टिव Word दस्तावेज़ बनाने में सक्षम बनाती हैं।

## अक्सर पूछे जाने वाले प्रश्न

### Aspose.Words for Java क्या है?

Aspose.Words for Java एक Java लाइब्रेरी है जो डेवलपर्स को प्रोग्रामेटिकली Word दस्तावेज़ बनाने, संशोधित करने और परिवर्तित करने की अनुमति देती है। यह विभिन्न फ़ॉर्मेट में दस्तावेज़ों के साथ काम करने के लिए सुविधाओं और टूल्स की विस्तृत श्रृंखला प्रदान करती है।

### मैं Aspose.Words for Java कैसे डाउनलोड कर सकता हूँ?

आप Aspose वेबसाइट से इस लिंक का पालन करके Aspose.Words for Java डाउनलोड कर सकते हैं: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### दस्तावेज़ आकारों का उपयोग करने के क्या लाभ हैं?

दस्तावेज़ आकार आपके दस्तावेज़ों में दृश्य तत्व और इंटरैक्टिविटी जोड़ते हैं, जिससे वे अधिक आकर्षक और सूचनात्मक बनते हैं। आकारों के साथ आप कॉलआउट, बटन, छवियां, वॉटरमार्क और अधिक बना सकते हैं, जिससे कुल मिलाकर उपयोगकर्ता अनुभव बेहतर होता है।

### क्या मैं आकारों की उपस्थिति को कस्टमाइज़ कर सकता हूँ?

हां, आप आकारों की उपस्थिति को उनके गुण जैसे आकार, स्थिति, घूर्णन, और भराव रंग को समायोजित करके कस्टमाइज़ कर सकते हैं। Aspose.Words for Java आकार कस्टमाइज़ेशन के लिए विस्तृत विकल्प प्रदान करता है।

### क्या Aspose.Words for Java SmartArt के साथ संगत है?

हां, Aspose.Words for Java SmartArt आकारों का समर्थन करता है, जिससे आप अपने दस्तावेज़ों में जटिल डायग्राम और ग्राफिक्स के साथ काम कर सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न

**Q: क्या मैं एक ही आकार में टेक्स्ट बॉक्स को छवि के साथ संयोजित कर सकता हूँ?**  
A: हाँ। आकार बनाकर `builder.insertImage()` का उपयोग करके टेक्स्ट बॉक्स आकार में छवि डालें, फिर आवश्यकतानुसार उसका लेआउट समायोजित करें।

**Q: मैं कैसे सुनिश्चित करूँ कि वॉटरमार्क सभी दस्तावेज़ सामग्री के पीछे दिखाई दे?**  
A: आकार के `WrapType` को `NONE` सेट करें और उसके `RelativeHorizontalPosition` और `RelativeVerticalPosition` को `PAGE` पर सेट करें। इससे वॉटरमार्क मुख्य प्रवाह के पीछे स्थित हो जाता है।

**Q: क्या Word में समूहित आकार को एनीमेट करना संभव है?**  
A: जबकि Aspose.Words आकार बना और समूहित कर सकता है, एनीमेशन सुविधाएँ समर्थित नहीं हैं क्योंकि वे Word के UI क्षमताओं पर निर्भर करती हैं।

**Q: SmartArt समर्थन के लिए Aspose.Words का कौन सा संस्करण आवश्यक है?**  
A: SmartArt का पता लगाना और अपडेट करना Aspose.Words 20.9 for Java और उसके बाद के संस्करणों से उपलब्ध है।

**Q: क्या लाइब्रेरी कई आकारों वाले बड़े दस्तावेज़ों को कुशलता से संभालती है?**  
A: हाँ। कई आकारों वाले दस्तावेज़ों में प्रदर्शन सुधारने के लिए `doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010)` या उच्च संस्करण का उपयोग करें।

---

**अंतिम अपडेट:** 2026-02-16  
**परीक्षित संस्करण:** Aspose.Words for Java 24.12  
**लेखक:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}