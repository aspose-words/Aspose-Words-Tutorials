---
title: テーブルをまとめる
linktitle: テーブルをまとめる
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、Word 文書内の表がページ間で分割されないようにする方法を学びます。プロフェッショナルで読みやすい文書を維持するには、ガイドに従ってください。
weight: 10
url: /ja/net/programming-with-tables/keep-table-together/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# テーブルをまとめる

## 導入

Word 文書の表が 2 ページに分割されてイライラしたことはありませんか? 慎重にレイアウトした情報が、途中で突然途切れてしまったような感じです。表を 1 ページにまとめることは、読みやすさとプレゼンテーションにとって非常に重要です。レポート、プロジェクト提案、または個人的な文書のいずれであっても、表が分割されるとかなり不快になります。幸いなことに、Aspose.Words for .NET にはこの問題を解決する優れた方法があります。このチュートリアルでは、表をそのままの状態で見栄えよく保つ手順を説明します。さっそく始めましょう!

## 前提条件

始める前に、以下のものを用意してください。

1.  Aspose.Words for .NET - まだインストールしていない場合は、こちらからダウンロードできます。[ここ](https://releases.aspose.com/words/net/).
2. 表を含む Word 文書 - 複数のページにわたる表を含むサンプル文書を操作します。
3. C# の基本知識 - このチュートリアルでは、C# プログラミングの基本を理解していることを前提としています。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートしましょう。これにより、Aspose.Words for .NET から必要なクラスとメソッドにアクセスできるようになります。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

プロセスを簡単でわかりやすいステップに分解してみましょう。まずドキュメントを読み込み、最後にテーブルがそのまま残る更新されたドキュメントを保存します。

## ステップ1: ドキュメントを読み込む

 Word文書を操作するには、まずそれを読み込む必要があります。`Document`このためのクラスです。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## ステップ2: テーブルにアクセスする

次に、一緒に保持したいテーブルを取得する必要があります。ドキュメント内の最初のテーブルであると仮定します。

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## ステップ3: 段落のKeepWithNextを設定する

表がページをまたいで分割されないようにするには、`KeepWithNext`最後の行の最後の段落を除く、表の各段落のプロパティ。

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

最後に、更新されたドキュメントを保存します。これにより、変更が適用され、表が 1 ページにまとめられるようになります。

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

## 結論

これで完了です。わずか数行のコードで、Word 文書内の表が複数のページに分割されるのを防ぐことができます。このシンプルかつ効果的なソリューションにより、表が整然とプロフェッショナルな状態を保ち、文書の読みやすさが向上します。Aspose.Words for .NET を使用すると、このような書式設定の問題を簡単に処理できるため、優れたコンテンツの作成に集中できます。

## よくある質問

### この方法を使用して複数のテーブルをまとめることはできますか?  
はい、ドキュメント内の各テーブルを反復処理することで、同じロジックを複数のテーブルに適用できます。

### 表が大きすぎて 1 ページに収まらない場合はどうすればよいですか?  
表が大きすぎて 1 ページに収まらない場合でも、複数のページにまたがって表示されます。この方法により、小さい表は分割されずにそのまま残ります。

### ドキュメント内のすべてのテーブルに対してこれを自動化する方法はありますか?  
はい、文書内のすべての表をループして適用することができます。`KeepWithNext`各段落にプロパティを設定します。

### Aspose.Words for .NET には有料ライセンスが必要ですか?  
まずは無料トライアルから始めましょう[ここ](https://releases.aspose.com/)ただし、完全な機能を使用するには、有料ライセンスをお勧めします。

### テーブルをまとめたまま、他の書式設定を適用できますか?  
もちろんです! 必要に応じてテーブルをフォーマットし、1 ページにまとめることができます。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
