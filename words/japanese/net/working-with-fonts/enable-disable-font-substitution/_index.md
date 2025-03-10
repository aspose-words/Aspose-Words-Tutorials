---
title: フォント置換を有効/無効にする
linktitle: フォント置換を有効/無効にする
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、Word 文書でフォントの置換を有効または無効にする方法を学びます。すべてのプラットフォームで文書の外観が一貫していることを確認します。
weight: 10
url: /ja/net/working-with-fonts/enable-disable-font-substitution/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# フォント置換を有効/無効にする

## 導入

Word 文書で慎重に選択したフォントが、別のコンピューターで表示したときに置き換えられてしまう状況に遭遇したことはありませんか? イライラしますよね? これは、不足しているフォントを使用可能なフォントに置き換えるプロセスであるフォント置換によって発生します。しかし、心配はいりません! Aspose.Words for .NET を使用すると、フォント置換を簡単に管理および制御できます。このチュートリアルでは、Word 文書でフォント置換を有効または無効にする手順を順を追って説明し、文書が常に希望どおりに表示されるようにします。

## 前提条件

手順に進む前に、必要なものがすべて揃っていることを確認しましょう。

-  Aspose.Words for .NET: 最新バージョンをダウンロード[ここ](https://releases.aspose.com/words/net/).
- Visual Studio: .NET をサポートする任意のバージョン。
- C# の基礎知識: コーディング例を理解するのに役立ちます。

## 名前空間のインポート

まず、プロジェクトに必要な名前空間がインポートされていることを確認します。これらを C# ファイルの先頭に追加します。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

それでは、プロセスをシンプルで管理しやすいステップに分解してみましょう。

## ステップ1: プロジェクトを設定する

まず、Visual Studioで新しいプロジェクトを設定し、Aspose.Words for .NETライブラリへの参照を追加します。まだダウンロードしていない場合は、[Aspose ウェブサイト](https://releases.aspose.com/words/net/).

## ステップ2: ドキュメントを読み込む

次に、作業するドキュメントを読み込みます。手順は次のとおりです。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

交換する`"YOUR DOCUMENT DIRECTORY"`ドキュメント ディレクトリへの実際のパスを入力します。このコードはドキュメントをメモリにロードし、操作できるようにします。

## ステップ3: フォント設定を構成する

さて、`FontSettings`フォント置換設定を管理するオブジェクト:

```csharp
FontSettings fontSettings = new FontSettings();
```

## ステップ4: デフォルトのフォントの置換を設定する

デフォルトのフォント置換を任意のフォントに設定します。元のフォントが利用できない場合は、このフォントが使用されます。

```csharp
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

この例では、デフォルトのフォントとして Arial を使用しています。

## ステップ5: フォント情報の置換を無効にする

フォント情報の置換を無効にして、システムが不足しているフォントを使用可能なフォントに置き換えるのを停止するには、次のコードを使用します。

```csharp
fontSettings.SubstitutionSettings.FontInfoSubstitution.Enabled = false;
```

## ステップ6: ドキュメントにフォント設定を適用する

次に、これらの設定をドキュメントに適用します。

```csharp
doc.FontSettings = fontSettings;
```

## ステップ7: ドキュメントを保存する

最後に、変更したドキュメントを保存します。任意の形式で保存できます。このチュートリアルでは、PDF として保存します。

```csharp
doc.Save(dataDir + "WorkingWithFonts.EnableDisableFontSubstitution.pdf");
```

## 結論

これで完了です。これらの手順に従うと、Aspose.Words for .NET を使用して Word 文書のフォント置換を簡単に制御できます。これにより、どこで表示しても、文書の意図した外観と操作性が維持されます。

## よくある質問

### 代替として Arial 以外のフォントを使用できますか?

もちろんです！フォント名を変更することで、システムで利用可能なフォントを指定できます。`DefaultFontName`財産。

### 指定されたデフォルトのフォントが利用できない場合はどうなりますか?

既定のフォントが使用できない場合、Aspose.Words はシステム フォールバック メカニズムを使用して適切な代替フォントを検索します。

### フォントの置換を無効にした後、再度有効にすることはできますか?

はい、切り替えることができます`Enabled`の所有物`FontInfoSubstitution`戻る`true`フォントの置換を再度有効にしたい場合。

### どのフォントが置き換えられているかを確認する方法はありますか?

はい、Aspose.Words にはフォントの置換をログに記録して追跡するメソッドが用意されており、どのフォントが置換されているかを確認できます。

### この方法は DOCX 以外のドキュメント形式にも使用できますか?

もちろんです! Aspose.Words はさまざまな形式をサポートしており、サポートされている任意の形式にこれらのフォント設定を適用できます。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
