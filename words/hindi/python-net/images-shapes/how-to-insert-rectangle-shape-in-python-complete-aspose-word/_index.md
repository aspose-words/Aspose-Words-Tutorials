---
category: general
date: 2026-06-27
description: Aspose.Words का उपयोग करके Python में आयताकार आकार कैसे डालें, शैडो का
  रंग बदलें, बाहरी शैडो जोड़ें, और आकार पर शैडो प्रभाव लागू करें—सब कुछ एक ही ट्यूटोरियल
  में सीखें।
draft: false
keywords:
- how to insert rectangle shape
- how to change shadow color
- how to add outer shadow
- apply shadow effect to shape
language: hi
og_description: Python में आयताकार आकार कैसे डालें, उसकी छाया का रंग बदलें, बाहरी
  छाया जोड़ें, और Aspose.Words के साथ आकार पर छाया प्रभाव लागू करना सीखें।
og_title: Python में आयताकार आकार कैसे डालें – Aspose.Words ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  headline: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  name: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: Pro tip
    text: If you need the rectangle positioned at a specific location, use `builder.move_to`
      before inserting, or adjust `rectangle.left` and `rectangle.top` after creation.
  - name: Edge case
    text: If you forget to set `shadow.opacity`, the default is fully opaque, which
      can make the shadow look like a solid shape. Always pair a color change with
      an appropriate opacity level.
  - name: Common pitfalls
    text: '- **Missing directory:** `doc.save` will raise an error if the folder doesn’t
      exist. Create it first or use `os.makedirs`. - **Version mismatch:** The shadow
      API requires Aspose.Words 22.9+; older versions silently ignore shadow settings.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: Python में आयताकार आकार कैसे डालें – पूर्ण Aspose.Words गाइड
url: /hi/python/images-shapes/how-to-insert-rectangle-shape-in-python-complete-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide

क्या आपने कभी **Python** का उपयोग करके Word दस्तावेज़ में **rectangle shape** डालने के बारे में सोचा है? आप अकेले नहीं हैं—कई डेवलपर्स रिपोर्ट ऑटोमेट करने या टेम्प्लेट बनाने के दौरान इस समस्या का सामना करते हैं। अच्छी खबर यह है कि Aspose.Words इसे बहुत आसान बनाता है, और इस ट्यूटोरियल में हम पूरी प्रक्रिया को कवर करेंगे, यानी rectangle को ड्रॉ करने से लेकर उसे एक सुन्दर outer shadow देने तक।

हम यह भी बताएँगे **shadow color कैसे बदलें**, **outer shadow कैसे जोड़ें**, और अंतिम चरण **shape पर shadow effect कैसे लागू करें**। अंत तक, आपके पास एक पूरी‑स्टाइल्ड rectangle होगा जिसे आप प्रोग्रामेटिकली किसी भी .docx फ़ाइल में डाल सकते हैं।

## Prerequisites

- आपके मशीन पर Python 3.8+ स्थापित हो  
- `pip install aspose-words` के माध्यम से Aspose.Words for Python स्थापित हो  
- Python स्क्रिप्टिंग की बुनियादी समझ (Word‑API का गहरा ज्ञान आवश्यक नहीं)  

यदि आपके पास ये सब है, तो चलिए शुरू करते हैं। यदि नहीं, तो पहले लाइब्रेरी प्राप्त करें; बाकी गाइड मानता है कि इम्पोर्ट बिना समस्या के काम करता है।

## How to Insert Rectangle Shape with Aspose.Words for Python

