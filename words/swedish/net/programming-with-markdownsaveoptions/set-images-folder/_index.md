---
"description": "Konvertera Word-dokument till Markdown med korrekt tabelljustering med Aspose.Words för .NET. Följ vår detaljerade guide för perfekta resultat."
"linktitle": "Ställ in bildmapp"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Ställ in bildmapp"
"url": "/sv/net/programming-with-markdownsaveoptions/set-images-folder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ställ in bildmapp

## Introduktion

Har du någonsin velat exportera ditt Word-dokument till Markdown-format samtidigt som du säkerställer att tabeller och innehåll justeras perfekt? Aspose.Words för .NET är din bästa lösning för den här uppgiften. I den här artikeln guidar vi dig genom processen att konfigurera Aspose.Words, förbereda ditt dokument och exportera det till Markdown med korrekt justering av tabellinnehållet. Vi bryter ner varje steg för att göra det enkelt att följa och förstå. Så, låt oss dyka in och omvandla dina Word-dokument till vackert justerade Markdown-filer!

## Förkunskapskrav

Innan vi börjar, se till att du har följande:

- Aspose.Words för .NET: Du kan ladda ner det [här](https://releases.aspose.com/words/net/).
- Giltig licens: Skaffa en gratis provperiod [här](https://releases.aspose.com/) eller en tillfällig licens [här](https://purchase.aspose.com/temporary-license/).
- Visual Studio: Eller någon annan IDE som stöder .NET-utveckling.
- Grundläggande kunskaper i C#: Förståelse för programmeringsspråket C#.

## Importera namnrymder

För att börja måste du importera de nödvändiga namnrymderna i ditt C#-projekt. Dessa namnrymder ger dig åtkomst till Aspose.Words-funktionaliteten.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;
```

## Steg 1: Konfigurera ditt projekt

Först och främst, konfigurera ditt .NET-projekt i din IDE. Skapa en ny konsolapplikation och lägg till en referens till Aspose.Words för .NET.

### 1.1 Skapa ett nytt projekt

Öppna Visual Studio och skapa ett nytt Console Application-projekt. Döp det till "MarkdownExporter" eller något liknande.

### 1.2 Lägg till Aspose.Words-referens

För att lägga till Aspose.Words i ditt projekt kan du antingen ladda ner DLL-filen från [Aspose webbplats](https://releases.aspose.com/words/net/) och lägg till den manuellt, eller använd NuGet Package Manager:

```bash
Install-Package Aspose.Words
```

## Steg 2: Skriv koden som ska exporteras som Markdown

Nu ska vi skriva koden för att läsa Word-dokumentet och spara det som en Markdown-fil med korrekt tabelljustering.

### 2.1 Definiera sökvägen till ditt dokument

Ange sökvägen till ditt Word-dokument och mappen där du vill spara bilderna.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
```

### 2.2 Ladda dokumentet

Ladda ditt Word-dokument med Aspose.Words.

```csharp
Document doc = new Document(dataDir + "Image bullet points.docx");
```

### 2.3 Konfigurera alternativ för att spara Markdown

Konfigurera `MarkdownSaveOptions` för att ange var bilderna ska lagras.

```csharp
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    ImagesFolder = dataDir + "Images"
};
```

### 2.4 Spara dokumentet som Markdown

Använd en `MemoryStream` för att spara dokumentet i Markdown-format.

```csharp
using (MemoryStream stream = new MemoryStream())
{
    doc.Save(stream, saveOptions);
}
```

## Slutsats

Att exportera ett Word-dokument till Markdown med tabellinnehållsjustering med Aspose.Words för .NET är enkelt när du följer dessa steg. Med några få rader kod kan du automatisera konverteringsprocessen och säkerställa att ditt innehåll är välformaterat. Nu kan du enkelt dela dina dokument i Markdown-format, i vetskap om att de kommer att se bra ut och behålla sin struktur.

## Vanliga frågor

### Kan jag använda Aspose.Words för .NET med andra programmeringsspråk?

Ja, Aspose.Words för .NET kan användas med alla .NET-kompatibla språk som VB.NET, F# och fler.

### Hur får jag en tillfällig licens för Aspose.Words?

Du kan få en tillfällig licens [här](https://purchase.aspose.com/temporary-license/).

### Vilka typer av dokument kan jag konvertera till Markdown?

Du kan konvertera olika Word-dokument, inklusive .doc, .docx, .rtf med flera.

### Finns det några begränsningar i testversionen av Aspose.Words?

Testversionen har vissa begränsningar, såsom vattenstämplar i utdatafilerna. Du kan få en gratis testversion. [här](https://releases.aspose.com/).

### Var kan jag hitta fler exempel och dokumentation för Aspose.Words?

Du hittar detaljerad dokumentation och exempel på [Aspose webbplats](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}