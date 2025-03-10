---
title: 異なるページ設定
linktitle: 異なるページ設定
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して Word 文書を結合するときに、さまざまなページ構成を設定する方法を学びます。ステップ バイ ステップ ガイドが含まれています。
weight: 10
url: /ja/net/join-and-append-documents/different-page-setup/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 異なるページ設定

## 導入

こんにちは! Aspose.Words for .NET を使った魅力的なドキュメント操作の世界に飛び込む準備はできていますか? 今日は、Word ドキュメントを結合するときに異なるページ設定を設定するという、非常に便利なことに取り組みます。レポートを結合する場合でも、小説を作成する場合でも、単に楽しみのためにドキュメントをいじる場合でも、このガイドでは手順を追って説明します。さあ、始めましょう!

## 前提条件

作業を始める前に、必要なものがすべて揃っていることを確認しましょう。

1.  Aspose.Words for .NET: Aspose.Words for .NETがインストールされていることを確認してください。[ここからダウンロード](https://releases.aspose.com/words/net/).
2. .NET Framework: Aspose.Words for .NET をサポートする任意のバージョン。
3. 開発環境: Visual Studio またはその他の .NET 互換 IDE。
4. 基本的な C# の知識: 構文と構造を理解するための基本のみ。

## 名前空間のインポート

まず最初に、C# プロジェクトに必要な名前空間をインポートしましょう。これらの名前空間は、Aspose.Words の機能にアクセスするために不可欠です。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Words.Tables;
```

さて、本題に入りましょう。プロセス全体をわかりやすいステップに分解していきます。

## ステップ1: プロジェクトを設定する

### ステップ1.1: 新しいプロジェクトを作成する

Visual Studio を起動し、新しい C# コンソール アプリケーションを作成します。「DifferentPageSetupExample」のようなかっこいい名前を付けます。

### ステップ 1.2: Aspose.Words 参照を追加する

Aspose.Words を使用するには、プロジェクトに追加する必要があります。まだダウンロードしていない場合は、Aspose.Words for .NET パッケージをダウンロードしてください。次のコマンドを使用して、NuGet パッケージ マネージャーからインストールできます。

```bash
Install-Package Aspose.Words
```

## ステップ2: ドキュメントを読み込む

次に、結合するドキュメントを読み込みます。この例では、2 つの Word ドキュメントが必要です。`Document source.docx`そして`Northwind traders.docx`これらのファイルがプロジェクト ディレクトリにあることを確認してください。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## ステップ3: ソースドキュメントのページ設定を構成する

ソース ドキュメントのページ設定が宛先ドキュメントと一致していることを確認する必要があります。この手順は、シームレスな結合に不可欠です。

### ステップ 3.1: 宛先ドキュメントの後に続行

ソース ドキュメントが宛先ドキュメントの直後に続くように設定します。

```csharp
srcDoc.FirstSection.PageSetup.SectionStart = SectionStart.Continuous;
```

### ステップ3.2: ページ番号付けを再開する

ソース ドキュメントの先頭からページ番号付けを再開します。

```csharp
srcDoc.FirstSection.PageSetup.RestartPageNumbering = true;
srcDoc.FirstSection.PageSetup.PageStartingNumber = 1;
```

## ステップ4: ページ設定を一致させる

レイアウトの不一致を避けるには、ソース ドキュメントの最初のセクションのページ設定が、宛先ドキュメントの最後のセクションのページ設定と一致していることを確認します。

```csharp
srcDoc.FirstSection.PageSetup.PageWidth = dstDoc.LastSection.PageSetup.PageWidth;
srcDoc.FirstSection.PageSetup.PageHeight = dstDoc.LastSection.PageSetup.PageHeight;
srcDoc.FirstSection.PageSetup.Orientation = dstDoc.LastSection.PageSetup.Orientation;
```

## ステップ5: 段落の書式を調整する

スムーズな流れを確保するには、ソース ドキュメントの段落の書式を調整する必要があります。

ソース文書内のすべての段落を反復処理し、`KeepWithNext`財産。

```csharp
foreach (Paragraph para in srcDoc.GetChildNodes(NodeType.Paragraph, true))
{
    para.ParagraphFormat.KeepWithNext = true;
}
```

## ステップ6: ソースドキュメントを追加する

最後に、元の書式が保持されるようにしながら、ソース ドキュメントを宛先ドキュメントに追加します。

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## ステップ7: 結合したドキュメントを保存する

次に、美しく結合されたドキュメントを保存します。

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.DifferentPageSetup.docx");
```

## 結論

これで完了です。Aspose.Words for .NET を使用して、ページ設定が異なる 2 つの Word 文書を結合しました。この強力なライブラリを使用すると、プログラムで文書を操作するのが非常に簡単になります。複雑なレポートを作成する場合でも、本を組み立てる場合でも、複数のセクションに分かれた文書を管理する場合でも、Aspose.Words が役立ちます。

## よくある質問

### この方法は 2 つ以上のドキュメントに使用できますか?
もちろんです! 結合する追加ドキュメントごとに手順を繰り返すだけです。

### ドキュメントの余白が異なる場合はどうなりますか?
ページの幅、高さ、向きを合わせたのと同様に、余白設定を合わせることができます。

### Aspose.Words は .NET Core と互換性がありますか?
はい、Aspose.Words for .NET は .NET Core と完全に互換性があります。

### 両方のドキュメントのスタイルを保持できますか?
はい、`ImportFormatMode.KeepSourceFormatting`このオプションにより、ソース ドキュメントのスタイルが保持されます。

### Aspose.Words に関する詳細なサポートはどこで受けられますか?
チェックしてください[Aspose.Words ドキュメント](https://reference.aspose.com/words/net/)または訪問する[サポートフォーラム](https://forum.aspose.com/c/words/8)さらにサポートが必要な場合はお問い合わせください。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
