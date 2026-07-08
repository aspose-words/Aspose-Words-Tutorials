---
category: general
date: 2026-06-30
description: DOCX को markdown में बदलते समय इमेज का नाम कैसे बदलें। इमेज के नाम बदलना
  सीखें और कस्टम इमेज फ़ाइलनामों के साथ Word को markdown के रूप में सहेजें।
draft: false
keywords:
- how to rename images
- convert docx to markdown
- change image names
- save word as markdown
- custom image filenames
language: hi
og_description: DOCX को मार्कडाउन में बदलते समय छवियों का नाम कैसे बदलें। यह गाइड
  आपको दिखाता है कि छवि नाम कैसे बदलें, वर्ड को मार्कडाउन के रूप में सहेजें, और कस्टम
  छवि फ़ाइलनामों का उपयोग कैसे करें।
og_title: DOCX को Markdown में परिवर्तित करते समय छवियों का नाम कैसे बदलें
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  headline: How to Rename Images When Converting DOCX to Markdown
  type: TechArticle
- description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  name: How to Rename Images When Converting DOCX to Markdown
  steps:
  - name: Why Use a GUID?
    text: '* **Uniqueness** – A GUID (`uuid4`) guarantees that two images will never
      clash, even across multiple runs. * **Traceability** – If you need to debug
      later, the GUID can be logged alongside the original Word paragraph number.
      * **Portability** – No reliance on the original Word naming scheme, which '
  - name: Expected Output (excerpt)
    text: '```markdown # Sample Document'
  - name: What if the document contains non‑image resources?
    text: Our callback already checks the file extension and returns `True` for anything
      that isn’t an image. This means CSS files, fonts, or embedded OLE objects keep
      their original names, which is usually what you want when you **save word as
      markdown**.
  - name: Can I use a custom naming scheme instead of GUIDs?
    text: 'Absolutely. Replace the `uuid.uuid4()` call with any function that returns
      a string. For example, you could prepend the original paragraph index:'
  - name: How does this affect performance on large documents?
    text: The callback runs once per resource, so the overhead is minimal—mostly the
      time to generate a GUID. Even a 200‑page report with dozens of images finishes
      in under a second on a modern laptop.
  - name: What if I need the image filenames to be deterministic (e.g., for CI builds)?
    text: 'Swap `uuid.uuid4()` for a hash of the original image bytes:'
  type: HowTo
tags:
- Aspose.Words
- Python
- Markdown
- Image Processing
title: DOCX को Markdown में बदलते समय इमेज का नाम कैसे बदलें
url: /hi/python/document-conversion/how-to-rename-images-when-converting-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX को Markdown में बदलते समय इमेज का नाम कैसे बदलें

क्या आपने कभी सोचा है कि DOCX फ़ाइल को Markdown में बदलते समय **इमेजों के नाम** को स्वचालित रूप से कैसे बदलें? आप अकेले नहीं हैं। कई दस्तावेज़ीकरण पाइपलाइन में डिफ़ॉल्ट इमेज नाम (जैसे `image1.png`) को ट्रैक करना एक दुःस्वप्न बन जाता है, विशेष रूप से जब वही markdown टीमों के बीच संस्करण‑नियंत्रित होता है।  

अच्छी खबर यह है कि Aspose.Words for Python इसे बहुत आसान बनाता है **इमेज के नाम** को तुरंत बदलने के लिए, और आप अपने Markdown को साफ़ रख सकते हैं जबकि कस्टम‑नामित एसेट्स के एक व्यवस्थित फ़ोल्डर को संरक्षित रख सकते हैं।  

इस ट्यूटोरियल में आप सीखेंगे:

* Python में एक Word दस्तावेज़ (`.docx`) लोड करें।  
* एक कॉलबैक के साथ Markdown सहेजने की प्रक्रिया में हुक करें जो प्रत्येक इमेज को GUID‑आधारित फ़ाइलनाम देता है।  
* दस्तावेज़ को Markdown के रूप में सहेजें ताकि उत्पन्न फ़ाइल नई‑नामित इमेजों को संदर्भित करे।  

यदि आप बुनियादी Python में सहज हैं और आपके पास Aspose.Words स्थापित है, तो आप पाँच मिनट से कम समय में तैयार हो जाएंगे। कोई बाहरी स्क्रिप्ट नहीं, कोई मैन्युअल नाम बदलना नहीं—सिर्फ एक ही, स्वतंत्र प्रोग्राम जो आपके लिए सभी कार्य संभाल लेगा।

---

## आवश्यकताएँ — शुरू करने से पहले आपको क्या चाहिए

