---
category: general
date: 2026-07-06
description: CMake प्रोजेक्ट को चरण‑दर‑चरण बनाएं। जानें कि CMake को कैसे कॉन्फ़िगर
  करें, CMake को कैसे बनाएं, और विश्वसनीय परीक्षण के लिए CTest को कैसे चलाएँ।
draft: false
keywords:
- build cmake project
- how to configure cmake
- how to build cmake
- how to run ctest
- cmake build and test
language: hi
og_description: स्पष्ट चरणों के साथ CMake प्रोजेक्ट को जल्दी बनाएं। यह गाइड दिखाता
  है कि CMake को कैसे कॉन्फ़िगर करें, CMake को कैसे बनाएं, और CTest को कैसे चलाएँ।
og_title: 'CMake प्रोजेक्ट बनाएं: कॉन्फ़िगर, बिल्ड और टेस्ट गाइड'
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Build CMake project step‑by‑step. Learn how to configure CMake, how
    to build CMake, and how to run CTest for reliable testing.
  headline: 'Build CMake Project: Configure, Build & Test'
  type: TechArticle
tags:
- cmake
- ctest
- build-system
title: 'CMake प्रोजेक्ट बनाएं: कॉन्फ़िगर, बिल्ड और टेस्ट'
url: /hi/python/getting-started/build-cmake-project-configure-build-test/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# CMake प्रोजेक्ट बनाएं: कॉन्फ़िगर, बिल्ड और टेस्ट

क्या आपने कभी सोचा है कि **build CMake project** को बिना घंटों StackOverflow खोजे कैसे बनाया जाए? आप अकेले नहीं हैं। अधिकांश डेवलपर्स को वही समस्या आती है जब वे एक साधारण `CMakeLists.txt` से एक पुनरुत्पादनीय बिल्ड पाइपलाइन पर जाने की कोशिश करते हैं। 

इस ट्यूटोरियल में हम पूरी प्रक्रिया—*how to configure CMake*, *how to build CMake*, और *how to run CTest*—पर चलेंगे ताकि आपको एक साफ़, दोहराने योग्य बिल्ड मिल सके जिसे आप किसी भी मशीन पर चला सकें। अंत तक आपके पास एक कार्यशील उदाहरण होगा जिसे आप अपनी रिपॉजिटरी में कॉपी‑पेस्ट कर सकते हैं, अतिरिक्त स्क्रिप्ट की आवश्यकता नहीं।

## आवश्यकताएँ — शुरू करने से पहले आपको क्या चाहिए

- एक नवीनतम CMake संस्करण (3.20 या नया) – पुराने रिलीज़ में उन फ़्लैग्स में से कुछ नहीं होते जिनका हम उपयोग करेंगे।
- आपके प्लेटफ़ॉर्म द्वारा समर्थित एक C++ कंपाइलर (gcc, clang, MSVC, आदि)।
- एक टर्मिनल या कमांड‑प्रॉम्प्ट जिसमें `cmake` और `ctest` तक पहुँच हो।
- (वैकल्पिक) Git ताकि आप उदाहरण रिपॉजिटरी को क्लोन कर सकें यदि आप सटीक स्रोत के साथ आगे बढ़ना चाहते हैं।

यदि इनमें से कोई भी अनुपलब्ध है, तो अभी प्राप्त करें; अन्यथा बाद में आपको “command not found” त्रुटियाँ मिलेंगी, और यह कभी मज़ेदार नहीं होता।

## चरण 1: CMake प्रोजेक्ट को कॉन्फ़िगर करें (Release कॉन्फ़िगरेशन)

जब आप *how to configure CMake* करते हैं, तो सबसे पहला काम CMake को बताना है कि स्रोत कहाँ स्थित है और बिल्ड आर्टिफैक्ट्स कहाँ रखे जाने चाहिए। `-S` फ़्लैग स्रोत डायरेक्टरी की ओर इशारा करता है, `-B` एक अलग बिल्ड फ़ोल्डर बनाता है, और `-D CMAKE_BUILD_TYPE=Release` एक ऑप्टिमाइज़्ड बिल्ड को मजबूर करता है।

```bash
# Replace YOUR_DIRECTORY with the path to your project root
cmake -S YOUR_DIRECTORY/Examples/DocsExamples \
      -B YOUR_DIRECTORY/Examples/DocsExamples/build \
      -D CMAKE_BUILD_TYPE=Release
```

**क्यों यह महत्वपूर्ण है:** स्रोत और बिल्ड फ़ाइलों को अलग रखना (`out‑of‑source` बिल्ड) आकस्मिक स्रोत संशोधनों को रोकता है और बाद में बिल्ड डायरेक्टरी को साफ़ करना आसान बनाता है। `Release` फ़्लैग कंपाइलर को ऑप्टिमाइज़ेशन सक्षम करने के लिए भी कहता है, जो आमतौर पर अंतिम बाइनरी के लिए वांछित होता है।

