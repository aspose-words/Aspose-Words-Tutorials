---
"description": "Aspose.Words for .NET で画像の箇条書きを処理する方法をステップバイステップガイドで学びましょう。ドキュメント管理を簡素化し、プロフェッショナルな Word 文書を簡単に作成できます。"
"linktitle": "画像を保存しない"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "画像を保存しない"
"url": "/ja/net/programming-with-docsaveoptions/do-not-save-picture-bullet/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 画像を保存しない

## 導入

開発者の皆さん、こんにちは！Word文書で作業していて、箇条書き画像の保存に戸惑ったことはありませんか？これは、文書の最終的な見た目を大きく左右する、ちょっとしたコツの一つです。そこで今回は、Aspose.Words for .NETで箇条書き画像を処理する手順を解説します。特に「箇条書き画像を保存しない」機能に焦点を当てています。さあ、始めましょう！

## 前提条件

コードの修正を始める前に、準備しておくべきことがいくつかあります。

1. Aspose.Words for .NET: この強力なライブラリがインストールされていることを確認してください。まだインストールされていない場合は、ダウンロードできます。 [ここ](https://releases。aspose.com/words/net/).
2. 開発環境: Visual Studio などの動作する .NET 開発環境。
3. C# の基本知識: C# プログラミングに関するある程度の知識があると役立ちます。
4. サンプル ドキュメント: テスト用の画像の箇条書きを含む Word ドキュメント。

## 名前空間のインポート

まず、必要な名前空間をインポートする必要があります。これは非常に簡単ですが、Aspose.Wordsの機能にアクセスするために不可欠です。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

プロセスを分かりやすいステップに分解してみましょう。こうすることで、コードの各部分を簡単に理解できるようになります。

## ステップ1: ドキュメントディレクトリを設定する

まず最初に、ドキュメントディレクトリへのパスを指定する必要があります。これはWord文書が保存される場所であり、変更されたファイルも保存される場所です。

```csharp
// ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

交換する `"YOUR DOCUMENTS DIRECTORY"` ドキュメントが保存されているシステム上の実際のパスを入力します。

## ステップ2: イメージ箇条書きを含むドキュメントを読み込む

次に、画像の箇条書きを含むWord文書を読み込みます。この文書は、保存時に画像の箇条書きを削除するように修正されます。

```csharp
// 画像の箇条書きを含むドキュメントを読み込む
Document doc = new Document(dataDir + "Image bullet points.docx");
```

ファイルが `"Image bullet points.docx"` 指定されたディレクトリに存在します。

## ステップ3: 保存オプションを設定する

さて、保存オプションを設定して、画像の箇条書きを保存しないように指定しましょう。ここで魔法が起こります！

```csharp
// 「画像の箇条書きを保存しない」機能を使用して保存オプションを設定します
DocSaveOptions saveOptions = new DocSaveOptions { SavePictureBullet = false };
```

設定により `SavePictureBullet` に `false`出力ドキュメントに画像の箇条書きを保存しないように Aspose.Words に指示します。

## ステップ4: ドキュメントを保存する

最後に、指定したオプションでドキュメントを保存します。これにより、画像の箇条書きが含まれない新しいファイルが生成されます。

```csharp
// 指定されたオプションでドキュメントを保存します
doc.Save(dataDir + "WorkingWithDocSaveOptions.DoNotSavePictureBullet.docx", saveOptions);
```

新しいファイル、 `"WorkingWithDocSaveOptions.DoNotSavePictureBullet.docx"`はドキュメントディレクトリに保存されます。

## 結論

これで完了です！わずか数行のコードで、Aspose.Words for .NET を設定して、ドキュメントの保存時に画像の箇条書きを省略できるようになりました。これは、画像の箇条書きに邪魔されずに、すっきりとした統一感のある外観を実現したい場合に非常に便利です。

## よくある質問

### Aspose.Words for .NET とは何ですか?
Aspose.Words for .NET は、.NET アプリケーション内で Word 文書を作成、編集、変換するための強力なライブラリです。

### この機能を他の種類の弾丸にも使用できますか?
いいえ、この機能は画像の箇条書き用です。ただし、Aspose.Words には他の種類の箇条書きを処理するための幅広いオプションが用意されています。

### Aspose.Words のサポートはどこで受けられますか?
サポートを受けるには [Aspose.Words フォーラム](https://forum。aspose.com/c/words/8).

### Aspose.Words for .NET の無料試用版はありますか?
はい、無料トライアルをご利用いただけます [ここ](https://releases。aspose.com/).

### Aspose.Words for .NET のライセンスを購入するにはどうすればよいですか?
ライセンスは以下から購入できます。 [Aspose ストア](https://purchase。aspose.com/buy).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}