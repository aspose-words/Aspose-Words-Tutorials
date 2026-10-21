---
category: general
date: 2026-10-16
description: एक खाली Word दस्तावेज़ बनाएं, Word में आकार डालें, बाहरी छाया जोड़ें,
  और Python का उपयोग करके PDF के रूप में सहेजें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert shape in word
- save as pdf python
- add outer shadow shape
- create pdf with shape
language: hi
lastmod: 2026-10-16
og_description: Aspose.Words for Python का उपयोग करके बाहरी शैडो आकार के साथ एक खाली
  Word दस्तावेज़ बनाएं। यह गाइड दिखाता है कि कैसे आकार डालें, शैडो लागू करें, और फ़ाइल
  को PDF के रूप में सहेजें।
og_image_alt: Screenshot of a Word document containing a rectangle shape with an outer
  shadow, saved as PDF
og_title: आकार की छाया के साथ खाली Word दस्तावेज़ बनाएं – Python गाइड
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document, insert shape in Word, add outer shadow,
    and save as PDF using Python.
  headline: Create blank Word document with shadowed shape in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- PDF generation
- Shape styling
title: Python में छाया वाले आकार के साथ खाली Word दस्तावेज़ बनाएं
url: /hi/python/word-automation/create-blank-word-document-with-shadowed-shape-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ब्लैंक Word दस्तावेज़ बनाएं जिसमें शैडो वाला आकार हो Python में

यदि आपको **ब्लैंक Word दस्तावेज़** बनाना है और एक कस्टम ग्राफिक जोड़ना है, तो यह गाइड आपके लिए है। हम आपको दिखाएंगे कि **Word में shape कैसे insert करें**, **outer shadow shape** लागू करें, और अंत में **Python का उपयोग करके PDF के रूप में save करें**।

आप सीखेंगे कि Aspose.Words for Python को कैसे सेटअप करें, एक rectangle बनाएं, उसकी shadow को style करें, और एक PDF जनरेट करें जो विज़ुअल इफ़ेक्ट को बरकरार रखे। Aspose API का कोई पूर्व अनुभव आवश्यक नहीं है, लेकिन आपके पास बुनियादी Python ज्ञान और Python 3.10 या बाद का कार्यशील इंस्टॉलेशन होना चाहिए।

## आवश्यकताएँ

* Python 3.10 या नया स्थापित हो।
* एक सक्रिय Aspose.Words for Python लाइसेंस (मुफ़्त ट्रायल मूल्यांकन के लिए काम करता है)।
* `pip` एक्सेस ताकि `aspose-words` पैकेज इंस्टॉल कर सकें।
* उस डायरेक्टरी में लिखने की अनुमति जहाँ PDF सेव किया जाएगा।

आप एक ही कमांड से लाइब्रेरी इंस्टॉल कर सकते हैं:

```bash
pip install aspose-words
```

## ब्लैंक Word दस्तावेज़ बनाएं – पर्यावरण सेटअप

पहला कदम एक खाली Word फ़ाइल बनाना है जो shape के लिए कैनवास के रूप में काम करेगी।

```python
import aspose.words as aw

# Initialize a new, empty document
doc = aw.Document()
# DocumentBuilder provides convenient methods for adding content
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` एक पूरी तरह से ब्लैंक Word फ़ाइल को दर्शाता है। `DocumentBuilder` का उपयोग करके आप `insert_shape` जैसे मेथड्स तक पहुंच प्राप्त करते हैं, जिन्हें हम अगले कदम में उपयोग करेंगे।

## Word में shape insert करें और आयाम सेट करें

अब हम एक rectangle जोड़ते हैं जो बाद में outer shadow प्राप्त करेगा। आकार पॉइंट्स में व्यक्त किया जाता है (1 pt ≈ 1/72 इंच)।

```python
# Insert a rectangle shape with a width of 200 pt and a height of 100 pt
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)
```

`insert_shape` कॉल एक `Shape` ऑब्जेक्ट रिटर्न करता है जिसे आप आगे कस्टमाइज़ कर सकते हैं। इस चरण पर दस्तावेज़ में Microsoft Word में खोलने पर एक दृश्यमान rectangle पहले से ही मौजूद है।

## outer shadow shape जोड़ें – इफ़ेक्ट को कस्टमाइज़ करना

Aspose.Words एक `ShadowEffect` क्लास प्रदान करता है जिससे आप shadow की प्रॉपर्टीज़ जैसे style, blur, distance, और color को परिभाषित कर सकते हैं।

```python
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a new shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # Choose an outer shadow
shadow.blur = 5.0                         # Softness of the shadow edges
shadow.distance = 3.0                     # Offset distance from the shape
shadow.color = aw.Color.black             # Shadow color

# Apply the shadow to the rectangle
rectangle.shadow = shadow
```

