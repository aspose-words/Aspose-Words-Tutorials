---
category: general
date: 2026-09-27
description: Aspose.Words for Python के साथ किसी आकार पर छाया सेट करना सीखें। यह गाइड
  आकार में छाया जोड़ने, छाया प्रभाव लागू करने और छाया का रंग सेट करने को कवर करता
  है।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set shadow
- add shadow to shape
- apply shadow effect
- set shadow color
- how to add shadow
language: hi
lastmod: 2026-09-27
og_description: Aspose.Words for Python का उपयोग करके किसी आकार पर शैडो कैसे सेट करें।
  शैडो जोड़ने, शैडो इफ़ेक्ट लागू करने और शैडो रंग सेट करने के लिए चरण‑दर‑चरण गाइड
  का पालन करें।
og_image_alt: Screenshot showing how to set shadow on a shape in a Word document
og_title: Aspose.Words for Python में किसी आकार पर छाया कैसे सेट करें
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to set shadow on a shape with Aspose.Words for Python. This
    guide covers add shadow to shape, apply shadow effect, and set shadow color.
  headline: How to set shadow on a shape in Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Shapes
- Shadow effect
title: Aspose.Words for Python में एक आकार पर छाया कैसे सेट करें
url: /hi/python/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Python में किसी shape पर shadow कैसे सेट करें

यदि आपको ड्राइंग ऑब्जेक्ट के लिए **shadow कैसे सेट करें** की आवश्यकता है, तो यह गाइड पूरी प्रक्रिया दिखाता है। आप देखेंगे कि shape में shadow कैसे जोड़ें, shadow के blur, offset, और color को कैसे कॉन्फ़िगर करें, और कोड से बाहर निकले बिना अपडेटेड डॉक्यूमेंट को सहेजें।

यह ट्यूटोरियल मानता है कि आपके पास पहले से ही एक बेसिक Aspose.Words for Python वातावरण है। लेख के अंत तक आप किसी भी DOCX फ़ाइल में किसी भी shape पर पेशेवर‑दिखाई देने वाला shadow इफ़ेक्ट लागू करने में सक्षम होंगे।

## पूर्वापेक्षाएँ

* Python 3.8+ स्थापित है।
* Aspose.Words for Python via .NET (`pip install aspose-words`) स्थापित है।
* एक Word डॉक्यूमेंट (`input.docx`) जिसमें कम से कम एक shape हो (जैसे, एक rectangle या picture)।  
  यदि डॉक्यूमेंट खाली है, तो कोड प्रदर्शन के लिए एक नया shape बनाएगा।

इन वस्तुओं से यह सुनिश्चित होता है कि आगे के चरण बिना import त्रुटियों के चलें।

## चरण 1: Word डॉक्यूमेंट लोड या बनाएं

पहला ऑपरेशन `Document` ऑब्जेक्ट प्राप्त करना है। आप या तो मौजूदा फ़ाइल लोड कर सकते हैं या एक नई फ़ाइल बना सकते हैं।

```python
import aspose.words as aw

# Load an existing document, or create a new blank document if the file does not exist.
try:
    doc = aw.Document("YOUR_DIRECTORY/input.docx")
except Exception:
    doc = aw.Document()          # Creates an empty document
    # Optional: add a paragraph so the document is not completely empty.
    builder = aw.DocumentBuilder(doc)
    builder.writeln("Document created for shadow demo.")
```

*इस चरण का महत्व*: `Document` ऑब्जेक्ट सभी Word‑प्रोसेसिंग ऑपरेशन्स का प्रवेश बिंदु है। इसके बिना आप shapes तक पहुँच नहीं सकते या visual effects लागू नहीं कर सकते।

## चरण 2: लक्ष्य shape प्राप्त करें

एक shape की उपस्थिति को बदलने के लिए आपको shape नोड का रेफ़रेंस चाहिए। नीचे दिया गया उदाहरण डॉक्यूमेंट हायरार्की में पाया गया पहला shape प्राप्त करता है।

