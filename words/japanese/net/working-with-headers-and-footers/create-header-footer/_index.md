---
"description": "Aspose.Words for .NET を使用して、Word 文書にヘッダーとフッターを追加およびカスタマイズする方法を学びます。このステップバイステップガイドに従えば、プロフェッショナルな文書の書式設定が可能になります。"
"linktitle": "ヘッダーフッターを作成"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "ヘッダーフッターを作成"
"url": "/ja/net/working-with-headers-and-footers/create-header-footer/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# ヘッダーフッターを作成

## 導入

ドキュメントにヘッダーとフッターを追加すると、プロフェッショナルな印象を与え、読みやすさが向上します。Aspose.Words for .NETを使えば、Word文書のヘッダーとフッターを簡単に作成・カスタマイズできます。このチュートリアルでは、これらの機能をシームレスに実装できるよう、手順を一つずつ解説します。

## 前提条件

始める前に、次のものがあることを確認してください。

- Aspose.Words for .NET: ダウンロードしてインストールするには、 [ダウンロードリンク](https://releases。aspose.com/words/net/).
- 開発環境: コードを記述して実行するための Visual Studio など。
- C# の基礎知識: C# と .NET フレームワークの理解。
- サンプル ドキュメント: ヘッダーとフッターを適用するためのサンプル ドキュメント、またはチュートリアルに示されているように新しいドキュメントを作成します。

## 名前空間のインポート

まず、Aspose.Words のクラスとメソッドにアクセスするために必要な名前空間をインポートする必要があります。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System;
```

## ステップ1: ドキュメントディレクトリを定義する

ドキュメントを保存するディレクトリを定義します。これにより、パスを効率的に管理できます。

```csharp
// ドキュメントディレクトリへのパス
string dataDir = "YOUR_DIRECTORY_OF_DOCUMENTS";
```

## ステップ2: 新しいドキュメントを作成する

新しいドキュメントを作成し、 `DocumentBuilder` コンテンツの追加を容易にするため。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ステップ3: ページ設定を構成する

最初のページに異なるヘッダー/フッターを表示するかどうかなど、ページ設定を行います。

```csharp
Section currentSection = builder.CurrentSection;
PageSetup pageSetup = currentSection.PageSetup;

pageSetup.DifferentFirstPageHeaderFooter = true;
pageSetup.HeaderDistance = 20;
```

## ステップ4: 最初のページにヘッダーを追加する

最初のページのヘッダーセクションに移動し、ヘッダーテキストを設定します。

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;

builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.Font.Size = 14;

builder.Write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

## ステップ5: プライマリヘッダーを追加する

プライマリ ヘッダー セクションに移動し、画像とテキストを挿入します。

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);

// ヘッダーに画像を挿入する
builder.InsertImage(dataDir + "Graphics Interchange Format.gif", 
    RelativeHorizontalPosition.Page, 10, RelativeVerticalPosition.Page, 10, 50, 50, WrapType.Through);

builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Aspose.Words Header/Footer Creation Primer.");
```

## ステップ6: プライマリフッターを追加する

プライマリ フッター セクションに移動し、フッター コンテンツをフォーマットするためのテーブルを作成します。

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.FooterPrimary);

builder.StartTable();
builder.CellFormat.ClearFormatting();
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);

// ページ番号を追加する
builder.Write("Page ");
builder.InsertField("PAGE", "");
builder.Write(" of ");
builder.InsertField("NUMPAGES", "");

builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Left;
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

builder.Write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Right;

builder.EndRow();
builder.EndTable();
```

## ステップ7: コンテンツと改ページを追加する

ドキュメントの末尾に移動し、改ページを追加して、異なるページ設定で新しいセクションを作成します。

```csharp
builder.MoveToDocumentEnd();
builder.InsertBreak(BreakType.PageBreak);
builder.InsertBreak(BreakType.SectionBreakNewPage);

currentSection = builder.CurrentSection;
pageSetup = currentSection.PageSetup;
pageSetup.Orientation = Orientation.Landscape;
pageSetup.DifferentFirstPageHeaderFooter = false;

currentSection.HeadersFooters.LinkToPrevious(false);
CopyHeadersFootersFromPreviousSection(currentSection);

HeaderFooter primaryFooter = currentSection.HeadersFooters[HeaderFooterType.FooterPrimary];
Row row = primaryFooter.Tables[0].FirstRow;
row.FirstCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);
row.LastCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

doc.Save(dataDir + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```

## ステップ8: 前のセクションからヘッダーとフッターをコピーする

前のセクションのヘッダーとフッターを再利用する場合は、それらをコピーして必要な変更を適用します。

```csharp
private static void CopyHeadersFootersFromPreviousSection(Section section)
{
    Section previousSection = (Section)section.PreviousSibling;
    if (previousSection == null) return;

    section.HeadersFooters.Clear();

    foreach (HeaderFooter headerFooter in previousSection.HeadersFooters)
    {
        section.HeadersFooters.Add(headerFooter.Clone(true));
    }
}
```

## 結論

以下の手順に従うことで、Aspose.Words for .NET を使用して Word 文書にヘッダーとフッターを効果的に追加およびカスタマイズできます。これにより、文書の見栄えとプロフェッショナルな印象が向上し、読みやすく魅力的な文書になります。

## よくある質問

### Aspose.Words for .NET とは何ですか?

Aspose.Words for .NET は、開発者が .NET アプリケーション内でプログラムによって Word 文書を作成、編集、変換できるようにするライブラリです。

### ヘッダーやフッターに画像を追加できますか?

はい、ヘッダーやフッターに画像を簡単に追加できます。 `DocumentBuilder.InsertImage` 方法。

### 最初のページに異なるヘッダーとフッターを設定するにはどうすればよいですか?

最初のページに異なるヘッダーとフッターを設定するには、 `DifferentFirstPageHeaderFooter` の財産 `PageSetup` クラス。

### Aspose.Words に関する詳細なドキュメントはどこで入手できますか?

包括的なドキュメントは以下でご覧いただけます。 [Aspose.Words API ドキュメントページ](https://reference。aspose.com/words/net/).

### Aspose.Words のサポートはありますか?

はい、Asposeはサポートを提供しています [サポートフォーラム](https://forum。aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}