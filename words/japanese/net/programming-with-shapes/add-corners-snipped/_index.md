---
title: 切り取ったコーナーを追加
linktitle: 切り取ったコーナーを追加
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、Word 文書に角を切り取った図形を追加する方法を学びます。このステップ バイ ステップ ガイドにより、文書を簡単に強化できます。
weight: 10
url: /ja/net/programming-with-shapes/add-corners-snipped/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 切り取ったコーナーを追加

## 導入

Word 文書にカスタム図形を追加すると、重要な情報を強調したり、コンテンツにちょっとしたセンスを加えたりするのに、楽しくて視覚的に魅力的な方法になります。このチュートリアルでは、Aspose.Words for .NET を使用して、Word 文書に「コーナーを切り取った」図形を挿入する方法について詳しく説明します。このガイドでは、すべての手順を順を追って説明し、これらの図形を簡単に追加して、プロのように文書をカスタマイズできるようにします。

## 前提条件

コードに進む前に、開始するために必要なものがすべて揃っていることを確認しましょう。

1.  Aspose.Words for .NET: まだダウンロードしていない場合は、[Aspose リリース ページ](https://releases.aspose.com/words/net/).
2. 開発環境: 開発環境を設定します。Visual Studio が一般的な選択肢ですが、.NET をサポートする任意の IDE を使用できます。
3. ライセンス: 実験だけなら、[無料トライアル](https://releases.aspose.com/)または[一時ライセンス](https://purchase.aspose.com/temporary-license/)全機能のロックを解除します。
4. C# の基本的な理解: C# プログラミングの知識があれば、例を理解するのに役立ちます。

## 名前空間のインポート

Aspose.Words for .NET の使用を開始する前に、必要な名前空間をインポートする必要があります。これらを C# ファイルの先頭に追加します。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

ここで、「コーナーを切り取った」図形を追加するプロセスを複数のステップに分解してみましょう。すべてがスムーズに機能するように、これらの手順に厳密に従ってください。

## ステップ 1: ドキュメントと DocumentBuilder を初期化する

まず最初に、新しいドキュメントを作成し、`DocumentBuilder`オブジェクト。このビルダーはドキュメントにコンテンツを追加するのに役立ちます。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

このステップでは、ドキュメントとビルダーを設定しました。`DocumentBuilder`デジタルペンと同じように、Word 文書に書き込んだり描画したりできます。

## ステップ2: 角を切り取った図形を挿入する

次に、`DocumentBuilder`「コーナーを切り取った」図形を挿入します。この図形の種類は Aspose.Words で事前定義されており、1 行のコードで簡単に挿入できます。

```csharp
builder.InsertShape(ShapeType.TopCornersSnipped, 50, 50);
```

ここでは、図形の種類とその寸法 (50x50) を指定しています。ドキュメントに、小さくて完全に切り取られたコーナー ステッカーを貼り付けていると想像してください。 

## ステップ3: コンプライアンスに従って保存オプションを定義する

文書を保存する前に、文書が特定の標準に準拠していることを確認するために保存オプションを定義する必要があります。`OoxmlSaveOptions`このためのクラスです。

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};
```

これらの保存オプションにより、ドキュメントが ISO/IEC 29500:2008 標準に準拠することが保証され、互換性とドキュメントの寿命にとって非常に重要です。

## ステップ4: ドキュメントを保存する

最後に、先ほど定義した保存オプションを使用して、ドキュメントを指定されたディレクトリに保存します。

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddCornersSnipped.docx", saveOptions);
```

これで、ドキュメントには、必要なコンプライアンス オプションとともに保存されたカスタムの「コーナーを切り取った」図形が含まれるようになりました。

## 結論

これで完了です。Aspose.Words for .NET を使用して Word 文書にカスタム図形を追加するのは簡単で、文書の見た目を大幅に向上させることができます。これらの手順に従うことで、「コーナーを切り取った」図形を簡単に挿入し、文書が必要な標準を満たすようにすることができます。コーディングを楽しんでください。

## よくある質問

### 「コーナーを切り取る」図形のサイズをカスタマイズできますか?
はい、寸法を変更することでサイズを調整できます。`InsertShape`方法。

### 他の種類の図形を追加することは可能ですか?
もちろんです！Aspose.Wordsはさまざまな図形をサポートしています。`ShapeType`ご希望の形状に。

### Aspose.Words を使用するにはライセンスが必要ですか?
無料トライアルまたは一時ライセンスを使用することもできますが、無制限に使用するにはフルライセンスが必要です。

### 図形のスタイルをさらに変更するにはどうすればよいですか?
Aspose.Words が提供する追加のプロパティとメソッドを使用して、図形の外観と動作をカスタマイズできます。

### Aspose.Words は他の形式と互換性がありますか?
はい、Aspose.Words は DOCX、PDF、HTML など複数のドキュメント形式をサポートしています。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
