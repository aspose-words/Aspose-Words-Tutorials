---
category: general
date: 2026-06-24
description: DOCX से इमेज़ निर्यात करने के लिए कॉलबैक कैसे सेट करें जब मार्कडाउन के
  रूप में सहेजा जाए। इमेज़ निकालना, Word से SVG निकालना, और कस्टम हैंडलिंग के साथ
  DOCX को मार्कडाउन में सहेजना सीखें।
draft: false
keywords:
- how to set callback
- export images from docx
- how to extract images
- save docx as markdown
- extract svg from word
language: hi
og_description: DOCX को Markdown में बदलते समय छवियों को निर्यात करने के लिए कॉलबैक
  कैसे सेट करें। यह गाइड आपको प्रभावी ढंग से छवियों और SVGs को निकालने का तरीका दिखाता
  है।
og_title: DOCX से इमेज निर्यात करने के लिए कॉलबैक कैसे सेट करें
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  headline: How to Set Callback for Exporting Images from DOCX
  type: TechArticle
- description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  name: How to Set Callback for Exporting Images from DOCX
  steps:
  - name: '**Deterministic names** – useful for version control or CDN publishing.'
    text: '**Deterministic names** – useful for version control or CDN publishing.'
  - name: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
    text: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
  - name: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
    text: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Conversion
title: DOCX से इमेज निर्यात करने के लिए कॉलबैक कैसे सेट करें
url: /hi/python/content-extraction-and-manipulation/how-to-set-callback-for-exporting-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX से इमेज निर्यात करने के लिए कॉलबैक कैसे सेट करें

क्या आप कभी सोचते रहे हैं **how to set callback** ताकि आप **DOCX से इमेज निर्यात** कर सकें जबकि इसे Markdown में बदल रहे हों? आप अकेले नहीं हैं। कई डेवलपर्स को समस्या आती है जब डिफ़ॉल्ट रूपांतरण सभी इमेज को एक सामान्य फ़ोल्डर में डाल देता है या, और भी बुरा, SVG ग्राफ़िक्स पूरी तरह खो देता है।  

इस ट्यूटोरियल में हम एक पूर्ण, तैयार‑से‑चलाने योग्य समाधान के माध्यम से चलेंगे जो “how to set callback” प्रश्न का उत्तर देता है, **how to extract images** दिखाता है, और यहाँ तक कि **extract SVG from Word** को भी कवर करता है। अंत तक आप **save DOCX as Markdown** कर पाएँगे, प्रत्येक इमेज रिसोर्स के लिए एक कस्टम नामकरण योजना के साथ—कोई मैन्युअल झंझट नहीं।

## आप क्या सीखेंगे

- कन्वर्ज़न के दौरान इमेज फ़ाइलनामों को नियंत्रित करने का सबसे साफ़ तरीका क्यों कॉलबैक है।  
- Aspose.Words के `MarkdownSaveOptions.resource_saving_callback` में कैसे हुक करें।  
- **PNG**, **JPG**, **SVG**, और किसी भी अन्य एम्बेडेड रिसोर्स को निकालने वाला चरण‑दर‑चरण कोड।  
- नाम टकराव, बड़े फ़ाइलों, और क्रॉस‑प्लेटफ़ॉर्म पाथ की अजीबियों को संभालने के टिप्स।  

> **Pro tip:** यदि आप पहले से ही बड़े पाइपलाइन में Aspose.Words का उपयोग कर रहे हैं, तो आप इस कॉलबैक को बिना अपने कोड के बाकी हिस्से को छुए जोड़ सकते हैं।

---

