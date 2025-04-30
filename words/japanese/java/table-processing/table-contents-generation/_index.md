---
"description": "Aspose.Words for Javaを使用して動的な目次を作成する方法を学びます。ステップバイステップのガイダンスとソースコードの例を使って、目次の作成方法をマスターしましょう。"
"linktitle": "目次生成"
"second_title": "Aspose.Words Java ドキュメント処理 API"
"title": "目次生成"
"url": "/ja/java/table-processing/table-contents-generation/"
"weight": 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 目次生成

## 導入

Word文書にダイナミックでプロフェッショナルな目次（TOC）を作成するのに苦労したことはありませんか？もう探す必要はありません！Aspose.Words for Javaを使えば、プロセス全体を自動化し、時間を節約し、正確性を確保できます。包括的なレポートを作成する場合でも、学術論文を作成する場合でも、このチュートリアルでは、Javaでプログラム的に目次を作成する方法を解説します。準備はできましたか？さあ、始めましょう！

## 前提条件

コーディングを始める前に、以下のものを用意してください。

1. Java開発キット（JDK）：システムにインストールされています。ダウンロードはこちらから。 [Oracleのウェブサイト](https://www。oracle.com/java/technologies/javase-downloads.html).
2. Aspose.Words for Javaライブラリ: 最新バージョンを以下からダウンロードしてください。 [リリースページ](https://releases。aspose.com/words/java/).
3. 統合開発環境 (IDE): IntelliJ IDEA、Eclipse、NetBeans など。
4. Aspose一時ライセンス: 評価制限を回避するには、 [一時ライセンス](https://purchase。aspose.com/temporary-license/).

## パッケージのインポート

Aspose.Words for Java を効果的に使用するには、必要なクラスをインポートする必要があります。インポートするクラスは以下のとおりです。

```java
import com.aspose.words.*;
```

Word 文書に動的な目次を生成するには、次の手順に従います。

## ステップ1: DocumentとDocumentBuilderを初期化する

最初のステップは、新しいドキュメントを作成し、 `DocumentBuilder` それを操作するクラス。


```java
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document`: Word 文書を表します。
- `DocumentBuilder`: ドキュメントを簡単に操作できるヘルパー クラス。

## ステップ2: 目次を挿入する

それでは、ドキュメントの先頭に目次を挿入してみましょう。


```java
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");
builder.insertBreak(BreakType.PAGE_BREAK);
```

- `insertTableOfContents`: TOCフィールドを挿入します。パラメータは以下を指定します。
  - `\o "1-3"`: レベル 1 ～ 3 の見出しを含めます。
  - `\h`: エントリをハイパーリンクにします。
  - `\z`: Web ドキュメントのページ番号を抑制します。
  - `\u`: ハイパーリンクのスタイルを保持します。
- `insertBreak`: 目次の後に改ページを追加します。

## ステップ3: 見出しを追加して目次を作成する

TOC を入力するには、見出しスタイルを使用して段落を追加する必要があります。


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 1");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_2);
builder.writeln("Heading 1.1");
builder.writeln("Heading 1.2");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 2");
```

- `setStyleIdentifier`: 段落スタイルを特定の見出しレベルに設定します（例： `HEADING_1`、 `HEADING_2`）。
- `writeln`指定されたスタイルでドキュメントにテキストを追加します。

## ステップ4: ネストされた見出しを追加する

TOC レベルを示すには、ネストされた見出しを含めます。


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_3);
builder.writeln("Heading 3.1.1");
builder.writeln("Heading 3.1.2");
builder.writeln("Heading 3.1.3");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_4);
builder.writeln("Heading 3.1.3.1");
builder.writeln("Heading 3.1.3.2");
```

- TOC の階層を表示するには、より深いレベルの見出しを追加します。

## ステップ5: TOCフィールドを更新する

最新の見出しを表示するには、TOC フィールドを更新する必要があります。


```java
doc.updateFields();
```

- `updateFields`: ドキュメント内のすべてのフィールドを更新し、追加された見出しが目次に反映されるようにします。

## ステップ6: ドキュメントを保存する

最後に、ドキュメントを希望の形式で保存します。


```java
doc.save(dataDir + "DocumentBuilder.InsertToc.docx");
```

- `save`: ドキュメントを `.docx` ファイル。他の形式を指定することもできます。 `.pdf` または `.txt` 必要であれば。

## 結論

おめでとうございます！Aspose.Words for Java を使って、Word 文書に動的な目次を作成できました。わずか数行のコードで、何時間もかかる作業を自動化できました。さて、次は何をしましょうか？さまざまな見出しスタイルや書式を試して、ニーズに合わせて目次をカスタマイズしてみましょう。

## よくある質問

### TOC 形式をさらにカスタマイズできますか?
もちろんです！ページ番号の追加、テキストの配置、カスタム見出しスタイルの使用など、目次パラメータを調整できます。

### Aspose.Words for Java にはライセンスが必須ですか?
はい、すべての機能を使用するにはライセンスが必要です。 [一時ライセンス](https://purchase。aspose.com/temporary-license/).

### 既存のドキュメントの目次を生成できますか?
はい！文書を `Document` オブジェクトを作成し、同じ手順に従って TOC を挿入および更新します。

### これは PDF エクスポートでも機能しますか?
はい、文書をPDF形式で保存すると目次が表示されます。 `.pdf` 形式。

### さらに詳しいドキュメントはどこで見つかりますか?
チェックしてください [Aspose.Words for Java ドキュメント](https://reference.aspose.com/words/java/) さらなる例と詳細については、こちらをご覧ください。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}