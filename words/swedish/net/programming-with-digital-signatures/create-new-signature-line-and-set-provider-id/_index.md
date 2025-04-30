---
"description": "Lär dig hur du skapar en ny signaturrad och anger leverantörs-ID i Word-dokument med Aspose.Words för .NET. Steg-för-steg-guide."
"linktitle": "Skapa ny signaturrad och ange leverantörs-ID"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Skapa ny signaturrad och ange leverantörs-ID"
"url": "/sv/net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Skapa ny signaturrad och ange leverantörs-ID

## Introduktion

Hej teknikentusiaster! Har du någonsin undrat hur man lägger till en signaturrad i dina Word-dokument programmatiskt? Idag ska vi titta närmare på just det med Aspose.Words för .NET. Den här guiden guidar dig genom varje steg, vilket gör det hur enkelt som helst att skapa en ny signaturrad och ange leverantörs-ID i dina Word-dokument. Oavsett om du automatiserar dokumenthantering eller bara vill effektivisera ditt arbetsflöde, har den här handledningen det du söker.

## Förkunskapskrav

Innan vi smutsar ner händerna, låt oss se till att vi har allt vi behöver:

1. Aspose.Words för .NET: Ladda ner det om du inte redan har gjort det. [här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Visual Studio eller annan C#-utvecklingsmiljö.
3. .NET Framework: Se till att du har .NET Framework installerat.
4. PFX-certifikat: För att signera dokument behöver du ett PFX-certifikat. Du kan få ett från en betrodd certifikatutfärdare.

## Importera namnrymder

Först och främst, låt oss importera de nödvändiga namnrymderna i ditt C#-projekt:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Okej, låt oss gå till det grundläggande. Här är en detaljerad genomgång av varje steg för att skapa en ny signaturrad och ange leverantörs-ID:t.

## Steg 1: Skapa ett nytt dokument

För att börja behöver vi skapa ett nytt Word-dokument. Detta kommer att fungera som arbetsyta för vår signaturrad.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

I det här utdraget initierar vi ett nytt `Document` och en `DocumentBuilder`Den `DocumentBuilder` hjälper oss att lägga till element i vårt dokument.

## Steg 2: Definiera alternativ för signaturrad

Nästa steg är att definiera alternativen för vår signaturrad. Detta inkluderar undertecknarens namn, titel, e-postadress och andra detaljer.

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

Dessa alternativ gör signaturraden mer personlig och professionell.

## Steg 3: Infoga signaturraden

Med våra alternativ inställda kan vi nu infoga signaturraden i dokumentet.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

Här, den `InsertSignatureLine` Metoden lägger till signaturraden, och vi tilldelar den ett unikt leverantörs-ID.

## Steg 4: Spara dokumentet

Efter att du har infogat signaturraden, låt oss spara dokumentet.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

Detta sparar ditt dokument med den nyligen tillagda signaturraden.

## Steg 5: Konfigurera signeringsalternativ

Nu behöver vi konfigurera alternativen för att signera dokumentet. Detta inkluderar signaturrads-ID, leverantörs-ID, kommentarer och signeringstid.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

Dessa alternativ säkerställer att dokumentet är signerat med korrekta uppgifter.

## Steg 6: Skapa certifikatinnehavare

För att signera dokumentet använder vi ett PFX-certifikat. Nu skapar vi en certifikatinnehavare för det.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

Se till att byta ut `"morzal.pfx"` med din faktiska certifikatfil och `"aw"` med ditt certifikatlösenord.

## Steg 7: Signera dokumentet

Slutligen signerar vi dokumentet med hjälp av verktyget för digital signatur.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

Detta signerar dokumentet och sparar det som en ny fil.

## Slutsats

Och där har du det! Du har skapat en ny signaturrad och angett leverantörs-ID i ett Word-dokument med Aspose.Words för .NET. Detta kraftfulla bibliotek gör det otroligt enkelt att hantera och automatisera dokumentbehandlingsuppgifter. Testa det och se hur det kan effektivisera ditt arbetsflöde.

## Vanliga frågor

### Kan jag anpassa utseendet på signaturraden?
Absolut! Du kan justera olika alternativ i `SignatureLineOptions` för att passa dina behov.

### Vad händer om jag inte har ett PFX-certifikat?
Du behöver skaffa ett från en betrodd certifikatutfärdare. Det är viktigt för att kunna signera dokument digitalt.

### Kan jag lägga till flera signaturrader i ett dokument?
Ja, du kan lägga till så många signaturrader som behövs genom att upprepa infogningsprocessen med olika alternativ.

### Är Aspose.Words för .NET kompatibelt med .NET Core?
Ja, Aspose.Words för .NET stöder .NET Core, vilket gör det mångsidigt för olika utvecklingsmiljöer.

### Hur säkra är de digitala signaturerna?
Digitala signaturer skapade med Aspose.Words är mycket säkra, förutsatt att du använder ett giltigt och pålitligt certifikat.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}