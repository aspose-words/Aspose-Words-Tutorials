---
title: テーブルをまとめる
linktitle: テーブルをまとめる
second_title: Aspose.Words ドキュメント処理 API
description: このステップバイステップガイドでは、Aspose.Words for .NET を使用して、表がページ間で分割されないようにする方法を学びます。整然としたプロフェッショナルな外観の Word 文書を実現します。
weight: 10
url: /ja/net/join-and-append-documents/keep-source-together/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# テーブルをまとめる

## 導入

表は多くの Word 文書の重要な部分ですが、表が 2 ページにまたがる状況に遭遇することがあります。これにより、文書の流れが乱れ、読みやすさに影響する可能性があります。表全体を 1 ページにまとめる方法があれば便利だと思いませんか? Aspose.Words for .NET を使用すると、この問題を簡単に解決できます。このチュートリアルでは、表が複数のページにまたがって分割されないようにし、文書がすっきりとプロフェッショナルに見えるようにする方法について説明します。

## 前提条件

チュートリアルに進む前に、スムーズに進めるために必要なものがすべて揃っていることを確認しましょう。

### Aspose.Words for .NET ライブラリ

まず、Aspose.Words for .NET をインストールする必要があります。これは、Word 文書をプログラムで操作できるようにする強力なライブラリです。

- [Aspose.Words for .NET をダウンロード](https://releases.aspose.com/words/net/)

### 開発環境

C# コードを実行するには、次のような開発環境を設定する必要があります。

- Visual Studio (最新バージョン)
- .NET Framework 2.0 以降

### 表を含む Word 文書

表を含むWord文書が必要です。このチュートリアルでは、サンプル文書「`"Table spanning two pages.docx"`このファイルには、現在 2 ページにまたがる表が含まれています。

### 一時ライセンス（オプション）

 Aspose.Wordsには無料トライアルが付属していますが、[一時ライセンス](https://purchase.aspose.com/temporary-license/)ライブラリの潜在能力を最大限に引き出します。

## パッケージのインポート

コードを記述する前に、Aspose.Words for .NET を操作するために必要な名前空間をインポートする必要があります。コード ファイルの先頭に次のインポートを追加します。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

これらの名前空間により、次のようなクラスにアクセスできます。`Document`, `Table`, `Cell`、およびこのチュートリアルで使用するその他のツールについて説明します。

## ステップ1: ドキュメントを読み込む

まず最初に、表を含むWord文書を読み込む必要があります。そのためには、`Document` Aspose.Words のクラス。このクラスを使用すると、Word ファイルをプログラムで開いて操作できます。

```csharp
//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENTS DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

このコードスニペットでは、ドキュメントの場所を指定します。`"YOUR DOCUMENTS DIRECTORY"`ドキュメントが保存されている実際のディレクトリに置き換えます。

## ステップ2: テーブルにアクセスする

ドキュメントが読み込まれたら、次のステップは、一緒に保持するテーブルにアクセスすることです。この例では、テーブルがドキュメント内の最初のテーブルであると想定しています。

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

このコード行は、文書内の最初の表を検索します。`GetChild`メソッドは特定のタイプのノードを取得します。この場合は`NodeType.Table` 。`0`最初のテーブルが必要であり、`true`フラグにより、すべての子ノードを再帰的に検索することが保証されます。

## ステップ3: 表のセルをループする

ここで、テーブル内の各セルをループする必要があります。テーブルには複数の行が含まれ、各行には複数のセルが含まれるため、各セルを反復処理して、ページ間で分割されないようにします。

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
```

ここ、`GetChildNodes`テーブル内のすべてのセルを取得し、各セルをループします。`EnsureMinimum()`このメソッドは、各セルに少なくとも 1 つの段落が含まれていることを確認します。空のセルがあると後で問題が発生する可能性があるためです。

## ステップ4: KeepWithNextプロパティを設定する

表がページをまたいで分割されないようにするには、`KeepWithNext`プロパティをテーブル内の各段落に適用します。このプロパティにより、段落が次の段落と連続して表示されるようになり、段落間の改ページが効果的に防止されます。

```csharp
    foreach (Paragraph para in cell.Paragraphs)
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
```

このループは各セル内のすべての段落をチェックします。条件は、`KeepWithNext`プロパティを最後の行の最後の段落に適用します。そうしないと、次の段落がないため、プロパティは効果がありません。

## ステップ5: ドキュメントを保存する

最後に、`KeepWithNext`プロパティを変更するには、変更したドキュメントを保存する必要があります。

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

この行は、元のファイルをそのまま残して、更新されたドキュメントを新しい名前で保存します。結果のファイルを開くと、表が 2 ページに分割されていないことがわかります。

## 結論

これで完了です。これらの簡単な手順に従うだけで、Aspose.Words for .NET を使用して Word 文書内の表がページ間で分割されるのを簡単に防ぐことができます。レポート、契約書、その他の文書のいずれで作業する場合でも、表をそのままにしておくと、より洗練されたプロフェッショナルな外観が保証されます。

Aspose.Words の優れた点は、柔軟性と使いやすさです。Microsoft Word をマシンにインストールしなくても、プログラムで Word 文書を操作できます。テーブルをまとめるコツをつかんだら、ライブラリの他の機能を調べて、文書処理スキルを次のレベルに引き上げましょう。

## よくある質問

### このコードを使用した後も、テーブルがページ間で分割されるのはなぜですか?

テーブルがまだ壊れている場合は、`KeepWithNext`プロパティを正しく設定してください。各セルの最後の段落を除くすべての段落にこのプロパティが設定されていることを再確認してください。

### 特定の行だけをまとめることはできますか?

はい、選択的に適用できます`KeepWithNext`テーブル内の特定の行または段落にプロパティを適用して、どの部分を一緒に保持するかを制御します。

### この方法は大きなテーブルでも機能しますか?

非常に大きな表の場合、表全体を 1 ページに収めるのに十分なスペースがない場合は、Word によって表が複数のページに分割されることがあります。大きな表に対応するには、表の書式設定や余白を調整することを検討してください。

### この方法を他のドキュメント形式でも使用できますか?

はい。Aspose.Words for .NET は、DOC、DOCX、PDF などの多くの形式をサポートしています。同じ方法が、テーブルをサポートするすべての形式で機能します。

### Aspose.Words for .NET は無料のライブラリですか?

 Aspose.Words for .NETは無料トライアルを提供していますが、すべての機能にアクセスするにはライセンスを購入する必要があります。ライセンスオプションについては、[Aspose 購入ページ](https://purchase.aspose.com/buy).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
