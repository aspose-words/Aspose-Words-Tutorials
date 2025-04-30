---
"description": "Aspose.Words for .NET を使用して、Word 文書のリスト番号を最初からやり直す方法を学びましょう。この 2,000 語の詳細なガイドでは、設定から高度なカスタマイズまで、必要な情報をすべて網羅しています。"
"linktitle": "再開リスト番号"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "再開リスト番号"
"url": "/ja/net/working-with-list/restart-list-number/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 再開リスト番号

## 導入

Aspose.Words for .NET を使って Word 文書のリスト操作をマスターしたいですか？まさにうってつけのチュートリアルです！このチュートリアルでは、リスト番号のリスタート機能について詳しく解説します。これは、文書作成の自動化スキルを次のレベルに引き上げる便利な機能です。さあ、シートベルトを締めて、さあ始めましょう！

## 前提条件

コードに進む前に、必要なものがすべて揃っていることを確認しましょう。

1. Aspose.Words for .NET: Aspose.Words for .NET がインストールされている必要があります。まだインストールしていない場合は、 [ここからダウンロード](https://releases。aspose.com/words/net/).
2. 開発環境: Visual Studio などの適切な開発環境があることを確認します。
3. C# の基本知識: C# の基本を理解していると、チュートリアルを理解するのに役立ちます。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートしましょう。これらはAspose.Wordsの機能にアクセスするために不可欠です。

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
using System.Drawing;
```

それでは、プロセスを分かりやすいステップに分解してみましょう。リストの作成から番号の振り直しまで、すべてを網羅します。

## ステップ1：ドキュメントとビルダーを設定する

リストを操作する前に、ドキュメントとDocumentBuilderが必要です。DocumentBuilderは、ドキュメントにコンテンツを追加するための頼りになるツールです。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ステップ2: 最初のリストを作成してカスタマイズする

次に、テンプレートに基づいてリストを作成し、その外観をカスタマイズします。この例では、括弧付きのアラビア数字形式を使用します。

```csharp
List list1 = doc.Lists.Add(ListTemplate.NumberArabicParenthesis);
list1.ListLevels[0].Font.Color = Color.Red;
list1.ListLevels[0].Alignment = ListLevelAlignment.Right;
```

ここでは、フォントの色を赤に設定し、テキストを右揃えにしています。

## ステップ3: 最初のリストにアイテムを追加する

リストが準備できたら、アイテムを追加しましょう。DocumentBuilderの `ListFormat.List` このプロパティは、テキストにリスト形式を適用するのに役立ちます。

```csharp
builder.Writeln("List 1 starts below:");
builder.ListFormat.List = list1;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## ステップ4: リストの番号付けを再開する

リストを再利用して番号付けをやり直すには、元のリストのコピーを作成する必要があります。これにより、新しいリストを個別に変更できるようになります。

```csharp
List list2 = doc.Lists.AddCopy(list1);
list2.ListLevels[0].StartAt = 10;
```

この例では、新しいリストは 10 番から始まります。

## ステップ5: 新しいリストにアイテムを追加する

前回と同じように、新しいリストにアイテムを追加します。これにより、リストが指定した番号から再開されます。

```csharp
builder.Writeln("List 2 starts below:");
builder.ListFormat.List = list2;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## ステップ6: ドキュメントを保存する

最後に、ドキュメントを指定したディレクトリに保存します。

```csharp
builder.Document.Save(dataDir + "WorkingWithList.RestartListNumber.docx");
```

## 結論

Aspose.Words for .NET を使えば、Word 文書のリスト番号を最初からやり直すのが簡単で非常に便利です。レポートの作成、構造化文書の作成、あるいは単にリストをより適切に管理したい場合でも、このテクニックが役立ちます。

## よくある質問

### NumberArabicParenthesis 以外のリスト テンプレートも使用できますか?

もちろんです！Aspose.Wordsには、箇条書き、文字、ローマ数字など、様々なリストテンプレートが用意されています。ニーズに最適なものをお選びいただけます。

### リストレベルを変更するにはどうすればよいですか?

リストレベルを変更するには、 `ListLevels` プロパティ。例えば、 `list1.ListLevels[1]` リストの 2 番目のレベルを参照します。

### 任意の番号から番号付けを再開できますか?

はい、開始番号を任意の整数値に設定できます。 `StartAt` リスト レベルのプロパティ。

### リストのレベルごとに異なる書式を設定することは可能ですか?

そうです！各リスト レベルには、フォント、配置、番号スタイルなどの独自の書式設定を設定できます。

### 再開するのではなく、前のリストから番号付けを継続したい場合はどうすればよいでしょうか?

番号付けを継続したい場合は、リストのコピーを作成する必要はありません。元のリストに項目を追加し続けるだけです。





{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}