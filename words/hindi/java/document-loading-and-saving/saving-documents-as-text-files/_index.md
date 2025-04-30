---
"description": "Aspose.Words for Java में दस्तावेज़ों को टेक्स्ट फ़ाइलों के रूप में सहेजना सीखें। Java कोड उदाहरणों के साथ हमारे चरण-दर-चरण मार्गदर्शिका का पालन करें।"
"linktitle": "दस्तावेज़ों को टेक्स्ट फ़ाइलों के रूप में सहेजना"
"second_title": "Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई"
"title": "Java के लिए Aspose.Words में दस्तावेज़ों को टेक्स्ट फ़ाइलों के रूप में सहेजना"
"url": "/hi/java/document-loading-and-saving/saving-documents-as-text-files/"
"weight": 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java के लिए Aspose.Words में दस्तावेज़ों को टेक्स्ट फ़ाइलों के रूप में सहेजना


## जावा के लिए Aspose.Words में दस्तावेज़ों को टेक्स्ट फ़ाइलों के रूप में सहेजने का परिचय

इस ट्यूटोरियल में, हम Aspose.Words for Java लाइब्रेरी का उपयोग करके दस्तावेज़ों को टेक्स्ट फ़ाइलों के रूप में सहेजने का तरीका जानेंगे। Aspose.Words Word दस्तावेज़ों के साथ काम करने के लिए एक शक्तिशाली Java API है, और यह सादे टेक्स्ट सहित विभिन्न प्रारूपों में दस्तावेज़ों को सहेजने के लिए विभिन्न विकल्प प्रदान करता है। हम इसे प्राप्त करने के लिए चरणों को कवर करेंगे और साथ ही नमूना Java कोड प्रदान करेंगे।

## आवश्यक शर्तें

शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ मौजूद हैं:

