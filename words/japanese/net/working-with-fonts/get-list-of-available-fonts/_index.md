---
title: 利用可能なフォントのリストを取得する
linktitle: 利用可能なフォントのリストを取得する
second_title: Aspose.Words ドキュメント処理 API
description: この詳細なステップバイステップのチュートリアルでは、Aspose.Words for .NET を使用して使用可能なフォントのリストを取得する方法を説明します。フォント管理スキルを高めましょう。
weight: 10
url: /ja/net/working-with-fonts/get-list-of-available-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 利用可能なフォントのリストを取得する

## 導入

Word 文書のフォント管理に苦労したことはありませんか? .NET 開発者なら、Aspose.Words for .NET が役に立ちます! この強力なライブラリは、Word 文書をプログラムで作成および操作するのに役立つだけでなく、広範なフォント管理機能も提供します。 このガイドでは、Aspose.Words for .NET を使用して使用可能なフォントのリストを取得する方法について、ステップ バイ ステップのチュートリアルで説明します。 理解しやすい手順に分解して、簡単に理解できるようにします。 では、早速始め、フォント管理を楽にしましょう!

## 前提条件

始める前に、いくつか必要なものがあります:

-  Aspose.Words for .NET: Aspose.Words for .NETライブラリがインストールされていることを確認してください。ここからダウンロードできます。[ここ](https://releases.aspose.com/words/net/).
- Visual Studio: この例では、開発環境として Visual Studio を使用します。
- .NET Framework: マシンに .NET Framework がインストールされていることを確認します。
- ドキュメント ディレクトリ: ドキュメントが保存されるディレクトリ パス。

## 名前空間のインポート

まず、必要な名前空間をプロジェクトにインポートします。

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

## ステップ1: フォント設定を初期化する

最初のステップは、フォント設定を初期化することです。これにより、ドキュメントのフォント ソースを管理できるようになります。

```csharp
FontSettings fontSettings = new FontSettings();
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

- FontSettings: このクラスは、フォントの置換とフォント ソースの設定を指定するために使用されます。
- fontSources: 現在のフォント設定から既存のフォント ソースのリストを作成します。

## ステップ2: ドキュメントディレクトリを定義する

次に、ドキュメント ディレクトリへのパスを指定します。ここで Aspose.Words はフォントを検索します。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

-  dataDir: この文字列変数はフォントが保存されているディレクトリへのパスを保持します。`"YOUR DOCUMENT DIRECTORY"`実際のパスを使用します。

## ステップ3: カスタムフォントフォルダを追加する

ここで、新しいフォルダー ソースを追加して、Aspose.Words にこのフォルダーでフォントを検索するように指示します。

```csharp
FolderFontSource folderFontSource = new FolderFontSource(dataDir, true);
```

- FolderFontSource: このクラスはフォルダのフォントソースを表します。2番目のパラメータ(`true`) は、サブフォルダー内でフォントを再帰的に検索するかどうかを示します。

## ステップ4: フォントソースを更新する

既存のフォント ソースのリストにカスタム フォント フォルダーを追加し、フォント設定を更新します。

```csharp
fontSources.Add(folderFontSource);
FontSourceBase[] updatedFontSources = fontSources.ToArray();
```

- fontSources.Add(folderFontSource): 既存のフォント ソースにカスタム フォント フォルダーを追加します。
- updatedFontSources: フォント ソースのリストを配列に変換します。

## ステップ5: フォントを取得して表示する

最後に、利用可能なフォントを取得し、その詳細を表示します。

```csharp
foreach (PhysicalFontInfo fontInfo in updatedFontSources[0].GetAvailableFonts())
{
    Console.WriteLine("FontFamilyName : " + fontInfo.FontFamilyName);
    Console.WriteLine("FullFontName  : " + fontInfo.FullFontName);
    Console.WriteLine("Version  : " + fontInfo.Version);
    Console.WriteLine("FilePath : " + fontInfo.FilePath);
}
```

- GetAvailableFonts(): 更新されたリストの最初のフォント ソースから使用可能なフォントのリストを取得します。
-  fontInfo: のインスタンス`PhysicalFontInfo`各フォントの詳細が記載されています。

## 結論

おめでとうございます! Aspose.Words for .NET を使用して、使用可能なフォントのリストを取得できました。このチュートリアルでは、フォント設定の初期化からフォントの詳細の表示まで、各手順を順を追って説明しました。この知識があれば、Word 文書内のフォントを簡単に管理できます。Aspose.Words for .NET は、文書処理機能を大幅に強化できる強力なツールです。ぜひ、開発プロセスをさらに効率化するためのその他の機能もご覧ください。

## よくある質問

### Aspose.Words for .NET を他の .NET フレームワークと一緒に使用できますか?
はい、Aspose.Words for .NET は、.NET Core や .NET 5+ を含むさまざまな .NET フレームワークと互換性があります。

### Aspose.Words for .NET をインストールするにはどうすればよいですか?
Visual Studio の NuGet パッケージ マネージャーで「Aspose.Words」を検索してインストールできます。

### 複数のカスタムフォントフォルダを追加することは可能ですか?
はい、複数のカスタムフォントフォルダを作成して追加できます。`FolderFontSource`インスタンスを作成してフォント ソース リストに追加します。

### 特定のフォント ソースからフォントの詳細を取得できますか?
はい、フォントソースのインデックスを指定することで、任意のフォントソースからフォントの詳細を取得できます。`updatedFontSources`配列。

### Aspose.Words for .NET はフォントの置換をサポートしていますか?
はい、元のフォントが利用できない場合でもテキストが正しくレンダリングされるように、フォントの置換をサポートしています。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
