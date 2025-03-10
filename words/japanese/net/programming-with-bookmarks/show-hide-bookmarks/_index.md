---
title: Word 文書のブックマークを表示/非表示
linktitle: Word 文書のブックマークを表示/非表示
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して Word 文書内のブックマークを動的に表示または非表示にする方法を、ステップバイステップ ガイドで学習します。開発者に最適です。
weight: 10
url: /ja/net/programming-with-bookmarks/show-hide-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 文書のブックマークを表示/非表示

## 導入

Word 文書の特定の部分を動的に表示または非表示にしたいと思ったことはありませんか? 幸運です! Aspose.Words for .NET を使用すると、文書内のブックマークされたコンテンツの表示を簡単に管理できます。このチュートリアルでは、Aspose.Words for .NET を使用して Word 文書内のブックマークを表示および非表示にする手順を説明します。コードを段階的に説明していくので、熟練した開発者でも初心者でも、このガイドは簡単に理解できます。

## 前提条件

コードに進む前に、必要なものがすべて揃っていることを確認しましょう。

1.  Aspose.Words for .NET: Aspose.Words for .NETライブラリがインストールされていることを確認してください。インストールされていない場合はダウンロードできます。[ここ](https://releases.aspose.com/words/net/).
2. 開発環境: Visual Studio のような IDE。
3. C# の基礎知識: C# プログラミングに精通していると有利です。
4. Word 文書: ブックマーク付きのサンプル Word 文書。

## 名前空間のインポート

コードを開始する前に、必要な名前空間をインポートする必要があります。C# ファイルの先頭に次のコードを追加します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

## ステップ1: ドキュメントを読み込む

まず最初に、ブックマークを含む Word 文書を読み込む必要があります。手順は次のとおりです。

```csharp
//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

### 説明

- dataDir: これは Word 文書が保存されているディレクトリ パスです。
- ドキュメントdoc: これは、`Document`指定したファイルを持つクラス。

## ステップ2: ブックマークしたコンテンツを表示または非表示にする

次に、ブックマークされたコンテンツを表示または非表示にするメソッドを定義します。完全なメソッドは次のとおりです。

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool showHide)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.MoveToDocumentEnd();

    // {IF "{MERGEFIELD ブックマーク}" = "true" "" ""}
    Field field = builder.InsertField("IF \"", null);
    builder.MoveTo(field.Start.NextSibling);
    builder.InsertField("MERGEFIELD " + bookmarkName + "", null);
    builder.Write("\" = \"true\" ");
    builder.Write("\"");
    builder.Write("\"");
    builder.Write(" \"\"");

    Node currentNode = field.Start;
    bool flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.Run)
            if (currentNode.ToString(SaveFormat.Text).Trim() == "\"")
                flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkStart.ParentNode.InsertBefore(currentNode, bm.BookmarkStart);
        currentNode = nextNode;
    }

    Node endNode = bm.BookmarkEnd;
    flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.FieldEnd)
            flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkEnd.ParentNode.InsertAfter(currentNode, endNode);
        endNode = currentNode;
        currentNode = nextNode;
    }

    doc.MailMerge.Execute(new[] { bookmarkName }, new object[] { showHide });
}
```

### 説明

- ブックマーク bm: ドキュメントからブックマークを取得します。
- DocumentBuilder ビルダー: ドキュメントのナビゲーションと変更に役立ちます。
- フィールド フィールド: ブックマークの条件を確認するための IF フィールドを挿入します。
- ノード currentNode: ノードをトラバースしてフィールドの開始と終了を見つけます。

## ステップ3: 表示/非表示機能を実行する

さて、あなたは`ShowHideBookmarkedContent`メソッドにドキュメント、ブックマーク名、および可視性フラグを渡します。

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", false);
```

### 説明

- doc: ドキュメント オブジェクト。
- 「MyBookmark1」: 表示/非表示にするブックマークの名前。
- false: 可視性フラグ (表示の場合は true、非表示の場合は false)。

## ステップ4: ドキュメントを保存する

最後に、変更したドキュメントを保存します。

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### 説明

- dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx": 変更が保存される新しいドキュメントのパスと名前。

## 結論

これで完了です。Aspose.Words for .NET を使用して Word 文書でブックマークを表示および非表示にする方法を学習しました。この手法は、条件付きコンテンツを含む文書を動的に生成する場合に非常に役立ちます。

## よくある質問

### Aspose.Words for .NET とは何ですか?
Aspose.Words for .NET は、開発者がプログラムによって Word ドキュメントを作成、変更、変換できるようにする強力なドキュメント処理ライブラリです。

### Aspose.Words for .NET を入手するにはどうすればよいですか?
 Aspose.Words for .NETは以下からダウンロードできます。[ここ](https://releases.aspose.com/words/net/)無料トライアルもございます。

### この方法は他の種類のブックマークにも使用できますか?
はい、この方法は、Word 文書内のブックマークの可視性を管理するために使用できます。

### ドキュメントに指定されたブックマークが含まれていない場合はどうなりますか?
ブックマークが存在しない場合、メソッドはエラーをスローします。ブックマークを表示/非表示にする前に、ブックマークが存在することを確認してください。

### 問題が発生した場合、どうすればサポートを受けることができますか?
 Asposeコミュニティからサポートを受けることができます[ここ](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
