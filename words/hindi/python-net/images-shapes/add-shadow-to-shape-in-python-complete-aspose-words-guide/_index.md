---
category: general
date: 2026-08-11
description: Aspose.Words for Python का उपयोग करके आकार में छाया जोड़ें। सीखें कि
  आकार में छाया कैसे जोड़ें, आकार पर ब्लर कैसे लागू करें, और ऑफ़सेट तथा रंग को कैसे
  अनुकूलित करें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- add shape shadow
- apply blur to shape
- Aspose.Words shadow effect
- Python Word shape styling
language: hi
lastmod: 2026-08-11
og_description: Aspose.Words for Python के साथ आकार में शैडो जोड़ें। यह गाइड आपको
  दिखाता है कि कैसे आकार पर ब्लर लागू करें, ऑफसेट सेट करें, और कुछ ही कोड लाइनों में
  शैडो रंग चुनें।
og_image_alt: Word document screenshot showing a shape with a black shadow applied
og_title: Python में आकृति में छाया जोड़ें – चरण‑दर‑चरण Aspose.Words ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-08-11'
  description: Add shadow to shape using Aspose.Words for Python. Learn how to add
    shape shadow, apply blur to shape, and customize offset and color.
  headline: Add shadow to shape in Python – complete Aspose.Words guide
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python. Learn how to add
    shape shadow, apply blur to shape, and customize offset and color.
  name: Add shadow to shape in Python – complete Aspose.Words guide
  steps:
  - name: Adding shadow to a specific shape by name
    text: 'If your document contains several shapes, you may want to target one by
      its `name` property:'
  - name: Skipping non‑visual nodes
    text: Sometimes a shape node can be a placeholder (e.g., a drawing canvas without
      visual content). Guard against this by checking `shape.is_image` or `shape.is_picture_frame`
      before applying the shadow.
  - name: Working with grouped shapes
    text: When shapes are grouped, the group itself is a `Shape` node. To apply a
      shadow to each member, iterate through `shape.get_child_nodes(aw.NodeType.SHAPE,
      True)`.
  - name: What’s next?
    text: '- Explore **apply blur to shape** for other effects like glow or soft edges.
      - Combine shadows with **shape borders** or **reflection** to create richer
      graphics. - Convert the edited document to PDF (`doc.save("output.pdf", aw.SaveFormat.PDF)`)
      for distribution.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Python में आकार में छाया जोड़ें – पूर्ण Aspose.Words गाइड
url: /hi/python/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python में shape पर छाया जोड़ें – पूर्ण Aspose.Words गाइड

यदि आपको Word दस्तावेज़ में **shape पर छाया जोड़नी** है, तो यह ट्यूटोरियल Aspose.Words for Python के साथ इसे कैसे किया जाए, बिल्कुल दिखाता है। चाहे आप रिपोर्ट जेनरेटर बना रहे हों या दस्तावेज़‑टेम्प्लेटिंग सेवा, आप कुछ ही पंक्तियों के कोड में shape की छाया जोड़ना, blur लागू करना, और छाया की उपस्थिति को फाइन‑ट्यून करना सीखेंगे।

यह गाइड सभी आवश्यक चीज़ें कवर करता है: आवश्यक इम्पोर्ट्स, लक्ष्य shape को ढूँढना (नेस्टेड नोड्स सहित), छाया गुणों को कॉन्फ़िगर करना, सामान्य किनारी मामलों को संभालना, और संशोधित दस्तावेज़ को सहेजना। अंत में आपके पास एक पुन: प्रयोज्य स्निपेट होगा जिसे आप किसी भी Python प्रोजेक्ट में .docx फ़ाइलों के साथ उपयोग कर सकते हैं।

## पूर्वापेक्षाएँ

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

- **Python 3.8+** स्थापित।
- **Aspose.Words for Python via .NET** (`pip install aspose-words` के साथ स्थापित)।
- एक Word दस्तावेज़ (`input.docx`) जिसमें कम से कम एक shape हो (जैसे, आयत, चित्र, या SmartArt)।
- Python और Aspose.Words ऑब्जेक्ट मॉडल की बुनियादी जानकारी।

## चरण 1: Aspose.Words को इम्पोर्ट करें और दस्तावेज़ खोलें

पहला चरण `aspose.words` पैकेज को इम्पोर्ट करना (आमतौर पर `aw` के रूप में उपनाम) और स्रोत दस्तावेज़ को लोड करना है।

```python
import aspose.words as aw

# Load the Word document from the file system
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)
```

*क्यों महत्वपूर्ण है*: दस्तावेज़ खोलने से आपको नोड ट्री तक पहुँच मिलती है जहाँ shapes स्थित होते हैं। `aw.Document` क्लास सभी आगे की मैनिपुलेशन की एंट्री पॉइंट है।

## चरण 2: पहला shape ढूँढें (नेस्टेड नोड्स सहित)

