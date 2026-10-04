---
category: general
date: 2026-10-04
description: Python में दस्तावेज़ कैसे बनाएं और Aspose.Words का उपयोग करके आकार पर
  छाया जोड़ें। छाया का रंग सेट करना, आयताकार आकार डालना, और बाहरी छाया को अनुकूलित
  करना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create document
- add shadow to shape
- set shadow color
- insert rectangle shape
- how to add shadow
language: hi
lastmod: 2026-10-04
og_description: Python में दस्तावेज़ कैसे बनाएं और आकार पर छाया जोड़ें। यह गाइड आपको
  दिखाता है कि कैसे छाया का रंग सेट करें, आयताकार आकार डालें, और Aspose.Words का उपयोग
  करके बाहरी छाया लागू करें।
og_image_alt: Python code inserting a rectangle shape with a visible shadow into a
  Word document
og_title: Python में आयताकार आकार और छाया के साथ दस्तावेज़ कैसे बनाएं
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  headline: How to create document with a rectangle shape and shadow in Python
  type: TechArticle
- description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  name: How to create document with a rectangle shape and shadow in Python
  steps:
  - name: Why does the shadow sometimes appear invisible?
    text: The shadow is only rendered if `shadow.visible` is set to `True` **and**
      the shape’s `wrap_type` allows it to be displayed. An inline shape works reliably;
      floating shapes may require additional layout adjustments.
  - name: How can I change the shadow color to match a brand palette?
    text: 'Replace `aw.drawing.Color.black` with a custom RGB value:'
  - name: What if I need the shape to appear behind text?
    text: Set the wrap type to `WrapType.BEHIND` and adjust the `z_order_position`
      if necessary. Keep in mind that some viewers may render behind‑text shapes differently.
  - name: Can I apply the same shadow settings to multiple shapes?
    text: Yes. Create a helper function that configures the shadow and call it for
      each shape you insert. This promotes code reuse and ensures consistent styling.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Python में आयत आकार और छाया के साथ दस्तावेज़ कैसे बनाएं
url: /hi/python/images-shapes/how-to-create-document-with-a-rectangle-shape-and-shadow-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python में आयताकार आकार और छाया के साथ दस्तावेज़ कैसे बनाएं

यदि आपको एक स्टाइल्ड आयताकार वाला **how to create document** चाहिए, तो यह गाइड एक पूर्ण समाधान प्रदान करता है। आप देखेंगे कि **add shadow to shape** कैसे किया जाता है, छाया का रंग कैसे सेट किया जाता है, और उसके ऑफ़सेट और ब्लर को कैसे नियंत्रित किया जाता है—सभी Aspose.Words for Python के साथ। ट्यूटोरियल के अंत तक आप एक `.docx` फ़ाइल बना सकते हैं जो परिष्कृत दिखती है और वितरण के लिए तैयार है।

नीचे दिए गए चरण लाइब्रेरी को इंस्टॉल करने से लेकर छाया की उपस्थिति को कस्टमाइज़ करने तक सब कुछ कवर करते हैं। बाहरी दस्तावेज़ीकरण की आवश्यकता नहीं है; कोड कॉपी, रन और अपने प्रोजेक्ट्स में अनुकूलित करने के लिए तैयार है। आप यह भी सीखेंगे कि **insert rectangle shape** कैसे किया जाता है, **outer shadow style** कैसे चुना जाता है, और सामान्य समस्याओं जैसे अदृश्य छाया या गलत रैप सेटिंग्स को कैसे संभालें।

## आवश्यकताएँ

* Python 3.8 या नया स्थापित हो।
* एक सक्रिय Aspose.Words for Python लाइसेंस (या एक मुफ्त इवैल्यूएशन की)।
* Python स्क्रिप्टिंग की बुनियादी समझ।
* उस फ़ाइल सिस्टम स्थान तक पहुंच जहाँ उत्पन्न दस्तावेज़ सहेजा जाएगा।

आप pip के साथ SDK इंस्टॉल कर सकते हैं:

```bash
pip install aspose-words
```

## चरण 1: लाइब्रेरी इम्पोर्ट करें और नया खाली दस्तावेज़ बनाएं

एक नया दस्तावेज़ बनाना किसी भी Word ऑटोमेशन परिदृश्य में पहला कार्य है। `aw.Document()` कंस्ट्रक्टर आपको एक खाली फ़ाइल देता है जिसे आप टेक्स्ट, इमेज या शैप्स से भर सकते हैं।

```python
import aspose.words as aw

# Create a new blank document
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

`DocumentBuilder` ऑब्जेक्ट कंटेंट इन्सर्शन को सरल बनाता है। यह वर्तमान कर्सर पोज़िशन का ट्रैक रखता है, इसलिए आप सेक्शन को मैन्युअली मैनेज किए बिना क्रमिक रूप से एलिमेंट जोड़ सकते हैं।

## चरण 2: इच्छित आकार का आयताकार आकार सम्मिलित करें

एक आयताकार आकार विज़ुअल एलिमेंट्स के लिए कंटेनर के रूप में कार्य करता है। आप इसकी चौड़ाई और ऊँचाई पॉइंट्स में परिभाषित कर सकते हैं (1 pt ≈ 1/72 in)।

```python
# Insert a rectangle shape that is 150 pt wide and 80 pt tall
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

