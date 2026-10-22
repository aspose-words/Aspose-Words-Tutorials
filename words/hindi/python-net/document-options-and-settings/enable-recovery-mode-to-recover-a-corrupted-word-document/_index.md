---
category: general
date: 2026-10-04
description: Aspose.Words में रिकवरी मोड सक्षम करें ताकि एक भ्रष्ट Word दस्तावेज़
  को सुरक्षित रूप से पुनर्प्राप्त किया जा सके। पूर्ण Python कोड और व्याख्याओं के साथ
  चरण‑दर‑चरण गाइड का पालन करें।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- enable recovery mode
- recover corrupted word document
- Aspose.Words load options
- document recovery Python
- handling damaged .docx files
language: hi
lastmod: 2026-10-04
og_description: Aspose.Words का उपयोग करके भ्रष्ट Word दस्तावेज़ को पुनर्प्राप्त करने
  के लिए रिकवरी मोड सक्षम करें। यह ट्यूटोरियल सटीक Python कोड, यह क्यों काम करता है,
  और किनारे के मामलों को कैसे संभालें, दिखाता है।
og_image_alt: Screenshot of Python code loading a corrupted Word document with recovery
  mode enabled
og_title: करप्ट वर्ड दस्तावेज़ को पुनर्प्राप्त करने के लिए रिकवरी मोड सक्षम करें –
  पूर्ण गाइड
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  headline: Enable recovery mode to recover a corrupted Word document
  type: TechArticle
- description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  name: Enable recovery mode to recover a corrupted Word document
  steps:
  - name: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
    text: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
  - name: Load the `.docx` using those options.
    text: Load the `.docx` using those options.
  - name: Verify the mode and optionally save a repaired copy.
    text: Verify the mode and optionally save a repaired copy.
  type: HowTo
tags:
- Aspose.Words
- Python
- Document processing
- Error handling
title: भ्रष्ट वर्ड दस्तावेज़ को पुनर्प्राप्त करने के लिए रिकवरी मोड सक्षम करें
url: /hi/python/document-options-and-settings/enable-recovery-mode-to-recover-a-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# भ्रष्ट Word दस्तावेज़ को पुनर्प्राप्त करने के लिए रिकवरी मोड सक्षम करें

यदि आपको Word फ़ाइल लोड करते समय **रिकवरी मोड सक्षम** करने की आवश्यकता है, तो यह गाइड Aspose.Words for Python के साथ इसे कैसे करना है, बिल्कुल दिखाता है। रिकवरी मोड को चालू करके आप **एक भ्रष्ट Word दस्तावेज़ को पुनर्प्राप्त** कर सकते हैं, जिसे अन्यथा एक अपवाद फेंका जाता।

इन अगले अनुभागों में आप सीखेंगे:

* कौन‑से क्लास और प्रॉपर्टी रिकवरी व्यवहार को नियंत्रित करती हैं।  
* कैसे संभावित रूप से क्षतिग्रस्त `.docx` फ़ाइल को आपके एप्लिकेशन को क्रैश किए बिना लोड करें।  
* सामान्य लोडिंग समस्याओं का निवारण करने और रिकवरी रणनीति को अनुकूलित करने के टिप्स।

> **Prerequisite** – आपके पास Aspose.Words for Python स्थापित है (`pip install aspose-words`) और Python फ़ाइल I/O की बुनियादी समझ है।

## रिकवरी मोड क्या करता है और आपको इसे क्यों सक्षम करना चाहिए

Aspose.Words एक Word फ़ाइल की आंतरिक संरचना को पार्स करता है, फिर उसे `Document` ऑब्जेक्ट के रूप में उजागर करता है। जब फ़ाइल भ्रष्ट होती है—जैसे भाग गायब होना, टूटा हुआ XML, या अमान्य रिलेशनशिप—तो पार्सर दो में से एक कर सकता है:

| मोड | व्यवहार |
|------|------------|
| `STRICT` | भ्रष्टाचार के पहले संकेत पर एक अपवाद फेंकता है। |
| `IGNORE_ERRORS` | अपठनीय भागों को छोड़ देता है लेकिन सामग्री चुपचाप खो सकती है। |
| `RECOVER` (the **enable recovery mode** option) | दस्तावेज़ को पुनर्निर्मित करने का प्रयास करता है, यथासंभव अधिक सामग्री को संरक्षित करता है और चुने हुए मोड को `load_options.recovery_mode` के माध्यम से उजागर करता है। |

`RECOVER` वह अनुशंसित विकल्प है जब आपको नीचे की प्रक्रिया के लिए **भ्रष्ट word दस्तावेज़** फ़ाइलों को पुनर्प्राप्त करना आवश्यक हो, जैसे कि टेक्स्ट निकालना या PDF में बदलना।

