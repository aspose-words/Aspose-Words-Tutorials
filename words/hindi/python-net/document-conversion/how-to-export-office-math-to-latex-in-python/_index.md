---
category: general
date: 2026-10-07
description: Aspose.Words के साथ Python में ऑफिस गणित को LaTeX में निर्यात करना सीखें।
  यह चरण‑दर‑चरण मार्गदर्शिका आपको दिखाती है कि Word से समीकरणों को LaTeX प्रारूप में
  कैसे निर्यात किया जाए।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to export office math to latex
- how to export equations from word
- Aspose.Words Python
- LaTeX conversion
- Office Math extraction
language: hi
lastmod: 2026-10-07
og_description: Aspose.Words का उपयोग करके Python में ऑफिस मैथ को LaTeX में कैसे निर्यात
  करें। वर्ड से समीकरणों को तेज़ और विश्वसनीय तरीके से निर्यात करने के लिए इस गाइड
  का पालन करें।
og_image_alt: Screenshot of LaTeX equation output generated from a Word document
og_title: Python में Office Math को LaTeX में निर्यात करें – पूर्ण गाइड
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to export office math to LaTeX in Python with Aspose.Words.
    This step‑by‑step guide shows you how to export equations from Word to LaTeX format.
  headline: How to export office math to LaTeX in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- LaTeX
- Office Math
title: Python में Office Math को LaTeX में कैसे निर्यात करें
url: /hi/python/document-conversion/how-to-export-office-math-to-latex-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Python में Office Math को LaTeX में निर्यात कैसे करें

यदि आपको Office Math को LaTeX में निर्यात करने की आवश्यकता है, तो यह गाइड आपको Aspose.Words for Python का उपयोग करके Word से समीकरण निर्यात करने का तरीका दिखाता है। आप एक पूर्ण, चलाने योग्य उदाहरण देखेंगे जो Office Math ऑब्जेक्ट्स वाले `.docx` फ़ाइल को साधारण‑पाठ LaTeX कोड में परिवर्तित करता है।

समीकरणों का निर्यात एक सामान्य आवश्यकता है जब आप Word सामग्री को वैज्ञानिक लेखों, स्थैतिक‑साइट जेनरेटरों, या किसी भी कार्यप्रवाह में पुनः उपयोग करना चाहते हैं जो LaTeX पर निर्भर करता है। नीचे दिए गए चरण SDK की स्थापना से लेकर उत्पन्न आउटपुट की जाँच तक सब कुछ कवर करते हैं।

## आवश्यकताएँ

शुरू करने से पहले सुनिश्चित करें कि आपके पास है:

* आपके मशीन पर Python 3.8 या उससे नया स्थापित हो।
* **Aspose.Words for Python via .NET** के लिए वैध लाइसेंस (नि:शुल्क मूल्यांकन परीक्षण के लिए काम करता है)।
* `pip` के माध्यम से `aspose-words` पैकेज स्थापित करने की पहुँच।
* एक Word दस्तावेज़ (`.docx`) जिसमें कम से कम एक Office Math ऑब्जेक्ट (समीकरण) हो। इस ट्यूटोरियल के लिए हम मानते हैं कि फ़ाइल का नाम `math.docx` है और यह `YOUR_DIRECTORY` में स्थित है।

> **Pro tip:** यदि आपके पास लाइसेंस फ़ाइल नहीं है, तो ट्रायल लाइसेंस (`Aspose.Words.lic`) को अपनी स्क्रिप्ट के समान डायरेक्टरी में रखें; SDK इसे स्वचालित रूप से पहचान लेगा।

## Aspose.Words for Python स्थापित करें

पहला कदम है Aspose.Words लाइब्रेरी को अपने Python वातावरण में जोड़ना।

```bash
pip install aspose-words
```

कमांड चलाने से `aspose.words` पैकेज और सभी आवश्यक .NET रनटाइम घटक स्थापित हो जाते हैं। स्थापना के बाद आप लाइब्रेरी को `import aspose.words as aw` के साथ इम्पोर्ट कर सकते हैं।

