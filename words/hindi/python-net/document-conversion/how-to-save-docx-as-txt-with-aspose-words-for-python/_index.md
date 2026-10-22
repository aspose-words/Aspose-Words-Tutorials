---
category: general
date: 2026-09-21
description: Aspose.Words for Python का उपयोग करके docx को txt में सहेजें। Word को
  साधारण टेक्स्ट में बदलें और समीकरणों को LaTeX में निर्यात करें, केवल तीन सरल चरणों
  में।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx as txt
- convert word to plain text
- how to convert docx to txt
- save document as plain text
- export equations to latex
language: hi
lastmod: 2026-09-21
og_description: Aspose.Words for Python के साथ docx को txt में सहेजें। केवल कुछ कोड
  लाइनों में Word को साधारण टेक्स्ट में बदलना और समीकरणों को LaTeX में निर्यात करना
  सीखें।
og_image_alt: Screenshot showing save docx as txt code snippet in Python
og_title: Aspose.Words for Python के साथ docx को txt में सहेजें – त्वरित मार्गदर्शिका
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Save docx as txt using Aspose.Words for Python. Convert Word to plain
    text and export equations to LaTeX in three simple steps.
  headline: How to save docx as txt with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- document conversion
- plain text
- LaTeX
title: Aspose.Words for Python के साथ docx को txt में कैसे सहेजें
url: /hi/python/document-conversion/how-to-save-docx-as-txt-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Python के साथ docx को txt के रूप में कैसे सहेजें

यदि आपको **docx को txt के रूप में सहेजना** है, तो यह गाइड आपको Aspose.Words for Python के साथ यह करने का तरीका दिखाता है। Word को साधारण टेक्स्ट में बदलते समय समीकरणों को संरक्षित रखना सरल है, बस इन चरणों का पालन करें।

आप सीखेंगे कि **word को plain text में कैसे बदलें**, Office Math ऑब्जेक्ट्स के लिए एक्सपोर्ट मोड कैसे कॉन्फ़िगर करें, और यह सत्यापित करें कि परिणामी फ़ाइल में समीकरणों के लिए LaTeX मार्कअप मौजूद है। यह ट्यूटोरियल मानता है कि आपके पास बुनियादी Python ज्ञान है और Python का हालिया संस्करण (3.8+) स्थापित है।

## Aspose.Words for Python स्थापित करें

कोई भी कोड लिखने से पहले, PyPI से Aspose.Words पैकेज इंस्टॉल करें।

```bash
pip install aspose-words
```

यह लाइब्रेरी `aw` नेमस्पेस प्रदान करती है, जिसका उपयोग इस ट्यूटोरियल में लगातार किया जाएगा। इंस्टॉलेशन एक बार का कदम है; यह पैकेज सभी बाद के रूपांतरणों के लिए काम करता है।

## स्रोत दस्तावेज़ तैयार करें

DOCX फ़ाइल को किसी ज्ञात डायरेक्टरी में रखें जिसे आप बदलना चाहते हैं। एक पूर्ण पाथ (absolute path) उपयोग करने से स्क्रिप्ट के अलग कार्यशील डायरेक्टरी से चलने पर भ्रम नहीं होता।

```python
import aspose.words as aw
import os

# Define input and output paths
input_path = os.path.abspath("YOUR_DIRECTORY/input.docx")
output_path = os.path.abspath("YOUR_DIRECTORY/output.txt")
```

`aw.Document` क्लास DOCX फ़ाइल को पढ़ती है और एक इन‑मे्मोरी प्रतिनिधित्व बनाती है जिसे आप संशोधित या अन्य फ़ॉर्मेट में सहेज सकते हैं।

## TXT सहेजने के विकल्प कॉन्फ़िगर करें

**docx को txt के रूप में सहेजने** के लिए, आपको एक `TxtSaveOptions` ऑब्जेक्ट बनाना होगा। यह ऑब्जेक्ट आपको Office Math ऑब्जेक्ट्स के रेंडरिंग को नियंत्रित करने की सुविधा देता है।

```python
# Step 1: Load the source document
doc = aw.Document(input_path)

# Step 2: Create TXT save options and specify how Office Math objects should be exported
txt_opts = aw.saving.TxtSaveOptions()
txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
```

`office_math_export_mode` को `LATEX` पर सेट करने से सभी समीकरण LaTeX कोड के रूप में लिखे जाते हैं, साधारण Unicode प्रतीकों की बजाय। यह **export equations to latex** आवश्यकता को पूरा करता है।

## दस्तावेज़ को साधारण टेक्स्ट के रूप में सहेजें

अब आप कॉन्फ़िगर किए गए विकल्पों के साथ दस्तावेज़ को साधारण‑टेक्स्ट फ़ाइल में लिख सकते हैं।

```python
# Step 3: Save the document as a plain‑text file using the configured options
doc.save(output_path, txt_opts)
print(f"Document saved as plain text at: {output_path}")
```

`doc.save` कॉल एक ही लाइन में रूपांतरण करता है, जिससे **save document as plain text** लक्ष्य पूरा होता है।

## आउटपुट सत्यापित करें

जनरेट की गई `output.txt` फ़ाइल को किसी भी टेक्स्ट एडिटर में खोलें। आपको सामान्य पैराग्राफ़ के बाद प्रत्येक समीकरण के लिए LaTeX अंश दिखने चाहिए, उदाहरण के तौर पर:

