---
title: Aspose.Words for .NET を使用して Word ドキュメントに水平ルール シェイプを挿入する
weight: 110
limit:
description: DocumentBuilder を使用して Aspose.Words for .NET で Word ドキュメントに水平ルール シェイプを追加する方法を学びます。
keywords: [Aspose.Words for .NET, insert horizontal rule shape, documentbuilder horizontal line, create Word document .NET, horizontal rule shape tutorial]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET を使用して Word ドキュメントに水平ルール シェイプを挿入する
このチュートリアルでは、Aspose.Words for .NET を使用してプログラムで Word ドキュメントに水平ルール シェイプを挿入する方法を学びます。Document と DocumentBuilder クラスを使用して新しいドキュメントを作成し、テキストの段落を追加し、目的の位置に水平線シェイプを配置します。水平ルールは、セクション区切りや視覚的強調に役立つビジュアルセパレーターを提供します。

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

**Q: `builder.InsertHorizontalRule()` はドキュメント内のどこに正確に線を配置しますか？**  
A: `InsertHorizontalRule` は `DocumentBuilder` の現在のカーソル位置に水平ルール シェイプを挿入します。独立した行にしたい場合は、挿入前に `builder.Writeln()` を呼び出してください。

**Q: 挿入された水平ルールの太さ、色、幅を変更できますか？**  
A: `InsertHorizontalRule` はデフォルトスタイルのルールを追加し、書式設定オプションは公開されていません。これらのプロパティをカスタマイズするには、`Shape` を手動で挿入（例: `builder.InsertShape(ShapeType.HorizontalLine)`）し、`LineFormat` プロパティを設定する必要があります。

**Q: 同じドキュメントに複数の水平ルールを追加することは可能ですか？**  
A: はい。新しいルールが必要なときは `builder.InsertHorizontalRule()` を呼び出すだけです。呼び出すたびに、builder の現在位置に個別のシェイプが作成されます。

**Q: 保存された .docx を Microsoft Word で開いたとき、水平ルールは表示されますか？**  
A: もちろんです。ルールは .docx ファイル内のシェイプとして保存されるため、Word は生成されたドキュメントと同じように正確に表示します。

**Q: `doc.Save(...)` を呼び出す前に `dataDir` フォルダーが存在しない場合、どうなりますか？**  
A: `doc.Save` は `DirectoryNotFoundException` をスローします。保存する前に対象ディレクトリが存在することを確認するか、プログラムで作成してください。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}