- आपके सिस्टम पर जावा डेवलपमेंट किट (JDK) स्थापित है।
- Aspose.Words for Java लाइब्रेरी आपके प्रोजेक्ट में एकीकृत है। आप इसे यहाँ से डाउनलोड कर सकते हैं [यहाँ](https://releases.aspose.com/words/java/).
- जावा प्रोग्रामिंग का बुनियादी ज्ञान.

## चरण 1: दस्तावेज़ बनाएँ

किसी दस्तावेज़ को टेक्स्ट फ़ाइल के रूप में सहेजने के लिए, हमें सबसे पहले Aspose.Words का उपयोग करके एक दस्तावेज़ बनाना होगा। यहाँ कुछ सामग्री के साथ एक दस्तावेज़ बनाने के लिए एक सरल जावा कोड स्निपेट दिया गया है:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

इस कोड में, हम एक नया दस्तावेज़ बनाते हैं और उसमें कुछ पाठ जोड़ते हैं, जिसमें विभिन्न भाषाओं में पाठ भी शामिल होता है।

## चरण 2: टेक्स्ट सेव विकल्प निर्धारित करें

इसके बाद, हमें टेक्स्ट सेव विकल्पों को परिभाषित करने की आवश्यकता है जो निर्दिष्ट करते हैं कि दस्तावेज़ को टेक्स्ट फ़ाइल के रूप में कैसे सहेजा जाना चाहिए। हम विभिन्न सेटिंग्स कॉन्फ़िगर कर सकते हैं जैसे कि बिडी चिह्न जोड़ना, सूची इंडेंटेशन, और बहुत कुछ। आइए दो उदाहरण देखें:

### उदाहरण 1: बीड़ी के निशान जोड़ना

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

इस उदाहरण में, हम एक बनाते हैं `TxtSaveOptions` ऑब्जेक्ट और सेट करें `AddBidiMarks` संपत्ति को `true` पाठ आउटपुट में बीड़ी चिह्नों को शामिल करने के लिए।

### उदाहरण 2: सूची इंडेंटेशन के लिए टैब कैरेक्टर का उपयोग करना

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

यहां, हम 1 की गिनती के साथ सूची इंडेंटेशन के लिए टैब वर्ण का उपयोग करने के लिए सेव विकल्पों को कॉन्फ़िगर करते हैं।

## चरण 3: दस्तावेज़ को टेक्स्ट के रूप में सहेजें

अब जब हमने टेक्स्ट सेव ऑप्शन परिभाषित कर लिए हैं, तो हम डॉक्यूमेंट को टेक्स्ट फ़ाइल के रूप में सेव कर सकते हैं। निम्न कोड यह दर्शाता है कि यह कैसे करना है:

```java
doc.save("output.txt", saveOptions);
```

प्रतिस्थापित करें `"output.txt"` इच्छित फ़ाइल पथ के साथ जहाँ आप पाठ फ़ाइल को सहेजना चाहते हैं।

## जावा के लिए Aspose.Words में दस्तावेज़ों को टेक्स्ट फ़ाइलों के रूप में सहेजने के लिए पूर्ण स्रोत कोड

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // तीन स्तर के इंडेंटेशन के साथ एक सूची बनाएं।
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // तीन स्तर के इंडेंटेशन के साथ एक सूची बनाएं।
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## निष्कर्ष

इस ट्यूटोरियल में, हमने सीखा है कि Java के लिए Aspose.Words में दस्तावेज़ों को टेक्स्ट फ़ाइलों के रूप में कैसे सहेजा जाए। हमने दस्तावेज़ बनाने, टेक्स्ट सेव विकल्पों को परिभाषित करने और दस्तावेज़ को टेक्स्ट फ़ॉर्मेट में सहेजने के चरणों को कवर किया है। Aspose.Words दस्तावेज़ों को सहेजने के मामले में व्यापक लचीलापन प्रदान करता है, जिससे आप अपनी विशिष्ट आवश्यकताओं के अनुसार आउटपुट तैयार कर सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न

### मैं टेक्स्ट आउटपुट में बीड़ी मार्क कैसे जोड़ूं?

टेक्स्ट आउटपुट में बीड़ी चिह्न जोड़ने के लिए, सेट करें `AddBidiMarks` की संपत्ति `TxtSaveOptions` को `true`। उदाहरण के लिए:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### क्या मैं सूची इंडेंटेशन वर्ण को अनुकूलित कर सकता हूँ?

हां, आप सूची इंडेंटेशन वर्ण को कॉन्फ़िगर करके अनुकूलित कर सकते हैं `ListIndentation` की संपत्ति `TxtSaveOptions`उदाहरण के लिए, सूची इंडेंटेशन के लिए टैब वर्ण का उपयोग करने के लिए, आप निम्न कार्य कर सकते हैं:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### क्या Java के लिए Aspose.Words बहुभाषी पाठ को संभालने के लिए उपयुक्त है?

हां, जावा के लिए Aspose.Words बहुभाषी पाठ को संभालने के लिए उपयुक्त है। यह विभिन्न भाषाओं और वर्ण एन्कोडिंग का समर्थन करता है, जिससे यह विभिन्न भाषाओं में दस्तावेज़ों के साथ काम करने के लिए एक बहुमुखी विकल्प बन जाता है।

### मैं Aspose.Words for Java के लिए अधिक दस्तावेज़ और संसाधन कैसे प्राप्त कर सकता हूँ?

आप Aspose प्रलेखन वेबसाइट पर Java के लिए Aspose.Words के लिए व्यापक प्रलेखन और संसाधन पा सकते हैं: [जावा दस्तावेज़ीकरण के लिए Aspose.Words](https://reference.aspose.com/words/java/).

### मैं Java के लिए Aspose.Words कहां से डाउनलोड कर सकता हूं?

आप Aspose.Words for Java लाइब्रेरी को Aspose वेबसाइट से डाउनलोड कर सकते हैं: [Java के लिए Aspose.Words डाउनलोड करें](https://releases.aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}