`style` को `OUTER` सेट करने से shadow rectangle की बॉर्डर के बाहर दिखाई देगा, जिससे एक सूक्ष्म 3‑D लुक मिलेगा। आप `blur` और `distance` के साथ प्रयोग करके अधिक टाइट या अधिक डिफ्यूज़्ड shadow प्राप्त कर सकते हैं।

## PDF के रूप में save करें python – दस्तावेज़ को अंतिम रूप देना

shape को स्टाइल करने के बाद, दस्तावेज़ को सीधे PDF के रूप में सेव किया जा सकता है। Aspose.Words आंतरिक रूप से कन्वर्ज़न संभालता है, जिससे shadow इफ़ेक्ट बरकरार रहता है।

```python
output_path = "output/shape_with_shadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

जब आप किसी भी PDF व्यूअर में `shape_with_shadow.pdf` खोलेंगे, तो आपको rectangle के साथ outer shadow वही दिखेगा जैसा कि वह Word में दिखाई देता था।

## पूर्ण कार्यशील उदाहरण

नीचे वह पूर्ण स्क्रिप्ट है जो सभी चरणों को मिलाती है। इसे `create_word_with_shadow.py` नाम की फ़ाइल में कॉपी करें और चलाएँ।

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1. Create a blank Word document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2. Insert a rectangle shape
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)

# 3. Define and apply an outer shadow
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER
shadow.blur = 5.0
shadow.distance = 3.0
shadow.color = aw.Color.black
rectangle.shadow = shadow

# 4. Save the document as PDF
pdf_path = os.path.join(output_dir, "shape_with_shadow.pdf")
doc.save(pdf_path)

print(f"PDF generated at: {pdf_path}")
```

**अपेक्षित आउटपुट**

स्क्रिप्ट चलाने पर एक पुष्टि लाइन प्रिंट होती है, उदाहरण के लिए:

```
PDF generated at: output/shape_with_shadow.pdf
```

परिणामी PDF खोलने पर एक सिंगल पेज दिखेगा जिसमें 200 pt × 100 pt का rectangle एक सॉफ्ट ब्लैक outer shadow के साथ होगा।

## सामान्य विविधताएँ और किनारे के मामले

* **शैडो का रंग बदलना** – `aw.Color.black` को किसी अन्य `aw.Color` वैल्यू से बदलें, जैसे `aw.Color.red` या `aw.Color.from_argb(255, 0, 120, 215)`।
* **विभिन्न shape का उपयोग करना** – `aw.drawing.ShapeType.RECTANGLE` को `OVAL`, `DIAMOND`, या किसी भी समर्थित enum वैल्यू में बदलें।
* **PDF के बजाय DOCX के रूप में save करना** – Word फ़ॉर्मेट रखने के लिए `doc.save("output/shape.docx")` कॉल करें।
* **एकाधिक shapes** – `builder.insert_shape` को फिर से कॉल करके अतिरिक्त shapes बनाएं; प्रत्येक shape का अपना `ShadowEffect` हो सकता है।

**प्रो टिप:** यदि आपको shape को किसी विशिष्ट स्थान पर रखना है, तो insertion के बाद `rectangle.left` और `rectangle.top` सेट करें। इससे आपको प्लेसमेंट पर पिक्सेल‑परफेक्ट कंट्रोल मिलता है।

## निष्कर्ष

अब आप जानते हैं कि **ब्लैंक Word दस्तावेज़ कैसे बनाएं**, **Word में shape कैसे insert करें**, **outer shadow shape कैसे जोड़ें**, और **Python का उपयोग करके PDF के रूप में कैसे save करें**। पूर्ण कोड सैंपल एंड‑टू‑एंड वर्कफ़्लो को दर्शाता है, और व्याख्याएँ स्पष्ट करती हैं कि प्रत्येक API कॉल क्यों आवश्यक है।

अब आप अधिक उन्नत स्टाइलिंग विकल्पों का अन्वेषण कर सकते हैं, shape के अंदर टेक्स्ट जोड़ सकते हैं, या कई shapes को मिलाकर जटिल डायग्राम बना सकते हैं। विभिन्न shadow पैरामीटर्स के साथ प्रयोग करें ताकि वे आपके ब्रांड की विज़ुअल लैंग्वेज से मेल खाएँ, और इस दृष्टिकोण को बड़े दस्तावेज़‑जनरेशन पाइपलाइन में इंटीग्रेट करें।

कोडिंग का आनंद लें!

## अब आपको क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोच को एक्सप्लोर करने में मदद करेंगे।

- [Rectangle shape बनाएं, शैडो जोड़ें और PDF सेव करें](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Word से PDF बनाएं – Aspose.Words के साथ पूर्ण Python गाइड](/words/english/python-net/document-conversion/create-pdf-from-word-complete-python-guide-with-aspose-words/)
- [Word में Shape में Shadow जोड़ें Aspose.Words के साथ – चरण‑दर‑चरण](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}