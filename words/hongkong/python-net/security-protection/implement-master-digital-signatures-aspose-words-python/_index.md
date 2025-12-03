---
"date": "2025-03-29"
"description": "Aspose.Words Python-net 程式碼教學"
"title": "使用 Aspose.Words for Python 掌握數位簽名"
"url": "/zh-hant/python-net/security-protection/implement-master-digital-signatures-aspose-words-python/"
"weight": 1
---
{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}
# 如何使用 Aspose.Words for Python 在文件中實現主數位簽名

## 介紹

在當今數位時代，確保文件的真實性和完整性至關重要。無論您是管理合約的商業專業人士還是保護個人記錄的個人，數位簽名都是為您的文件提供安全性和可信度的重要工具。和 **Aspose.Words for Python**，將數位簽章功能整合到您的工作流程中變得無縫且有效率。

在本教學中，我們將探討如何使用 Python 中的 Aspose.Words 載入、刪除和簽署文件。您將輕鬆了解處理數位簽章的來龍去脈。

**您將學到什麼：**
- 從文件加載現有的數位簽名
- 從文件中刪除數位簽名
- 使用 X.509 憑證對文件進行數位簽名
- 安全地簽署加密文檔
- 應用 XML-DSig 標準進行簽名

讓我們深入設定您的環境並開始掌握 Python 中的數位簽章。

## 先決條件

在開始之前，請確保您已準備好以下先決條件：

- **Python 環境**：您的系統上安裝了 Python 3.x。
- **Aspose.Words for Python**：透過 pip 安裝：
  ```bash
  pip install aspose-words
  ```
