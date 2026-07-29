---
category: general
date: 2026-07-29
description: Lägg till en kommandoknapp i Word-dokument med Aspose.Words. Lär dig
  hur du ställer in ActiveX‑kontrollegenskaper och sätter kommandoknappens rubrik
  i några enkla steg.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button to word document
- set activex control properties
- set command button caption
- Aspose.Words ActiveX example
- C# insert ActiveX control
language: sv
lastmod: 2026-07-29
og_description: Lägg till kommandoknapp i Word‑dokument med Aspose.Words. Den här
  handledningen visar hur du snabbt ställer in ActiveX‑kontrollens egenskaper och
  sätter kommandoknappens etikett.
og_image_alt: Screenshot of a Word document with a Submit command button inserted
  via C#
og_title: Lägg till kommandoknapp i Word‑dokument – Aspose.Words steg för steg
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  headline: Add Command Button to Word Document with Aspose.Words – Complete Guide
  type: TechArticle
- description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  name: Add Command Button to Word Document with Aspose.Words – Complete Guide
  steps:
  - name: Setting the Caption
    text: 'The caption is the text that appears on the button itself. To **set command
      button caption**, simply assign a string to the `Caption` property:'
  - name: Naming the Control
    text: 'Giving the control a meaningful name makes it easier to reference later
      (for example, when automating Word macros). We’ll set the `Name` property:'
  - name: Positioning on the Page
    text: 'Word uses points (1/72 of an inch) for layout. Adjust the `Left` and `Top`
      properties to place the button where you need it:'
  - name: Expected Result
    text: 1. The Word document opens with a single page. 2. A rectangular button labeled
      **Submit** appears at the coordinates you specified. 3. If you right‑click the
      button and choose **Properties**, you’ll see the name `btnSubmit` and other
      properties you set.
  - name: Inserting Other ActiveX Types
    text: 'The `InsertForms2OleControl` method isn’t limited to command buttons. You
      can embed check boxes, option buttons, or even custom ActiveX objects:'
  - name: Handling Word Versions
    text: Older Word versions (pre‑2007) use the binary `.doc` format, which stores
      ActiveX controls differently. Aspose.Words automatically converts the control
      when you save as `.doc`, but some properties (like precise positioning) may
      shift. If you target legacy formats, test the output in the specific Wor
  - name: Security Settings
    text: 'Word may disable ActiveX controls on machines with strict macro security.
      To avoid a “Security Warning” dialog, consider:'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Lägg till kommandoknapp i Word‑dokument med Aspose.Words – Komplett guide
url: /sv/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till kommandoknapp i Word-dokument – Komplett programmeringsgenomgång

Har du någonsin behövt **add command button to word document** men varit osäker på vilka API-anrop du ska använda? Du är inte ensam; många utvecklare stöter på detta när de första gången försöker bädda in interaktiva kontroller i en DOCX-fil. Den goda nyheten är att Aspose.Words gör det förvånansvärt smärtfritt. I den här guiden går vi igenom hur du skapar en CommandButton ActiveX-kontroll, **set activex control properties**, och **set command button caption**—allt med ren C#-kod som du kan kopiera‑klistra just nu.

I slutet av den här handledningen kommer du att ha en fullt funktionell Word-fil som innehåller en klickbar “Submit”-knapp, klar att öppnas i Microsoft Word. Inga externa VBA‑skript, ingen manuell UI‑justering—bara ren programmatisk kontroll.

## Vad du kommer att lära dig

* Hur man skapar ett tomt Word-dokument och en `DocumentBuilder`.
* Det exakta metodanropet för att **add command button to word document** med Aspose.Words.
* Sätt att **set activex control properties** såsom storlek, position och namn.
* Den korrekta tekniken för att **set command button caption** så att knappen visar exakt vad du vill.
* Tips för att hantera edge cases som olika knapptyper, DPI‑skalning och Word‑versionskompatibilitet.

