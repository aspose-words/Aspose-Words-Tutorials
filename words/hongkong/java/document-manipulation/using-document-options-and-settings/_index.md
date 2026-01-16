---
date: 2026-01-16
description: 學習如何在 Word 中使用 Aspose.Words for Java 標示拼寫錯誤，並了解如何設定每行字元數、客製化檢視選項以及清理樣式。
linktitle: Using Document Options and Settings
second_title: Aspose.Words Java Document Processing API
title: 使用 Aspose.Words Java 在 Word 中突顯拼寫錯誤
url: /zh-hant/java/document-manipulation/using-document-options-and-settings/
weight: 31
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中使用文件選項與設定

## 介紹在 Aspose.Words for Java 中使用文件選項與設定

在本完整指南中，您將學習 **如何在 Word 中標示拼寫錯誤**，同時掌握相關設定，如檢視選項、頁面佈局與樣式清理。無論您是資深開發者或剛入門，以下範例都能協助您建立具備錯誤偵測功能的穩健文件，且相容於各版本的 Word。

## 快速解答
- **如何在 Word 中標示拼寫錯誤？** 使用 `setShowSpellingErrors(true)` 於 `Document` 物件。  
- **我也能顯示文法錯誤嗎？** 可以——呼叫 `setShowGrammaticalErrors(true)`。  
- **哪個方法設定每行字元數？** `getPageSetup().setCharactersPerLine(int)`。  
- **哪個 API 可針對特定 Word 版本進行最佳化？** `doc.getCompatibilityOptions().optimizeFor(MsWordVersion)`。  
- **有沒有方式清除未使用的樣式？** 使用 `CleanupOptions` 並呼叫 `setUnusedStyles(true)`，再執行 `doc.cleanup(options)`。

## 如何在 Word 中標示拼寫錯誤？

Aspose.Words 讓開啟拼寫錯誤標示變得相當簡單。當文件在 Microsoft Word 中開啟時，拼寫錯誤的單字會出現熟悉的紅色底線，協助最終使用者即時發現問題。

## 如何設定每行字元數

控制每行的字元數對於固定寬度的版面（例如程式碼清單或舊式表單）相當重要。`PageSetup` 類別提供 `setCharactersPerLine(int)`，讓您精確定義此數值。

## 如何顯示文法錯誤

除了拼寫，您也可以啟用文法錯誤的顯示。這對於必須遵循寫作指南的內容草稿或建構校對工具相當有用。

## 為相容性最佳化文件

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.OptimizeForMsWord.docx");
```

文件管理的一個關鍵面向是確保與不同版本的 Microsoft Word 相容。Aspose.Words for Java 提供簡易方式，讓文件針對特定 Word 版本進行最佳化。上述範例將文件最佳化為 Word 2016，確保無縫相容。

## 辨識文法與拼寫錯誤

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

在處理文件時，準確性至關重要。Aspose.Words for Java 讓您在文件中標示文法與拼寫錯誤，提升校對與編輯效率。

## 清理未使用的樣式與清單

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

有效管理文件樣式與清單對於維持文件一致性必不可少。Aspose.Words for Java 允許您清除未使用的樣式與清單，確保文件結構精簡有序。

## 移除重複樣式

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

重複的樣式會導致文件混亂與不一致。使用 Aspose.Words for Java，您可以輕鬆移除重複樣式，維持文件的清晰與連貫。

## 自訂文件檢視選項

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

為文件打造合適的檢視體驗相當重要。Aspose.Words for Java 讓您設定各種檢視選項，如頁面佈局與縮放比例，提升文件可讀性。

## 設定文件頁面配置

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

精確的頁面配置對於文件排版至關重要。Aspose.Words for Java 讓您設定版面模式、**每行字元數** 與每頁行數，確保文件視覺上賞心悅目。

## 設定編輯語言

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

編輯語言在文件處理中扮演關鍵角色。使用 Aspose.Words for Java，您可以設定與自訂編輯語言，以符合文件的語言需求。

## 結論

在本指南中，我們深入探討了 Aspose.Words for Java 中各種文件選項與設定。從最佳化、錯誤顯示到樣式清理與檢視選項，這套功能強大的函式庫提供了廣泛的能力，協助您管理與自訂文件。

## 常見問題

### 如何為特定的 Word 版本最佳化文件？

使用 `optimizeFor` 方法並指定目標版本即可。例如，要最佳化為 Word 2016：

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "OptimizedForWord2016.docx");
```

### 如何在文件中標示文法與拼寫錯誤？

您可以使用以下程式碼啟用文法與拼寫錯誤的顯示：

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.setShowGrammaticalErrors(true);
doc.setShowSpellingErrors(true);
doc.save("Your Directory Path" + "ShowErrors.docx");
```

### 清理未使用的樣式與清單的目的為何？

清理未使用的樣式與清單有助於維持文件結構的整潔與有序。它會移除不必要的雜訊，提升文件的可讀性與一致性。

### 如何從文件中移除重複樣式？

使用 `cleanup` 方法，將 `duplicateStyle` 選項設為 `true` 即可。以下為範例：

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
CleanupOptions options = new CleanupOptions();
options.setDuplicateStyle(true);
doc.cleanup(options);
doc.save("Your Directory Path" + "CleanedDocument.docx");
```

### 如何自訂文件的檢視選項？

您可以使用 `ViewOptions` 類別自訂檢視選項。例如，將檢視類型設為頁面佈局並將縮放設定為 50%：

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
doc.getViewOptions().setZoomPercent(50);
doc.save("Your Directory Path" + "CustomView.docx");
```

## 其他提示與常見陷阱

- **同時啟用拼寫與文法檢查**，以獲得完整的校對功能。忘記設定其中一個旗標（`setShowGrammaticalErrors` 或 `setShowSpellingErrors`）可能會導致錯誤未被偵測。  
- **設定每行字元數時**，請留意該數值會與所選字型與頁邊距互動。務必以實際文件版面測試，以免出現意外的換行。  
- **清理操作在原始檔案上是不可逆的**。請務必在副本上執行或使用版本控制，以保留原始樣式。  
- **編輯語言偏好**會影響拼寫檢查行為。若您的文件需支援多語言，請將所有相關語言加入 `LanguagePreferences`。

---

**最後更新：** 2026-01-16  
**測試環境：** Aspose.Words for Java 24.12  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}