---
"description": "Aspose.Words for .NET を使用して Word 文書のシステム フォント フォルダーとカスタム フォント フォルダーを設定し、さまざまな環境で文書が正しく表示されるようにする方法を学習します。"
"linktitle": "フォントフォルダシステムとカスタムフォルダの設定"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "フォントフォルダシステムとカスタムフォルダの設定"
"url": "/ja/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# フォントフォルダシステムとカスタムフォルダの設定

## 導入

独自のフォントスタイルを使ってドキュメントを作成しているのに、別のマシンでフォントが正しく表示されないとしたらどうでしょう。イライラしますよね？そんな時こそ、フォントフォルダーの設定が役立ちます。Aspose.Words for .NET を使えば、システムフォントフォルダーとカスタムフォントフォルダーを定義して、ドキュメントが常に意図したとおりに表示されるようにすることができます。では、その方法を見ていきましょう。

## 前提条件

始める前に、以下のものを用意してください。

- Aspose.Words for .NET ライブラリ: まだダウンロードしていない場合はダウンロードしてください。 [ここ](https://releases。aspose.com/words/net/).
- 開発環境: Visual Studio のような IDE。
- C# の基本知識: C# に精通していると、コード例を理解するのに役立ちます。

## 名前空間のインポート

まず、プロジェクトに必要な名前空間をインポートします。

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

それでは、プロセスを簡単なステップに分解してみましょう。

## ステップ1：ドキュメントを読み込む

まず、Word文書をAspose.Wordsに読み込みます。 `Document` オブジェクト。このドキュメントは、フォントフォルダを設定するドキュメントになります。

```csharp
// ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## ステップ2: フォント設定を初期化する

新しいインスタンスを作成する `FontSettings`このオブジェクトを使用すると、フォント ソースを管理できます。

```csharp
FontSettings fontSettings = new FontSettings();
```

## ステップ3: システムフォントソースを取得する

デフォルトのシステムフォントソースを取得します。Windowsマシンでは、通常「Windows\Fonts」ディレクトリが含まれます。

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## ステップ4: カスタムフォントフォルダを追加する

追加フォントを格納するカスタムフォルダを追加します。これは、システムフォントディレクトリにインストールされていない特定のフォントがある場合に便利です。

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## ステップ5: フォントソースを更新する

フォントソースのリストを配列に変換し、それを `FontSettings` 物体。

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## ステップ6: ドキュメントにフォント設定を適用する

最後に、設定した `FontSettings` ドキュメントに追加し、PDF などの希望の形式で保存します。

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## 結論

これで完了です！これらの手順に従うことで、Word文書でシステムフォントでも特定のディレクトリに保存されているカスタムフォントでも、正しいフォントが使用されるようになります。この設定により、異なる環境でも文書の外観の整合性が維持されます。

## よくある質問

### システム フォルダーとカスタム フォルダーの両方にフォントがない場合はどうなりますか?

Aspose.Words は、不足しているフォントをデフォルトのフォントで置き換え、ドキュメントが読みやすい状態を維持できるようにします。

### 複数のカスタムフォントフォルダを追加できますか?

はい、作成のプロセスを繰り返すことで、複数のカスタムフォントフォルダを追加できます。 `FolderFontSource` オブジェクトをフォント ソース リストに追加します。

### カスタム フォント フォルダーにネットワーク パスを使用することは可能ですか?

はい、ネットワークパスを指定できます。 `FolderFontSource` コンストラクタ。

### Aspose.Words はドキュメントの保存にどのようなファイル形式をサポートしていますか?

Aspose.Words は、DOCX、PDF、HTML など、さまざまな形式をサポートしています。

### フォント置換通知をどのように処理すればよいですか?

フォント置換通知は、 `FontSettings` クラスの `FontSubstitutionWarning` イベント。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}