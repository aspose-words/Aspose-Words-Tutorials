---
category: general
date: 2026-08-20
description: Leer hoe u een Word‑document ondertekent met een digitale handtekening
  voor contractbestanden. Deze gids behandelt het laden van een x509‑certificaat uit
  een PFX en het creëren van de handtekening.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- sign word document
- load x509 certificate
- digital signature for contract
- how to sign document
- load certificate from pfx
language: nl
lastmod: 2026-08-20
og_description: Onderteken Word‑document met een digitale handtekening voor contractbestanden.
  Volg deze stapsgewijze handleiding om een certificaat uit een PFX te laden en een
  XAdES EPES‑handtekening te maken.
og_image_alt: Diagram showing how to sign word document using an X509 certificate
og_title: Word-document ondertekenen in C# – X509‑certificaat laden en een digitale
  handtekening toepassen
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
title: Hoe een Word-document ondertekenen in C# met een X509-certificaat
url: /nl/java/document-security/how-to-sign-word-document-in-c-using-an-x509-certificate/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een Word‑document ondertekenen in C# met een X509‑certificaat

Als je een **word document** programmatically wilt ondertekenen, laat deze tutorial je een complete, kant‑klaar oplossing zien. Je leert hoe je een **x509 certificaat** laadt vanuit een *.pfx*‑bestand, het ondertekeningsniveau configureert en een aan de norm voldane XML‑handtekening genereert die aan een contract kan worden toegevoegd.  

De onderstaande stappen werken met .NET 6+ en de gratis GroupDocs.Signature for .NET‑bibliotheek, die de low‑level XML‑DSig‑details abstraheert terwijl je toch volledige controle over het ondertekeningsproces behoudt.

## Vereisten

- .NET 6 SDK of later geïnstalleerd  
- Visual Studio 2022 (of een IDE die .NET ondersteunt)  
- Een geldig X509‑certificaat in **PFX**‑formaat (`certificate.pfx`) met een bekend wachtwoord  
- Het NuGet‑pakket `GroupDocs.Signature` (installeren met `dotnet add package GroupDocs.Signature`)  

> **Waarom deze vereisten?**  
> De `X509Certificate2`‑klasse kan een PFX alleen lezen wanneer de privésleutel exporteerbaar is, en GroupDocs.Signature behandelt het XAdES EPES‑niveau dat vereist is voor veel **digital signature for contract**‑scenario's.

## Stap 1: Het ondertekeningscertificaat laden (x509 certificaat laden)

```csharp
using System.Security.Cryptography.X509Certificates;

// Replace with the actual path to your PFX file and its password
string certPath = @"C:\Certificates\certificate.pfx";
string certPassword = "yourPassword";

// Load the certificate that contains the private key
X509Certificate2 certificate = new X509Certificate2(certPath, certPassword,
    X509KeyStorageFlags.MachineKeySet | X509KeyStorageFlags.PersistKeySet);
```

**Uitleg**  
`X509Certificate2` leest het **certificaat uit pfx**‑bestand en maakt de privésleutel beschikbaar voor ondertekening. De vlaggen zorgen ervoor dat de sleutel in de machine‑store wordt opgeslagen, waardoor machtigingsproblemen bij Windows‑services worden voorkomen.

**Pro tip:** Als je een `CryptographicException` over sleuteltoegang ontvangt, controleer dan of het account dat de code uitvoert leesrechten heeft op het PFX‑bestand en of de sleutel als exporteerbaar is gemarkeerd.

## Stap 2: Initialiseer de SignatureHelper en wijs het certificaat toe

```csharp
using GroupDocs.Signature;
using GroupDocs.Signature.Options;

// Create the helper that will perform the signing
SignatureHelper signer = new SignatureHelper();

// Attach the previously loaded certificate
signer.SetCertificate(certificate);
```

**Uitleg**  
`SignatureHelper` is een dunne wrapper rond GroupDocs.Signature die de workflow vereenvoudigt. Door `SetCertificate` aan te roepen, geef je de bibliotheek aan welke privésleutel moet worden gebruikt voor de **how to sign document**‑operatie.

## Stap 3: Kies het XAdES‑ondertekeningsniveau (digital signature for contract)

```csharp
// XAdES_EPES is commonly required for contract signing because it embeds
// the signing certificate and timestamp information directly in the XML.
signer.SetXmlDsigLevel(XmlDsigLevel.XAdES_EPES);
```

