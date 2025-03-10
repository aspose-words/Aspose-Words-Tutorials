---
title: リソースのエクスポート
linktitle: リソースのエクスポート
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して Word 文書を HTML として保存しながら、CSS やフォントなどのリソースをエクスポートする方法を学びます。ステップバイステップのガイドに従ってください。
weight: 10
url: /ja/net/programming-with-htmlsaveoptions/export-resources/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# リソースのエクスポート

## 導入

こんにちは、テクノロジー愛好家の皆さん! Word 文書を HTML に変換する必要があると感じたことがあれば、ここが最適な場所です。今日は、Aspose.Words for .NET の素晴らしい世界に飛び込みます。この強力なライブラリを使用すると、Word 文書をプログラムで簡単に操作できます。このチュートリアルでは、Aspose.Words for .NET を使用して Word 文書を HTML として保存するときに、フォントや CSS などのリソースをエクスポートする手順を説明します。楽しくてためになる旅に出発しましょう!

## 前提条件

コードに進む前に、始めるのに必要なものがすべて揃っていることを確認しましょう。簡単なチェックリストを以下に示します。

1.  Visual Studio: お使いのマシンにVisual Studioがインストールされていることを確認してください。[Visual Studio の Web サイト](https://visualstudio.microsoft.com/).
2. Aspose.Words for .NET: Aspose.Words for .NETライブラリが必要です。まだ入手していない場合は、無料トライアル版を入手してください。[Aspose リリース](https://releases.aspose.com/words/net/)または、[アポーズストア](https://purchase.aspose.com/buy).
3. C# の基礎知識: C# の基礎を理解しておくと、コード例を理解するのに役立ちます。

すべて理解できましたか? 素晴らしい! 必要な名前空間のインポートに進みましょう。

## 名前空間のインポート

Aspose.Words for .NET を使用するには、プロジェクトに関連する名前空間を含める必要があります。手順は次のとおりです。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

これらの名前空間は、チュートリアルで使用する Aspose.Words のクラスとメソッドにアクセスするために不可欠です。

Word 文書を HTML として保存するときにリソースをエクスポートするプロセスを詳しく説明します。手順を 1 つ 1 つ説明していくので、わかりやすいでしょう。

## ステップ1: ドキュメントディレクトリを設定する

まず最初に、ドキュメント ディレクトリへのパスを指定する必要があります。これは、Word ドキュメントが保存される場所であり、HTML ファイルが保存される場所です。

```csharp
//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

交換する`"YOUR DOCUMENT DIRECTORY"`ディレクトリへの実際のパスを入力します。

## ステップ2: Word文書を読み込む

次に、HTMLに変換したいWord文書を読み込みます。このチュートリアルでは、次の名前の文書を使用します。`Rendering.docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

このコード行は、指定されたディレクトリからドキュメントを読み込みます。

## ステップ3: HTML保存オプションを設定する

CSSやフォントなどのリソースをエクスポートするには、`HtmlSaveOptions`この手順は、HTML 出力が適切に構造化され、必要なリソースが含まれていることを確認するために重要です。

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
- `ExportFontResources = true`: これにより、フォント リソースのエクスポートが可能になります。
- `ResourceFolder = dataDir + "Resources"`: リソース (フォントや CSS ファイルなど) が保存されるローカル フォルダーを指定します。
- `ResourceFolderAlias = "http://example.com/resources"`: HTML ファイルで使用されるリソース フォルダーのエイリアスを設定します。

## ステップ4: ドキュメントをHTMLとして保存する

保存オプションを設定したら、最後の手順としてドキュメントを HTML ファイルとして保存します。手順は次のとおりです。

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

このコード行は、エクスポートされたリソースとともにドキュメントを HTML 形式で保存します。

## 結論

これで完了です。Aspose.Words for .NET を使用して Word 文書を HTML として保存しながら、リソースを正常にエクスポートできました。この強力なライブラリを使用すると、Word 文書をプログラムで処理することが簡単になります。Web アプリケーションで作業している場合でも、オフラインで使用するために文書を変換する必要がある場合でも、Aspose.Words が役立ちます。

## よくある質問

### フォントや CSS と一緒に画像をエクスポートできますか?
はい、できます。Aspose.Words for .NETは画像のエクスポートもサポートしています。`HtmlSaveOptions`それに応じて。

### 外部スタイルシートを使用する代わりに CSS を埋め込む方法はありますか?
もちろんです。設定できます`CssStyleSheetType`に`CssStyleSheetType.Embedded`埋め込みスタイルを好む場合。

### 出力 HTML ファイルの名前をカスタマイズするにはどうすればよいですか?
任意のファイル名を指定できます。`doc.Save`方法。例えば、`doc.Save(dataDir + "CustomFileName.html", saveOptions);`.

### Aspose.Words は HTML 以外の形式もサポートしていますか?
はい、PDF、DOCX、TXTなど、さまざまな形式をサポートしています。[ドキュメント](https://reference.aspose.com/words/net/)完全なリストについてはこちらをご覧ください。

### さらにサポートやリソースを入手できる場所はどこですか?
さらに詳しい情報については、[Aspose.Words サポート フォーラム](https://forum.aspose.com/c/words/8)詳細なドキュメントと例は、[Aspose ウェブサイト](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
