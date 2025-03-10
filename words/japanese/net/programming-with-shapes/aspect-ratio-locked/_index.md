---
title: アスペクト比が固定されています
linktitle: アスペクト比が固定されています
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、Word 文書内の図形の縦横比を固定する方法を学びます。このステップ バイ ステップ ガイドに従って、画像と図形の比率を維持します。
weight: 10
url: /ja/net/programming-with-shapes/aspect-ratio-locked/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# アスペクト比が固定されています

## 導入

Word 文書内の画像や図形の完璧な比率を維持する方法を考えたことはありませんか? 場合によっては、サイズを変更したときに画像や図形が歪まないようにする必要があります。このような場合に、アスペクト比をロックすると便利です。このチュートリアルでは、Aspose.Words for .NET を使用して Word 文書内の図形のアスペクト比を設定する方法について説明します。わかりやすい手順に分解して、これらのスキルを自信を持ってプロジェクトに適用できるようにします。

## 前提条件

コードに進む前に、始めるために必要なものを確認しましょう。

- Aspose.Words for .NETライブラリ: Aspose.Words for .NETがインストールされている必要があります。まだインストールしていない場合は、[ここからダウンロード](https://releases.aspose.com/words/net/).
- 開発環境: .NET 開発環境が設定されていることを確認します。Visual Studio が一般的な選択肢です。
- C# の基礎知識: C# プログラミングに関するある程度の知識があると役立ちます。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートしましょう。これらの名前空間により、Word 文書や図形を操作するために必要なクラスやメソッドにアクセスできるようになります。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## ステップ1: ドキュメントディレクトリを設定する

図形を操作する前に、ドキュメントを保存するディレクトリを設定する必要があります。簡単にするために、プレースホルダーを使用します。`YOUR DOCUMENT DIRECTORY`これをドキュメント ディレクトリへの実際のパスに置き換えます。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## ステップ2: 新しいドキュメントを作成する

次に、Aspose.Words を使用して新しい Word 文書を作成します。この文書は、図形や画像を追加するためのキャンバスとして機能します。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

ここでは、`Document`クラスと使用`DocumentBuilder`ドキュメントコンテンツの構築に役立てます。

## ステップ3: 画像を挿入する

さて、文書に画像を挿入してみましょう。`InsertImage`方法の`DocumentBuilder`クラス。指定したディレクトリにイメージがあることを確認してください。

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

交換する`dataDir + "Transparent background logo.png"`画像ファイルへのパスを入力します。

## ステップ4: アスペクト比をロックする

画像を挿入したら、そのアスペクト比をロックできます。アスペクト比をロックすると、サイズを変更しても画像の比率が一定に保たれます。

```csharp
shape.AspectRatioLocked = true;
```

設定`AspectRatioLocked`に`true`画像の元のアスペクト比が維持されます。

## ステップ5: ドキュメントを保存する

最後に、ドキュメントを指定されたディレクトリに保存します。この手順では、ドキュメント ファイルに加えたすべての変更が書き込まれます。

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## 結論

おめでとうございます。Aspose.Words for .NET を使用して Word 文書内の図形の縦横比を設定する方法を学習しました。これらの手順に従うことで、画像と図形の比率が維持され、文書がプロフェッショナルで洗練された外観になります。さまざまな画像と図形を試して、さまざまなシナリオで縦横比のロック機能がどのように機能するかを確認してください。

## よくある質問

### アスペクト比をロックした後でロックを解除できますか?
はい、設定することでアスペクト比をロック解除できます`shape.AspectRatioLocked = false`.

### アスペクト比を固定した画像のサイズを変更するとどうなりますか?
画像は元の幅と高さの比率を維持しながら比例してサイズ変更されます。

### これを画像以外の図形にも適用できますか?
もちろんです! アスペクト比ロック機能は、長方形、円など、あらゆる形状に適用できます。

### Aspose.Words for .NET は .NET Core と互換性がありますか?
はい、Aspose.Words for .NET は .NET Framework と .NET Core の両方をサポートしています。

### Aspose.Words for .NET に関する詳細なドキュメントはどこで入手できますか?
包括的なドキュメントが見つかります[ここ](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