## चरण 1: समीकरणों वाले Word दस्तावेज़ को लोड करें

आपको अपनी सामग्री को संशोधित करने से पहले स्रोत `.docx` फ़ाइल को लोड करना होगा। `Document` क्लास फ़ाइल को मेमोरी में पढ़ती है और आपको प्रत्येक तत्व तक पहुँच देती है, जिसमें Office Math ऑब्जेक्ट्स भी शामिल हैं।

```python
import aspose.words as aw

# Replace YOUR_DIRECTORY with the actual path to your files
doc_path = "YOUR_DIRECTORY/math.docx"

# Load the Word document that holds the equations
document = aw.Document(doc_path)
```

दस्तावेज़ को लोड करना आवश्यक है क्योंकि निर्यात प्रक्रिया फ़ाइल सिस्टम पर सीधे नहीं, बल्कि इन‑मेमोरी प्रतिनिधित्व पर काम करती है।

## चरण 2: TXT सहेजने के विकल्प बनाएं और निर्यात मोड सेट करें

Aspose.Words `TxtSaveOptions` का उपयोग करके दस्तावेज़ को साधारण पाठ के रूप में सहेजता है। डिफ़ॉल्ट रूप से, Office Math ऑब्जेक्ट्स को Unicode अक्षरों के रूप में रेंडर किया जाता है, जिससे गणितीय संरचना खो जाती है। `office_math_export_mode` को `LATEX` पर सेट करने से SDK प्रत्येक समीकरण के लिए LaTeX कोड उत्पन्न करता है।

```python
# Create TXT save options to control the export behavior
txt_options = aw.saving.TxtSaveOptions()

# Export any Office Math (equations) in LaTeX format
txt_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
```

`OfficeMathExportMode.LATEX` कॉन्स्टेंट वह कुंजी है जो LaTeX रूपांतरण को सक्षम करती है। इसके बिना आउटपुट में समीकरणों के साधारण‑पाठ अनुमान ही रहेंगे।

## चरण 3: कॉन्फ़िगर किए गए विकल्पों का उपयोग करके दस्तावेज़ को साधारण‑पाठ फ़ाइल के रूप में सहेजें

अब दस्तावेज़ को एक `.txt` फ़ाइल में लिखें। SDK पिछले चरण में कॉन्फ़िगर किए गए विकल्पों को लागू करता है, जिससे प्रत्येक समीकरण LaTeX अंश के रूप में दिखाई देता है।

```python
# Destination path for the exported LaTeX text file
out_path = "YOUR_DIRECTORY/out.txt"

# Save the document using the TXT options that include LaTeX conversion
document.save(out_path, txt_options)

print(f"LaTeX export completed. File saved to: {out_path}")
```

जब स्क्रिप्ट समाप्त हो जाती है, `out.txt` में मूल Word पाठ के साथ प्रत्येक Office Math ऑब्जेक्ट की LaTeX प्रतिनिधित्व भी शामिल हो जाता है।

## LaTeX आउटपुट की जाँच करें

`out.txt` को किसी भी टेक्स्ट एडिटर में खोलें ताकि परिणाम देख सकें। एक सामान्य समीकरण जैसे *\(a^2 + b^2 = c^2\)* इस प्रकार दिखेगा:

```
\[
a^{2}+b^{2}=c^{2}
\]
```

यदि आप LaTeX को सीधे कंसोल में देखना पसंद करते हैं, तो फ़ाइल को फिर से पढ़कर उसकी सामग्री प्रिंट कर सकते हैं:

```python
with open(out_path, "r", encoding="utf-8") as f:
    latex_content = f.read()
    print("--- LaTeX content start ---")
    print(latex_content)
    print("--- LaTeX content end ---")
```

