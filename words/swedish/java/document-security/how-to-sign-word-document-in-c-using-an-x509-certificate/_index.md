---
category: general
date: 2026-08-20
description: Lär dig hur du signerar Word-dokument med en digital signatur för kontraktsfiler.
  Denna guide täcker hur du laddar ett x509‑certifikat från en PFX och skapar signaturen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- sign word document
- load x509 certificate
- digital signature for contract
- how to sign document
- load certificate from pfx
language: sv
lastmod: 2026-08-20
og_description: Signera Word‑dokument med en digital signatur för kontraktsfiler.
  Följ den här steg‑för‑steg‑guiden för att ladda ett certifikat från PFX och skapa
  en XAdES EPES‑signatur.
og_image_alt: Diagram showing how to sign word document using an X509 certificate
og_title: Signera Word-dokument i C# – ladda X509‑certifikat och applicera en digital
  signatur
schemas:
- author: GroupDocs
  dateModified: '2026-08-20'
  description: Learn how to sign word document with a digital signature for contract
    files. This guide covers loading x509 certificate from a PFX and creating the
    signature.
  headline: How to sign word document in C# using an X509 certificate
  type: TechArticle
tags:
- digital signature
- C#
- X509Certificate2
title: Hur man signerar Word-dokument i C# med ett X509‑certifikat
url: /sv/java/document-security/how-to-sign-word-document-in-c-using-an-x509-certificate/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man signerar Word-dokument i C# med ett X509‑certifikat

Om du behöver **signera Word-dokument** programatiskt visar den här handledningen en komplett, färdig‑att‑kör lösning. Du kommer att lära dig hur du **läser in x509‑certifikat** från en *.pfx*-fil, konfigurerar signaturnivån och genererar en standard‑kompatibel XML‑signatur som kan bifogas ett avtal.  

Stegen nedan fungerar med .NET 6+ och det kostnadsfria GroupDocs.Signature for .NET‑biblioteket, som abstraherar de lågnivå XML‑DSig‑detaljerna samtidigt som du behåller full kontroll över signeringsprocessen.

## Förutsättningar

- .NET 6 SDK eller senare installerat  
- Visual Studio 2022 (eller någon IDE som stödjer .NET)  
- Ett giltigt X509‑certifikat i **PFX**‑format (`certificate.pfx`) med ett känt lösenord  
- NuGet‑paketet `GroupDocs.Signature` (installera med `dotnet add package GroupDocs.Signature`)  

> **Varför dessa förutsättningar?**  
> Klassen `X509Certificate2` kan läsa en PFX endast när den privata nyckeln är exportabel, och GroupDocs.Signature hanterar XAdES EPES‑nivån som krävs för många **digitala signaturer för avtal** scenarier.

## Steg 1: Läs in signeringscertifikatet (läs in x509‑certifikat)

```csharp
using System.Security.Cryptography.X509Certificates;

// Replace with the actual path to your PFX file and its password
string certPath = @"C:\Certificates\certificate.pfx";
string certPassword = "yourPassword";

// Load the certificate that contains the private key
X509Certificate2 certificate = new X509Certificate2(certPath, certPassword,
    X509KeyStorageFlags.MachineKeySet | X509KeyStorageFlags.PersistKeySet);
```

**Förklaring**  
`X509Certificate2` läser **ladda certifikat från pfx**‑filen och gör den privata nyckeln tillgänglig för signering. Flaggan säkerställer att nyckeln lagras i maskinlagret, vilket undviker behörighetsproblem på Windows‑tjänster.

**Proffstips:** Om du får ett `CryptographicException` om nyckelåtkomst, kontrollera att kontot som kör koden har läsrättighet till PFX‑filen och att nyckeln är markerad som exportabel.

## Steg 2: Initiera SignatureHelper och tilldela certifikatet

```csharp
using GroupDocs.Signature;
using GroupDocs.Signature.Options;

// Create the helper that will perform the signing
SignatureHelper signer = new SignatureHelper();

// Attach the previously loaded certificate
signer.SetCertificate(certificate);
```

**Förklaring**  
`SignatureHelper` är ett lätt omslag runt GroupDocs.Signature som förenklar arbetsflödet. Genom att anropa `SetCertificate` talar du om för biblioteket vilken privat nyckel som ska användas för **hur man signerar dokument**‑operationen.

## Steg 3: Välj XAdES‑signaturnivå (digital signatur för avtal)

```csharp
// XAdES_EPES is commonly required for contract signing because it embeds
// the signing certificate and timestamp information directly in the XML.
signer.SetXmlDsigLevel(XmlDsigLevel.XAdES_EPES);
```

**Förklaring**  
XAdES‑EPES (Explicit Policy‑Based Electronic Signature) uppfyller de flesta lagkrav för en **digital signatur för avtal**. Biblioteket kommer automatiskt att skapa de nödvändiga `<QualifyingProperties>`‑elementen.

## Steg 4: Läs in Word‑dokumentet som ska signeras

```csharp
using GroupDocs.Signature.Domain;

// The document you want to sign – a .docx contract, for example
string docPath = @"C:\Contracts\contract.docx";
Document document = new Document(docPath);
```

