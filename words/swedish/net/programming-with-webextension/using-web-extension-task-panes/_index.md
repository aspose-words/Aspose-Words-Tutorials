---
title: Använda aktivitetsrutor för webbtillägg
linktitle: Använda aktivitetsrutor för webbtillägg
second_title: Aspose.Words Document Processing API
description: Lär dig hur du lägger till och konfigurerar webbtilläggsuppgiftsrutor i Word-dokument med Aspose.Words för .NET i denna detaljerade, steg-för-steg handledning.
weight: 10
url: /sv/net/programming-with-webextension/using-web-extension-task-panes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Använda aktivitetsrutor för webbtillägg

## Introduktion

Välkommen till denna djupgående handledning om hur du använder webbtilläggsuppgiftsrutor i ett Word-dokument med Aspose.Words för .NET. Om du någonsin har velat förbättra dina Word-dokument med interaktiva uppgiftsrutor, är du på rätt plats. Den här guiden leder dig genom varje steg för att uppnå detta sömlöst.

## Förutsättningar

Innan vi dyker in, låt oss se till att du har allt du behöver:

-  Aspose.Words för .NET: Du kan ladda ner det[här](https://releases.aspose.com/words/net/).
- .NET-utvecklingsmiljö: Visual Studio eller någon annan IDE du föredrar.
- Grundläggande kunskaper om C#: Detta hjälper dig att följa med i kodexemplen.
-  Licens för Aspose.Words: Du kan köpa en[här](https://purchase.aspose.com/buy) eller få en tillfällig licens[här](https://purchase.aspose.com/temporary-license/).

## Importera namnområden

Innan vi börjar koda, se till att du har följande namnrymder importerade i ditt projekt:

```csharp
using Aspose.Words;
using Aspose.Words.WebExtensions;
```

## Steg-för-steg-guide

Låt oss nu dela upp processen i lätta att följa steg.

### Steg 1: Konfigurera din dokumentkatalog

Först och främst måste vi ställa in sökvägen till din dokumentkatalog. Det är här ditt Word-dokument kommer att sparas.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersätta`"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen till din dokumentmapp.

### Steg 2: Skapa ett nytt dokument

Därefter kommer vi att skapa ett nytt Word-dokument med Aspose.Words.

```csharp
Document doc = new Document();
```

 Denna rad initierar en ny instans av`Document` klass, som representerar ett Word-dokument.

### Steg 3: Lägga till en uppgiftsruta

Nu kommer vi att lägga till en uppgiftsruta i vårt dokument. Uppgiftsrutor är användbara för att tillhandahålla ytterligare funktioner och verktyg i ett Word-dokument.

```csharp
TaskPane taskPane = new TaskPane();
doc.WebExtensionTaskPanes.Add(taskPane);
```

 Här skapar vi en ny`TaskPane` objekt och lägg till det i dokumentets`WebExtensionTaskPanes` samling.

### Steg 4: Konfigurera aktivitetsfönstret

För att göra vår uppgiftsruta synlig och ställa in dess egenskaper använder vi följande kod:

```csharp
taskPane.DockState = TaskPaneDockState.Right;
taskPane.IsVisible = true;
taskPane.Width = 300;
```

- `DockState` anger var aktivitetsfönstret ska visas. I det här fallet är det till höger.
- `IsVisible` ser till att aktivitetsfönstret är synligt.
- `Width` anger bredden på aktivitetsfönstret.

### Steg 5: Konfigurera webbtilläggsreferens

Därefter ställer vi in webbtilläggsreferensen som inkluderar ID, version, butikstyp och butik.

```csharp
taskPane.WebExtension.Reference.Id = "wa102923726";
taskPane.WebExtension.Reference.Version = "1.0.0.0";
taskPane.WebExtension.Reference.StoreType = WebExtensionStoreType.OMEX;
taskPane.WebExtension.Reference.Store = "th-TH";
```

- `Id`är en unik identifierare för webbtillägget.
- `Version` anger versionen av tillägget.
- `StoreType` anger typen av butik (i detta fall OMEX).
- `Store` anger butikens språk-/kulturkod.

### Steg 6: Lägga till egenskaper till webbtillägget

Du kan lägga till egenskaper i ditt webbtillägg för att definiera dess beteende eller innehåll.

```csharp
taskPane.WebExtension.Properties.Add(new WebExtensionProperty("mailchimpCampaign", "mailchimpCampaign"));
```

 Här lägger vi till en egendom som heter`mailchimpCampaign`.

### Steg 7: Bindning av webbtillägget

Slutligen lägger vi till bindningar till vårt webbtillägg. Bindningar låter dig länka tillägget till specifika delar av dokumentet.

```csharp
taskPane.WebExtension.Bindings.Add(new WebExtensionBinding("UnnamedBinding_0_1506535429545", WebExtensionBindingType.Text, "194740422"));
```

- `UnnamedBinding_0_1506535429545` är namnet på bindningen.
- `WebExtensionBindingType.Text` indikerar att bindningen är av texttyp.
- `194740422` är ID för den del av dokumentet som tillägget är bundet till.

### Steg 8: Spara dokumentet

När du har ställt in allt, spara ditt dokument.

```csharp
doc.Save(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");
```

Denna rad sparar dokumentet i den angivna katalogen med det angivna filnamnet.

### Steg 9: Ladda och visa information om uppgiftsfönstret

För att verifiera och visa informationen i aktivitetsfönstret laddar vi dokumentet och itererar genom aktivitetsrutorna.

```csharp
doc = new Document(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");

Console.WriteLine("Task panes sources:\n");

foreach (TaskPane taskPaneInfo in doc.WebExtensionTaskPanes)
{
    WebExtensionReference reference = taskPaneInfo.WebExtension.Reference;
    Console.WriteLine($"Provider: \"{reference.Store}\", version: \"{reference.Version}\", catalog identifier: \"{reference.Id}\";");
}
```

Den här koden laddar dokumentet och skriver ut leverantören, versionen och katalogidentifieraren för varje aktivitetsfönster i konsolen.

## Slutsats

Och det är det! Du har framgångsrikt lagt till och konfigurerat en aktivitetsruta för webbtillägg i ett Word-dokument med Aspose.Words för .NET. Denna kraftfulla funktion kan avsevärt förbättra dina Word-dokument genom att tillhandahålla ytterligare funktioner direkt i dokumentet. 

## FAQ's

### Vad är en uppgiftsruta i Word?
En uppgiftspanel är ett gränssnittselement som tillhandahåller ytterligare verktyg och funktioner i ett Word-dokument, vilket förbättrar användarinteraktion och produktivitet.

### Kan jag anpassa aktivitetsfönstrets utseende?
 Ja, du kan anpassa aktivitetsfönstrets utseende genom att ställa in egenskaper som`DockState`, `IsVisible` , och`Width`.

### Vad är webbtilläggsegenskaper?
Webbtilläggsegenskaper är anpassade egenskaper som du kan lägga till i ett webbtillägg för att definiera dess beteende eller innehåll.

### Hur binder jag ett webbtillägg till en del av dokumentet?
 Du kan binda ett webbtillägg till en del av dokumentet med hjälp av`WebExtensionBinding` klass, med angivande av bindningstyp och mål-ID.

### Var kan jag hitta mer information om Aspose.Words för .NET?
 Du kan hitta detaljerad dokumentation[här](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
