---
category: general
date: 2026-09-27
description: Python में Aspose.Words का उपयोग करके docx को txt में बदलें। एक Word
  दस्तावेज़ को लोड करना, UTF‑8 एन्कोडिंग सेट करना, और कुछ लाइनों में Word दस्तावेज़
  को txt में निर्यात करना सीखें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- convert docx to txt
- convert word to plain text
- save word as plain text
- export word document txt
- load word document python
language: hi
lastmod: 2026-09-27
og_description: Aspose.Words के साथ Python में docx को txt में बदलें। यह ट्यूटोरियल
  दिखाता है कि कैसे एक Word दस्तावेज़ लोड करें, एन्कोडिंग कॉन्फ़िगर करें, और शब्द
  को साधारण टेक्स्ट के रूप में सहेजें।
og_image_alt: Screenshot of Python code that converts a DOCX file to a TXT file
og_title: Python में docx को txt में बदलें – चरण‑दर‑चरण मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Convert docx to txt in Python using Aspose.Words. Learn to load a Word
    document, set UTF‑8 encoding, and export Word document txt in a few lines.
  headline: How to convert docx to txt in Python with Aspose.Words
  type: TechArticle
tags:
- Python
- Aspose.Words
- Document conversion
title: Python में Aspose.Words का उपयोग करके docx को txt में कैसे परिवर्तित करें
url: /hi/python/document-conversion/how-to-convert-docx-to-txt-in-python-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python के साथ Aspose.Words का उपयोग करके docx को txt में कैसे बदलें

यदि आपको जल्दी से **convert docx to txt** करने की आवश्यकता है, तो यह गाइड आपको Python में एक पूर्ण समाधान दिखाता है। आप सीखेंगे कि **load word document python** कैसे किया जाता है, UTF‑8 एन्कोडिंग को कैसे कॉन्फ़िगर किया जाए, और केवल कुछ लाइनों के कोड से **export word document txt** कैसे किया जाए।

यह ट्यूटोरियल वह सब कुछ कवर करता है जो आपको Python 3 को सपोर्ट करने वाले किसी भी प्लेटफ़ॉर्म पर रूपांतरण चलाने के लिए चाहिए। लेख के अंत तक आप भरोसेमंद तरीके से **save word as plain text** कर सकेंगे, भले ही स्रोत दस्तावेज़ में विशेष अक्षर या गैर‑ASCII प्रतीक हों।

## आवश्यकताएँ

* Python 3.8 या नया स्थापित हो।
* Aspose.Words for Python का सक्रिय लाइसेंस (मुफ़्त ट्रायल मूल्यांकन के लिए काम करता है)।
* `aspose-words` पैकेज `pip install aspose-words` द्वारा स्थापित हो।
* एक DOCX फ़ाइल जिसे आप बदलना चाहते हैं (उदाहरण में `input.docx` उपयोग किया गया है)।

> **Pro tip:** अपना लाइसेंस फ़ाइल (`Aspose.Words.lic`) अपनी स्क्रिप्ट के समान फ़ोल्डर में रखें या `Aspose.Words.License` पाथ को स्पष्ट रूप से सेट करें ताकि मूल्यांकन‑मोड वॉटरमार्क से बचा जा सके।

## Aspose.Words स्थापित करें

अपने टर्मिनल या कमांड प्रॉम्प्ट में निम्न कमांड चलाएँ:

```bash
pip install aspose-words
```

यह पैकेज `aw` नेमस्पेस शामिल करता है जिसका उपयोग कोड उदाहरणों में लगातार किया जाता है।

## चरण 1 – Word दस्तावेज़ लोड करें (convert docx to txt)

पहला ऑपरेशन DOCX फ़ाइल को `aw.Document` ऑब्जेक्ट में पढ़ना है। यह चरण **load word document python** आवश्यकता के अनुरूप है।

