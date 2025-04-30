---
"description": "Lär dig hur du exporterar teckensnitt som Base64 med Aspose.Words för .NET i den här detaljerade handledningen. Se till att teckensnitt är inbäddade och visas korrekt i HTML-filer."
"linktitle": "Exportera teckensnitt som bas 64"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Exportera teckensnitt som bas 64"
"url": "/sv/net/programming-with-htmlsaveoptions/export-fonts-as-base-64/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Exportera teckensnitt som bas 64

## Introduktion

När det gäller att manipulera Word-dokument programmatiskt är Aspose.Words för .NET ett kraftpaket. En av dess smarta funktioner är att exportera teckensnitt som Base64 i HTML-filer, vilket säkerställer att teckensnitt bäddas in och visas korrekt i olika webbläsare och system. I den här handledningen ska vi dyka in i hur du kan uppnå detta. Redo att göra dina Word-dokuments teckensnitt webbvänliga? Nu sätter vi igång!

## Förkunskapskrav

Innan vi börjar med kodningen, låt oss se till att du har allt du behöver:

- Aspose.Words för .NET-biblioteket: Du kan ladda ner det från [Aspose-utgåvor](https://releases.aspose.com/words/net/) sida.
- .NET-utvecklingsmiljö: Alla IDE:er som Visual Studio fungerar perfekt.
- Grundläggande kunskaper i C#: Du behöver inte vara ett proffs, men grundläggande förståelse är bra.

## Importera namnrymder

För att använda Aspose.Words för .NET måste du importera nödvändiga namnrymder i din C#-kod. Detta gör alla klasser och metoder tillgängliga för användning.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Steg 1: Konfigurera ditt projekt

Först och främst, låt oss konfigurera ditt projekt och installera Aspose.Words-biblioteket.

### 1.1 Skapa ett nytt projekt

Öppna Visual Studio och skapa ett nytt Console App-projekt. Ge det något betydelsefullt namn, till exempel "ExportFontsBase64".

### 1.2 Installera Aspose.Words

Du kan installera Aspose.Words för .NET via NuGet Package Manager:

1. Högerklicka på ditt projekt i lösningsutforskaren.
2. Välj "Hantera NuGet-paket".
3. Sök efter "Aspose.Words" och installera det.

Alternativt kan du köra följande kommando i pakethanterarkonsolen:

```sh
Install-Package Aspose.Words
```

## Steg 2: Ladda ditt Word-dokument

Nu när ditt projekt är konfigurerat, låt oss ladda Word-dokumentet som du vill exportera teckensnitt från.

### 2.1 Definiera dokumentkatalogen

Först, definiera katalogen där ditt Word-dokument finns:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Ersätta `"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen till din dokumentkatalog.

### 2.2 Ladda dokumentet

Ladda sedan in ditt dokument med hjälp av `Document` klass:

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Se till att "Rendering.docx" finns i den angivna katalogen.

## Steg 3: Konfigurera HTML-sparalternativ

För att exportera teckensnitt som Base64 måste vi konfigurera `HtmlSaveOptions`.


Skapa en instans av `HtmlSaveOptions` och ställ in `ExportFontsAsBase64` egendom till `true`:

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions { ExportFontsAsBase64 = true };
```

## Steg 4: Spara dokumentet som HTML

Slutligen, låt oss spara dokumentet med de konfigurerade alternativen.


Använd `Save` metod för `Document` klass för att spara ditt dokument:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
```

Den här raden sparar ditt dokument som en HTML-fil med teckensnitt exporterade som Base64, vilket säkerställer att de är inbäddade i HTML-koden.

## Slutsats

Grattis! Du har exporterat teckensnitt som Base64 från ett Word-dokument med Aspose.Words för .NET. Detta säkerställer att dina teckensnitt bevaras och visas korrekt på olika plattformar. Oavsett om du förbereder dokument för webbvisning eller helt enkelt säkerställer kompatibilitet är den här funktionen otroligt användbar.

## Vanliga frågor

### Vad är Base64-kodning?
Base64 är en metod för att koda binär data (som teckensnitt) till ett textformat. Detta säkerställer kompatibilitet med textbaserade format som HTML.

### Varför ska jag använda Base64 för teckensnitt i HTML?
Genom att använda Base64 säkerställs att teckensnitt bäddas in direkt i HTML-koden, vilket undviker problem med saknade teckensnittsfiler och säkerställer en konsekvent visning.

### Kan jag använda den här metoden för andra resurser, som bilder?
Absolut! Aspose.Words för .NET låter dig bädda in olika resurser, inklusive bilder, som Base64 i dina HTML-filer.

### Vad händer om mitt dokument har flera teckensnitt?
Inga problem! Aspose.Words för .NET kommer att bädda in alla teckensnitt som används i ditt dokument som Base64 i den resulterande HTML-filen.

### Är Aspose.Words för .NET gratis att använda?
Aspose.Words för .NET är ett kommersiellt bibliotek. Du kan dock ladda ner en gratis provversion från [Aspose-utgåvor](https://releases.aspose.com/) sida.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}