---
title: ドキュメントビルダーを使用せずに TOA フィールドを挿入する
linktitle: ドキュメントビルダーを使用せずに TOA フィールドを挿入する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET でドキュメント ビルダーを使用せずに TOA フィールドを挿入する方法を学びます。法的引用を効率的に管理するには、ステップ バイ ステップ ガイドに従ってください。
weight: 10
url: /ja/net/working-with-fields/insert-toafield-without-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ドキュメントビルダーを使用せずに TOA フィールドを挿入する

## 導入

Word 文書に引用文献一覧 (TOA) フィールドを作成するのは、複雑なパズルを組み立てるような作業です。しかし、Aspose.Words for .NET を使用すると、プロセスはスムーズかつ簡単になります。この記事では、ドキュメント ビルダーを使用せずに TOA フィールドを挿入する手順を説明します。これにより、Word 文書内で引用文献や法的な参照文献を簡単に管理できるようになります。

## 前提条件

チュートリアルに進む前に、必要な基本事項について説明しましょう。

-  Aspose.Words for .NET: 最新バージョンがインストールされていることを確認してください。[Aspose ウェブサイト](https://releases.aspose.com/words/net/).
- 開発環境: Visual Studio などの .NET 互換 IDE。
- 基本的な C# の知識: 基本的な C# の構文と概念を理解しておくと役立ちます。
- サンプル Word 文書: TOA フィールドを挿入する場所にサンプル文書を作成するか、用意しておきます。

## 名前空間のインポート

開始するには、Aspose.Words ライブラリから必要な名前空間をインポートする必要があります。このセットアップにより、ドキュメント操作に必要なすべてのクラスとメソッドにアクセスできるようになります。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

プロセスをシンプルでわかりやすいステップに分解してみましょう。各段階をガイドしながら、各コードが何を実行し、それが TOA フィールドの作成にどのように貢献するかを説明します。

## ステップ1: ドキュメントを初期化する

まず、インスタンスを作成する必要があります`Document`クラス。このオブジェクトは、作業中の Word 文書を表します。

```csharp
//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

このコードは、新しい Word 文書を初期化します。これは、コンテンツを追加する空白のキャンバスを作成するものと考えることができます。

## ステップ2: TAフィールドを作成して構成する

次に、TA (Table of Authorities) フィールドを追加します。このフィールドは、TOA に表示されるエントリをマークします。

```csharp
Paragraph para = new Paragraph(doc);

// TA フィールドと TOA フィールドを次のように挿入します。
// { TA \c 1 \l "値 0" }
FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);
fieldTA.EntryCategory = "1";
fieldTA.LongCitation = "Value 0";

doc.FirstSection.Body.AppendChild(para);
```

内訳は次のとおりです。
- Paragraph para = new Paragraph(doc);: ドキュメント内に新しい段落を作成します。
-  FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);: TA フィールドを段落に追加します。の`FieldType.FieldTOAEntry`これは TOA エントリ フィールドであることを指定します。
- fieldTA.EntryCategory = "1";: エントリ カテゴリを設定します。これは、さまざまな種類のエントリを分類するのに役立ちます。
- fieldTA.LongCitation = "Value 0";: 長い引用テキストを指定します。これは TOA に表示されるテキストです。
- doc.FirstSection.Body.AppendChild(para);: TA フィールドを含む段落をドキュメントの本文に追加します。

## ステップ3: TOAフィールドを追加する

ここで、すべての TA エントリをテーブルにコンパイルする実際の TOA フィールドを挿入します。

```csharp
para = new Paragraph(doc);

FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);
fieldToa.EntryCategory = "1";
doc.FirstSection.Body.AppendChild(para);
```

このステップでは、次の操作を行います。
- FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);: TOA フィールドを段落に追加します。
- fieldToa.EntryCategory = "1";: カテゴリ「1」でマークされたエントリのみを含むようにエントリをフィルタリングします。

## ステップ4: TOAフィールドを更新する

TOA フィールドを挿入した後、最新のエントリが反映されるように更新する必要があります。

```csharp
fieldToa.Update();
```

このコマンドは TOA フィールドを更新し、マークされたすべてのエントリがテーブルに正しく表示されるようにします。

## ステップ5: ドキュメントを保存する

最後に、新しく追加された TOA フィールドを含むドキュメントを保存します。

```csharp
doc.Save(dataDir + "WorkingWithFields.InsertTOAFieldWithoutDocumentBuilder.docx");
```

このコード行は、ドキュメントを指定されたディレクトリに保存します。`"YOUR DOCUMENT DIRECTORY"`ファイルを保存する実際のパスを入力します。

## 結論

これで完了です。ドキュメント ビルダーを使用せずに、Word ドキュメントに TOA フィールドを正常に追加できました。これらの手順に従うことで、法務文書の引用を効率的に管理し、包括的な引用文献一覧を作成できます。Aspose.Words for .NET を使用すると、このプロセスがスムーズかつ効率的になり、複雑なドキュメント タスクを簡単に処理できるツールが提供されます。

## よくある質問

### 異なるカテゴリの複数の TA フィールドを追加できますか?
はい、異なるカテゴリの複数のTAフィールドを追加できます。`EntryCategory`それに応じて財産。

### TOA の外観をカスタマイズするにはどうすればよいですか?
エントリの書式設定やカテゴリ ラベルなどの TOA フィールドのプロパティを変更することで、TOA の外観をカスタマイズできます。

### TOA フィールドを自動的に更新することは可能ですか?
 TOAフィールドを手動で更新することもできますが、`Update`メソッドでは、Aspose.Words は現在、ドキュメントの変更に対する自動更新をサポートしていません。

### ドキュメントの特定の部分に TA フィールドをプログラムで追加できますか?
はい、目的の段落またはセクションに TA フィールドを挿入することで、特定の場所に TA フィールドを追加できます。

### 1 つのドキュメントで複数の TOA フィールドを処理するにはどうすればよいですか?
異なるTOAフィールドを割り当てることで複数のTOAフィールドを管理できます。`EntryCategory`値を設定し、各 TOA フィールドがカテゴリに基づいてエントリをフィルター処理するようにします。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
