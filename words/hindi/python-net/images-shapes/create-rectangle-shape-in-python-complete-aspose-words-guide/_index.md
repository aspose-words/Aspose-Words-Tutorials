---
category: general
date: 2026-06-24
description: Aspose.Words के साथ Python में आयताकार आकार बनाएं, सीखें कि आकार में
  छाया कैसे जोड़ें, छाया का कोण सेट करें, और मिनटों में दस्तावेज़ को PDF के रूप में
  सहेजें।
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shape shadow
- set shadow angle
language: hi
og_description: Python में आयताकार आकार बनाएं, आकार पर छाया जोड़ें, छाया का कोण सेट
  करें, और Aspose.Words के साथ दस्तावेज़ को PDF के रूप में सहेजें। इस चरण‑दर‑चरण मार्गदर्शिका
  का पालन करें।
og_title: Python में आयताकार आकार बनाएं – पूर्ण Aspose.Words ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  headline: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  name: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: What if I need a different shape?
    text: Aspose.Words supports many `ShapeType` values (ellipse, star, callout, etc.).
      Simply replace `aw.drawing.ShapeType.RECTANGLE` with the desired enum, like
      `aw.drawing.ShapeType.ELLIPSE`.
  - name: Can I add multiple shadows?
    text: The API exposes only one `ShadowFormat` per shape, but you can simulate
      multiple shadows by duplicating the shape, offsetting each copy, and adjusting
      transparency.
  - name: How do I change the shadow color to match my brand?
    text: Just set `shadow.color` to any `aw.drawing.Color`. For a brand blue, use
      `aw.drawing.Color.from_argb(255, 0, 120, 215)`.
  - name: What about saving as DOCX instead of PDF?
    text: Replace `document.save(pdf_path)` with `document.save("output/shadowed_rectangle.docx")`.
      The shadow rendering is preserved across both formats.
  - name: Does the shadow work on older PDF viewers?
    text: Aspose.Words renders the shadow as a vector effect, which is widely supported.
      However, very old viewers might flatten the effect; testing on your target audience’s
      devices is always a good habit.
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Python में आयताकार आकार बनाएं – Aspose.Words का पूर्ण गाइड
url: /hi/python/images-shapes/create-rectangle-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python में आयताकार आकार बनाएं – पूर्ण Aspose.Words गाइड

क्या आपने कभी सोचा है कि Python का उपयोग करके Word दस्तावेज़ में **आयताकार आकार** कैसे बनाएं? शायद आपको एक बोल्ड कॉल‑आउट बॉक्स, एक आरेख के लिए दृश्य संकेत, या सिर्फ रिपोर्ट के लिए एक शानदार आयत चाहिए। जो भी हो, आप सही जगह पर आए हैं। इस ट्यूटोरियल में हम पूरी प्रक्रिया को समझेंगे—आयत को डालने से लेकर, एक सूक्ष्म छाया जोड़ने, छाया के कोण को समायोजित करने, और अंत में **दस्तावेज़ को PDF के रूप में सहेजने** तक, ताकि आप इसे किसी के साथ भी साझा कर सकें।

हम **Aspose.Words for Python via .NET** का उपयोग करेंगे, जो एक शक्तिशाली लाइब्रेरी है जो आपको Word फ़ाइलों को बिना Word खोले ही संशोधित करने देती है। इस गाइड के अंत तक आप आत्मविश्वास के साथ प्रश्न *“shape shadow कैसे जोड़ें”* का उत्तर दे पाएंगे, और आपके पास एक तैयार‑चलाने‑योग्य स्क्रिप्ट होगी जिसे आप किसी भी प्रोजेक्ट में डाल सकते हैं।

---

## आप को क्या चाहिए

- **Python 3.8+** आपके मशीन पर स्थापित होना चाहिए।  
- **Aspose.Words for Python via .NET** (`aspose-words` पैकेज)। इसे इस तरह स्थापित करें:

  ```bash
  pip install aspose-words
  ```

- एक लिखने योग्य फ़ोल्डर जहाँ उत्पन्न PDF सहेजा जाएगा।  
- (वैकल्पिक) एक IDE या टेक्स्ट एडिटर—VS Code बहुत अच्छा काम करता है।  

बस इतना ही। कोई अतिरिक्त DLLs नहीं, कोई Office इंस्टॉलेशन नहीं, सिर्फ एक ही pip पैकेज।

---

## चरण 1: दस्तावेज़ और बिल्डर सेट अप करें

पहला काम जो आपको करना है वह है **आयताकार आकार**‑मित्र ऑब्जेक्ट्स बनाना: एक `Document` और एक `DocumentBuilder`। बिल्डर को अपने पेन की तरह सोचें; यह आपके लिए सब कुछ ड्रॉ करता है।

```python
import aspose.words as aw

# Initialize a new blank document
document = aw.Document()

# DocumentBuilder gives us a convenient way to add content
builder = aw.DocumentBuilder(document)
```

