---
category: general
date: 2026-09-08
description: Hur man signerar Word-dokument med ett digitalt signatur‑docx‑arbetsflöde,
  laddar pfx‑certifikat och skapar XAdES‑signatur i C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to sign word
- digital signature docx
- load pfx certificate
- digitally sign word
- create xades signature
language: sv
lastmod: 2026-09-08
og_description: Hur man signerar Word-dokument med ett digitalt signatur‑docx‑flöde,
  laddar pfx‑certifikat och skapar XAdES‑signatur i C#. Följ det fullständiga exemplet.
og_image_alt: Screenshot showing a Word document signed with XAdES EPES digital signature
og_title: Hur man signerar Word‑dokument med XAdES EPES i C# – steg‑för‑steg‑guide
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
title: Hur man signerar Word-dokument med XAdES EPES i C#
url: /sv/net/programming-with-digital-signatures/how-to-sign-word-documents-with-xades-epes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man signerar Word‑dokument med XAdES EPES i C#

Om du behöver **signera Word**‑filer programatiskt visar den här guiden en komplett, produktionsklar lösning. Du lär dig hur du laddar ett PFX‑certifikat, konfigurerar en digital signatur för docx och skapar en XAdES‑EPES‑signatur som kan verifieras av Microsoft Word och tredjepartsvaliderare.

Exemplet använder GroupDocs.Signature för .NET‑biblioteket, men koncepten gäller för alla API:er som stödjer XAdES. I slutet av tutorialen har du ett signerat `Signed_XAdES_EPES.docx` klart för distribution.

## Vad du behöver

- .NET 6.0 eller senare (koden fungerar också med .NET Framework 4.7+)
- En giltig PFX‑certifikatfil (`.pfx`) som innehåller en privat nyckel
- Lösenordet för PFX‑filen
- Ett Word‑dokument (`.docx`) som du vill signera
- NuGet‑paketet **GroupDocs.Signature** (installera med `dotnet add package GroupDocs.Signature`)

## Steg 1: Installera det erforderliga NuGet‑paketet

```bash
dotnet add package GroupDocs.Signature
```

Paketet tillhandahåller klassen `Document`, `XadesSignatureOptions` och hjälptyper för att skapa en **digitalt signerad Word**‑fil.

## Steg 2: Ladda det osignerade Word‑dokumentet

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

När du laddar dokumentet får du en objektmodell som du kan manipulera innan du applicerar signaturen.

## Steg 3: Ladda PFX‑certifikatet (load pfx certificate)

```csharp
// Load the certificate that holds the private key
var certPath = @"C:\Certificates\mycert.pfx";
var certPassword = "yourPassword";          // keep this secret!
X509Certificate2 certificate = new X509Certificate2(certPath, certPassword);
```

> **Proffstips:** Om certifikatet lagras i Windows‑certifikatlagret kan du hämta det med `X509Store` istället för att läsa in en fil. Metoden **load pfx certificate** fungerar på alla plattformar, inklusive Linux‑behållare.

## Steg 4: (Valfritt) Lägg till en visuell signaturlinje

En visuell ledtråd hjälper mottagare att se var signaturen visas i Word.

```csharp
// Create a signature line that will be displayed in the document
SignatureLine signatureLine = new SignatureLine(document);
signatureLine.Id = Guid.NewGuid().ToString();
signatureLine.Signer = "John Smith";
signatureLine.Title = "Approved";

// Append the line to the first paragraph of the first section
document.FirstSection.Body.FirstParagraph.AppendChild(signatureLine);
```

Om du föredrar en osynlig signatur kan du hoppa över detta steg. **Digital signature docx** kommer fortfarande att vara kryptografiskt giltig.

## Steg 5: Konfigurera XAdES‑EPES‑alternativ (create xades signature)

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

Flaggan `XadesSignatureType.XAdES_EPES` instruerar biblioteket att bädda in signaturen enligt EPES‑profilen (Explicit Policy‑based Electronic Signature), som är brett accepterad enligt EU:s e‑IDAS‑regler.

