---
category: general
date: 2026-09-24
description: Lär dig hur du använder Aspose.Words för Java för att lägga till en digital
  signatur, signera med ett certifikat och spara det signerade dokumentet i några
  steg.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- digital signature word
- save signed document
- sign word with certificate
- certificate based signing
- aspose words signature
language: sv
lastmod: 2026-09-24
og_description: 'digital signatur Word: Den här guiden visar hur du signerar en Word-fil
  med ett certifikat med hjälp av Aspose.Words för Java och sedan sparar det signerade
  dokumentet.'
og_image_alt: Screenshot of Java code signing a Word document with Aspose.Words
og_title: Lägg till en digital signatur i ett Word‑dokument – Aspose.Words Java‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to apply a digital signature word using Aspose.Words for
    Java, sign with a certificate, and save the signed document in a few steps.
  headline: How to add a digital signature to a Word document
  type: TechArticle
- description: Learn how to apply a digital signature word using Aspose.Words for
    Java, sign with a certificate, and save the signed document in a few steps.
  name: How to add a digital signature to a Word document
  steps:
  - name: Expected output
    text: Running the program does not produce console output, but you will find a
      new file named `SignedContract.docx` in the target folder. Opening the file
      in Microsoft Word shows a blue ribbon that reads **“Signed”** along with the
      signer’s name. Clicking the signature line reveals details such as the sig
  - name: Signing a document that already contains a signature
    text: Aspose.Words allows multiple signatures in the same file. Each call to `DigitalSignatureUtil.sign`
      adds a new signature package without overwriting existing ones. If you need
      to replace an old signature, you must first remove it via the `SignatureCollection`
      API.
  - name: Using a different XML‑DSig level
    text: 'If your organization requires XAdES‑T (which includes a trusted timestamp),
      replace the option line with:'
  - name: Handling large documents
    text: For documents larger than 100 MB, consider streaming the file instead of
      loading it entirely into memory. Aspose.Words provides a `LoadOptions` constructor
      with `LoadFormat.AUTO` that works with streams, reducing heap consumption.
  type: HowTo
tags:
- Aspose.Words
- Java
- Digital Signature
- XAdES
- Certificate
title: Hur man lägger till en digital signatur i ett Word‑dokument
url: /sv/java/document-security/how-to-add-a-digital-signature-to-a-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man lägger till en digital signatur i ett Word‑dokument

Om du behöver en digital signatur för ett kontrakt, en rapport eller något officiellt dokument, guidar den här handledningen dig genom hela processen. Du kommer att lära dig hur du signerar en Word‑fil med ett certifikat, konfigurerar XAdES‑EPES‑alternativ och sparar det signerade dokumentet utan att lämna ditt Java‑projekt.

En digital signatur bevisar inte bara äkthet utan skyddar också innehållet mot oidentifierade ändringar. Stegen nedan använder Aspose.Words for Java, ett bibliotek som abstraherar de lågnivå OpenXML‑detaljerna och låter dig fokusera på signeringsflödet. Inga ytterligare tredjepartsverktyg krävs.

## Förutsättningar

Innan du börjar, se till att du har:

* Java 8 eller nyare installerat.
* En Aspose.Words for Java‑licens (gratis provversion fungerar för utvärdering).
* En PKCS#12 (`.pfx`)‑certifikatfil och dess lösenord.
* Ett Word‑dokument (`.docx`) som du vill signera.

Att ha dessa komponenter redo låter dig köra koden exakt som den visas.

## Steg 1: Ladda Word‑dokumentet för digital signatur

Den första operationen är att ladda källdokumentet i ett Aspose.Words `Document`‑objekt. Detta objekt representerar hela Word‑filen i minnet och ger dig åtkomst till signerings‑API:er.

```java
import com.aspose.words.*;

public class DigitalSignatureDemo {
    public static void main(String[] args) throws Exception {
        // Load the Word document you plan to sign
        Document doc = new Document("YOUR_DIRECTORY/Contract.docx");
```

Att ladda filen ändrar den inte; den förbereder bara den in‑memory‑representationen för nästa steg. Om filsökvägen är felaktig kastar Aspose.Words ett informativt `FileNotFoundException`, som du kan fånga för att ge ett tydligt felmeddelande.

## Steg 2: Konfigurera XAdES‑EPES‑signeringsalternativ

Aspose.Words stöder flera XML‑DSig‑nivåer. För de flesta juridiska scenarier uppfyller XAdES‑EPES (Extended Electronic Signature—Explicit Policy) efterlevnadskraven. Du skapar en `DigitalSignatureOptions`‑instans och anger den önskade nivån.

```java
        // Prepare XAdES‑EPES signing options
        DigitalSignatureOptions signatureOptions = new DigitalSignatureOptions();
        signatureOptions.setXmlDsigLevel(XmlDsigLevel.XADES_EPES);
```

Att sätta `XmlDsigLevel.XADES_EPES` instruerar biblioteket att bädda in den nödvändiga policyinformationen i signaturen. Om du behöver en annan policy (t.ex. XAdES‑T) kan du ändra enum‑värdet därefter.

## Steg 3: Applicera certifikatbaserad signering

Nu applicerar du den faktiska signaturen med metoden `DigitalSignatureUtil.sign`. Metoden kräver dokumentet, sökvägen till `.pfx`‑filen, certifikatets lösenord och de alternativ du konfigurerade i föregående steg.

