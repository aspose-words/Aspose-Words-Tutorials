---
title: Comparison Granularity In Word Document
linktitle: Comparison Granularity In Word Document
second_title: Aspose.Words Document Processing API
description: Learn Compare Granularity in word document feature of Aspose.Words for .NET that allows documents to be compared character by character, reporting changes made.
weight: 10
url: /net/compare-documents/comparison-granularity/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Comparison Granularity In Word Document

Here is a step-by-step guide to explain the C# source code below, which uses the Compare Granularity in word document feature of Aspose.Words for .NET.

## Step 1: Introduction

The Compare Granularity feature of Aspose.Words for .NET allows you to compare documents at the character level. This means that each character will be compared and changes will be reported accordingly.

## Step 2: Setting up the environment

Before you start, you need to set up your development environment to work with Aspose.Words for .NET. Make sure you have the Aspose.Words library installed and have a suitable C# project to embed the code in.

## Step 3: Add Required Assemblies

To use the Compare Granularity feature of Aspose.Words for .NET, you need to add the necessary assemblies to your project. Make sure you have the proper references to Aspose.Words in your project.

```csharp
using Aspose.Words;
using Aspose.Words.DocumentBuilder;
```

## Step 4: Creating Documents

In this step, we will create two documents using the DocumentBuilder class. These documents will be used for the comparison.

```csharp
// Create document A.
DocumentBuilder builderA = new DocumentBuilder(new Document());
builderA.Writeln("This is a simple A word.");

// Create document B.
DocumentBuilder builderB = new DocumentBuilder(new Document());
builderB.Writeln("This is simple B words.");
```

## Step 5: Configuring Compare Options

In this step, we will configure the comparison options to specify the comparison granularity. Here we will use character-level granularity.

```csharp
CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };
```

## Step 6: Document Comparison

Now let's compare the documents using the Compare method of the Document class. Changes will be saved in document A.

```csharp
builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);
```

The `Compare` method compares document A with document B and saves the changes to document A. You can specify the author's name and the date of comparison for reference.

## Conclusion

In this article, we explored the Compare Granularity feature of Aspose.Words for .NET. This feature allows you to compare documents at the character level and report changes. You can use this knowledge to perform detailed document comparisons in your projects.

### Sample source code for Comparison Granularity using Aspose.Words for .NET

```csharp
            
DocumentBuilder builderA = new DocumentBuilder(new Document());
DocumentBuilder builderB = new DocumentBuilder(new Document());

builderA.Writeln("This is A simple word");
builderB.Writeln("This is B simple words");

CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };

builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);            
        
```

## Conclusion

In this tutorial, we explored the Comparison Granularity feature of Aspose.Words for .NET. This feature allows you to specify the level of detail when comparing documents. By choosing different granularity levels, you can perform detailed comparisons at the character, word, or block level, depending on your specific requirements. Aspose.Words for .NET provides a flexible and powerful document comparison capability, making it easy to identify differences in documents with varying levels of granularity.

### FAQ's

#### Q: What is the purpose of using Comparison Granularity in Aspose.Words for .NET?

A: Comparison Granularity in Aspose.Words for .NET allows you to specify the level of detail when comparing documents. With this feature, you can compare documents at different levels, such as character-level, word-level, or even block-level. Each level of granularity provides a different level of detail in the comparison results.

#### Q: How do I use Comparison Granularity in Aspose.Words for .NET?

A: To use Comparison Granularity in Aspose.Words for .NET, follow these steps:
1. Set up your development environment with the Aspose.Words library.
2. Add the necessary assemblies to your project by referencing Aspose.Words.
3. Create the documents that you want to compare using the `DocumentBuilder` class.
4. Configure the comparison options by creating a `CompareOptions` object and setting the `Granularity` property to the desired level (e.g., `Granularity.CharLevel` for character-level comparison).
5. Use the `Compare` method on one document, passing the other document and the `CompareOptions` object as parameters. This method will compare the documents based on the specified granularity and save the changes in the first document.

#### Q: What are the available levels of Comparison Granularity in Aspose.Words for .NET?

A: Aspose.Words for .NET provides three levels of Comparison Granularity:
- `Granularity.CharLevel`: Compares documents at the character level.
- `Granularity.WordLevel`: Compares documents at the word level.
- `Granularity.BlockLevel`: Compares documents at the block level.

#### Q: How can I interpret the comparison results with character-level granularity?

A: With character-level granularity, each character in the compared documents is analyzed for differences. The comparison results will show changes at the individual character level, including additions, deletions, and modifications.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
