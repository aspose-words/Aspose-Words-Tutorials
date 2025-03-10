---
title: 目次の生成
linktitle: 目次の生成
second_title: Aspose.Words Java ドキュメント処理 API
description: Aspose.Words for Java を使用して動的な目次を作成する方法を学びます。ステップバイステップのガイダンスとソース コードの例を使用して、目次の生成をマスターします。
weight: 14
url: /ja/java/table-processing/table-contents-generation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 目次の生成

## 導入

Word 文書で動的でプロフェッショナルな外観の目次 (TOC) を作成するのに苦労したことはありませんか? もう探す必要はありません。Aspose.Words for Java を使用すると、プロセス全体を自動化して時間を節約し、正確性を確保できます。包括的なレポートを作成する場合でも、学術論文を作成する場合でも、このチュートリアルでは、Java を使用してプログラムで目次を生成する手順を説明します。準備はできましたか? さあ、始めましょう!

## 前提条件

コーディングを始める前に、以下のものを用意してください。

1.  Java開発キット（JDK）：システムにインストールされています。ここからダウンロードできます。[Oracleのウェブサイト](https://www.oracle.com/java/technologies/javase-downloads.html).
2. Aspose.Words for Javaライブラリ:最新バージョンをダウンロードしてください。[リリースページ](https://releases.aspose.com/words/java/).
3. 統合開発環境 (IDE): IntelliJ IDEA、Eclipse、NetBeans など。
4.  Aspose一時ライセンス: 評価制限を回避するには、[一時ライセンス](https://purchase.aspose.com/temporary-license/).

## パッケージのインポート

Aspose.Words for Java を効果的に使用するには、必要なクラスをインポートする必要があります。インポートは次のとおりです。

```java
import com.aspose.words.*;
```

Word 文書に動的な目次を生成するには、次の手順に従います。

## ステップ 1: ドキュメントと DocumentBuilder を初期化する

最初のステップは、新しいドキュメントを作成し、`DocumentBuilder`それを操作するクラス。


```java
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document`: Word 文書を表します。
- `DocumentBuilder`: ドキュメントを簡単に操作できるヘルパー クラス。

## ステップ2: 目次を挿入する

それでは、ドキュメントの先頭に目次を挿入しましょう。


```java
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");
builder.insertBreak(BreakType.PAGE_BREAK);
```

- `insertTableOfContents`: TOC フィールドを挿入します。パラメータは以下を指定します。
  - `\o "1-3"`: レベル 1 から 3 までの見出しを含めます。
  - `\h`: エントリをハイパーリンクにします。
  - `\z`: Web ドキュメントのページ番号を抑制します。
  - `\u`: ハイパーリンクのスタイルを保持します。
- `insertBreak`: 目次の後に改ページを追加します。

## ステップ3: 目次に見出しを追加する

TOC に内容を入力するには、見出しスタイルを使用して段落を追加する必要があります。


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 1");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_2);
builder.writeln("Heading 1.1");
builder.writeln("Heading 1.2");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 2");
```

- `setStyleIdentifier` : 段落スタイルを特定の見出しレベルに設定します（例：`HEADING_1`, `HEADING_2`）。
- `writeln`: 指定されたスタイルでドキュメントにテキストを追加します。

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

- 目次に階層を表示するために、より深いレベルの見出しを追加します。

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

- `save` : ドキュメントを`.docx`ファイル。他の形式も指定できます。`.pdf`または`.txt`必要であれば。

## 結論

おめでとうございます。Aspose.Words for Java を使用して、Word 文書に動的な目次を作成することができました。わずか数行のコードで、何時間もかかるタスクを自動化できました。では、次は何をしましょうか。さまざまな見出しスタイルと形式を試して、特定のニーズに合わせて目次をカスタマイズしてみてください。

## よくある質問

### TOC 形式をさらにカスタマイズできますか?
もちろんです! ページ番号の追加、テキストの配置、カスタム見出しスタイルの使用など、目次パラメータを調整できます。

### Aspose.Words for Java にはライセンスが必須ですか?
はい、フル機能を使用するにはライセンスが必要です。[一時ライセンス](https://purchase.aspose.com/temporary-license/).

### 既存のドキュメントの目次を生成できますか?
はい！文書を`Document`オブジェクトを作成し、同じ手順に従って TOC を挿入および更新します。

### これは PDF エクスポートでも機能しますか?
はい、文書をPDF形式で保存すると目次が表示されます。`.pdf`形式。

### さらに詳しいドキュメントはどこで見つかりますか?
チェックしてください[Aspose.Words for Java ドキュメント](https://reference.aspose.com/words/java/)さらなる例と詳細については、こちらをご覧ください。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
