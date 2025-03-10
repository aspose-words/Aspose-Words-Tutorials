---
title: リストのソース書式を保持
linktitle: リストのソース書式を保持
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、書式を保持しながら Word 文書を結合する方法を学びます。このチュートリアルでは、シームレスな文書結合の手順を順を追って説明します。
weight: 10
url: /ja/net/join-and-append-documents/list-keep-source-formatting/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# リストのソース書式を保持

## 導入

このチュートリアルでは、Aspose.Words for .NET を使用して、ソースの書式設定を保持しながらドキュメントを結合する方法について説明します。この機能は、ドキュメントの元の外観を維持することが重要なシナリオでは不可欠です。

## 前提条件

続行する前に、次の前提条件を満たしていることを確認してください。

- マシンに Visual Studio がインストールされています。
-  Aspose.Words for .NETがインストールされています。ダウンロードはこちらから[ここ](https://releases.aspose.com/words/net/).
- C# プログラミングと .NET 環境に関する基本的な知識。

## 名前空間のインポート

まず、必要な名前空間を C# プロジェクトにインポートします。

```csharp
using Aspose.Words;
```

## ステップ1: プロジェクトを設定する

まず、Visual Studio で新しい C# プロジェクトを作成します。プロジェクトで Aspose.Words for .NET が参照されていることを確認します。参照されていない場合は、NuGet パッケージ マネージャーを使用して追加できます。

## ステップ2: ドキュメント変数を初期化する

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";

//ソースドキュメントと宛先ドキュメントを読み込む
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Document destination with list.docx");
```

## ステップ3: セクション設定を構成する

結合されたドキュメント内の連続したフローを維持するには、セクションの開始を調整します。

```csharp
srcDoc.FirstSection.PageSetup.SectionStart = SectionStart.Continuous;
```

## ステップ4: ドキュメントを結合する

ソース文書の内容を追加します（`srcDoc`）を宛先ドキュメント（`dstDoc`）を元の書式のまま変更します。

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## ステップ5: 結合した文書を保存する

最後に、結合したドキュメントを指定したディレクトリに保存します。

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.ListKeepSourceFormatting.docx");
```

## 結論

結論として、Aspose.Words for .NET を使用すると、元の書式設定を維持しながらドキュメントを結合することが簡単になります。このチュートリアルでは、結合されたドキュメントがソース ドキュメントのレイアウトとスタイルを維持するように、プロセスをガイドしました。

## よくある質問

### ドキュメントのスタイルが異なる場合はどうなりますか?
Aspose.Words はさまざまなスタイルを適切に処理し、元の書式設定を可能な限り維持します。

### 異なる形式のドキュメントを結合できますか?
はい、Aspose.Words は、DOCX、DOC、RTF など、さまざまな形式のドキュメントの結合をサポートしています。

### Aspose.Words は .NET Core と互換性がありますか?
はい、Aspose.Words は .NET Core を完全にサポートしており、クロスプラットフォーム開発が可能になります。

### 大きな文書を効率的に処理するにはどうすればよいでしょうか?
Aspose.Words は、大規模なドキュメントでもパフォーマンスが最適化された、ドキュメント操作用の効率的な API を提供します。

### その他の例やドキュメントはどこで見つかりますか?
より多くの例と詳細なドキュメントについては、[Aspose.Words ドキュメント](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