```
This is a sample paragraph.

\[
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
\]

Another paragraph without equations.
```

यदि फ़ाइल में LaTeX मार्कअप मौजूद है, तो **export equations to latex** चरण सही ढंग से काम किया है।

## किनारे के मामलों और व्यावहारिक टिप्स

* **Missing fonts** – Aspose.Words अनुपलब्ध फ़ॉन्ट्स को डिफ़ॉल्ट फ़ॉन्ट से बदल देता है। साधारण‑टेक्स्ट आउटपुट पर इसका असर नहीं पड़ता, लेकिन रेंडर किए गए समीकरणों की दृश्य सटीकता बदल सकती है। सुनिश्चित करें कि स्रोत दस्तावेज़ मानक फ़ॉन्ट्स का उपयोग करता है या संभव हो तो उन्हें एम्बेड करें।
* **Large documents** – 100 MB से बड़ी फ़ाइलों के लिए `aw.loading.LoadOptions` का उपयोग करके इनपुट को स्ट्रीम करने पर विचार करें, जिससे मेमोरी खपत घटेगी।
* **Non‑ASCII characters** – `TxtSaveOptions` क्लास डिफ़ॉल्ट रूप से UTF‑8 एन्कोडिंग उपयोग करती है, जो Unicode अक्षरों को संरक्षित रखती है। यदि आपको अलग एन्कोडिंग चाहिए, तो `txt_opts.encoding = aw.saving.Encoding.ASCII` सेट करें (अधिकांश भाषाओं के लिए अनुशंसित नहीं)।
* **Path handling** – हमेशा `os.path.abspath` या `pathlib.Path` का उपयोग करें ताकि रिलेटिव‑पाथ की आश्चर्यजनक स्थितियों से बचा जा सके, विशेषकर जब स्क्रिप्ट शेड्यूल्ड टास्क के रूप में चलती हो।

## तेज़ कॉपी‑एंड‑पेस्ट के लिए पूर्ण स्क्रिप्ट

नीचे वह संपूर्ण, चलाने योग्य उदाहरण है जिसमें सभी चरण सम्मिलित हैं।

```python
import aspose.words as aw
import os

def save_docx_as_txt(input_docx: str, output_txt: str) -> None:
    """
    Converts a DOCX file to plain text and exports any Office Math objects as LaTeX.
    """
    # Load the source document
    doc = aw.Document(input_docx)

    # Configure TXT save options
    txt_opts = aw.saving.TxtSaveOptions()
    txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX

    # Save as plain‑text file
    doc.save(output_txt, txt_opts)

if __name__ == "__main__":
    # Adjust these paths for your environment
    input_path = os.path.abspath("YOUR_DIRECTORY/input.docx")
    output_path = os.path.abspath("YOUR_DIRECTORY/output.txt")

    # Ensure the output directory exists
    os.makedirs(os.path.dirname(output_path), exist_ok=True)

    save_docx_as_txt(input_path, output_path)
    print(f"Document saved as plain text at: {output_path}")
```

इस स्क्रिप्ट को चलाने से एक `.txt` फ़ाइल बनती है जिसमें मूल दस्तावेज़ का टेक्स्ट और किसी भी समीकरण का LaTeX प्रतिनिधित्व शामिल होता है, जिससे **how to convert docx to txt** लक्ष्य प्राप्त होता है।

![Screenshot of save docx as txt code snippet in Python](placeholder-image.png){: .img-fluid alt="Python में docx को txt के रूप में सहेजने वाले कोड स्निपेट का स्क्रीनशॉट"}

## निष्कर्ष

अब आप जानते हैं कि Aspose.Words for Python का उपयोग करके **docx को txt के रूप में कैसे सहेजें**, **word को plain text में कैसे बदलें**, और आवश्यकता पड़ने पर **equations को latex में कैसे निर्यात करें**। पूर्ण उदाहरण दिखाता है कि Word दस्तावेज़ों को साधारण‑टेक्स्ट फ़ाइलों में बदलते समय गणितीय सामग्री को कैसे संरक्षित रखें।

अगला कदम, HTML या PDF जैसे अन्य एक्सपोर्ट फ़ॉर्मेट को सहेजने के विकल्प क्लास को बदलकर आज़माएँ। आप साधारण‑टेक्स्ट आउटपुट के लिए कस्टम डिलिमिटर भी प्रयोग कर सकते हैं या इस रूपांतरण को बड़े दस्तावेज़‑प्रोसेसिंग पाइपलाइन में एकीकृत कर सकते हैं।

हैप्पी कोडिंग!

## अगला आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जिससे आप अतिरिक्त API सुविधाओं में महारत हासिल कर सकें और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण कर सकें।

- [Aspose.Words – Save docx as txt और Export Word Equations as LaTeX – पूर्ण गाइड](/words/english/net/basic-conversions/save-docx-as-txt-complete-guide-to-export-word-equations-as/)
- [Save docx as txt – Export Equations to LaTeX with Aspose.Words](/words/english/net/programming-with-officemath/save-docx-as-txt-export-equations-to-latex-with-aspose-words/)
- [Convert docx to txt – Export Word Equations as LaTeX](/words/english/java/document-conversion-and-export/convert-docx-to-txt-export-word-equations-as-latex/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}