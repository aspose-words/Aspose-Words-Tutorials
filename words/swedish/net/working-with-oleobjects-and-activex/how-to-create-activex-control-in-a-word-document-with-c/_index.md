---
category: general
date: 2026-09-14
description: Skapa ActiveX‑kontroll i ett Word‑dokument med C#. Lär dig hur du infogar
  ActiveX, lägger till en interaktiv knapp och genererar .docx‑filen programatiskt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- how to insert activex
- add interactive button
- create word document
- create button with code
language: sv
lastmod: 2026-09-14
og_description: Skapa en ActiveX‑kontroll i ett Word‑dokument med C#. Följ detta kompletta
  exempel för att infoga ActiveX, lägga till en interaktiv knapp och spara filen.
og_image_alt: Screenshot of a Word document containing a newly created ActiveX CommandButton
og_title: Skapa en ActiveX‑kontroll i Word med C# – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Create ActiveX control in a Word document with C#. Learn how to insert
    ActiveX, add interactive button, and generate the .docx file programmatically.
  headline: How to create ActiveX control in a Word document with C#
  type: TechArticle
tags:
- ActiveX
- C#
- Word automation
title: Hur man skapar en ActiveX‑kontroll i ett Word‑dokument med C#
url: /sv/net/working-with-oleobjects-and-activex/how-to-create-activex-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så skapar du en ActiveX‑kontroll i ett Word‑dokument med C#

Om du behöver **skapa ActiveX‑kontroll** i en Microsoft Word‑fil, visar den här guiden en komplett, färdig‑att‑köra‑lösning. Du kommer att se exakt hur du infogar en ActiveX CommandButton, ställer in dess egenskaper och sparar den resulterande `.docx`‑filen med endast C#‑kod.

Att lägga till en interaktiv knapp i ett Word‑dokument är ett vanligt krav när du vill att slutanvändare ska kunna trigga makron eller anpassad logik direkt från dokumentets UI. Exemplet nedan demonstrerar **hur man infogar ActiveX** utan att förlita sig på tredjepartsverktyg, och det täcker också **hur man skapar Word‑dokument** programatiskt.

I slutet av den här handledningen kommer du att kunna **skapa knapp med kod**, anpassa dess rubrik och producera en portabel Word‑fil som bevarar ActiveX‑kontrollen.

## Förutsättningar

- .NET 6.0 eller senare (Aspose.Words för .NET‑biblioteket fungerar med .NET Core och .NET Framework)
- En referens till NuGet‑paketet `Aspose.Words`  
  ```bash
  dotnet add package Aspose.Words
  ```
- Grundläggande kunskaper i C# och objekt‑orienterad programmering

## Steg 1: Ställ in projektet och importera namnrymder

