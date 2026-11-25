---
category: general
date: 2026-11-25
description: Python के साथ Word दस्तावेज़ में आकृति पर छाया जोड़ें। Word में आयताकार
  आकृति डालना और Aspose.Words का उपयोग करके पारदर्शी छाया लागू करना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- insert rectangle shape word
- how to create word document python
- Aspose.Words Python
- shape formatting Python
language: hi
lastmod: 2026-11-25
og_description: Python का उपयोग करके Word दस्तावेज़ में आकृति पर छाया जोड़ें। यह ट्यूटोरियल
  दिखाता है कि Word में एक आयताकार आकृति कैसे डालें और Aspose.Words के साथ 30 % पारदर्शी
  छाया कैसे सेट करें।
og_image_alt: Add shadow to shape example in a Word document created by Python
og_title: Python के साथ Word दस्तावेज़ में आकार पर छाया जोड़ें – चरण‑दर‑चरण गाइड
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Add shadow to shape in a Word document with Python. Learn how to insert
    rectangle shape in Word and apply a transparent shadow using Aspose.Words.
  headline: How to add shadow to shape in a Word document using Python
  type: TechArticle
tags:
- Python
- Aspose.Words
- Word automation
title: Python का उपयोग करके Word दस्तावेज़ में आकृति पर छाया कैसे जोड़ें
url: /hi/python/images-shapes/how-to-add-shadow-to-shape-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python का उपयोग करके Word दस्तावेज़ में shape पर shadow कैसे जोड़ें

यदि आपको Word दस्तावेज़ में **add shadow to shape** की आवश्यकता है, यह गाइड आपको एक पूर्ण, runnable समाधान दिखाता है। आप देखेंगे कि कैसे एक Word फ़ाइल बनाएं, एक rectangle shape डालें, और 30 % transparent shadow लागू करें—सभी Aspose.Words for Python लाइब्रेरी के साथ।

Word दस्तावेज़ों को प्रोग्रामेटिकली संभालने से आप मैन्युअल फॉर्मेटिंग से बचते हैं और बड़े पैमाने पर रिपोर्ट, अनुबंध, या मार्केटिंग फ़्लायर बना सकते हैं। इस ट्यूटोरियल के अंत तक आप “**how to create Word document python**” का उत्तर एक तैयार‑to‑run कोड नमूने के साथ दे पाएँगे।

## आवश्यकताएँ

* Python 3.8 या नया स्थापित हो।
* एक सक्रिय Aspose.Words for Python लाइसेंस (फ्री ट्रायल मूल्यांकन के लिए काम करता है)।
* `aspose-words` पैकेज `pip install aspose-words` के माध्यम से स्थापित हो।
* एक फ़ोल्डर जहाँ आउटपुट फ़ाइल लिखी जा सके (कोड में `YOUR_DIRECTORY` को बदलें)।

कोई अतिरिक्त निर्भरताएँ आवश्यक नहीं हैं।

## चरण 1: नया Word दस्तावेज़ बनाएं

पहला चरण `Document` ऑब्जेक्ट को इंस्टैंशिएट करना है। यह ऑब्जेक्ट संपूर्ण .docx फ़ाइल को मेमोरी में दर्शाता है।

```python
import aspose.words as aw

# Create an empty Word document
doc = aw.Document()
# DocumentBuilder provides a convenient API for adding content
builder = aw.DocumentBuilder(doc)
```

`DocumentBuilder` एक वर्चुअल कर्सर की तरह काम करता है। जब आप इसके मेथड्स को कॉल करते हैं, लाइब्रेरी वर्तमान कर्सर स्थान पर संबंधित तत्व सम्मिलित करती है।

## चरण 2: rectangle shape word डालें

अब आप बिल्डर के `insert_shape` मेथड का उपयोग करके **insert rectangle shape word** करेंगे। इस मेथड को shape प्रकार और उसके आकार को पॉइंट्स में चाहिए (1 पॉइंट = 1/72 इंच)।

```python
# Insert a rectangle shape that is 100 points wide and 50 points tall
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)
```

