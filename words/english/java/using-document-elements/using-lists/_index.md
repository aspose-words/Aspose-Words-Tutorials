---
title: Using Lists in Aspose.Words for Java
linktitle: Using Lists
second_title: Aspose.Words Java Document Processing API
description: Learn to use lists in Aspose.Words for Java with this step-by-step tutorial. Organize and format your documents effectively.
weight: 18
url: /java/using-document-elements/using-lists/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Using Lists in Aspose.Words for Java


In this comprehensive tutorial, we'll explore how to effectively use lists in Aspose.Words for Java, a powerful API for working with Microsoft Word documents programmatically. Lists are essential for structuring and organizing content in your documents. We'll cover two key aspects of working with lists: restarting lists at each section and specifying list levels. Let's dive in!

## Introduction to Aspose.Words for Java

Before we start working with lists, let's get acquainted with Aspose.Words for Java. This API provides developers with the tools to create, modify, and manipulate Word documents in a Java environment. It's a versatile solution for tasks ranging from simple document generation to complex formatting and content management.

### Setting Up Your Environment

To begin, make sure you have Aspose.Words for Java installed and set up in your development environment. You can download it [here](https://releases.aspose.com/words/java/). 

## Restarting Lists at Each Section

In many scenarios, you might need to restart lists at each section of your document. This can be useful for creating structured documents with multiple sections, such as reports, manuals, or academic papers.

Here's a step-by-step guide on how to achieve this using Aspose.Words for Java:

### Initialize Your Document: 
Start by creating a new document object.

```java
Document doc = new Document();
```

### Add a Numbered List: 
Add a numbered list to your document. We'll use the default numbering style.

```java
doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
```

### Configure List Settings: 
\Enable the list to restart at each section.

```java
List list = doc.getLists().get(0);
list.isRestartAtEachSection(true);
```

### DocumentBuilder Setup: 
Create a DocumentBuilder to add content to your document.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getListFormat().setList(list);
```

### Add List Items: 
Use a loop to add list items to your document. We'll insert a section break after the 15th item.

```java
for (int i = 1; i < 45; i++) {
    builder.writeln(MessageFormat.format("List Item {0}", i));
    if (i == 15)
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
}
```

### Save Your Document: 
Save the document with the desired options.

```java
OoxmlSaveOptions options = new OoxmlSaveOptions();
options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);
doc.save(outPath + "RestartListAtEachSection.docx", options);
```

By following these steps, you can create documents with lists that restart at each section, maintaining clear and organized content structure.

## Specifying List Levels

Aspose.Words for Java allows you to specify list levels, which is particularly useful when you need different list formats within your document. Let's explore how to do this:

### Initialize Your Document: 
Create a new document object.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Create a Numbered List: 
Apply a numbered list template from Microsoft Word.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
```

### Specify List Levels: 
Iterate through different list levels and add content.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Create a Bulleted List: 
Now, let's create a bulleted list.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
```

### Specify Bulleted List Levels: 
Similar to the numbered list, specify levels and add content.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Stop List Formatting: 
To stop list formatting, set the list to null.

```java
builder.getListFormat().setList(null);
```

### Save Your Document: 
Save the document.

```java
builder.getDocument().save(outPath + "SpecifyListLevel.docx");
```

By following these steps, you can create documents with custom list levels, allowing you to control the formatting of lists in your documents.

## Complete Source Code
```java
	string outPath = "Your Output Directory";
 public void restartListAtEachSection() throws Exception
    {
        Document doc = new Document();
        doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
        List list = doc.getLists().get(0);
        list.isRestartAtEachSection(true);
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.getListFormat().setList(list);
        for (int i = 1; i < 45; i++)
        {
            builder.writeln(MessageFormat.format("List Item {0}", i));
            if (i == 15)
                builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        }
        // IsRestartAtEachSection will be written only if compliance is higher then OoxmlComplianceCore.Ecma376.
        OoxmlSaveOptions options = new OoxmlSaveOptions(); { options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL); }
        doc.save(outPath + "WorkingWithList.RestartListAtEachSection.docx", options);
    }
    @Test
    public void specifyListLevel() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a numbered list based on one of the Microsoft Word list templates
        // and apply it to the document builder's current paragraph.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
        // There are nine levels in this list, let's try them all.
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Create a bulleted list based on one of the Microsoft Word list templates
        // and apply it to the document builder's current paragraph.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // This is a way to stop list formatting.
        builder.getListFormat().setList(null);
        builder.getDocument().save(outPath + "WorkingWithList.SpecifyListLevel.docx");
    }
    @Test
    public void restartListNumber() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a list based on a template.
        List list1 = doc.getLists().add(ListTemplate.NUMBER_ARABIC_PARENTHESIS);
        list1.getListLevels().get(0).getFont().setColor(Color.RED);
        list1.getListLevels().get(0).setAlignment(ListLevelAlignment.RIGHT);
        builder.writeln("List 1 starts below:");
        builder.getListFormat().setList(list1);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        // To reuse the first list, we need to restart numbering by creating a copy of the original list formatting.
        List list2 = doc.getLists().addCopy(list1);
        // We can modify the new list in any way, including setting a new start number.
        list2.getListLevels().get(0).setStartAt(10);
        builder.writeln("List 2 starts below:");
        builder.getListFormat().setList(list2);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        builder.getDocument().save(outPath + "WorkingWithList.RestartListNumber.docx");
	}
```

## Conclusion

Congratulations! You've learned how to work with lists in Aspose.Words for Java effectively. Lists are crucial for organizing and presenting content in your documents. Whether you need to restart lists at each section or specify list levels, Aspose.Words for Java provides the tools you need to create professional-looking documents.

Now you can confidently use these features to enhance your document generation and formatting tasks. If you have any questions or need further assistance, don't hesitate to reach out to the [Aspose community forum](https://forum.aspose.com/) for support.

## FAQs

### How do I install Aspose.Words for Java?
You can download Aspose.Words for Java from [here](https://releases.aspose.com/words/java/) and follow the installation instructions in the documentation.

### Can I customize the numbering format of lists?
Yes, Aspose.Words for Java provides extensive options for customizing list numbering formats. You can refer to the API documentation for details.

### Is Aspose.Words for Java compatible with the latest Word document standards?
Yes, you can configure Aspose.Words for Java to comply with various Word document standards, including ISO 29500.

### Can I generate complex documents with tables and images using Aspose.Words for Java?
Absolutely! Aspose.Words for Java supports advanced document formatting, including tables, images, and more. Check the documentation for examples.

### Where can I get a temporary license for Aspose.Words for Java?
You can obtain a temporary license [here](https://purchase.aspose.com/temporary-license/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
