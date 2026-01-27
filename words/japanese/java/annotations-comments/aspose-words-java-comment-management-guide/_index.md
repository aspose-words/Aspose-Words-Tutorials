---
date: '2026-01-27'
description: Aspose.Words for Java を使用して、Word 文書にコメントを追加したり、コメントを削除したりする方法を学びましょう。コメントの管理、印刷、削除、タイムスタンプ付与を簡単に行えます。
keywords:
- Aspose.Words Java
- comment management in Word documents
- managing comments with Aspose.Words
title: Aspose.Words で Java にコメントを追加 – コメント管理のマスター
url: /ja/java/annotations-comments/aspose-words-java-comment-management-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java: Word ドキュメントにおけるコメント管理のマスター

## Introduction
プログラムで **add comment java** を追加し、コメントのライフサイクルを完全にコントロールしたい場合は、ここが最適です。共同レビュー ツールの構築やドキュメント ワークフローの自動化を行う際、コメントの管理（追加、返信、削除、タイムスタンプの追跡）は大きな課題となります。このチュートリアルでは Aspose.Words for Java を使用したすべての必須操作を順に解説し、**add remove word comments** を自信を持って実行し、コメントを印刷し、完了（解決）としてマークし、UTC タイムスタンプを取得できるようにします。

**What You’ll Learn**
- 1 行のコードでコメントと返信を追加する方法  
- すべてのトップレベルコメントとそのネストされた返信を印刷する方法  
- コメントの返信を削除する、またはスレッド全体をクリアする方法  
- コメントを完了（解決）としてマークする方法  
- コメントが作成された正確な UTC 日付と時刻を取得する方法  

Ready? コードに入る前に環境が正しく設定されているか確認しましょう。

## Prerequisites
開始する前に、以下が揃っていることを確認してください。

- Java Development Kit (JDK) 8 以上がインストール済み  
- Java の構文とオブジェクト指向プログラミングの基本知識  
- IntelliJ IDEA や Eclipse など、プロジェクト管理がしやすい IDE  

### Setting Up Aspose.Words for Java
Aspose.Words は、さまざまな形式の Word ドキュメントを操作できる強力なライブラリです。ビルドシステムに合わせて依存関係を追加してください。

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

