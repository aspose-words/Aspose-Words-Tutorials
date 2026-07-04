---
category: general
date: 2026-05-04
description: Aspose.Words for Python का उपयोग करके आयताकार आकार कैसे बनाएं, छाया के
  साथ आकार कैसे जोड़ें, छाया का रंग बदलें, छाया की दूरी सेट करें और दस्तावेज़ को PDF
  के रूप में सहेजें, यह सीखें।
draft: false
keywords:
- create rectangle shape
- how to add shape
- change shadow color
- save document as pdf
- set shadow distance
language: hi
og_description: Aspose.Words for Python के साथ आयताकार आकार बनाएं, आकार जोड़ना, छाया
  का रंग बदलना, छाया की दूरी सेट करना, और दस्तावेज़ को PDF के रूप में सहेजना सीखें।
og_title: आयताकार आकार बनाएं – छाया जोड़ें, रंग बदलें और PDF के रूप में सहेजें
tags:
- Aspose.Words
- Python
- PDF generation
title: Python में आयताकार आकार बनाएं – छायाएँ जोड़ने और PDF के रूप में सहेजने के लिए
  पूर्ण मार्गदर्शिका
url: /hi/python/images-shapes/create-rectangle-shape-in-python-full-guide-to-adding-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# आयताकार आकार बनाएं – Python डेवलपर्स के लिए पूर्ण ट्यूटोरियल

क्या आपको कभी Word दस्तावेज़ में **create rectangle shape** बनाने की ज़रूरत पड़ी है और आप सोचते हैं कि इसे एक परिष्कृत शैडो कैसे दिया जाए? शायद आप एक रिपोर्ट जेनरेटर बना रहे हैं और विज़ुअल पॉलिश महत्वपूर्ण है—विशेषकर जब अंतिम आउटपुट PDF हो। अच्छी खबर? Aspose.Words for Python के साथ आप न केवल **how to add shape** कर सकते हैं बल्कि रंग से लेकर दूरी तक हर शैडो प्रॉपर्टी को ट्यून कर सकते हैं, और फिर **save document as pdf** एक ही सहज प्रवाह में कर सकते हैं।

इस गाइड में हम पूरे प्रोसेस को चरण‑बद्ध तरीके से देखेंगे। आप वह सटीक कोड देखेंगे जिसे आप कॉपी‑पेस्ट कर सकते हैं, समझेंगे कि *क्यों* प्रत्येक लाइन महत्वपूर्ण है, और कुछ टिप्स भी सीखेंगे जो एज केस (जैसे ट्रांसपेरेंट शैडो या नॉन‑स्टैंडर्ड DPI) को संभालने में मदद करेंगे। अंत तक आप **create rectangle shape** बना पाएँगे, उसकी शैडो को कस्टमाइज़ करेंगे, और बिना किसी परेशानी के एक साफ़ PDF एक्सपोर्ट करेंगे।

## आवश्यकताएँ

- Python 3.8+ आपके मशीन पर स्थापित हो।  
- Aspose.Words for Python `pip install aspose-words` के माध्यम से।  
- ऑब्जेक्ट‑ओरिएंटेड Python की बुनियादी समझ (कुछ भी जटिल नहीं)।  

यदि आपका वर्चुअल एनवायरनमेंट पहले से सेट है, तो बस इंस्टॉल कमांड चलाएँ और आप तैयार हैं।

## चरण 1: दस्तावेज़ और बिल्डर को प्रारंभ करें

शैडो जोड़ने से पहले, आपको एक खाली दस्तावेज़ चाहिए। `Document` क्लास पूरी फ़ाइल को दर्शाता है, और `DocumentBuilder` आपका पेंटब्रश है।

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder to edit it
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

*क्यों यह महत्वपूर्ण है:* `Document` सभी सेक्शन, पेज और रिसोर्सेज़ को रखता है। `DocumentBuilder` आपको एक फ़्लुएंट API देता है जिससे आप कंटेंट ठीक उसी जगह डाल सकते हैं जहाँ चाहिए—जैसे वर्ड प्रोसेसर में कर्सर।

## चरण 2: आयताकार आकार डालें