आप अपने डिज़ाइन के अनुसार आयाम बदल सकते हैं। rectangle दस्तावेज़ की ड्राइंग लेयर का हिस्सा बन जाता है, जिसका अर्थ है कि आप बाद में इसका fill, outline, या shadow संशोधित कर सकते हैं।

## चरण 3: shape की shadow format तक पहुँचें

हर ड्राइंग ऑब्जेक्ट एक `shadow_format` प्रॉपर्टी प्रदान करता है जो shadow की उपस्थिति को नियंत्रित करती है। इसे प्राप्त करें ताकि आप transparency, offset, blur, और color को समायोजित कर सकें।

```python
# Get the ShadowFormat object for the rectangle
shadow = shape.shadow_format
```

इस चरण पर shape के पास डिफ़ॉल्ट shadow है (कोई shadow नहीं)। `ShadowFormat` ऑब्जेक्ट सभी पैरामीटर रखता है जो आपको यथार्थवादी प्रभाव बनाने के लिए चाहिए।

## चरण 4: shadow को 30 % पारदर्शी बनाएं

Transparency को `0` (पूरी तरह अपारदर्शी) और `1` (पूरी तरह पारदर्शी) के बीच मान के रूप में दर्शाया जाता है। इसे `0.3` सेट करने से 30 % पारदर्शी shadow मिलता है, जो अक्सर टेक्स्ट को अधिक बोझिल किए बिना गहराई जोड़ने के लिए पर्याप्त होता है।

```python
# Apply a 30 % transparent shadow
shadow.transparency = 0.3
# Optional: adjust other shadow properties for a nicer look
shadow.visible = True               # Ensure the shadow is turned on
shadow.distance = 4                 # Distance of the shadow from the shape (points)
shadow.blur = 4                     # Amount of blur applied to the shadow
shadow.color = aw.Color.black       # Shadow color
```

ये अतिरिक्त प्रॉपर्टीज़ आवश्यक नहीं हैं, लेकिन वे दिखाती हैं कि आप प्रभाव को कैसे फाइन‑ट्यून कर सकते हैं। `visible` फ़्लैग आवश्यक है; यदि आप इसे भूल जाते हैं, तो अन्य सेटिंग्स कॉन्फ़िगर होने के बावजूद shadow दिखाई नहीं देगा।

## चरण 5: परिणाम देखने के लिए दस्तावेज़ को सहेजें

अंत में, दस्तावेज़ को डिस्क पर लिखें। परिणामी `.docx` फ़ाइल को Microsoft Word या किसी भी संगत व्यूअर में खोलने पर rectangle पर लागू पारदर्शी shadow दिखेगा।

```python
# Save the document to the desired location
output_path = r"YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

जब आप `output.docx` खोलेंगे, तो आपको एक साधारण rectangle दिखेगा जिसके नीचे‑दाएँ ओर हल्का ग्रे shadow होगा। shadow की 30 % transparency आकार को पृष्ठ से उठे हुए जैसा दिखाती है।

![shape पर shadow जोड़ने का उदाहरण](placeholder-image.png){: .align-center alt="Python से निर्मित Word दस्तावेज़ में shape पर shadow जोड़ने का उदाहरण"}

## पूर्ण, runnable स्क्रिप्ट

सभी हिस्सों को एक साथ जोड़ने से आपको एक self‑contained स्क्रिप्ट मिलती है जिसे आप तुरंत कॉपी, पेस्ट और चलाकर उपयोग कर सकते हैं।

```python
import aspose.words as aw

def create_word_with_shadow(output_path: str):
    """
    Creates a Word document that contains a rectangle shape
    with a 30 % transparent shadow.
    """
    # Step 1: Initialize document and builder
    doc = aw.Document()
    builder = aw.DocumentBuilder(doc)

    # Step 2: Insert rectangle shape
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)

    # Step 3: Access shadow format
    shadow = shape.shadow_format

    # Step 4: Configure shadow properties
    shadow.visible = True
    shadow.transparency = 0.3
    shadow.distance = 4
    shadow.blur = 4
    shadow.color = aw.Color.black

    # Step 5: Save the document
    doc.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    # Replace with a valid folder on your machine
    create_word_with_shadow(r"YOUR_DIRECTORY/output.docx")
