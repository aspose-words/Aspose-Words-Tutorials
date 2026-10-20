---
category: general
date: 2026-08-07
description: Aspose.Words for Python का उपयोग करके PDF में आयत बनाएं और सीखें कि आकार
  में छाया कैसे जोड़ें, आकार की छाया को कॉन्फ़िगर करें, और दस्तावेज़ को PDF के रूप
  में सहेजें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle in pdf
- add shadow to shape
- save document as pdf
- configure shape shadow
language: hi
lastmod: 2026-08-07
og_description: Aspose.Words for Python के साथ PDF में आयत बनाएं। यह ट्यूटोरियल दिखाता
  है कि कैसे आकार में छाया जोड़ें, आकार की छाया को कॉन्फ़िगर करें, और पेशेवर दस्तावेज़
  निर्माण के लिए दस्तावेज़ को PDF के रूप में सहेजें।
og_image_alt: PDF page showing a rectangle shape with a visible shadow created by
  Aspose.Words for Python
og_title: Aspose.Words for Python के साथ PDF में आयत बनाएं – गाइड
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Draw rectangle in PDF using Aspose.Words for Python and learn how to
    add shadow to shape, configure shape shadow, and save document as PDF.
  headline: Draw rectangle in PDF with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF
- Shape
- Shadow
title: Aspose.Words for Python के साथ PDF में आयत बनाएं
url: /hi/python/images-shapes/draw-rectangle-in-pdf-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Python के साथ PDF में आयत बनाएं

यदि आप Python में काम करते समय **PDF में आयत बनाना** चाहते हैं, तो यह गाइड आपको एक पूर्ण, तैयार‑से‑चलाने वाला समाधान देता है। आप देखेंगे कि **आकार में छाया जोड़ना**, उस छाया को कॉन्फ़िगर करना, और अंत में **दस्तावेज़ को PDF के रूप में सहेजना** कैसे किया जाता है, ताकि वितरण या अभिलेखीय कार्य हो सके।

शेडेड आयत बनाना रिपोर्ट, इनवॉइस या विज़ुअल एनोटेशन के लिए एक सामान्य आवश्यकता है। इस ट्यूटोरियल के अंत तक आपके पास एक ही स्क्रिप्ट होगी जो एक वास्तविक छाया वाली आयत के साथ PDF उत्पन्न करती है, और आप आकार, रंग और ऑफ़सेट को किसी भी डिज़ाइन के अनुसार समायोजित करना सीखेंगे।

## पूर्वापेक्षाएँ

* Python 3.8+ स्थापित है।
* Aspose.Words for Python via .NET पैकेज (`aspose-words`) – इसे इस प्रकार स्थापित करें:

```bash
pip install aspose-words
```

* उस फ़ोल्डर में लिखने की अनुमति जहाँ आप PDF सहेजना चाहते हैं।

कोई अतिरिक्त लाइब्रेरी आवश्यक नहीं है; Aspose.Words आकार निर्माण, छाया कॉन्फ़िगरेशन और PDF निर्यात को आंतरिक रूप से संभालता है।

## चरण 1: एक नया खाली दस्तावेज़ बनाएं (PDF में आयत बनाएं – प्रारंभिक सेटअप)

पहला चरण `Document` ऑब्जेक्ट को इंस्टैंशिएट करना है। यह ऑब्जेक्ट पूरे PDF फ़ाइल का प्रतिनिधित्व करता है और सेक्शन, पैराग्राफ और आकारों के लिए कंटेनर प्रदान करता है।

```python
import aspose.words as aw

# Create an empty Word document – it will become a PDF later
doc = aw.Document()
```

**Why this matters:** Aspose.Words PDF जनरेशन को एक Word दस्तावेज़ मॉडल से रूपांतरण के रूप में देखता है, इसलिए हम `Document` से शुरू करते हैं हालांकि अंतिम आउटपुट PDF है।

## चरण 2: दस्तावेज़ बॉडी में एक आयत आकार सम्मिलित करें

एक आयत एक विशिष्ट `ShapeType` है। हम इसे पहले सेक्शन के बॉडी में जोड़ते हैं, जो PDF के रूप में सहेजने पर स्वचालित रूप से एक नया पृष्ठ बनाता है।

```python
# Append a rectangle shape to the first section's body
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Set the rectangle's dimensions (points = 1/72 inch)
rectangle.width = 200   # 200 pt ≈ 2.78 in
rectangle.height = 100  # 100 pt ≈ 1.39 in

# Optional: give the shape some visible text
rectangle.text = "Shadow demo"
```

**Explanation:** `width` और `height` प्रॉपर्टी PDF में आकार के दृश्य आकार को नियंत्रित करती हैं। टेक्स्ट जोड़ने से परीक्षण के दौरान आयत को सत्यापित करना आसान हो जाता है।

## चरण 3: आकार में छाया जोड़ें – सक्षम करें और अनुकूलित करें

अब हम छाया प्रभाव को चालू करते हैं और उसकी उपस्थिति को बारीकी से समायोजित करते हैं। यही वह जगह है जहाँ **add shadow to shape** कीवर्ड काम आता है।

```python
# Access the shape's shadow effect object
shadow = rectangle.shadow_effect

# Make the shadow visible
shadow.visible = True

# Configure blur radius (pt) – higher values produce a softer edge
shadow.blur = 8

# Set the distance (offset) from the shape in points
shadow.distance = 5

# Define the direction of the shadow in degrees (0 = right, 90 = down)
shadow.angle = 45

# Choose a shadow color – black works for most documents
shadow.color = aw.drawing.Color.black
```

**Why configure shape shadow?** `blur`, `distance` और `angle` को समायोजित करने से आप वास्तविक प्रकाश की नकल कर सकते हैं, जो उत्पन्न PDFs में पठनीयता और दृश्य पदानुक्रम को सुधारता है।

