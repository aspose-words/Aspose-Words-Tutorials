---
title: Word 文書での複数レベルのリストの書式設定
linktitle: Word 文書での複数レベルのリストの書式設定
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して Word 文書のマルチレベル リストの書式設定を習得する方法を、ステップ バイ ステップ ガイドで学習します。文書構造を簡単に強化できます。
weight: 10
url: /ja/net/document-formatting/multilevel-list-formatting/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 文書での複数レベルのリストの書式設定

## 導入

Word 文書の作成と書式設定を自動化したい開発者にとって、Aspose.Words for .NET は画期的なツールです。今日は、この強力なライブラリを使用して、マルチレベル リストの書式設定をマスターする方法について詳しく説明します。構造化文書の作成、レポートのアウトライン作成、技術文書の生成など、マルチレベル リストを使用すると、コンテンツの読みやすさと整理性が向上します。

## 前提条件

細かい詳細に入る前に、このチュートリアルを実行するために必要なものがすべて揃っていることを確認しましょう。

1. 開発環境: 開発環境が設定されていることを確認してください。Visual Studio は最適な選択肢です。
2.  Aspose.Words for .NET: Aspose.Words for .NETライブラリをダウンロードしてインストールします。[ここ](https://releases.aspose.com/words/net/).
3. ライセンス: フルライセンスを持っていない場合は、一時ライセンスを取得してください。取得する[ここ](https://purchase.aspose.com/temporary-license/).
4. 基本的な C# の知識: C# と .NET フレームワークに精通していると有利です。

## 名前空間のインポート

プロジェクトで Aspose.Words for .NET を使用するには、必要な名前空間をインポートする必要があります。手順は次のとおりです。

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
```

## ステップ1: ドキュメントとビルダーを初期化する

まず最初に、新しい Word 文書を作成し、DocumentBuilder を初期化します。DocumentBuilder クラスは、文書にコンテンツを挿入するためのメソッドを提供します。

```csharp
//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ステップ2: デフォルトの番号付けを適用する

番号付きリストを開始するには、`ApplyNumberDefault`メソッド。これにより、デフォルトの番号付きリストの書式が設定されます。

```csharp
builder.ListFormat.ApplyNumberDefault();
builder.Writeln("Item 1");
builder.Writeln("Item 2");
```

これらの行では、`ApplyNumberDefault`番号付きリストを開始し、`Writeln`リストに項目を追加します。

## ステップ3: サブレベルのインデント

次に、リスト内にサブレベルを作成するには、`ListIndent`メソッド。このメソッドはリスト項目をインデントし、前の項目のサブレベルにします。

```csharp
builder.ListFormat.ListIndent();
builder.Writeln("Item 2.1");
builder.Writeln("Item 2.2");
```

このコード スニペットは項目をインデントし、第 2 レベルのリストを作成します。

## ステップ4: より深いレベルにインデントする

インデントを続けると、リスト内にさらに深いレベルを作成できます。ここでは、3 番目のレベルを作成します。

```csharp
builder.ListFormat.ListIndent();
builder.Writeln("Item 2.2.1");
builder.Writeln("Item 2.2.2");
```

これで、「項目 2.2」の下に第 3 レベルのリストが作成されました。

## ステップ5: アウトデントして上位レベルに戻る

より高いレベルに戻るには、`ListOutdent`メソッド。これにより、アイテムが前のリスト レベルに戻ります。

```csharp
builder.ListFormat.ListOutdent();
builder.Writeln("Item 2.3");
```

これにより、「項目 2.3」が第 2 レベルに戻ります。

## ステップ6: 番号を削除する

リストの作成が完了したら、番号を削除して、通常のテキストまたは別の種類の書式設定を続行できます。

```csharp
builder.ListFormat.ListOutdent();
builder.Writeln("Item 3");
builder.ListFormat.RemoveNumbers();
```

このコード スニペットはリストを完了し、番号付けを停止します。

## ステップ7: ドキュメントを保存する

最後に、ドキュメントを目的のディレクトリに保存します。

```csharp
doc.Save(dataDir + "DocumentFormatting.MultilevelListFormatting.docx");
```

これにより、複数レベルのリストを含む美しくフォーマットされたドキュメントが保存されます。

## 結論

これで完了です。Aspose.Words for .NET を使用して、Word 文書にマルチレベル リストを作成できました。この強力なライブラリを使用すると、複雑な文書の書式設定タスクを簡単に自動化できます。これらのツールを習得すると、時間を節約できるだけでなく、文書生成プロセスの一貫性と専門性が確保されることを忘れないでください。

## よくある質問

### リストの番号付けスタイルをカスタマイズできますか?
はい、Aspose.Words for .NETでは、リストの番号付けスタイルをカスタマイズできます。`ListTemplate`クラス。

### 数字の代わりに箇条書きを追加するにはどうすればよいですか?
箇条書きを適用するには、`ApplyBulletDefault`方法の代わりに`ApplyNumberDefault`.

### 以前のリストから番号を続けて付けることは可能ですか?
はい、番号付けを続けるには、`ListFormat.List`既存のリストにリンクするプロパティ。

### インデント レベルを動的に変更するにはどうすればよいですか?
インデントレベルを動的に変更するには、`ListIndent`そして`ListOutdent`必要に応じて方法を選択します。

### PDF などの他のドキュメント形式で複数レベルのリストを作成できますか?
はい、Aspose.Words は書式を維持したまま、PDF を含むさまざまな形式でのドキュメントの保存をサポートしています。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