पहला कदम वही है जो मुख्य कीवर्ड वादा करता है: **how to insert rectangle shape**। हम एक नया दस्तावेज़ बनाएँगे, एक `DocumentBuilder` बनायेंगे, और पेज पर एक rectangle डालेंगे।

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a fresh document and a builder to add content
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle shape of 200x100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Optional: give the rectangle a light fill so the shadow is visible
rectangle.fill_color = aw.drawing.Color.light_blue
```

> **Why this matters:** `insert_shape` कॉल *how to insert rectangle shape* का मुख्य भाग है। यह एक `Shape` ऑब्जेक्ट लौटाता है जिसे आप बाद में आकार, स्थिति, fill, borders आदि के लिए बदल सकते हैं। हमने `fill_color` भी सेट किया है; इसके बिना shadow सफ़ेद पेज में मिलकर दिखाई नहीं देगा।

### Pro tip
यदि आपको rectangle को किसी विशिष्ट स्थान पर रखना है, तो `builder.move_to` का उपयोग करके डालने से पहले या निर्माण के बाद `rectangle.left` और `rectangle.top` को समायोजित करें।

## Changing the Shadow Color of a Shape

अब rectangle दस्तावेज़ में मौजूद है, चलिए **how to change shadow color** का उत्तर देते हैं। Aspose.Words एक `ShadowEffect` ऑब्जेक्ट प्रदान करता है जहाँ आप `color` प्रॉपर्टी को किसी भी RGB वैल्यू पर सेट कर सकते हैं।

```python
# Create a shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # we’ll also cover outer shadow later
shadow.blur_radius = 8.0                  # smooth edges
shadow.distance = 6.0                     # how far the shadow sits from the shape
shadow.direction = 45                     # angle in degrees
shadow.opacity = 0.6                      # semi‑transparent

# Change the shadow color to a deep gray instead of black
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)

# Apply the shadow to our rectangle
rectangle.shadow = shadow
```

> **Why you’d want this:** एक गहरा काला shadow बहुत कठोर लग सकता है, विशेषकर हल्के‑रंग के दस्तावेज़ों में। रंग बदलने से आप कॉरपोरेट ब्रांडिंग से मेल खा सकते हैं या सिर्फ़ एक नरम दृश्य प्रभाव प्राप्त कर सकते हैं।

### Edge case
यदि आप `shadow.opacity` सेट करना भूल जाते हैं, तो डिफ़ॉल्ट रूप से यह पूरी तरह opaque रहेगा, जिससे shadow एक ठोस shape जैसा दिखेगा। हमेशा रंग परिवर्तन के साथ उपयुक्त opacity लेवल जोड़ें।

## Adding an Outer Shadow Effect

अगला अक्सर पूछे जाने वाला प्रश्न है **how to add outer shadow**। `ShadowStyle.OUTER` फ़्लैग Aspose.Words को shape की outline के बाहर shadow रेंडर करने के लिए बताता है, अंदर नहीं।

ऊपर दिया गया कोड स्निपेट पहले से ही `ShadowStyle.OUTER` का उपयोग करता है, लेकिन स्पष्टता के लिए इसे अलग से दिखाते हैं:

```python
# Ensure the shadow style is outer
shadow.style = ShadowStyle.OUTER
```

यदि आप `ShadowStyle.INNER` पर स्विच करते हैं, तो shadow *rectangle के अंदर* दिखाई देगा, जो embossing प्रभाव के लिए उपयोगी है। अधिकांश दस्तावेज़‑डिज़ाइन परिदृश्यों में, outer style एक प्राकृतिक ड्रॉप‑shadow लुक देता है।

## Applying the Shadow Effect to Your Shape

हमने पहले ही `rectangle.shadow = shadow` असाइन करके **apply shadow effect to shape** किया है। अब सब कुछ एक साथ रखें और दस्तावेज़ को सेव करें, यह सुनिश्चित करते हुए कि प्रभाव बना रहे।

```python
# Save the document – choose a folder you have write access to
output_path = "output/RectangleWithShadow.docx"
doc.save(output_path)

