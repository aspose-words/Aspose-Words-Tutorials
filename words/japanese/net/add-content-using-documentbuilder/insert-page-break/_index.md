---
title: Aspose.Words for .NET を使用して Word 文書に改ページを挿入する
weight: 110
limit:
description: Aspose.Words for .NET の Document と DocumentBuilder を使用して、Word ファイルに改ページを追加する方法を学びます。
keywords: [Aspose.Words for .NET, insert page break, documentbuilder page break, c# add page break, word document pagination]
url: /net/add-content-using-documentbuilder/insert-page-break/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET を使用して Word 文書に改ページを挿入する
このインタラクティブチュートリアルでは、Aspose.Words for .NET を使用してプログラムから Word 文書に改ページを追加する方法を学びます。Document オブジェクトを作成し DocumentBuilder を使用することで、新しいページが開始される位置を制御でき、レポートや請求書、マルチセクション文書の書式設定に不可欠です。ステップバイステップの例に従ってコードの動作を確認し、生成されたファイルをプレビューしてください。

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-page-break" >}}


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

**Q: InsertBreak を使用して、改ページの代わりに改行やセクションブレークを追加できますか？**
A: はい、InsertBreak は BreakType 列挙体の任意の値を受け付けます。たとえば BreakType.LineBreak や BreakType.SectionBreakContinuous などを指定すると、対応するブレークが挿入されます。

**Q: 新しいページのテキストを書き込む前に InsertBreak を呼び出す必要がありますか、それとも後ですか？**
A: InsertBreak は現在のページに配置したいコンテンツの後で呼び出すべきです。次の Writeln が改ページによって作成された新しいページで開始されます。

**Q: dataDir パスがディレクトリ区切り文字で終わっていない場合、どうなりますか？**
A: dataDir に末尾のスラッシュがないと、ファイル名が直接連結されます（例: "C:\\DocsAddContentUsingDocumentBuilder.InsertBreak.docx"）。これにより無効なパスになる可能性があるため、パスの末尾に "\\" を付けるか、Path.Combine を使用してください。

**Q: 同じ DocumentBuilder インスタンスを再利用して、文書全体に複数のブレークを挿入できますか？**
A: はい、同じ DocumentBuilder を繰り返し使用できます。InsertBreak を呼び出すたびに、ビルダーの現在のカーソル位置にブレークが挿入されます。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}