अब हम वास्तव में **how to add shape** करेंगे। `insert_shape` मेथड को आकार का प्रकार और उसके आयाम (पॉइंट्स में) चाहिए। यहाँ हम 200 × 100 pt का आयत चुनते हैं और उसे हल्के‑नीले रंग से भरते हैं।

```python
# Step 2: Insert a rectangle shape and give it a light‑blue fill
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,  # shape type
    200,                            # width in points
    100)                            # height in points
rectangle_shape.fill_color = aw.Color.light_blue
```

*प्रो टिप:* यदि आपको आकार को मौजूदा टेक्स्ट के साथ संरेखित करना है, तो डालने से पहले `builder.move_to` का उपयोग करें, या निर्माण के बाद `left`/`top` प्रॉपर्टीज़ को समायोजित करें।

## चरण 3: शैडो चालू करें

शैडो के बिना आकार सपाट दिखता है। शैडो की दूरी सेट करने और प्रभाव दिखाने के लिए, शैडो फ़ॉर्मेट को प्राप्त करें और उसे एनेबल करें।

```python
# Step 3: Access the shape's shadow format and make the shadow visible
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
```

*क्यों यह कदम:* शैडो फ़ॉर्मेट एक अलग ऑब्जेक्ट है; `visible` को टॉगल करना पहला काम है, अन्यथा सभी शैडो प्रॉपर्टीज़ अनदेखी रह जाती हैं।

## चरण 4: शैडो को स्टाइल करें – रंग, ब्लर, दूरी, दिशा

यहीं पर जादू होता है। हम **change shadow color** करेंगे, ब्लर रेडियस को एडजस्ट करेंगे, शैडो को आयत से कितनी दूरी पर रखेंगे, और उसे 45° घुमा देंगे।

```python
# Step 4: Configure the appearance of the shadow
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER   # outer shadow
rectangle_shadow.blur_radius = 10.0                    # blur amount (pixels)
rectangle_shadow.distance = 5.0                        # distance from the shape
rectangle_shadow.direction = 45.0                     # angle in degrees
rectangle_shadow.color = aw.Color.gray                 # shadow colour
```

*प्रत्येक प्रॉपर्टी की व्याख्या:*

| प्रॉपर्टी | क्या करता है | सामान्य मान |
|----------|--------------|------------|
| `style` | निर्धारित करता है कि शैडो *inner* है या *outer*। | `OUTER` (सबसे आम) |
| `blur_radius` | नरमी को नियंत्रित करता है; अधिक मान = धुंधले किनारे। | 0–20 px सामान्यतः |
| `distance` | शैडो आकार से कितनी दूरी पर ऑफ़सेट है। | 0–10 pt सूक्ष्म के लिए, >10 नाटकीय के लिए |
| `direction` | प्रकाश स्रोत का कोण, x‑axis से घड़ी की दिशा में मापा गया। | 0‑360° |
| `color` | शैडो का रंग। | कोई भी `aw.Color` (जैसे `gray`, `dark_red`) |

*एज केस:* यदि आप `distance` को `0` सेट करते हैं तो शैडो सीधे आकार के नीचे बैठ जाएगी, जिससे आकार का फ़िल छिप जाएगा। दृश्यमान ऑफ़सेट के लिए इसे `0` से ऊपर रखें।

## चरण 5: दस्तावेज़ को PDF के रूप में सहेजें

अंत में, हम **save document as pdf** करेंगे। Aspose.Words स्वचालित रूप से शैडो को रास्टराइज़ कर देता है, इसलिए PDF बिल्कुल Word व्यू जैसा दिखेगा।

