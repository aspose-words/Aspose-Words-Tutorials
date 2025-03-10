---
title: フォントフォルダの設定 複数のフォルダ
linktitle: フォントフォルダの設定 複数のフォルダ
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して Word 文書に複数のフォント フォルダーを設定する方法を学びます。このステップ バイ ステップ ガイドでは、文書に必要なフォントが正確に使用されるようにします。
weight: 10
url: /ja/net/working-with-fonts/set-fonts-folders-multiple-folders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# フォントフォルダの設定 複数のフォルダ

## 導入

Word 文書で複数のフォント ソースを管理する方法を考えたことはありませんか? おそらく、さまざまなフォルダーにフォント コレクションが散在していて、文書でそれらをシームレスに使用する方法が必要です。 幸運にも、今日は Aspose.Words for .NET を使用してフォント フォルダーを設定する方法について詳しく説明します。 このガイドでは、プロセスを段階的に説明し、文書が希望どおりに表示されるようにします。

## 前提条件

始める前に、必要なものがすべて揃っていることを確認しましょう。この手順を実行するために必要なものは次のとおりです。

-  Aspose.Words for .NET: まだダウンロードしていない場合は、Aspose.Words for .NETをダウンロードしてインストールしてください。[ここ](https://releases.aspose.com/words/net/).
- 開発環境: Visual Studio またはその他の .NET 互換開発環境。
- C# の基本知識: C# に少し精通していると、例を理解するのに役立ちます。
- フォント ファイル: フォント ファイルが簡単にアクセスできるディレクトリに保存されていることを確認します。

## 名前空間のインポート

まず最初に、C# プロジェクトに必要な名前空間をインポートしましょう。これにより、必要なすべての Aspose.Words 機能にアクセスできるようになります。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

これで準備が整いましたので、Aspose.Words for .NET でフォント フォルダーを設定するためのステップ バイ ステップ ガイドに進みましょう。

## ステップ1: ドキュメントを読み込む

さて、まずは作業したい Word 文書を読み込んでみましょう。文書のパスが準備されていることを確認してください。この例では、「Rendering.docx」という名前の文書を使用します。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

ここでは、指定されたディレクトリからドキュメントを読み込みます。とても簡単ですよね?

## ステップ2: FontSettingsオブジェクトを作成する

次に、`FontSettings`オブジェクト。このオブジェクトを使用すると、ドキュメントのフォント ソースを管理できます。

```csharp
FontSettings fontSettings = new FontSettings();
```

これ`FontSettings`オブジェクトは、使用するフォント フォルダーを定義するのに役立ちます。

## ステップ3: フォントフォルダを設定する

次は重要な部分、フォントフォルダの設定です。ここではフォントが配置されているディレクトリを指定します。この例では、「C:\MyFonts」にフォントがあります。\" および "D:\Misc\Fonts\「」。

```csharp
fontSettings.SetFontsFolders(new[] { @"C:\MyFonts\", @"D:\Misc\Fonts\" }, true);
```

2番目のパラメータ（`true` ）は、これらのフォルダがデフォルトのフォントソースを上書きすることを示します。システムフォントソースも保持したい場合は、`GetFontSources`そして`SetFontSources`.

## ステップ4: ドキュメントにフォント設定を適用する

フォント フォルダーを設定したら、これらの設定をドキュメントに適用する必要があります。これにより、レンダリング中にドキュメントで指定されたフォントが使用されるようになります。

```csharp
doc.FontSettings = fontSettings;
```

## ステップ5: ドキュメントを保存する

最後に、ドキュメントを保存しましょう。フォントの動作を確認するために、PDF として保存します。

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersMultipleFolders.pdf");
```

これで完了です。ドキュメントに複数のフォント フォルダーが正常に設定されました。

## 結論

ドキュメント内のフォントを管理するのは大変な作業のように思えるかもしれませんが、Aspose.Words for .NET を使えば簡単です。これらの簡単な手順に従うだけで、ドキュメントの見栄えをプロフェッショナルなものにし、必要なフォントを正確に使用できます。特定のブランド化が必要なプロジェクトに取り組んでいる場合でも、ドキュメントの外観をより細かく制御したい場合でも、フォント フォルダーの設定は習得する価値のあるスキルです。

## よくある質問

### フォント フォルダーにネットワーク パスを使用できますか?
はい、フォント フォルダーにネットワーク パスを使用できます。アプリケーションからパスにアクセスできることを確認してください。

### 指定されたフォルダーにフォントがない場合はどうなりますか?
フォントが見つからない場合、Aspose.Words は指定された既定のフォントに戻るか、代替フォントを使用します。

### システムフォントを上書きせずにフォントフォルダーを追加できますか?
もちろんです！`FontSettings.GetFontSources`既存のソースを取得し、カスタムフォルダと組み合わせるには、`FontSettings.SetFontSources`.

### 追加できるフォント フォルダーの数に制限はありますか?
フォント フォルダーの数に厳密な制限はありません。ただし、フォルダーの数が増えるとフォントの読み込み時間が長くなる可能性があるため、パフォーマンスに注意してください。

### ドキュメントで使用されているフォントを確認するにはどうすればよいですか?
あなたは`FontSettings.GetFontsSources`ドキュメントに現在設定されているフォント ソースを取得して検査するメソッド。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