```

**अपेक्षित आउटपुट:** उत्पन्न `output.docx` खोलने पर एक पृष्ठ पर एक rectangle दिखेगा जो हल्की, अर्द्ध‑पारदर्शी shadow डालता है। कोई अतिरिक्त फॉर्मेटिंग आवश्यक नहीं है।

## सामान्य विविधताएँ और किनारे के मामले

| स्थिति | कोड को कैसे अनुकूलित करें |
|-----------|-----------------------|
| **विभिन्न shape प्रकार** (जैसे, ellipse) | `aw.drawing.ShapeType.RECTANGLE` को `aw.drawing.ShapeType.ELLIPSE` में बदलें। |
| **कस्टम shadow रंग** | एक लालिश shadow के लिए `shadow.color = aw.Color.from_argb(255, 128, 0, 0)` सेट करें। |
| **एकाधिक shapes** | `builder.insert_shape` को बार‑बार कॉल करें; प्रत्येक कॉल एक अलग `Shape` ऑब्जेक्ट लौटाता है जिसे आप स्वतंत्र रूप से स्टाइल कर सकते हैं। |
| **PDF के रूप में सहेजना** | `doc.save(output_path)` को `doc.save(output_path.replace('.docx', '.pdf'))` से बदलें और `.pdf` एक्सटेंशन का उपयोग करें। |
| **लाइसेंस के बिना चलाना** | फ्री ट्रायल पहली पृष्ठ पर एक वॉटरमार्क जोड़ता है। प्रोडक्शन उपयोग के लिए इसे हटाने हेतु लाइसेंस प्राप्त करें। |

## टिप्स और सर्वोत्तम प्रथाएँ

* **Reuse the builder**: पूरे दस्तावेज़ के लिए एक ही `DocumentBuilder` इंस्टेंस रखें ताकि अनावश्यक ऑब्जेक्ट निर्माण से बचा जा सके।
* **Dispose resources**: लंबे‑समय चलने वाली सेवाओं में, सहेजने के बाद `doc.dispose()` कॉल करके नेटिव मेमोरी मुक्त करें।
* **Validate output**: यदि आपको Open XML मानक के अनुपालन को सुनिश्चित करना है तो सहेजने से पहले `doc.validate(aw.ValidationType.FULL_VALIDATION)` का उपयोग करें।
* **Version compatibility**: यह कोड Aspose.Words for Python ≥ 22.9 के साथ काम करता है। सुनिश्चित करें कि आपका पैकेज `pip install --upgrade aspose-words` से अद्यतित है।

## निष्कर्ष

अब आप जानते हैं कि Python का उपयोग करके Word दस्तावेज़ में **add shadow to shape** कैसे करें। पाँच चरणों—दस्तावेज़ बनाना, **insert rectangle shape word**, shadow को कॉन्फ़िगर करना, और सहेजना—का पालन करके आप रिपोर्ट, इनवॉइस, या मार्केटिंग सामग्री के लिए परिष्कृत दस्तावेज़ निर्माण को स्वचालित कर सकते हैं।  

अब आप ग्रेडिएंट फ़िल्स, टेक्स्ट रैपिंग, या दस्तावेज़ को PDF में बदलने जैसे अन्य फॉर्मेटिंग विकल्पों का अन्वेषण कर सकते हैं। इन सभी विषयों का आधार वही `DocumentBuilder` और shape‑formatting अवधारणाएँ हैं जो इस ट्यूटोरियल में प्रस्तुत की गई हैं।

कोडिंग का आनंद लें, और एक साधारण shadow द्वारा आपके स्वचालित Word दस्तावेज़ों में लाई गई दृश्य गहराई का आनंद उठाएँ!

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन निकट-संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में निपुण बनने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Python का उपयोग करके Word दस्तावेज़ में rectangle shape कैसे बनाएं](/words/english/python-net/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/)
- [Python में Shape पर Shadow जोड़ें – पूर्ण Aspose.Words ट्यूटोरियल](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [खाली Word दस्तावेज़ बनाएं और Shape पर Shadow जोड़ें – पूर्ण Python गाइड](/words/english/python-net/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}