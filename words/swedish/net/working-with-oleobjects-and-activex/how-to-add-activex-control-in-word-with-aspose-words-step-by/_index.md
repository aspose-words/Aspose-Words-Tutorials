---
category: general
date: 2026-08-07
description: Lär dig hur du lägger till en ActiveX‑kontroll i ett Word‑dokument med
  C#. Inkluderar att associera ett makro med en knapp och lägga till klickbara knapp‑exempel
  i Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex control
- associate macro with button
- add clickable button word
- add command button word
language: sv
lastmod: 2026-08-07
og_description: hur du lägger till en ActiveX‑kontroll i ett Word‑dokument med Aspose.Words.
  Följ den här guiden för att infoga en knapp, associera ett makro med knappen och
  lägga till ett klickbart knappord.
og_image_alt: Screenshot showing a Word document with an ActiveX command button inserted
  via Aspose.Words
og_title: hur man lägger till ActiveX‑kontroll i Word – komplett C#‑handledning
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  headline: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  name: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  steps:
  - name: Why each line matters
    text: '| Line | Purpose | |------|---------| | `Document doc = new Document();`
      | Instantiates a fresh Word package in memory. | | `DocumentBuilder builder
      = new DocumentBuilder(doc);` | Provides a fluent API for inserting content,
      including ActiveX controls. | | `InsertForms2OleControl` | The only Aspose.'
  - name: Common pitfalls when associating a macro
    text: '* **Macro security settings** – If the document is opened on a machine
      with strict security policies, the macro may be blocked. Provide instructions
      to lower the security level or sign the macro. * **Naming conflicts** – The
      macro name must be unique within the document’s VBA project; otherwise Word'
  - name: 'Edge case: Long captions'
    text: Word truncates captions that exceed the button’s width. To avoid clipping,
      either increase the width argument in `InsertForms2OleControl` or shorten the
      text. Testing with different languages (e.g., German or Japanese) is advisable
      because character width varies.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Hur man lägger till ActiveX‑kontroll i Word med Aspose.Words – steg‑för‑steg‑guide
url: /sv/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# hur man lägger till ActiveX-kontroll i Word med Aspose.Words

Om du behöver **lägga till en ActiveX‑kontroll** i en Microsoft Word‑fil programatiskt, visar den här handledningen de exakta stegen med Aspose.Words för .NET. Du får se hur du infogar en kommandoknapp, sätter dess rubrik och **kopplar ett makro till knappen** så att kontrollen reagerar när en användare klickar på den. I slutet har du en makro‑aktiverad `.docm`‑fil som innehåller en fullt fungerande knapp.

