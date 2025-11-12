---
date: '2025-11-12'
description: Aspose.Words का उपयोग करके जावा में नियंत्रण अक्षर डालना, कैरिज रिटर्न
  को प्रबंधित करना, और पृष्ठ या कॉलम ब्रेक जोड़ना सीखें, ताकि सटीक दस्तावेज़ स्वरूपण
  हो सके।
keywords:
- Aspose.Words control characters
- Java document formatting with Aspose.Words
- inserting control characters in Java
- insert control characters java
- manage carriage returns
- add page break aspose
- insert non‑breaking space
- create multi‑column layout
language: hi
title: Aspose.Words के साथ जावा में नियंत्रण अक्षर सम्मिलित करें
url: /java/advanced-text-processing/aspose-words-java-control-characters-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insert Control Characters in Java with Aspose.Words
## Introduction
क्या आपको इनवॉइस, रिपोर्ट या न्यूज़लेटर बनाते समय लाइन ब्रेक, टैब या पेज डिवीजन पर पिक्सेल‑परफेक्ट नियंत्रण चाहिए?  
Control characters वे अदृश्य बिल्डिंग ब्लॉक्स हैं जो आपको प्रोग्रामेटिक रूप से डॉक्यूमेंट लेआउट को आकार देने की अनुमति देते हैं।  
इस ट्यूटोरियल में आप सीखेंगे कि **insert**, **verify**, और **manage** कैसे करें ऐसे control characters जैसे carriage returns, non‑breaking spaces, और column breaks, Aspose.Words for Java API का उपयोग करके।

**आप क्या हासिल करेंगे:**
1. Carriage returns, line feeds, और page breaks को insert और validate करना।  
2. Spaces, tabs, non‑breaking spaces, और column breaks जोड़कर multi‑column लेआउट बनाना।  
3. बड़े‑पैमाने पर डॉक्यूमेंट ऑटोमेशन के लिए best‑practice performance टिप्स लागू करना।

## Prerequisites
शुरू करने से पहले सुनिश्चित करें कि आपके पास निम्नलिखित तैयार हैं:

| Requirement | Details |
|-------------|----------|
| **Aspose.Words for Java** | Version 25.3 या नया (API बाद के रिलीज़ में भी स्थिर रहता है)। |
| **JDK** | Java 8 + (Java 11 या 17 की सलाह दी जाती है)। |
| **IDE** | IntelliJ IDEA, Eclipse, या कोई भी Java‑compatible एडिटर। |
| **Build tool** | Maven **or** Gradle डिपेंडेंसी मैनेजमेंट के लिए। |
| **License** | एक अस्थायी या खरीदा हुआ Aspose.Words लाइसेंस फ़ाइल। |

### Quick Environment Checklist
1. Maven **or** Gradle इंस्टॉल हो।  
2. लाइसेंस फ़ाइल उपलब्ध हो (जैसे, `src/main/resources/aspose.words.lic`)।  
3. प्रोजेक्ट बिना त्रुटियों के कम्पाइल हो रहा हो।

## Setting Up Aspose.Words
पहले लाइब्रेरी को प्रोजेक्ट में जोड़ेंगे, फिर लाइसेंस लोड करेंगे। अपनी वर्कफ़्लो के अनुसार बिल्ड सिस्टम चुनें।

### Maven Dependency
`pom.xml` में `<dependencies>` के अंदर निम्न स्निपेट जोड़ें:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle Dependency
`build.gradle` के `dependencies` ब्लॉक में यह लाइन डालें:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### License Initialization (Java code)
```java
License license = new License();
license.setLicense("path/to/aspose.words.lic");
```

> **Note:** `"path/to/aspose.words.lic"` को अपनी लाइसेंस फ़ाइल के वास्तविक पाथ से बदलें।

## Feature 1: Handle Carriage Returns and Page Breaks
Carriage returns (`ControlChar.CR`) और page breaks (`ControlChar.PAGE_BREAK`) तब आवश्यक होते हैं जब आप चाहते हैं कि आउटपुट टेक्स्ट डॉक्यूमेंट के विज़ुअल लेआउट को दर्शाए।

