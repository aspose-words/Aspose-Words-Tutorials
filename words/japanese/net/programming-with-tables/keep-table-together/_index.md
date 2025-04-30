---
"description": "Aspose.Words for .NET を使用して、Word 文書内の表がページをまたいで改ページされないようにする方法を学びましょう。ガイドに従って、プロフェッショナルで読みやすい文書を作成しましょう。"
"linktitle": "テーブルを一緒に保つ"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "テーブルを一緒に保つ"
"url": "/ja/net/programming-with-tables/keep-table-together/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# テーブルを一緒に保つ

## 導入

Word文書の表が2ページに分割されてしまい、イライラしたことはありませんか？まるで、せっかく丁寧にレイアウトした情報が途中で途切れてしまったかのようです。表を1ページにまとめることは、読みやすさと見栄えを良くするために不可欠です。レポート、プロジェクト提案書、あるいは個人的な文書など、どんな文書でも、表が分割されると見苦しく感じることがあります。幸いなことに、Aspose.Words for .NETには、この問題を解決する便利な機能が備わっています。このチュートリアルでは、表を元の状態に保ち、見栄えを良くするための手順を順に解説します。さあ、始めましょう！

## 前提条件

始める前に、次のものを用意してください。

1. Aspose.Words for .NET - まだインストールしていない場合は、こちらからダウンロードできます。 [ここ](https://releases。aspose.com/words/net/).
2. 表を含む Word 文書 - 複数のページにわたる表を含むサンプル文書を操作します。
3. C# の基本知識 - このチュートリアルでは、C# プログラミングの基本を理解していることを前提としています。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートしましょう。これにより、Aspose.Words for .NET から必要なクラスとメソッドにアクセスできるようになります。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

プロセスを分かりやすく、理解しやすいステップに分解してみましょう。まずドキュメントを読み込み、最後にテーブルがそのまま残る更新されたドキュメントを保存します。

## ステップ1：ドキュメントを読み込む

Word文書を扱うには、まずそれを読み込む必要があります。 `Document` このためのクラスです。

```csharp
// ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## ステップ2: テーブルにアクセスする

次に、まとめておきたい表を取得する必要があります。ここでは、文書内の最初の表だと仮定します。

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## ステップ3: 段落のKeepWithNextを設定する

表がページをまたいで改ページされないようにするには、 `KeepWithNext` 最後の行の最後の段落を除く、表内の各段落のプロパティ。

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
    foreach (Paragraph para in cell.Paragraphs)
    {
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
    }
}
```

## ステップ4: ドキュメントを保存する

最後に、更新したドキュメントを保存します。これにより変更が適用され、表が1ページに収まります。

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

## 結論

これで完了です！わずか数行のコードで、Word文書内の表がページをまたいで分割されるのを防ぐことができます。このシンプルでありながら効果的なソリューションにより、表は整然としたプロフェッショナルな外観を保ち、文書の読みやすさが向上します。Aspose.Words for .NET を使えば、こうした書式設定の問題を簡単に処理できるため、優れたコンテンツの作成に集中できます。

## よくある質問

### この方法を使用して複数のテーブルをまとめることはできますか?  
はい、ドキュメント内の各テーブルを反復処理することで、同じロジックを複数のテーブルに適用できます。

### 表が大きすぎて 1 ページに収まらない場合はどうすればよいですか?  
表が1ページに収まらないほど大きい場合でも、複数のページにまたがって表示されます。この方法により、小さな表は分割されることなくそのまま表示されます。

### ドキュメント内のすべてのテーブルに対してこれを自動化する方法はありますか?  
はい、文書内のすべての表をループして適用することができます。 `KeepWithNext` 各段落にプロパティを設定します。

### Aspose.Words for .NET には有料ライセンスが必要ですか?  
無料トライアルから始めることができます [ここ](https://releases.aspose.com/)ただし、完全な機能を使用するには、有料ライセンスをお勧めします。

### テーブルをまとめたまま、他の書式設定を適用できますか?  
もちろんです！表を 1 ページにまとめたまま、必要に応じて書式設定できます。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}