---
title: जावा के लिए Aspose.Words में सूचियों का उपयोग करना
linktitle: सूचियों का उपयोग करना
second_title: Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई
description: इस चरण-दर-चरण ट्यूटोरियल के साथ Java के लिए Aspose.Words में सूचियों का उपयोग करना सीखें। अपने दस्तावेज़ों को प्रभावी ढंग से व्यवस्थित और प्रारूपित करें।
weight: 18
url: /hi/java/using-document-elements/using-lists/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# जावा के लिए Aspose.Words में सूचियों का उपयोग करना


इस व्यापक ट्यूटोरियल में, हम जावा के लिए Aspose.Words में सूचियों का प्रभावी ढंग से उपयोग करने का तरीका जानेंगे, जो कि Microsoft Word दस्तावेज़ों के साथ प्रोग्रामेटिक रूप से काम करने के लिए एक शक्तिशाली API है। आपके दस्तावेज़ों में सामग्री को संरचित और व्यवस्थित करने के लिए सूचियाँ आवश्यक हैं। हम सूचियों के साथ काम करने के दो मुख्य पहलुओं को कवर करेंगे: प्रत्येक अनुभाग में सूचियों को फिर से शुरू करना और सूची स्तरों को निर्दिष्ट करना। आइए गोता लगाएँ!

## जावा के लिए Aspose.Words का परिचय

सूचियों के साथ काम करना शुरू करने से पहले, आइए जावा के लिए Aspose.Words से परिचित हो जाएं। यह API डेवलपर्स को जावा वातावरण में Word दस्तावेज़ बनाने, संशोधित करने और हेरफेर करने के लिए उपकरण प्रदान करता है। यह सरल दस्तावेज़ निर्माण से लेकर जटिल स्वरूपण और सामग्री प्रबंधन तक के कार्यों के लिए एक बहुमुखी समाधान है।

### अपना वातावरण स्थापित करना

 आरंभ करने के लिए, सुनिश्चित करें कि आपके पास Aspose.Words for Java स्थापित है और आपके विकास परिवेश में सेट अप है। आप इसे डाउनलोड कर सकते हैं[यहाँ](https://releases.aspose.com/words/java/). 

## प्रत्येक अनुभाग पर सूचियाँ पुनः आरंभ करना

कई परिदृश्यों में, आपको अपने दस्तावेज़ के प्रत्येक अनुभाग पर सूचियों को पुनः आरंभ करने की आवश्यकता हो सकती है। यह कई अनुभागों वाले संरचित दस्तावेज़ बनाने के लिए उपयोगी हो सकता है, जैसे रिपोर्ट, मैनुअल या अकादमिक पेपर।

यहाँ Java के लिए Aspose.Words का उपयोग करके इसे प्राप्त करने के बारे में चरण-दर-चरण मार्गदर्शिका दी गई है:

### अपना दस्तावेज़ आरंभ करें: 
एक नया दस्तावेज़ ऑब्जेक्ट बनाकर प्रारंभ करें.

```java
Document doc = new Document();
```

### क्रमांकित सूची जोड़ें: 
अपने दस्तावेज़ में क्रमांकित सूची जोड़ें। हम डिफ़ॉल्ट क्रमांकन शैली का उपयोग करेंगे।

```java
doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
```

### सूची सेटिंग कॉन्फ़िगर करें: 
\प्रत्येक अनुभाग पर सूची को पुनः आरंभ करने में सक्षम करें.

```java
List list = doc.getLists().get(0);
list.isRestartAtEachSection(true);
```

### दस्तावेज़बिल्डर सेटअप: 
अपने दस्तावेज़ में सामग्री जोड़ने के लिए एक दस्तावेज़बिल्डर बनाएँ।

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getListFormat().setList(list);
```

### सूची आइटम जोड़ें: 
अपने दस्तावेज़ में सूची आइटम जोड़ने के लिए लूप का उपयोग करें। हम 15वें आइटम के बाद एक सेक्शन ब्रेक डालेंगे।

```java
for (int i = 1; i < 45; i++) {
    builder.writeln(MessageFormat.format("List Item {0}", i));
    if (i == 15)
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
}
```

### अपना दस्तावेज़ सहेजें: 
दस्तावेज़ को इच्छित विकल्पों के साथ सहेजें.

```java
OoxmlSaveOptions options = new OoxmlSaveOptions();
options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);
doc.save(outPath + "RestartListAtEachSection.docx", options);
```

इन चरणों का पालन करके, आप प्रत्येक अनुभाग पर पुनः आरंभ होने वाली सूचियों के साथ दस्तावेज़ बना सकते हैं, तथा स्पष्ट और संगठित सामग्री संरचना बनाए रख सकते हैं।

## सूची स्तर निर्दिष्ट करना

Aspose.Words for Java आपको सूची स्तर निर्दिष्ट करने की अनुमति देता है, जो विशेष रूप से तब उपयोगी होता है जब आपको अपने दस्तावेज़ में अलग-अलग सूची प्रारूपों की आवश्यकता होती है। आइए जानें कि यह कैसे किया जाता है:

### अपना दस्तावेज़ आरंभ करें: 
एक नया दस्तावेज़ ऑब्जेक्ट बनाएँ.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### क्रमांकित सूची बनाएं: 
माइक्रोसॉफ्ट वर्ड से क्रमांकित सूची टेम्पलेट लागू करें।

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
```

