---
category: general
date: 2026-10-26
description: Lär dig hur du skapar ett Word‑dokument i C# och lägger till en ActiveX‑knapp
  programatiskt. Denna steg‑för‑steg‑guide täcker hur du infogar en kommandoknapp,
  döljer den vid designtid och sparar filen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to add activex button
- create command button word
- programmatically add command button
language: sv
lastmod: 2026-10-26
og_description: Skapa ett Word‑dokument i C# och programatiskt lägga till en ActiveX‑knapp.
  Följ den här kompletta handledningen för att bädda in en kommandoknapp som bara
  visas vid körning.
og_image_alt: Screenshot of a Word document created with C# that contains an ActiveX
  command button
og_title: Skapa ett Word‑dokument i C# med en ActiveX‑kommandoknapp – fullständig
  guide
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document C# and add an ActiveX button programmatically.
    This step‑by‑step guide covers inserting a command button, hiding it at design
    time, and saving the file.
  headline: How to create Word document C# with an ActiveX command button
  type: TechArticle
tags:
- C#
- Aspose.Words
- ActiveX
- Word automation
title: Hur man skapar ett Word‑dokument i C# med en ActiveX‑kommandoknapp
url: /sv/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så skapar du ett Word-dokument i C# med en ActiveX-kommandoknapp

Om du behöver **skapa Word-dokument C#** som innehåller en interaktiv knapp, visar den här guiden exakt hur du gör. Efter de två första meningarna vet du den övergripande metoden, och de följande stegen går igenom varje kodrad du måste skriva.

Du kommer att lära dig hur du lägger till en ActiveX‑knapp, döljer den under design och gör den synlig endast när användaren öppnar filen. Handledningen täcker också vanliga fallgropar som säkerhetsvarningar och versionskompatibilitet, så att du kan leverera pålitliga dokument.

## Förutsättningar

* .NET 6.0 eller senare installerat  
* En licensierad kopia av **Aspose.Words for .NET** (gratis provversion fungerar för experiment)  
* Grundläggande kunskap om C# och Visual Studio (vilken IDE som helst som stödjer .NET räcker)

Inga ytterligare NuGet‑paket krävs utöver `Aspose.Words`.

## Steg 1: Skapa ett Word-dokument i C# och initiera DocumentBuilder

Det första steget är att instansiera ett `Document`‑objekt och en `DocumentBuilder`. `Document` representerar hela .docx‑filen, medan `DocumentBuilder` erbjuder flödande metoder för att lägga till innehåll.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document document = new Document();

        // Attach a builder to the document so we can insert nodes.
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Varför detta är viktigt:** Utan en `DocumentBuilder` skulle du behöva manipulera OpenXML‑DOM manuellt, vilket är felbenäget och svårare att läsa. Buildern abstraherar dessa detaljer och garanterar en välformad Word‑fil.

## Steg 2: Hur du lägger till en ActiveX‑knapp – infoga en CommandButton‑kontroll

Nu infogar vi en **CommandButton ActiveX‑kontroll** på en specifik plats. Rektangeln definierar knappens position (X, Y) och storlek (bredd, höjd) i punkter.

```csharp
        // Define the button's position and size.
        RectangleF buttonRect = new RectangleF(100, 100, 120, 30);

        // Insert the ActiveX CommandButton control.
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,   // Type of ActiveX control
            buttonRect,                          // Geometry
            "ClickMe");                          // Caption shown at design time
```

**Varför detta är viktigt:** `InsertForms2OleControl` är den enda Aspose.Words‑metoden som skapar ett riktigt ActiveX‑OLE‑objekt. Enum‑värdet `Forms2OleControlType.CommandButton` instruerar Word att bädda in en klickbar knapp istället för en generisk OLE‑behållare.

## Steg 3: Programmera in kommandoknapp – dölja den tills körning

Word behandlar alla infogade former som synliga som standard. För att hålla knappen osynlig medan du designar mallen, sätt `Hidden`‑egenskapen på formen som buildern just skapade.

```csharp
        // Retrieve the shape that represents the newly added control.
        Shape oleShape = (Shape)builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)[0];

        // Hide the shape; it will become visible when the document is opened.
        oleShape.Hidden = true;
```

**Varför detta är viktigt:** Att sätta `Hidden = true` förhindrar att knappen stör designvyn. När dokumentet öppnas i Word avslöjar körningsmiljön automatiskt kontrollen, vilket bevarar den avsedda användarupplevelsen.

## Steg 4: Spara filen – skapa Word-dokument med kommandoknapp

Till sist, skriv dokumentet till disk. Välj en sökväg som din applikation kan skriva till, och använd `.docx`‑extensionen för att säkerställa modern kompatibilitet.

```csharp
        // Save the document containing the ActiveX button.
        document.Save(@"C:\Temp\ActiveXButton.docx");
    }
}
```

