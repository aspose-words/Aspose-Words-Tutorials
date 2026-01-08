---
date: 2025-12-24
description: Aspose.Words for Java का उपयोग करके Word दस्तावेज़ों से सादा टेक्स्ट
  फ़ाइल बनाना सीखें। यह गाइड दिखाता है कि Word को txt में कैसे बदलें, टैब इंडेंटेशन
  का उपयोग करें, और Word को txt के रूप में सहेजें।
linktitle: Saving Documents as Text Files
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java के साथ साधारण टेक्स्ट फ़ाइल कैसे बनाएं
url: /hi/java/document-loading-and-saving/saving-documents-as-text-files/
weight: 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java के साथ प्लेन टेक्स्ट फ़ाइल कैसे बनाएं

## Aspose.Words for Java में दस्तावेज़ों को टेक्स्ट फ़ाइलों के रूप में सहेजने का परिचय

इस ट्यूटोरियल में, आप Aspose.Words for Java लाइब्रेरी का उपयोग करके एक Word दस्तावेज़ से **plain text फ़ाइल कैसे बनाएं** सीखेंगे। चाहे आपको **word को txt में बदलना** हो, रिपोर्ट जनरेशन को स्वचालित करना हो, या आगे की प्रोसेसिंग के लिए कच्चा टेक्स्ट निकालना हो, यह गाइड आपको पूरे वर्कफ़्लो के माध्यम से ले जाता है—दस्तावेज़ निर्माण से लेकर सहेजने के विकल्पों को सूक्ष्म‑समायोजन तक, जैसे **टैब इंडेंटेशन का उपयोग** या bidi मार्क्स जोड़ना। आइए शुरू करते हैं!

## त्वरित उत्तर
- **दस्तावेज़ बनाने के लिए मुख्य क्लास कौन सी है?** Aspose.Words से `Document`।
- **कौन सा विकल्प दाएँ‑से‑बाएँ भाषाओं के लिए bidi मार्क्स जोड़ता है?** `TxtSaveOptions.setAddBidiMarks(true)`।
- **मैं टैब्स के साथ सूची आइटम्स को कैसे इंडेंट कर सकता हूँ?** `ListIndentation.Character` को `'\t'` सेट करें।
- **क्या विकास के लिए मुझे लाइसेंस चाहिए?** परीक्षण के लिए एक फ्री ट्रायल काम करता है; उत्पादन के लिए लाइसेंस आवश्यक है।
- **क्या मैं फ़ाइल को कस्टम नाम और पाथ के साथ सहेज सकता हूँ?** हाँ—`doc.save()` में पूर्ण पाथ पास करें।

## पूर्वापेक्षाएँ

शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ मौजूद हैं:

