---
title: Word 文書の目次タブ位置を変更する
linktitle: Word 文書の目次タブ位置を変更する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して Word 文書の目次タブ ストップを変更する方法を学びます。このステップ バイ ステップ ガイドは、プロフェッショナルな外観の目次を作成するのに役立ちます。
weight: 10
url: /ja/net/programming-with-table-of-content/change-toc-tab-stops/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 文書の目次タブ位置を変更する

## 導入

Word 文書の目次 (TOC) を華やかにするにはどうしたらよいか考えたことはありますか? プロフェッショナルなタッチを出すために、タブ ストップを完璧に揃えたいかもしれません。ここで説明しました。今日は、Aspose.Words for .NET を使用して TOC タブ ストップを変更する方法について詳しく説明します。最後までお読みいただければ、TOC をおしゃれですっきりと見せるためのノウハウをすべて習得できることをお約束します。

## 前提条件

始める前に、必要なものがすべて揃っていることを確認しましょう。

1.  Aspose.Words for .NET: 次のようなことができます[ここからダウンロード](https://releases.aspose.com/words/net/).
2. 開発環境: Visual Studio または C# 互換の IDE。
3. Word 文書: 具体的には、目次を含む文書。

全部理解できましたか？素晴らしい！始めましょう。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートする必要があります。これは、プロジェクトを開始する前にツールを梱包するようなものです。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

このプロセスを、シンプルで理解しやすいステップに分解してみましょう。ドキュメントの読み込み、目次タブ ストップの変更、更新されたドキュメントの保存について説明します。

## ステップ1: ドキュメントを読み込む

なぜでしょうか? 変更したい目次が含まれている Word 文書にアクセスする必要があるからです。

どうやって？始めるための簡単なコード スニペットを次に示します。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENTS DIRECTORY";

//目次を含む文書を読み込む
Document doc = new Document(dataDir + "Table of contents.docx");
```

ドキュメントがケーキのようなもので、これからアイシングを加えるところだと想像してください。最初のステップは、ケーキを箱から取り出すことです。

## ステップ2: TOC段落を特定する

なぜでしょうか? TOC を構成する段落を正確に特定する必要があるからです。 

方法は？段落をループしてスタイルを確認します。

```csharp
foreach(Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.Style.StyleIdentifier >= StyleIdentifier.Toc1 &&
        para.ParagraphFormat.Style.StyleIdentifier <= StyleIdentifier.Toc9)
    {
        //目次の段落が見つかりました
    }
}
```

群衆をスキャンして友達を見つけるようなものだと考えてください。ここでは、目次エントリとしてスタイル設定された段落を探します。

## ステップ3: タブストップを変更する

なぜでしょうか? ここで魔法が起こります。タブ ストップを変更すると、目次がよりすっきりした外観になります。

方法は? 既存のタブ ストップを削除し、変更された位置に新しいタブ ストップを追加します。

```csharp
foreach(Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.Style.StyleIdentifier >= StyleIdentifier.Toc1 &&
        para.ParagraphFormat.Style.StyleIdentifier <= StyleIdentifier.Toc9)
    {
        TabStop tab = para.ParagraphFormat.TabStops[0];
        para.ParagraphFormat.TabStops.RemoveByPosition(tab.Position);
        para.ParagraphFormat.TabStops.Add(tab.Position - 50, tab.Alignment, tab.Leader);
    }
}
```

それは、リビングルームの家具をちょうどいい感じになるまで調整するようなものです。私たちは、完璧さを求めてタブ ストップを微調整しています。

## ステップ4: 変更したドキュメントを保存する

なぜでしょうか? あなたの努力がすべて保存され、閲覧または共有できるようにするためです。

方法は？ 元のドキュメントをそのまま残すために、新しい名前でドキュメントを保存します。

```csharp
//変更したドキュメントを保存する
doc.Save(dataDir + "WorkingWithTableOfContent.ChangeTocTabStops.docx");
```

すると、出来上がりです。TOC のタブ ストップが希望どおりの位置に設定されます。

## 結論

Aspose.Words for .NET を使用して Word 文書の TOC タブ ストップを変更するのは、一度分解してしまえば簡単です。文書を読み込み、TOC 段落を識別し、タブ ストップを変更して文書を保存することで、洗練されたプロフェッショナルな外観を実現できます。練習を重ねれば完璧になります。さまざまなタブ ストップ位置を試して、希望どおりのレイアウトを実現してください。

## よくある質問

### 異なる TOC レベルのタブ ストップを個別に変更できますか?
はい、できます。それぞれの特定の TOC レベル (Toc1、Toc2 など) を確認し、それに応じて調整するだけです。

### ドキュメントに複数の目次がある場合はどうなりますか?
コードはすべての TOC スタイルの段落をスキャンし、ドキュメント内に存在するすべての TOC を変更します。

### TOC エントリに複数のタブ ストップを追加することは可能ですか?
もちろんです！タブストップを必要な数だけ追加するには、`para.ParagraphFormat.TabStops`コレクション。

### タブ ストップの配置とリーダー スタイルを変更できますか?
はい、新しいタブ ストップを追加するときに、異なる配置とリーダー スタイルを指定できます。

### Aspose.Words for .NET を使用するにはライセンスが必要ですか?
はい、試用期間を超えてAspose.Words for .NETを使用するには有効なライセンスが必要です。[一時ライセンス](https://purchase.aspose.com/temporary-license/)または[1つ買う](https://purchase.aspose.com/buy).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