## Steg 6: Applicera den digitala signaturen

```csharp
// Sign the document with the loaded certificate and options
document.DigitalSignatures.Sign(certificate, signOptions);
```

Metoden `Sign` utför allt kryptografiskt arbete: den hash‑ar dokumentdelarna, skapar XML‑DSig‑strukturen och infogar XAdES‑omslaget i Word‑filen.

## Steg 7: Spara det signerade dokumentet

```csharp
// Save the signed file – you can overwrite or create a new file
var signedPath = @"C:\Docs\Signed_XAdES_EPES.docx";
document.Save(signedPath);
Console.WriteLine($"Document signed and saved to: {signedPath}");
```

Efter sparandet, öppna `Signed_XAdES_EPES.docx` i Microsoft Word. Du bör se en signaturlinje (om du lade till en) och en **digitalt signerad Word**‑statusrad som indikerar att filen är signerad och signaturen är giltig.

## Fullt, körbart exempel

Nedan är hela programmet som du kan kopiera och klistra in i en konsolapplikation.

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

### Förväntad utdata

```
Signed document saved to: C:\Docs\Signed_XAdES_EPES.docx
```

När du öppnar filen i Word visas en grön “Signed”-banner och, om du lade till den visuella linjen, visas signaturlinjen på den plats du angav.

## Hantera vanliga fallgropar

| Problem | Varför det händer | Lösning |
|---------|-------------------|---------|
| **Certifikatlösenordet är fel** | `X509Certificate2`‑konstruktorn kastar ett `CryptographicException`. | Verifiera lösenordet, eller använd en säker hemlighets‑hanterare (Azure Key Vault, AWS Secrets Manager). |
| **Word visar “Signature is invalid”** | Dokumentet har ändrats efter signering, eller signeringspolicyn saknas. | Säkerställ att filen sparas **efter** signering och inte redigeras igen. Bädda in rätt XAdES‑policy om din regulator kräver det. |
| **Signaturlinjen syns inte** | Dokumentet använder en annan sektionslayout. | Lägg till `SignatureLine` i rätt stycke eller skapa ett nytt stycke innan du lägger till den. |
| **Prestandaförsämring på stora dokument** | XAdES‑signaturer hash‑ar varje del av paketet. | Använd streaming‑API:er (`SignAsync`) eller öka maskinresurserna för mycket stora filer (>50 MB). |

## Utöka lösningen

- **Flera undertecknare** – anropa `Sign` upprepade gånger med olika certifikat och sätt `SignatureId` för att särskilja varje undertecknare.
- **Tidsstämpling** – lägg till ett `TimestampOptions`‑objekt i `XadesSignatureOptions` för att bädda in en betrodd tidsstämpel.
- **Anpassade policys** – ange en XML‑policyfil via `XadesSignatureOptions.PolicyFilePath` för efterlevnad av specifika standarder.

## Slutsats

Du vet nu **hur man signerar Word**‑dokument programatiskt, hur man **laddar pfx‑certifikat**, och hur man **skapar xades‑signatur** med GroupDocs.Signature. Tutorialen gick igenom varje steg från att ladda dokumentet till att spara den signerade utdata, med praktiska tips för vanliga edge‑cases.  

Nästa steg är att utforska relaterade ämnen såsom **digitalt signera Word**‑PDF:er, integrera **digital signature docx**‑verifiering, eller lägga till **timestamp**‑stöd för att möta avancerade efterlevnadskrav. Lycka till med signeringen!


## Vad bör du lära dig härnäst?


Följande tutorialer täcker nära besläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Detect Digital Signature on Word Document](/words/english/net/programming-with-fileformat/detect-document-signatures/)
- [Signing Existing Signature Line In Word Document](/words/english/net/programming-with-digital-signatures/signing-existing-signature-line/)
- [Access And Verify Signature In Word Document](/words/english/net/programming-with-digital-signatures/access-and-verify-signature/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}