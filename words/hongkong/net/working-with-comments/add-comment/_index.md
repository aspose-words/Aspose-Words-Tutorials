---
title: 使用 Aspose.Words for .NET 在 Word 文件的特定段落插入註解
weight: 210
limit:
description: 逐步指南：在 Word 文件中為選定段落新增作者註解，並使用 Aspose.Words for .NET 儲存為 DOCX。
keywords: [add comment Aspose.Words for .NET, insert comment Word document, comment author Aspose.Words, c# add comment to Word, save DOCX with comment]
url: /net/working-with-comments/add-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 逐步指南：在 Word 文件中為選定段落新增作者註解，並使用 Aspose.Words for .NET 儲存為 DOCX。
  headline: 使用 Aspose.Words for .NET 在 Word 文件的特定段落插入註解
  type: TechArticle
- description: 逐步指南：在 Word 文件中為選定段落新增作者註解，並使用 Aspose.Words for .NET 儲存為 DOCX。
  name: 使用 Aspose.Words for .NET 在 Word 文件的特定段落插入註解
  steps:
  - name: 建立一個新的 Document 以及 DocumentBuilder，以開始建構 Word 檔案。
    text: 建立一個新的 Document 以及 DocumentBuilder，以開始建構 Word 檔案。
  - name: 使用 DocumentBuilder.Writeln 向文件新增三個獨立的文字段落。
    text: 使用 DocumentBuilder.Writeln 向文件新增三個獨立的文字段落。
  - name: 安全地取得第二個段落；若文件少於兩個段落，則回退使用第一個段落。
    text: 安全地取得第二個段落；若文件少於兩個段落，則回退使用第一個段落。
  - name: 建立帶有作者資訊的 Comment，設定其文字，並將其附加至選取的段落。
    text: 建立帶有作者資訊的 Comment，設定其文字，並將其附加至選取的段落。
  - name: 將修改後的文件儲存為目前資料夾下名為 'sample.docx' 的 DOCX 檔案。
    text: 將修改後的文件儲存為目前資料夾下名為 'sample.docx' 的 DOCX 檔案。
  type: HowTo
- questions:
  - answer: '`if` 區塊在 `paraList.Count` 小於 2 時會回退至第一個段落 (`paraList[0]`)，因此註解會附加在唯一的段落上，而不是缺失的第二段。'
    question: 如果文件只有一個段落，程式碼會怎麼處理？
  - answer: 它們作為第二與第三個參數傳入 `Comment` 建構式，例如 `new Comment(wordDoc, "Jordan", "JH",
      DateTime.Now)`，其中 "Jordan" 為作者名稱，"JH" 為縮寫。
    question: 在此範例中，註解的作者名稱與縮寫是如何設定的？
  - answer: 在此程式碼片段中，註解透過 `AppendChild` 連結至整個 `Paragraph`，若要對文字範圍加註解，需在目標 `Run` 節點前後建立
      `CommentRangeStart` 與 `CommentRangeEnd`，再將 `Comment` 節點插入其間。
    question: 我可以將註解附加在特定文字片段，而不是整個段落嗎？
  - answer: '`AppendChild` 會將 `Comment` 節點加入段落的子集合，且 Aspose.Words 會在文件儲存時自動產生所需的註解開始/結束標記。'
    question: 我需要手動插入註解標記嗎，還是 `AppendChild` 會自動處理？
  type: FAQPage
images:
- /net/working-with-comments/add-comment/og-image.png
og_title: 在 Word 段落中插入註解
og_description: 為特定段落加入作者註解，並使用 Aspose.Words 匯出為 DOCX 檔案。
og_image_alt: 指南說明如何使用 Aspose.Words for .NET 為 Word 文件的段落加入註解
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在 Word 文件的特定段落插入註解
使用 Aspose.Words for .NET，您可以以程式方式向 Word 檔案加入註解。本教學說明如何建立新文件、插入三個段落、定位第二個段落，並附加包含作者與日期資訊的註解。最後，文件會以保留註解的方式儲存為 DOCX 檔案。

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-comment" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: 如果文件只有一個段落，程式碼會怎麼處理？**  
A: `if` 區塊在 `paraList.Count` 小於 2 時會回退至第一個段落 (`paraList[0]`)，因此註解會附加在唯一的段落上，而不是缺失的第二段。

**Q: 在此範例中，註解的作者名稱與縮寫是如何設定的？**  
A: 它們作為第二與第三個參數傳入 `Comment` 建構式，例如 `new Comment(wordDoc, "Jordan", "JH", DateTime.Now)`，其中 "Jordan" 為作者名稱，"JH" 為縮寫。

**Q: 我可以將註解附加在特定文字片段，而不是整個段落嗎？**  
A: 在此程式碼片段中，註解透過 `AppendChild` 連結至整個 `Paragraph`，若要對文字範圍加註解，需在目標 `Run` 節點前後建立 `CommentRangeStart` 與 `CommentRangeEnd`，再將 `Comment` 節點插入其間。

**Q: 我需要手動插入註解標記嗎，還是 `AppendChild` 會自動處理？**  
A: `AppendChild` 會將 `Comment` 節點加入段落的子集合，且 Aspose.Words 會在文件儲存時自動產生所需的註解開始/結束標記。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}