#### License Acquisition
Aspose.Words は商用製品ですが、無料トライアルで開始したり、フル機能アクセス用の一時ライセンスをリクエストしたりできます。ライセンスオプションは [purchase page](https://purchase.aspose.com/buy) をご覧ください。

## Quick Answers
- **Can I add comment java without a license?** はい、トライアルは利用可能ですが評価用の透かしが追加されます。  
- **Which method adds a reply?** `comment.addReply(author, initials, date, text)`。  
- **How do I mark a comment as done?** `comment.setDone(true)` を呼び出します。  
- **Is UTC timestamp available?** `comment.getDateTimeUtc()` を使用します。  
- **What version is tested?** Aspose.Words 25.3 (Java)。

## Implementation Guide
以下のセクションで各機能をステップバイステップで分解し、実装のポイントや実用的なヒントを交えて解説します。

### Feature 1: Add Comment with Reply
#### Overview
コメントと返信を追加することは、共同編集の基礎です。コメントを作成し、段落に添付し、さらにネストされた返信を追加する方法を示します。

#### Implementation Steps
**Step 1:** Initialize the Document Object  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
```

**Step 2:** Create and Add a Comment  
```java
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```

**Step 3:** Add a Reply to the Comment  
```java
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentWithReply.docx");
```

### Feature 2: Print All Comments
#### Overview
大規模なドキュメントをレビューする際、すべてのトップレベルコメントとその返信を一括で印刷できれば時間を大幅に節約できます。このスニペットは、ドキュメントの読み込みとコメント階層の列挙方法を示します。

#### Implementation Steps
**Step 1:** Load the Document  
```java
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/Comments.docx");
```

**Step 2:** Retrieve and Print Comments  
```java
NodeCollection<Comment> comments = doc.getChildNodes(NodeType.COMMENT, true);
for (Comment comment : (Iterable<Comment>) comments) {
    if (comment.getAncestor() == null) {
        System.out.println("Top-level comment:");
        System.out.println("\t" + comment.getText().trim() + ", by " + comment.getAuthor());
        for (Comment reply : comment.getReplies()) {
            System.out.println("\t" + reply.getText().trim() + ", by " + reply.getAuthor());
        }
    }
}
```

### Feature 3: Remove Comment Replies
#### Overview
コメントスレッドがノイズになることがあります。この例では、単一の返信を削除する方法と、返信リスト全体をクリアする方法を示します。

#### Implementation Steps
**Step 1:** Initialize and Add Comments with Replies  
```java
Document document = new Document();
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
comment.addReply("Joe Bloggs", "J.B.", new Date(), "Another reply");
```

**Step 2:** Remove Replies  
```java
comment.removeReply(comment.getReplies().get(0)); // Remove one reply
comment.removeAllReplies(); // Remove all remaining replies
```

### Feature 4: Mark Comment as Done
#### Overview
コメントを「完了」とマークすることで、問題が解決されたことを示します。このフラグは UI 層で完了済みフィードバックを除外する際に利用できます。

#### Implementation Steps
**Step 1:** Create a Document and Add a Comment  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
documentBuilder.writeln("Hello world!");
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("Fix the spelling error!");
```

**Step 2:** Mark the Comment as Done  
```java
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
document.getFirstSection().getBody().getFirstParagraph().getRuns().get(0).setText("Hello world!");
comment.setDone(true);
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentDone.docx");
```

### Feature 5: Get UTC Date and Time from Comment
#### Overview
正確なタイムスタンプは監査トレイルに不可欠です。Aspose.Words は作成時刻を UTC で保存しており、取得して比較できます。

#### Implementation Steps
**Step 1:** Create a Document with a Timestamped Comment  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
Date dateTime = new Date();
Comment comment = new Comment(document, "John Doe", "J.D.", dateTime);
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```

**Step 2:** Save and Retrieve the UTC Date  
```java
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Comment currentComment = (Comment) doc.getChild(NodeType.COMMENT, 0, true);
assert currentComment.getDateTimeUtc().toString() == dateTime.toString();
```

## Practical Applications
これらの API を理解することで、ドキュメント中心のソリューションを大幅に向上させることができます。

- **Collaborative Editing:** 複数のレビュアがフィードバックを残し、返信し、ファイル内で直接問題を解決できます。  
- **Document Review Pipelines:** コメントの抽出を自動化し、レポート作成やコンプライアンスチェックに活用できます。  
- **Audit Trails:** 法的・規制上の目的で UTC タイムスタンプを保存できます。  

これらのスニペットは、コンテンツ管理プラットフォーム、レポート自動生成ツール、カスタム Word 処理ツールなど、より大規模なシステムに組み込むことが可能です。

## Performance Considerations
数百ページ、数千件のコメントがある大規模 Word ファイルを扱う際は、以下の点に留意してください。

- コメントを一括でメモリに読み込むのではなく、バッチ処理で処理する。  
- 複数の操作を行う場合は、`Document` インスタンスを再利用する。  
- 最新の Aspose.Words バージョンにアップグレードし、パフォーマンス最適化とバグ修正の恩恵を受ける。

## Common Issues and Solutions
| 問題 | 原因 | 対策 |
|------|------|------|
| **`NullPointerException` when accessing replies** | コメントに返信が存在しない（`getReplies()` が空を返す） | `comment.getReplies().getCount() > 0` を確認してから要素にアクセスする。 |
| **Comments not appearing after saving** | ドキュメントが別フォルダーに保存された、または上書きされた | `YOUR_DOCUMENT_DIRECTORY` が意図した場所を指しているか、書き込み権限があるか確認する。 |
| **UTC timestamp differs from local time** | `Date` がシステムロケールを使用し、`getDateTimeUtc()` が UTC に変換する | 作成時は `new Date()` を使用し、保存時は `getDateTimeUtc()` で一貫した時刻を取得する。 |

## FAQ Section
1. **What is Aspose.Words for Java?**  
   - Word ドキュメントをさまざまな形式でプログラムから操作できるライブラリです。  

2. **How do I install Aspose.Words for my project?**  
   - 前述の Maven または Gradle の依存関係をプロジェクトファイルに追加します。  

3. **Can I use Aspose.Words without a license?**  
   - はい、ただし評価用の透かしや機能制限があります。  

4. **What are some common issues when managing comments?**  
   - 正しいドキュメントの読み込み、返信が null になるケースへの対処、コメント階層の確認が重要です。  

5. **How do I track changes across multiple documents?**  
   - アプリケーション側でバージョン管理ロジックを実装するか、Aspose.Words の組み込みリビジョン追跡機能を利用します。  

---

**Last Updated:** 2026-01-27  
**Tested With:** Aspose.Words 25.3 for Java  
**Author:** Aspose  

{{< blocks/products/products-backtop-button >}}

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}