> **यह क्यों महत्वपूर्ण है:** `Document` ऑब्जेक्ट पूरे .docx फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` ऐसे मेथड्स प्रदान करता है जैसे `insert_shape` जो आकार ड्रॉ करना आसान बनाते हैं।

---

## चरण 2: आयताकार आकार डालें

अब जब हमारे पास बिल्डर है, हम अंततः **आयताकार आकार** बना सकते हैं। `insert_shape` मेथड को तीन आर्ग्यूमेंट्स चाहिए: आकार का प्रकार, चौड़ाई, और ऊँचाई। हम एक अच्छा अनुपात पाने के लिए 200 pt चौड़ाई और 100 pt ऊँचाई का उपयोग करेंगे।

```python
# Insert a rectangle with a width of 200 points and a height of 100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

इस चरण पर आपने सफलतापूर्वक अपने दस्तावेज़ में **आयताकार आकार** बना लिया है। यदि आप उत्पन्न DOCX खोलते हैं (हम बाद में करेंगे), तो आप देखेंगे कि कर्सर की स्थिति पर एक साधारण आयत मौजूद है।

---

## चरण 3: शैडो फ़ॉर्मेटिंग ऑब्जेक्ट तक पहुँचें

**shape में शैडो जोड़ने** के लिए, हमें पहले shape की शैडो फ़ॉर्मेटिंग को पकड़ना होगा। Aspose.Words में हर shape के पास एक `shadow_format` प्रॉपर्टी होती है जो सभी शैडो‑संबंधी सेटिंग्स को उजागर करती है।

```python
# Grab the shadow formatting object for later tweaks
shadow = rectangle.shadow_format
```

`shadow` रेफ़रेंस होने से हम दृश्यता, ब्लर, दूरी, कोण, रंग, और पारदर्शिता को कुछ ही कोड लाइनों में टॉगल कर सकते हैं।

---

## चरण 4: शैडो को सक्षम करें और उसकी उपस्थिति कॉन्फ़िगर करें

यहीं पर जादू होता है। हम **shape में शैडो जोड़ेंगे**, उसे थोड़ा ब्लर करेंगे, थोड़ा ऑफ़सेट करेंगे, दिशा सेट करेंगे (यह **शैडो कोण सेट करना** भाग है), और उसे अर्द्ध‑पारदर्शी काली रंगत देंगे।

```python
# Turn the shadow on
shadow.visible = True

# Soften the edges – a blur radius of 8 points looks natural
shadow.blur_radius = 8.0

# Push the shadow away from the rectangle by 5 points
shadow.distance = 5.0

# Set the direction of the light source – 45 degrees creates a diagonal drop
shadow.angle = 45

# Choose a color; black works well for most documents
shadow.color = aw.drawing.Color.black

# Make the shadow 30 % transparent for a subtle effect
shadow.transparency = 0.3
```

> **प्रो टिप:** यदि आपको कभी अधिक नाटकीय प्रभाव चाहिए, तो `blur_radius` बढ़ाएँ या `transparency` घटाएँ। इसके विपरीत, एक तीखा, पूरी तरह अपारदर्शी शैडो `blur_radius = 0` और `transparency = 0` के साथ प्राप्त किया जा सकता है।

---

## चरण 5: दस्तावेज़ को PDF के रूप में सहेजें

हमने **आयताकार आकार बनाया**, हमने **shape में शैडो जोड़ी**, और अब हम **दस्तावेज़ को PDF के रूप में सहेजेंगे** ताकि परिणाम किसी भी डिवाइस पर समान दिखे। Aspose.Words इसे एक लाइन में कर देता है।

```python
# Define where you want the PDF to land
output_path = "output/shadowed_rectangle.pdf"

# Save the whole document (including the rectangle with its shadow) as PDF
document.save(output_path)
print(f"PDF saved to {output_path}")
```

स्क्रिप्ट चलाने पर `output` फ़ोल्डर में `shadowed_rectangle.pdf` उत्पन्न होगा। इसे किसी भी PDF व्यूअर से खोलें और आप एक साफ़ आयत को नरम, 45‑डिग्री शैडो के साथ देखेंगे—बिल्कुल वही जो हमने कॉन्फ़िगर किया था।

---

## पूरा कार्यशील उदाहरण

नीचे वह पूर्ण, तैयार‑चलाने‑योग्य स्क्रिप्ट है जो ऊपर के सभी चरणों को मिलाती है। इसे `create_rectangle_with_shadow.py` नाम की फ़ाइल में कॉपी‑पेस्ट करें और `python create_rectangle_with_shadow.py` चलाएँ।

```python
import aspose.words as aw
import os

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Initialize document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert the rectangle shape (200 pt × 100 pt)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Access shadow formatting
shadow = rectangle.shadow_format

# 4️⃣ Configure shadow – visible, blurred, offset, angled, colored, semi‑transparent
shadow.visible = True
shadow.blur_radius = 8.0          # softer edges
shadow.distance = 5.0            # how far the shadow sits from the shape
shadow.angle = 45                # direction in degrees – this is the **set shadow angle** step
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.3        # 30 % transparent

# 5️⃣ Save the document as PDF
pdf_path = os.path.join(output_dir, "shadowed_rectangle.pdf")
document.save(pdf_path)

print(f"✅ PDF created at: {pdf_path}")
```

