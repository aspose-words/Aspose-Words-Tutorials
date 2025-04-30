---
"description": "このガイドでは、Aspose.Words for .NET を使用して Word 文書に双方向（Bidi）マークを追加する方法を学びます。多言語コンテンツで適切なテキスト方向を確保します。"
"linktitle": "Word文書にBidiマークを追加する"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "Word文書にBidiマークを追加する"
"url": "/ja/net/programming-with-txtsaveoptions/add-bidi-marks/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Word文書にBidiマークを追加する

## 導入

ドキュメント処理の世界では、双方向（Bidi）テキストの管理はしばしば少々複雑になります。特に、アラビア語やヘブライ語など、テキストの方向が異なる言語を扱う場合はなおさらです。しかし、Aspose.Words for .NETを使えば、このようなシナリオも簡単に処理できます。このチュートリアルでは、Aspose.Words for .NETを使ってWord文書にBidiマークを追加する方法を解説します。

## 前提条件

コードに進む前に、次のものを用意してください。

1. Aspose.Words for .NET: Aspose.Words for .NET がインストールされている必要があります。ダウンロードは以下から行えます。 [Aspose ダウンロードページ](https://releases。aspose.com/words/net/).
2. .NET Framework または .NET Core: 例を実行するために互換性のある .NET 環境が設定されていることを確認します。
3. C# の基礎知識: C# プログラミング言語と .NET の基本的な操作に精通していること。

## 名前空間のインポート

まず、必要な名前空間をインポートする必要があります。プロジェクトにそれらを組み込む方法は次のとおりです。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Word文書にBidiマークを追加するプロセスを、分かりやすい手順に分解して解説します。各手順で、コードとその目的を詳しく説明します。

## ステップ1：ドキュメントを設定する

まず、 `Document` クラスと `DocumentBuilder` ドキュメントにコンテンツを追加します。

```csharp
// ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// ドキュメントを作成し、コンテンツを追加する
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

このステップでは、新しいWord文書を初期化し、 `DocumentBuilder` コンテンツの挿入を容易にするため。

## ステップ2: ドキュメントにコンテンツを追加する

次に、ドキュメントにテキストを追加します。ここでは、Bidiテキストの処理方法を説明するために、さまざまな言語のテキストを追加します。

```csharp
builder.Writeln("Hello world!");
builder.ParagraphFormat.Bidi = true;
builder.Writeln("שלום עולם!");
builder.Writeln("مرحبا بالعالم!");
```

ここでは、まず標準的な英語のフレーズを追加します。次に、後続のヘブライ語とアラビア語のテキストに対してBidiテキスト書式設定を有効にします。これは、双方向テキストを組み込む方法を示しています。

## ステップ3: Bidiマークの保存オプションを構成する

文書にBidiマークが正しく保存されるようにするには、 `TxtSaveOptions` そして、 `AddBidiMarks` オプション。

```csharp
// Bidiマークを追加する
TxtSaveOptions saveOptions = new TxtSaveOptions { AddBidiMarks = true };
doc.Save(dataDir + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
```

このステップでは、 `TxtSaveOptions` そして設定する `AddBidiMarks` 財産に `true`これにより、ドキュメントをテキスト ファイルとして保存するときに、Bidi マークが確実に含まれるようになります。

## 結論

Word文書にBidiマークを追加することは、テキストの方向が異なる言語を含む多言語コンテンツを扱う際に非常に重要なステップとなります。Aspose.Words for .NETを使えば、このプロセスは簡単かつ効率的に行えます。上記の手順に従うことで、文書がBidiテキストを正しく表現し、読みやすさと正確性を向上させることができます。

## よくある質問

### Bidi マークとは何ですか? なぜ重要ですか?
Bidiマークは、文書内のテキストの方向を制御するために使用される特殊文字です。アラビア語やヘブライ語のように、右から左に読む言語を正しく表示するために不可欠です。

### Aspose.Words for .NET を使用して他の種類のテキスト方向の問題を処理できますか?
はい、Aspose.Words for .NET は、右から左に記述する言語や左から右に記述する言語など、さまざまなテキスト方向と書式設定のニーズを包括的にサポートします。

### ドキュメントの特定の部分にのみ Bidi フォーマットを適用することは可能ですか?
はい、必要に応じて、ドキュメントの特定の段落またはセクションに Bidi 書式を適用できます。

### Bidi マーク付きのドキュメントをどのような形式で保存できますか?
この例では、ドキュメントはテキストファイルとして保存されていますが、Aspose.Words は Bidi マークを維持しながら、さまざまな形式でドキュメントを保存することもできます。

### Aspose.Words for .NET の詳細情報はどこで入手できますか?
Aspose.Words for .NETの詳細については、 [Aspose ドキュメント](https://reference.aspose.com/words/net/) アクセスして [サポートフォーラム](https://forum.aspose.com/c/words/8) 追加のヘルプが必要な場合は、


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}