> **Förutsättning:** Visual Studio (eller någon C#‑IDE) med Aspose.Words för .NET installerat (NuGet‑paketet `Aspose.Words`). Ingen tidigare ActiveX‑erfarenhet krävs.

---

## Steg 1: Ställ in projektet och importera namnrymder

Innan vi kan **add command button to word document** behöver vi ett C#‑projekt som refererar till Aspose.Words. Skapa en ny .NET‑konsolapp och lägg sedan till NuGet‑paketet:

```bash
dotnet add package Aspose.Words
```

Importera nu de nödvändiga namnrymderna i din källkod:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;
```

Dessa tre `using`‑direktiv ger dig åtkomst till klasserna `Document`, `DocumentBuilder` och `Forms2OleControl` som driver ActiveX‑infogning.

*Pro tip:* Om du använder Visual Studio kommer IDE:n föreslå att lägga till dessa automatiskt när du skriver klassnamnen.

---

## Steg 2: Skapa ett tomt dokument och en Builder

Ett nytt `Document`‑objekt representerar en tom Word‑fil. `DocumentBuilder` är vår praktiska “penna” som låter oss rita, infoga text och—viktigt—placera ActiveX‑kontroller.

```csharp
// Initialize a new, empty Word document.
Document doc = new Document();

// Attach a builder to the document for editing.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Vid detta tillfälle är dokumentet bara en tom canvas—tänk på det som ett rent papper som väntar på din kommandoknapp.

---

## Steg 3: Infoga CommandButton ActiveX‑kontrollen

Nu **add command button to word document** äntligen. Aspose.Words tillhandahåller metoden `InsertForms2OleControl`, som accepterar kontrolltyp och dimensioner. Vi kommer att använda `Forms2OleControlType.CommandButton` och ge den en bekväm bredd på 150 punkter och en höjd på 30 punkter.

```csharp
// Insert a CommandButton ActiveX control with a specific size.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton,
    width: 150,
    height: 30);
```

Metoden returnerar en `Forms2OleControl`‑instans, som vi kommer att använda för att **set activex control properties** i nästa steg.

---

## Steg 4: Konfigurera kontrollen – namn, rubrik och position

### Ställa in rubriken

Rubriken är den text som visas på själva knappen. För att **set command button caption**, tilldela helt enkelt en sträng till egenskapen `Caption`:

```csharp
commandButton.Caption = "Submit";
```

Du kan ändra `"Submit"` till vad som helst—“Save”, “Export”, “Launch”, etc.—och Word kommer att visa exakt den texten.

### Namnge kontrollen

Att ge kontrollen ett meningsfullt namn gör det enklare att referera till den senare (till exempel när du automatiserar Word‑makron). Vi kommer att sätta egenskapen `Name`:

```csharp
commandButton.Name = "btnSubmit";
```

### Positionering på sidan

Word använder punkter (1/72 tum) för layout. Justera egenskaperna `Left` och `Top` för att placera knappen där du behöver den:

```csharp
commandButton.Left = 100; // 100 points from the left margin
commandButton.Top  = 200; // 200 points from the top of the page
```

Om du behöver justera knappen relativt ett stycke kan du först flytta builderns markör och sedan infoga kontrollen; koordinaterna blir relativa till den platsen.

*Edge case:* På hög‑DPI‑monitorer kan den visuella storleken se något annorlunda ut i Word. För att hålla knappens fysiska storlek konsekvent över enheter kan du beräkna punkterna baserat på mål‑DPI (vanligtvis 96 DPI för Word).

---

## Steg 5: Spara dokumentet

När knappen är helt konfigurerad är det en enradig kod för att spara filen:

```csharp
// Save the document; the ActiveX control is stored inside the DOCX.
doc.Save("CommandButton.docx");
```

Den resulterande `CommandButton.docx` innehåller en fullt funktionell ActiveX‑knapp. Öppna den i Microsoft Word så ser du en “Submit”-knapp placerad exakt där du placerade den.

### Förväntat resultat

1. Word‑dokumentet öppnas med en enda sida.
2. En rektangulär knapp med etiketten **Submit** visas på de koordinater du angav.
3. Om du högerklickar på knappen och väljer **Properties**, ser du namnet `btnSubmit` och andra egenskaper du har satt.

---

## Steg 6: Avancerade varianter och vanliga fallgropar

### Infoga andra ActiveX‑typer

`InsertForms2OleControl`‑metoden är inte begränsad till kommandoknappar. Du kan bädda in kryssrutor, alternativknappar eller till och med anpassade ActiveX‑objekt:

```csharp
// Example: Insert a CheckBox instead of a CommandButton.
Forms2OleControl checkBox = builder.InsertForms2OleControl(
    Forms2OleControlType.CheckBox,
    width: 20,
    height: 20);
checkBox.Name = "chkAgree";
checkBox.Caption = "I Agree";
```

Samma **set activex control properties**‑mönster gäller—byt bara typ‑enum.

### Hantera Word‑versioner

Äldre Word‑versioner (före 2007) använder det binära `.doc`‑formatet, som lagrar ActiveX‑kontroller på ett annat sätt. Aspose.Words konverterar automatiskt kontrollen när du sparar som `.doc`, men vissa egenskaper (som exakt positionering) kan förskjutas. Om du riktar dig mot äldre format, testa utdata i den specifika Word‑version du behöver.

### Säkerhetsinställningar

Word kan inaktivera ActiveX‑kontroller på maskiner med strikt makrosäkerhet. För att undvika en “Security Warning”-dialog, överväg:

* Signera dokumentet med ett betrott certifikat.
* Instruera användare att aktivera ActiveX‑innehåll för den filplatsen.
* Använda ett makrofritt alternativ (t.ex. enkla innehållskontroller) om säkerhet är en oro.

---

## Steg 7: Fullt fungerande exempel

Nedan är det kompletta, färdiga att köra‑programmet som innehåller varje steg vi diskuterat. Kopiera det till din `Program.cs`, justera utsökvägen om nödvändigt, och tryck på **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            width: 150,   // Width in points
            height: 30);  // Height in points

        // Step 3: Set the control's name and caption.
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Step 4: Position the control on the page.
        commandButton.Left = 100; // 100 points from left edge
        commandButton.Top  = 200; // 200 points from top edge

        // Optional: Add a paragraph above the button for context.
        builder.MoveToDocumentEnd();
        builder.Writeln("Click the button below to submit the form:");

        // Step 5: Save the document.
        string outputPath = "CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved successfully to {outputPath}");
    }
}
```

**Vad den här koden gör:**

* Börjar med ett nytt dokument.
* Infogar en kommandoknapp, **sets activex control properties**, och **sets command button caption**.
* Lägger till ett kort förklarande stycke.
* Sparar filen som `CommandButton.docx`.

Kör programmet, öppna den genererade filen, så ser du knappen placerad under den förklarande texten.

## Slutsats

Vi har just demonstrerat hur man **add command button to word document** med Aspose.Words, hur man **set activex control properties**, och hur man **set command button caption**—allt i ett koncist, produktionsklart C#‑snippet. Metoden kan skalas: byt kontrolltyp, justera dimensioner, eller loopa över en datakälla för att automatiskt bädda in dussintals knappar.

Vill du gå längre? Prova:

* Koppla knappen till ett makro som triggar en dataexport.
* Lägga till bilder eller anpassade ikoner i knappen med egenskapen `Picture`.
* Bygga ett komplett formulär med flera ActiveX‑kontroller (textfält, kombinationsrutor, etc.).

Experimentering är det bästa sättet att bemästra Word‑automation. Om du stöter på problem, kom ihåg att dubbelkolla dina DPI‑beräkningar och Word‑säkerhetsinställningar. Lycka till med kodandet, och må dina dokument bli ännu mer interaktiva!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Lägg till innehåll med Document Builder i Aspose.Words för .NET](/words/english/net/add-content-using-document-builder/)
- [Skapa gruppform i Word-dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Skapa Word-dokument med sidhuvud och sidfot med Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}