---
category: general
date: 2026-11-25
description: Aspose.Words for Python के साथ Word में आकृति पर छाया कैसे जोड़ें, सीखें
  – चरण‑दर‑चरण कोड, व्याख्याएँ और सर्वोत्तम प्रथाएँ।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add shadow to shape in word
- Aspose.Words shadow formatting
- Python shape shadow
- Word document shape manipulation
- configure shadow offset
- set shape shadow color
language: hi
lastmod: 2026-11-25
og_description: Aspose.Words for Python के साथ Word में आकृति में छाया कैसे जोड़ें।
  अपने दस्तावेज़ों में आकृति की छायाओं को सक्षम करने और अनुकूलित करने के लिए इस ट्यूटोरियल
  का पालन करें।
og_image_alt: Screenshot showing a Word shape with a black shadow applied using Python
og_title: Python का उपयोग करके Word में आकृति में शैडो कैसे जोड़ें – पूर्ण गाइड
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to add shadow to shape in Word with Aspose.Words for Python
    – step‑by‑step code, explanations, and best practices.
  headline: How to add shadow to shape in Word using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- Shape formatting
title: Python का उपयोग करके Word में आकृति में छाया कैसे जोड़ें
url: /hi/python/images-shapes/how-to-add-shadow-to-shape-in-word-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python का उपयोग करके Word में आकार पर छाया कैसे जोड़ें

यदि आपको **Word में आकार पर छाया कैसे जोड़ें** की आवश्यकता है, तो यह गाइड Aspose.Words for Python के साथ सटीक चरण दिखाता है। ट्यूटोरियल के अंत तक आपके पास एक Word दस्तावेज़ होगा जिसमें पहला आकार कस्टम ऑफ़सेट और ब्लर के साथ काली छाया प्रदर्शित करेगा।

आप यह भी देखेंगे कि वही तकनीक दस्तावेज़ में किसी भी आकार पर कैसे काम करती है, जिससे रिपोर्ट, फ़्लायर या मार्केटिंग सामग्री को बढ़ाना आसान हो जाता है। Aspose.Words के साथ कोई पूर्व अनुभव आवश्यक नहीं है—सिर्फ बुनियादी Python ज्ञान चाहिए।

## आप को क्या चाहिए

- Python 3.8+ (कोड Windows, macOS, और Linux पर काम करता है)  
- `aspose-words` package (`pip install aspose-words`)  
- एक `.docx` फ़ाइल जिसमें कम से कम एक आकार हो (उदाहरण के लिए, डाली गई आयत या चित्र)  

## चरण 1: Aspose.Words for Python सेट अप करें

पहले लाइब्रेरी स्थापित करें और आवश्यक नेमस्पेस इम्पोर्ट करें। `aspose.words` पैकेज आपको Word के ऑब्जेक्ट मॉडल तक पूरी पहुंच देता है, जिसमें आकार की छाया गुण शामिल हैं।

```python
# Install the package (run once in your terminal)
# pip install aspose-words

import aspose.words as aw
```

> **Pro tip:** एक वर्चुअल एनवायरनमेंट का उपयोग करें ताकि निर्भरताएँ अन्य प्रोजेक्ट्स से अलग रहें।

## चरण 2: Word दस्तावेज़ लोड करें

`aw.Document` के साथ दस्तावेज़ लोड करना सीधा है। `"YOUR_DIRECTORY/input.docx"` को अपने स्रोत फ़ाइल के पथ से बदलें।

```python
# Load the Word document
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

`Document` ऑब्जेक्ट पूरे Word फ़ाइल का प्रतिनिधित्व करता है और नोड ट्री को नेविगेट करने के लिए मेथड्स प्रदान करता है।

## चरण 3: दस्तावेज़ में पहला आकार प्राप्त करें

एक आकार `NodeType.SHAPE` प्रकार का नोड होता है। `get_child` मेथड दस्तावेज़ ट्री को खोजता है और पहला मिलते-जुलते नोड को लौटाता है।

```python
# Retrieve the first shape (index 0) in the document
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
```

यदि आपके दस्तावेज़ में कई आकार हैं, तो अलग आकार को लक्षित करने के लिए इंडेक्स बदलें। `True` फ़्लैग सुनिश्चित करता है कि खोज गहरी हो (यानी यह हेडर, फुटर और टेबल के अंदर भी देखता है)।

## चरण 4: आकार पर छाया फ़ॉर्मेटिंग लागू करें

प्रत्येक आकार में `shadow_format` प्रॉपर्टी होती है जो दृश्यता, रंग, ऑफ़सेट, ब्लर और अधिक को नियंत्रित करती है। नीचे हम छाया को सक्षम करते हैं, उसका रंग काला सेट करते हैं, और क्षैतिज/ऊर्ध्वाधर ऑफ़सेट और ब्लर रेडियस को कॉन्फ़िगर करते हैं।

```python
# Access the shape's shadow formatting object
shadow_format = first_shape.shadow_format

