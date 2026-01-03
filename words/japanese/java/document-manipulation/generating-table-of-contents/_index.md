---
date: 2026-01-03
description: Aspose.Words for Java を使用して目次を挿入しながらページ番号を調整する方法を学びましょう。目次のスタイルをカスタマイズし、手軽に文書を作成できます。
linktitle: Generating Table of Contents
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Javaでページ番号を調整し、目次を生成する
url: /ja/java/document-manipulation/generating-table-of-contents/
weight: 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でページ番号を調整し、目次を生成する

このチュートリアルでは、Aspose.Words for Java を使用して **ページ番号を調整** し、**目次 (TOC) を挿入** する方法を学びます。構造化された目次は長い文書のナビゲーションを容易にし、ページ番号の配置を微調整することで、読者にプロフェッショナルな体験を提供できます。ドキュメントの作成、目次スタイルのカスタマイズ、タブストップの調整方法を順に解説します。

## クイック回答
- **「ページ番号を調整する」とは何ですか？** 目次内のページ番号を揃えるタブストップを変更することです。  
- **目次を自動的に挿入できますか？** はい – `FieldToc` クラスを使用します。  
- **コード実行にライセンスは必要ですか？** 開発段階は無料トライアルで動作しますが、本番環境ではライセンスが必要です。  
- **対応している Aspose のバージョンは？** 最新の Aspose.Words for Java リリースで動作します。  
- **目次スタイルのカスタマイズは可能ですか？** もちろんです – フォントや太字などを変更できます。

## Aspose.Words の目次とは？
目次は、文書内の見出しスタイル（例: Heading 1、Heading 2）をスキャンし、ページ番号付きのエントリ一覧を生成するフィールドです。Aspose.Words では、このフィールドをプログラムから挿入でき、外観を完全に制御できます。

## なぜ目次のページ番号を調整するのか？
タブストップを調整することで、ページ番号の表示位置を正確にコントロールでき、以下のようなメリットがあります。

- 列揃えされたクリーンなレイアウトを維持できる。  
- 社内のスタイルガイドに合わせられる。  
- 印刷物・デジタル文書の可読性が向上する。

## 前提条件
- プロジェクトに Aspose.Words for Java を追加済み（Maven/Gradle）。  
- Java の基本構文に慣れていること。

## 手順ガイド

### 手順 1: 新しいドキュメントを作成
まず、コンテンツと目次を保持する空の `Document` オブジェクトをインスタンス化します。

```java
Document doc = new Document();
```

### 手順 2: 目次スタイルをカスタマイズ
各目次レベルの外観を変更できます。この例では、1 番目のレベルのエントリを太字にしています。これは一般的な要望です。

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

### 手順 3: ドキュメントにコンテンツを追加
見出し（例: `Heading1`、`Heading2`）や通常の段落を挿入します。目次フィールドは後でこれらの見出しを自動的に取得します。*(コードは省略 – 目的は目次生成にあります。)*

### 手順 4: 目次フィールドを挿入
目次は通常、文書の冒頭に配置します。

```java
// Insert a TOC field at the desired location in your document.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

### 手順 5: ドキュメントを保存
ドキュメントをディスクに永続化します。DOCX、PDF、HTML など、サポートされている任意の形式を選択できます。

```java
doc.save("your_output_path_here");
```

## 目次のタブストップをカスタマイズ (ページ番号の調整)
デフォルトのタブストップが期待通りにページ番号を揃えない場合、すべての目次段落を走査してタブ位置を変更できます。

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Get the first tab used in this paragraph, which aligns the page numbers.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Remove the old tab.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // Insert a new tab at a modified position (e.g., 50 units to the left).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

これで目次エントリはページ番号が正確に配置され、文書が洗練された印象になります。

## よくある問題とヒント
- **目次に見出しが表示されない:** 見出しが組み込みスタイル (`Heading1`、`Heading2` など) を使用しているか、カスタムスタイルを目次レベルにマッピングしてください。  
- **タブストップが適用されない:** 該当段落が目次スタイル (`TOC_1`‑`TOC_9`) に属しているか確認してください。  
- **大容量文書でのパフォーマンス:** 目次挿入後に `doc.updateFields()` を呼び出し、エントリを一括で更新すると効率的です。

## FAQ

**Q: 目次エントリの書式を変更するには？**  
A: `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`（*X* はレベル 1‑9）でスタイルを取得し、フォントや色、段落設定を変更します。

**Q: 目次にレベルを追加するには？**  
A: `FieldToc` のスイッチ `\o "1-3"`（例）を拡張して追加の見出しレベルを含め、対応する `TOC_X` スタイルも調整します。

**Q: 特定の目次エントリだけタブ位置を変えられる？**  
A: はい – 「タブストップのカスタマイズ」セクションのように段落を走査し、個別にタブストップを変更できます。

**Q: PDF 出力で目次を生成できる？**  
A: 可能です。目次生成後に `doc.save("output.pdf")` とすれば、フィールドは自動的に PDF にレンダリングされます。

**Q: `updateFields()` を手動で呼ぶ必要がある？**  
A: `FieldToc` を挿入すると保存時に自動更新されますが、デバッグ時に即座に結果を確認したい場合は `doc.updateFields()` を呼び出すと便利です。

## 結論
Aspose.Words for Java を使って **ページ番号の調整**、**目次の挿入**、そして **目次スタイルのカスタマイズ** 方法を学びました。これらのテクニックにより、どんな出版基準にも合致した、クリーンでナビゲーションしやすいプロフェッショナル文書を作成できます。

---  

**最終更新日:** 2026-01-03  
**テスト環境:** Aspose.Words for Java（最新リリース）  
**作者:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}