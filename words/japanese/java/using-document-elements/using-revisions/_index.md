---
"description": "Aspose.Words for Javaのリビジョンを効率的に活用する方法を学びましょう。開発者向けのステップバイステップガイド。ドキュメント管理を最適化します。"
"linktitle": "リビジョンの使用"
"second_title": "Aspose.Words Java ドキュメント処理 API"
"title": "Aspose.Words for Java でリビジョンを使用する"
"url": "/ja/java/using-document-elements/using-revisions/"
"weight": 22
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でリビジョンを使用する


Java開発者で、ドキュメントを扱い、リビジョン管理を実装する必要がある場合、Aspose.Words for Javaは、リビジョン管理を効果的に行うための強力なツールセットを提供します。このチュートリアルでは、Aspose.Words for Javaのリビジョン機能の使い方を段階的に説明します。 

## 1. Aspose.Words for Java の紹介

Aspose.Words for Javaは、Microsoft Wordを必要とせずにWord文書を作成、変更、操作できる堅牢なJava APIです。特に、文書内で修正機能を導入する必要がある場合に便利です。

## 2. 開発環境の設定

Aspose.Words for Java の使用を開始する前に、開発環境をセットアップする必要があります。必要な Java 開発ツールと Aspose.Words for Java ライブラリがインストールされていることを確認してください。

## 3. 新しいドキュメントを作成する

まずはAspose.Words for Javaを使って新しいWord文書を作成しましょう。手順は以下のとおりです。

```java
string outPath = "Your Output Directory";
Document doc = new Document();
Body body = doc.getFirstSection().getBody();
Paragraph para = body.getFirstParagraph();
```

## 4. ドキュメントにコンテンツを追加する

空白のドキュメントができたので、コンテンツを追加できます。この例では、3つの段落を追加します。

```java
para.appendChild(new Run(doc, "Paragraph 1. "));
body.appendParagraph("Paragraph 2. ");
body.appendParagraph("Paragraph 3. ");
```

## 5. リビジョントラッキングの開始

ドキュメント内の変更履歴を追跡するには、次のコードを使用できます。

```java
doc.startTrackRevisions("John Doe", new Date());
```

## 6. 修正を行う

別の段落を追加して修正してみましょう。

```java
para = body.appendParagraph("Paragraph 4. ");
```

## 7. 修正の承認と拒否

Aspose.Words for Java を使用すると、ドキュメントの修正を承認または拒否できます。ドキュメント生成後は、Microsoft Word で簡単に修正を管理できます。

## 8. リビジョン追跡の停止

リビジョンの追跡を停止するには、次のコードを使用します。

```java
doc.stopTrackRevisions();
```

## 9. ドキュメントの保存

最後に、ドキュメントを保存します。

```java
doc.save(outPath + "WorkingWithRevisions.AcceptRevisions.docx");
```

## 10. 結論

このチュートリアルでは、Aspose.Words for Java におけるリビジョン機能の基本について説明しました。ドキュメントの作成、コンテンツの追加、リビジョン管理の開始と停止、そしてドキュメントの保存方法を学習しました。

Aspose.Words for Java を使用して Java アプリケーションのリビジョンを効果的に管理するために必要なツールが手に入りました。

## 完全なソースコード
```java
string outPath = "Your Output Directory";
Document doc = new Document();
Body body = doc.getFirstSection().getBody();
Paragraph para = body.getFirstParagraph();
// 最初の段落にテキストを追加し、さらに 2 つの段落を追加します。
para.appendChild(new Run(doc, "Paragraph 1. "));
body.appendParagraph("Paragraph 2. ");
body.appendParagraph("Paragraph 3. ");
// 3つの段落がありますが、いずれも修正として登録されていません。
// 改訂履歴を追跡しながら文書内のコンテンツを追加または削除すると、
// これらはドキュメント内にそのように表示され、承認/拒否することができます。
doc.startTrackRevisions("John Doe", new Date());
// この段落はリビジョンであり、それに応じて「IsInsertRevision」フラグが設定されます。
para = body.appendParagraph("Paragraph 4. ");
Assert.assertTrue(para.isInsertRevision());
// ドキュメントの段落コレクションを取得し、段落を削除します。
ParagraphCollection paragraphs = body.getParagraphs();
Assert.assertEquals(4, paragraphs.getCount());
para = paragraphs.get(2);
para.remove();
// リビジョンを追跡しているので、段落はまだ文書内に存在し、「IsDeleteRevision」が設定されます。
// すべての修正が承認または拒否されるまで、Microsoft Word に修正として表示されます。
Assert.assertEquals(4, paragraphs.getCount());
Assert.assertTrue(para.isDeleteRevision());
// 変更を承認すると、削除リビジョン段落は削除されます。
doc.acceptAllRevisions();
Assert.assertEquals(3, paragraphs.getCount());
Assert.assertEquals(para.getRuns().getCount(), 0); //空でした
// リビジョンの追跡を停止すると、このテキストは通常のテキストとして表示されます。
// ドキュメントが変更された場合、リビジョンはカウントされません。
doc.stopTrackRevisions();
// ドキュメントを保存します。
doc.save(outPath + "WorkingWithRevisions.AcceptRevisions.docx");
  
```

## よくある質問

### 1. Aspose.Words for Java を他のプログラミング言語で使用できますか?

いいえ、Aspose.Words for Java は Java 開発用に特別に設計されています。

### 2. Aspose.Words for Java は Microsoft Word のすべてのバージョンと互換性がありますか?

はい、Aspose.Words for Java はさまざまなバージョンの Microsoft Word と互換性があるように設計されています。

### 3. 既存の Word 文書の変更履歴を追跡できますか?

はい、Aspose.Words for Java を使用して、既存の Word 文書の変更履歴を追跡できます。

### 4. Aspose.Words for Java を使用するにはライセンス要件がありますか?

はい、Aspose.Words for Javaをプロジェクトで使用するにはライセンスを取得する必要があります。 [ライセンスはこちらから](https://purchase。aspose.com/buy).

### 5. Aspose.Words for Java のサポートはどこで受けられますか?

ご質問や問題がある場合は、 [Aspose.Words for Java サポートフォーラム](https://forum。aspose.com/).

今すぐ Aspose.Words for Java を使い始めて、ドキュメント管理プロセスを効率化しましょう。



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}