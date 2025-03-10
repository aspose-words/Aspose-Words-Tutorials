---
title: Tillåt endast formulärfält att skydda i Word-dokument
linktitle: Tillåt endast formulärfält att skydda i Word-dokument
second_title: Aspose.Words Document Processing API
description: Lär dig hur du skyddar Word-dokument, så att endast formulärfält kan redigeras med Aspose.Words för .NET. Följ vår guide för att säkerställa att dina dokument är säkra och lätta att redigera.
weight: 10
url: /sv/net/document-protection/allow-only-form-fields-protect/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tillåt endast formulärfält att skydda i Word-dokument

## Introduktion

Hej där! Någonsin behövt skydda specifika delar av ett Word-dokument samtidigt som andra delar kan redigeras? Aspose.Words för .NET gör detta superenkelt. I den här självstudien går vi in på hur man endast tillåter skydd av formulärfält i ett Word-dokument. I slutet av den här guiden har du en gedigen förståelse för dokumentskydd med Aspose.Words för .NET. Redo? Låt oss hoppa in!

## Förutsättningar

Innan vi dyker in i kodningsdelen, låt oss se till att du har allt du behöver:

1.  Aspose.Words för .NET Library: Du kan ladda ner det från[här](https://releases.aspose.com/words/net/).
2. Visual Studio: Alla nyare versioner fungerar bra.
3. Grundläggande kunskaper om C#: Att förstå grunderna hjälper dig att följa handledningen.

## Importera namnområden

Först och främst måste vi importera de nödvändiga namnrymden. Detta ställer in vår miljö för att använda Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Steg 1: Konfigurera ditt projekt

Skapa ett nytt projekt i Visual Studio  
Öppna Visual Studio och skapa ett nytt Console App-projekt (.NET Core). Döp det till något meningsfullt, som "AsposeWordsProtection".

## Steg 2: Installera Aspose.Words för .NET

Installera via NuGet Package Manager  
Högerklicka på ditt projekt i Solution Explorer, välj "Manage NuGet Packages" och sök efter`Aspose.Words`. Installera den.

## Steg 3: Initiera dokumentet

Skapa ett nytt dokumentobjekt  
Låt oss börja med att skapa ett nytt dokument och en dokumentbyggare för att lägga till lite text.

```csharp
// Sökväg till din dokumentkatalog
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Initiera ett nytt Document and DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.Writeln("Text added to a document.");
```

 Här skapar vi en ny`Document` och`DocumentBuilder` exempel. De`DocumentBuilder` låter oss lägga till text i vårt dokument.

## Steg 4: Skydda dokumentet

Använd skydd som endast tillåter redigering av formulärfält  
Låt oss nu lägga till skyddet i vårt dokument.

```csharp
// Skydda dokumentet, så att endast formulärfält kan redigeras
doc.Protect(ProtectionType.AllowOnlyFormFields, "password");
```

Denna kodrad skyddar dokumentet och tillåter endast att formulärfält redigeras. Lösenordet "lösenord" används för att upprätthålla skyddet.

## Steg 5: Spara dokumentet

Spara det skyddade dokumentet  
Slutligen, låt oss spara vårt dokument i den angivna katalogen.

```csharp
// Spara det skyddade dokumentet
doc.Save(dataDir + "DocumentProtection.AllowOnlyFormFieldsProtect.docx");
```

Detta sparar dokumentet med tillämpat skydd.

## Slutsats

Och där har du det! Du har precis lärt dig hur man skyddar ett Word-dokument så att endast formulärfält kan redigeras med Aspose.Words för .NET. Detta är en praktisk funktion när du behöver se till att vissa delar av ditt dokument förblir oförändrade samtidigt som specifika fält kan fyllas i.

## FAQ's

###	 Hur tar jag bort skyddet från ett dokument?  
 För att ta bort skyddet, använd`doc.Unprotect("password")` metod, där "lösenord" är lösenordet som används för att skydda dokumentet.

###	 Kan jag använda olika typer av skydd med Aspose.Words för .NET?  
 Ja, Aspose.Words stöder olika skyddstyper som t.ex`ReadOnly`, `NoProtection` , och`AllowOnlyRevisions`.

###	 Är det möjligt att använda ett annat lösenord för olika sektioner?  
Nej, skyddet på dokumentnivå i Aspose.Words gäller för hela dokumentet. Du kan inte tilldela olika lösenord till olika sektioner.

###	 Vad händer om fel lösenord används?  
Om ett felaktigt lösenord används förblir dokumentet skyddat och de angivna ändringarna kommer inte att tillämpas.

###	 Kan jag programmässigt kontrollera om ett dokument är skyddat?  
 Ja, du kan använda`doc.ProtectionType` egendom för att kontrollera skyddsstatusen för ett dokument.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
