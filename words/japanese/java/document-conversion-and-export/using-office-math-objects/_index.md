---
date: 2026-02-14
description: Aspose.Words for Java を使用して、インラインで数式を表示し、数式を挿入し、Office Math オブジェクトを簡単に操作する方法を学びましょう。
linktitle: Using Office Math Objects
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for JavaでOffice Mathをインライン表示
url: /ja/java/document-conversion-and-export/using-office-math-objects/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java で Office Math を使用したインライン数式の表示

この包括的なチュートリアルでは、Aspose.Words for Java の Office Math オブジェクトを使用して **インラインで数式を表示** する方法を学びます。レポートに **数式を挿入** したり、複雑な式の書式設定を微調整したりする必要がある場合でも、Word 文書の読み込みから最終結果の保存まで、すべての手順を丁寧に解説します。

## Quick Answers
- **「インラインで数式を表示する」とはどういう意味ですか？** 数式がテキストの流れの中に表示され、別行になりません。  
- **数式オブジェクトを表すクラスはどれですか？** Aspose.Words API の `OfficeMath`。  
- **配置を変更できますか？** はい、`setJustification` に LEFT、CENTER、または RIGHT を指定します。  
- **この機能を使用するのにライセンスは必要ですか？** 本番環境で使用する場合は有効な Aspose.Words for Java ライセンスが必要です。  
- **デモで使用しているバージョンは？** コードは最新の Aspose.Words for Java リリース（2026）で動作します。

## 「インラインで数式を表示する」とは？
インラインで数式を表示するとは、数式が段落テキストの一部として扱われ、周囲の単語と自然に折り返されることを意味します。読み進める流れを妨げない短い式に適しています。

## なぜ Aspose.Words for Java で Office Math オブジェクトを使用するのか？
- **正確なレイアウト制御** が可能（インライン vs. ディスプレイ）。  
- **プログラムから数式を操作** でき、Word を手動で開く必要がありません。  
- **プラットフォーム間で一貫したレンダリング** が保証され、自動レポート生成に最適です。

## 前提条件
以下を事前に用意してください：

- プロジェクトに Aspose.Words for Java がインストールされ、参照設定されていること。  
- 既に Office Math 数式が含まれている Word ファイル（例: `OfficeMath.docx`）。  
- 評価モード以外で実行する場合は有効なライセンスを用意すること。

## Step‑by‑Step Guide

### Load the Document
まず、操作対象となる Office Math 数式が含まれる文書を読み込みます：

```java
Document doc = new Document("Your Directory Path" + "OfficeMath.docx");
```

### Access the Office Math Object
文書から最初の Office Math ノードを取得します：

```java
OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
```

### Set Display Type (Inline vs. Display)
数式をテキストと同じ行に表示するか、別行に表示するかを制御します。**インラインで数式を表示** する場合は `INLINE` 列挙体を、別行にしたい場合は `DISPLAY` を使用します：

```java
officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
```

*数式をインラインのままにしたい場合は、`DISPLAY` を `INLINE` に置き換えてください。*

### Set Justification
数式の配置を調整します。以下の例では左揃えにしていますが、`CENTER` や `RIGHT` も選択可能です：

```java
officeMath.setJustification(OfficeMathJustification.LEFT);
```

### Save the Modified Document
変更を新しいファイルに書き出して完了です：

```java
doc.save("Your Directory Path" + "ModifiedOfficeMath.docx");
```

## Complete Source Code for Using Office Math Objects in Aspose.Words for Java

```java
        Document doc = new Document("Your Directory Path" + "Office math.docx");
        OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
        // OfficeMath display type represents whether an equation is displayed inline with the text or displayed on its line.
        officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
        officeMath.setJustification(OfficeMathJustification.LEFT);
        doc.save("Your Directory Path" + "WorkingWithOfficeMath.MathEquations.docx");
```

## Common Issues & Troubleshooting
- **数式が見つからない:** 文書に実際に Office Math オブジェクトが含まれているか確認してください。存在しない場合、`doc.getChild` は `null` を返します。  
- **表示タイプが反映されない:** 使用している Aspose.Words のバージョンが古い可能性があります。`OfficeMathDisplayType` のサポートは比較的新しいリリースで追加されています。  
- **ライセンス例外:** ライセンスエラーが出たら、`Document` インスタンスを作成する前にライセンスファイルが正しくロードされているか再確認してください。

## Frequently Asked Questions

**Q: Aspose.Words for Java の Office Math オブジェクトの目的は何ですか？**  
A: Office Math オブジェクトを使用すると、数式をプログラムから表現・操作でき、表示や書式設定を完全にコントロールできます。

**Q: 文書内の Office Math 数式の配置を個別に変更できますか？**  
A: はい、`setJustification` メソッドで左揃え、右揃え、中央揃えを指定できます。

**Q: 複雑な数式を含む文書の処理に Aspose.Words for Java は適していますか？**  
A: 完全に対応しています。入れ子になった分数や行列、その他高度な数式も問題なく扱えます。

**Q: Aspose.Words for Java の詳細情報はどこで入手できますか？**  
A: 包括的なドキュメントとダウンロードは、[Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/) をご覧ください。

**Q: Aspose.Words for Java はどこからダウンロードできますか？**  
A: 以下のページから入手可能です: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)。

---

**最終更新日:** 2026-02-14  
**テスト環境:** Aspose.Words for Java 24.12（2026年2月時点の最新）  
**作者:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}