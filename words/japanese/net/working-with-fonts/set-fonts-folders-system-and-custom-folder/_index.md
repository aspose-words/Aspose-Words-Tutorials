---
title: フォントフォルダシステムとカスタムフォルダを設定する
linktitle: フォントフォルダシステムとカスタムフォルダを設定する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して Word 文書にシステム フォント フォルダーとカスタム フォント フォルダーを設定し、さまざまな環境で文書が正しく表示されるようにする方法を学習します。
weight: 10
url: /ja/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# フォントフォルダシステムとカスタムフォルダを設定する

## 導入

独自のフォント スタイルを使用してドキュメントを作成しているときに、別のマシンでフォントが正しく表示されないことに気付いたとします。イライラしますよね。ここで、フォント フォルダーの構成が役立ちます。Aspose.Words for .NET を使用すると、システム フォント フォルダーとカスタム フォント フォルダーを定義して、ドキュメントが常に意図したとおりに表示されるようにすることができます。これを実現する方法について詳しく説明します。

## 前提条件

始める前に、以下のものを用意してください。

-  Aspose.Words for .NET ライブラリ: まだダウンロードしていない場合はダウンロードしてください[ここ](https://releases.aspose.com/words/net/).
- 開発環境: Visual Studio のような IDE。
- C# の基礎知識: C# に精通していると、コード例を理解するのに役立ちます。

## 名前空間のインポート

まず、プロジェクトに必要な名前空間をインポートします。

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

それでは、プロセスを簡単なステップに分解してみましょう。

## ステップ1: ドキュメントを読み込む

まず、Word文書をAspose.Wordsに読み込みます。`Document`オブジェクト。このドキュメントは、フォント フォルダーを設定するドキュメントになります。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## ステップ2: フォント設定を初期化する

新しいインスタンスを作成する`FontSettings`このオブジェクトを使用すると、フォント ソースを管理できます。

```csharp
FontSettings fontSettings = new FontSettings();
```

## ステップ3: システムフォントソースを取得する

デフォルトのシステムフォントソースを取得します。Windowsマシンでは、通常、これには「Windows\Fonts」が含まれます。\「ディレクトリ」

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## ステップ4: カスタムフォントフォルダを追加する

追加のフォントを含むカスタム フォルダーを追加します。これは、システム フォント ディレクトリに特定のフォントがインストールされていない場合に便利です。

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## ステップ5: フォントソースを更新する

フォントソースのリストを配列に変換し、それを`FontSettings`物体。

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## ステップ6: ドキュメントにフォント設定を適用する

最後に、設定した`FontSettings`ドキュメントに追加し、PDF などの希望の形式で保存します。

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## 結論

これで完了です。これらの手順に従うことで、システム フォントでも、特定のディレクトリに保存されているカスタム フォントでも、Word 文書で正しいフォントが使用されるようになります。この設定により、さまざまな環境間で文書の外観の整合性が維持されます。

## よくある質問

### システム フォルダーとカスタム フォルダーの両方にフォントがない場合はどうなりますか?

Aspose.Words は、不足しているフォントをデフォルトのフォントで置き換えて、ドキュメントが読みやすい状態を維持できるようにします。

### 複数のカスタムフォントフォルダーを追加できますか?

はい、作成のプロセスを繰り返すことで、複数のカスタムフォントフォルダを追加できます。`FolderFontSource`オブジェクトをフォント ソース リストに追加します。

### カスタムフォントフォルダーにネットワークパスを使用することは可能ですか?

はい、ネットワークパスを指定できます。`FolderFontSource`コンストラクタ。

### Aspose.Words はドキュメントの保存にどのようなファイル形式をサポートしていますか?

Aspose.Words は、DOCX、PDF、HTML など、さまざまな形式をサポートしています。

### フォント置換通知をどのように処理すればよいですか?

フォント置換通知は、`FontSettings`クラスの`FontSubstitutionWarning`イベント。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
