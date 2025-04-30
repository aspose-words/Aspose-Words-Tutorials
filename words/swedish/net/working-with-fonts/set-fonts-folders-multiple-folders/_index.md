---
"description": "Lär dig hur du ställer in flera teckensnittsmappar i dina Word-dokument med Aspose.Words för .NET. Den här steg-för-steg-guiden säkerställer att dina dokument använder exakt de teckensnitt du behöver."
"linktitle": "Ställ in teckensnitt Mappar Flera mappar"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Ställ in teckensnitt Mappar Flera mappar"
"url": "/sv/net/working-with-fonts/set-fonts-folders-multiple-folders/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ställ in teckensnitt Mappar Flera mappar

## Introduktion

Har du någonsin undrat hur du hanterar flera teckensnittskällor i dina Word-dokument? Kanske har du en samling teckensnitt utspridda över olika mappar och behöver ett sätt att säkerställa att dina dokument använder dem sömlöst. Då har du tur! Idag dyker vi ner i hur man ställer in teckensnittsmappar med Aspose.Words för .NET. Den här guiden tar dig steg för steg genom processen och säkerställer att dina dokument ser ut precis som du vill.

## Förkunskapskrav

Innan vi börjar, låt oss se till att du har allt du behöver. Här är vad du behöver följa:

- Aspose.Words för .NET: Om du inte redan har gjort det, ladda ner och installera Aspose.Words för .NET. Du kan få det [här](https://releases.aspose.com/words/net/).
- Utvecklingsmiljö: Visual Studio eller annan .NET-kompatibel utvecklingsmiljö.
- Grundläggande kunskaper i C#: Lite förtrogenhet med C# hjälper dig att följa exemplen.
- Typsnittsfiler: Se till att du har dina typsnittsfiler lagrade i kataloger som du enkelt kan komma åt.

## Importera namnrymder

Först och främst, låt oss importera de nödvändiga namnrymderna i ditt C#-projekt. Detta säkerställer att du har tillgång till alla Aspose.Words-funktioner du behöver.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Med det inställt, låt oss dyka ner i steg-för-steg-guiden för att ställa in teckensnittsmappar i Aspose.Words för .NET.

## Steg 1: Ladda ditt dokument

Okej, låt oss börja med att ladda Word-dokumentet du vill arbeta med. Se till att du har dokumentsökvägen redo. I det här exemplet använder vi ett dokument med namnet "Rendering.docx".

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

Här laddar vi dokumentet från den angivna katalogen. Enkelt nog, eller hur?

## Steg 2: Skapa FontSettings-objekt

Nästa steg är att skapa en `FontSettings` objekt. Det här objektet låter oss hantera teckensnittskällor för vårt dokument.

```csharp
FontSettings fontSettings = new FontSettings();
```

Detta `FontSettings` objektet hjälper oss att definiera vilka teckensnittsmappar som ska användas.

## Steg 3: Ställ in teckensnittsmappar

Nu kommer den avgörande delen – att ställa in mapparna för typsnitt. Det är här du anger katalogerna där dina typsnitt finns. I det här exemplet har vi typsnitt i "C:\MyFonts" och "D:\Misc\Fonts".

```csharp
fontSettings.SetFontsFolders(new[] { @"C:\MyFonts\", @"D:\Misc\Fonts\" }, true);
```

Den andra parametern (`true`) indikerar att dessa mappar åsidosätter alla standardfontkällor. Om du också vill behålla systemets fontkällor kan du använda en kombination av `GetFontSources` och `SetFontSources`.

## Steg 4: Tillämpa teckensnittsinställningar på dokumentet

När teckensnittsmapparna är inställda måste vi tillämpa dessa inställningar på vårt dokument. Detta säkerställer att dokumentet använder de angivna teckensnitten under renderingen.

```csharp
doc.FontSettings = fontSettings;
```

## Steg 5: Spara dokumentet

Slutligen, låt oss spara dokumentet. Vi sparar det som en PDF för att se typsnitten i aktion.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersMultipleFolders.pdf");
```

Och där har du det! Du har framgångsrikt ställt in flera teckensnittsmappar för ditt dokument.

## Slutsats

Att hantera teckensnitt i dina dokument kan verka som en skrämmande uppgift, men med Aspose.Words för .NET är det hur enkelt som helst! Genom att följa dessa enkla steg kan du se till att dina dokument ser professionella ut och använder exakt de teckensnitt du behöver. Oavsett om du arbetar med ett projekt som kräver specifik varumärkesbyggande eller bara vill ha mer kontroll över ditt dokuments utseende, är det värt att bemästra att ställa in teckensnittsmappar.

## Vanliga frågor

### Kan jag använda nätverkssökvägar för teckensnittsmappar?
Ja, du kan använda nätverkssökvägar för dina teckensnittsmappar. Se bara till att sökvägarna är tillgängliga från ditt program.

### Vad händer om ett teckensnitt saknas i de angivna mapparna?
Om ett teckensnitt saknas kommer Aspose.Words att återgå till det angivna standardteckensnittet eller använda ett ersättningsteckensnitt.

### Kan jag lägga till teckensnittsmappar utan att åsidosätta systemteckensnitt?
Absolut! Använd `FontSettings.GetFontSources` för att hämta befintliga källor och kombinera dem med dina anpassade mappar med hjälp av `FontSettings.SetFontSources`.

### Finns det en gräns för hur många teckensnittsmappar jag kan lägga till?
Det finns ingen strikt gräns för antalet teckensnittsmappar. Var dock uppmärksam på prestandan, eftersom fler mappar kan öka laddningstiden för teckensnitt.

### Hur kan jag kontrollera vilka teckensnitt som används i mitt dokument?
Du kan använda `FontSettings.GetFontsSources` metod för att hämta och granska de teckensnittskällor som för närvarande är inställda för ditt dokument.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}