इस चरण पर आकार में कोई विज़ुअल स्टाइलिंग नहीं है, इसलिए यह एक साधारण रूपरेखा के रूप में दिखता है। अगले चरण इसे गहराई और रंग देंगे।

## चरण 3: आकार को आसपास के टेक्स्ट के साथ इनलाइन प्रवाह में सेट करें

जब कोई आकार **inline** होता है, तो वह पैराग्राफ में एक कैरेक्टर की तरह व्यवहार करता है। यह सुनिश्चित करता है कि आयताकार दस्तावेज़ लेआउट में वही जगह पर रहे जहाँ आप अपेक्षा करते हैं।

```python
# Make the shape inline so it follows the text flow
rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE
```

यदि आप आकार को टेक्स्ट के ऊपर फ़्लोट करना पसंद करते हैं, तो आप `WrapType.SQUARE` या `WrapType.TOP_BOTTOM` का उपयोग कर सकते हैं, लेकिन अधिकांश रिपोर्ट्स में एक इनलाइन आकार लेआउट को पूर्वानुमेय रखता है।

## चरण 4: छाया को दृश्यमान बनाएं और उसका रंग चुनें

एक छाया जो दृश्यमान नहीं है, कोई विज़ुअल लाभ नहीं देती। `visible` फ़्लैग प्रभाव को सक्रिय करता है, और `color` प्रॉपर्टी उसकी टोन निर्धारित करती है। काली छाया क्लासिक, सूक्ष्म गहराई देती है।

```python
# Enable the shadow and set its color to black
rectangle_shape.shadow.visible = True
rectangle_shape.shadow.color = aw.drawing.Color.black
```

आप `aw.drawing.Color.black` को किसी भी अन्य रंग से बदल सकते हैं, जैसे `aw.drawing.Color.gray` या एक कस्टम RGB वैल्यू (`aw.drawing.Color.from_argb(255, 128, 128, 128)`)।

## चरण 5: छाया का ऑफ़सेट और ब्लर निर्धारित करें ताकि गहराई मिले

ऑफ़सेट नियंत्रित करता है कि छाया आकार से कितनी दूरी पर विस्थापित होती है, जबकि ब्लर रेडियस किनारों को नरम करता है। छोटे मान एक तेज़ छाया बनाते हैं; बड़े मान एक मुलायम लुक देते हैं।

```python
# Horizontal and vertical offset of 5 pt each
rectangle_shape.shadow.offset_x = 5
rectangle_shape.shadow.offset_y = 5

# Blur radius of 3 pt for a gentle feather
rectangle_shape.shadow.blur = 3
```

इन संख्याओं के साथ प्रयोग करें ताकि वे आपके डिज़ाइन गाइडलाइन से मेल खाएँ। भारी ड्रॉप शैडो के लिए आप दोनों ऑफ़सेट और ब्लर बढ़ा सकते हैं।

## चरण 6: बाहरी छाया शैली चुनें

Aspose.Words कई शैडो स्टाइल्स प्रदान करता है, जैसे `INNER`, `OUTER`, और `PERSPECTIVE`। **outer** शैली छाया को आकार की बॉर्डर के बाहर रखती है, जो साफ़, पेशेवर लुक के लिए आदर्श है।

```python
# Apply an outer shadow style
rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

यदि आपको अधिक नाटकीय प्रभाव चाहिए, तो `ShadowStyle.PERSPECTIVE` आज़माएँ—यह एक त्रि‑आयामी झुकाव जोड़ता है।

## चरण 7: आकार वाली छाया के साथ दस्तावेज़ सहेजें

सेव करना फ़ाइल को अंतिम रूप देता है और सभी फ़ॉर्मेटिंग को डिस्क पर लिखता है। ऐसी डायरेक्टरी चुनें जहाँ आपके पास लिखने की अनुमति हो, और फ़ाइल को एक वर्णनात्मक नाम दें।

```python
# Save the document to the desired location
output_path = "output/ShapeWithShadow.docx"
document.save(output_path)
print(f"Document saved to {output_path}")
```

स्क्रिप्ट चलाने से एक Word फ़ाइल बनती है जिसमें एक आयताकार के साथ दृश्यमान, रंगीन छाया होती है। परिणाम सत्यापित करने के लिए फ़ाइल को Microsoft Word या LibreOffice में खोलें।

## पूर्ण चलाने योग्य उदाहरण

नीचे वह संपूर्ण स्क्रिप्ट है जो चर्चा किए गए सभी चरणों को सम्मिलित करती है। कोड को `create_shadowed_shape.py` नामक फ़ाइल में कॉपी करें और `python create_shadowed_shape.py` के साथ चलाएँ।

```python
import aspose.words as aw
import os

