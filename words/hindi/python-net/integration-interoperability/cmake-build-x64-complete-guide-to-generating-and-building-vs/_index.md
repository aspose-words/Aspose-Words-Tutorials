---
category: general
date: 2026-07-16
description: cmake build x64 ट्यूटोरियल दिखाता है कि CMake का उपयोग करके Visual Studio
  2022 सॉल्यूशन कैसे जनरेट करें और 64‑बिट होस्ट पर VS प्रोजेक्ट कैसे बनाएं। इसमें
  स्रोत निर्देशिका सेट करने के चरण शामिल हैं।
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- cmake build x64
- cmake generate visual studio
- build vs project
- how to use cmake
- set source directory
language: hi
lastmod: 2026-07-16
og_description: 'cmake बिल्ड x64 समझाया गया: सीखें कैसे स्रोत निर्देशिका सेट करें,
  Visual Studio 2022 समाधान जनरेट करें, और 64‑बिट होस्ट पर VS प्रोजेक्ट को संकलित
  करें।'
og_image_alt: Diagram illustrating cmake build x64 workflow from source folder to
  VS2022 solution
og_title: cmake बिल्ड x64 – VS 2022 सॉल्यूशन्स को जेनरेट और बिल्ड करने के लिए चरण‑दर‑चरण
  गाइड
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: cmake build x64 tutorial shows how to use CMake to generate a Visual
    Studio 2022 solution and build a VS project on a 64‑bit host. Includes set source
    directory steps.
  headline: cmake build x64 – Complete Guide to Generating and Building VS 2022 Projects
  type: TechArticle
tags:
- cmake
- visual-studio
- x64
- build-automation
title: cmake बिल्ड x64 – VS 2022 प्रोजेक्ट्स को जेनरेट और बिल्ड करने की पूरी गाइड
url: /hi/python/integration-interoperability/cmake-build-x64-complete-guide-to-generating-and-building-vs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cmake build x64 – VS 2022 प्रोजेक्ट्स को जनरेट और बिल्ड करने की पूरी गाइड

क्या आप कभी सोचते रहे हैं **how to use CMake** को 64‑बिट Visual Studio सॉल्यूशन बनाने के लिए बिना सिर दर्द के? आप अकेले नहीं हैं। इस ट्यूटोरियल में हम एक **cmake build x64** वर्कफ़्लो को देखेंगे जो स्रोत डायरेक्टरी सेट करता है, Visual Studio 2022 के लिए जेनरेटर चलाता है, और अंत में VS प्रोजेक्ट को बिल्ड करता है—सभी कुछ साफ़ Bash कमांड्स के साथ।

गाइड के अंत तक आपके पास एक पुनरुत्पादक स्क्रिप्ट होगी जिसे आप किसी भी रिपॉज़िटरी में डाल सकते हैं, साथ ही मूल अवधारणाओं की ठोस समझ होगी जिससे आप इसे अपनी ज़रूरतों के अनुसार बदल सकेंगे।

---

## आप क्या सीखेंगे

- **Set source directory** को सही तरीके से सेट करें ताकि CMake को पता चले कि आपका `CMakeLists.txt` कहाँ है।  
- **cmake generate visual studio** – सही होस्ट और आर्किटेक्चर फ़्लैग्स के साथ Visual Studio 2022 जेनरेटर को कॉल करें।  
- जनरेटेड सॉल्यूशन का **cmake build x64** करें, वैकल्पिक रूप से Release कॉन्फ़िगरेशन चुनें।  
- जब आप 64‑बिट मशीन पर **build vs project** करने की कोशिश करते हैं तो आम समस्याओं को समझें।  

पहले से कोई CMake जादू नहीं चाहिए; बस एक टर्मिनल और एक नवीनतम Visual Studio इंस्टॉलेशन।

## आवश्यकताएँ

| Requirement | Why it matters |
|-------------|----------------|
| CMake ≥ 3.20 | 64‑बिट बिल्ड्स के लिए उपयोग किए जाने वाले `-Thost=` और `-Ax64` फ़्लैग्स को सपोर्ट करता है। |
| Visual Studio 2022 (Community, Professional, or Enterprise) | `Visual Studio 17 2022` जेनरेटर इस संस्करण की ओर इशारा करता है। |
| A Bash‑compatible shell (Git Bash, WSL, PowerShell with `bash` alias) | नीचे दिया गया स्क्रिप्ट स्पष्टता के लिए Bash सिंटैक्स का उपयोग करता है। |
| Source tree containing a valid `CMakeLists.txt` | CMake बिना इसके सॉल्यूशन जनरेट नहीं कर सकता। |

यदि इनमें से कोई भी अनुपलब्ध है, तो पहले उन्हें इंस्टॉल करें—CMake <https://cmake.org/download/> से और VS 2022 माइक्रोसॉफ्ट इंस्टॉलर से।

## चरण 1 – स्रोत और बिल्ड डायरेक्टरी सेट करें (`set source directory`)

