---
"description": "了解如何在 Aspose.Words for Java 中儲存具有固定佈局的 HTML 文件。按照我們的逐步指南進行操作，實現無縫文件格式化。"
"linktitle": "儲存具有固定佈局的 HTML 文檔"
"second_title": "Aspose.Words Java文件處理API"
"title": "在 Aspose.Words for Java 中儲存具有固定佈局的 HTML 文檔"
"url": "/zh-hant/java/document-loading-and-saving/saving-html-documents-with-fixed-layout/"
"weight": 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中儲存具有固定佈局的 HTML 文檔


## Aspose.Words for Java 中固定版面配置 HTML 文件保存簡介

在本綜合指南中，我們將引導您完成使用 Aspose.Words for Java 儲存具有固定佈局的 HTML 文件的過程。透過逐步說明和程式碼範例，您將學習如何無縫地實現這一點。那麼，就讓我們開始吧！

## 先決條件

在開始之前，請確保您已滿足以下先決條件：

- Java開發環境搭建。
- Aspose.Words for Java 程式庫已安裝並配置。

## 步驟 1：載入文檔

首先，我們需要載入我們想要以 HTML 格式儲存的文件。您可以按照以下步驟操作：

```java
Document doc = new Document("Your Directory Path" + "YourDocument.docx");
```

代替 `"YourDocument.docx"` 以及您的 Word 文件的路徑。

## 步驟 2：設定 HTML 固定保存選項

要以固定佈局儲存文檔，我們需要配置 `HtmlFixedSaveOptions` 班級。我們將設定 `useTargetMachineFonts` 財產 `true` 確保在 HTML 輸出中使用目標機器的字型：

```java
HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions();
saveOptions.setUseTargetMachineFonts(true);
```

## 步驟 3：將文件儲存為 HTML

現在，讓我們使用先前配置的選項將文件儲存為具有固定佈局的 HTML：

```java
doc.save("Your Directory Path" + "FixedLayoutDocument.html", saveOptions);
```

代替 `"FixedLayoutDocument.html"` 使用您所需的 HTML 檔案名稱。

## 在 Aspose.Words for Java 中儲存固定佈局 HTML 文件的完整原始碼

```java
        Document doc = new Document("Your Directory Path" + "Bullet points with alternative font.docx");
        HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions();
        {
            saveOptions.setUseTargetMachineFonts(true);
        }
        doc.save("Your Directory Path" + "WorkingWithHtmlFixedSaveOptions.UseFontFromTargetMachine.html", saveOptions);
    }
```

## 結論

在本教學中，我們學習如何使用 Aspose.Words for Java 儲存具有固定佈局的 HTML 文件。透過遵循這些簡單的步驟，您可以確保您的文件在不同平台上保持一致的視覺結構。

## 常見問題解答

### 如何在我的專案中設定 Aspose.Words for Java？

為 Java 設定 Aspose.Words 非常簡單。您可以從 [這裡](https://releases.aspose.com/words/java/) 並按照文件中提供的安裝說明進行操作 [這裡](https://reference。aspose.com/words/java/).

### 使用 Aspose.Words for Java 有任何授權要求嗎？

是的，Aspose.Words for Java 需要有效的授權才能在生產環境中使用。您可以從 Aspose 網站取得許可證。更多詳細資訊請參閱文件。

### 我可以進一步自訂 HTML 輸出嗎？

當然！ Aspose.Words for Java 提供了多種選項來客製化 HTML 輸出以滿足您的特定要求。您可以瀏覽文件以獲取有關自訂選項的詳細資訊。

### Aspose.Words for Java 是否與不同 Java 版本相容？

是的，Aspose.Words for Java 與各種版本的 Java 相容。確保您使用的 Aspose.Words for Java 相容版本與您的 Java 開發環境相符。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}