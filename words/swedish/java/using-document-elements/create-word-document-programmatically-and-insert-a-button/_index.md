---
category: general
date: 2026-09-21
description: Skapa ett Word‑dokument programatiskt och lär dig hur du sparar Word‑dokument‑knappen,
  infogar en kommandoknapp för ord och ställer in kommandoknappens rubrik med DocumentBuilder.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- save word document button
- insert command button word
- set command button caption
- how to use documentbuilder
language: sv
lastmod: 2026-09-21
og_description: Skapa Word‑dokument programatiskt med Aspose.Words. Lär dig hur du
  sparar Word‑dokument med en knapp, infogar en kommandoknapp i Word, anger kommandoknappens
  rubrik och använder DocumentBuilder för interaktiva formulär.
og_image_alt: Screenshot of a Word file that contains an inserted CommandButton created
  programmatically
og_title: Skapa Word-dokument programatiskt och lägg till en knapp
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically and learn how to save word document
    button, insert command button word, and set command button caption using DocumentBuilder.
  headline: Create word document programmatically and insert a button
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Skapa Word-dokument programatiskt och infoga en knapp
url: /sv/java/using-document-elements/create-word-document-programmatically-and-insert-a-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa Word-dokument programatiskt och infoga en knapp

Om du behöver **skapa Word-dokument programatiskt**, erbjuder Aspose.Words ett flytande API som låter dig lägga till interaktiva kontroller såsom en CommandButton. Denna handledning förklarar också **hur man använder DocumentBuilder**, hur man **sparar Word-dokumentknapp**, och hur man **sätter kommandoknappens rubrik** så att knappen visas exakt som du förväntar dig i .docx-filen.

Du kommer att lära dig hur du:

* Initierar ett tomt dokument med `Document`.
* Arbetar med `DocumentBuilder` för att redigera dokumentet.
* Infogar en **CommandButton** (`insert command button word`).
* Anger knappens namn och synliga rubrik (`set command button caption`).
* Sparar resultatet till disk (`save word document button`).

Stegen är skrivna för .NET-utvecklare som använder C# och den senaste Aspose.Words för .NET (v24.10). Inga extra NuGet-paket krävs utöver Aspose.Words.

---

## Vad du behöver innan du börjar