print(f"Document saved to {output_path}. Open it to see the rectangle with its outer shadow.")
```

जब आप `RectangleWithShadow.docx` को Microsoft Word में खोलेंगे, तो आपको एक हल्के‑नीले rectangle के साथ एक सूक्ष्म ग्रे outer shadow 45° कोण पर दिखाई देगा। shadow थोड़ा ब्लर और ऑफ़सेट होगा, बिल्कुल जैसा हमने कॉन्फ़िगर किया था।

### Common pitfalls
- **Missing directory:** `doc.save` फ़ोल्डर न होने पर एरर देगा। पहले इसे बनाएं या `os.makedirs` का उपयोग करें।
- **Version mismatch:** shadow API को Aspose.Words 22.9+ चाहिए; पुराने संस्करण shadow सेटिंग्स को चुपचाप अनदेखा कर देंगे।

## Full Working Example

नीचे पूरा, तैयार‑to‑run स्क्रिप्ट है जो सभी चरणों को मिलाता है। इसे `rectangle_shadow.py` नाम की फ़ाइल में कॉपी‑पेस्ट करें और `python rectangle_shadow.py` से चलाएँ।

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Create a new document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2️⃣ Insert the rectangle shape (how to insert rectangle shape)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle.fill_color = aw.drawing.Color.light_blue   # make the shape visible

# 3️⃣ Define the shadow (how to change shadow color, how to add outer shadow)
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # outer shadow
shadow.blur_radius = 8.0
shadow.distance = 6.0
shadow.direction = 45
shadow.opacity = 0.6
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)  # custom gray

# 4️⃣ Apply the shadow (apply shadow effect to shape)
rectangle.shadow = shadow

# 5️⃣ Save the file
output_path = os.path.join(output_dir, "RectangleWithShadow.docx")
doc.save(output_path)

print(f"✅ Document generated: {output_path}")
```

**Expected output:** एक Word दस्तावेज़ (`RectangleWithShadow.docx`) जिसमें एकल rectangle के साथ ग्रे outer shadow होगा। प्रभाव को सत्यापित करने के लिए Word में खोलें।

## Frequently Asked Questions

| Question | Answer |
|----------|--------|
| *Can I use a different shape type?* | बिल्कुल—`ShapeType.RECTANGLE` को `ShapeType.OVAL`, `ShapeType.TRIANGLE` आदि से बदलें, और वही shadow लॉजिक लागू होगा। |
| *What if I need a thicker border?* | `rectangle.line_width = 2.0` (points) को shadow लागू करने से पहले सेट करें। |
| *Is it possible to animate the shadow?* | सीधे Aspose.Words से नहीं; एनीमेशन के लिए आपको HTML/CSS में एक्सपोर्ट करना पड़ेगा। |
| *Does this work on macOS?* | हाँ—Aspose.Words प्लेटफ़ॉर्म‑अज्ञेय है जब तक Python चल रहा हो। |

## Conclusion

हमने **how to insert rectangle shape** को समझा, **how to change shadow color** दिखाया, **how to add outer shadow** समझाया, और अंत में **apply shadow effect to shape** को लागू किया Aspose.Words for Python का उपयोग करके। पूरा स्क्रिप्ट किसी भी ऑटोमेशन पाइपलाइन में डालने के लिए तैयार है, जिससे आप सेकंडों में एक प्रोफ़ेशनल‑लुकिंग rectangle के साथ पॉलिश्ड shadow प्राप्त कर सकते हैं।

अगला कदम क्या है? fill color बदलें, विभिन्न `direction` एंगल के साथ प्रयोग करें, या एक ही पेज पर कई shapes जोड़ें। आप Aspose.Words के रिच टेक्स्ट‑फ़ॉर्मेटिंग API को भी एक्सप्लोर कर सकते हैं ताकि shadows को styled text के साथ मिलाकर आकर्षक रिपोर्ट बना सकें।

यदि आपको यह ट्यूटोरियल उपयोगी लगा, तो इसे थम्स‑अप दें, टीम के साथ शेयर करें, या अपने स्वयं के वैरिएशन के साथ कमेंट छोड़ें। Happy coding!

![Diagram showing how to insert rectangle shape with an outer shadow applied in a Word document](/images/rectangle-shadow.png)


## What Should You Learn Next?


नीचे दिए गए ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑बद्ध व्याख्याएँ हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ को एक्सप्लोर करने में मदद करेंगे।

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}