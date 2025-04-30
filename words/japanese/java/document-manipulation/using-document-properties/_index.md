---
"description": "Aspose.Words for Javaでドキュメント管理を最適化しましょう。この包括的なチュートリアルでは、ドキュメントプロパティの操作、カスタムメタデータの追加など、様々な方法を学習できます。"
"linktitle": "ドキュメントプロパティの使用"
"second_title": "Aspose.Words Java ドキュメント処理 API"
"title": "Aspose.Words for Java でのドキュメント プロパティの使用"
"url": "/ja/java/document-manipulation/using-document-properties/"
"weight": 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でのドキュメント プロパティの使用


## ドキュメントプロパティの概要

ドキュメントプロパティは、あらゆるドキュメントにとって不可欠な要素です。タイトル、作成者、件名、キーワードなど、ドキュメント自体に関する追加情報を提供します。Aspose.Words for Javaでは、組み込みプロパティとカスタムプロパティの両方を操作できます。

## ドキュメントプロパティの列挙

### 組み込みプロパティ

組み込みのドキュメント プロパティを取得して操作するには、次のコード スニペットを使用できます。

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

このコードは、ドキュメントの名前と組み込みプロパティ（「タイトル」、「作成者」、「キーワード」などのプロパティを含む）を表示します。

### カスタムプロパティ

カスタム ドキュメント プロパティを操作するには、次のコード スニペットを使用できます。

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

このコード スニペットは、ブール値、文字列、日付、リビジョン番号、数値などのカスタム ドキュメント プロパティを追加する方法を示しています。

## ドキュメントプロパティの削除

特定のドキュメント プロパティを削除するには、次のコードを使用できます。

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

このコードは、ドキュメントからカスタム プロパティ「承認日」を削除します。

## コンテンツへのリンクの設定

場合によっては、ドキュメント内にリンクを作成したいことがあります。その方法は次のとおりです。

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

    // コンテンツプロパティにリンクを追加します。
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

このコード スニペットは、ドキュメント内にブックマークを作成し、そのブックマークにリンクするカスタム ドキュメント プロパティを追加する方法を示しています。

## 測定単位の変換

Aspose.Words for Java では、測定単位を簡単に変換できます。以下に例を示します。

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // 余白をインチ単位で設定します。
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

このコード スニペットは、さまざまな余白と距離をインチ単位でポイントに変換して設定します。

## 制御文字の使用

制御文字はテキストを扱う際に便利です。テキスト内の制御文字を置換する方法は次のとおりです。

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // 「\r」制御文字を「\r\n」に置き換えます。
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

この例では、キャリッジリターン（`\r`）に続いて改行（`\r\n`）。

## 結論

Aspose.Words for Java では、ドキュメントプロパティがドキュメントを効果的に管理・整理する上で重要な役割を果たします。組み込みプロパティ、カスタムプロパティ、制御文字など、ドキュメント管理機能を強化するための様々なツールをご利用いただけます。

## よくある質問

### 組み込みドキュメント プロパティにアクセスするにはどうすればよいですか?

Aspose.Words for Javaの組み込みドキュメントプロパティにアクセスするには、 `getBuiltInDocumentProperties` 方法 `Document` オブジェクト。このメソッドは、反復処理できる組み込みプロパティのコレクションを返します。

### ドキュメントにカスタム ドキュメント プロパティを追加できますか?

はい、カスタムドキュメントプロパティをドキュメントに追加できます。 `CustomDocumentProperties` コレクション。文字列、ブール値、日付、数値など、さまざまなデータ型のカスタム プロパティを定義できます。

### 特定のカスタム ドキュメント プロパティを削除するにはどうすればよいですか?

特定のカスタムドキュメントプロパティを削除するには、 `remove` 方法 `CustomDocumentProperties` コレクションに、削除するプロパティの名前をパラメータとして渡します。

### ドキュメント内のコンテンツにリンクする目的は何ですか?

ドキュメント内のコンテンツへのリンクを設定すると、ドキュメントの特定の部分への動的な参照を作成できます。これは、インタラクティブなドキュメントやセクション間の相互参照を作成する際に便利です。

### Aspose.Words for Java で異なる測定単位を変換するにはどうすればよいですか?

Aspose.Words for Javaでは、以下の方法で異なる測定単位を変換することができます。 `ConvertUtil` クラスです。インチをポイントに、ポイントをセンチメートルになど、単位を変換するメソッドを提供します。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}