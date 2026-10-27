---
category: general
date: 2026-10-23
description: Lär dig hur du skapar ett tomt Word‑dokument och infogar en vanlig textinnehållskontroll
  (SDT) med en platshållare med C#. Inkluderar steg‑för‑steg‑kod.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert control
- plain text content control
- how to add sdt
- add placeholder to tag
language: sv
lastmod: 2026-10-23
og_description: Skapa ett tomt Word‑dokument och infoga en enkel textinnehållskontroll
  (SDT) med en platshållare med C#. Följ det kompletta, körbara exemplet.
og_image_alt: Screenshot showing a blank Word document with a highlighted plain text
  content control
og_title: Skapa ett tomt Word‑dokument och lägg till en enkel textinnehållskontroll
  – C#‑guide
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to create a blank Word document and insert a plain text content
    control (SDT) with a placeholder using C#. Includes step‑by‑step code.
  headline: How to create blank Word document with a plain text content control in
    C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- ContentControl
- WordAutomation
title: Hur man skapar ett tomt Word‑dokument med en vanlig textinnehållskontroll i
  C#
url: /sv/java/document-manipulation/how-to-create-blank-word-document-with-a-plain-text-content/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar ett tomt Word-dokument med en plain text content control i C#

Om du behöver **skapa ett tomt Word-dokument** programatiskt, visar den här guiden exakt hur. Med Aspose.Words för .NET kan du börja med en tom fil, infoga en plain‑text StructuredDocumentTag (SDT), ge den en titel och lägga till en hjälpsam platshållare—allt i några rader C#.

Handledningen täcker varje steg du behöver, från att initiera dokumentet till att spara den slutgiltiga `.docx`. I slutet har du ett återanvändbart kodsnutt som du kan lägga in i vilket .NET‑projekt som helst.

## Förutsättningar

* .NET 6.0 (eller senare) installerat.
* En referens till NuGet‑paketet **Aspose.Words**.
* En IDE såsom Visual Studio 2022 eller Visual Studio Code.

Inga ytterligare bibliotek krävs.

## Hur man skapar ett tomt Word-dokument och lägger till en plain text content control

Den första stora uppgiften är att skapa ett **tomt Word-dokument**. Detta ger dig en ren arbetsyta som du senare kan **infoga kontroll**‑element på.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Step 1: Create a new blank document and a DocumentBuilder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Varför detta fungerar*: `Document()` skapar en in‑memory‑representation av en Word‑fil utan sidor. `DocumentBuilder` är hjälparklassen som låter dig lägga till stycken, tabeller och content controls.

## Hur man infogar kontroll med DocumentBuilder

Nu när dokumentet finns, kan du **infoga kontroll**‑objekt direkt där markören är placerad. För en plain‑text content control, använd `InsertStructuredDocumentTag`.

```csharp
// Step 2: Insert a plain‑text StructuredDocumentTag (SDT) inline
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, MarkupLevel.Inline);
```

*Förklaring*:  
* `StructuredDocumentTagType.PlainText` talar om för Aspose.Words att skapa en **plain text content control**.  
* `MarkupLevel.Inline` placerar kontrollen i det aktuella stycket, vilket får den att fungera som vanlig text.

## Hur man lägger till sdt-titel och platshållartext

En välnamngiven kontroll är lättare att hitta senare, särskilt när du behöver binda data eller utföra validering. Steget **add placeholder to tag** förbättrar också användarupplevelsen.

```csharp
// Step 3: Give the SDT a meaningful title (used for identification)
sdt.Title = "CustomerName";

// Step 4: Add placeholder text so the user knows what to enter
sdt.AppendChild(new Run(doc, "Enter name here"));
```

