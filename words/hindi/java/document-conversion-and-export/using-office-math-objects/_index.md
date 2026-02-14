---
date: 2026-02-14
description: Aspose.Words for Java के साथ इनलाइन गणित प्रदर्शित करना, गणित समीकरण
  सम्मिलित करना और Office Math ऑब्जेक्ट्स को सहजता से नियंत्रित करना सीखें।
linktitle: Using Office Math Objects
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java में Office Math के साथ इनलाइन गणित प्रदर्शित करें
url: /hi/java/document-conversion-and-export/using-office-math-objects/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java में Office Math के साथ इनलाइन गणित प्रदर्शित करें

इस व्यापक ट्यूटोरियल में आप जानेंगे कि Aspose.Words for Java में Office Math ऑब्जेक्ट्स का उपयोग करके **गणित को इनलाइन प्रदर्शित** कैसे किया जाता है। चाहे आपको रिपोर्ट में **गणितीय समीकरण डालना** हो या जटिल सूत्रों के फ़ॉर्मेटिंग को बारीकी से समायोजित करना हो, यह गाइड आपको हर चरण के माध्यम से ले जाता है—Word दस्तावेज़ लोड करने से लेकर अंतिम परिणाम सहेजने तक।

## त्वरित उत्तर
- **“display math inline” का क्या अर्थ है?** समीकरण पाठ प्रवाह के भीतर प्रदर्शित होता है, अलग पंक्ति में नहीं।  
- **कौन सा क्लास गणितीय ऑब्जेक्ट का प्रतिनिधित्व करता है?** Aspose.Words API में `OfficeMath`।  
- **क्या मैं संरेखण बदल सकता हूँ?** हाँ, `setJustification` को LEFT, CENTER, या RIGHT के साथ उपयोग करें।  
- **क्या इस सुविधा के लिए लाइसेंस चाहिए?** उत्पादन उपयोग के लिए एक वैध Aspose.Words for Java लाइसेंस आवश्यक है।  
- **कौन सा संस्करण प्रदर्शित किया गया है?** कोड नवीनतम Aspose.Words for Java रिलीज़ (2026) के साथ काम करता है।

## “display math inline” क्या है?
गणित को इनलाइन प्रदर्शित करने का मतलब है कि समीकरण को पैराग्राफ़ के पाठ का हिस्सा माना जाता है, जिससे वह आसपास के शब्दों के साथ स्वाभाविक रूप से रैप हो सके। यह छोटे सूत्रों के लिए उपयोगी है जो पढ़ने के प्रवाह को बाधित नहीं करना चाहिए।

## Aspose.Words for Java में Office Math ऑब्जेक्ट्स का उपयोग क्यों करें?
- **सटीक नियंत्रण** समीकरण लेआउट (इनलाइन बनाम डिस्प्ले) पर।  
- **प्रोग्रामेटिक हेरफेर** समीकरणों का, बिना Word को मैन्युअली खोले।  
- **सुसंगत रेंडरिंग** विभिन्न प्लेटफ़ॉर्म पर, स्वचालित रिपोर्ट जनरेशन के लिए उपयुक्त।

## पूर्वापेक्षाएँ
शुरू करने से पहले, सुनिश्चित करें कि आपके पास है:

- आपके प्रोजेक्ट में Aspose.Words for Java स्थापित और संदर्भित हो।  
- एक Word फ़ाइल जिसमें पहले से ही Office Math समीकरण हो (उदा., `OfficeMath.docx`)।  
- यदि आप कोड को मूल्यांकन मोड के बाहर चलाने की योजना बनाते हैं तो एक वैध लाइसेंस।

## स्टेप‑बाय‑स्टेप गाइड

### दस्तावेज़ लोड करें
सबसे पहले, उस दस्तावेज़ को लोड करें जिसमें वह Office Math समीकरण है जिसे आप उपयोग करना चाहते हैं:

```java
Document doc = new Document("Your Directory Path" + "OfficeMath.docx");
```

### Office Math ऑब्जेक्ट तक पहुँचें
दस्तावेज़ से पहला Office Math नोड प्राप्त करें:

```java
OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
```