- **執照**：考慮取得臨時許可證或購買許可證以解鎖全部功能。訪問 [Aspose 許可證購買](https://purchase.aspose.com/buy) 了解更多詳情。

此外，熟悉使用 Python 和處理文件也會很有幫助。

## 為 Python 設定 Aspose.Words

### 安裝

首先使用 pip 安裝 Aspose.Words 函式庫：

```bash
pip install aspose-words
```

### 許可證獲取

若要解鎖所有功能，請取得許可證。你可以從 [免費試用](https://releases.aspose.com/words/python/) 或購買許可證以獲得更長的使用期限。

#### 基本初始化

安裝並取得授權後，您可以在 Python 腳本中初始化 Aspose.Words：

```python
import aspose.words as aw

# 如果可用，請申請許可證
license = aw.License()
license.set_license('path_to_your_license.lic')
```

## 實施指南

我們將逐步分解每個功能，以幫助您了解如何有效地實施數位簽章。

### 從文件載入數位簽章（H2）

**概述**：此功能可讓您提取和檢視文件中嵌入的數位簽名，以確保其真實性。

#### 使用檔案路徑載入數位簽章（H3）

以下是從文件加載簽名的方法：

```python
import aspose.words as aw

def load_signatures_from_file(file_path):
    """
    Loads digital signatures from the specified document.
    """
    digital_signatures = aw.digitalsignatures.DigitalSignatureUtil.load_signatures(file_name=file_path)
    return digital_signatures

# 範例用法
signatures = load_signatures_from_file('path_to_your_document.docx')
print(signatures)
```

**解釋**：函數 `load_signatures_from_file` 從指定的文件中讀取數位簽名 `file_path`。它使用 Aspose.Words 實用程式來檢索和顯示這些簽章。

#### 使用串流加載數位簽章（H3）

對於在記憶體中處理文件的場景，請使用文件流：

```python
import aspose.words as aw
from io import BytesIO

def load_signatures_from_stream(stream):
    """
    Loads digital signatures from the provided stream.
    """
    with aw.FileStream(stream, aw.FileMode.OPEN) as fs_stream:
        digital_signatures = aw.digitalsignatures.DigitalSignatureUtil.load_signatures(stream=fs_stream)
    return digital_signatures

# 範例用法
stream = BytesIO(b'Your document content')
signatures = load_signatures_from_stream(stream)
print(signatures)
```

**解釋**：這種方法使用 `BytesIO` 流來讀取和處理文件的簽名，這對於處理記憶體資料的應用程式很有用。

### 從文件中刪除數位簽章 (H2)

**概述**：更新或重新授權文件時可能需要刪除數位簽章。 Aspose.Words 讓這個過程變得簡單。

#### 依檔案名稱刪除簽章 (H3)

以下是從文件中刪除所有簽名的程式碼：

```python
import aspose.words as aw

def remove_signatures_by_filename(src_file_name, dst_file_name):
    """
    Removes digital signatures and saves an unsigned copy.
    """
    aw.digitalsignatures.DigitalSignatureUtil.remove_all_signatures(
        src_file_name=src_file_name,
        dst_file_name=dst_file_name
    )

# 範例用法
remove_signatures_by_filename('source.docx', 'unsigned_document.docx')
```

**解釋**：此功能會取得簽名文件的路徑並刪除所有嵌入的簽名，並依照指定方式儲存未簽名的版本。

#### 按流刪除簽名（H3）

處理記憶體中的文件：

```python
import aspose.words as aw
from io import BytesIO

def remove_signatures_by_stream(src_stream, dst_stream):
    """
    Removes digital signatures from the document streams.
    """
    with aw.FileStream(src_stream, aw.FileMode.OPEN) as fs_src_stream:
        with aw.FileStream(dst_stream, aw.FileMode.CREATE) as fs_dst_stream:
            aw.digitalsignatures.DigitalSignatureUtil.remove_all_signatures(
                src_stream=fs_src_stream,
                dst_stream=fs_dst_stream
            )

# 範例用法
src = BytesIO(b'Signed document content')
dst = BytesIO()
remove_signatures_by_stream(src, dst)
```

**解釋**：此功能與文件流配合使用，直接從記憶體文件中刪除數位簽章。

### 簽署文件 (H2)

簽署文件可以保證其真實性。我們將探討如何對常規文件和加密文件進行數位簽章。

#### 對常規文件進行數位簽章（H3）

```python
import aspose.words as aw
from io import BytesIO
import datetime

def sign_document(src_file_name, dst_file_name, pfx_file_name, pfx_password):
    """
    Signs the document using an X.509 certificate.
    """
    certificate_holder = aw.digitalsignatures.CertificateHolder.create(
        file_name=pfx_file_name,
        password=pfx_password
    )
    
    sign_options = aw.digitalsignatures.SignOptions()
    sign_options.comments = 'My comment'
    sign_options.sign_time = datetime.datetime.now()

    with aw.FileStream(src_file_name, aw.FileMode.OPEN) as stream_in:
        with aw.FileStream(dst_file_name, aw.FileMode.OPEN_OR_CREATE) as stream_out:
            aw.digitalsignatures.DigitalSignatureUtil.sign(
                src_stream=stream_in,
                dst_stream=stream_out,
                cert_holder=certificate_holder,
                sign_options=sign_options
            )

# 範例用法
sign_document('document.docx', 'signed_document.docx', 'morzal.pfx', 'aw')
```

**解釋**：此功能使用 X.509 憑證對文件進行簽名，並添加時間戳記和可選註釋以便更清晰地理解。

#### 對加密文件進行數位簽章（H3）

對於加密文檔：

```python
import aspose.words as aw
from io import BytesIO
import datetime

def sign_encrypted_document(src_file_name, dst_file_name, pfx_file_name, pfx_password, doc_password):
    """
    Signs an encrypted document with a certificate.
    """
    certificate_holder = aw.digitalsignatures.CertificateHolder.create(
        file_name=pfx_file_name,
        password=pfx_password
    )
    
    doc = aw.Document(src_file_name, load_options=aw.loading.LoadOptions(password=doc_password))
    
    sign_options = aw.digitalsignatures.SignOptions()
    sign_options.comments = 'Comment'
    sign_options.sign_time = datetime.datetime.now()
    sign_options.decryption_password = doc_password

    aw.digitalsignatures.DigitalSignatureUtil.sign(
        src_file_name=doc.original_file_name,
        dst_file_name=dst_file_name,
        cert_holder=certificate_holder,
        sign_options=sign_options
    )

# 範例用法
sign_encrypted_document('encrypted.docx', 'signed_encrypted.docx', 'morzal.pfx', 'aw', 'password')
```

**解釋**：此功能可對加密文件進行簽章前解密處理，確保整個流程的安全處理。

### 使用 XML-DSig (H2) 簽署文檔

**概述**：遵守 XML-DSig 標準為簽署數位文件提供了標準化的方法，增強了互通性和合規性。

```python
import aspose.words as aw
from io import BytesIO
import datetime

def sign_with_xml_dsig(src_file_name, dst_file_name, pfx_file_name, pfx_password):
    """
    Signs the document using XML-DSig standards.
    """
    certificate_holder = aw.digitalsignatures.CertificateHolder.create(
        file_name=pfx_file_name,
        password=pfx_password
    )
    
    sign_options = aw.digitalsignatures.SignOptions()
    sign_options.comments = 'XML-DSig signed'
    sign_options.sign_time = datetime.datetime.now()

    with aw.FileStream(src_file_name, aw.FileMode.OPEN) as stream_in:
        with aw.FileStream(dst_file_name, aw.FileMode.OPEN_OR_CREATE) as stream_out:
            aw.digitalsignatures.DigitalSignatureUtil.sign(
                src_stream=stream_in,
                dst_stream=stream_out,
                cert_holder=certificate_holder,
                sign_options=sign_options
            )

# 範例用法
sign_with_xml_dsig('document.docx', 'xml_signed_document.docx', 'morzal.pfx', 'aw')
```

**解釋**：此功能依照 XML-DSig 標準對文件進行簽名，確保其符合數位簽章的產業合規性。

## 實際應用

使用 Aspose.Words 掌握數位簽章可以帶來無數的可能性：

1. **合約管理**：在法律環境下自動簽署和驗證合約。
2. **文件安全**：在共享之前對敏感文件進行數位簽名，以增強安全性。
3. **遵守**：確保遵守金融領域文件真實性的監管標準。

## 性能考慮

使用 Aspose.Words 時，請考慮以下提示以獲得最佳效能：

- 透過按順序（而不是同時）處理大量文件來優化記憶體使用情況。
- 利用高效的文件流處理來最大限度地減少 I/O 開銷。
- 定期更新您的庫以受益於最新的效能改進和錯誤修復。

## 結論

現在，您應該對如何使用 Aspose.Words 在 Python 中實現數位簽章有了深入的了解。從載入和刪除簽名到安全地簽署文件，這些工具使您能夠輕鬆地維護文件的完整性。

接下來，考慮探索更高級的功能或將這些功能整合到需要強大文件處理功能的大型應用程式中。

## 常見問題部分

**問題1：我可以免費使用Aspose.Words嗎？**
A1：是的， [免費試用](https://releases.aspose.com/words/python/) 可用。為了延長使用時間，您需要購買許可證。

**問題 2：數位簽章時如何處理大型文件？**
A2：透過以更小的區塊進行處理或使用高效的流處理技術來有效地管理內存，從而進行最佳化。

**Q3：XML-DSig 標準有什麼好處？**
A3：XML-DSig 提供互通性並符合業界標準的數位簽章協議，增強文件的安全性和真實性。

**Q4：我可以一次簽署多份文件嗎？**
A4：是的，可以實現批次處理，使用循環或並行處理策略有效地處理多個文件。

**Q5：簽署文件時證書密碼錯誤怎麼辦？**
A5：請確保您的密碼準確。密碼不正確將導致簽名申請無法成功。如果需要，請與您的證書提供者仔細核對。

## 資源

- **文件**： [Aspose.Words for Python](https://reference.aspose.com/words/python-net/)
- **下載**： [Aspose 版本](https://releases.aspose.com/words/python/)
- **購買許可證**： [Aspose 購買](https://purchase.aspose.com/buy)
- **免費試用**： [Aspose 免費試用](https://releases.aspose.com/words/python/)
- **臨時執照**： [Aspose臨時許可證](https://purchase.aspose.com/temporary-license/)
- **支援論壇**： [Aspose 支援](https://forum.aspose.com/c/words/10)

我們希望本指南能幫助您掌握使用 Aspose.Words for Python 進行數位簽章。編碼愉快！
{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}