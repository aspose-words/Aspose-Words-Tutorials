---
category: general
date: 2026-10-10
description: Create signature options and sign a Word doc using XAdES EPES in Java.
  Learn how to sign office document with a certificate in a few clear steps.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create signature options
- sign word doc
- sign office document
- how to sign docx
language: en
lastmod: 2026-10-10
og_description: Create signature options and sign a Word doc using XAdES EPES in Java.
  This guide shows you how to sign office document securely with a certificate.
og_image_alt: Screenshot of Java code that creates signature options and signs a DOCX
  file
og_title: Create signature options and sign a Word doc with XAdES EPES
schemas:
- author: GroupDocs
  dateModified: '2026-10-10'
  description: Create signature options and sign a Word doc using XAdES EPES in Java.
    Learn how to sign office document with a certificate in a few clear steps.
  headline: Create signature options and sign a Word doc with XAdES EPES
  type: TechArticle
- description: Create signature options and sign a Word doc using XAdES EPES in Java.
    Learn how to sign office document with a certificate in a few clear steps.
  name: Create signature options and sign a Word doc with XAdES EPES
  steps:
  - name: The library loads the `.pfx` file and extracts the private key using the
      supplied password.
    text: The library loads the `.pfx` file and extracts the private key using the
      supplied password.
  - name: It creates an XML‑DSig structure matching the XAdES‑EPES profile.
    text: It creates an XML‑DSig structure matching the XAdES‑EPES profile.
  - name: The signature is embedded into the DOCX package, preserving the original
      document layout.
    text: The signature is embedded into the DOCX package, preserving the original
      document layout.
  - name: Open `SignedXades.docx` in Word.
    text: Open `SignedXades.docx` in Word.
  - name: Click **File → Info → View signatures**.
    text: Click **File → Info → View signatures**.
  - name: Word should display a green checkmark indicating a valid digital signature.
    text: Word should display a green checkmark indicating a valid digital signature.
  type: HowTo
tags:
- digital signature
- Java
- XAdES
title: Create signature options and sign a Word doc with XAdES EPES
url: /java/document-security/create-signature-options-and-sign-a-word-doc-with-xades-epes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create signature options and sign a Word doc with XAdES EPES

If you need to **create signature options** for a DOCX file, this guide shows you how to sign a Word doc using the XAdES‑EPES level in Java. You’ll get a complete, runnable example that signs an Office document with a PFX certificate in just a few lines of code.

Signing office documents is a common requirement for legal workflows, automated contract processing, and secure document exchange. In this tutorial you’ll learn:

* How to configure `SignatureOptions` for XAdES‑EPES.
* How to call `DigitalSignatureUtil.sign` to **sign word doc** files.
* How to handle common pitfalls such as certificate loading and password errors.

> **Prerequisite** – Java 17 or later, the GroupDocs.Signature for Java library (or a compatible XAdES library), and a valid `.pfx` certificate file.

---

## What you’ll need

| Item | Reason |
|------|--------|
| Java 17+ | Modern language features and better security APIs |
| GroupDocs.Signature for Java (or equivalent) | Provides `SignatureOptions`, `XmlDsigLevel`, and `DigitalSignatureUtil` |
| A PFX certificate (`.pfx`) | Supplies the private key for the digital signature |
| Password for the certificate | Required to unlock the private key |
| An unsigned DOCX file (`Unsigned.docx`) | The source document you want to **sign office document** |

Make sure the library JAR is on your classpath:

```bash
# Example using Maven
mvn dependency:copy -Dartifact=com.groupdocs:groupdocs-signature:23.3
```

---

## Step 1: Import the required classes

Start by importing the classes that handle signatures and file I/O.

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import java.io.IOException;
```

These imports give you access to the API used to **create signature options** and to perform the actual signing operation.

---

## Step 2: Create signature options

The `SignatureOptions` object holds all configuration needed for the signing process, such as the signature level, visual appearance, and timestamp settings.

```java
// Step 2: Create signature options
SignatureOptions signatureOptions = new SignatureOptions();
```

Creating a fresh `SignatureOptions` instance is the first step in **how to sign docx** files because it isolates each signing request, preventing cross‑document side effects.

---

## Step 3: Specify the XAdES EPES signature level

XAdES‑EPES (Explicit Policy-based Electronic Signature) is a widely accepted policy for Office document signatures. Setting the level tells the library which cryptographic profile to use.

```java
// Step 3: Specify the XAdES EPES signature level
signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);
```

Why XAdES‑EPES? It embeds the signing policy directly in the signature, making the signed document self‑contained and compliant with many e‑signature regulations.

---

## Step 4: Sign the DOCX file

Now invoke `DigitalSignatureUtil.sign`. This method reads the source file, applies the signature, and writes the signed output.

```java
// Step 4: Sign the document using the provided certificate
try {
    DigitalSignatureUtil.sign(
        "YOUR_DIRECTORY/Unsigned.docx",   // input file
        "YOUR_DIRECTORY/SignedXades.docx", // output file
        "YOUR_DIRECTORY/mycert.pfx",      // certificate file
        "password",                       // certificate password
        signatureOptions                  // options configured above
    );
    System.out.println("Document signed successfully: SignedXades.docx");
} catch (IOException e) {
    System.err.println("Failed to sign the document: " + e.getMessage());
}
```

**What happens under the hood?**  
1. The library loads the `.pfx` file and extracts the private key using the supplied password.  
2. It creates an XML‑DSig structure matching the XAdES‑EPES profile.  
3. The signature is embedded into the DOCX package, preserving the original document layout.  

If the certificate password is wrong or the file cannot be read, an `IOException` is thrown, which you should handle as shown.

---

## Step 5: Verify the signed document (optional)

After signing, you may want to confirm that the signature is present and valid. GroupDocs provides a verification API, but a quick manual check can be done with Microsoft Word:

1. Open `SignedXades.docx` in Word.  
2. Click **File → Info → View signatures**.  
3. Word should display a green checkmark indicating a valid digital signature.

Automated verification with the library looks like this:

```java
import com.groupdocs.signature.VerificationResult;

