---
"description": "Lär dig hur du lägger till och konfigurerar aktivitetsrutor för webbtillägg i Word-dokument med Aspose.Words för .NET i den här detaljerade steg-för-steg-handledningen."
"linktitle": "Använda aktivitetsfönster för webbtillägg"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Använda aktivitetsfönster för webbtillägg"
"url": "/sv/net/programming-with-webextension/using-web-extension-task-panes/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Använda aktivitetsfönster för webbtillägg

## Introduktion

Välkommen till den här djupgående handledningen om hur du använder aktivitetsfönster för webbtillägg i ett Word-dokument med Aspose.Words för .NET. Om du någonsin velat förbättra dina Word-dokument med interaktiva aktivitetsfönster har du kommit rätt. Den här guiden guidar dig genom varje steg för att uppnå detta smidigt.

## Förkunskapskrav

Innan vi börjar, låt oss se till att du har allt du behöver:

- Aspose.Words för .NET: Du kan ladda ner det [här](https://releases.aspose.com/words/net/).
- .NET-utvecklingsmiljö: Visual Studio eller annan IDE du föredrar.
- Grundläggande kunskaper i C#: Detta hjälper dig att följa kodexemplen.
- Licens för Aspose. Ord: Du kan köpa en [här](https://purchase.aspose.com/buy) eller skaffa ett tillfälligt körkort [här](https://purchase.aspose.com/temporary-license/).

## Importera namnrymder

Innan vi börjar koda, se till att du har importerat följande namnrymder i ditt projekt:

```csharp
using Aspose.Words;
using Aspose.Words.WebExtensions;
```

## Steg-för-steg-guide

Nu ska vi dela upp processen i enkla steg.

### Steg 1: Konfigurera din dokumentkatalog

Först och främst måste vi ange sökvägen till din dokumentkatalog. Det är här ditt Word-dokument kommer att sparas.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Ersätta `"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen till din dokumentmapp.

### Steg 2: Skapa ett nytt dokument

Nästa steg är att skapa ett nytt Word-dokument med hjälp av Aspose.Words.

```csharp
Document doc = new Document();
```

Den här raden initierar en ny instans av `Document` klassen, som representerar ett Word-dokument.

### Steg 3: Lägga till en aktivitetsruta

Nu ska vi lägga till en aktivitetsruta i vårt dokument. Aktivitetsrutor är användbara för att ge ytterligare funktioner och verktyg i ett Word-dokument.

```csharp
TaskPane taskPane = new TaskPane();
doc.WebExtensionTaskPanes.Add(taskPane);
```

Här skapar vi ett nytt `TaskPane` objektet och lägg till det i dokumentets `WebExtensionTaskPanes` samling.

### Steg 4: Konfigurera aktivitetsfönstret

För att göra vår aktivitetsruta synlig och ange dess egenskaper använder vi följande kod:

```csharp
taskPane.DockState = TaskPaneDockState.Right;
taskPane.IsVisible = true;
taskPane.Width = 300;
```

- `DockState` anger var aktivitetsfönstret ska visas. I det här fallet är det till höger.
- `IsVisible` säkerställer att aktivitetsfönstret är synligt.
- `Width` anger bredden på aktivitetsfönstret.

### Steg 5: Konfigurera webbtilläggsreferens

Därefter konfigurerar vi webbtilläggsreferensen som inkluderar ID, version, butikstyp och butik.

```csharp
taskPane.WebExtension.Reference.Id = "wa102923726";
taskPane.WebExtension.Reference.Version = "1.0.0.0";
taskPane.WebExtension.Reference.StoreType = WebExtensionStoreType.OMEX;
taskPane.WebExtension.Reference.Store = "th-TH";
```

- `Id` är en unik identifierare för webbtillägget.
- `Version` anger versionen av tillägget.
- `StoreType` anger typen av butik (i det här fallet OMEX).
- `Store` anger butikens språk-/kulturkod.

### Steg 6: Lägga till egenskaper i webbtillägget

Du kan lägga till egenskaper i ditt webbtillägg för att definiera dess beteende eller innehåll.

```csharp
taskPane.WebExtension.Properties.Add(new WebExtensionProperty("mailchimpCampaign", "mailchimpCampaign"));
```

Här lägger vi till en egenskap med namnet `mailchimpCampaign`.

### Steg 7: Bindning av webbtillägget

Slutligen lägger vi till bindningar till vårt webbtillägg. Bindningar låter dig länka tillägget till specifika delar av dokumentet.

```csharp
taskPane.WebExtension.Bindings.Add(new WebExtensionBinding("UnnamedBinding_0_1506535429545", WebExtensionBindingType.Text, "194740422"));
```

- `UnnamedBinding_0_1506535429545` är namnet på bindningen.
- `WebExtensionBindingType.Text` indikerar att bindningen är av texttyp.
- `194740422` är ID:t för den del av dokumentet som tillägget är kopplat till.

### Steg 8: Spara dokumentet

När du har konfigurerat allt, spara dokumentet.

```csharp
doc.Save(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");
```

Den här raden sparar dokumentet till den angivna katalogen med det angivna filnamnet.

### Steg 9: Läsa in och visa information i aktivitetsfönstret

För att verifiera och visa informationen i åtgärdsfönstret laddar vi dokumentet och itererar genom åtgärdsrutorna.

```csharp
doc = new Document(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");

Console.WriteLine("Task panes sources:\n");

foreach (TaskPane taskPaneInfo in doc.WebExtensionTaskPanes)
{
    WebExtensionReference reference = taskPaneInfo.WebExtension.Reference;
    Console.WriteLine($"Provider: \"{reference.Store}\", version: \"{reference.Version}\", catalog identifier: \"{reference.Id}\";");
}
```

Den här koden laddar dokumentet och skriver ut leverantör, version och katalog-ID för varje åtgärdsfönster i konsolen.

## Slutsats

Och det var allt! Du har lagt till och konfigurerat en aktivitetsruta för webbtillägg i ett Word-dokument med Aspose.Words för .NET. Den här kraftfulla funktionen kan avsevärt förbättra dina Word-dokument genom att tillhandahålla ytterligare funktioner direkt i dokumentet. 

## Vanliga frågor

### Vad är en aktivitetsruta i Word?
En aktivitetsfönster är ett gränssnittselement som tillhandahåller ytterligare verktyg och funktioner i ett Word-dokument, vilket förbättrar användarinteraktion och produktivitet.

### Kan jag anpassa utseendet på aktivitetsfönstret?
Ja, du kan anpassa aktivitetsfönstrets utseende genom att ställa in egenskaper som `DockState`, `IsVisible`och `Width`.

### Vad är egenskaper för webbtillägg?
Egenskaper för webbtillägg är anpassade egenskaper som du kan lägga till i ett webbtillägg för att definiera dess beteende eller innehåll.

### Hur binder jag ett webbtillägg till en del av dokumentet?
Du kan binda ett webbtillägg till en del av dokumentet med hjälp av `WebExtensionBinding` klass, som anger bindningstyp och mål-ID.

### Var kan jag hitta mer information om Aspose.Words för .NET?
Du kan hitta detaljerad dokumentation [här](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}