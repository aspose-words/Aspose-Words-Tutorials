---
category: general
date: 2026-10-20
description: Skapa ett Word‑dokument programatiskt och lägg till en kommandoknapp
  med Aspose.Words. Lär dig att infoga en ActiveX‑kontroll och ange knappens rubrik.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add command button
- add activex control
- insert activex button
- set button caption
language: sv
lastmod: 2026-10-20
og_description: Skapa Word-dokument programatiskt och bädda in en ActiveX‑kommandoknapp.
  Denna handledning förklarar hur du infogar kontrollen och sätter dess etikett med
  Aspose.Words.
og_image_alt: Word file showing an ActiveX command button inserted by Aspose.Words
og_title: Skapa ett Word‑dokument programatiskt – lägg till en ActiveX‑knapp
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  headline: Create Word document programmatically with an ActiveX button
  type: TechArticle
- description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  name: Create Word document programmatically with an ActiveX button
  steps:
  - name: 'Open a terminal or Visual Studio and create a new console project:'
    text: 'Open a terminal or Visual Studio and create a new console project:'
  - name: 'Add the Aspose.Words package:'
    text: 'Add the Aspose.Words package:'
  - name: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
    text: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
  - name: Open `ActiveXCommandButton.docx` in Microsoft Word.
    text: Open `ActiveXCommandButton.docx` in Microsoft Word.
  - name: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
    text: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
  - name: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
    text: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
  - name: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
    text: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Skapa Word-dokument programatiskt med en ActiveX‑knapp
url: /sv/net/working-with-oleobjects-and-activex/create-word-document-programmatically-with-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa Word-dokument programatiskt med en ActiveX-knapp

Skapa Word-dokument programatiskt med Aspose.Words, och lägg sedan till en kommandoknapp som användare kan klicka på. Denna guide visar dig hur du infogar en ActiveX-kontroll, konfigurerar dess egenskaper och sparar resultatet som en **.docx**-fil.

Du kommer att se ett komplett, körbart exempel som du kan kopiera in i en konsolapplikation. I slutet av handledningen kan du generera en Word-fil som innehåller en fullt fungerande kommandoknapp, och du kommer att förstå hur du **add command button**, **add activex control**, **insert activex button**, och **set button caption** utan att lämna din C#-kod.

## Förutsättningar

* .NET 6.0 SDK eller senare installerat  
* Visual Studio 2022 (eller någon C#‑kompatibel IDE)  
* En Aspose.Words för .NET-licensfil (gratis provversion fungerar för detta exempel)  
* Grundläggande kunskap om C# och .NET-projektsystemet  

Inga ytterligare NuGet-paket krävs utöver **Aspose.Words** eftersom ActiveX-stödet är inbyggt i biblioteket.

## Steg 1: Ställ in projektet och lägg till Aspose.Words

1. Öppna en terminal eller Visual Studio och skapa ett nytt konsolprojekt:

   ```bash
   dotnet new console -n WordActiveXDemo
   cd WordActiveXDemo
   ```

2. Lägg till Aspose.Words-paketet:

   ```bash
   dotnet add package Aspose.Words
   ```

3. (Valfritt) Om du har en licensfil, placera den i projektets rot och lägg till följande rad i början av `Program.cs` för att undvika utvärderingsvattenmärken:

   ```csharp
   Aspose.Words.License license = new Aspose.Words.License();
   license.SetLicense("Aspose.Words.lic");
   ```

## Steg 2: Skapa Word-dokument programatiskt – initiera dokumentet

Den första operationen är att **create Word document programmatically**. Du gör detta genom att instansiera ett `Document`-objekt och en `DocumentBuilder` som låter dig redigera dokumentets innehåll.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;   // Provides ActiveX control types
using System.Drawing;        // For Point and Size structs

// Initialize a new blank document
Document document = new Document();

// DocumentBuilder gives a cursor‑based API for inserting elements
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` representerar hela filen, medan `DocumentBuilder` håller ett markör som du kan flytta till vilken plats som helst i dokumentet. Denna separation håller API:t rent och gör det möjligt att **add activex control** senare utan att manuellt hantera lågnivåstrukturer.

## Steg 3: Lägg till kommandoknapp – infoga en ActiveX-kontroll

Nu kommer du att **add command button** genom att infoga en ActiveX-kontroll av typen `OleControlType.CommandButton`. Metoden `InsertForms2OleControl` kräver kontrolltypen, en plats (`Point`) och en storlek (`Size`).

```csharp
// Define where the button will appear (X = 100 pt, Y = 150 pt)
Point buttonPosition = new Point(100, 150);

// Define the button dimensions (width = 120 pt, height = 30 pt)
Size buttonSize = new Size(120, 30);

// Insert the ActiveX command button at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton, // control type
    buttonPosition,              // position
    buttonSize);                 // size
