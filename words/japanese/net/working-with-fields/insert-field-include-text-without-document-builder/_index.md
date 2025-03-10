---
title: ドキュメント ビルダーなしでテキストを含むフィールドを挿入する
linktitle: ドキュメント ビルダーを使用せずに FieldIncludeText を挿入する
second_title: Aspose.Words ドキュメント処理 API
description: 詳細なステップバイステップ ガイドを使用して、Aspose.Words for .NET で DocumentBuilder を使用せずに FieldIncludeText を挿入する方法を学習します。
weight: 10
url: /ja/net/working-with-fields/insert-field-include-text-without-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ドキュメント ビルダーなしでテキストを含むフィールドを挿入する

## 導入

ドキュメントの自動化と操作の世界では、Aspose.Words for .NET は強力なツールとして知られています。今日は、DocumentBuilder を使用せずに FieldIncludeText を挿入する方法について、詳細なガイドを紹介します。このチュートリアルでは、プロセスをステップごとに説明し、コードの各部分とその目的を理解できるようにします。

## 前提条件

コードに進む前に、必要なものがすべて揃っていることを確認しましょう。

1.  Aspose.Words for .NET: 最新バージョンがインストールされていることを確認してください。こちらからダウンロードできます。[ここ](https://releases.aspose.com/words/net/).
2. .NET 開発環境: Visual Studio などの .NET 互換 IDE。
3. C# の基礎知識: C# プログラミングの知識があると、理解しやすくなります。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートする必要があります。これらの名前空間は、Word 文書の操作に必要なクラスとメソッドへのアクセスを提供します。

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

それでは、例を複数のステップに分解してみましょう。わかりやすくするために、各ステップを詳しく説明します。

## ステップ1: ディレクトリパスを設定する

最初のステップは、ドキュメント ディレクトリへのパスを定義することです。これは、Word ドキュメントが保存され、アクセスされる場所です。

```csharp
//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## ステップ2: 文書と段落を作成する

次に、新しいドキュメントを作成し、そのドキュメント内に段落を作成します。この段落には FieldIncludeText フィールドが含まれます。

```csharp
//ドキュメントと段落を作成します。
Document doc = new Document();
Paragraph para = new Paragraph(doc);
```

## ステップ3: フィールドを挿入するテキストフィールドを含める

ここで、FieldIncludeText フィールドを段落に挿入します。このフィールドを使用すると、別のドキュメントのテキストを含めることができます。

```csharp
// FieldIncludeText フィールドを挿入します。
FieldIncludeText fieldIncludeText = (FieldIncludeText)para.AppendField(FieldType.FieldIncludeText, false);
```

## ステップ4: フィールドプロパティを設定する

FieldIncludeText フィールドのプロパティを指定する必要があります。これには、ブックマーク名とソース ドキュメントの完全なパスの設定が含まれます。

```csharp
fieldIncludeText.BookmarkName = "bookmark";
fieldIncludeText.SourceFullName = dataDir + "IncludeText.docx";
```

## ステップ5: 文書に段落を追加する

フィールドを設定したら、ドキュメントの最初のセクション本体に段落を追加します。

```csharp
doc.FirstSection.Body.AppendChild(para);
```

## ステップ6: フィールドの更新

ドキュメントを保存する前に、FieldIncludeText を更新して、ソース ドキュメントから正しいコンテンツが取得されるようにする必要があります。

```csharp
fieldIncludeText.Update();
```

## ステップ7: ドキュメントを保存する

最後に、ドキュメントを指定されたディレクトリに保存します。

```csharp
doc.Save(dataDir + "InsertionFieldFieldIncludeTextWithoutDocumentBuilder.docx");
```

## 結論

これで完了です。これらの手順に従うと、Aspose.Words for .NET で DocumentBuilder を使用せずに FieldIncludeText を簡単に挿入できます。このアプローチにより、あるドキュメントのコンテンツを別のドキュメントに組み込むための効率的な方法が提供され、ドキュメントの自動化タスクが大幅に簡素化されます。

## よくある質問

### Aspose.Words for .NET とは何ですか?  
Aspose.Words for .NET は、.NET アプリケーションで Word 文書を操作するための強力なライブラリです。プログラムで文書を作成、編集、変換できます。

### FieldIncludeText を使用する理由は何ですか?  
FieldIncludeText は、あるドキュメントのコンテンツを別のドキュメントに動的に含め、よりモジュール化され保守しやすいドキュメントを作成するのに役立ちます。

### この方法を使用して、他のファイル形式のテキストを含めることはできますか?  
FieldIncludeText は、特に Word 文書で機能します。他の形式では、Aspose.Words によって提供される別のメソッドまたはクラスが必要になる場合があります。

### Aspose.Words for .NET は .NET Core と互換性がありますか?  
はい、Aspose.Words for .NET は .NET Framework、.NET Core、.NET 5/6 をサポートしています。

### Aspose.Words for .NET の無料試用版を入手するにはどうすればいいですか?  
無料トライアルはこちらから[ここ](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
