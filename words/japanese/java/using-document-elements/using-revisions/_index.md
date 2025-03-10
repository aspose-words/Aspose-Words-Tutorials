---
title: Aspose.Words for Java でのリビジョンの使用
linktitle: リビジョンの使用
second_title: Aspose.Words Java ドキュメント処理 API
description: Aspose.Words for Java のリビジョンを効率的に使用する方法を学習します。開発者向けのステップバイステップ ガイド。ドキュメント管理を最適化します。
weight: 22
url: /ja/java/using-document-elements/using-revisions/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でのリビジョンの使用


ドキュメントを操作し、リビジョン管理を実装する必要がある Java 開発者の場合、Aspose.Words for Java には、リビジョンを効果的に管理するのに役立つ強力なツール セットが用意されています。このチュートリアルでは、Aspose.Words for Java でリビジョンを使用する方法を段階的に説明します。 

## 1. Aspose.Words for Java の紹介

Aspose.Words for Java は、Microsoft Word を必要とせずに Word ドキュメントを作成、変更、操作できる強力な Java API です。ドキュメント内で修正を実装する必要がある場合に特に便利です。

## 2. 開発環境の設定

Aspose.Words for Java の使用を開始する前に、開発環境を設定する必要があります。必要な Java 開発ツールと Aspose.Words for Java ライブラリがインストールされていることを確認してください。

## 3. 新しいドキュメントを作成する

まず、Aspose.Words for Java を使用して新しい Word 文書を作成しましょう。手順は次のとおりです。

```java
string outPath = "Your Output Directory";
Document doc = new Document();
Body body = doc.getFirstSection().getBody();
Paragraph para = body.getFirstParagraph();
```

## 4. ドキュメントにコンテンツを追加する

空白のドキュメントができたので、コンテンツを追加できます。この例では、3 つの段落を追加します。

```java
para.appendChild(new Run(doc, "Paragraph 1. "));
body.appendParagraph("Paragraph 2. ");
body.appendParagraph("Paragraph 3. ");
```

## 5. リビジョントラッキングの開始

ドキュメント内の変更を追跡するには、次のコードを使用できます。

```java
doc.startTrackRevisions("John Doe", new Date());
```

## 6. 修正を行う

別の段落を追加して修正してみましょう。

```java
para = body.appendParagraph("Paragraph 4. ");
```

## 7. 修正の承認と拒否

Aspose.Words for Java を使用して、ドキュメントの修正を承認または拒否できます。ドキュメントの生成後、Microsoft Word で修正を簡単に管理できます。

## 8. リビジョン追跡の停止

リビジョンの追跡を停止するには、次のコードを使用します。

```java
doc.stopTrackRevisions();
```

## 9. ドキュメントを保存する

最後に、ドキュメントを保存します。

```java
doc.save(outPath + "WorkingWithRevisions.AcceptRevisions.docx");
```

## 10. 結論

このチュートリアルでは、Aspose.Words for Java でのリビジョンの使用の基本について説明しました。ドキュメントの作成方法、コンテンツの追加方法、リビジョンの追跡の開始と停止方法、ドキュメントの保存方法を学習しました。

Aspose.Words for Java を使用して、Java アプリケーションのリビジョンを効果的に管理するために必要なツールが手に入りました。

## 完全なソースコード
```java
string outPath = "Your Output Directory";
Document doc = new Document();
Body body = doc.getFirstSection().getBody();
Paragraph para = body.getFirstParagraph();
//最初の段落にテキストを追加し、さらに 2 つの段落を追加します。
para.appendChild(new Run(doc, "Paragraph 1. "));
body.appendParagraph("Paragraph 2. ");
body.appendParagraph("Paragraph 3. ");
// 3つの段落がありますが、いずれも修正として登録されていません
//改訂を追跡しながら文書内のコンテンツを追加/削除すると、
//これらはドキュメント内にそのように表示され、承認/拒否することができます。
doc.startTrackRevisions("John Doe", new Date());
//この段落はリビジョンであり、それに応じて「IsInsertRevision」フラグが設定されます。
para = body.appendParagraph("Paragraph 4. ");
Assert.assertTrue(para.isInsertRevision());
//ドキュメントの段落コレクションを取得し、段落を削除します。
ParagraphCollection paragraphs = body.getParagraphs();
Assert.assertEquals(4, paragraphs.getCount());
para = paragraphs.get(2);
para.remove();
//リビジョンを追跡しているので、段落はまだ文書内に存在し、「IsDeleteRevision」が設定されます。
//すべての修正が承認または拒否されるまで、Microsoft Word に修正として表示されます。
Assert.assertEquals(4, paragraphs.getCount());
Assert.assertTrue(para.isDeleteRevision());
//変更を承認すると、削除リビジョンの段落は削除されます。
doc.acceptAllRevisions();
Assert.assertEquals(3, paragraphs.getCount());
Assert.assertEquals(para.getRuns().getCount(), 0); //空でした
//リビジョンの追跡を停止すると、このテキストは通常のテキストとして表示されます。
//ドキュメントが変更された場合、リビジョンはカウントされません。
doc.stopTrackRevisions();
//ドキュメントを保存します。
doc.save(outPath + "WorkingWithRevisions.AcceptRevisions.docx");
  
```

## よくある質問

### 1. Aspose.Words for Java を他のプログラミング言語で使用できますか?

いいえ、Aspose.Words for Java は Java 開発用に特別に設計されています。

### 2. Aspose.Words for Java は Microsoft Word のすべてのバージョンと互換性がありますか?

はい、Aspose.Words for Java はさまざまなバージョンの Microsoft Word と互換性があるように設計されています。

### 3. 既存の Word 文書の変更履歴を追跡できますか?

はい、Aspose.Words for Java を使用して、既存の Word 文書の変更を追跡できます。

### 4. Aspose.Words for Java を使用するにはライセンス要件がありますか?

はい、プロジェクトでAspose.Words for Javaを使用するにはライセンスを取得する必要があります。[ライセンスはこちらから入手できます](https://purchase.aspose.com/buy).

### 5. Aspose.Words for Java のサポートはどこで受けられますか?

ご質問やご不明な点がございましたら、[Aspose.Words for Java サポート フォーラム](https://forum.aspose.com/).

今すぐ Aspose.Words for Java を使い始めて、ドキュメント管理プロセスを効率化しましょう。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
