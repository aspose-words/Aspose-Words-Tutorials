---
category: general
date: 2026-08-20
description: Lär dig hur du skapar en ActiveX‑kontroll, ställer in knappens storlek
  och lägger till knappen i Word med ett komplett C#‑exempel.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- set button size
- add button to word
- how to insert button
- create clickable button
language: sv
lastmod: 2026-08-20
og_description: Skapa ActiveX‑kontroll i en Word‑fil med C#. Den här handledningen
  visar hur du ställer in knappens storlek, lägger till knappen i Word och gör den
  klickbar.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX control
  button
og_title: Skapa en ActiveX‑kontroll i Word – steg‑för‑steg C#‑guide
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  headline: How to create ActiveX control in a Word document using C#
  type: TechArticle
- description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  name: How to create ActiveX control in a Word document using C#
  steps:
  - name: Why this works
    text: '* `InsertForms2OleControl` tells Word to embed an OLE object of type **CommandButton**,
      which is the classic ActiveX button class. * The width and height arguments
      directly **set button size**; Word translates the values from points (1 pt ≈
      1/72 in). * Naming the control (`Name = "btnSubmit"`) makes'
  - name: Pro tip
    text: 'If you want a square button, set both dimensions to the same value:'
  - name: 1. What if the button does not appear after saving?
    text: '* Verify that the Aspose.Words version supports `InsertForms2OleControl`.
      Versions prior to 22.5 lack this feature. * Ensure the target file format is
      `.docx` or `.doc`. Older formats like `.rtf` cannot store ActiveX objects.'
  - name: 2. Can I insert the button at a specific bookmark?
    text: 'Yes. Move the builder to the bookmark before calling `InsertForms2OleControl`:'
  - name: 3. How to **set button size** dynamically based on text length?
    text: Calculate the required width using the `Graphics.MeasureString` method (from
      `System.Drawing`) and convert pixels to points (`points = pixels * 72 / DPI`).
      Then pass the computed width to `InsertForms2OleControl`.
  - name: 4. Is there a way to add multiple buttons in a loop?
    text: 'Absolutely. Wrap the insertion logic in a `for` loop and adjust the `Left`
      and `Top` properties for each iteration:'
  type: HowTo
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
title: Hur man skapar en ActiveX‑kontroll i ett Word‑dokument med C#
url: /sv/java/integration-interoperability/how-to-create-activex-control-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så skapar du ActiveX‑kontroll i ett Word‑dokument med C#

Om du behöver **create ActiveX control** i en Microsoft Word‑fil, visar den här guiden exakt hur du gör det. Du kommer att se hur du **add button to Word**, ställer in knappens dimensioner och gör kontrollen klickbar—allt med ett kort, självständigt C#‑program.

I den här handledningen kommer du att:

* Förstå varför en ActiveX‑kontroll är användbar för interaktiva Word‑dokument.  
* Lära dig den exakta koden som krävs för att **set button size** och tilldela en rubrik.  
* Se hur du **create clickable button** som senare kan kopplas till ett makro eller extern logik.  

Stegen fungerar med Aspose.Words .NET 23.12 eller senare och kräver endast en .NET‑utvecklingsmiljö.

> **Prerequisite** – Du har en giltig Aspose.Words‑licens (eller så använder du utvärderingsversionen) och Visual Studio 2022 eller någon C#‑IDE.

---

## Så skapar du ActiveX‑kontroll i ett Word‑dokument

Det första steget är att instansiera ett tomt `Document` och en `DocumentBuilder`. Buildern tillhandahåller ett hög‑nivå‑API för att infoga objekt såsom ActiveX‑kontroller.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document and obtain a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // The rest of the steps are explained in the following sections.
            InsertActiveXButton(builder);

            // Save the result so you can open it in Word.
            doc.Save("ActiveXButton.docx");
            Console.WriteLine("Document saved as ActiveXButton.docx");
        }
