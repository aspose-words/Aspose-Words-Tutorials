---
"description": "詳細なステップバイステップ ガイドを使用して、Aspose.Words for .NET を使用して Word 文書内の表のフローティング位置を制御する方法を学習します。"
"linktitle": "フローティングテーブルの位置"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "フローティングテーブルの位置"
"url": "/ja/net/programming-with-tables/floating-table-position/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# フローティングテーブルの位置

## 導入

Aspose.Words for .NET を使って、Word 文書内の表の位置を操作する世界に飛び込んでみませんか？さあ、シートベルトを締めましょう。今日は、表のフローティング位置を簡単に制御する方法を学びます。あっという間に、表の配置の達人になれるはずです！

## 前提条件

このエキサイティングな旅に乗り出す前に、必要なものがすべて揃っていることを確認しましょう。

1. Aspose.Words for .NETライブラリ：最新バージョンであることを確認してください。最新バージョンでない場合は、 [ここからダウンロード](https://releases。aspose.com/words/net/).
2. .NET Framework: 開発環境が .NET で設定されていることを確認します。
3. 開発環境: Visual Studio または任意の推奨 IDE。
4. Word 文書: 表が含まれる Word 文書を用意します。

## 名前空間のインポート

まず、.NETプロジェクトに必要な名前空間をインポートする必要があります。C#ファイルの先頭に追加するスニペットは次のとおりです。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;
```

## ステップバイステップガイド

それでは、プロセスをシンプルで理解しやすいステップに分解してみましょう。

## ステップ1：ドキュメントを読み込む

まず最初に、Word文書を読み込む必要があります。ここに表が配置されています。

```csharp
// ドキュメントディレクトリへのパス 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

Word文書をキャンバス、そして表をその上のアート作品だと想像してみてください。私たちの目標は、このアートをキャンバス上の希望の場所に正確に配置することです。

## ステップ2: テーブルにアクセスする

次に、ドキュメント内の表にアクセスする必要があります。通常は、ドキュメント本体の最初の表を操作します。

```csharp
Table table = doc.FirstSection.Body.Tables[0];
```

このステップは、物理的なドキュメント内で作業したい表を見つけるようなものだと考えてください。変更を加えるには、その表がどこにあるかを正確に把握しておく必要があります。

## ステップ3：水平位置を設定する

次に、表の水平位置を設定しましょう。これにより、表がドキュメントの左端からどのくらい離れた位置に配置されますか？

```csharp
table.AbsoluteHorizontalDistance = 10;
```

これを文書上で表を水平に動かすものとしてイメージしてください。 `AbsoluteHorizontalDistance` 左端からの正確な距離です。

## ステップ4: 垂直方向の配置を設定する

表の垂直方向の配置も設定する必要があります。これにより、表が周囲のテキストの垂直方向の中央に配置されます。

```csharp
table.RelativeVerticalAlignment = VerticalAlignment.Center;
```

壁に絵を掛けるところを想像してみてください。美しく見せるために、絵が垂直方向の中央に配置されるようにしたいですよね。このステップでそれが実現できます。

## ステップ5: 変更したドキュメントを保存する

最後に、テーブルを配置した後、変更したドキュメントを保存します。

```csharp
doc.Save(dataDir + "WorkingWithTables.FloatingTablePosition.docx");
```

これは編集したドキュメントで「保存」をクリックするのと同じです。すべての変更が保存されます。

## 結論

これで完了です！Aspose.Words for .NET を使って、Word 文書内の表のフローティング位置を制御する方法をマスターしました。これらのスキルを活用すれば、表を最適な位置に配置して、文書の読みやすさと美しさを向上させることができます。Aspose.Words for .NET の幅広い機能をぜひお試しください。

## よくある質問

### ページの上部からの表の垂直距離を設定できますか?

はい、使えます `AbsoluteVerticalDistance` ページの上端からのテーブルの垂直距離を設定するプロパティ。

### 表をドキュメントの右側に揃えるにはどうすればよいでしょうか?

表を右揃えにするには、 `HorizontalAlignment` テーブルの特性 `HorizontalAlignment。Right`.

### 同じドキュメント内で複数のテーブルを異なる位置に配置することは可能ですか?

もちろんです！複数のテーブルに個別にアクセスして位置を設定するには、 `Tables` ドキュメント内のコレクション。

### 水平方向の配置に相対位置を使用できますか?

はい、Aspose.Wordsは、次のようなプロパティを使用して、水平方向と垂直方向の両方の配置の相対的な配置をサポートしています。 `RelativeHorizontalAlignment`。

### Aspose.Words は、ドキュメントの異なるセクションにあるフローティング テーブルをサポートしていますか?

はい、ドキュメント内の特定のセクションとそのテーブルにアクセスすることで、フローティング テーブルをさまざまなセクションに配置できます。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}