**अपेक्षित आउटपुट:** एक PDF फ़ाइल जिसमें एकल आयत को हल्की, तिरछी शैडो के साथ दिखाया गया है। कोई अतिरिक्त पेज नहीं, कोई छिपे हुए आर्टिफैक्ट नहीं—सिर्फ वह shape जो हमने बनाया।

---

## सामान्य प्रश्न और किनारे के मामलों

### अगर मुझे कोई अलग shape चाहिए तो?

Aspose.Words कई `ShapeType` मानों (ellipse, star, callout, आदि) को सपोर्ट करता है। बस `aw.drawing.ShapeType.RECTANGLE` को इच्छित enum से बदल दें, जैसे `aw.drawing.ShapeType.ELLIPSE`।

### क्या मैं कई शैडो जोड़ सकता हूँ?

API प्रत्येक shape के लिए केवल एक `ShadowFormat` प्रदान करती है, लेकिन आप shape को डुप्लिकेट करके, प्रत्येक कॉपी को ऑफ़सेट करके, और पारदर्शिता को समायोजित करके कई शैडो का सिमुलेशन कर सकते हैं।

### मैं शैडो का रंग अपने ब्रांड से मेल खाने के लिए कैसे बदलूँ?

बस `shadow.color` को किसी भी `aw.drawing.Color` पर सेट करें। ब्रांड ब्लू के लिए, `aw.drawing.Color.from_argb(255, 0, 120, 215)` उपयोग करें।

### PDF के बजाय DOCX के रूप में सहेजने के बारे में क्या?

`document.save(pdf_path)` को `document.save("output/shadowed_rectangle.docx")` से बदलें। शैडो रेंडरिंग दोनों फ़ॉर्मेट में संरक्षित रहती है।

### क्या शैडो पुराने PDF व्यूअर्स पर काम करता है?

Aspose.Words शैडो को एक वेक्टर इफ़ेक्ट के रूप में रेंडर करता है, जो व्यापक रूप से समर्थित है। हालांकि, बहुत पुराने व्यूअर्स इस इफ़ेक्ट को फ्लैट कर सकते हैं; अपने लक्षित दर्शकों के डिवाइसों पर परीक्षण करना हमेशा एक अच्छी आदत है।

---

## अपने PDF को निखारने के टिप्स

- **बॉर्डर जोड़ें:** `rectangle.line_format.width = 1.5` और एक साफ़ आउटलाइन के लिए रंग सेट करें।  
- **आयत को केंद्रित करें:** डालने से पहले `builder.move_to_document_start()` उपयोग करें, फिर `builder.paragraph_format.alignment = aw.ParagraphAlignment.CENTER` सेट करें।  
- **टेक्स्ट के साथ मिलाएँ:** आयत के बाद एक `TextFragment` डालें ताकि उसे लेबल किया जा सके, उदाहरण के लिए `"Important Section"`।

ये छोटे बदलाव एक साधारण आयत को एक निखरा हुआ कॉल‑आउट बॉक्स बना सकते हैं जो रिपोर्ट, प्रस्ताव, या ई‑बुक्स में पेशेवर दिखता है।

---

## निष्कर्ष

अब आपके पास Python में **आयताकार आकार बनाने**, **shape में शैडो जोड़ने**, **शैडो का कोण सेट करने**, और Aspose.Words का उपयोग करके **दस्तावेज़ को PDF के रूप में सहेजने** की एक ठोस, अंत‑से‑अंत रेसिपी है। चरण सरल हैं, कोड पूरी तरह से स्वतंत्र है, और आपने देखा कि प्रत्येक लाइन क्यों महत्वपूर्ण है—दस्तावेज़ को इनिशियलाइज़ करने से लेकर अंतिम PDF को निखारने तक।

आगे, आप **shape में शैडो कैसे जोड़ें** को अधिक जटिल ड्रॉइंग्स में खोज सकते हैं, ग्रेडिएंट फ़िल्स के साथ प्रयोग कर सकते हैं, या अपने shapes के अंदर टेबल बना सकते हैं। लाइब्रेरी shapes को बुकमार्क्स से लिंक करने का भी समर्थन करती है, जो इंटरैक्टिव PDFs के लिए उपयोगी हो सकता है।

क्या आपने कोई नया तरीका आज़माया? टिप्पणी में साझा करें, या कोई भी बचे हुए प्रश्न पूछें। कोडिंग का आनंद लें, और अपने दस्तावेज़ों में अतिरिक्त गहराई जोड़ने का मज़ा लें! 

![शैडो के साथ आयताकार आकार – Python में आयताकार आकार बनाने का उदाहरण](/images/rectangle-shadow.png)


## अगला क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Word दस्तावेज़ Java बनाएं – शैडो इफ़ेक्ट के साथ आयताकार आकार जोड़ें](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow ट्यूटोरियल – C# में Word Shape में शैडो जोड़ें](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [C# का उपयोग करके Word में आयताकार आकार बनाएं – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}