## चरण 1: लोड विकल्प बनाएं और रिकवरी मोड सक्षम करें

पहला कदम `LoadOptions` को इंस्टैंशिएट करना और `recovery_mode` प्रॉपर्टी को `RecoveryMode.RECOVER` पर सेट करना है। यह लाइब्रेरी को पार्सिंग के दौरान रिकवरी पाथ में प्रवेश करने के लिए बताता है।

```python
import aspose.words as aw

# Step 1: Create load options and enable recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER  # alternatives: .IGNORE_ERRORS, .STRICT
```

**यह क्यों महत्वपूर्ण है:**  
यदि आप इस चरण को छोड़ देते हैं और दस्तावेज़ क्षतिग्रस्त है, तो कंस्ट्रक्टर `aw.Document(...)` `InvalidOperationException` उठाएगा। रिकवरी मोड को सक्षम करने से क्रैश से बचा जा सकता है और आपको एक आंशिक‑मरम्मत किया हुआ `Document` ऑब्जेक्ट मिलता है, जिसपर आप अभी भी काम कर सकते हैं।

## चरण 2: निर्दिष्ट विकल्पों का उपयोग करके संभावित रूप से भ्रष्ट दस्तावेज़ लोड करें

`load_options` इंस्टेंस को `Document` कंस्ट्रक्टर में पास करें। लोडर अब स्वचालित रूप से रिकवरी एल्गोरिद्म लागू करेगा।

```python
# Step 2: Load the potentially corrupted document using the specified options
doc_path = "YOUR_DIRECTORY/Corrupted.docx"
doc = aw.Document(doc_path, load_options)
```

**Tip:** `YOUR_DIRECTORY` को उस पूर्ण या सापेक्ष पथ से बदलें जिसे आपका रनटाइम एक्सेस कर सकता है। यदि फ़ाइल मौजूद नहीं है, तो Aspose.Words रिकवरी लॉजिक तक पहुँचने से पहले ही `FileNotFoundError` उठाएगा।

## चरण 3: सत्यापित करें कि रिकवरी मोड लागू किया गया था

आप `load_options.recovery_mode` को निरीक्षण करके सक्रिय मोड की पुष्टि कर सकते हैं। यह लॉगिंग या पाइपलाइन में बाद की शर्तीय हैंडलिंग के लिए उपयोगी है।

```python
# Step 3: Confirm that the document was loaded with the chosen recovery mode
print("Document loaded with recovery mode:", load_options.recovery_mode)
```

**अपेक्षित आउटपुट**

```
Document loaded with recovery mode: RecoveryMode.RECOVER
```

यदि आउटपुट `RECOVER` दिखाता है, तो आपने सफलतापूर्वक **रिकवरी मोड सक्षम** किया है और दस्तावेज़ अब आगे की प्रोसेसिंग (जैसे टेक्स्ट एक्सट्रैक्शन, PDF में रूपांतरण, या मरम्मत की गई कॉपी सहेजना) के लिए तैयार है।

## चरण 4 (वैकल्पिक): भविष्य के उपयोग के लिए एक मरम्मत की गई प्रति सहेजें

लोड करने के बाद, आप पुनर्प्राप्त दस्तावेज़ को स्थायी रूप से सहेजना चाह सकते हैं ताकि आपको रिकवरी चरण दोहराना न पड़े।

```python
# Optional: Save the repaired document
repaired_path = "YOUR_DIRECTORY/Corrupted_Repaired.docx"
doc.save(repaired_path)
print(f"Repaired document saved to {repaired_path}")
```

सेव करने से एक नई `.docx` बनती है जिसे Aspose.Words वैध मानता है, और इसे Microsoft Word में बिना किसी चेतावनी के खोला जा सकता है।

## सामान्य प्रश्न और किनारे‑के‑केस हैंडलिंग

| प्रश्न | उत्तर |
|----------|--------|
| **यदि दस्तावेज़ पूरी तरह से अपठनीय है तो क्या होगा?** | भले ही `RECOVER` मोड में, कुछ फ़ाइलें मरम्मत से बाहर होती हैं। `Document` ऑब्जेक्ट बनाया जाएगा लेकिन इसमें केवल एक खाली पृष्ठ हो सकता है। सामग्री की पुष्टि के लिए `doc.get_page_count()` जांचें। |
| **क्या मैं लोड करने के बाद `IGNORE_ERRORS` पर स्विच कर सकता हूँ?** | नहीं। रिकवरी मोड को **`Document` कंस्ट्रक्टर** चलने से पहले सेट किया जाना चाहिए। यदि आपको अलग रणनीति चाहिए तो नया `LoadOptions` इंस्टेंस बनाएं। |
| **क्या रिकवरी मोड प्रदर्शन को प्रभावित करता है?** | हां, यह थोड़ा ओवरहेड जोड़ता है क्योंकि लाइब्रेरी टूटे हुए भागों को पुनर्निर्मित करने का प्रयास करती है। अधिकांश फ़ाइलों (< 2 MB) के लिए प्रभाव नगण्य है। |
| **क्या यह दृष्टिकोण भाषा‑अज्ञेय है?** | इसी अवधारणा .NET, Java, और Node.js APIs (`LoadOptions.RecoveryMode`) में भी मौजूद है। कोड सिंटैक्स बदलता है, लेकिन लॉजिक समान है। |