```java
        // Sign the document with a certificate
        DigitalSignatureUtil.sign(
                doc,
                "YOUR_DIRECTORY/mycert.pfx",
                "certPassword",
                signatureOptions);
```

`sign`‑anropet utför alla kryptografiska operationer internt: det extraherar den privata nyckeln från PKCS#12‑behållaren, skapar XML‑DSig‑strukturen och bäddar in signaturen i dokumentet. Eftersom metoden arbetar direkt på `Document`‑instansen behöver du inte skapa en separat signerad fil först.

## Steg 4: Spara det signerade dokumentet

Efter att signaturen har applicerats måste du spara ändringarna. Använd `save`‑metoden för att skriva det signerade innehållet tillbaka till disk. Det är här nyckelordet **save signed document** kommer i spel.

```java
        // Persist the signed document
        doc.save("YOUR_DIRECTORY/SignedContract.docx");
    }
}
```

Den resulterande `SignedContract.docx` innehåller en inbäddad digital signatur som kan verifieras i Microsoft Word, LibreOffice eller någon OpenXML‑kompatibel visare. Word visar en signaturpanel som indikerar signerarens namn, signeringstid och valideringsstatus.

## Fullständig källkod för referens

När vi sätter ihop delarna ser det kompletta programmet ut så här:

```java
import com.aspose.words.*;

public class DigitalSignatureDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the Word document you plan to sign
        Document doc = new Document("YOUR_DIRECTORY/Contract.docx");

        // Step 2: Prepare XAdES‑EPES signing options
        DigitalSignatureOptions signatureOptions = new DigitalSignatureOptions();
        signatureOptions.setXmlDsigLevel(XmlDsigLevel.XADES_EPES);

        // Step 3: Sign the document with a certificate
        DigitalSignatureUtil.sign(
                doc,
                "YOUR_DIRECTORY/mycert.pfx",
                "certPassword",
                signatureOptions);

        // Step 4: Persist the signed document
        doc.save("YOUR_DIRECTORY/SignedContract.docx");
    }
}
```

### Förväntad utdata

Att köra programmet ger ingen konsolutskrift, men du kommer att hitta en ny fil med namnet `SignedContract.docx` i mål‑mappen. När du öppnar filen i Microsoft Word visas ett blått band som säger **“Signed”** tillsammans med signerarens namn. Om du klickar på signaturraden visas detaljer som signeringscertifikat, tidsstämpel och valideringsresultat.

## Vanliga variationer och specialfall

### Signera ett dokument som redan innehåller en signatur

Aspose.Words tillåter flera signaturer i samma fil. Varje anrop till `DigitalSignatureUtil.sign` lägger till ett nytt signaturpaket utan att skriva över befintliga. Om du behöver ersätta en gammal signatur måste du först ta bort den via `SignatureCollection`‑API:et.

### Använda en annan XML‑DSig‑nivå

Om din organisation kräver XAdES‑T (som inkluderar en betrodd tidsstämpel), ersätt optionsraden med:

```java
signatureOptions.setXmlDsigLevel(XmlDsigLevel.XADES_T);
```

Se till att din certifikatleverantör stödjer tidsstämpling; annars kommer signeringsanropet att kasta ett undantag.

### Hantera stora dokument

För dokument som är större än 100 MB, överväg att strömma filen istället för att ladda den helt i minnet. Aspose.Words erbjuder en `LoadOptions`‑konstruktor med `LoadFormat.AUTO` som fungerar med strömmar, vilket minskar heap‑förbrukningen.

## Proffstips

* **Validera innan du sparar** – anropa `DigitalSignatureUtil.verify(doc)` efter signering för att säkerställa att signaturen är korrekt inbäddad.
* **Skydda den privata nyckeln** – lagra `.pfx`‑filen i en säker valv (t.ex. Azure Key Vault eller AWS Secrets Manager) och hämta den vid körning istället för att hårdkoda sökvägen.
* **Logga signeringsoperationen** – inkludera dokumentnamn, signerarens identitet och tidsstämpel i dina applikationsloggar för revisionsspår.

## Slutsats

Du har nu en fungerande lösning som lägger till en digital signatur i ett Word‑dokument, använder certifikatbaserad signering och sparar det signerade dokumentet med Aspose.Words for Java. Handledningen täckte inläsning av filen, konfiguration av XAdES‑EPES, applicering av signaturen och sparande av resultatet, samt variationer som flera signaturer och alternativa signeringsnivåer.

Härifrån kan du utforska relaterade ämnen som **sign word with certificate** i PDF‑filer, integrera tidsstämpel‑auktoriteter för **certificate based signing**, eller automatisera batch‑signering av flera kontrakt. Experimentera med olika policy‑identifierare och verifieringsinställningar för att matcha din organisations efterlevnadskrav.

Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Detect Digital Signature on Word Document](/words/english/net/programming-with-fileformat/detect-document-signatures/)
- [Verify Digital Signature with Aspose.Words for Java](/words/english/java/document-operations/aspose-words-java-handling-exceptions-formats/)
- [Aspose Words Java Digital Signature Management](/words/hindi/java/security-protection/aspose-words-java-digital-signature-management/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}