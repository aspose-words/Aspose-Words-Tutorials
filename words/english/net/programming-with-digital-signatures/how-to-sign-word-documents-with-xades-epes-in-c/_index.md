---
category: general
date: 2026-09-08
description: How to sign word documents using a digital signature docx workflow, load
  pfx certificate, and create XAdES signature in C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to sign word
- digital signature docx
- load pfx certificate
- digitally sign word
- create xades signature
language: en
lastmod: 2026-09-08
og_description: How to sign word documents using a digital signature docx flow, load
  pfx certificate, and create XAdES signature in C#. Follow the complete example.
og_image_alt: Screenshot showing a Word document signed with XAdES EPES digital signature
og_title: How to sign word documents with XAdES EPES in C# – step‑by‑step guide
schemas:
- author: GroupDocs
  dateModified: '2026-09-08'
  description: How to sign word documents using a digital signature docx workflow,
    load pfx certificate, and create XAdES signature in C#.
  headline: How to sign word documents with XAdES EPES in C#
  type: TechArticle
tags:
- digital-signature
- C#
- Word
- XAdES
title: How to sign word documents with XAdES EPES in C#
url: /net/programming-with-digital-signatures/how-to-sign-word-documents-with-xades-epes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to sign word documents with XAdES EPES in C#

If you need to **how to sign word** files programmatically, this guide shows you a complete, production‑ready solution. You’ll learn how to load a PFX certificate, configure a digital signature docx, and create an XAdES‑EPES signature that can be verified by Microsoft Word and third‑party validators.

The example uses the GroupDocs.Signature for .NET library, but the concepts apply to any API that supports XAdES. By the end of the tutorial you will have a signed `Signed_XAdES_EPES.docx` ready for distribution.

## What you’ll need

- .NET 6.0 or later (the code also works with .NET Framework 4.7+)
- A valid PFX certificate file (`.pfx`) that contains a private key
- The password for the PFX file
- A Word document (`.docx`) that you want to sign
- NuGet package **GroupDocs.Signature** (install with `dotnet add package GroupDocs.Signature`)

## Step 1: Install the required NuGet package

```bash
dotnet add package GroupDocs.Signature
```

The package provides the `Document` class, `XadesSignatureOptions`, and helper types for creating a **digitally sign word** file.

## Step 2: Load the unsigned Word document

```csharp
using GroupDocs.Signature;
using GroupDocs.Signature.Options;
using System;
using System.Security.Cryptography.X509Certificates;

...

// Load the original Word file (must be a .docx)
var documentPath = @"C:\Docs\Unsigned.docx";
Document document = new Document(documentPath);
```

Loading the document gives you an object model that you can manipulate before applying the signature.

## Step 3: Load the PFX certificate (load pfx certificate)

```csharp
// Load the certificate that holds the private key
var certPath = @"C:\Certificates\mycert.pfx";
var certPassword = "yourPassword";          // keep this secret!
X509Certificate2 certificate = new X509Certificate2(certPath, certPassword);
```

> **Pro tip:** If the certificate is stored in the Windows certificate store, you can retrieve it with `X509Store` instead of loading a file. The `load pfx certificate` approach works on any platform, including Linux containers.

## Step 4: (Optional) Add a visual signature line

A visual cue helps recipients see where the signature appears in Word.

```csharp
// Create a signature line that will be displayed in the document
SignatureLine signatureLine = new SignatureLine(document);
signatureLine.Id = Guid.NewGuid().ToString();
signatureLine.Signer = "John Smith";
signatureLine.Title = "Approved";

// Append the line to the first paragraph of the first section
document.FirstSection.Body.FirstParagraph.AppendChild(signatureLine);
```

If you prefer an invisible signature, you can skip this step. The **digital signature docx** will still be cryptographically valid.

## Step 5: Configure XAdES‑EPES options (create xades signature)

```csharp
// Set up XAdES‑EPES options – this creates a “qualified” electronic signature
XadesSignatureOptions signOptions = new XadesSignatureOptions
{
    SignatureType = XadesSignatureType.XAdES_EPES,
    // Optional: add a custom signing reason or location
    Reason = "Document approval",
    Location = "New York, USA"
};
```

The `XadesSignatureType.XAdES_EPES` flag tells the library to embed the signature according to the EPES (Explicit Policy-based Electronic Signature) profile, which is widely accepted by EU e‑IDAS regulations.

## Step 6: Apply the digital signature

