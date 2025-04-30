---
"description": "この包括的なステップバイステップ ガイドでは、Aspose.Words for .NET を使用してテキスト入力フォーム フィールドをプレーン テキストとしてエクスポートする方法を学習します。"
"linktitle": "テキスト入力フォームフィールドをテキストとしてエクスポート"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "テキスト入力フォームフィールドをテキストとしてエクスポート"
"url": "/ja/net/programming-with-htmlsaveoptions/export-text-input-form-field-as-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# テキスト入力フォームフィールドをテキストとしてエクスポート

## 導入

Aspose.Words for .NETの世界に飛び込もうとしているのですか？素晴らしい選択です！テキスト入力フォームフィールドをテキストとしてエクスポートする方法を学びたいなら、ここがまさにうってつけです。初心者の方でも、スキルアップを目指す方でも、このガイドで必要な知識をすべて網羅できます。さあ、始めましょう！

## 前提条件

具体的な内容に入る前に、スムーズに進めるために必要なものがすべて揃っていることを確認しましょう。

- Aspose.Words for .NET: 最新バージョンをダウンロードしてインストールしてください。 [ここ](https://releases。aspose.com/words/net/).
- IDE: Visual Studio または任意の C# 開発環境。
- 基本的な C# の知識: 基本的な C# 構文とオブジェクト指向プログラミングの概念を理解していること。
- 文書: サンプルの Word 文書 (`Rendering.docx`) にテキスト入力フォーム フィールドを追加します。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートする必要があります。これらは、すべてがシームレスに動作するための構成要素のようなものです。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

さて、名前空間の準備ができたので、早速実行してみましょう。

## ステップ1: プロジェクトの設定

コードに入る前に、プロジェクトが正しく設定されていることを確認しましょう。

## プロジェクトの作成

1. Visual Studio を開く: まず、Visual Studio またはお好みの C# 開発環境を開きます。
2. 新しいプロジェクトを作成する: `File > New > Project`選択 `Console App (.NET Core)` またはその他の関連するプロジェクト タイプ。
3. プロジェクトに名前を付ける: プロジェクトに意味のある名前を付けます。 `AsposeWordsExportExample`。

## Aspose.Wordsの追加

1. NuGetパッケージの管理: ソリューションエクスプローラーでプロジェクトを右クリックし、 `Manage NuGet Packages`。
2. Aspose.Wordsを検索: NuGetパッケージマネージャーで、 `Aspose。Words`.
3. Aspose.Wordsをインストール: クリック `Install` Aspose.Words ライブラリをプロジェクトに追加します。

## ステップ2: Word文書を読み込む

プロジェクトが設定されたので、テキスト入力フォーム フィールドを含む Word 文書を読み込みます。

1. ドキュメント ディレクトリの指定: ドキュメントが保存されるディレクトリへのパスを定義します。
2. ドキュメントを読み込む: `Document` Word 文書を読み込むためのクラス。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

## ステップ3: エクスポートディレクトリを準備する

エクスポートする前に、エクスポートディレクトリが準備されていることを確認しましょう。ここにHTMLファイルと画像が保存されます。

1. エクスポート ディレクトリを定義する: エクスポートされたファイルを保存するパスを指定します。
2. ディレクトリの確認とクリーンアップ: ディレクトリが存在し、空であることを確認します。

```csharp
string imagesDir = Path.Combine(dataDir, "Images");

if (Directory.Exists(imagesDir))
    Directory.Delete(imagesDir, true);

Directory.CreateDirectory(imagesDir);
```

## ステップ4: 保存オプションを設定する

ここで魔法が起こります。テキスト入力フォームフィールドをプレーンテキストとしてエクスポートするための保存オプションを設定する必要があります。

1. 保存オプションの作成: 新しい `HtmlSaveOptions` 物体。
2. エクスポートテキストオプションの設定: `ExportTextInputFormFieldAsText` 財産に `true`。
3. 画像フォルダの設定: 画像を保存するフォルダを定義します。

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    ExportTextInputFormFieldAsText = true,
    ImagesFolder = imagesDir
};
```

## ステップ5: ドキュメントをHTMLとして保存する

最後に、設定した保存オプションを使用して、Word 文書を HTML ファイルとして保存します。

1. 出力パスの定義: HTML ファイルを保存するパスを指定します。
2. ドキュメントを保存する: `Save` の方法 `Document` ドキュメントをエクスポートするクラス。

```csharp
doc.Save(dataDir + "ExportedDocument.html", saveOptions);
```

## 結論

これで完了です！Aspose.Words for .NET を使用して、テキスト入力フォームフィールドをプレーンテキストとしてエクスポートできました。このガイドでは、このタスクを実現するための明確な手順をステップバイステップで説明しました。「練習すれば完璧になる」ということを忘れないでください。さまざまなオプションや設定を試して、Aspose.Words で何ができるか試してみてください。

## よくある質問

### 同じ方法を使用して他の種類のフォーム フィールドをエクスポートできますか?

はい、異なるプロパティを設定することで、他の種類のフォームフィールドをエクスポートできます。 `HtmlSaveOptions` クラス。

### ドキュメントに画像が含まれている場合はどうなりますか?

画像は指定された画像フォルダに保存されます。 `ImagesFolder` の財産 `HtmlSaveOptions`。

### Aspose.Words のライセンスは必要ですか?

はい、無料トライアルをご利用いただけます [ここ](https://releases.aspose.com/) またはライセンスを購入する [ここ](https://purchase。aspose.com/buy).

### エクスポートされた HTML をカスタマイズできますか?

もちろんです！Aspose.WordsにはHTML出力をカスタマイズするための様々なオプションが用意されています。 [ドキュメント](https://reference.aspose.com/words/net/) 詳細についてはこちらをご覧ください。

### Aspose.Words は .NET Core と互換性がありますか?

はい、Aspose.Words は .NET Core、.NET Framework、およびその他の .NET プラットフォームと互換性があります。



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}