### Step‑by‑Step Implementation
1. **एक नया Document और DocumentBuilder बनाएं।**  
2. **दो पैराग्राफ लिखें।**  
3. **जांचें कि जेनरेटेड टेक्स्ट में अपेक्षित control characters मौजूद हैं या नहीं।**  
4. **टेक्स्ट को trim करें और परिणाम फिर से चेक करें।**

#### 1. Create a Document
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

#### 2. Insert Paragraphs
```java
builder.writeln("Hello world!");
builder.writeln("Hello again!");
```

#### 3. Verify Control Characters
```java
String expectedTextWithCR = MessageFormat.format("Hello world!{0}", ControlChar.CR) +
        MessageFormat.format("Hello again!{0}", ControlChar.CR) +
        ControlChar.PAGE_BREAK;
assert doc.getText().equals(expectedTextWithCR) :
        "Text does not match expected value with control characters.";
```

#### 4. Trim and Check Text
```java
String expectedTrimmedText = MessageFormat.format("Hello world!{0}", ControlChar.CR) + "Hello again!";
assert doc.getText().trim().equals(expectedTrimmedText) :
        "Trimmed text does not match expected value.";
```

**Result:** `doc.getText()` स्ट्रिंग अब स्पष्ट CR और page‑break सिम्बॉल्स रखती है, जिससे डाउनस्ट्रीम सिस्टम (जैसे plain‑text exporters) लेआउट को बरकरार रखते हैं।

## Feature 2: Insert Various Control Characters
Carriage returns के अलावा, Aspose.Words spaces, tabs, line feeds, paragraph breaks, और column breaks के लिए भी कॉन्स्टेंट्स प्रदान करता है। इस सेक्शन में हम दिखाएंगे कि प्रत्येक को कैसे एम्बेड किया जाए।

### Step‑by‑Step Implementation
1. **एक नया DocumentBuilder इनिशियलाइज़ करें।**  
2. **space, non‑breaking space, और tab कैरेक्टर्स के उदाहरण लिखें।**  
3. **line feeds, paragraph breaks, और section breaks जोड़ें, फिर node काउंट वैलिडेट करें।**  
4. **दो‑कॉलम लेआउट बनाएं और column break डालें।**

#### 1. Initialize DocumentBuilder
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

#### 2. Insert Space‑Related Characters
- **Space (`ControlChar.SPACE_CHAR`)**
```java
builder.write("Before space." + ControlChar.SPACE_CHAR + "After space.");
```
- **Non‑Breaking Space (`ControlChar.NON_BREAKING_SPACE`)**
```java
builder.write("Before NBSP." + ControlChar.NON_BREAKING_SPACE + "After NBSP.");
```
- **Tab (`ControlChar.TAB`)**
```java
builder.write("Before tab." + ControlChar.TAB + "After tab.");
```

#### 3. Line, Paragraph, and Section Breaks
```java
// Verify initial paragraph count is 1
Assert.assertEquals(1, doc.getFirstSection().getBody()
        .getChildNodes(NodeType.PARAGRAPH, true).getCount());

// Insert a line feed (creates a new paragraph)
builder.write("Before line feed." + ControlChar.LINE_FEED + "After line feed.");
Assert.assertEquals(2, doc.getFirstSection().getBody()
        .getChildNodes(NodeType.PARAGRAPH, true).getCount());

// Insert a paragraph break
builder.write("Before paragraph break." + ControlChar.PARAGRAPH_BREAK + "After paragraph break.");
Assert.assertEquals(3, doc.getFirstSection().getBody()
        .getChildNodes(NodeType.PARAGRAPH, true).getCount());

// Insert a section break (still one Section object, but a break marker)
builder.write("Before section break." + ControlChar.SECTION_BREAK + "After section break.");
assert doc.getSections().getCount() == 1 :
        "Section count mismatch after section break.";
```

