---
title: 文書のテキスト方向
linktitle: 文書のテキスト方向
second_title: Aspose.Words ドキュメント処理 API
description: このステップバイステップ ガイドでは、Aspose.Words for .NET を使用して Word でドキュメントのテキスト方向を設定する方法を説明します。右から左に記述する言語の処理に最適です。
weight: 10
url: /ja/net/programming-with-txtloadoptions/document-text-direction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 文書のテキスト方向

## 導入

Word 文書、特に複数の言語や特殊な書式設定が必要な文書を扱う場合、テキストの方向を設定することは非常に重要です。たとえば、ヘブライ語やアラビア語などの右から左に記述する言語を扱う場合、それに応じてテキストの方向を調整する必要があります。このガイドでは、Aspose.Words for .NET を使用して文書のテキストの方向を設定する方法について説明します。 

## 前提条件

コードに進む前に、次のものを用意してください。

-  Aspose.Words for .NET ライブラリ: Aspose.Words for .NET がインストールされていることを確認してください。[Aspose ウェブサイト](https://releases.aspose.com/words/net/).
- Visual Studio: C# コードを記述および実行するための開発環境。
- C# の基礎知識: コードを書くことになるので、C# プログラミングの知識があると役立ちます。

## 名前空間のインポート

まず、プロジェクトで Aspose.Words を操作するために必要な名前空間をインポートする必要があります。手順は次のとおりです。

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
```

これらの名前空間は、Word 文書を操作するために必要なクラスとメソッドへのアクセスを提供します。

## ステップ1: ドキュメントディレクトリへのパスを定義する

まず、ドキュメントが保存されている場所へのパスを設定します。これは、ファイルを正しく読み込み、保存するために重要です。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

交換する`"YOUR DOCUMENT DIRECTORY"`ドキュメントが保存されている実際のパスを入力します。

## ステップ 2: ドキュメント方向設定を含む TxtLoadOptions を作成する

次に、インスタンスを作成する必要があります`TxtLoadOptions`そしてその`DocumentDirection`プロパティ。これは、ドキュメント内のテキストの方向をどのように処理するかを Aspose.Words に指示します。

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DocumentDirection = DocumentDirection.Auto };
```

この例では、`DocumentDirection.Auto` Aspose.Words がコンテンツに基づいて方向を自動的に決定できるようにします。

## ステップ3: ドキュメントを読み込む

次に、`Document`クラスと以前に定義された`loadOptions`.

```csharp
Document doc = new Document(dataDir + "Hebrew text.txt", loadOptions);
```

ここ、`"Hebrew text.txt"`はテキスト ファイルの名前です。このファイルが指定したディレクトリに存在することを確認してください。

## ステップ4: 段落の双方向書式にアクセスして確認する

テキストの方向が正しく設定されていることを確認するには、ドキュメントの最初の段落にアクセスし、双方向の書式設定を確認します。

```csharp
Paragraph paragraph = doc.FirstSection.Body.FirstParagraph;
Console.WriteLine(paragraph.ParagraphFormat.Bidi);
```

この手順は、ドキュメントのテキスト方向が期待どおりに適用されているかどうかをデバッグおよび検証するのに役立ちます。

## ステップ5: 新しい設定でドキュメントを保存する

最後に、ドキュメントを保存して変更を適用し、保持します。

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
```

ここ、`"WorkingWithTxtLoadOptions.DocumentTextDirection.docx"`出力ファイルの名前です。変更を反映した名前を選択してください。

## 結論

Word 文書のテキスト方向の設定は、Aspose.Words for .NET を使用すると簡単に行えます。次の手順に従うと、文書で右から左または左から右のテキストを処理する方法を簡単に構成できます。多言語文書を扱っている場合でも、特定の言語のテキスト方向をフォーマットする必要がある場合でも、Aspose.Words はニーズを満たす強力なソリューションを提供します。

## よくある質問

### 何ですか`DocumentDirection` property used for?

の`DocumentDirection`不動産の`TxtLoadOptions`文書のテキスト方向を決定します。設定できるのは`DocumentDirection.Auto`, `DocumentDirection.LeftToRight`、 または`DocumentDirection.RightToLeft`.

### 文書全体ではなく、特定の段落のテキスト方向を設定できますか?

はい、特定の段落のテキストの方向を設定するには、`ParagraphFormat.Bidi`財産ですが、`TxtLoadOptions.DocumentDirection`プロパティは、ドキュメント全体のデフォルトの方向を設定します。

### 読み込みにサポートされているファイル形式は`TxtLoadOptions`?

`TxtLoadOptions`主にテキストファイル（.txt）を読み込むために使用されます。他のファイル形式の場合は、次のような異なるクラスを使用します。`DocLoadOptions`または`DocxLoadOptions`.

### テキスト方向が混在するドキュメントをどのように処理すればよいでしょうか?

複数のテキスト方向が混在する文書では、段落ごとに書式設定を行う必要がある場合があります。`ParagraphFormat.Bidi`必要に応じて各段落の方向を調整するプロパティ。

### Aspose.Words for .NET の詳細情報はどこで入手できますか?

詳細については、[Aspose.Words for .NET ドキュメント](https://reference.aspose.com/words/net/)次のような追加リソースもご覧ください[ダウンロードリンク](https://releases.aspose.com/words/net/), [買う](https://purchase.aspose.com/buy), [無料トライアル](https://releases.aspose.com/), [一時ライセンス](https://purchase.aspose.com/temporary-license/) 、 そして[サポート](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