Shapes सीधे `Paragraph` के चाइल्ड हो सकते हैं या अन्य कंटेनरों (जैसे टेबल) के अंदर नेस्टेड हो सकते हैं। `get_child` को `is_deep=True` के साथ उपयोग करने से आप नेस्टिंग की परवाह किए बिना पहला shape प्राप्त कर लेते हैं।

```python
# Retrieve the first shape in the document, searching recursively
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

if shape is None:
    raise ValueError("No shape found in the document. Add a shape before applying a shadow.")
```

*क्यों महत्वपूर्ण है*: `add shape shadow` ऑपरेशन को एक `Shape` ऑब्जेक्ट चाहिए। डीप सर्च आपको टेबल या ग्रुप कंटेनर के अंदर छिपे हुए shapes को मिस करने से बचाती है।

## चरण 3: छाया सक्षम करें और बुनियादी गुण सेट करें

Aspose.Words छाया को कई गुणों के साथ दर्शाता है। सबसे पहले, `shadow_visible` को `True` सेट करके छाया को चालू करें।

```python
# Enable the shadow effect
shape.shadow_visible = True
```

अब आप blur radius, offsets, और रंग कॉन्फ़िगर कर सकते हैं।

## चरण 4: shape पर blur लागू करें और offset मान निर्धारित करें

blur radius यह तय करता है कि छाया कितनी मुलायम दिखेगी। `5.0` का मान एक स्पष्ट लेकिन अत्यधिक न होने वाला blur देता है। Offsets छाया को क्षैतिज और लंबवत रूप से स्थानांतरित करते हैं।

```python
# Apply blur to shape – this is the "apply blur to shape" part
shape.shadow_blur = 5.0          # Blur radius in points

# Define horizontal (X) and vertical (Y) offsets
shape.shadow_offset_x = 2.0     # Move shadow 2 points to the right
shape.shadow_offset_y = 2.0     # Move shadow 2 points down
```

*क्यों महत्वपूर्ण है*: `shadow_blur` और offset मानों को समायोजित करने से आप ऐसे यथार्थवादी गहराई प्रभाव बना सकते हैं जो आपके दस्तावेज़ की दृश्य शैली से मेल खाते हों।

## चरण 5: छाया का रंग चुनें (कस्टम रंग के साथ shape पर छाया जोड़ें)

आप कोई भी `aw.Color` उपयोग कर सकते हैं। यहाँ हमने काला चुना है, लेकिन आप इसे `aw.Color.red`, `aw.Color.from_argb(255, 0, 120, 215)` आदि से बदल सकते हैं।

```python
# Set the shadow color – black in this example
shape.shadow_color = aw.Color.black
```

*क्यों महत्वपूर्ण है*: रंग यह निर्धारित करता है कि छाया आसपास की सामग्री के साथ कैसे इंटरैक्ट करती है। हल्के बैकग्राउंड पर गहरी छाया अधिक दिखती है, जबकि गहरे पृष्ठों पर हल्की छाया बेहतर काम करती है।

## चरण 6: अपडेटेड दस्तावेज़ सहेजें

अंत में, बदलावों को डिस्क पर लिखें। आप मूल फ़ाइल को ओवरराइट कर सकते हैं या नई फ़ाइल बना सकते हैं।

```python
output_path = "YOUR_DIRECTORY/output_with_shadow.docx"
doc.save(output_path)

print(f"Shadow applied successfully. Saved to {output_path}")
```

जब आप `output_with_shadow.docx` को Microsoft Word में खोलेंगे, तो पहला shape निर्दिष्ट blur और offset के साथ एक मुलायम काली छाया दिखाएगा।

## पूर्ण, चलाने योग्य उदाहरण

सब कुछ एक साथ रखने पर, यहाँ एक स्व-निहित स्क्रिप्ट है जिसे आप तुरंत चला सकते हैं:

```python
import aspose.words as aw

def add_shadow_to_first_shape(input_path: str, output_path: str,
                              blur: float = 5.0,
                              offset_x: float = 2.0,
                              offset_y: float = 2.0,
                              color: aw.Color = aw.Color.black) -> None:
    """
    Loads a Word document, finds the first shape (deep search),
    and applies a shadow effect.

    Parameters
    ----------
    input_path : str
        Path to the source .docx file.
    output_path : str
        Path where the modified document will be saved.
    blur : float, optional
        Blur radius for the shadow. Default is 5.0 points.
    offset_x : float, optional
        Horizontal offset of the shadow. Default is 2.0 points.
    offset_y : float, optional
        Vertical offset of the shadow. Default is 2.0 points.
    color : aw.Color, optional
        Shadow color. Default is black.
    """
    # Load the document
    doc = aw.Document(input_path)

    # Retrieve the first shape, searching recursively
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

    if shape is None:
        raise ValueError("No shape found in the document. Insert a shape before calling this function.")

    # Enable shadow and configure its appearance
    shape.shadow_visible = True
    shape.shadow_blur = blur
    shape.shadow_offset_x = offset_x
    shape.shadow_offset_y = offset_y
    shape.shadow_color = color

    # Save the result
    doc.save(output_path)

if __name__ == "__main__":
    INPUT_DOC = "YOUR_DIRECTORY/input.docx"
    OUTPUT_DOC = "YOUR_DIRECTORY/output_with_shadow.docx"
    add_shadow_to_first_shape(INPUT_DOC, OUTPUT_DOC)
```

