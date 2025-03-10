---
title: Skapa ny signaturlinje och ställ in leverantörs-ID
linktitle: Skapa ny signaturlinje och ställ in leverantörs-ID
second_title: Aspose.Words Document Processing API
description: Lär dig hur du skapar en ny signaturrad och ställer in leverantörs-ID i Word-dokument med Aspose.Words för .NET. Steg-för-steg guide.
weight: 10
url: /sv/net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa ny signaturlinje och ställ in leverantörs-ID

## Introduktion

Hej där, teknikentusiaster! Har du någonsin undrat hur man lägger till en signaturrad i dina Word-dokument programmatiskt? Nåväl, idag går vi in på just det med Aspose.Words för .NET. Den här guiden går igenom varje steg, vilket gör det så enkelt som en plätt att skapa en ny signaturrad och ange leverantörs-ID i dina Word-dokument. Oavsett om du automatiserar dokumentbearbetning eller bara vill effektivisera ditt arbetsflöde, har den här handledningen täckt dig.

## Förutsättningar

Innan vi smutsar ner händerna, låt oss se till att vi har allt vi behöver:

1.  Aspose.Words för .NET: Ladda ner det om du inte redan har gjort det[här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Visual Studio eller någon annan C#-utvecklingsmiljö.
3. .NET Framework: Se till att du har .NET Framework installerat.
4. PFX-certifikat: För att signera dokument behöver du ett PFX-certifikat. Du kan få en från en betrodd certifikatutfärdare.

## Importera namnområden

Först och främst, låt oss importera de nödvändiga namnrymden i ditt C#-projekt:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Okej, låt oss gå ner till det nitty-gritty. Här är en detaljerad uppdelning av varje steg för att skapa en ny signaturrad och ange leverantörs-ID.

## Steg 1: Skapa ett nytt dokument

För att börja måste vi skapa ett nytt Word-dokument. Detta kommer att vara duken för vår signaturlinje.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 I det här utdraget initierar vi en ny`Document` och a`DocumentBuilder` . De`DocumentBuilder` hjälper oss att lägga till element i vårt dokument.

## Steg 2: Definiera signaturlinjealternativ

Därefter definierar vi alternativen för vår signaturlinje. Detta inkluderar undertecknarens namn, titel, e-postadress och andra detaljer.

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

Dessa alternativ anpassar signaturlinjen, vilket gör den tydlig och professionell.

## Steg 3: Sätt in signaturraden

Med våra alternativ inställda kan vi nu infoga signaturraden i dokumentet.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

 Här, den`InsertSignatureLine` metod lägger till signaturraden och vi tilldelar den ett unikt leverantörs-ID.

## Steg 4: Spara dokumentet

När vi har infogat signaturraden, låt oss spara dokumentet.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

Detta sparar ditt dokument med den nyligen tillagda signaturraden.

## Steg 5: Ställ in signeringsalternativ

Nu måste vi ställa in alternativen för att signera dokumentet. Detta inkluderar signaturrads-ID, leverantörs-ID, kommentarer och signeringstiden.

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

För att signera dokumentet använder vi ett PFX-certifikat. Låt oss skapa en certifikatinnehavare för det.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

 Se till att byta ut`"morzal.pfx"` med din faktiska certifikatfil och`"aw"` med ditt certifikatlösenord.

## Steg 7: Signera dokumentet

Slutligen signerar vi dokumentet med hjälp av det digitala signaturverktyget.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

Detta signerar dokumentet och sparar det som en ny fil.

## Slutsats

Och där har du det! Du har framgångsrikt skapat en ny signaturrad och angett leverantörs-ID i ett Word-dokument med Aspose.Words för .NET. Detta kraftfulla bibliotek gör det otroligt enkelt att hantera och automatisera dokumentbearbetningsuppgifter. Prova det och se hur det kan effektivisera ditt arbetsflöde.

## FAQ's

### Kan jag anpassa utseendet på signaturlinjen?
 Absolut! Du kan justera olika alternativ i`SignatureLineOptions`för att passa dina behov.

### Vad händer om jag inte har ett PFX-certifikat?
Du måste skaffa en från en betrodd certifikatutfärdare. Det är viktigt för digital signering av dokument.

### Kan jag lägga till flera signaturrader i ett dokument?
Ja, du kan lägga till så många signaturrader som behövs genom att upprepa infogningsprocessen med olika alternativ.

### Är Aspose.Words for .NET kompatibelt med .NET Core?
Ja, Aspose.Words för .NET stöder .NET Core, vilket gör den mångsidig för olika utvecklingsmiljöer.

### Hur säkra är de digitala signaturerna?
Digitala signaturer skapade med Aspose.Words är mycket säkra, förutsatt att du använder ett giltigt och pålitligt certifikat.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
