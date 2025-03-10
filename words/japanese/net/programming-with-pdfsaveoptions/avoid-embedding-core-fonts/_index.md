---
title: コアフォントを埋め込まないことでPDFファイルのサイズを縮小する
linktitle: コアフォントを埋め込まないことでPDFファイルのサイズを縮小する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用してコア フォントを埋め込まないことで PDF ファイルのサイズを縮小する方法を学びます。ステップ バイ ステップ ガイドに従って PDF を最適化してください。
weight: 10
url: /ja/net/programming-with-pdfsaveoptions/avoid-embedding-core-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# コアフォントを埋め込まないことでPDFファイルのサイズを縮小する

## 導入

PDF ファイルがなぜこんなに大きいのかと首をかしげたことはありませんか? そう思っているのはあなただけではありません。よくある原因の 1 つは、Arial や Times New Roman などのコア フォントを埋め込むことです。幸い、Aspose.Words for .NET にはこの問題に対処する優れた方法があります。このチュートリアルでは、これらのコア フォントを埋め込まないようにして PDF ファイルのサイズを縮小する方法を紹介します。早速始めましょう!

## 前提条件

このエキサイティングな旅に出発する前に、必要なものがすべて揃っているかどうか確認しましょう。簡単なチェックリストを以下に示します。

-  Aspose.Words for .NET: Aspose.Words for .NETがインストールされていることを確認してください。まだインストールしていない場合は、ダウンロードできます。[ここ](https://releases.aspose.com/words/net/).
- 開発環境: Visual Studio などの開発環境が必要です。
- Word 文書: このチュートリアルでは、Word 文書 (例: 「Rendering.docx」) を使用します。
- 基本的な C# の知識: C# の基本的な理解があれば、理解しやすくなります。

さて、準備が整いましたので、本題に入りましょう。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートしましょう。この手順により、必要なすべての Aspose.Words 機能にアクセスできるようになります。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## ステップ1: ドキュメントディレクトリを初期化する

ドキュメントの操作を始める前に、ドキュメントが保存されているディレクトリを指定する必要があります。これは、ファイルにアクセスするために不可欠です。

```csharp
//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

交換する`"YOUR DOCUMENT DIRECTORY"` Word 文書が保存されている実際のパスを入力します。

## ステップ2: Word文書を読み込む

次に、PDF に変換する Word 文書を読み込む必要があります。この例では、「Rendering.docx」という名前の文書を使用しています。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

このコード行はドキュメントをメモリに読み込み、さらに処理する準備を整えます。

## ステップ3: PDF保存オプションを設定する

次は魔法のパートです! コアフォントが埋め込まれないように PDF 保存オプションを設定します。これは PDF ファイルのサイズを縮小するのに役立つ重要なステップです。

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    UseCoreFonts = true
};
```

設定`UseCoreFonts`に`true`Arial や Times New Roman などのコアフォントが PDF に埋め込まれないようにすることで、ファイル サイズが大幅に削減されます。

## ステップ4: ドキュメントをPDFとして保存する

最後に、設定された保存オプションを使用して、Word 文書を PDF として保存します。この手順では、コア フォントを埋め込まずに PDF ファイルが生成されます。

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.AvoidEmbeddingCoreFonts.pdf", saveOptions);
```

これで完了です。PDF ファイルは、かさばるコア フォントなしで、指定したディレクトリに保存されます。

## 結論

Aspose.Words for .NET を使用すると、PDF ファイルのサイズを簡単に縮小できます。コア フォントの埋め込みを回避することで、ファイル サイズを大幅に縮小でき、ドキュメントの共有や保存が容易になります。このチュートリアルが役に立ち、プロセスを明確に理解していただければ幸いです。小さな調整が大きな違いを生むことを忘れないでください。

## よくある質問

### PDF にコアフォントを埋め込まないほうがよいのはなぜですか?
コアフォントの埋め込みを避けることでファイルサイズが小さくなり、共有や保存が容易になります。

### 埋め込まれたコアフォントがなくても PDF を正しく表示できますか?
はい、Arial や Times New Roman などのコアフォントは、ほとんどのシステムで一般的に利用できます。

### カスタムフォントを埋め込む必要がある場合はどうすればよいですか?
カスタマイズできます`PdfSaveOptions`必要に応じて特定のフォントを埋め込みます。

### Aspose.Words for .NET は無料で使用できますか?
 Aspose.Words for .NETにはライセンスが必要です。無料トライアルをご利用いただけます。[ここ](https://releases.aspose.com/).

### Aspose.Words for .NET に関する詳細なドキュメントはどこで入手できますか?
詳細なドキュメントは以下をご覧ください[ここ](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
