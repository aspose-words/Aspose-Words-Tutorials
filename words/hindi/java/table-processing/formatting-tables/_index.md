---
"description": "Aspose.Words for Java का उपयोग करके दस्तावेज़ों में तालिकाओं को फ़ॉर्मेट करने की कला में महारत हासिल करें। सटीक तालिका फ़ॉर्मेटिंग के लिए चरण-दर-चरण मार्गदर्शन और स्रोत कोड उदाहरणों का अन्वेषण करें।"
"linktitle": "दस्तावेज़ों में तालिकाओं का प्रारूपण"
"second_title": "Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई"
"title": "दस्तावेज़ों में तालिकाओं का प्रारूपण"
"url": "/hi/java/table-processing/formatting-tables/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# दस्तावेज़ों में तालिकाओं का प्रारूपण

## परिचय

क्या आप आसानी से जावा के लिए Aspose.Words का उपयोग करके Word दस्तावेज़ों में टेबल बनाने के लिए तैयार हैं? डेटा को व्यवस्थित करने के लिए टेबल बहुत ज़रूरी हैं, और इस शक्तिशाली लाइब्रेरी के साथ, आप अपने Word दस्तावेज़ों में प्रोग्रामेटिक रूप से टेबल बना सकते हैं, पॉपुलेट कर सकते हैं और नेस्ट भी कर सकते हैं। इस चरण-दर-चरण मार्गदर्शिका में, हम टेबल बनाने, सेल मर्ज करने और नेस्टेड टेबल जोड़ने का तरीका जानेंगे।

## आवश्यक शर्तें

कोडिंग शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित चीजें हैं:

- आपके सिस्टम पर जावा डेवलपमेंट किट (JDK) स्थापित है।
- जावा लाइब्रेरी के लिए Aspose.Words. [यहाँ पर डाउनलोड करो](https://releases.aspose.com/words/java/).
- जावा प्रोग्रामिंग की बुनियादी समझ.
- एक IDE जैसे IntelliJ IDEA, Eclipse, या कोई अन्य जिससे आप सहज हों।
- ए [अस्थायी लाइसेंस](https://purchase.aspose.com/temporary-license/) Aspose.Words की पूर्ण क्षमताओं को अनलॉक करने के लिए.

## पैकेज आयात करें

Java के लिए Aspose.Words का उपयोग करने के लिए, आपको आवश्यक क्लास और पैकेज आयात करने होंगे। इन आयातों को अपनी Java फ़ाइल के शीर्ष पर जोड़ें:

```java
import com.aspose.words.*;
```

आइये इस प्रक्रिया को छोटे-छोटे चरणों में विभाजित करें ताकि इसका अनुसरण करना बेहद आसान हो जाए।

## चरण 1: दस्तावेज़ और तालिका बनाएँ

सबसे पहले आपको क्या चाहिए? काम करने के लिए एक दस्तावेज़!

एक नया वर्ड डॉक्यूमेंट और एक टेबल बनाकर शुरू करें। टेबल को डॉक्यूमेंट के मुख्य भाग में जोड़ें।

```java
Document doc = new Document();
Table table = new Table(doc);
doc.getFirstSection().getBody().appendChild(table);
```

- `Document`: वर्ड दस्तावेज़ का प्रतिनिधित्व करता है.
- `Table`: एक रिक्त तालिका बनाता है.
- `appendChild`: दस्तावेज़ के मुख्य भाग में तालिका जोड़ता है.

## चरण 2: तालिका में पंक्तियाँ और कक्ष जोड़ें

बिना पंक्तियों और कक्षों वाली टेबल? यह बिना पहियों वाली कार की तरह है! चलिए इसे ठीक करते हैं।

```java
Row firstRow = new Row(doc);
table.appendChild(firstRow);

Cell firstCell = new Cell(doc);
firstRow.appendChild(firstCell);
```

- `Row`: तालिका में एक पंक्ति का प्रतिनिधित्व करता है.
- `Cell`: पंक्ति में एक सेल का प्रतिनिधित्व करता है.
- `appendChild`: तालिका में पंक्तियाँ और कक्ष जोड़ता है.

## चरण 3: सेल में टेक्स्ट जोड़ें

अब समय आ गया है कि हम अपनी मेज पर कुछ व्यक्तित्व जोड़ें!

```java
Paragraph paragraph = new Paragraph(doc);
firstCell.appendChild(paragraph);

Run run = new Run(doc, "Hello world!");
paragraph.appendChild(run);
```

- `Paragraph`: सेल में एक पैराग्राफ जोड़ता है.
- `Run`: पैराग्राफ में पाठ जोड़ता है.

## चरण 4: तालिका में कक्षों को मर्ज करें

क्या आप हेडर या स्पैन बनाने के लिए सेल्स को संयोजित करना चाहते हैं? यह बहुत आसान है!

```java
DocumentBuilder builder = new DocumentBuilder(doc);

builder.insertCell();
builder.getCellFormat().setHorizontalMerge(CellMerge.FIRST);
builder.write("Text in merged cells.");

builder.insertCell();
builder.getCellFormat().setHorizontalMerge(CellMerge.PREVIOUS);
builder.endRow();
```

- `DocumentBuilder`: दस्तावेज़ निर्माण को सरल बनाता है.
- `setHorizontalMerge`: कोशिकाओं को क्षैतिज रूप से विलीन करता है.
- `write`मर्ज किए गए कक्षों में सामग्री जोड़ता है.

## चरण 5: नेस्टेड टेबल्स जोड़ें

क्या आप आगे बढ़ने के लिए तैयार हैं? चलिए एक टेबल के अंदर एक टेबल जोड़ते हैं।

```java
builder.moveTo(table.getRows().get(0).getCells().get(0).getFirstParagraph());

builder.startTable();
builder.insertCell();
builder.write("Hello world!");
builder.endTable();
```

- `moveTo`: कर्सर को दस्तावेज़ में एक विशिष्ट स्थान पर ले जाता है।
- `startTable`: नेस्टेड तालिका बनाना प्रारंभ करता है.
- `endTable`: नेस्टेड तालिका को समाप्त करता है.

## निष्कर्ष

बधाई हो! आपने Aspose.Words for Java का उपयोग करके टेबल बनाना, भरना और स्टाइल करना सीख लिया है। टेक्स्ट जोड़ने से लेकर सेल मर्ज करने और टेबल नेस्टिंग करने तक, अब आपके पास Word दस्तावेज़ों में डेटा को प्रभावी ढंग से संरचित करने के लिए उपकरण हैं।

## अक्सर पूछे जाने वाले प्रश्न

### क्या किसी तालिका सेल में हाइपरलिंक जोड़ना संभव है?

हां, आप Aspose.Words for Java में टेबल सेल में हाइपरलिंक जोड़ सकते हैं। यहां बताया गया है कि आप यह कैसे कर सकते हैं:

```java
builder.moveTo(table.getRows().get(0).getCells().get(0).getFirstParagraph());

// एक हाइपरलिंक डालें और उसे कस्टम फ़ॉर्मेटिंग के साथ ज़ोर दें.
// हाइपरलिंक एक क्लिक करने योग्य पाठ होगा जो हमें URL में निर्दिष्ट स्थान पर ले जाएगा।
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Google website", "https://www.google.com", गलत);
```

### क्या मैं Java के लिए Aspose.Words का निःशुल्क उपयोग कर सकता हूँ?  
आप इसे सीमाओं के साथ उपयोग कर सकते हैं या प्राप्त कर सकते हैं [मुफ्त परीक्षण](https://releases.aspose.com/) इसकी पूर्ण क्षमता का पता लगाने के लिए।

### मैं किसी तालिका में कोशिकाओं को लंबवत रूप से कैसे मर्ज करूं?  
उपयोग `setVerticalMerge` की विधि `CellFormat` वर्ग, क्षैतिज विलय के समान।

### क्या मैं किसी तालिका सेल में छवियाँ जोड़ सकता हूँ?  
हां, आप इसका उपयोग कर सकते हैं `DocumentBuilder` तालिका कक्षों में छवियाँ सम्मिलित करने के लिए.

### मैं Java के लिए Aspose.Words पर अधिक संसाधन कहां पा सकता हूं?  
जाँचें [प्रलेखन](https://reference.aspose.com/words/java/) या [सहयता मंच](https://forum.aspose.com/c/words/8/) विस्तृत मार्गदर्शन के लिए.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}