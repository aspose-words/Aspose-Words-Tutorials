---
date: 2026-01-16
description: Aspose.Words for Java का उपयोग करके Word में वर्तनी त्रुटियों को हाइलाइट
  करना सीखें, और प्रति पंक्ति अक्षर सेट करना, दृश्य विकल्पों को अनुकूलित करना, तथा
  शैलियों को साफ़ करना कैसे करें, यह जानें।
linktitle: Using Document Options and Settings
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words Java के साथ Word में वर्तनी त्रुटियों को हाइलाइट करें
url: /hi/java/document-manipulation/using-document-options-and-settings/
weight: 31
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java में दस्तावेज़ विकल्प और सेटिंग्स का उपयोग

## Aspose.Words for Java में दस्तावेज़ विकल्प और सेटिंग्स के उपयोग का परिचय

इस व्यापक गाइड में, आप Aspose.Words for Java का उपयोग करके **Word में वर्तनी त्रुटियों को हाइलाइट करने** का तरीका सीखेंगे, साथ ही व्यूइंग विकल्प, पेज लेआउट, और स्टाइल क्लीनअप जैसी संबंधित सेटिंग्स में निपुणता प्राप्त करेंगे। चाहे आप एक अनुभवी डेवलपर हों या अभी शुरुआत कर रहे हों, नीचे दिए गए उदाहरण आपको मजबूत, त्रुटि‑सजग दस्तावेज़ बनाने में मदद करेंगे जो विभिन्न Word संस्करणों में काम करेंगे।

## त्वरित उत्तर
- **मैं Word में वर्तनी त्रुटियों को कैसे हाइलाइट कर सकता हूँ?** `Document` ऑब्जेक्ट पर `setShowSpellingErrors(true)` का उपयोग करें।  
- **क्या मैं व्याकरणिक त्रुटियों को भी दिखा सकता हूँ?** हाँ—`setShowGrammaticalErrors(true)` को कॉल करें।  
- **लाइन प्रति अक्षर सेट करने की विधि कौन सी है?** `getPageSetup().setCharactersPerLine(int)`।  
- **कौन सा API विशिष्ट Word संस्करण के लिए ऑप्टिमाइज़ करता है?** `doc.getCompatibilityOptions().optimizeFor(MsWordVersion)`।  
- **क्या अनउपयोगी स्टाइल्स को साफ़ करने का कोई तरीका है?** `CleanupOptions` के साथ `setUnusedStyles(true)` का उपयोग करें और `doc.cleanup(options)` को कॉल करें।

## Word में वर्तनी त्रुटियों को हाइलाइट कैसे करें?

Aspose.Words वर्तनी‑त्रुटि हाइलाइटिंग को सक्षम करना आसान बनाता है। जब दस्तावेज़ Microsoft Word में खोला जाता है, तो गलत लिखे शब्द परिचित लाल रेखा के साथ दिखते हैं, जिससे अंतिम उपयोगकर्ता तुरंत समस्याओं को पहचान सकते हैं।

## लाइन प्रति अक्षर कैसे सेट करें

लाइन प्रति अक्षर की संख्या को नियंत्रित करना निश्चित‑चौड़ाई वाले लेआउट (जैसे कोड लिस्टिंग या पुरानी फ़ॉर्म) के लिए आवश्यक है। `PageSetup` क्लास `setCharactersPerLine(int)` प्रदान करती है जो आपको इस मान को सटीक रूप से निर्धारित करने देती है।

## व्याकरणिक त्रुटियों को कैसे दिखाएँ

वर्तनी के अलावा, आप व्याकरणिक‑त्रुटि प्रदर्शन को भी सक्षम कर सकते हैं। यह उन सामग्री के मसौदे के लिए उपयोगी है जिन्हें शैली गाइड का पालन करना होता है या प्रूफ़रीडिंग टूल बनाने के लिए।

