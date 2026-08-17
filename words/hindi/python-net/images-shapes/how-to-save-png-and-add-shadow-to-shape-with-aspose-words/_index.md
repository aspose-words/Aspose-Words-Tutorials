---
category: general
date: 2026-08-17
description: Aspose.Words for Python का उपयोग करके PNG कैसे सहेजें। एक गाइड में शैडो
  जोड़ना, दस्तावेज़ को PDF के रूप में सहेजना और Word को PNG में निर्यात करना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save png
- add shadow to shape
- save document as pdf
- export word to png
- convert word to pdf
language: hi
lastmod: 2026-08-17
og_description: Aspose.Words के साथ PNG कैसे सहेजें। यह ट्यूटोरियल एक आकार में छाया
  जोड़ना, दस्तावेज़ को PDF के रूप में सहेजना, और Word को PNG में निर्यात करना दिखाता
  है।
og_image_alt: Screenshot of a Word document with a rectangle shape that has a shadow,
  saved as PNG and PDF
og_title: Aspose.Words के साथ PNG कैसे सहेजें और आकार में छाया जोड़ें
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  headline: How to save PNG and add shadow to shape with Aspose.Words
  type: TechArticle
- description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  name: How to save PNG and add shadow to shape with Aspose.Words
  steps:
  - name: Pro tip
    text: If you need a sharper shadow, reduce `blur`. For a more pronounced offset,
      increase `distance`. The `Shadow` class also exposes `angle` and `transparency`
      for fine‑tuned control.
  - name: 'Optional: higher‑resolution PNG'
    text: '```python png_options = aw.image.PngSaveOptions() png_options.resolution
      = 300 # DPI doc.save("output/high_res_output.png", png_options) ```'
  - name: Expected output
    text: 'Running the script creates three files:'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Image export
title: Aspose.Words के साथ PNG को कैसे सहेजें और आकृति में छाया जोड़ें
url: /hi/python/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words के साथ PNG कैसे सहेजें और आकार में छाया जोड़ें

यदि आपको Word फ़ाइल से **PNG कैसे सहेजें** की आवश्यकता है, तो यह गाइड आपको एक पूर्ण, चलाने योग्य समाधान देता है। आप यह भी देखेंगे कि **आकार में छाया कैसे जोड़ें**, **दस्तावेज़ को PDF के रूप में सहेजें**, और **Word को PNG में निर्यात करें** Aspose.Words पर्यावरण से बाहर निकले बिना।

यह ट्यूटोरियल यह बताता है कि कैसे एक खाली Word दस्तावेज़ को PDF और PNG छवि में बदलें, साथ ही एक आयताकार आकार पर सरल छाया प्रभाव लागू करें। कोई बाहरी टूल आवश्यक नहीं है, और कोड Aspose.Words for Python via .NET 7 या बाद के संस्करणों के साथ काम करता है।

## आप क्या प्राप्त करेंगे

इस लेख के अंत तक आप सक्षम होंगे:

* प्रोग्रामेटिक रूप से एक नया Word दस्तावेज़ बनाना।  
* एक आयताकार आकार डालना और छाया प्रभाव कॉन्फ़िगर करना।  
* उसी दस्तावेज़ को PDF फ़ाइल के रूप में सहेजना।  
* दस्तावेज़ को PNG छवि के रूप में निर्यात करना।  

ये चरण सामान्य प्रश्न **PNG कैसे सहेजें** का उत्तर देते हैं, साथ ही **आकार में छाया जोड़ें** और **दस्तावेज़ को PDF के रूप में सहेजें** को एक ही वर्कफ़्लो में संभालते हैं।

## पूर्वापेक्षाएँ

* Python 3.9 या नया।  
* Aspose.Words for Python via .NET स्थापित (`pip install aspose-words`)।  
* आप जिस आउटपुट डायरेक्टरी को निर्दिष्ट करेंगे, उस पर लिखने की अनुमति।  

यदि आपने अभी तक Aspose.Words स्थापित नहीं किया है, तो चलाएँ:

```bash
pip install aspose-words
```

## Aspose.Words के साथ PNG कैसे सहेजें

