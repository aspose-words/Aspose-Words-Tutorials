---
"description": "Lär dig hur du skapar och digitalt signerar en signaturrad i ett Word-dokument med Aspose.Words för .NET med den här steg-för-steg-handledningen. Perfekt för dokumentautomation."
"linktitle": "Skapa och signera en ny signaturrad"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Skapa och signera en ny signaturrad"
"url": "/sv/net/programming-with-digital-signatures/creating-and-signing-new-signature-line/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Skapa och signera en ny signaturrad

## Introduktion

Hej där! Så, du har ett Word-dokument och du behöver lägga till en signaturrad och sedan signera det digitalt. Låter det knepigt? Inte alls! Tack vare Aspose.Words för .NET kan du göra detta smidigt med bara några rader kod. I den här handledningen guidar vi dig genom hela processen från att konfigurera din miljö till att spara ditt dokument med en skinande ny signatur. Är du redo? Nu kör vi!

## Förkunskapskrav

Innan vi går in i koden, låt oss se till att du har allt du behöver:
1. Aspose.Words för .NET - Du kan [ladda ner den här](https://releases.aspose.com/words/net/).
2. En .NET-utvecklingsmiljö – Visual Studio – rekommenderas starkt.
3. Ett dokument att signera – Skapa ett enkelt Word-dokument eller använd ett befintligt.
4. En certifikatfil – Denna behövs för digitala signaturer. Du kan använda en `.pfx` fil.
5. Bilder för signaturrad – valfritt en bildfil för signaturen.

## Importera namnrymder

Först måste vi importera de nödvändiga namnrymderna. Detta steg är avgörande eftersom det konfigurerar miljön för att använda Aspose.Words-funktioner.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## Steg 1: Konfigurera dokumentkatalogen

Varje projekt behöver en bra start. Nu konfigurerar vi sökvägen till din dokumentkatalog. Det är här dina dokument sparas och hämtas.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Steg 2: Skapa ett nytt dokument

Nu ska vi skapa ett nytt Word-dokument med Aspose.Words. Detta blir vår arbetsyta där vi lägger till signaturraden.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 3: Infoga signaturraden

Det är här magin händer. Vi infogar en signaturrad i vårt dokument med hjälp av `DocumentBuilder` klass.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Steg 4: Spara dokumentet med signaturraden

När signaturraden är på plats måste vi spara dokumentet. Detta är ett mellansteg innan vi fortsätter att signera det.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Steg 5: Konfigurera signeringsalternativ

Nu ska vi konfigurera alternativen för att signera dokumentet. Detta inkluderar att ange signaturrads-ID och vilken bild som ska användas.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf")
};
```

## Steg 6: Ladda certifikatet

Digitala signaturer kräver ett certifikat. Här laddar vi certifikatfilen som ska användas för att signera dokumentet.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## Steg 7: Signera dokumentet

Detta är det sista steget. Vi använder `DigitalSignatureUtil` klass för att signera dokumentet. Det signerade dokumentet sparas med ett nytt namn.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.NewSignatureLine.docx", certHolder, signOptions);
```

## Slutsats

Och där har du det! Med dessa steg har du skapat ett nytt Word-dokument, lagt till en signaturrad och signerat det digitalt med Aspose.Words för .NET. Det är ett kraftfullt verktyg som gör dokumentautomation till en barnlek. Oavsett om du har att göra med kontrakt, avtal eller andra formella dokument, säkerställer den här metoden att de är säkert signerade och autentiserade.

## Vanliga frågor

### Kan jag använda andra bildformat för signaturraden?
Ja, du kan använda olika bildformat som PNG, JPG, BMP, etc.

### Är det nödvändigt att använda en `.pfx` ansöka om certifikat?
Ja, en `.pfx` fil är ett vanligt format för att lagra kryptografisk information, inklusive certifikat och privata nycklar.

### Kan jag lägga till flera signaturrader i ett enda dokument?
Absolut! Du kan infoga flera signaturrader genom att upprepa infogningssteget för varje signatur.

### Vad händer om jag inte har ett digitalt certifikat?
Du måste skaffa ett digitalt certifikat från en betrodd certifikatutfärdare eller generera ett med verktyg som OpenSSL.

### Hur verifierar jag den digitala signaturen i dokumentet?
Du kan öppna det signerade dokumentet i Word och gå till signaturinformationen för att verifiera signaturens äkthet och integritet.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}