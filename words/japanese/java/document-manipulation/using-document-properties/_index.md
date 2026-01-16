---
date: 2026-01-16
description: Aspose.Words for Java を使用して、インチをポイントに変換する方法、Java でドキュメントのメタデータを読み取る方法、カスタムプロパティを追加する方法、ページ余白を設定する方法を学びます。
linktitle: Using Document Properties
second_title: Aspose.Words Java Document Processing API
title: インチからポイントへ変換 – Aspose.Words for Java のドキュメント プロパティを使用
url: /ja/java/document-manipulation/using-document-properties/
weight: 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# インチをポイントに変換 – Aspose.Words for Java のドキュメントプロパティを使用する方法

このチュートリアルでは、ページ余白を設定する際の **インチをポイントに変換** の方法、Java でのドキュメントメタデータの読み取り、カスタムプロパティの追加、組み込みドキュメントプロパティの操作について学びます。レポート、請求書、法的文書の生成において、これらのテクニックを習得すれば、Word ファイルの外観とメタデータを細かく制御できます。

## クイック回答
- **インチをポイントに変換するには？** Aspose.Words の `ConvertUtil.inchToPoint(value)` を使用します。  
- **Java でドキュメントメタデータを読み取れる？** はい – `doc.getBuiltInDocumentProperties()` または `doc.getCustomDocumentProperties()` を呼び出します。  
- **Java でカスタムプロパティを追加するには？** `doc.getCustomDocumentProperties().add(name, value)` を使用します。  
- **ポイント単位でページ余白を設定するメソッドは？** `PageSetup.setTopMargin`、`setBottomMargin` などはポイント値を受け取ります。  
- **ブックマークへのリンクはサポートされている？** はい – カスタムプロパティコレクションの `addLinkToContent` を使用します。

## ドキュメントプロパティの概要

ドキュメントプロパティは Word ファイルにとって重要な要素です。タイトル、作成者、テーマ、キーワード、そして下流処理に必要なカスタムメタデータなどを格納します。Aspose.Words for Java では、組み込みプロパティとカスタムプロパティの両方を操作でき、余白などのレイアウト詳細も単位変換（例：**インチをポイントに変換**）で制御できます。

## 「インチをポイントに変換」とは？

Word のレイアウト測定はポイントで表されます（1 ポイント = 1/72 インチ）。インチをポイントに変換することで、慣れ親しんだインペリアル単位で余白やインデント、間隔を指定でき、API は内部的にポイントを扱います。

## Java でドキュメントメタデータを管理する理由

メタデータを埋め込むことで、検索・分類・ワークフローの自動化が容易になります。たとえば、契約書に「Authorized」フラグを付与したり、監査用にリビジョン番号を保存したりできます。プログラムで読み書きすることで、大量のドキュメント間で一貫性を保てます。

## 前提条件
- Java 17+（または互換性のある JDK）
- Aspose.Words for Java ライブラリをプロジェクトに追加（Maven/Gradle）
- サンプル `.docx` ファイル（例: `Properties.docx`）をアクセス可能なディレクトリに配置

## 手順ガイド

### 組み込みドキュメントプロパティの列挙
以下はドキュメントを開き、Title、Author、Keywords などの組み込みプロパティをすべて出力するシンプルなテストです。

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

> **プロのコツ:** このスニペットを使って、メタデータが前段階で正しく書き込まれたかを確認できます。

### カスタムドキュメントプロパティの追加（add custom properties java）
カスタムプロパティは任意のデータ型（ブール、文字列、日付、数値など）を格納できます。

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

> **重要性:** **Authorized** のようなフラグを追加すれば、ドキュメント内容を変更せずに承認フローを駆動できます。

### カスタムプロパティの削除
不要になったプロパティはきれいに削除できます。

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

### コンテンツへのリンク設定（ブックマークリンク）
ブックマークを作成し、そこへ指すカスタムプロパティを追加すると、動的な相互参照が可能になります。

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Add linked to content property.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

### 測定単位の変換（set page margins java）
ここが主要キーワードの出番です。余白をインチで指定し、`ConvertUtil` で **インチをポイントに変換** します。

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Set margins in inches.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

> **注記:** `ConvertUtil` には `pointToInch`、`mmToPoint` など、柔軟なレイアウト処理用メソッドも用意されています。

### 制御文字の使用（read document metadata java）
制御文字はテキストストリームのクリーンアップに役立ちます。この例ではキャリッジリターン（`\r`）を Windows の改行シーケンス（`\r\n`）に置換しています。

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Replace "\r" control character with "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

## よくある問題と解決策
| 問題 | 原因 | 対策 |
|------|------|------|
| 変換後の余白がずれる | 単位ミス（例: cm を使用） | インインチ値には必ず `ConvertUtil.inchToPoint` を呼び出す |
| カスタムプロパティが表示されない | プロパティ追加後に保存していない | プロパティ追加後に `doc.save(...)` を実行 |
| ブックマークリンクが切れる | ブックマーク名のタイプミス | `addLinkToContent` のブックマーク名が正確に一致しているか確認 |

## FAQ

### 組み込みドキュメントプロパティへのアクセス方法は？

Aspose.Words for Java では、`Document` オブジェクトの `getBuiltInDocumentProperties` メソッドを使用します。このメソッドは組み込みプロパティのコレクションを返し、イテレーションが可能です。

### カスタムドキュメントプロパティを追加できますか？

はい。`CustomDocumentProperties` コレクションを介して、文字列、ブール、日付、数値など様々なデータ型のカスタムプロパティを定義できます。

### 特定のカスタムドキュメントプロパティを削除するには？

`CustomDocumentProperties` コレクションの `remove` メソッドにプロパティ名を渡すことで削除できます。

### ドキュメント内コンテンツへのリンクの目的は？

コンテンツへのリンクは、文書内の特定部分への動的参照を作成します。インタラクティブ文書やセクション間の相互参照に有用です。

### Aspose.Words for Java で測定単位を変換する方法は？

`ConvertUtil` クラスを使用します。インチからポイント、ポイントからセンチメートルなど、様々な単位変換メソッドが提供されています。

## Frequently Asked Questions

**Q: Document metadata を Java で、ファイル全体をロードせずに取得するには？**  
A: `DocumentInfo` を使用すれば、コンテンツを完全にロードせずにコアプロパティを取得できます。

**Q: 既存ドキュメントのページ余白を Java でプログラム的に設定できる？**  
A: はい。ドキュメントを開き、`PageSetup` の余白を（必要ならインチをポイントに変換して）変更し、保存します。

**Q: カスタムプロパティを PDF メタデータにエクスポートできる？**  
A: PDF に保存する際、Aspose.Words はカスタムドキュメントプロパティを PDF のカスタムメタデータへ自動的にマッピングします。

**Q: 制御文字は PDF 変換に影響するか？**  
A: 変換時に保持されますが、一貫性のために改行コードを正規化しておくと良いでしょう。

**Q: `ConvertUtil` を使用するのに必要な Aspose.Words のバージョンは？**  
A: `ConvertUtil` は Aspose.Words 16.5 以降に実装されており、最新バージョンであれば利用可能です。

## 結論

**インチをポイントに変換**、Java でのドキュメントメタデータの読み取り、カスタムプロパティの追加をマスターすれば、Word ファイルの見た目と隠れたデータの両方を完全にコントロールできます。これにより、ドキュメントパイプラインの自動化、コンプライアンスの強化、リッチレポートの作成が実現し、すべて Aspose.Words for Java で実現できます。

---

**最終更新日:** 2026-01-16  
**テスト環境:** Aspose.Words for Java 24.11  
**作者:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}