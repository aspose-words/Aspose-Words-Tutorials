---
title: フィールドの変更 カルチャーソースの更新
linktitle: フィールドの変更 カルチャーソースの更新
second_title: Aspose.Words ドキュメント処理 API
description: このガイドでは、Aspose.Words for .NET でフィールド更新カルチャ ソースを変更する方法を説明します。さまざまなカルチャに基づいて日付の書式を簡単に制御します。
weight: 10
url: /ja/net/working-with-fields/change-field-update-culture-source/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# フィールドの変更 カルチャーソースの更新

## 導入

このチュートリアルでは、Aspose.Words for .NET の世界を詳しく見ていき、フィールド更新カルチャ ソースを変更する方法を探ります。日付フィールドを含む Word 文書を扱っていて、さまざまなカルチャに基づいてこれらの日付の書式設定を制御する必要がある場合は、このガイドが役立ちます。プロセスを段階的に説明し、各概念を理解してプロジェクトに効果的に適用できるようにします。

## 前提条件

コードに進む前に、次のものを用意してください。

-  Aspose.Words for .NET: ダウンロードはこちらから[ここ](https://releases.aspose.com/words/net/).
- 開発環境: .NET 互換の IDE (Visual Studio など)。
- C# の基本知識: このチュートリアルでは、C# プログラミングの基礎を理解していることを前提としています。

## 名前空間のインポート

まず、プロジェクトに必要な名前空間をインポートしましょう。これにより、Aspose.Words によって提供されるすべての必要なクラスとメソッドにアクセスできるようになります。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

ここで、Aspose.Words for .NET でフィールド更新カルチャ ソースを変更する方法を理解できるように、例を複数の手順に分解してみましょう。

## ステップ1: ドキュメントを初期化する

最初のステップは、`Document`クラスと`DocumentBuilder`これにより、Word 文書の作成と操作の基盤が確立されます。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ステップ2: 特定のロケールのフィールドを挿入する

次に、ドキュメントにフィールドを挿入する必要があります。この例では、2 つの日付フィールドを挿入します。フォントのロケールをドイツ語 (LocaleId = 1031) に設定して、カルチャが日付形式にどのように影響するかを示します。

```csharp
builder.Font.LocaleId = 1031; //ドイツ語
builder.InsertField("MERGEFIELD Date1 \\@ \"dddd, d MMMM yyyy\"");
builder.Write(" - ");
builder.InsertField("MERGEFIELD Date2 \\@ \"dddd, d MMMM yyyy\"");
```

## ステップ3: フィールド更新カルチャソースを設定する

フィールドを更新するときに使用する文化を制御するには、`FieldUpdateCultureSource`の財産`FieldOptions`クラス。このプロパティは、カルチャがフィールド コードから取得されるか、ドキュメントから取得されるかを決定します。

```csharp
doc.FieldOptions.FieldUpdateCultureSource = FieldUpdateCultureSource.FieldCode;
```

## ステップ4: 差し込み印刷を実行する

次に、実際のデータをフィールドに入力するために差し込み印刷を実行する必要があります。この例では、2番目の日付フィールドを設定します（`Date2`）から2011年1月1日まで。

```csharp
doc.MailMerge.Execute(new string[] { "Date2" }, new object[] { new DateTime(2011, 1, 1) });
```

## ステップ5: ドキュメントを保存する

最後に、ドキュメントを指定されたディレクトリに保存します。この手順で、フィールド更新カルチャ ソースを変更するプロセスが完了します。

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeFieldUpdateCultureSource.docx");
```

## 結論

これで完了です。Aspose.Words for .NET でフィールド更新カルチャ ソースを正常に変更できました。次の手順に従うことで、Word ドキュメントに日付やその他のフィールド値が指定されたカルチャ設定に従って表示されるようになります。これは、国際的なユーザー向けのドキュメントを生成する場合に特に役立ちます。

## よくある質問

### 設定の目的は何ですか？`LocaleId`?
の`LocaleId`テキストのカルチャ設定を指定します。これは、日付やその他のロケールに依存するデータの書式設定に影響します。

### ドイツ語以外のロケールを使用できますか?
はい、設定できます`LocaleId`有効なロケール識別子に置き換えます。たとえば、英語 (米国) の場合は 1033 です。

### 設定しないとどうなるか`FieldUpdateCultureSource` property?
このプロパティが設定されていない場合、フィールドを更新するときにドキュメントのデフォルトのカルチャ設定が使用されます。

### フィールド コードではなく、ドキュメントのカルチャに基づいてフィールドを更新することは可能ですか?
はい、設定できます`FieldUpdateCultureSource`に`FieldUpdateCultureSource.Document`ドキュメントのカルチャ設定を使用します。

### 日付を別のパターンでフォーマットするにはどうすればよいですか?
日付のフォーマットパターンは、`InsertField`方法を変更することにより`\\@`スイッチ値。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