| आवश्यकता | क्यों महत्वपूर्ण है |
|-------------|----------------|
| **Python 3.7+** | उदाहरण f‑strings और type hints का उपयोग करता है जो 3.6 में पेश किए गए थे, लेकिन 3.7+ आपको `os.path.splitext` की सुविधाएँ देता है। |
| **Aspose.Words for Python via .NET** (`pip install aspose-words`) | यह लाइब्रेरी `aw.Document` क्लास और `MarkdownSaveOptions` प्रदान करती है, जिन पर हम निर्भर हैं। |
| **Write permission** to the output folder | कॉलबैक नई इमेज फ़ाइलें बनाएगा, इसलिए स्क्रिप्ट को उन्हें लिखने की अनुमति होनी चाहिए। |
| **A DOCX file** you want to convert | साधारण रिपोर्ट से लेकर जटिल मैनुअल तक कुछ भी काम करेगा। |

> **Pro tip:** यदि आप वर्चुअल एनवायरनमेंट का उपयोग कर रहे हैं, तो Aspose.Words स्थापित करने से पहले उसे सक्रिय करें। यह निर्भरताओं को अलग करता है और संस्करण टकराव से बचाता है।

---

## चरण 1: Word दस्तावेज़ लोड करें  

जब आप **docx को markdown में बदलना** चाहते हैं, तो सबसे पहला काम स्रोत फ़ाइल को खोलना है। Aspose.Words सभी लो‑लेवल OPC हैंडलिंग को एब्स्ट्रैक्ट कर देता है, इसलिए एक ही पंक्ति काम कर देती है।

```python
import aspose.words as aw

# Replace YOUR_DIRECTORY with the folder that holds your .docx file
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*यह क्यों महत्वपूर्ण है:* दस्तावेज़ को लोड किए बिना आप उसकी संसाधनों की जाँच नहीं कर सकते, और Markdown एक्सपोर्टर के पास लिखने के लिए कुछ नहीं रहेगा। `aw.Document` ऑब्जेक्ट पूरी Word पैकेज को मेमोरी में रखता है, जिससे सहेजने से पहले इसे सुरक्षित रूप से बदल सकते हैं।

---

## चरण 2: एक कॉलबैक लिखें जो **इमेज संसाधनों का नाम बदलता** है  

Aspose.Words आपको `MarkdownSaveOptions` में `resource_saving_callback` प्लग करने देता है। कॉलबैक प्रत्येक संसाधन (इमेज, CSS, आदि) को डिस्क पर लिखे जाने से ठीक पहले प्राप्त करता है। `resource.file_name` को बदलकर हम **कस्टम इमेज फ़ाइलनाम** लागू कर सकते हैं।

```python
def rename_image_resource(resource):
    """
    Rename image resources with a unique GUID before saving.
    This is where we implement how to rename images.
    """
    import uuid, os

    # Guard: only process image resources, ignore CSS or other files
    if not resource.file_name.lower().endswith(('.png', '.jpg', '.jpeg', '.gif', '.bmp')):
        return True  # Let Aspose handle non‑image resources unchanged

    # Extract the original extension so we keep PNG as PNG, JPG as JPG, etc.
    _, ext = os.path.splitext(resource.file_name)

    # Generate a globally unique identifier and tack the original extension on
    new_name = f"{uuid.uuid4()}{ext}"
    resource.file_name = new_name

    # Returning True tells Aspose to proceed with the default saving logic
    return True
```

### GUID क्यों उपयोग करें?

* **Uniqueness** – एक GUID (`uuid4`) यह सुनिश्चित करता है कि दो इमेज कभी टकराएँ नहीं, यहाँ तक कि कई रन में भी।  
* **Traceability** – यदि बाद में डिबग करने की आवश्यकता हो, तो GUID को मूल Word पैराग्राफ नंबर के साथ लॉग किया जा सकता है।  
* **Portability** – मूल Word नामकरण योजना पर निर्भरता नहीं है, जिसमें स्पेस या विशेष अक्षर हो सकते हैं जो Markdown लिंक को तोड़ सकते हैं।

---

## चरण 3: कॉलबैक को Markdown सहेजने विकल्पों से जोड़ें  

अब हम Aspose को बताते हैं कि जब भी वह आउटपुट फ़ोल्डर में इमेज लिखता है, तो हमारी नाम बदलने की लॉजिक का उपयोग करे।

```python
md_options = aw.saving.MarkdownSaveOptions()
md_options.resource_saving_callback = rename_image_resource

