---
title: Doc を Docx に変換する
linktitle: Doc を Docx に変換する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して DOC を DOCX に変換する方法を学びます。コード例付きのステップバイステップ ガイド。開発者に最適です。
weight: 10
url: /ja/net/basic-conversions/doc-to-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Doc を Docx に変換する

## 導入

このチュートリアルでは、Aspose.Words for .NET を使用して DOC ファイルを DOCX 形式に変換する方法について説明します。Aspose.Words は、開発者が Word ドキュメントをプログラムで操作および変換できるようにする強力なドキュメント処理ライブラリです。

## 前提条件

始める前に、次の設定がされていることを確認してください。
- Visual Studio がシステムにインストールされています。
-  Aspose.Words for .NETがインストールされています。ダウンロードはこちらから[ここ](https://releases.aspose.com/words/net/).
- C# プログラミング言語に関する基本的な知識。

## 名前空間のインポート

まず、C# コードに必要な名前空間をインポートする必要があります。
```csharp
using Aspose.Words;
```

この名前空間は Aspose.Words API へのアクセスを提供し、アプリケーションで Word ドキュメントを操作できるようにします。

## ステップ1: DOCファイルを読み込む

まず、変換したい DOC ファイルを読み込みます。
```csharp
//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Aspose.Wordsを使用してDOCファイルを読み込む
Document doc = new Document(dataDir + "Document.doc");
```

## ステップ2: DOCXとして保存

次に、読み込んだドキュメントを DOCX 形式で保存します。
```csharp
//文書をDOCXとして保存する
doc.Save(dataDir + "ConvertedDocument.docx", SaveFormat.Docx);
```

## ステップ3: コードを実行する

アプリケーションをコンパイルして実行し、変換プロセスを実行します。指定されたディレクトリに入力ファイル「Document.doc」が存在することを確認します。

## ステップ4: 出力を確認する

出力ディレクトリで、「ConvertedDocument.docx」という名前の変換された DOCX ファイルを確認します。Aspose.Words for .NET を使用して DOC ファイルを DOCX に正常に変換しました。

## 結論

Aspose.Words for .NET を使用してプログラムで DOC を DOCX に変換するのは簡単で効率的です。わずか数行のコードでドキュメント変換を自動化し、時間と労力を節約できます。バッチ変換を処理する場合でも、ドキュメント処理をアプリケーションに統合する場合でも、Aspose.Words はニーズを満たす強力な機能を提供します。

## よくある質問

### Aspose.Words は他のドキュメント形式を変換できますか?
はい、Aspose.Words は、DOC、DOCX、RTF、HTML、PDF など、さまざまな形式間の変換をサポートしています。

### Aspose.Words のドキュメントはどこにありますか?
ドキュメントにアクセスできます[ここ](https://reference.aspose.com/words/net/).

### Aspose.Words の無料トライアルはありますか?
はい、無料トライアルをご利用いただけます[ここ](https://releases.aspose.com/).

### Aspose.Words のライセンスを購入するにはどうすればよいですか?
ライセンスを購入することができます[ここ](https://purchase.aspose.com/buy).

### Aspose.Words のサポートはどこで受けられますか?
サポートについては、Aspose.Wordsをご覧ください。[フォーラム](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
