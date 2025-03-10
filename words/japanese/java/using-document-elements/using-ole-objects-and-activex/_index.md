---
title: Aspose.Words for Java での OLE オブジェクトと ActiveX コントロールの使用
linktitle: OLE オブジェクトと ActiveX コントロールの使用
second_title: Aspose.Words Java ドキュメント処理 API
description: Aspose.Words for Java で OLE オブジェクトと ActiveX コントロールを使用する方法を学びます。インタラクティブなドキュメントを簡単に作成できます。今すぐ始めましょう!
weight: 21
url: /ja/java/using-document-elements/using-ole-objects-and-activex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java での OLE オブジェクトと ActiveX コントロールの使用

このチュートリアルでは、Aspose.Words for Java で OLE (オブジェクトのリンクと埋め込み) オブジェクトと ActiveX コントロールを操作する方法について説明します。OLE オブジェクトと ActiveX コントロールは、スプレッドシート、マルチメディア ファイル、対話型コントロールなどの外部コンテンツを埋め込んだりリンクしたりすることでドキュメントを強化できる強力なツールです。コード例を詳しく調べながら、これらの機能を効果的に使用する方法を学習してください。

### 前提条件

始める前に、次の前提条件が満たされていることを確認してください。

1.  Aspose.Words for Java: JavaプロジェクトにAspose.Wordsライブラリがインストールされていることを確認してください。ここからダウンロードできます。[ここ](https://releases.aspose.com/words/java/).

2. Java 開発環境: システムに動作する Java 開発環境が設定されている必要があります。

### OLE オブジェクトの挿入

まず、Word 文書に OLE オブジェクトを挿入してみましょう。簡単な Word 文書を作成し、Web ページを表す OLE オブジェクトを挿入します。

```java
string outPath = "Your Output Directory";
public void insertOleObject() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObject("http://www.aspose.com", "htmlfile", true, true, null);
    doc.save("Your Directory Path" + "WorkingWithOleObjectsAndActiveX.InsertOleObject.docx");
}
```

このコードでは、新しいドキュメントを作成し、Aspose Web サイトを表示する OLE オブジェクトを挿入します。URL を目的のコンテンツに置き換えることができます。

### OlePackage を使用した OLE オブジェクトの挿入

次に、OlePackage を使用して OLE オブジェクトを挿入する方法を説明します。これにより、外部ファイルを OLE オブジェクトとしてドキュメントに埋め込むことができます。

```java
@Test
public void insertOleObjectWithOlePackage() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    byte[] bs = FileUtils.readFileToByteArray(new File("Your Directory Path" + "Zip file.zip"));
    try (ByteArrayInputStream stream = new ByteArrayInputStream(bs))
    {
        Shape shape = builder.insertOleObject(stream, "Package", true, null);
        OlePackage olePackage = shape.getOleFormat().getOlePackage();
        olePackage.setFileName("filename.zip");
        olePackage.setDisplayName("displayname.zip");
        doc.save(outPath + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
    }
}
```

この例では、OlePackage を使用して OLE オブジェクトを挿入し、外部ファイルを埋め込みオブジェクトとして含めることができるようになります。

### OLE オブジェクトをアイコンとして挿入する

ここで、OLE オブジェクトをアイコンとして挿入する方法を見てみましょう。これは、埋め込まれたファイルを表すアイコンを表示する場合に便利です。

```java
@Test
public void insertOleObjectAsIcon() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObjectAsIcon("Your Directory Path" + "Presentation.pptx", false, getImagesDir() + "Logo icon.ico", "My embedded file");
    doc.save(outPath + "WorkingWithOleObjectsAndActiveX.InsertOleObjectAsIcon.docx");
}
```

このコードでは、OLE オブジェクトをアイコンとして挿入し、埋め込まれたコンテンツを視覚的に魅力的な形で表現します。

### ActiveX コントロールのプロパティの読み取り

さて、焦点を ActiveX コントロールに移しましょう。Word 文書内の ActiveX コントロールのプロパティを読み取る方法を学習します。

```java
@Test
public void readActiveXControlProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "ActiveX controls.docx");
    String properties = "";
    for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true))
    {
        if (shape.getOleFormat() == null) break;
        OleControl oleControl = shape.getOleFormat().getOleControl();
        if (oleControl.isForms2OleControl())
        {
            Forms2OleControl checkBox = (Forms2OleControl) oleControl;
            properties = properties + "\nCaption: " + checkBox.getCaption();
            properties = properties + "\nValue: " + checkBox.getValue();
            properties = properties + "\nEnabled: " + checkBox.getEnabled();
            properties = properties + "\nType: " + checkBox.getType();
            if (checkBox.getChildNodes() != null)
            {
                properties = properties + "\nChildNodes: " + checkBox.getChildNodes();
            }
            properties += "\n";
        }
    }
    properties = properties + "\nTotal ActiveX Controls found: " + doc.getChildNodes(NodeType.SHAPE, true).getCount();
    System.out.println("\n" + properties);
}
```

このコードでは、Word 文書内の図形を反復処理し、ActiveX コントロールを識別して、そのプロパティを取得します。

### 結論

おめでとうございます。Aspose.Words for Java で OLE オブジェクトと ActiveX コントロールを操作する方法を学習しました。これらの機能により、動的でインタラクティブなドキュメントを作成するための可能性が広がります。

### よくある質問

### Word 文書内の OLE オブジェクトの目的は何ですか? 
   - OLE オブジェクトを使用すると、Word 文書内にファイルや Web ページなどの外部コンテンツを埋め込んだりリンクしたりできます。

### ドキュメント内の OLE オブジェクトの外観をカスタマイズできますか? 
   - はい、アイコンやファイル名の設定など、OLE オブジェクトの外観をカスタマイズできます。

### ActiveX コントロールとは何ですか? また、ActiveX コントロールによってドキュメントをどのように強化できますか? 
   - ActiveX コントロールは、フォーム コントロールやマルチメディア プレーヤーなど、Word 文書に機能を追加できるインタラクティブな要素です。

### Aspose.Words for Java はエンタープライズ レベルのドキュメント自動化に適していますか? 
   - はい、Aspose.Words for Java は、Java アプリケーションでのドキュメントの生成と操作を自動化するための強力なライブラリです。

### Aspose.Words for Java にはどこでアクセスできますか? 
   -  Aspose.Words for Javaは以下からダウンロードできます。[ここ](https://releases.aspose.com/words/java/).

今すぐ Aspose.Words for Java を使い始めて、ドキュメントの自動化とカスタマイズの可能性を最大限に引き出しましょう。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