**Uitleg**  
XAdES‑EPES (Explicit Policy‑Based Electronic Signature) voldoet aan de meeste wettelijke eisen voor een **digital signature for contract**. De bibliotheek zal automatisch de benodigde `<QualifyingProperties>`‑elementen aanmaken.

## Stap 4: Laad het Word‑document dat ondertekend zal worden

```csharp
using GroupDocs.Signature.Domain;

// The document you want to sign – a .docx contract, for example
string docPath = @"C:\Contracts\contract.docx";
Document document = new Document(docPath);
```

**Uitleg**  
`Document` vertegenwoordigt het Word‑bestand in het geheugen. Het kan elk `.docx`‑bestand zijn; dezelfde code werkt voor PDF’s of andere OpenXML‑formaten als je de bestandsextensie wijzigt.

## Stap 5: Genereer het XML‑handtekeningbestand

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

**Uitleg**  
`SignDocument` maakt een XML‑bestand dat voldoet aan het XAdES EPES‑profiel. Het resulterende `signature.xml` kan samen met het originele Word‑bestand worden verzonden of later worden ingebed met een aangepast XML‑deel.

**Verwachte output**

```
Signature saved to: C:\Contracts\signature.xml
```

Het XML‑bestand zal elementen bevatten zoals `<Signature>`, `<SignedInfo>` en `<X509Data>` die verwijzen naar het geladen **x509 certificaat laden**.

## Volledig, uitvoerbaar voorbeeld

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

Sla het bestand op als `Program.cs`, voer `dotnet run` uit, en je krijgt een ondertekend XML‑bestand dat klaar is voor juridische verificatie.

## Veelvoorkomende variaties en randgevallen

| Scenario | Wat te wijzigen | Waarom |
|----------|----------------|--------|
| **Een PDF ondertekenen in plaats van Word** | Vervang `Document` door `PdfDocument` en pas de bestandsextensie aan. | GroupDocs.Signature ondersteunt meerdere formaten; de ondertekeningsstroom blijft identiek. |
| **Een certificaat uit de Windows Store gebruiken** | Laad het certificaat via `X509Store` in plaats van een PFX‑bestand. | Handig wanneer de privésleutel nooit de machine verlaat om compliance‑redenen. |
| **Een tijdstempel toevoegen** | Roep `signer.SetTimestampProvider(new Rfc3161TimestampProvider(url))` aan. | Veel contractprocessen vereisen een vertrouwde tijdstempel om aan te tonen wanneer de handtekening is toegepast. |
| **De handtekening in de .docx insluiten** | Gebruik `signer.SignDocument(document, signaturePath, new XmlSignatureOptions { EmbedIntoDocument = true })`. | Insluiten vereenvoudigt distributie omdat er slechts één bestand nodig is. |

## Tips voor productiegebruik

- **Beveilig de PFX** – sla deze op in Azure Key Vault of AWS Secrets Manager in plaats van op het bestandssysteem.  
- **Valideer de certificaatketen** vóór ondertekening om te verzekeren dat de ondertekenaar vertrouwd wordt.  
- **Log de ondertekeningsoperatie** (certificaat‑thumbprint, document‑hash, tijdstempel) voor audit‑trails die vereist zijn door de meeste **digital signature for contract**‑beleid.  

## Conclusie

Je weet nu hoe je een **word document** programmatically kunt **ondertekenen**, hoe je een **x509 certificaat** uit een PFX‑bestand kunt **laden**, en hoe je een aan de norm voldende **digital signature for contract**‑bestanden kunt produceren. Het voorbeeld bestrijkt de volledige **how to sign document**‑workflow, van het laden van het certificaat tot het genereren van de handtekening, en bevat veelvoorkomende variaties die je in echte projecten kunt tegenkomen.

**Volgende stappen**

- Verken andere ondertekeningsniveaus zoals XAdES‑T of XAdES‑LT voor langdurige geldigheid.  
- Probeer de XML‑handtekening direct in het Word‑bestand in te sluiten met de `EmbedIntoDocument`‑optie.  
- Integreer verificatielogica (`signer.VerifyDocument`) om handtekeningen op binnenkomende contracten te bevestigen.

Voel je vrij om de code aan te passen aan je eigen projectstructuur, en veel succes met ondertekenen!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Detect Digital Signature on Word Document](/words/english/net/programming-with-fileformat/detect-document-signatures/)
- [Access And Verify Signature In Word Document](/words/english/net/programming-with-digital-signatures/access-and-verify-signature/)
- [Signing Existing Signature Line In Word Document](/words/english/net/programming-with-digital-signatures/signing-existing-signature-line/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}