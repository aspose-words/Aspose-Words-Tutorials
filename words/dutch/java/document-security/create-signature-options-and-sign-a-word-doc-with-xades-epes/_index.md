---
category: general
date: 2026-10-10
description: Maak handtekeningopties aan en onderteken een Word‑document met XAdES EPES
  in Java. Leer hoe je een Office‑document ondertekent met een certificaat in een
  paar duidelijke stappen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create signature options
- sign word doc
- sign office document
- how to sign docx
language: nl
lastmod: 2026-10-10
og_description: Maak handtekeningopties aan en onderteken een Word‑document met XAdES EPES
  in Java. Deze gids laat zien hoe je een Office‑document veilig ondertekent met een
  certificaat.
og_image_alt: Screenshot of Java code that creates signature options and signs a DOCX
  file
og_title: Maak handtekeningopties aan en onderteken een Word‑document met XAdES EPES
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
title: Maak handtekeningopties en onderteken een Word‑document met XAdES EPES
url: /nl/java/document-security/create-signature-options-and-sign-a-word-doc-with-xades-epes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak handtekeningopties aan en onderteken een Word‑document met XAdES EPES

Als je **handtekeningopties wilt maken** voor een DOCX‑bestand, laat deze gids zien hoe je een Word‑document ondertekent met het XAdES‑EPES‑niveau in Java. Je krijgt een volledig, uitvoerbaar voorbeeld dat een Office‑document ondertekent met een PFX‑certificaat in slechts een paar regels code.

Het ondertekenen van Office‑documenten is een veelvoorkomende eis voor juridische workflows, geautomatiseerde contractverwerking en veilige documentuitwisseling. In deze tutorial leer je:

* Hoe je `SignatureOptions` configureert voor XAdES‑EPES.  
* Hoe je `DigitalSignatureUtil.sign` aanroept om **word‑doc‑bestanden** te ondertekenen.  
* Hoe je veelvoorkomende valkuilen afhandelt, zoals het laden van certificaten en wachtwoordfouten.

> **Voorwaarde** – Java 17 of hoger, de GroupDocs.Signature for Java‑bibliotheek (of een compatibele XAdES‑bibliotheek), en een geldig `.pfx`‑certificaatbestand.

## Wat je nodig hebt

| Item | Reden |
|------|-------|
| Java 17+ | Moderne taalfeatures en betere beveiligings‑API's |
| GroupDocs.Signature for Java (or equivalent) | Biedt `SignatureOptions`, `XmlDsigLevel` en `DigitalSignatureUtil` |
| A PFX certificate (`.pfx`) | Levert de private sleutel voor de digitale handtekening |
| Password for the certificate | Vereist om de private sleutel te ontgrendelen |
| An unsigned DOCX file (`Unsigned.docx`) | Het bron‑document dat je wilt **office‑document ondertekenen** |

Make sure the library JAR is on your classpath:

```bash
# Example using Maven
mvn dependency:copy -Dartifact=com.groupdocs:groupdocs-signature:23.3
```

## Stap 1: Importeer de vereiste klassen

