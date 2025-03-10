---
title: 連続参加
linktitle: 連続参加
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して 2 つの Word 文書をシームレスに結合する方法を学びます。スムーズで効率的な文書の結合については、ステップ バイ ステップ ガイドに従ってください。
weight: 10
url: /ja/net/join-and-append-documents/join-continuous/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 連続参加

## 導入

2 つの Word 文書を途切れることなく 1 つに結合したいとお考えですか? Aspose.Words for .NET では、連続セクション区切り機能を使用してこれを実現する素晴らしい方法を提供しています。このチュートリアルでは、プロセスをステップごとに説明し、手間をかけずに簡単に文書を結合できるようにします。さっそく始めましょう!

## 前提条件

始める前に、必要なものがすべて揃っていることを確認しましょう。

-  .NET 用 Aspose.Words: まだダウンロードしていない場合は、ダウンロードしてインストールしてください。[Aspose.Words for .NET](https://releases.aspose.com/words/net/).
- 開発環境: Visual Studio またはその他の .NET 開発環境を使用できます。
- サンプル ドキュメント: 結合する 2 つの Word ドキュメントを用意します。

## 名前空間のインポート

Aspose.Words for .NET を使用するには、プロジェクトに必要な名前空間をインポートする必要があります。手順は次のとおりです。

```csharp
using Aspose.Words;
```

ここで、わかりやすくするために、例を複数のステップに分解してみましょう。

## ステップ1: ドキュメントディレクトリを設定する

まず、ドキュメントが保存されているディレクトリを設定する必要があります。これにより、コードは結合するファイルを見つけることができるようになります。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

交換する`"YOUR DOCUMENT DIRECTORY"`ドキュメントが保存されている実際のパスを入力します。

## ステップ2: ソースドキュメントと宛先ドキュメントを読み込む

次に、ソース ドキュメントとターゲット ドキュメントをプログラムに読み込みます。これらは結合する 2 つのドキュメントです。

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

ファイル名とパスが実際に使用するファイルと一致していることを確認します。

## ステップ3: セクションの開始を連続として設定する

ソース文書の内容を宛先文書の直後に表示させるには、`SectionStart`ソース文書の最初のセクションのプロパティを`Continuous`.

```csharp
//ドキュメントを、宛先ドキュメントのコンテンツの直後に表示します。
srcDoc.FirstSection.PageSetup.SectionStart = SectionStart.Continuous;
```

これにより、ドキュメントを結合したときにドキュメント間に中断が生じなくなります。

## ステップ4: ソースドキュメントを追加する

ここで、ソース ドキュメントを宛先ドキュメントに追加します。この手順により、ソース ドキュメントのコンテンツが宛先ドキュメントの末尾に追加されることが保証されます。

```csharp
//ソース ドキュメントにある元のスタイルを使用して、ソース ドキュメントを追加します。
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

使用`ImportFormatMode.KeepSourceFormatting`ソース ドキュメントの書式設定が最終的な結合ドキュメントに保持されることを保証します。

## ステップ5: 結合した文書を保存する

最後に、結合したドキュメントを指定したディレクトリに保存します。これでドキュメントの結合プロセスは完了です。

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.JoinContinuous.docx");
```

パスとファイル名がニーズに合っていることを確認してください。

## 結論

これで完了です。わずか数行のコードで、Aspose.Words for .NET を使用して 2 つの Word 文書を 1 つの連続した文書に結合することができました。このプロセスは簡単なだけでなく、非常に効率的で、文書の元の書式設定が維持されます。

## よくある質問

### 2 つ以上のドキュメントを結合できますか?
はい、追加のドキュメントをロードして順番に追加することで、複数のドキュメントを結合するプロセスを繰り返すことができます。

### 元の書式は保持されますか?
はい、使用しています`ImportFormatMode.KeepSourceFormatting`ソース ドキュメントの書式が保持されることを保証します。

### Aspose.Words for .NET は .NET Core と互換性がありますか?
はい、Aspose.Words for .NET は .NET Framework と .NET Core の両方と互換性があります。

### ページ設定が異なるドキュメントを結合できますか?
はい、ただし、シームレスなマージを確実に行うには、ページ設定プロパティを調整する必要があるかもしれません。

### 問題が発生した場合、どこでサポートを受けることができますか?
 Asposeコミュニティフォーラムからサポートを受けることができます[ここ](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
