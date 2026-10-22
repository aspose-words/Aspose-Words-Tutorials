---
category: general
date: 2026-09-27
description: Lär dig hur du digitalt signerar ett Word‑dokument i Java. Den här guiden
  visar hur du lägger till en digital signatur för en Word‑fil och hur du lägger till
  en digital signatur i docx med bästa praxis.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- digitally sign word document
- digital signature for word file
- add digital signature to docx
language: sv
lastmod: 2026-09-27
og_description: Signera Word-dokument digitalt med Java. Följ den här handledningen
  för att lägga till en digital signatur för Word-filen och lär dig hur du säkert
  lägger till en digital signatur i docx.
og_image_alt: Screenshot showing a Java program that digitally signs a Word document
og_title: Digitalt signera Word-dokument i Java – komplett steg‑för‑steg‑guide
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
title: Hur man digitalt signerar ett Word‑dokument med Java
url: /sv/java/document-security/how-to-digitally-sign-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man digitalt signerar Word‑dokument med Java

Om du behöver **digitalt signera Word‑dokument** i en Java‑applikation visar den här guiden de exakta stegen. Du får se hur du lägger till en **digital signatur för Word‑fil** och säkert **lägger till digital signatur till docx** med GroupDocs.Signature (eller ett liknande bibliotek).

Processen är enkel: ladda `.docx`, applicera ett PKCS#12‑certifikat, konfigurera XML‑DSig‑nivån och spara den signerade filen. I slutet av tutorialen har du ett körbart program som producerar en XAdES‑EPES‑kompatibel signatur.

## Förutsättningar

- Java 17 eller nyare (koden kompilerar även med Java 11)  
- Maven eller Gradle för beroendehantering  
- En PKCS#12 (`.pfx`)‑certifikatfil och dess lösenord  
- Grundläggande kunskap om Java I/O  

> **Pro tip:** Förvara certifikatlösenordet i en säker valv (t.ex. Azure Key Vault) istället för att hårdkoda det.

## Steg 1: Lägg till GroupDocs.Signature‑beroendet

Om du använder Maven, lägg till följande i din `pom.xml`. För Gradle visas motsvarande `implementation`‑rad i kommentaren.

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

Dessa artefakter tillhandahåller `Document`, `DigitalSignatureUtil` och de relaterade enum‑värdena som används i exemplet.

## Steg 2: Ladda Word‑dokumentet du vill signera

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

**Varför detta är viktigt:** Att ladda filen i bibliotekets `Document`‑objekt ger dig full åtkomst till signaturfält och innehållsmanipulation utan att ändra den ursprungliga filen på disken.

## Steg 3: Applicera en digital signatur med ett PKCS#12‑certifikat

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

**Förklaring:**  
- `SignatureType.XML_DSIG` talar om för biblioteket att skapa en XML‑DSig‑signatur, vilket krävs för XAdES‑kompatibilitet.  
- Att använda ett PKCS#12‑certifikat säkerställer att signaturen är kryptografiskt stark och kan valideras av standardverktyg (t.ex. Microsoft Word, Adobe Acrobat).

## Steg 4: Ställ in XAdES‑EPES‑nivån för starkare efterlevnad

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

**Varför XAdES‑EPES?**  
XAdES‑EPES lägger till tidsstämplar och signaturpolicy‑information, vilket gör signaturen juridiskt giltig i många jurisdiktioner. Det är den rekommenderade nivån när du behöver **digital signatur för Word‑fil** som följer e‑IDAS eller liknande regelverk.

## Steg 5: Spara det signerade dokumentet

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

**Resultat:** Efter att programmet har körts innehåller `SignedXAdES.docx` ett synligt signaturfält. När du öppnar filen i Microsoft Word visas *Signed and all signatures are valid* om certifikatkedjan är betrodd.

### Förväntad konsolutmatning

```
Document loaded successfully.
Digital signature applied.
Signature level set to XAdES‑EPES.
Signed document saved to: YOUR_DIRECTORY/SignedXAdES.docx
```

## Hantera flera signaturfält (avancerat)

Om din mall redan innehåller flera signaturplatshållare kan du iterera över dem:

```java
for (SignatureSignatureField field : document.getSignatureFields()) {
    field.setXmlDsigLevel(XmlDsigLevel.XADES_EPES);
}
```

Detta säkerställer **lägga till digital signatur till docx** på varje nödvändig plats, vilket är användbart för flersignatörs‑arbetsflöden.

## Vanliga fallgropar och hur du undviker dem

| Problem | Orsak | Lösning |
|---------|-------|---------|
| *Signature field not created* | Using a non‑XML signature type (e.g., `SignatureType.CMS`) | Always use `SignatureType.XML_DSIG` when you plan to set XAdES levels |
| *Word shows “Signature is not valid”* | Certificate chain not trusted on the local machine | Import the root/intermediate certificates into the Windows Trusted Root store |
| *File size blows up* | Saving the document without compression | Call `document.save(outputPath, SaveOptions.create().setCompress(true))` |

## Fullt körbart exempel (kopiera‑klistra)

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

Kör klassen med `java -cp target/your‑jar.jar WordSigner`. Programmet skapar `SignedXAdES.docx` som innehåller en fullt kompatibel **digital signatur för Word‑fil**.

## Slutsats

Du vet nu hur du **digitalt signerar Word‑dokument** med Java, från att ladda filen till att applicera ett PKCS#12‑certifikat, ställa in XAdES‑EPES‑nivån och spara resultatet. Denna kompletta lösning låter dig **lägga till digital signatur till docx**‑filer i alla företagsarbetsflöden.

### Vad blir nästa steg?

- Utforska **digital signatur för Word‑fil** med tidsstämplingsservrar (RFC 3161) för långtidsvalidering.  
- Kombinera flera signaturer för flerpardsgodkännandeprocesser.  
- Integrera signeringsrutinen i en Spring Boot REST‑endpoint för att erbjuda “sign‑on‑the‑fly”-tjänster.

Känn dig fri att experimentera med olika certifikattyper, signaturpolicyer eller till och med byta till `SignatureType.CMS` om du behöver en fristående CMS‑signatur istället för XML‑DSig. Lycka till med kodandet!


## Vad bör du lära dig härnäst?


Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Detect Digital Signature on Word Document](/words/english/net/programming-with-fileformat/detect-document-signatures/)
- [Access And Verify Signature In Word Document](/words/english/net/programming-with-digital-signatures/access-and-verify-signature/)
- [Signing Existing Signature Line In Word Document](/words/english/net/programming-with-digital-signatures/signing-existing-signature-line/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}