VerificationResult result = DigitalSignatureUtil.verify(
    "YOUR_DIRECTORY/SignedXades.docx",
    signatureOptions
);

if (result.isSuccessful()) {
    System.out.println("Signature verification succeeded.");
} else {
    System.out.println("Signature verification failed: " + result.getErrorMessage());
}
```

Running the verification step gives you programmatic confidence that **sign office document** succeeded.

---

## Full, runnable example

Putting all the pieces together, here is a self‑contained Java class you can copy, paste, and run.

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import com.groupdocs.signature.VerificationResult;
import java.io.IOException;

/**
 * Demonstrates how to create signature options and sign a DOCX file with XAdES EPES.
 */
public class XadesSignatureDemo {

    public static void main(String[] args) {
        // Paths – update these to match your environment
        String inputPath = "YOUR_DIRECTORY/Unsigned.docx";
        String outputPath = "YOUR_DIRECTORY/SignedXades.docx";
        String certPath = "YOUR_DIRECTORY/mycert.pfx";
        String certPassword = "password";

        // 1️⃣ Create signature options
        SignatureOptions signatureOptions = new SignatureOptions();

        // 2️⃣ Set XAdES EPES level
        signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);

        // 3️⃣ Sign the document
        try {
            DigitalSignatureUtil.sign(inputPath, outputPath, certPath, certPassword, signatureOptions);
            System.out.println("Document signed successfully: " + outputPath);
        } catch (IOException e) {
            System.err.println("Signing failed: " + e.getMessage());
            return;
        }

        // 4️⃣ (Optional) Verify the signature
        VerificationResult verification = DigitalSignatureUtil.verify(outputPath, signatureOptions);
        if (verification.isSuccessful()) {
            System.out.println("Signature verification succeeded.");
        } else {
            System.out.println("Signature verification failed: " + verification.getErrorMessage());
        }
    }
}
```

**Expected output**

```
Document signed successfully: YOUR_DIRECTORY/SignedXades.docx
Signature verification succeeded.
```

If anything goes wrong, the console will display a clear error message, helping you troubleshoot certificate or file‑path issues.

---

## Common questions and edge‑case handling

| Question | Answer |
|----------|--------|
| **Can I use a different signature level?** | Yes. Replace `XmlDsigLevel.XAdES_EPES` with `XAdES_BES`, `XAdES_T`, etc., depending on compliance needs. |
| **What if my certificate is stored in a keystore instead of a .pfx file?** | Load the `KeyStore` manually, extract the `PrivateKey` and `Certificate`, then pass them to an overload of `sign` that accepts a `KeyStore` object. |
| **How do I add a visible signature image?** | Use `signatureOptions.setSignatureImage("path/to/image.png")` before calling `sign`. |
| **Is the signing process thread‑safe?** | The `DigitalSignatureUtil.sign` method is stateless; you can safely call it from multiple threads as long as each thread uses its own `SignatureOptions` instance. |
| **What if the DOCX contains existing signatures?** | The library will append a new signature package entry, preserving earlier signatures. Verify that the signing policy allows multiple signatures if required. |

---

## Tips and best practices (E‑E‑A‑T)

* **Pro tip:** Store your certificate password in a secure vault (e.g., Azure Key Vault) rather than hard‑coding it.  
* **Watch out for:** File path separators on Windows (`\`) vs. Unix (`/`). Use `Paths.get(...)` to build platform‑independent paths.  
* **Performance:** Signing large DOCX files can be I/O‑bound; consider streaming the input file if you process many documents in batch.  
* **Compliance:** XAdES‑EPES complies with EU eIDAS regulation; verify your local legal requirements before choosing a signature level.

---

## Conclusion

In this tutorial you learned how to **create signature options** and **sign a Word doc** with the XAdES‑EPES level using Java. The complete example covers certificate loading, option configuration, the signing call, and optional verification, giving you a ready‑to‑use solution for **how to sign docx** files in production.


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Load Options in Java – Detect Missing Fonts & How to Load DOCX](/words/english/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [How to Create Editable Ranges in Read-Only Documents Using Aspose.Words for Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}