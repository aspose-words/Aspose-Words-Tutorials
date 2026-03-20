---
date: '2026-03-20'
description: Aspose.Words for Java を使用して、入れ子ブックマークの作成方法とブックマーク付き PDF の生成方法を学び、可読性とナビゲーションを向上させます。
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: Aspose.Words JavaでPDFに階層ブックマークを作成する
url: /ja/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# PDFでAspose.Words Javaを使用してネストされたブックマークを作成する

## はじめに
Word 文書を PDF に変換した後、ブックマークの整理に苦労したことがある方は多いでしょう。このチュートリアルでは **ネストされたブックマークを作成** し、**ブックマーク付き PDF を生成** して簡単にナビゲートできるようにする方法を学びます。Aspose.Words の設定、ブックマーク階層の構築、アウトラインレベルの割り当て、そして最終的にクリーンな PDF をエクスポートする手順を順に解説します。

**学べること**
- Aspose.Words for Java のセットアップ方法
- Word 文書内で **ネストされたブックマークを作成** する方法
- PDF のナビゲーションを明確にするためのブックマークアウトラインレベルの設定方法
- 定義した階層を反映した **ブックマーク付き PDF を生成** する方法

### クイック回答
- **ドキュメント作成の主要クラスは何ですか？** `DocumentBuilder`
- **ブックマークを追加するメソッドはどれですか？** `startBookmark(String name)`
- **ブックマークにアウトラインレベルを設定するには？** `outlineLevels.add(name, level)`
- **本番環境でライセンスは必要ですか？** はい、購入したライセンスで全機能が有効になります。
- **Maven や Gradle でも使用できますか？** もちろんです。両方ともサポートされています。

### 前提条件
作業を始める前に以下を用意してください。
- **Aspose.Words for Java**（バージョン 25.3 以降）。  
- JDK がインストールされた環境と、IntelliJ IDEA または Eclipse などの IDE。  
- 基本的な Java の知識と、Maven または Gradle の基本操作に慣れていること。

## 「ネストされたブックマークを作成する」とは？
ネストされたブックマークを作成するとは、あるブックマークの内部に別のブックマークを配置し、親子関係の階層を構築することです。文書を PDF として保存すると、これらの関係が PDF のブックマークパネルに折りたたみ可能なエントリとして表示され、大規模な文書でも簡単に探索できるようになります。

## PDF にブックマークを生成する際にアウトラインレベルを使用する理由は？
アウトラインレベルは、PDF ビューアでのブックマークの視覚的階層を定義します。レベル 1 のブックマークは最上位エントリとして表示され、レベル 2 はその子として表示されます。適切なアウトラインレベルを設定することで、フラットなブックマークリストが構造化された目次に変わり、特に法的契約書、技術報告書、電子書籍などで有用です。

## Aspose.Words のセットアップ
Maven または Gradle を使用してライブラリをプロジェクトに追加します。

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

### ライセンス取得
Aspose.Words は商用製品ですが、無料トライアルで始められます。

1. **無料トライアル** – 完全機能をテストするには、[Aspose のリリースページ](https://releases.aspose.com/words/java/)からダウンロードしてください。  
2. **一時ライセンス** – 短期評価用に、[Aspose の一時ライセンスページ](https://purchase.aspose.com/temporary-license/)から取得できます。  
3. **購入** – 永続ライセンスは、[Aspose の購入ポータル](https://purchase.aspose.com/buy)から入手してください。

取得した `.lic` ファイルをコード内で読み込むことで、すべての機能が有効になります。

## 実装ガイド
以下は、ドキュメント作成、ネストされたブックマークの追加、アウトラインレベルの設定、PDF への保存をステップバイステップで示したものです。

### 手順 1: ドキュメントとビルダーの初期化
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
空の Word 文書と、テキストやブックマークの挿入に使用するビルダーオブジェクトを作成します。

### 手順 2: 最初の（親）ブックマークを作成
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```
`startBookmark` 呼び出しで **Bookmark 1** という名前の新しいブックマークが開始されます。この呼び出し以降に記述した内容は、ブックマークを閉じるまですべて **Bookmark 1** に属します。

### 手順 3: 最初のブックマーク内に 2 番目のブックマークをネスト
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```
このブックマークは **最初のブックマークの後に開始** され、**最初のブックマークの前に閉じる** ため、**Bookmark 1** の子ブックマーク（**Bookmark 2**）となります。

### 手順 4: 親ブックマークを閉じる
```java
builder.endBookmark("Bookmark 1");
```
これで階層は次のようになります。

- Bookmark 1（レベル 1）  
  - Bookmark 2（レベル 2）

### 手順 5: 独立した 3 番目のブックマークを追加
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```
このブックマークは最上位に配置され、最初の 2 つとは別の階層になります。

### 手順 6: PDF エクスポート用にアウトラインレベルを設定
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
`PdfSaveOptions` オブジェクトを使用して、最終的な PDF でブックマークがどのように表示されるかを制御します。

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 1);
```
ここでは、最上位ブックマークにレベル 1、ネストされたブックマークにレベル 2 を割り当てています。

### 手順 7: ドキュメントを PDF として保存
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```
生成された PDF は、定義した階層を反映したクリーンで折りたたみ可能なブックマークパネルを表示します。

## よくある問題と解決策
- **ブックマークが表示されない** – すべての `startBookmark` には対応する `endBookmark` が必要です。1 つでも欠けると PDF でブックマークが無視されます。  
- **アウトラインレベルが正しく適用されない** – `outlineLevels.add` に渡す名前を再確認してください。タイプミスがあるとレベルが適用されません。  
- **大容量文書** – 非常に大きなファイルの場合、`doc.removeMacros()` を呼び出すか、未使用のスタイルをクリアして PDF サイズを抑えてください。

## 実用例
1. **法的契約書** – 条項やサブ条項間を素早くジャンプ。  
2. **技術報告書** – セクション、表、図をスクロールせずにナビゲート。  
3. **e‑ラーニング教材** – 学習者向けにクリック可能な目次を提供。

## パフォーマンスのヒント
- 保存前に未使用のリソース（画像、スタイル）を削除。  
- 100 MB 超の PDF を処理する場合は、ストリーミング API を使用してメモリ使用量を抑える。

## 結論
これで **ネストされたブックマークの作成**、アウトラインレベルの割り当て、そして **ブックマーク付き PDF の生成** ができるようになりました。階層をさらに深くしたり、ドキュメント生成パイプラインに組み込んで自動化を推し進めてみてください。

## FAQ

**Q: Aspose.Words for Java のインストール方法は？**  
A: 上記の Maven または Gradle 依存関係を追加し、実行時にライセンスファイルをロードします。

**Q: アウトラインレベルを設定せずにブックマークは使用できますか？**  
A: はい、可能ですが PDF はフラットなリストとして表示され、複雑な文書ではナビゲートが困難になります。

**Q: ブックマークのネスト深さに制限はありますか？**  
A: 技術的な上限はありませんが、可読性を保つために 3〜4 レベル程度に抑えることを推奨します。

**Q: 非常に大きな文書はどのように処理されますか？**  
A: Aspose はコンテンツをストリーミングし、メモリ管理ユーティリティを提供します。ただし、未使用要素は削除しておくと安全です。

**Q: PDF 作成後にブックマークを編集できますか？**  
A: もちろんです。Aspose.PDF for Java を使用すれば、ブックマークのタイトル、リンク先、アウトラインレベルを生成後に変更できます。

## リソース
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

**Last Updated:** 2026-03-20  
**Tested With:** Aspose.Words for Java 25.3  
**Author:** Aspose