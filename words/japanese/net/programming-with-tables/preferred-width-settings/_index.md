---
"description": "このステップバイステップ ガイドでは、Aspose.Words for .NET で絶対幅、相対幅、自動幅の設定を使用してテーブルを作成する方法を学習します。"
"linktitle": "推奨幅設定"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "推奨幅設定"
"url": "/ja/net/programming-with-tables/preferred-width-settings/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 推奨幅設定

## 導入

表は、Word文書で情報を整理し、提示するための強力な手段です。Aspose.Words for .NETで表を操作する際、表のセルの幅を文書のレイアウトに完璧にフィットさせる複数のオプションが用意されています。このガイドでは、Aspose.Words for .NETを使用して、最適な幅で表を作成する手順を、絶対サイズ、相対サイズ、自動サイズ設定の各オプションに焦点を当てて解説します。 

## 前提条件

チュートリアルに進む前に、次のものを用意してください。

1. Aspose.Words for .NET: 開発環境にAspose.Words for .NETがインストールされていることを確認してください。ダウンロードできます。 [ここ](https://releases。aspose.com/words/net/).

2. .NET 開発環境: Visual Studio などの .NET 開発環境をセットアップします。

3. C# の基礎知識: C# プログラミングに精通していると、コード スニペットや例をよりよく理解できるようになります。

4. Aspose.Wordsドキュメント: [Aspose.Words ドキュメント](https://reference.aspose.com/words/net/) 詳細な API 情報と参考資料については、こちらをご覧ください。

## 名前空間のインポート

コーディングを始める前に、必要な名前空間を C# プロジェクトにインポートする必要があります。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

これらの名前空間は、Aspose.Words と Table オブジェクトのコア機能へのアクセスを提供し、ドキュメント テーブルを操作できるようにします。

さまざまな推奨幅設定を持つテーブルを作成するプロセスを、明確で管理しやすい手順に分解してみましょう。

## ステップ1: DocumentとDocumentBuilderを初期化する

見出し: 新しいドキュメントとドキュメントビルダーの作成

説明: まず、新しいWord文書を作成し、 `DocumentBuilder` インスタンス。 `DocumentBuilder` クラスは、ドキュメントにコンテンツを追加する簡単な方法を提供します。

```csharp
// ドキュメントを保存するパスを定義します。
string dataDir = "YOUR DOCUMENT DIRECTORY";

// 新しいドキュメントを作成します。
Document doc = new Document();

// このドキュメントの DocumentBuilder を作成します。
DocumentBuilder builder = new DocumentBuilder(doc);
```

ここで、ドキュメントを保存するディレクトリを指定し、 `Document` そして `DocumentBuilder` オブジェクト。

## ステップ2: 絶対幅を持つ最初の表セルを挿入する

表の最初のセルを40ポイントの固定幅で挿入します。これにより、表のサイズに関係なく、このセルの幅は常に40ポイントに保たれます。

```csharp
// 絶対サイズのセルを挿入します。
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPoints(40);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightYellow;
builder.Writeln("Cell at 40 points width");
```

このステップでは、表の作成を開始し、絶対幅を持つセルを挿入します。 `PreferredWidth.FromPoints(40)` メソッドはセルの幅を40ポイントに設定し、 `Shading.BackgroundPatternColor` 明るい黄色の背景色を適用します。

## ステップ3: 相対サイズのセルを挿入する

表全体の幅の20%の幅を持つ別のセルを挿入します。この相対的なサイズ設定により、セルは表の幅に比例して調整されます。

```csharp
// 相対的 (パーセント) サイズのセルを挿入します。
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(20);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
builder.Writeln("Cell at 20% width");
```

このセルの幅はテーブル全体の幅の 20% となり、さまざまな画面サイズやドキュメント レイアウトに適応できます。

### ステップ4: 自動サイズ調整セルを挿入する

最後に、テーブル内の残りの使用可能なスペースに基づいて自動的にサイズが決定されるセルを挿入します。

```csharp
// 自動サイズ調整されたセルを挿入します。
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.Auto;
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightGreen;
builder.Writeln("Cell automatically sized. その size of this cell is calculated from the table preferred width.");
builder.Writeln("In this case the cell will fill up the rest of the available space.");
```

The `PreferredWidth.Auto` この設定により、他のセルの余白を考慮して、このセルの拡大または縮小を設定できます。これにより、表のレイアウトがバランスよく、プロフェッショナルな印象を与えます。

## ステップ5: ドキュメントを完成させて保存する

すべてのセルを挿入したら、表を完成させ、指定したパスにドキュメントを保存します。

```csharp
// ドキュメントを保存します。
doc.Save(dataDir + "WorkingWithTables.PreferredWidthSettings.docx");
```

この手順では、テーブルを完成させ、指定したディレクトリに「WorkingWithTables.PreferredWidthSettings.docx」というファイル名でドキュメントを保存します。

## 結論

Aspose.Words for .NET で、好みの幅の設定で表を作成するのは、利用可能な様々なサイズ設定オプションを理解すれば簡単です。固定幅、相対幅、自動幅など、セル幅の指定方法を問わず、Aspose.Words は様々な表レイアウトシナリオを効率的に処理する柔軟性を備えています。このガイドで概説されている手順に従うことで、Word 文書内で表が適切に構造化され、視覚的に魅力的に見えるようになります。

## よくある質問

### 絶対セル幅と相対セル幅の違いは何ですか?
絶対セル幅は固定されており変化しませんが、相対幅はテーブルの合計幅に基づいて調整されます。

### 相対的な幅に負のパーセンテージを使用できますか?
いいえ、セル幅には負のパーセンテージは無効です。正のパーセンテージのみ使用できます。

### 自動サイズ調整機能はどのように機能しますか?
自動サイズ調整では、他のセルのサイズが変更された後にテーブル内の残りのスペースを埋めるようにセルの幅が調整されます。

### 幅の設定が異なるセルに異なるスタイルを適用できますか?
はい、セルの幅の設定に関係なく、さまざまなスタイルと書式を適用できます。

### テーブルの合計幅がすべてのセルの幅の合計より小さい場合はどうなりますか?
表は、使用可能なスペースに収まるようにセルの幅を自動的に調整するため、一部のセルが縮小される可能性があります。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}