## प्रो टिप: विस्तृत रिकवरी जानकारी लॉग करें

Aspose.Words एक `LoadOptions.recovery_callback` प्रदान करता है जो प्रत्येक रिकवरी चरण के बारे में विस्तृत संदेश प्राप्त करता है। इसे जोड़ने से आप यह निदान कर सकते हैं कि कोई विशेष दस्तावेज़ क्यों विफल हुआ।

```python
def recovery_logger(message):
    print("[Recovery] ", message)

load_options.recovery_callback = recovery_logger
```

अब हर आंतरिक सुधार (जैसे “Removed duplicate relationship”) कंसोल में प्रिंट होगा।

## पूर्ण, चलाने योग्य उदाहरण

सभी भागों को मिलाकर, यहाँ एक स्व-निहित स्क्रिप्ट है जिसे आप कॉपी‑पेस्ट करके तुरंत चला सकते हैं:

```python
import aspose.words as aw

def enable_recovery_and_load(doc_path: str, save_repaired: bool = False):
    # Create load options and enable recovery mode
    load_options = aw.loading.LoadOptions()
    load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER

    # Optional: attach a simple logger
    load_options.recovery_callback = lambda msg: print("[Recovery] ", msg)

    # Load the document with recovery enabled
    doc = aw.Document(doc_path, load_options)

    # Verify the mode
    print("Document loaded with recovery mode:", load_options.recovery_mode)

    # Show basic info
    print("Page count:", doc.page_count)
    print("Word count:", doc.get_text().split())

    # Optionally save a repaired copy
    if save_repaired:
        repaired_path = doc_path.replace(".docx", "_repaired.docx")
        doc.save(repaired_path)
        print(f"Repaired document saved to {repaired_path}")

    return doc

if __name__ == "__main__":
    corrupted_path = "YOUR_DIRECTORY/Corrupted.docx"
    enable_recovery_and_load(corrupted_path, save_repaired=True)
```

स्क्रिप्ट चलाने से रिकवरी मोड, पेज काउंट, और मरम्मत किए गए दस्तावेज़ से निकाले गए शब्दों की सूची प्रिंट होगी। यदि आप `save_repaired=True` सेट करते हैं, तो मूल फ़ाइल के साथ एक नई साफ़ फ़ाइल दिखाई देगी।

## निष्कर्ष

आप अब जानते हैं कि Aspose.Words for Python में **रिकवरी मोड सक्षम** कैसे किया जाता है और विश्वसनीय रूप से **भ्रष्ट Word दस्तावेज़** फ़ाइलों को कैसे **पुनर्प्राप्त** किया जाता है। मुख्य कदम हैं:

1. `LoadOptions` बनाएं और `recovery_mode` को `RECOVER` पर सेट करें।  
2. उन विकल्पों के साथ `.docx` लोड करें।  
3. मोड की पुष्टि करें और वैकल्पिक रूप से एक मरम्मत की गई कॉपी सहेजें।

अब आप आगे के विषयों का अन्वेषण कर सकते हैं जैसे **पुनर्प्राप्त दस्तावेज़ से टेक्स्ट निकालना**, **इसे PDF में बदलना**, या **बड़ी दस्तावेज़ लाइब्रेरी के लिए बैच रिकवरी को स्वचालित करना**।

---


## अगला आप क्या सीखें?

निम्नलिखित ट्यूटोरियल निकट संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों का पता लगाने में मदद करती हैं।

- [भ्रष्ट DOCX पुनर्प्राप्त करें – रिकवरी मोड सक्षम करने और पेज प्राप्त करने के लिए पूर्ण गाइड](/words/english/python-net/document-operations/recover-corrupted-docx-complete-guide-to-enable-recovery-mod/)
- [भ्रष्ट DOCX पुनर्प्राप्त करें – वर्ड दस्तावेज़ खोलें और लोड करें](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)
- [Aspose.Words के साथ क्षतिग्रस्त docx को पुनर्प्राप्त करें – रिकवरी मोड सेट करें और लोड विकल्प](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}