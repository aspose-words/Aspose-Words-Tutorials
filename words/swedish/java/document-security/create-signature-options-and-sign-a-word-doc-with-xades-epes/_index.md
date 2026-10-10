---
category: general
date: 2026-10-10
description: Skapa signaturalternativ och signera ett Word‑dokument med XAdES EPES
  i Java. Lär dig hur du signerar ett Office‑dokument med ett certifikat i några tydliga
  steg.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create signature options
- sign word doc
- sign office document
- how to sign docx
language: sv
lastmod: 2026-10-10
og_description: Skapa signeringsalternativ och signera ett Word‑dokument med XAdES EPES
  i Java. Den här guiden visar hur du signerar ett Office‑dokument säkert med ett
  certifikat.
og_image_alt: Screenshot of Java code that creates signature options and signs a DOCX
  file
og_title: Skapa signaturalternativ och signera ett Word‑dokument med XAdES EPES
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
title: Skapa signeringsalternativ och signera ett Word‑dokument med XAdES EPES
url: /sv/java/document-security/create-signature-options-and-sign-a-word-doc-with-xades-epes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa signaturalternativ och signera ett Word-dokument med XAdES EPES

Om du behöver **create signature options** för en DOCX-fil, visar den här guiden hur du signerar ett Word-dokument med XAdES‑EPES-nivån i Java. Du får ett komplett, körbart exempel som signerar ett Office-dokument med ett PFX‑certifikat på bara några rader kod.

Att signera office-dokument är ett vanligt krav för juridiska arbetsflöden, automatiserad kontraktshantering och säker dokumentutbyte. I den här handledningen kommer du att lära dig:

* Hur man konfigurerar `SignatureOptions` för XAdES‑EPES.
* Hur man anropar `DigitalSignatureUtil.sign` för att **sign word doc** filer.
* Hur man hanterar vanliga fallgropar såsom certifikatladdning och lösenordsfel.

> **Förutsättning** – Java 17 eller senare, GroupDocs.Signature for Java‑biblioteket (eller ett kompatibelt XAdES‑bibliotek) och en giltig `.pfx`‑certifikatfil.

---

## Vad du behöver

| Objekt | Orsak |
|------|--------|
| Java 17+ | Moderna språkfunktioner och bättre säkerhets‑API:er |
| GroupDocs.Signature for Java (or equivalent) | Tillhandahåller `SignatureOptions`, `XmlDsigLevel` och `DigitalSignatureUtil` |
| A PFX certificate (`.pfx`) | Tillhandahåller den privata nyckeln för den digitala signaturen |
| Password for the certificate | Krävs för att låsa upp den privata nyckeln |
| An unsigned DOCX file (`Unsigned.docx`) | Källdokumentet du vill **sign office document** |

Se till att bibliotekets JAR finns i din classpath:

```bash
# Example using Maven
mvn dependency:copy -Dartifact=com.groupdocs:groupdocs-signature:23.3
```

---

## Steg 1: Importera de nödvändiga klasserna

