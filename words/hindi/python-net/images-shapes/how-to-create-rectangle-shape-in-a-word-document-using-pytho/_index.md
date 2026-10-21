---
category: general
date: 2026-09-30
description: Aspose.Words for Python का उपयोग करके आयताकार आकार बनाना, आकार पर छाया
  लागू करना, और आकार के साथ Word को सहेजना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- how to add shape
- apply shadow to shape
- set shadow blur
- save word with shape
language: hi
lastmod: 2026-09-30
og_description: Word दस्तावेज़ में जल्दी से आयताकार आकार बनाएं। यह ट्यूटोरियल दिखाता
  है कि कैसे आकार जोड़ें, आकार पर छाया लागू करें, छाया ब्लर सेट करें, और आकार के साथ
  Word सहेजें।
og_image_alt: Screenshot of a Word document showing a rectangle shape with a soft
  shadow
og_title: Python के साथ Word में आयताकार आकार बनाएं – चरण‑दर‑चरण गाइड
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Learn how to create rectangle shape, apply shadow to shape, and save
    Word with shape using Aspose.Words for Python.
  headline: How to create rectangle shape in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- Shapes
title: Python का उपयोग करके Word दस्तावेज़ में आयताकार आकार कैसे बनाएं
url: /hi/python/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python का उपयोग करके Word दस्तावेज़ में आयताकार आकार कैसे बनाएं

यदि आपको Word फ़ाइल में **आयताकार आकार बनाना** है, तो यह गाइड आपको एक पूर्ण, चलाने योग्य समाधान दिखाता है। आप देखेंगे कि आकार कैसे जोड़ें, शैडो इफ़ेक्ट कैसे लागू करें, ब्लर को कैसे समायोजित करें, और अंत में **आकार के साथ Word सहेजें** ताकि परिणाम को Microsoft Word या किसी भी संगत व्यूअर में खोला जा सके।

उदाहरण में **Aspose.Words for Python via .NET** का उपयोग किया गया है, जो एक लाइब्रेरी है जो आपको Microsoft Office स्थापित किए बिना Word दस्तावेज़ों को नियंत्रित करने देती है। API का पूर्व अनुभव आवश्यक नहीं है—सिर्फ बुनियादी Python ज्ञान चाहिए।

## आप क्या हासिल करेंगे

- नए दस्तावेज़ के पहले सेक्शन में एक आयत जोड़ें।  
- ब्लर, ऑफ़सेट और रंग सेट करके एक सॉफ्ट शैडो कॉन्फ़िगर करें।  
- दस्तावेज़ को डिस्क पर सहेजें और दृश्य परिणाम की पुष्टि करें।

## आवश्यकताएँ

- Python 3.8 या उससे नया संस्करण।  
- `aspose-words` पैकेज स्थापित हो (`pip install aspose-words`).  
- आउटपुट डायरेक्टरी में लिखने की अनुमति।

## आयताकार आकार बनाएं और उसकी उपस्थिति कॉन्फ़िगर करें

पहला कदम एक खाली दस्तावेज़ बनाना और उसमें आयताकार आकार जोड़ना है। यह आकार शैडो इफ़ेक्ट के लिए कैनवास के रूप में कार्य करेगा।

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Step 1: Create a new blank document
doc = aw.Document()