Att lägga till en ActiveX‑knapp är ett vanligt krav när man bygger interaktiva mallar såsom låneansökningar, anställningsformulär eller automatiserade rapporter. Denna guide går igenom varje kodrad, förklarar **varför** varje steg är viktigt och tar upp vanliga fallgropar du kan stöta på.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6 (eller .NET Core 3.1 / .NET Framework 4.8) installerat.
* En giltig Aspose.Words för .NET‑licens eller en tillfällig utvärderingsnyckel.
* Visual Studio 2022 (eller någon IDE som stödjer C#).
* Grundläggande kunskap om Word‑makron (VBA) om du planerar att skriva makrot som knappen ska trigga.

> **Pro tip:** När du kör exemplet, spara utdata till en mapp där du har skrivbehörighet, annars kommer `doc.Save` att kasta ett undantag.

## Hur man lägger till ActiveX‑kontroll i ett Word‑dokument med Aspose.Words

Kärnan i lösningen är ett kort C#‑program som skapar ett nytt dokument, infogar en ActiveX **CommandButton**‑kontroll och sparar filen som ett makro‑aktiverat dokument (`.docm`). Koden är komplett och klar att kopiera‑klistra in.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert an ActiveX CommandButton control (Forms2OleControl)
        // Parameters: control type, left, top, width, height (in points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            0,   // left position (points)
            0,   // top position (points)
            150, // width (points)
            30   // height (points)
        );

        // Step 3: Set the button's visible caption – this is the add clickable button word
        commandButton.Caption = "Click Me";

        // Step 4 (optional): Associate a macro with the button's click action
        // This demonstrates how to associate macro with button
        commandButton.OnAction = "MyMacro";

        // Step 5: Save the document as a macro‑enabled file to preserve the button reference
        // The file extension .docm tells Word to keep ActiveX controls and macros
        doc.Save("CommandButton.docm");
    }
}
```

### Varför varje rad är viktig

| Rad | Syfte |
|------|---------|
| `Document doc = new Document();` | Skapar ett nytt Word‑paket i minnet. |
| `DocumentBuilder builder = new DocumentBuilder(doc);` | Tillhandahåller ett flytande API för att infoga innehåll, inklusive ActiveX‑kontroller. |
| `InsertForms2OleControl` | Den enda Aspose.Words‑metoden som skapar en ActiveX‑kontroll; du anger kontrolltypen (`CommandButton`) och dess geometri. |
| `commandButton.Caption = "Click Me";` | Sätter **knapptexten** som slutanvändaren ser. Utan en rubrik visas knappen tom. |
| `commandButton.OnAction = "MyMacro";` | **kopplar ett makro till knappen** – talar om för Word vilket VBA‑makro som ska köras när kontrollen klickas. |
| `doc.Save("CommandButton.docm");` | Sparar dokumentet som en makro‑aktiverad fil; en vanlig `.docx` skulle ta bort kontrollen och makrot. |

> **Obs:** Koordinaterna (vänster, topp) mäts i punkter (1 pt ≈ 1/72 tum). Justera dem för att placera knappen där du vill på sidan.

## Hur man kopplar ett makro till knappen

`OnAction`‑egenskapen länkar knappen till ett VBA‑makro med namnet `MyMacro`. Du måste fortfarande skapa det makrot i Word‑filen, antingen manuellt eller genom att injicera VBA‑kod programatiskt (Aspose.Words skriver inte VBA‑kod). Här är ett minimalt makro du kan lägga till via Word’s **Developer → Visual Basic**‑editor:

```vba
Sub MyMacro()
    MsgBox "Button clicked!", vbInformation, "ActiveX Demo"
End Sub
```

När användaren öppnar `CommandButton.docm` och klickar på knappen, kör Word `MyMacro` och visar en meddelanderuta. Om makrosäkerheten är inställd på **Disable all macros without notification**, visas knappen som inaktiverad. Råda användarna att aktivera makron för dokumentet eller signera makrot med ett betrott certifikat.

### Vanliga fallgropar när du kopplar ett makro

* **Makrosäkerhetsinställningar** – Om dokumentet öppnas på en maskin med strikta säkerhetspolicyer kan makrot blockeras. Ge instruktioner för att sänka säkerhetsnivån eller signera makrot.
* **Namnkrockar** – Makronamnet måste vara unikt inom dokumentets VBA‑projekt; annars ger Word felmeddelandet “duplicate procedure name”.
* **64‑bit vs 32‑bit Word** – ActiveX‑kontroller fungerar likadant, men VBA‑editorn kan visa olika varningsmeddelanden beroende på Office‑versionen.

## Hur man lägger till knapptext i ett Word‑formulär

`Caption`‑egenskapen är vad användarna ser på knappen. Du kan anpassa den ytterligare:

```csharp
commandButton.Caption = "Submit Form";
commandButton.Font.Size = 10;      // Adjust font size
commandButton.Font.Name = "Arial"; // Choose a readable font
```

Om du behöver att rubriken ska ändras dynamiskt baserat på användarens inmatning, kan du senare komma åt kontrollen via Word‑objektmodellen:

```vba
Sub UpdateButtonCaption()
    Dim btn As InlineShape
    Set btn = ActiveDocument.InlineShapes(1).OLEFormat.Object
    btn.Caption = "Updated Text"
