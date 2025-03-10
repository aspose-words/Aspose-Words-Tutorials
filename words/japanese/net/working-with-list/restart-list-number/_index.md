---
title: 再開リスト番号
linktitle: 再開リスト番号
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して Word 文書のリスト番号を再開する方法を学びます。この 2,000 語の詳細なガイドには、セットアップから高度なカスタマイズまで、知っておく必要のあるすべての内容が記載されています。
weight: 10
url: /ja/net/working-with-list/restart-list-number/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 再開リスト番号

## 導入

Aspose.Words for .NET を使用して Word 文書のリスト操作の技術を習得したいとお考えですか? まさに、ここが最適な場所です! このチュートリアルでは、リスト番号の再開について詳しく説明していきます。これは、文書の自動化スキルを次のレベルに引き上げる便利な機能です。シートベルトを締めて、始めましょう!

## 前提条件

コードに進む前に、必要なものがすべて揃っていることを確認しましょう。

1.  Aspose.Words for .NET: Aspose.Words for .NETがインストールされている必要があります。まだインストールしていない場合は、[ここからダウンロード](https://releases.aspose.com/words/net/).
2. 開発環境: Visual Studio などの適切な開発環境があることを確認します。
3. C# の基礎知識: C# の基礎を理解していると、チュートリアルを理解するのに役立ちます。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートしましょう。これらは Aspose.Words 機能にアクセスするために重要です。

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
using System.Drawing;
```

それでは、プロセスをわかりやすい手順に分解してみましょう。リストの作成から番号の付け直しまで、すべてをカバーします。

## ステップ1: ドキュメントとビルダーを設定する

リストの操作を開始する前に、ドキュメントと DocumentBuilder が必要です。DocumentBuilder は、ドキュメントにコンテンツを追加するためのツールです。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ステップ2: 最初のリストを作成してカスタマイズする

次に、テンプレートに基づいてリストを作成し、その外観をカスタマイズします。この例では、括弧付きのアラビア数字形式を使用しています。

```csharp
List list1 = doc.Lists.Add(ListTemplate.NumberArabicParenthesis);
list1.ListLevels[0].Font.Color = Color.Red;
list1.ListLevels[0].Alignment = ListLevelAlignment.Right;
```

ここでは、フォントの色を赤に設定し、テキストを右揃えにしています。

## ステップ3: 最初のリストにアイテムを追加する

リストが準備できたら、アイテムを追加します。DocumentBuilderの`ListFormat.List`プロパティは、テキストにリスト形式を適用するのに役立ちます。

```csharp
builder.Writeln("List 1 starts below:");
builder.ListFormat.List = list1;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## ステップ4: リストの番号付けを再開する

リストを再利用して番号付けを再開するには、元のリストのコピーを作成する必要があります。これにより、新しいリストを個別に変更できます。

```csharp
List list2 = doc.Lists.AddCopy(list1);
list2.ListLevels[0].StartAt = 10;
```

この例では、新しいリストは 10 番から始まります。

## ステップ5: 新しいリストにアイテムを追加する

前と同じように、新しいリストに項目を追加します。これにより、リストが指定された番号で再開されます。

```csharp
builder.Writeln("List 2 starts below:");
builder.ListFormat.List = list2;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## ステップ6: ドキュメントを保存する

最後に、指定したディレクトリにドキュメントを保存します。

```csharp
builder.Document.Save(dataDir + "WorkingWithList.RestartListNumber.docx");
```

## 結論

Aspose.Words for .NET を使用して Word 文書のリスト番号を再開するのは簡単で非常に便利です。レポートを生成する場合、構造化された文書を作成する場合、または単にリストをより適切に制御する必要がある場合でも、このテクニックが役立ちます。

## よくある質問

### NumberArabicParenthesis 以外のリスト テンプレートを使用できますか?

もちろんです! Aspose.Words には、箇条書き、文字、ローマ数字など、さまざまなリスト テンプレートが用意されています。ニーズに最適なものを選択できます。

### リストレベルを変更するにはどうすればよいですか?

リストレベルを変更するには、`ListLevels`プロパティ。たとえば、`list1.ListLevels[1]`リストの 2 番目のレベルを参照します。

### 任意の番号から番号付けを再開できますか?

はい、開始番号を任意の整数値に設定できます。`StartAt`リスト レベルのプロパティ。

### リストのレベルごとに異なる書式を設定することは可能ですか?

確かにそうです。各リスト レベルには、フォント、配置、番号付けスタイルなどの独自の書式設定を設定できます。

### 再開するのではなく、前のリストから番号付けを継続したい場合はどうすればよいですか?

番号付けを続行する場合は、リストのコピーを作成する必要はありません。元のリストに項目を追加し続けるだけです。



{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
