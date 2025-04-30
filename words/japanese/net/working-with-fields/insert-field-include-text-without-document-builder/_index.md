---
"description": "詳細なステップバイステップ ガイドを使用して、Aspose.Words for .NET で DocumentBuilder を使用せずに FieldIncludeText を挿入する方法を学びます。"
"linktitle": "ドキュメントビルダーを使用せずにFieldIncludeTextを挿入する"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "ドキュメントビルダーなしでテキストを含むフィールドを挿入"
"url": "/ja/net/working-with-fields/insert-field-include-text-without-document-builder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# ドキュメントビルダーなしでテキストを含むフィールドを挿入

## 導入

ドキュメントの自動化と操作の世界において、Aspose.Words for .NET は強力なツールとして知られています。本日は、DocumentBuilder を使用せずに FieldIncludeText を挿入する方法を詳しく説明します。このチュートリアルでは、ステップバイステップで手順を説明し、コードの各部分とその目的を理解できるようにします。

## 前提条件

コードに進む前に、必要なものがすべて揃っていることを確認しましょう。

1. Aspose.Words for .NET: 最新バージョンがインストールされていることを確認してください。こちらからダウンロードできます。 [ここ](https://releases。aspose.com/words/net/).
2. .NET 開発環境: Visual Studio などの .NET 互換 IDE。
3. C# の基本知識: C# プログラミングの知識があると、理解しやすくなります。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートする必要があります。これらの名前空間は、Word文書の操作に必要なクラスとメソッドへのアクセスを提供します。

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

それでは、例を複数のステップに分解してみましょう。分かりやすくするために、各ステップを詳しく説明します。

## ステップ1: ディレクトリパスを設定する

最初のステップは、ドキュメントディレクトリへのパスを定義することです。Word文書はここに保存され、アクセスされます。

```csharp
// ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## ステップ2: 文書と段落を作成する

次に、新しいドキュメントを作成し、その中に段落を作成します。この段落にFieldIncludeTextフィールドを配置します。

```csharp
// ドキュメントと段落を作成します。
Document doc = new Document();
Paragraph para = new Paragraph(doc);
```

## ステップ3: フィールドを挿入するテキストフィールドを含める

次に、FieldIncludeTextフィールドを段落に挿入します。このフィールドを使用すると、別のドキュメントからテキストを取り込むことができます。

```csharp
// FieldIncludeText フィールドを挿入します。
FieldIncludeText fieldIncludeText = (FieldIncludeText)para.AppendField(FieldType.FieldIncludeText, false);
```

## ステップ4: フィールドプロパティを設定する

FieldIncludeTextフィールドのプロパティを指定する必要があります。これには、ブックマーク名とソースドキュメントのフルパスの設定が含まれます。

```csharp
fieldIncludeText.BookmarkName = "bookmark";
fieldIncludeText.SourceFullName = dataDir + "IncludeText.docx";
```

## ステップ5: 文書に段落を追加する

フィールドを設定したら、段落をドキュメントの最初のセクション本体に追加します。

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

これで完了です！これらの手順に従うことで、Aspose.Words for .NET の DocumentBuilder を使用せずに、FieldIncludeText を簡単に挿入できます。このアプローチにより、あるドキュメントのコンテンツを別のドキュメントに効率的に組み込むことができ、ドキュメント自動化タスクが大幅に簡素化されます。

## よくある質問

### Aspose.Words for .NET とは何ですか?  
Aspose.Words for .NETは、.NETアプリケーションでWord文書を操作するための強力なライブラリです。プログラムによる文書の作成、編集、変換が可能です。

### FieldIncludeText を使用する理由は何ですか?  
FieldIncludeText は、あるドキュメントのコンテンツを別のドキュメントに動的に組み込むのに役立ち、よりモジュール化され保守しやすいドキュメントを実現します。

### この方法を使用して、他のファイル形式のテキストを含めることはできますか?  
FieldIncludeTextはWord文書に特化しています。他の形式では、Aspose.Wordsが提供する別のメソッドやクラスが必要になる場合があります。

### Aspose.Words for .NET は .NET Core と互換性がありますか?  
はい、Aspose.Words for .NET は .NET Framework、.NET Core、.NET 5/6 をサポートしています。

### Aspose.Words for .NET の無料試用版を入手するにはどうすればいいですか?  
無料トライアルは [ここ](https://releases。aspose.com/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}