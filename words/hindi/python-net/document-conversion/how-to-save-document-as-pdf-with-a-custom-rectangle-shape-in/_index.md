---
category: general
date: 2026-10-07
description: Aspose.Words for Python का उपयोग करके दस्तावेज़ को PDF के रूप में सहेजना
  सीखें, साथ ही एक आयताकार आकार और कस्टम शैडो जोड़ें। चरण‑दर‑चरण कोड शामिल है।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as pdf
- add rectangle shape
- export word to pdf
- set rectangle dimensions
- draw rectangle word
language: hi
lastmod: 2026-10-07
og_description: Aspose.Words for Python का उपयोग करके कस्टम आयताकार आकार के साथ दस्तावेज़
  को PDF के रूप में सहेजें। ड्रॉ करने, स्टाइल करने और Word को PDF में निर्यात करने
  के लिए पूर्ण उदाहरण का पालन करें।
og_image_alt: Screenshot of the generated PDF showing the rectangle shape after save
  document as pdf
og_title: दस्तावेज़ को आयताकार आकार के साथ PDF के रूप में सहेजें – पूर्ण पायथन गाइड
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  headline: How to save document as PDF with a custom rectangle shape in Python
  type: TechArticle
- description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  name: How to save document as PDF with a custom rectangle shape in Python
  steps:
  - name: Initialize a new blank document
    text: '```python import aspose.words as aw'
  - name: Add rectangle shape to the document
    text: '```python # Create a rectangle shape and attach it to the document. rectangle
      = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)'
  - name: Set rectangle dimensions
    text: '```python # Define width and height in points (1 point = 1/72 inch). rectangle.width
      = 200 # 200 points ≈ 2.78 inches rectangle.height = 100 # 100 points ≈ 1.39
      inches ```'
  - name: (Optional) Apply a visible custom shadow
    text: '```python shadow = rectangle.shadow_format shadow.visible = True # Show
      the shadow shadow.blur = 5.0 # Softness of the shadow edge shadow.distance =
      3.0 # How far the shadow is offset shadow.angle = 45 # Direction in degrees
      shadow.color = aw.drawing.Color.black ```'
  - name: Save document as PDF
    text: '```python output_path = "output/shadow_rectangle.pdf" document.save(output_path)
      print(f"PDF saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Word automation
title: Python में कस्टम आयताकार आकार के साथ दस्तावेज़ को PDF के रूप में कैसे सहेजें
url: /hi/python/document-conversion/how-to-save-document-as-pdf-with-a-custom-rectangle-shape-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python में कस्टम आयताकार आकार के साथ दस्तावेज़ को PDF के रूप में सहेजें

यदि आपको कस्टम ग्राफ़िक्स जोड़ते हुए **save document as PDF** करना है, तो यह गाइड आपको दिखाएगा कैसे। हम एक खाली Word फ़ाइल बनाने, **drawing a rectangle shape** करने, उसका आकार सेट करने, एक दृश्यमान शैडो लागू करने, और अंत में Aspose.Words for Python लाइब्रेरी का उपयोग करके **export Word to PDF** करने की प्रक्रिया से गुजरेंगे।

आपके पास एक PDF होगा जिसमें एक बिल्कुल सही स्थान पर रखा गया आयताकार होगा, जो रिपोर्ट, इनवॉइस या किसी भी दस्तावेज़‑ऑटोमेशन परिदृश्य के लिए तैयार है। कोई बाहरी टूल आवश्यक नहीं—सिर्फ Python और Aspose.Words पैकेज।

## आपको क्या चाहिए

| आवश्यकता | क्यों महत्वपूर्ण है |
|-------------|----------------|
| Python 3.8+ | Aspose.Words for Python API आधुनिक इंटरप्रेटर्स को लक्षित करता है। |
| `aspose-words` पैकेज (`pip install aspose-words`) | कोड उदाहरणों में उपयोग किए जाने वाले `aw` नेमस्पेस को प्रदान करता है। |
| Python और ऑब्जेक्ट‑ओरिएंटेड प्रोग्रामिंग की बुनियादी परिचितता | ट्यूटोरियल `Document` और `Shape` जैसे ऑब्जेक्ट्स को नियंत्रित करता है। |
| उस फ़ोल्डर में लिखने की अनुमति जहाँ PDF सहेजा जाएगा | `save document as pdf` चरण डिस्क पर फ़ाइल लिखता है। |

> **Pro tip:** निर्भरताओं को अलग रखने के लिए एक वर्चुअल एनवायरनमेंट (`python -m venv venv`) उपयोग करें।

## आयताकार आकार के साथ दस्तावेज़ को PDF के रूप में सहेजने का तरीका

नीचे एक पूर्ण, चलाने योग्य उदाहरण दिया गया है। प्रत्येक चरण की व्याख्या की गई है ताकि आप समझ सकें **why** हम यह कार्रवाई करते हैं, न कि केवल **what** कोड करता है।

### चरण 1: एक नया खाली दस्तावेज़ प्रारंभ करें

```python
import aspose.words as aw

# Create an empty Word document – this is the canvas for our shape.
document = aw.Document()
```

एक नया `Document` ऑब्जेक्ट बनाने से आपको एक साफ़ पेज कलेक्शन मिलता है। आप बाद में **export Word to PDF** करने के लिए मौजूदा *.docx* भी लोड कर सकते हैं, लेकिन खाली से शुरू करने से उदाहरण केंद्रित रहता है।

### चरण 2: दस्तावेज़ में आयताकार आकार जोड़ें

```python
# Create a rectangle shape and attach it to the document.
rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

# The shape must be placed inside a paragraph before it appears.
paragraph = document.first_section.body.first_paragraph
paragraph.append_child(rectangle)
```

`add rectangle shape` चरण `ShapeType.RECTANGLE` का उपयोग करता है। आकार को पैराग्राफ में जोड़ने से, Aspose.Words को पता चलता है कि अंतिम PDF में इसे कहाँ रेंडर करना है।

### चरण 3: आयताकार आयाम सेट करें

```python
# Define width and height in points (1 point = 1/72 inch).
rectangle.width = 200   # 200 points ≈ 2.78 inches
rectangle.height = 100  # 100 points ≈ 1.39 inches
```

स्पष्ट **rectangle dimensions** सेट करने से आकार विभिन्न प्लेटफ़ॉर्म पर समान दिखता है। यदि आप इम्पीरियल इकाइयाँ पसंद करते हैं तो आप `convert_to_inches` हेल्पर्स का भी उपयोग कर सकते हैं।

### चरण 4: (वैकल्पिक) दृश्यमान कस्टम शैडो लागू करें

```python
shadow = rectangle.shadow_format
shadow.visible = True          # Show the shadow
shadow.blur = 5.0              # Softness of the shadow edge
shadow.distance = 3.0          # How far the shadow is offset
shadow.angle = 45              # Direction in degrees
shadow.color = aw.drawing.Color.black
```

शैडो PDF में आयताकार को उभारा बनाता है। `shadow.visible` फ़्लैग आवश्यक है; इसके बिना अन्य प्रॉपर्टीज़ का कोई प्रभाव नहीं होगा।

### चरण 5: दस्तावेज़ को PDF के रूप में सहेजें

```python
output_path = "output/shadow_rectangle.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

`document.save` को **.pdf** एक्सटेंशन के साथ कॉल करने से Aspose.Words के बिल्ट‑इन PDF रेंडरर का उपयोग करके स्वचालित रूप से **save document as pdf** हो जाता है। अतिरिक्त रूपांतरण चरणों की आवश्यकता नहीं है, इसलिए यह विधि **export Word to PDF** करने का अनुशंसित तरीका है।

> **Why this works:** Aspose.Words दस्तावेज़ का लेआउट, जिसमें आयताकार और उसकी शैडो शामिल है, सीधे PDF स्ट्रीम में लिखता है। प्रक्रिया लॉसलेस है और वेक्टर गुणवत्ता को बनाए रखती है।

## पूर्ण स्रोत कोड (एकल स्क्रिप्ट)

```python
import aspose.words as aw

def create_pdf_with_rectangle(output_path: str):
    """
    Creates a PDF that contains a single rectangle shape with a custom shadow.
    The function demonstrates:
    • add rectangle shape
    • set rectangle dimensions
    • export Word to PDF (save document as pdf)
    """
    # 1️⃣ Create a new blank document
    document = aw.Document()

    # 2️⃣ Insert a rectangle shape
    rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

    # 3️⃣ Set the shape's size
    rectangle.width = 200   # points
    rectangle.height = 100  # points

    # 4️⃣ Configure a visible shadow
    shadow = rectangle.shadow_format
    shadow.visible = True
    shadow.blur = 5.0
    shadow.distance = 3.0
    shadow.angle = 45
    shadow.color = aw.drawing.Color.black

    # 5️⃣ Add shape to the first paragraph
    paragraph = document.first_section.body.first_paragraph
    paragraph.append_child(rectangle)

    # 6️⃣ Save the document as PDF
    document.save(output_path)
    print(f"PDF successfully saved to: {output_path}")

if __name__ == "__main__":
    create_pdf_with_rectangle("output/shadow_rectangle.pdf")
```

इस स्क्रिप्ट को चलाने से `shadow_rectangle.pdf` बनता है जो इस प्रकार दिखता है:

![सहेजे गए दस्तावेज़ को PDF के रूप में बनाने के बाद आयताकार आकार दिखाने वाला उत्पन्न PDF का आरेख](placeholder-image.png)

*PDF में एक पृष्ठ है जिसमें दस्तावेज़ के केंद्र में काली‑शैडो वाला आयताकार है।*

## सामान्य प्रश्न और किनारे के मामले

| प्रश्न | उत्तर |
|----------|--------|
| **क्या मैं आयताकार को एक विशिष्ट स्थान पर रख सकता हूँ?** | हाँ। सहेजने से पहले `rectangle.left` और `rectangle.top` (पॉइंट्स में) सेट करें। |
| **यदि मुझे कई आकार चाहिए तो क्या करें?** | अतिरिक्त `Shape` ऑब्जेक्ट बनाएं, प्रत्येक को कॉन्फ़िगर करें, और उन्हें एक ही या अलग पैराग्राफ में जोड़ें। |
| **क्या शैडो PDF के आकार को प्रभावित करती है?** | केवल थोड़ा; शैडो वेक्टर मेटाडेटा के रूप में संग्रहीत होती है, न कि रास्टर इमेज के रूप में। |
| **क्या मैं इसे मौजूदा *.docx* फ़ाइलों को बदलने के लिए उपयोग कर सकता हूँ?** | बिल्कुल। `aw.Document()` को `aw.Document("input.docx")` से बदलें और बाकी चरण अपरिवर्तित रहेंगे। |
| **क्या आयताकार के भराव रंग को बदलने का कोई तरीका है?** | `rectangle.fill_color = aw.drawing.Color.light_blue` सेट करें (या कोई भी `Color` जो आप पसंद करें)। |

## अगले कदम

अब जब आप जानते हैं कि कैसे **save document as PDF** को कस्टम आयताकार के साथ किया जाता है, आप आगे खोज सकते हैं:

* **Export Word to PDF** को हेडर, फुटर और पेज नंबरों के साथ।  
* **Add other drawing objects** (`Ellipse`, `Polygon`) को उसी `Shape` क्लास का उपयोग करके जोड़ें।  
* **Batch process** एक फ़ोल्डर में Word फ़ाइलों को, प्रत्येक पर समान आयताकार ओवरले लागू करके।  

ये विस्तार समान पैटर्न का पालन करते हैं: एक आकार बनाएं, उसकी प्रॉपर्टीज़ कॉन्फ़िगर करें, और **save document as pdf**।

---

**Summary:** इस ट्यूटोरियल ने आपको दिखाया कि कैसे **save document as PDF** करते हुए **add rectangle shape**, **set rectangle dimensions**, और Aspose.Words for Python का उपयोग करके कस्टम शैडो लागू किया जाए। पूर्ण स्क्रिप्ट कॉपी, चलाने और अपने दस्तावेज़‑ऑटोमेशन पाइपलाइन में अनुकूलित करने के लिए तैयार है। कोडिंग का आनंद लें!

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स निकटतम संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का पता लगाने में मदद करती हैं।

- [आयताकार आकार बनाएं, शैडो जोड़ें और PDF सहेजें](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Aspose.Words के साथ PDF में आयताकार जोड़ें – चरण‑दर‑चरण गाइड](/words/english/python-net/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/)
- [Aspose.Words के साथ दस्तावेज़ को PDF के रूप में सहेजें – पूर्ण C# गाइड](/words/english/net/programming-with-pdfsaveoptions/save-document-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}