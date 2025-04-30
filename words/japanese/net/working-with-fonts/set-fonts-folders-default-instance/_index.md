---
"description": "このステップバイステップのチュートリアルでは、Aspose.Words for .NET のデフォルトインスタンスのフォントフォルダーを設定する方法を学びます。Word 文書を簡単にカスタマイズできます。"
"linktitle": "フォントフォルダのデフォルトインスタンスを設定する"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "フォントフォルダのデフォルトインスタンスを設定する"
"url": "/ja/net/working-with-fonts/set-fonts-folders-default-instance/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# フォントフォルダのデフォルトインスタンスを設定する

## 導入

こんにちは、コーダーの皆さん！.NETでWord文書を扱っている方なら、フォント選びの重要性はご存知でしょう。今日は、Aspose.Words for .NETを使って、デフォルトのインスタンスのフォントフォルダーを設定する方法について詳しく解説します。カスタムフォントがすべて手元にあって、思い描いた通りの文書が作れるなんて、想像してみてください。最高ですよね？さあ、始めましょう！

## 前提条件

細かい詳細に入る前に、必要なものがすべて揃っていることを確認しましょう。
- Aspose.Words for .NET: ライブラリがインストールされていることを確認してください。インストールされていない場合は、 [ここからダウンロード](https://releases。aspose.com/words/net/).
- 開発環境: Visual Studio またはその他の .NET 互換 IDE。
- C# の基本知識: C# プログラミングに慣れている必要があります。
- フォント フォルダー: カスタム フォントが含まれるディレクトリ。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートしましょう。これにより、フォントフォルダの設定に必要なクラスやメソッドにアクセスできるようになります。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

プロセスをシンプルで理解しやすいステップに分解してみましょう。

## ステップ1: データディレクトリを定義する

すべての素晴らしい旅は、たった一つのステップから始まります。私たちの旅も、ドキュメントが保存されているディレクトリを定義することから始まります。Aspose.Words は、このディレクトリで Word 文書を検索します。

```csharp
// ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

ここで、 `"YOUR DOCUMENT DIRECTORY"` ドキュメントディレクトリへの実際のパスを入力します。これはソースドキュメントが保存される場所であり、出力が保存される場所です。

## ステップ2: フォントフォルダを設定する

さて、Aspose.Wordsにカスタムフォントの場所を教えましょう。これは、フォントフォルダを設定することで行います。 `FontSettings.DefaultInstance.SetFontsFolder` 方法。

```csharp
FontSettings.DefaultInstance.SetFontsFolder("C:\\MyFonts\\", true);
```

この行では、 `"C:\\MyFonts\\"` はカスタムフォントフォルダへのパスです。2番目のパラメータは `true`は、このフォルダー内のフォントを再帰的にスキャンする必要があることを示します。

## ステップ3: ドキュメントを読み込む

フォントフォルダの設定が完了したら、次のステップはWord文書をAspose.Wordsに読み込むことです。これは、 `Document` クラス。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

ここ、 `dataDir + "Rendering.docx"` Word文書のフルパスを指します。文書が指定されたディレクトリにあることを確認してください。

## ステップ4: ドキュメントを保存する

最後のステップは、フォントフォルダを設定した後、ドキュメントを保存することです。これにより、カスタムフォントが出力に正しく適用されるようになります。

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersDefaultInstance.pdf");
```

この行は、カスタムフォントを適用したPDFとしてドキュメントを保存します。出力ファイルはソースドキュメントと同じディレクトリに保存されます。

## 結論

これで完了です！Aspose.Words for .NET のデフォルトインスタンスのフォントフォルダーの設定は、シンプルな手順に分解すれば簡単です。このガイドに従えば、カスタムフォントがすべて適用され、Word 文書が思い通りの見栄えになります。さあ、試してみて、素敵な文書を作りましょう！

## よくある質問

### 複数のフォントフォルダを設定できますか?
はい、複数のフォントフォルダを設定するには、 `SetFontsFolders` フォルダー パスの配列を受け入れるメソッド。

### Aspose.Words はドキュメントの保存にどのようなファイル形式をサポートしていますか?
Aspose.Words は、DOCX、PDF、HTML、EPUB など、さまざまな形式をサポートしています。

### Aspose.Words でオンライン フォントを使用することは可能ですか?
いいえ、Aspose.Words は現在、ローカル フォント ファイルのみをサポートしています。

### 保存した PDF にカスタム フォントが埋め込まれていることを確認するにはどうすればよいですか?
設定することで `FontSettings` 正しく設定され、フォントが使用可能であることが確認されると、Aspose.Words はそれらを PDF 出力に埋め込みます。

### 指定されたフォルダーにフォントが見つからない場合はどうなりますか?
指定されたフォントが見つからない場合、Aspose.Words はフォールバック フォントを使用します。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}