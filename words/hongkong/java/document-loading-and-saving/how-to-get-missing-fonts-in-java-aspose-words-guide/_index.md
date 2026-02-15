---
category: general
date: 2026-02-15
description: 學習如何在 Java 中使用 Aspose.Words 載入 Word 文件時取得缺失的字型。包括警告回呼和字型替換處理。
draft: false
keywords:
- how to get missing fonts
- Aspose.Words missing font
- font substitution warning
- Java LoadOptions warning callback
- document processing Java
language: zh-hant
og_description: 如何在 Java 中使用 Aspose.Words 獲取缺失字型。了解警告回調、字型替換處理以及文件處理的最佳實踐。
og_title: 如何在 Java 中取得缺失字型 – Aspose.Words 指南
tags:
- Aspose.Words
- Java
- Font Management
title: 如何在 Java 中取得缺失字型 – Aspose.Words 指南
url: /zh-hant/java/document-loading-and-saving/how-to-get-missing-fonts-in-java-aspose-words-guide/
---

Be careful with bold formatting and code formatting.

Proceed.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Java 中獲取缺失字體 – Aspose.Words 指南

是否曾在 Java 中打開 Word 文件，卻看到奇怪的字體替換，並想知道 **如何獲取缺失字體**？你不是第一個遇到這種情況的人。在許多企業應用程式中，缺失字體警告會破壞報告、合約或行銷資料的視覺完整性。

好消息是？Aspose.Words 為你提供了一個乾淨的方式，透過回呼捕捉這些警告，讓你可以在文件渲染前記錄、替換，甚至提醒使用者。在本教學中，我們將逐步示範一個完整、可執行的範例，說明 **如何獲取缺失字體**、解釋回呼的重要性，並涵蓋在實務專案中可能需要的幾個邊緣案例技巧。

> **專業提示：** 若你已使用 Aspose.Words 22.12 或更新版本，以下 API 可直接使用，無需額外設定。

![說明如何使用 Aspose.Words 警告回呼取得缺失字體的圖示](how-to-get-missing-fonts-diagram.png "取得缺失字體圖示")

## 本教學涵蓋內容

- 設定 **Java LoadOptions warning callback** 以捕捉字體替換警告。  
- 篩選警告，只保留與缺失字體相關的項目。  
- 輸出清晰、易讀的報告，說明哪些字體被替換以及替換成什麼。  
- 處理大型文件的技巧、客製化警告等級，以及將此解決方案整合到更大的處理流程中。

完成本指南後，你將能以可直接執行的程式碼片段回答「**如何獲取缺失字體**？」這個問題，並對其背後機制有扎實的了解。

### 前置條件

- 已安裝 Java 8 或更新版本。  
- Aspose.Words for Java 套件（可從官方網站下載或透過 Maven/Gradle 加入）。  
- 一個引用了本機未安裝字體的 Word 文件（例如 `MissingFont.docx`）。  

若缺少上述任一項，請立即取得套件——將它加入 Maven 如下即可：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version> <!-- replace with the latest version -->
</dependency>
```

## Step 1: Prepare a Collection for Font‑Substitution Warnings

在載入文件之前，我們需要一個地方來儲存 Aspose.Words 所拋出的任何警告。`ArrayList<WarningInfo>` 非常適合，因為它能保留順序，且之後可以輕鬆遍歷。

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

// Step 1: Create a list that will hold warning information.
List<WarningInfo> fontWarnings = new ArrayList<>();
```

*Why this matters:* 警告回呼在單一檔案上可能會被觸發數十次——每個缺失的字形、每個嵌入圖像問題等皆會產生警告。先收集起來再處理，可保持載入階段的效能，並在受控的迴圈中完成後續工作。

## Step 2: Configure LoadOptions with a Warning Callback

Aspose.Words 允許你插入一個 `IWarningCallback`。在回呼內，我們會把 Step 1 中的 `WarningInfo` 全部加入清單。

```java
// Step 2: Set up LoadOptions with a custom warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Capture every warning; we'll filter later.
        fontWarnings.add(info);
    }
});
```

*Explanation:* `warning` 方法會在文件載入期間 **同步** 被呼叫。只要把 `WarningInfo` 推入 `fontWarnings`，即可避免可能拖慢載入速度的重 I/O（例如寫檔）。此「收集‑再‑處理」模式是處理大量警告的推薦做法。

## Step 3: Load the Document Using the Configured Options

現在正式讀取 Word 檔案。若文件內含未安裝的字體，Aspose.Words 會自動替換並觸發先前設定好的警告回呼。

