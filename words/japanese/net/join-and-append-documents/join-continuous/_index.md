---
"description": "Aspose.Words for .NET を使用して、2つのWord文書をシームレスに結合する方法を学びましょう。ステップバイステップのガイドに従って、スムーズかつ効率的に文書を結合しましょう。"
"linktitle": "連続参加"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "連続参加"
"url": "/ja/net/join-and-append-documents/join-continuous/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 連続参加

## 導入

2つのWord文書を途切れることなく1つの文書に結合したいとお考えですか？Aspose.Words for .NETの「連続セクション区切り」機能を使えば、これを実現できます。このチュートリアルでは、手順をステップバイステップで解説し、手間をかけずに簡単に文書を結合する方法をご紹介します。さあ、始めましょう！

## 前提条件

始める前に、必要なものがすべて揃っていることを確認しましょう。

- Aspose.Words for .NET: まだダウンロードしていない場合は、ダウンロードしてインストールしてください。 [Aspose.Words の .NET 版](https://releases。aspose.com/words/net/).
- 開発環境: Visual Studio またはその他の .NET 開発環境を使用できます。
- サンプル ドキュメント: 結合する 2 つの Word ドキュメントを用意します。

## 名前空間のインポート

Aspose.Words for .NET を使用するには、プロジェクトに必要な名前空間をインポートする必要があります。手順は以下のとおりです。

```csharp
using Aspose.Words;
```

ここで、わかりやすくするために、例を複数のステップに分解してみましょう。

## ステップ1: ドキュメントディレクトリを設定する

まず、ドキュメントが保存されているディレクトリを設定する必要があります。これにより、コードが結合するファイルを見つけられるようになります。

```csharp
// ドキュメントディレクトリへのパス 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

交換する `"YOUR DOCUMENT DIRECTORY"` ドキュメントが保存されている実際のパスを入力します。

## ステップ2: ソースドキュメントとターゲットドキュメントを読み込む

次に、結合元と結合先の文書をプログラムに読み込みます。これらが結合したい2つの文書です。

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

ファイル名とパスが実際に使用するファイルと一致していることを確認してください。

## ステップ3: セクションの開始を連続に設定する

ソース文書の内容をターゲット文書の直後に表示させるには、 `SectionStart` ソース文書の最初のセクションのプロパティを `Continuous`。

```csharp
// ドキュメントを、宛先ドキュメントのコンテンツの直後に表示します。
srcDoc.FirstSection.PageSetup.SectionStart = SectionStart.Continuous;
```

これにより、ドキュメントを結合したときにドキュメント間に中断が生じなくなります。

## ステップ4: ソースドキュメントを追加する

次に、ソースドキュメントをターゲットドキュメントに追加します。この手順により、ソースドキュメントのコンテンツがターゲットドキュメントの末尾に追加されます。

```csharp
// ソース ドキュメントにある元のスタイルを使用して、ソース ドキュメントを追加します。
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

使用 `ImportFormatMode.KeepSourceFormatting` ソース ドキュメントの書式が最終的な結合ドキュメントで保持されることを保証します。

## ステップ5: 結合した文書を保存する

最後に、結合したドキュメントを指定されたディレクトリに保存します。これでドキュメントの結合プロセスは完了です。

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.JoinContinuous.docx");
```

パスとファイル名がニーズに合っていることを確認してください。

## 結論

これで完了です！わずか数行のコードで、Aspose.Words for .NET を使用して 2 つの Word 文書を 1 つの連続した文書に結合することができました。このプロセスはシンプルであるだけでなく、非常に効率的で、文書の元の書式設定が維持されます。

## よくある質問

### つ以上のドキュメントを結合できますか?
はい、追加のドキュメントをロードして順番に追加することで、複数のドキュメントを結合するプロセスを繰り返すことができます。

### 元の書式は保持されますか?
はい、使用しています `ImportFormatMode.KeepSourceFormatting` ソース ドキュメントの書式が保持されます。

### Aspose.Words for .NET は .NET Core と互換性がありますか?
はい、Aspose.Words for .NET は .NET Framework と .NET Core の両方と互換性があります。

### ページ設定が異なるドキュメントを結合できますか?
はい。ただし、シームレスなマージを確実に行うには、ページ設定プロパティを調整する必要があるかもしれません。

### 問題が発生した場合、どこでサポートを受けることができますか?
Asposeコミュニティフォーラムからサポートを受けることができます [ここ](https://forum。aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}