# Step 2: Add a rectangle shape to the first section
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Optional: Define the shape’s size and position (in points)
shape.width = aw.ConvertUtil.inch_to_point(2)   # 2 inches wide
shape.height = aw.ConvertUtil.inch_to_point(1)  # 1 inch tall
shape.left = aw.ConvertUtil.inch_to_point(1)    # 1 inch from the left margin
shape.top = aw.ConvertUtil.inch_to_point(1)     # 1 inch from the top margin
```

**यह क्यों महत्वपूर्ण है:**  
आयत बनाकर आपको एक ठोस ऑब्जेक्ट (`shape`) मिलता है जिसे आप बाद में स्टाइल कर सकते हैं। स्पष्ट आयाम सेट करने से सुनिश्चित होता है कि आकार हर प्लेटफ़ॉर्म पर समान दिखे।

## Word दस्तावेज़ में आकार कैसे जोड़ें

जबकि ऊपर का कोड पहले से ही आयत जोड़ता है, आपको बाद में अतिरिक्त आकार (जैसे, वृत्त, तीर) जोड़ने की आवश्यकता हो सकती है। वही पैटर्न लागू होता है: दस्तावेज़ के बॉडी पर `append_child` कॉल करें और वांछित `ShapeType` पास करें।

```python
# Example: Adding a second shape – an ellipse
ellipse = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.ELLIPSE)
)
ellipse.width = aw.ConvertUtil.inch_to_point(1.5)
ellipse.height = aw.ConvertUtil.inch_to_point(1)
ellipse.left = aw.ConvertUtil.inch_to_point(3.5)
ellipse.top = aw.ConvertUtil.inch_to_point(1)
```

**टिप:** सभी समर्थित आकारों को खोजने के लिए `ShapeType` एनेमरेशन का उपयोग करें। यह आपके कोड को पढ़ने योग्य रखता है और मैजिक नंबरों से बचाता है।

## आकार पर शैडो लागू करें और शैडो ब्लर सेट करें

शैडो गहराई और दृश्य आकर्षण जोड़ता है। `ShadowEffect` क्लास आपको ब्लर, ऑफ़सेट और रंग नियंत्रित करने देती है। नीचे हम आयत पर एक सॉफ्ट ब्लैक शैडो लागू करते हैं।

```python
# Step 3: Configure a shadow effect for the rectangle
shadow = ShadowEffect()
shadow.blur = 5.0          # Sets the softness of the shadow edge
shadow.offset_x = 2.0      # Horizontal displacement from the shape
shadow.offset_y = 2.0      # Vertical displacement from the shape
shadow.color = aw.Color.black

