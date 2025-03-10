---
title: 相対的な水平または垂直位置を設定する
linktitle: 相対的な水平または垂直位置を設定する
second_title: Aspose.Words ドキュメント処理 API
description: このステップバイステップ ガイドでは、Aspose.Words for .NET を使用して Word 文書内の表の相対的な水平位置と垂直位置を設定する方法を学習します。
weight: 10
url: /ja/net/programming-with-tables/set-relative-horizontal-or-vertical-position/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 相対的な水平または垂直位置を設定する

## 導入

Word 文書で表を希望どおりに配置する方法に困ったことはありませんか? それはあなただけではありません。プロフェッショナルなレポートを作成する場合でも、スタイリッシュなパンフレットを作成する場合でも、表を揃えると大きな違いが生まれます。そこで Aspose.Words for .NET が役立ちます。このチュートリアルでは、Word 文書で表の相対的な水平位置または垂直位置を設定する方法をステップごとに説明します。さっそく始めましょう!

## 前提条件

始める前に、以下のものを用意してください。

1.  Aspose.Words for .NET: まだダウンロードしていない場合は、ダウンロードできます。[ここ](https://releases.aspose.com/words/net/).
2. 開発環境: Visual Studio またはその他の .NET 互換 IDE。
3. C# の基本知識: このチュートリアルでは、C# プログラミングの基礎を理解していることを前提としています。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートする必要があります。これは、Aspose.Words の機能にアクセスするために不可欠です。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## ステップ1: ドキュメントを読み込む

まず、Word 文書をプログラムに読み込む必要があります。手順は次のとおりです。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

このコード スニペットは、ドキュメント ディレクトリへのパスを設定し、作業する特定のドキュメントを読み込みます。読み込みの問題を回避するために、ドキュメント パスが正しいことを確認してください。

## ステップ2: テーブルにアクセスする

次に、ドキュメント内の表にアクセスする必要があります。通常は、本文セクションの最初の表を操作します。

```csharp
Table table = doc.FirstSection.Body.Tables[0];
```

このコード行は、ドキュメント本体から最初のテーブルを取得します。ドキュメントに複数のテーブルがある場合は、それに応じてインデックスを調整できます。

## ステップ3: 水平位置を設定する

ここで、特定の要素を基準にしてテーブルの水平位置を設定してみましょう。この例では、列を基準にして配置します。

```csharp
table.HorizontalAnchor = RelativeHorizontalPosition.Column;
```

設定することで`HorizontalAnchor`に`RelativeHorizontalPosition.Column`、テーブルが存在する列に対して水平方向に揃えるように指示します。

## ステップ4: 垂直位置を設定する

水平方向の配置と同様に、垂直方向の位置も設定できます。ここでは、ページを基準にして配置します。

```csharp
table.VerticalAnchor = RelativeVerticalPosition.Page;
```

設定`VerticalAnchor`に`RelativeVerticalPosition.Page`テーブルがページに応じて垂直に配置されるようにします。

## ステップ5: ドキュメントを保存する

最後に、変更内容を新しいドキュメントに保存します。これは、変更内容が確実に保存されるようにするための重要な手順です。

```csharp
doc.Save(dataDir + "WorkingWithTables.SetFloatingTablePosition.docx");
```

このコマンドは、変更されたドキュメントを新しい名前で保存し、元のファイルを上書きしないようにします。

## 結論

これで完了です。Aspose.Words for .NET を使用して、Word 文書内の表の相対的な水平位置と垂直位置を設定できました。この新しいスキルにより、文書のレイアウトと読みやすさが向上し、よりプロフェッショナルで洗練された外観になります。さまざまな位置を試して、ニーズに最適な位置を見つけてください。

## よくある質問

### 他の要素を基準にしてテーブルを配置できますか?  
はい、Aspose.Words を使用すると、余白、ページ、列などのさまざまな要素を基準にしてテーブルを配置できます。

### Aspose.Words for .NET を使用するにはライセンスが必要ですか?  
はい、ライセンスを購入できます[ここ](https://purchase.aspose.com/buy)または一時免許を取得する[ここ](https://purchase.aspose.com/temporary-license/).

### Aspose.Words for .NET の無料試用版はありますか?  
もちろんです！無料トライアルをダウンロードできます[ここ](https://releases.aspose.com/).

### Aspose.Words を他のプログラミング言語で使用できますか?  
Aspose.Words は主に .NET 向けに設計されていますが、Java、Python、その他のプラットフォーム用のバージョンも用意されています。

### より詳細なドキュメントはどこで見つかりますか?  
より詳しい情報については、Aspose.Wordsのドキュメントをご覧ください。[ここ](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
