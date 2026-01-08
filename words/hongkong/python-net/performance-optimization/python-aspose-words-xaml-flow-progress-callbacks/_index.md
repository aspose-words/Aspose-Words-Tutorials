---
"date": "2025-03-29"
"description": "了解如何使用 XAML 流格式和進度回調優化 Aspose.Words for Python 的文件保存。提高文件管理效率。"
"title": "優化 Python 中的文件保存&#58; Aspose.Words XAML 流程和進度回調"
"url": "/zh-hant/python-net/performance-optimization/python-aspose-words-xaml-flow-progress-callbacks/"
"weight": 1
---
{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}
# 如何使用 Aspose.Words 優化 Python 中的文件保存：XAML 流程和進度回調

## 介紹

您是否希望使用 Python 有效地管理文件轉換？在處理影像和追蹤文件保存過程中的進度時遇到困難嗎？本教學將指導您使用 Aspose.Words for Python 優化文件保存，重點介紹兩個強大的功能： `XamlFlowSaveOptions` 帶有圖像資料夾和文件保存進度回調。

本綜合指南非常適合希望使用 Aspose.Words 函式庫來增強其文件處理工作流程的開發人員。

**您將學到什麼：**
- 如何在管理映像資源的同時以 XAML 流格式儲存文件。
- 在文件保存期間實現進度回調以防止長時間操作。
- 在您的開發環境中設定和設定 Aspose.Words for Python。
- 這些功能在文件管理系統中的實際應用。

在開始編碼之前，讓我們深入了解先決條件！

## 先決條件

在開始之前，請確保您已具備以下條件：

### 所需的庫和版本
- **Aspose.Words for Python**：確保您擁有 23.3 或更高版本。
- **Python**：建議使用 3.6 或更高版本。

### 環境設定要求
- 像 VSCode 或 PyCharm 這樣的程式碼編輯器。
- Python 程式設計的基礎知識。

### 知識前提
- 熟悉文件處理概念。
- 了解 Python 中的檔案處理和目錄管理。

## 為 Python 設定 Aspose.Words

要開始使用 Aspose.Words，您需要透過 pip 安裝它。打開終端機或命令提示字元並運行：

```bash
pip install aspose-words
```