**अपेक्षित आउटपुट**: `output_with_shadow.docx` खोलने पर पहला shape एक सूक्ष्म काली छाया के साथ दिखेगा जो 2 pt क्षैतिज और लंबवत रूप से blur और offset किया गया है, जैसा कि आपने पैरामीटर पास किए थे।

## कई shapes और किनारी मामलों को संभालना

### नाम द्वारा विशिष्ट shape पर छाया जोड़ना

यदि आपके दस्तावेज़ में कई shapes हैं, तो आप `name` प्रॉपर्टी के आधार पर किसी एक को लक्षित करना चाह सकते हैं:

```python
target_name = "MyRectangle"
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)  # start with first shape
while shape is not None and shape.name != target_name:
    shape = shape.next_sibling(aw.NodeType.SHAPE)

if shape is None:
    raise ValueError(f"Shape named '{target_name}' not found.")
```

### गैर‑दृश्यमान नोड्स को स्किप करना

कभी‑कभी एक shape नोड प्लेसहोल्डर हो सकता है (जैसे, बिना दृश्य सामग्री के ड्राइंग कैनवास)। छाया लागू करने से पहले `shape.is_image` या `shape.is_picture_frame` की जाँच करके इसे बचें।

```python
if not shape.is_image and not shape.is_picture_frame:
    # Proceed only if the shape can display a shadow
    shape.shadow_visible = True
```

### ग्रुपेड shapes के साथ काम करना

जब shapes ग्रुपेड होते हैं, तो स्वयं ग्रुप एक `Shape` नोड होता है। प्रत्येक सदस्य पर छाया लागू करने के लिए `shape.get_child_nodes(aw.NodeType.SHAPE, True)` के माध्यम से इटररेट करें।

```python
if shape.is_group:
    for child in shape.get_child_nodes(aw.NodeType.SHAPE, True):
        child.shadow_visible = True
        child.shadow_blur = blur
        child.shadow_offset_x = offset_x
        child.shadow_offset_y = offset_y
        child.shadow_color = color
```

इन विविधताओं से आपका कोड विभिन्न दस्तावेज़ लेआउट्स में मजबूती से काम करेगा।

## परिपूर्ण छायाओं के लिए प्रो टिप्स

- **संगतता**: रिपोर्ट में सभी shapes के लिए समान blur radius और offset उपयोग करें ताकि दृश्य भाषा सुसंगत रहे।
- **प्रदर्शन**: कई हाई‑रेज़ोल्यूशन चित्रों पर छाया लागू करने से फ़ाइल आकार बढ़ सकता है। यदि बाद में PDF जनरेट करने की योजना है तो आउटपुट आकार का परीक्षण करें।
- **रंग कंट्रास्ट**: गहरे पृष्ठ पृष्ठभूमि पर, दृश्यता बनाए रखने के लिए हल्की छाया (`aw.Color.gray`) पर विचार करें।
- **प्रिव्यू**: Word की “Shadow” UI Aspose.Words गुणों को प्रतिबिंबित करती है, इसलिए आप मैन्युअली प्रयोग कर सकते हैं, फिर प्राप्त मानों को अपने स्क्रिप्ट में कॉपी कर सकते हैं।

## निष्कर्ष

अब आप Aspose.Words for Python का उपयोग करके Word दस्तावेज़ में **shape पर छाया जोड़ना** जानते हैं। गाइड ने shape को ढूँढना, छाया सक्षम करना, कस्टम blur, offsets, और रंग के साथ **add shape shadow** करना, और परिणाम सहेजना कवर किया। ऊपर दिया गया पुन: प्रयोज्य फ़ंक्शन आपके किसी भी दस्तावेज़‑जनरेशन पाइपलाइन में इस प्रभाव को एकीकृत कर सकता है।

### आगे क्या करें?

- अन्य प्रभावों जैसे glow या soft edges के लिए **apply blur to shape** का अन्वेषण करें।
- richer ग्राफिक्स बनाने के लिए छायाओं को **shape borders** या **reflection** के साथ मिलाएँ।
- वितरण के लिए संपादित दस्तावेज़ को PDF में बदलें (`doc.save("output.pdf", aw.SaveFormat.PDF)`)।

विभिन्न रंगों, blur स्तरों, और offset मानों के साथ प्रयोग करें ताकि वे आपके ब्रांडिंग दिशानिर्देशों से मेल खाएँ। Happy coding!

## आप आगे क्या सीख सकते हैं?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API सुविधाओं में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों की खोज करने में मदद करेंगे।

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}