CMake को कॉल करने से पहले आपको उसे बताना होगा कि प्रोजेक्ट फ़ाइलें **कहाँ** हैं। पाथ को हार्ड‑कोड करने से स्क्रिप्ट नाज़ुक बन जाती है, इसलिए हम पर्यावरण वेरिएबल्स का उपयोग करेंगे जिन्हें आप प्रोजेक्ट के अनुसार समायोजित कर सकते हैं।

```bash
# Define where your source lives and where the generated files will be placed
SRC_DIR="YOUR_DIRECTORY/Examples/DocsExamples"
BUILD_DIR="${SRC_DIR}/build"
```

> **यह क्यों महत्वपूर्ण है:**  
> CMake *source directory* (`SRC_DIR`) को प्रोजेक्ट की रूट मानता है। *build directory* (`BUILD_DIR`) वह जगह है जहाँ सभी मध्यवर्ती फ़ाइलें, कैश, और अंतिम `.sln` रहती हैं। इन्हें अलग रखने से आपके स्रोत ट्री को गंदा होने से बचाया जाता है और सफ़ाई आसान हो जाती है (`rm -rf "$BUILD_DIR"`).

`YOUR_DIRECTORY` को किसी भी absolute या relative पाथ से बदल सकते हैं; बस यह सुनिश्चित करें कि फ़ोल्डर में `CMakeLists.txt` मौजूद हो।

## चरण 2 – Visual Studio 2022 सॉल्यूशन जनरेट करें (`cmake generate visual studio`)

अब हम CMake को कहते हैं कि वह एक VS 2022 सॉल्यूशन बनाए जो **x64** को टार्गेट करे। मुख्य फ़्लैग्स हैं:

- `-G "Visual Studio 17 2022"` – VS 2022 जेनरेटर को चुनता है।  
- `-Thost=x64` – CMake को बताता है कि *host* (IDE) 64‑बिट प्रोसेस के रूप में चल रहा है।  
- `-Ax64` – जनरेटेड प्रोजेक्ट को x64 आर्किटेक्चर के लिए बिल्ड करने के लिए मजबूर करता है।

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
```

> **आंतरिक रूप से क्या होता है?**  
> CMake `$SRC_DIR` से `CMakeLists.txt` पढ़ता है, सभी `add_executable()` और `add_library()` कॉल्स को हल करता है, फिर `$BUILD_DIR` के अंदर एक `.sln` फ़ाइल और कई `.vcxproj` फ़ाइलें बनाता है। ये प्रोजेक्ट फ़ाइलें अब Visual Studio में खोलने या कमांड लाइन से बिल्ड करने के लिए तैयार हैं।

यदि आप कमांड चलाते हैं और `-- Configuring done` और `-- Generating done` के साथ समाप्त होने वाले कॉन्फ़िगरेशन संदेशों की लंबी सूची देखते हैं, तो आपने सफलतापूर्वक **cmake generate visual studio** चरण पूरा कर लिया है।

## चरण 3 – जनरेटेड सॉल्यूशन बिल्ड करें (`cmake build x64`)

सॉल्यूशन तैयार होने के बाद, अगला तर्कसंगत कदम इसे कंपाइल करना है। CMake आपके लिए बिल्ड चलाता है, पीछे से MSBuild को डेलीगेट करता है।

```bash
cmake --build "$BUILD_DIR" --config Release
```

> **`--config Release` क्यों उपयोग करें?**  
> Visual Studio प्रोजेक्ट्स कई कॉन्फ़िगरेशन (Debug, Release, RelWithDebInfo, आदि) को सपोर्ट करते हैं। `Release` निर्दिष्ट करने से बाइनरीज़ प्रोडक्शन के लिए ऑप्टिमाइज़ हो जाती हैं और परिणामी `.exe` या `.dll` बिल्ड ट्री के अंदर `Release/` में रहती है।

यदि आप Debug बिल्ड पसंद करते हैं, तो `Release` को `Debug` से बदल दें। कमांड वही काम करता है, यह प्रमाणित करता है कि विभिन्न कॉन्फ़िगरेशन के लिए **how to use CMake** केवल इस फ़्लैग को बदलने की बात है।

## चरण 4 – बिल्ड की पुष्टि करें (`build vs project` sanity check)

एक सफल कंपाइलेशन के बाद आपके पास एक executable या लाइब्रेरी होनी चाहिए। चलिए पुष्टि करते हैं कि यह मौजूद है:

```bash
# Example for an executable named MyApp.exe
if [[ -f "$BUILD_DIR/Release/MyApp.exe" ]]; then
  echo "✅ Build succeeded! Executable ready at $BUILD_DIR/Release/MyApp.exe"
else
  echo "❌ Build failed or executable not found."