```python
# Step 5: Save the document as a PDF with the shadowed shape
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

*PDF क्यों?* PDFs लेआउट को सभी प्लेटफ़ॉर्म पर बरकरार रखते हैं, जिससे वे रिपोर्ट, इनवॉइस या किसी भी प्रिंटेबल आर्टिफैक्ट के लिए आदर्श होते हैं।

---

![Create rectangle shape with shadow](https://example.com/images/rectangle-shadow.png){: .align-center alt="शैडो के साथ आयताकार आकार बनाने का उदाहरण"}

*ऊपर की छवि अंतिम PDF आउटपुट दिखाती है – एक हल्के‑नीले आयत के साथ एक नरम ग्रे आउटर शैडो, बिल्कुल वही जैसा हमने कॉन्फ़िगर किया था।*

## सामान्य प्रश्न और विविधताएँ

### अगर मुझे **transparent** शैडो चाहिए तो क्या करें?

शैडो के रंग पर अल्फा चैनल सेट करें:

```python
transparent_gray = aw.Color.from_argb(128, 0, 0, 0)  # 50% opacity black
rectangle_shadow.color = transparent_gray
```

### क्या मैं एक ही शैडो कई आकारों पर लागू कर सकता हूँ?

हाँ। एक आकार से `ShadowFormat` निकालें और उसे दूसरे में असाइन करें:

```python
another_shape = builder.insert_shape(aw.drawing.ShapeType.ELLIPSE, 150, 150)
another_shape.shadow_format = rectangle_shadow.clone()
```

### **different shape type** के लिए शैडो कैसे बदलें?

सभी आकार प्रकार एक ही `ShadowFormat` प्रॉपर्टीज़ साझा करते हैं, इसलिए आप वही कॉन्फ़िगरेशन ब्लॉक री‑यूज़ कर सकते हैं—सिर्फ `ShapeType.RECTANGLE` को `ShapeType.OVAL`, `ShapeType.TRIANGLE` आदि से बदलें।

### प्रिंट के लिए **high‑resolution PDFs** कैसे बनाएं?

`PdfSaveOptions` को उच्च DPI के साथ निर्दिष्ट करें:

```python
options = aw.saving.PdfSaveOptions()
options.image_resolution = 300  # 300 DPI for print quality
document.save(output_path, options)
```

## सारांश

हमने वह सब कवर किया जो आपको **create rectangle shape**, **how to add shape**, उसकी **shadow colour** को कस्टमाइज़ करने, **set shadow distance**, और अंत में **save document as pdf** करने के लिए चाहिए। पूरा, चलाने योग्य स्क्रिप्ट इस प्रकार है:

```python
import aspose.words as aw

# Initialise document
document = aw.Document()
builder = aw.DocumentBuilder(document)

# Insert rectangle shape
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle_shape.fill_color = aw.Color.light_blue

# Enable and style shadow
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER
rectangle_shadow.blur_radius = 10.0
rectangle_shadow.distance = 5.0
rectangle_shadow.direction = 45.0
rectangle_shadow.color = aw.Color.gray

# Save as PDF
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

स्क्रिप्ट चलाएँ, उत्पन्न `ShadowedShape.pdf` खोलें, और आपको एक साफ़ आयत के साथ एक सूक्ष्म ग्रे शैडो दिखेगा—बिल्कुल वही जो एक प्रोफ़ेशनल रिपोर्ट में अपेक्षित है।

## आगे क्या?

- **अन्य shape types** (`ShapeType.OVAL`, `ShapeType.LINE`) को एक्सप्लोर करें ताकि आपके दस्तावेज़ समृद्ध हों।  
- **कई शैडो को लेयर करके** संयोजित करें; आप एक इंटीरियर शैडो के साथ चमकीले रंग का उपयोग करके “ग्लो” इफ़ेक्ट भी बना सकते हैं।  
- **बैच प्रोसेसिंग को ऑटोमेट करें**: डेटा की एक कलेक्शन पर लूप चलाएँ, प्रत्येक पंक्ति के लिए एक आकार जनरेट करें, और सबको एक ही PDF में मर्ज करें।  
- **अन्य Aspose लाइब्रेरीज़** (जैसे Aspose.Slides) के साथ इंटीग्रेट करें यदि आपको वही विज़ुअल PowerPoint में भी एक्सपोर्ट करना है।

बिना झिझक प्रयोग करें—`blur_radius` बदलें, `direction` के साथ खेलें, या `gray` को अपने ब्रांड के रंग से बदलें। API इतना लचीला है कि कुछ छोटे बदलाव से विज़ुअल इम्पैक्ट में बड़ा अंतर आ सकता है।

कोई सवाल या जटिल केस है? नीचे कमेंट करें या Aspose कम्युनिटी फ़ोरम में पूछें। हैप्पी कोडिंग, और उन खूबसूरत शैडो वाले आयतों का आनंद लें!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}