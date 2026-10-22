---
category: general
date: 2026-09-27
description: Learn how to digitally sign a Word document in Java. This guide shows
  adding a digital signature for Word file and how to add digital signature to docx
  with best practices.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- digitally sign word document
- digital signature for word file
- add digital signature to docx
language: en
lastmod: 2026-09-27
og_description: Digitally sign Word document with Java. Follow this tutorial to add
  a digital signature for Word file and learn how to add digital signature to docx
  securely.
og_image_alt: Screenshot showing a Java program that digitally signs a Word document
og_title: Digitally sign Word document in Java – complete step‑by‑step guide
schemas:
- author: GroupDocs
  dateModified: '2026-09-27'
  description: Learn how to digitally sign a Word document in Java. This guide shows
    adding a digital signature for Word file and how to add digital signature to docx
    with best practices.
  headline: How to digitally sign Word document using Java
  type: TechArticle
tags:
- Java
- Digital Signature
- Docx
title: How to digitally sign Word document using Java
url: /java/document-security/how-to-digitally-sign-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to digitally sign Word document using Java

If you need to **digitally sign Word document** in a Java application, this guide shows you the exact steps. You’ll see how to add a **digital signature for Word file** and securely **add digital signature to docx** using GroupDocs.Signature (or a similar library).  

The process is straightforward: load the `.docx`, apply a PKCS#12 certificate, configure the XML‑DSig level, and save the signed file. By the end of this tutorial you’ll have a runnable program that produces a compliant XAdES‑EPES signature.

## Prerequisites

- Java 17 or newer (the code compiles with Java 11 as well)  
- Maven or Gradle for dependency management  
- A PKCS#12 (`.pfx`) certificate file and its password  
- Basic familiarity with Java I/O  

> **Pro tip:** Store the certificate password in a secure vault (e.g., Azure Key Vault) instead of hard‑coding it.

## Step 1: Add the GroupDocs.Signature dependency

If you’re using Maven, add the following to your `pom.xml`. For Gradle, the equivalent `implementation` line is shown in the comment.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-signature</artifactId>
    <version>23.10</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.groupdocs:groupdocs-signature:23.10'
```

These artifacts provide `Document`, `DigitalSignatureUtil`, and the related enums used in the example.

## Step 2: Load the Word document you want to sign

```java
import com.groupdocs.signature.Signature;
import com.groupdocs.signature.domain.docx.Document;
import com.groupdocs.signature.exception.SignatureException;

public class WordSigner {

    public static void main(String[] args) {
        // Path to the source .docx file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        try {
            // Load the Word document into the GroupDocs model
            Document document = new Document(inputPath);
            System.out.println("Document loaded successfully.");
            // Continue with signing...
            signDocument(document);
        } catch (SignatureException e) {
            System.err.println("Failed to load the document: " + e.getMessage());
        }
    }
```

**Why this matters:** Loading the file into the library’s `Document` object gives you full access to signature fields and content manipulation without altering the original file on disk.

## Step 3: Apply a digital signature using a PKCS#12 certificate

```java
    private static void signDocument(Document document) {
        // Path to your .pfx certificate and its password
        String certPath = "YOUR_DIRECTORY/cert.pfx";
        String certPassword = "pwd";

        try {
            // Apply an XML‑DSig signature (XAdES‑EPES will be set later)
            DigitalSignatureUtil.sign(
                document,
                certPath,
                certPassword,
                SignatureType.XML_DSIG
            );
            System.out.println("Digital signature applied.");
        } catch (SignatureException e) {
            System.err.println("Signing failed: " + e.getMessage());
            return;
        }

        // Proceed to configure the signature level
        configureSignatureLevel(document);
    }
```

**Explanation:**  
- `SignatureType.XML_DSIG` tells the library to create an XML‑DSig signature, which is required for XAdES compliance.  
- Using a PKCS#12 certificate ensures the signature is cryptographically strong and can be validated by standard tools (e.g., Microsoft Word, Adobe Acrobat).

## Step 4: Set the XAdES‑EPES level for stronger compliance

```java
    private static void configureSignatureLevel(Document document) {
        // The signing operation creates a signature field automatically
        if (document.getSignatureFields().isEmpty()) {
            System.err.println("No signature fields were created.");
            return;
        }

        // Grab the first (and usually only) signature field
        SignatureSignatureField signatureField = document.getSignatureFields().get(0);

        // Set the XML‑DSig level to XAdES‑EPES (Enhanced Electronic Signature)
        signatureField.setXmlDsigLevel(XmlDsigLevel.XADES_EPES);
        System.out.println("Signature level set to XAdES‑EPES.");

        // Save the signed document
        saveSignedDocument(document);
    }