| Förutsättning | Orsak |
|--------------|--------|
| Visual Studio 2022 (eller någon C#-IDE) | För att kompilera och köra exempelprogrammet. |
| .NET 6.0 SDK eller senare | Tillhandahåller runtime för exemplet. |
| Aspose.Words for .NET (v24.10 eller nyare) | Biblioteket som låter dig **skapa Word-dokument programatiskt** och manipulera formulärkontroller. |
| Grundläggande kunskap om C# och OOP-koncept | Krävs för att förstå kodflödet. |

Du kan installera Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Skapa Word-dokument programatiskt

Det första steget är att instansiera ett tomt `Document`. Detta objekt representerar hela Word-filen i minnet.

```csharp
// Step 1: Create a new blank document
Document doc = new Document();
```

Att skapa dokumentet programatiskt ger dig en ren canvas där du kan lägga till stycken, tabeller eller interaktiva kontroller.  

---

## Så använder du DocumentBuilder

`DocumentBuilder` är huvudklassen för att redigera ett `Document`. Den erbjuder metoder för att infoga text, bilder och formulärfält. I den här handledningen använder vi den för att placera en CommandButton.

```csharp
// Step 2: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

Buildern upprätthåller en intern markör som pekar på den aktuella infogningsplatsen. Som standard startar den i början av den första sektionen, vilket är idealiskt för vårt exempel.

---

## Infoga kommandoknapp i Word

Aspose.Words behandlar en CommandButton som en ActiveX-kontroll. Metoden `InsertForms2OleControl` skapar en generisk OLE-kontroll som vi sedan konfigurerar som en knapp.

```csharp
// Step 3: Insert an ActiveX Forms2OleControl (a CommandButton)
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

Vid detta steg finns kontrollen i dokumentet men har ingen visuell representation förrän vi definierar dess typ.

---

## Sätt kommandoknappens rubrik

Nu talar vi om för OLE-kontrollen att den ska fungera som en CommandButton och ger den en vänlig etikett.

```csharp
// Step 4: Define the control as a CommandButton
commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

// Step 5: Set a unique name for the button (used for identification)
commandButton.SetName("btnSubmit");

// Step 6: Set the visible caption that appears on the button
commandButton.SetCaption("Submit");
```

Att sätta **kommandoknappens rubrik** är viktigt eftersom Word visar denna text på knappens yta. Om du utelämnar `SetCaption` kommer knappen att visas med en generisk etikett.

---

## Spara Word-dokumentknapp

Slutligen sparas dokumentet till disk. Metoden `Save` skriver hela Word-paketet, inklusive den nyinfogade knappen, till en .docx-fil.

```csharp
// Step 7: Save the document containing the CommandButton
doc.Save("YOUR_DIRECTORY/CommandButton.docx");
```

Filen `CommandButton.docx` innehåller nu en fullt funktionell knapp med etiketten **Submit**. När användaren öppnar filen i Microsoft Word och klickar på knappen, kommer standardåtgärden (som du senare kan binda via VBA) att triggas.

---

## Fullt fungerande exempel

Nedan är det kompletta programmet som du kan kopiera, klistra in och köra. Det demonstrerar hela arbetsflödet från dokumentskapande till att spara knappen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder (how to use DocumentBuilder)
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a CommandButton (insert command button word)
        Forms2OleControl commandButton = builder.InsertForms2OleControl();

        // 4. Define the control type as CommandButton
        commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

        // 5. Give the button a unique name (optional but useful)
        commandButton.SetName("btnSubmit");

        // 6. Set the visible caption (set command button caption)
        commandButton.SetCaption("Submit");

        // 7. Save the document (save word document button)
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Förväntat resultat**

* En fil med namnet `CommandButton.docx` placerad på den sökväg du angav.
* När filen öppnas i Microsoft Word visas en enda **Submit**-knapp på första sidan.
* Knappen kan väljas, ändras i storlek eller länkas till ett makro från Word's **Developer**-flik.

---

## Vanliga frågor och hantering av kantfall

| Fråga | Svar |
|----------|--------|
| *Vad händer om jag behöver mer än en knapp?* | Upprepa steg 3–6 med olika namn och rubriker. Varje knapp måste ha ett unikt `SetName`-värde. |
| *Kan jag ange knappens storlek?* | Ja. Efter att ha infogat kontrollen kan du ändra dess `Width`- och `Height`-egenskaper via `OleFormat`-objektet. |
| *Fungerar knappen i alla Word-versioner?* | ActiveX-kontroller stöds i skrivbordsversionen av Word (Windows). De renderas inte i Word Online eller på macOS. |
| *Hur lägger man till en klick‑hanterare?* | Du måste skriva VBA‑kod som refererar till knappens namn (`btnSubmit`). VBA‑makrot kan bäddas in med `doc.VbaProject`. |
| *Vad händer om jag behöver infoga knappen i en tabellcell?* | Flytta builderns markör till önskad cell (`builder.MoveTo(cell.FirstParagraph)`) innan du anropar `InsertForms2OleControl`. |

---

## Pro‑tips

* **Pro‑tips:** Ange alltid ett meningsfullt namn med `SetName`. Det förenklar VBA‑automation och gör felsökning enklare.
* **Se upp för:** Att glömma att anropa `SetControlType`. Utan detta anrop visas OLE‑objektet som en generisk platshållare snarare än en klickbar knapp.
* **Prestandatips:** Om du genererar många dokument i en loop, återanvänd en enda `DocumentBuilder`‑instans och anropa `builder.MoveToDocumentEnd()` före varje infogning för att undvika onödiga marköråterställningar.

---

## Nästa steg

Nu när du vet hur man **skapar Word-dokument programatiskt**, **infogar kommandoknapp i Word**, **sätter kommandoknappens rubrik**, och **sparar Word-dokumentknapp**, kan du utforska mer avancerade scenarier:

* Lägg till **TextFormField**-kontroller för användarinmatning.
* Kombinera knappar med **MacroButton**-fält för att köra VBA direkt.
* Använd **DocumentBuilder.InsertImage** för att placera ikoner på dina knappar.
* Integrera med ASP.NET för att generera Word-formulär på

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa nytt Word-dokument](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Skapa Word-dokument med Aspose.Words för .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Infoga inbäddad bild i Word-dokument med Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}