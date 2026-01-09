---
date: 2026-01-09
description: Aspose.Words for Java を使用して、書式を保持し、ヘッダーとフッターをリンクさせるなど、ドキュメントの結合方法を学びましょう。
linktitle: Joining and Appending Documents
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java を使用したドキュメントの結合方法
url: /ja/java/document-manipulation/joining-and-appending-documents/
weight: 30
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java を使用したドキュメントの結合方法

Word ファイルをプログラムで結合するのは頭痛の種です—特にスタイルやページ番号、ヘッダー/フッターをそのまま保持する必要がある場合はなおさらです。このチュートリアルでは Aspose.Words for Java ライブラリを使用して **ドキュメントの結合方法** をステップバイステップで学びます。シンプルな追加、詳細なインポートオプション、異なるページ設定の処理、そして実際のシナリオで **書式を保持した結合** を実現するコツをカバーします。

## クイック回答
- **Word ドキュメントを結合する最も簡単な方法は何ですか？** `Document.appendDocument` と `ImportFormatMode.KEEP_SOURCE_FORMATTING` を使用します。  
- **各ソースファイルの元のスタイルを保持できますか？** はい—`ImportFormatMode.USE_DESTINATION_STYLES` を設定するか、Smart Style Behavior を有効にします。  
- **結合後にページ番号を正しく保つにはどうすればよいですか？** `NUMPAGES` フィールドをページ参照に変換し、`updatePageLayout()` を呼び出します。  
- **ヘッダーとフッターは自動的にリンクされたままですか？** `linkToPrevious(true/false)` でリンクまたはリンク解除できます。  
- **開始前に何が必要ですか？** プロジェクトに Aspose.Words for Java を追加し、ソースの `.docx` ファイルを用意してください。

## Aspose.Words for Java におけるドキュメントの結合と追加の概要

このチュートリアルでは、Aspose.Words for Java ライブラリを使用してドキュメントを結合および追加する方法を探ります。書式と構造を保持しながら複数のドキュメントをシームレスに結合する方法を学びます。

## 前提条件

開始する前に、Java プロジェクトに Aspose.Words for Java API が設定されていることを確認してください。

## ドキュメント結合オプション

### シンプルな追加

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### インポート書式オプション付きの追加

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### 空白ドキュメントへの追加

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### ページ番号変換付きの追加

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // Convert NUMPAGES fields
dstDoc.updatePageLayout(); // Update page layout for correct numbering
```

## 異なるページ設定の処理

異なるページ設定のドキュメントを追加する場合：

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// Ensure page setup settings match the destination document
```

## 異なるスタイルのドキュメントの結合

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## スマートスタイル動作

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setSmartStyleBehavior(true);
builder.insertDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

## DocumentBuilder を使用したドキュメントの挿入

```java
DocumentBuilder builder = new DocumentBuilder(dstDoc);
builder.insertDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## ソースの番号付けを保持する

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## テキストボックスの処理

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setIgnoreTextBoxes(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## ヘッダーとフッターの管理

### ヘッダーとフッターのリンク

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### ヘッダーとフッターのリンク解除

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## “merge word documents java” プロジェクトでこれが重要な理由

**merge word documents java** スタイルでドキュメントを結合する必要がある場合、各ファイルの外観と感覚を保持することは、法務、出版、レポート作業フローで極めて重要です。上記の手法を使用すると、以下が保証されます：

* 各ソースのスタイルがそのまま保持されます（または選択に応じて統一されます）。
* ページ番号とセクション区切りが予測可能に動作します。
* ヘッダーとフッターは、1 行のコードでリンクまたは独立させることができます。

## よくある落とし穴とヒント

| 問題 | 発生理由 | 対処方法 |
|-------|----------------|------------|
| 結合後に番号付けが失われる | `NUMPAGES` フィールドが元のセクションを指したまま | `convertNumPageFieldsToPageRef` と `updatePageLayout()` を呼び出す |
| スタイルの衝突 | 競合するスタイルで `KEEP_SOURCE_FORMATTING` を使用 | `USE_DESTINATION_STYLES` に切り替えるか、Smart Style Behavior を有効にする |
| 空白ページが出現する | `SectionStart` の値が異なる | 追加前にソースセクションの `SectionStart.CONTINUOUS` を設定する |

## よくある質問

**Q: 異なるスタイルのドキュメントをシームレスに結合するにはどうすればよいですか？**  
**A:** 追加時に `ImportFormatMode.USE_DESTINATION_STYLES` を使用するか、`SmartStyleBehavior` を有効にしてスマートに結合します。

**Q: ドキュメントを追加する際にページ番号を保持できますか？**  
**A:** はい、`convertNumPageFieldsToPageRef` で `NUMPAGES` フィールドをページ参照に変換し、`updatePageLayout()` を呼び出します。

**Q: Smart Style Behavior とは何ですか？**  
**A:** 可能な場合にソーススタイルを宛先スタイルに自動的にマッピングし、結合されたコンテンツ全体で一貫した外観を保つ機能です。

**Q: ドキュメントを追加する際にテキストボックスをどう処理すればよいですか？**  
**A:** `importFormatOptions.setIgnoreTextBoxes(false)` を設定して、結合時にテキストボックスを保持します。

**Q: ドキュメント間でヘッダーとフッターをリンクまたはリンク解除したい場合はどうすればよいですか？**  
**A:** `appendDocument` を呼び出す前に、`linkToPrevious(true)` でリンク、`linkToPrevious(false)` で別々に保ちます。

## 結論

Aspose.Words for Java は、**ドキュメントの結合方法** に柔軟かつ強力なツールを提供します。正確な書式を維持したり、さまざまなページ設定に対応したり、ヘッダー/フッターのリンクを制御したりする必要がある場合でも、上記のコードスニペットを試して独自のドキュメント処理ワークフローに合わせてください。これにより、**merge word documents java** スタイルで自信を持って結合できるようになります。

---

**Last Updated:** 2026-01-09  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}