---
category: general
date: 2026-09-08
description: Hoe Word-documenten ondertekenen met een digitale handtekening‑docx‑workflow,
  een pfx‑certificaat laden en een XAdES‑handtekening maken in C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to sign word
- digital signature docx
- load pfx certificate
- digitally sign word
- create xades signature
language: nl
lastmod: 2026-09-08
og_description: Hoe Word-documenten te ondertekenen met een digitale handtekening
  docx-flow, een pfx‑certificaat te laden en een XAdES‑handtekening te maken in C#.
  Volg het volledige voorbeeld.
og_image_alt: Screenshot showing a Word document signed with XAdES EPES digital signature
og_title: Hoe onderteken je Word‑documenten met XAdES EPES in C# – stapsgewijze handleiding
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
title: Hoe Word‑documenten te ondertekenen met XAdES EPES in C#
url: /nl/net/programming-with-digital-signatures/how-to-sign-word-documents-with-xades-epes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe Word-documenten te ondertekenen met XAdES EPES in C#

Als je **how to sign word** bestanden programmatisch moet ondertekenen, laat deze gids je een complete, productie‑klare oplossing zien. Je leert hoe je een PFX‑certificaat laadt, een digitale handtekening docx configureert, en een XAdES‑EPES‑handtekening maakt die kan worden geverifieerd door Microsoft Word en validators van derden.

Het voorbeeld maakt gebruik van de GroupDocs.Signature voor .NET bibliotheek, maar de concepten zijn toepasbaar op elke API die XAdES ondersteunt. Aan het einde van de tutorial heb je een ondertekend `Signed_XAdES_EPES.docx` klaar voor distributie.

## Wat je nodig hebt

- .NET 6.0 of later (de code werkt ook met .NET Framework 4.7+)
- Een geldig PFX‑certificaatbestand (`.pfx`) dat een privésleutel bevat
- Het wachtwoord voor het PFX‑bestand
- Een Word‑document (`.docx`) dat je wilt ondertekenen
- NuGet‑pakket **GroupDocs.Signature** (installeer met `dotnet add package GroupDocs.Signature`)

## Stap 1: Installeer het vereiste NuGet‑pakket

```bash
dotnet add package GroupDocs.Signature
```

Het pakket levert de `Document`‑klasse, `XadesSignatureOptions`, en hulptype­s voor het maken van een **digitally sign word** bestand.

## Stap 2: Laad het niet-ondertekende Word‑document

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

Het laden van het document geeft je een objectmodel dat je kunt manipuleren voordat je de handtekening toepast.

## Stap 3: Laad het PFX‑certificaat (load pfx certificate)

```csharp
// Load the certificate that holds the private key
var certPath = @"C:\Certificates\mycert.pfx";
var certPassword = "yourPassword";          // keep this secret!
X509Certificate2 certificate = new X509Certificate2(certPath, certPassword);
```

> **Pro tip:** Als het certificaat is opgeslagen in de Windows‑certificaatopslag, kun je het ophalen met `X509Store` in plaats van een bestand te laden. De `load pfx certificate`‑aanpak werkt op elk platform, inclusief Linux‑containers.

## Stap 4: (Optioneel) Voeg een visuele handtekeningregel toe

Een visuele aanwijzing helpt ontvangers te zien waar de handtekening in Word verschijnt.

```csharp
// Create a signature line that will be displayed in the document
SignatureLine signatureLine = new SignatureLine(document);
signatureLine.Id = Guid.NewGuid().ToString();
signatureLine.Signer = "John Smith";
signatureLine.Title = "Approved";

// Append the line to the first paragraph of the first section
document.FirstSection.Body.FirstParagraph.AppendChild(signatureLine);
```

Als je een onzichtbare handtekening verkiest, kun je deze stap overslaan. De **digital signature docx** blijft cryptografisch geldig.

## Stap 5: Configureer XAdES‑EPES‑opties (create xades signature)

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

De `XadesSignatureType.XAdES_EPES`‑vlag vertelt de bibliotheek om de handtekening in te sluiten volgens het EPES‑profiel (Explicit Policy-based Electronic Signature), dat breed wordt geaccepteerd door de EU‑e‑IDAS‑regelgeving.