Begin met het importeren van de klassen die handtekeningen en bestands‑I/O afhandelen.

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import java.io.IOException;
```

Deze imports geven je toegang tot de API die wordt gebruikt om **handtekeningopties te maken** en om de daadwerkelijke ondertekeningsbewerking uit te voeren.

## Stap 2: Maak handtekeningopties

Het `SignatureOptions`‑object bevat alle configuratie die nodig is voor het ondertekeningsproces, zoals het handtekeningniveau, de visuele weergave en tijdstempelinstellingen.

```java
// Step 2: Create signature options
SignatureOptions signatureOptions = new SignatureOptions();
```

Het aanmaken van een nieuwe `SignatureOptions`‑instantie is de eerste stap in **hoe docx‑bestanden te ondertekenen** omdat het elke ondertekeningsaanvraag isoleert, waardoor neveneffecten tussen documenten worden voorkomen.

## Stap 3: Specificeer het XAdES‑EPES‑handtekeningniveau

XAdES‑EPES (Explicit Policy‑based Electronic Signature) is een breed geaccepteerd beleid voor Office‑documenthandtekeningen. Het instellen van het niveau vertelt de bibliotheek welk cryptografisch profiel gebruikt moet worden.

```java
// Step 3: Specify the XAdES EPES signature level
signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);
```

Waarom XAdES‑EPES? Het embedde het ondertekeningsbeleid direct in de handtekening, waardoor het ondertekende document zelf‑voorzienend is en voldoet aan vele e‑handtekening‑regelgevingen.

## Stap 4: Onderteken het DOCX‑bestand

Roep nu `DigitalSignatureUtil.sign` aan. Deze methode leest het bronbestand, past de handtekening toe en schrijft de ondertekende output.

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

**Wat gebeurt er onder de motorkap?**  
1. De bibliotheek laadt het `.pfx`‑bestand en extraheert de private sleutel met het opgegeven wachtwoord.  
2. Het maakt een XML‑DSig‑structuur die overeenkomt met het XAdES‑EPES‑profiel.  
3. De handtekening wordt ingebed in het DOCX‑pakket, waarbij de oorspronkelijke lay-out van het document behouden blijft.

Als het wachtwoord van het certificaat onjuist is of het bestand niet gelezen kan worden, wordt een `IOException` gegooid, die je zoals getoond moet afhandelen.

## Stap 5: Verifieer het ondertekende document (optioneel)

Na het ondertekenen wil je misschien bevestigen dat de handtekening aanwezig en geldig is. GroupDocs biedt een verificatie‑API, maar een snelle handmatige controle kan worden gedaan met Microsoft Word:

1. Open `SignedXades.docx` in Word.  
2. Klik op **Bestand → Info → Handtekeningen weergeven**.  
3. Word zou een groen vinkje moeten tonen dat een geldige digitale handtekening aangeeft.

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

Het uitvoeren van de verificatiestap geeft je programmatische zekerheid dat **office‑document ondertekenen** geslaagd is.

## Volledig, uitvoerbaar voorbeeld

Door alle onderdelen samen te voegen, hier is een zelfstandige Java‑klasse die je kunt kopiëren, plakken en uitvoeren.

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

**Verwachte output**

```
Document signed successfully: YOUR_DIRECTORY/SignedXades.docx
Signature verification succeeded.
```

Als er iets misgaat, toont de console een duidelijke foutmelding, waardoor je certificaat‑ of bestands‑padproblemen kunt oplossen.

## Veelgestelde vragen en afhandeling van randgevallen

| Vraag | Antwoord |
|-------|----------|
| **Kan ik een ander handtekeningniveau gebruiken?** | Ja. Vervang `XmlDsigLevel.XAdES_EPES` door `XAdES_BES`, `XAdES_T`, enz., afhankelijk van de compliance‑behoeften. |
| **Wat als mijn certificaat is opgeslagen in een keystore in plaats van een .pfx‑bestand?** | Laad de `KeyStore` handmatig, extraheer de `PrivateKey` en `Certificate`, en geef ze vervolgens door aan een overload van `sign` die een `KeyStore`‑object accepteert. |
| **Hoe voeg ik een zichtbare handtekeningafbeelding toe?** | Gebruik `signatureOptions.setSignatureImage("path/to/image.png")` vóór het aanroepen van `sign`. |
| **Is het ondertekeningsproces thread‑safe?** | De `DigitalSignatureUtil.sign`‑methode is stateless; je kunt deze veilig vanuit meerdere threads aanroepen zolang elke thread zijn eigen `SignatureOptions`‑instantie gebruikt. |
| **Wat als het DOCX‑bestand al bestaande handtekeningen bevat?** | De bibliotheek voegt een nieuw handtekening‑pakketitem toe, waarbij eerdere handtekeningen behouden blijven. Controleer of het ondertekeningsbeleid meerdere handtekeningen toestaat indien nodig. |

## Tips en best practices (E‑E‑A‑T)

* **Pro tip:** Bewaar je certificaatwachtwoord in een veilige kluis (bijv. Azure Key Vault) in plaats van het hard‑coded op te nemen.  
* **Let op:** Pad‑scheidingstekens op Windows (`\`) versus Unix (`/`). Gebruik `Paths.get(...)` om platform‑onafhankelijke paden te bouwen.  
* **Prestaties:** Het ondertekenen van grote DOCX‑bestanden kan I/O‑gebonden zijn; overweeg het streamen van het invoerbestand als je veel documenten in batch verwerkt.  
* **Compliance:** XAdES‑EPES voldoet aan de EU‑eIDAS‑regelgeving; controleer je lokale wettelijke vereisten voordat je een handtekeningniveau kiest.

## Conclusie

In deze tutorial heb je geleerd hoe je **handtekeningopties maakt** en een **Word‑document ondertekent** met het XAdES‑EPES‑niveau met Java. Het volledige voorbeeld behandelt het laden van certificaten, het configureren van opties, de ondertekeningsaanroep en optionele verificatie, waardoor je een kant‑en‑klaar oplossing krijgt voor **hoe docx‑bestanden te ondertekenen** in productie.

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Laadopties maken in Java – Ontbrekende lettertypen detecteren & hoe DOCX te laden](/words/english/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/)
- [Documentopties en -instellingen gebruiken in Aspose.Words voor Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Hoe bewerkbare bereiken te maken in alleen‑lezen documenten met Aspose.Words voor Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}