### 許可證取得步驟
1. **免費試用**：取得臨時許可證 [這裡](https://purchase.aspose.com/temporary-license/) 用於測試目的。
2. **購買**：如需長期使用，請購買許可證 [這裡](https://purchase。aspose.com/buy).
3. **基本初始化和設定**：
   - 使用載入文檔 `aw。Document()`.
   - 根據需要配置儲存選項。

## 實施指南

本節將引導您實現本教學的兩個主要功能：具有映像資料夾的 XamlFlowSaveOptions 和文件保存進度回調。

### 功能 1：帶有影像資料夾的 XamlFlowSaveOptions

#### 概述
此功能可讓您在指定映像資料夾和別名的同時以 XAML 流格式儲存文件。它非常適合高效管理嵌入影像的大型文件。

#### 實施步驟

##### 步驟 1：導入必要的函式庫
```python
import os
from datetime import datetime
import aspose.words as aw
```

##### 步驟2：定義ImageUriPrinter回呼類
此類在轉換期間會對影像流進行計數並將其重定向到指定的別名資料夾。

```python
class ExXamlFlowSaveOptionsImageFolder:
    class ImageUriPrinter(aw.saving.IImageSavingCallback):
        """Counts and prints filenames of images while their parent document is converted to flow-form .xaml."""
        
        def __init__(self, images_folder_alias: str):
            self.images_folder_alias = images_folder_alias
            self.resources = []  # 類型：List[str]

        def image_saving(self, args: aw.saving.ImageSavingArgs):
            self.resources.append(args.image_file_name)
            with open(f"{self.images_folder_alias}/{args.image_file_name}", "wb") as image_stream:
                args.image_stream = image_stream
            args.keep_image_stream_open = False

    def test_image_folder(self):
        YOUR_DOCUMENT_DIRECTORY = 'YOUR_DOCUMENT_DIRECTORY'
        YOUR_OUTPUT_DIRECTORY = 'YOUR_OUTPUT_DIRECTORY'

        doc = aw.Document(f"{YOUR_DOCUMENT_DIRECTORY}/Rendering.docx")
        callback = self.ImageUriPrinter(YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolderAlias")

        options = aw.saving.XamlFlowSaveOptions()
        options.images_folder = YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolder"
        options.images_folder_alias = YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolderAlias"
        options.image_saving_callback = callback

        os.makedirs(options.images_folder_alias, exist_ok=True)
        
        doc.save(f"{YOUR_OUTPUT_DIRECTORY}/XamlFlowSaveOptions.image_folder.xaml", options)

        for resource in callback.resources:
            print(f"{callback.images_folder_alias}/{resource}")
```
**關鍵配置選項：**
- `images_folder`：指定圖片保存的目錄。
- `images_folder_alias`：設定文檔轉換時使用的別名路徑。

##### 故障排除提示
- 確保在運行程式碼之前所有目錄都存在，以避免檔案未找到錯誤。
- 檢查輸出目錄中的寫入權限。

### 功能二：文件保存進度回調

#### 概述
此功能透過使用進度回調來管理保存流程，讓您取消長時間運行的儲存操作。

#### 實施步驟

##### 步驟 1：定義 SavingProgressCallback 類
該類監控文件保存時間，如果超過指定的時間限制則取消。

```python
class ExXamlFlowSaveOptionsProgressCallback:
    class SavingProgressCallback(aw.saving.IDocumentSavingCallback):
        """Saving progress callback. Cancel document saving after the 'max_duration' seconds."""
        
        def __init__(self):
            self.saving_started_at = datetime.now()
            self.max_duration = 0.01  # 允許的最大持續時間（秒）。

        def notify(self, args: aw.saving.DocumentSavingArgs):
            canceled_at = datetime.now()
            elapsed_seconds = (canceled_at - self.saving_started_at).total_seconds()
            if elapsed_seconds > self.max_duration:
                raise OperationCanceledException(f"estimated_progress = {args.estimated_progress}; canceled_at = {canceled_at}")

    def test_progress_callback(self):
        YOUR_DOCUMENT_DIRECTORY = 'YOUR_DOCUMENT_DIRECTORY'
        YOUR_OUTPUT_DIRECTORY = 'YOUR_OUTPUT_DIRECTORY'

        parameters = [
            (aw.SaveFormat.XAML_FLOW, "xamlflow"),
            (aw.SaveFormat.XAML_FLOW_PACK, "xamlflowpack"),
        ]

        for save_format, ext in parameters:
            doc = aw.Document(f"{YOUR_DOCUMENT_DIRECTORY}/Big document.docx")
            save_options = aw.saving.XamlFlowSaveOptions(save_format)
            save_options.progress_callback = self.SavingProgressCallback()

            try:
                doc.save(f"{YOUR_OUTPUT_DIRECTORY}/XamlFlowSaveOptions.progress_callback.{ext}", save_options)
            except OperationCanceledException as e:
                print(e)
```
**關鍵配置選項：**
- `save_format`：在 XAML_FLOW 和 XAML_FLOW_PACK 之間進行選擇。
- `progress_callback`：監控保存進度以處理長時間操作。

##### 故障排除提示
- 調整 `max_duration` 根據文件的大小和複雜性。
- 妥善處理異常以提供資訊豐富的錯誤訊息。

## 實際應用

以下是這些功能的一些實際用例：
1. **文件管理系統**：透過指定影像資料夾有效管理嵌入影像的大型文檔，提高效能和組織性。
2. **自動報告工具**：使用進度回調確保報告在可接受的時間範圍內生成，從而改善使用者體驗。
3. **內容傳遞網絡**：簡化文件轉換以便在網路上分發，同時有效管理資源。

## 性能考慮

為了優化使用 Aspose.Words 與 Python 時的效能：
- **記憶體管理**：監控資源使用情況並透過在使用後處置物件來有效管理記憶體。
- **文件 I/O 操作**：盡量減少文件讀取/寫入操作以提高速度。
- **批次處理**：盡可能分批處理文件以減少開銷。

## 結論

在本教學中，我們探討如何使用 XAML Flow 和進度回呼優化 Aspose.Words for Python 的文件保存。透過實現這些功能，您可以提高文件處理工作流程的效率，有效地管理資源並確保及時操作。
{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}