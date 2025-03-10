---
title: テーブルを分割
linktitle: テーブルを分割
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して Word 文書内の表を分割する方法を学びます。ステップバイステップのガイドにより、表の管理が簡単かつ効率的になります。
weight: 10
url: /ja/net/programming-with-tables/split-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# テーブルを分割

## 導入

Word 文書で大きな表を操作していて、それを 2 つのより小さくて扱いやすい表に分割したいと思ったことはありませんか? 今日は、Aspose.Words for .NET を使用してこれを実現する方法について詳しく説明します。大規模なデータ テーブルを扱っている場合でも、複雑なドキュメント構造を扱っている場合でも、表を分割すると読みやすさと整理性が向上します。Aspose.Words for .NET を使用して表を分割する手順を順に見ていきましょう。

## 前提条件

チュートリアルに進む前に、次のものを用意してください。

1.  Aspose.Words for .NET ライブラリ: Aspose.Words for .NET ライブラリをダウンロードしてインストールしたことを確認してください。[Aspose リリース ページ](https://releases.aspose.com/words/net/).
2. 開発環境: Visual Studio などの .NET フレームワークをサポートする開発環境をセットアップします。
3. サンプル文書: Word文書を準備する(`Tables.docx`) を少なくとも 1 つのテーブルに分割操作を適用します。

## 名前空間のインポート

まず、プロジェクトに必要な名前空間をインポートします。これにより、Aspose.Words によって提供されるクラスとメソッドにアクセスできるようになります。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## ステップ1: ドキュメントを読み込む

まず、分割するテーブルを含むドキュメントを読み込みます。ドキュメントへの正しいパスを指定してください。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Tables.docx");
```

## ステップ2: 分割するテーブルを特定する

次に、分割するテーブルを識別して取得します。この例では、ドキュメント内の最初のテーブルをターゲットにします。

```csharp
Table firstTable = (Table)doc.GetChild(NodeType.Table, 0, true);
```

## ステップ3: 分割する行を選択する

テーブルを分割する行を決定します。ここでは、3 行目 (3 行目を含む) でテーブルを分割します。

```csharp
Row row = firstTable.Rows[2];
```

## ステップ4: 新しいテーブルコンテナを作成する

元のテーブルから移動される行を保持するための新しいテーブル コンテナーを作成します。

```csharp
Table table = (Table)firstTable.Clone(false);
```

## ステップ5: 新しいテーブルコンテナを挿入する

ドキュメント内の元のテーブルの直後に新しいテーブル コンテナーを挿入します。

```csharp
firstTable.ParentNode.InsertAfter(table, firstTable);
```

## ステップ6: バッファ段落を追加する

つのテーブルが分離されていることを確認するために、テーブル間にバッファ段落を追加します。

```csharp
firstTable.ParentNode.InsertAfter(new Paragraph(doc), firstTable);
```

## ステップ7: 行を新しいテーブルに移動する

元のテーブルから新しいテーブル コンテナーに行を移動します。このループは、指定された行 (含む) が移動されるまで続行されます。

```csharp
Row currentRow;
do
{
    currentRow = firstTable.LastRow;
    table.PrependChild(currentRow);
} while (currentRow != row);
```

## ステップ8: ドキュメントを保存する

最後に、テーブルを分割した変更済みのドキュメントを保存します。

```csharp
doc.Save(dataDir + "WorkingWithTables.SplitTable.docx");
```

## 結論

これで完了です。これらの手順に従うと、Aspose.Words for .NET を使用して Word 文書内の表を簡単に分割できます。この方法により、大きな表をより効率的に管理でき、文書の読みやすさと構成が向上します。試してみて、Word 文書内の表の操作がいかに簡単になるかを確認してください。

## よくある質問

### テーブルを複数の行に分割できますか?
はい、分割ポイントごとにプロセスを繰り返すことで、テーブルを複数の行で分割できます。

### 元の表の書式設定はどうなりますか?
新しいテーブルは元のテーブルの書式設定を継承します。必要に応じて、特定の書式設定の変更を新しいテーブルに適用できます。

### テーブルを再び結合することは可能ですか?
はい、同様の方法を使用して、あるテーブルから別のテーブルに行を移動することで、テーブルを結合できます。

### この方法はネストされたテーブルでも機能しますか?
はい、Aspose.Words for .NET はネストされたテーブルでの操作もサポートしています。

### 複数のドキュメントに対してこのプロセスを自動化できますか?
もちろんです! 複数のドキュメントのテーブル分割プロセスを自動化するスクリプトまたはアプリケーションを作成できます。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
