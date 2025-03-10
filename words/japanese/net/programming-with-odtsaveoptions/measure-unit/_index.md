---
title: 測定単位
linktitle: 測定単位
second_title: Aspose.Words ドキュメント処理 API
description: ODT 変換中にドキュメントの書式設定を保持するために、Aspose.Words for .NET の測定単位機能を構成する方法を学習します。
weight: 10
url: /ja/net/programming-with-odtsaveoptions/measure-unit/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 測定単位

## 導入

Word 文書を別の形式に変換しなければならなかったのに、レイアウトに特定の測定単位が必要になったことはありませんか? インチ、センチメートル、ポイントのいずれを扱う場合でも、変換プロセス中に文書の整合性が維持されるようにすることが重要です。このチュートリアルでは、Aspose.Words for .NET で測定単位機能を構成する方法について説明します。この強力な機能により、ODT (Open Document Text) 形式に変換するときに、文書の書式設定が正確に保持されます。

## 前提条件

コードに進む前に、始めるために必要なことがいくつかあります。

1. Aspose.Words for .NET: 最新バージョンのAspose.Words for .NETがインストールされていることを確認してください。まだインストールしていない場合は、こちらからダウンロードできます。[ここ](https://releases.aspose.com/words/net/).
2. 開発環境: C# コードを記述して実行するための Visual Studio などの IDE。
3. C# の基礎知識: C# の基礎を理解しておくと、チュートリアルを理解しやすくなります。
4. Word 文書: 変換に使用できるサンプルの Word 文書を用意しておきます。

## 名前空間のインポート

コーディングを始める前に、必要な名前空間がインポートされていることを確認しましょう。コード ファイルの先頭に次の using ディレクティブを追加します。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## ステップ1: ドキュメントディレクトリを設定する

まず、ドキュメント ディレクトリへのパスを定義する必要があります。これは、Word ドキュメントが保存される場所であり、変換されたファイルが保存される場所です。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

交換する`"YOUR DOCUMENTS DIRECTORY"`ディレクトリへの実際のパスを使用します。これにより、コードが Word 文書の場所を認識できるようになります。

## ステップ2: Word文書を読み込む

次に、変換したいWord文書を読み込む必要があります。これは、`Document` Aspose.Words のクラス。

```csharp
// Word文書を読み込む
Document doc = new Document(dataDir + "Document.docx");
```

「Document.docx」という名前の Word 文書が指定されたディレクトリに存在することを確認します。

## ステップ3: 測定単位を設定する

さて、ODT変換の測定単位を設定しましょう。ここで魔法が起こります。`OdtSaveOptions`測定単位としてインチを使用する。

```csharp
// 「測定単位」機能を使用したバックアップ オプションの構成
OdtSaveOptions saveOptions = new OdtSaveOptions { MeasureUnit = OdtSaveMeasureUnit.Inches };
```

この例では、測定単位をインチに設定しています。他の単位を選択することもできます。`OdtSaveMeasureUnit.Centimeters`または`OdtSaveMeasureUnit.Points`ご要望に応じて。

## ステップ4: ドキュメントをODTに変換する

最後に、Word文書をODT形式に変換します。`OdtSaveOptions`.

```csharp
//ドキュメントをODTに変換する
doc.Save(dataDir + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

このコード行は、新しい測定単位を適用した変換されたドキュメントを指定されたディレクトリに保存します。

## 結論

これで完了です。これらの手順に従うことで、Aspose.Words for .NET の測定単位機能を簡単に構成し、変換中にドキュメントのレイアウトが保持されるようにすることができます。インチ、センチメートル、ポイントのいずれで作業する場合でも、このチュートリアルでは、ドキュメントの書式設定を簡単に制御する方法を説明しました。

## よくある質問

### Aspose.Words for .NET とは何ですか?
Aspose.Words for .NET は、Word 文書をプログラムで操作するための強力なライブラリです。開発者は、Microsoft Word を必要とせずに、Word 文書を作成、変更、変換、および処理できます。

### インチ以外の測定単位も使用できますか?
はい、Aspose.Words for .NETはセンチメートルやポイントなどの他の測定単位もサポートしています。`OdtSaveMeasureUnit`列挙。

### Aspose.Words for .NET の無料試用版はありますか?
はい、Aspose.Words for .NETの無料トライアルをこちらからダウンロードできます。[ここ](https://releases.aspose.com/).

### Aspose.Words for .NET のドキュメントはどこにありますか?
 Aspose.Words for .NETの包括的なドキュメントは以下からアクセスできます。[このリンク](https://reference.aspose.com/words/net/).

### Aspose.Words for .NET のサポートを受けるにはどうすればよいですか?
サポートについては、Aspose.Wordsフォーラムをご覧ください。[このリンク](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
