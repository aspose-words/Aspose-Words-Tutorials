---
category: general
date: 2026-08-07
description: Aspose.Words を使用した Java での脚注編集方法 – カスタムダッシュを追加し、脚注線を変更し、洗練された文書のために段落の配置を設定する
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit footnote
- add custom dash
- change footnote line
- change footnote separator
- set paragraph alignment
language: ja
lastmod: 2026-08-07
og_description: Aspose.Words を使用した Java での脚注の編集方法。カスタムダッシュの追加、脚注線の変更、段落の配置設定を数ステップで学びましょう。
og_image_alt: Java code editing footnote separator with a custom dash and centered
  alignment
og_title: Javaで脚注を編集する方法 – ダッシュを追加、行を変更、配置を設定
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  headline: How to edit footnote in Java with Aspose.Words
  type: TechArticle
- description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  name: How to edit footnote in Java with Aspose.Words
  steps:
  - name: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
    text: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
  - name: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
    text: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
  - name: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
    text: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
  - name: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
    text: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
  - name: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
    text: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
title: Aspose.Words を使用した Java で脚注を編集する方法
url: /ja/java/document-styling/how-to-edit-footnote-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# JavaでAspose.Wordsを使用した脚注の編集方法

JavaでWord文書の**脚注を編集する方法**が必要な場合、このガイドでは完全なワークフローを示します。カスタムダッシュの追加、脚注ラインの変更、段落の配置設定を学び、脚注セパレーターをプロフェッショナルに見せることができます。

脚注の編集は、法的契約書、学術論文、マーケティングパンフレットを作成する際に頻繁に求められる要件です。以下の手順は、ドキュメントの読み込みから最終ファイルの保存まで、追加ツールを必要とせずに必要なすべてをカバーしています。

## 前提条件

開始する前に、以下が揃っていることを確認してください。

* Java 17 以上がインストールされていること。
* Aspose.Words for Java（最新バージョン）をプロジェクトのクラスパスに追加していること。
* 少なくとも1つの脚注を含む DOCX ファイル（`input.docx`）があること。

これらの項目により、コードが実行時エラーなしで動作することが保証されます。

## 脚注セパレーターとラインの編集方法

脚注セパレーターは、本文と脚注リストの間に表示される段落です。その外観を変更すると可読性が向上し、企業のブランディングに合わせることができます。

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the document containing footnotes
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Get the footnote separator paragraph (the line before the footnote list)
        Paragraph separator = doc.getFootnoteSeparator();

        // Step 3: Center‑align the separator for better appearance
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Step 4: Replace the default separator line with a custom dash
        separator.getRuns().clear();                 // Remove existing runs
        separator.getRuns().add(new Run(doc, "—"));   // Add a custom dash character

        // Step 5: Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### 各行が重要な理由

1. **ドキュメントの読み込み** – `new Document(...)` は DOCX ファイルをメモリに読み込み、すべてのノードへのアクセスを可能にします。  
2. **セパレーターの取得** – `getFootfootnoteSeparator()` は Aspose.Words が脚注ラインとして扱う特別な段落を返します。このオブジェクトはセパレーターを安全に変更できる唯一の場所です。  
3. **段落配置の設定** – `setAlignment(ParagraphAlignment.CENTER)` はラインの配置を変更します。キーワード *set paragraph alignment* はセパレーターに直接適用され、中央揃えのダッシュが保証されます。  
4. **カスタムダッシュの追加** – 既存の Run をクリアし、エムダッシュ文字（`—`）を持つ新しい `Run` を追加することで、*add custom dash* の効果を実現し、同時に *change footnote line* を希望のスタイルに変更します。  
5. **ドキュメントの保存** – `doc.save(...)` は変更をディスクに書き込み、すべての修正が反映された出力ファイルを生成します。

## 脚注セパレーターにカスタムダッシュを追加する

**Step 4** のコードは *add custom dash* 手法を示しています。エムダッシュを `"***"` や `"---"` など任意の文字列に置き換えて、文書のビジュアル言語に合わせることができます。

```java
separator.getRuns().clear();                     // Remove default line
separator.getRuns().add(new Run(doc, "***"));    // Insert three asterisks as a custom dash
```

デフォルトの細い線がブランディングガイドラインに合わない場合、カスタムダッシュは特に有用です。

## 脚注ラインのスタイルを変更する

ダッシュではなく実線が好みの場合、Unicode のボックス描画文字や連続したアンダースコアを挿入できます。

```java
separator.getRuns().clear();
separator.getRuns().add(new Run(doc, "_____")); // Five underscores create a solid line
```

*change footnote line* の手順は、選択した文字に関係なく同じように機能します。セパレーター段落は含まれるテキストをそのまま描画するだけだからです。

## 脚注セパレーターの段落配置を設定する

*set paragraph alignment* の操作は中央揃えに限定されません。レイアウトの要件に応じて左揃え、右揃え、または両端揃えに設定できます。

```java
separator.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT); // Right‑align
```

セパレーターを右揃えにすると、右揃え脚注を使用するバイリンガル出版物などで便利です。

## 完全な実行可能サンプル

以下は、ドキュメントの読み込み、脚注セパレーターの編集、カスタムダッシュの追加、ラインスタイルの変更、配置設定というすべての概念を組み込んだ完全なプログラムです。

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Retrieve the footnote separator paragraph
        Paragraph separator = doc.getFootnoteSeparator();

        // Set the desired alignment (center, left, right, or justify)
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Clear any existing content in the separator
        separator.getRuns().clear();

        // Add a custom dash – replace with any string to change footnote line
        separator.getRuns().add(new Run(doc, "—")); // Em‑dash as the custom dash

        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Expected output:** `output.docx` ファイルには、元の細い線があった場所に中央揃えのエムダッシュが含まれます。すべての脚注はそのまま残り、文書のレイアウトは新しいセパレーターのスタイルを反映します。

## よくある落とし穴と回避策

| 問題 | 理由 | 対策 |
|------|------|------|
| セパレーターが見つからない | 文書に脚注がない、またはカスタム脚注スタイルが使用されている | `getFootnoteSeparator()` を呼び出す前に、ソース DOCX に少なくとも1つの脚注が含まれていることを確認する |
| カスタムダッシュが表示されない | フォントが選択した文字をサポートしていない | 文書のデフォルトフォントがサポートする Unicode 文字を使用するか、互換性のあるフォントを埋め込む |
| 配置が変わらない | 後続のコードで段落書式が上書きされている | 配置設定を、書式をリセットする可能性のある他の呼び出し **の後** に適用する |

これらのポイントに対処すれば、実行時エラーを防ぎ、*脚注を編集する方法* のプロセスが確実に機能します。

## 次のステップ

**脚注を編集する方法** の要素を理解した今、関連タスクを探求できます。

* **カスタム脚注参照スタイルの追加** – `FootnoteReference` ノードを変更して番号付けや記号を変える。  
* **プログラムから新しい脚注を挿入** – 動的コンテンツ用に `DocumentBuilder.insertFootnote()` を使用する。  
* **条件付き書式の適用** – 段落スタイルやコンテンツ長に基づいて脚注の外観を変更する。

これらの拡張は、*add custom dash*、*change footnote line*、*set paragraph alignment* で使用したのと同じ API を基盤に構築されています。

---

*Happy coding! If the tutorial helped you master footnote editing, consider sharing it with your team or contributing a pull request to improve the example further.*

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法に基づく密接に関連したトピックをカバーしています。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを探求するのに役立ちます。

- [Set Footnote And End Note Position](/words/hindi/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}