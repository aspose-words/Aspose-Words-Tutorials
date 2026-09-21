---
category: general
date: 2026-09-21
description: Lär dig hur du skapar en ActiveX‑kommandoknapp i ett Word‑dokument med
  Aspose.Words och C#. En steg‑för‑steg‑guide täcker infogning, placering och sparande.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- aspose.words activex
- c# documentbuilder
- insertforms2olecontrol
- activeX control in word
- programmatically add button
language: sv
lastmod: 2026-09-21
og_description: Skapa en ActiveX‑kommandoknapp i ett Word‑dokument med C# och Aspose.Words.
  Följ den här kompletta handledningen för att programatiskt infoga, placera och spara
  knappen.
og_image_alt: Screenshot showing an ActiveX command button inserted in a Word document
  using C#
og_title: Skapa en ActiveX‑kommandoknapp i Word med C# – fullständig guide
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create ActiveX command button in a Word document with
    Aspose.Words and C#. Step‑by‑step guide covers insertion, positioning, and saving.
  headline: How to create ActiveX command button in Word using C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
- DocumentBuilder
title: Hur man skapar en ActiveX‑kommandoknapp i Word med C#
url: /sv/net/working-with-oleobjects-and-activex/how-to-create-activex-command-button-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så skapar du en ActiveX‑kommandoknapp i Word med C#

Om du behöver **skapa en ActiveX‑kommandoknapp** i ett Word‑dokument, visar den här guiden de exakta stegen. Med Aspose.Words för .NET kan du lägga till, placera och konfigurera knappen helt från C#‑kod.

Programmatisk insättning av en ActiveX‑knapp eliminerar manuellt UI‑arbete och möjliggör automatiserad dokumentgenerering för formulär, rapporter eller interaktiva mallar. I den här handledningen lär du dig hur du använder **DocumentBuilder**, metoden **InsertForms2OleControl** och relaterade egenskaper för att skapa en fullt funktionell knapp.

## Vad du behöver

* .NET 6.0 SDK eller senare (koden fungerar också med .NET Framework 4.7+)
* Aspose.Words för .NET (NuGet‑paket `Aspose.Words`)
* En IDE såsom Visual Studio 2022 eller VS Code
* Grundläggande kunskap om C# och Word‑dokumentkoncept

Ingen extra Office‑installation krävs eftersom Aspose.Words fungerar oberoende av Microsoft Word.

## Steg 1: Ställ in C#‑projektet

Skapa ett nytt konsolprojekt och lägg till Aspose.Words‑paketet.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

`Aspose.Words`‑biblioteket tillhandahåller klassen **DocumentBuilder** som vi kommer att använda för att manipulera dokumentet.

## Steg 2: Initiera dokumentet och buildern

Det första kodblocket skapar ett tomt dokument och en `DocumentBuilder`‑instans. Detta objekt är ingångspunkten för alla Word‑bearbetningsoperationer.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// Create a new blank document.
Document doc = new Document();

// Create a builder to edit the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Varför detta är viktigt:** `DocumentBuilder` behåller den aktuella markörpositionen, så varje efterföljande insättning kommer att visas exakt där du placerar markören.

## Steg 3: Infoga ActiveX‑kommandoknappen

Metoden **InsertForms2OleControl** skapar en ActiveX‑kontroll av den begärda typen. Här begär vi en `CommandButton` och anger dess storlek i punkter (200 × 30 pt).

```csharp
// Insert an ActiveX CommandButton control (200 × 30 pt).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    OleControlType.CommandButton, 200, 30);
```

**Förklaring:**  
* `OleControlType.CommandButton` talar om för Aspose.Words att skapa en knapp snarare än en annan kontrolltyp.  
* Metoden returnerar ett `Forms2OleControl`‑objekt, som exponerar positionerings‑ och egenskapsfält.

## Steg 4: Positionera knappen och ställ in dess egenskaper

Efter insättningen kan du flytta knappen till valfri plats på sidan och ge den ett programatiskt namn samt en synlig rubrik.