```python
# Retrieve the first shape in the document tree.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# If the document has no shapes, create one for demonstration purposes.
if shape is None:
    builder = aw.DocumentBuilder(doc)
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
    shape.wrap_type = aw.drawing.WrapType.INLINE
```

*इस चरण का महत्व*: `add shadow to shape` को एक ठोस shape ऑब्जेक्ट चाहिए। कोड सुरक्षित रूप से उस स्थिति को संभालता है जहाँ डॉक्यूमेंट में कोई shape नहीं होता, जिससे ट्यूटोरियल हर पाठक के लिए काम करता है।

## चरण 3: shadow की उपस्थिति कॉन्फ़िगर करें

अब आप **apply shadow effect** को shape की `shadow` प्रॉपर्टी को समायोजित करके लागू कर सकते हैं। निम्न सेटिंग्स एक सूक्ष्म, गहरा shadow देती हैं।

```python
# Set the shadow blur radius (softness). Larger values produce a more diffused shadow.
shape.shadow.blur = 5.0

# Horizontal displacement of the shadow in points.
shape.shadow.offset_x = 2.0

# Vertical displacement of the shadow in points.
shape.shadow.offset_y = 2.0

# Set the shadow color. This demonstrates **set shadow color** to black.
shape.shadow.color = aw.Color.black

# Enable the shadow (some older versions require explicit visibility).
shape.shadow.visible = True
```

*प्रत्येक प्रॉपर्टी का महत्व*:

| Property | Effect |
|----------|--------|
| `blur`   | shadow की धुंधलापन को नियंत्रित करता है। |
| `offset_x` / `offset_y` | shape से दिशा और दूरी निर्धारित करता है। |
| `color`  | shadow का रंग निर्धारित करता है; आप कोई भी `aw.Color` उपयोग कर सकते हैं। |
| `visible`| सुनिश्चित करता है कि shadow आउटपुट फ़ाइल में रेंडर हो। |

आप `aw.Color.black` को `aw.Color.from_argb(255, 0, 0, 0)` से बदलकर कस्टम RGBA मान या किसी अन्य प्री‑डिफाइंड रंग का उपयोग कर सकते हैं।

## चरण 4: संशोधित डॉक्यूमेंट सहेजें

shadow को कॉन्फ़िगर करने के बाद, बदलावों को नई फ़ाइल में सहेजें।

```python
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved with shadow effect at: {output_path}")
```

जब आप `output.docx` को Microsoft Word में खोलेंगे, तो चयनित shape 2 pt दाईं ओर और 2 pt नीचे स्थानांतरित एक नरम काले shadow के साथ प्रदर्शित होगा।

## पूर्ण कार्यशील उदाहरण

सभी चरणों को मिलाकर एक self‑contained स्क्रिप्ट बनती है जिसे आप अपने IDE में copy‑paste कर सकते हैं।

```python
import aspose.words as aw

def add_shadow_to_first_shape(input_path: str, output_path: str):
    # Load or create the document.
    try:
        doc = aw.Document(input_path)
    except Exception:
        doc = aw.Document()
        builder = aw.DocumentBuilder(doc)
        builder.writeln("Document created for shadow demo.")

    # Retrieve the first shape; create one if none exist.
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if shape is None:
        builder = aw.DocumentBuilder(doc)
        shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
        shape.wrap_type = aw.drawing.WrapType.INLINE

    # Apply shadow settings.
    shape.shadow.blur = 5.0
    shape.shadow.offset_x = 2.0
    shape.shadow.offset_y = 2.0
    shape.shadow.color = aw.Color.black
    shape.shadow.visible = True

    # Save the result.
    doc.save(output_path)
    print(f"Shadow applied and saved to {output_path}")

# Example usage
if __name__ == "__main__":
    add_shadow_to_first_shape(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.docx"
    )
```

