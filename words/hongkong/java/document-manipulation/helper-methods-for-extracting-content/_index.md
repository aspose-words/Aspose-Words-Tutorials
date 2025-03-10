---
title: 在 Aspose.Words for Java 中提取內容的輔助方法
linktitle: 擷取內容的輔助方法
second_title: Aspose.Words Java 文件處理 API
description: 了解如何使用 Aspose.Words for Java 從 Word 文件中高效提取內容。在這份綜合指南中探索幫助器方法、自訂格式等。
weight: 14
url: /zh-hant/java/document-manipulation/helper-methods-for-extracting-content/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中提取內容的輔助方法


## Aspose.Words for Java 中擷取內容的輔助方法簡介

Aspose.Words for Java 是一個功能強大的函式庫，可讓開發人員以程式設計方式處理 Word 文件。使用 Word 文件時的常見任務是從中提取內容。在本文中，我們將探索一些使用 Aspose.Words for Java 有效提取內容的輔助方法。

## 先決條件

在我們深入研究程式碼範例之前，請確保您已在 Java 專案中安裝並設定了 Aspose.Words for Java。您可以從以下位置下載：[這裡](https://releases.aspose.com/words/java/).

## 輔助方法1：依樣式擷取段落

```java
public static ArrayList<Paragraph> paragraphsByStyleName(Document doc, String styleName) {
    //建立一個陣列來收集指定樣式的段落。
    ArrayList<Paragraph> paragraphsWithStyle = new ArrayList<Paragraph>();
    NodeCollection paragraphs = doc.getChildNodes(NodeType.PARAGRAPH, true);

    //瀏覽所有段落以尋找具有指定樣式的段落。
    for (Paragraph paragraph : (Iterable<Paragraph>) paragraphs) {
        if (paragraph.getParagraphFormat().getStyle().getName().equals(styleName))
            paragraphsWithStyle.add(paragraph);
    }
    return paragraphsWithStyle;
}
```

您可以使用此方法提取 Word 文件中具有特定樣式的段落。當您想要提取具有特定格式的內容（例如標題或區塊引號）時，這非常有用。

## 輔助方法2：透過節點擷取內容

```java
public static ArrayList<Node> extractContentBetweenNodes(Node startNode, Node endNode, boolean isInclusive) {
    //首先，檢查傳遞給此方法的節點是否有效。
    verifyParameterNodes(startNode, endNode);
    
    //建立一個清單來儲存提取的節點。
    ArrayList<Node> nodes = new ArrayList<Node>();

    //如果任一標記是評論的一部分，包括評論本身，我們需要移動指針
    //轉發到 CommentRangeEnd 節點之後找到的 Comment 節點。
    if (endNode.getNodeType() == NodeType.COMMENT_RANGE_END && isInclusive) {
        Node node = findNextNode(NodeType.COMMENT, endNode.getNextSibling());
        if (node != null)
            endNode = node;
    }
    
    //保留傳遞給此方法的原始節點的記錄，以便在需要時分割標記節點。
    Node originalStartNode = startNode;
    Node originalEndNode = endNode;

    //基於區塊級節點（段落和表格）提取內容。遍歷父節點來找到它們。
    //我們將根據標記節點是否內聯來分割第一個和最後一個節點的內容。
    startNode = getAncestorInBody(startNode);
    endNode = getAncestorInBody(endNode);
    boolean isExtracting = true;
    boolean isStartingNode = true;
    //我們從文檔中提取的當前節點。
    Node currNode = startNode;

    //開始提取內容。處理所有區塊級節點並專門分割第一個
    //需要時加入最後一個節點，以便保留段落格式。
    //這種方法比常規提取器稍微複雜一些，因為我們需要考慮因素
    //使用內聯節點、字段、書籤等進行提取，使其有用。
    while (isExtracting) {
        //克隆當前節點及其子節點以獲得副本。
        Node cloneNode = currNode.deepClone(true);
        boolean isEndingNode = currNode.equals(endNode);
        if (isStartingNode || isEndingNode) {
            //我們需要單獨處理每個標記，因此將其傳遞給單獨的方法。
            //應先處理End以保留節點索引。
            if (isEndingNode) {
                // !isStartingNode：如果標記是同一節點，請勿新增節點兩次。
                processMarker(cloneNode, nodes, originalEndNode, currNode, isInclusive,
                        false, !isStartingNode, false);
                isExtracting = false;
            }
            //條件需要分開，因為區塊級開始和結束標記可能是同一節點。
            if (isStartingNode) {
                processMarker(cloneNode, nodes, originalStartNode, currNode, isInclusive,
                        true, true, false);
                isStartingNode = false;
            }
        } else
            //節點不是開始或結束標記，只需將副本添加到清單中即可。
            nodes.add(cloneNode);

        //移動到下一個節點並將其提取。如果下一個節點為空，
        //其餘內容可以在不同的部分中找到。
        if (currNode.getNextSibling() == null && isExtracting) {
            //轉到下一部分。
            Section nextSection = (Section) currNode.getAncestor(NodeType.SECTION).getNextSibling();
            currNode = nextSection.getBody().getFirstChild();
        } else {
            //移動到主體中的下一個節點。
            currNode = currNode.getNextSibling();
        }
    }

    //為了與內嵌書籤模式相容，請新增下一段（空）。
    if (isInclusive && originalEndNode == endNode && !originalEndNode.isComposite())
        includeNextParagraph(endNode, nodes);

    //返回節點標記之間的節點。
    return nodes;
}
```

此方法可讓您提取兩個指定節點之間的內容，無論它們是段落、表格或任何其他區塊級元素。它處理各種場景，包括內聯標記、欄位和書籤。

## 輔助方法 3：產生新文檔

```java
public static Document generateDocument(Document srcDoc, ArrayList<Node> nodes) throws Exception {
    Document dstDoc = new Document();
    
    //從空白文檔中刪除第一段。
    dstDoc.getFirstSection().getBody().removeAllChildren();
    
    //將清單中的每個節點匯入到新文件中。保留節點的原始格式。
    NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
    for (Node node : nodes) {
        Node importNode = importer.importNode(node, true);
        dstDoc.getFirstSection().getBody().appendChild(importNode);
    }
    
    return dstDoc;
}
```

此方法可讓您透過從來源文件匯入節點清單來產生新文件。它保留了節點的原始格式，這使得它對於創建具有特定內容的新文件非常有用。

## 結論

從 Word 文件中提取內容可能是許多文件處理任務的關鍵部分。 Aspose.Words for Java 提供了強大的幫助器方法來簡化此過程。無論您需要按樣式、節點之間的內容提取段落，還是產生新文檔，這些方法都將幫助您在 Java 應用程式中有效地處理 Word 文件。

## 常見問題解答

### 如何安裝 Aspose.Words for Java？

要安裝 Aspose.Words for Java，您可以從 Aspose 網站下載。訪問[這裡](https://releases.aspose.com/words/java/)取得最新版本。

### 我可以從 Word 文件的特定部分提取內容嗎？

是的，您可以使用本文中提到的方法從 Word 文件的特定部分中提取內容。只需指定定義要提取的部分的開始和結束節點即可。

### Aspose.Words for Java 與 Java 11 相容嗎？

是的，Aspose.Words for Java 與 Java 11 及更高版本相容。您可以在 Java 應用程式中使用它，不會出現任何問題。

### 我可以自訂提取內容的格式嗎？

是的，您可以透過修改生成文件中匯入的節點來自訂提取內容的格式。 Aspose.Words for Java 提供了廣泛的格式化選項來滿足您的需求。

### 在哪裡可以找到 Aspose.Words for Java 的更多文件和範例？

您可以在 Aspose 網站上找到 Aspose.Words for Java 的綜合文件和範例。訪問[https://reference.aspose.com/words/java/](https://reference.aspose.com/words/java/)取得詳細的文件和資源。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
