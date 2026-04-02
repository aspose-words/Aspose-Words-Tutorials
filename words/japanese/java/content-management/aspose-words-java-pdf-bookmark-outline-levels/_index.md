---
date: '2026-04-02'
description: Aspose.Words for Java を使用して、入れ子ブックマークの作成方法、ブックマークのアウトラインレベルの設定方法、Word
  文書を PDF として保存する方法を学びましょう。
keywords:
- create nested bookmarks
- how to set bookmark
- save word pdf bookmarks
title: Aspose.Words for Java を使用して PDF に入れ子ブックマークを作成し、アウトラインレベルを設定する
url: /ja/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java を使用して PDF で入れ子ブックマークを作成し、アウトラインレベルを設定する

## はじめに
Word ドキュメントを PDF に変換する際にブックマークの管理に苦労していますか？**このチュートリアルでは、入れ子ブックマークの作成方法**、アウトラインレベルの設定方法、そして Aspose.Words for Java を使用して結果をクリーンでナビゲート可能な PDF として保存する方法を示します。このガイドの最後までに、読者が必要なセクションへ直接ジャンプできるプロフェッショナルな PDF を手に入れることができます。

**学べること**
- プロジェクトに Aspose.Words for Java を設定する  
- Word ドキュメントで入れ子ブックマークを作成する  
- 明確な階層構造のためにブックマークのアウトラインレベルを設定する方法  
- 正しい構造で Word PDF ブックマークを保存する  

### クイック回答
- **ドキュメント作成の主なクラスは何ですか？** `DocumentBuilder`  
- **ブックマークのアウトラインレベルを追加するメソッドはどれですか？** `BookmarksOutlineLevels.add()`  
- **PDF をエクスポートするのにライセンスが必要ですか？** 本番環境ではライセンスが必要です。評価目的では無料トライアルで動作します。  
- **ブックマークを任意の深さに入れ子にできますか？** はい、ただしエンドユーザーが読みやすい階層に保ってください。  
- **必要な Aspose.Words のバージョンは何ですか？** バージョン 25.3 以降です。

## 「入れ子ブックマークの作成」とは？
入れ子ブックマークとは、他のブックマークの内部に配置されたブックマークで、親子階層を形成します。PDF ではブックマークパネルに展開可能な項目として表示され、読者は必要に応じてセクションを折りたたんだり展開したりできます。

## なぜブックマークのアウトラインレベルを設定するのか？
アウトラインレベルは PDF のブックマークパネルでの視覚的な入れ子順序を定義します。適切なレベル設定により、特に長大な法的契約書、技術レポート、または情報を迅速に探す必要がある電子書籍において、ナビゲーションが向上します。

## 前提条件
- **ライブラリと依存関係**: Aspose.Words for Java（バージョン 25.3 以降）。  
- **環境**: JDK 8 以上と IntelliJ IDEA や Eclipse などの IDE。  
- **知識**: 基本的な Java、Maven または Gradle の知識。  

### Aspose.Words の設定
Maven または Gradle を使用してライブラリをプロジェクトに追加します。

**Maven**  
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle**  
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### ライセンス取得
Aspose.Words は商用製品ですが、無料トライアルから始めることができます。

1. **無料トライアル** – 完全な機能をテストするために [Aspose のリリースページ](https://releases.aspose.com/words/java/) からダウンロードしてください。  
2. **一時ライセンス** – 短期キーが必要な場合は [Aspose の一時ライセンスページ](https://purchase.aspose.com/temporary-license/) で申し込んでください。  
3. **購入** – 永続ライセンスは [Aspose の購入ポータル](https://purchase.aspose.com/buy) から購入してください。

すべての Aspose API を使用する前に、コード内でライセンスファイルを初期化してすべての機能を有効にしてください。

## 実装ガイド

### Word ドキュメントで入れ子ブックマークを作成する方法
シンプルなドキュメントを作成し、3 つのブックマークを追加します。そのうちの 1 つは別のブックマークを含みます。

#### 手順 1: ドキュメントとビルダーの初期化
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

#### 手順 2: 最初の（親）ブックマークを挿入する
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

#### 手順 3: 最初のブックマークの内部に 2 番目のブックマークを入れ子にする
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

#### 手順 4: 外側のブックマークを閉じる
```java
builder.endBookmark("Bookmark 1");
```

#### 手順 5: 独立した 3 番目のブックマークを追加する
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### PDF エクスポート用にブックマークのアウトラインレベルを設定する方法
次に、最終的な PDF に表示されるアウトライン階層を設定します。

#### 手順 1: `PdfSaveOptions` を準備する
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

#### 手順 2: 各ブックマークにアウトラインレベルを割り当てる
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### 手順 3: 設定したブックマークでドキュメントを PDF として保存する
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## よくある問題と解決策
- **ブックマークが欠落** – すべての `startBookmark` に対応する `endBookmark` があることを確認してください。  
- **階層が正しくない** – 割り当てたレベル番号を再確認してください。番号が小さいほど上位（親）レベルを意味します。  
- **ライセンスが適用されていない** – ブックマークが消える場合は、ドキュメント処理の前にライセンスファイルが読み込まれていることを確認してください。  

## 実用例
1. **法的契約書** – 条項、サブ条項、付録にすばやくジャンプできます。  
2. **技術レポート** – セクション、表、図をスクロールせずにナビゲートできます。  
3. **eラーニング教材** – 学生が必要に応じて章を展開し、例を折りたたむことができます。  

## パフォーマンスのヒント
- 保存前に未使用のセクションや画像を削除して、PDF のサイズを小さく保ちます。  
- 非常に大きなドキュメントの場合、`doc.cleanup()` を呼び出すか、ファイルをチャンク処理してメモリ負荷を軽減してください。  

## よくある質問

**Q: Aspose.Words for Java のインストール方法は？**  
A: 上記の Maven または Gradle 依存関係を追加し、ライセンスファイルをプロジェクトに配置してコード内で初期化してください。

**Q: アウトラインレベルを設定せずにブックマークを使用できますか？**  
A: はい、可能ですが、アウトラインレベルがないと PDF のブックマークパネルはフラットなリストになり、ナビゲーションが困難になります。

**Q: ブックマークの入れ子深さに制限はありますか？**  
A: 技術的には制限はありませんが、ユーザーの可読性を考慮して階層は適切（3〜4 レベル）に保ってください。

**Q: Aspose は非常に大きな Word ファイルをどのように処理しますか？**  
A: ライブラリはコンテンツをストリーミングし、`Document.optimizeResources()` のようなメソッドを提供してメモリ使用量を低く保ちます。

**Q: PDF 作成後にブックマークを編集できますか？**  
A: はい、Aspose.PDF for Java を使用して、ブックマークのタイトル、目的地、階層を作成後に変更できます。

## リソース
- [Aspose.Words Documentation](https://reference.aspose.com/words/java/)
- [Download Latest Releases](https://releases.aspose.com/words/java/)
- [Purchase a License](https://purchase.aspose.com/buy)
- [Free Trial](https://releases.aspose.com/words/java/)
- [Temporary License Application](https://purchase.aspose.com/temporary-license/)
- [Aspose Support Forum](https://forum.aspose.com/c/words/10)

---

**最終更新日:** 2026-04-02  
**テスト環境:** Aspose.Words 25.3 for Java  
**作者:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}