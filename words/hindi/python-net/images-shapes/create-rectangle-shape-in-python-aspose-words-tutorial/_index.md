---
category: general
date: 2026-06-21
description: Aspose.Words का उपयोग करके Python में आयताकार आकार बनाएं। सीखें कि कैसे
  आकार में छाया जोड़ें, आकार का भराव रंग सेट करें, और मिनटों में दस्तावेज़ को PDF
  के रूप में सहेजें।
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- set shape fill color
language: hi
og_description: Aspose.Words के साथ Python में आयताकार आकार बनाएं। यह गाइड दिखाता
  है कि आकार में छाया कैसे जोड़ें, आकार का भराव रंग कैसे सेट करें, और दस्तावेज़ को
  PDF के रूप में कैसे सहेजें।
og_title: Python में आयताकार आकार बनाएं – Aspose.Words ट्यूटोरियल
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Create rectangle shape in Python using Aspose.Words. Learn how to add
    shadow to shape, set shape fill color, and save document as PDF in minutes.
  headline: Create rectangle shape in Python – Aspose.Words tutorial
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF generation
title: Python में आयताकार आकार बनाएं – Aspose.Words ट्यूटोरियल
url: /hi/python/images-shapes/create-rectangle-shape-in-python-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python में आयताकार आकार बनाएं – Aspose.Words ट्यूटोरियल

क्या आपने कभी **Word दस्तावेज़ में आयताकार आकार** बनाने के बारे में सोचा है जबकि आप Python में कोड लिख रहे हैं? आप अकेले नहीं हैं। कई डेवलपर्स को तब रुकावट आती है जब उन्हें एक तेज़ विज़ुअल एलिमेंट चाहिए—जैसे कि हल्के रंग का बॉक्स जिसमें हल्की छाया हो—और फिर उसे पूरी तरह PDF के रूप में एक्सपोर्ट करना होता है।  

इस गाइड में हम एक पूर्ण, चलाने योग्य उदाहरण के माध्यम से **आयताकार आकार बनाना**, **आकार का फ़िल रंग सेट करना**, **आकार में छाया जोड़ना**, और अंत में **दस्तावेज़ को PDF के रूप में सेव करना** दिखाएंगे। कोई अस्पष्ट संदर्भ नहीं, सिर्फ ठोस कोड जिसे आप आज़ ही कॉपी‑पेस्ट करके चला सकते हैं।

## What You’ll Need

शुरू करने से पहले सुनिश्चित करें कि आपके मशीन पर निम्नलिखित स्थापित हैं:

- Python 3.8 या नया (हमारी सिंटैक्स किसी भी हालिया संस्करण पर काम करती है)।
- एक सक्रिय Aspose.Words for Python लाइसेंस या फ्री ट्रायल (लाइब्रेरी पूरी तरह Python में है, कोई COM इंटरऑप आवश्यक नहीं)।
- वह टेक्स्ट एडिटर या IDE जिसमें आप सहज हों—VS Code बहुत अच्छा है, लेकिन कोई भी चलेगा।

बस इतना ही। कोई भारी फ्रेमवर्क नहीं, कोई अतिरिक्त OS‑लेवल डिपेंडेंसी नहीं। चलिए शुरू करते हैं।

## Step 1: Install Aspose.Words for Python

सबसे पहले, अगर आपने अभी तक नहीं किया है, तो पैकेज को PyPI से प्राप्त करें:

```bash
pip install aspose-words
```

यह कदम क्यों महत्वपूर्ण है: Aspose.Words वह `Document` और `DocumentBuilder` क्लास प्रदान करता है जिस पर हम निर्भर करेंगे। लाइब्रेरी के बिना, बाद में आने वाले कॉल—जैसे `insert_shape`—मौजूद नहीं होते, इसलिए स्क्रिप्ट लाइन भी खींचने से पहले ही क्रैश हो जाएगी।

> **Pro tip:** अपना वर्चुअल एनवायरनमेंट साफ़ रखें। `python -m venv .venv && source .venv/bin/activate` चलाएँ और फिर इंस्टॉल करें, ताकि लाइब्रेरी सिस्टम पैकेजों से अलग रहे।

## Step 2: Create a New Document and a DocumentBuilder

अब हम वास्तव में **आयताकार आकार बनाते** हैं—लेकिन पहले हमें एक खाली कैनवास चाहिए।

```python
import aspose.words as aw

# Initialize a new, empty Word document
doc = aw.Document()
# DocumentBuilder lets us add content programmatically
builder = aw.DocumentBuilder(doc)
```

`Document` ऑब्जेक्ट पूरी फ़ाइल का प्रतिनिधित्व करता है, जबकि `DocumentBuilder` एक सहायक टूल है जो कर्सर की स्थिति जानता है और उस बिंदु पर एलिमेंट इन्सर्ट कर सकता है। बिल्डर को एक पेन समझें जो पेज पर लिखता है।

## Step 3: Insert the Rectangle Shape

यहीं पर मुख्य कार्रवाई होती है। हम **आयताकार आकार** को निश्चित चौड़ाई और ऊँचाई के साथ बनाएँगे, फिर उसे पेज पर स्थित करेंगे।

