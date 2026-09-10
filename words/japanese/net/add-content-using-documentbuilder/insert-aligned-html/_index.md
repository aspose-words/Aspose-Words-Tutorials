---
title: Aspose.Words for .NET を使用して、Word 文書に整列された HTML を挿入する
weight: 210
limit:
description: Aspose.Words for .NET を使用して、左揃え、中央揃え、右揃えのいずれかで生の HTML を Word 文書に挿入する方法を学びます。
keywords: [Aspose.Words for .NET, insert html word document, html alignment, documentbuilder html, c# insert html, aligned html in word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET を使用して、Word 文書に整列された HTML を挿入する
このインタラクティブなチュートリアルでは、Aspose.Words for .NET を使用して、生の HTML を Word 文書に埋め込み、左・中央・右の配置を制御する方法を示します。Document と DocumentBuilder を活用することで、HTML 文字列を挿入し、数行のコードだけで目的の段落配置を適用できます。HTML の書式を保持し、コンテンツを文書内の正確な位置に配置したい場合に最適な例です。

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-aligned-html" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: DocumentBuilder.InsertHtml に渡された HTML 文字列に、<script> や <iframe> のように Aspose.Words がサポートしていないタグが含まれている場合、どうなりますか？**
A: サポートされていないタグは無視されます。Aspose.Words はレンダリング可能な HTML のサブセットのみを解析するため、<script>、<iframe> などの要素は除去され、残りのコンテンツが挿入されます。

**Q: InsertHtml を使用する際、インライン CSS スタイル（例: <span style=\"color:red;\">）は保持されますか？**
A: はい、InsertHtml は color、font-size、background など多数のインライン CSS プロパティを尊重し、対応する Word の書式に変換します。

**Q: InsertHtml は <div> や <h1> などのブロックレベル要素に対して自動的に新しい段落を作成しますか？**
A: ブロックレベル要素は Word の段落にマッピングされるため、各 <div>、<p>、<h1> などは文書内で個別の段落となります。

**Q: 既存の文書の先頭ではなく、特定の位置に HTML を挿入するにはどうすればよいですか？**
A: InsertHtml を呼び出す前に DocumentBuilder のカーソルを目的のノードに移動します（例: builder.MoveToDocumentEnd() や builder.MoveToParagraph(index)）。HTML は現在のカーソル位置に挿入されます。

**Q: 文書に既にテキストが含まれている場合、InsertHtml を呼び出すと既存のコンテンツが上書きされますか？**
A: いいえ、InsertHtml は解析された HTML を builder の現在位置に挿入し、事前にカーソルをそのノードに移動したり削除しない限り、既存のノードは削除されません。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}