```python
import aspose.words as aw

# Load the source DOCX file
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*Why this matters*: दस्तावेज़ को लोड करने से एक इन‑मेमोरी प्रतिनिधित्व बनता है जिसे Aspose.Words मूल फ़ाइल फ़ॉर्मेट की परवाह किए बिना हेर-फेर कर सकता है।

## चरण 2 – TXT सहेजने के विकल्प कॉन्फ़िगर करें (convert word to plain text)

Aspose.Words `TxtSaveOptions` प्रदान करता है जिससे आप नियंत्रित कर सकते हैं कि प्लेन‑टेक्स्ट आउटपुट कैसे उत्पन्न हो। `encoding` प्रॉपर्टी को `"utf-8"` सेट करने से सभी यूनिकोड अक्षर संरक्षित रहते हैं।

```python
# Create TXT save options and set UTF‑8 encoding
txt_options = aw.saving.TxtSaveOptions()
txt_options.encoding = "utf-8"
```

*Why this matters*: स्पष्ट एन्कोडिंग न होने पर, डिफ़ॉल्ट सिस्टम कोड पेज गैर‑ASCII अक्षरों को प्रश्नचिह्न से बदल सकता है। UTF‑8 बहुभाषी दस्तावेज़ों के लिए सबसे सुरक्षित विकल्प है।

## चरण 3 – दस्तावेज़ को प्लेन टेक्स्ट के रूप में सहेजें (save word as plain text)

अब ऊपर परिभाषित विकल्पों का उपयोग करके दस्तावेज़ को `.txt` फ़ाइल में लिखें।

```python
# Export the document to a plain‑text file
output_path = "YOUR_DIRECTORY/out.txt"
doc.save(output_path, txt_options)
print(f"Document exported successfully to {output_path}")
```

परिणामी `out.txt` फ़ाइल में केवल `input.docx` की टेक्स्ट सामग्री होती है, जिसमें लाइन ब्रेक मूल पैराग्राफ संरचना से मेल खाते हैं।

### अपेक्षित आउटपुट

यदि `input.docx` में वाक्य है:

> **“Hello, world! Привет мир!”**

तो उत्पन्न `out.txt` इस प्रकार दिखेगा:

```
Hello, world! Привет мир!
```

सभी अक्षर अपरिवर्तित रहते हैं क्योंकि UTF‑8 एन्कोडिंग लागू की गई थी।

## सामान्य किनारी मामलों का निपटारा

| Situation | Recommended approach |
|-----------|----------------------|
| **Document contains tables** | Aspose.Words टेबल कोशिकाओं को टैब द्वारा विभाजित प्लेन टेक्स्ट में फ़्लैटन करता है। यदि आपको कस्टम डिलिमिटर चाहिए, तो `txt_options.table_cell_separator` को उसी अनुसार सेट करें। |
| **Large files (≥ 100 MB)** | डॉक्यूमेंट को स्ट्रीम करें ताकि उच्च मेमोरी उपयोग से बचा जा सके: `doc.save(output_stream, txt_options)` का उपयोग करें जहाँ `output_stream` बाइनरी मोड में खोली गई फ़ाइल ऑब्जेक्ट है। |
| **Missing fonts** | होस्ट मशीन पर आवश्यक फ़ॉन्ट स्थापित करें या परिवर्तन से पहले उन्हें DOCX में एम्बेड करें। लापता फ़ॉन्ट केवल दृश्य रेंडरिंग को प्रभावित करते हैं, प्लेन‑टेक्स्ट एक्सट्रैक्शन को नहीं। |
| **Password‑protected DOCX** | लोड करते समय पासवर्ड प्रदान करें: `doc = aw.Document("secure.docx", aw.LoadOptions(password="MySecret"))`। |

## पूर्ण स्क्रिप्ट – चलाने के लिए तैयार

निम्न कोड को `convert_docx_to_txt.py` के रूप में सहेजें और `python convert_docx_to_txt.py` के साथ चलाएँ।

```python
import aspose.words as aw
import os

def convert_docx_to_txt(input_path: str, output_path: str, encoding: str = "utf-8") -> None:
    """
    Converts a DOCX file to a TXT file using Aspose.Words.

    Args:
        input_path: Path to the source .docx file.
        output_path: Desired path for the resulting .txt file.
        encoding: Text encoding for the output file (default UTF‑8).
    """
    if not os.path.isfile(input_path):
        raise FileNotFoundError(f"Input file not found: {input_path}")

    # Load the Word document (load word document python)
    document = aw.Document(input_path)

    # Configure TXT save options (convert word to plain text)
    txt_options = aw.saving.TxtSaveOptions()
    txt_options.encoding = encoding

    # Save as plain‑text (save word as plain text)
    document.save(output_path, txt_options)
    print(f"Conversion complete: {output_path}")

if __name__ == "__main__":
    INPUT_FILE = "YOUR_DIRECTORY/input.docx"
    OUTPUT_FILE = "YOUR_DIRECTORY/out.txt"
    convert_docx_to_txt(INPUT_FILE, OUTPUT_FILE)
```

स्क्रिप्ट चलाने पर एक पुष्टि पंक्ति प्रदर्शित होती है और निर्दिष्ट डायरेक्टरी में `out.txt` बनता है।

## परिणाम की पुष्टि करें

चलाने के बाद, किसी भी टेक्स्ट एडिटर (जैसे VS Code, Notepad++) में `out.txt` खोलें और पुष्टि करें कि सामग्री मूल DOCX टेक्स्ट से मेल खाती है। यदि आप गड़बड़ अक्षर देखते हैं, तो दोबारा जांचें कि `txt_options.encoding` `"utf-8"` पर सेट है।

## अगले कदम और संबंधित विषय

* **Convert docx to pdf** – उच्च‑गुणवत्ता PDF आउटपुट के लिए `aw.saving.PdfSaveOptions` का उपयोग करें।
* **Extract images from a Word document** – `aw.NodeType.SHAPE` और `Shape` क्लास को एक्सप्लोर करें।
* **Batch conversion** – DOCX फ़ाइलों के फ़ोल्डर पर इटरेट करें और प्रत्येक एंट्री के लिए `convert_docx_to_txt` को कॉल करें।
* **Advanced encoding** – दाएँ‑से‑बाएँ स्क्रिप्ट्स को संभालते समय `txt_options.add_bidi_marks` के साथ प्रयोग करें।

ऊपर बताए गए चरणों में महारत हासिल करके, आप किसी भी ऑटोमेशन पाइपलाइन में **export word document txt** कर सकते हैं, चाहे आप कमांड‑लाइन टूल बना रहे हों, वेब सर्विस के साथ इंटीग्रेट कर रहे हों, या क्लाउड में दस्तावेज़ प्रोसेस कर रहे हों।

---

## अब आपको क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [Convert docx to txt – Complete Guide to Saving Word as Plain Text](/words/english/net/programming-with-txtsaveoptions/convert-docx-to-txt-complete-guide-to-saving-word-as-plain-t/)
- [Aspose.Words – Save docx as txt and Export Word Equations as LaTeX – Complete Guide](/words/english/net/basic-conversions/save-docx-as-txt-complete-guide-to-export-word-equations-as/)
- [Word to PDF Tutorial: Convert DOCX to PDF with Aspose.Words](/words/english/net/basic-conversions/word-to-pdf-tutorial-convert-docx-to-pdf-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}