## संगतता के लिए दस्तावेज़ों का ऑप्टिमाइज़ेशन

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.OptimizeForMsWord.docx");
```

दस्तावेज़ प्रबंधन का एक प्रमुख पहलू विभिन्न Microsoft Word संस्करणों के साथ संगतता सुनिश्चित करना है। Aspose.Words for Java विशिष्ट Word संस्करणों के लिए दस्तावेज़ों को ऑप्टिमाइज़ करने का सरल तरीका प्रदान करता है। ऊपर के उदाहरण में, हम एक दस्तावेज़ को Word 2016 के लिए ऑप्टिमाइज़ करते हैं, जिससे सहज संगतता सुनिश्चित होती है।

## व्याकरणिक और वर्तनी त्रुटियों की पहचान

```java
@Test
public void showGrammaticalAndSpellingErrors() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    doc.setShowGrammaticalErrors(true);
    doc.setShowSpellingErrors(true);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ShowGrammaticalAndSpellingErrors.docx");
}
```

दस्तावेज़ों के साथ काम करते समय सटीकता अत्यंत महत्वपूर्ण है। Aspose.Words for Java आपको आपके दस्तावेज़ों में व्याकरणिक और वर्तनी त्रुटियों को हाइलाइट करने की सुविधा देता है, जिससे प्रूफ़रीडिंग और संपादन अधिक कुशल बनता है।

## अनउपयोगी स्टाइल्स और सूचियों को साफ़ करना

```java
@Test
public void cleanupUnusedStylesAndLists() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Unused styles.docx");
    // Define cleanup options
    CleanupOptions cleanupOptions = new CleanupOptions();
    cleanupOptions.setUnusedLists(false);
    cleanupOptions.setUnusedStyles(true);
    doc.cleanup(cleanupOptions);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupUnusedStylesAndLists.docx");
}
```

दस्तावेज़ स्टाइल्स और सूचियों का कुशल प्रबंधन दस्तावेज़ की स्थिरता बनाए रखने के लिए आवश्यक है। Aspose.Words for Java आपको अनउपयोगी स्टाइल्स और सूचियों को साफ़ करने की अनुमति देता है, जिससे एक सुव्यवस्थित और संगठित दस्तावेज़ संरचना सुनिश्चित होती है।

## डुप्लिकेट स्टाइल्स को हटाना

```java
@Test
public void cleanupDuplicateStyle() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Clean duplicate styles
    CleanupOptions options = new CleanupOptions();
    options.setDuplicateStyle(true);
    doc.cleanup(options);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupDuplicateStyle.docx");
}
```

डुप्लिकेट स्टाइल्स आपके दस्तावेज़ों में भ्रम और असंगतता पैदा कर सकते हैं। Aspose.Words for Java के साथ, आप आसानी से डुप्लिकेट स्टाइल्स को हटा सकते हैं, जिससे दस्तावेज़ की स्पष्टता और संगति बनी रहती है।

## दस्तावेज़ व्यूइंग विकल्पों को अनुकूलित करना

```java
@Test
public void viewOptions() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Customize viewing options
    doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
    doc.getViewOptions().setZoomPercent(50);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ViewOptions.docx");
}
```

अपने दस्तावेज़ों के व्यूइंग अनुभव को अनुकूलित करना महत्वपूर्ण है। Aspose.Words for Java आपको विभिन्न व्यूइंग विकल्प सेट करने की अनुमति देता है, जैसे पेज लेआउट और ज़ूम प्रतिशत, जिससे दस्तावेज़ की पठनीयता बढ़ती है।

## दस्तावेज़ पेज सेटअप को कॉन्फ़िगर करना

```java
@Test
public void documentPageSetup() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Configure page setup options
    doc.getFirstSection().getPageSetup().setLayoutMode(SectionLayoutMode.GRID);
    doc.getFirstSection().getPageSetup().setCharactersPerLine(30);
    doc.getFirstSection().getPageSetup().setLinesPerPage(10);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.DocumentPageSetup.docx");
}
```

सटीक पेज सेटअप दस्तावेज़ फ़ॉर्मेटिंग के लिए आवश्यक है। Aspose.Words for Java आपको लेआउट मोड, **लाइन प्रति अक्षर**, और पेज प्रति पंक्तियों को सेट करने की शक्ति देता है, जिससे आपके दस्तावेज़ दृश्यात्मक रूप से आकर्षक बनते हैं।

## संपादन भाषाओं को सेट करना

```java
@Test
public void addJapaneseAsEditingLanguages() throws Exception
{
    LoadOptions loadOptions = new LoadOptions();
    // Set language preferences for editing
    loadOptions.getLanguagePreferences().addEditingLanguage(EditingLanguage.JAPANESE);
    Document doc = new Document("Your Directory Path" + "No default editing language.docx", loadOptions);
    // Check the overridden editing language
    int localeIdFarEast = doc.getStyles().getDefaultFont().getLocaleIdFarEast();
    System.out.println(localeIdFarEast == (int) EditingLanguage.JAPANESE
            ? "The document either has no any FarEast language set in defaults or it was set to Japanese originally."
            : "The document default FarEast language was set to another than Japanese language originally, so it is not overridden.");
}
```

संपादन भाषाएँ दस्तावेज़ प्रसंस्करण में महत्वपूर्ण भूमिका निभाती हैं। Aspose.Words for Java के साथ, आप अपने दस्तावेज़ की भाषाई आवश्यकताओं के अनुसार संपादन भाषाओं को सेट और अनुकूलित कर सकते हैं।

## निष्कर्ष

इस गाइड में, हमने Aspose.Words for Java में उपलब्ध विभिन्न दस्तावेज़ विकल्पों और सेटिंग्स को विस्तृत रूप से समझा। ऑप्टिमाइज़ेशन और त्रुटि प्रदर्शन से लेकर स्टाइल क्लीनअप और व्यूइंग विकल्पों तक, यह शक्तिशाली लाइब्रेरी आपके दस्तावेज़ों को प्रबंधित और अनुकूलित करने के लिए व्यापक क्षमताएँ प्रदान करती है।

## अक्सर पूछे जाने वाले प्रश्न

### मैं किसी विशिष्ट Word संस्करण के लिए दस्तावेज़ को कैसे ऑप्टिमाइज़ करूँ?

किसी विशिष्ट Word संस्करण के लिए दस्तावेज़ को ऑप्टिमाइज़ करने के लिए, `optimizeFor` मेथड का उपयोग करें और इच्छित संस्करण निर्दिष्ट करें। उदाहरण के लिए, Word 2016 के लिए ऑप्टिमाइज़ करने हेतु:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "OptimizedForWord2016.docx");
```