```python
# Insert a rectangle 200 points wide and 100 points tall
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

आयत क्यों? यह सबसे सरल आकार है जो अभी भी फ़िल रंग और छाया दिखा सकता है। अगर बाद में आपको सर्कल या स्टार चाहिए, तो बस `ShapeType.RECTANGLE` को किसी अन्य enum वैल्यू से बदल दें।

## Step 4: Set Shape Fill Color

सादा सफ़ेद बॉक्स बहुत आकर्षक नहीं होता, इसलिए चलिए **आकार का फ़िल रंग** कुछ नरम—जैसे हल्का नीला—से सेट करते हैं।

```python
# Apply a light‑blue background to the rectangle
rectangle.fill_color = aw.Color.light_blue
```

आप किसी भी प्री‑डिफाइंड `aw.Color` मेंबर (`red`, `green`, `dark_gray` आदि) का उपयोग कर सकते हैं या एक RGB ट्यूपल पास कर सकते हैं (`aw.Color.from_argb(255, 30, 144, 255)`)। फ़िल रंग वह है जो उपयोगकर्ता को छाया या बॉर्डर लागू होने से पहले दिखता है।

## Step 5: Add Shadow to Shape

अब विज़ुअल पॉलिश का समय: **आकार में छाया जोड़ें**। छाया गहराई देती है और आयत को पेज पर उभरा बनाती है।

```python
# Grab the shadow format object
shadow = rectangle.shadow_format

# Turn the shadow on
shadow.visible = True
# Choose a dark gray tone for realism
shadow.color = aw.Color.dark_gray
# Blur radius controls softness (5 points is a nice middle ground)
shadow.blur = 5
# Horizontal and vertical offsets shift the shadow relative to the shape
shadow.offset_x = 3
shadow.offset_y = 3
# Slight transparency makes the shadow feel natural
shadow.transparency = 0.2
# Use an outer shadow – you could also try INSET for a different effect
shadow.type = aw.drawing.ShadowType.OUTER
```

**छाया कैसे जोड़ें**? ऊपर दिया गया कोड ठीक वही करता है, लेकिन चलिए समझते हैं कि प्रत्येक प्रॉपर्टी क्यों महत्वपूर्ण है:

- `visible` – प्रभाव को ऑन/ऑफ़ करता है।
- `color` – रंग निर्धारित करता है; डार्क ग्रे प्राकृतिक प्रकाश की नकल करता है।
- `blur` – बड़े मान से किनारा नरम हो जाता है।
- `offset_x` / `offset_y` – छाया को आकार से दूर ले जाता है; विभिन्न प्रकाश कोणों को सिमुलेट करने के लिए इन्हें समायोजित करें।
- `transparency` – 0 पूरी तरह ठोस, 1 पूरी तरह अदृश्य; 0.2 एक सूक्ष्म प्रभाव देता है।
- `type` – `OUTER` छाया को आकार के बाहर डालता है, जबकि `INNER` उसे अंदर की ओर बनाता है।

अगर आपको ड्रामैटिक ड्रॉप शैडो चाहिए, तो `blur` को 10‑15 तक बढ़ाएँ और `offset_x`/`offset_y` को 6‑8 तक बढ़ाएँ।

## Step 6: Save the Document as PDF

सारा काम बेकार है जब तक हम **दस्तावेज़ को PDF के रूप में सेव** नहीं कर पाते और शेयर नहीं कर पाते। Aspose.Words इसे एक लाइन में कर देता है:

```python
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

PDF क्यों? PDFs लेआउट को सभी प्लेटफ़ॉर्म पर बरकरार रखते हैं, जिससे वे रिपोर्ट, इनवॉइस या किसी भी प्रिंटेबल सामग्री के लिए आदर्श होते हैं। `save` मेथड फ़ाइल एक्सटेंशन को स्वचालित रूप से पहचान लेता है और सही फ़ॉर्मेट चुन लेता है—सिर्फ यह सुनिश्चित करें कि पाथ `.pdf` पर समाप्त हो।

### Expected Result

जनरेटेड `ShapeWithShadow.pdf` खोलें और आपको पहले पेज के शीर्ष के पास केंद्रित एक हल्का‑नीला आयत दिखेगा, जिसके दाएँ और नीचे की ओर हल्की डार्क ग्रे छाया होगी। आकार की किनारे स्पष्ट हैं, छाया सूक्ष्म है, और फ़ाइल साइज आमतौर पर 100 KB से कम रहता है।

## Bonus: Tweaking Shadows – Answers to “how to add shadow”

आप सोच रहे होंगे, *“क्या मैं आकार को मूव किए बिना छाया की दिशा बदल सकता हूँ?”* बिल्कुल। छाया की पोज़िशन आकार के कोऑर्डिनेट्स से स्वतंत्र है; बस `offset_x` और `offset_y` को समायोजित करें। पॉज़िटिव वैल्यू छाया को दाएँ/नीचे ले जाती है, नेगेटिव वैल्यू बाएँ/ऊपर।

