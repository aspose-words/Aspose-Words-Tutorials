---
date: '2025-11-12'
description: Aspose.Words for Java के LayoutCollector और LayoutEnumerator का उपयोग
  करके पेज स्पैन निर्धारित करना, लेआउट एंटिटीज़ को ट्रैवर्स करना, और निरंतर सेक्शनों
  में पेज नंबरिंग को रीस्टार्ट करना सीखें।
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
- determine page span
- analyze document pagination
- restart page numbering
language: hi
title: 'Aspose.Words Java: LayoutCollector और LayoutEnumerator गाइड'
url: /java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java: LayoutCollector & LayoutEnumerator मार्गदर्शिका

## Introduction  

क्या आप जटिल Java दस्तावेज़ों में **पेज स्पैन निर्धारित करने**, पेजिनेशन का विश्लेषण करने, या पेज नंबरिंग को रीस्टार्ट करने में संघर्ष कर रहे हैं? **Aspose.Words for Java** के साथ, आप `LayoutCollector` और `LayoutEnumerator` का उपयोग करके इन समस्याओं को जल्दी हल कर सकते हैं। इस मार्गदर्शिका में हम आपको दिखाएंगे **LayoutCollector का उपयोग कैसे करें**, **LayoutEnumerator को कैसे ट्रैवर्स करें**, और निरंतर सेक्शन में पेज नंबरिंग को कैसे नियंत्रित करें—सभी स्पष्ट, चरण‑दर‑चरण कोड के साथ जिसे आप आज ही चला सकते हैं।

आप सीखेंगे:

1. किसी भी नोड का **पेज स्पैन निर्धारित करने** के लिए `LayoutCollector` का उपयोग।  
2. `LayoutEnumerator` के साथ **लेआउट एंटिटीज़ को ट्रैवर्स** करना।  
3. डायनामिक रेंडरिंग के लिए लेआउट कॉलबैक लागू करना।  
4. निरंतर सेक्शन में **पेज नंबरिंग रीस्टार्ट** करना।  

आइए शुरू करें और सुनिश्चित करें कि आपका वातावरण तैयार है।

## Prerequisites  

### Required Libraries  

> **Note:** The code works with the latest Aspose.Words for Java release (no version number needed).  

**Maven**

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>latest</version>
</dependency>
```

**Gradle**

```gradle
implementation 'com.aspose:aspose-words:latest'
```

### Environment  

- JDK 17 या नया।  
- IntelliJ IDEA, Eclipse, या कोई भी पसंदीदा Java IDE।  

### Knowledge  

Java सिंटैक्स और ऑब्जेक्ट‑ओरिएंटेड अवधारणाओं की बुनियादी परिचितता आपको उदाहरणों को समझने में मदद करेगी।

## Setting Up Aspose.Words  

सबसे पहले, अपने प्रोजेक्ट में Aspose.Words लाइब्रेरी जोड़ें और लाइसेंस लागू करें (या ट्रायल उपयोग करें)। नीचे दिया गया स्निपेट लाइसेंस लोड करने और लाइब्रेरी तैयार होने की पुष्टि दिखाता है:

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Load your license file (skip this line for a trial)
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

> **Tip:** लाइसेंस फ़ाइल को संस्करण नियंत्रण के बाहर रखें ताकि आपके क्रेडेंशियल सुरक्षित रहें।

अब हम दो मुख्य फीचर्स में डुबकी लगाते हैं।

## 1. How to Use LayoutCollector for Page‑Span Analysis  

`LayoutCollector` आपको दस्तावेज़ में किसी भी नोड के लिए **पेज स्पैन निर्धारित करने** की सुविधा देता है, जो पेजिनेशन विश्लेषण के लिए आवश्यक है।

### Step‑by‑Step Implementation  

1. **एक नया Document और LayoutCollector इंस्टेंस बनाएं।**  
2. **ऐसी सामग्री जोड़ें जो कई पृष्ठों में फैले।**  
3. **लेआउट रीफ़्रेश करें और पेज‑स्पैन मेट्रिक्स क्वेरी करें।**  

```java
// 1. Initialize Document and LayoutCollector
Document doc = new Document();
LayoutCollector layoutCollector = new LayoutCollector(doc);

// 2. Populate the Document with multi‑page content
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);

// 3. Update layout and retrieve page‑span information
layoutCollector.clear();          // Reset any previous state
doc.updatePageLayout();           // Force layout calculation

int pagesSpanned = layoutCollector.getNumPagesSpanned(doc);
assert pagesSpanned == 5;         // Expected number of pages
System.out.println("Document spans " + pagesSpanned + " pages.");
```

**Explanation**

- `DocumentBuilder` टेक्स्ट और ब्रेक्स डालता है, जिससे एक ऐसा दस्तावेज़ बनता है जो स्वाभाविक रूप से कई पृष्ठों में फैला होता है।  
- `updatePageLayout()` Aspose.Words को लेआउट गणना करने के लिए मजबूर करता है, जिससे सटीक पेज नंबर मिलते हैं।  
- `getNumPagesSpanned()` प्रदान किए गए नोड द्वारा कवर किए गए कुल पृष्ठों की संख्या लौटाता है (यहाँ पूरे दस्तावेज़ के लिए)।

## 2. How to Traverse LayoutEnumerator  

`LayoutEnumerator` **लेआउट एंटिटीज़ का संरचित दृश्य** (पेज, पैराग्राफ, रन आदि) प्रदान करता है और आपको उन्हें आगे‑या‑पीछे नेविगेट करने देता है।

### Step‑by‑Step Implementation  

1. ऐसी मौजूदा दस्तावेज़ लोड करें जिसमें लेआउट एंटिटीज़ हों।  
2. एक `LayoutEnumerator` इंस्टेंस बनाएं।  
3. पेज लेवल पर जाएँ, फिर हेल्पर मेथड्स का उपयोग करके आगे और पीछे ट्रैवर्स करें।

```java
// 1. Load the document containing layout entities
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");

// 2. Initialize LayoutEnumerator
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);

// 3. Position the enumerator at the page level
layoutEnumerator.moveParent(LayoutEntityType.PAGE);

// Forward traversal
traverseLayoutForward(layoutEnumerator, 1);

// Backward traversal
traverseLayoutBackward(layoutEnumerator, 1);
```

> **Note:** `traverseLayoutForward` और `traverseLayoutBackward` मेथड्स रीकर्सिव हेल्पर हैं जो लेआउट ट्री को चलाते हैं। आप इन्हें बाउंडिंग बॉक्स, फ़ॉन्ट विवरण, या कस्टम मेटाडेटा जैसी जानकारी एकत्र करने के लिए कस्टमाइज़ कर सकते हैं।

## 3. How to Implement Page‑Layout Callbacks  

कभी‑कभी आपको लेआउट इवेंट्स पर प्रतिक्रिया देनी होती है—जैसे जब कोई सेक्शन रीफ़्लो समाप्त करता है या जब किसी अन्य फ़ॉर्मेट में कन्वर्ज़न पूरा हो जाता है। `IPageLayoutCallback` इंटरफ़ेस को इम्प्लीमेंट करके आप ये नोटिफ़िकेशन प्राप्त कर सकते हैं।

### Step‑by‑Step Implementation  

1. दस्तावेज़ की लेआउट ऑप्शन्स पर एक कॉलबैक इंस्टेंस सेट करें।  
2. `PART_REFLOW_FINISHED` और `CONVERSION_FINISHED` इवेंट्स को हैंडल करने के लिए कॉलबैक लॉजिक परिभ