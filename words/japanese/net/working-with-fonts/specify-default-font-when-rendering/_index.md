---
"description": "Aspose.Words for .NET を使用して Word 文書をレンダリングする際に、デフォルトのフォントを指定する方法を学びます。プラットフォーム間で一貫したドキュメントの外観を実現します。"
"linktitle": "レンダリング時にデフォルトのフォントを指定する"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "レンダリング時にデフォルトのフォントを指定する"
"url": "/ja/net/working-with-fonts/specify-default-font-when-rendering/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# レンダリング時にデフォルトのフォントを指定する

## 導入

Word文書を異なるプラットフォーム間で正しくレンダリングすることは、特にフォントの互換性を考慮すると、困難な場合があります。外観の一貫性を保つ一つの方法は、文書をPDFやその他の形式にレンダリングする際に、デフォルトのフォントを指定することです。このチュートリアルでは、Aspose.Words for .NETを使用してデフォルトのフォントを設定する方法を学び、どのプラットフォームで表示しても文書が美しく表示されるようにします。

## 前提条件

コードに進む前に、このチュートリアルで必要な手順について説明しましょう。

- Aspose.Words for .NET: 最新バージョンがインストールされていることを確認してください。ダウンロードできます。 [ここ](https://releases。aspose.com/words/net/).
- 開発環境: Visual Studio またはその他の .NET 開発環境。
- C# の基本知識: このチュートリアルでは、読者が C# プログラミングに精通していることを前提としています。

## 名前空間のインポート

まず、必要な名前空間をインポートする必要があります。これにより、Aspose.Words の操作に必要なクラスとメソッドにアクセスできるようになります。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

ここで、デフォルトのフォントを指定するプロセスを、わかりやすい手順に分解してみましょう。

## ステップ1: ドキュメントディレクトリを設定する

まず、ドキュメントディレクトリへのパスを定義します。ここに入力ファイルと出力ファイルが保存されます。

```csharp
// ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## ステップ2: ドキュメントを読み込む

次に、レンダリングしたいドキュメントを読み込みます。この例では、「Rendering.docx」というファイルを使用します。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## ステップ3: フォント設定を構成する

インスタンスを作成する `FontSettings` デフォルトのフォントを指定します。レンダリング時に定義されたフォントが見つからない場合、Aspose.Words はマシン上で利用可能な最も近いフォントを使用します。

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

最後に、ドキュメントを希望の形式で保存します。今回はPDF形式で保存します。

```csharp
doc.Save(dataDir + "WorkingWithFonts.SpecifyDefaultFontWhenRendering.pdf");
```

## 結論

これらの手順に従うことで、Word文書が指定されたデフォルトフォントでレンダリングされ、異なるプラットフォーム間で一貫性が維持されます。これは、文書を広く共有する場合や、フォントの可用性が異なるシステムで閲覧する場合に特に役立ちます。


## よくある質問

### Aspose.Words でデフォルトのフォントを指定するのはなぜですか?
デフォルトのフォントを指定すると、元のフォントが使用できない場合でも、さまざまなプラットフォーム間でドキュメントの表示が統一されます。

### レンダリング中にデフォルトのフォントが見つからない場合はどうなりますか?
Aspose.Words は、ドキュメントの外観を可能な限り維持するために、マシン上で使用可能な最も近いフォントを使用します。

### 複数のデフォルトフォントを指定できますか?
いいえ、デフォルトフォントは1つしか指定できません。ただし、特定のケースでは、 `FontSettings` クラス。

### Aspose.Words for .NET は、すべてのバージョンの Word 文書と互換性がありますか?
はい、Aspose.Words for .NET は、DOC、DOCX、RTF など、幅広い Word ドキュメント形式をサポートしています。

### 問題が発生した場合、どこでサポートを受けることができますか?
Asposeコミュニティと開発者からのサポートは、 [Aspose.Words サポートフォーラム](https://forum。aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}