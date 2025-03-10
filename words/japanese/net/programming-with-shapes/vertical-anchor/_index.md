---
title: 垂直アンカー
linktitle: 垂直アンカー
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、Word 文書内のテキスト ボックスの垂直アンカー位置を設定する方法を学びます。簡単なステップ バイ ステップ ガイドが含まれています。
weight: 10
url: /ja/net/programming-with-shapes/vertical-anchor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 垂直アンカー

## 導入

Word 文書のテキスト ボックス内でテキストが表示される場所を正確に制御する必要に迫られたことはありませんか? テキストをテキスト ボックスの上部、中央、または下部に固定したいとお考えですか? もしそうなら、ここが最適な場所です! このチュートリアルでは、Aspose.Words for .NET を使用して Word 文書のテキスト ボックスの垂直アンカーを設定する方法について説明します。垂直アンカーは、コンテナー内の希望する場所にテキストを正確に配置する魔法の杖と考えてください。準備はできましたか? さあ、始めましょう!

## 前提条件

垂直アンカーの詳細に入る前に、いくつかの準備が必要です。

1.  Aspose.Words for .NET: Aspose.Words for .NETライブラリがインストールされていることを確認してください。まだインストールされていない場合は、[ここからダウンロード](https://releases.aspose.com/words/net/).
2. Visual Studio: このチュートリアルでは、コーディングに Visual Studio または別の .NET IDE を使用していることを前提としています。
3. C# の基礎知識: C# と .NET に精通していると、スムーズに理解できるようになります。

## 名前空間のインポート

まず、C# コードに必要な名前空間をインポートする必要があります。ここで、使用するクラスとメソッドがどこにあるかをアプリケーションに指示します。手順は次のとおりです。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

これらの名前空間は、ドキュメントや図形を操作するために必要なクラスを提供します。

## ステップ1: ドキュメントを初期化する

まず最初に、新しい Word 文書を作成する必要があります。これは、絵を描き始める前にキャンバスを設定することと考えてください。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

ここ、`Document`あなたの空白のキャンバスであり、`DocumentBuilder`はペイントブラシであり、図形やテキストを追加できます。

## ステップ2: テキストボックス図形を挿入する

さて、ドキュメントにテキストボックスを追加しましょう。ここにテキストが配置されます。 

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextBox, 200, 200);
```

この例では、`ShapeType.TextBox`希望する形状を指定し、`200, 200`テキストボックスの幅と高さをポイント単位で表したものです。

## ステップ3: 垂直アンカーを設定する

ここで魔法が起こります! テキスト ボックス内のテキストの垂直方向の配置を設定できます。これにより、テキストがテキスト ボックスの上部、中央、下部のいずれに固定されるかが決まります。

```csharp
textBox.TextBox.VerticalAnchor = TextBoxAnchor.Bottom;
```

この場合、`TextBoxAnchor.Bottom`テキストがテキストボックスの下部に固定されることを保証します。中央揃えまたは上揃えにしたい場合は、次のようにします。`TextBoxAnchor.Center`または`TextBoxAnchor.Top`、 それぞれ。

## ステップ4: テキストボックスにテキストを追加する

次に、テキストボックスにコンテンツを追加します。キャンバスに最後の仕上げとして記入すると考えてください。

```csharp
builder.MoveTo(textBox.FirstParagraph);
builder.Write("Textbox contents");
```

ここ、`MoveTo`テキストがテキストボックスに挿入されることを保証し、`Write`実際のテキストを追加します。

## ステップ5: ドキュメントを保存する

最後のステップは、ドキュメントを保存することです。これは、完成した絵画を額縁に入れるようなものです。

```csharp
doc.Save(dataDir + "WorkingWithShapes.VerticalAnchor.docx");
```

## 結論

これで完了です。Aspose.Words for .NET を使用して、Word 文書のテキスト ボックス内のテキストの垂直方向の配置を制御する方法を学習しました。テキストを上部、中央、下部のいずれに配置する場合でも、この機能により文書のレイアウトを正確に制御できます。次回、文書のテキスト配置を微調整する必要がある場合は、何をすればよいかがわかります。

## よくある質問

### Word 文書の垂直アンカーとは何ですか?
垂直アンカーは、テキスト ボックス内でテキストが配置される場所 (上、中央、下など) を制御します。

### テキストボックス以外の図形も使用できますか?
はい、他の図形でも垂直アンカーを使用できますが、最も一般的な使用例はテキスト ボックスです。

### テキストボックスを作成した後、アンカーポイントを変更するにはどうすればよいですか?
アンカーポイントを変更するには、`VerticalAnchor`テキスト ボックス シェイプ オブジェクトのプロパティ。

### テキストをテキストボックスの中央に固定することは可能ですか?
もちろんです！`TextBoxAnchor.Center`テキストボックス内でテキストを垂直方向に中央揃えにします。

### Aspose.Words for .NET の詳細情報はどこで入手できますか?
チェックしてください[Aspose.Words ドキュメント](https://reference.aspose.com/words/net/)詳細とガイドについてはこちらをご覧ください。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
