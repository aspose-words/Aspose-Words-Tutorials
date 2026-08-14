---
category: general
date: 2026-08-14
description: Leer hoe je docx‑bestanden ondertekent met een PFX‑certificaat. Deze
  tutorial behandelt het instellen van PFX voor het ondertekenen van documenten, XAdES‑EPES‑opties
  en volledige Java‑code.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to sign docx
- sign document pfx
language: nl
lastmod: 2026-08-14
og_description: Hoe docx‑bestanden te ondertekenen met een PFX‑certificaat. Volg deze
  gids om het ondertekenen van documenten met PFX in te stellen, XAdES‑EPES toe te
  passen en een ondertekend DOCX in Java te genereren.
og_image_alt: Screenshot showing how to sign docx with a PFX certificate in Java
og_title: Hoe docx‑bestanden te ondertekenen met een PFX‑certificaat – volledige gids
schemas:
- author: GroupDocs
  dateModified: '2026-08-14'
  description: Learn how to sign docx files using a PFX certificate. This tutorial
    covers sign document pfx setup, XAdES‑EPES options, and full Java code.
  headline: How to sign docx files with a PFX certificate – step‑by‑step guide
  type: TechArticle
- description: Learn how to sign docx files using a PFX certificate. This tutorial
    covers sign document pfx setup, XAdES‑EPES options, and full Java code.
  name: How to sign docx files with a PFX certificate – step‑by‑step guide
  steps:
  - name: Load the PFX certificate holder
    text: The signing SDK needs a wrapper that knows where the PFX file lives and
      what password protects it. The `CertificateHolder` class encapsulates this information.
  - name: Sign the document with default XML‑DSIG settings
    text: 'The first signature demonstrates the simplest scenario: a standard XML‑DSIG
      envelope. This is useful when you only need a basic integrity check.'
  - name: Configure XAdES‑EPES signature options
    text: XAdES‑EPES (Extended Advanced Electronic Signature – Explicit Policy‑Based
      Electronic Signature) adds policy information and stronger non‑repudiation guarantees.
      To use it, you must create a `SignatureOptions` instance and set the desired
      level.
  - name: Sign the document with XAdES‑EPES
    text: Now we apply the options created in the previous step. The overload of `sign`
      that accepts a `SignatureOptions` object lets you inject the policy.
  - name: Full runnable example
    text: Combine the pieces into a single `main` method so you can execute the workflow
      with one command.
  type: HowTo
tags:
- docx signing
- pfx certificate
- java
- digital signature
title: Hoe docx‑bestanden te ondertekenen met een PFX‑certificaat – stapsgewijze handleiding
url: /nl/java/document-security/how-to-sign-docx-files-with-a-pfx-certificate-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe docx-bestanden te ondertekenen met een PFX-certificaat – stapsgewijze gids

Als je **how to sign docx** bestanden programmatisch moet ondertekenen, laat deze gids je de exacte stappen zien. Je leert hoe je **sign document pfx** bestanden ondertekent, XAdES‑EPES configureert en een verifieerbare DOCX-uitvoer produceert – alles in plain Java.

Het ondertekenen van een DOCX-bestand is een veelvoorkomende vereiste voor contractautomatisering, wettelijke naleving en veilige documentuitwisseling. Aan het einde van deze tutorial heb je een volledig, uitvoerbaar voorbeeld dat een invoer‑Word‑document twee keer ondertekent – eenmaal met de standaard XML‑DSIG‑instellingen en eenmaal met het sterkere XAdES‑EPES‑niveau.

## Vereisten

