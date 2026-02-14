---
date: 2026-02-14
description: 了解如何在 Aspose.Words for Java 中輕鬆顯示內嵌數學、插入數學方程式以及操作 Office 數學物件。
linktitle: Using Office Math Objects
second_title: Aspose.Words Java Document Processing API
title: 在 Aspose.Words for Java 中以 Office Math 內嵌方式顯示數學公式
url: /zh-hant/java/document-conversion-and-export/using-office-math-objects/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中以 Office Math 內嵌顯示數學

在本完整教學中，您將了解如何使用 Aspose.Words for Java 的 Office Math 物件 **內嵌顯示數學**。無論您需要在報告中 **插入數學方程式**，或是微調複雜公式的格式，本指南都會一步步帶領您，從載入 Word 文件到儲存最終結果。

## Quick Answers
- **什麼是「內嵌顯示數學」？** 方程式會出現在文字流中，而不是另起一行。  
- **哪個類別代表數學物件？** Aspose.Words API 中的 `OfficeMath`。  
- **我可以更改對齊方式嗎？** 可以，使用 `setJustification` 搭配 LEFT、CENTER 或 RIGHT。  
- **使用此功能需要授權嗎？** 生產環境必須使用有效的 Aspose.Words for Java 授權。  
- **示範使用哪個版本？** 此程式碼適用於最新的 Aspose.Words for Java 版本（2026）。

## 什麼是「內嵌顯示數學」？
內嵌顯示數學表示方程式被視為段落文字的一部分，能夠自然地隨周圍文字換行。這對於不希望中斷閱讀流程的簡短公式非常有用。

## 為何在 Aspose.Words for Java 中使用 Office Math 物件？
- **精確控制** 方程式的版面配置（內嵌或顯示）。  
- **程式化操作** 方程式，無需手動開啟 Word。  
- **跨平台一致的渲染**，非常適合自動化報告產生。

## 前置條件
在開始之前，請確保您已具備以下條件：

- 已在專案中安裝並引用 Aspose.Words for Java。  
- 已包含 Office Math 方程式的 Word 檔（例如 `OfficeMath.docx`）。  
- 若在評估模式之外執行程式碼，需具備有效授權。

## 步驟說明

### 載入文件
首先，載入包含您想操作之 Office Math 方程式的文件：

```java
Document doc = new Document("Your Directory Path" + "OfficeMath.docx");
```

### 取得 Office Math 物件
從文件中取得第一個 Office Math 節點：

```java
OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
```

### 設定顯示類型（內嵌或顯示）
控制方程式是與周圍文字內嵌顯示，還是另起一行。若要 **內嵌顯示數學**，使用 `INLINE` 列舉；若要另起一行，使用 `DISPLAY`：

```java
officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
```

*如果您希望方程式保持內嵌，請將 `DISPLAY` 改為 `INLINE`。*

### 設定對齊方式
調整方程式的對齊方式。以下範例將其左對齊，您亦可選擇 `CENTER` 或 `RIGHT`：

```java
officeMath.setJustification(OfficeMathJustification.LEFT);
```

### 儲存已修改的文件
最後，將變更寫入新檔案：

```java
doc.save("Your Directory Path" + "ModifiedOfficeMath.docx");
```

## 完整範例程式碼：在 Aspose.Words for Java 中使用 Office Math 物件

```java
        Document doc = new Document("Your Directory Path" + "Office math.docx");
        OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
        // OfficeMath display type represents whether an equation is displayed inline with the text or displayed on its line.
        officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
        officeMath.setJustification(OfficeMathJustification.LEFT);
        doc.save("Your Directory Path" + "WorkingWithOfficeMath.MathEquations.docx");
```

## 常見問題與除錯
- **找不到方程式：** 確認文件確實包含 Office Math 物件；否則 `doc.getChild` 會回傳 `null`。  
- **顯示類型無效：** 請確認使用的是最新版本的 Aspose.Words；較舊版本可能對 `OfficeMathDisplayType` 支援有限。  
- **授權例外：** 若出現授權錯誤，請再次確認在建立 `Document` 實例前已正確載入授權檔案。

## 常見問答

**Q: 在 Aspose.Words for Java 中使用 Office Math 物件的目的為何？**  
A: Office Math 物件讓您能以程式方式表示與操作數學方程式，並完整掌控其顯示與格式設定。

**Q: 我可以在文件中以不同方式對齊 Office Math 方程式嗎？**  
A: 可以，使用 `setJustification` 方法即可將其左對齊、右對齊或置中。

**Q: Aspose.Words for Java 能否處理複雜的數學文件？**  
A: 當然可以。此函式庫完整支援複雜方程式、巢狀分數、矩陣等。

**Q: 如何取得更多關於 Aspose.Words for Java 的資訊？**  
A: 欲取得完整文件與下載，請造訪 [Aspose.Words for Java 文件說明](https://reference.aspose.com/words/java/)。

**Q: 從哪裡可以下載 Aspose.Words for Java？**  
A: 您可於官方網站下載 Aspose.Words for Java： [下載 Aspose.Words for Java](https://releases.aspose.com/words/java/)。

**最後更新：** 2026-02-14  
**測試環境：** Aspose.Words for Java 24.12（截至 2026 年 2 月的最新版本）  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}