### सूची स्तर निर्दिष्ट करें: 
विभिन्न सूची स्तरों पर पुनरावृत्ति करें और सामग्री जोड़ें।

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### बुलेटेड सूची बनाएं: 
अब, आइए एक बुलेटेड सूची बनाएं।

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
```

### बुलेटेड सूची स्तर निर्दिष्ट करें: 
क्रमांकित सूची के समान, स्तर निर्दिष्ट करें और सामग्री जोड़ें।

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### स्टॉप सूची स्वरूपण: 
सूची स्वरूपण रोकने के लिए, सूची को शून्य पर सेट करें.

```java
builder.getListFormat().setList(null);
```

### अपना दस्तावेज़ सहेजें: 
दस्तावेज़ सहेजें.

```java
builder.getDocument().save(outPath + "SpecifyListLevel.docx");
```

इन चरणों का पालन करके, आप कस्टम सूची स्तरों वाले दस्तावेज़ बना सकते हैं, जिससे आप अपने दस्तावेज़ों में सूचियों के स्वरूपण को नियंत्रित कर सकते हैं।

## संपूर्ण स्रोत कोड
```java
	string outPath = "Your Output Directory";
 public void restartListAtEachSection() throws Exception
    {
        Document doc = new Document();
        doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
        List list = doc.getLists().get(0);
        list.isRestartAtEachSection(true);
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.getListFormat().setList(list);
        for (int i = 1; i < 45; i++)
        {
            builder.writeln(MessageFormat.format("List Item {0}", i));
            if (i == 15)
                builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        }
        // IsRestartAtEachSection केवल तभी लिखा जाएगा जब अनुपालन OoxmlComplianceCore.Ecma376 से अधिक हो।
        OoxmlSaveOptions options = new OoxmlSaveOptions(); { options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL); }
        doc.save(outPath + "WorkingWithList.RestartListAtEachSection.docx", options);
    }
    @Test
    public void specifyListLevel() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Microsoft Word सूची टेम्पलेट्स में से किसी एक के आधार पर क्रमांकित सूची बनाएं
        //और इसे दस्तावेज़ निर्माता के वर्तमान पैराग्राफ़ पर लागू करें.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
        // इस सूची में नौ स्तर हैं, आइए उन सभी को आज़माएँ।
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Microsoft Word सूची टेम्पलेट्स में से किसी एक के आधार पर बुलेटेड सूची बनाएं
        //और इसे दस्तावेज़ निर्माता के वर्तमान पैराग्राफ़ पर लागू करें.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // यह सूची स्वरूपण को रोकने का एक तरीका है।
        builder.getListFormat().setList(null);
        builder.getDocument().save(outPath + "WorkingWithList.SpecifyListLevel.docx");
    }
    @Test
    public void restartListNumber() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // एक टेम्पलेट के आधार पर एक सूची बनाएं.
        List list1 = doc.getLists().add(ListTemplate.NUMBER_ARABIC_PARENTHESIS);
        list1.getListLevels().get(0).getFont().setColor(Color.RED);
        list1.getListLevels().get(0).setAlignment(ListLevelAlignment.RIGHT);
        builder.writeln("List 1 starts below:");
        builder.getListFormat().setList(list1);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        // पहली सूची का पुनः उपयोग करने के लिए, हमें मूल सूची स्वरूपण की प्रतिलिपि बनाकर क्रमांकन पुनः आरंभ करना होगा।
        List list2 = doc.getLists().addCopy(list1);
        // हम नई सूची को किसी भी तरह से संशोधित कर सकते हैं, जिसमें नई आरंभ संख्या निर्धारित करना भी शामिल है।
        list2.getListLevels().get(0).setStartAt(10);
        builder.writeln("List 2 starts below:");
        builder.getListFormat().setList(list2);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        builder.getDocument().save(outPath + "WorkingWithList.RestartListNumber.docx");
	}