# Optional: control where images are placed relative to the markdown file
md_options.images_folder = "images"  # creates a sub‑folder called 'images'
```

*व्याख्या:* `MarkdownSaveOptions` क्लास लाइन ब्रेक से लेकर इमेज फ़ोल्डर स्थान तक सब कुछ नियंत्रित करता है। `resource_saving_callback` सेट करके, आपको एक **हुक** मिलता है जो प्रत्येक एम्बेडेड संसाधन के लिए फायर होता है, जिससे आपको फ़ाइल डिस्क पर लिखे जाने से पहले **इमेज के नाम बदलने** का अवसर मिलता है।

---

## चरण 4: दस्तावेज़ को Markdown के रूप में सहेजें – अंतिम भाग  

कॉलबैक स्थापित होने के साथ, अंतिम चरण सीधा है।

```python
output_path = "YOUR_DIRECTORY/CustomResources.md"
doc.save(output_path, md_options)
print(f"Markdown saved to {output_path}")
```

जब स्क्रिप्ट समाप्त हो जाएगी, तो आपको मिलेगा:

* `CustomResources.md` – आपके Word फ़ाइल का Markdown प्रतिनिधित्व।  
* `images/` फ़ोल्डर (या जो भी आपने सेट किया) जिसमें `d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png` जैसी फ़ाइलें होंगी।  

Markdown फ़ाइल नए GUID‑आधारित फ़ाइलनामों को संदर्भित करेगी, इसलिए कोई भी डाउनस्ट्रीम प्रोसेसर (GitHub, MkDocs, आदि) सही इमेजों को बिना मैन्युअल रूप से नाम बदले ही ले लेगा।

### अपेक्षित आउटपुट (उद्धरण)

```markdown
# Sample Document

Here is an image that was originally called `image1.png` in the DOCX:

![d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e](images/d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png)

And another one:

![a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6](images/a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6.jpg)
```

GUID प्रत्येक रन में अलग होंगे, लेकिन पैटर्न वही रहेगा।

---

## किनारे के मामलों और सामान्य प्रश्नों को संभालना  

### यदि दस्तावेज़ में गैर‑इमेज संसाधन हों तो क्या होगा?

हमारा कॉलबैक पहले से ही फ़ाइल एक्सटेंशन जांचता है और इमेज नहीं होने पर `True` लौटाता है। इसका मतलब है कि CSS फ़ाइलें, फ़ॉन्ट्स, या एम्बेडेड OLE ऑब्जेक्ट्स अपने मूल नाम रखेंगे, जो आमतौर पर तब चाहिए जब आप **word को markdown के रूप में सहेजते** हैं।

### क्या मैं GUID के बजाय कस्टम नामकरण योजना उपयोग कर सकता हूँ?

बिल्कुल। `uuid.uuid4()` कॉल को किसी भी फ़ंक्शन से बदलें जो स्ट्रिंग लौटाता हो। उदाहरण के लिए, आप मूल पैराग्राफ इंडेक्स को प्रीपेंड कर सकते हैं:

```python
new_name = f"para{resource.resource_id}{ext}"
```

सिर्फ यह सुनिश्चित करें कि परिणामी नाम दस्तावेज़ में अद्वितीय हो।

### बड़े दस्तावेज़ों पर इसका प्रदर्शन कैसे प्रभावित होता है?

कॉलबैक प्रत्येक संसाधन पर एक बार चलता है, इसलिए ओवरहेड न्यूनतम है—मुख्यतः GUID उत्पन्न करने का समय। यहां तक कि 200‑पेज की रिपोर्ट जिसमें दर्जनों इमेज हों, आधुनिक लैपटॉप पर एक सेकंड से कम समय में समाप्त हो जाती है।

### यदि मुझे इमेज फ़ाइलनामों को निर्धारक (deterministic) चाहिए (जैसे CI बिल्ड्स के लिए) तो क्या करें?

`uuid.uuid4()` को मूल इमेज बाइट्स के हैश से बदलें:

```python
import hashlib
hash = hashlib.sha256(resource.raw_bytes).hexdigest()[:12]
new_name = f"{hash}{ext}"
```

यह प्रत्येक बार जब आप स्क्रिप्ट को समान स्रोत इमेज पर चलाते हैं, तो वही फ़ाइलनाम उत्पन्न करता है।

---

## पूर्ण कार्यशील स्क्रिप्ट – कॉपी, पेस्ट, रन  



## अब आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स निकटतम संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API सुविधाओं में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का अन्वेषण करने में मदद करती हैं।

- [save docx as markdown – इमेज एक्सट्रैक्शन के साथ पूर्ण C# गाइड](/words/english/net/programming-with-markdownsaveoptions/save-docx-as-markdown-full-c-guide-with-image-extraction/)
- [DOCX से Markdown सहेजने का तरीका – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}