---
title: 図形を挿入
linktitle: 図形を挿入
second_title: Aspose.Words ドキュメント処理 API
description: ステップバイステップ ガイドを使用して、Aspose.Words for .NET を使用して Word 文書に図形を挿入および操作する方法を学習します。
weight: 10
url: /ja/net/programming-with-shapes/insert-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 図形を挿入

## 導入

見た目が魅力的で構造がしっかりした Word 文書を作成する場合、図形が重要な役割を果たします。矢印、ボックス、複雑なカスタム図形を追加する場合でも、これらの要素をプログラムで操作する機能は、比類のない柔軟性を提供します。このチュートリアルでは、Aspose.Words for .NET を使用して Word 文書に図形を挿入および操作する方法について説明します。

## 前提条件

チュートリアルに進む前に、次の前提条件を満たしていることを確認してください。

1.  Aspose.Words for .NET: 最新バージョンをダウンロードしてインストールしてください。[Aspose リリース ページ](https://releases.aspose.com/words/net/).
2. 開発環境: Visual Studio などの適切な .NET 開発環境。
3. C# の基礎知識: C# プログラミング言語と基本概念に精通していること。

## 名前空間のインポート

開始するには、C# プロジェクトに必要な名前空間をインポートする必要があります。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## ステップ1: プロジェクトを設定する

図形の挿入を開始する前に、プロジェクトをセットアップし、Aspose.Words for .NET ライブラリを追加する必要があります。

1. 新しいプロジェクトを作成する: Visual Studio を開き、新しい C# コンソール アプリケーション プロジェクトを作成します。
2. Aspose.Words for .NET を追加します。NuGet パッケージ マネージャーを使用して Aspose.Words for .NET ライブラリをインストールします。

```bash
Install-Package Aspose.Words
```

## ステップ2: ドキュメントを初期化する

まず、ドキュメントの構築に役立つ新しいドキュメントとドキュメント ビルダーを初期化する必要があります。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";

//新しいドキュメントを初期化する
Document doc = new Document();

//ドキュメントの構築を支援するためにDocumentBuilderを初期化する
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ステップ3: 図形を挿入する

それでは、ドキュメントに図形を挿入してみましょう。まず、単純なテキスト ボックスを追加します。

```csharp
//ドキュメントにテキストボックス図形を挿入する
Shape shape = builder.InsertShape(ShapeType.TextBox, RelativeHorizontalPosition.Page, 100, RelativeVerticalPosition.Page, 100, 50, 50, WrapType.None);

//図形を回転する
shape.Rotation = 30.0;
```

この例では、幅と高さがそれぞれ 50 単位のテキスト ボックスを位置 (100, 100) に挿入します。また、図形を 30 度回転させます。

## ステップ4: 別の図形を追加する

今回は位置を指定せずに、ドキュメントに別の図形を追加してみましょう。

```csharp
//別のテキストボックス図形を追加する
Shape secondShape = builder.InsertShape(ShapeType.TextBox, 50, 50);

//図形を回転する
secondShape.Rotation = 30.0;
```

このコード スニペットは、最初のテキスト ボックスと同じ寸法と回転で、位置を指定せずに別のテキスト ボックスを挿入します。

## ステップ5: ドキュメントを保存する

図形を追加したら、最後のステップはドキュメントを保存することです。`OoxmlSaveOptions`保存形式を指定します。

```csharp
//コンプライアンスに準拠した保存オプションを定義する
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};

//文書を保存する
doc.Save(dataDir + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## 結論

これで完了です。Aspose.Words for .NET を使用して、Word 文書に図形を挿入し、操作することができました。このチュートリアルでは基本について説明しましたが、Aspose.Words には、カスタム スタイル、コネクタ、グループ図形など、図形を操作するためのより高度な機能が多数用意されています。

詳しい情報については、[Aspose.Words for .NET ドキュメント](https://reference.aspose.com/words/net/).

## よくある質問

### さまざまな種類の図形を挿入するにはどうすればよいですか?
変更することができます`ShapeType`の`InsertShape`円、四角形、矢印など、さまざまな種類の図形を挿入する方法。

### 図形内にテキストを追加できますか?
はい、`builder.Write`図形を挿入した後、図形内にテキストを追加する方法。

### 図形にスタイルを設定することは可能ですか?
はい、次のようなプロパティを設定することで図形のスタイルを設定できます。`FillColor`, `StrokeColor` 、 そして`StrokeWeight`.

### 他の要素を基準にして図形を配置するにはどうすればよいですか?
使用`RelativeHorizontalPosition`そして`RelativeVerticalPosition`ドキュメント内の他の要素を基準に図形を配置するためのプロパティ。

### 複数の図形をグループ化できますか?
はい、Aspose.Words for .NETでは、`GroupShape`クラス。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