- Java Development Kit (JDK) आपके सिस्टम पर स्थापित हो।  
- Aspose.Words for Java लाइब्रेरी आपके प्रोजेक्ट में एकीकृत हो। आप इसे [here](https://releases.aspose.com/words/java/) से डाउनलोड कर सकते हैं।  
- Java प्रोग्रामिंग का बुनियादी ज्ञान।

## चरण 1: दस्तावेज़ बनाएं

**word को txt के रूप में सहेजने** के लिए, हमें पहले एक `Document` इंस्टेंस चाहिए। नीचे एक सरल Java स्निपेट है जो एक दस्तावेज़ बनाता है और कई भाषाओं का कुछ टेक्स्ट लिखता है:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

इस कोड में हम एक नया दस्तावेज़ बनाते हैं, अंग्रेज़ी, हिब्रू, और अरबी टेक्स्ट जोड़ते हैं, और हिब्रू पैराग्राफ के लिए दाएँ‑से‑बाएँ फ़ॉर्मेटिंग सक्षम करते हैं।

## चरण 2: टेक्स्ट सहेजने के विकल्प निर्धारित करें

अगला, हम कॉन्फ़िगर करते हैं कि दस्तावेज़ को प्लेन टेक्स्ट फ़ाइल के रूप में कैसे सहेजा जाएगा। Aspose.Words `TxtSaveOptions` क्लास प्रदान करता है, जो आपको bidi मार्क्स से लेकर सूची इंडेंटेशन तक सब कुछ नियंत्रित करने देता है।

### उदाहरण 1: Bidi मार्क्स जोड़ना (सही RTL समर्थन के साथ txt कैसे सहेजें)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

`AddBidiMarks` को `true` सेट करने से यह सुनिश्चित होता है कि दाएँ‑से‑बाएँ अक्षर परिणामस्वरूप **plain text फ़ाइल** में सही ढंग से दर्शाए जाएँ।

### उदाहरण 2: सूची इंडेंटेशन के लिए टैब कैरेक्टर का उपयोग (टैब इंडेंटेशन का उपयोग)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

यहाँ हम Aspose.Words को प्रत्येक सूची स्तर से पहले एक टैब कैरेक्टर (`'\t'`) जोड़ने के लिए कहते हैं, जिससे टेक्स्ट आउटपुट पढ़ने में आसान हो जाता है।

## चरण 3: दस्तावेज़ को टेक्स्ट के रूप में सहेजें

अब जब सहेजने के विकल्प तैयार हैं, आप दस्तावेज़ को **plain text फ़ाइल** के रूप में सहेज सकते हैं:

```java
doc.save("output.txt", saveOptions);
```

`"output.txt"` को उस पूर्ण पाथ से बदलें जहाँ आप फ़ाइल सहेजना चाहते हैं।

## Aspose.Words for Java में टेक्स्ट फ़ाइलों के रूप में दस्तावेज़ सहेजने के लिए पूर्ण स्रोत कोड

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
        // Create a list with three levels of indentation.
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
        // Create a list with three levels of indentation.
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

## सामान्य समस्याएँ और समाधान

| समस्या | समाधान |
|-------|----------|
| **Bidi अक्षर गड़बड़ टेक्स्ट के रूप में दिखते हैं** | `setAddBidiMarks(true)` सक्षम है यह सुनिश्चित करें और आउटपुट फ़ाइल को UTF‑8 एन्कोडिंग के साथ खोलें। |
| **सूची इंडेंटेशन गलत दिख रहा है** | `ListIndentation.Count` और `Character` को इच्छित मानों (टैब `'\t'` या स्पेस `' '` ) पर सेट किया गया है यह जाँचें। |
| **फ़ाइल नहीं बनी** | जाँचें कि डायरेक्टरी पाथ मौजूद है और एप्लिकेशन के पास लिखने की अनुमति है। |

## अक्सर पूछे जाने वाले प्रश्न

### मैं टेक्स्ट आउटपुट में bidi मार्क्स कैसे जोड़ूँ?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### क्या मैं सूची इंडेंटेशन कैरेक्टर को कस्टमाइज़ कर सकता हूँ?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### क्या Aspose.Words for Java बहुभाषी टेक्स्ट को संभालने के लिए उपयुक्त है?

हां, Aspose.Words for Java कई भाषाओं और कैरेक्टर एन्कोडिंग्स को सपोर्ट करता है, जिससे बहुभाषी सामग्री को निकालना और प्लेन टेक्स्ट के रूप में सहेजना आदर्श बन जाता है।

### मैं Aspose.Words for Java के लिए अधिक दस्तावेज़ीकरण और संसाधनों तक कैसे पहुँच सकता हूँ?

आप Aspose.Words for Java Documentation पेज पर व्यापक दस्तावेज़ीकरण और संसाधन पा सकते हैं: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/)।

### मैं Aspose.Words for Java कहाँ से डाउनलोड कर सकता हूँ?

आप आधिकारिक साइट से लाइब्रेरी डाउनलोड कर सकते हैं: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)।

### यदि मुझे बैच प्रोसेस में **word को txt में बदलना** हो तो क्या करें?

ऊपर दिखाए गए कोड को एक लूप में रखें जो प्रत्येक `.docx` फ़ाइल को लोड करे, समान `TxtSaveOptions` लागू करे, और प्रत्येक को `.txt` के रूप में सहेजे। प्रत्येक इटरशन के बाद `Document` ऑब्जेक्ट्स को डिस्पोज़ करके संसाधनों का प्रबंधन सुनिश्चित करें।

### क्या API फ़ाइल के बजाय सीधे स्ट्रीम में सहेजने का समर्थन करता है?

हां, आप `doc.save(outputStream, saveOptions)` में `OutputStream` पास कर सकते हैं इन‑मेमोरी प्रोसेसिंग या वेब सर्विसेज़ के साथ इंटीग्रेशन के लिए।

**अंतिम अपडेट:** 2025-12-24  
**परीक्षित संस्करण:** Aspose.Words for Java 24.12 (latest)  
**लेखक:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}