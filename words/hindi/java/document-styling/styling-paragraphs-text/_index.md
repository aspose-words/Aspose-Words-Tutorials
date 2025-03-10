---
title: दस्तावेज़ों में पैराग्राफ़ और टेक्स्ट की स्टाइलिंग
linktitle: दस्तावेज़ों में पैराग्राफ़ और टेक्स्ट की स्टाइलिंग
second_title: Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई
description: Java के लिए Aspose.Words का उपयोग करके दस्तावेज़ों में पैराग्राफ़ और टेक्स्ट को स्टाइल करना सीखें। प्रभावी दस्तावेज़ फ़ॉर्मेटिंग के लिए स्रोत कोड के साथ चरण-दर-चरण मार्गदर्शिका।
weight: 11
url: /hi/java/document-styling/styling-paragraphs-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# दस्तावेज़ों में पैराग्राफ़ और टेक्स्ट की स्टाइलिंग

## परिचय

जब जावा में प्रोग्रामेटिक रूप से दस्तावेज़ों में हेरफेर और फ़ॉर्मेटिंग की बात आती है, तो जावा के लिए Aspose.Words डेवलपर्स के बीच एक शीर्ष विकल्प है। यह शक्तिशाली API आपको अपने दस्तावेज़ों में पैराग्राफ़ और टेक्स्ट को आसानी से बनाने, संपादित करने और स्टाइल करने की अनुमति देता है। इस व्यापक गाइड में, हम आपको जावा के लिए Aspose.Words का उपयोग करके पैराग्राफ़ और टेक्स्ट को स्टाइल करने की प्रक्रिया से अवगत कराएँगे। चाहे आप एक अनुभवी डेवलपर हों या अभी शुरुआत कर रहे हों, स्रोत कोड के साथ यह चरण-दर-चरण मार्गदर्शिका आपको दस्तावेज़ फ़ॉर्मेटिंग में महारत हासिल करने के लिए आवश्यक ज्ञान और कौशल से लैस करेगी। आइए शुरू करते हैं!

## जावा के लिए Aspose.Words को समझना

Aspose.Words for Java एक जावा लाइब्रेरी है जो डेवलपर्स को Microsoft Word की आवश्यकता के बिना Word दस्तावेज़ों के साथ काम करने में सक्षम बनाती है। यह दस्तावेज़ निर्माण, हेरफेर और स्वरूपण के लिए कई प्रकार की सुविधाएँ प्रदान करता है। Aspose.Words for Java के साथ, आप रिपोर्ट, चालान, अनुबंध और बहुत कुछ के निर्माण को स्वचालित कर सकते हैं, जिससे यह व्यवसायों और डेवलपर्स के लिए एक अमूल्य उपकरण बन जाता है।

## अपना विकास वातावरण स्थापित करना

