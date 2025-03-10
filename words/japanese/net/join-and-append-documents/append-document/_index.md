---
title: ドキュメントを追加
linktitle: ドキュメントを追加
second_title: Aspose.Words ドキュメント処理 API
description: この包括的なステップバイステップ ガイドでは、Aspose.Words for .NET を使用して Word 文書を追加する方法を説明します。ドキュメント ワークフローの自動化に最適です。
weight: 10
url: /ja/net/join-and-append-documents/append-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ドキュメントを追加


## 導入

こんにちは! 元の書式をそのままに、2 つの Word 文書を 1 つに結合したいと思ったことはありませんか? レポートをコンパイルする場合でも、広範なプロジェクト ドキュメントを作成する場合でも、または単にドキュメント管理を合理化しようとする場合でも、Aspose.Words for .NET を使用すると作業がずっと簡単になります。このチュートリアルでは、Aspose.Words for .NET を使用して 1 つの Word 文書を別の Word 文書に追加する方法を、各手順を詳細に説明しながら説明します。このガイドを読み終える頃には、プロのように文書を結合できるようになります。

## 前提条件

細かい点に入る前に、必要なものがすべて揃っているかどうか確認しましょう。

1. C# の基礎知識: C# の構文と概念に精通している必要があります。
2.  Aspose.Words for .NET: ダウンロード[ここ](https://releases.aspose.com/words/net/)探索だけなら、[無料トライアル](https://releases.aspose.com/).
3. Visual Studio: 最新バージョンであればどれでも動作しますが、最新バージョンが推奨されます。
4. .NET Framework: システムにインストールされていることを確認します。

準備はできましたか? 素晴らしい! さあ始めましょう。

## 名前空間のインポート

Aspose.Words for .NET の使用を開始するには、必要な名前空間をインポートする必要があります。この手順により、必要なすべてのクラスとメソッドにアクセスできるようになります。

```csharp
using System;
using Aspose.Words;
```

これらの名前空間は、Word 文書の作成、操作、保存に不可欠です。

## ステップ1: ドキュメントディレクトリの設定

まず、ドキュメントが保存されているディレクトリを指定する必要があります。これにより、Aspose.Words は操作するファイルを見つけやすくなります。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

交換する`"YOUR DOCUMENT DIRECTORY"`ドキュメントへの実際のパスを入力します。

## ステップ2: ソースドキュメントと宛先ドキュメントの読み込み

次に、ソース ドキュメント (追加するドキュメント) と宛先ドキュメント (ソースが追加されるドキュメント) を読み込みます。

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

ここでは2つの`Document`オブジェクト。`srcDoc`ソース文書を表し、`dstDoc`宛先ドキュメントを表します。

## ステップ3: ソース文書を宛先文書に追加する

ここで、興味深い部分、つまり、元の書式をそのまま維持しながらソース ドキュメントを宛先ドキュメントに追加します。

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

このステップでは、`AppendDocument`2つの文書を結合する方法。`ImportFormatMode.KeepSourceFormatting`パラメータにより、ソース ドキュメントの書式が保持されます。

## ステップ4: 結合したドキュメントを保存する

ドキュメントを追加した後、最後の手順として、結合したドキュメントを新しい名前で保存します。

```csharp
dstDoc.Save(dataDir + "AppendedDocument.docx");
```

ここでは、追加されたコンテンツが含まれていることを示す説明的なファイル名で追加されたドキュメントを保存します。

## 結論

これで完了です。Aspose.Words for .NET を使用して Word 文書を別の文書に追加する方法を学習しました。このチュートリアルでは、環境の設定、文書の読み込み、元の書式を維持したまま文書を別の文書に追加する方法、結合した文書を保存する方法について説明しました。Aspose.Words にはさまざまな機能がありますので、ぜひ詳細を確認してください。[APIドキュメント](https://reference.aspose.com/words/net/)その潜在能力を最大限に引き出すために。

## よくある質問

### 1. Aspose.Words for .NET とは何ですか?

Aspose.Words for .NET は、開発者が Word ドキュメントをプログラムで作成、操作、変換できるようにする強力なライブラリです。ドキュメント関連のタスクを自動化するのに最適です。

### 2. Aspose.Words for .NET を無料で使用できますか?

 Aspose.Words for .NETを試すには、[無料トライアル](https://releases.aspose.com/)長期使用にはライセンスを購入する必要があります。

### 3. ドキュメントを追加するときに書式設定が保持されるようにするにはどうすればよいですか?

使用`ImportFormatMode.KeepSourceFormatting`パラメータの`AppendDocument`ソース ドキュメントの書式を保持する方法。

### 4. Aspose.Words for .NET のサポートを受けるにはどうすればよいですか?

サポートを受けるには、[Aspose サポート フォーラム](https://forum.aspose.com/c/words/8).

### 5. 異なる形式の文書を追加できますか?

はい、Aspose.Words はさまざまな形式をサポートしており、DOCX、DOC、RTF などのさまざまな形式のドキュメントを追加できます。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
