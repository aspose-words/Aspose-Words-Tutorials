---
"description": "この詳細なステップバイステップ ガイドでは、Aspose.Words for .NET を使用して Word 文書内のブックマークされたコンテンツを表示および非表示にする方法を学習します。"
"linktitle": "Word文書内のブックマークされたコンテンツの表示/非表示"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "Word文書内のブックマークされたコンテンツの表示/非表示"
"url": "/ja/net/programming-with-bookmarks/show-hide-bookmarked-content/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Word文書内のブックマークされたコンテンツの表示/非表示

## 導入

Aspose.Words for .NET を使ったドキュメント操作の世界に飛び込んでみませんか？ドキュメント作成タスクの自動化を目指す開発者の方にも、Word ファイルをプログラムで操作してみたいという方にも、この記事はまさにうってつけです。今日は、Aspose.Words for .NET を使って、Word 文書内のブックマークされたコンテンツの表示と非表示を切り替える方法をご紹介します。このステップバイステップガイドを読めば、ブックマークに基づいてコンテンツの表示/非表示を自在にコントロールできるようになります。さあ、始めましょう！

## 前提条件

細かい点に入る前に、いくつか必要なものがあります。

1. Visual Studio: .NET と互換性のある任意のバージョン。
2. Aspose.Words for .NET: ダウンロード [ここ](https://releases。aspose.com/words/net/).
3. C# の基本的な理解: 簡単な「Hello World」プログラムを書くことができれば、準備は完了です。
4. ブックマーク付きの Word 文書: このチュートリアルでは、ブックマーク付きのサンプル文書を使用します。

## 名前空間のインポート

まずは必要な名前空間をインポートしましょう。これにより、タスクに必要なツールがすべて揃います。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

これらの名前空間が準備できたら、旅を始める準備は完了です。

## ステップ1: プロジェクトの設定

さて、まずは Visual Studio でプロジェクトを設定するところから始めましょう。

### 新しいプロジェクトを作成する

Visual Studioを開き、新しいコンソールアプリ（.NET Core）プロジェクトを作成します。「BookmarkVisibilityManager」など、わかりやすい名前を付けます。

### Aspose.Words for .NET を追加する

Aspose.Words for .NET をプロジェクトに追加する必要があります。これは NuGet パッケージマネージャーから実行できます。

1. [ツール] > [NuGet パッケージ マネージャー] > [ソリューションの NuGet パッケージの管理] に移動します。
2. 「Aspose.Words」を検索します。
3. パッケージをインストールします。

素晴らしい！プロジェクトの設定が完了したので、ドキュメントの読み込みに進みましょう。

## ステップ2: ドキュメントの読み込み

ブックマークを含むWord文書を読み込む必要があります。このチュートリアルでは、「Bookmarks.docx」というサンプル文書を使用します。

```csharp
// ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

このコードスニペットはドキュメントディレクトリへのパスを設定し、ドキュメントを `doc` 物体。

## ステップ3: ブックマークしたコンテンツの表示/非表示

いよいよ楽しい部分です。ブックマークに基づいてコンテンツを表示または非表示にします。 `ShowHideBookmarkedContent` これを処理します。

ブックマークしたコンテンツの表示を切り替える方法は次のとおりです。

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    Node currentNode = bm.BookmarkStart;
    while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
    {
        if (currentNode.NodeType == NodeType.Run)
        {
            Run run = currentNode as Run;
            run.Font.Hidden = isHidden;
        }
        currentNode = currentNode.NextSibling;
    }
}
```

### 方法の内訳

- ブックマークの取得: `Bookmark bm = doc.Range.Bookmarks[bookmarkName];` ブックマークを取得します。
- ノード トラバーサル: ブックマーク内のノードをトラバースします。
- 表示の切り替え: ノードが `Run` （連続したテキスト）の場合、 `Hidden` 財産。

## ステップ4：メソッドの適用

メソッドが完成したら、それを適用してブックマークに基づいてコンテンツを表示または非表示にしてみましょう。

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true);
```

このコード行は、「MyBookmark1」という名前のブックマーク内のコンテンツを非表示にします。

## ステップ5: ドキュメントを保存する

最後に、変更したドキュメントを保存しましょう。

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

これにより、変更を加えたドキュメントが保存されます。

## 結論

これで完了です！Aspose.Words for .NET を使って、Word 文書内のブックマークされたコンテンツを表示/非表示にする方法を学習しました。この強力なツールを使えば、レポートの自動化、テンプレートの作成、あるいは Word ファイルのちょっとした修正など、あらゆるドキュメント操作が簡単になります。コーディングを楽しんでください！

## よくある質問

### 複数のブックマークを一度に切り替えることはできますか?
はい、電話できます `ShowHideBookmarkedContent` 切り替えるブックマークごとにメソッドを使用します。

### コンテンツを非表示にすると、ドキュメントの構造に影響しますか?
いいえ、コンテンツを非表示にしても表示は維持されます。コンテンツはドキュメント内に残ります。

### この方法は他の種類のコンテンツにも使用できますか?
このメソッドは、テキストランを切り替えます。他のコンテンツタイプの場合は、ノードトラバーサルロジックを変更する必要があります。

### Aspose.Words for .NET は無料ですか?
Aspose.Wordsは無料トライアルを提供しています [ここ](https://releases.aspose.com/)ただし、本番環境での使用にはフルライセンスが必要です。ご購入いただけます。 [ここ](https://purchase。aspose.com/buy).

### 問題が発生した場合、どうすればサポートを受けることができますか?
Asposeコミュニティからサポートを受けることができます [ここ](https://forum。aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}