स्क्रिप्ट चलाने पर `output.docx` बनता है जहाँ पहला shape कॉन्फ़िगर किया गया shadow रखता है।

## सामान्य समस्याएँ और उन्हें कैसे टालें

| समस्या | कारण | समाधान |
|-------|--------|-----|
| `shape` लोड करने के बाद भी `None` है | डॉक्यूमेंट में कोई drawing ऑब्जेक्ट नहीं है। | Step 2 में दिखाए गए fallback shape निर्माण ब्लॉक का उपयोग करें। |
| Word में shadow दिखाई नहीं देता | `shape.shadow.visible` को `False` रखा गया है या डॉक्यूमेंट पुराने फॉर्मेट (जैसे `.doc`) में सहेजा गया है। | `visible = True` सुनिश्चित करें और `.docx` के रूप में सहेजें। |
| रंग अपेक्षा से अलग दिख रहा है | डॉक्यूमेंट की थीम स्पष्ट रंगों को ओवरराइड करती है। | `shape.shadow.color` को थीम ओवरराइड बंद करने के बाद सेट करें, या `aw.Color.from_argb` उपयोग करें। |

इन किनारी मामलों को संबोधित करने से समाधान उत्पादन कोड के लिए मजबूत बनता है।

## प्रभाव का विस्तार (अगले कदम)

अब जब आप **shadow कैसे जोड़ें** जानते हैं, तो आप संबंधित सुधारों का अन्वेषण कर सकते हैं:

* **apply shadow effect** को ग्रेडिएंट या कई shadows के साथ `shape.shadow` उप‑प्रॉपर्टीज़ को समायोजित करके लागू करें।
* उपयोगकर्ता इनपुट या थीम रंगों के आधार पर **set shadow color** को डायनामिक रूप से उपयोग करें।
* **add shadow to shape** को अन्य फ़ॉर्मेटिंग कार्यों जैसे rotation, line style, या 3‑D effects के साथ संयोजित करें।
* `doc.get_child_nodes(aw.NodeType.SHAPE, True)` के माध्यम से इटररेट करके डॉक्यूमेंट में प्रत्येक shape के लिए shadow जोड़ने को स्वचालित करें।

इन विस्तारों से आप परिष्कृत डॉक्यूमेंट‑जनरेशन पाइपलाइन बना सकते हैं जो पॉलिश्ड, विज़ुअली कंसिस्टेंट आउटपुट उत्पन्न करती हैं।

## निष्कर्ष

अब आपके पास Aspose.Words for Python का उपयोग करके shape पर **shadow कैसे सेट करें** का एक पूर्ण, चलने योग्य समाधान है। गाइड ने डॉक्यूमेंट लोड करना, shape प्राप्त या बनाना, blur, offset, और **set shadow color** को कॉन्फ़िगर करना, और अंत में फ़ाइल सहेजना कवर किया। इस पैटर्न को अपने ऑटोमेशन प्रोजेक्ट्स में किसी भी shape पर लागू करें और अतिरिक्त विज़ुअल ट्यूनिंग के साथ प्रयोग करें ताकि आपके डिज़ाइन आवश्यकताओं को पूरा किया जा सके।

--- 

*कोड को अन्य shape प्रकारों, रंगों, या offset मानों के लिए अनुकूलित करने में संकोच न करें। यदि आपको कोई समस्या आती है, तो “सामान्य समस्याएँ” तालिका की समीक्षा पहला अच्छा कदम है।*


## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट-संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [C# में shape पर shadow जोड़ें – shadow effect लागू करने के लिए पूर्ण गाइड](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-c-complete-guide-to-apply-shadow-effe/)
- [Word में shape पर shadow जोड़ें – पूर्ण Aspose.Words गाइड](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [rectangle shape बनाएं, shadow जोड़ें और PDF सहेजें](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}