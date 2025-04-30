---
"description": "Aspose.Words for .NET を使用して、Word 文書内の単語の修正タイプを取得する方法を学びます。このステップバイステップガイドは、文書の修正を効率的に処理するのに役立ちます。"
"linktitle": "単語の修正タイプを取得する"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "単語の修正タイプを取得する"
"url": "/ja/net/working-with-revisions/get-revision-types/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 単語の修正タイプを取得する

## 導入

ドキュメントの改訂履歴が山積みで、誰がいつ何を変更したのか分からず途方に暮れたことはありませんか？そんな経験はありませんか？ドキュメントの改訂履歴の管理は、特に大規模なドキュメントを扱う場合は、大変な作業になりがちです。でも、ご安心ください！Aspose.Words for .NETを使えば、これらの改訂履歴を簡単に特定し、管理できます。このガイドでは、Aspose.Words for .NETを使ってWord文書内の単語の改訂履歴を取得する方法を、ステップバイステップで解説します。さあ、シートベルトを締めて、早速始めましょう！

## 前提条件

コードに取り掛かる前に、必要なものがいくつかあります。

1. Aspose.Words for .NET ライブラリ: まだダウンロードしていない場合は、こちらからダウンロードしてください。 [ここ](https://releases。aspose.com/words/net/).
2. 開発環境: Visual Studio またはその他の .NET 互換 IDE。
3. C# の基礎知識: C# プログラミング言語を理解していると役立ちます。
4. 修正されたWord文書: `.docx` コードをテストするための変更追跡ファイル。

## 名前空間のインポート

まず、C#プロジェクトに必要な名前空間をインポートする必要があります。これにより、Aspose.Words for .NETが提供する機能にアクセスできるようになります。

```csharp
using Aspose.Words;
using Aspose.Words.Revision;
using System;
```

理解と実装を深めるために、例を複数のステップに分解してみましょう。

## ステップ1: ドキュメントディレクトリを設定する

まず最初に、ドキュメントディレクトリへのパスを定義する必要があります。ここに、変更を加えたWord文書が保存されます。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

交換する `"YOUR DOCUMENT DIRECTORY"` ドキュメント フォルダーへの実際のパスを入力します。

## ステップ2: Word文書を読み込む

次に、Word文書をプロジェクトに読み込みます。この文書には、分析したいリビジョンが含まれている必要があります。

```csharp
Document doc = new Document(dataDir + "Revisions.docx");
```

ファイルが `Revisions.docx` 指定されたディレクトリに存在します。

## ステップ3: 段落コレクションにアクセスする

ドキュメントが読み込まれたら、ドキュメント本体の最初のセクションにある段落にアクセスする必要があります。これにより、各段落を反復処理して修正箇所を確認できます。

```csharp
ParagraphCollection paragraphs = doc.FirstSection.Body.Paragraphs;
```

## ステップ4：段落を繰り返して修正箇所を確認する

ここで魔法が起こります。各段落を反復処理し、移動（削除または挿入）されたかどうかを確認します。

```csharp
for (int i = 0; i < paragraphs.Count; i++)
{
    if (paragraphs[i].IsMoveFromRevision)
        Console.WriteLine("Paragraph {0} has been moved (deleted).", i);
    if (paragraphs[i].IsMoveToRevision)
        Console.WriteLine("Paragraph {0} has been moved (inserted).", i);
}
```

このループは各段落を巡回し、 `IsMoveFromRevision` そして `IsMoveToRevision` 段落が移動 (削除) されたか、移動 (挿入) されたかを判断するプロパティ。

## 結論

これで完了です！Aspose.Words for .NETを使えば、わずか数行のコードでWord文書内の変更内容を簡単に識別できます。この強力なライブラリを使えば、文書の変更管理が簡単になり、より重要なタスクに集中できるようになります。 

## よくある質問

### Aspose.Words for .NET を使用して、特定のユーザーによる変更を追跡できますか?

はい、Aspose.Words for .NET には、変更の作成者を含むリビジョンの詳細にアクセスする機能が用意されています。

### Aspose.Words for .NET の無料試用版はありますか?

もちろんです！無料トライアルをご利用いただけます [ここ](https://releases。aspose.com/).

### Aspose.Words for .NET の一時ライセンスを適用するにはどうすればよいですか?

一時ライセンスの申請と申請は、 [ここ](https://purchase。aspose.com/temporary-license/).

### Aspose.Words for .NET の詳細なドキュメントはどこで入手できますか?

詳細な資料は、 [Aspose ウェブサイト](https://reference。aspose.com/words/net/).

### Aspose.Words for .NET を非商用プロジェクトで使用できますか?

はい、Aspose.Words for .NET は商用プロジェクトと非商用プロジェクトの両方で使用できますが、ライセンス条件を必ず確認してください。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}