**Förklaring**  
`Document` representerar Word‑filen i minnet. Det kan vara vilken `.docx`‑fil som helst; samma kod fungerar för PDF‑filer eller andra OpenXML‑format om du ändrar filändelsen.

## Steg 5: Generera XML‑signaturfilen

```csharp
// Destination for the generated XML signature
string signaturePath = @"C:\Contracts\signature.xml";

// Perform the signing operation
signer.SignDocument(document, signaturePath);

// Optional: verify that the file was created
if (System.IO.File.Exists(signaturePath))
{
    Console.WriteLine($"Signature saved to: {signaturePath}");
}
```

**Förklaring**  
`SignDocument` skapar en XML‑fil som följer XAdES EPES‑profilen. Den resulterande `signature.xml` kan skickas tillsammans med den ursprungliga Word‑filen eller inbäddas senare med ett anpassat XML‑del.

**Förväntat resultat**

```
Signature saved to: C:\Contracts\signature.xml
```

XML‑filen kommer att innehålla element som `<Signature>`, `<SignedInfo>` och `<X509Data>` som refererar till det inlästa **ladda x509‑certifikat**.

## Fullt, körbart exempel

```csharp
using System;
using System.Security.Cryptography.X509Certificates;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;

class Program
{
    static void Main()
    {
        // 1. Load the signing certificate (load x509 certificate)
        string certPath = @"C:\Certificates\certificate.pfx";
        string certPassword = "yourPassword";
        X509Certificate2 certificate = new X509Certificate2(certPath, certPassword,
            X509KeyStorageFlags.MachineKeySet | X509KeyStorageFlags.PersistKeySet);

        // 2. Initialize the SignatureHelper and assign the certificate
        SignatureHelper signer = new SignatureHelper();
        signer.SetCertificate(certificate);

        // 3. Set the XAdES signature level (digital signature for contract)
        signer.SetXmlDsigLevel(XmlDsigLevel.XAdES_EPES);

        // 4. Load the Word document that will be signed
        string docPath = @"C:\Contracts\contract.docx";
        Document document = new Document(docPath);

        // 5. Generate the XML signature file
        string signaturePath = @"C:\Contracts\signature.xml";
        signer.SignDocument(document, signaturePath);

        // Confirmation
        Console.WriteLine(File.Exists(signaturePath)
            ? $"Signature saved to: {signaturePath}"
            : "Failed to create signature file.");
    }
}
```

Spara filen som `Program.cs`, kör `dotnet run`, så får du en signerad XML‑fil klar för juridisk verifiering.

## Vanliga variationer och kantfall

| Scenario | Vad som ska ändras | Varför |
|----------|--------------------|--------|
| **Signera en PDF istället för Word** | Ersätt `Document` med `PdfDocument` och justera filändelsen. | GroupDocs.Signature stödjer flera format; signeringsflödet förblir identiskt. |
| **Använda ett certifikat från Windows Store** | Läs in certifikatet via `X509Store` istället för en PFX‑fil. | Användbart när den privata nyckeln aldrig lämnar maskinen av efterlevnadsskäl. |
| **Lägga till en tidsstämpel** | Anropa `signer.SetTimestampProvider(new Rfc3161TimestampProvider(url))`. | Många avtalsflöden kräver en betrodd tidsstämpel för att bevisa när signaturen applicerades. |
| **Bädda in signaturen i .docx‑filen** | Använd `signer.SignDocument(document, signaturePath, new XmlSignatureOptions { EmbedIntoDocument = true })`. | Inbäddning förenklar distribution eftersom endast en fil behövs. |

## Tips för produktion

- **Säkra PFX‑filen** – lagra den i Azure Key Vault eller AWS Secrets Manager istället för filsystemet.  
- **Validera certifikatkedjan** innan signering för att säkerställa att undertecknaren är betrodd.  
- **Logga signeringsoperationen** (certifikatets thumbprint, dokumenthash, tidsstämpel) för revisionsspår som krävs av de flesta **digitala signaturer för avtal**‑policyer.  

## Slutsats

Du vet nu hur du **signerar Word-dokument** programatiskt, hur du **läser in x509‑certifikat** från en PFX‑fil, och hur du producerar standard‑kompatibla **digitala signaturer för avtal**‑filer. Exemplet täcker hela **hur man signerar dokument**‑arbetsflödet, från certifikatladdning till signaturgenerering, och inkluderar vanliga variationer du kan stöta på i riktiga projekt.

**Nästa steg**

- Utforska andra signaturnivåer såsom XAdES‑T eller XAdES‑LT för längre giltighetstid.  
- Prova att bädda in XML‑signaturen direkt i Word‑filen med `EmbedIntoDocument`‑alternativet.  
- Integrera verifieringslogik (`signer.VerifyDocument`) för att bekräfta signaturer på inkommande avtal.

Känn dig fri att anpassa koden till din egen projektstruktur, och lycka till med signeringen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Upptäck digital signatur i Word-dokument](/words/english/net/programming-with-fileformat/detect-document-signatures/)
- [Åtkomst och verifiera signatur i Word-dokument](/words/english/net/programming-with-digital-signatures/access-and-verify-signature/)
- [Signera befintlig signaturlinje i Word-dokument](/words/english/net/programming-with-digital-signatures/signing-existing-signature-line/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}