![कॉलबैक सेट करने का आरेख](https://example.com/images/how-to-set-callback.png "कॉलबैक सेट करना")

## पूर्वापेक्षाएँ

- Python 3.8+ (उदाहरण f‑strings का उपयोग करता है, इसलिए 3.6+ पर्याप्त है)।  
- `aspose-words` पैकेज स्थापित हो (`pip install aspose-words`)।  
- एक DOCX फ़ाइल जिसमें रास्टर इमेज **और** वेक्टर ग्राफ़िक्स (SVG) हों।  
- Python फ़ंक्शन्स और फ़ाइल I/O की बुनियादी समझ।  

यदि आपके पास ये हैं, तो चलिए शुरू करते हैं।

---

## DOCX से इमेज निर्यात करने के लिए कॉलबैक कैसे सेट करें

समाधान का मुख्य भाग एक **resource‑saving callback** में रहता है। जब आप `document.save` को कॉल करते हैं, तो Aspose.Words हर इमेज या SVG के लिए इस डेलीगेट को कॉल करता है जिसे वह लिखना चाहता है। एक ट्यूपल `(new_name, data)` लौटाकर आप फ़ाइलनाम और बाइट पेलोड दोनों तय करते हैं।

```python
import aspose.words as aw
import os
import hashlib

# Step 1: Load the source document
document = aw.Document("YOUR_DIRECTORY/input.docx")
```

### कॉलबैक क्यों?

बिना कॉलबैक के, Aspose.Words `image1.png`, `image2.svg` आदि नाम की फ़ाइलें बनाता है और उन्हें Markdown फ़ाइल के बगल में एक फ़ोल्डर में रखता है। यह त्वरित डेमो के लिए ठीक है, लेकिन प्रोडक्शन में अक्सर आपको आवश्यकता होती है:

1. **Deterministic names** – संस्करण नियंत्रण या CDN प्रकाशन के लिए उपयोगी।  
2. **Collision avoidance** – समान मूल नाम वाली दो इमेज एक-दूसरे को ओवरराइट नहीं करेंगी।  
3. **Custom folder structures** – शायद आप सभी एसेट्स को `/assets/docs/` के तहत रखना चाहें।  

---

## रिसोर्स कॉलबैक का उपयोग करके DOCX से इमेज निर्यात करें

नीचे कॉलबैक कार्यान्वयन दिया गया है। यह बाइनरी डेटा को हैश करके एक अनूठा उपसर्ग बनाता है, मूल फ़ाइल एक्सटेंशन को बरकरार रखता है, और नई फ़ाइलनाम को कच्चे बाइट्स के साथ लौटाता है।

```python
def resource_callback(resource):
    """
    Called for every image/SVG that MarkdownSaveOptions wants to write.
    Returns a tuple (new_name, data) to control the saved file name.
    """
    # Preserve the original extension (.png, .svg, …)
    extension = os.path.splitext(resource.name)[1]

    # Compute a short hash of the image bytes – guarantees uniqueness
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]

    # Build a deterministic, collision‑free filename
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data
```

#### किनारी‑केस हैंडलिंग

- **Large files:** SHA‑256 किसी भी आकार के लिए ठीक काम करता है; हैश मेमोरी में गणना किया जाता है, इसलिए यदि आप बड़े PDF प्रोसेस कर रहे हैं तो मेमोरी सीमाओं का ध्यान रखें।  
- **Missing extensions:** कुछ पुराने Word फ़ाइलों में इमेज बिना स्पष्ट एक्सटेंशन के संग्रहीत हो सकते हैं। ऐसे में `extension` खाली रहेगा; आप डिफ़ॉल्ट रूप से `.bin` उपयोग कर सकते हैं या प्रारंभिक कुछ बाइट्स देख कर फ़ॉर्मेट का अनुमान लगा सकते हैं।  
- **Non‑image resources:** कॉलबैक हर बाहरी रिसोर्स (जैसे OLE ऑब्जेक्ट) के लिए बुलाया जाता है। यदि आप केवल इमेज/ SVG में रुचि रखते हैं, तो आगे बढ़ने से पहले `resource.type` से फ़िल्टर करें।  

---

## Word से इमेज और SVG निकालें

अब हम कॉलबैक को Markdown सहेजने वाले पाइपलाइन में जोड़ते हैं। `MarkdownSaveOptions` ऑब्जेक्ट इस उद्देश्य के लिए `resource_saving_callback` प्रॉपर्टी को उजागर करता है।

```python
# Step 2: Configure Markdown save options to use the callback
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.resource_saving_callback = resource_callback

# Optional: set the folder where images will be placed relative to the .md file
markdown_options.resource_folder = "assets/images"
```

`resource_folder` सेट करना वैकल्पिक है लेकिन अक्सर उपयोगी होता है। यदि आप इसे छोड़ देते हैं, तो इमेजें Markdown फ़ाइल के बगल में रखी जाती हैं, जिससे आपके प्रोजेक्ट रूट में गड़बड़ी हो सकती है।

### दस्तावेज़ सहेजना

```python
# Step 3: Save the document as Markdown, letting the callback store the resources
output_md_path = "YOUR_DIRECTORY/output.md"
document.save(output_md_path, markdown_options)
print(f"Markdown saved to {output_md_path}")
```

जब आप स्क्रिप्ट चलाएंगे, तो आपको इस प्रकार की फ़ाइलें दिखेंगी:

```
assets/images/img_a1b2c3d4e5.png
assets/images/img_f6g7h8i9j0.svg
```

और उत्पन्न `output.md` में इमेज लिंक होंगे जो उन सटीक फ़ाइलनामों की ओर इशारा करेंगे:

```markdown
![Image](assets/images/img_a1b2c3d4e5.png)
```

यह **how to extract images** भाग कार्रवाई में है—हर चित्र, रास्टर या वेक्टर, अब एक अलग, अनूठे नाम वाला एसेट है।

---

## कस्टम इमेज हैंडलिंग के साथ DOCX को Markdown के रूप में सहेजें

सब कुछ एक साथ जोड़ते हुए, यहाँ पूर्ण स्क्रिप्ट है जिसे आप `convert_docx_to_md.py` नामक फ़ाइल में कॉपी‑पेस्ट कर सकते हैं:

```python
import aspose.words as aw
import os
import hashlib

def resource_callback(resource):
    """Control the naming of each exported image/SVG."""
    extension = os.path.splitext(resource.name)[1] or ".bin"
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data

def convert_docx_to_markdown(input_path, output_md_path, image_folder="assets/images"):
    # Load the DOCX
    document = aw.Document(input_path)

    # Set up Markdown options with our callback
    md_options = aw.saving.MarkdownSaveOptions()
    md_options.resource_saving_callback = resource_callback
    md_options.resource_folder = image_folder

    # Ensure the output directory exists
    os.makedirs(os.path.dirname(output_md_path), exist_ok=True)
    os.makedirs(os.path.join(os.path.dirname(output_md_path), image_folder), exist_ok=True)

    # Perform the conversion
    document.save(output_md_path, md_options)
    print(f"✅ Conversion complete! Markdown at: {output_md_path}")

if __name__ == "__main__":
    # Adjust these paths to your environment
    INPUT_DOCX = "YOUR_DIRECTORY/input.docx"
    OUTPUT_MD = "YOUR_DIRECTORY/output.md"
    convert_docx_to_markdown(INPUT_DOCX, OUTPUT_MD)
```

**यह क्यों काम करता है:**  
- `resource_callback` सुनिश्चित करता है कि हर इमेज को एक अनूठा, पुनरुत्पादनीय नाम मिले।  
- `resource_folder` एसेट्स को अलग करके Markdown को व्यवस्थित रखता है।  
- `os.makedirs` कॉल्स आपको “folder not found” त्रुटियों से बचाते हैं जब स्क्रिप्ट नई मशीन पर चलती है।  

---

## Word से SVG निकालें – वेक्टर ग्राफ़िक्स के बारे में क्या?

कॉलबैक द्वारा SVG को PNG की तरह ही माना जाता है क्योंकि वे सिर्फ एक और `resource` हैं। एकमात्र अंतर यह है कि कुछ पुराने Word संस्करण SVG को *OfficeArt* ऑब्जेक्ट के रूप में एम्बेड करते हैं, जिसे Aspose.Words स्वचालित रूप से रास्टर PNG में बदल देता है जब तक आप स्पष्ट रूप से **preserve SVG** फ़्लैग सक्षम नहीं करते:

```python
md_options.export_svg = True  # Keep original SVG markup
```

सेव करने से पहले वह लाइन जोड़ें, और कॉलबैक `.svg` एक्सटेंशन वाले रिसोर्स प्राप्त करेगा, जिससे स्पष्ट वेक्टर डेटा संरक्षित रहेगा—रिस्पॉन्सिव वेब डॉक्यूमेंट्स के लिए उत्तम।

---

## सामान्य प्रश्न और समस्याएँ

| प्रश्न | उत्तर |
|----------|--------|
| **यदि दो इमेज समान हों तो क्या होगा?** | SHA‑256 हैश समान होगा, इसलिए फ़ाइलनाम टकराएंगे। यदि आपको दोनों कॉपी चाहिए, तो हैश गणना में मूल `resource.name` शामिल करें (उदाहरण के लिए, `hash(resource.name + resource.data)`)। |
| **क्या मैं फ़ाइल प्रकार के अनुसार फ़ोल्डर बदल सकता हूँ?** | हां। `resource_callback` के अंदर आप `extension` की जाँच कर सकते हैं और रास्टर इमेज के लिए `f"png/{new_name}"` तथा वेक्टर के लिए `f"svg/{new_name}"` जैसे पाथ लौटा सकते हैं। |
| **क्या यह Linux/macOS पर काम करता है?** | बिल्कुल। कोड `os.path` का उपयोग करता है जो पाथ सेपरेटर को एब्स्ट्रैक्ट करता है। बस यह सुनिश्चित करें कि यदि आप पेड वर्ज़न उपयोग कर रहे हैं तो आपके पास Aspose.Words लाइसेंस फ़ाइल (`aspose.words.lic`) उपलब्ध हो। |
| **बड़े दस्तावेज़ों के लिए मेमोरी उपयोग के बारे में क्या?** | कॉलबैक प्रत्येक रिसोर्स के लिए **पूरा बाइट एरे** प्राप्त करता है, जिसका मतलब है कि पूरी इमेज अस्थायी रूप से मेमोरी में रहती है। मल्टी‑गिगाबाइट फ़ाइलों के लिए आप कॉलबैक के भीतर डेटा को डिस्क पर स्ट्रीम करना चाह सकते हैं बजाय इसे लौटाने के। |

---

## निष्कर्ष

अब आप जानते हैं **how to set callback** ताकि आप **DOCX को Markdown के रूप में सहेजते** समय इमेज एक्सट्रैक्शन को नियंत्रित कर सकें। यह तरीका आपको **DOCX से इमेज निर्यात**, **Word से SVG निकालने**, और आपका Markdown साफ़ और निर्धारक रखने देता है।  

एक ही, स्वतंत्र स्क्रिप्ट में हमने डॉक्यूमेंट लोड करना, रिसोर्स‑saving कॉलबैक परिभाषित करना, `MarkdownSaveOptions` को कॉन्फ़िगर करना, और नाम टकराव तथा वेक्टर ग्राफ़िक्स जैसी किनारी स्थितियों को संभालना कवर किया। परिणामस्वरूप एक सेट अनूठे नाम वाले एसेट्स और एक पूरी तरह लिंक किया हुआ Markdown फ़ाइल मिलती है—स्टैटिक साइट जेनरेटर, डॉक्यूमेंटेशन पाइपलाइन, या किसी भी वर्कफ़्लो के लिए तैयार जो साफ़, पुन: उपयोग योग्य एसेट्स चाहता है।  

**अगले कदम?**  
- MkDocs जैसे स्टैटिक‑साइट जेनरेटर के साथ इसे जोड़ने की कोशिश करें ताकि Word‑आधारित डॉक्यूमेंट्स को स्वचालित रूप से प्रकाशित किया जा सके।  
- `markdown_options.export_images_as_base64 = True` के साथ प्रयोग करें यदि आप बाहरी फ़ाइलों के बजाय इनलाइन इमेज पसंद करते हैं।  
- Aspose.Words के अन्य कॉलबैक (जैसे, `document_saving_callback`) में गहराई से जाएँ ताकि आप स्वयं Markdown आउटपुट को नियंत्रित कर सकें।  

क्या आपके पास अन्य Office फ़ॉर्मेट्स से **how to extract images** के बारे में और प्रश्न हैं, या किसी विशिष्ट नामकरण नियम के लिए कॉलबैक को ट्यून करने में मदद चाहिए? नीचे टिप्पणी छोड़ें, और कोडिंग का आनंद लें!

## आप आगे क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन संबंधित विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर में महारत हासिल करने और अपने प्रोजेक्ट में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [DOCX को Markdown में बदलते समय इमेज का नाम कैसे बदलें](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)
- [DOCX से Markdown कैसे सहेजें – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}