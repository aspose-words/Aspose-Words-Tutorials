---
"description": "Aspose.Words for .NET を使用して、Word 文書内の図形のアスペクト比を固定する方法を学びます。このステップバイステップガイドに従って、画像と図形のアスペクト比を維持してください。"
"linktitle": "アスペクト比を固定"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "アスペクト比を固定"
"url": "/ja/net/programming-with-shapes/aspect-ratio-locked/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# アスペクト比を固定

## 導入

Word文書内の画像や図形の縦横比を完璧に維持したいと思ったことはありませんか？サイズを変更しても画像や図形が歪んでしまわないようにしたい時があります。そんな時に役立つのが、アスペクト比を固定する機能です。このチュートリアルでは、Aspose.Words for .NETを使ってWord文書内の図形のアスペクト比を設定する方法を学びます。分かりやすい手順に分解して解説するので、自信を持ってプロジェクトに応用できます。

## 前提条件

コードに進む前に、開始するために必要なものを確認しましょう。

- Aspose.Words for .NETライブラリ: Aspose.Words for .NETがインストールされている必要があります。まだインストールされていない場合は、 [ここからダウンロード](https://releases。aspose.com/words/net/).
- 開発環境：.NET開発環境がセットアップされていることを確認してください。Visual Studioが一般的な選択肢です。
- C# の基本知識: C# プログラミングに関するある程度の知識があると役立ちます。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートしましょう。これらの名前空間により、Word文書や図形を操作するために必要なクラスやメソッドにアクセスできるようになります。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## ステップ1: ドキュメントディレクトリを設定する

図形の操作を始める前に、ドキュメントを保存するディレクトリを設定する必要があります。ここでは、簡略化のためプレースホルダーを使用します。 `YOUR DOCUMENT DIRECTORY`これをドキュメント ディレクトリへの実際のパスに置き換えます。

```csharp
// ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## ステップ2: 新しいドキュメントを作成する

次に、Aspose.Wordsを使って新しいWord文書を作成します。この文書は、図形や画像を追加するためのキャンバスとして機能します。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

ここでは、 `Document` クラスと使用 `DocumentBuilder` ドキュメントコンテンツの構築に役立てます。

## ステップ3: 画像を挿入する

さて、文書に画像を挿入してみましょう。 `InsertImage` の方法 `DocumentBuilder` クラス。指定したディレクトリにイメージがあることを確認してください。

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

交換する `dataDir + "Transparent background logo.png"` 画像ファイルへのパスを入力します。

## ステップ4：アスペクト比を固定する

画像を挿入したら、アスペクト比をロックできます。アスペクト比をロックすることで、画像のサイズを変更しても画像の比率が一定に保たれます。

```csharp
shape.AspectRatioLocked = true;
```

設定 `AspectRatioLocked` に `true` 画像の元のアスペクト比が維持されます。

## ステップ5: ドキュメントを保存する

最後に、ドキュメントを指定のディレクトリに保存します。このステップで、ドキュメントファイルに加えたすべての変更が書き込まれます。

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## 結論

おめでとうございます！Aspose.Words for .NET を使用して、Word 文書内の図形のアスペクト比を設定する方法を習得しました。これらの手順に従うことで、画像や図形の縦横比が維持され、文書がプロフェッショナルで洗練された外観になります。様々な画像や図形を試して、アスペクト比の固定機能が様々なシナリオでどのように機能するかを確認してください。

## よくある質問

### アスペクト比をロックした後でロックを解除できますか?
はい、設定することでアスペクト比をロック解除できます `shape。AspectRatioLocked = false`.

### アスペクト比を固定した画像のサイズを変更するとどうなりますか?
画像は元の幅と高さの比率を維持しながら比例してサイズ変更されます。

### これを画像以外の図形にも適用できますか？
もちろんです！アスペクト比ロック機能は、長方形や円など、あらゆる図形に適用できます。

### Aspose.Words for .NET は .NET Core と互換性がありますか?
はい、Aspose.Words for .NET は .NET Framework と .NET Core の両方をサポートしています。

### Aspose.Words for .NET に関する詳細なドキュメントはどこで入手できますか?
包括的なドキュメントが見つかります [ここ](https://reference。aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}