*Varför detta är viktigt*:  
* `Title`‑egenskapen är metadata som du kan fråga med `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.  
* Platshållaren (`Run` med “Enter name here”) visas gråtonad i Word, vilket uppmanar slutanvändaren att ersätta den.

## Hur man sparar dokumentet med SDT

Slutligen, spara filen till disk. Sökvägen kan vara absolut eller relativ till ditt programs arbetskatalog.

```csharp
// Step 5: Save the document with the SDT to a file
doc.Save("SDTExample.docx");
```

När du öppnar **SDTExample.docx** i Microsoft Word kommer du att se en enda rad som innehåller en gråtonad platshållare i en ram—exakt den **plain text content control** du skapade.

### Förväntat resultat

| Plats | Visuell ledtråd |
|----------|------------|
| Inuti det första stycket | En rektangulär ruta märkt “Enter name here” (platshållare) |

Du kan skriva ett namn direkt i rutan; Word kommer att behandla den angivna texten som innehållet i SDT.

## Lägg till flera kontroller (valfritt)

Om du behöver mer än en **plain text content control**, upprepa steg 2‑4 med en ny `DocumentBuilder`‑position. Till exempel, för att lägga till ett adressfält:

```csharp
builder.Writeln(); // Move to a new paragraph
StructuredDocumentTag addressSdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, MarkupLevel.Inline);
addressSdt.Title = "CustomerAddress";
addressSdt.AppendChild(new Run(doc, "Enter address here"));
```

*Tips*: Använd `builder.Writeln()` för att starta ett nytt stycke innan du infogar en annan SDT, så att layouten hålls prydlig.

## Vanliga fallgropar och hur man undviker dem

| Problem | Orsak | Lösning |
|-------|-------|-----|
| Platshållartext försvinner efter sparning | SDT skapades med `MarkupLevel.Block` istället för `Inline` | Använd `MarkupLevel.Inline` för inline‑platshållare |
| Titel är inte sökbar | Titel sattes aldrig eller sattes efter sparning | Sätt `sdt.Title` **innan** du anropar `doc.Save()` |
| Dokumentet visas tomt i Word | Inget innehåll lades till efter att dokumentet skapades | Se till att du lägger till minst ett stycke eller en kontroll innan du sparar |

## Proffstips: Återanvända kodsnutten i en hjälpfunktion

Att kapsla in logiken gör den återanvändbar i flera projekt:

```csharp
public static Document CreateDocumentWithPlainTextControl(string title, string placeholder)
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);

    StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
        StructuredDocumentTagType.PlainText, MarkupLevel.Inline);
    sdt.Title = title;
    sdt.AppendChild(new Run(doc, placeholder));

    return doc;
}

// Usage
Document myDoc = CreateDocumentWithPlainTextControl("OrderNumber", "Enter order #");
myDoc.Save("OrderForm.docx");
```

*Varför detta hjälper*: Metoden isolerar logiken för **skapa ett tomt Word-dokument**, vilket låter dig generera flera mallar med olika titlar och platshållare utan att duplicera kod.

## Nästa steg

Nu när du vet **hur man infogar kontroll** och **lägger till platshållare till tagg**, kan du utforska:

* Bindning av SDT till anpassade XML-delar (`doc.CustomXmlParts`) – användbart för datadrivna mallar.
* Konvertera dokumentet till PDF samtidigt som content controls bevaras.
* Använda andra `StructuredDocumentTagType`‑värden såsom `Date`, `ComboBox` eller `CheckBox` för mer avancerade formulär.

Var och en av dessa ämnen bygger på det grundläggande mönstret som demonstrerats här.

---

**Sammanfattning**

Denna handledning gick igenom hur du skapar ett **tomt Word-dokument**, infogar en **plain text content control**, ger den en titel och lägger till en hjälpsam platshållare. Det kompletta, körbara exemplet kan kopieras in i vilket .NET‑projekt som helst, och den valfria hjälpfunktionen visar hur man skalar metoden. Med detta fundament är du redo att bygga sofistikerade Word‑baserade formulär och mallar i C#.

---

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa nytt Word-dokument och infoga innehållskontroll i C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)
- [Skapa Word-dokument programatiskt – lägg till innehållskontroll och platshållare](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Hur man lägger till innehållskontroll och skapar Word-dokument med Aspose – Komplett](/words/english/net/programming-with-sdt/how-to-add-content-control-and-create-word-document-with-asp/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}