आउटपुट मूल Word दस्तावेज़ में मौजूद समीकरणों से मेल खाना चाहिए, जिसमें भिन्न, सुपरस्क्रिप्ट, सबस्क्रिप्ट और अन्य गणितीय प्रतीक संरक्षित हों।

## Word से समीकरण निर्यात करना – किनारे के मामलों को संभालना

बुनियादी प्रवाह अधिकांश दस्तावेज़ों के लिए काम करता है, लेकिन कुछ परिस्थितियों में अतिरिक्त ध्यान की आवश्यकता होती है:

| स्थिति | अनुशंसित उपाय |
|-----------|----------------------|
| **दस्तावेज़ में मिश्रित MathML और Office Math है** | MathML आउटपुट के लिए `OfficeMathExportMode.MATHML` का उपयोग करें, या MathML को मैन्युअल रूप से LaTeX में बदलने के बाद `LATEX` के साथ दूसरा पास चलाएँ। |
| **बड़े दस्तावेज़ मेमोरी दबाव उत्पन्न करते हैं** | दस्तावेज़ को सेक्शन में प्रोसेस करें: एक सेक्शन लोड करें, निर्यात करें, फिर अगले सेक्शन पर जाने से पहले उसे हटाएँ। |
| **समीकरण हेडर या फुटनोट में हैं** | निर्यात मोड उन्हें स्वचालित रूप से संभालता है, लेकिन यह सुनिश्चित करें कि कस्टम सहेजने विकल्पों द्वारा आसपास का पाठ हटाया न गया हो। |
| **लाइसेंस न होने पर मूल्यांकन वॉटरमार्क दिखता है** | किसी भी `Document` ऑपरेशन से पहले लाइसेंस फ़ाइल लोड करना सुनिश्चित करें: `aw.License().set_license("Aspose.Words.lic")`. |

इन किनारे के मामलों को संभालने से यह सुनिश्चित होता है कि **how to export office math to LaTeX** विभिन्न Word फ़ाइलों में विश्वसनीय रूप से काम करे।

## पूर्ण स्क्रिप्ट

नीचे पूर्ण, स्व-निहित Python स्क्रिप्ट दी गई है जिसे आप कॉपी, पेस्ट और चलाकर उपयोग कर सकते हैं। इसमें त्रुटि संभालना और स्पष्टता के लिए टिप्पणी शामिल हैं।

```python
import aspose.words as aw
import os
import sys

def export_office_math_to_latex(input_docx: str, output_txt: str) -> None:
    """
    Exports Office Math objects from a Word document to LaTeX format.
    Parameters
    ----------
    input_docx : str
        Path to the source .docx file containing equations.
    output_txt : str
        Path where the LaTeX‑enhanced plain‑text file will be saved.
    """
    if not os.path.isfile(input_docx):
        sys.exit(f"Error: Input file not found – {input_docx}")

    # Load the document
    document = aw.Document(input_docx)

    # Configure TXT save options for LaTeX conversion
    txt_options = aw.saving.TxtSaveOptions()
    txt_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX

    # Save the result
    document.save(output_txt, txt_options)
    print(f"LaTeX export completed. File saved to: {output_txt}")

if __name__ == "__main__":
    # Update these paths to match your environment
    INPUT_PATH = "YOUR_DIRECTORY/math.docx"
    OUTPUT_PATH = "

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API सुविधाओं में निपुण बनने और अपने प्रोजेक्ट में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [docx को markdown में बदलें – Aspose.Words के साथ Math Equations को LaTeX में निर्यात करें](/words/english/java/document-conversion-and-export/convert-docx-to-markdown-export-math-equations-to-latex-with/)
- [docx को txt के रूप में सहेजें – Aspose.Words के साथ समीकरणों को LaTeX में निर्यात करें](/words/english/net/programming-with-officemath/save-docx-as-txt-export-equations-to-latex-with-aspose-words/)
- [Word से LaTeX निर्यात कैसे करें – DOCX को Markdown में बदलें](/words/english/python-net/document-conversion/how-to-export-latex-from-word-convert-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}