fi
```

> **सामान्य समस्याएँ:**  
> - `CMakeLists.txt` बदलने के बाद जेनरेटर चरण चलाना भूल जाना इस जांच को विफल कर देगा।  
> - 32‑बिट और 64‑बिट टूलचेन को मिलाने से लिंकर एरर हो सकते हैं; हमेशा `-Ax64` को सुसंगत रखें।  
> - यदि आप “MSB3073” एरर देखते हैं, तो आमतौर पर इसका मतलब है कि पोस्ट‑बिल्ड स्टेप (जैसे रिसोर्स कॉपी करना) विफल हुआ—आउटपुट में संकेत देखें।

## चरण 5 – साफ़ करें और पुनः चलाएँ (`cmake build x64` पर इटरेट करना)

डेवलपमेंट के दौरान अक्सर आपको स्क्रैच से रीबिल्ड करना पड़ता है। सबसे साफ़ तरीका है बिल्ड फ़ोल्डर को डिलीट करके फिर से शुरू करना:

```bash
rm -rf "$BUILD_DIR"
mkdir "$BUILD_DIR"
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
cmake --build "$BUILD_DIR" --config Release
```

> **टिप:**  
> जेनरेटर कमांड में `-DCMAKE_BUILD_TYPE=Release` जोड़ना Visual Studio जैसे मल्टी‑कॉन्फ़िग जेनरेटर के लिए वैकल्पिक है, लेकिन Ninja जैसे सिंगल‑कॉन्फ़िग जेनरेटर पर स्विच करते समय यह उपयोगी हो सकता है।

## चरण 6 – स्क्रिप्ट का विस्तार (उन्नत `cmake generate visual studio` परिदृश्य)

अगर आपका प्रोजेक्ट सब‑डायरेक्टरी में है, या आपको कस्टम डिफ़िनिशन पास करने की ज़रूरत है? CMake आपको `-D` आर्ग्युमेंट्स के साथ यह करने देता है:

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 \
      -S "$SRC_DIR" -B "$BUILD_DIR" \
      -DMyFeature_ENABLED=ON -DCMAKE_INSTALL_PREFIX="/opt/myapp"
```

अब जनरेटेड VS सॉल्यूशन में `MyFeature_ENABLED` मैक्रो परिभाषित होगा, और इंस्टॉल टार्गेट फ़ाइलें `/opt/myapp` के तहत रखेगा। यह **how to use CMake** की लचीलापन को बुनियादी तीन‑स्टेप फ्लो से आगे दिखाता है।

## अपेक्षित आउटपुट

जब आप पूरी स्क्रिप्ट को शुरू से अंत तक चलाते हैं, तो टर्मिनल में कुछ इस तरह दिखना चाहिए:

```
-- The C compiler identification is MSVC 19.35.31107.0
-- The CXX compiler identification is MSVC 19.35.31107.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
...
-- Configuring done
-- Generating done
-- Build files have been written to: /path/to/Examples/DocsExamples/build
...
[ 50%] Building CXX object CMakeFiles/MyApp.dir/main.cpp.obj
[100%] Linking CXX executable Release/MyApp.exe
✅ Build succeeded! Executable ready at /path/to/Examples/DocsExamples/build/Release/MyApp.exe
```

यदि कुछ भी गड़बड़ हो, तो CMake ऐसी एरर मैसेज देगा जो `CMakeLists.txt` में समस्या वाली लाइन या गायब SDK कंपोनेंट्स की ओर इशारा करेंगे—तेज़ डिबगिंग के लिए एकदम उपयुक्त।

## निष्कर्ष

हमने **cmake build x64** करने के लिए आवश्यक सभी चीज़ें कवर कर ली हैं: स्रोत डायरेक्टरी सेट करना, **cmake generate visual studio** चरण को कॉल करना, परिणामी **build vs project** को कंपाइल करना, और आउटपुट की पुष्टि करना। स्क्रिप्ट कॉम्पैक्ट, पोर्टेबल, और CI पाइपलाइन या लोकल डेवलपमेंट वर्कफ़्लो में इंटीग्रेशन के लिए तैयार है।

अगले कदम में आप खोज सकते हैं:

- `ctest` के साथ यूनिट‑टेस्ट एक्ज़ीक्यूशन जोड़ना।  
- तेज़ इन्क्रिमेंटल बिल्ड्स के लिए Ninja जेनरेटर पर स्विच करना (`-G Ninja`)।  
- `CMakePresets.json` का उपयोग करके उन फ़्लैग्स को स्टोर करना जो हमने अभी टाइप किए।

बिना हिचकिचाए प्रयोग करें, चीज़ें तोड़ें, और फिर रीबिल्ड करें—आख़िरकार, यही CMake को प्रभावी ढंग से सीखने का सबसे तेज़ तरीका है। खुशहाल बिल्डिंग!

## आगे आप क्या सीखें?

निम्नलिखित ट्यूटोरियल्स उन विषयों को कवर करते हैं जो इस गाइड में दिखाए गए तकनीकों पर आधारित हैं। प्रत्येक संसाधन में पूर्ण कार्यशील कोड उदाहरण और चरण‑दर‑चरण व्याख्याएँ शामिल हैं, जो आपको अतिरिक्त API फीचर्स में महारत हासिल करने और अपने प्रोजेक्ट्स में वैकल्पिक इम्प्लीमेंटेशन एप्रोच को एक्सप्लोर करने में मदद करेंगे।

- [टेबल बनाएं](/words/hindi/net/add-content-using-documentbuilder/build-table/)
- [स्टाइल के साथ टेबल बनाएं](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-style/)
- [बॉर्डर्स के साथ टेबल बनाएं](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-borders/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}