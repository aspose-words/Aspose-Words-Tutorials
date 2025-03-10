---
title: Skapa och signera ny signaturlinje
linktitle: Skapa och signera ny signaturlinje
second_title: Aspose.Words Document Processing API
description: Lär dig hur du skapar och digitalt signerar en signaturrad i ett Word-dokument med Aspose.Words för .NET med denna steg-för-steg-handledning. Perfekt för dokumentautomatisering.
weight: 10
url: /sv/net/programming-with-digital-signatures/creating-and-signing-new-signature-line/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa och signera ny signaturlinje

## Introduktion

Hej där! Så du har ett Word-dokument och du måste lägga till en signaturrad och sedan signera den digitalt. Låter det knepigt? Inte alls! Tack vare Aspose.Words för .NET kan du uppnå detta sömlöst med bara några rader kod. I den här självstudien går vi igenom hela processen från att ställa in din miljö till att spara ditt dokument med en skinande ny signatur. Redo? Låt oss dyka in!

## Förutsättningar

Innan vi hoppar in i koden, låt oss se till att du har allt du behöver:
1.  Aspose.Words för .NET - Du kan[ladda ner den här](https://releases.aspose.com/words/net/).
2. En .NET-utvecklingsmiljö - Visual Studio rekommenderas starkt.
3. Ett dokument att signera - Skapa ett enkelt Word-dokument eller använd ett befintligt.
4.  En certifikatfil - Detta behövs för digitala signaturer. Du kan använda en`.pfx` fil.
5. Bilder för signaturlinje - Valfritt, en bildfil för signaturen.

## Importera namnområden

Först måste vi importera de nödvändiga namnrymden. Detta steg är avgörande eftersom det ställer in miljön för användning av Aspose.Words-funktioner.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## Steg 1: Konfigurera dokumentkatalogen

Varje projekt behöver en bra start. Låt oss ställa in sökvägen till din dokumentkatalog. Det är här dina dokument kommer att sparas och hämtas.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Steg 2: Skapa ett nytt dokument

Låt oss nu skapa ett nytt Word-dokument med Aspose.Words. Detta kommer att vara vår duk där vi lägger till signaturlinjen.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 3: Infoga signaturlinjen

 Det är här magin händer. Vi infogar en signaturrad i vårt dokument med hjälp av`DocumentBuilder` klass.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Steg 4: Spara dokumentet med signaturraden

När signaturraden är på plats måste vi spara dokumentet. Detta är ett mellansteg innan vi fortsätter med att signera det.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Steg 5: Ställa in signeringsalternativ

Låt oss nu ställa in alternativen för att signera dokumentet. Detta inkluderar att specificera signaturrads-ID och bilden som ska användas.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf")
};
```

## Steg 6: Laddar certifikatet

Digitala signaturer kräver ett certifikat. Här laddar vi certifikatfilen som kommer att användas för att signera dokumentet.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## Steg 7: Signera dokumentet

 Detta är det sista steget. Vi använder`DigitalSignatureUtil`klass för att underteckna dokumentet. Det signerade dokumentet sparas med ett nytt namn.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.NewSignatureLine.docx", certHolder, signOptions);
```

## Slutsats

Och där har du det! Med dessa steg har du framgångsrikt skapat ett nytt Word-dokument, lagt till en signaturrad och signerat det digitalt med Aspose.Words för .NET. Det är ett kraftfullt verktyg som gör dokumentautomatisering till en lek. Oavsett om du har att göra med kontrakt, avtal eller några formella dokument, säkerställer den här metoden att de är säkert signerade och autentiserade.

## FAQ's

### Kan jag använda andra bildformat för signaturraden?
Ja, du kan använda olika bildformat som PNG, JPG, BMP, etc.

###  Är det nödvändigt att använda en`.pfx` file for the certificate?
 Ja, a`.pfx` fil är ett vanligt format för lagring av kryptografisk information inklusive certifikat och privata nycklar.

### Kan jag lägga till flera signaturrader i ett enda dokument?
Absolut! Du kan infoga flera signaturrader genom att upprepa infogningssteget för varje signatur.

### Vad händer om jag inte har ett digitalt certifikat?
Du måste skaffa ett digitalt certifikat från en betrodd certifikatutfärdare eller skapa ett med hjälp av verktyg som OpenSSL.

### Hur verifierar jag den digitala signaturen i dokumentet?
Du kan öppna det signerade dokumentet i Word och gå till signaturinformationen för att verifiera signaturens äkthet och integritet.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