**Varför detta är viktigt:** Att spara som `.docx` garanterar att den inbäddade ActiveX‑kontrollen följer Office Open XML‑standarden, som stöds av Word 2007 och senare. Om du behöver äldre `.doc`‑stöd, byt extensionen och använd `SaveFormat.Doc`.

## Fullt fungerande exempel

När allt sätts ihop, här är det kompletta programmet som du kan kopiera, klistra in och köra:

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Step 1: Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control.
        RectangleF commandButtonRect = new RectangleF(100, 100, 120, 30);
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            commandButtonRect,
            "ClickMe");

        // Step 3: Hide the control so it appears only at runtime.
        Shape oleShape = (Shape)builder.CurrentParagraph
                                         .GetChildNodes(NodeType.Shape, true)[0];
        oleShape.Hidden = true;

        // Step 4: Save the document containing the ActiveX control.
        document.Save(@"C:\Temp\ActiveX.docx");
    }
}
```

**Förväntat resultat:** Efter att programmet har körts, öppna `C:\Temp\ActiveX.docx` i Microsoft Word. Du kommer att se ett tomt dokument; knappen är inte synlig i designläge. Tryck **Alt + F9** för att växla fältkoder, klicka sedan på knappområdet—Word kommer att rendera ActiveX‑kontrollen, och du kan interagera med den (t.ex. dubbelklicka för att visa dess egenskaper).

## Edge‑fall och bästa‑praxis‑tips

| Situation | Vad att hålla utkik efter | Rekommenderad åtgärd |
|-----------|---------------------------|---------------------|
| **Användaren inaktiverar ActiveX** | Word kan visa en säkerhetsvarning eller blockera kontrollen. | Instruera slutanvändare att aktivera “ActiveX‑kontroller” i Trust Center, eller tillhandahåll ett makro‑signerat alternativ. |
| **Dokument öppnas i Word Online** | Word Online stödjer inte ActiveX; knappen kommer att utelämnas. | Använd en reserv‑hyperlänk eller ett innehållskontroll om du behöver molnkompatibilitet. |
| **Olika DPI‑inställningar** | Rektangelns storlek kan visas större eller mindre på hög‑DPI‑skärmar. | Använd `GraphicsUnit.Point` (standard) och testa på vanliga DPI‑inställningar (96 dpi, 120 dpi). |
| **Flera knappar** | Anropet `GetChildNodes(NodeType.Shape, true)[0]` hämtar bara den första formen. | Loopa igenom `builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)` och sätt `Hidden` för varje form du lägger till. |
| **Legacy .doc‑format** | Vissa ActiveX‑egenskaper går förlorade när du sparar som `.doc`. | Föredra `.docx` om du inte har ett strikt legacy‑krav. |

**Proffstips:** Efter att du har infogat knappen kan du tilldela ett makro till dess `OnAction`‑egenskap via Word‑gränssnittet. Detta låter dig definiera anpassat klickbeteende utan att skriva extra C#‑kod.

## Vanliga frågor

* **Fungerar detta med .NET Core?**  
  Ja. Aspose.Words for .NET är fullt kompatibel med .NET 5, .NET 6 och senare. Referera bara samma NuGet‑paket.

* **Kan jag ändra knappens rubrik efter att dokumentet har genererats?**  
  Rubriken som sätts i `InsertForms2OleControl` blir standardtexten i designläget. Användare kan redigera den i Word, men du kan också uppdatera rubriken programatiskt genom att komma åt OLE‑objektets egenskaper via `Shape.OleFormat`‑API:et.

* **Vad gör jag om jag behöver en annan storlek på knappen?**  
  Justera `RectangleF`‑värdena. De två första parametrarna är X‑ och Y‑koordinaterna; de två sista är bredd och höjd i punkter (1 pt = 1/72 tum).

## Slutsats

Du vet nu hur du **skapar Word-dokument i C#** och **programmerar in en kommandoknapp** med hjälp av Aspose.Words. Handledningen gick igenom hur du initierar dokumentet, infogar en ActiveX‑knapp, döljer den tills körning och sparar den slutliga filen. Med dessa byggstenar kan du bädda in interaktiva kontroller i vilken Word‑mall du än genererar.

Nästa steg är att utforska relaterade ämnen som **hur du lägger till ActiveX‑knapp**‑händelsehantering, **skapa kommandoknapp‑Word**‑formatering med VBA, och **programmerat lägga till kommandoknapp** i befintliga dokument. Att utöka detta mönster till kryssrutor, kombinationsrutor eller anpassade OLE‑objekt följer samma steg – byt bara `Forms2OleControlType`‑enum‑värdet.

Börja experimentera: ersätt rubriken, justera positionen eller kedja flera kontroller tillsammans. Ju mer du övar, desto smidigare blir du på att leverera rika, interaktiva Word‑dokument från C#. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närliggande ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur du lägger till en kommandoknapp programatiskt i ett Word-dokument](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Hur du lägger till en ActiveX‑knapp i ett Word-dokument med Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Skapa Word-dokument med ActiveX‑knapp – C#‑guide](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}