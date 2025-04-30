---
"description": "Aspose.Words for .NET を使用して Word 文書内のページ間の改行を無効にし、表の読みやすさと書式を維持する方法を学習します。"
"linktitle": "行形式 ページ間の改ページを無効にする"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "行形式 ページ間の改ページを無効にする"
"url": "/ja/net/programming-with-tables/row-format-disable-break-across-pages/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 行形式 ページ間の改ページを無効にする

## 導入

Word文書で表を操作する際、ページをまたいで行が改行されないようにしたい場合があります。これは、文書の読みやすさと書式設定を維持するために不可欠です。Aspose.Words for .NET は、ページをまたいで行が改行されないようにする簡単な方法を提供します。

このチュートリアルでは、Aspose.Words for .NET を使用して Word 文書内のページ間の改行を無効にする手順について説明します。

## 前提条件

始める前に、次の前提条件が満たされていることを確認してください。
- Aspose.Words for .NET ライブラリがインストールされています。
- 複数のページにまたがる表を含む Word 文書。

## 名前空間のインポート

まず、プロジェクトに必要な名前空間をインポートします。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## ステップ1：ドキュメントを読み込む

複数ページにまたがる表を含むドキュメントを読み込みます。

```csharp
// ドキュメントディレクトリへのパス 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## ステップ2: テーブルにアクセスする

文書内の最初の表にアクセスします。これは、変更したい表が文書内の最初の表であることを前提としています。

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## ステップ3: すべての行で改ページを無効にする

テーブルの各行をループし、 `AllowBreakAcrossPages` 財産に `false`これにより、行がページ間で分割されなくなります。

```csharp
// 表内のすべての行でページ間の改ページを無効にします。
foreach (Row row in table.Rows)
    row.RowFormat.AllowBreakAcrossPages = false;
```

## ステップ4: ドキュメントを保存する

変更したドキュメントを指定したディレクトリに保存します。

```csharp
doc.Save(dataDir + "WorkingWithTables.RowFormatDisableBreakAcrossPages.docx");
```

## 結論

このチュートリアルでは、Aspose.Words for .NET を使用して、Word 文書内のページをまたがる改行を無効にする方法を説明しました。上記の手順に従うことで、表の行がページをまたがって改行されることを防ぎ、文書の読みやすさと書式設定を維持できます。

## よくある質問

### すべての行ではなく、特定の行のページ間の行区切りを無効にすることはできますか?  
はい、特定の行の改行を無効にするには、目的の行にアクセスして設定します。 `AllowBreakAcrossPages` 財産に `false`。

### この方法は結合されたセルのあるテーブルでも機能しますか?  
はい、この方法は結合されたセルを持つ表でも機能します。プロパティ `AllowBreakAcrossPages` セルの結合に関係なく、行全体に適用されます。

### テーブルが別のテーブル内にネストされている場合、この方法は機能しますか?  
はい、ネストされたテーブルにも同じようにアクセスして変更できます。ネストされたテーブルをインデックスやその他のプロパティで正しく参照していることを確認してください。

### 行がページをまたいで改ページできるかどうかを確認するにはどうすればよいですか?  
行がページをまたいで改ページできるかどうかを確認するには、 `AllowBreakAcrossPages` の財産 `RowFormat` そしてその値を確認します。

### この設定をドキュメント内のすべての表に適用する方法はありますか?  
はい、ドキュメント内のすべてのテーブルをループして、各テーブルにこの設定を適用できます。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}