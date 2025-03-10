---
title: 文書の相違点を比較する
linktitle: 文書の相違点を比較する
second_title: Aspose.Words Java ドキュメント処理 API
description: Java で Aspose.Words を使用してドキュメントの相違点を比較する方法を学びます。ステップバイステップのガイドにより、正確なドキュメント管理が保証されます。
weight: 12
url: /ja/java/document-merging/comparing-documents-for-differences/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 文書の相違点を比較する

## 導入

つの Word 文書間のすべての違いを見つける方法を考えたことがありますか? 文書を修正したり、共同作業者による変更点を見つけようとしているときなどです。手動での比較は面倒で間違いが起きやすいですが、Aspose.Words for Java を使えば簡単です! このライブラリを使用すると、文書の比較を自動化し、修正箇所を強調表示し、変更点を簡単にマージできます。

## 前提条件

コードに進む前に、次のものが準備されていることを確認してください。  
1. システムに Java 開発キット (JDK) がインストールされています。  
2.  Aspose.Words for Javaライブラリ。[ここからダウンロード](https://releases.aspose.com/words/java/).  
3. IntelliJ IDEA や Eclipse のような開発環境。  
4. Java プログラミングに関する基本的な知識。  
5. 有効なAsposeライセンス。お持ちでない場合は、[一時ライセンスはこちら](https://purchase.aspose.com/temporary-license/).

## パッケージのインポート

Aspose.Words を使用するには、必要なクラスをインポートする必要があります。必要なインポートは次のとおりです。

```java
import com.aspose.words.*;
import java.util.Date;
```

これらのパッケージがプロジェクトの依存関係に正しく追加されていることを確認してください。


このセクションでは、プロセスを簡単なステップに分解します。


## ステップ1: ドキュメントを設定する

まず、元のバージョンを表す 1 つのドキュメントと編集されたバージョンを表す 1 つのドキュメントの 2 つが必要です。作成方法は次のとおりです。

```java
Document doc1 = new Document();
DocumentBuilder builder = new DocumentBuilder(doc1);
builder.writeln("This is the original document.");

Document doc2 = new Document();
builder = new DocumentBuilder(doc2);
builder.writeln("This is the edited document.");
```

これにより、基本的な内容を含む2つの文書がメモリに作成されます。また、既存のWord文書を読み込むこともできます。`new Document("path/to/document.docx")`.


## ステップ2: 既存のリビジョンを確認する

Word 文書のリビジョンは変更履歴を表します。比較する前に、どちらの文書にも既存のリビジョンが含まれていないことを確認してください。

```java
if (doc1.getRevisions().getCount() == 0 && doc2.getRevisions().getCount() == 0) {
    System.out.println("No revisions found. Proceeding with comparison...");
}
```

修正が存在する場合は、続行する前に修正を承認または拒否することをお勧めします。


## ステップ3: ドキュメントを比較する

使用`compare`相違点を見つける方法。この方法は、ターゲット文書（`doc2`）をソースドキュメント（`doc1`):

```java
doc1.compare(doc2, "AuthorName", new Date());
```

ここ：
- AuthorName は変更を行った人の名前です。
- 日付は比較タイムスタンプです。


## ステップ4: プロセスの修正

比較が完了すると、Aspose.Words はソース文書にリビジョンを生成します (`doc1`）。これらのリビジョンを分析してみましょう。

```java
for (Revision r : doc1.getRevisions()) {
    System.out.println("Revision type: " + r.getRevisionType());
    System.out.println("Node type: " + r.getParentNode().getNodeType());
    System.out.println("Changed text: " + r.getParentNode().getText());
}
```

このループは、変更の種類や影響を受けるテキストなど、各リビジョンに関する詳細な情報を提供します。


## ステップ5: すべての変更を承認する

ソース文書（`doc1`）をターゲット文書（`doc2`）、すべての修正を承認します。

```java
doc1.getRevisions().acceptAll();
```

このアップデート`doc1`すべての変更を反映するために`doc2`.


## ステップ6: 更新されたドキュメントを保存する

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

ドキュメントが同一であることを確認するには、テキストを比較します。

```java
if (doc1.getText().trim().equals(doc2.getText().trim())) {
    System.out.println("Documents are equal.");
}
```

テキストが一致した場合、おめでとうございます。ドキュメントの比較と同期が正常に完了しました。


## 結論

Aspose.Words for Java のおかげで、ドキュメントの比較はもはや面倒な作業ではなくなりました。わずか数行のコードで、相違点を特定し、修正を処理し、ドキュメントの一貫性を確保できます。共同執筆プロジェクトを管理する場合でも、法的文書を監査する場合でも、この機能は画期的なものです。

## よくある質問

### 画像や表を含むドキュメントを比較できますか?  
はい、Aspose.Words は、画像、表、書式設定を含む複雑なドキュメントの比較をサポートしています。

### この機能を使用するにはライセンスが必要ですか?  
はい、フル機能を使用するにはライセンスが必要です。[一時ライセンスはこちら](https://purchase.aspose.com/temporary-license/).

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
