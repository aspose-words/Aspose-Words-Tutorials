---
"description": "Aspose.Words के साथ Java के लिए दस्तावेज़ निर्माण में महारत हासिल करें। टेक्स्ट, टेबल, इमेज और बहुत कुछ जोड़ने के लिए चरण-दर-चरण मार्गदर्शिका। आसानी से शानदार Word दस्तावेज़ बनाएँ।"
"linktitle": "डॉक्यूमेंटबिल्डर का उपयोग करके सामग्री जोड़ना"
"second_title": "Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई"
"title": "Java के लिए Aspose.Words में DocumentBuilder का उपयोग करके सामग्री जोड़ना"
"url": "/hi/java/document-manipulation/adding-content-using-documentbuilder/"
"weight": 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java के लिए Aspose.Words में DocumentBuilder का उपयोग करके सामग्री जोड़ना


## Aspose.Words for Java में DocumentBuilder का उपयोग करके सामग्री जोड़ने का परिचय

इस चरण-दर-चरण मार्गदर्शिका में, हम यह पता लगाएंगे कि Word दस्तावेज़ में विभिन्न प्रकार की सामग्री जोड़ने के लिए Aspose.Words for Java के DocumentBuilder का उपयोग कैसे करें। हम टेक्स्ट, टेबल, क्षैतिज नियम, फ़ॉर्म फ़ील्ड, HTML, हाइपरलिंक, सामग्री की तालिका, इनलाइन और फ़्लोटिंग इमेज, पैराग्राफ़ और बहुत कुछ सम्मिलित करना कवर करेंगे। चलिए शुरू करते हैं!

## आवश्यक शर्तें

