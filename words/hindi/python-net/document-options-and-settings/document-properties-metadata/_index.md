---
title: दस्तावेज़ गुण और मेटाडेटा प्रबंधन
linktitle: दस्तावेज़ गुण और मेटाडेटा प्रबंधन
second_title: Aspose.Words पायथन दस्तावेज़ प्रबंधन API
description: पायथन के लिए Aspose.Words का उपयोग करके दस्तावेज़ गुण और मेटाडेटा को प्रबंधित करना सीखें। स्रोत कोड के साथ चरण-दर-चरण मार्गदर्शिका।
weight: 12
url: /hi/python-net/document-options-and-settings/document-properties-metadata/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# दस्तावेज़ गुण और मेटाडेटा प्रबंधन


## दस्तावेज़ गुण और मेटाडेटा का परिचय

दस्तावेज़ गुण और मेटाडेटा इलेक्ट्रॉनिक दस्तावेज़ों के आवश्यक घटक हैं। वे दस्तावेज़ के बारे में महत्वपूर्ण जानकारी प्रदान करते हैं, जैसे कि लेखकत्व, निर्माण तिथि और कीवर्ड। मेटाडेटा में अतिरिक्त प्रासंगिक जानकारी शामिल हो सकती है, जो दस्तावेज़ वर्गीकरण और खोज में सहायता करती है। पायथन के लिए Aspose.Words इन पहलुओं को प्रोग्रामेटिक रूप से प्रबंधित करने की प्रक्रिया को सरल बनाता है।

## पायथन के लिए Aspose.Words के साथ आरंभ करना

इससे पहले कि हम दस्तावेज़ गुण और मेटाडेटा का प्रबंधन करना शुरू करें, आइए Python के लिए Aspose.Words के साथ अपना वातावरण सेट करें।

```python
# Install the Aspose.Words for Python package
pip install aspose-words

# Import the necessary classes
import aspose.words as aw
```

## दस्तावेज़ गुण पुनर्प्राप्त करना

आप Aspose.Words API का उपयोग करके आसानी से दस्तावेज़ गुण प्राप्त कर सकते हैं। यहाँ एक उदाहरण दिया गया है कि दस्तावेज़ के लेखक और शीर्षक को कैसे प्राप्त किया जाए:

```python
# Load the document
doc = aw.Document("document.docx")

# Retrieve document properties
author = doc.built_in_document_properties["Author"]
title = doc.built_in_document_properties["Title"]

print("Author:", author)
print("Title:", title)
```

## दस्तावेज़ गुण सेट करना

दस्तावेज़ के गुणों को अपडेट करना भी उतना ही सरल है। मान लीजिए कि आप लेखक का नाम और शीर्षक अपडेट करना चाहते हैं:

```python
# Update document properties
doc.built_in_document_properties["Author"] = "John Doe"
doc.built_in_document_properties["Title"] = "My Updated Document"

# Save the changes
doc.save("updated_document.docx")
```

## कस्टम दस्तावेज़ गुणों के साथ कार्य करना

कस्टम दस्तावेज़ गुण आपको दस्तावेज़ के भीतर अतिरिक्त जानकारी संग्रहीत करने की अनुमति देते हैं। आइए "विभाग" नामक एक कस्टम गुण जोड़ें:

```python
# Add a custom document property
doc.custom_document_properties.add("Department", "Marketing")

# Save the changes
doc.save("document_with_custom_property.docx")
```

## मेटाडेटा जानकारी प्रबंधित करना

मेटाडेटा प्रबंधन में ट्रैक परिवर्तन, दस्तावेज़ सांख्यिकी और अधिक जैसी जानकारी को नियंत्रित करना शामिल है। Aspose.Words आपको इस मेटाडेटा को प्रोग्रामेटिक रूप से एक्सेस और संशोधित करने देता है।

```python
# Access and modify metadata
doc.metadata["Keywords"] = "Python, Aspose.Words, Metadata"
```

