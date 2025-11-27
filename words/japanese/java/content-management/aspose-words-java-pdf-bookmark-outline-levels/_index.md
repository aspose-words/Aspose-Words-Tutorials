---
date: '2025-11-27'
description: Aspose.Words を使用して Java でブックマークの作成、ブックマーク付き PDF の生成、Word から PDF への変換方法を学びます。このガイドでは、入れ子になったブックマークとアウトラインレベルについて説明します。
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
language: ja
title: Aspose.Words Java を使用して PDF にブックマークを作成し、アウトラインレベルを設定する方法
url: /java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java を使用して PDF にブックマークを作成し、アウトラインレベルを設定する方法

## Introduction
Word 文書を PDF に変換する際に **ブックマークの作成方法** で整理がうまくいかないとお悩みの方へ。本チュートリアルでは、ブックマーク付き PDF を生成し、ブックマークを入れ子にし、アウトラインレベルを割り当てて最終的な PDF を簡単にナビゲートできるようにする手順をすべて解説します。最後まで読めば、**Word PDF Java** スタイルでクリーンなブックマーク階層を持つ PDF を任意の PDF ビューアで利用できるようになります。

### What You’ll Learn
- 開発環境に Aspose.Words for Java をセットアップする方法。  
- **ブックマークの作成方法** をプログラムで実装し、入れ子にする方法。  
- ブックマークのアウトラインレベルを設定し、文書構造を反映した PDF を生成する方法。  
- ブックマーク階層を保持したまま Word ファイルを PDF として保存する方法。

## Quick Answers
- **文書作成の主要クラスは何ですか？** `DocumentBuilder`。  
- **ブックマーク階層を制御するオプションはどれですか？** `PdfSaveOptions` 内の `BookmarksOutlineLevelCollection`。  
- **Maven または Gradle を使用できますか？** はい、以下に両方の例を示します。  
- **ライセンスは必要ですか？** テスト用に無料トライアルが利用可能です。製品版では永続ライセンスが必要です。  
- **大規模文書にもこの方法は適していますか？** はい。ただし、メモリ最適化手法（例：未使用リソースの削除）を検討してください。

### Prerequisites
開始する前に、以下を確認してください。

- **ライブラリと依存関係** – Aspose.Words for Java（バージョン 25.3 以降）。  
- **環境** – JDK 8 以上、IntelliJ IDEA または Eclipse などの IDE。  
- **基本知識** – Java のプログラミング基礎と Maven または Gradle の基本操作。

## Setting Up Aspose.Words
まず、プロジェクトに必要な依存関係を追加します。以下は Maven と Gradle で Aspose.Words を追加する方法です。

**Maven:**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### License Acquisition
Aspose.Words は商用ライブラリですが、無料トライアルから始められます。