```

## निष्कर्ष

बधाई हो! आपने Aspose.Words for Java में सूचियों के साथ प्रभावी ढंग से काम करना सीख लिया है। आपके दस्तावेज़ों में सामग्री को व्यवस्थित करने और प्रस्तुत करने के लिए सूचियाँ महत्वपूर्ण हैं। चाहे आपको प्रत्येक अनुभाग में सूचियों को फिर से शुरू करने की आवश्यकता हो या सूची स्तर निर्दिष्ट करने की, Aspose.Words for Java आपको पेशेवर दिखने वाले दस्तावेज़ बनाने के लिए आवश्यक उपकरण प्रदान करता है।

अब आप अपने दस्तावेज़ निर्माण और फ़ॉर्मेटिंग कार्यों को बेहतर बनाने के लिए इन सुविधाओं का आत्मविश्वास से उपयोग कर सकते हैं। यदि आपके पास कोई प्रश्न है या आपको और सहायता की आवश्यकता है, तो बेझिझक हमसे संपर्क करें[Aspose समुदाय मंच](https://forum.aspose.com/) समर्थन के लिए।

## पूछे जाने वाले प्रश्न

### मैं Java के लिए Aspose.Words कैसे स्थापित करूं?
 आप Java के लिए Aspose.Words को यहां से डाउनलोड कर सकते हैं[यहाँ](https://releases.aspose.com/words/java/) और दस्तावेज़ में दिए गए स्थापना निर्देशों का पालन करें।

### क्या मैं सूचियों के क्रमांकन प्रारूप को अनुकूलित कर सकता हूँ?
हां, Aspose.Words for Java सूची क्रमांकन प्रारूपों को अनुकूलित करने के लिए व्यापक विकल्प प्रदान करता है। विवरण के लिए आप API दस्तावेज़ देख सकते हैं।

### क्या Aspose.Words for Java नवीनतम Word दस्तावेज़ मानकों के साथ संगत है?
हां, आप ISO 29500 सहित विभिन्न Word दस्तावेज़ मानकों का अनुपालन करने के लिए Aspose.Words for Java को कॉन्फ़िगर कर सकते हैं।

### क्या मैं Java के लिए Aspose.Words का उपयोग करके तालिकाओं और छवियों के साथ जटिल दस्तावेज़ तैयार कर सकता हूँ?
बिलकुल! Aspose.Words for Java उन्नत दस्तावेज़ स्वरूपण का समर्थन करता है, जिसमें तालिकाएँ, चित्र और बहुत कुछ शामिल है। उदाहरणों के लिए दस्तावेज़ देखें।

### मैं Java के लिए Aspose.Words का अस्थायी लाइसेंस कहां से प्राप्त कर सकता हूं?
आप अस्थायी लाइसेंस प्राप्त कर सकते हैं[यहाँ](https://purchase.aspose.com/temporary-license/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
