---
"description": "Aspose.Words for .NET を使用して、Word 文書に角を切り取った図形を追加する方法を学びます。このステップバイステップガイドを使えば、文書を簡単に魅力的に仕上げることができます。"
"linktitle": "切り取った角を追加"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "切り取った角を追加"
"url": "/ja/net/programming-with-shapes/add-corners-snipped/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 切り取った角を追加

## 導入

Word文書にカスタム図形を追加すると、重要な情報を強調したり、コンテンツにちょっとしたアクセントを加えたりするのに、楽しく視覚的に魅力的な方法になります。このチュートリアルでは、Aspose.Words for .NETを使用して「角を切り取った」図形をWord文書に挿入する方法を詳しく説明します。このガイドでは、すべての手順を丁寧に解説するので、これらの図形を簡単に追加し、プロのように文書をカスタマイズできるようになります。

## 前提条件

コードに進む前に、開始するために必要なものがすべて揃っていることを確認しましょう。

1. Aspose.Words for .NET: 最新バージョンをまだダウンロードしていない場合は、 [Aspose リリースページ](https://releases。aspose.com/words/net/).
2. 開発環境：開発環境を構築します。Visual Studio が一般的ですが、.NET をサポートする任意の IDE を使用できます。
3. ライセンス: 実験だけなら、 [無料トライアル](https://releases.aspose.com/) または [一時ライセンス](https://purchase.aspose.com/temporary-license/) 全機能のロックを解除します。
4. C# の基本的な理解: C# プログラミングの知識があれば、例を理解するのに役立ちます。

## 名前空間のインポート

Aspose.Words for .NET を使い始める前に、必要な名前空間をインポートする必要があります。C# ファイルの先頭に以下を追加してください。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

それでは、「角切り」図形を追加するプロセスを複数のステップに分けて解説しましょう。これらの手順を注意深く実行することで、すべてがスムーズに動作するようになります。

## ステップ1: DocumentとDocumentBuilderを初期化する

まず最初に、新しいドキュメントを作成し、 `DocumentBuilder` オブジェクトです。このビルダーはドキュメントにコンテンツを追加するのに役立ちます。

```csharp
// ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

このステップでは、ドキュメントとビルダーを設定しました。 `DocumentBuilder` デジタルペンと同じように、Word 文書に書き込んだり描画したりできます。

## ステップ2：角を切り取った図形を挿入する

次に、 `DocumentBuilder` 「角切り」図形を挿入します。この図形の種類はAspose.Wordsで事前定義されており、1行のコードで簡単に挿入できます。

```csharp
builder.InsertShape(ShapeType.TopCornersSnipped, 50, 50);
```

ここでは、図形の種類と寸法（50x50）を指定しています。書類の角にぴったりと収まる小さなシールを貼るところを想像してみてください。 

## ステップ3: コンプライアンスに準拠した保存オプションを定義する

文書を保存する前に、文書が特定の規格に準拠していることを確認するための保存オプションを定義する必要があります。 `OoxmlSaveOptions` このためのクラスです。

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};
```

これらの保存オプションにより、ドキュメントは互換性とドキュメントの寿命にとって非常に重要な ISO/IEC 29500:2008 標準に準拠することが保証されます。

## ステップ4: ドキュメントを保存する

最後に、先ほど定義した保存オプションを使用して、ドキュメントを指定されたディレクトリに保存します。

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddCornersSnipped.docx", saveOptions);
```

これで、ドキュメントには、必要なコンプライアンス オプションとともに保存されたカスタムの「コーナーを切り取った」図形が含まれるようになります。

## 結論

これで完了です！Aspose.Words for .NET を使えば、Word 文書にカスタム図形を簡単に追加でき、文書の見た目を大幅に向上させることができます。これらの手順に従うことで、「角を切り取った」図形を簡単に挿入し、文書が要件を満たしていることを確認できます。コーディングを楽しみましょう！

## よくある質問

### 「コーナー切り取り」図形のサイズをカスタマイズできますか?
はい、寸法を変更することでサイズを調整できます。 `InsertShape` 方法。

### 他の種類の図形を追加することは可能ですか?
もちろんです！Aspose.Wordsは様々な図形をサポートしています。 `ShapeType` ご希望の形状に。

### Aspose.Words を使用するにはライセンスが必要ですか?
無料トライアルまたは一時ライセンスを使用することもできますが、無制限に使用するには完全なライセンスが必要です。

### 図形のスタイルをさらに変更するにはどうすればよいですか?
Aspose.Words が提供する追加のプロパティとメソッドを使用して、図形の外観と動作をカスタマイズできます。

### Aspose.Words は他の形式と互換性がありますか?
はい、Aspose.Words は DOCX、PDF、HTML など複数のドキュメント形式をサポートしています。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}