```

`InsertActiveXButton`‑metoden (definierad nedan) innehåller logiken för **how to insert button** och konfigurerar den.

```csharp
        /// <summary>
        /// Inserts a CommandButton ActiveX control, sets its size, name, and caption.
        /// </summary>
        static void InsertActiveXButton(DocumentBuilder builder)
        {
            // Step 2: Insert a CommandButton ActiveX control with the desired size (width: 100, height: 30).
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                "CommandButton", 100, 30);

            // Step 3: Assign a name to the control for later reference.
            commandButton.Name = "btnSubmit";

            // Step 4: Set the caption that will be displayed on the button.
            commandButton.Caption = "Submit";

            // Optional: Position the button on the page (e.g., 100 points from the top left).
            commandButton.Left = 100;
            commandButton.Top = 150;
        }
    }
}
```

När programmet körs skapas **ActiveXButton.docx**. När du öppnar filen i Word visas en knapp med etiketten **Submit**. Kontrollen är fullt funktionell—att klicka på den utlöser standard‑händelsen `CommandButton_Click`, som du senare kan binda till ett VBA‑makro.

### Varför detta fungerar

* `InsertForms2OleControl` talar om för Word att bädda in ett OLE‑objekt av typen **CommandButton**, vilket är den klassiska ActiveX‑knappklassen.  
* Bredd‑ och höjdför argumenten sätter direkt **set button size**; Word översätter värdena från punkter (1 pt ≈ 1/72 tum).  
* Att namnge kontrollen (`Name = "btnSubmit"`) gör det enkelt att hitta den från VBA (`ActiveDocument.InlineShapes("btnSubmit")`).  

## Ställ in knappstorlek och rubrik

Om du behöver ett annat utseende, justera de numeriska argumenten i anropet till `InsertForms2OleControl`. Metodsignaturen är:

```csharp
Forms2OleControl InsertForms2OleControl(string progId, double width, double height);
```

* **progId** – Det programatiska identifieraren för ActiveX‑klassen (`"CommandButton"` för en standardknapp).  
* **width / height** – Storlek i punkter. För en knapp som är 2 cm bred, använd `width = 56.7` (2 cm ≈ 56.7 pt).  

Du kan också ändra rubriken efter infogning:

```csharp
commandButton.Caption = "Send Request";
```

Att ändra rubriken påverkar inte storleken, men den påverkar den visuella återkopplingen för användaren.

### Proffstips

Om du vill ha en fyrkantig knapp, sätt båda dimensionerna till samma värde:

```csharp
Forms2OleControl squareBtn = builder.InsertForms2OleControl("CommandButton", 50, 50);
squareBtn.Caption = "OK";
```

## Lägg till knapp i Word och gör den klickbar

Koden ovan har redan **add button to Word**. För att få knappen att utföra en åtgärd måste du skriva ett VBA‑makro som hanterar `Click`‑händelsen. Här är ett minimalt makro som du kan klistra in i Word‑VBA‑redigeraren (`Alt+F11` → Insert → Module):

```vba
Sub btnSubmit_Click()
    MsgBox "You clicked the Submit button!", vbInformation
End Sub
```

Eftersom kontrollen heter `btnSubmit` mappar Word automatiskt `Click`‑händelsen till `btnSubmit_Click`. Detta är det standardmässiga sättet att **create clickable button**‑funktionalitet utan externa bibliotek.

> **Note:** Säkerhetsinställningarna för makron i Word kan blockera ActiveX‑kontroller. Se till att “Enable all macros” eller “Enable VBA macros” är valt för dokumentet, eller signera makrot digitalt för produktionsbruk.

## Vanliga frågor: hur man infogar knapp och felsökning

### 1. Vad händer om knappen inte visas efter sparning?

* Verifiera att Aspose.Words‑versionen stödjer `InsertForms2OleControl`. Versioner före 22.5 saknar denna funktion.  
* Säkerställ att målfilformatet är `.docx` eller `.doc`. Äldre format som `.rtf` kan inte lagra ActiveX‑objekt.

### 2. Kan jag infoga knappen vid ett specifikt bokmärke?

Ja. Flytta buildern till bokmärket innan du anropar `InsertForms2OleControl`:

```csharp
builder.MoveToBookmark("InsertHere");
builder.InsertForms2OleControl("CommandButton", 100, 30);
```

### 3. Hur man **set button size** dynamiskt baserat på textlängd?

Beräkna den nödvändiga bredden med hjälp av `Graphics.MeasureString`‑metoden (från `System.Drawing`) och konvertera pixlar till punkter (`points = pixels * 72 / DPI`). Skicka sedan den beräknade bredden till `InsertForms2OleControl`.

### 4. Finns det ett sätt att lägga till flera knappar i en loop?

Absolut. Omge infogningslogiken med en `for`‑loop och justera `Left`‑ och `Top`‑egenskaperna för varje iteration:

```csharp
for (int i = 0; i < 3; i++)
{
    Forms2OleControl btn = builder.InsertForms2OleControl("CommandButton", 80, 25);
    btn.Name = $"btnOption{i + 1}";
    btn.Caption = $"Option {i + 1}";
    btn.Left = 50;
    btn.Top = 100 + i * 40; // stagger vertically
}
```

## Förväntat resultat

När du kör programmet och öppnar **ActiveXButton.docx**:

* En enda **Submit**‑knapp visas nära övre vänstra hörnet på den första sidan.  
* Knappens storlek matchar de dimensioner du angav (`100 pt × 30 pt`).  
* Om du lade till VBA‑makrot, visar ett klick på knappen en meddelanderuta: “You clicked the Submit button!”.

Du har nu framgångsrikt **create ActiveX control**, **set button size** och **add button to Word** samtidigt som du har lärt dig **how to insert button** och **create clickable button** för framtida automatiseringsuppgifter.

## Slutsats

I den här handledningen lärde du dig hur du **create ActiveX control** i ett Word‑dokument med C#. Genom att följa stegen kan du **set button size**, ge kontrollen ett meningsfullt namn och **add button to Word** så att den blir en **clickable button** kopplad till ett VBA‑makro.  

Härifrån kan du utforska:

* Att binda knappen till ett .NET COM‑tillägg istället för VBA.  
* Att använda andra ActiveX‑klasser såsom `CheckBox` eller `ComboBox`.  
* Att automatisera skapandet av fullständiga formulär med flera kontroller.

Känn dig fri att experimentera med olika storlekar

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa Word‑dokument med flytande bild i .NET](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [Skapa Word‑dokument med sidhuvud och sidfot med Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Skapa tillgänglig PDF från Word – Komplett guide](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}