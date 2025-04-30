---
"description": "了解如何使用 Aspose.Words for Python 追蹤和審查文件修訂。具有原始程式碼的逐步指南，可實現高效協作。立即增強您的文件管理！"
"linktitle": "追蹤和審查文件修訂"
"second_title": "Aspose.Words Python文件管理API"
"title": "追蹤和審查文件修訂"
"url": "/zh-hant/python-net/document-structure-and-content-manipulation/document-revisions/"
"weight": 23
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 追蹤和審查文件修訂


文件修訂和追蹤是協作工作環境的關鍵方面。 Aspose.Words for Python 提供了強大的工具來促進高效追蹤和審查文件修訂。在本綜合指南中，我們將逐步探討如何使用 Aspose.Words for Python 來實現這一點。在本教學結束時，您將對如何將修訂追蹤功能整合到 Python 應用程式中有深入的了解。

## 文件修訂介紹

文件修訂涉及追蹤一段時間內對文件所做的更改。這對於協作寫作、法律文件和法規遵循至關重要。 Aspose.Words for Python 透過提供一套全面的工具以程式設計方式管理文件修訂，簡化了此過程。

## 為 Python 設定 Aspose.Words

在開始之前，請確保您已安裝 Aspose.Words for Python。您可以從下載 [這裡](https://releases.aspose.com/words/python/)。安裝完成後，您可以在 Python 腳本中匯入必要的模組即可開始使用。

```python
import aspose.words as aw
```

## 載入和顯示文檔

要處理文檔，首先需要將其載入到 Python 應用程式中。使用以下程式碼片段載入文件並顯示其內容：

```python
doc = aw.Document("document.docx")
print(doc.get_text())
```

## 啟用修訂

要啟用文件的追蹤更改，您需要設定 `TrackRevisions` 財產 `True`：

```python
doc.track_revisions = True
```

## 新增修訂

當對文件進行任何更改時，Aspose.Words 可以自動將其作為修訂進行追蹤。例如，如果我們想要替換特定的單詞，我們可以這樣做，同時追蹤變化：

```python
run = doc.get_child_nodes(aw.NodeType.RUN, True)[0]
run.text = "modified content"
```

## 審查及接受修訂

若要查看文件中的修訂，請遍歷修訂集合並顯示它們：

```python
revisions = doc.revisions
for revision in revisions:
    print(f"Revision Type: {revision.revision_type}, Text: {revision.parent_node.get_text()}")
```

## 比較不同版本

Aspose.Words 可讓您比較兩份文件以直觀地看到它們之間的差異：

```python
doc1 = aw.Document("document_v1.docx")
doc2 = aw.Document("document_v2.docx")
comparison = doc1.compare(doc2, "John Doe", datetime.now())
comparison.save("comparison_result.docx")
```

## 處理評論和註解

合作者可以為文件添加評論和註釋。您可以透過程式設計方式管理這些元素：

```python
comment = aw.Comment(doc, "John Doe", datetime.now(), "This is a comment.")
paragraph = doc.get_child(aw.NodeType.PARAGRAPH, 0)
paragraph.insert_before(comment, paragraph.runs[0])
```

## 自訂修訂外觀

您可以自訂修訂在文件中的顯示方式，例如變更插入和刪除文字的顏色：

```python
doc.revision_options.inserted_text_color = aw.layout.RevisionColor.GREEN
doc.revision_options.deleted_text_color = aw.layout.RevisionColor.RED
```

## 儲存和共享文檔

審閱並接受修訂後，儲存文件：

```python
doc.save("final_document.docx")
```

與合作者分享最終文件以獲得進一步的回饋。

## 結論

Aspose.Words for Python 簡化了文件的修訂和跟踪，增強了協作並確保了文件的完整性。借助其強大的功能，您可以簡化審查、接受和管理文件變更的過程。

## 常見問題解答

### 如何安裝 Aspose.Words for Python？

您可以從以下位置下載 Aspose.Words for Python [這裡](https://releases.aspose.com/words/python/)。按照安裝說明在您的環境中進行設定。

### 我可以停用文件特定部分的修訂追蹤嗎？

是的，您可以透過程式調整 `TrackRevisions` 這些部分的屬性。

### 是否可以合併來自多個貢獻者的變更？

絕對地。 Aspose.Words 可讓您比較文件的不同版本並無縫合併變更。

### 轉換為不同格式時修訂歷史記錄是否會保留？

是的，當您使用 Aspose.Words 將文件轉換為不同格式時，修訂記錄會保留。

### 我如何以程式方式接受或拒絕修訂？

您可以遍歷修訂集合，並使用 Aspose.Words 的 API 函數以程式設計方式接受或拒絕每個修訂。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}