```

**Why XAdES‑EPES?**  
XAdES‑EPES adds timestamps and signing policy information, making the signature legally admissible in many jurisdictions. It’s the recommended level when you need **digital signature for Word file** that complies with e‑IDAS or similar regulations.

## Step 5: Save the signed document

```java
    private static void saveSignedDocument(Document document) {
        String outputPath = "YOUR_DIRECTORY/SignedXAdES.docx";

        try {
            document.save(outputPath);
            System.out.println("Signed document saved to: " + outputPath);
        } catch (SignatureException e) {
            System.err.println("Failed to save signed document: " + e.getMessage());
        }
    }
}
```

**Result:** After running the program, `SignedXAdES.docx` contains a visible signature field. Opening the file in Microsoft Word will show *Signed and all signatures are valid* if the certificate chain is trusted.

### Expected console output

```
Document loaded successfully.
Digital signature applied.
Signature level set to XAdES‑EPES.
Signed document saved to: YOUR_DIRECTORY/SignedXAdES.docx
```

## Handling multiple signature fields (advanced)

If your template already contains several signature placeholders, you can iterate over them:

```java
for (SignatureSignatureField field : document.getSignatureFields()) {
    field.setXmlDsigLevel(XmlDsigLevel.XADES_EPES);
}
```

This ensures **add digital signature to docx** in every required location, useful for multi‑signer workflows.

## Common pitfalls and how to avoid them

| Issue | Cause | Fix |
|-------|-------|-----|
| *Signature field not created* | Using a non‑XML signature type (e.g., `SignatureType.CMS`) | Always use `SignatureType.XML_DSIG` when you plan to set XAdES levels |
| *Word shows “Signature is not valid”* | Certificate chain not trusted on the local machine | Import the root/intermediate certificates into the Windows Trusted Root store |
| *File size blows up* | Saving the document without compression | Call `document.save(outputPath, SaveOptions.create().setCompress(true))` |

## Full runnable example (copy‑paste)

```java
import com.groupdocs.signature.Signature;
import com.groupdocs.signature.domain.SignatureSignatureField;
import com.groupdocs.signature.domain.docx.Document;
import com.groupdocs.signature.domain.enums.SignatureType;
import com.groupdocs.signature.domain.enums.XmlDsigLevel;
import com.groupdocs.signature.exception.SignatureException;

public class WordSigner {

    public static void main(String[] args) {
        String inputPath = "YOUR_DIRECTORY/input.docx";
        String certPath  = "YOUR_DIRECTORY/cert.pfx";
        String certPwd   = "pwd";
        String outputPath = "YOUR_DIRECTORY/SignedXAdES.docx";

        try {
            // 1️⃣ Load the document
            Document document = new Document(inputPath);
            System.out.println("Document loaded.");

            // 2️⃣ Apply XML‑DSig signature
            DigitalSignatureUtil.sign(document, certPath, certPwd, SignatureType.XML_DSIG);
            System.out.println("Signature applied.");

            // 3️⃣ Set XAdES‑EPES level
            if (!document.getSignatureFields().isEmpty()) {
                SignatureSignatureField sigField = document.getSignatureFields().get(0);
                sigField.setXmlDsigLevel(XmlDsigLevel.XADES_EPES);
                System.out.println("XAdES‑EPES level set.");
            } else {
                System.err.println("No signature fields found.");
            }

            // 4️⃣ Save the signed file
            document.save(outputPath);
            System.out.println("Signed document saved at " + outputPath);
        } catch (SignatureException e) {
            System.err.println("Error: " + e.getMessage());
        }
    }
}
```

Run the class with `java -cp target/your‑jar.jar WordSigner`. The program will create `SignedXAdES.docx` containing a fully compliant **digital signature for Word file**.

## Conclusion

You now know how to **digitally sign Word document** using Java, from loading the file to applying a PKCS#12 certificate, setting the XAdES‑EPES level, and saving the result. This complete solution lets you **add digital signature to docx** files in any enterprise workflow.

### What’s next?

- Explore **digital signature for Word file** with timestamp servers (RFC 3161) for long‑term validation.  
- Combine multiple signatures for multi‑party approval processes.  
- Integrate the signing routine into a Spring Boot REST endpoint to offer “sign‑on‑the‑fly” services.

Feel free to experiment with different certificate types, signature policies, or even switching to `SignatureType.CMS` if you need a detached CMS signature instead of XML‑DSig. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Detect Digital Signature on Word Document](/words/english/net/programming-with-fileformat/detect-document-signatures/)
- [Access And Verify Signature In Word Document](/words/english/net/programming-with-digital-signatures/access-and-verify-signature/)
- [Signing Existing Signature Line In Word Document](/words/english/net/programming-with-digital-signatures/signing-existing-signature-line/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}