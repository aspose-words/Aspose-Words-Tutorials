---
"description": "この詳細なチュートリアルでは、Aspose.Words for .NET を使用してフォントをBase64形式でエクスポートする方法を学びます。フォントがHTMLファイルに埋め込まれ、正しく表示されることを確認します。"
"linktitle": "フォントをBase64としてエクスポート"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "フォントをBase64としてエクスポート"
"url": "/ja/net/programming-with-htmlsaveoptions/export-fonts-as-base-64/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# フォントをBase64としてエクスポート

## 導入

Word文書をプログラムで操作する場合、Aspose.Words for .NETは強力なツールです。その優れた機能の一つは、HTMLファイル内でフォントをBase64形式でエクスポートすることです。これにより、異なるブラウザやシステム間でフォントが正しく埋め込まれ、表示されるようになります。このチュートリアルでは、その方法を詳しく説明します。Word文書のフォントをWeb対応にする準備はできましたか？さあ、始めましょう！

## 前提条件

コーディングを始める前に、必要なものがすべて揃っていることを確認しましょう。

- Aspose.Words for .NETライブラリ: ダウンロードはこちらから [Aspose リリース](https://releases.aspose.com/words/net/) ページ。
- .NET 開発環境: Visual Studio などの IDE はすべて完璧に動作します。
- C# の基本知識: プロである必要はありませんが、基本的な理解があれば役立ちます。

## 名前空間のインポート

Aspose.Words for .NET を使用するには、C# コードに必要な名前空間をインポートする必要があります。これにより、すべてのクラスとメソッドが使用できるようになります。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## ステップ1: プロジェクトの設定

まず最初に、プロジェクトをセットアップして Aspose.Words ライブラリをインストールしましょう。

### 1.1 新しいプロジェクトを作成する

Visual Studioを開き、新しいコンソールアプリプロジェクトを作成します。「ExportFontsBase64」など、分かりやすい名前を付けます。

### 1.2 Aspose.Wordsをインストールする

Aspose.Words for .NET は NuGet パッケージ マネージャー経由でインストールできます。

1. ソリューション エクスプローラーでプロジェクトを右クリックします。
2. 「NuGet パッケージの管理」を選択します。
3. 「Aspose.Words」を検索してインストールします。

あるいは、パッケージ マネージャー コンソールで次のコマンドを実行することもできます。

```sh
Install-Package Aspose.Words
```

## ステップ2: Word文書を読み込む

プロジェクトがセットアップされたので、フォントをエクスポートする Word 文書を読み込みます。

### 2.1 ドキュメントディレクトリを定義する

まず、Word 文書が保存されているディレクトリを定義します。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

交換する `"YOUR DOCUMENT DIRECTORY"` ドキュメント ディレクトリへの実際のパスを入力します。

### 2.2 ドキュメントを読み込む

次に、 `Document` クラス：

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

「Rendering.docx」が指定したディレクトリにあることを確認します。

## ステップ3: HTML保存オプションを設定する

フォントをBase64でエクスポートするには、 `HtmlSaveOptions`。


インスタンスを作成する `HtmlSaveOptions` そして設定する `ExportFontsAsBase64` 財産に `true`：

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions { ExportFontsAsBase64 = true };
```

## ステップ4: ドキュメントをHTMLとして保存する

最後に、設定したオプションでドキュメントを保存しましょう。


使用 `Save` の方法 `Document` ドキュメントを保存するクラス:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
```

この行は、フォントが Base64 としてエクスポートされ、HTML 内に埋め込まれた状態でドキュメントを HTML ファイルとして保存します。

## 結論

おめでとうございます！Aspose.Words for .NET を使用して、Word 文書からフォントを Base64 形式でエクスポートできました。これにより、異なるプラットフォーム間でフォントが保持され、正しく表示されるようになります。Web 表示用の文書を作成する場合でも、単に互換性を確保する場合でも、この機能は非常に便利です。

## よくある質問

### Base64 エンコーディングとは何ですか?
Base64は、バイナリデータ（フォントなど）をテキスト形式にエンコードする方式です。これにより、HTMLなどのテキストベースの形式との互換性が確保されます。

### HTML のフォントに Base64 を使用する必要があるのはなぜですか?
Base64 を使用すると、フォントが HTML に直接埋め込まれるため、フォント ファイルが見つからないという問題が回避され、一貫した表示が保証されます。

### この方法は画像などの他のリソースにも使用できますか?
もちろんです! Aspose.Words for .NET を使用すると、画像などのさまざまなリソースを Base64 として HTML ファイルに埋め込むことができます。

### ドキュメントに複数のフォントがある場合はどうなりますか?
問題ありません。Aspose.Words for .NET は、ドキュメントで使用されているすべてのフォントを、結果の HTML ファイルに Base64 として埋め込みます。

### Aspose.Words for .NET は無料で使用できますか?
Aspose.Words for .NETは商用ライブラリです。ただし、無料トライアル版は以下からダウンロードできます。 [Aspose リリース](https://releases.aspose.com/) ページ。



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}