# Enable the shadow and configure its appearance
shadow_format.visible = True                     # Make the shadow visible
shadow_format.color = aw.drawing.Color.black    # Set shadow color to black
shadow_format.offset_x = 4                      # Horizontal offset (points)
shadow_format.offset_y = 4                      # Vertical offset (points)
shadow_format.blur = 6                          # Blur radius (points)
```

### इन सेटिंग्स का महत्व क्यों है

- `visible = True` प्रभाव को चालू करता है; इसके बिना अन्य प्रॉपर्टीज़ का कोई असर नहीं होता।  
- `color` छाया की शेड निर्धारित करता है; काला सबसे अधिक कंट्रास्ट देता है।  
- `offset_x` और `offset_y` नियंत्रित करते हैं कि छाया आकार से कितनी दूरी पर विस्थापित हो; समान मान एक विकर्ण ड्रॉप शैडो बनाते हैं।  
- `blur` किनारों को नरम करता है, जिससे छाया अधिक प्राकृतिक दिखती है।  

आप अन्य रंगों (`aw.drawing.Color.red`) या बड़े ऑफ़सेट के साथ प्रयोग कर सकते हैं ताकि नाटकीय प्रभाव मिले। यह लचीलापन **Aspose.Words shadow formatting** का हिस्सा है।

## चरण 5: संशोधित दस्तावेज़ को सहेजें (वैकल्पिक)

छाया को कॉन्फ़िगर करने के बाद, बदलावों को डिस्क पर वापस लिखें। आप मूल फ़ाइल को ओवरराइट कर सकते हैं या नई फ़ाइल बना सकते हैं।

```python
# Save the updated document
doc.save("YOUR_DIRECTORY/output.docx")
```

`output.docx` को Microsoft Word में खोलने पर पहला आकार एक दृश्यमान काली छाया के साथ दिखेगा, जो क्षैतिज और ऊर्ध्वाधर रूप से 4 pts ऑफ़सेट और 6 pts ब्लर किया गया है।

![Word में आकार पर छाया जोड़ने का स्क्रीनशॉट](image.png){alt="Python का उपयोग करके Word में आकार पर छाया कैसे जोड़ें"}

## सामान्य विविधताएँ और किनारे के मामले

| स्थिति | कोड को कैसे समायोजित करें |
|-----------|------------------------|
| **एकाधिक आकार** | `doc.get_child_nodes(aw.NodeType.SHAPE, True)` पर लूप करें और प्रत्येक आकार पर समान `shadow_format` लागू करें। |
| **विभिन्न छाया रंग** | लाल छाया के लिए `shadow_format.color = aw.drawing.Color.from_argb(255, 255, 0, 0)` सेट करें। |
| **कुछ आकारों पर छाया आवश्यक नहीं** | एक शर्तीय जांच जोड़ें: `if shape.name == "TitleShape": continue`। |
| **PDF के रूप में सहेजना** | `doc.save("output.pdf")` का उपयोग करें; छाया PDF रेंडरिंग में संरक्षित रहती है। |
| **पुराने Word संस्करण** | Aspose.Words .doc और .docx दोनों के साथ काम करता है; वही API लागू होती है। |

ये विविधताएँ **Word दस्तावेज़ आकार हेरफेर** की विस्तृत सीमा को दर्शाती हैं जिसे आप कुछ पंक्तियों के Python से प्राप्त कर सकते हैं।

## निष्कर्ष

अब आप Aspose.Words for Python के साथ प्रोग्रामेटिक रूप से **Word में आकार पर छाया कैसे जोड़ें** जानते हैं। पूर्ण वर्कफ़्लो—लाइब्रेरी सेट अप करना, दस्तावेज़ लोड करना, आकार प्राप्त करना, उसकी छाया कॉन्फ़िगर करना, और परिणाम सहेजना—सबसे सामान्य उपयोग केस को कवर करता है और आपको अधिक उन्नत आकार फ़ॉर्मेटिंग के लिए एक ठोस आधार देता है।

अब, इस तकनीक को अन्य फ़ॉर्मेटिंग विकल्पों जैसे **set shape shadow color**, **configure shadow offset**, या यहाँ तक कि ग्रेडिएंट और रिफ्लेक्शन लागू करने के साथ संयोजित करने का प्रयास करें। इन सुविधाओं का अन्वेषण करने से आप पूरी तरह कोड से पॉलिश्ड, प्रिंट‑रेडी दस्तावेज़ बना सकते हैं।

--- 

*क्या आप अधिक Word सुविधाओं को स्वचालित करने के लिए तैयार हैं? हमारे ट्यूटोरियल देखें “Word में आकार भरने का रंग कैसे बदलें” और “Aspose.Words के साथ वॉटरमार्क कैसे डालें” पर।*

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API सुविधाओं में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Python में Aspose.Words के साथ आकार पर छाया जोड़ें – पूर्ण गाइड](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-with-aspose-words-full-guide/)
- [Aspose.Words के साथ Word आकार पर छाया प्रभाव कैसे लागू करें](/words/english/python-net/images-shapes/how-to-apply-shadow-effect-to-a-word-shape-with-aspose-words/)
- [Word दस्तावेज़ Python बनाएं – आकार पर छाया जोड़ने का गाइड](/words/english/python-net/images-shapes/create-word-document-python-add-shadow-to-shape-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}