```csharp
// Position the button (coordinates are in points).
cmdBtn.Left = 100;          // X‑coordinate
cmdBtn.Top = 150;           // Y‑coordinate

// Set the button's programmatic name and displayed text.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

**Proffstips:** Koordinatsystemet börjar i sidans övre vänstra hörn. Justera `Left` och `Top` för att alignera knappen med andra formulärfält.

## Steg 5: Spara dokumentet

Slutligen skriver du dokumentet till disk. Filen kommer att innehålla ActiveX‑knappen, redo att öppnas i Microsoft Word där knappen blir interaktiv.

```csharp
// Save the document that now contains the ActiveX button.
doc.Save("ActiveXCommandButton.docx");
```

När du öppnar `ActiveXCommandButton.docx` i Word ser du en knapp med etiketten **Submit** på den angivna platsen. Att klicka på den i Word utlöser standardbeteendet för kommandoknappen (som du senare kan anpassa med VBA eller Word‑tillägg).

## Komplett, körbart exempel

Att sätta ihop alla bitar ger ett fristående program som du kan kopiera, klistra in och köra.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX CommandButton (200 × 30 pt).
        Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
            OleControlType.CommandButton, 200, 30);

        // 3. Position and configure the button.
        cmdBtn.Left = 100;          // X‑coordinate (points)
        cmdBtn.Top = 150;           // Y‑coordinate (points)
        cmdBtn.Name = "btnSubmit";
        cmdBtn.Caption = "Submit";

        // 4. Save the document.
        doc.Save("ActiveXCommandButton.docx");

        Console.WriteLine("Document created successfully.");
    }
}
```

**Förväntad output:** Konsolen skriver ut *“Document created successfully.”* och mappen innehåller nu `ActiveXCommandButton.docx`. När filen öppnas i Microsoft Word visas en klickbar **Submit**‑knapp placerad 100 pt från vänstermarginalen och 150 pt från sidans topp.

## Vanliga fallgropar och hur du undviker dem

| Problem | Varför det händer | Lösning |
|---------|-------------------|--------|
| Knappen visas utanför sidan | `Left`/`Top`‑värdena överstiger sidans dimensioner | Använd `doc.FirstSection.PageSetup.PageWidth` och `PageHeight` för att beräkna säkra koordinater |
| Knappen är inte synlig i Word | Dokumentet sparades i ett format som tar bort ActiveX‑kontroller (t.ex. `.txt`) | Spara alltid som `.docx` eller `.doc` |
| Körtidsfel `ArgumentOutOfRangeException` | Bredd eller höjd är satt till noll eller negativ | Se till att storleksargumenten som skickas till `InsertForms2OleControl` är positiva tal |

## Utöka lösningen

Du kan ytterligare anpassa knappen genom att ställa in extra egenskaper såsom `Enabled`, `Visible` eller bifoga ett makro via VBA. Klassen **Forms2OleControl** låter dig också infoga andra ActiveX‑kontroller som kryssrutor (`OleControlType.CheckBox`) eller kombinationsrutor (`OleControlType.ComboBox`).

Om du behöver generera flera knappar i en loop, kapsla in insättningslogiken i en hjälpfunktion:

```csharp
static Forms2OleControl AddCommandButton(DocumentBuilder builder,
    string name, string caption, double left, double top)
{
    var btn = builder.InsertForms2OleControl(OleControlType.CommandButton, 200, 30);
    btn.Name = name;
    btn.Caption = caption;
    btn.Left = left;
    btn.Top = top;
    return btn;
}
```

## Slutsats

Du vet nu hur du **skapar en ActiveX‑kommandoknapp** i ett Word‑dokument med C# och Aspose.Words. Handledningen täckte hur du ställer in projektet, infogar knappen med `InsertForms2OleControl`, positionerar den och sparar den slutliga filen. Med detta fundament kan du automatisera komplexa formulär, bädda in interaktiva kontroller och integrera Word‑dokument i större .NET‑lösningar.

Nästa steg är att utforska relaterade ämnen som **Aspose.Words ActiveX**‑formulärfält, **C# DocumentBuilder**‑avancerad formatering, eller programmatisk tillägg av **ActiveX‑kontroller i Word** för kryssrutor och rullgardinslistor. Experimentera med olika koordinater och storlekar för att passa dina specifika layoutkrav. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa Word‑dokument med Aspose.Words för .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Skapa rektangel‑form i Word med Aspose.Words – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Skapa ett Word‑dokument med tabell med Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}