1. **Free Trial** – [Aspose リリースページ](https://releases.aspose.com/words/java/)からダウンロード。  
2. **Temporary License** – 短期キーが必要な場合は[temporary‑license ページ](https://purchase.aspose.com/temporary-license/)で取得。  
3. **Full License** – 本番環境で使用する場合は[Aspose 購入ポータル](https://purchase.aspose.com/buy)で購入。

ライセンスファイルを取得したら、アプリケーション起動時にロードしてすべての機能を有効化してください。

## How to Create Bookmarks in PDFs with Aspose.Words Java
以下では実装手順を番号付きで分かりやすく解説します。各ステップには簡単な説明と、元のコードブロック（変更なし）を示します。

### Step 1: Initialize a Document and a DocumentBuilder
新しい `Document` インスタンスと、コンテンツやブックマークを挿入できる `DocumentBuilder` を作成します。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Step 2: Insert the First (Parent) Bookmark
後で子ブックマークを含めるトップレベルのブックマークを作成します。

```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

### Step 3: Nest a Child Bookmark Inside the Parent
最初のブックマークの内部に 2 番目のブックマークを追加し、入れ子構造を示します。

```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

### Step 4: Close the Parent Bookmark
入れ子コンテンツの後で外側のブックマークを閉じます。

```java
builder.endBookmark("Bookmark 1");
```

### Step 5: Add an Independent Third Bookmark
入れ子にしない独立したブックマークを追加することも可能です。

```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

## Configuring Bookmark Outline Levels
ブックマークが配置されたら、PDF のアウトライン（左側ナビゲーションペイン）での表示方法を Aspose.Words に指示します。

### Step 6: Prepare PdfSaveOptions
`PdfSaveOptions` を使用してアウトライン設定にアクセスします。

```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

### Step 7: Assign Hierarchy Levels
各ブックマークに整数のレベルを割り当てます。数値が小さいほど階層上位になります。

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

### Step 8: Save the Document as a PDF
最後に、ブックマークアウトラインを保持したまま Word 文書を PDF にエクスポートします。

```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## Why Use This Approach to Generate PDF with Bookmarks?
- **Professional Navigation** – 読者はセクションへ直接ジャンプでき、大規模レポートや法的契約書の使い勝手が向上します。  
- **Full Control** – 階層は PDF ビューアではなく自分で決定できます。  
- **Cross‑Platform** – 純粋な Java で動作するため、Windows、Linux、macOS で同じ結果が得られます。  

## Common Issues and Solutions
| Symptom | Likely Cause | Fix |
|---|---|---|
| Missing bookmarks in PDF | `startBookmark` に対応する `endBookmark` がない | すべての `startBookmark` に対応する `endBookmark` があることを確認してください。 |
| Incorrect hierarchy | アウトラインレベルが順序どおりに設定されていない | 親ブックマークのレベル番号を子ブックマークより低く設定してください。 |
| License not applied | ドキュメント作成前にライセンスファイルがロードされていない | アプリケーション開始時に `License license = new License(); license.setLicense("Aspose.Words.lic");` を実行してライセンスをロードしてください。 |

## Practical Applications
1. **Legal Documents** – 条項、付録、添付書類を素早くナビゲート。  
2. **Financial Reports** – 損益計算書、貸借対照表、注記などのセクション間を簡単に移動。  
3. **E‑Learning Materials** – PDF アウトラインと一致した目次を提供。

## Performance Considerations
- **Memory Management** – 非常に大きな Word ファイルの場合、保存前に `doc.cleanup()` を呼び出すことを検討してください。  
- **Resource Optimization** – 未使用の画像やスタイルを削除して PDF サイズを小さく保ちます。

## Frequently Asked Questions

**Q: How do I install Aspose.Words for Java?**  
A: 前述の Maven または Gradle の依存関係を追加し、ライセンスファイルをクラスパスに配置して実行時にロードします。

**Q: Can I create bookmarks without setting outline levels?**  
A: はい、可能ですが PDF ビューアではフラットなリストとして表示され、複雑な文書ではナビゲーションが困難になります。

**Q: Is there a limit to how deep bookmarks can be nested?**  
A: 技術的な制限はありませんが、ほとんどの PDF ビューアは快適に 9 レベルまでサポートします。読者にとって論理的な階層を保つようにしてください。

**Q: How does Aspose handle very large Word files?**  
A: ライブラリはコンテンツをストリーミングし、`Document.optimizeResources()` などのメソッドでメモリ使用量を削減できます。

**Q: Can I edit the bookmarks after the PDF is generated?**  
A: もちろん可能です。Aspose.PDF for Java を使用すれば、既存の PDF に対してブックマークの追加、削除、名前変更が行えます。

## Resources
- [Aspose.Words Documentation](https://reference.aspose.com/words/java/)  
- [Download Latest Releases](https://releases.aspose.com/words/java/)  
- [Purchase a License](https://purchase.aspose.com/buy)  
- [Free Trial](https://releases.aspose.com/words/java/)  
- [Temporary License Application](https://purchase.aspose.com/temporary-license/)  
- [Aspose Support Forum](https://forum.aspose.com/c/words/10)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Last Updated:** 2025-11-27  
**Tested With:** Aspose.Words 25.3 for Java  
**Author:** Aspose