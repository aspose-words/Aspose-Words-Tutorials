---
title: フォントフォルダのデフォルトインスタンスを設定する
linktitle: フォントフォルダのデフォルトインスタンスを設定する
second_title: Aspose.Words ドキュメント処理 API
description: このステップバイステップのチュートリアルで、Aspose.Words for .NET の既定のインスタンスのフォント フォルダーを設定する方法を学びます。Word ドキュメントを簡単にカスタマイズできます。
weight: 10
url: /ja/net/working-with-fonts/set-fonts-folders-default-instance/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# フォントフォルダのデフォルトインスタンスを設定する

## 導入

こんにちは、コーダーの皆さん! .NET で Word 文書を扱っているなら、フォントが適切であることの重要性はご存知でしょう。今日は、Aspose.Words for .NET を使用して既定のインスタンスのフォント フォルダーを設定する方法について詳しく説明します。すべてのカスタム フォントが手元にあり、思い描いたとおりの文書を作成できると想像してみてください。すばらしいと思いませんか? さあ、始めましょう!

## 前提条件

細かい詳細に入る前に、必要なものがすべて揃っていることを確認しましょう。
-  Aspose.Words for .NET: ライブラリがインストールされていることを確認してください。インストールされていない場合は、[ここからダウンロード](https://releases.aspose.com/words/net/).
- 開発環境: Visual Studio またはその他の .NET 互換 IDE。
- C# の基礎知識: C# プログラミングに慣れている必要があります。
- フォント フォルダー: カスタム フォントが含まれるディレクトリ。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートしましょう。これにより、フォント フォルダーの設定に必要なクラスとメソッドにアクセスできるようになります。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

プロセスをシンプルで理解しやすいステップに分解してみましょう。

## ステップ1: データディレクトリを定義する

すべての偉大な旅は 1 つのステップから始まります。私たちの旅は、ドキュメントが保存されているディレクトリを定義することから始まります。Aspose.Words はここで Word ドキュメントを検索します。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

ここで、`"YOUR DOCUMENT DIRECTORY"`ドキュメント ディレクトリへの実際のパスを入力します。これはソース ドキュメントが保存される場所であり、出力が保存される場所です。

## ステップ2: フォントフォルダを設定する

さて、Aspose.Wordsにカスタムフォントの場所を教えましょう。これは、フォントフォルダーを設定することで行われます。`FontSettings.DefaultInstance.SetFontsFolder`方法。

```csharp
FontSettings.DefaultInstance.SetFontsFolder("C:\\MyFonts\\", true);
```

この行では、`"C:\\MyFonts\\"`はカスタムフォントフォルダへのパスです。2番目のパラメータは`true`は、このフォルダー内のフォントを再帰的にスキャンする必要があることを示します。

## ステップ3: ドキュメントを読み込む

フォントフォルダを設定したら、次のステップはWord文書をAspose.Wordsに読み込むことです。これは、`Document`クラス。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

ここ、`dataDir + "Rendering.docx"` Word 文書の完全なパスを参照します。文書が指定されたディレクトリにあることを確認してください。

## ステップ4: ドキュメントを保存する

最後の手順は、フォント フォルダーを設定した後、ドキュメントを保存することです。これにより、カスタム フォントが出力に正しく適用されるようになります。

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersDefaultInstance.pdf");
```

この行は、カスタム フォントが適用された PDF としてドキュメントを保存します。出力ファイルは、ソース ドキュメントと同じディレクトリに配置されます。

## 結論

これで完了です。Aspose.Words for .NET の既定のインスタンスのフォント フォルダーを設定するのは、簡単な手順に分解すれば簡単です。このガイドに従うことで、カスタム フォントがすべて配置された、Word ドキュメントが希望どおりに表示されるようになります。さあ、試してみて、ドキュメントを輝かせましょう。

## よくある質問

### 複数のフォントフォルダを設定できますか?
はい、複数のフォントフォルダを設定するには、`SetFontsFolders`フォルダー パスの配列を受け入れるメソッド。

### Aspose.Words はドキュメントの保存にどのようなファイル形式をサポートしていますか?
Aspose.Words は、DOCX、PDF、HTML、EPUB など、さまざまな形式をサポートしています。

### Aspose.Words でオンライン フォントを使用することは可能ですか?
いいえ、Aspose.Words は現在、ローカル フォント ファイルのみをサポートしています。

### 保存した PDF にカスタム フォントが埋め込まれていることを確認するにはどうすればよいですか?
設定することで`FontSettings`正しく設定され、フォントが使用可能であることが確認されると、Aspose.Words はそれらを PDF 出力に埋め込みます。

### 指定したフォルダーにフォントが見つからない場合はどうなりますか?
指定されたフォントが見つからない場合、Aspose.Words はフォールバック フォントを使用します。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