## चरण 4: दस्तावेज़ को PDF के रूप में सहेजें – अंतिम आउटपुट

आयत और उसकी छाया परिभाषित होने के बाद, अंतिम चरण Word दस्तावेज़ को PDF में निर्यात करना है। यह **save document as pdf** आवश्यकता को पूरा करता है।

```python
# Define the output path – replace YOUR_DIRECTORY with an actual folder
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)
print(f"PDF saved to {output_path}")
```

जब आप `shadow_rectangle.pdf` खोलेंगे, तो आपको एक ही पृष्ठ पर ग्रे‑बॉर्डर वाली आयत दिखाई देगी जिसका शीर्षक “Shadow demo” है और जिसमें एक स्पष्ट, विकर्ण छाया होगी।

### अपेक्षित आउटपुट

* `shadow_rectangle.pdf` नाम की एक PDF फ़ाइल।
* 200 pt × 100 pt आयत के साथ एक पृष्ठ।
* 45° कोण पर 5 pt ऑफ़सेट वाली दृश्यमान छाया, 8 pt ब्लर के साथ।

## चरण 5: विविधताओं और किनारी मामलों का अन्वेषण (वैकल्पिक)

नीचे सामान्य ट्यून‑अप्स दिए गए हैं जो आपको वास्तविक‑दुनिया प्रोजेक्ट्स में चाहिए हो सकते हैं:

| विविधता | कोड स्निपेट | कब उपयोग करें |
|-----------|--------------|-------------|
| **विभिन्न आकार प्रकार** (जैसे, एलिप्स) | `aw.drawing.ShapeType.OVAL` instead of `RECTANGLE` | गोलाकार ग्राफ़िक्स या बैज के लिए |
| **कस्टम छाया रंग** | `shadow.color = aw.drawing.Color.from_argb(255, 100, 100, 100)` | जब ग्रे या ब्रांड‑विशिष्ट छाया की आवश्यकता हो |
| **एकाधिक आकार** | Repeat the shape‑creation block and adjust `left`/`top` properties | जटिल आरेख बनाने के लिए |
| **आकार के अंदर कोई टेक्स्ट नहीं** | Omit `rectangle.text = "..."` | जब आकार केवल सजावटी हो |
| **उच्च DPI आउटपुट** | `doc.save(output_path, aw.SaveFormat.PDF, aw.PdfSaveOptions())` with `PdfSaveOptions` set for image quality | प्रिंट‑तैयार PDFs के लिए |

**Pro tip:** अन्य प्रॉपर्टीज़ समायोजित करने से पहले हमेशा `shadow.visible = True` सेट करें; अन्यथा परिवर्तन चुपचाप अनदेखा हो जाते हैं।

## पूर्ण स्क्रिप्ट – कॉपी, पेस्ट और चलाएँ

```python
import aspose.words as aw

# 1️⃣ Create a new blank document
doc = aw.Document()

# 2️⃣ Add a rectangle shape
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
rectangle.width = 200          # width in points
rectangle.height = 100         # height in points
rectangle.text = "Shadow demo"

# 3️⃣ Configure a visible shadow effect
shadow = rectangle.shadow_effect
shadow.visible = True
shadow.blur = 8                # blur radius (pt)
shadow.distance = 5            # offset distance (pt)
shadow.angle = 45              # direction (degrees)
shadow.color = aw.drawing.Color.black

# 4️⃣ Save the document as a PDF
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)

print(f"PDF successfully created at: {output_path}")
```

टर्मिनल या IDE से स्क्रिप्ट चलाएँ। `YOUR_DIRECTORY` को वास्तविक फ़ोल्डर पाथ से बदलें, जैसे `"/tmp"` या `"C:\\Users\\Me\\Documents"`।

## निष्कर्ष

आप अब जानते हैं कि Aspose.Words for Python का उपयोग करके **PDF में आयत बनाना**, **आकार में छाया जोड़ना**, **आकार की छाया कॉन्फ़िगर करना**, और **दस्तावेज़ को PDF के रूप में सहेजना** कैसे किया जाता है। पूरा उदाहरण दस्तावेज़ निर्माण से लेकर अंतिम निर्यात तक हर चरण को दर्शाता है, और वैकल्पिक विविधताएँ दिखाती हैं कि अधिक जटिल परिदृश्यों के लिए कोड को कैसे अनुकूलित किया जाए।

आगे आप खोज सकते हैं:

* अन्य आकार प्रकार जोड़ना (`ShapeType.LINE`, `ShapeType.ELLIPSE`)।
* ग्रेडिएंट फिल या बॉर्डर लागू करना ताकि दृश्य आकर्षण बढ़े।
* फ़ॉन्ट एम्बेड करने या इमेज कम्प्रेशन नियंत्रित करने के लिए `PdfSaveOptions` का उपयोग करना।

पैरामीटरों के साथ प्रयोग करने में संकोच न करें ताकि वे आपके ब्रांडिंग या डिज़ाइन गाइडलाइन से मेल खाएँ। हैप्पी PDF स्क्रिप्टिंग!

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करेंगे।

- [Aspose.Words for Python का उपयोग करके PDF बुकमार्क अनुकूलित करें](/words/english/python-net/performance-optimization/optimize-pdf-bookmarks-aspose-words-python/)
- [Python Aspose Words के साथ PDF लोडिंग अनुकूलित करें (इमेज स्किप)](/words/hindi/python-net/performance-optimization/optimize-pdf-loading-python-aspose-words-skip-images/)
- [Aspose Words Python PDF हेरफेर](/words/hongkong/python-net/document-operations/aspose-words-python-pdf-manipulation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}