---
title: Word 文書に Bidi マークを追加する
linktitle: Word 文書に Bidi マークを追加する
second_title: Aspose.Words ドキュメント処理 API
description: このガイドでは、Aspose.Words for .NET を使用して Word 文書に双方向 (Bidi) マークを追加する方法を学習します。多言語コンテンツのテキスト方向が適切であることを確認します。
weight: 10
url: /ja/net/programming-with-txtsaveoptions/add-bidi-marks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 文書に Bidi マークを追加する

## 導入

ドキュメント処理の世界では、双方向 (Bidi) テキストの管理が少々難しいことがよくあります。これは、アラビア語やヘブライ語など、テキストの方向が異なる言語を扱う場合に特に当てはまります。幸い、Aspose.Words for .NET を使用すると、このようなシナリオを簡単に処理できます。このチュートリアルでは、Aspose.Words for .NET を使用して Word ドキュメントに Bidi マークを追加する方法について説明します。

## 前提条件

コードに進む前に、次のものを用意してください。

1. Aspose.Words for .NET: Aspose.Words for .NETがインストールされている必要があります。[Aspose ダウンロード ページ](https://releases.aspose.com/words/net/).
2. .NET Framework または .NET Core: 例を実行するために互換性のある .NET 環境が設定されていることを確認します。
3. C# の基礎知識: C# プログラミング言語と .NET の基本的な操作に精通していること。

## 名前空間のインポート

開始するには、必要な名前空間をインポートする必要があります。プロジェクトにそれらを含める方法は次のとおりです。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Word 文書に Bidi マークを追加するプロセスを明確な手順に分解してみましょう。各手順でコードとその目的を説明します。

## ステップ1: ドキュメントを設定する

まず、`Document`クラスと`DocumentBuilder`ドキュメントにコンテンツを追加します。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENTS DIRECTORY";

//ドキュメントを作成し、コンテンツを追加する
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

このステップでは、新しいWord文書を初期化し、`DocumentBuilder`コンテンツの挿入を容易にするため。

## ステップ2: ドキュメントにコンテンツを追加する

次に、ドキュメントにテキストを追加します。ここでは、Bidi テキストの処理を説明するために、さまざまな言語でテキストを追加します。

```csharp
builder.Writeln("Hello world!");
builder.ParagraphFormat.Bidi = true;
builder.Writeln("שלום עולם!");
builder.Writeln("مرحبا بالعالم!");
```

ここでは、まず標準的な英語のフレーズを追加します。次に、ヘブライ語とアラビア語で書かれた後続のテキストに対して Bidi テキスト書式設定を有効にします。これは、双方向テキストを組み込む方法を示しています。

## ステップ3: Bidiマークの保存オプションを構成する

Bidiマークが文書に正しく保存されるようにするには、`TxtSaveOptions`そして、`AddBidiMarks`オプション。

```csharp
// Bidiマークを追加する
TxtSaveOptions saveOptions = new TxtSaveOptions { AddBidiMarks = true };
doc.Save(dataDir + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
```

このステップでは、`TxtSaveOptions`そして、`AddBidiMarks`財産に`true`これにより、ドキュメントをテキスト ファイルとして保存するときに、Bidi マークが確実に含まれるようになります。

## 結論

Word 文書に Bidi マークを追加することは、テキスト方向が異なる言語を含む多言語コンテンツを扱う場合に重要なステップになります。Aspose.Words for .NET を使用すると、このプロセスは簡単かつ効率的になります。上記の手順に従うことで、文書が Bidi テキストを正しく表現し、読みやすさと正確性を向上させることができます。

## よくある質問

### Bidi マークとは何ですか? また、なぜ重要ですか?
Bidi マークは、文書内のテキストの方向を制御するために使用される特殊文字です。アラビア語やヘブライ語など、右から左に読む言語を適切に表示するために不可欠です。

### Aspose.Words for .NET を使用して他の種類のテキスト方向の問題を処理できますか?
はい、Aspose.Words for .NET は、右から左、左から右の言語を含む、さまざまなテキスト方向と書式設定のニーズを包括的にサポートします。

### ドキュメントの特定の部分にのみ Bidi フォーマットを適用することは可能ですか?
はい、必要に応じて、ドキュメントの特定の段落またはセクションに Bidi 書式を適用できます。

### Bidi マーク付きのドキュメントをどのような形式で保存できますか?
提供されている例では、ドキュメントはテキスト ファイルとして保存されます。ただし、Aspose.Words では、Bidi マークを保持しながらさまざまな形式でドキュメントを保存することもサポートされています。

### Aspose.Words for .NET の詳細情報はどこで入手できますか?
 Aspose.Words for .NETの詳細については、[Aspose ドキュメント](https://reference.aspose.com/words/net/)アクセスして[サポートフォーラム](https://forum.aspose.com/c/words/8)追加のヘルプについては。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
