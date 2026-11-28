---
category: general
date: 2026-09-05
description: Leer hoe je Word ondertekent met een certificaat in C# met behulp van
  Aspose.Words. Deze stapsgewijze handleiding behandelt XAdES‑EPES ondertekening met
  een PFX‑certificaat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- sign word with certificate
- XAdES EPES signing
- Aspose.Words digital signature
- C# sign Word document
- digital signature with certificate
- XadesSignatureOptions
language: nl
lastmod: 2026-09-05
og_description: Onderteken Word met certificaat met Aspose.Words in C#. Volg dit volledige
  voorbeeld om een XAdES‑EPES-handtekening te maken met uw PFX‑bestand.
og_image_alt: Screenshot showing a Word document that has been signed with a certificate
og_title: Word ondertekenen met certificaat in C# – stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to sign Word with certificate in C# using Aspose.Words. This
    step‑by‑step guide covers XAdES‑EPES signing with a PFX certificate.
  headline: How to sign Word with certificate using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- digital signature
- XAdES
- certificate
title: Hoe Word te ondertekenen met een certificaat met Aspose.Words in C#
url: /nl/net/programming-with-digital-signatures/how-to-sign-word-with-certificate-using-aspose-words-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe Word te ondertekenen met certificaat met Aspose.Words in C#

Als je **Word wilt ondertekenen met een certificaat** in een .NET‑applicatie, toont deze gids een complete, kant‑klaar werkende oplossing. Aan het einde van de tutorial heb je een ondertekend .docx‑bestand dat voldoet aan de XAdES‑EPES (Explicit Policy‑based Electronic Signature)‑norm.

Het programmatisch ondertekenen van een Word‑document verwijdert de handmatige stappen van het openen van het bestand in Microsoft Word en het toepassen van een handtekening. Je leert hoe je een niet‑ondertekend document laadt, XAdES‑EPES‑opties configureert, een digitale handtekening toepast met een PFX‑certificaat, en het ondertekende resultaat opslaat — alles met Aspose.Words voor .NET.

## Vereisten

Voordat je begint, zorg dat je het volgende hebt:

* .NET 6.0 SDK of later geïnstalleerd  
* Een Aspose.Words for .NET‑licentie (of een tijdelijke evaluatiesleutel)  
* Een PFX‑certificaatbestand (`.pfx`) dat de privésleutel en het wachtwoord bevat  
* Visual Studio 2022 of een andere C#‑compatibele IDE  

Dit zijn de enige externe afhankelijkheden; de onderstaande code werkt direct zodra ze aanwezig zijn.

## Stap 1: Laad het niet‑ondertekende Word‑document

De eerste handeling is het lezen van het bron‑`.docx`‑bestand dat je wilt ondertekenen. Het laden van het document creëert een in‑memory‑representatie die Aspose.Words kan manipuleren.

```csharp
using Aspose.Words;
using Aspose.Words.Signing;

// Replace with the actual path to your unsigned document
string sourcePath = @"C:\Docs\Unsigned.docx";

Document document = new Document(sourcePath);
```

*Waarom deze stap belangrijk is*: De `Document`‑klasse is het toegangspunt voor alle Word‑verwerkingsfuncties in Aspose.Words. Zonder het bestand te laden, is er niets om te ondertekenen.

## Stap 2: Configureer XAdES‑EPES‑handtekeningopties

XAdES‑EPES voegt een expliciete beleidsreferentie toe aan de handtekening, wat vereist is voor veel compliance‑scenario’s (bijv. EU eIDAS). Het `XadesSignatureOptions`‑object laat je het beleids‑identificatie, de hash en het hash‑algoritme definiëren.

```csharp
// Create XAdES‑EPES options
XadesSignatureOptions xadesOptions = new XadesSignatureOptions
{
    SignaturePolicyInfo = new XadesSignaturePolicyInfo
    {
        Identifier = "YourPolicyIdentifier",          // Unique policy ID
        Hash = "ABCD1234...",                         // Base‑64 encoded hash of the policy document
        HashAlgorithm = XadesHashAlgorithm.Sha256   // Strong hash algorithm
    },
    IsEpesEnabled = true // Turn on EPES support
};
```

*Waarom deze stap belangrijk is*: Het instellen van `IsEpesEnabled` op `true` vertelt Aspose.Words de beleidsreferentie in te sluiten, waardoor een gewone XAdES‑handtekening een EPES‑conforme handtekening wordt. Dit voldoet aan auditors die een gedocumenteerd ondertekeningsbeleid eisen.

## Stap 3: Pas de digitale handtekening toe met je certificaat

Nu koppel je het certificaat (`.pfx`) en roep je de `DigitalSignature.Sign`‑methode aan. Het wachtwoord beschermt de privésleutel in het PFX‑bestand.

```csharp
// Path to your certificate and its password
string certPath = @"C:\Certificates\mycert.pfx";
string certPassword = "yourPassword";

// Apply the signature
document.DigitalSignature.Sign(certPath, certPassword, xadesOptions);
```