# Step 4: Apply the shadow effect to the shape
shape.shadow = shadow
```

**ब्लर क्यों सेट करें?**  
`blur` निर्धारित करता है कि शैडो कितनी फैलावदार दिखे। कम मान (जैसे 1.0) तेज़ किनारा देता है, जबकि उच्च मान (जैसे 5.0) एक नरम फेड बनाता है, जो अक्सर अधिक सौंदर्यपूर्ण लगता है।

**एज केस:** यदि आप `blur` को 0 सेट करते हैं, तो शैडो एक ठोस सिल्हूट बन जाता है। कुछ व्यूअर इसे एलिएसिंग आर्टिफैक्ट्स के साथ रेंडर कर सकते हैं, इसलिए स्मूद आउटपुट के लिए 0 से बड़ा मान चुनें।

## आकार के साथ Word सहेजें

दस्तावेज़ को स्थायी बनाना सभी बदलावों को अंतिम रूप देता है। `save` मेथड एक `.docx` फ़ाइल लिखता है जिसे कोई भी आधुनिक Word प्रोसेसर खोल सकता है।

```python
# Step 5: Save the document to see the result
output_path = "output.docx"   # Adjust the path as needed
doc.save(output_path)
print(f"Document saved to {output_path}")
```

जब आप `output.docx` खोलेंगे, तो आपको एक आयत दिखेगा जो शीर्ष‑बाएँ कोने से एक इंच की दूरी पर स्थित है, साथ ही एक सॉफ्ट ब्लैक शैडो जो दो पॉइंट दाएँ और नीचे स्थानांतरित है। शैडो का ब्लर इसे ऐसा दिखाता है जैसे आकार पृष्ठ से उठाया गया हो।

**प्रो टिप:** यदि आपको लूप में कई दस्तावेज़ बनाने हैं, तो वही `Document` इंस्टेंस पुन: उपयोग करें और प्रत्येक इटरशन के बीच उसके बॉडी को साफ़ करें ताकि मेमोरी ओवरहेड कम हो।

## सामान्य विविधताएँ और समस्या निवारण

| Situation | What to change | Reason |
|-----------|----------------|--------|
| विभिन्न शैडो रंग | `shadow.color = aw.Color.red` | ब्रांड रंगों का उपयोग करें या महत्वपूर्ण आकारों को हाइलाइट करें। |
| बड़ा शैडो ऑफ़सेट | Increase `shadow.offset_x`/`offset_y` | UI मॉक‑अप के लिए गहराई को उजागर करें। |
| बिल्कुल शैडो नहीं | Omit the `shape.shadow = shadow` line | मिनिमलिस्ट रिपोर्टों के लिए उपयोगी। |
| DOCX के बजाय PDF निर्यात करें | `doc.save("output.pdf")` | PDF पढ़ने‑के‑लिए‑केवल वितरण के लिए आदर्श है। |

यदि आकार दिखाई नहीं देता है, तो सुनिश्चित करें कि आप इसे सही सेक्शन (`get_first_section()`) में जोड़ रहे हैं और संशोधनों के बाद दस्तावेज़ सहेजा गया है।

## पूर्ण, चलाने योग्य उदाहरण

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Create a new blank document
doc = aw.Document()

# Add a rectangle shape
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
shape.width = aw.ConvertUtil.inch_to_point(2)
shape.height = aw.ConvertUtil.inch_to_point(1)
shape.left = aw.ConvertUtil.inch_to_point(1)
shape.top = aw.ConvertUtil.inch_to_point(1)

# Configure and apply a shadow
shadow = ShadowEffect()
shadow.blur = 5.0
shadow.offset_x = 2.0
shadow.offset_y = 2.0
shadow.color = aw.Color.black
shape.shadow = shadow

# Save the document
output_path = "output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

स्क्रिप्ट चलाने से `output.docx` बनता है जिसमें सॉफ्ट शैडो वाला आयत होता है। फ़ाइल को Microsoft Word में खोलें ताकि यह पुष्टि हो सके कि दृश्य प्रभाव विवरण से मेल खाता है।

## निष्कर्ष

अब आप जानते हैं कि **आयताकार आकार कैसे बनाएं**, **Word दस्तावेज़ में आकार कैसे जोड़ें**, **आकार पर शैडो कैसे लागू करें**, **शैडो ब्लर कैसे सेट करें**, और अंत में **Aspose.Words for Python** का उपयोग करके **आकार के साथ Word कैसे सहेजें**। वही पैटर्न अन्य आकार प्रकार, रंग और इफ़ेक्ट्स तक विस्तारित किया जा सकता है, जिससे आप Office ऑटोमेशन पर निर्भर हुए बिना दस्तावेज़ ग्राफ़िक्स पर पूर्ण नियंत्रण प्राप्त कर सकते हैं।

**अगले कदम**

- `Shape.fill` के साथ प्रयोग करें ताकि ग्रेडिएंट या चित्र पृष्ठभूमि जोड़ सकें।  
- `Paragraph` ऑब्जेक्ट्स का उपयोग करके आयत के अंदर टेक्स्ट रखें।  
- एकाधिक आकारों को मिलाकर जटिल डायग्राम बनाएं, फिर वितरण के लिए PDF में निर्यात करें।  

कोड को अपनी रिपोर्टिंग या टेम्प्लेटिंग आवश्यकताओं के अनुसार अनुकूलित करने में संकोच न करें, और अपने परिणाम कमेंट्स में साझा करें!

## अब आपको क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण-दर-चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का पता लगाने में मदद करती हैं।

- [Word दस्तावेज़ जावा बनाएं – शैडो इफ़ेक्ट के साथ आयताकार आकार जोड़ें](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [आयताकार आकार बनाएं, शैडो जोड़ें और PDF सहेजें](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Aspose.Words Shape Shadow ट्यूटोरियल – C# में Word आकार में शैडो जोड़ें](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}