> **प्रो टिप:** यदि आपको ट्रबलशूटिंग के लिए एक Debug बिल्ड चाहिए, तो बस `Release` को `Debug` से बदल दें। वही कमांड काम करता है—CMake बाकी सब संभाल लेता है।

## चरण 2: कॉन्फ़िगर किए गए प्रोजेक्ट को बिल्ड करें

अब जबकि कॉन्फ़िगरेशन चरण ने सभी आवश्यक मेकफ़ाइल्स या Visual Studio प्रोजेक्ट फ़ाइलें जेनरेट कर ली हैं, आप वास्तव में कोड को कंपाइल कर सकते हैं। `--build` विकल्प अंतर्निहित बिल्ड टूल (`make`, `ninja`, `MSBuild`, आदि) को एब्स्ट्रैक्ट कर देता है, इसलिए वही कमांड Linux, macOS, और Windows पर काम करता है।

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build
```

**आंतरिक रूप से क्या हो रहा है?** CMake पिछले चरण में बनाई गई `CMakeCache.txt` को पढ़ता है, उपयुक्त बिल्ड टूल निर्धारित करता है, और सही फ़्लैग्स के साथ उसे चलाता है। यह *how to build CMake* का मूल है—आपको याद रखने की ज़रूरत नहीं कि आप `make` या `ninja` का उपयोग कर रहे हैं; CMake यह आपके लिए करता है।

यदि आप मल्टी‑कोर मशीनों पर गति बढ़ाना चाहते हैं, तो कमांड के बाद `-- -j$(nproc)` (Linux/macOS) या `-- /m` (Windows) जोड़ें:

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build -- -j$(nproc)
```

## चरण 3: विस्तृत आउटपुट के साथ उदाहरण टेस्ट चलाएँ

टेस्टिंग वह जगह है जहाँ असली काम होता है। CMake `ctest` के साथ आता है, एक टेस्ट ड्राइवर जो आपके `CMakeLists.txt` में `add_test()` द्वारा जोड़े गए किसी भी टेस्ट को खोज और चलाता है। टेस्ट चलाने और विस्तृत आउटपुट देखने के लिए, पहले `-E chdir` हेल्पर का उपयोग करके बिल्ड डायरेक्टरी में जाएँ:

```bash
cmake -E chdir YOUR_DIRECTORY/Examples/DocsExamples/build \
      ctest --verbose
```

**`--verbose` क्यों उपयोग करें?** यह प्रत्येक टेस्ट की कमांड लाइन, एग्ज़िट कोड, और टेस्ट द्वारा लिखा गया कोई भी आउटपुट प्रिंट करता है। यह *how to run CTest* सीखते समय आवश्यक है क्योंकि यह सीन में क्या हो रहा है, ठीक‑ठीक दिखाता है।

सामान्य आउटपुट इस प्रकार दिखता है:

```
Test project /path/to/DocsExamples/build
    Start 1: MyFirstTest
1/1 Test #1: MyFirstTest .......................   Passed    0.02 sec

100% tests passed, 0 tests failed
```

यदि कोई टेस्ट फेल हो जाता है, तो विस्तृत लॉग में फेल होने वाली कमांड और कोई भी एरर संदेश शामिल होंगे, जिससे डिबगिंग बहुत तेज़ हो जाती है।

## चरण 4: पूरे वर्कफ़्लो को ऑटोमेट करें (वैकल्पिक)

कई प्रोजेक्ट्स के लिए आप एक ही लाइन में कॉन्फ़िगर, बिल्ड और टेस्ट करने वाला कमांड चाहते हैं। आप इसे एक साधारण Bash (या PowerShell) स्क्रिप्ट से हासिल कर सकते हैं:

```bash
#!/usr/bin/env bash
SRC=YOUR_DIRECTORY/Examples/DocsExamples
BUILD=$SRC/build

# 1️⃣ Configure
cmake -S "$SRC" -B "$BUILD" -D CMAKE_BUILD_TYPE=Release

# 2️⃣ Build
cmake --build "$BUILD" -- -j$(nproc)

# 3️⃣ Test
cmake -E chdir "$BUILD" ctest --verbose
```

इसे `run_all.sh` के रूप में सेव करें, इसे executable बनाएं (`chmod +x run_all.sh`), और आपके पास एक पुनरुत्पादनीय **cmake build and test** पाइपलाइन होगी जिसे आप किसी भी CI सिस्टम (GitHub Actions, GitLab CI, Azure Pipelines, आदि) में डाल सकते हैं।

## किनारे के मामले और सामान्य जाल

