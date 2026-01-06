---
date: 2026-01-06
description: Aspose.Words for Java を使用して Word 文書からフッターを削除する方法や、セクション区切りやページ区切り、その他の削除方法を学びましょう。
linktitle: Removing Content from Documents
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java を使用して Word 文書からフッターを削除する方法
url: /ja/java/document-manipulation/removing-content-from-documents/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java を使用して Word ドキュメントからフッターを削除する方法

## Introduction to Aspose.Words for Java

このチュートリアルでは、Aspose.Words for Java を使って **Word ファイルからフッターを削除する方法** をプログラムで実装する方法を紹介します。生成されたレポートのクリーンアップ、機密情報の除去、テンプレートの整理など、ページブレーク、セクションブレーク、フッター、目次といった一般的なコンテンツ削除シナリオを順に解説します。さっそく始めましょう！

## Quick Answers
- **フッターだけを削除して他のコンテンツに影響させない方法はありますか？** はい、API でフッターノードだけを対象にできます。
- **これらのサンプルを実行するのにライセンスは必要ですか？** 開発段階は無料トライアルで動作します。製品環境ではライセンスが必要です。
- **対応している Word フォーマットは何ですか？** DOC、DOCX、DOCM、そして OOXML ベースの形式です。
- **コードは Java 8 以降で動作しますか？** もちろんです。ライブラリはバージョン 8 以降の Java と互換性があります。
- **セクションブレークはどうやって削除しますか？** 以下の「セクションブレークの削除方法」セクションをご参照ください。

## What is “remove footers from Word”?

Word ドキュメントからフッターを削除するとは、各ページ下部に表示される `HeaderFooter` ノードを削除することを指します。ヘッダーのみのレイアウトにしたい場合や、フッターに機密情報が含まれていて共有できない場合に頻繁に行われる操作です。

## Why use Aspose.Words for Java for this task?

Aspose.Words は DOCX ファイル形式の複雑さを抽象化した高レベルのオブジェクトモデルを提供します。サーバー上に Microsoft Word をインストールせずに、数行の Java コードで段落、ラン、セクション、フッターを操作できます。

## Prerequisites
- Java Development Kit (JDK) 8 以上。
- Aspose.Words for Java ライブラリ（Aspose の公式サイトからダウンロード）。
- 既知のディレクトリに配置したサンプル Word ドキュメント（`Document.docx`）。

## Removing Page Breaks

ページブレークはページ割り付けを制御しますが、削除したいケースもあります。以下のスニペットはすべての段落を走査し、`PageBreakBefore` フラグをクリアし、明示的なページブレーク文字を除去します。

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
NodeCollection paragraphs = doc.getChildNodes(NodeType.PARAGRAPH, true);
for (Paragraph para : (Iterable<Paragraph>) paragraphs) {
    if (para.getParagraphFormat().getPageBreakBefore()) {
        para.getParagraphFormat().setPageBreakBefore(false);
    }
    for (Run run : para.getRuns()) {
        if (run.getText().contains(ControlChar.PAGE_BREAK)) {
            run.setText(run.getText().replace(ControlChar.PAGE_BREAK, ""));
        }
    }
}
doc.save("Your Directory Path" + "RemoveContent.RemovePageBreaks.docx");
```

*Pro tip:* フッターを削除する前に実行すると、単一ページレイアウトにしやすくなります。

## How to delete section breaks

セクションブレークはドキュメントを独立したセクションに分割し、各セクションが独自のヘッダー、フッター、ページ設定を持ちます。**セクションブレークを削除** してセクションを統合するには、逆順に走査し、各前方セクションのコンテンツを最後のセクションに前置きしてから、空になったセクションを削除します。

```java
for (int i = doc.getSections().getCount() - 2; i >= 0; i--) {
    doc.getLastSection().prependContent(doc.getSections().get(i));
    doc.getSections().get(i).remove();
}
```

この方法はコンテンツをすべて保持しながら、構造上のブレークだけを取り除きます。

## Removing Footers (Primary Goal: remove footers from Word)

フッターにはページ番号、日付、機密メモなどが含まれることが多いです。以下のコードは **すべてのフッタータイプ**（最初のページ、プライマリ、偶数ページ・奇数ページ）を各セクションから削除します。

```java
Document doc = new Document("Your Directory Path" + "Header and footer types.docx");
for (Section section : doc.getSections()) {
    HeaderFooter footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_FIRST);
    footer.remove();
    footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
    footer.remove();
    footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_EVEN);
    footer.remove();
}
doc.save("Your Directory Path" + "RemoveContent.RemoveFooters.docx");
```

このスニペットを実行すると、結果のドキュメントには **フッターが一切存在しない** ことになり、 “remove footers from Word” の主目的が達成されます。

## Removing Table of Contents

目次（TOC）はフィールドとして保存されています。目次を削除するには、インデックスで TOC フィールドを特定し、関連ノードを除去します。

```java
Document doc = new Document("Your Directory Path" + "Table of contents.docx");
removeTableOfContents(doc, 0);
doc.save("Your Directory Path" + "RemoveContent.RemoveToc.doc");
```

*(`removeTableOfContents` メソッドは Aspose.Words のサンプルに含まれており、指定した TOC ノードを削除します。)*

## Common Issues & Troubleshooting

| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| フッターがコード実行後も残る | アクセスしていない **header/footer** ペアが存在する（例: `FOOTER_FIRST` が欠落） | すべての `HeaderFooterType` をループするか、`remove()` 呼び出し前に `null` チェックを行う。 |
| セクションブレーク削除後にページレイアウトが予期せず変わる | セクション固有のページ設定（余白、向き）が失われた | 削除前に対象セクションへ設定をコピーしてから削除する。 |
| `ControlChar.PAGE_BREAK` が除去されない | ドキュメントがページブレーク文字ではなく **セクションブレーク** を使用している | まず「セクションブレークの削除方法」を実行する。 |

## Frequently Asked Questions

**Q: 特定のフッターだけ（例: 最初のページのフッター）を削除したいですか？**  
A: はい。`FOOTER_FIRST` などのタイプでフッターを取得し、そのインスタンスに対して `remove()` を呼び出すだけです。

**Q: コンテンツをマージせずにセクションブレークだけを削除する方法はありますか？**  
A: コンテンツを保持する必要がなければ `Section` ノードを直接削除できます。ただし、そのセクションに紐付くヘッダー/フッターも同時に失われます。

**Q: 目次が存在するかどうかをプログラムで検出してから削除することは可能ですか？**  
A: `doc.getRange().getFields()` を使用し、`FieldType.FIELD_TABLE_OF_CONTENTS` のフィールドがあるか確認してください。

**Q: 暗号化された Word ファイルからフッターを削除できますか？**  
A: はい。パスワード付きでドキュメントを開くだけです: `new Document(path, new LoadOptions(password))`。

**Q: フッターを削除するとページ番号付けに影響しますか？**  
A: フッター自体にページ番号フィールドが含まれていない限り、ページ番号は変わりません。ページ番号を再付与したい場合は、ページ番号フィールドを更新してください。

## Conclusion

Aspose.Words for Java を使用して **Word ドキュメントからフッターを削除** する方法と、ページブレーク削除、**セクションブレークの削除方法**、目次の除去といった関連タスクをすべて網羅しました。これらのコードスニペットを活用すれば、アプリケーションの要件に合わせたクリーンでプロフェッショナルな文書を生成できます。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Last Updated:** 2026-01-06  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

---