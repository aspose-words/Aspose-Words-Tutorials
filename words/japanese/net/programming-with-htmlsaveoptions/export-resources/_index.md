---
"description": "Aspose.Words for .NET を使用して、Word 文書を HTML として保存しながら、CSS やフォントなどのリソースをエクスポートする方法を学びましょう。ステップバイステップのガイドに従ってください。"
"linktitle": "エクスポートリソース"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "エクスポートリソース"
"url": "/ja/net/programming-with-htmlsaveoptions/export-resources/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# エクスポートリソース

## 導入

テクノロジーに興味のある皆さん、こんにちは！Word文書をHTMLに変換したいと思ったことがあるなら、まさにうってつけの場所です。今日は、Aspose.Words for .NETの素晴らしい世界をご紹介します。この強力なライブラリを使えば、Word文書をプログラムで簡単に操作できます。このチュートリアルでは、Aspose.Words for .NETを使ってWord文書をHTMLとして保存する際に、フォントやCSSなどのリソースをエクスポートする手順を詳しく解説します。さあ、シートベルトを締めて、楽しくてためになる旅に出かけましょう！

## 前提条件

コードに進む前に、始めるのに必要なものがすべて揃っていることを確認しましょう。簡単なチェックリストを以下に示します。

1. Visual Studio: お使いのマシンにVisual Studioがインストールされていることを確認してください。ダウンロードは以下から行えます。 [Visual Studioのウェブサイト](https://visualstudio。microsoft.com/).
2. Aspose.Words for .NET: Aspose.Words for .NETライブラリが必要です。まだお持ちでない場合は、無料トライアル版をダウンロードしてください。 [Aspose リリース](https://releases.aspose.com/words/net/) または、 [Aspose ストア](https://purchase。aspose.com/buy).
3. C# の基礎知識: C# の基礎を理解しておくと、コード例を理解するのに役立ちます。

すべて理解できましたか？素晴らしい！必要な名前空間のインポートに進みましょう。

## 名前空間のインポート

Aspose.Words for .NET を使用するには、プロジェクトに適切な名前空間を含める必要があります。手順は以下のとおりです。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

これらの名前空間は、チュートリアルで使用する Aspose.Words のクラスとメソッドにアクセスするために重要です。

Word文書をHTMLとして保存する際のリソースのエクスポート手順を詳しく説明します。手順を1つずつ解説するので、分かりやすいです。

## ステップ1: ドキュメントディレクトリを設定する

まず最初に、ドキュメントディレクトリへのパスを指定する必要があります。これはWord文書が保存される場所であり、HTMLファイルも保存されます。

```csharp
// ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

交換する `"YOUR DOCUMENT DIRECTORY"` ディレクトリへの実際のパスを入力します。

## ステップ2: Word文書を読み込む

次に、HTMLに変換したいWord文書を読み込みます。このチュートリアルでは、 `Rendering。docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

このコード行は、指定されたディレクトリからドキュメントを読み込みます。

## ステップ3: HTML保存オプションを設定する

CSSやフォントなどのリソースをエクスポートするには、 `HtmlSaveOptions`この手順は、HTML 出力が適切に構造化され、必要なリソースが含まれていることを確認するために重要です。

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External,
    ExportFontResources = true,
    ResourceFolder = dataDir + "Resources",
    ResourceFolderAlias = "http://example.com/resources"
};
```

それぞれのオプションの機能について詳しく見ていきましょう。
- `CssStyleSheetType = CssStyleSheetType.External`: このオプションは、CSS スタイルを外部スタイルシートに保存することを指定します。
- `ExportFontResources = true`: フォント リソースのエクスポートが可能になります。
- `ResourceFolder = dataDir + "Resources"`: リソース (フォントや CSS ファイルなど) が保存されるローカル フォルダーを指定します。
- `ResourceFolderAlias = "http://example.com/resources"`: HTML ファイルで使用されるリソース フォルダーのエイリアスを設定します。

## ステップ4: ドキュメントをHTMLとして保存する

保存オプションを設定したら、最後のステップはドキュメントをHTMLファイルとして保存することです。手順は以下のとおりです。

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

このコード行は、エクスポートされたリソースとともにドキュメントを HTML 形式で保存します。

## 結論

これで完了です！Aspose.Words for .NET を使って、Word 文書を HTML として保存しながらリソースをエクスポートできました。この強力なライブラリがあれば、Word 文書をプログラムで操作するのは簡単です。Web アプリケーションを開発している場合でも、オフラインで使用できるように文書を変換するだけの場合でも、Aspose.Words がきっと役に立ちます。

## よくある質問

### フォントや CSS と一緒に画像をエクスポートできますか?
はい、できます！Aspose.Words for .NETは画像のエクスポートもサポートしています。 `HtmlSaveOptions` それに応じて。

### 外部スタイルシートを使用する代わりに CSS を埋め込む方法はありますか?
もちろんです。設定できます `CssStyleSheetType` に `CssStyleSheetType.Embedded` 埋め込みスタイルを好む場合。

### 出力 HTML ファイルの名前をカスタマイズするにはどうすればよいですか?
任意のファイル名を指定できます。 `doc.Save` 方法。例えば、 `doc。Save(dataDir + "CustomFileName.html", saveOptions);`.

### Aspose.Words は HTML 以外の形式もサポートしていますか?
はい、PDF、DOCX、TXTなど、様々な形式に対応しています。 [ドキュメント](https://reference.aspose.com/words/net/) 完全なリストについてはこちらをご覧ください。

### さらにサポートやリソースを入手できる場所はどこですか?
さらに詳しいヘルプについては、 [Aspose.Words サポートフォーラム](https://forum.aspose.com/c/words/8)詳細なドキュメントと例は、 [Aspose ウェブサイト](https://reference。aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}