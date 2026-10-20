---
category: general
date: 2026-08-14
description: Python का उपयोग करके Word के आकार में छाया कैसे जोड़ें – छाया प्रभाव
  लागू करना सीखें, छाया प्रभाव बनाएं, और Word दस्तावेज़ को कुशलतापूर्वक सहेजें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add shadow
- apply shadow effect
- create shadow effect
- save word document
- add shadow to shape
language: hi
lastmod: 2026-08-14
og_description: Python का उपयोग करके Word आकार में छाया कैसे जोड़ें। इस पूर्ण ट्यूटोरियल
  का पालन करके छाया प्रभाव लागू करें, छाया प्रभाव बनाएं, और पेशेवर लुक के साथ Word
  दस्तावेज़ सहेजें।
og_image_alt: Screenshot illustrating how to add shadow to a Word shape using Python
og_title: Python का उपयोग करके Word आकृति में छाया कैसे जोड़ें – चरण‑दर‑चरण मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add shadow to a Word shape using Python – learn to apply shadow
    effect, create shadow effect, and save Word document efficiently.
  headline: How to add shadow to a Word shape using Python
  type: TechArticle
- description: How to add shadow to a Word shape using Python – learn to apply shadow
    effect, create shadow effect, and save Word document efficiently.
  name: How to add shadow to a Word shape using Python
  steps:
  - name: Load the Word document
    text: '```python import aspose.words as aw'
  - name: Retrieve the target shape
    text: '```python # Get the first shape in the document tree. shape = doc.get_child(aw.NodeType.SHAPE,
      0, True) ```'
  - name: Create a shadow object for the shape
    text: '```python # Instantiate a Shadow object and assign it to the shape. shape.shadow
      = aw.Shadow() ```'
  - name: Configure the shadow’s appearance
    text: '```python # Adjust the softness of the shadow edges. shape.shadow.blur
      = 5 # Higher values = softer edges'
  - name: Save the document to apply the changes
    text: '```python # Save the modified document. Overwrite or specify a new file
      name. doc.save("YOUR_DIRECTORY/output.docx") ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word:'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
- Document styling
title: Python का उपयोग करके Word आकृति में छाया कैसे जोड़ें
url: /hi/python/images-shapes/how-to-add-shadow-to-a-word-shape-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python का उपयोग करके Word आकार में छाया कैसे जोड़ें

यदि आपको Word दस्तावेज़ के भीतर किसी आकार में **छाया कैसे जोड़ें** की आवश्यकता है, तो यह गाइड आपको सटीक चरण दिखाता है। आप सीखेंगे कि छाया प्रभाव कैसे लागू करें, छाया प्रभाव कैसे बनाएं, और अपना IDE छोड़े बिना Word दस्तावेज़ कैसे सहेजें।

एक दृश्य छाया जोड़ने से आरेख, कॉलआउट और आइकॉन अधिक प्रमुख दिखते हैं, जिससे अंतिम उपयोगकर्ताओं के लिए पठनीयता बेहतर होती है। यह ट्यूटोरियल मानता है कि आपके पास बुनियादी Python ज्ञान है और Aspose.Words for Python लाइब्रेरी का नवीनतम संस्करण स्थापित है।

## Prerequisites

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

* Python 3.8 या उससे नया संस्करण स्थापित हो।
* `aspose-words` पैकेज (`pip install aspose-words`) – वह लाइब्रेरी जो DOCX फ़ाइलों को नियंत्रित करती है।
* एक Word दस्तावेज़ (`input.docx`) जिसमें कम से कम एक आकार हो (जैसे AutoShape या चित्र)।

ये आवश्यकताएँ सुनिश्चित करती हैं कि कोड Windows, macOS या Linux पर बिना बदलाव के चले।

## Word दस्तावेज़ में आकार में छाया कैसे जोड़ें

निम्नलिखित अनुभाग कार्य को स्पष्ट, क्रमांकित चरणों में विभाजित करते हैं। प्रत्येक चरण यह बताता है कि **क्यों** वह ऑपरेशन महत्वपूर्ण है, न कि केवल **क्या** टाइप करना है।

### Step 1: Load the Word document