| Situation | What to Watch For | Fix |
|-----------|-------------------|-----|
| **कम्पाइलर गायब** | CMake “No CMAKE_CXX_COMPILER could be found.” त्रुटि के साथ बंद हो जाता है। | एक कम्पाइलर इंस्टॉल करें (`sudo apt install build-essential` Ubuntu पर, `xcode-select --install` macOS पर)। |
| **Out‑of‑source फ़ोल्डर पहले से मौजूद** | यदि फ़ोल्डर में पुरानी फ़ाइलें हैं तो CMake पुनः कॉन्फ़िगर करने से इनकार कर सकता है। | `build` डायरेक्टरी हटाएँ (`rm -rf build`) या `cmake --fresh` चलाएँ (CMake 3.24+). |
| **CTest टेस्ट नहीं ढूँढ पा रहा है** | `add_test()` कभी कॉल नहीं किया गया या टेस्ट एग्जीक्यूटेबल कंपाइल नहीं हो सका। | पुष्टि करें कि `add_test(NAME MyTest COMMAND MyTestExe)` `CMakeLists.txt` में मौजूद है और टार्गेट बिल्ड होता है। |
| **कस्टम कमांड्स पर पैरेलल बिल्ड्स रेस** | कुछ कस्टम कमांड्स को `DEPENDS` के रूप में चिह्नित नहीं किया गया है, जिससे अनिश्चित विफलताएँ होती हैं। | उचित `add_custom_command(... DEPENDS ...)` एंट्रीज़ जोड़ें। |

इन बारीकियों को समझना एक अस्थिर बिल्ड और एक ठोस CI पाइपलाइन के बीच अंतर बनाता है।

## दृश्य अवलोकन (Alt टेक्स्ट में मुख्य कीवर्ड शामिल है)

![CMake प्रोजेक्ट को कॉन्फ़िगर, बिल्ड और टेस्ट करने के प्रवाह को दर्शाता आरेख](/images/cmake-workflow.png "CMake प्रोजेक्ट वर्कफ़्लो आरेख")

## पुनरावलोकन – आपने क्या सीखा

हमने मूल प्रश्न से शुरुआत की: *how to build CMake project* को शून्य से। अंत तक आप अब जानते हैं कि **configure CMake** को एक साफ़ out‑of‑source बिल्ड के साथ कैसे करें, **build CMake** को सार्वभौमिक `--build` फ़्लैग से कैसे चलाएँ, और **run CTest** को विस्तृत आउटपुट के साथ कैसे चलाएँ ताकि सब कुछ काम करे। आपके पास एक तैयार‑स्क्रिप्ट भी है जो तीनों चरणों को जोड़ती है, जिससे आपको एक पूर्ण **cmake build and test** वर्कफ़्लो मिलता है।

## आगे क्या?

- **कवरेज रिपोर्टिंग जोड़ें** – `gcov` या `llvm-cov` को इंटीग्रेट करें और CTest को परिणाम प्रकाशित करने दें।
- **क्रॉस‑कम्पाइलेशन** – एम्बेडेड डिवाइसों पर बिल्ड करने के लिए `-DCMAKE_TOOLCHAIN_FILE` का अन्वेषण करें।
- **पैकेज निर्माण** – वितरण के लिए अपने बाइनरी को बंडल करने हेतु `cpack` का उपयोग करें।
- **CI इंटीग्रेशन** – स्क्रिप्ट को GitHub Actions वर्कफ़्लो में कॉपी करें और हर पुल रिक्वेस्ट पर ऑटोमेशन चलते देखें।

विभिन्न बिल्ड प्रकारों के साथ प्रयोग करने, अधिक टेस्ट जोड़ने, या उदाहरण स्रोत को अपने प्रोजेक्ट से बदलने में संकोच न करें। आज हमने जिन पैटर्न को कवर किया, वे किसी भी CMake‑आधारित कोडबेस पर लागू होते हैं, चाहे वह एक छोटा यूटिलिटी हो या एक विशाल मल्टी‑मॉड्यूल सिस्टम।

बिल्डिंग का आनंद लें, और आपके CMake बिल्ड हमेशा पुनरुत्पादनीय रहें!

## आपको आगे क्या सीखना चाहिए?

निम्नलिखित ट्यूटोरियल्स उन निकट-संबंधित विषयों को कवर करते हैं जो इस गाइड में प्रदर्शित तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक कार्यान्वयन दृष्टिकोणों की खोज करने में मदद करती हैं।

- [Word से LaTeX निर्यात कैसे करें – चरण‑दर‑चरण गाइड](/words/english/net/basic-conversions/how-to-export-latex-from-word-step-by-step-guide/)
- [DOCX से Markdown सहेजें – चरण‑दर‑चरण गाइड](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [Python और .NET में Aspose.Words संस्करण कैसे दिखाएँ – एक चरण‑दर‑चरण गाइड](/words/english/python-net/document-properties-metadata/display-aspose-words-version-python-net/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}