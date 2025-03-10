---
title: Show Hide Bookmarked Content In Word Document
linktitle: Show Hide Bookmarked Content In Word Document
second_title: Aspose.Words Document Processing API
description: Learn how to show and hide bookmarked content in Word documents using Aspose.Words for .NET with this detailed, step-by-step guide.
weight: 10
url: /net/programming-with-bookmarks/show-hide-bookmarked-content/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Show Hide Bookmarked Content In Word Document

## Introduction

Ready to dive into the world of document manipulation with Aspose.Words for .NET? Whether you're a developer looking to automate document tasks or just someone curious about handling Word files programmatically, you're in the right place. Today, we'll explore how to show and hide bookmarked content in a Word document using Aspose.Words for .NET. This step-by-step guide will make you a pro at controlling content visibility based on bookmarks. Let's get started!

## Prerequisites

Before we jump into the nitty-gritty, there are a few things you'll need:

1. Visual Studio: Any version compatible with .NET.
2. Aspose.Words for .NET: Download it [here](https://releases.aspose.com/words/net/).
3. Basic Understanding of C#: If you can write a simple "Hello World" program, you're good to go.
4. A Word Document with Bookmarks: We'll be using a sample document with bookmarks for this tutorial.

## Import Namespaces

First things first, let's import the necessary namespaces. This ensures we have all the tools we need for our task.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

With these namespaces in place, we're all set to start our journey.

## Step 1: Setting Up Your Project

Alright, let's kick things off by setting up our project in Visual Studio.

### Create a New Project

Open Visual Studio and create a new Console App (.NET Core) project. Name it something catchy, like "BookmarkVisibilityManager".

### Add Aspose.Words for .NET

You'll need to add Aspose.Words for .NET to your project. You can do this via NuGet Package Manager.

1. Go to Tools > NuGet Package Manager > Manage NuGet Packages for Solution.
2. Search for "Aspose.Words".
3. Install the package.

Great! Now that our project is set up, let's move on to loading our document.

## Step 2: Loading the Document

We need to load the Word document that contains the bookmarks. For this tutorial, we'll use a sample document named "Bookmarks.docx".

```csharp
// The path to the documents directory.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

This code snippet sets the path to your document directory and loads the document into the `doc` object.

## Step 3: Show/Hide Bookmarked Content

Now comes the fun part – showing or hiding the content based on bookmarks. We'll create a method called `ShowHideBookmarkedContent` to handle this.

Here's the method that will toggle the visibility of bookmarked content:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    Node currentNode = bm.BookmarkStart;
    while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
    {
        if (currentNode.NodeType == NodeType.Run)
        {
            Run run = currentNode as Run;
            run.Font.Hidden = isHidden;
        }
        currentNode = currentNode.NextSibling;
    }
}
```

### Breakdown of the Method

- Bookmark Retrieval: `Bookmark bm = doc.Range.Bookmarks[bookmarkName];` fetches the bookmark.
- Node Traversal: We traverse the nodes within the bookmark.
- Visibility Toggle: If the node is a `Run` (a contiguous run of text), we set its `Hidden` property.

## Step 4: Applying the Method

With our method in place, let's apply it to show or hide content based on a bookmark.

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true);
```

This line of code will hide the content within the bookmark named "MyBookmark1".

## Step 5: Saving the Document

Finally, let's save our modified document.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

This saves the document with the changes we've made.

## Conclusion

And there you have it! You've just learned how to show and hide bookmarked content in a Word document using Aspose.Words for .NET. This powerful tool makes document manipulation a breeze, whether you're automating reports, creating templates, or just tinkering with Word files. Happy coding!

## FAQ's

### Can I toggle multiple bookmarks at once?
Yes, you can call the `ShowHideBookmarkedContent` method for each bookmark you want to toggle.

### Does hiding content affect the document's structure?
No, hiding content only affects its visibility. The content remains in the document.

### Can I use this method for other types of content?
This method specifically toggles text runs. For other content types, you'll need to modify the node traversal logic.

### Is Aspose.Words for .NET free?
Aspose.Words offers a free trial [here](https://releases.aspose.com/), but a full license is required for production use. You can purchase it [here](https://purchase.aspose.com/buy).

### How can I get support if I encounter issues?
You can get support from the Aspose community [here](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
