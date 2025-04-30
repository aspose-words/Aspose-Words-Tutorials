---
"description": "Aspose.Words for JavaでOLEオブジェクトとActiveXコントロールの使い方を学びましょう。インタラクティブなドキュメントを簡単に作成できます。今すぐ始めましょう！"
"linktitle": "OLE オブジェクトと ActiveX コントロールの使用"
"second_title": "Aspose.Words Java ドキュメント処理 API"
"title": "Aspose.Words for Java での OLE オブジェクトと ActiveX コントロールの使用"
"url": "/ja/java/using-document-elements/using-ole-objects-and-activex/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java での OLE オブジェクトと ActiveX コントロールの使用

このチュートリアルでは、Aspose.Words for Java で OLE (Object Linking and Embedding) オブジェクトと ActiveX コントロールを操作する方法を学びます。OLE オブジェクトと ActiveX コントロールは、スプレッドシート、マルチメディアファイル、インタラクティブコントロールなどの外部コンテンツを埋め込んだりリンクしたりすることで、ドキュメントの機能を強化できる強力なツールです。コード例を詳しく見ながら、これらの機能を効果的に使用する方法を学んでいきましょう。

### 前提条件

始める前に、次の前提条件が満たされていることを確認してください。

1. Aspose.Words for Java: JavaプロジェクトにAspose.Wordsライブラリがインストールされていることを確認してください。ダウンロードはこちらから可能です。 [ここ](https://releases。aspose.com/words/java/).

2. Java 開発環境: システムに動作する Java 開発環境が設定されている必要があります。

### OLEオブジェクトの挿入

まず、Word文書にOLEオブジェクトを挿入してみましょう。簡単なWord文書を作成し、Webページを表すOLEオブジェクトを挿入します。

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

このコードでは、新しいドキュメントを作成し、Aspose Webサイトを表示するOLEオブジェクトを挿入します。URLは必要なコンテンツに置き換えることができます。

### OlePackage を使用した OLE オブジェクトの挿入

次に、OlePackageを使ってOLEオブジェクトを挿入する方法を見てみましょう。これにより、外部ファイルをOLEオブジェクトとしてドキュメントに埋め込むことができます。

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

それでは、OLEオブジェクトをアイコンとして挿入する方法を見てみましょう。これは、埋め込まれたファイルを表すアイコンを表示したい場合に便利です。

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

さて、次はActiveXコントロールに焦点を当てましょう。Word文書内のActiveXコントロールのプロパティを読み取る方法を学びます。

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

おめでとうございます！Aspose.Words for JavaでOLEオブジェクトとActiveXコントロールを操作する方法を習得しました。これらの機能により、ダイナミックでインタラクティブなドキュメントを作成するための可能性が無限に広がります。

### よくある質問

### Word 文書における OLE オブジェクトの目的は何ですか? 
   - OLE オブジェクトを使用すると、Word 文書内にファイルや Web ページなどの外部コンテンツを埋め込んだりリンクしたりすることができます。

### ドキュメント内の OLE オブジェクトの外観をカスタマイズできますか? 
   - はい、アイコンやファイル名の設定など、OLE オブジェクトの外観をカスタマイズできます。

### ActiveX コントロールとは何ですか? また、ActiveX コントロールによってドキュメントをどのように強化できますか? 
   - ActiveX コントロールは、フォーム コントロールやマルチメディア プレーヤーなど、Word 文書に機能を追加できるインタラクティブな要素です。

### Aspose.Words for Java はエンタープライズ レベルのドキュメント自動化に適していますか? 
   - はい、Aspose.Words for Java は、Java アプリケーションでのドキュメント生成と操作を自動化する強力なライブラリです。

### Aspose.Words for Java にはどこでアクセスできますか? 
   - Aspose.Words for Javaは以下からダウンロードできます。 [ここ](https://releases。aspose.com/words/java/).

今すぐ Aspose.Words for Java を使い始めて、ドキュメントの自動化とカスタマイズの可能性を最大限に引き出しましょう。



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}