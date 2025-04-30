---
"description": "Aspose.Words for .NET を使用して、Word 文書に特定のオプションでテキスト透かしを追加する方法を学びます。フォント、サイズ、色、レイアウトを簡単にカスタマイズできます。"
"linktitle": "特定のオプションでテキスト透かしを追加する"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "特定のオプションでテキスト透かしを追加する"
"url": "/ja/net/programming-with-watermark/add-text-watermark-with-specific-options/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 特定のオプションでテキスト透かしを追加する

## 導入

透かしは、Word文書にスタイリッシュかつ機能的な機能を追加できます。機密文書としてマークしたり、個性的なタッチを加えたりと、様々な用途に活用できます。このチュートリアルでは、Aspose.Words for .NET を使用してWord文書にテキスト透かしを追加する方法を説明します。フォントファミリー、フォントサイズ、色、レイアウトなど、設定可能なオプションについて詳しく説明します。チュートリアルを最後まで読めば、文書の透かしをニーズに合わせてカスタマイズできるようになります。さあ、コードエディターを手に取って、早速始めましょう！

## 前提条件

始める前に、次のものを用意しておいてください。

1. Aspose.Words for .NET ライブラリ: Aspose.Words ライブラリがインストールされている必要があります。まだインストールされていない場合は、以下のリンクからダウンロードできます。 [Aspose.Words ダウンロードリンク](https://releases。aspose.com/words/net/).
2. C#の基礎知識：このチュートリアルでは、プログラミング言語としてC#を使用します。C#の構文を基礎的に理解しておくと役立ちます。
3. .NET 開発環境: .NET アプリケーションを作成して実行できる開発環境 (Visual Studio など) が設定されていることを確認します。

## 名前空間のインポート

Aspose.Words を使用するには、プロジェクトに必要な名前空間を含める必要があります。インポートする必要があるものは以下のとおりです。

```csharp
using Aspose.Words;
using Aspose.Words.Rendering;
using System.Drawing;
```

## ステップ1：ドキュメントを設定する

まず、作業したいドキュメントを読み込む必要があります。このチュートリアルでは、サンプルドキュメント「 `Document.docx`このドキュメントが指定したディレクトリに存在することを確認してください。

```csharp
// ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

このステップでは、ドキュメントが配置されているディレクトリを定義し、それを `Document` クラス。

## ステップ2: 透かしオプションを設定する

次に、テキスト透かしのオプションを設定します。フォントファミリー、フォントサイズ、色、レイアウトなど、さまざまな要素をカスタマイズできます。これらのオプションを設定しましょう。

```csharp
TextWatermarkOptions options = new TextWatermarkOptions()
{
    FontFamily = "Arial",
    FontSize = 36,
    Color = Color.Black,
    Layout = WatermarkLayout.Horizontal,
    IsSemitrasparent = false
};
```

各オプションの機能は次のとおりです。
- `FontFamily`: 透かしテキストのフォントを指定します。
- `FontSize`透かしテキストのサイズを設定します。
- `Color`: 透かしテキストの色を定義します。
- `Layout`: 透かしの方向 (水平または斜め) を決定します。
- `IsSemitrasparent`: 透かしを半透明にするかどうかを設定します。

## ステップ3：透かしテキストを追加する

先ほど設定したオプションを使用して、ドキュメントに透かしを適用します。このステップでは、透かしのテキストを「Test」に設定し、定義したオプションを適用します。

```csharp
doc.Watermark.SetText("Test", options);
```

このコード行は、指定されたオプションを適用して、ドキュメントに「Test」というテキストの透かしを追加します。

## ステップ4: ドキュメントを保存する

最後に、新しい透かしを適用したドキュメントを保存します。元のドキュメントを上書きしないように、新しい名前を付けて保存することもできます。

```csharp
doc.Save(dataDir + "WorkWithWatermark.AddTextWatermarkWithSpecificOptions.docx");
```

このコード スニペットは、変更されたドキュメントを新しいファイル名で同じディレクトリに保存します。

## 結論

Aspose.Words for .NET を使用して Word 文書にテキスト透かしを追加するのは、管理しやすい手順に分解すれば簡単です。このチュートリアルでは、フォント、サイズ、色、レイアウト、透明度など、透かしのさまざまなオプションを設定する方法を学習しました。これらのスキルを習得すれば、ニーズに合わせて文書をカスタマイズしたり、機密情報やブランド情報などの重要な情報を追加したりできるようになります。

ご質問やさらなるサポートが必要な場合は、お気軽に [Aspose.Words ドキュメント](https://reference.aspose.com/words/net/) または、 [Aspose サポートフォーラム](https://forum.aspose.com/c/words/8) さらに詳しいヘルプについては、こちらをご覧ください。

## よくある質問

### 透かしに異なるフォントを使用できますか?

はい、システムにインストールされているフォントを任意に選択できます。 `FontFamily` の財産 `TextWatermarkOptions`。

### 透かしの色を変更するにはどうすればよいですか?

透かしの色は、 `Color` の財産 `TextWatermarkOptions` いずれにせよ `System.Drawing.Color` 価値。

### 文書に複数の透かしを追加することは可能ですか?

Aspose.Words では、一度に 1 つの透かしを追加できます。複数の透かしを追加するには、透かしを順番に作成して適用する必要があります。

### 透かしの位置を調整できますか？

その `WatermarkLayout` プロパティは向きを決定しますが、正確な位置調整は直接サポートされていません。正確な配置には他の手法を使用する必要がある場合があります。

### 半透明の透かしが必要な場合はどうすればいいでしょうか?

設定する `IsSemitrasparent` 財産に `true` 透かしを半透明にします。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}