Skapa ett nytt konsolprojekt (eller integrera koden i ett befintligt C#‑program). Importera de nödvändiga namnrymderna så att kompilatorn kan hitta Word‑bearbetningsklasserna.

```csharp
using System;
using System.Drawing;               // Provides RectangleF
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
```

> **Varför detta steg är viktigt** – `Aspose.Words`‑API:et tillhandahåller klasserna `Document`, `DocumentBuilder` och `Forms2OleControl` som låter dig manipulera Word‑filer på objektnivå. Utan dessa referenser skulle resten av koden inte kunna kompileras.

## Steg 2: Skapa ett nytt Word‑dokument och en DocumentBuilder

`Document`‑objektet representerar hela `.docx`‑paketet, medan `DocumentBuilder` erbjuder ett flytande API för att infoga innehåll.

```csharp
// Step 2: Initialize a fresh Word document
Document document = new Document();

// Attach a builder to the document – the builder knows where to write next
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Förklaring** – Att instansiera ett nytt `Document` ger dig en ren canvas. Builderns markör startar i början av den första sektionen, redo för nästa infogning.

## Steg 3: Infoga ActiveX CommandButton

Använd `InsertForms2OleControl` för att placera en ActiveX‑kontroll på en specifik plats. Metoden kräver kontrolltypen och en `RectangleF` som definierar X/Y‑koordinaterna och storleken (i punkter).

```csharp
// Step 3: Add an ActiveX CommandButton at (100,100) with width 120 and height 30
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Varför detta fungerar** – `OleControlType.CommandButton` instruerar API:et att skapa en standard Windows CommandButton. Rektangeln placerar knappen relativt till sidans övre‑vänstra hörn, vilket låter dig **lägga till en interaktiv knapp** exakt där du behöver den.

## Steg 4: Konfigurera knappens egenskaper

Ställ nu in knappens synliga text (`Caption`) och dess interna namn (`Name`). Dessa egenskaper är vad användarna ser och vad VBA‑kod kan referera till senare.

```csharp
// Step 4: Define the button’s caption and programmatic name
commandButton.Caption = "Click Me";
commandButton.Name = "btnClick";
```

> **Praktiskt tips** – `Name` måste vara unikt inom dokumentet; annars kan VBA‑makron referera till fel kontroll.

## Steg 5: Spara dokumentet

Skriv slutligen filen till disk. ActiveX‑kontrollen lagras i Word‑paketet, så den sparade filen behåller full funktionalitet när den öppnas i Microsoft Word.

```csharp
// Step 5: Persist the document – the ActiveX control stays embedded
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Resultat** – När du öppnar `CommandButton.docx` i Word visas en klickbar CommandButton med etiketten “Click Me”. Kontrollen kan länkas till ett makro via Word‑UI (`Developer → Design Mode → Properties`).

## Fullständig källkodslista

Att sätta ihop alla steg ger ett enda, självständigt program som du kan kopiera, klistra in och köra.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an ActiveX CommandButton at the desired location
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new RectangleF(100, 100, 120, 30));

        // Set the button's caption and internal name
        commandButton.Caption = "Click Me";
        commandButton.Name = "btnClick";

        // Save the document – the control is preserved
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Förväntad output

När programmet körs skrivs en bekräftelsesats ut:

```
Document saved to C:\Temp\CommandButton.docx
```

När du öppnar den genererade filen i Microsoft Word kommer du att se en **CommandButton** placerad på de angivna koordinaterna. Att klicka på knappen i designläge markerar den; i körläge beter den sig som vilken standard‑ActiveX‑knapp som helst.

## Vanliga varianter och edge‑cases

| Scenario | Adjustment |
|----------|------------|
| **Olika kontrolltyp** | Byt ut `OleControlType.CommandButton` mot `OleControlType.CheckBox`, `OleControlType.OptionButton` osv. |
| **Flera knappar** | Anropa `InsertForms2OleControl` upprepade gånger och uppdatera `RectangleF`‑koordinaterna för varje ny knapp. |
| **Dynamisk storlek** | Beräkna rektangelns dimensioner baserat på sidstorlek (`builder.PageSetup.PageWidth`). |
| **Spara till en ström** | Använd `document.Save(stream, SaveFormat.Docx)` när du behöver returnera filen från ett webb‑API. |
| **Word 97‑2003‑format** | Ändra sparformatet till `SaveFormat.Doc` för att producera en `.doc`‑fil som fortfarande bäddar in ActiveX‑kontrollen. |

> **Proffstips:** Testa alltid det genererade dokumentet i den målversion av Word, eftersom äldre versioner kan ha säkerhetsinställningar som inaktiverar ActiveX‑kontroller som standard.

## Vanliga frågor

**Fungerar detta med .NET Core?**  
Ja. Aspose.Words‑biblioteket är plattformsoberoende och fullt kompatibelt med .NET Core och .NET 5/6+.

**Kan jag tilldela ett makro till knappen programatiskt?**  
API:et bäddar inte in VBA‑kod direkt. Efter att dokumentet har genererats, öppna det i Word, aktivera fliken Developer och spela in eller skriv ett makro som refererar `btnClick`.

**Vad händer om knappen inte visas?**  
Kontrollera att fliken `Developer` är aktiverad i Word och att dokumentet inte öppnas i **Protected View**. Verifiera också att rektangelkoordinaterna ligger inom sidmarginalerna.

## Slutsats

Du vet nu hur du **skapar ActiveX‑kontroll** i en Word‑fil med C#. Handledningen täckte **hur man infogar ActiveX**, demonstrerade **lägg till interaktiv knapp**, visade **hur man skapar Word‑dokument** från grunden och illustrerade **hur man skapar knapp med kod** som kvarstår efter sparning.  

Härifrån kan du utforska ytterligare ActiveX‑typer, koppla knappen till VBA‑makron eller bädda in logiken i en större dokument‑genereringstjänst. Experimentera med olika storlekar, positioner och kontroll‑egenskaper för att passa exakt den användarupplevelse du behöver.

---

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Skapa nytt Word‑dokument](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Skapa VBA‑projekt i Word‑dokument](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Skapa och formatera ett Word‑dokument i Aspose.Words för .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}