Börja med att importera klasserna som hanterar signaturer och fil‑I/O.

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import java.io.IOException;
```

Dessa importeringar ger dig åtkomst till API‑et som används för att **create signature options** och för att utföra den faktiska signeringsoperationen.

---

## Steg 2: Skapa signaturalternativ

`SignatureOptions`‑objektet innehåller all konfiguration som behövs för signeringsprocessen, såsom signaturnivå, visuellt utseende och tidsstämpelinställningar.

```java
// Step 2: Create signature options
SignatureOptions signatureOptions = new SignatureOptions();
```

Att skapa en ny `SignatureOptions`‑instans är det första steget i **how to sign docx**‑filer eftersom den isolerar varje signeringsbegäran och förhindrar sidoeffekter mellan dokument.

---

## Steg 3: Ange XAdES EPES‑signaturnivå

XAdES‑EPES (Explicit Policy‑based Electronic Signature) är en allmänt accepterad policy för Office‑dokumentsignaturer. Genom att ange nivån talar du om för biblioteket vilken kryptografisk profil som ska användas.

```java
// Step 3: Specify the XAdES EPES signature level
signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);
```

Varför XAdES‑EPES? Det inbäddar signaturpolicyn direkt i signaturen, vilket gör det signerade dokumentet självständigt och i enlighet med många e‑signaturregler.

---

## Steg 4: Signera DOCX‑filen

Anropa nu `DigitalSignatureUtil.sign`. Denna metod läser källfilen, applicerar signaturen och skriver den signerade utdata.

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

**Vad händer under huven?**  
1. Biblioteket laddar `.pfx`‑filen och extraherar den privata nyckeln med det angivna lösenordet.  
2. Det skapar en XML‑DSig‑struktur som matchar XAdES‑EPES‑profilen.  
3. Signaturen inbäddas i DOCX‑paketet och bevarar det ursprungliga dokumentets layout.  

Om certifikatets lösenord är felaktigt eller filen inte kan läsas, kastas ett `IOException`, vilket du bör hantera enligt exemplet.

---

## Steg 5: Verifiera det signerade dokumentet (valfritt)

Efter signering kan du vilja bekräfta att signaturen finns och är giltig. GroupDocs tillhandahåller ett verifierings‑API, men en snabb manuell kontroll kan göras med Microsoft Word:

1. Öppna `SignedXades.docx` i Word.  
2. Klicka på **File → Info → View signatures**.  
3. Word bör visa en grön bock som indikerar en giltig digital signatur.

Automatiserad verifiering med biblioteket ser ut så här:

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

Att köra verifieringssteget ger dig programmatisk förtroende för att **sign office document** lyckades.

---

## Fullt, körbart exempel

När alla bitar satts ihop, här är en självständig Java‑klass som du kan kopiera, klistra in och köra.

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

**Förväntad output**

```
Document signed successfully: YOUR_DIRECTORY/SignedXades.docx
Signature verification succeeded.
```

Om något går fel kommer konsolen att visa ett tydligt felmeddelande, vilket hjälper dig att felsöka certifikat‑ eller fil‑sökvägsproblem.

---

## Vanliga frågor och hantering av kantfall

| Question | Answer |
|----------|--------|
| **Kan jag använda en annan signaturnivå?** | Ja. Ersätt `XmlDsigLevel.XAdES_EPES` med `XAdES_BES`, `XAdES_T` osv., beroende på efterlevnadskrav. |
| **Vad händer om mitt certifikat lagras i en keystore istället för en .pfx‑fil?** | Läs in `KeyStore` manuellt, extrahera `PrivateKey` och `Certificate`, och skicka dem till en overload av `sign` som accepterar ett `KeyStore`‑objekt. |
| **Hur lägger jag till en synlig signaturbild?** | Använd `signatureOptions.setSignatureImage("path/to/image.png")` innan du anropar `sign`. |
| **Är signeringsprocessen trådsäker?** | Metoden `DigitalSignatureUtil.sign` är stateless; du kan säkert anropa den från flera trådar så länge varje tråd använder sin egen `SignatureOptions`‑instans. |
| **Vad händer om DOCX‑filen redan innehåller signaturer?** | Biblioteket kommer att lägga till ett nytt signaturpaket, och bevara tidigare signaturer. Verifiera att signaturpolicyn tillåter flera signaturer om det krävs. |

---

## Tips och bästa praxis (E‑E‑A‑T)

* **Proffstips:** Förvara ditt certifikatlösenord i en säker valv (t.ex. Azure Key Vault) istället för att hårdkoda det.  
* **Var uppmärksam på:** Fil‑sökvägsavgränsare i Windows (`\`) vs. Unix (`/`). Använd `Paths.get(...)` för att bygga plattformsoberoende sökvägar.  
* **Prestanda:** Signering av stora DOCX‑filer kan vara I/O‑beroende; överväg att strömma indatafilen om du bearbetar många dokument i batch.  
* **Efterlevnad:** XAdES‑EPES följer EU:s eIDAS‑förordning; verifiera dina lokala lagkrav innan du väljer en signaturnivå.

---

## Slutsats

I den här handledningen har du lärt dig hur du **create signature options** och **sign a Word doc** med XAdES‑EPES‑nivån med Java. Det kompletta exemplet täcker certifikatladdning, konfiguration av alternativ, signeringsanropet och valfri verifiering, vilket ger dig en färdig lösning för **how to sign docx**‑filer i produktion.

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa laddningsalternativ i Java – Upptäck saknade teckensnitt & hur man laddar DOCX](/words/english/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/)
- [Använda dokumentalternativ och inställningar i Aspose.Words för Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Hur man skapar redigerbara områden i skrivskyddade dokument med Aspose.Words för Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}