कोडिंग पहलुओं में गोता लगाने से पहले, अपने विकास वातावरण को सेट करना महत्वपूर्ण है। सुनिश्चित करें कि आपके पास जावा स्थापित है, और फिर Aspose.Words for Java लाइब्रेरी को डाउनलोड और कॉन्फ़िगर करें। आप विस्तृत इंस्टॉलेशन निर्देश यहाँ पा सकते हैं[प्रलेखन](https://reference.aspose.com/words/java/).

## नया दस्तावेज़ बनाना

आइए Aspose.Words for Java का उपयोग करके एक नया दस्तावेज़ बनाकर शुरू करें। नीचे आपको आरंभ करने के लिए एक सरल कोड स्निपेट दिया गया है:

```java
// नया दस्तावेज़ बनाएँ
Document doc = new Document();

// दस्तावेज़ सहेजें
doc.save("NewDocument.docx");
```

यह कोड एक रिक्त वर्ड दस्तावेज़ बनाता है और इसे "NewDocument.docx" के रूप में सहेजता है। आप सामग्री और स्वरूपण जोड़कर दस्तावेज़ को और भी अनुकूलित कर सकते हैं।

## पैराग्राफ जोड़ना और प्रारूपित करना

पैराग्राफ किसी भी दस्तावेज़ के निर्माण खंड हैं। आप पैराग्राफ जोड़ सकते हैं और उन्हें आवश्यकतानुसार प्रारूपित कर सकते हैं। पैराग्राफ जोड़ने और उनका संरेखण सेट करने का एक उदाहरण यहां दिया गया है:

```java
// नया दस्तावेज़ बनाएँ
Document doc = new Document();

// एक पैराग्राफ़ बनाएँ
Paragraph para = new Paragraph(doc);

// पैराग्राफ का संरेखण सेट करें
para.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

// पैराग्राफ़ में पाठ जोड़ें
Run run = new Run(doc, "This is a centered paragraph.");
para.appendChild(run);

// दस्तावेज़ में पैराग्राफ़ जोड़ें
doc.getFirstSection().getBody().appendChild(para);

// दस्तावेज़ सहेजें
doc.save("FormattedDocument.docx");
```

यह कोड स्निपेट "यह एक केंद्रित पैराग्राफ़ है" टेक्स्ट के साथ एक केंद्रित पैराग्राफ़ बनाता है। आप इच्छित फ़ॉर्मेटिंग प्राप्त करने के लिए फ़ॉन्ट, रंग और बहुत कुछ अनुकूलित कर सकते हैं।

## पैराग्राफ़ के भीतर टेक्स्ट की स्टाइलिंग

पैराग्राफ़ के भीतर अलग-अलग टेक्स्ट को फ़ॉर्मेट करना एक आम ज़रूरत है। Aspose.Words for Java आपको आसानी से टेक्स्ट को स्टाइल करने की सुविधा देता है। यहाँ टेक्स्ट का फ़ॉन्ट और रंग बदलने का एक उदाहरण दिया गया है:

```java
// नया दस्तावेज़ बनाएँ
Document doc = new Document();

// एक पैराग्राफ़ बनाएँ
Paragraph para = new Paragraph(doc);

// अलग-अलग स्वरूपण के साथ पाठ जोड़ें
Run run = new Run(doc, "This is ");
run.getFont().setName("Arial");
run.getFont().setSize(14);
para.appendChild(run);

Run coloredRun = new Run(doc, "colored text.");
coloredRun.getFont().setColor(Color.RED);
para.appendChild(coloredRun);

// दस्तावेज़ में पैराग्राफ़ जोड़ें
doc.getFirstSection().getBody().appendChild(para);

// दस्तावेज़ सहेजें
doc.save("StyledTextDocument.docx");
```

इस उदाहरण में, हम पाठ के साथ एक पैराग्राफ बनाते हैं, और फिर हम फ़ॉन्ट और रंग बदलकर पाठ के एक हिस्से को अलग ढंग से स्टाइल करते हैं।

## शैलियाँ और स्वरूपण लागू करना

Aspose.Words for Java पूर्वनिर्धारित शैलियाँ प्रदान करता है जिन्हें आप पैराग्राफ़ और टेक्स्ट पर लागू कर सकते हैं। यह फ़ॉर्मेटिंग प्रक्रिया को सरल बनाता है। यहाँ बताया गया है कि पैराग्राफ़ पर स्टाइल कैसे लागू करें:

```java
// नया दस्तावेज़ बनाएँ
Document doc = new Document();

// एक पैराग्राफ़ बनाएँ
Paragraph para = new Paragraph(doc);

// पूर्वनिर्धारित शैली लागू करें
para.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);

// पैराग्राफ़ में पाठ जोड़ें
Run run = new Run(doc, "Heading 1 Style");
para.appendChild(run);

// दस्तावेज़ में पैराग्राफ़ जोड़ें
doc.getFirstSection().getBody().appendChild(para);

// दस्तावेज़ सहेजें
doc.save("StyledDocument.docx");
```

इस कोड में, हम एक पैराग्राफ पर "शीर्षक 1" शैली लागू करते हैं, जो स्वचालित रूप से इसे पूर्वनिर्धारित शैली के अनुसार प्रारूपित करता है।

## फ़ॉन्ट और रंगों के साथ काम करना

टेक्स्ट के स्वरूप को बेहतर बनाने में अक्सर फ़ॉन्ट और रंगों को संशोधित करना शामिल होता है। जावा के लिए Aspose.Words फ़ॉन्ट और रंग प्रबंधन के लिए व्यापक विकल्प प्रदान करता है। फ़ॉन्ट आकार और रंग बदलने का एक उदाहरण यहां दिया गया है:

```java
// नया दस्तावेज़ बनाएँ
Document doc = new Document();

// एक पैराग्राफ़ बनाएँ
Paragraph para = new Paragraph(doc);

// कस्टम फ़ॉन्ट आकार और रंग के साथ पाठ जोड़ें
Run run = new Run(doc, "Customized Text");
run.getFont().setSize(18); // फ़ॉन्ट आकार 18 पॉइंट पर सेट करें
run.getFont().setColor(Color.BLUE); // टेक्स्ट का रंग नीला सेट करें

para.appendChild(run);

// दस्तावेज़ में पैराग्राफ़ जोड़ें
doc.getFirstSection().getBody().appendChild(para);

// दस्तावेज़ सहेजें
doc.save("FontAndColorDocument.docx");
```

इस कोड में, हम पैराग्राफ के भीतर पाठ के फ़ॉन्ट आकार और रंग को अनुकूलित करते हैं।

## संरेखण और रिक्ति का प्रबंधन

पैराग्राफ़ और टेक्स्ट के संरेखण और स्पेसिंग को नियंत्रित करना दस्तावेज़ लेआउट के लिए ज़रूरी है। संरेखण और स्पेसिंग को समायोजित करने का तरीका इस प्रकार है:

```java
// नया दस्तावेज़ बनाएँ
Document doc = new Document();

// एक पैराग्राफ़ बनाएँ
Paragraph para = new Paragraph(doc);

// पैराग्राफ संरेखण सेट करें
para.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);

// स्पेसिंग के साथ टेक्स्ट जोड़ें
Run run = new Run(doc, "Right-aligned text with spacing.");
para.appendChild(run);

// पैराग्राफ़ के पहले और बाद में स्पेस जोड़ें
para.getParagraphFormat().setSpaceBefore(10); // 10 अंक पहले
para.getParagraphFormat().setSpaceAfter(10);  // 10 अंक के बाद

// दस्तावेज़ में पैराग्राफ़ जोड़ें
doc.getFirstSection().getBody().appendChild(para);

// दस्तावेज़ सहेजें
doc.save("AlignmentAndSpacingDocument.docx");
```

इस उदाहरण में, हमने पैराग्राफ का संरेखण इस प्रकार सेट किया है

 दाएं संरेखित करें और पैराग्राफ के पहले और बाद में रिक्त स्थान जोड़ें।

## सूचियों और बुलेट्स को संभालना

बुलेट या नंबरिंग के साथ सूचियाँ बनाना एक सामान्य दस्तावेज़ स्वरूपण कार्य है। जावा के लिए Aspose.Words इसे सरल बनाता है। बुलेटेड सूची बनाने का तरीका यहाँ बताया गया है:

```java
List list = doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
builder.getListFormat().setList(list);
builder.writeln("Item 1");
builder.writeln("Item 2");
builder.writeln("Item 3");
```

इस कोड में, हम तीन आइटमों वाली बुलेटेड सूची बनाते हैं।

## हाइपरलिंक्स सम्मिलित करना

हाइपरलिंक आपके दस्तावेज़ों में अन्तरक्रियाशीलता जोड़ने के लिए आवश्यक हैं। Aspose.Words for Java आपको हाइपरलिंक आसानी से डालने की अनुमति देता है। यहाँ एक उदाहरण दिया गया है:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

builder.write("For more information, please visit the ");

// एक हाइपरलिंक डालें और उसे कस्टम फ़ॉर्मेटिंग के साथ ज़ोर दें।
// हाइपरलिंक एक क्लिक करने योग्य पाठ होगा जो हमें URL में निर्दिष्ट स्थान पर ले जाएगा।
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Google website", "https://www.google.com", गलत);
builder.getFont().clearFormatting();
builder.writeln(".");

// माइक्रोसॉफ्ट वर्ड में टेक्स्ट में दिए गए लिंक पर Ctrl + बायाँ-क्लिक करने से हम एक नए वेब ब्राउज़र विंडो के माध्यम से URL पर पहुँच जाएँगे।
doc.save("InsertHyperlink.docx");
```

यह कोड "Visit Example.com" पाठ के साथ "https://www.example.com" के लिए एक हाइपरलिंक सम्मिलित करता है।

## छवियाँ और आकृतियाँ जोड़ना

दस्तावेज़ों में अक्सर छवियों और आकृतियों जैसे दृश्य तत्वों की आवश्यकता होती है। Aspose.Words for Java आपको छवियों और आकृतियों को सहजता से सम्मिलित करने में सक्षम बनाता है। यहाँ बताया गया है कि छवि कैसे जोड़ें:

```java
builder.insertImage("path/to/your/image.png");
```

इस कोड में, हम एक फ़ाइल से एक छवि लोड करते हैं और इसे दस्तावेज़ में सम्मिलित करते हैं।

## पेज लेआउट और मार्जिन

अपने दस्तावेज़ के पेज लेआउट और मार्जिन को नियंत्रित करना वांछित स्वरूप प्राप्त करने के लिए महत्वपूर्ण है। पेज मार्जिन सेट करने का तरीका यहां बताया गया है:

```java
// नया दस्तावेज़ बनाएँ
Document doc = new Document();

// पेज मार्जिन सेट करें (पॉइंट में)
PageSetup pageSetup = doc.getFirstSection().getPageSetup();
pageSetup.setLeftMargin(72);   // 1 इंच (72 अंक)
pageSetup.setRightMargin(72);  // 1 इंच (72 अंक)
pageSetup.setTopMargin(72);    // 1 इंच (72 अंक)
pageSetup.setBottomMargin(72); // 1 इंच (72 अंक)

// दस्तावेज़ में सामग्री जोड़ें
// ...

// दस्तावेज़ सहेजें
doc.save("PageLayoutDocument.docx");
```

इस उदाहरण में, हमने पृष्ठ के सभी तरफ 1 इंच का बराबर मार्जिन निर्धारित किया है।

## शीर्षक और पृष्ठांक

हेडर और फ़ुटर आपके दस्तावेज़ के प्रत्येक पृष्ठ पर सुसंगत जानकारी जोड़ने के लिए आवश्यक हैं। हेडर और फ़ुटर के साथ काम करने का तरीका यहां बताया गया है:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

builder.moveToHeaderFooter(HeaderFooterType.HEADER_PRIMARY);
builder.write("Header Text");
builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);

builder.write("Page Number: ");
builder.insertField(FieldType.FIELD_PAGE, true);

// दस्तावेज़ मुख्य भाग में सामग्री जोड़ें.
// ...

// दस्तावेज़ सहेजें.
doc.save("HeaderFooterDocument.docx");
```

इस कोड में, हम दस्तावेज़ के शीर्षलेख और पादलेख दोनों में सामग्री जोड़ते हैं।

## तालिकाओं के साथ कार्य करना

टेबल आपके दस्तावेज़ों में डेटा को व्यवस्थित करने और प्रस्तुत करने का एक शक्तिशाली तरीका है। जावा के लिए Aspose.Words टेबल के साथ काम करने के लिए व्यापक समर्थन प्रदान करता है। यहाँ टेबल बनाने का एक उदाहरण दिया गया है:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

builder.startTable();

builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

builder.insertCell();
builder.write("Row 1, Col 1");

builder.insertCell();
builder.write("Row 1, Col 2");
builder.endRow();

// स्वरूपण बदलने से यह वर्तमान सेल पर लागू हो जाएगा,
// और कोई भी नई कोशिकाएँ जो हम बाद में बिल्डर के साथ बनाते हैं।
// इससे उन कोशिकाओं पर कोई प्रभाव नहीं पड़ेगा जिन्हें हमने पहले जोड़ा है।
builder.getCellFormat().getShading().clearFormatting();

builder.insertCell();
builder.write("Row 2, Col 1");

builder.insertCell();
builder.write("Row 2, Col 2");

builder.endRow();

// ऊर्ध्वाधर पाठ को फिट करने के लिए पंक्ति की ऊंचाई बढ़ाएँ.
builder.insertCell();
builder.getRowFormat().setHeight(150.0);
builder.getCellFormat().setOrientation(TextOrientation.UPWARD);
builder.write("Row 3, Col 1");

builder.insertCell();
builder.getCellFormat().setOrientation(TextOrientation.DOWNWARD);
builder.write("Row 3, Col 2");

builder.endRow();
builder.endTable();
```

इस कोड में, हम तीन पंक्तियों और तीन स्तंभों वाली एक सरल तालिका बनाते हैं।

## दस्तावेज़ सहेजना और निर्यात करना

एक बार जब आप अपना दस्तावेज़ बना लेते हैं और उसे फ़ॉर्मेट कर लेते हैं, तो उसे अपने इच्छित फ़ॉर्मेट में सहेजना या निर्यात करना ज़रूरी होता है। Aspose.Words for Java विभिन्न दस्तावेज़ फ़ॉर्मेट का समर्थन करता है, जिसमें DOCX, PDF और अन्य शामिल हैं। यहाँ बताया गया है कि दस्तावेज़ को PDF के रूप में कैसे सहेजा जाए:

```java
// नया दस्तावेज़ बनाएँ
Document doc = new Document();

// दस्तावेज़ में सामग्री जोड़ें
// ...

// दस्तावेज़ को PDF के रूप में सहेजें
doc.save("Document.pdf");
```

यह कोड स्निपेट दस्तावेज़ को PDF फ़ाइल के रूप में सहेजता है।

## उन्नत विशेषताएँ

Aspose.Words for Java जटिल दस्तावेज़ हेरफेर के लिए उन्नत सुविधाएँ प्रदान करता है। इनमें मेल मर्ज, दस्तावेज़ तुलना, और बहुत कुछ शामिल है। इन उन्नत विषयों पर गहन मार्गदर्शन के लिए दस्तावेज़ देखें।

## सुझाव और सर्वोत्तम अभ्यास

- आसान रखरखाव के लिए अपने कोड को मॉड्यूलर और सुव्यवस्थित रखें।
- जटिल तर्क को समझाने और कोड की पठनीयता में सुधार करने के लिए टिप्पणियों का उपयोग करें।
- अद्यतनों और अतिरिक्त संसाधनों के लिए नियमित रूप से Aspose.Words for Java दस्तावेज़ देखें।

## सामान्य समस्याओं का निवारण

Aspose.Words for Java के साथ काम करते समय कोई समस्या आ रही है? सामान्य समस्याओं के समाधान के लिए सहायता फ़ोरम और दस्तावेज़ देखें।

## अक्सर पूछे जाने वाले प्रश्न (एफएक्यू)

### मैं अपने दस्तावेज़ में पृष्ठ विराम कैसे जोड़ूँ?
अपने दस्तावेज़ में पृष्ठ विराम जोड़ने के लिए, आप निम्नलिखित कोड का उपयोग कर सकते हैं:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// पृष्ठ विराम डालें
builder.insertBreak(BreakType.PAGE_BREAK);

// दस्तावेज़ में सामग्री जोड़ना जारी रखें
```

### क्या मैं Java के लिए Aspose.Words का उपयोग करके किसी दस्तावेज़ को PDF में परिवर्तित कर सकता हूँ?
हां, आप आसानी से Aspose.Words for Java का उपयोग करके किसी दस्तावेज़ को PDF में बदल सकते हैं। यहाँ एक उदाहरण दिया गया है:

```java
Document doc = new Document("input.docx");
doc.save("output.pdf");
```

### मैं टेक्स्ट को किस प्रकार फ़ॉर्मेट करूँ?

 बोल्ड या इटैलिक?
पाठ को बोल्ड या इटैलिक स्वरूपित करने के लिए आप निम्नलिखित कोड का उपयोग कर सकते हैं:

```java
Run run = new Run(doc, "Bold and Italic Text");
run.getFont().setBold(true);    // टेक्स्ट को बोल्ड करें
run.getFont().setItalic(true);  // पाठ को इटैलिक बनाएं
```

### Java के लिए Aspose.Words का नवीनतम संस्करण क्या है?
आप Java के लिए Aspose.Words के नवीनतम संस्करण के लिए Aspose वेबसाइट या Maven रिपोजिटरी की जांच कर सकते हैं।

### क्या Aspose.Words for Java, Java 11 के साथ संगत है?
हां, Aspose.Words for Java, Java 11 और बाद के संस्करणों के साथ संगत है।

### मैं अपने दस्तावेज़ के विशिष्ट अनुभागों के लिए पृष्ठ मार्जिन कैसे निर्धारित कर सकता हूँ?
 आप अपने दस्तावेज़ के विशिष्ट अनुभागों के लिए पृष्ठ मार्जिन सेट कर सकते हैं`PageSetup` क्लास। यहाँ एक उदाहरण है:

```java
Section section = doc.getSections().get(0); // पहला भाग प्राप्त करें
PageSetup pageSetup = section.getPageSetup();
pageSetup.setLeftMargin(72);   // बायां मार्जिन अंकों में
pageSetup.setRightMargin(72);  // दायाँ मार्जिन (पॉइंट में)
pageSetup.setTopMargin(72);    // अंकों में शीर्ष अंतर
pageSetup.setBottomMargin(72); // अंकों में निचला मार्जिन
```

## निष्कर्ष

इस व्यापक गाइड में, हमने दस्तावेज़ों में पैराग्राफ़ और टेक्स्ट को स्टाइल करने के लिए Aspose.Words for Java की शक्तिशाली क्षमताओं का पता लगाया है। आपने सीखा है कि बुनियादी टेक्स्ट हेरफेर से लेकर उन्नत सुविधाओं तक, अपने दस्तावेज़ों को प्रोग्रामेटिक रूप से कैसे बनाएँ, फ़ॉर्मेट करें और बेहतर बनाएँ। Aspose.Words for Java डेवलपर्स को दस्तावेज़ फ़ॉर्मेटिंग कार्यों को कुशलतापूर्वक स्वचालित करने में सक्षम बनाता है। Aspose.Words for Java के साथ दस्तावेज़ स्टाइलिंग में कुशल बनने के लिए विभिन्न सुविधाओं के साथ अभ्यास और प्रयोग करते रहें।

अब जब आपको Aspose.Words for Java का उपयोग करके दस्तावेज़ों में पैराग्राफ़ और टेक्स्ट को स्टाइल करने के बारे में ठोस समझ हो गई है, तो आप अपनी विशिष्ट आवश्यकताओं के अनुरूप सुंदर स्वरूपित दस्तावेज़ बनाने के लिए तैयार हैं। हैप्पी कोडिंग!
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