एक और आम सवाल: *“अगर मुझे एक ही आकार पर कई छायाएँ चाहिए तो?”* Aspose.Words एक आकार पर केवल एक ही छाया सपोर्ट करता है। यदि आपको लेयरड इफ़ेक्ट चाहिए, तो एक डुप्लिकेट आकार बनाएं, उसे थोड़ा ऑफ़सेट करें, और प्रत्येक पर अलग छाया लगाएँ। यह थोड़ा हैक है, लेकिन काम करता है।

## Full Script – Ready to Run

नीचे पूरा, स्वतंत्र स्क्रिप्ट दिया गया है। इसे `create_rectangle_with_shadow.py` नाम की फ़ाइल में कॉपी करें और `python create_rectangle_with_shadow.py` से चलाएँ।

```python
import aspose.words as aw

# ---------- Initialize document ----------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ---------- Insert rectangle ----------
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# ---------- Set fill color ----------
rectangle.fill_color = aw.Color.light_blue

# ---------- Configure shadow ----------
shadow = rectangle.shadow_format
shadow.visible = True
shadow.color = aw.Color.dark_gray
shadow.blur = 5
shadow.offset_x = 3
shadow.offset_y = 3
shadow.transparency = 0.2
shadow.type = aw.drawing.ShadowType.OUTER

# ---------- Save as PDF ----------
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

> **Note:** `YOUR_DIRECTORY` को अपने मशीन पर मौजूद किसी भी एब्सोल्यूट या रिलेटिव पाथ से बदलें। अगर फ़ोल्डर मौजूद नहीं है, तो Python `FileNotFoundError` उठाएगा।

## Common Pitfalls & How to Avoid Them

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| Shadow not appearing | `shadow.visible` डिफ़ॉल्ट `False` पर रहता है | `shadow.visible = True` सुनिश्चित करें |
| Shape is invisible | फ़िल रंग `aw.Color.transparent` या `None` पर सेट है | `aw.Color.light_blue` जैसे सॉलिड रंग का उपयोग करें |
| PDF is empty | `doc.save` कॉल करना भूल गए या गलत एक्सटेंशन के साथ सेव किया | `doc.save("output.pdf")` कॉल करें और पाथ जांचें |
| Runtime error `ImportError` | Aspose.Words इंस्टॉल नहीं है या गलत Python env इस्तेमाल हुआ | सक्रिय venv में `pip install aspose-words` चलाएँ |

## Next Steps – Explore More Shapes and Formatting

अब जब आप **आयताकार आकार बनाना** में निपुण हो गए हैं, तो आप:

- `ShapeType.RECTANGLE` को `ShapeType.ELLIPSE` या `ShapeType.PENTAGON` से बदलकर अन्य ज्योमेट्री आज़मा सकते हैं।
- `builder.move_to(rectangle.absolute_position)` के बाद `builder.writeln("Hello World")` से आकार के अंदर टेक्स्ट जोड़ सकते हैं।
- `group = aw.drawing.GroupShape(doc)` का उपयोग करके कई आकारों को एक समूह में जोड़ सकते हैं, जिससे जटिल डायग्राम बनेंगे।
- DOCX (`doc.save("output.docx")`) या HTML (`doc.save("output.html")`) जैसे अन्य फ़ॉर्मेट में एक्सपोर्ट करके देख सकते हैं कि छाया कैसे ट्रांसलेट होती है।

इन सभी एक्सटेंशन का आधार वही कोर कॉन्सेप्ट है: **आकार में छाया जोड़ें**, **आकार का फ़िल रंग सेट करें**, और **दस्तावेज़ को PDF (या अन्य फ़ॉर्मेट) में सेव करें**।

---

### Image Preview *(optional)*

![Create rectangle shape with shadow in Python](https://example.com/rectangle-shadow.png "Create rectangle shape with shadow in Python")

*स्क्रीनशॉट में अंतिम PDF आउटपुट दिखाया गया है जिसमें हल्का‑नीला आयत और सूक्ष्म बाहरी छाया है।*

---

## Conclusion

हमने हर वह कदम समझाया जो **Python में आयताकार आकार बनाना**, कस्टम फ़िल लागू करना, **आकार में छाया जोड़ना**, और अंत में **दस्तावेज़ को PDF के रूप में सेव करना** के लिए आवश्यक है। कोड पूरी तरह चलाने योग्य है, व्याख्याएँ प्रत्येक प्रॉपर्टी के पीछे का *क्यों* बताती हैं, और हमने सामान्य एज़ केस और अगले कदमों को भी कवर किया है।

## What Should You Learn Next?

नीचे दिए गए ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक रिसोर्स में पूर्ण कार्यशील कोड उदाहरण और स्टेप‑बाय‑स्टेप व्याख्याएँ हैं, जिससे आप अतिरिक्त API फीचर सीख सकते हैं और अपने प्रोजेक्ट में वैकल्पिक इम्प्लीमेंटेशन अप्रोचेज़ को एक्सप्लोर कर सकते हैं।

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}