- Java 17 of nieuwer (de code gebruikt de moderne `var`‑syntaxis voor beknoptheid)
- Maven of Gradle om afhankelijkheden te beheren
- Een geldig **PFX** (PKCS #12) bestand dat een privésleutel en de certificaatketen bevat
- De GroupDocs.Signature for Java bibliotheek (of een compatibel onderteken‑SDK). Het voorbeeld gebruikt Maven‑coördinaten `com.groupdocs:groupdocs-signature:23.5`.

Als je nog geen PFX‑bestand hebt, kun je er een maken met OpenSSL:

```bash
openssl pkcs12 -export -out mycert.pfx -inkey private.key -in certificate.crt -certfile ca_bundle.crt
```

> **Pro tip:** Bescherm de PFX met een sterk wachtwoord en sla deze op buiten versiebeheer.

## Hoe docx te ondertekenen met een PFX‑certificaat

De kernworkflow bestaat uit vier logische stappen:

1. Laad het PFX‑bestand in een `CertificateHolder`.
2. Onderteken de DOCX met het standaard XML‑DSIG‑profiel.
3. Definieer XAdES‑EPES‑opties.
4. Onderteken de DOCX opnieuw met die opties.

Elke stap wordt hieronder uitgelegd, en de volledige broncode volgt de uitleg.

### Stap 1: Laad de PFX‑certificaat‑houder

Het onderteken‑SDK heeft een wrapper nodig die weet waar het PFX‑bestand zich bevindt en welk wachtwoord het beschermt. De `CertificateHolder`‑klasse omsluit deze informatie.

```java
import com.groupdocs.signature.options.sign.SignatureOptions;
import com.groupdocs.signature.utils.DigitalSignatureUtil;
import com.groupdocs.signature.options.enumerations.SignatureType;
import com.groupdocs.signature.options.enumerations.XmlDsigLevel;
import com.groupdocs.signature.certificate.CertificateHolder;

public class DocxSigner {
    // Path to the PFX file and its password
    private static final String PFX_PATH = "YOUR_DIRECTORY/mycert.pfx";
    private static final String PFX_PASSWORD = "password";

    // Helper method to create a CertificateHolder
    private static CertificateHolder loadCertificate() {
        // The CertificateHolder reads the PFX file and prepares the private key for signing
        return new CertificateHolder(PFX_PATH, PFX_PASSWORD);
    }
}
```

**Waarom dit belangrijk is:** Het SDK kan niet direct toegang krijgen tot de privésleutel; deze moet worden geladen via een veilige container. Het gebruik van `CertificateHolder` abstraheert bovendien de platform‑specifieke keystore‑afhandeling.

### Stap 2: Onderteken het document met de standaard XML‑DSIG‑instellingen

De eerste handtekening toont het eenvoudigste scenario: een standaard XML‑DSIG‑envelop. Dit is nuttig wanneer je alleen een basis‑integriteitscontrole nodig hebt.

```java
public static void signWithDefaultXmlDsig(CertificateHolder cert) throws Exception {
    String inputPath = "YOUR_DIRECTORY/input.docx";
    String outputPath = "YOUR_DIRECTORY/signed.docx";

    // The static sign method performs the actual signing operation.
    DigitalSignatureUtil.sign(
        inputPath,
        outputPath,
        cert,
        SignatureType.XML_DSIG   // Use the XML‑DSIG profile
    );

    System.out.println("Document signed with default XML‑DSIG: " + outputPath);
}
```

**Uitleg:** `DigitalSignatureUtil.sign` abstraheert de low‑level XML‑manipulatie. De constante `SignatureType.XML_DSIG` vertelt de bibliotheek om een standaard XML‑digitale handtekening te genereren die voldoet aan de W3C‑specificatie.

### Stap 3: Configureer XAdES‑EPES‑handtekeningopties

XAdES‑EPES (Extended Advanced Electronic Signature – Explicit Policy‑Based Electronic Signature) voegt beleidsinformatie en sterkere non‑repudiatie‑garanties toe. Om het te gebruiken, moet je een `SignatureOptions`‑instantie aanmaken en het gewenste niveau instellen.

```java
private static SignatureOptions createXadesEpesOptions() {
    SignatureOptions options = new SignatureOptions();
    // XAdES‑EPES is the most commonly required level for regulated environments
    options.setXmlDsigLevel(XmlDsigLevel.XADES_EPES);
    return options;
}
```

**Waarom XAdES‑EPES?** Veel juridische kaders (bijv. eIDAS in de EU) vereisen handtekeningen die een ondertekeningsbeleid embedden. Het EPES‑niveau voldoet aan die eisen zonder de overhead van volledige XAdES‑T (timestamped) handtekeningen.

### Stap 4: Onderteken het document met XAdES‑EPES

Nu passen we de opties toe die in de vorige stap zijn gemaakt. De overload van `sign` die een `SignatureOptions`‑object accepteert, stelt je in staat het beleid in te voegen.

```java
public static void signWithXadesEpes(CertificateHolder cert, SignatureOptions options) throws Exception {
    String inputPath = "YOUR_DIRECTORY/input.docx";
    String outputPath = "YOUR_DIRECTORY/signed_epes.docx";

    DigitalSignatureUtil.sign(
        inputPath,
        outputPath,
        cert,
        SignatureType.XML_DSIG, // Still XML‑DSIG, but with XAdES‑EPES policy
        options                 // Pass the configured options
    );

    System.out.println("Document signed with XAdES‑EPES: " + outputPath);
}
```

### Volledig uitvoerbaar voorbeeld

Combineer de onderdelen in één `main`‑methode zodat je de workflow met één commando kunt uitvoeren.

```java
public class DocxSigner {
    private static final String PFX_PATH = "YOUR_DIRECTORY/mycert.pfx";
    private static final String PFX_PASSWORD = "password";

    public static void main(String[] args) {
        try {
            // Load the certificate holder (sign document pfx)
            CertificateHolder cert = new CertificateHolder(PFX_PATH, PFX_PASSWORD);

            // 1️⃣ Default XML‑DSIG signature
            signWithDefaultXmlDsig(cert);

            // 2️⃣ XAdES‑EPES signature
            SignatureOptions xadesOptions = createXadesEpesOptions();
            signWithXadesEpes(cert, xadesOptions);

            System.out.println("Both signatures created successfully.");
        } catch (Exception e) {
            System.err.println("Signing failed: " + e.getMessage());
            e.printStackTrace();
        }
    }

    // --- Methods from previous sections (omitted for brevity) ---
    // signWithDefaultXmlDsig, createXadesEpesOptions, signWithXadesEpes
}
```

**Verwachte output**

```
Document signed with default XML‑DSIG: YOUR_DIRECTORY/signed.docx
Document signed with XAdES‑EPES: YOUR_DIRECTORY/signed_epes.docx
Both signatures created successfully.
```

Open `signed.docx` of `signed_epes.docx` in Microsoft Word → **File → Info → View Signatures** om te verifiëren dat de digitale handtekening verschijnt en vertrouwd wordt (mits de certificaatketen op de machine is geïnstalleerd).

## Veelgestelde vragen en randgevallen

| Vraag | Antwoord |
|----------|--------|
| *Wat als het PFX‑wachtwoord onjuist is?* | Het SDK gooit een `InvalidKeyException`. Valideer het wachtwoord voordat je `sign` aanroept. |
| *Kan ik dezelfde DOCX meerdere keren ondertekenen?* | Ja. Elke aanroep voegt een nieuw `<Signature>`‑element toe. Houd er rekening mee dat de bestandsgrootte toeneemt met elke handtekening. |
| *Moet ik het certificaat toevoegen aan de Windows Trusted Store?* | Niet voor verificatie binnen Word, maar externe validators (bijv. Adobe Acrobat) kunnen vereisen dat de keten vertrouwd wordt. |
| *Hoe een DOCX ondertekenen die al een handtekening bevat?* | Het SDK voegt automatisch een nieuw handtekening‑element toe; er is geen extra code nodig. |
| *Wat als ik een timestamp nodig heb (XAdES‑T)?* | Vervang `XmlDsigLevel.XADES_EPES` door `XmlDsigLevel.XADES_T` en geef een TSA‑URL op in `SignatureOptions`. |

## Best practices voor het ondertekenen van DOCX met een PFX‑certificaat

- **Bewaar de PFX veilig** – gebruik een kluis of omgevingsvariabele voor het wachtwoord.
- **Valideer de certificaatketen** vóór het ondertekenen om latere vertrouwensfouten te voorkomen.
- **Geef de voorkeur aan XAdES‑EPES** voor gereguleerde sectoren; val terug op plain XML‑DSIG alleen wanneer compatibiliteit een zorg is.
- **Log de ondertekeningsoperatie** (bestandsnaam, tijdstempel, ondertekenaar) voor audit‑trails.
- **Test verificatie** op meerdere platforms (Word, LibreOffice, online validators) om interoperabiliteit te waarborgen.

## Conclusie

In deze tutorial heb je geleerd **how to sign docx** bestanden te ondertekenen met een **sign document pfx** certificaat, hoe XAdES‑EPES te configureren, en hoe je twee verifieerbare handtekeningen kunt produceren met één Java‑programma. Het volledige voorbeeld kan worden gekopieerd naar elk Maven‑ of Gradle‑project, aangepast aan verschillende invoer‑paden, en uitgebreid met timestamps of aangepaste handtekening‑beleid.

Vervolgens kun je gerelateerde onderwerpen verkennen, zoals **sign PDF with a PXX certificate**, **embed visible signature images**, of **automate batch signing of multiple Word documents**. Deze uitbreidingen bouwen voort op dezelfde concepten die hier worden gepresenteerd en versterken je documentbeveiligingsworkflow verder. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Word‑document ondertekenen](/words/english/net/programming-with-digital-signatures/sign-document/)
- [Document ondertekenen](/words/hindi/net/programming-with-digital-signatures/sign-document/)
- [Document ondertekenen](/words/spanish/net/programming-with-digital-signatures/sign-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}