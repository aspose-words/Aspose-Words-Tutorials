---
"description": "Aspose.Words for Java を使用して目次（TOC）を生成およびカスタマイズする方法を学びましょう。整理されたプロフェッショナルなドキュメントを簡単に作成できます。"
"linktitle": "目次を生成しています"
"second_title": "Aspose.Words Java ドキュメント処理 API"
"title": "Aspose.Words for Java で目次を生成する"
"url": "/ja/java/document-manipulation/generating-table-of-contents/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java で目次を生成する


## Aspose.Words for Java での目次生成の概要

このチュートリアルでは、Aspose.Words for Java を使用して目次（TOC）を作成する手順を詳しく説明します。TOCは、整理されたドキュメントを作成する上で不可欠な機能です。TOCの外観とレイアウトをカスタマイズする方法についても説明します。

## 前提条件

始める前に、Aspose.Words for Java が Java プロジェクトにインストールされ、設定されていることを確認してください。

## ステップ1：新しいドキュメントを作成する

まず、作業する新しいドキュメントを作成しましょう。

```java
Document doc = new Document();
```

## ステップ2: TOCスタイルをカスタマイズする

目次の外観をカスタマイズするには、関連するスタイルを変更します。この例では、第1レベルの目次エントリを太字にします。

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

## ステップ3: ドキュメントにコンテンツを追加する

ドキュメントにコンテンツを追加できます。このコンテンツは目次の生成に使用されます。

## ステップ4: TOCを生成する

目次を生成するには、ドキュメント内の任意の場所に目次フィールドを挿入します。このフィールドは、ドキュメント内の見出しとスタイルに基づいて自動的に入力されます。

```java
// ドキュメント内の目的の場所に TOC フィールドを挿入します。
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

## ステップ5: ドキュメントを保存する

最後に、目次とともにドキュメントを保存します。

```java
doc.save("your_output_path_here");
```

## TOC のタブストップのカスタマイズ

目次のタブ位置をカスタマイズして、ページ番号のレイアウトを制御することもできます。タブ位置の変更方法は次のとおりです。

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // この段落で使用されている最初のタブを取得し、ページ番号を揃えます。
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // 古いタブを削除します。
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // 変更した位置（たとえば、50 ユニット左）に新しいタブを挿入します。
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

これで、ページ番号の位置合わせのためにタブ ストップが調整された、カスタマイズされた目次がドキュメントに作成されました。


## 結論

このチュートリアルでは、Word文書を扱うための強力なライブラリであるAspose.Words for Javaを使用して、目次（TOC）を作成する方法を解説しました。長大な文書を整理し、操作するには、適切に構造化された目次が不可欠です。Aspose.Wordsは、TOCを簡単に作成およびカスタマイズするためのツールを提供します。

## よくある質問

### TOC エントリの書式を変更するにはどうすればよいですか?

TOCレベルに関連付けられたスタイルを変更するには、 `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`ここで、X は TOC レベルです。

### TOC にさらにレベルを追加するにはどうすればよいですか?

TOC にさらに多くのレベルを含めるには、TOC フィールドを変更し、必要なレベル数を指定します。

### 特定の TOC エントリのタブ ストップの位置を変更できますか?

はい、上記のコード例に示されているように、段落を反復処理し、それに応じてタブ ストップを変更することで、特定の TOC エントリのタブ ストップの位置を変更できます。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}