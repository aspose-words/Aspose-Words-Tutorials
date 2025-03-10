---
title: 順序付きリスト
linktitle: 順序付きリスト
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して Word 文書に順序付きリストを作成する方法を、ステップバイステップ ガイドで学習します。文書作成の自動化に最適です。
weight: 10
url: /ja/net/working-with-markdown/ordered-list/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 順序付きリスト

## 導入

それで、Aspose.Words for .NET を使って、素晴らしい Word 文書をプログラムで作成することに決めたのですね。素晴らしい選択です! 今日は、Word 文書で順序付きリストを作成する方法を詳しく説明します。ステップ バイ ステップで説明しますので、コーディング初心者でも熟練したプロでも、このガイドは非常に役立ちます。さあ、始めましょう!

## 前提条件

コードに進む前に、いくつか必要なものがあります。

1. Aspose.Words for .NET: Aspose.Words for .NETがインストールされていることを確認してください。インストールされていない場合はダウンロードできます。[ここ](https://releases.aspose.com/words/net/).
2. 開発環境: Visual Studio またはその他の .NET 互換 IDE。
3. C# の基礎知識: 簡単に理解するには、C# の基礎を理解している必要があります。

## 名前空間のインポート

プロジェクトで Aspose.Words を使用するには、必要な名前空間をインポートする必要があります。これは、作業を開始する前にツールボックスを設定するようなものです。

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
```

コードを一口サイズのステップに分解して、各部分を説明しましょう。準備はいいですか? さあ、始めましょう!

## ステップ1: ドキュメントを初期化する

まず最初に、新しいドキュメントを作成する必要があります。これは、コンピューター上で空白の Word ドキュメントを開くようなものと考えてください。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

ここでは、新しいドキュメントと DocumentBuilder オブジェクトを初期化しています。DocumentBuilder はペンのようなもので、ドキュメントにコンテンツを書き込むことができます。

## ステップ2: 番号付きリスト形式を適用する

ここで、デフォルトの番号付きリスト形式を適用してみましょう。これは、番号付きの箇条書きを使用するように Word 文書を設定するのと似ています。

```csharp
builder.ListFormat.ApplyNumberDefault();
```

このコード行はリストの番号付けを設定します。簡単ですよね?

## ステップ3: リスト項目を追加する

次に、リストにいくつかの項目を追加してみましょう。買い物リストを書き留めていると想像してください。

```csharp
builder.Writeln("Item 1");
builder.Writeln("Item 2");
```

これらの行を使用して、最初の 2 つの項目をリストに追加します。

## ステップ4: リストをインデントする

アイテムの下にサブアイテムを追加したい場合はどうすればいいでしょうか? やってみましょう!

```csharp
builder.ListFormat.ListIndent();

builder.Writeln("Item 2a");
builder.Writeln("Item 2b");
```

の`ListIndent`メソッドはリストをインデントしてサブリストを作成します。これで、ネストされた ToDo リストのような階層型リストが作成されます。

## 結論

プログラムで Word 文書に順序付きリストを作成するのは、最初は大変に思えるかもしれませんが、Aspose.Words for .NET を使えば簡単です。これらの簡単な手順に従うだけで、文書にリストを簡単に追加して管理できます。レポートを生成する場合でも、構造化された文書を作成する場合でも、ワークフローを自動化する場合でも、Aspose.Words for .NET が対応します。今すぐ始めましょう。コーディングを開始して、魔法が繰り広げられるのを見てください。

## よくある質問

### リストの番号付けスタイルをカスタマイズできますか?  
はい、番号のスタイルは、`ListFormat`プロパティ。ローマ数字、文字などのさまざまな番号スタイルを設定できます。

### インデントのレベルをさらに追加するにはどうすればよいですか?  
あなたは`ListIndent`メソッドを複数回実行して、より深いレベルのサブリストを作成します。`ListIndent`インデントを 1 レベル追加します。

### 箇条書きと番号付きリストを混在させてもいいですか?  
もちろんです！同じ文書内で異なるリスト形式を適用するには、`ListFormat`財産。

### 以前のリストから番号を続けて付けることは可能ですか?  
はい、同じリスト形式を使用して番号付けを継続できます。Aspose.Words を使用すると、異なる段落間でのリスト番号付けを制御できます。

### リスト形式を削除するにはどうすればよいですか?  
リスト形式を削除するには、`ListFormat.RemoveNumbers()`これにより、リスト項目が通常の段落に戻ります。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