## मेटाडेटा अपडेट को स्वचालित करना

Aspose.Words का उपयोग करके बार-बार मेटाडेटा अपडेट को स्वचालित किया जा सकता है। उदाहरण के लिए, आप "अंतिम संशोधित तिथि" प्रॉपर्टी को स्वचालित रूप से अपडेट कर सकते हैं:

```python
# Automatically update "Last Modified By"
doc.built_in_document_properties["LastModifiedBy"] = "Automated Process"
```

## मेटाडेटा में संवेदनशील जानकारी की सुरक्षा

मेटाडेटा में कभी-कभी संवेदनशील जानकारी हो सकती है। डेटा गोपनीयता सुनिश्चित करने के लिए, आप कुछ खास गुण हटा सकते हैं:

```python
# Remove sensitive metadata properties
sensitive_properties = ["LastPrinted", "LastSavedBy"]
for prop in sensitive_properties:
    if prop in doc.built_in_document_properties:
        doc.built_in_document_properties.remove(prop)
```

## दस्तावेज़ संस्करण और इतिहास को संभालना

दस्तावेज़ इतिहास को बनाए रखने के लिए संस्करणीकरण महत्वपूर्ण है। Aspose.Words आपको संस्करणों को प्रभावी ढंग से प्रबंधित करने की अनुमति देता है:

```python
# Add version history information
version_info = doc.built_in_document_properties.add("VersionInfo")
version_info.value = "Version 1.0 - Initial Release"
```

## दस्तावेज़ संपत्ति सर्वोत्तम अभ्यास

- दस्तावेज़ के गुणों को सटीक और अद्यतन रखें.
- अतिरिक्त संदर्भ के लिए कस्टम गुणों का उपयोग करें.
- मेटाडेटा का नियमित रूप से ऑडिट और अद्यतन करें।
- मेटाडेटा में संवेदनशील जानकारी को सुरक्षित रखें.

## निष्कर्ष

दस्तावेज़ के गुणों और मेटाडेटा को प्रभावी ढंग से प्रबंधित करना दस्तावेज़ संगठन और पुनर्प्राप्ति के लिए महत्वपूर्ण है। पायथन के लिए Aspose.Words इस प्रक्रिया को सुव्यवस्थित करता है, जिससे डेवलपर्स को प्रोग्रामेटिक रूप से दस्तावेज़ विशेषताओं में आसानी से हेरफेर और नियंत्रण करने में सक्षम बनाता है।

## अक्सर पूछे जाने वाले प्रश्न

### मैं Python के लिए Aspose.Words कैसे स्थापित करूं?

आप निम्न आदेश का उपयोग करके Python के लिए Aspose.Words स्थापित कर सकते हैं:

```python
pip install aspose-words
```

### क्या मैं Aspose.Words का उपयोग करके मेटाडेटा अपडेट को स्वचालित कर सकता हूं?

हां, आप Aspose.Words का उपयोग करके मेटाडेटा अपडेट को स्वचालित कर सकते हैं। उदाहरण के लिए, आप "अंतिम संशोधित द्वारा" प्रॉपर्टी को स्वचालित रूप से अपडेट कर सकते हैं।

### मैं मेटाडेटा में संवेदनशील जानकारी की सुरक्षा कैसे कर सकता हूँ?

 मेटाडेटा में संवेदनशील जानकारी की सुरक्षा के लिए, आप इसका उपयोग करके विशिष्ट गुणों को हटा सकते हैं`remove` तरीका।

### दस्तावेज़ गुणों के प्रबंधन के लिए कुछ सर्वोत्तम अभ्यास क्या हैं?

- दस्तावेज़ गुणों की सटीकता और नवीनता सुनिश्चित करें।
- अतिरिक्त संदर्भ के लिए कस्टम गुणों का उपयोग करें.
- मेटाडेटा की नियमित समीक्षा करें और उसे अद्यतन करें.
- मेटाडेटा में निहित संवेदनशील जानकारी की सुरक्षा करें।
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
