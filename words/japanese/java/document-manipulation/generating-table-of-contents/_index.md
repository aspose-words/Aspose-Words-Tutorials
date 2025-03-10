---
title: Aspose.Words for Java で目次を生成する
linktitle: 目次の生成
second_title: Aspose.Words Java ドキュメント処理 API
description: Aspose.Words for Java を使用して目次 (TOC) を生成およびカスタマイズする方法を学びます。整理されたプロフェッショナルなドキュメントを簡単に作成します。
weight: 21
url: /ja/java/document-manipulation/generating-table-of-contents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java で目次を生成する


## Aspose.Words for Java での目次生成の概要

このチュートリアルでは、Aspose.Words for Java を使用して目次 (TOC) を生成する手順を説明します。TOC は、整理されたドキュメントを作成するための重要な機能です。TOC の外観とレイアウトをカスタマイズする方法について説明します。

## 前提条件

始める前に、Aspose.Words for Java がインストールされ、Java プロジェクトに設定されていることを確認してください。

## ステップ1: 新しいドキュメントを作成する

まず、作業する新しいドキュメントを作成しましょう。

```java
Document doc = new Document();
```

## ステップ2: TOCスタイルをカスタマイズする

TOC の外観をカスタマイズするには、それに関連付けられているスタイルを変更します。この例では、第 1 レベルの TOC エントリを太字にします。

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

## ステップ3: ドキュメントにコンテンツを追加する

ドキュメントにコンテンツを追加できます。このコンテンツは目次の生成に使用されます。

## ステップ4: TOCを生成する

TOC を生成するには、ドキュメント内の目的の場所に TOC フィールドを挿入します。このフィールドは、ドキュメント内の見出しとスタイルに基づいて自動的に入力されます。

```java
//ドキュメント内の目的の場所に TOC フィールドを挿入します。
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

## ステップ5: ドキュメントを保存する

最後に、目次とともにドキュメントを保存します。

```java
doc.save("your_output_path_here");
```

## TOC のタブ ストップのカスタマイズ

また、目次のタブ ストップをカスタマイズして、ページ番号のレイアウトを制御することもできます。タブ ストップを変更する方法は次のとおりです。

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        //この段落で使用されている最初のタブを取得し、ページ番号を揃えます。
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        //古いタブを削除します。
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        //変更した位置（たとえば、50 単位左）に新しいタブを挿入します。
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

これで、ページ番号の位置合わせのためにタブ ストップが調整された、カスタマイズされた目次がドキュメントに作成されました。


## 結論

このチュートリアルでは、Word 文書を操作するための強力なライブラリである Aspose.Words for Java を使用して目次 (TOC) を生成する方法について説明しました。長い文書を整理してナビゲートするには、適切に構造化された TOC が不可欠です。Aspose.Words には、TOC を簡単に作成およびカスタマイズするためのツールが用意されています。

## よくある質問

### TOC エントリの書式を変更するにはどうすればよいですか?

 TOCレベルに関連付けられたスタイルを変更するには、`doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`ここで、X は TOC レベルです。

### TOC にさらにレベルを追加するにはどうすればよいですか?

TOC にさらに多くのレベルを含めるには、TOC フィールドを変更し、必要なレベル数を指定します。

### 特定の TOC エントリのタブ ストップの位置を変更できますか?

はい、上記のコード例に示すように、段落を反復処理し、それに応じてタブ ストップを変更することで、特定の TOC エントリのタブ ストップの位置を変更できます。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