```csharp
// Sign the document with the loaded certificate and options
document.DigitalSignatures.Sign(certificate, signOptions);
```

The `Sign` method performs all the cryptographic work: it hashes the document parts, creates the XML‑DSig structure, and inserts the XAdES envelope into the Word file.

## Step 7: Save the signed document

```csharp
// Save the signed file – you can overwrite or create a new file
var signedPath = @"C:\Docs\Signed_XAdES_EPES.docx";
document.Save(signedPath);
Console.WriteLine($"Document signed and saved to: {signedPath}");
```

After saving, open `Signed_XAdES_EPES.docx` in Microsoft Word. You should see a signature line (if you added one) and a **digitally sign word** status bar indicating that the file is signed and the signature is valid.

## Full, runnable example

Below is the complete program you can copy‑paste into a console application.

```csharp
using System;
using System.Security.Cryptography.X509Certificates;
using GroupDocs.Signature;
using GroupDocs.Signature.Options;

namespace WordXadesSigner
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the unsigned Word document
            string docPath = @"C:\Docs\Unsigned.docx";
            Document document = new Document(docPath);

            // 2️⃣ Load the signing certificate (load pfx certificate)
            string pfxPath = @"C:\Certificates\mycert.pfx";
            string pfxPassword = "yourPassword";
            X509Certificate2 cert = new X509Certificate2(pfxPath, pfxPassword);

            // 3️⃣ (Optional) Add a visual signature line
            SignatureLine sigLine = new SignatureLine(document)
            {
                Id = Guid.NewGuid().ToString(),
                Signer = "John Smith",
                Title = "Approved"
            };
            document.FirstSection.Body.FirstParagraph.AppendChild(sigLine);

            // 4️⃣ Configure XAdES‑EPES options (create xades signature)
            XadesSignatureOptions xadesOptions = new XadesSignatureOptions
            {
                SignatureType = XadesSignatureType.XAdES_EPES,
                Reason = "Document approval",
                Location = "New York, USA"
            };

            // 5️⃣ Apply the digital signature (digitally sign word)
            document.DigitalSignatures.Sign(cert, xadesOptions);

            // 6️⃣ Save the signed document
            string signedPath = @"C:\Docs\Signed_XAdES_EPES.docx";
            document.Save(signedPath);

            Console.WriteLine($"Signed document saved to: {signedPath}");
        }
    }
}
```

### Expected output

```
Signed document saved to: C:\Docs\Signed_XAdES_EPES.docx
```

Opening the file in Word shows a green “Signed” banner and, if you added the visual line, the signature line appears at the location you specified.

## Handling common pitfalls

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| **Certificate password is wrong** | The `X509Certificate2` constructor throws a `CryptographicException`. | Verify the password, or use a secure secrets manager (Azure Key Vault, AWS Secrets Manager). |
| **Word shows “Signature is invalid”** | The document was altered after signing, or the signing policy is missing. | Ensure the file is saved **after** signing and not edited again. Embed the correct XAdES policy if required by your regulator. |
| **Signature line not visible** | The document uses a different section layout. | Append the `SignatureLine` to the correct paragraph or create a new paragraph before adding it. |
| **Performance slowdown on large docs** | XAdES signatures hash every part of the package. | Use streaming APIs (`SignAsync`) or increase machine resources for very large files (>50 MB). |

## Extending the solution

- **Multiple signers** – call `Sign` repeatedly with different certificates and set `SignatureId` to differentiate each signer.
- **Timestamping** – add a `TimestampOptions` object to `XadesSignatureOptions` to embed a trusted timestamp.
- **Custom policies** – supply an XML policy file via `XadesSignatureOptions.PolicyFilePath` for compliance with specific standards.

## Conclusion

You now know **how to sign word** documents programmatically, how to **load pfx certificate**, and how to **create xades signature** using GroupDocs.Signature. The tutorial covered every step from loading the document to saving the signed output, with practical tips for common edge cases.  

Next, explore related topics such as **digitally sign word** PDFs, integrate **digital signature docx** verification, or add **timestamp** support to meet advanced compliance requirements. Happy signing!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Detect Digital Signature on Word Document](/words/english/net/programming-with-fileformat/detect-document-signatures/)
- [Signing Existing Signature Line In Word Document](/words/english/net/programming-with-digital-signatures/signing-existing-signature-line/)
- [Access And Verify Signature In Word Document](/words/english/net/programming-with-digital-signatures/access-and-verify-signature/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}