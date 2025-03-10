---
title: 行の書式設定 ページ間の区切りを無効にする
linktitle: 行の書式設定 ページ間の区切りを無効にする
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して Word 文書内のページ間の行区切りを無効にし、表の読みやすさと書式を維持する方法を学習します。
weight: 10
url: /ja/net/programming-with-tables/row-format-disable-break-across-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 行の書式設定 ページ間の区切りを無効にする

## 導入

Word 文書で表を操作する場合、ページ間で行が分割されないようにする必要があります。これは、文書の読みやすさと書式を維持するために不可欠です。Aspose.Words for .NET では、ページ間での行の分割を簡単に無効にできます。

このチュートリアルでは、Aspose.Words for .NET を使用して Word 文書内のページ間の行区切りを無効にする手順を説明します。

## 前提条件

始める前に、次の前提条件を満たしていることを確認してください。
- Aspose.Words for .NET ライブラリがインストールされています。
- 複数ページにまたがる表を含む Word 文書。

## 名前空間のインポート

まず、プロジェクトに必要な名前空間をインポートします。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## ステップ1: ドキュメントを読み込む

複数ページにまたがる表を含むドキュメントを読み込みます。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## ステップ2: テーブルにアクセスする

ドキュメント内の最初のテーブルにアクセスします。これは、変更するテーブルがドキュメント内の最初のテーブルであることを前提としています。

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## ステップ3: すべての行でページ間の改ページを無効にする

テーブルの各行をループし、`AllowBreakAcrossPages`財産に`false`これにより、行がページ間で分割されなくなります。

```csharp
//テーブル内のすべての行でページ間の分割を無効にします。
foreach (Row row in table.Rows)
    row.RowFormat.AllowBreakAcrossPages = false;
```

## ステップ4: ドキュメントを保存する

変更したドキュメントを指定したディレクトリに保存します。

```csharp
doc.Save(dataDir + "WorkingWithTables.RowFormatDisableBreakAcrossPages.docx");
```

## 結論

このチュートリアルでは、Aspose.Words for .NET を使用して Word 文書内のページ間の行区切りを無効にする方法を説明しました。上記の手順に従うことで、表の行がそのまま残り、ページ間で分割されることがなくなり、文書の読みやすさと書式が維持されます。

## よくある質問

### すべての行ではなく、特定の行のページ間の行区切りを無効にすることはできますか?  
はい、特定の行の行区切りを無効にするには、目的の行にアクセスして設定します。`AllowBreakAcrossPages`財産に`false`.

### この方法は結合されたセルを含むテーブルでも機能しますか?  
はい、この方法は結合されたセルを持つテーブルでも機能します。プロパティ`AllowBreakAcrossPages`セルの結合に関係なく、行全体に適用されます。

### テーブルが別のテーブル内にネストされている場合、この方法は機能しますか?  
はい、同じ方法でネストされたテーブルにアクセスして変更できます。ネストされたテーブルをインデックスまたはその他のプロパティで正しく参照していることを確認してください。

### 行がページ間での分割を許可しているかどうかを確認するにはどうすればよいですか?  
行がページをまたいで改ページできるかどうかを確認するには、`AllowBreakAcrossPages`の財産`RowFormat`そしてその値を確認します。

### この設定をドキュメント内のすべての表に適用する方法はありますか?  
はい、ドキュメント内のすべてのテーブルをループして、各テーブルにこの設定を適用できます。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