```python
import aspose.words as aw

# Load the existing DOCX file. Replace YOUR_DIRECTORY with the actual path.
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*Why this matters:* दस्तावेज़ को लोड करने से एक इन‑मेमोरी प्रतिनिधित्व बनता है जिसे आप संशोधित कर सकते हैं। इस ऑब्जेक्ट के बिना आप आकारों तक पहुँच नहीं सकते या स्टाइलिंग लागू नहीं कर सकते।

### Step 2: Retrieve the target shape

```python
# Get the first shape in the document tree.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
```

*Why this matters:* `get_child` दस्तावेज़ नोड पदानुक्रम को पार करता है और अनुरोधित नोड प्रकार लौटाता है। तीसरा तर्क (`True`) Aspose.Words को पुनरावर्ती रूप से खोजने के लिए कहता है, जिससे आप वह आकार भी पा लेते हैं जो पैराग्राफ या तालिका के भीतर स्थित हो।

> **Pro tip:** यदि आपके दस्तावेज़ में कई आकार हैं, तो `doc.get_child_nodes(aw.NodeType.SHAPE, True)` के साथ इटररेट करें और इंडेक्स या `shape.title` या `shape.alt_text` की जाँच करके आवश्यक आकार चुनें।

### Step 3: Create a shadow object for the shape

```python
# Instantiate a Shadow object and assign it to the shape.
shape.shadow = aw.Shadow()
```

*Why this matters:* `Shadow` इंस्टेंस सभी दृश्य पैरामीटर (blur, distance, color आदि) रखता है। इसे आकार को असाइन करने से Word को दस्तावेज़ खोलते समय छाया रेंडर करने का निर्देश मिलता है।

### Step 4: Configure the shadow’s appearance

```python
# Adjust the softness of the shadow edges.
shape.shadow.blur = 5          # Higher values = softer edges

# Set how far the shadow is offset from the shape.
shape.shadow.distance = 3     # Measured in points

# Optional: change the shadow color to a light gray.
shape.shadow.color = aw.Color.gray

# Optional: set the shadow's transparency (0 = opaque, 255 = fully transparent).
shape.shadow.transparency = 50
```

*Why this matters:* `blur` छाया के प्रसार को नियंत्रित करता है, जबकि `distance` ऑफ़सेट निर्धारित करता है। इन मानों को समायोजित करने से आप सूक्ष्म लिफ्ट या नाटकीय ड्रॉप‑शैडो प्रभाव प्राप्त कर सकते हैं। `color` और `transparency` को बदलने से लुक और भी कस्टमाइज़ हो जाता है, जो कॉरपोरेट स्टाइल गाइड के अनुरूप होने पर आवश्यक है।

### Step 5: Save the document to apply the changes

```python
# Save the modified document. Overwrite or specify a new file name.
doc.save("YOUR_DIRECTORY/output.docx")
```

*Why this matters:* `save` मेथड इन‑मेमोरी बदलावों को वास्तविक DOCX फ़ाइल में लिखता है। सहेजने के बाद, `output.docx` को Microsoft Word में खोलने पर आकार पर कॉन्फ़िगर की गई छाया दिखाई देगी।

## Full script you can run today

नीचे पूरा, तैयार‑से‑चलाने वाला Python प्रोग्राम दिया गया है। `YOUR_DIRECTORY` को उस फ़ोल्डर से बदलें जहाँ आपकी फ़ाइलें स्थित हैं।

```python
import aspose.words as aw

# 1️⃣ Load the source document.
doc = aw.Document("YOUR_DIRECTORY/input.docx")

# 2️⃣ Retrieve the first shape (you can loop for multiple shapes).
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# 3️⃣ Attach a new Shadow object.
shape.shadow = aw.Shadow()

# 4️⃣ Configure shadow properties.
shape.shadow.blur = 5
shape.shadow.distance = 3
shape.shadow.color = aw.Color.gray
shape.shadow.transparency = 50