पहला मुख्य कदम एक दस्तावेज़ और एक `DocumentBuilder` बनाना है। बिल्डर आपको आकार, तालिका या टेक्स्ट जैसे कंटेंट को डालने के लिए एक फ़्लुएंट API प्रदान करता है।

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` मेमोरी में पूरे Word फ़ाइल का प्रतिनिधित्व करता है। `aw.DocumentBuilder` वर्तमान इंसर्शन लोकेशन की ओर इशारा करता है, जो प्रारंभ में पहले (और केवल) सेक्शन की शुरुआत होती है।

## निर्यात से पहले आकार में छाया जोड़ें

एक आकार कोई भी ड्राइंग ऑब्जेक्ट हो सकता है—आयत, दीर्घवृत्त, या कस्टम पॉलीगॉन। यहाँ हम 100 × 100 पॉइंट का आयत बनाते हैं और एक सॉफ्ट शैडो लागू करते हैं।

```python
# Insert a rectangle shape (100x100 points)
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

# Configure a simple shadow
shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Softness of the shadow edges
shape.shadow.distance = 3.0      # Distance from the shape
shape.shadow.color = aw.Color.black
```

सहेजने से पहले छाया क्यों कॉन्फ़िगर करें? Aspose.Words PDF और PNG निर्यात चरणों के दौरान छाया को रेंडर करता है, इसलिए दृश्य प्रभाव दोनों आउटपुट फ़ॉर्मेट में संरक्षित रहता है।

### प्रो टिप
यदि आपको तेज़ छाया चाहिए, तो `blur` को कम करें। अधिक स्पष्ट ऑफ़सेट के लिए `distance` बढ़ाएँ। `Shadow` क्लास `angle` और `transparency` भी प्रदान करता है जिससे आप फाइन‑ट्यून कंट्रोल कर सकते हैं।

## दस्तावेज़ को PDF के रूप में सहेजें

सामग्री तैयार होने के बाद Word दस्तावेज़ को PDF में बदलना एक‑लाइनर है। `SaveFormat.PDF` कॉन्स्टेंट Aspose.Words को रूपांतरण करने के लिए बताता है।

```python
# Save the document as PDF (shadow is rendered in the output)
pdf_path = "output/output.pdf"
doc.save(pdf_path, aw.SaveFormat.PDF)
```

परिणामी PDF में वह आयत होगा जिसमें आपने परिभाषित की हुई ठीक वही छाया होगी। Aspose.Words वेक्टर ग्राफ़िक्स को संभालता है, इसलिए PDF का आकार मध्यम रहता है।

## Word को PNG में निर्यात करें

PNG में निर्यात करने से प्रत्येक पृष्ठ की एक रास्टर छवि बनती है। डिफ़ॉल्ट रूप से Aspose.Words 96 DPI उपयोग करता है; आप `PngSaveOptions` ऑब्जेक्ट प्रदान करके इस मान को बढ़ा सकते हैं जिससे उच्च‑रिज़ॉल्यूशन आउटपुट मिलेगा।

```python
# Export the same document as PNG
png_path = "output/output.png"
doc.save(png_path, aw.SaveFormat.PNG)
```

जब आप **Word को PNG में निर्यात** करते हैं, तो प्रत्येक पृष्ठ अलग‑अलग PNG फ़ाइल के रूप में सहेजा जाता है। क्योंकि हमारे उदाहरण दस्तावेज़ में केवल एक पृष्ठ है, केवल एक ही PNG फ़ाइल बनती है।

### वैकल्पिक: उच्च‑रिज़ॉल्यूशन PNG

```python
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI
doc.save("output/high_res_output.png", png_options)
```

उच्च DPI तब उपयोगी होता है जब PNG को प्रिंट में उपयोग किया जाना हो या आपको एक तीखा थंबनेल चाहिए।

## पूर्ण स्क्रिप्ट – कॉपी, पेस्ट और चलाएँ

नीचे वह पूर्ण, स्व‑निर्भर स्क्रिप्ट है जो ऊपर वर्णित प्रत्येक चरण को लागू करती है। इसे `generate_assets.py` के रूप में सहेजें और कमांड लाइन से चलाएँ।

```python
import os
import aspose.words as aw

# ------------------------------------------------------------------
# 1. Prepare output folder
# ------------------------------------------------------------------
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# ------------------------------------------------------------------
# 2. Create a new blank document and a builder
# ------------------------------------------------------------------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ------------------------------------------------------------------
# 3. Insert a rectangle shape and add a shadow
# ------------------------------------------------------------------
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Soft edges
shape.shadow.distance = 3.0      # Offset from shape
shape.shadow.color = aw.Color.black

# ------------------------------------------------------------------
# 4. Save as PDF (demonstrates "save document as pdf")
# ------------------------------------------------------------------
pdf_path = os.path.join(output_dir, "output.pdf")
doc.save(pdf_path, aw.SaveFormat.PDF)

# ------------------------------------------------------------------
# 5. Export as PNG (demonstrates "how to save png")
# ------------------------------------------------------------------
png_path = os.path.join(output_dir, "output.png")
doc.save(png_path, aw.SaveFormat.PNG)

