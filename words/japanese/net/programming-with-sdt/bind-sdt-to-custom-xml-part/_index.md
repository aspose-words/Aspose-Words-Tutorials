---
title: SDT をカスタム XML パーツにバインドする
linktitle: SDT をカスタム XML パーツにバインドする
second_title: Aspose.Words ドキュメント処理 API
description: このステップバイステップのチュートリアルでは、Aspose.Words for .NET を使用して、構造化ドキュメント タグ (SDT) を Word 文書内のカスタム XML パーツにバインドする方法を学習します。
weight: 10
url: /ja/net/programming-with-sdt/bind-sdt-to-custom-xml-part/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# SDT をカスタム XML パーツにバインドする

## 導入

カスタム XML データとやり取りする動的な Word ドキュメントを作成すると、アプリケーションの柔軟性と機能性を大幅に向上できます。Aspose.Words for .NET には、構造化ドキュメント タグ (SDT) をカスタム XML パーツにバインドする強力な機能が用意されており、データを動的に表示するドキュメントを作成できます。このチュートリアルでは、SDT をカスタム XML パーツにバインドするプロセスを段階的に説明します。さっそく始めましょう。

## 前提条件

始める前に、次の前提条件が満たされていることを確認してください。

-  Aspose.Words for .NET: 最新バージョンは以下からダウンロードできます。[Aspose.Words for .NET リリース](https://releases.aspose.com/words/net/).
- 開発環境: Visual Studio またはその他の互換性のある .NET IDE。
- C# の基本的な理解: C# プログラミング言語と .NET フレームワークに精通していること。

## 名前空間のインポート

Aspose.Words for .NET を効果的に使用するには、必要な名前空間をプロジェクトにインポートする必要があります。コード ファイルの先頭に次の using ディレクティブを追加します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Saving;
```

プロセスを管理しやすいステップに分割して、わかりやすくしましょう。各ステップでは、タスクの特定の部分をカバーします。

## ステップ1: ドキュメントを初期化する

まず、新しいドキュメントを作成し、環境を設定する必要があります。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";

//新しいドキュメントを初期化する
Document doc = new Document();
```

この手順では、カスタム XML データと SDT を保持する新しいドキュメントを初期化します。

## ステップ2: カスタムXMLパーツを追加する

次に、ドキュメントにカスタム XML パーツを追加します。このパーツには、SDT にバインドする XML データが含まれます。

```csharp
//ドキュメントにカスタムXMLパーツを追加する
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(Guid.NewGuid().ToString("B"), "<root><text>Hello, World!</text></root>");
```

ここでは、一意の識別子を持つ新しいカスタム XML パーツを作成し、いくつかのサンプル XML データを追加します。

## ステップ3: 構造化ドキュメントタグ (SDT) を作成する

カスタム XML パーツを追加した後、XML データを表示するための SDT を作成します。

```csharp
//構造化ドキュメントタグ (SDT) を作成する
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Block);
doc.FirstSection.Body.AppendChild(sdt);
```

PlainText タイプの SDT を作成し、それをドキュメント本体の最初のセクションに追加します。

## ステップ 4: SDT をカスタム XML パーツにバインドする

ここで、XPath 式を使用して SDT をカスタム XML パーツにバインドします。

```csharp
// SDT をカスタム XML パーツにバインドする
sdt.XmlMapping.SetMapping(xmlPart, "/root[1]/text[1]", "");
```

このステップではSDTを`<text>`要素内の`<root>`カスタム XML パーツのノード。

## ステップ5: ドキュメントを保存する

最後に、ドキュメントを指定されたディレクトリに保存します。

```csharp
//文書を保存する
doc.Save(dataDir + "WorkingWithSdt.BindSDTtoCustomXmlPart.doc");
```

このコマンドは、バインドされた SDT を含むドキュメントを指定されたディレクトリに保存します。

## 結論

おめでとうございます! Aspose.Words for .NET を使用して、SDT をカスタム XML パーツにバインドできました。この強力な機能により、XML コンテンツを変更するだけで新しいデータで簡単に更新できる動的なドキュメントを作成できます。レポートの生成、テンプレートの作成、ドキュメント ワークフローの自動化など、Aspose.Words for .NET には、タスクをより簡単かつ効率的にするために必要なツールが用意されています。

## よくある質問

### 構造化ドキュメントタグ (SDT) とは何ですか?
構造化ドキュメント タグ (SDT) は、動的なデータをバインドしてドキュメントをインタラクティブかつデータ駆動型にするために使用できる Word ドキュメント内のコンテンツ制御要素です。

### 複数の SDT を 1 つのドキュメント内の異なる XML パーツにバインドできますか?
はい、複数の SDT を同じドキュメント内の異なる XML 部分にバインドして、複雑なデータ駆動型テンプレートを作成できます。

### カスタム XML パーツ内の XML データを更新するにはどうすればよいですか?
 XMLデータを更新するには、`CustomXmlPart`オブジェクトを作成し、その XML コンテンツを直接変更します。

### SDT を要素ではなく XML 属性にバインドすることは可能ですか?
はい、目的の属性を対象とする適切な XPath 式を指定することにより、SDT を XML 属性にバインドできます。

### Aspose.Words for .NET に関する詳細なドキュメントはどこで入手できますか?
 Aspose.Words for .NETに関する包括的なドキュメントは以下でご覧いただけます。[Aspose.Words ドキュメント](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
