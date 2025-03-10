---
title: レンダリング時にデフォルトのフォントを指定する
linktitle: レンダリング時にデフォルトのフォントを指定する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して Word 文書をレンダリングするときに既定のフォントを指定する方法を学習します。プラットフォーム間で一貫した文書の外観を確保します。
weight: 10
url: /ja/net/working-with-fonts/specify-default-font-when-rendering/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# レンダリング時にデフォルトのフォントを指定する

## 導入

Word 文書をさまざまなプラットフォームで正しくレンダリングすることは、特にフォントの互換性を扱う場合には難しい場合があります。一貫した外観を維持する方法の 1 つは、文書を PDF またはその他の形式にレンダリングするときに既定のフォントを指定することです。このチュートリアルでは、Aspose.Words for .NET を使用して既定のフォントを設定し、どこで表示しても文書が適切に表示されるようにする方法について説明します。

## 前提条件

コードに進む前に、このチュートリアルに沿って実行するために必要な内容について説明します。

- Aspose.Words for .NET: 最新バージョンがインストールされていることを確認してください。ダウンロードできます。[ここ](https://releases.aspose.com/words/net/).
- 開発環境: Visual Studio またはその他の .NET 開発環境。
- C# の基本知識: このチュートリアルでは、C# プログラミングに精通していることを前提としています。

## 名前空間のインポート

開始するには、必要な名前空間をインポートする必要があります。これにより、Aspose.Words の操作に必要なクラスとメソッドにアクセスできるようになります。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

ここで、デフォルトのフォントを指定するプロセスを、わかりやすい手順に分解してみましょう。

## ステップ1: ドキュメントディレクトリを設定する

まず、ドキュメント ディレクトリへのパスを定義します。ここに入力ファイルと出力ファイルが保存されます。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## ステップ2: ドキュメントを読み込む

次に、レンダリングするドキュメントを読み込みます。この例では、「Rendering.docx」という名前のファイルを使用します。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## ステップ3: フォント設定を構成する

インスタンスを作成する`FontSettings`デフォルトのフォントを指定します。レンダリング中に定義されたフォントが見つからない場合、Aspose.Words はマシン上で使用可能な最も近いフォントを使用します。

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";
```

## ステップ4: ドキュメントにフォント設定を適用する

構成されたフォント設定をドキュメントに割り当てます。

```csharp
doc.FontSettings = fontSettings;
```

## ステップ5: ドキュメントを保存する

最後に、ドキュメントを希望の形式で保存します。この場合は、PDF として保存します。

```csharp
doc.Save(dataDir + "WorkingWithFonts.SpecifyDefaultFontWhenRendering.pdf");
```

## 結論

これらの手順に従うことで、Word 文書が指定された既定のフォントでレンダリングされ、異なるプラットフォーム間で一貫性が維持されます。これは、文書が広く共有されている場合や、フォントの可用性が異なるシステムで表示される場合に特に便利です。


## よくある質問

### Aspose.Words でデフォルトのフォントを指定するのはなぜですか?
デフォルトのフォントを指定すると、元のフォントが使用できない場合でも、さまざまなプラットフォーム間でドキュメントの一貫した表示が保証されます。

### レンダリング中にデフォルトのフォントが見つからない場合はどうなりますか?
Aspose.Words は、ドキュメントの外観を可能な限り維持するために、マシン上で使用可能な最も近いフォントを使用します。

### 複数のデフォルトフォントを指定できますか?
いいえ、デフォルトフォントは1つしか指定できません。ただし、特定のケースでは、`FontSettings`クラス。

### Aspose.Words for .NET はすべてのバージョンの Word 文書と互換性がありますか?
はい、Aspose.Words for .NET は、DOC、DOCX、RTF など、さまざまな Word ドキュメント形式をサポートしています。

### 問題が発生した場合、どこでサポートを受けることができますか?
 Asposeコミュニティと開発者からのサポートは、[Aspose.Words サポート フォーラム](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