शुरू करने से पहले, सुनिश्चित करें कि आपके प्रोजेक्ट में Aspose.Words for Java लाइब्रेरी सेट अप है। आप इसे यहाँ से डाउनलोड कर सकते हैं [यहाँ](https://releases.aspose.com/words/java/).

## पाठ जोड़ना

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// एक सरल पाठ पैराग्राफ डालें
builder.write("This is a simple text paragraph.");

// दस्तावेज़ सहेजें
doc.save("path/to/your/document.docx");
```

## तालिकाएँ जोड़ना

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// तालिका प्रारंभ करें
Table table = builder.startTable();

// कक्ष और सामग्री सम्मिलित करें
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// तालिका समाप्त करें
builder.endTable();

// दस्तावेज़ सहेजें
doc.save("path/to/your/document.docx");
```

## क्षैतिज नियम जोड़ना

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// क्षैतिज नियम डालें
builder.insertHorizontalRule();

// दस्तावेज़ सहेजें
doc.save("path/to/your/document.docx");
```

## फॉर्म फ़ील्ड जोड़ना

### टेक्स्ट इनपुट फॉर्म फ़ील्ड

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// टेक्स्ट इनपुट फ़ॉर्म फ़ील्ड डालें
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// दस्तावेज़ सहेजें
doc.save("path/to/your/document.docx");
```

### चेक बॉक्स फॉर्म फ़ील्ड

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// चेक बॉक्स फ़ॉर्म फ़ील्ड डालें
builder.insertCheckBox("CheckBox", true, true, 0);

// दस्तावेज़ सहेजें
doc.save("path/to/your/document.docx");
```

### कॉम्बो बॉक्स फॉर्म फ़ील्ड

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// कॉम्बो बॉक्स के लिए आइटम परिभाषित करें
String[] items = { "Option 1", "Option 2", "Option 3" };

// कॉम्बो बॉक्स फॉर्म फ़ील्ड डालें
builder.insertComboBox("DropDown", items, 0);

// दस्तावेज़ सहेजें
doc.save("path/to/your/document.docx");
```

## HTML जोड़ना

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// HTML सामग्री डालें
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// दस्तावेज़ सहेजें
doc.save("path/to/your/document.docx");
```

## हाइपरलिंक जोड़ना

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// हाइपरलिंक डालें
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", गलत);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// दस्तावेज़ सहेजें
doc.save("path/to/your/document.docx");
```

## विषय-सूची जोड़ना

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// विषय सूची डालें
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// दस्तावेज़ सामग्री जोड़ें
// ...

// विषय-सूची को अद्यतन करें
doc.updateFields();

// दस्तावेज़ सहेजें
doc.save("path/to/your/document.docx");
```

## छवियाँ जोड़ना

### इनलाइन छवि

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// इनलाइन छवि डालें
builder.insertImage("path/to/your/image.png");

// दस्तावेज़ सहेजें
doc.save("path/to/your/document.docx");
```

### तैरती हुई छवि

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// एक फ़्लोटिंग छवि डालें
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// दस्तावेज़ सहेजें
doc.save("path/to/your/document.docx");
```

## पैराग्राफ जोड़ना

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// पैराग्राफ़ फ़ॉर्मेटिंग सेट करें
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// एक पैराग्राफ डालें
builder.writeln("This is a formatted paragraph.");

// दस्तावेज़ सहेजें
doc.save("path/to/your/document.docx");
```

## चरण 10: कर्सर को ले जाना

आप विभिन्न तरीकों का उपयोग करके दस्तावेज़ के भीतर कर्सर की स्थिति को नियंत्रित कर सकते हैं जैसे `moveToParagraph`, `moveToCell`, और भी बहुत कुछ। यहाँ एक उदाहरण है:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// कर्सर को किसी विशिष्ट पैराग्राफ़ पर ले जाएँ
builder.moveToParagraph(2, 0);

// नए कर्सर स्थान पर सामग्री जोड़ें
builder.writeln("This is the 3rd paragraph.");
```

ये कुछ सामान्य ऑपरेशन हैं जिन्हें आप Aspose.Words for Java के DocumentBuilder का उपयोग करके कर सकते हैं। अधिक उन्नत सुविधाओं और अनुकूलन विकल्पों के लिए लाइब्रेरी के दस्तावेज़ देखें। दस्तावेज़ निर्माण की शुभकामनाएँ!


## निष्कर्ष

इस विस्तृत गाइड में, हमने Word दस्तावेज़ों में विभिन्न प्रकार की सामग्री जोड़ने के लिए Aspose.Words for Java के DocumentBuilder की क्षमताओं का पता लगाया है। हमने टेक्स्ट, टेबल, क्षैतिज नियम, फ़ॉर्म फ़ील्ड, HTML, हाइपरलिंक, सामग्री की तालिका, छवियाँ, पैराग्राफ़ और कर्सर मूवमेंट को कवर किया है।

## अक्सर पूछे जाने वाले प्रश्न

### प्रश्न: Java के लिए Aspose.Words क्या है?

उत्तर: Aspose.Words for Java एक जावा लाइब्रेरी है जो डेवलपर्स को प्रोग्रामेटिक रूप से Microsoft Word दस्तावेज़ बनाने, संशोधित करने और हेरफेर करने की अनुमति देती है। यह दस्तावेज़ निर्माण, स्वरूपण और सामग्री प्रविष्टि के लिए कई प्रकार की सुविधाएँ प्रदान करता है।

### प्रश्न: मैं अपने दस्तावेज़ में विषय-सूची कैसे जोड़ सकता हूँ?

उत्तर: विषय सूची जोड़ने के लिए, का उपयोग करें `DocumentBuilder` अपने दस्तावेज़ में विषय-सूची फ़ील्ड सम्मिलित करने के लिए। विषय-सूची को भरने के लिए विषय-सूची जोड़ने के बाद दस्तावेज़ में फ़ील्ड को अपडेट करना सुनिश्चित करें। यहाँ एक उदाहरण दिया गया है:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// विषय-सूची फ़ील्ड सम्मिलित करें
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// दस्तावेज़ सामग्री जोड़ें
// ...

// विषय-सूची को अद्यतन करें
doc.updateFields();
```

### प्रश्न: मैं Java के लिए Aspose.Words का उपयोग करके दस्तावेज़ में छवियाँ कैसे सम्मिलित करूँ?

उत्तर: आप इनलाइन और फ्लोटिंग दोनों तरह की छवियों को सम्मिलित कर सकते हैं। `DocumentBuilder`यहां दोनों के उदाहरण दिए गए हैं:

#### इनलाइन छवि:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// इनलाइन छवि डालें
builder.insertImage("path/to/your/image.png");
```

#### अस्थायी छवि:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// एक फ़्लोटिंग छवि डालें
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### प्रश्न: क्या मैं सामग्री जोड़ते समय पाठ और पैराग्राफ को प्रारूपित कर सकता हूँ?

उत्तर: हां, आप इसका उपयोग करके पाठ और पैराग्राफ को प्रारूपित कर सकते हैं `DocumentBuilder`. आप फ़ॉन्ट गुण, पैराग्राफ़ संरेखण, इंडेंटेशन और बहुत कुछ सेट कर सकते हैं। यहाँ एक उदाहरण दिया गया है:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// फ़ॉन्ट और पैराग्राफ़ फ़ॉर्मेटिंग सेट करें
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// एक प्रारूपित पैराग्राफ़ डालें
builder.writeln("This is a formatted paragraph.");
```

### प्रश्न: मैं दस्तावेज़ के भीतर कर्सर को किसी विशिष्ट स्थान पर कैसे ले जा सकता हूँ?

उत्तर: आप निम्न विधियों का उपयोग करके कर्सर की स्थिति को नियंत्रित कर सकते हैं `moveToParagraph`, `moveToCell`, और भी बहुत कुछ। यहाँ एक उदाहरण है:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// कर्सर को किसी विशिष्ट पैराग्राफ़ पर ले जाएँ
builder.moveToParagraph(2, 0);

// नए कर्सर स्थान पर सामग्री जोड़ें
builder.writeln("This is the 3rd paragraph.");
```

ये कुछ सामान्य प्रश्न और उत्तर हैं जो आपको Aspose.Words for Java के DocumentBuilder के साथ आरंभ करने में सहायता करेंगे। यदि आपके पास और प्रश्न हैं या आपको और सहायता की आवश्यकता है, तो देखें [पुस्तकालय का दस्तावेज़ीकरण](https://reference.aspose.com/words/java/) या Aspose.Words समुदाय और समर्थन संसाधनों से मदद लें।


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}