#### 4. Column Break in a Multi‑Column Layout
```java
// Add a second section to host two columns
doc.appendChild(new Section(doc));
builder.moveToSection(1);
builder.getCurrentSection().getPageSetup().getTextColumns().setCount(2);

// Insert a column break between the two columns
builder.write("Text at end of column 1." + ControlChar.COLUMN_BREAK + "Text at beginning of column 2.");
```

**Result:** अब डॉक्यूमेंट में एक दो‑कॉलम पेज है जहाँ `COLUMN_BREAK` के बाद टेक्स्ट स्वचालित रूप से पहले कॉलम से दूसरे कॉलम में प्रवाहित होता है।

## Practical Applications
| Scenario | How Control Characters Help |
|----------|-----------------------------|
| **Invoice Generation** | प्रत्येक इनवॉइस बैच के लिए नया पेज शुरू करने हेतु `PAGE_BREAK` का उपयोग करें। |
| **Financial Report** | आंकड़ों को `TAB` से अलाइन करें और हेडिंग्स को साथ रखने के लिए `NON_BREAKING_SPACE` रखें। |
| **Newsletter Layout** | मल्टी‑कॉलम सेक्शन में `COLUMN_BREAK` से साइड‑बाय‑साइड आर्टिकल्स बनाएं। |
| **CMS Content Export** | रिच टेक्स्ट को plain text में बदलते समय `LINE_FEED` से लाइन स्ट्रक्चर बरकरार रखें। |
| **Automated Templates** | यूज़र इनपुट के आधार पर डायनामिक रूप से `PARAGRAPH_BREAK` या `SECTION_BREAK` डालें। |

## Performance Considerations
* **Batch Inserts:** कई `write` कॉल्स को एक ही ऑपरेशन में ग्रुप करें ताकि इंटरनल रीफ़्लो कम हो।  
* **Avoid Frequent Node Traversal:** जब बार‑बार पैराग्राफ काउंट चाहिए तो `NodeCollection` रिजल्ट को कैश करें।  
* **Profile Large Docs:** Java प्रोफाइलर (जैसे VisualVM) का उपयोग करके टेक्स्ट मैनीपुलेशन लूप में हॉटस्पॉट्स पहचानें।

## Conclusion
अब आपके पास Java डॉक्यूमेंट्स में Aspose.Words का उपयोग करके **insert**, **validate**, और **optimize** करने की एक ठोस, स्टेप‑बाय‑स्टेप विधि है। ये तकनीकें आपको प्रोग्रामेटिक रूप से प्रोफेशनल‑ग्रेड इनवॉइस, रिपोर्ट, और मल्टी‑कॉलम पब्लिकेशन बनाने में सक्षम बनाती हैं।

## Next Steps
1. `EM_SPACE` या `EN_SPACE` जैसे अतिरिक्त `ControlChar` कॉन्स्टेंट्स के साथ प्रयोग करें।  
2. डायनामिक डॉक्यूमेंट जेनरेशन के लिए control characters को mail‑merge फ़ील्ड्स के साथ कॉम्बाइन करें।  
3. Aspose.Words की अन्य सुविधाओं जैसे **document protection**, **watermarks**, और **image insertion** को एक्सप्लोर करें ताकि आउटपुट और भी समृद्ध हो सके।

**Try it today:** ऊपर दिए गए स्निपेट्स को अपने अगले Java प्रोजेक्ट में जोड़ें और देखें कि सटीक control characters आपके डॉक्यूमेंट वर्कफ़्लो को कैसे आसान बनाते हैं!

## FAQ
1. **What is a control character?**  
   एक non‑printable सिंबल (जैसे tab, line feed) जो डॉक्यूमेंट लेआउट को प्रभावित करता है बिना दृश्यमान टेक्स्ट के रूप में दिखे।

2. **How do I start using Aspose.Words for Java?**  
   Maven या Gradle डिपेंडेंसी जोड़ें, लाइसेंस लोड करें, और इस गाइड में दिए गए कोड उदाहरणों का पालन करें।

3. **Can I use column breaks for newsletters?**  
   हाँ—`ControlChar.COLUMN_BREAK` `TextColumns` प्रॉपर्टी के साथ मिलकर कंटेंट को कॉलम्स में विभाजित करता है।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}