# ------------------------------------------------------------------
# 6. Optional high‑resolution PNG (demonstrates "export word to png")
# ------------------------------------------------------------------
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI for sharper output
high_res_png_path = os.path.join(output_dir, "high_res_output.png")
doc.save(high_res_png_path, png_options)

print(f"Files written to {os.path.abspath(output_dir)}")
```

### अपेक्षित आउटपुट

स्क्रिप्ट चलाने से तीन फ़ाइलें बनती हैं:

* `output/output.pdf` – एक PDF जिसमें आयत पर काली छाया है।  
* `output/output.png` – वही पृष्ठ का 96 DPI PNG रेंडरिंग।  
* `output/high_res_output.png` – उच्च गुणवत्ता के लिए 300 DPI PNG।

किसी भी फ़ाइल को अपने पसंदीदा व्यूअर में खोलें और सत्यापित करें कि छाया ठीक वैसी ही दिखाई दे रही है जैसा आपने परिभाषित किया था।

## सामान्य प्रश्न और किनारी स्थितियाँ

**यदि आउटपुट डायरेक्टरी मौजूद नहीं है तो क्या होगा?**  
स्क्रिप्ट `os.makedirs(output_dir, exist_ok=True)` को कॉल करती है, जो फ़ोल्डर को स्वचालित रूप से बनाता है। इससे सहेजने के दौरान `FileNotFoundError` से बचा जाता है।

**क्या मैं विभिन्न छायाओं के साथ कई आकार जोड़ सकता हूँ?**  
हां। अतिरिक्त `Shape` ऑब्जेक्ट बनाएं, प्रत्येक `shadow` प्रॉपर्टी को स्वतंत्र रूप से कॉन्फ़िगर करें, और सहेजने से पहले `builder.insert_node(shape)` से उन्हें डालें।

**क्या छाया अन्य रास्टर फ़ॉर्मेट (जैसे JPEG) में बदलते समय बनी रहती है?**  
Aspose.Words `SaveFormat` द्वारा समर्थित सभी रास्टर फ़ॉर्मेट के लिए छाया रेंडर करता है। आप `aw.SaveFormat.PNG` को `aw.SaveFormat.JPEG` से बदल सकते हैं और छाया अभी भी दिखाई देगी।

**यह “convert word to pdf” से कैसे अलग है?**  
`convert word to pdf` मूलतः चरण 4 में किया गया वही ऑपरेशन है। वही `doc.save` कॉल `SaveFormat.PDF` के साथ लेआउट, फ़ॉन्ट और ग्राफ़िक्स (जैसे छाया) को आंतरिक रूप से संरक्षित करता है।

**आकार के आकार पर कोई सीमा है क्या?**  
आकार पॉइंट में मापे जाते हैं (1 pt ≈ 1/72 इंच)। बहुत बड़े आयाम फ़ाइल आकार बढ़ा सकते हैं, लेकिन Aspose.Words कोई कठोर सीमा नहीं लगाता। अपने लेआउट के अनुसार `aw.Shape` बनाते समय `width` और `height` आर्ग्यूमेंट को समायोजित करें।

## निष्कर्ष

अब आप **Word दस्तावेज़ से PNG कैसे सहेजें** को जानते हैं, साथ ही **आकार में छाया कैसे जोड़ें**, **दस्तावेज़ को PDF के रूप में सहेजें**, और Aspose.Words for Python का उपयोग करके **Word को PNG में निर्यात करें**। पूर्ण स्क्रिप्ट एक साफ़, दोहराने योग्य पैटर्न दर्शाती है जिसे आप बड़े दस्तावेज़ों, कई पृष्ठों या अधिक जटिल ग्राफ़िक प्रभावों के लिए अनुकूलित कर सकते हैं।

आगे के कदम हो सकते हैं:

* अन्य `ShapeType` मानों (ellipse, cloud, आदि) के साथ प्रयोग करना।  
* Using 

## आप अगला क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API फीचर्स में महारत हासिल कर सकें और अपने प्रोजेक्ट में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण कर सकें।

- [Aspose.Words Shape Shadow ट्यूटोरियल – C# में Word Shape में छाया जोड़ें](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Java में DOCX को PNG में कैसे बदलें – Aspose.Words](/words/english/java/document-converting/converting-documents-images/)
- [Python में Aspose.Words का उपयोग करके Word दस्तावेज़ को PostScript के रूप में सहेजें: एक व्यापक गाइड](/words/english/python-net/document-operations/save-docs-as-postscript-using-aspose-words-python/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}