# 5️⃣ Save the updated document.
doc.save("YOUR_DIRECTORY/output.docx")
```

### Expected result

जब आप `output.docx` को Microsoft Word में खोलेंगे:

* पहला आकार तीन पॉइंट ऑफ़सेट के साथ एक नरम ग्रे छाया दिखाएगा।
* छाया के किनारे धुंधले दिखेंगे, जिससे आकार को हल्का त्रि‑आयामी लिफ्ट मिलेगा।
* दस्तावेज़ की अन्य कोई सामग्री नहीं बदलेगी।

यदि आपको छाया नहीं दिख रही है, तो जाँचें कि आकार कोई चित्र तो नहीं है जिसका ट्रांसपैरेंसी 100 % पर सेट है या दस्तावेज़ का व्यू मोड (Print Layout) सक्रिय है।

## Common variations and edge cases

| Situation | How to adapt the code |
|-----------|-----------------------|
| **Multiple shapes** | `doc.get_child_nodes(aw.NodeType.SHAPE, True)` का उपयोग करें और कलेक्शन पर इटररेट करके प्रत्येक आकार पर समान छाया कॉन्फ़िगरेशन लागू करें। |
| **Only certain shapes need a shadow** | लूप के भीतर `shape.name` या `shape.title` की जाँच करें और तभी छाया लागू करें जब नाम आपकी शर्तों से मेल खाता हो। |
| **Different shadow colors** | लाल छाया के लिए `shape.shadow.color = aw.Color(255, 0, 0)` सेट करें, या कस्टम अपारदर्शिता के लिए `aw.Color.from_argb(alpha, r, g, b)` का प्रयोग करें। |
| **No existing shape** | रिट्रीवल को `try/except` ब्लॉक में रखें; यदि `shape` `None` है, तो नया `Shape` (जैसे एक आयत) बनाकर दस्तावेज़ में जोड़ें और फिर छाया लागू करें। |
| **Saving to PDF** | छाया जोड़ने के बाद `doc.save("output.pdf")` कॉल करें – PDF निर्यात में छाया सही ढंग से रेंडर होगी। |

ये विविधताएँ सुनिश्चित करती हैं कि ट्यूटोरियल एकल टेम्पलेट या दस्तावेज़ों के बैच दोनों के लिए उपयोगी रहे।

## How to add shadow without Aspose.Words (alternative)

यदि आप `python-docx` लाइब्रेरी पसंद करते हैं, तो आप सीधे छाया सेट नहीं कर सकते क्योंकि यह लाइब्रेरी अंतर्निहित VML/OOXML छाया तत्वों को उजागर नहीं करती। ऐसे में आपको XML को मैन्युअल रूप से संशोधित करना होगा:

```python
from docx import Document
from lxml import etree

doc = Document("input.docx")
shape = doc.inline_shapes[0]._inline
# Insert <v:shadow> element here (complex XML manipulation)
```

क्योंकि Aspose.Words एक उच्च‑स्तरीय `Shadow` API प्रदान करता है, **छाया कैसे जोड़ें** इस लाइब्रेरी के साथ बहुत अधिक सरल है।

## Next steps

अब जब आप जानते हैं कि **छाया कैसे जोड़ें** आकार में, तो आप कर सकते हैं:

* **apply shadow effect** को टेबल या टेक्स्ट बॉक्स पर उसी `Shadow` क्लास का उपयोग करके लागू करें।
* **create shadow effect** विभिन्न blur और distance संयोजनों के साथ ब्रांडिंग उद्देश्यों के लिए बनाएं।
* **add shadow to shape** को अन्य फ़ॉर्मेटिंग विकल्पों जैसे लाइन वेट, फ़िल कलर और रोटेशन के साथ मिलाकर खोजें।
* फ़ोल्डर में मौजूद कई DOCX फ़ाइलों को पढ़कर, छाया लागू करके, और प्रत्येक को टाइम‑स्टैम्प वाले नाम से सहेजकर बुल्क प्रोसेसिंग को ऑटोमेट करें।

इन विस्तारों से आप एक पूर्ण‑फ़ीचर दस्तावेज़‑स्टाइलिंग पाइपलाइन बना सकते हैं जो कॉरपोरेट डिज़ाइन मानकों को पूरा करती है।

---

*आपने Python का उपयोग करके Word आकार में छाया कैसे जोड़ें, छाया प्रभाव कैसे लागू करें, छाया प्रभाव कैसे बनाएं, और नई स्टाइलिंग के साथ Word दस्तावेज़ कैसे सहेजें, यह सीख लिया है।* पैरामीटर के साथ प्रयोग करने में संकोच न करें, और अपने परिणाम टिप्पणियों में साझा करें!

## What Should You Learn Next?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API सुविधाओं में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण कर सकें।

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [How to Save Markdown from Word – Complete Python Guide](/words/english/python-net/document-conversion/how-to-save-markdown-from-word-complete-python-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}