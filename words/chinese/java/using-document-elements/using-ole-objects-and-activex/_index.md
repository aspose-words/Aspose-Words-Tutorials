---
"description": "学习在 Aspose.Words for Java 中使用 OLE 对象和 ActiveX 控件。轻松创建交互式文档。立即开始！"
"linktitle": "使用 OLE 对象和 ActiveX 控件"
"second_title": "Aspose.Words Java文档处理API"
"title": "在 Aspose.Words for Java 中使用 OLE 对象和 ActiveX 控件"
"url": "/zh/java/using-document-elements/using-ole-objects-and-activex/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中使用 OLE 对象和 ActiveX 控件

在本教程中，我们将探索如何在 Aspose.Words for Java 中使用 OLE（对象链接与嵌入）对象和 ActiveX 控件。OLE 对象和 ActiveX 控件是功能强大的工具，可让您通过嵌入或链接外部内容（例如电子表格、多媒体文件或交互式控件）来增强文档效果。请跟随我们深入研究代码示例，学习如何有效地使用这些功能。

### 先决条件

在开始之前，请确保您已满足以下先决条件：

1. Aspose.Words for Java：确保你的 Java 项目中已安装 Aspose.Words 库。你可以从 [这里](https://releases。aspose.com/words/java/).

2. Java 开发环境：您应该在系统上设置一个可运行的 Java 开发环境。

### 插入 OLE 对象

首先，我们将在 Word 文档中插入一个 OLE 对象。我们将创建一个简单的 Word 文档，然后插入一个代表网页的 OLE 对象。

```java
string outPath = "Your Output Directory";
public void insertOleObject() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObject("http://www.aspose.com”， “htmlfile”， true，true，null）；
    doc.save("Your Directory Path" + "WorkingWithOleObjectsAndActiveX.InsertOleObject.docx");
}
```

在这段代码中，我们创建一个新文档，并插入一个显示 Aspose 网站的 OLE 对象。您可以将 URL 替换为所需的内容。

### 使用 OlePackage 插入 OLE 对象

接下来，我们来探索如何使用 OlePackage 插入 OLE 对象。这允许您将外部文件作为 OLE 对象嵌入到文档中。

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

在此示例中，我们使用 OlePackage 插入一个 OLE 对象，允许您将外部文件作为嵌入对象包含在内。

### 将 OLE 对象作为图标插入

现在，我们来看看如何将 OLE 对象作为图标插入。当你想显示一个代表嵌入文件的图标时，这很有用。

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

在此代码中，我们插入一个 OLE 对象作为图标，以提供嵌入内容的更具视觉吸引力的表示。

### 读取 ActiveX 控件属性

现在，让我们将焦点转移到 ActiveX 控件上。我们将学习如何在 Word 文档中读取 ActiveX 控件的属性。

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

在此代码中，我们遍历 Word 文档中的形状，识别 ActiveX 控件并检索它们的属性。

### 结论

恭喜！您已经学习了如何在 Aspose.Words for Java 中使用 OLE 对象和 ActiveX 控件。这些功能为创建动态交互式文档开辟了无限可能。

### 常见问题解答

### Word 文档中的 OLE 对象的用途是什么？ 
   - OLE 对象允许您在 Word 文档中嵌入或链接外部内容，例如文件或网页。

### 我可以自定义文档中 OLE 对象的外观吗？ 
   - 是的，您可以自定义 OLE 对象的外观，包括设置图标和文件名。

### 什么是 ActiveX 控件？它们如何增强我的文档？ 
   - ActiveX 控件是可以为 Word 文档添加功能的交互式元素，例如表单控件或多媒体播放器。

### Aspose.Words for Java 适合企业级文档自动化吗？ 
   - 是的，Aspose.Words for Java 是一个功能强大的库，用于自动生成和处理 Java 应用程序中的文档。

### 在哪里可以访问 Aspose.Words for Java？ 
   - 您可以从以下位置下载 Aspose.Words for Java [这里](https://releases。aspose.com/words/java/).

立即开始使用 Aspose.Words for Java 并释放文档自动化和定制的全部潜力！



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}