def main():
    # Ensure the output directory exists
    output_dir = "output"
    os.makedirs(output_dir, exist_ok=True)

    # Step 1: Create a new blank document
    document = aw.Document()
    builder = aw.DocumentBuilder(document)

    # Step 2: Insert a rectangle shape of the desired size
    rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

    # Step 3: Set the shape to be inline with the text flow
    rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE

    # Step 4: Make the shadow visible and choose its color
    rectangle_shape.shadow.visible = True
    rectangle_shape.shadow.color = aw.drawing.Color.black

    # Step 5: Define the shadow's offset and blur to give it depth
    rectangle_shape.shadow.offset_x = 5   # horizontal offset in points
    rectangle_shape.shadow.offset_y = 5   # vertical offset in points
    rectangle_shape.shadow.blur = 3       # blur radius in points

    # Step 6: Choose an outer shadow style
    rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER

    # Step 7: Save the document with the shaped shadow
    output_path = os.path.join(output_dir, "ShapeWithShadow.docx")
    document.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    main()
```

**अपेक्षित आउटपुट**

जब आप `ShapeWithShadow.docx` खोलेंगे, तो आपको पेज के केंद्र में एक एकल आयताकार दिखाई देगा। आयताकार के साथ एक सूक्ष्म काली छाया नीचे‑दाएँ ओर ऑफ़सेट की हुई, थोड़ा ब्लर की हुई, गहराई बनाती हुई होगी। छाया बाहरी शैली का सम्मान करती है, इसलिए यह आयताकार के अंदरूनी हिस्से को नहीं काटती।

## सामान्य प्रश्न और किनारी स्थितियाँ

### क्यों कभी‑कभी छाया अदृश्य दिखाई देती है?

छाया केवल तब रेंडर होती है जब `shadow.visible` को `True` **और** आकार के `wrap_type` को इसे प्रदर्शित करने की अनुमति हो। एक इनलाइन आकार विश्वसनीय रूप से काम करता है; फ़्लोटिंग आकारों को अतिरिक्त लेआउट समायोजन की आवश्यकता हो सकती है।

### मैं छाया का रंग ब्रांड पैलेट से मेल खाने के लिए कैसे बदल सकता हूँ?

`aw.drawing.Color.black` को एक कस्टम RGB वैल्यू से बदलें:

```python
rectangle_shape.shadow.color = aw.drawing.Color.from_argb(255, 0, 120, 215)  # corporate blue
```

### यदि मुझे आकार को टेक्स्ट के पीछे दिखाना हो तो क्या करें?

रैप टाइप को `WrapType.BEHIND` सेट करें और आवश्यक होने पर `z_order_position` को समायोजित करें। ध्यान रखें कि कुछ व्यूअर पीछे‑टेक्स्ट शैप्स को अलग तरह से रेंडर कर सकते हैं।

### क्या मैं कई आकारों पर समान छाया सेटिंग्स लागू कर सकता हूँ?

हाँ। एक हेल्पर फ़ंक्शन बनाएं जो छाया को कॉन्फ़िगर करे और इसे प्रत्येक सम्मिलित आकार के लिए कॉल करें। यह कोड पुन: उपयोग को बढ़ावा देता है और स्टाइलिंग में निरंतरता सुनिश्चित करता है।

```python
def apply_shadow(shape, color=aw.drawing.Color.black, offset=5, blur=3):
    shape.shadow.visible = True
    shape.shadow.color = color
    shape.shadow.offset_x = offset
    shape.shadow.offset_y = offset
    shape.shadow.blur = blur
    shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

## निष्कर्ष

आप अब **how to create document** फ़ाइलें बना सकते हैं जिनमें Aspose.Words for Python का उपयोग करके एक आयताकार आकार और कस्टमाइज़्ड छाया होती है। ट्यूटोरियल ने आयताकार सम्मिलित करना, आकार को इनलाइन बनाना, छाया को सक्षम करना, उसका रंग, ऑफ़सेट, ब्लर और शैली सेट करना, और अंत में फ़ाइल को सहेजना कवर किया।

अब आप संबंधित विषयों जैसे अन्य शैप प्रकारों के लिए **add shadow to shape**, डेटा के आधार पर **set shadow color** को डायनामिक रूप से बदलना, या **how to add shadow** को इमेज और टेक्स्ट बॉक्स पर लागू करना एक्सप्लोर कर सकते हैं। विभिन्न आयाम, रंग और शैडो स्टाइल्स के साथ प्रयोग करें ताकि वे आपके ब्रांड गाइडलाइन या डिज़ाइन सिस्टम से मेल खाएँ।

अधिक Word दस्तावेज़ों को ऑटोमेट करने के लिए तैयार हैं? अगली बार टेबल, हेडर या डायनामिक कंटेंट जोड़ें—प्रत्येक चरण यहाँ दिखाए गए सिद्धांतों पर आधारित है। कोडिंग का आनंद लें!

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोचेज़ को एक्सप्लोर करने में मदद करेंगे।

- [आयताकार आकार बनाएं, छाया जोड़ें और PDF सहेजें](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [छायादार आयताकार आकार के साथ खाली Word दस्तावेज़ बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Python में Aspose.Words के साथ दस्तावेज़ वेरिएबल्स प्रबंधित करने का तरीका&#58; एक पूर्ण गाइड](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}