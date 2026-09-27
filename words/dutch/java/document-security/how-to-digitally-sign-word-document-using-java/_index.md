---
category: general
date: 2026-09-27
description: Leer hoe je een Word‑document digitaal ondertekent in Java. Deze gids
  laat zien hoe je een digitale handtekening toevoegt aan een Word‑bestand en hoe
  je een digitale handtekening aan een docx toevoegt volgens de best practices.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- digitally sign word document
- digital signature for word file
- add digital signature to docx
language: nl
lastmod: 2026-09-27
og_description: Digitale onderteken Word‑document met Java. Volg deze tutorial om
  een digitale handtekening toe te voegen aan een Word‑bestand en leer hoe je veilig
  een digitale handtekening aan een docx kunt toevoegen.
og_image_alt: Screenshot showing a Java program that digitally signs a Word document
og_title: Word-document digitaal ondertekenen in Java – complete stapsgewijze handleiding
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
title: Hoe een Word-document digitaal te ondertekenen met Java
url: /nl/java/document-security/how-to-digitally-sign-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een Word-document digitaal te ondertekenen met Java

Als u een **Word-document digitaal wilt ondertekenen** in een Java-toepassing, laat deze gids u de exacte stappen zien. U ziet hoe u een **digitale handtekening voor een Word‑bestand** kunt toevoegen en veilig **een digitale handtekening aan een docx kunt toevoegen** met GroupDocs.Signature (of een vergelijkbare bibliotheek).  

Het proces is eenvoudig: laad de `.docx`, pas een PKCS#12‑certificaat toe, configureer het XML‑DSig‑niveau en sla het ondertekende bestand op. Aan het einde van deze tutorial heeft u een uitvoerbaar programma dat een conforme XAdES‑EPES‑handtekening genereert.

## Vereisten

- Java 17 of nieuwer (de code compileert ook met Java 11)  
- Maven of Gradle voor afhankelijkheidsbeheer  
- Een PKCS#12 (`.pfx`) certificaatbestand en het bijbehorende wachtwoord  
- Basiskennis van Java I/O  

> **Pro tip:** Bewaar het certificaatwachtwoord in een veilige kluis (bijv. Azure Key Vault) in plaats van het hard‑gecodeerd op te nemen.

## Stap 1: Voeg de GroupDocs.Signature‑afhankelijkheid toe

Als u Maven gebruikt, voeg dan het volgende toe aan uw `pom.xml`. Voor Gradle wordt de equivalente `implementation`‑regel in de commentaar weergegeven.

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

Deze artefacten leveren `Document`, `DigitalSignatureUtil` en de gerelateerde enums die in het voorbeeld worden gebruikt.

## Stap 2: Laad het Word-document dat u wilt ondertekenen

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

**Waarom dit belangrijk is:** Het laden van het bestand in het `Document`‑object van de bibliotheek geeft u volledige toegang tot handtekeningvelden en inhoudsmanipulatie zonder het oorspronkelijke bestand op schijf te wijzigen.

## Stap 3: Pas een digitale handtekening toe met een PKCS#12‑certificaat

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

**Uitleg:**  
- `SignatureType.XML_DSIG` geeft de bibliotheek de opdracht een XML‑DSig‑handtekening te maken, wat vereist is voor XAdES‑conformiteit.  
- Het gebruik van een PKCS#12‑certificaat zorgt ervoor dat de handtekening cryptografisch sterk is en kan worden gevalideerd door standaardtools (bijv. Microsoft Word, Adobe Acrobat).

## Stap 4: Stel het XAdES‑EPES‑niveau in voor sterkere conformiteit

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

**Waarom XAdES‑EPES?**  
XAdES‑EPES voegt tijdstempels en ondertekeningsbeleid toe, waardoor de handtekening juridisch toelaatbaar is in veel rechtsgebieden. Het is het aanbevolen niveau wanneer u een **digitale handtekening voor een Word‑bestand** nodig heeft die voldoet aan e‑IDAS of vergelijkbare regelgeving.

## Stap 5: Sla het ondertekende document op

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

**Resultaat:** Na het uitvoeren van het programma bevat `SignedXAdES.docx` een zichtbaar handtekeningveld. Het openen van het bestand in Microsoft Word toont *Signed and all signatures are valid* als de certificaatketen vertrouwd is.

### Verwachte console‑output

```
Document loaded successfully.
Digital signature applied.
Signature level set to XAdES‑EPES.
Signed document saved to: YOUR_DIRECTORY/SignedXAdES.docx
```

## Meerdere handtekeningvelden verwerken (geavanceerd)

Als uw sjabloon al meerdere handtekening‑plaatsaanduidingen bevat, kunt u er over itereren:

```java
for (SignatureSignatureField field : document.getSignatureFields()) {
    field.setXmlDsigLevel(XmlDsigLevel.XADES_EPES);
}
```

Dit zorgt ervoor dat **een digitale handtekening aan een docx** wordt toegevoegd op elke vereiste locatie, nuttig voor workflows met meerdere ondertekenaars.

## Veelvoorkomende valkuilen en hoe ze te vermijden

| Probleem | Oorzaak | Oplossing |
|----------|---------|-----------|
| *Handtekeningveld niet aangemaakt* | Gebruik van een niet‑XML handtekeningtype (bijv. `SignatureType.CMS`) | Gebruik altijd `SignatureType.XML_DSIG` wanneer u XAdES‑niveaus wilt instellen |
| *Word toont ‘Signature is not valid’* | Certificaatketen niet vertrouwd op de lokale machine | Importeer de root-/intermediaire certificaten in de Windows Trusted Root‑store |
| *Bestandsgrootte explodeert* | Het document opslaan zonder compressie | Roep `document.save(outputPath, SaveOptions.create().setCompress(true))` aan |

## Volledig uitvoerbaar voorbeeld (copy‑paste)

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

Voer de klasse uit met `java -cp target/your‑jar.jar WordSigner`. Het programma maakt `SignedXAdES.docx` aan met een volledig conforme **digitale handtekening voor een Word‑bestand**.

## Conclusie

U weet nu hoe u een **Word-document digitaal kunt ondertekenen** met Java, van het laden van het bestand tot het toepassen van een PKCS#12‑certificaat, het instellen van het XAdES‑EPES‑niveau en het opslaan van het resultaat. Deze volledige oplossing stelt u in staat **een digitale handtekening aan een docx** toe te voegen in elke bedrijfsworkflow.

### Wat is het volgende?

- Verken **digital signature for Word file** met timestamp‑servers (RFC 3161) voor langetermijnvalidatie.  
- Combineer meerdere handtekeningen voor goedkeuringsprocessen met meerdere partijen.  
- Integreer de ondertekeningsroutine in een Spring Boot REST‑endpoint om ‘sign‑on‑the‑fly’ services aan te bieden.

Voel u vrij om te experimenteren met verschillende certificaattype­s, ondertekeningsbeleid, of zelfs over te schakelen naar `SignatureType.CMS` als u een detached CMS‑handtekening nodig heeft in plaats van XML‑DSig. Veel programmeerplezier!

## Wat moet u hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om u te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in uw eigen projecten te verkennen.

- [Detect Digital Signature on Word Document](/words/english/net/programming-with-fileformat/detect-document-signatures/)
- [Access And Verify Signature In Word Document](/words/english/net/programming-with-digital-signatures/access-and-verify-signature/)
- [Signing Existing Signature Line In Word Document](/words/english/net/programming-with-digital-signatures/signing-existing-signature-line/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}