```java
// Step 3: Load the document with the warning‑aware LoadOptions.
String filePath = "YOUR_DIRECTORY/MissingFont.docx"; // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

*What happens under the hood?* Aspose.Words 會解析檔案的字體表，與主機作業系統上可用的字體進行比對，對每個缺失的條目產生 `WarningInfo`，其 `WarningSource` 為 `FontSubstitution`。我們稍後將以此來源篩選出缺失字體的警告。

## Step 4: Filter and Display Only Font‑Substitution Warnings

載入完成後，`fontWarnings` 可能混雜了多種訊息（例如已棄用功能、圖像問題）。我們只關心缺失字體，於是遍歷清單並印出簡潔報告。

```java
// Step 4: Output any font‑substitution warnings that were captured.
for (WarningInfo warning : fontWarnings) {
    if (warning.getSource() == WarningSource.FontSubstitution) {
        System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                           warning.getAdditionalInfo() + "'");
    }
}
```

**Sample output**

```
Substituted 'Comic Sans MS' with 'Arial'
Substituted 'Times New Roman PS' with 'Times New Roman'
```

*Why this is useful:* `description` 欄位告訴你文件原本要求的字體名稱，`additionalInfo` 則說明 Aspose.Words 最終使用了哪個字體。取得這些資訊後，你可以：

- 提示使用者安裝缺失的字體。  
- 程式化地將替代字體嵌入文件 (`doc.getFontInfos().add(...)`)。  
- 為合規稽核記錄此事件。

## Handling Edge Cases and Common Variations

### 1. Suppressing Non‑Font Warnings

若只想保留與字體相關的訊息，可在回呼中進一步過濾：

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        fontWarnings.add(info);
    }
});
```

這樣在處理巨量批次時可減少記憶體佔用。

### 2. Adjusting Warning Severity

Aspose.Words 會依 `WarningType` 分類警告。缺失字體通常會出現 `WarningType.FontSubstitution`。若希望將其視為錯誤（例如中止載入），可在回呼內拋出例外：

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        throw new RuntimeException("Missing font detected: " + info.getDescription());
    }
});
```

### 3. Working with Streams Instead of Files

有時文件是從資料庫或 HTTP 請求取得的。相同的做法同樣適用於 `InputStream`：

```java
InputStream docStream = new ByteArrayInputStream(bytesFromDb);
Document doc = new Document(docStream, loadOptions);
```

只需在載入完畢後記得關閉串流。

### 4. Using a Custom Font Folder

若公司有一套共用字體庫，請將 Aspose.Words 指向該資料夾：

```java
loadOptions.setFontSettings(new FontSettings());
loadOptions.getFontSettings().setFontsFolder("C:/CorporateFonts", true);
```

如此一來，程式會先在此資料夾搜尋字體，然後才回退至系統字體，能大幅降低缺失字體警告的數量。

## Full Working Example

將上述所有步驟整合起來，以下是一個可直接放入任何 Java 專案的自包含類別：

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

public class MissingFontDetector {

    public static void main(String[] args) {
        // 1️⃣ Prepare a collection for warnings.
        List<WarningInfo> fontWarnings = new ArrayList<>();

        // 2️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(info -> fontWarnings.add(info));

        // (Optional) Point to a custom font folder.
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.setFontsFolder("C:/CorporateFonts", true);
        // loadOptions.setFontSettings(fontSettings);

        // 3️⃣ Load the document.
        String docPath = "YOUR_DIRECTORY/MissingFont.docx";
        Document doc;
        try {
            doc = new Document(docPath, loadOptions);
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            return;
        }

        // 4️⃣ Print missing‑font warnings.
        System.out.println("=== Missing Font Report ===");
        for (WarningInfo warning : fontWarnings) {
            if (warning.getSource() == WarningSource.FontSubstitution) {
                System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                                   warning.getAdditionalInfo() + "'");
            }
        }
        System.out.println("=== End of Report ===");
    }
}
```

執行此程式，即可看到 Aspose.Words 必須替換的每一個字體的整潔清單。無需額外套件、無隱藏魔法——只有純粹的 Java 與 **Aspose.Words missing font** API 的威力。

## Conclusion

我們已在 Java 環境中使用 Aspose.Words 解答了核心問題 **如何獲取缺失字體**。透過在 `LoadOptions` 中掛載警告回呼、收集 `WarningInfo` 物件，並以 `FontSubstitution` 為來源篩選，你可以在任何渲染發生前完整掌握字體相關問題。此方法可從單一檔案工具擴展至大規模批次處理，且彈性足以支援自訂字體資料夾、嚴重度處理或串流輸入。

接下來的步驟？嘗試將替代字體直接嵌入文件 (`doc.getFontInfos().add(...)`) 使最終檔案真正自包含，或將警告報告整合至監控儀表板。你也可以進一步探索 **document processing Java**、**Aspose.Words font substitution warning**、**Java LoadOptions warning callback** 等相關主題，深化專業知識。

祝程式開發順利，願你的文件永遠以預期的字體正確呈現！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}