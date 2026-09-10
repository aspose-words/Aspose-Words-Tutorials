---
title: Aspose.Words for .NET を使用して Word 文書に水平罫線シェイプを挿入する
weight: 110
limit:
description: Aspose.Words for .NET を使用して Word 文書に水平罫線シェイプを挿入するステップバイステップガイド。
keywords: [Aspose.Words for .NET, insert horizontal rule shape, horizontal rule shape .NET, DocumentBuilder horizontal rule, add horizontal line Word, create Word document Aspose]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET を使用して Word 文書に水平罫線シェイプを挿入する
Aspose.Words for .NET を使用して Word 文書に水平罫線シェイプを挿入する方法を学びます。このチュートリアルでは、新しい文書の作成、テキスト行の追加、DocumentBuilder を使った水平罫線シェイプの配置、ファイルの保存手順を順に説明します。水平罫線はコンテンツのシンプルな視覚的区切りとして機能します。

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-horizontal-rule-shape" >}}


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

**Q: DocumentBuilder.InsertHorizontalRule() で挿入した水平罫線の外観（色や太さ）を変更できますか？**
A: InsertHorizontalRule はデフォルトの書式設定を持つ組み込みの水平線シェイプを作成します。外観を変更するには、挿入された Shape オブジェクト（builder.CurrentParagraph.LastChild）を取得し、LineFormat プロパティを調整する必要があります。

**Q: すでに改行で終わっている段落の後で InsertHorizontalRule() を呼び出すとどうなりますか？**
A: このメソッドは水平罫線を別の段落として挿入するため、前の改行は単に水平罫線の前に空の段落を作ります。結果として水平罫線は独立した行に表示されます。

**Q: DocumentBuilder を使用して同じ文書に複数の水平罫線を挿入することは可能ですか？**
A: はい、builder.InsertHorizontalRule() を呼び出すたびに現在のカーソル位置に新しい水平罫線シェイプが追加され、文書全体に複数の罫線を配置できます。

**Q: DOCX 以外の形式（例えば PDF）で文書を保存する際にも InsertHorizontalRule() は機能しますか？**
A: 水平罫線は文書モデル内でシェイプとして保存されるため、PDF、XPS、その他のサポートされている形式で保存した場合でも、出力に正しくレンダリングされます。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}