*Waarom deze stap belangrijk is*: De `Sign`‑methode voert de cryptografische bewerkingen uit: het berekent de hash van het document, maakt de XML‑DSig‑structuur en embedt de handtekeningonderdelen in het Word‑bestand. Het gebruik van een certificaat zorgt voor niet‑weerlegbaarheid en integriteitsverificatie door elke Office‑compatibele viewer.

### Pro tip

Als je applicatie op een server zonder UI draait, sla het certificaat dan op in een veilige kluis (Azure Key Vault, AWS Secrets Manager) en laad het in een `X509Certificate2`‑object, waarna je dat object aan `Sign` doorgeeft in plaats van een bestands­pad.

## Stap 4: Sla het ondertekende document op

Tot slot schrijf je het ondertekende document naar schijf. Je kunt het originele bestand overschrijven of een nieuw bestand aanmaken; het voorbeeld hieronder maakt een nieuw bestand om de niet‑ondertekende versie intact te houden.

```csharp
// Destination path for the signed file
string signedPath = @"C:\Docs\SignedXadesEpes.docx";

document.Save(signedPath);
```

*Waarom deze stap belangrijk is*: Opslaan persisteert de handtekening‑XML binnen het Word‑pakket. Het openen van `SignedXadesEpes.docx` in Microsoft Word toont een “Signed”‑badge, en de handtekeningdetails kunnen worden bekeken via het **File → Info → View Signatures**‑paneel.

## Volledig werkend voorbeeld

Alle onderdelen samengevoegd, hier is een zelfstandige console‑applicatie die je kunt kopiëren, plakken en uitvoeren:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Signing;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the unsigned document
        string sourcePath = @"C:\Docs\Unsigned.docx";
        Document doc = new Document(sourcePath);

        // 2️⃣ Set up XAdES‑EPES options
        XadesSignatureOptions xadesOptions = new XadesSignatureOptions
        {
            SignaturePolicyInfo = new XadesSignaturePolicyInfo
            {
                Identifier = "YourPolicyIdentifier",
                Hash = "ABCD1234...", // Replace with actual Base‑64 hash
                HashAlgorithm = XadesHashAlgorithm.Sha256
            },
            IsEpesEnabled = true
        };

        // 3️⃣ Apply the signature using a PFX certificate
        string certPath = @"C:\Certificates\mycert.pfx";
        string certPassword = "yourPassword";
        doc.DigitalSignature.Sign(certPath, certPassword, xadesOptions);

        // 4️⃣ Save the signed document
        string signedPath = @"C:\Docs\SignedXadesEpes.docx";
        doc.Save(signedPath);

        Console.WriteLine("Document signed successfully: " + signedPath);
    }
}
```

**Verwachte output**: De console print `Document signed successfully: C:\Docs\SignedXadesEpes.docx`. Het openen van het opgeslagen bestand in Word toont een geldige digitale handtekening die voldoet aan XAdES‑EPES.

## Veelgestelde vragen & randgevallen

| Vraag | Antwoord |
|----------|--------|
| *Kan ik een document ondertekenen dat al een handtekening bevat?* | Ja. Aspose.Words ondersteunt meerdere handtekeningen. Roep `Sign` opnieuw aan met een nieuwe `XadesSignatureOptions`‑instantie. |
| *Wat als ik een ander hash‑algoritme nodig heb?* | Stel `HashAlgorithm` in op `XadesHashAlgorithm.Sha1`, `Sha384` of `Sha512` zoals vereist door je beleid. |
| *Hoe verifieer ik de handtekening programmatisch?* | Gebruik `DigitalSignatureUtil.Verify` of de `SignatureCollection`‑API om handtekeningen te enumereren en te valideren. |
| *Wordt XAdES‑EPES ondersteund op .NET Core?* | Volledig ondersteund vanaf Aspose.Words 22.9 op .NET 5/6/7. |
| *Wat als het certificaat is opgeslagen in de Windows‑certificaatopslag?* | Laad het met `new X509Certificate2(StoreName.My, StoreLocation.CurrentUser, certThumbprint)` en geef het `X509Certificate2`‑object door aan `Sign`. |

## Conclusie

Je weet nu hoe je **Word kunt ondertekenen met een certificaat** met behulp van Aspose.Words in C#. De tutorial behandelde het laden van een document, het configureren van XAdES‑EPES‑opties, het toepassen van een digitale handtekening met een PFX‑certificaat, en het opslaan van het ondertekende bestand. Dit end‑to‑end‑voorbeeld voldoet aan compliance‑eisen en kan worden geïntegreerd in elke geautomatiseerde document‑generatie‑pipeline.

### Volgende stappen

* Verdiep je verder in **XAdES EPES‑ondertekening** door een timestamp‑server toe te voegen (`XadesTimestampOptions`).  
* Combineer deze aanpak met **Aspose.PDF** om het ondertekende Word‑bestand om te zetten naar een ondertekende PDF.  
* Leer hoe je **digitale validatie** kunt uitvoeren.

## Wat moet je hierna leren?


De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [How to Load Word Documents Using Aspose.Words LoadOptions](/words/english/net/programming-with-loadoptions/)
- [Add Text Watermark in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-watermark/add-text-watermark/)
- [convert word to pdf in C# using Aspose.Words – Guide](/words/english/net/basic-conversions/convert-word-to-pdf-in-c-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}