---
title: フォントフォールバック設定
linktitle: フォントフォールバック設定
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET でフォント フォールバック設定を設定する方法を学びます。この包括的なガイドにより、ドキュメント内のすべての文字が正しく表示されるようになります。
weight: 10
url: /ja/net/working-with-fonts/set-font-fallback-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# フォントフォールバック設定

## 導入

異なる言語や特殊文字などの多様なテキスト要素を含むドキュメントを扱う場合、これらの要素が正しく表示されるようにすることが重要です。Aspose.Words for .NET には、フォント フォールバック設定と呼ばれる強力な機能があり、元のフォントが特定の文字をサポートしていない場合にフォントを置き換えるルールを定義するのに役立ちます。このガイドでは、Aspose.Words for .NET を使用してフォント フォールバック設定を設定する方法を、ステップ バイ ステップのチュートリアルで説明します。

## 前提条件

チュートリアルに進む前に、次の前提条件が満たされていることを確認してください。

- C# の基礎知識: C# プログラミング言語と .NET フレームワークに精通していること。
-  Aspose.Words for .NET: ダウンロードしてインストールしてください。[ダウンロードリンク](https://releases.aspose.com/words/net/).
- 開発環境: コードを記述して実行するための Visual Studio のようなセットアップ。
- サンプル文書: サンプル文書(例:`Rendering.docx`) テストの準備ができました。
- フォント フォールバック ルール XML: フォント フォールバック ルールを定義する XML ファイルを準備します。

## 名前空間のインポート

Aspose.Words を使用するには、必要な名前空間をインポートする必要があります。これにより、ドキュメント処理に必要なさまざまなクラスとメソッドにアクセスできるようになります。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;
```

## ステップ1: ドキュメントディレクトリを定義する

まず、ドキュメントが保存されているディレクトリを定義します。これは、ドキュメントを見つけて処理するために不可欠です。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## ステップ2: ドキュメントを読み込む

ドキュメントをAspose.Wordsにロードする`Document`オブジェクト。この手順により、ドキュメントをプログラムで操作できるようになります。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## ステップ3: フォント設定を構成する

新規作成`FontSettings`オブジェクトを作成し、XML ファイルからフォント フォールバック設定を読み込みます。この XML ファイルには、フォント フォールバックのルールが含まれています。

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.FallbackSettings.Load(dataDir + "Font fallback rules.xml");
```

## ステップ4: ドキュメントにフォント設定を適用する

設定された割り当て`FontSettings`ドキュメントに追加します。これにより、ドキュメントをレンダリングするときにフォント フォールバック ルールが適用されます。

```csharp
doc.FontSettings = fontSettings;
```

## ステップ5: ドキュメントを保存する

最後に、ドキュメントを保存します。保存操作中にフォント フォールバック設定が使用され、適切なフォントの置き換えが確実に行われます。

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontFallbackSettings.pdf");
```

## XML ファイル: フォント フォールバック ルール

フォント フォールバック ルールを定義する XML ファイルの例を次に示します。

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<FontFallbackSettings xmlns="Aspose.Words">
    <FallbackTable>
        <Rule Ranges="0B80-0BFF" FallbackFonts="Vijaya"/>
        <Rule Ranges="1F300-1F64F" FallbackFonts="Segoe UI Emoji, Segoe UI Symbol"/>
        <Rule Ranges="2000-206F, 2070-209F, 20B9" FallbackFonts="Arial" />
        <Rule Ranges="3040-309F" FallbackFonts="MS Gothic" BaseFonts="Times New Roman"/>
        <Rule Ranges="3040-309F" FallbackFonts="MS Mincho"/>
        <Rule FallbackFonts="Arial Unicode MS"/>
    </FallbackTable>
</FontFallbackSettings>
```

## 結論

これらの手順に従うことで、Aspose.Words for .NET でフォント フォールバック設定を効果的に設定して使用できます。これにより、元のフォントが特定の文字をサポートしていない場合でも、ドキュメントですべての文字が正しく表示されるようになります。これらの設定を実装すると、ドキュメントの品質と読みやすさが大幅に向上します。

## よくある質問

### Q1: フォントフォールバックとは何ですか?

フォント フォールバックは、元のフォントが特定の文字をサポートしていない場合にフォントを置き換えて、すべてのテキスト要素が適切に表示されるようにする機能です。

### Q2: 複数のフォールバックフォントを指定できますか?

はい、XML ルールで複数のフォールバック フォントを指定できます。Aspose.Words は、文字をサポートするフォントが見つかるまで、指定された順序で各フォントをチェックします。

### Q3: Aspose.Words for .NET はどこからダウンロードできますか?

ダウンロードはこちらから[Aspose ダウンロード ページ](https://releases.aspose.com/words/net/).

### Q4: フォントフォールバックルールの XML ファイルを作成するにはどうすればよいですか?

XML ファイルは任意のテキスト エディターを使用して作成できます。このチュートリアルで提供されている例に示されている構造に従う必要があります。

### Q5: Aspose.Words のサポートはありますか?

はい、サポートは[Aspose.Words サポート フォーラム](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
