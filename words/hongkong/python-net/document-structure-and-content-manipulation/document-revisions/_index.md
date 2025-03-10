---
title: 追蹤和審查文件修訂
linktitle: 追蹤和審查文件修訂
second_title: Aspose.Words Python 文件管理 API
description: 了解如何使用 Aspose.Words for Python 追蹤和審查文件修訂。具有原始程式碼的逐步指南，可實現高效協作。立即增強您的文件管理！
weight: 23
url: /zh-hant/python-net/document-structure-and-content-manipulation/document-revisions/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 追蹤和審查文件修訂


文件修訂和追蹤是協作工作環境的重要方面。 Aspose.Words for Python 提供了強大的工具來促進文件修訂的高效追蹤和審查。在本綜合指南中，我們將逐步探索如何使用 Aspose.Words for Python 來實現這一目標。在本教學結束時，您將深入了解如何將修訂追蹤功能整合到 Python 應用程式中。

## 文件修訂簡介

文件修訂涉及追蹤一段時間內對文件所做的更改。這對於協作寫作、法律文件和法規遵循至關重要。 Aspose.Words for Python 透過提供一套全面的工具來以程式設計方式管理文件修訂，從而簡化了這個過程。

## 為 Python 設定 Aspose.Words

在開始之前，請確保您已安裝 Aspose.Words for Python。您可以從以下位置下載：[這裡](https://releases.aspose.com/words/python/)。安裝後，您可以在 Python 腳本中匯入必要的模組以開始使用。

```python
import aspose.words as aw
```

## 載入和顯示文檔

要使用文檔，您首先需要將其載入到 Python 應用程式中。使用以下程式碼片段載入文件並顯示其內容：

```python
doc = aw.Document("document.docx")
print(doc.get_text())
```

## 啟用追蹤更改

要啟用文件的追蹤更改，您需要設定`TrackRevisions`財產給`True`:

```python
doc.track_revisions = True
```

## 新增對文件的修訂

當對文件進行任何更改時，Aspose.Words 可以自動追蹤它們作為修訂。例如，如果我們想要替換特定單詞，我們可以在追蹤更改的同時進行操作：

```python
run = doc.get_child_nodes(aw.NodeType.RUN, True)[0]
run.text = "modified content"
```

## 審查並接受修訂

若要查看文件中的修訂，請迭代修訂集合並顯示它們：

```python
revisions = doc.revisions
for revision in revisions:
    print(f"Revision Type: {revision.revision_type}, Text: {revision.parent_node.get_text()}")
```

## 比較不同版本

Aspose.Words 可讓您比較兩份文件以視覺化它們之間的差異：

```python
doc1 = aw.Document("document_v1.docx")
doc2 = aw.Document("document_v2.docx")
comparison = doc1.compare(doc2, "John Doe", datetime.now())
comparison.save("comparison_result.docx")
```

## 處理評論和註釋

協作者可以為文件添加評論和註釋。您可以透過程式設計方式管理這些元素：

```python
comment = aw.Comment(doc, "John Doe", datetime.now(), "This is a comment.")
paragraph = doc.get_child(aw.NodeType.PARAGRAPH, 0)
paragraph.insert_before(comment, paragraph.runs[0])
```

## 自訂修訂版外觀

您可以自訂修訂在文件中的顯示方式，例如變更插入和刪除文字的顏色：

```python
doc.revision_options.inserted_text_color = aw.layout.RevisionColor.GREEN
doc.revision_options.deleted_text_color = aw.layout.RevisionColor.RED
```

## 儲存和共享文檔

檢查並接受修訂後，請儲存文件：

```python
doc.save("final_document.docx")
```

與合作者共享最終文檔以獲得進一步回饋。

## 結論

Aspose.Words for Python 簡化了文件修訂和追蹤、增強協作並確保文件完整性。憑藉其強大的功能，您可以簡化文件中的審閱、接受和管理變更的流程。

## 常見問題解答

### 如何安裝 Aspose.Words for Python？

您可以從以下位置下載 Aspose.Words for Python[這裡](https://releases.aspose.com/words/python/)。按照安裝說明在您的環境中進行設定。

### 我可以停用文件特定部分的修訂追蹤嗎？

是的，您可以透過以程式方式調整`TrackRevisions`這些部分的屬性。

### 是否可以合併多個貢獻者的變更？

絕對地。 Aspose.Words 可讓您比較文件的不同版本並無縫合併變更。

### 轉換為不同格式時是否保留修訂歷史記錄？

是的，當您使用 Aspose.Words 將文件轉換為不同格式時，修訂記錄會保留。

### 如何以程式設計方式接受或拒絕修訂？

您可以迭代修訂集合並使用 Aspose.Words 的 API 函數以程式設計方式接受或拒絕每個修訂。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