## Stap 6: Pas de digitale handtekening toe

```csharp
// Sign the document with the loaded certificate and options
document.DigitalSignatures.Sign(certificate, signOptions);
```

De `Sign`‑methode voert al het cryptografische werk uit: het maakt hash‑waarden van de documentonderdelen, creëert de XML‑DSig‑structuur, en voegt de XAdES‑envelop toe aan het Word‑bestand.

## Stap 7: Sla het ondertekende document op

```csharp
// Save the signed file – you can overwrite or create a new file
var signedPath = @"C:\Docs\Signed_XAdES_EPES.docx";
document.Save(signedPath);
Console.WriteLine($"Document signed and saved to: {signedPath}");
```

Na het opslaan, open `Signed_XAdES_EPES.docx` in Microsoft Word. Je zou een handtekeningregel moeten zien (als je er een hebt toegevoegd) en een **digitally sign word** statusbalk die aangeeft dat het bestand is ondertekend en de handtekening geldig is.

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren‑plakken in een console‑applicatie.

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

### Verwachte output

```
Signed document saved to: C:\Docs\Signed_XAdES_EPES.docx
```

Het openen van het bestand in Word toont een groene “Signed”‑banner en, als je de visuele regel hebt toegevoegd, verschijnt de handtekeningregel op de opgegeven locatie.

## Veelvoorkomende valkuilen behandelen

| Probleem | Waarom het gebeurt | Oplossing |
|----------|--------------------|-----------|
| **Certificate password is wrong** | De `X509Certificate2` constructor gooit een `CryptographicException`. | Controleer het wachtwoord, of gebruik een veilige geheimen‑manager (Azure Key Vault, AWS Secrets Manager). |
| **Word shows “Signature is invalid”** | Het document is gewijzigd na ondertekening, of het ondertekeningsbeleid ontbreekt. | Zorg ervoor dat het bestand **na** ondertekening wordt opgeslagen en niet opnieuw wordt bewerkt. Voeg het juiste XAdES‑beleid in indien vereist door je regelgevende instantie. |
| **Signature line not visible** | Het document gebruikt een andere sectie‑indeling. | Voeg de `SignatureLine` toe aan de juiste alinea of maak een nieuwe alinea aan voordat je deze toevoegt. |
| **Performance slowdown on large docs** | XAdES‑handtekeningen hash elke onderdeel van het pakket. | Gebruik streaming‑API’s (`SignAsync`) of vergroot de machine‑resources voor zeer grote bestanden (>50 MB). |

## De oplossing uitbreiden

- **Multiple signers** – roep `Sign` herhaaldelijk aan met verschillende certificaten en stel `SignatureId` in om elke ondertekenaar te onderscheiden.
- **Timestamping** – voeg een `TimestampOptions`‑object toe aan `XadesSignatureOptions` om een vertrouwde tijdstempel in te sluiten.
- **Custom policies** – lever een XML‑beleidsbestand via `XadesSignatureOptions.PolicyFilePath` voor naleving van specifieke standaarden.

## Conclusie

Je weet nu hoe je **how to sign word** documenten programmatisch kunt ondertekenen, hoe je een **load pfx certificate** laadt, en hoe je een **create xades signature** maakt met GroupDocs.Signature. De tutorial besprak elke stap van het laden van het document tot het opslaan van de ondertekende output, met praktische tips voor veelvoorkomende randgevallen.  

Vervolgens kun je gerelateerde onderwerpen verkennen, zoals **digitally sign word** PDF’s, **digital signature docx** verificatie integreren, of **timestamp**‑ondersteuning toevoegen om te voldoen aan geavanceerde compliance‑vereisten. Veel succes met ondertekenen!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Detect Digital Signature on Word Document](/words/english/net/programming-with-fileformat/detect-document-signatures/)
- [Signing Existing Signature Line In Word Document](/words/english/net/programming-with-digital-signatures/signing-existing-signature-line/)
- [Access And Verify Signature In Word Document](/words/english/net/programming-with-digital-signatures/access-and-verify-signature/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}