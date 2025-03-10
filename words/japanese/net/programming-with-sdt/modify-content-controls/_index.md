---
title: コンテンツコントロールの変更
linktitle: コンテンツコントロールの変更
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して Word で構造化ドキュメント タグを変更する方法を学びます。テキスト、ドロップダウン、画像を段階的に更新します。
weight: 10
url: /ja/net/programming-with-sdt/modify-content-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# コンテンツコントロールの変更

## 導入

Word 文書を操作したことがあり、プレーン テキスト、ドロップダウン リスト、画像などの構造化コンテンツ コントロールを Aspose.Words for .NET を使用して変更する必要がある場合は、適切な場所にいます。構造化ドキュメント タグ (SDT) は、ドキュメントの自動化をより簡単に、より柔軟にするための強力なツールです。このチュートリアルでは、ニーズに合わせてこれらの SDT を変更する方法について詳しく説明します。テキストを更新する場合、ドロップダウンの選択を変更する場合、または画像を交換する場合など、このガイドでは、プロセスをステップごとに説明します。

## 前提条件

コンテンツ コントロールの変更の詳細に入る前に、次のものを用意しておいてください。

1.  Aspose.Words for .NET がインストールされている: Aspose.Words ライブラリがインストールされていることを確認してください。インストールされていない場合は、[ここからダウンロード](https://releases.aspose.com/words/net/).

2. C# の基本知識: このチュートリアルでは、基本的な C# プログラミングの概念を理解していることを前提としています。

3. .NET 開発環境: .NET アプリケーションを実行するには、Visual Studio などの IDE をセットアップする必要があります。

4. サンプル ドキュメント: さまざまな種類の SDT を含むサンプル Word ドキュメントを使用します。サンプルのドキュメントを使用することも、独自のドキュメントを作成することもできます。

5.  Asposeドキュメントへのアクセス: 詳しい情報については、[Aspose.Words ドキュメント](https://reference.aspose.com/words/net/).

## 名前空間のインポート

Aspose.Words の使用を開始するには、関連する名前空間を C# プロジェクトにインポートする必要があります。手順は次のとおりです。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

これらの名前空間を使用すると、Word 文書内の構造化文書タグを操作するために必要なクラスとメソッドにアクセスできるようになります。

## ステップ1: ドキュメントパスを設定する

変更を加える前に、ドキュメントへのパスを指定する必要があります。`"YOUR DOCUMENT DIRECTORY"`ドキュメントが保存されている実際のパスを入力します。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## ステップ2: 構造化ドキュメントタグをループする

SDTを変更するには、まずドキュメント内のすべてのSDTをループする必要があります。これは、`GetChildNodes`タイプのノードをすべて取得するメソッド`StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    //SDTの種類に応じて変更する
}
```

## ステップ3: プレーンテキストSDTを変更する

SDT がプレーン テキスト タイプの場合、そのコンテンツを置き換えることができます。まず、既存のコンテンツをクリアしてから、新しいテキストを追加します。

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

説明: ここでは、`RemoveAllChildren()`SDTの既存の内容をクリアします。次に新しいSDTを作成します。`Paragraph`そして`Run`新しいテキストを挿入するオブジェクト。

## ステップ4: ドロップダウンリストSDTを変更する

ドロップダウンリストSDTの場合、選択項目を変更するには、`ListItems`コレクション。ここでは、リストの 3 番目の項目を選択します。

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

説明: このコード スニペットは、ドロップダウン リストからインデックス 2 (3 番目の項目) の項目を選択します。必要に応じてインデックスを調整してください。

## ステップ5: 画像SDTを変更する

画像 SDT 内の画像を更新するには、既存の画像を新しい画像に置き換えます。

```csharp
if (sdt.SdtType == SdtType.Picture)
{
    Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
    if (shape.HasImage)
    {
        shape.ImageData.SetImage(ImagesDir + "Watermark.png");
    }
}
```

説明: このコードは、図形に画像が含まれているかどうかを確認し、それを次の場所にある新しい画像に置き換えます。`ImagesDir`.

## ステップ6: 変更したドキュメントを保存する

必要な変更をすべて行った後、元のドキュメントをそのまま維持するために、変更したドキュメントを新しい名前で保存します。

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

説明: これにより、ドキュメントが新しいファイル名で保存され、元のドキュメントと簡単に区別できるようになります。

## 結論

Aspose.Words for .NET を使用して Word 文書内のコンテンツ コントロールを変更するのは、必要な手順を理解すれば簡単です。テキストの更新、ドロップダウンの選択の変更、画像の入れ替えなど、Aspose.Words はこれらのタスクに強力な API を提供します。このチュートリアルに従うことで、文書の構造化コンテンツ コントロールを効果的に管理およびカスタマイズし、文書をより動的にし、ニーズに合わせてカスタマイズすることができます。

## よくある質問

1. 構造化ドキュメントタグ (SDT) とは何ですか?

SDT は、テキスト ボックス、ドロップダウン リスト、画像などのドキュメント コンテンツの管理と書式設定に役立つ Word ドキュメント内の要素です。

2. SDT に新しいドロップダウン項目を追加するにはどうすればよいですか?

新しいアイテムを追加するには、`ListItems`プロパティを追加して新しい`SdtListItem`コレクションに追加します。

3. Aspose.Words を使用してドキュメントから SDT を削除できますか?

はい、ドキュメントのノードにアクセスし、目的の SDT を削除することで、SDT を削除できます。

4. 他の要素内にネストされた SDT をどのように処理すればよいですか?

使用`GetChildNodes`ネストされた SDT にアクセスするための適切なパラメータを持つメソッド。

5. 変更する必要がある SDT がドキュメント内に表示されない場合はどうすればよいでしょうか?

SDT が非表示または保護されていないことを確認します。ドキュメント設定を確認し、コードが SDT タイプを正しくターゲットにしていることを確認します。


### Aspose.Words for .NET を使用してコンテンツ コントロールを変更するためのサンプル ソース コード 

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Structured document tags.docx");
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
	switch (sdt.SdtType)
	{
		case SdtType.PlainText:
		{
			sdt.RemoveAllChildren();
			Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
			Run run = new Run(doc, "new text goes here");
			para.AppendChild(run);
			break;
		}
		case SdtType.DropDownList:
		{
			SdtListItem secondItem = sdt.ListItems[2];
			sdt.ListItems.SelectedValue = secondItem;
			break;
		}
		case SdtType.Picture:
		{
			Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
			if (shape.HasImage)
			{
				shape.ImageData.SetImage(ImagesDir + "Watermark.png");
			}
			break;
		}
	}
}
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");

```

これで完了です。Aspose.Words for .NET を使用して、Word 文書内のさまざまな種類のコンテンツ コントロールを正常に変更できました。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
