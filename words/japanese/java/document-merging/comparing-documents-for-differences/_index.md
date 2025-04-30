---
"description": "JavaでAspose.Wordsを使用してドキュメントの相違点を比較する方法を学びましょう。ステップバイステップガイドで正確なドキュメント管理を実現します。"
"linktitle": "文書の相違点を比較する"
"second_title": "Aspose.Words Java ドキュメント処理 API"
"title": "文書の相違点を比較する"
"url": "/ja/java/document-merging/comparing-documents-for-differences/"
"weight": 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 文書の相違点を比較する

## 導入

2つのWord文書の違いを一つ一つ見つける方法に困ったことはありませんか？文書を修正しているときや、共同編集者による変更点を探しているときなど、様々な場面で役立ちます。手作業での比較は面倒でミスも発生しがちですが、Aspose.Words for Javaを使えば簡単です！このライブラリを使えば、文書の比較を自動化し、修正箇所をハイライト表示し、変更点を簡単にマージできます。

## 前提条件

コードに進む前に、次のものが準備されていることを確認してください。  
1. Java Development Kit (JDK) がシステムにインストールされています。  
2. Aspose.Words for Javaライブラリ。 [ここからダウンロード](https://releases。aspose.com/words/java/).  
3. IntelliJ IDEA や Eclipse のような開発環境。  
4. Java プログラミングに関する基本的な知識。  
5. 有効なAsposeライセンス。お持ちでない場合は、 [仮免許証はこちら](https://purchase。aspose.com/temporary-license/).

## パッケージのインポート

Aspose.Wordsを使用するには、必要なクラスをインポートする必要があります。必要なインポートは以下のとおりです。

```java
import com.aspose.words.*;
import java.util.Date;
```

これらのパッケージがプロジェクトの依存関係に正しく追加されていることを確認してください。


このセクションでは、プロセスを簡単な手順に分解します。


## ステップ1：ドキュメントを設定する

まず、元の文書と編集後の文書の2つのドキュメントが必要です。作成方法は次のとおりです。

```java
Document doc1 = new Document();
DocumentBuilder builder = new DocumentBuilder(doc1);
builder.writeln("This is the original document.");

Document doc2 = new Document();
builder = new DocumentBuilder(doc2);
builder.writeln("This is the edited document.");
```

これにより、基本的な内容を持つ2つの文書がメモリ上に作成されます。また、既存のWord文書を読み込むこともできます。 `new Document("path/to/document。docx")`.


## ステップ2: 既存のリビジョンを確認する

Word文書の履歴は変更履歴を表します。比較する前に、どちらの文書にも既存の履歴が含まれていないことを確認してください。

```java
if (doc1.getRevisions().getCount() == 0 && doc2.getRevisions().getCount() == 0) {
    System.out.println("No revisions found. Proceeding with comparison...");
}
```

修正が存在する場合は、続行する前に修正を承認または拒否することをお勧めします。


## ステップ3：文書を比較する

使用 `compare` 相違点を見つける方法。この方法は、対象文書（`doc2`）をソースドキュメント（`doc1`):

```java
doc1.compare(doc2, "AuthorName", new Date());
```

ここ：
- AuthorName は変更を行った人の名前です。
- 日付は比較のタイムスタンプです。


## ステップ4：プロセスの修正

比較すると、Aspose.Words はソースドキュメントにリビジョンを生成します (`doc1`）。これらの改訂版を分析してみましょう。

```java
for (Revision r : doc1.getRevisions()) {
    System.out.println("Revision type: " + r.getRevisionType());
    System.out.println("Node type: " + r.getParentNode().getNodeType());
    System.out.println("Changed text: " + r.getParentNode().getText());
}
```

このループは、変更の種類や影響を受けるテキストなど、各リビジョンに関する詳細な情報を提供します。


## ステップ5: すべての変更を承認する

ソースドキュメント（`doc1`）をターゲット文書に一致させる（`doc2`）、すべての修正を承認します。

```java
doc1.getRevisions().acceptAll();
```

このアップデート `doc1` すべての変更を反映するために `doc2`。


## ステップ6: 更新したドキュメントを保存する

最後に、更新されたドキュメントをディスクに保存します。

```java
doc1.save("Document.Compare.docx");
```

変更を確認するには、ドキュメントを再読み込みし、残りのリビジョンがないことを確認します。

```java
doc1 = new Document("Document.Compare.docx");
if (doc1.getRevisions().getCount() == 0) {
    System.out.println("Documents are now identical.");
}
```


## ステップ7: ドキュメントの同一性を確認する

文書が同一であることを確認するには、テキストを比較します。

```java
if (doc1.getText().trim().equals(doc2.getText().trim())) {
    System.out.println("Documents are equal.");
}
```

テキストが一致する場合、おめでとうございます。ドキュメントの比較と同期が正常に完了しました。


## 結論

Aspose.Words for Javaのおかげで、ドキュメントの比較はもはや面倒な作業ではありません。わずか数行のコードで、差異を正確に特定し、修正を処理し、ドキュメントの一貫性を確保できます。共同執筆プロジェクトの管理でも、法務文書の監査でも、この機能は画期的なものです。

## よくある質問

### 画像や表を含む文書を比較できますか?  
はい、Aspose.Words は、画像、表、書式設定を含む複雑なドキュメントの比較をサポートしています。

### この機能を使用するにはライセンスが必要ですか?  
はい、すべての機能を使用するにはライセンスが必要です。 [仮免許証はこちら](https://purchase。aspose.com/temporary-license/).

### 既存のリビジョンがある場合はどうなりますか?  
競合を避けるために、ドキュメントを比較する前にそれらを承認または拒否する必要があります。

### 文書内の変更箇所を強調表示できますか?  
はい、Aspose.Words では、変更の強調表示など、リビジョンの表示方法をカスタマイズできます。

### この機能は他のプログラミング言語でも利用できますか?  
はい、Aspose.Words は .NET や Python を含む複数の言語をサポートしています。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}