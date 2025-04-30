---
"description": "Aspose.Words for .NETを使用して、表がページ間で分割されるのを防ぐ方法をステップバイステップで解説します。整然としたプロフェッショナルなWord文書を作成できます。"
"linktitle": "テーブルを一緒に保つ"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "テーブルを一緒に保つ"
"url": "/ja/net/join-and-append-documents/keep-source-together/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# テーブルを一緒に保つ

## 導入

表は多くのWord文書に欠かせない要素ですが、表が2ページにまたがってしまう場合があります。これは文書の流れを乱し、読みやすさを損なう可能性があります。表全体を1ページにまとめる方法があれば便利だと思いませんか？Aspose.Words for .NETを使えば、この問題を簡単に解決できます。このチュートリアルでは、表がページにまたがって表示されるのを防ぎ、文書をすっきりとプロフェッショナルな印象に仕上げる方法を解説します。

## 前提条件

チュートリアルに進む前に、スムーズに進めるために必要なものがすべて揃っていることを確認しましょう。

### Aspose.Words for .NET ライブラリ

まず、Aspose.Words for .NET をインストールする必要があります。これは、Word 文書をプログラムで操作できる強力なライブラリです。

- [Aspose.Words for .NET をダウンロード](https://releases.aspose.com/words/net/)

### 開発環境

C# コードを実行するには、次のような開発環境をセットアップする必要があります。

- Visual Studio（最新バージョン）
- .NET Framework 2.0以降

### 表を含むWord文書

表を含むWord文書が必要です。このチュートリアルでは、「表」というサンプル文書を使用します。 `"Table spanning two pages.docx"`このファイルには、現在 2 ページにまたがる表が含まれています。

### 一時ライセンス（オプション）

Aspose.Wordsには無料トライアルが付属していますが、 [一時ライセンス](https://purchase.aspose.com/temporary-license/) ライブラリの潜在能力を最大限に引き出します。

## パッケージのインポート

コードを記述する前に、Aspose.Words for .NET を使用するために必要な名前空間をインポートする必要があります。コードファイルの先頭に以下のインポートを追加してください。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

これらの名前空間は次のようなクラスへのアクセスを提供します `Document`、 `Table`、 `Cell`、およびこのチュートリアルで使用するその他のツールについて説明します。

## ステップ1：ドキュメントを読み込む

まず最初に、表を含むWord文書を読み込みましょう。そのためには、 `Document` Aspose.Words のクラスです。このクラスを使用すると、Word ファイルをプログラムで開いて操作できます。

```csharp
// ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENTS DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

このコードスニペットでは、ドキュメントの場所を指定します。 `"YOUR DOCUMENTS DIRECTORY"` ドキュメントが保存されている実際のディレクトリに置き換えます。

## ステップ2: テーブルにアクセスする

ドキュメントが読み込まれたら、次のステップは、一緒に保持したい表にアクセスすることです。この例では、その表がドキュメント内の最初の表であると仮定します。

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

このコード行は、文書内の最初の表を検索します。 `GetChild` メソッドは特定のタイプのノードを取得します。この場合は `NodeType.Table`。その `0` 最初のテーブルが必要であり、 `true` フラグにより、すべての子ノードを再帰的に検索することが保証されます。

## ステップ3: 表のセルをループする

次に、表の各セルをループ処理する必要があります。表には複数の行があり、各行には複数のセルが含まれているため、各セルを反復処理し、ページをまたいで改行されないようにします。

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
```

ここ、 `GetChildNodes` 表内のすべてのセルを取得し、各セルをループ処理します。 `EnsureMinimum()` このメソッドは、各セルに少なくとも 1 つの段落が含まれていることを確認します。空のセルがあると、後で問題が発生する可能性があるためです。

## ステップ4: KeepWithNextプロパティを設定する

表がページをまたいで改ページされないようにするには、 `KeepWithNext` 表内の各段落にプロパティを設定します。このプロパティにより、段落が次の段落と連続して配置され、段落間の改ページを効果的に防止できます。

```csharp
    foreach (Paragraph para in cell.Paragraphs)
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
```

このループは各セル内のすべての段落をチェックします。条件は、 `KeepWithNext` プロパティを最後の行の最後の段落に適用します。そうしないと、次の段落が存在しないため、プロパティは効果がありません。

## ステップ5: ドキュメントを保存する

最後に、 `KeepWithNext` プロパティを変更するには、変更したドキュメントを保存する必要があります。

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

この行は、元のファイルを維持しながら、更新されたドキュメントを新しい名前で保存します。保存したファイルを開くと、表が2ページに分割されていないことがわかります。

## 結論

これで完了です！これらの簡単な手順に従うだけで、Aspose.Words for .NET を使って Word 文書内の表がページをまたいで改ページされるのを簡単に防ぐことができます。レポート、契約書、その他の文書を作成する場合でも、表を改ページせずにそのままにしておくことで、より洗練されたプロフェッショナルな外観を実現できます。

Aspose.Words の優れた点は、その柔軟性と使いやすさです。Microsoft Word をマシンにインストールしていなくても、Word 文書をプログラムで操作できます。表の作成方法を習得したら、ライブラリの他の機能も試して、ドキュメント処理スキルを次のレベルに引き上げましょう。

## よくある質問

### このコードを使用した後でも、テーブルがページ間で分割されるのはなぜですか?

テーブルがまだ壊れている場合は、 `KeepWithNext` プロパティを正しく設定してください。各セルの最後の段落を除くすべての段落でこのプロパティが設定されていることを確認してください。

### 特定の行だけをまとめることはできますか?

はい、選択的に適用できます `KeepWithNext` 表内の特定の行または段落にプロパティを適用して、どの部分を一緒にしておくかを制御します。

### この方法は大きなテーブルでも機能しますか?

非常に大きな表の場合、1ページに表全体を収めるスペースが足りないと、Wordでは表が複数のページに分割されることがあります。大きな表を収容できるように、表の書式設定や余白を調整することを検討してください。

### この方法は他のドキュメント形式でも使用できますか?

はい！Aspose.Words for .NET は、DOC、DOCX、PDF など、多くの形式をサポートしています。表をサポートするすべての形式で同じ方法が使えます。

### Aspose.Words for .NET は無料のライブラリですか?

Aspose.Words for .NETは無料トライアルを提供していますが、すべての機能にアクセスするにはライセンスを購入する必要があります。ライセンスオプションについては、 [Aspose 購入ページ](https://purchase。aspose.com/buy).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}