### डिस्प्ले प्रकार सेट करें (इनलाइन बनाम डिस्प्ले)
नियंत्रित करें कि समीकरण आसपास के पाठ के साथ इनलाइन दिखे या अपनी अलग पंक्ति में। **display math inline** के लिए, `INLINE` एन्‍युम का उपयोग करें; अलग पंक्ति के लिए, `DISPLAY` का उपयोग करें:

```java
officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
```

*यदि आप चाहते हैं कि समीकरण इनलाइन ही रहे, तो `DISPLAY` को `INLINE` से बदल दें।*

### संरेखण सेट करें
समीकरण का संरेखण समायोजित करें। नीचे हम इसे बाएँ संरेखित कर रहे हैं, लेकिन आप `CENTER` या `RIGHT` भी चुन सकते हैं:

```java
officeMath.setJustification(OfficeMathJustification.LEFT);
```

### संशोधित दस्तावेज़ सहेजें
अंत में, परिवर्तनों को एक नई फ़ाइल में लिखें:

```java
doc.save("Your Directory Path" + "ModifiedOfficeMath.docx");
```

## Aspose.Words for Java में Office Math ऑब्जेक्ट्स के उपयोग के लिए पूर्ण स्रोत कोड

```java
        Document doc = new Document("Your Directory Path" + "Office math.docx");
        OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
        // OfficeMath display type represents whether an equation is displayed inline with the text or displayed on its line.
        officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
        officeMath.setJustification(OfficeMathJustification.LEFT);
        doc.save("Your Directory Path" + "WorkingWithOfficeMath.MathEquations.docx");
```

## सामान्य समस्याएँ और ट्रबलशूटिंग
- **समीकरण नहीं मिला:** सुनिश्चित करें कि दस्तावेज़ में वास्तव में Office Math ऑब्जेक्ट है; अन्यथा `doc.getChild` `null` लौटाता है।  
- **डिस्प्ले प्रकार का कोई प्रभाव नहीं:** जांचें कि आप Aspose.Words का नवीनतम संस्करण उपयोग कर रहे हैं; पुराने रिलीज़ में `OfficeMathDisplayType` के समर्थन में सीमाएँ हो सकती हैं।  
- **लाइसेंस अपवाद:** यदि आपको लाइसेंस त्रुटि दिखती है, तो `Document` इंस्टेंस बनाने से पहले यह दोबारा जांचें कि आपका लाइसेंस फ़ाइल सही ढंग से लोड हुआ है।

## अक्सर पूछे जाने वाले प्रश्न

**प्रश्न: Aspose.Words for Java में Office Math ऑब्जेक्ट्स का उद्देश्य क्या है?**  
उत्तर: Office Math ऑब्जेक्ट्स आपको गणितीय समीकरणों को प्रोग्रामेटिक रूप से प्रतिनिधित्व और हेरफेर करने की अनुमति देते हैं, जिससे आपको डिस्प्ले और फ़ॉर्मेटिंग पर पूर्ण नियंत्रण मिलता है।

**प्रश्न: क्या मैं अपने दस्तावेज़ में Office Math समीकरणों को अलग‑अलग संरेखित कर सकता हूँ?**  
उत्तर: हाँ, `setJustification` मेथड का उपयोग करके बाएँ, दाएँ या केंद्र में संरेखित कर सकते हैं।

**प्रश्न: क्या Aspose.Words for Java जटिल गणितीय दस्तावेज़ों को संभालने के लिए उपयुक्त है?**  
उत्तर: बिल्कुल। यह लाइब्रेरी जटिल समीकरणों, नेस्टेड फ्रैक्शन, मैट्रिक्स और अधिक को पूरी तरह समर्थन देती है।

**प्रश्न: मैं Aspose.Words for Java के बारे में और कैसे सीख सकता हूँ?**  
उत्तर: व्यापक दस्तावेज़ीकरण और डाउनलोड के लिए, देखें [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/)।

**प्रश्न: मैं Aspose.Words for Java कहाँ से डाउनलोड कर सकता हूँ?**  
उत्तर: आप वेबसाइट से Aspose.Words for Java डाउनलोड कर सकते हैं: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)।

---

**अंतिम अपडेट:** 2026-02-14  
**परीक्षित संस्करण:** Aspose.Words for Java 24.12 (Feb 2026 तक नवीनतम)  
**लेखक:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}