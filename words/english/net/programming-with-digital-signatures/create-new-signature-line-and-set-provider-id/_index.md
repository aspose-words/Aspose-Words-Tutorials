---
title: Create New Signature Line And Set Provider Id
linktitle: Create New Signature Line And Set Provider Id
second_title: Aspose.Words Document Processing API
description: Learn how to create a new signature line and set the provider ID in Word documents using Aspose.Words for .NET. Step-by-step guide.
weight: 10
url: /net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Create New Signature Line And Set Provider Id

## Introduction

Hey there, tech enthusiasts! Ever wondered how to add a signature line in your Word documents programmatically? Well, today we're diving into just that using Aspose.Words for .NET. This guide will walk you through every step, making it as easy as pie to create a new signature line and set the provider ID in your Word documents. Whether you're automating document processing or just looking to streamline your workflow, this tutorial has got you covered.

## Prerequisites

Before we get our hands dirty, let's make sure we've got everything we need:

1. Aspose.Words for .NET: If you haven't already, download it [here](https://releases.aspose.com/words/net/).
2. Development Environment: Visual Studio or any other C# development environment.
3. .NET Framework: Make sure you've got .NET Framework installed.
4. PFX Certificate: For signing documents, you'll need a PFX certificate. You can get one from a trusted certificate authority.

## Import Namespaces

First things first, let's import the necessary namespaces in your C# project:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Alright, let's get down to the nitty-gritty. Here's a detailed breakdown of each step to create a new signature line and set the provider ID.

## Step 1: Create a New Document

To start, we need to create a new Word document. This will be the canvas for our signature line.

```csharp
// The path to the documents directory.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

In this snippet, we're initializing a new `Document` and a `DocumentBuilder`. The `DocumentBuilder` helps us add elements to our document.

## Step 2: Define Signature Line Options

Next, we define the options for our signature line. This includes the signer's name, title, email, and other details.

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

These options personalize the signature line, making it clear and professional.

## Step 3: Insert the Signature Line

With our options set, we can now insert the signature line into the document.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

Here, the `InsertSignatureLine` method adds the signature line, and we assign a unique provider ID to it.

## Step 4: Save the Document

After inserting the signature line, let's save the document.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

This saves your document with the newly added signature line.

## Step 5: Set Up Signing Options

Now, we need to set up the options for signing the document. This includes the signature line ID, provider ID, comments, and the sign time.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

These options ensure the document is signed with the correct details.

## Step 6: Create Certificate Holder

To sign the document, we'll use a PFX certificate. Let's create a certificate holder for it.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

Make sure to replace `"morzal.pfx"` with your actual certificate file and `"aw"` with your certificate password.

## Step 7: Sign the Document

Finally, we sign the document using the digital signature utility.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

This signs the document and saves it as a new file.

## Conclusion

And there you have it! You've successfully created a new signature line and set the provider ID in a Word document using Aspose.Words for .NET. This powerful library makes it incredibly easy to manage and automate document processing tasks. Give it a try and see how it can streamline your workflow.

## FAQ's

### Can I customize the appearance of the signature line?
Absolutely! You can tweak various options in the `SignatureLineOptions` to suit your needs.

### What if I don't have a PFX certificate?
You'll need to obtain one from a trusted certificate authority. It's essential for digitally signing documents.

### Can I add multiple signature lines to a document?
Yes, you can add as many signature lines as needed by repeating the insertion process with different options.

### Is Aspose.Words for .NET compatible with .NET Core?
Yes, Aspose.Words for .NET supports .NET Core, making it versatile for different development environments.

### How secure are the digital signatures?
Digital signatures created with Aspose.Words are highly secure, provided you use a valid and trusted certificate.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