### मैं दस्तावेज़ में व्याकरणिक और वर्तनी त्रुटियों को कैसे हाइलाइट करूँ?

आप निम्नलिखित कोड का उपयोग करके दस्तावेज़ में व्याकरणिक और वर्तनी त्रुटियों को प्रदर्शित करने को सक्षम कर सकते हैं:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.setShowGrammaticalErrors(true);
doc.setShowSpellingErrors(true);
doc.save("Your Directory Path" + "ShowErrors.docx");
```

### अनउपयोगी स्टाइल्स और सूचियों को साफ़ करने का उद्देश्य क्या है?

अनउपयोगी स्टाइल्स और सूचियों को साफ़ करने से एक साफ़ और व्यवस्थित दस्तावेज़ संरचना बनाए रखने में मदद मिलती है। यह अनावश्यक अव्यवस्था को हटाता है, जिससे दस्तावेज़ की पठनीयता और स्थिरता में सुधार होता है।

### मैं दस्तावेज़ से डुप्लिकेट स्टाइल्स को कैसे हटा सकता हूँ?

दस्तावेज़ से डुप्लिकेट स्टाइल्स को हटाने के लिए, `duplicateStyle` विकल्प को `true` सेट करके `cleanup` मेथड का उपयोग करें। यहाँ एक उदाहरण है:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
CleanupOptions options = new CleanupOptions();
options.setDuplicateStyle(true);
doc.cleanup(options);
doc.save("Your Directory Path" + "CleanedDocument.docx");
```

### मैं दस्तावेज़ के व्यूइंग विकल्पों को कैसे अनुकूलित करूँ?

आप `ViewOptions` क्लास का उपयोग करके दस्तावेज़ के व्यूइंग विकल्पों को अनुकूलित कर सकते हैं। उदाहरण के लिए, व्यू टाइप को पेज लेआउट पर सेट करने और ज़ूम को 50% करने के लिए:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
doc.getViewOptions().setZoomPercent(50);
doc.save("Your Directory Path" + "CustomView.docx");
```

## अतिरिक्त टिप्स और सामान्य गलतियाँ

- **वर्तनी और व्याकरण दोनों जांचें** को सक्षम करें जब आपको व्यापक प्रूफ़रीडिंग की आवश्यकता हो। इन फ़्लैग्स में से किसी एक को भूलने (`setShowGrammaticalErrors` या `setShowSpellingErrors`) से त्रुटियाँ अनदेखी रह सकती हैं।
- **लाइन प्रति अक्षर सेट करते समय**, याद रखें कि यह मान चयनित फ़ॉन्ट और पेज मार्जिन के साथ इंटरैक्ट करता है। अप्रत्याशित लाइन ब्रेक से बचने के लिए वास्तविक दस्तावेज़ लेआउट के साथ परीक्षण करें।
- **क्लीनअप ऑपरेशन्स मूल फ़ाइल पर अपरिवर्तनीय होते हैं**। हमेशा एक कॉपी पर काम करें या मूल स्टाइलिंग को संरक्षित रखने के लिए संस्करण नियंत्रण का उपयोग करें।
- **संपादन भाषा प्राथमिकताएँ** स्पेल‑चेक व्यवहार को प्रभावित करती हैं। यदि आप बहुभाषी दस्तावेज़ों को लक्षित कर रहे हैं, तो सभी संबंधित भाषाओं को `LanguagePreferences` में जोड़ें।

---

**अंतिम अपडेट:** 2026-01-16  
**परीक्षित संस्करण:** Aspose.Words for Java 24.12  
**लेखक:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}