---
title: Using OLE Objects and ActiveX Controls in Aspose.Words for Java
linktitle: Using OLE Objects and ActiveX Controls
second_title: Aspose.Words Java Document Processing API
description: Learn to use OLE objects and ActiveX controls in Aspose.Words for Java. Create interactive documents with ease. Get started now!
weight: 21
url: /java/using-document-elements/using-ole-objects-and-activex/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Using OLE Objects and ActiveX Controls in Aspose.Words for Java

In this tutorial, we will explore how to work with OLE (Object Linking and Embedding) objects and ActiveX controls in Aspose.Words for Java. OLE objects and ActiveX controls are powerful tools that allow you to enhance your documents by embedding or linking external content, such as spreadsheets, multimedia files, or interactive controls. Follow along as we delve into the code examples and learn how to use these features effectively.

### Prerequisites

Before we get started, make sure you have the following prerequisites in place:

1. Aspose.Words for Java : Ensure you have the Aspose.Words library installed in your Java project. You can download it from [here](https://releases.aspose.com/words/java/).

2. Java Development Environment : You should have a working Java development environment set up on your system.

### Inserting an OLE Object

Let's begin by inserting an OLE object into a Word document. We'll create a simple Word document and then insert an OLE object representing a web page.

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

In this code, we create a new document and insert an OLE object that displays the Aspose website. You can replace the URL with the desired content.

### Inserting an OLE Object with OlePackage

Next, let's explore how to insert an OLE object using an OlePackage. This allows you to embed external files as OLE objects in your document.

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

In this example, we insert an OLE object using an OlePackage, allowing you to include external files as embedded objects.

### Inserting an OLE Object as an Icon

Now, let's see how to insert an OLE object as an icon. This is useful when you want to display an icon representing an embedded file.

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

In this code, we insert an OLE object as an icon, providing a more visually appealing representation of the embedded content.

### Reading ActiveX Control Properties

Now, let's shift our focus to ActiveX controls. We'll learn how to read properties of ActiveX controls within a Word document.

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

In this code, we iterate through the shapes in a Word document, identify ActiveX controls, and retrieve their properties.

### Conclusion

Congratulations! You've learned how to work with OLE objects and ActiveX controls in Aspose.Words for Java. These features open up a world of possibilities for creating dynamic and interactive documents.

### FAQs

### What is the purpose of OLE objects in a Word document? 
   - OLE objects allow you to embed or link external content, such as files or web pages, within a Word document.

### Can I customize the appearance of OLE objects in my document? 
   - Yes, you can customize the appearance of OLE objects, including setting icons and filenames.

### What are ActiveX controls, and how can they enhance my documents? 
   - ActiveX controls are interactive elements that can add functionality to your Word documents, such as form controls or multimedia players.

### Is Aspose.Words for Java suitable for enterprise-level document automation? 
   - Yes, Aspose.Words for Java is a powerful library for automating document generation and manipulation in Java applications.

### Where can I get access to Aspose.Words for Java? 
   - You can download Aspose.Words for Java from [here](https://releases.aspose.com/words/java/).

Get started with Aspose.Words for Java today and unlock the full potential of document automation and customization!



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