End Sub
```

### Edge case: Långa rubriker

Word trunkerar rubriker som överskrider knappens bredd. För att undvika avklippning, öka breddargumentet i `InsertForms2OleControl` eller förkorta texten. Testa med olika språk (t.ex. tyska eller japanska) eftersom teckenbredden varierar.

## Hur man lägger till kommandoknapp för formulärautomatisering

Utöver den visuella rubriken täcker begreppet **add command button word** det programatiska namnet på kontrollen. Aspose.Words exponerar inte en direkt `Name`‑egenskap för ActiveX‑kontroller, men du kan sätta `AltText`‑fältet, som Word behandlar som kontrollens identifierare:

```csharp
commandButton.AltText = "SubmitButton";
```

Senare i VBA kan du referera till knappen via dess `AltText`‑värde:

```vba
Sub FindButton()
    Dim shp As Shape
    For Each shp In ActiveDocument.Shapes
        If shp.AlternativeText = "SubmitButton" Then
            MsgBox "Found the Submit button!"
        End If
    Next shp
End Sub
```

Denna teknik är användbar när du har flera knappar och behöver skilja dem åt programatiskt.

## Fullt fungerande exempel

Nedan är det kompletta programmet som du kan kompilera och köra som en konsolapplikation. Det inkluderar valfri formatering, makrokoppling och en kommentarsblock som beskriver varje steg.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class AddActiveXButton
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert an ActiveX CommandButton.
        //    left=50pt, top=100pt places the button away from the margin.
        Forms2OleControl btn = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            50,   // left
            100,  // top
            200,  // width
            40    // height
        );

        // 3️⃣ Add clickable button word (caption) and style it.
        btn.Caption = "Submit Form";
        btn.Font.Size = 11;
        btn.Font.Name = "Calibri";

        // 4️⃣ Associate macro with button – this is how to associate macro with button.
        btn.OnAction = "SubmitMacro";

        // 5️⃣ Give the control a friendly identifier (add command button word).
        btn.AltText = "SubmitButton";

        // 6️⃣ Save as macro‑enabled document.
        doc.Save("SubmitForm.docm");
    }
}
```

**Förväntat resultat:** När du öppnar `SubmitForm.docm` i Microsoft Word visas en blåramad knapp med etiketten *Submit Form*. Att klicka på knappen triggar VBA‑makrot `SubmitMacro` (förutsatt att du har lagt till makrot i dokumentet). Knappen kan flyttas, storleksändras eller stylas ytterligare med samma `Forms2OleControl`‑objekt.

## Testa lösningen

1. Bygg och kör C#‑konsolappen.
2. Öppna den genererade `SubmitForm.docm` i Word.
3. Om du blir ombedd, aktivera makron.
4. Klicka på *Submit Form*-knappen – du bör se meddelanderutan som definierats i `SubmitMacro`.

Om knappen visas men ingenting händer, dubbelkolla att makronamnet exakt matchar (`SubmitMacro`) och att makrosäkerheten inte blockerar körning.

## Vanliga frågor

| Fråga | Svar |
|----------|--------|
| *Kan jag lägga till mer än en ActiveX‑knapp?* | Ja. Anropa `InsertForms2OleControl` flera gånger med olika koordinater. Använd olika `OnAction`‑ och `AltText`‑värden för att särskilja dem. |
| *Är ActiveX‑kontrollen synlig i Word Online?* | Nej. |

## Vad bör du lära dig härnäst?

De följande handledningarna täcker närbesläktade ämnen som bygger vidare på teknikerna i den här guiden. Varje resurs innehåller kompletta kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationssätt i dina egna projekt.

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Add a New Section to Word Document | Aspose.Words for .NET](/words/english/net/document-sections/add-section/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}