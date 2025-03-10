---
title: フォントフォルダを設定する
linktitle: フォントフォルダを設定する
second_title: Aspose.Words ドキュメント処理 API
description: この包括的なステップバイステップ ガイドでは、Aspose.Words for .NET でカスタム フォント フォルダーを設定する方法を学習します。ドキュメント フォントを強化したい開発者に最適です。
weight: 10
url: /ja/net/working-with-fonts/set-fonts-folders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# フォントフォルダを設定する

## 導入

こんにちは! Aspose.Words for .NET のカスタム フォントの世界に飛び込む準備はできましたか? さあ、始めましょう。このチュートリアルでは、カスタム フォント フォルダーを設定する手順を案内し、ドキュメントが希望どおりに表示されるようにします。熟練した開発者でも、初心者でも、このガイドではすべての手順を案内します。それでは、フォントをすばらしいものにしましょう!

## 前提条件

始める前に、必要なものがすべて揃っていることを確認しましょう。

-  Aspose.Words for .NET: 次のようなことができます[ダウンロード](https://releases.aspose.com/words/net/)まだ読んでいない場合は読んでみてください。
- Visual Studio: どのバージョンでも動作しますが、常に最新のバージョンが最適です。
- ドキュメント: このチュートリアルでは Word ドキュメントを使用します。独自のドキュメントを作成することも、既存のドキュメントを使用することもできます。
- カスタム フォント: カスタム フォントをいくつか用意します。これらを使用して、フォント フォルダーを設定する方法を説明します。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートしましょう。これは、Aspose.Words から必要なクラスとメソッドにアクセスするために不可欠です。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

これらの名前空間をインポートしたら、カスタム フォント フォルダーの設定を開始する準備が整いました。

## ステップ1: ドキュメントディレクトリを定義する

まず、ドキュメントディレクトリへのパスを定義します。これはWord文書が保存される場所です。`dataDir`このパスを保存します。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

交換する`"YOUR DOCUMENT DIRECTORY"`ディレクトリへの実際のパスを入力します。Aspose.Words はドキュメントがどこにあるかを知る必要があるため、これは非常に重要です。

## ステップ2: フォントソースを設定する

次に、フォントソースを設定する必要があります。ここで、Aspose.Wordsにカスタムフォントの場所を指定します。`FontSettings.DefaultInstance.SetFontsSources`これを実現する方法。

```csharp
FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
	new SystemFontSource(), new FolderFontSource("C:\\MyFonts\\", true)
});
```

私たちがやっていることは次のとおりです:

- SystemFontSource: これは、Aspose.Words にシステムの既定のフォントを使用するように指示します。
-  FolderFontSource: ここでカスタムフォントを含むフォルダを指定します。`"C:\\MyFonts\\"`カスタムフォントディレクトリへのパスを入力します。`true`パラメータはサブディレクトリも含める必要があることを示します。

## ステップ3: ドキュメントを読み込む

フォントソースの設定が終わったので、作業したいドキュメントをロードします。`Document` Aspose.Words のクラスです。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

確実に`"Rendering.docx"`は Word 文書の名前です。文書の名前が異なる場合は、それに応じて更新してください。

## ステップ4: ドキュメントをPDFとして保存する

最後に、カスタムフォントの動作を確認するために、ドキュメントをPDFとして保存します。`Save`方法の`Document`クラス。

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFolders.pdf");
```

これにより、前に設定したカスタム フォントを使用して、ドキュメントが指定されたディレクトリに PDF として保存されます。

## 結論

これで完了です。Aspose.Words for .NET でカスタム フォント フォルダーを正常に設定し、そのカスタム フォントを使用してドキュメントを PDF として保存しました。すばらしいと思いませんか? フォントをカスタマイズすると、ドキュメントの外観が大きく変わります。これで、フォントのカスタマイズ方法を正確に理解できました。コーディングを楽しんでください。

## よくある質問

### Aspose.Words for .NET をインストールするにはどうすればよいですか?

あなたはできる[ダウンロード](https://releases.aspose.com/words/net/) Aspose.Words for .NET の最新バージョンを Web サイトから入手します。

### 複数のカスタムフォントフォルダーを使用できますか?

はい、複数追加できます`FolderFontSource`インスタンスに`SetFontsSources`異なるディレクトリのフォントを使用する方法。

### システムフォントを含める必要がありますか?

システム フォントを含めることはオプションですが、すべての標準フォントが使用可能であることを確認するために推奨されます。

### Aspose.Words ではどのようなファイル形式がサポートされていますか?

Aspose.Words は、DOCX、DOC、PDF、TXT、HTML など、幅広いファイル形式をサポートしています。

### Aspose.Words の一時ライセンスを取得するにはどうすればよいですか?

あなたは[一時ライセンス](https://purchase.aspose.com/temporary-license/)Aspose.Words の全機能を試すには、Aspose Web サイトからアクセスしてください。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