```

Anropet ovan **insert activex button** i dokumentet på de exakta koordinater du anger. Koordinaterna mäts i punkter (1 pt ≈ 1/72 in). Om du behöver knappen i ett specifikt stycke, flytta först byggarens markör:

```csharp
builder.Writeln("Click the button below:");
builder.MoveToDocumentEnd(); // places the cursor after the paragraph
```

## Steg 4: Ställ in knappens rubrik – anpassa kommandoknappens text

En knapp utan etikett är förvirrande, så du kommer att **set button caption** till något meningsfullt. `Caption`-egenskapen definierar texten som visas på knappen, medan `Name` ger kontrollen en programmatisk identifierare.

```csharp
// Give the button a unique name for later reference
commandButton.Name = "btnSubmit";

// Set the visible text on the button
commandButton.Caption = "Submit";

// Optional: assign a macro name that Word will call when the button is clicked
commandButton.OnClick = "SubmitForm()";
```

Om du senare exporterar dokumentet till ett makro‑aktiverat format (`.docm`), måste `OnClick`-värdet matcha ett VBA-makronamn. För en vanlig `.docx` lagras egenskapen men körs inte, vilket är okej för de flesta automationsscenarier.

## Steg 5: Spara dokumentet som innehåller ActiveX-knappen

Efter att ha konfigurerat kontrollen kan du **save the document**. Välj en katalog som du har skrivbehörighet till, och använd `.docx`-extensionen för maximal kompatibilitet.

```csharp
// Replace with your desired output folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ActiveXCommandButton.docx");

// Save the document to disk
document.Save(outputPath);
```

När du öppnar den genererade filen i Microsoft Word kommer du att se en knapp med etiketten **Submit** på de koordinater du angav. Att klicka på knappen i skrivbordsklienten kommer att försöka köra `SubmitForm`-makrot (om det finns).

## Steg 6: Verifiera resultatet och felsök vanliga problem

1. Öppna `ActiveXCommandButton.docx` i Microsoft Word.  
2. Byt till **Design Mode** (Developer-fliken → **Design Mode**) för att se knappens kanter.  
3. Om knappen inte visas, kontrollera att **Developer**-fliken är aktiverad och att din Word-version stöder ActiveX-kontroller.  
4. För makro‑aktiverade filer (`.docm`), säkerställ att makronamnet i `OnClick` matchar en VBA‑rutin; annars kommer Word att visa en säkerhetsvarning.

### Proffstips

ActiveX-kontroller är endast för Windows. Om du behöver plattformsoberoende interaktivitet, överväg att använda **Content Controls** (`RichTextContentControl`) istället för en ActiveX-knapp.

## Fullständig källkod

Nedan är det kompletta, färdiga att köra programmet. Kopiera det till `Program.cs` och kör `dotnet run`.



## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa Word-dokument med ActiveX-knapp – C#-guide](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)
- [Lägg till kommandoknapp i Word-dokument med Aspose.Words – Komplett guide](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)
- [Skapa Word-dokumentknapp med Aspose.Words – Fullt kodexempel](/words/english/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}