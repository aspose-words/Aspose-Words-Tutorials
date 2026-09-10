---
title: Aspose.Words for .NET を使用して Word 文書に配置された HTML を挿入する
weight: 210
limit:
description: Aspose.Words for .NET を使用して、特定の配置で HTML を Word 文書に挿入する方法を学びましょう。
keywords: [insert aligned html, Aspose.Words for .NET, documentbuilder html insertion, html alignment in word, c# insert html word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET を使用して Word 文書に配置された HTML を挿入する
このチュートリアルでは、Aspose.Words for .NET の DocumentBuilder を使用して HTML マークアップを Word 文書に埋め込み、配置を制御する方法を示します。HTML の挿入方法、段落の配置（左、中央、右）の設定方法、そして結果の文書の保存方法がわかります。この例は、Web スタイルの書式設定を保持しながらプログラムで Word ファイルを生成する必要がある開発者に最適です。

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

**Q: InsertHtml は新規文書ではなく、既存の Word 文書に HTML を追加するために使用できますか？**
A: はい。既存のファイルから Document を作成し、HTML を挿入したい位置に DocumentBuilder のカーソルを移動させます（例: builder.MoveToDocumentEnd() を使用）。その後、builder.InsertHtml にマークアップを渡して呼び出します。

**Q: InsertHtml が配置のために尊重する HTML 属性はどれですか？**
A: InsertHtml は <p>、<div>、見出しタグなどのブロックレベル要素の "align" 属性を尊重し、結果の Word 文書で対応する段落配置を適用します。

**Q: HTML 文字列にサポートされていないタグや CSS が含まれている場合はどうなりますか？**
A: サポートされていないタグは無視され、その内部テキストはプレーンテキストとして挿入されます。Aspose.Words が認識しないインライン CSS スタイルも無視されるため、サポートされている HTML のサブセットのみがレンダリングされます。

**Q: 文書を保存する前に DocumentBuilder を閉じる必要がありますか？**
A: 明示的に閉じる必要はありません。HTML を挿入した後は、目的のファイル名と形式で直接 doc.Save を呼び出せばよく、Builder のリソースは自動的に解放されます。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}