---
title: CSSクラス名プレフィックスを追加する
linktitle: CSSクラス名プレフィックスを追加する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して Word 文書を HTML として保存するときに CSS クラス名プレフィックスを追加する方法を学びます。ステップバイステップ ガイド、コード スニペット、FAQ が含まれています。
weight: 10
url: /ja/net/programming-with-htmlsaveoptions/add-css-class-name-prefix/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# CSSクラス名プレフィックスを追加する

## 導入

ようこそ! Aspose.Words for .NET の世界に飛び込むなら、素晴らしい体験が待っています。今日は、Aspose.Words for .NET を使用して Word 文書を HTML として保存するときに、CSS クラス名プレフィックスを追加する方法について説明します。この機能は、HTML ファイルでクラス名の競合を回避する場合に非常に便利です。

## 前提条件

始める前に、以下のものを用意してください。

-  Aspose.Words for .NET: まだインストールしていない場合は、[ここからダウンロード](https://releases.aspose.com/words/net/).
- 開発環境: Visual Studio またはその他の C# IDE。
-  Word文書: という文書を使用します。`Rendering.docx`プロジェクトディレクトリに配置します。

## 名前空間のインポート

まず、必要な名前空間が C# プロジェクトにインポートされていることを確認します。コード ファイルの先頭に以下を追加します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

それでは、ステップバイステップのガイドを見ていきましょう。

## ステップ1: プロジェクトを設定する

CSS クラス名プレフィックスを追加する前に、プロジェクトを設定しましょう。

### ステップ1.1: 新しいプロジェクトを作成する

 Visual Studioを起動し、新しいコンソールアプリプロジェクトを作成します。次のようなキャッチーな名前を付けます。`AsposeCssPrefixExample`.

### ステップ 1.2: Aspose.Words for .NET を追加する

まだ行っていない場合は、NuGet 経由で Aspose.Words for .NET をプロジェクトに追加します。NuGet パッケージ マネージャー コンソールを開いて、次のコマンドを実行するだけです。

```bash
Install-Package Aspose.Words
```

素晴らしい！これでコーディングを始める準備ができました。

## ステップ2: ドキュメントを読み込む

最初に行う必要があるのは、HTML に変換する Word 文書を読み込むことです。

### ステップ 2.1: ドキュメント パスを定義する

ドキュメントディレクトリへのパスを設定します。このチュートリアルでは、ドキュメントが次のフォルダにあると仮定します。`Documents`プロジェクト ディレクトリ内。

```csharp
string dataDir = @"C:\YourProject\Documents\";
```

### ステップ 2.2: ドキュメントを読み込む

次に、Aspose.Words を使用してドキュメントを読み込みます。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## ステップ3: HTML保存オプションを設定する

次に、CSS クラス名プレフィックスを含めるように HTML 保存オプションを構成する必要があります。

### ステップ3.1: HTML保存オプションを作成する

インスタンス化する`HtmlSaveOptions`オブジェクトを作成し、CSSスタイルシートタイプを`External`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External
};
```

### ステップ3.2: CSSクラス名プレフィックスを設定する

さて、設定しましょう`CssClassNamePrefix`プロパティを希望のプレフィックスに変更します。この例では、`"pfx_"`.

```csharp
saveOptions.CssClassNamePrefix = "pfx_";
```

## ステップ4: ドキュメントをHTMLとして保存する

最後に、設定したオプションを使用してドキュメントを HTML ファイルとして保存します。


出力 HTML ファイルのパスを指定してドキュメントを保存します。

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
```

## ステップ5: 出力を確認する

プロジェクトを実行した後、`Documents`フォルダ内に、`WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html`このファイルをテキストエディタまたはブラウザで開き、CSSクラスにプレフィックスが付いていることを確認します。`pfx_`.

## 結論

これで完了です。これらの手順に従うことで、Aspose.Words for .NET を使用して HTML 出力に CSS クラス名プレフィックスを正常に追加できました。このシンプルでありながら強力な機能により、HTML ドキュメントでクリーンかつ競合のないスタイルを維持できます。

## よくある質問

### 保存操作ごとに異なるプレフィックスを使用できますか?
はい、文書を保存するたびにプレフィックスをカスタマイズできます。`CssClassNamePrefix`財産。

### このメソッドはインライン CSS をサポートしていますか?
の`CssClassNamePrefix`プロパティは外部 CSS で機能します。インライン CSS の場合は、別のアプローチが必要になります。

### 他の HTML 保存オプションを含めるにはどうすればいいですか?
さまざまなプロパティを設定できます`HtmlSaveOptions`HTML出力をカスタマイズするには、[ドキュメント](https://reference.aspose.com/words/net/)詳細についてはこちらをご覧ください。

### HTML をストリームに保存することは可能ですか?
もちろんです！ストリームオブジェクトを渡すことで、ドキュメントをストリームに保存できます。`Save`方法。

### 問題が発生した場合、どうすればサポートを受けることができますか?
サポートを受けるには[Aspose フォーラム](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
